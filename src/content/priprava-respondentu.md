# Příprava respondentů

**Využití umělé inteligence ke sběru kontaktů na vedení škol.**

Mějme například následující seznam škol:
```text
Gymnázium J. G. Mendela a jeho zařízení a Základní umělecká škola, školská právnická osoba
Akademické gymnázium a Jazyková škola s právem státní jazykové zkoušky, školy hlavního města Prahy
Českoslovanská akademie obchodní, střední odborná škola, Praha 2, Resslova 5
```

---

## Webové rozhraní (Gemini s Google Search)

Pro tento příklad využijeme oficiální rozhraní: <a href="https://gemini.google.com/" target="_blank">gemini.google.com</a>

### Prompt

Zkopírujte a vložte následující text do Gemini:

```text
Pro níže uvedený seznam škol najdi na jejich oficiálních webových stránkách jméno současného ředitele/ředitelky a jejich pracovní e-mailovou adresu. 

Výsledek zpracuj do přehledné tabulky, která bude obsahovat sloupce: Název školy, Jméno ředitele, E-mail a Zdroj (URL webu).

Seznam škol:
- Gymnázium J. G. Mendela a jeho zařízení a Základní umělecká škola, školská právnická osoba
- Akademické gymnázium a Jazyková škola s právem státní jazykové zkoušky, školy hlavního města Prahy
- Českoslovanská akademie obchodní, střední odborná škola, Praha 2, Resslova 5
```

### Očekávaný výstup

Gemini vám vrátí podobnou tabulku:

| Název školy | Jméno ředitele | E-mail | Zdroj |
| :--- | :--- | :--- | :--- |
| **Gymnázium J. G. Mendela...** | PhDr. Ludmila Čápová | capova@gjgm.cz | <a href="https://www.gjgm.cz" target="_blank">gjgm.cz</a> |
| **Akademické gymnázium...** | PaedDr. Milan Macek, CSc. | macek@akademickegymnazium.cz | <a href="https://www.akademickegymnazium.cz" target="_blank">akademickegymnazium.cz</a> |

---

## 💡 **Tip pro hromadné zpracování**
> 
> Pokud potřebujete zpracovat <a href="./assets/data/skoly.csv" target="_blank">seznam o více položkách</a>, stačí školy do promptu vložit najednou (například zkopírovat sloupec z Excelu). Gemini projde weby za vás a vy jen zkontrolujete finální data. 
> 
> Aby se vám data lépe přenášela zpět do Excelu, můžete prompt upravit přidáním věty: **„Výstup vrať ve formátu CSV.

```text
Pro tento seznam škol najdi na jejich oficiálních webových stránkách jméno současného ředitele/ředitelky a jejich pracovní e-mailovou adresu. Výsledek zpracuj do přehledné tabulky, která bude obsahovat sloupce: Název školy, Jméno ředitele, E-mail a Zdroj (URL).

Data vrať ve formátu CSV-
```

---

## Automatizace pomocí kódu (Python)

Pro rozsáhlejší seznamy je ideální využít skript. Pro tento příklad použijeme <a href="https://colab.research.google.com/" target="_blank">Google Colab</a>. 

Zdrojem dat je <a href="./assets/data/skoly.csv" target="_blank">seznam o více položkách</a>. API klíč pro přístup k modelům lze zdarma získat přes <a href="https://aistudio.google.com/" target="_blank">Google AI Studio</a>.

### Python skript

```python
# 1. Instalace potřebných balíčků
!pip install -q -U google-genai

import pandas as pd
import json
import time
from google import genai
from google.genai import types

# 2. Nastavení klienta (vložte svůj vlastní API klíč)
API_KEY = "<VÁŠ_API_KLÍČ>"
client = genai.Client(api_key=API_KEY)

# 3. Definice promptu
# DŮLEŽITÉ: Složené závorky pro JSON uvnitř f-stringu musí být zdvojené {{ }}
# Jinak se je Python snaží interpretovat jako proměnné a skript selže.
prompt = """
Najdi na oficiálním webu jméno současného ředitele/ředitelky a jejich pracovní e-mail pro tuto školu: {skola}.
Odpověz striktně a pouze ve formátu JSON:
{{
    "jmeno": "Jméno Příjmení",
    "email": "email@skola.cz",
    "zdroj": "URL adresa webu školy"
}}
"""

# Vstupní data (zde můžete případně načíst vaše CSV)
skoly = [
    "Gymnázium Jiřího Gutha-Jarkovského, Praha 1, Truhlářská 22", 
    "Gymnázium prof. Jana Patočky, Praha 1, Jindřišská 36"
]

vysledky = []

# Konfigurace pro využití Google Search nástroje
config = types.GenerateContentConfig(
    tools=[types.Tool(google_search=types.GoogleSearch())]
)

# 4. Zpracování seznamu
for skola in skoly:
    print(f"Hledám: {skola}...")
    
    # Používáme model s podporou vyhledávání
    response = client.models.generate_content(
        model='gemini-2.5-flash', # Doporučujeme používat aktuální stabilní model
        contents=prompt.format(skola=skola),
        config=config
    )
    
    # Očištění textu odpovědi od markdown formátování (pokud ho model vrátí)
    clean_text = response.text.strip().replace("```json", "").replace("```", "")
    
    try:
        data = json.loads(clean_text)
        data['nazev_skoly'] = skola # Přidáme název školy do výsledku pro přehlednost
        vysledky.append(data)
        print(f"Výsledek: Nalezeno ({data.get('jmeno')})")
    except json.JSONDecodeError:
        print(f"Chyba při zpracování JSONu u školy: {skola}")
        print(f"Surová odpověď modelu: {response.text}")
        
    time.sleep(1) # Krátká pauza, abychom nepřetížili API

# 5. Uložení do tabulky a export do CSV s UTF-8 kódováním pro Excel
df = pd.DataFrame(vysledky)
df.to_csv('skoly_search_vysledky.csv', index=False, encoding='utf-8-sig')

# Zobrazení výsledků v Colabu
display(df)
```