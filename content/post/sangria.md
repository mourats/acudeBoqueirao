---
title: "Quantas vezes o açude sangrou desde 1990?"
date: 2017-11-15T16:29:06-03:00
draft: false
---


<!--more-->
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
