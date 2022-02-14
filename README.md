New features will be added just to this API
> PROD: https://v2.custojusto.pt  
> QA: https://v2qa.custojusto.pt

### Table of contents

* TOC
{:toc}

### Get valid districts /locations
* * *
> This endpoint will return all valid regions  
> Requires valid token for authentication

<pre>
Method 
  GET
Headers
  Content-Type: application/json
  Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /locations
</pre>
  
```json
{
"locations":[
    {
        "locationName":"Aveiro",
        "locationId":6
    },
    {
        "locationName":"Açores",
        "locationId":19
    }
],
"type":"regions"
}
```


### Get valid areas /locations/{locationId}
* * *
> This endpoint will return all valid counties by area  
> Requires valid token for authentication
  
  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /locations/6
 </pre>
 
  ```json  
{
"locations":[
    {
        "locationName": "Albergaria-a-Velha",
        "locationId": 70
    },
    {
        "locationName": "Anadia",
        "locationId": 71
    }
],
"type":"counties"
}
  ```

### Get valid sub areas /locations/{locationId}/{county_locationId}
* * *
> This endpoint will return all valid parishes by area  
> Requires valid token for authentication

  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /locations/6/70
  </pre>
  
```json  
{
"locations":[
    {
        "locationName": "Albergaria-a-Velha e Valmaior",
        "locationId": 1
    },
    {
        "locationName": "Alquerubim",
        "locationId": 6
    }
],
"type":"parishes"
}
```


### Get location IDs tree based on CP6 /cp6/{cp6}
* * *
> This endpoint will return the needed IDs for region (district), county (area) and parish (sub area)  
> Requires valid token for authentication  
> In some cases, when CP6 was not found, IDs might return 0, which means that they should be lookup on /locations endpoint.  
> Let us know about these cases so we can improve our database
  
<pre>
Method 
  GET
Headers
  Content-Type: application/json
  Authorization: kiYiuYTiuTiUTYiytIut
Response signature for /cp6/4300-200
</pre>
  
```json  
{
    "districtID": 5,
    "areaID": 62,
    "subAreaID": 3
}
```

### Get possible adtypes /adtypes
* * *
> This endpoint will return the all types of ads available on our platform  
> Requires valid token for authentication

<pre>
Method 
  GET
Headers
  Content-Type: application/json
  Authorization: kiYiuYTiuTiUTYiytIut
Response signature for /adtypes
</pre>

```json  
[
    {
        "typeID": "t",
        "description": "Trespasse"
    },
    {
        "typeID": "s",
        "description": "Venda"
    },
    {
        "typeID": "u",
        "description": "Aluguer/Arrendamento"
    },
    {
        "typeID": "d",
        "description": "Doação"
    },
    {
        "typeID": "k",
        "description": "Compra"
    }
]
```


### Get possible adtypes /adtypes/bycategory/{categoryID}
* * *
> This endpoint will return the all ad types allowed for this token and for the specified category  
> Requires valid token for authentication  
  
<pre>
Method 
  GET
Headers
  Content-Type: application/json
  Authorization: kiYiuYTiuTiUTYiytIut
Response signature for /adtypes/bycategory/2021
</pre>
```json
[
  {
      "typeID": "s",
      "description": "Venda"
  }
]
```

### Get possible categories /categories
> This endpoint will return the all the existing categories on our platform  
> Only categories that contain hasChildren: False are allowed to be used when creating an ad  
> Requires valid token for authentication

<pre>
Method 
  GET
Headers
  Content-Type: application/json
  Authorization: kiYiuYTiuTiUTYiytIut
Response signature for /categories
</pre>

```json  
[
    {
        "categoryID": "7000",
        "name": "Emprego & Serviços",
        "keywords": "ofertas de emprego, procura de emprego, serviços",
        "hasChildren": true
    },
    {
        "categoryID": "1000",
        "name": "Imobiliário",
        "keywords": "apartamentos,quartos,moradias,prédios,lojas,escritórios,imobiliário,imóveis,vivendas,empreendimentos,",
        "hasChildren": true
    },
    {
        "categoryID": "2000",
        "name": "Veículos",
        "keywords": "carros usados,automóveis,motos,caravanas,comerciais,peugeot,vw,volkswagen,mercedes,renault,bmw,opel,audi,seat,citroen,toyota,nissan",
        "hasChildren": true
    }
]
```

### Get categories tree /categories/tree
> This endpoint will return the all full category tree for our platform  
> Deepest level is 3  
> Requires valid token for authentication  

<pre>
Method 
  GET
Headers
  Content-Type: application/json
  Authorization: kiYiuYTiuTiUTYiytIut
Response signature for /categories/tree
</pre>

```json  
[
  {
      "categoryID": "6000",
      "name": "Desporto & Lazer",
      "keywords": "arte, coleccões, desporto, bicicleta, música, filmes, livros, animais domésticos",
      "hasChildren": true,
      "subCategory": [
          {
              "subCategoryID": "6080",
              "name": "Música & Filmes",
              "keywords": "livros,filmes,dvd,cd,música",
              "hasChildren": false
          },
          {
              "subCategoryID": "6040",
              "name": "Artigos desporto",
              "keywords": "bicicleta,ski,snooker,surf,futebol,equipamento",
              "hasChildren": false
          }
      ]
  },
  {
      "categoryID": "7000",
      "name": "Emprego & Serviços",
      "keywords": "ofertas de emprego, procura de emprego, serviços",
      "hasChildren": true,
      "subCategory": [
          {
              "subCategoryID": "7020",
              "name": "Ofertas de Emprego",
              "keywords": "emprego,oferta emprego,estágio profissional,comissionista",
              "hasChildren": false
          },
          {
              "subCategoryID": "7060",
              "name": "Serviços",
              "keywords": "serviços,carpintaria,babysitter,canalizador,pintura,geriatria,carpintaria,mudanças,contabilidade,design,fotografiamotorista,explicações",
              "hasChildren": true,
              "subSubCategory": [
                  {
                      "subSubCategoryID": "7062",
                      "name": "Serviço Doméstico",
                      "keywords": "",
                      "hasChildren": false
                  },
                  {
                      "subSubCategoryID": "7063",
                      "name": "Formação",
                      "keywords": "",
                      "hasChildren": false
                  },
              ]
          }
      ]
  }
]
```

### Get categories by level 1 /categories/{categoryID}
* * *
> This endpoint will return the all categories by level 1  
> Requires valid token for authentication
  
<pre>
Method 
  GET
Headers
  Content-Type: application/json
  Authorization: kiYiuYTiuTiUTYiytIut
Response signature for /categories/2000
</pre>

```json  
[
    {
        "subCategoryID": "2020",
        "name": "Carros & Autocaravanas",
        "keywords": "carros usados,automóveis",
        "hasChildren": true
    },
    {
        "subCategoryID": "2060",
        "name": "Motos & Scooters",
        "keywords": "vender,comprar,pesquisar,usados,motas",
        "hasChildren": false
    },
    {
        "subCategoryID": "2120",
        "name": "Peças e acessórios de carros",
        "keywords": "capacete,jante,pneu,gps,motor,peças",
        "hasChildren": true
    },
    {
        "subCategoryID": "2140",
        "name": "Peças e acessórios de motas",
        "keywords": "capacete, pneu, blusões, escapes, faróis, paralamas, carenagem, luvas, botas,",
        "hasChildren": false
    }
]
```

### Get categories by level 2 /categories/{categoryID}/{subCategoryID}
* * *
> This endpoint will return the all categories by level 2  
> Requires valid token for authentication

<pre>
Method 
  GET
Headers
  Content-Type: application/json
  Authorization: kiYiuYTiuTiUTYiytIut
Response signature for /categories/2000/2020
</pre>

```json  
[
    {
        "subSubCategoryID": "2021",
        "name": "Ligeiros Passageiros",
        "keywords": "ligeiros passageiros, carros usados, automóveis usados, motas, renault, mercedes, bmw, fiat",
        "hasChildren": false
    },
    {
        "subSubCategoryID": "2023",
        "name": "Monovolume / SUV",
        "keywords": "monovolumes, suvs, carros usados, automóveis usados, coupé, descapotável, cabriolé, motas, renault, mercedes, bmw, fiat",
        "hasChildren": false
    },
    {
        "subSubCategoryID": "2024",
        "name": "Pick-up/ Todo-o-Terreno",
        "keywords": "pick-up, todo-o-terreno, jipe, jeeps, carros usados, automóveis usados, cherokee, land rover, renault, mercedes, bmw, fiat,",
        "hasChildren": false
    }
]
```

### Get allowed/custom fields by category /categories/fields/{categoryID}
* * * 
> This endpoint will return the default allowed fields by category, these may vary for each different ad type  
> Requires valid token for authentication

<pre>
Method 
  GET
Headers
  Content-Type: application/json
  Authorization: kiYiuYTiuTiUTYiytIut
Response signature for /categories/fields/1020
</pre>

```json  
[
  {
    "label": "Tipologia",
    "json": "typology",
    "type": "int",
    "values": "/roomtypologies",
    "accelerator": "/roomtypologies/{value}",
    "required": true
  },
  {
    "label": "Área útil",
    "json": "size",
    "type": "int",
    "required": true
  },
  {
    "label": "Certificado Energético",
    "json": "energyRating",
    "type": "int",
    "values": "/energyratings",
    "required": true
  },
  {
    "label": "Ano de Construção",
    "json": "constructionYear",
    "type": "date",
    "format": "YYYY",
    "required": false
  },
  {
    "label": "Licença de Utilização",
    "json": "usageLicense",
    "type": "string",
    "required": false
  },
  {
    "label": "Link do vídeo",
    "json": "videoURL",
    "type": "string",
    "required": false
  },
  {
    "label": "Link da visita virtual",
    "json": "virtualTourURL",
    "type": "string",
    "required": false
  }
]
```

