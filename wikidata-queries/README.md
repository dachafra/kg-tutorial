
# Query 1

```
SELECT ?pintura
{
  ?pintura wdt:P31 wd:Q3305213 .
} LIMIT 100
```

## Query 2

```
SELECT ?pintura ?pinturaLabel
WHERE
{
  ?pintura wdt:P31 wd:Q3305213 ;
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
} LIMIT 100
```

## Query 3

```
SELECT ?pintura ?pinturaLabel
WHERE
{
  ?pintura wdt:P31/wdt:P279* wd:Q3305213 ;
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
} LIMIT 100
```

## Query 4
```
SELECT ?pintura ?pinturaLabel ?exposicion ?exposicionLabel
WHERE
{
  ?pintura wdt:P31/wdt:P279* wd:Q3305213 ;
   		   wdt:P608 ?exposicion
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
} LIMIT 100
```

## Query 5

```
SELECT ?pintura ?pinturaLabel ?exposicionLabel ?fecha_inicio ?fecha_fin
WHERE
{
  ?pintura wdt:P31/wdt:P279* wd:Q3305213 ;
   wdt:P608 ?exposicion .
  ?exposicion wdt:P580 ?fecha_inicio;
                wdt:P582 ?fecha_fin 
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
} LIMIT 100
```

## Query 6 (does not work)
```
SELECT ?pintura ?pinturaLabel ?exposicionLabel ?fecha_inicio ?fecha_fin
WHERE
{
  ?pintura wdt:P31/wdt:P279* wd:Q3305213 ;
   wdt:P608 ?exposicion .
  ?exposicion wdt:P580 ?fecha_inicio;
                wdt:P582 ?fecha_fin .
  FILTER (?fecha_fin > 2021)
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
} LIMIT 100
```

## Query 7
```
SELECT ?pintura ?pinturaLabel ?exposicionLabel ?fecha_inicio ?fecha_fin
WHERE
{
  ?pintura wdt:P31/wdt:P279* wd:Q3305213 ;
   wdt:P608 ?exposicion .
  ?exposicion wdt:P580 ?fecha_inicio;
                wdt:P582 ?fecha_fin .
  FILTER (YEAR(?fecha_fin) > 2021)
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
} ORDER BY desc(?fecha_fin) LIMIT 100 
```

## Query 8
```
SELECT ?pintura ?pinturaLabel ?exposicionLabel ?fecha_inicio ?fecha_fin ?ancho ?alto
WHERE
{
  ?pintura wdt:P31/wdt:P279* wd:Q3305213 ;
   wdt:P608 ?exposicion .
  ?exposicion wdt:P580 ?fecha_inicio;
                wdt:P582 ?fecha_fin .
  
  ?pintura wdt:P2049 ?ancho;
           wdt:P2048 ?alto .
  FILTER (YEAR(?fecha_fin) > 2021)
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
} ORDER BY desc(?fecha_fin) LIMIT 100 
```