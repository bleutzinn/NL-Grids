# NL Grids
NL Grids genereert ruimtelijk complementaire hexagon grids gebaseerd op en geldig voor het Rijksdriehoekstelsel.

Doordat alle grids hun oorsprong delen met die van het Rijksdriehoekstelsel zijn lokale kleine grids later altijd samen te voegen en uit te breiden tot een groter en eventueel zelfs landsdekkend grid.

## Geometrie
- De oorsprong van het grid valt samen met de oorsprong van het Rijksdriehoekstelsel
- De grootte van cellen is op basis van cel oppervlakte
- Elke cel is een polygon met als vorm een hexagon

## Attribuut data
Elke cel heeft de volgende attributen:
- 'q_r': de relatieve positie van een cel in het grid ten opzichte van de oorsprong cel (155000 463000); ook te gebruiken als cel id
- 'dekopp_&lt;eenheid&gt;': de oppervlakte van de cel die overlapt met het gebied (dekking); de eenheid is onderdeel van de attribuut naam, bijvoorbeeld `dekopp_km2`

![NL Grid voor Nederland met cellen van 100 km2](https://github.com/bleutzinn/NL-Grids/blob/main/nlgrid_Nederland_100km2.png)

## Restricties
- De code van NL Grids gebruikt alleen het Rijksdriehoekstelsel
- Met NL Grids gemaakte grids zijn alleen geldig binnen het geldigheidsgebied van het Rijksdriehoekstelsel

## Python code
NL Grids is geschreven in Python en beschikbaar als Jupyter notebook.

## Licentie
Op NL Grids en de met NL Grids gemaakte grids is de MIT licentie van toepassing

## Parameters

NL Grids kent als parameters:
- eenheid: dit is de eenheid van de oppervlakte per grid cel (m2, ha of km2)
- oppervlakte: dit is de oppervlakte per grid cel in de opgegeven eenheid
- gebied: dit is voor welk gebied grid cellen worden gegenereerd
- trim: als 'ja' dan worden cellen die niet overlappen met het gebied uit het grid verwijderd
- export: 'gml' voor GML file, 'shp' voor Esri Shapefile

De invoer parameters maken deel uit van de code, zie na de paragraaf Uitvoer.

### Toelichting op de parameters

Richtlijn voor de gebruikelijke eenheid per oppervlakte bereik:
- tot 100 m<sup>2</sup> in vierkante meters (m2) ( [0 - 99] m2)
- van 100 m<sup>2</sup> tot 1000 m<sup>2</sup> in hectare (ha) ( [1 - 99] ha)
- vanaf 1000 m<sup>2</sup> in vierkante kilometers (km2) ( [1 - &infin;> km2)

Geldige waarden voor gebied zijn "Nederland" of "provincie &lt;naam&gt;" of "gemeente &lt;naam&gt;" waarbij &lt;naam&gt; een provincie- of gemeentenaam is. Het opgeven van meerdere provincies of gemeenten kan door die met komma's gescheiden op te geven.

Bijvoorbeeld:   
```gebied = 'provincie Zeeland, provincie Noord-Brabant, provincie Limburg'```

De opgegeven gebieden worden samengevoegd en gebruikt voor de dekking van 1 grid. Het combineren van gemeente en provincie namen mag ook.

Voor de gebieden worden de bestuurlijke grenzen uit de Basisregistratie Kadaster (BRK) gebruikt. Het genereren van NL Grids op basis van andere gebieden of grenzen vereist aanpassing van de code.

## Uitvoer
Een grid in de vorm van een vector dataset in het gespecificeerde formaat. De dataset wordt bewaard in de directory van het Jupyter notebook.

## Copyright en contact
Ron Wardenier, ron@rwgc.nl