### Get allowed/custom fields by category and ad type /categories/fields/{categoryID}/{adType}
* * * 
> This endpoint will return the allowed fields for a specific category and ad type (u,s,d,k,t)  
> Requires valid token for authentication

<pre>
Method 
  GET
Headers
  Content-Type: application/json
  Authorization: kiYiuYTiuTiUTYiytIut
Response signature for /categories/fields/1020/s
</pre>

```json  
[
  {
    "label": "Tipologia",
    "json": "typology",
    "type": "int",
    "values": "/roomtypologies",
    "accelerator": "/roomtypologies/{value}",
    "required": true
  },
  {
    "label": "Área útil",
    "json": "size",
    "type": "int",
    "required": true
  },
  {
    "label": "Certificado Energético",
    "json": "energyRating",
    "type": "int",
    "values": "/energyratings",
    "required": true
  },
  {
    "label": "Ano de Construção",
    "json": "constructionYear",
    "type": "date",
    "format": "YYYY",
    "required": false
  },
  {
    "label": "Link do vídeo",
    "json": "videoURL",
    "type": "string",
    "required": false
  },
  {
    "label": "Link da visita virtual",
    "json": "virtualTourURL",
    "type": "string",
    "required": false
  }
]
```

### Get allowed tags by category /tags/{categoryID}
* * * 
> This endpoint will return the allowed tags by category  
> Requires valid token for authentication

<pre>
Method 
  GET
Headers
  Content-Type: application/json
  Authorization: kiYiuYTiuTiUTYiytIut
Response signature for /tags/1100
</pre>

```json  
{
	"type": "checkbox",
	"tags": [
		{
			"id": "piscina",
			"name": "Piscina"
		},
		{
			"id": "cozinha",
			"name": "Cozinha"
		},
		{
			"id": "animais",
			"name": "Permitido animais"
		},
		{
			"id": "wifi",
			"name": "Wifi"
		},
		{
			"id": "ac",
			"name": "Ar condicionado"
		}
	]
}
```

### Get the existing car phone brands /phonebrands
* * * 
> This endpoint will return the existing phone brands on our platform  
> Requires valid token for authentication  

  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /phonebrands
  </pre>
  ```json  
[
    {
        "id": 1,
        "name": "AEG"
    },
    {
        "id": 2,
        "name": "Alcatel"
    },
    {
        "id": 3,
        "name": "Apple"
    },
    {
        "id": 4,
        "name": "HTC"
    },
    {
        "id": 5,
        "name": "Huawei"
    },
    {
        "id": 6,
        "name": "LG"
    }
]
```

### Find phone brand by similar name /phonebrands/byname/{lowercaseName}
* * *
> This endpoint searches for phone brand by name, such as Apple.  
> Requires valid token for authentication  
  
  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /phonebrand/byname/aple
  </pre>
```json 
    {
        "id": 3,
        "name": "Apple"
    }
```

### Get the existing car brands /carbrands
* * * 
> This endpoint will return the existing car brands on our platform  
> Requires valid token for authentication  

  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /carbrands
  </pre>
  ```json  
    [
        {
            "id": 1,
            "name": "Alfa Romeo"
        },
        {
            "id": 2,
            "name": "Aston Martin"
        },
        {
            "id": 3,
            "name": "Audi"
        },
        {
            "id": 6,
            "name": "BMW"
        }
    ]
```

### Get the existing car models per brand /carbrands/{brandID}
* * * 
> This endpoint will return the existing car models on our platform, per brand  
> Requires valid token for authentication  

  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /carbrands/6
  </pre>

  ```json
    {
        "id": 6,
        "name": "BMW",
        "models": [
            {
                "id": 99,
                "name": "114"
            },
            {
                "id": 28,
                "name": "116"
            },
            {
                "id": 29,
                "name": "118"
            }
    }
```

### Get the existing car models per brand /carbrands/{brandID}/series
* * *
> This endpoint will return the existing car models on our platform, per brand, grouped by serie. Usefull for BMW and Mercedes  
> Requires valid token for authentication  
  
  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /carbrands/6/series
  </pre>
  ```json  
    {
        "series": [
            {
                "name": "Série 2",
                "models": [
                    {
                        "id": 107,
                        "name": "216 Active Tourer"
                    },
                    {
                        "id": 108,
                        "name": "216 Gran Tourer"
                    },
                    {
                        "id": 109,
                        "name": "218"
                    },
                    {
                        "id": 110,
                        "name": "218 Active Tourer"
                    }
                ]
            }
        ],
        "models": null
    }
```


### Find car brand by similar name /carbrands/byname/{lowercaseName}
* * *
> This endpoint searches for car brand by name, such as toyota.  
> Requires valid token for authentication  
  
  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /carbrands/byname/tayotaa
  </pre>
```json 
    {
        "id": 48,
        "name": "Toyota"
    }
```


### Find car model by similar name /carbrands/{brandID}/byname/{lowercaseName}
* * *
> This endpoint searches for car model by name, such as corola  
> Requires valid token for authentication  

  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /carbrands/48/byname/corola
  </pre>
```json
    {
        "id": 10,
        "name": "Corolla"
    }
```

### Get the existing moto brands /motobrands
* * *
> This endpoint will return the existing moto brands on our platform  
> Requires valid token for authentication  

  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /motobrands
  </pre>
```json
  [
      {
    "id": 4,
    "name": "AJP"
      },
      {
    "id": 1,
    "name": "Adly"
      },
      {
    "id": 2,
    "name": "Aeon"
      },
      {
    "id": 3,
    "name": "Aixam"
      },
      {
    "id": 5,
    "name": "Aprilia"
      },
      {
    "id": 9,
    "name": "BMW"
      }
    ]
 ```

### Get the existing moto models per brand /motobrands/{brandID}
* * *
> This endpoint will return the existing moto models on our platform, per brand  
> Requires valid token for authentication  
  
  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /motobrands/9
  </pre>
```json  
  {
      "id": 9,
      "name": "BMW",
      "models": [
    {
        "id": 1,
        "name": "C1"
    },
    {
        "id": 2,
        "name": "F"
    },
    {
        "id": 3,
        "name": "GS"
    },
    {
        "id": 4,
        "name": "HP2"
    }
      ]
  }
```

### Find moto brand by similar name /motobrands/byname/{lowercaseName}
* * *
> This endpoint searches for moto brand by name, such as cavasaqui.  
> Requires valid token for authentication  

  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /motobrands/byname/cavasaqui
  </pre>
```json
  {
      "id": 28,
      "name": "Kawasaki"
  }
```


### Find car model by similar name /motobrands/{brandID}/byname/{lowercaseName}
* * *
> This endpoint searches for moto model by name, such as eliminador  
> Requires valid token for authentication  

  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /motobrands/28/byname/eliminador
  </pre>
```json
  {
      "id": 19,
      "name": "Eliminator"
  }
```

### Get Cubic Centemeters configurations /cc
* * *
> This endpoint returns the CC intervals used on our platform  
> Requires valid token for authentication  

  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /cc
  </pre>
```json
    [
        {
            "min": 0,
            "max": 50,
            "id": "1",
            "name": "Até 50cc"
        },
        {
            "min": 50,
            "max": 125,
            "id": "2",
            "name": "51 - 125 cc"
        },
        {
            "min": 126,
            "max": 500,
            "id": "3",
            "name": "126 - 500 cc"
        },
        {
            "min": 501,
            "max": 1000,
            "id": "4",
            "name": "501 - 1000 cc"
        },
        {
            "min": 1001,
            "max": 9999,
            "id": "5",
            "name": "Mais de 1000 cc"
        }
    ]
```

### Get Cubic Centimeters configuration based on CC value /cc/{CubicCentimetersValue}
* * *
> This endpoint returns the CC data used on our platform  
> Requires valid token for authentication  
  
<pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /cc/350
</pre>
```json
    {
        "min": 126,
        "max": 500,
        "id": "3",
        "name": "126 - 500 cc"
    }
```


### Get our color list /colors
* * *
> This endpoint returns the available colors on our platform  
> Requires valid token for authentication  
  
  
  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /colors
  </pre>
```json  
    [
        {
            "id": 6,
            "name": "Amarelo",
            "hexColor": "#f1c40f"
        },
        {
            "id": 8,
            "name": "Azul",
            "hexColor": "#3498db"
        },
        {
            "id": 1,
            "name": "Branco",
            "hexColor": "#fff"
        }
    ]
```
### Get our fuel type list /fuels
* * *
> This endpoint returns the available fuel types on our platform  
> Requires valid token for authentication  
  
  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /fuels
  </pre>
```json
    [
        {
            "id": 2,
            "name": "Diesel"
        },
        {
            "id": 4,
            "name": "ECO/Híbrido"
        },
        {
            "id": 5,
            "name": "Eléctrico"
        },
        {
            "id": 3,
            "name": "GPL"
        },
        {
            "id": 1,
            "name": "Gasolina"
        }
    ]
  ```
### Get our animal/dogs breed list /animals/canine-breeds
* * *
> This endpoint returns the available dog breeds on our platform  
> Requires valid token for authentication  
  
  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /animals/canine-breeds
  </pre>
