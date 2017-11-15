---
title: "Quanto o açude diminuiu em seu volume nos últimos cinco anos?"
date: 2017-11-15T16:29:14-03:00
draft: false
---

<!--more-->



Tempos de seca! Mas essa seca não pode ter ocorrido do dia pra noite certo? De fato não ocorreu, em janeiro de 2012 o açude estava com 90,8% de sua capacidade, ou seja, 373.600.000 metro cúbicos de água! 

Podemos perceber no gráfico abaixo que nossa água apenas foi se esvaindo durante esses cinco anos, tendo chegado ao percentual de 2,90% em abril desse ano, graças a Transposição do Rio São Francisco esses números estão subindo, e hoje estamos com 9,3% de água. 


<div id="vis" width=300></div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/vega/3.0.7/vega.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/vega-lite/2.0.1/vega-lite.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/vega-embed/3.0.0-rc7/vega-embed.js"></script>
<script>
    const spec = {
  "$schema": "https://vega.github.io/schema/vega-lite/v2.json",
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
  "vconcat": [{
    "width": 680,
        "transform":[{"filter": {"timeUnit": "year", "field": "DataInformacao", "range":[2012,2017]
        }
       }],
    "mark": "area",
    "encoding": {
      "x": {
        "field": "DataInformacao",
        "type": "temporal",
        "scale": {"domain": {"selection": "brush"}},
        "axis": {"title": ""}
      },
      "y": {"field": "Volume","type": "quantitative", "title": ""}
    }
  }, {
        "transform":[{"filter": {"timeUnit": "year", "field": "DataInformacao", "range":[2012,2017]
        }
       }],
    "width": 680,
    "height": 60,
    "mark": "area",
    "selection": {
      "brush": {"type": "interval", "encodings": ["x"]}
    },
    "encoding": {
      "x": {
        "field": "DataInformacao",
        "type": "temporal",
        "axis": {"format": "%Y", "title": "Anos (2012-2017)"}
      },
      "y": {
        "field": "VolumePercentual",
        "type": "quantitative",
        "axis": {"tickCount": 3, "grid": false, "title": ""}
      }
    }
  }]
};
  	vegaEmbed('#vis', spec).catch(console.warn);
</script>

