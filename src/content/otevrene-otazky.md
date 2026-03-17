# Otevřené otázek

**Využití NotebookLM pro hloubkovou analýzu kvalitativních dat z výzkumu.**

Máte-li stovky odpovědí na otevřené otázky jako je: **Uveďte, co považujete za největší problém v souvislosti se vzděláváním žáků s nedostatečnou znalostí vyučovacího jazyka ve Vaší škole?** Ruční třídění do kategorií je časově náročné. NotebookLM od Googlu funguje jako inteligentní asistent, který pracuje **pouze nad vašimi daty**, což eliminuje halucinace a umožňuje bleskovou syntézu témat.

---

## Webové rozhraní (NotebookLM)

Oficiální rozhraní najdete na adrese: <a href="https://notebooklm.google.com/" target="_blank">notebooklm.google.com</a>

### Příprava dat

1. Exportujte odpovědi z vašeho dotazníku (např. z Google Forms nebo SurveyMonkey) do formátu Excel nebo CSV.
2. Sloupec s odpověďmi zkopírujte do dokumentu Google (Google Doc) nebo uložte jako PDF/TXT.
3. V NotebookLM vytvořte nový zápisník (**New Notebook**) a nahrajte tento soubor jako zdroj (**Source**).

Připravená data ke stažení s v souboru <a href="./assets/data/odpovedi.otevrena-otazka.txt" target="_blank">odpovedi.otevrena-otazka.txt</a>

--- 

### Prompt pro analýzu témat

Jakmile jsou data nahraná, do chatu vložte následující zadání:

```text
Jsi expert na kvalitativní analýzu dat. V nahraném dokumentu jsou odpovědi respondentů na otázku **Uveďte, co považujete za největší problém v souvislosti se vzděláváním žáků s nedostatečnou znalostí vyučovacího jazyka ve Vaší škole?**.

Proveď tematickou analýzu těchto odpovědí na otázku: **„Uveďte, co považujete za největší problém v souvislosti se vzděláváním žáků s nedostatečnou znalostí vyučovacího jazyka ve Vaší škole?“**

1. **Identifikuj 5–7 hlavních problémových témat**, která se v odpovědích opakují (např. jazyková bariéra, nedostatek asistentů pedagoga, obtížná komunikace s rodiči, nedostatek metodické podpory apod.).
2. **U každého tématu uveď stručný popis** a **odhadni, kolik procent respondentů jej zmiňuje**.
3. **Ke každému tématu vyber 2–3 reprezentativní citace** z odpovědí (anonymizované), které daný problém ilustrují.
4. **Na závěr shrň celkový charakter odpovědí**, zejména zda se soustředí spíše na organizační, pedagogické, jazykové nebo sociální problémy, a případně porovnej rozdíly mezi skupinami respondentů (např. učitelé, vedení školy, asistenti pedagoga).

```

### Očekávaný výstup

NotebookLM vám vygeneruje strukturovaný přehled. Velkou výhodou je, že u každého tvrzení uvidíte **citace (zdroje)** – po kliknutí na číslo v textu se vám v levém panelu zobrazí přesná pasáž z nahraného dokumentu, ze které AI čerpala.

---

## 💡 Tip pro pokročilou práci s daty

> NotebookLM není jen chat, ale analytický prostor. Pokud pracujete na rozsáhlém výzkumu školní integrace, vyzkoušejte tyto funkce:
> * **Vytvoření person:** Zeptejte se: *„Na základě odpovědí vytvoř 3 archetypy (persony) respondentů (např. přetížený učitel, adaptující se žák, zmatený rodič) a popiš jejich hlavní obavy a potřeby při začleňování.“*
> * **Hledání extrémů:** Zkuste prompt: *„Najdi v odpovědích názory na výuku češtiny jako druhého jazyka, které jdou proti hlavnímu proudu nebo nabízejí neobvyklá řešení.“*
> * **Audio Overview:** V pravém horním rohu můžete nechat vygenerovat „podcast“, kde dva AI moderátoři prodiskutují výsledky vašeho průzkumu. Skvělé pro rychlé představení výsledků sborovně nebo vedení školy.

---

## Srovnání: ChatGPT vs. NotebookLM

| Funkce | Standardní AI (ChatGPT/Gemini) | NotebookLM |
| --- | --- | --- |
| **Zdroj dat** | Trénovací data + vložený text | **Pouze vámi nahrané dokumenty** |
| **Ověřitelnost** | Často bez přesných odkazů | **Okamžité citace z vašich dat** |
| **Kapacita** | Omezená délkou kontextového okna | Zvládne tisíce stran textu |
| **Soukromí** | Data mohou sloužit k trénování | Data jsou v rámci NotebookLM soukromá |