```json
[
  {
    "id": 1,
    "name": "Beagle"
  },
  {
    "id": 2,
    "name": "Boxer"
  },
  {
    "id": 3,
    "name": "Braco Alemão"
  },
  {
    "id": 4,
    "name": "Bull Terrier"
  },
  {
    "id": 5,
    "name": "Bulldog"
  },
  {
    "id": 6,
    "name": "Caniche"
  },
  {
    "id": 9,
    "name": "Castro Laboreiro"
  },
  {
    "id": 10,
    "name": "Chihuahua"
  },
  {
    "id": 11,
    "name": "Cocker Spaniel"
  },
  {
    "id": 8,
    "name": "Cão De Gado Transmontano"
  },
  {
    "id": 7,
    "name": "Cão De Ýgua"
  },
  {
    "id": 12,
    "name": "Dogue"
  },
  {
    "id": 13,
    "name": "Epagneul"
  },
  {
    "id": 14,
    "name": "Golden Retriever"
  },
  {
    "id": 27,
    "name": "Indeterminada"
  },
  {
    "id": 15,
    "name": "Labrador"
  },
  {
    "id": 28,
    "name": "Outras Raças"
  },
  {
    "id": 16,
    "name": "Pastor Alemão"
  },
  {
    "id": 17,
    "name": "Perdigueiro"
  },
  {
    "id": 18,
    "name": "Pinscher"
  },
  {
    "id": 19,
    "name": "Podengo"
  },
  {
    "id": 20,
    "name": "Rafeiro do Alentejo"
  },
  {
    "id": 22,
    "name": "Serra Da Estrela"
  },
  {
    "id": 23,
    "name": "Shar Pei"
  },
  {
    "id": 24,
    "name": "Shih-Tzu"
  },
  {
    "id": 25,
    "name": "Spitz"
  },
  {
    "id": 21,
    "name": "São Bernardo"
  },
  {
    "id": 26,
    "name": "Yorkshire Terrier"
  }
]
```

### Get our animal/dogs gender list /animals/genders
* * *
> This endpoint returns the available dog/animal genders on our platform  
> Requires valid token for authentication  
  
  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /animals/genders
  </pre>
```json
[
  {
    "id": 1,
    "name": "Macho"
  },
  {
    "id": 2,
    "name": "Fêmea"
  }
]
```

### Get our animal/dogs size list /animals/sizes
* * *
> This endpoint returns the available dog/animal sizes on our platform  
> Requires valid token for authentication  
  
  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /animals/sizes
  </pre>
```json
[
  {
    "id": 2,
    "name": "Pequeno"
  },
  {
    "id": 3,
    "name": "Médio"
  },
  {
    "id": 4,
    "name": "Grande"
  },
  {
    "id": 5,
    "name": "Muito grande"
  },
  {
    "id": 1,
    "name": "Muito pequeno"
  }
]
```

### Get our animal/dogs ageing intervals /animals/ageing
* * *
> This endpoint returns the available dog ageing intervals on our platform  
> Requires valid token for authentication  
  
  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /animals/ageing
  </pre>
```json
[
    {
        "id": 1,
        "name": "0-2 meses"
    },
    {
        "id": 2,
        "name": "2-12 meses"
    },
    {
        "id": 3,
        "name": "1-3 anos"
    },
    {
        "id": 4,
        "name": "3-6 anos"
    },
    {
        "id": 5,
        "name": "6 anos"
    }
]
```

### Get our gear boxes list /gearboxes
* * *
> This endpoint returns the available gearboxes types on our platform  
> Requires valid token for authentication  

  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /gearboxes
  </pre>
```json  
    [
        {
            "id": 2,
            "name": "Automática"
        },
        {
            "id": 1,
            "name": "Manual"
        },
        {
            "id": 4,
            "name": "Mista"
        },
        {
            "id": 3,
            "name": "Sequencial"
        }
    ]
  ```

### Get our mileage intervals /mileages
* * *
> This endpoint returns the available mileage intervals on our platform  
> Requires valid token for authentication  
  
  
  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /mileages
  </pre>
```json
    [
        {
            "min": 0,
            "max": 4999,
            "name": "Menos de 4999",
            "id": 1
        },
        {
            "min": 5000,
            "max": 9999,
            "name": "5000 - 9999",
            "id": 2
        },
        {
            "min": 10000,
            "max": 19999,
            "name": "10000 - 19999",
            "id": 3
        }
    ]
  ```

### Get mileage id by mileage value /mileages/{mileageValue}
* * *
> This endpoint returns the mileage id based on actual mileages (km)  
> Requires valid token for authentication  
  
  
  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /mileages/14000
  </pre>
```json
    {
        "min": 10000,
        "max": 19999,
        "name": "10000 - 19999",
        "id": 3
    }
```

### Get energy rating list /energyratings
* * *
> This endpoint returns our energy rating list  
> Requires valid token for authentication  
  
  
  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /energyratings
  </pre>
```json
    [
        {
            "id": 0,
            "name": "A+"
        },
        {
            "id": 1,
            "name": "A"
        },
        {
            "id": 2,
            "name": "B"
        },
        {
            "id": 3,
            "name": "B-"
        },
        {
            "id": 4,
            "name": "C"
        }
        {
            "id": 9,
            "name": "Isento"
        }
    ]
  ```



### Get room typologies list /roomtypologies
* * *
> This endpoint returns our room typologies list  
> Requires valid token for authentication  
  
<pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /roomtypologies
</pre>
```json  
    [
        {
            "id": 3,
            "name": "T0"
        },
        {
            "id": 4,
            "name": "T1"
        },
        {
            "id": 5,
            "name": "T2"
        }
        {
            "id": 9,
            "name": "T6 ou maior"
        }
    ]
  ```


### Get room typology /roomtypologies/{typologyName}
* * *
> This endpoint returns our room typology based on keyword, uppercase  
> Requires valid token for authentication  
  
  
  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /roomtypologies/T4
  </pre>
```json  
    {
        "id": 7,
        "name": "T4"
    }
```

### Get accommodation types list accommodationtypes
* * *
> This endpoint returns our accommodation types list  
> Requires valid token for authentication  
  
<pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /accommodationtypes
</pre>
```json  
    [
      {
        "id": 1,
        "name": "Apartamento"
      },
      {
        "id": 2,
        "name": "Casa"
      },
      {
        "id": 3,
        "name": "Quarto de hóspedes"
      }
    ]
```

### Get vacation types list vacationtypes
* * *
> This endpoint returns our vacation types list  
> Requires valid token for authentication  
  
<pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /vacationtypes
</pre>
```json  
    [
      {
        "id": 1,
        "name": "Praia"
      },
      {
        "id": 2,
        "name": "Rural"
      },
      {
        "id": 3,
        "name": "Cidade"
      }
    ]
```
### Get partner allowed categories /partner/categories
* * *
> This endpoint returns the category tree allowed for the provided partner token  
> Requires valid token for authentication  
> hasChildren = false will indicate which categories allow ad insertion
  
  
  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /partner/categories
  </pre>
```json  
    [
        {
            "categoryID": "2000",
            "name": "Veículos",
            "keywords": "carros usados,automóveis,motos,caravanas,comerciais,peugeot,vw,volkswagen,mercedes,renault,bmw,opel,audi,seat,citroen,toyota,nissan",
            "hasChildren": true,
            "subCategory": [
                {
                    "subCategoryID": "2080",
                    "name": "Barcos",
                    "keywords": "veleiro,barco,mota de água,jet ski",
                    "hasChildren": false
                },
                {
                    "subCategoryID": "2020",
                    "name": "Carros & Autocaravanas",
                    "keywords": "carros usados,automóveis",
                    "hasChildren": true,
                    "subSubCategory": [
                        {
                            "subSubCategoryID": "2025",
                            "name": "Comerciais / Van",
                            "keywords": "comerciais, carrinhas van, carros usados, automóveis usados, iveco, nissan, renault, mercedes, bmw, fiat",
                            "hasChildren": false
                        },
                        {
                            "subSubCategoryID": "2021",
                            "name": "Ligeiros Passageiros",
                            "keywords": "ligeiros passageiros, carros usados, automóveis usados, motas, renault, mercedes, bmw, fiat",
                            "hasChildren": false
                        },
                    ]
                },
                {
                    "subCategoryID": "2060",
                    "name": "Motos & Scooters",
                    "keywords": "vender,comprar,pesquisar,usados,motas",
                    "hasChildren": false
                }
            ]
        }
    ]
  ```


### Get partner data /partner
* * *
> This endpoint returns partner data  Partners who have shops, will get extra object, "shop"  
> Requires valid token for authentication  
  
  
  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /partner
  </pre>
