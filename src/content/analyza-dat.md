# Analyza dat

Využití umělé inteligence k transformaci surových dat (CSV) do interaktivních přehledů a hloubkových analýz.

Máte-li k dispozici výsledky dotazníku v podobě datové tabulky Gemini dokáže s těmito daty pracovat přímo – pomocí analýzy kódu (Python) nebo vytvořením interaktivních aplikací (React).

![analza-dat](./assets/img/dashboard.png)

--- 

## Datová analýza (Python)

Zdrojová data jsou dostupná v CSV souboru <a href="./assets/data/odpovedi.csv" target="_blank">odpovedi.csv</a>. V této fázi necháte AI, aby se "podívala" dovnitř souboru, spočítala klíčové metriky a identifikovala trendy.

### Prompt

```text
Jsi datový analytik. Analyzuj přiložený soubor s výsledky dotazníku. 
Proveď následující kroky:
1. Vyčisti názvy sloupců pro lepší čitelnost.
2. Spočítej celkové počty respondentů a rozděl je podle hlavních kategorií.
3. Identifikuj 3 nejdůležitější trendy, které z dat vyplývají.
4. Výsledky shrň do přehledných bodů v češtině.
```

---
## Interaktivní infografika

Statické grafy jsou užitečné, ale interaktivní webová stránka umožní uživateli data "prozkoumávat" a přepínat mezi různými pohledy. Jakmile máte data zanalyzovaná, použijte následující prompt pro vytvoření vizuálního výstupu:

### Prompt

```text
Na základě předchozí analýzy vytvoř interaktivní infografiku jako statickou webovou aplikaci za použití HTML/CSS a vanilla JS. Použij Tailwind CSS pro styl a Lucide pro ikony.

Požadavky na aplikaci:
- Moderní a čistý design (tmavé záhlaví, světlý zbytek).
- Přehledné karty s hlavními statistikami (KPIs).
- Interaktivní grafy (použij knihovnu Recharts) – např. koláčový graf pro rozdělení skupin a sloupcový pro bariéry.
- Navigační tabulka pro přepínání mezi různými tématy (např. Přehled, Podpora, Problémy).
- Přidej krátké textové shrnutí a citace z otevřených otázek pro dokreslení kontextu.

### **Barevná paleta**

* **Primární barvy:** Licorice (#2E3544) , Tropical Blue (#B3C9F2) , White Smoke (#F2F2F2) , Cerise (#F22574) , Medium Spring Green (#13EAB7) a Dark Tangerine (#F7A520).

* **Sekundární barvy (akcenty):** Světle růžová (#FFA9D4) , světle žlutá (#FFEC90) , světle mátová (#A9FFE6) a světle modrá (#89AADB).

### **Typografie a sazba**

* **Písmo:** Hlavním fontem je **Roboto** (v řezech Black a Thin).

Využíj nástroj @canva
```

--- 

# 💡 Tip

Pokud pracujete s daty, která obsahují citlivé údaje, nebo jsou příliš rozsáhlá, zaměřte se na tyto funkce:

- **Code Execution**: Gemini spouští kód v izolovaném prostředí. Můžete ji požádat o vygenerování grafů ke stažení (PNG/JPG) pomocí knihovny Matplotlib.
- **Agregace dat**: Nechte AI vytvořit novou, zjednodušenou tabulku (např. summary.csv), kterou pak můžete snadněji importovat do svých prezentací.
- **Srovnávání**: Pokud máte data z více let, nahrajte oba soubory a zeptejte se: "Porovnej výsledky z roku 2023 a 2024. V čem nastal největší posun?"