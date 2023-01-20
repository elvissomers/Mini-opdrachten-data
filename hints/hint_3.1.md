# Hints voor opdracht 3.1
1. Kopieer een van de prijzen (bijvoorbeeld `'€ 1.200.000 k.k.`) en pas bijvoorbeeld `.split()` en selectie (met `[index]`) toe om het getal te selecteren. Daarna kan je de `.replace()` methode gebruiken om de punten te verwijderen.
2. Schrijf een functie met één parameter die deze split en selectie uitvoert op de parameter en het resultaat teruggeeft.
3. Pas de functie toe op de `price` kolom met `df['price'].apply(naam_van_functie)`.
4. Probeer de kolom van type te veranderen met `.astype(int)`.
5. De error die je nu ziet (`ValueError: invalid literal for int() with base 10: 'op'`) wordt veroorzaakt door waarden in de originele kolom die geen prijs bevatten.
6. Om deze op te lossen kunnen we de unieke waarden in de kolom `price` bekijken met `.unique()`. Als je deze sorteert (of doorspit), zal je zien dat er twee waarden zijn die geen prijzen bevatten.
7. Voeg een `if` statement toe aan de functie die deze twee waarden onderschept en dan `None` teruggeeft.
8. Als je nu nogmaals `df['price'].apply(naam_van_functie).astype(int)` uit probeert te voeren (of `.astype(int)` op een variabele waar je de nieuwe kolom in hebt opgeslagen) dan zal je alsnog een error krijgen (`TypeError: int() argument must be a string, a bytes-like object or a real number, not 'NoneType'`).
9. Dit komt omdat er geen plek is voor `None`/`NaN` in een `int`. Dit is op te lossen door in plaats van gehele getallen `float` te gebruiken. Ook al zijn alle waarden in de kolom gehele getallen (naast de `None`/`NaN`), `float` is hier de beter keus omdat het ook `NaN`, `Inf` en `-Inf` kan opslaan. Dat er alleen gehele getallen in de kolom voorkomen is iets wat we zelf kunnen onthouden, of beter, ergens noteren.
    - Alternatief zou je de regels zonder prijs kunnen laten vallen met `.dropna()`. Echter is dit niet handig als je nog wel gebruik wil maken van de waarden in de andere kolommen. Bijvoorbeeld om te kijken hoeveel huizen er verkocht zijn in bepaalde steden.
10. Sla het resultaat op in een nieuwe kolom (`df['nieuwe_kolom_naam'] = ...`)

- Een alternatieve manier om deze opdracht op te lossen is met `regex` (regular expressions). Door bijvoorbeeld `df['price'].str.extract()` te gebruiken met het juiste patroon.
- Een ander alternatief zou kunnen zijn om de volgende keten te gebruiken: `df['price'].str.split(expand=True)[1].str.replace('.', '', regex=False).replace('op', None).replace('bij', None).astype(float)`. Echter is dit niet het meeste leesbare ooit om in één stap te doen.
- De twee alternatieven zijn echter wel sneller omdat ze gebruikt maken van de methoden van Pandas zelf, die in C geschreven zijn. (C is een snellere taal dan Python, als je interesse hebt in waarom, vraag het of zoek online naar het antwoord!)