```json  
    {
        "userID": "4234123414",
        "name": "Partner Name",
        "notifications": ["wnl", "activads", "promo"],
        "email": "partner_email@partner.com",
        "phone": "911234567",
        "address": "Partner main address",
        "location": {
            "district": 5,
            "area": 66,
            "subArea": 4,
            "cp6": "4445-371"
        },
        "vatNumber": "987456321",
        "token": "Future new api integrations token",
        "profileImage": "https://www.custojusto.pt/profiles/25/2555207721.jpg",
        "partnerId": "Partner-Name-987456321",
        "firstApprovedAd": "2019-07-11 10:21:55.933294+01",
        "allowedCategories": [
          "2000"
          ],
        "chatEnabled": true,
        "hasShop": true,
        "shop": {
            "name": "Partner Name shop",
            "description": "By amazing shop",
            "address": "Partner shop address",
            "website": "https://www.partner.com",
            "shopUrl": "https://www.custojusto.pt/loja/partner-name",
            "phones": [
                {
                    "name": "Geral",
                    "phone": "911234567",
                    "order": 1
                }
            ],
            "businessHours": [
                {
                    "day": 1,
                    "openingHours": "08:15",
                    "closingHours": "12:00"
                },
                {
                    "day": 2,
                    "openingHours": "08:30",
                    "closingHours": "12:15"
                },
                {
                    "day": 3,
                    "openingHours": "08:45",
                    "closingHours": "12:30"
                },
                {
                    "day": 4,
                    "openingHours": "09:00",
                    "closingHours": "12:45"
                },
                {
                    "day": 5,
                    "openingHours": "",
                    "closingHours": ""
                },
                {
                    "day": 6,
                    "openingHours": "",
                    "closingHours": ""
                },
                {
                    "day": 7,
                    "openingHours": "",
                    "closingHours": ""
                }
            ],
            "shopImage": "https://www.custojusto.pt/profiles/28/2863731040.jpg"
        },
        "stats": {
            "total": {
                "pageViews": 294,
                "adReplies": 11,
                "phoneViews": 2,
                "favourites": 10
            },
            "previousMonth": {
                "pageViews": 69,
                "adReplies": 4,
                "phoneViews": 0,
                "favourites": 5
            },
            "currentMonth": {
                "pageViews": 45,
                "adReplies": 2,
                "phoneViews": 0,
                "favourites": 5
            },
            "previousWeek": {
                "pageViews": 10,
                "adReplies": 0,
                "phoneViews": 0,
                "favourites": 4
            },
            "currentWeek": {
                "pageViews": 33,
                "adReplies": 2,
                "phoneViews": 0,
                "favourites": 1
            },
            "last90Days": {
                "pageViews": 33,
                "adReplies": 2,
                "phoneViews": 0,
                "favourites": 1
            },
            "last30Days": {
                "pageViews": 33,
                "adReplies": 2,
                "phoneViews": 0,
                "favourites": 1
            }
        },
        "subscriptionStatus":{
            "partnerParentID":"auto",
            "partnerParentName":"Vehicles",
            "crmEnabled":false,
            "package":"Prestige",
            "expireAt":"2021-06-03T23:59:59Z",
            "numberImageUploads":36,
            "adsActive":7,
            "adsTotal":11,
            "adsLeft":4,
            "adsActionsLeft":999,
            "availableCredits":52
        },
        "adsStatus":{
            "disabled":4,
            "active":7,
            "refused":0,
            "inactive":0
        }
    }
```


### Update partner profile /partner/profile
* * *
> This endpoint update profile details, such as location, main phone and address  Editing the phone number won't update ads  
> Requires valid token for authentication  
  
  
  <pre>
  Method 
    PUT
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /partner/profile
  </pre>
```json  
    {
      "address":"Estrada Granja do Marques",
      "phone":"911234567",
      "location":{
          "district":5,
          "area":66,
          "subArea":4,
          "cp6":"4445-371"
      },
      "notifications":["wnl", "activads", "promo"]
    }
```

### Valid notifications
* * *
> wnl - Newsletter semanal com as estatísticas dos seus anúncios activos  
> activads - Anúncios activos há 10 e 30 dias  
> promo - Sugestões e promoções para vender mais rápido no CustoJusto  
> saveds - Pesquisas favoritas, sempre que houver novidades nas suas pesquisas favoritas  
> partnerpromo - Promoções de parceiros  


### Fail errors will return the field and error description
* * *
  <pre>
  StatusCode 
    400 - Bad Request
  Response example when providing an unexisting district (consequently no match for area and subarea), a bad format CP6 and bad format phone number
  </pre>
```json
    {
        "results": [
            {
                "field": "subarea",
                "value": "Seleccionar uma zona no município"
            },
            {
                "field": "phone",
                "value": "Verificar o número de telefone"
            },
            {
                "field": "district",
                "value": "Seleccione um distrito"
            },
            {
                "field": "area",
                "value": "Seleccione um concelho"
            },
            {
                "field": "cp6",
                "value": "Código postal errado"
            }
        ]
    }
```


### Change partner password /partner/profile/changepassword
* * *
> This endpoint will reset partner password  
> Requires valid token for authentication  
  
  
  <pre>
  Method 
    POST
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Payload signature for /partner/profile/changepassword
  </pre>
```json  
    {
      "password":"Pass1234"
    }
```

### Update partner shop details /partner/shop
* * *
> This endpoint update shop details for parthers with enabled shop  Limit for phone numbers is 5  
> Requires valid token for authentication  

  <pre>
  Method 
    PUT
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /partner/shop
  </pre>
```json
    {
      "name":"O nome da minha loja",
      "description":"Vendemos todo o tipo de veículos",
      "address":"Morada da shop",
      "website":"https://www.partner.pt",
      "phones":[
          {
            "name":"Geral",
            "phone":"911234567",
            "order":1
          }
      ],
      "businessHours":[
          {
            "day":1,
            "openingHours":"08:15",
            "closingHours":"12:00"
          },
          {
            "day":2,
            "openingHours":"08:30",
            "closingHours":"12:15"
          },
          {
            "day":3,
            "openingHours":"08:45",
            "closingHours":"12:30"
          },
          {
            "day":4,
            "openingHours":"09:00",
            "closingHours":"12:45"
          },
          {
            "day":5,
            "openingHours":"",
            "closingHours":""
          },
          {
            "day":6,
            "openingHours":"",
            "closingHours":""
          },
          {
            "day":7,
            "openingHours":"",
            "closingHours":""
          }
      ]
    }
```

### Fail errors will return the field and error description
* * *
  <pre>
  StatusCode
    417 - Expectation Failed
    <small>When provided data has a wrong format. Such as providing strings when int is expected or the opposite</small>
  StatusCode 
    400 - Bad Request
  Response example when providing wrong phone format and several wrong schedule hours. Having shop_hours_1 meaning, opening/closing time has a wrong time value for Monday.
  </pre>
```json
    {
        "results": [
            {
                "field": "shop_hours_1",
                "value": "Número de horas inválido"
            },
            {
                "field": "shop_hours_2",
                "value": "Número de horas inválido"
            },
            {
                "field": "shop_hours_3",
                "value": "Número de horas inválido"
            },
            {
                "field": "shop_hours_4",
                "value": "Número de horas inválido"
            },
            {
                "field": "shop_phone_1",
                "value": "Verificar o número de telefone"
            }
        ]
    }
```


### Update shop banner /images/users/shop
* * *
> This endpoint allows a banner update. Will remove the existing image.  Only jpg files are allowed  
> Requires valid token for authentication  
  
  
  <pre>
  Method 
    POST
  Headers
    Authorization: kiYiuYTiuTiUTYiytIut
    Content-Type: multipart/form-data
    Form field: file
    <small>curl --location --request POST '{API_URL}/images/users/shop' --header 'Authorization: kiYiuYTiuTiUTYiytIut' --header 'Content-Type: multipart/form-data' --form 'file=@/image_location/filename.jpg'</small>
  Response signature for /images/users/shop
  </pre>
```json  
    {
        "image": {
            "image_url": "/profiles/32/3280777678.jpg",
            "server_url": "https://www.custojusto.pt"
        }
    }
```

### Delete shop banner /images/users/shop
* * *
> This endpoint allows removal of the banner image completely  
> Requires valid token for authentication  
  
  
  <pre>
  Method 
    DELETE
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  </pre>


### Update user profile image /images/users/profile
* * *
> This endpoint allows profile logo update. Will remove the existing image.  Only jpg files are allowed  
> Requires valid token for authentication  
  
  
  <pre>
  Method 
    POST
  Headers
    Authorization: kiYiuYTiuTiUTYiytIut
    Content-Type: multipart/form-data
    Form field: file
    <small>curl --location --request POST '{API_URL}/images/users/profile' --header 'Authorization: kiYiuYTiuTiUTYiytIut' --header 'Content-Type: multipart/form-data' --form 'file=@/image_location/filename.jpg'</small>
  Response signature for /images/users/shop
  </pre>
```json
    {
        "image": {
            "image_url": "/profiles/31/311123321.jpg",
            "server_url": "https://www.custojusto.pt"
        }
    }
```

### Delete profile image /images/users/profile
* * *
> This endpoint allows removal of the profile image completely  
> Requires valid token for authentication  
  
  <pre>
  Method 
    DELETE
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  </pre>


### Get partner ads /partner/entries
* * *
> This endpoint returns all partner ads, with a few information  All 4 Status apply: active (published), inactive (under approval), disabled (marked as deleted for less than 60 days), refused (when ad has been refused, refusalReason field will contain more details)  
> Requires valid token for authentication  
  
  **it's possible to filter data based on url route**
  * /partner/entries/active will return just active ads  
  * /partner/entries/refused will return just refused ads  
  * /partner/entries/disabled will return just ads marked as disabled. Auto removal after 60 days of the deactivation  
  * /partner/entries/inactive will return just inactive ads  
  **pagination is also possible**   Params: p=0 (page number, index 0 based) c=40 (count per page)    
  **sorting is also possible**   Param: "s" possible values are: price_desc | price_asc | pub_date_desc | pub_date_asc    
  **stats per ad also possible**  Param: stats=enabled adds a new object to each ad


