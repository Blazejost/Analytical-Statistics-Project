# Dokumentacja projektu – Analiza statystyczna kosztów leczenia

## Dane i źródło
- Zbiór danych: Medical Cost Personal Dataset (plik `insurance.csv`).
- Liczebność próby: 1338 obserwacji, 7 zmiennych.
- Zmienne:
  - `age` – wiek
  - `sex` – płeć
  - `bmi` – wskaźnik BMI
  - `children` – liczba dzieci
  - `smoker` – status palenia
  - `region` – region zamieszkania
  - `charges` – koszty leczenia (USD)

## Cel analizy
1. Opis rozkładu kosztów leczenia.
2. Porównanie kosztów między palaczami i niepalącymi.
3. Weryfikacja normalności BMI i porównanie kosztów wg płci metodą nieparametryczną.
4. Sprawdzenie wpływu regionu na koszty (ANOVA).
5. Budowa prostego modelu regresji liniowej dla `charges`.

## Metody i założenia
- Statystyki opisowe: średnia, mediana, odchylenie standardowe, skośność, kurtoza.
- Test t-Studenta dla dwóch prób niezależnych z weryfikacją równości wariancji (Levene).
- Test Shapiro–Wilka dla normalności BMI.
- Test Manna–Whitneya dla porównania kosztów wg płci.
- Jednoczynnikowa ANOVA dla zmiennej `region`.
- Regresja liniowa OLS: $\text{charges} = \beta_0 + \beta_1\,\text{age} + \beta_2\,\text{bmi} + \beta_3\,\text{children} + \epsilon$.

## Statystyki opisowe `charges`
- $n = 1338$
- Średnia: 13270.42
- Mediana: 9382.03
- Odchylenie standardowe: 12110.01
- Min/Max: 1121.87 / 63770.43
- Skośność: 1.516 (prawoskośny rozkład)
- Kurtoza: 1.606

Wnioski: rozkład kosztów jest silnie prawoskośny z długim ogonem wartości wysokich, co jest typowe dla kosztów medycznych.

## Tabela wyników (podsumowanie)

| Analiza | Statystyka | p-value | Wniosek |
|---|---:|---:|---|
| Test Levene’a (palacze vs niepalący) | — | < 0.0001 | Wariancje nierówne |
| Test t-Studenta (palacze vs niepalący) | $t = 32.75$ | $5.89\times10^{-103}$ | Różnica istotna |
| Shapiro–Wilk (`bmi`) | — | < 0.0001 | Brak normalności |
| Manna–Whitney (płeć vs koszty) | — | 0.7287 | Brak różnic |
| ANOVA (region) | $F = 2.97$ | 0.0309 | Różnice istotne |
| Regresja OLS | $R^2 = 0.12$ | — | Niskie dopasowanie |

**Wyjaśnienie:** tabela syntetyzuje kluczowe testy. Najsilniejszy efekt dotyczy palenia, natomiast różnice regionalne są niewielkie. Niska wartość $R^2$ w regresji wynika z pominięcia zmiennych kategorycznych (np. `smoker`).

## Test t-Studenta: palacze vs niepalący
Hipotezy:
- $H_0: \mu_{palacz} = \mu_{niepalacz}$
- $H_1: \mu_{palacz} \neq \mu_{niepalacz}$

Wyniki:
- Test Levene’a: $p < 0.0001$ (wariancje różne)
- Test t: $t = 32.75$, $p = 5.89\times 10^{-103}$

Wniosek: istotnie wyższe koszty leczenia u palaczy.

## Test normalności i Manna–Whitney
- Shapiro–Wilk dla `bmi`: $p < 0.0001$ → brak normalności.
- Manna–Whitney (płeć vs koszty): $p = 0.7287$.

Wniosek: brak istotnych różnic kosztów między kobietami i mężczyznami.

## ANOVA: wpływ regionu
Hipotezy:
- $H_0$: średnie koszty w regionach są takie same
- $H_1$: co najmniej jeden region różni się średnią

Wyniki:
- $F = 2.97$, $p = 0.0309$

Wniosek: region ma istotny, ale niewielki wpływ na koszty.

## Regresja liniowa OLS
Model: $\text{charges} = \beta_0 + \beta_1\,\text{age} + \beta_2\,\text{bmi} + \beta_3\,\text{children} + \epsilon$

Wyniki:
- $R^2 = 0.12$ (niska moc wyjaśniająca)
- Istotne predyktory: `age`, `bmi`, `children` (p < 0.05)

Wniosek: model liniowy wyjaśnia tylko część zmienności kosztów; brak zmiennych kluczowych (np. `smoker`) obniża dopasowanie.

## Interpretacja praktyczna
- Najsilniejszym czynnikiem różnicującym koszty jest status palenia.
- Rozkład kosztów jest nienormalny, dlatego testy nieparametryczne są uzasadnione.
- Prosty model liniowy nie wystarcza do dobrej predykcji kosztów; zalecane jest uwzględnienie zmiennych kategorycznych (`smoker`, `region`) i ewentualnie modelowania nieliniowego.

## Ograniczenia
- Analiza oparta na jednym zbiorze danych (USA), bez walidacji zewnętrznej.
- Brak kontroli współliniowości i testów diagnostycznych reszt w regresji.

## Reprodukowalność
- Notebook automatycznie wczytuje `insurance.csv`, a w razie braku pliku generuje dane syntetyczne o tej samej strukturze.

## Jak wygenerować PDF
Plik [REPORT.md](REPORT.md) można bezpośrednio przekonwertować do PDF (np. Pandoc lub wtyczki VS Code).

---
Autor: ..............................................

Data: 2026-01-17
