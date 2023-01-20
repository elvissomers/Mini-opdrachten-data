# Hints voor opdracht 3.3
1. Begin met `plt.boxplot()`.
2. Een boxplot accepteert geen `NaN` waarden, om uit je data te filteren kan je `.dropna()` gebruiken.
3. Vergeet niet de grafiek netjes te labelen met `plt.title()` en bijvoorbeeld `plt.xlabel()` of `plt.ylabel()`.

## Andere dingen die toegepast zijn in de voorbeeldgrafiek
4. De boxplot is horizontaal gemaakt met het keyword argument `vert=False`.
5. De prijzen zijn omgevormd naar miljoenen Euro door de data door 1.000.000 te delen (`df['prijs'].dropna() / 1_000_000`). (In Python kan je een `_` gebruiken als arbitrair scheidingsteken binnen getallen. Hierdoor kan je de getallen leesbaarder maken zonder iets te beïnvloeden.)
6. De grid kan je toevoegen met `plt.grid()`, dan is het wel handig om de keyword argument `zorder=3` toe te voegen aan `plt.boxplot()`.
7. Als laatste zijn de yticks verwijderd met de volgende code:
```py
plt.tick_params(
    axis='y',         # changes apply to the x-axis
    which='both',     # both major and minor ticks are affected
    left=False,       # ticks along the bottom edge are off
    right=False,      # ticks along the top edge are off
    labelleft=False)  # labels along the bottom edge are off
```
[Bron (StackOverflow)](https://stackoverflow.com/questions/12998430/remove-xticks-in-a-matplotlib-plot)