```json
  "adStats": {
      "total": {
          "pageViews": 294,
          "adReplies": 11,
          "phoneViews": 2,
          "favourites": 10
      },
      "previousMonth": {
          "pageViews": 69,
          "adReplies": 4,
          "phoneViews": 0,
          "favourites": 5
      },
      "currentMonth": {
          "pageViews": 45,
          "adReplies": 2,
          "phoneViews": 0,
          "favourites": 5
      },
      "previousWeek": {
          "pageViews": 10,
          "adReplies": 0,
          "phoneViews": 0,
          "favourites": 4
      },
      "currentWeek": {
          "pageViews": 33,
          "adReplies": 2,
          "phoneViews": 0,
          "favourites": 1
      },
      "last90Days": {
          "pageViews": 33,
          "adReplies": 2,
          "phoneViews": 0,
          "favourites": 1
      },
      "last30Days": {
          "pageViews": 33,
          "adReplies": 2,
          "phoneViews": 0,
          "favourites": 1
      },
      "yesterday": {
          "pageViews": 10,
          "adReplies": 1,
          "phoneViews": 0,
          "favourites": 0
      }
  }
```
    
  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /partner/entries
  </pre>
```json
    {
        "ads": [
            {
                "adID": 12505727,
                "subject": "BMW 216 Active Tourer XPTO",
                "status": "active",
                "price": 1967,
                "url": "https://www.custojusto.pt/11812874",
                "deleteID": "11812874",
                "listID": "11812874",
                "externalAdID": "4562846523542",
                "imageURL": "https://cdn.custojusto.pt/api/v1/images/images/2140593119-mercedes-benz-cl-500-347.jpg?rule=gallery",
                "notice": "Ad imported using partners API",
                "listTime": "2020-06-18T20:05:49.596596Z",
                "category": {
                    "id": "2021",
                    "name": "Ligeiros Passageiros"
                },
                "location": {
                    "districtID": 5,
                    "district": "Porto",
                    "areaID": 66,
                    "area": "Valongo",
                    "subAreaID": 4,
                    "subArea": "Ermesinde"
                }
            },
            {
                "adID": 12505712,
                "subject": "Mercedes-Benz CLS 53 AMG XPTO",
                "status": "refused",
                "price": 20000,
                "deleteID": "11812861",
                "listID": "11812861",
                "externalAdID": "385648345",
                "notice": "Ad imported using partners API",
                "refusalReason": "Profissionais",
                "listTime": "2020-06-15T16:41:20.167749Z",
                "category": {
                    "id": "2022",
                    "name": "Descapotável / Coupé"
                },
                "location": {
                    "districtID": 14,
                    "district": "Lisboa",
                    "areaID": 213,
                    "area": "Lisboa",
                    "subAreaID": 34,
                    "subArea": "Olivais"
                }
            }
        ],
        "pagination": {
            "total": 24,
            "adsPerPage": 0,
            "currentOffset": 0
        }
    }
```

### Read ad complete details /partner/entries/{adID}
* * *
> This endpoint will return the ad details, regardless the ad state  
> General ad type, without special parameters  
> Requires valid token for authentication  
  
  <pre>
  Method 
    GET
  StatusCode
    417 - Expectation Failed
    <small>When requesting a bad or not authorized adID</small>
    200 - OK
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /partner/entries/12505606
  </pre>
```json  
    {
        "adID": 12505606,
        "author": {
            "email": "nome@partner.pt",
            "name": "Nome da loja",
            "phone": "911234567",
            "phoneDisabled": false,
            "professionalAd": true,
            "salesmanDisabled": false,
            "vatNumber": "999999990"
        },
        "body": "[{Título do anúncio a bold}]\n\nVeículo com as seguintes características\n[*] 4 Rodas\n[*] 5 Portas\n[*] Radio\n[*] GPS\n[*] Vidros escurecidos\n[*] Volante à esquerda\n\n",
        "category": "2080",
        "categoryPath": "2000>2080",
        "imageURLs": [
            "https://cdn.custojusto.pt/api/v1/images/images/953910819-teste-de-teste-de-trigger-em-anuncio-via-api.jpg?rule=gallery",
            "https://cdn.custojusto.pt/api/v1/images/images/919434168-teste-de-teste-de-trigger-em-anuncio-via-api.jpg?rule=gallery"
        ],
        "images": [
            "0953910819",
            "0919434168"
        ],
        "listID": "11812765",
        "deleteID": "11812765",
        "location": {
            "area": 66,
            "cp6": "4440-777",
            "district": 5,
            "subArea": 3
        },
        "partner": {
            "externalAdID": "7780p6yhgtr",
            "externalGroupID": "partner-group-name",
            "partnerParentID": "partner-name-999999990"
        },
        "price": 19999,
        "status": "active",
        "subject": "Teste de teste de trigger em anúncio via API",
        "type": "s",
        "url": "https://www.custojusto.pt/11812765"
    }
```

### Read ad complete details - Vehicles /partner/entries/{adID}
* * *
> This endpoint will return the ad details, regardless the ad state  
> Car type ad, with custom parameters  
> Requires valid token for authentication  
  
  
  <pre>
  Method 
    GET
  StatusCode
    417 - Expectation Failed
    <small>When requesting a bad or not authorized adID</small>
    200 - OK
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /partner/entries/12505606
  </pre>
```json    
    {
        "adID": 12505606,
        "author": {
            "email": "nome@partner.pt",
            "name": "Nome da loja",
            "phone": "911234567",
            "phoneDisabled": false,
            "professionalAd": true,
            "salesmanDisabled": false,
            "vatNumber": "999999990"
        },
        "body": "[{Título do anúncio a bold}]\n\nVeículo com as seguintes características\n[*] 4 Rodas\n[*] 5 Portas\n[*] Radio\n[*] GPS\n[*] Vidros escurecidos\n[*] Volante à esquerda\n\n",
        "category": "2021",
        "categoryPath": "2000>2020>2021",
        "imageURLs": [
            "https://cdn.custojusto.pt/api/v1/images/images/953910819-teste-de-teste-de-trigger-em-anuncio-via-api.jpg?rule=gallery",
            "https://cdn.custojusto.pt/api/v1/images/images/919434168-teste-de-teste-de-trigger-em-anuncio-via-api.jpg?rule=gallery"
        ],
        "images": [
            "0953910819",
            "0919434168"
        ],
        "listID": "11812765",
        "deleteID": "11812765",
        "location": {
            "area": 66,
            "cp6": "4440-777",
            "district": 5,
            "subArea": 3
        },
        "params": {
            "brand": 31,
            "capacity": 3000,
            "color": 4,
            "fuel": 1,
            "gearbox": 4,
            "licensePlate": "00-AA-00",
            "mileage": 10,
            "model": 243,
            "power": 230,
            "regMonth": 2,
            "regYear": 2013,
            "variant": "XPTO",
            "occupancy": 7,
            "videoURL": "https://www.youtube.com/watch?v=jNlqg72IeDU"
        },
        "partner": {
            "externalAdID": "7780p6yhgtr",
            "externalGroupID": "partner-group-name",
            "partnerParentID": "partner-name-999999990"
        },
        "price": 19999,
        "status": "active",
        "subject": "Mercedes-Benz CLS 400 XPTO",
        "type": "s",
        "url": "https://www.custojusto.pt/11812765"
    }
```

### Read ad complete details - Vehicle Parts /partner/entries/{adID}
* * *
> This endpoint will return the ad details, regardless the ad state  
> Vehicle part type ad, with custom parameters  
> Requires valid token for authentication  
  
  
  <pre>
  Method 
    GET
  StatusCode
    417 - Expectation Failed
    <small>When requesting a bad or not authorized adID</small>
    200 - OK
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /partner/entries/12505606
  </pre>
```json    
    {
        "adID": 12505606,
        "author": {
            "email": "nome@partner.pt",
            "name": "Nome da loja",
            "phone": "911234567",
            "phoneDisabled": false,
            "professionalAd": true,
            "salesmanDisabled": false,
            "vatNumber": "999999990"
        },
        "body": "[{Título do anúncio a bold}]\n\nVeículo com as seguintes características\n[*] 4 Rodas\n[*] 5 Portas\n[*] Radio\n[*] GPS\n[*] Vidros escurecidos\n[*] Volante à esquerda\n\n",
        "category": "2121",
        "categoryPath": "2000>2120>2121",
        "imageURLs": [
            "https://cdn.custojusto.pt/api/v1/images/images/953910819-teste-de-teste-de-trigger-em-anuncio-via-api.jpg?rule=gallery",
            "https://cdn.custojusto.pt/api/v1/images/images/919434168-teste-de-teste-de-trigger-em-anuncio-via-api.jpg?rule=gallery"
        ],
        "images": [
            "0953910819",
            "0919434168"
        ],
        "listID": "11812765",
        "deleteID": "11812765",
        "location": {
            "area": 66,
            "cp6": "4440-777",
            "district": 5,
            "subArea": 3
        },
        "params": {
            "partNumber": "222-AAA_123"
        },
        "partner": {
            "externalAdID": "7780p6yhgtr",
            "externalGroupID": "partner-group-name",
            "partnerParentID": "partner-name-999999990"
        },
        "price": 233,
        "status": "active",
        "subject": "Peça para Carro X",
        "type": "s",
        "url": "https://www.custojusto.pt/11812765"
    }
```

