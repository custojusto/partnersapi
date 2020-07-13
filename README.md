New features will be added just to this API


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
        "hasChildren": false
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
[
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


### Get our color list /color
* * *
> This endpoint returns the available colors on our platform  
> Requires valid token for authentication  
  
  
  <pre>
  Method 
    GET
  Headers
    Content-Type: application/json
    Authorization: kiYiuYTiuTiUTYiytIut
  Response signature for /color
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


### Get room typology /partner/categories
* * *
> This endpoint returns the category tree allowed for the privided partner token  
> Requires valid token for authentication  
  
  
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
        "allowedCategory": "2000",
        "hasShop": true,
        "shop": {
            "name": "Partner Name shop",
            "description": "By amazing shop",
            "address": "Partner shop address",
            "website": "https://www.partner.com",
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
                "phoneViews": 2
            },
            "previousMonth": {
                "pageViews": 69,
                "adReplies": 4,
                "phoneViews": 0
            },
            "currentMonth": {
                "pageViews": 45,
                "adReplies": 2,
                "phoneViews": 0
            },
            "previousWeek": {
                "pageViews": 10,
                "adReplies": 0,
                "phoneViews": 0
            },
            "currentWeek": {
                "pageViews": 33,
                "adReplies": 2,
                "phoneViews": 0
            }
        },
        "subscriptionStatus": {
            "partnerParentID": "auto",
            "package": "prestige",
            "expireAt": "2021-06-03T23:59:59Z",
            "numberImageUploads": 36,
            "adsActive": 7,
            "adsTotal": 100,
            "adsLeft": 93,
            "adsActionsLeft": 990,
            "availableCredits": 3657
        },
        "adsStatus": {
            "deleted": 13,
            "active": 6,
            "refused": 1,
            "inactive": 0
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
      }
    }
```

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
    Authorization: Token kiYiuYTiuTiUTYiytIut
    Content-Type: multipart/form-data
    Form field: file
    <small>curl --location --request POST '{API_URL}/images/users/shop' --header 'Authorization: Token kiYiuYTiuTiUTYiytIut' --header 'Content-Type: multipart/form-data' --form 'file=@/image_location/filename.jpg'</small>
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
    Authorization: Token kiYiuYTiuTiUTYiytIut
  </pre>


### Update user profile image /images/users/profile
* * *
> This endpoint allows profile logo update. Will remove the existing image.  Only jpg files are allowed  
> Requires valid token for authentication  
  
  
  <pre>
  Method 
    POST
  Headers
    Authorization: Token kiYiuYTiuTiUTYiytIut
    Content-Type: multipart/form-data
    Form field: file
    <small>curl --location --request POST '{API_URL}/images/users/profile' --header 'Authorization: Token kiYiuYTiuTiUTYiytIut' --header 'Content-Type: multipart/form-data' --form 'file=@/image_location/filename.jpg'</small>
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
    Authorization: Token kiYiuYTiuTiUTYiytIut
  </pre>


### Get partner ads /partner/entries
* * *
> This endpoint returns all partner ads, with a few information  All 4 Status apply: active (published), inactive (under approval), disabled (marked as deleted for less than 60 days), refused (when ad has been refused, refusalReason field will contain more details)  
> Requires valid token for authentication  
  
 <pre>
  **it's possible to filter data based on url route**
  * /partner/entries/active will return just active ads  
  * /partner/entries/refused will return just refused ads  
  * /partner/entries/disabled will return just ads marked as disabled. Auto removal after 60 days of the deactivation  
  * /partner/entries/inactive will return just inactive ads  
  ** pagination also possible **   Params: p=0 (page number, index 0 based) c=40 (count per page)    
  ** stats per ad also possible **  Param: stats=enabled adds a new object to each ad
  </pre>
```json
  "adStats": {
      "month": {
          "pageViews": 16,
          "replies": 5,
          "phoneViews": 0
      },
      "yesterday": {
          "pageViews": 13,
          "replies": 5,
          "phoneViews": 0
      },
      "today": {
          "pageViews": 3,
          "replies": 0,
          "phoneViews": 0
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
            "variant": "XPTO"
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
    
  <pre>
    * Custom Params for Vehicles category *
    brand - BrandID
    capacity - Cubic Centimeters (CC)
    color - ColorID
    fuel - Fuel TypeID
    gearbox - Gearbox TypeID
    licensePlate - Valid, uppercased, Portuguese format, licenseplate
    mileage - MileageID
    model - ModelID
    power - BHP (CV)
    regMonth - First registration - Month
    regYear - First registration - Year
    variant - Variant/Version (SW, S-Line, etc)
  </pre>



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
      "category":"1100",
      "categoryPath":"1000>1100",
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
          "tags":[
            "piscina",
            "cozinha",
            "wifi",
            "ac"
          ],
          "typology":5
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
    
  <pre>
    * Custom Params for Real Estate *
        availability - To be defined a custom layout
        beds - Capacity, number of beds or rooms. Is this case, the website will show 4 as capacity
        energyRating - Not used for Vacation rental
        gotAffordableRental - Not used for Vacation rental. This parameter indicates if the rental allows PAA (arrendamento-acessivel)
        rntLicence - Rental license
        size - Mt² available
        tags - Available amenities. Check /tags/{category} endpoint
        typology - Check /roomtypologies for correct ID
  </pre>


### Update shop banner /images/ads
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
    <small>curl --location --request POST '{API_URL}/images/ads' --header 'Authorization: Token kiYiuYTiuTiUTYiytIut' --header 'Content-Type: multipart/form-data' --form 'file=@/image_location/filename.jpg'</small>
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
          "externalGroupID":"partner-group-name",
      },
      "price":32022,
      "subject":"Barco para 6 pessoas, motor 175cv",
      "type":"s",
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
          "variant":"XPTO"
      },
      "partner":{
          "externalAdID":"BMW-112233",
          "externalGroupID":"partner-group-name",
      },
      "price":4967,
      "subject":"Auto subject will apply for cars",
      "type":"s",
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
          "typology":7
      },
      "partner":{
          "externalAdID":"Partner-T4-33123",
          "externalGroupID":"partner-group-name",
      },
      "price":4967,
      "subject":"Auto subject will apply for cars",
      "type":"s",
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
          "typology":5
      },
      "partner":{
          "externalAdID":"Partner-T2-33123",
          "externalGroupID":"partner-group-name",
      },
      "price":130,
      "subject":"Propriedade situada em Vila-do-Bispo-Ref: 4640",
      "type":"u",
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


### Edit ad /partner/entries/{adID}
* * *
> Edit an ad  
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