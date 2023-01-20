# Hints voor opdracht 3.2
1. Begin met `plt.hist()`.
2. Voeg bijvoorbeeld `plt.title()`, `plt.xlabel()` en `plt.ylabel()` toe.
3. Het is altijd beter om ook `plt.show()` toe te passen aan het eind.

## Andere dingen die zijn toegepast in de voorbeeldgrafiek:
4. De grid kan je toevoegen met `plt.grid()`, dan is het wel handig om de keyword argument `zorder=3` toe te voegen aan `plt.hist()`.
5. De prijzen in tonnen zijn toegepast door de de waarden te delen door 100.000 (`df['prijs'] / 100_000`). (In Python kan je een `_` gebruiken als arbitrair scheidingsteken binnen getallen. Hierdoor kan je de getallen leesbaarder maken zonder iets te beïnvloeden.)
6. Het histogram in het voorbeeld toont alleen de prijzen tot 2 miljoen, om de uitschieters tot 6 miljoen weg te laten. Als dit de enige histogram zou zijn in een rapportage is dit een slecht idee. Het geeft wel een beter idee van het meerendeel van de verdeling, dus kan goed gebruikt worden voor verduidelijking. (`df.loc[df['prijs'] < 2_000_000, 'prijs']`)