### Read ad complete details - Real Estate /partner/entries/{adID}
* * *
> This endpoint will return the ad details, regardless the ad state  
> Real Estate type ad, with custom parameters  
> Requires valid token for authentication  
  
  
  <pre>
  Method 
    GET
  StatusCode
    417 - Expectation Failed
    <small>When requesting a bad or not authorized adID</small>
    200 - OK
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /partner/entries/12497547
  </pre>
```json  
    {
      "adID":12497547,
      "author":{
          "email":"name@partner.pt",
          "name":"Partner name",
          "phone":"911234567",
          "phoneDisabled":false,
          "professionalAd":true,
          "rntLicence":"12345",
          "salesmanDisabled":false,
          "vatNumber":"999999990"
      },
      "body":"Apartamento localizado em Burgau, o segredo mais bem guardado do Algarve. É um típico porto de pesca debruçado sobre o mar. Por estar inclinada sobre a praia, de qualquer lado da pequena localidade se vê as águas calmas e transparentes.\u003cbr\u003e\u003cbr\u003ePossui dois quartos de casal, uma casa de banho, sala de jantar/estar e cozinha equipada. Esta propriedade tem a possibilidade de alojar mais pessoas em camas suplementares.\u003cbr\u003e\u003cbr\u003eAo abrir a janela vai desfrutar de uma vista fantástica sobre o mar e a praia. Tem ainda à sua disposição um pequeno terraço onde poderá efetuar refeições ao ar livre com a família.\u003cbr\u003e\u003cbr\u003eDevido à sua excelente localização, os hóspedes têm à sua disposição restaurantes, supermercados, comércios, praia e animação noturna sem precisar de utilizar o carro. As referências a este sítio recuam ao século XVI e ainda se vê as ruínas de um forte antigo. O local é propício a atividades ao ar livre, como desportos náuticos e aquáticos.\u003cbr\u003e\u003cbr\u003e De: 2018-03-23 até: 2018-03-30: Por noite: 48.8 euros e por semana: 341.6 euros (obrigatorio permanecer 4 noites na casa!)\u003cbr\u003e De: 2018-03-31 até: 2018-05-31: Por noite: 67.1 euros e por semana: 469.7 euros (obrigatorio permanecer 4 noites na casa!)\u003cbr\u003e De: 2018-06-01 até: 2018-07-15: Por noite: 79.3 euros e por semana: 555.1 euros (obrigatorio permanecer 5 noites na casa!)\u003cbr\u003e De: 2018-07-16 até: 2018-09-15: Por noite extra: 97.6 euros ou por semana: 683.2 euros (mínimo de 7 noites na casa)\u003cbr\u003e De: 2018-09-16 até: 2018-10-31: Por noite: 79.3 euros e por semana: 555.1 euros (obrigatorio permanecer 5 noites na casa!)\u003cbr\u003e De: 2018-11-01 até: 2018-12-29: Por noite: 54.9 euros e por semana: 384.3 euros (o",
      "category":"1020",
      "categoryPath":"1000>1020",
      "imageURLs":[
          "https://cdn.custojusto.pt/api/v1/images/images/1335591203-propriedade-situada-em-vila-do-bispo-ref-4640.jpg?rule=gallery",
          "https://cdn.custojusto.pt/api/v1/images/images/1392974608-propriedade-situada-em-vila-do-bispo-ref-4640.jpg?rule=gallery",
          "https://cdn.custojusto.pt/api/v1/images/images/1301497927-propriedade-situada-em-vila-do-bispo-ref-4640.jpg?rule=gallery",
          "https://cdn.custojusto.pt/api/v1/images/images/1327067884-propriedade-situada-em-vila-do-bispo-ref-4640.jpg?rule=gallery",
          "https://cdn.custojusto.pt/api/v1/images/images/1344114522-propriedade-situada-em-vila-do-bispo-ref-4640.jpg?rule=gallery",
          "https://cdn.custojusto.pt/api/v1/images/images/1310021246-propriedade-situada-em-vila-do-bispo-ref-4640.jpg?rule=gallery",
          "https://cdn.custojusto.pt/api/v1/images/images/1384451289-propriedade-situada-em-vila-do-bispo-ref-4640.jpg?rule=gallery",
          "https://cdn.custojusto.pt/api/v1/images/images/1318544565-propriedade-situada-em-vila-do-bispo-ref-4640.jpg?rule=gallery"
      ],
      "images":[
          "1335591203",
          "1392974608",
          "1301497927",
          "1327067884",
          "1344114522",
          "1310021246",
          "1384451289",
          "1318544565"
      ],
      "listID":"11804904",
      "deleteID":"11804904",
      "location":{
          "area":278,
          "cp6":"8650-111",
          "district":18,
          "subArea":2
      },
      "params":{
          "availability":"custom string, please contact us for more details",
          "beds":4,
          "energyRating":0,
          "gotAffordableRental":false,
          "rntLicence":"12345",
          "size":400,
          "terrainSize": 700,
          "constructionYear": 1850,
          "usageLicense": "XYZ/2021/AND/1234567",
          "tags":[
            "piscina",
            "cozinha",
            "wifi",
            "ac"
          ],
          "typology": 5,
          "videoURL": "https://www.youtube.com/embed/Z8XP7UjzvnU",
          "virtualTourURL": "https://my.matterport.com/show/?m=B3p9vSWmXcG"
      },
      "partner":{
          "externalAdID":"4640",
          "externalGroupID":"partner-group-name",
          "partnerParentID":"partner-name-999999990"
      },
      "price":59,
      "status":"active",
      "subject":"Propriedade situada em Vila-do-Bispo-Ref: 4640",
      "type":"u",
      "url":"https://www.custojusto.pt/11804904"
    }
```

### Upload images /images/ads
* * *
> When creating ads, image ids are needed. Use this endpoint to upload those images, image id will be returned  This endpoint will return a valid and temporary image url (valid for 24h).  
> Requires valid token for authentication  
  
  
  <pre>
  Method 
    POST
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
    Form field: file
    <small>curl --location --request POST '{API_URL}/images/ads' --header 'Authorization: kiYiuYTiuTiUTYiytIut' --header 'Content-Type: multipart/form-data' --form 'file=@/image_location/filename.jpg'</small>
  Response signature for /images/ads
  </pre>
```json  
    {
      "image":{
          "id":"3568575919",
          "image_url":"/mi/full/3568575919.jpg",
          "thumbnail_url":"/mi/thumbnail/3568575919.jpg",
          "gallery_url":"/mi/gallery/3568575919.jpg",
          "server_url":"https://www.custojusto.pt",
          "bytes_received":318373,
          "valid_until":"2020-06-23T15:15:48.201486653+01:00"
      }
    }
```


### Create general ad /partner/entries
> Create new general ad  
> Requires valid token for authentication    
  
  <pre>
  Method 
    POST
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Payload signature
  </pre>
```json
    {
      "author":{
          "email":"name@partner.pt",
          "name":"Partner name",
          "phone":"911234567",
          "phoneDisabled":false,
          "professionalAd":true,
          "salesmanDisabled":false,
          "vatNumber":"999999990"
      },
      "body": "[{Título do anúncio a bold}]\n\nIsto é um anúncio genérico, \n[*]Um barco com capacidade para 6 pessoas.",
      "category":"2080",
      "images":[
          "3568575919",
      ],
      "location":{
          "area":66,
          "cp6":"4440-777",
          "district":5,
          "subArea":3
      },
      "partner":{
          "externalAdID":"BOAT-123321",
          "externalGroupID":"partner-group-name"
      },
      "price":32022,
      "subject":"Barco para 6 pessoas, motor 175cv",
      "type":"s"
    }
```    
<pre>
  Response signature
  StatusCode
    200 - OK
</pre>
```json      
    {
      "results":[
          {
            "field":"adID",
            "value":"12505607"
          },
          {
            "field":"remainingCredits",
            "value":"985"
          }
      ]
    }
```
<pre>
  StatusCode
    417 - Expectation Failed
  </pre>
```json  
    {
      "results":[
          {
            "field":"fieldName",
            "value":"Error description"
          }
      ]
    }
```
    
<pre>
adID - ID used to edit or deactivate an exported ad
remainingCredits - Indicates the number of new ads + number of Edits remaning
</pre>


### Create vehicle ad /partner/entries
* * *
> Create new vehicle ad  
> Requires valid token for authentication  
  
  
  <pre>
  Method 
    POST
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Payload signature
  </pre>
```json    
    {
      "author":{
          "email":"name@partner.pt",
          "name":"Partner name",
          "phone":"911234567",
          "phoneDisabled":false,
          "professionalAd":true,
          "salesmanDisabled":false,
          "vatNumber":"999999990"
      },
      "body": "[{Título do anúncio a bold}]\n\nIsto é um anúncio de veículo\n[*]BMW 216 Active Tourer 17",
      "category":"2021",
      "images":[
          "3568575919",
      ],
      "location":{
          "area":66,
          "cp6":"4445-371",
          "district":5,
          "subArea":4
      },
      "params":{
          "brand":6,
          "capacity":200,
          "color":8,
          "fuel":1,
          "gearbox":2,
          "licensePlate":"00-XX-00",
          "mileage":5,
          "model":107,
          "power":200,
          "regMonth":3,
          "regYear":2017,
          "variant":"XPTO",
          "videoURL":"https://www.youtube.com/watch?v=jNlqg72IeDU"
      },
      "partner":{
          "externalAdID":"BMW-112233",
          "externalGroupID":"partner-group-name"
      },
      "price":4967,
      "subject":"Auto subject will apply for cars",
      "type":"s"
    }
```
<pre>
  Response signature
  StatusCode
    200 - OK
  </pre>
