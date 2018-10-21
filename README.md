

### 1) Uttrekk fra Realfagstermer

```
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX dct: <http://purl.org/dc/terms/>
PREFIX real: <http://data.ub.uio.no/realfagstermer/>
PREFIX ubo: <http://data.ub.uio.no/onto#>

CONSTRUCT {
  ?c skos:prefLabel ?term ;
    skos:closeMatch ?concept .
}
FROM <http://data.ub.uio.no/realfagstermer>
WHERE
{
  ?concept a skos:Concept ;
           skos:prefLabel ?term ;
           ubo:MSC ?msc .

  FILTER(LANG(?term) = "nb")
  BIND(URI(CONCAT("http://data.ub.uio.no/msc-ubo/", REPLACE(?msc, " ", ""))) AS ?c)
}
ORDER BY ?msc
```


### 2) Manuell vask og hierarkisk ordning

### 3) Skosify-vask

```
skosify -c skosify.cfg < msc-ubo.ttl >| msc-ubo-fixed.ttl
```
