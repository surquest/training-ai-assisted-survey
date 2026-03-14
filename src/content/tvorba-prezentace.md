# Tvorba prezentací

**Využití umělé inteligence pro rychlou přípravu podkladů a struktury slidů při dodržení korporátní identity.**

Místo zaplnění prázdného bílého papíru nechte Gemini navrhnout:

* logickou strukturu, 
* texty 
* vizuální koncept, který odpovídá vašim pravidlům (barvy, tón komunikace, cílová skupina).

---

## Webové rozhraní (Gemini)

Pro návrh obsahu využijeme standardní rozhraní [gemini.google.com](https://gemini.google.com/). Gemini vám nepomůže jen s textem, ale dokáže připravit i instrukce pro grafika nebo kód pro automatické vygenerování slidů v PowerPointu.

### Prompt pro definici vizuálu a obsahu

Dokument shrnující informace: [Shrnutí](./assets/data/shrnuti.otevrena-otazka.md).

```text
Jsi expert na vizuální komunikaci a tvorbu prezentací. Tvým úkolem je navrhnout strukturu prezentace na téma: **Největší problémy vzdělávání žáku s nedostatečnou znalostí češtiny**.

Cílová skupina: Ministerstvo školství, mládeže a tělovýchovy 
Zde je stručný přehled brandingu surQuest v češtině:

### **Barevná paleta**

* **Primární barvy:** Licorice (#2E3544) , Tropical Blue (#B3C9F2) , White Smoke (#F2F2F2) , Cerise (#F22574) , Medium Spring Green (#13EAB7) a Dark Tangerine (#F7A520).

* **Sekundární barvy (akcenty):** Světle růžová (#FFA9D4) , světle žlutá (#FFEC90) , světle mátová (#A9FFE6) a světle modrá (#89AADB).

### **Typografie a sazba**

* **Písmo:** Hlavním fontem je **Roboto** (v řezech Black a Thin).
* **Hierarchie:** Nadpis H1 je Black , zatímco H2, H3 a odstavce jsou v řezu Thin.
* **Velikosti:** H2 je dvojnásobkem H1; H3 a H1 mají stejnou velikost ; odstavec tvoří 75 % velikosti H1.
* **Mezery:** Prokládání (kerning) je 200 u nadpisů a 100 u odstavců. Řádkování (leading) je vždy dvojnásobkem velikosti písma.

Navrhni obsah maximálně 15 slidů. Pro každý slide uveď:
1. Název (Nadpis)
2. Klíčové body (max 3)
3. Návrh vizuálu (popis obrázku, grafu nebo ikony)
4. Poznámky pro řečníka (2 věty)

Použíj nástroj @canva.

```

--- 

### Očekávaný výstup

Gemini vám vrátí strukturovaný přehled, který slouží jako „scénář“ vaší prezentace.

| Číslo slidu | Název | Vizuální prvek | Hlavní sdělení |
| --- | --- | --- | --- |
| **1** | Úvodní slide | Logo školy v levém horním rohu, fotka týmu | Představení projektu |
| **2** | Kontext a cíle | Ikony znázorňující růst a spolupráci | Proč to děláme |
| **3** | Datový přehled | Sloupcový graf v barvě #000080 | Konkrétní počty žáků |

---

## 💡 **Tip pro bleskovou automatizaci (VBA)**

> Pokud nechcete texty do PowerPointu kopírovat ručně, Gemini vám může napsat **VBA makro**. Stačí do chatu připsat:
> *„Napiš mi VBA kód pro PowerPoint, který automaticky vytvoří tyto slidy s textem a nastaví pozadí na barvu #000080.“*
> Vy pak jen v PowerPointu stisknete `Alt + F11`, vložíte kód a prezentace se „sama“ vykliká.

---

## Generování obrázků do prezentace

Pro zachování jednotného stylu je důležité, aby všechny obrázky v prezentaci měly podobnou estetiku. Můžete využít integrovaný generátor obrázků přímo v Gemini.

### Prompt pro vizuální sadu

```text
Vygeneruj 3 fotorealistické obrázky pro mou prezentaci.
Téma: Spolupráce dětí v multikulturní třídě.
Vizuální styl: Jasné barvy, denní světlo, moderní česká škola, rozostřené pozadí.
Obrázky musí působit inkluzivně a optimisticky.

```

---

## Srovnání: Manuální tvorba vs. AI asistence

| Funkce | Manuální tvorba | S využitím Gemini |
| --- | --- | --- |
| **Příprava struktury** | 60+ minut (přemýšlení) | **2 minuty (generování návrhu)** |
| **Hledání obrázků** | Procházení fotobank (často placené) | **Okamžité generování na míru** |
| **Sjednocení stylu** | Riziko nekonzistence | **Striktní dodržení zadané CI** |
| **Technické provedení** | Ruční formátování | Možnost exportu přes VBA/Markdown |
