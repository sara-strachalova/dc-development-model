# Model vývoje dendritických buněk a klastrování průběhů

Tento projekt vznikl ke zkoumání algoritmů shlukové analýzy při použití na data získaná z modelu vývoje dendritických buněk. Jde o soubor časových průběhů jednotlivých simulací, přičemž různé simulace vykazují podobné chování, na základě čehož je lze řadit do tříd. Projekt též slouží k ukládání výsledků pro další analýzu. Nedatová část projektu je psána v jazyce `python` v prostředí `jupyter notebooků`.

## Navigace

Projekt sestává ze dvou hlavních adresářů, `Bakalarka` a `Klasterizace`. `Bakalarka` obsahuje práci, v níž je model definován. `Klasterizace` se dále dělí na `Datasety`, `NB` a `Vysledky`.

### Datasety

Obsahuje datasety využívané ke shlukové analýze. Extra sloupec u `labeled-dataset-clean.csv` a `smaller-labeled-dataset.csv` slouží jako reference k určení přesnosti algoritmu.

- `dataset-clean.csv` → dataset z původní práce s odstraněnými NaNy
- `labeled-dataset-clean.csv` → vychází z předchozího datasetu, k němuž je přidaný sloupec s informací o třídě, která byla průběhu přiřazena při dřívější "ruční" analýze 
- `smaller-labeled-dataset.csv` → vychází z předchozího datasetu, vznikl náhodným výběrem deseti záznamů z každé kategorie. Jde o testovací dataset umožňující zkoumání více variant algoritmu, metrik a dalších parametrů v rozumném čase.

### NB

Obsahuje `jupyter notebooky` pro shlukovou analýzu a její zkoumání.

- `timeseries-classification.ipynb` → původní "návodný" nb ke klasifikacím časových řad
- `timeseries-classification-edit.ipynb` → upravený nb sloužící k průzkumu dat a jejich modifikací a k průzkumu klastrů
- `timeseries-classification-mapping-i.ipynb` → nb k shlukové analýze, majoritní mapování (**TODO** viz níže)
- `timeseries-classification-mapping-ii.ipynb` → nb k shlukové analýze, mapování na základě absolutního množství (**TODO** viz níže)

### Vysledky

Rozdělené do `mapping-i` a `mapping-ii` podle typu mapování. V mapování dále rozdělené podle použité metriky. Samotné soubory s daty jsou typu `.csv`. Názvy souborů specifikují podmínky a parametry, které nejsou zahrnuté v samotných datech.

Vysvětlení:
- `dtw`, `euclid`, `soft-dtw-init5`, `soft-dtw-init5-max-iters` → "základní" běh s danou metrikou, `sz`=100, `random_state`=1234, `n_jobs`=-1, `n_init`=5. `soft-dtw-init5` a `soft-dtw-init5-max-iters` se liší v množství testovaných hodnot pro `max_iter`, což je vidět v datech v jednotlivých souborech. Další podmínky vychází z těchto, u dalších vysvětlení budou tedy uvedeny jen rozdíly oproti tomuto nastavení
- `bez-inits-jobs` → neuvedené `n_init` a `n_jobs`
- `bez-inits-s-jobs` → neuvedené `n_init`
- `seed-69` → `random_state`=69
- `sz-200` → `sz`=200
- `sz-200-s69` → `sz`=200, `random_state`=69
- `ten-inits` → `n_init`=10
- `twenty-inits` → `n_init`=20
- `twenty-inits-69` → `n_init`=20, `random_state`=69
