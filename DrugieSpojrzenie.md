Zapamiętać: trzymać ludzi chaotycznych z dala od szeroko-rozumianej architektury.

[![Mermaid diagram](https://mermaid.ink/img/eyJjb2RlIjoiZ3JhcGggVERcbkFbRWR5dG9yXSAtLT4gfFR3b3J6eXwgQltKU09OIFNjaGVtYV1cblpbVcW8eXRrb3duaWtdIC0tPiB8V3Bpc3VqZXwgRFt3d3cuZXhhbXBsZS5jb20vYWJjXVxuRCAtLT4gWFxuWFtQcnplZ2zEhWRhcmthXSAtLT4gfFd5c3nFgmEgxbzEhWRhbmllfCBDW1NlcndlciBkeW5hbWljem55XVxuWCAtLT4gfGFsdGVybmF0eXduaWV8IEVbU2Vyd2VyIHN0YXR5c3R5Y3pueV1cbkMgLS0-IHxTcHJhd2R6YSBwbGlrfCBGW2V2ZW50cy9hYmNdXG5GIC0tPiB8SmXFm2xpIGlzdG5pZWplfCBIWyBdXG5IIC0tPiB8VVBEQVRFIHh4eCBXSEVSRSBsb2NhdGlvbiA9ICdhYmMnfCBHW0JhemEgZGFueWNoXVxuSCAtLT4gfFd5c3nFgmEgxbzEhWRhbmllfCBFXG5FIC0tPiB8RmV0Y2h8IElbd3d3LmFub3RoZXJzaXRlLmNvbS9hYmMuanNvbl1cbkkgLS0-IHxad3JhY2EgcGxpayBrb25maWd1cmFjeWpueXwgWFxuSSAtLT4gQiIsIm1lcm1haWQiOnsidGhlbWUiOiJkZWZhdWx0In0sInVwZGF0ZUVkaXRvciI6ZmFsc2V9)](https://mermaid-js.github.io/mermaid-live-editor/#/edit/eyJjb2RlIjoiZ3JhcGggVERcbkFbRWR5dG9yXSAtLT4gfFR3b3J6eXwgQltKU09OIFNjaGVtYV1cblpbVcW8eXRrb3duaWtdIC0tPiB8V3Bpc3VqZXwgRFt3d3cuZXhhbXBsZS5jb20vYWJjXVxuRCAtLT4gWFxuWFtQcnplZ2zEhWRhcmthXSAtLT4gfFd5c3nFgmEgxbzEhWRhbmllfCBDW1NlcndlciBkeW5hbWljem55XVxuWCAtLT4gfGFsdGVybmF0eXduaWV8IEVbU2Vyd2VyIHN0YXR5c3R5Y3pueV1cbkMgLS0-IHxTcHJhd2R6YSBwbGlrfCBGW2V2ZW50cy9hYmNdXG5GIC0tPiB8SmXFm2xpIGlzdG5pZWplfCBIWyBdXG5IIC0tPiB8VVBEQVRFIHh4eCBXSEVSRSBsb2NhdGlvbiA9ICdhYmMnfCBHW0JhemEgZGFueWNoXVxuSCAtLT4gfFd5c3nFgmEgxbzEhWRhbmllfCBFXG5FIC0tPiB8RmV0Y2h8IElbd3d3LmFub3RoZXJzaXRlLmNvbS9hYmMuanNvbl1cbkkgLS0-IHxad3JhY2EgcGxpayBrb25maWd1cmFjeWpueXwgWFxuSSAtLT4gQiIsIm1lcm1haWQiOnsidGhlbWUiOiJkZWZhdWx0In0sInVwZGF0ZUVkaXRvciI6ZmFsc2V9)

Przykładowe pliki JSON 
```yaml
# anothersite.com/city.json
{
  "city": [
    {
      "district": [
        {
          "name": "Pierwsza dzielnica",
          "location": [
            {
              "name": "Miejsce",
              "link": "https://example.com/"
            },
            {
              "name": "Miejsce2",
              "link": "https://example.com/"
            }
          ]
        },
        {
          "name": "Druga dzielnica",
          "location": [
            {
              "name": "Miejsce",
              "link": "https://example.com/"
            },
            {
              "name": "Miejsce2",
              "link": "https://example.com/"
            }
          ]
        }
      ]
    }
  ]
}
```
```yaml
# anothersite.com/monster.json
{
  "monster": {
    "HP": 100,
    "attack": 10,
    "defense": 25,
    "name": "monster123"
  }
}
```
```yaml
# anothersite.com/schemas/city.json
{
    "$schema": "https://json-schema.org/draft-07/schema",
    "$id": "http://example.com/city.json",
    "type": "object",
    "title": "The root schema",
    "description": "The root schema comprises the entire JSON document.",
    "default": {},
    "examples": [
      {
        "city": [
          {
            "district": [
              {
                "name": "first district",
                "location": [
                  {
                    "name": "prime location",
                    "link": "https://example.com/"
                  }
                ]
              }
            ]
          }
        ]
      }
    ],
    "required": [
      "city"
    ],
    "properties": {
      "city": {
        "$id": "#/properties/city",
        "type": "array",
        "title": "The city schema",
        "description": "An explanation about the purpose of this instance.",
        "default": [],
        "examples": [
          [
            {
              "district": [
                {
                  "name": "first district",
                  "location": [
                    {
                      "name": "prime location",
                      "link": "https://example.com/"
                    }
                  ]
                }
              ]
            }
          ]
        ],
        "additionalItems": true,
        "items": {
          "$id": "#/properties/city/items",
          "anyOf": [
            {
              "$id": "#/properties/city/items/anyOf/0",
              "type": "object",
              "title": "The first anyOf schema",
              "description": "An explanation about the purpose of this instance.",
              "default": {},
              "examples": [
                {
                  "district": [
                    {
                      "name": "first district",
                      "location": [
                        {
                          "name": "prime location",
                          "link": "https://example.com/"
                        }
                      ]
                    }
                  ]
                }
              ],
              "required": [
                "district"
              ],
              "properties": {
                "district": {
                  "$id": "#/properties/city/items/anyOf/0/properties/district",
                  "type": "array",
                  "title": "The district schema",
                  "description": "An explanation about the purpose of this instance.",
                  "default": [],
                  "examples": [
                    [
                      {
                        "name": "first district",
                        "location": [
                          {
                            "name": "prime location",
                            "link": "https://example.com/"
                          }
                        ]
                      }
                    ]
                  ],
                  "additionalItems": true,
                  "items": {
                    "$id": "#/properties/city/items/anyOf/0/properties/district/items",
                    "anyOf": [
                      {
                        "$id": "#/properties/city/items/anyOf/0/properties/district/items/anyOf/0",
                        "type": "object",
                        "title": "The first anyOf schema",
                        "description": "An explanation about the purpose of this instance.",
                        "default": {},
                        "examples": [
                          {
                            "name": "first district",
                            "location": [
                              {
                                "name": "prime location",
                                "link": "https://example.com/"
                              }
                            ]
                          }
                        ],
                        "required": [
                          "name",
                          "location"
                        ],
                        "properties": {
                          "name": {
                            "$id": "#/properties/city/items/anyOf/0/properties/district/items/anyOf/0/properties/name",
                            "type": "string",
                            "title": "The name schema",
                            "description": "An explanation about the purpose of this instance.",
                            "default": "",
                            "examples": [
                              "first district"
                            ]
                          },
                          "location": {
                            "$id": "#/properties/city/items/anyOf/0/properties/district/items/anyOf/0/properties/location",
                            "type": "array",
                            "title": "The location schema",
                            "description": "An explanation about the purpose of this instance.",
                            "default": [],
                            "examples": [
                              [
                                {
                                  "name": "prime location",
                                  "link": "https://example.com/"
                                }
                              ]
                            ],
                            "additionalItems": true,
                            "items": {
                              "$id": "#/properties/city/items/anyOf/0/properties/district/items/anyOf/0/properties/location/items",
                              "anyOf": [
                                {
                                  "$id": "#/properties/city/items/anyOf/0/properties/district/items/anyOf/0/properties/location/items/anyOf/0",
                                  "type": "object",
                                  "title": "The first anyOf schema",
                                  "description": "An explanation about the purpose of this instance.",
                                  "default": {},
                                  "examples": [
                                    {
                                      "name": "prime location",
                                      "link": "https://example.com/"
                                    }
                                  ],
                                  "required": [
                                    "name",
                                    "link"
                                  ],
                                  "properties": {
                                    "name": {
                                      "$id": "#/properties/city/items/anyOf/0/properties/district/items/anyOf/0/properties/location/items/anyOf/0/properties/name",
                                      "type": "string",
                                      "title": "The name schema",
                                      "description": "An explanation about the purpose of this instance.",
                                      "default": "",
                                      "examples": [
                                        "prime location"
                                      ]
                                    },
                                    "link": {
                                      "$id": "#/properties/city/items/anyOf/0/properties/district/items/anyOf/0/properties/location/items/anyOf/0/properties/link",
                                      "type": "string",
                                      "title": "The link schema",
                                      "description": "An explanation about the purpose of this instance.",
                                      "format": "uri",
                                      "default": "",
                                      "examples": [
                                        "https://example.com/"
                                      ]
                                    }
                                  },
                                  "additionalProperties": false
                                }
                              ]
                            }
                          }
                        },
                        "additionalProperties": false
                      }
                    ]
                  }
                }
              },
              "additionalProperties": false
            }
          ]
        }
      }
    },
    "additionalProperties": false
  }
```
```javascript
json = {
  "properties": {
    "txt": {
      "type": "string",
      "minLength": 3,
      "maxLength": 7
    },
    "int": {
      "type": "number",
      "minimum": 3,
      "maximum": 7
    }
  }
};
for (var _i = 0, _a = Object.entries(json.properties); _i < _a.length; _i++) {
  var key = _a[_i][0];
  var parentNode = document.getElementById("app");
  var input = document.createElement("input");

  if (json.properties[key].type === "string") {
    input.type = "text";
  } else {
    input.type = json.properties[key].type;
  }

  if (json.properties[key].minLength) {
    input.minLength = json.properties[key].minLength;
  }
  if (json.properties[key].maxLength) {
    input.maxLength = json.properties[key].maxLength;
  }
  if (json.properties[key].minimum) {
    input.min = json.properties[key].minimum;
  }
  if (json.properties[key].maximum) {
    input.max = json.properties[key].maximum;
  }
  if (json.properties[key].pattern) {
    input.pattern = json.properties[key].pattern;
  }
  parentNode.appendChild(input);
}
```

Plan jest taki, że nie ma planu. \
Zamiast tworzyć cokolwiek, przeglądarka pobiera kilka funkcji o nazwach 
city, monster … \
W zależności od nazwy tablicy, wykonuje jedną z funkcji. W ten sposób mogę 
stworzyć praktycznie nieograniczony świat, z dwoma podstawowymi uprawnieniami 
'read' tworzy poszczególne strony, za pomocą edytora (który pobiera informacje o 
polach które ma wyświetlić z pliku JSON Schema) ale nie może tworzyć nowych 
obiektów. Za to 'write' ręcznie tworzy nowe pliki JSON Schema oraz funkcje, które 
przetworzą wynik. \
Można więc uznać, że nic się nie zmienia ale dzięki ultra elastycznej 
architekturze mogę pozwolić administratorom na dodawanie nowych miast 
bez obaw, że coś zepsują. 

Możliwe, że w wersji produkcyjnej przetworzony kod XHTML zostanie zapisany 
bezpośrednio w IndexedDB. Możliwe że powstanie rozszerzenie w postaci 
widgetów, możliwsze że największym problemem tego systemu będzie dysk twardy. 
Możliwe że po początkowym sukcesie 
projekt upadnie przez brak systemu wtyczek. Być może administratorzy powinni 
mieć możliwość edycji wzorów bezpośrednio z panelu administratora, a być może 
zwykli gracze powinni mieć możliwość proponowania zmian na forum.\
Sama strona zmieści się w 1MB ale bazy danych (fora, wiadomości, strony profilowe) 
zajmą kilka GB. Serwer statystyczny będzie najbardziej obciążoną częścią systemu 
ale nie powinno to mieć żadnego znaczenia.
