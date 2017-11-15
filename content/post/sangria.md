---
title: "Quantas vezes o açude sangrou desde 1990?"
date: 2017-11-15T16:29:06-03:00
draft: false
---

<!--more-->


<html>
<head></head>
<body>
<h3>
Em 2017 nós passamos pela maior seca no açude boqueirão desde 1990. E por conta disso, é difícil lembrar da última vez em que o açude sangrou e virou ponto turístico onde as pessoas iam tirar fotos e registrar a fartura de água no açude.  

De 1990 até hoje, o açude de boqueirão já sangrou 14 vezes, sendo a ultima vez em agosto de 2011. Crianças de 6 anos de idade nunca viram o açude transbordar! Entre essas sangrias, a maior delas foi a de março de 2008, quando o açude atingiu incríveis 110% de sua capacidade. 

Todas essas informações podem ser vistas no gráfico abaixo:
</h3>

<div id="vis" width=300></div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/vega/3.0.7/vega.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/vega-lite/2.0.1/vega-lite.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/vega-embed/3.0.0-rc7/vega-embed.js"></script>
<script>
    const spec = {  
  "$schema":"https://vega.github.io/schema/vega-lite/v2.json",
    "data": {     
        "url":"https://api.insa.gov.br/reservatorios/12172/monitoramento",
        "format": {
            "type": "json",
            "property": "volumes",
            "parse":{
              "DataInformacao": "utc:'%d/%m/%Y'"
            }
        }
    },
    
    "transform":[{"filter": {"field": "VolumePercentual", "range":[101,200]
        }
       }],
     "mark": "point",
     "config": {
    "point": {
      "color": "purple",
      "shape": ""
    }},
        "encoding": {
        "y": {"timeUnit": "yearmonthdate", "field": "DataInformacao", "type": "ordinal", "axis": {"title": ""}},

		    "x":{"field": "VolumePercentual", "type": "quantitative", "axis": {"title": "% Percentual do volume de água"}, "scale": {
          "domain": [100,111]}
        }

        }
};
  	vegaEmbed('#vis', spec).catch(console.warn);
</script>
</body>
</html>