```json  
    {
      "results":[
          {
            "field":"adID",
            "value":"11505679"
          },
          {
            "field":"remainingCredits",
            "value":"984"
          }
      ]
    }
```
<pre>
  StatusCode
    417 - Expectation Failed
  </pre>
```json  
    {
      "results":[
          {
            "field":"fieldName",
            "value":"Error description"
          }
      ]
    }
```
    
<pre>
  adID - ID used to edit or deactivate an exported ad
  remainingCredits - Indicates the number of new ads + number of Edits remaning
</pre>

**Custom Params for Vehicles category** - Check [section](#get-allowedcustom-fields-by-category-categoriesfieldscategoryid) and [section](#get-allowedcustom-fields-by-category-and-ad-type-categoriesfieldscategoryidadtype)
   > brand - BrandID  
   > capacity - Cubic Centimeters (CC)  
   > color - ColorID  
   > fuel - Fuel TypeID  
   > gearbox - Gearbox TypeID  
   > licensePlate - Valid, uppercased, Portuguese format, licenseplate  
   > mileage - MileageID  
   > model - ModelID  
   > power - BHP (CV)  
   > regMonth - First registration - Month  
   > regYear - First registration - Year  
   > variant - Variant/Version (SW, S-Line, etc)  
   > occupancy - Int value, number of seats in vehicle (only appliable in categories: 2141, 2142, 2143, 2144, 2145, 2146, 2181)  
   > videoURL - A link for a video, we currently support:
   >> YouTube (https://www.youtube.com/watch?v=jNlqg72IeDU)  
   >> Vimeo (https://vimeo.com/347119375)  
   >> DailyMotion (https://www.dailymotion.com/video/x75z2pn)  


**Custom Params for Vehicles/Motos category** - Check [section](#get-allowedcustom-fields-by-category-categoriesfieldscategoryid) and [section](#get-allowedcustom-fields-by-category-and-ad-type-categoriesfieldscategoryidadtype)
   > motobrand - BrandID (/motobrands or /motobrands/byname/{value})  
   > motomodel - ModelID (/motobrands/{id} or /motobrands/{id}/byname/{value})  
   > cubicCentimeters - Cubic Centimeters ID (/cc or using /cc/{value})  
   > regYear - License plate year (yyyy)  
   > mileage - Mileages (/mileages or /mileages/{value})  
   > videoURL - A link for a video, we currently support:  
   >> YouTube (https://www.youtube.com/watch?v=jNlqg72IeDU)  
   >> Vimeo (https://vimeo.com/347119375)  
   >> DailyMotion (https://www.dailymotion.com/video/x75z2pn)  



### Create vehicle part ad /partner/entries
* * *
> Create new vehicle part ad  
> Requires valid token for authentication  
  
  
  <pre>
  Method 
    POST
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Payload signature
  </pre>
```json    
    {
      "author":{
          "email":"name@partner.pt",
          "name":"Partner name",
          "phone":"911234567",
          "phoneDisabled":false,
          "professionalAd":true,
          "salesmanDisabled":false,
          "vatNumber":"999999990"
      },
      "body": "[{Título do anúncio a bold}]\n\nIsto é um anúncio de peças\n[*]Peça X",
      "category":"2121",
      "images":[
          "3568575919",
      ],
      "location":{
          "area":66,
          "cp6":"4445-371",
          "district":5,
          "subArea":4
      },
      "params":{
          "partNumber": "222-AAA_123"
      },
      "partner":{
          "externalAdID":"BMW-112233",
          "externalGroupID":"partner-group-name"
      },
      "price":4967,
      "subject":"Auto subject will apply for cars",
      "type":"s"
    }
```
<pre>
  Response signature
  StatusCode
    200 - OK
  </pre>
```json  
    {
      "results":[
          {
            "field":"adID",
            "value":"11505679"
          },
          {
            "field":"remainingCredits",
            "value":"984"
          }
      ]
    }
```
<pre>
  StatusCode
    417 - Expectation Failed
  </pre>
```json  
    {
      "results":[
          {
            "field":"fieldName",
            "value":"Error description"
          }
      ]
    }
```
    
<pre>
  adID - ID used to edit or deactivate an exported ad
  remainingCredits - Indicates the number of new ads + number of Edits remaning
</pre>

**Custom Params for Vehicle Parts** - Check [section](#get-allowedcustom-fields-by-category-categoriesfieldscategoryid) and [section](#get-allowedcustom-fields-by-category-and-ad-type-categoriesfieldscategoryidadtype)
   > partNumber - part number/reference  


### Create animal ad /partner/entries
* * *
> Create new animal ad  
> Requires valid token for authentication  
  
  
  <pre>
  Method 
    POST
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Payload signature
  </pre>
```json    
    {
      "author":{
          "email":"name@partner.pt",
          "name":"Partner name",
          "phone":"911234567",
          "phoneDisabled":false,
          "professionalAd":true,
          "salesmanDisabled":false,
          "vatNumber":"999999990"
      },
      "body": "[{Título do anúncio a bold}]\n\nIsto é um novo anúncio",
      "category":"6061",
      "images":[
          "3568575919",
      ],
      "location":{
          "area":66,
          "cp6":"4445-371",
          "district":5,
          "subArea":4
      },
      "params":{
          "animalAge": 1,
          "animalBreedOther": "Bengal",
          "breedingFemaleNr": "3456789",
          "breedingNr": "345678",
          "creatorRegistrationNr": "456789",
          "nrOfLitterAnimals": "2"
      },
      "partner":{
          "externalAdID":"DOG-112233",
          "externalGroupID":"partner-group-name"
      },
      "price":4967,
      "subject":"Auto subject will apply for cars",
      "type":"s"
    }
```
<pre>
  Response signature
  StatusCode
    200 - OK
  </pre>
```json  
    {
      "results":[
          {
            "field":"adID",
            "value":"11501677"
          },
          {
            "field":"remainingCredits",
            "value":"983"
          }
      ]
    }
```
<pre>
  StatusCode
    417 - Expectation Failed
  </pre>
```json  
    {
      "results":[
          {
            "field":"fieldName",
            "value":"Error description"
          }
      ]
    }
```
    
<pre>
  adID - ID used to edit or deactivate an exported ad
  remainingCredits - Indicates the number of new ads + number of Edits remaning
</pre>

**Custom Params for Animals category, valid categories for custom params are ony Dogs and Cats** - Check [section](#get-allowedcustom-fields-by-category-categoriesfieldscategoryid) and [section](#get-allowedcustom-fields-by-category-and-ad-type-categoriesfieldscategoryidadtype)
   > animalAge - age interval ID  
   > animalBreed - Dogs category only, accepts a valid ID from breeds listing  
   > animalBreedOther - Cats category only, accepts a string  
   > breedingFemaleNr - "Nº de identificação electrónica da fêmea reprodutora"  
   > breedingNr - "Nº de identificação electrónica da cria"  
   > creatorRegistrationNr - "Nº de inscrição do criador"  
   > lop - Dogs category only  
   > nrOfLitterAnimals - "Nº de animais da ninhada"  


### Create real estate ad /partner/entries
* * *
> Create new real estate ad  
> Requires valid token for authentication  
    
  <pre>
  Method 
    POST
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Payload signature
  </pre>
```json  
    {
      "author":{
          "email":"name@partner.pt",
          "name":"Partner name",
          "phone":"911234567",
          "phoneDisabled":false,
          "professionalAd":true,
          "salesmanDisabled":false,
          "vatNumber":"999999990"
      },
      "body": "[{Título do anúncio a bold}]\n\nVenda de apartamento com vista de mar e terra",
      "category":"1020",
      "images":[
          "3568575919",
      ],
      "location":{
          "area":66,
          "cp6":"4445-371",
          "district":5,
          "subArea":4
      },
      "params":{
          "energyRating":3,
          "size":500,
          "typology":7,
          "videoURL":"https://www.youtube.com/watch?v=jNlqg72IeDU",
          "virtualTourURL":"https://my.matterport.com/show/?m=B3p9vSWmXcG"
      },
      "partner":{
          "externalAdID":"Partner-T4-33123",
          "externalGroupID":"partner-group-name"
      },
      "price":4967,
      "subject":"Auto subject will apply for cars",
      "type":"s"
    }
```

<pre>
  Response signature
  StatusCode
    200 - OK
  </pre>
```json  
    {
      "results":[
          {
            "field":"adID",
            "value":"11505679"
          },
          {
            "field":"remainingCredits",
            "value":"983"
          }
      ]
    }
```
<pre>
  StatusCode
    417 - Expectation Failed
  </pre>
```json  
    {
      "results":[
          {
            "field":"fieldName",
            "value":"Error description"
          }
      ]
    }
```
    
<pre>
  adID - ID used to edit or deactivate an exported ad
  remainingCredits - Indicates the number of new ads + number of Edits remaning
</pre>
    
**Custom Params for Real Estate** - Check [section](#get-allowedcustom-fields-by-category-categoriesfieldscategoryid) and [section](#get-allowedcustom-fields-by-category-and-ad-type-categoriesfieldscategoryidadtype)
  > availability - To be defined a custom layout  
  > beds - Capacity, number of beds or rooms. Is this case, the website will show 4 as capacity  
  > energyRating - Not used for Vacation rental  
  > gotAffordableRental - Not used for Vacation rental. This parameter indicates if the rental allows PAA (arrendamento-acessivel)  
  > rntLicence - Rental license  
  > size - Mt² available  
  > terrainSize - Mt² terrain size (only appliable in categories: 1040, 1060)  
  > constructionYear - Building construction year (only appliable in categories: 1020, 1040; in the near future it will be mandatory for renting)  
  > usageLicense - Building usage license (only appliable in categories: 1020, 1040 and for constructionYear >= 1951; in the near future it will be mandatory for renting) 
  > tags - Available amenities. Check /tags/{category} endpoint  
  > typology - Check /roomtypologies for correct ID  
  > videoURL - A link for a video, we currently support:  
  >> YouTube (https://www.youtube.com/watch?v=jNlqg72IeDU)  
  >> Vimeo (https://vimeo.com/347119375)  
  >> DailyMotion (https://www.dailymotion.com/video/x75z2pn)  
  >
  > virtualTourURL - A link for a virtual tour, we currently support:  
  >> Matterport (https://my.matterport.com/show/?m=B3p9vSWmXcG)  
  >> Remax Virtual Tour Premier (https://www.remaxvtp.com/remax/porto/oceanus/080/tour.html)  
  >> Nodalview (https://www.nodalview.com/7oUdKXnqY2jD5YDmTquVKJkF)  
  >> X-IMO (https://XYZ.ximo.pt/vtour/tourPlayer.htm?idImovel=123)  


### Create real estate - Vacation rental ad /partner/entries
* * *
> Create new VR ad  
> Requires valid token for authentication  
  
 <pre>
  Method 
    POST
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Payload signature
  </pre>
```json  
    {
      "author":{
          "email":"name@partner.pt",
          "name":"Partner name",
          "phone":"911234567",
          "phoneDisabled":false,
          "professionalAd":true,
          "salesmanDisabled":false,
          "vatNumber":"999999990"
      },
      "body": "[{Título do anúncio a bold}]\n\nApartamento localizado em Burgau, o segredo mais bem guardado do Algarve",
      "category":"1100",
      "images":[
          "3568575919",
      ],
      "location":{
          "area":278,
          "cp6":"8650-111",
          "district":18,
          "subArea":2
      },
      "params":{
          "accommodationType":1,
          "vacationType":1,
          "availability":"custom string, please contact us for more details",
          "beds":4,
          "rntLicence":"12345",
          "size":400,
          "tags":[
            "piscina",
            "cozinha",
            "wifi",
            "ac"
          ],
          "typology":5,
          "videoURL":"https://www.youtube.com/watch?v=jNlqg72IeDU",
          "virtualTourURL":"https://my.matterport.com/show/?m=B3p9vSWmXcG"
      },
      "partner":{
          "externalAdID":"Partner-T2-33123",
          "externalGroupID":"partner-group-name"
      },
      "price":130,
      "subject":"Propriedade situada em Vila-do-Bispo-Ref: 4640",
      "type":"u"
    }
```
<pre>
  Response signature
  StatusCode
    200 - OK
  </pre>
```json  
    {
      "results":[
          {
            "field":"adID",
            "value":"11505679"
          },
          {
            "field":"remainingCredits",
            "value":"983"
          }
      ]
    }
```
<pre>
  StatusCode
    417 - Expectation Failed
  </pre>
```json  
    {
      "results":[
          {
            "field":"fieldName",
            "value":"Error description"
          }
      ]
    }
```
    
<pre>
  adID - ID used to edit or deactivate an exported ad
  remainingCredits - Indicates the number of new ads + number of Edits remaning
</pre>
    
**Custom Params for Real Estate - Vacation rental** - Check [section](#get-allowedcustom-fields-by-category-categoriesfieldscategoryid) and [section](#get-allowedcustom-fields-by-category-and-ad-type-categoriesfieldscategoryidadtype)
   > accommodationType - accommodation type ID (/accommodationtypes)  
   > vacationType - vacation type ID (/cavationtypes)  


### Edit ad /partner/entries/{adID}
* * *
> Edit/reactivate an ad
> Requires valid token for authentication  
  
  
  <pre>
  Method 
    PUT
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Payload signature
    Same as for creating  <small>It will not bump the ad</small>
  Response signature
  StatusCode
    200 - OK
  </pre>
```json  
    {
      "results":[
          {
            "field":"adID",
            "value":"11505679"
          },
          {
            "field":"remainingCredits",
            "value":"983"
          }
      ]
    }
```
<pre>
  StatusCode
    417 - Expectation Failed
  </pre>
```json  
    {
      "results":[
          {
            "field":"fieldName",
            "value":"Error description"
          }
      ]
    }
```
    
### Deactivate ad /partner/entries/{deleteID}
> Deactivate an ad  deleteID field is preset on /partner/entries and it's the same as the listID found when reading the full ad details.  
> Requires valid token for authentication  
  
  <pre>
  Method 
    DELETE
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Payload signature
    None
  Response signature
  StatusCode
    200 - OK
  </pre>
```json  
    {
      "results":[
          {
            "field":"message",
            "value":"ok, ad deleted"
          }
      ]
    }
```
<pre>
  StatusCode
    417 - Expectation Failed
  </pre>
```json  
    {
      "results":[
          {
            "field":"error",
            "value":"Este anúncio já se encontra excluído, e será removido do site dentro de poucos minutos."
          }
      ]
    }
```

### Callbacks
> The API will perform callbacks to notify CRMs of actions related to partners.  
> For this to be possible, a callback URL has to be configured first. Please contact us to set your callback URL. It should be in https and have a valid certiticate associated.  
> As the main api, all data is sent as JSON, with UTF-8 encodings. The HTTP verb used is always POST.  

| Name | Type | Description |
| --- | --- | --- |
| **event** | string | The event type. |
| **request_id** | string | The unique identifier for this request. Please mention this when contacting us for debugging issues. |
| **token** |	string | The token for the respective partner. |


#### Ad reply callback
> This callback is sent when an ad is replied to. The **event** value for this callback is **replied**.  

| Name | Type | Description |
| --- | --- | --- |
| **ad_id** | string | The ad_id specified when inserting this ad. |
| **body** | string | The message body. |
| **sender_email** | string | The sender's email address. |
| **sender_name**	| string | The sender's name. |
| **sender_phone** | string | The sender's phone number. |

```json  
    {
      "event": "replied",
      "request_id": "1xChI.5",
      "token": "mfzIgH9tnOMrnD5oszO1",
      "ad_id": "20170921.112229",
      "body": "Olá, estou interessado no imóvel\nPodemos agendar uma visita amanhã?",
      "sender_email":"antonio@example.pt",
      "sender_name":"António Lolladas",
      "sender_phone":"910000001"
    }
```

#### Ad refused callback
> This callback is sent when an ad is refused. The **event** value for this callback is **refused**.  

| Name | Type | Description |
| --- | --- | --- |
| **ad_id** | string | The ad_id specified when inserting this ad. |
| **reason** | string | The reason why the ad was refused. |

```json  
    {
        "event": "refused",
        "request_id": "1xChI.5",
        "token": "mfzIgH9tnOMrnD5oszO1",
        "ad_id": "20170921.112229",
        "reason": "O bem ou serviço que pretende anunciar já se encontra actualmente publicado. Cada bem ou serviço apenas pode ter um anúncio publicado de cada vez. Não é permitida a publicação do mesmo bem ou serviço em mais do que uma região ou em mais do que uma categoria. Caso os artigos sejam semelhantes, mas não idênticos, por favor contacte-nos através do link \"Ajuda\", disponível no rodapé da homepage e no cabeçalho de cada página."
    }
```

#### Ad published callback
> This callback is sent when an ad is published, which usually occurs soon after it's inserted/updated. The **event** value for this callback is **published**.  

| Name | Type | Description |
| --- | --- | --- |
| **ad_id** | string | The ad_id specified when inserting this ad. |
| **url** | string | The URL where the ad is published. |

```json  
    {
        "event": "published",
        "request_id": "1xChI.5",
        "token": "mfzIgH9tnOMrnD5oszO1",
        "ad_id": "20170921.112229",
        "url": "http://www.custojusto.pt/madeira/apartamentos/apartamento-t3-colinas-da-achada-24605948"
    }
```

#### Partner created callback
> This callback is sent when a new partner is created. This event will also be communicated through email, but this callback may be used to automate the process. The **event** value for this callback is **created**.  

| Name | Type | Description |
| --- | --- | --- |
| **credit** | int | The number of credits (ads active at a given time) allowed for the partner. |
| **email** | string | The email address of the partner. |
| **name** | string | The name of the partner. |
| **vat** | string | The portuguese VAT number of the partner. |
| **ami** | string | The portuguese AMI number of the partner (Real Estate only). |

```json  
    {
        "event": "created",
        "request_id": "1xChI.5",
        "token": "mfzIgH9tnOMrnD5oszO1",
        "credit": 150,
        "email": "imox@example.com",
        "name": "IMO X",
        "vat": "123456789",
        "ami": "12345"
    }
```

#### Partner changed callback
> This callback is sent when a new partner is changed. The **event** value for this callback is **changed**.  

| Name | Type | Description |
| --- | --- | --- |
| **credit** | int | The new number of credits (ads active at a given time) allowed for the partner. |

```json  
    {
        "event": "changed",
        "request_id": "1xChI.5",
        "token": "mfzIgH9tnOMrnD5oszO1",
        "credit": 150
    }
```
