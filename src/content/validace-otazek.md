# Validace otázek

Vytvořit dotazník, který respondenty neotráví a vám přinese použitelná data, je trochu alchymie. Tady je 5 základních ingrediencí pro správně položenou otázku:

## 5 pravidel pro otázky v dotazníku

* **Srozumitelnost:** Používejte jednoduchý jazyk a vyhněte se odbornému slangu, kterému by respondent nemusel rozumět.
* **Jednoznačnost:** Otázka musí mít pro všechny stejný význam; nesmí připouštět různé výklady.
* **Jedna věc v jedné otázce:** Neptejte se na dvě různá témata najednou (tzv. „double-barreled questions“).
* **Neutralita:** Formulujte otázku nezaujatě, bez podsouvání konkrétní „správné“ odpovědi.
* **Vyčerpávající a výlučné odpovědi:** U uzavřených otázek nabídněte všechny reálné možnosti tak, aby se vzájemně nepřekrývaly.

--- 

## Příklady špatně formulovaných otázek

1. *Jak hodnotíte přístup vedení školy a připravenost učitelů na začleňování žáků s odlišným mateřským jazykem?*
2. *Souhlasíte s většinou odborníků, že integrace cizinců je pro české školství jednoznačně prospěšná?*
3. *Máte ve své třídě hodně dětí cizinců?*

--- 

## Kontrola otázek pomocí AI

Pro tento příklad využijeme oficiální rozhraní: <a href="https://gemini.google.com/" target="_blank">gemini.google.com</a>

```text
Jsi expert na tvorbu dotazníků a uživatelský průzkum. Tvým úkolem je zkontrolovat níže uvedené otázky podle těchto 5 pravidel:

1. **Srozumitelnost** (žádný slang, jednoduchý jazyk).
2. **Jednoznačnost** (pouze jeden možný výklad).
3. **Jedna věc v jedné otázce** (zákaz "double-barreled" otázek).
4. **Neutralita** (žádné podsouvání odpovědi).
5. **Vyčerpávající a výlučné odpovědi** (jasné a nepřekrývající se možnosti).

Pro každou zadanou otázku vypracuj analýzu v tomto formátu:

# Otázka: {text otázky}

# Hodnocení

* {stručné zhodnocení dle 1. kritéria}
* {stručné zhodnocení dle 2. kritéria, atd.}

# Návrh

{Zde napiš opravenou a lépe formulovanou verzi otázky}


**Zde jsou otázky ke kontrole:**

1. *Jak hodnotíte přístup vedení školy a připravenost učitelů na začleňování žáků s odlišným mateřským jazykem?*
2. *Souhlasíte s většinou odborníků, že integrace cizinců je pro české školství jednoznačně prospěšná?*
3. *Máte ve své třídě hodně dětí cizinců?*
```
