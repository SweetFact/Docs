---
title: API SweetFact

language_tabs: # must be one of https://git.io/vQNgJ
  - json
  - shell
  - php
  - java
  - python
  - ruby
  - csharp
  - vb
  - javascript
  - swift
 

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introducción

Este documento describe la integración al API de facturación <a href="https://www.sweetfact.com" target="_blank"><strong>SweetFact.com</strong></a>

Para poder hacer uso del API es necesario verificar que tu cuenta tenga el API activado ingresa al portal de SweetFact.com, después verifica que la empresa seleccionada sea la que deseas conectar al API, dirígete a Menú > API > Datos de acceso. Allí podrás verificar que cuentes con el API Activa también encontrarás las credenciales necesarias para poder comenzar a timbrar.

# Entorno de sandbox

El entorno de sandbox te servirá para hacer testeo antes de entrar a modo producción. Es necesario solicitar el acceso enviando un correo a soporte@sweetfact.com / soporte@crystalsoft.com.mx con el asunto "Acceso a Prueba SweetFact", en caso de no contar con él.

Para el entorno de prueba es necesario ingresar el <strong>API-KEY, SECRET-KEY y HOST </strong> proporcinados por el departamento de soporte.

<strong>HOST:</strong> <br/>
https://api.devsweetfact.com/

# Entorno de desarrollo

El entorno de desarrollo una vez probado el sandbox es necesario cambiar las <strong>API-KEY, SECRET-KEY y HOST</strong> a las proporcionadas en la plataforma.

<strong>HOST:</strong> <br/>
https://api.sweetfact.com/

# Actualizaciones

<aside class="notice">
Las versiones 2 de CFDI dejarán de funcionar el 1 de diciembre del 2017, dejando como única versión para facturar la 3.3
</aside>


# CFDI 3.3

Aquí encontrarás todo lo relacionado a la facturación con la nueva versión de CFDI 3.3


## Facturar CFDI 3.3

> <span class="destinationMethod">POST</span> &nbsp;  https://api.sweetfact.com/api/v2/cfdi33/create

> HEADER <br>
> <span class="text-red">Content-Type:</span> application/json <br>
> <span class="text-red">F-API-KEY:</span> Api_Key <br>
> <span class="text-red">F-SECRET-KEY:</span> Secret_Key

```json
+ Request (application/json)

    + Headers

            F-API-KEY: Api_Key
            F-SECRET-KEY: Secret_Key
    
    + body

            {
              "Receptor": {
               "UID": "2093208989d99i3",
               "ResidenciaFiscal": "USA",
              },
              "TipoDocumento":"factura",
              "Conceptos": [{
                "ClaveProdServ":"93151502",
                "NoIdentificacion": "SKU-24364",
                "Cantidad":10,
                "ClaveUnidad":"E48",
                "Unidad":"Unidad de servicio",
                "ValorUnitario":1500,
                "Descripcion":"Diseño de aplicaciones móviles",
                "Descuento":0,
                "Impuestos":{
                  "Traslados":[{"Base" : 15000, "Impuesto": "002", "TipoFactor": "Tasa", "TasaOCuota": 0.16, "Importe": 2400}],
                  "Retenidos":[{"Base" : 15000, "Impuesto": "001", "TipoFactor": "Tasa", "TasaOCuota": 0.10, "Importe": 1500}],
                },
                "Aduana":"06 27 4609 0004321",
                "Predial":"219845327ee",
                }],
              "UsoCFDI": "G03",
              "Serie":"453",
              "Sucursal":"432"
              "FormaPago":"03",
              "MetodoPago": "PUE",
              "CondicionesDePago": "Pago en 20 dias",
              "CfdiRelacionados": {
              "TipoRelacion": "04",
                "UUID": [
                 "UUID",
                 "UUD"
                ]
              },
              "Moneda": "MXN",
              "TipoCambio": 19.89,
              "NumOrder": "MI-Orden-90",
              "FechaFromAPI": "2018-05-10T10:05:51",
              "Comentarios": "Comentarios para agregar a la factura PDF",
              "EnviarCorreo": true
            }

```
```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "https://api.sweetfact.com/api/v2/cfdi33/create");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_POST, TRUE);

curl_setopt($ch, CURLOPT_POSTFIELDS, {
  \"Receptor\": {
   \"UID\": \"2093208989d99i3\",
   \"ResidenciaFiscal\": \"USA\",
  },
  \"TipoDocumento\":\"factura\",
  \"Conceptos\": [{
    \"ClaveProdServ\":\"93151502\",
    \"NoIdentificacion\": \"SKU-24364\",
    \"Cantidad\":10,
    \"ClaveUnidad\":\"E48\",
    \"Unidad\":\"Unidad de servicio\",
    \"ValorUnitario\":1500,
    \"Descripcion\":\"Diseño de aplicaciones móviles\",
    \"Descuento\":0,
    \"Impuestos\":{
      \"Traslados\":[{\"Base\" : 15000, \"Impuesto\": \"002\", \"TipoFactor\": \"Tasa\", \"TasaOCuota\": 0.16, \"Importe\": 2400}],
      \"Retenidos\":[{\"Base\" : 15000, \"Impuesto\": \"001\", \"TipoFactor\": \"Tasa\", \"TasaOCuota\": 0.10, \"Importe\": 1500}],
    },
    \"Aduana\":\"06 27 4609 0004321\",
    \"Predial\":\"219845327ee\",
    }],
  \"UsoCFDI\": \"G03\",
  \"Serie\":\"453\",
  \"Sucursal\":\"432\"
  \"FormaPago\":\"03\",
  \"MetodoPago\": \"PUE\",
  \"CondicionesDePago\": \"Pago en 20 dias\",
  \"CfdiRelacionados\": {
  \"TipoRelacion\": \"04\",
    \"UUID\": [
     \"UUID\",
     \"UUD\"
    ]
  },
  \"Moneda\": \"MXN\",
  \"TipoCambio\": 19.89,
  \"NumOrder\": \"MI-Orden-90\",
  \"FechaFromAPI\": \"2018-05-10T10:05:51\",
  \"Comentarios\": \"Comentarios para agregar a la factura PDF\",
  \"EnviarCorreo\": true
});

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Content-Type: application/json",
  "F-API-KEY: Api_Key",
  "F-SECRET-KEY: Secret_Key"
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```ruby
require 'rubygems' if RUBY_VERSION < '1.9'
require 'rest_client'

values = {
  "Receptor": {
   "UID": "2093208989d99i3",
   "ResidenciaFiscal": "USA",
  },
  "TipoDocumento":"factura",
  "Conceptos": [{
    "ClaveProdServ":"93151502",
    "NoIdentificacion": "SKU-24364",
    "Cantidad":10,
    "ClaveUnidad":"E48",
    "Unidad":"Unidad de servicio",
    "ValorUnitario":1500,
    "Descripcion":"Diseño de aplicaciones móviles",
    "Descuento":0,
    "Impuestos":{
      "Traslados":[{"Base" : 15000, "Impuesto": "002", "TipoFactor": "Tasa", "TasaOCuota": 0.16, "Importe": 2400}],
      "Retenidos":[{"Base" : 15000, "Impuesto": "001", "TipoFactor": "Tasa", "TasaOCuota": 0.10, "Importe": 1500}],
    },
    "Aduana":"06 27 4609 0004321",
    "Predial":"219845327ee",
    }],
  "UsoCFDI": "G03",
  "Serie":"453",
  "Sucursal":"432"
  "FormaPago":"03",
  "MetodoPago": "PUE",
  "CondicionesDePago": "Pago en 20 dias",
  "CfdiRelacionados": {
  "TipoRelacion": "04",
    "UUID": [
     "UUID",
     "UUD"
    ]
  },
  "Moneda": "MXN",
  "TipoCambio": 19.89,
  "NumOrder": "MI-Orden-90",
  "FechaFromAPI": "2018-05-10T10:05:51",
  "Comentarios": "Comentarios para agregar a la factura PDF",
  "EnviarCorreo": true
}

headers = {
  :content_type => 'application/json',
  :f_api_key => 'Api_Key',
  :f_secret_key => 'Secret_Key'
}

response = RestClient.post 'https://api.sweetfact.com/api/v2/cfdi33/create', values, headers
puts response
```

```java
// Maven : Add these dependecies to your pom.xml (java6+)
// <dependency>
//     <groupId>org.glassfish.jersey.core</groupId>
//     <artifactId>jersey-client</artifactId>
//     <version>2.8</version>
// </dependency>
// <dependency>
//     <groupId>org.glassfish.jersey.media</groupId>
//     <artifactId>jersey-media-json-jackson</artifactId>
//     <version>2.8</version>
// </dependency>

import javax.ws.rs.client.Client;
import javax.ws.rs.client.ClientBuilder;
import javax.ws.rs.client.Entity;
import javax.ws.rs.core.Response;
import javax.ws.rs.core.MediaType;

Client client = ClientBuilder.newClient();
Entity payload = Entity.json("{
  \"Receptor\": {
   \"UID\": \"2093208989d99i3\",
   \"ResidenciaFiscal\": \"USA\",
  },
  \"TipoDocumento\":\"factura\",
  \"Conceptos\": [{
    \"ClaveProdServ\":\"93151502\",
    \"NoIdentificacion\": \"SKU-24364\",
    \"Cantidad\":10,
    \"ClaveUnidad\":\"E48\",
    \"Unidad\":\"Unidad de servicio\",
    \"ValorUnitario\":1500,
    \"Descripcion\":\"Diseño de aplicaciones móviles\",
    \"Descuento\":0,
    \"Impuestos\":{
      \"Traslados\":[{\"Base\" : 15000, \"Impuesto\": \"002\", \"TipoFactor\": \"Tasa\", \"TasaOCuota\": 0.16, \"Importe\": 2400}],
      \"Retenidos\":[{\"Base\" : 15000, \"Impuesto\": \"001\", \"TipoFactor\": \"Tasa\", \"TasaOCuota\": 0.10, \"Importe\": 1500}],
    },
    \"Aduana\":\"06 27 4609 0004321\",
    \"Predial\":\"219845327ee\",
    }],
  \"UsoCFDI\": \"G03\",
  \"Serie\":\"453\",
  \"Sucursal\":\"432\"
  \"FormaPago\":\"03\",
  \"MetodoPago\": \"PUE\",
  \"CondicionesDePago\": \"Pago en 20 dias\",
  \"CfdiRelacionados\": {
  \"TipoRelacion\": \"04\",
    \"UUID\": [
     \"UUID\",
     \"UUD\"
    ]
  },
  \"Moneda\": \"MXN\",
  \"TipoCambio\": 19.89,
  \"NumOrder\": \"MI-Orden-90\",
  \"FechaFromAPI\": \"2018-05-10T10:05:51\",
  \"Comentarios\": \"Comentarios para agregar a la factura PDF\",
  \"EnviarCorreo\": true
}");
Response response = client.target("https://api.sweetfact.com/api/v2/cfdi33/create")
  .request(MediaType.APPLICATION_JSON_TYPE)
  .header("F-API-KEY", "Api_Key")
  .header("F-SECRET-KEY", "Secret_Key")
  .post(payload);

System.out.println("status: " + response.getStatus());
System.out.println("headers: " + response.getHeaders());
System.out.println("body:" + response.readEntity(String.class));
```

```python
from urllib2 import Request, urlopen

values = """
{
  "Receptor": {
   "UID": "2093208989d99i3",
   "ResidenciaFiscal": "USA",
  },
  "TipoDocumento":"factura",
  "Conceptos": [{
    "ClaveProdServ":"93151502",
    "NoIdentificacion": "SKU-24364",
    "Cantidad":10,
    "ClaveUnidad":"E48",
    "Unidad":"Unidad de servicio",
    "ValorUnitario":1500,
    "Descripcion":"Diseño de aplicaciones móviles",
    "Descuento":0,
    "Impuestos":{
      "Traslados":[{"Base" : 15000, "Impuesto": "002", "TipoFactor": "Tasa", "TasaOCuota": 0.16, "Importe": 2400}],
      "Retenidos":[{"Base" : 15000, "Impuesto": "001", "TipoFactor": "Tasa", "TasaOCuota": 0.10, "Importe": 1500}],
    },
    "Aduana":"06 27 4609 0004321",
    "Predial":"219845327ee",
    }],
  "UsoCFDI": "G03",
  "Serie":"453",
  "Sucursal":"432"
  "FormaPago":"03",
  "MetodoPago": "PUE",
  "CondicionesDePago": "Pago en 20 dias",
  "CfdiRelacionados": {
  "TipoRelacion": "04",
    "UUID": [
     "UUID",
     "UUD"
    ]
  },
  "Moneda": "MXN",
  "TipoCambio": 19.89,
  "NumOrder": "MI-Orden-90",
  "FechaFromAPI": "2018-05-10T10:05:51",
  "Comentarios": "Comentarios para agregar a la factura PDF",
  "EnviarCorreo": true
}"""

headers = {
  'Content-Type': 'application/json',
  'F-API-KEY': 'Api_Key',
  'F-SECRET-KEY': 'Secret_Key'
}
request = Request('https://api.sweetfact.com/api/v2/cfdi33/create', data=values, headers=headers)

response_body = urlopen(request).read()
print response_body
```

```csharp
//Common testing requirement. If you are consuming an API in a sandbox/test region, uncomment this line of code ONLY for non production uses.
//System.Net.ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };

//Be sure to run "Install-Package Microsoft.Net.Http" from your nuget command line.
using System;
using System.Net.Http;

var baseAddress = new Uri("https://api.sweetfact.com/");

using (var httpClient = new HttpClient{ BaseAddress = baseAddress })
{

  
  httpClient.DefaultRequestHeaders.TryAddWithoutValidation("f-api-key", "Api_Key");
  
  httpClient.DefaultRequestHeaders.TryAddWithoutValidation("f-secret-key", "Secret_Key");
  
    using (var content = new StringContent("{
  \"Receptor\": {
   \"UID\": \"2093208989d99i3\",
   \"ResidenciaFiscal\": \"USA\",
  },
  \"TipoDocumento\":\"factura\",
  \"Conceptos\": [{
    \"ClaveProdServ\":\"93151502\",
    \"NoIdentificacion\": \"SKU-24364\",
    \"Cantidad\":10,
    \"ClaveUnidad\":\"E48\",
    \"Unidad\":\"Unidad de servicio\",
    \"ValorUnitario\":1500,
    \"Descripcion\":\"Diseño de aplicaciones móviles\",
    \"Descuento\":0,
    \"Impuestos\":{
      \"Traslados\":[{\"Base\" : 15000, \"Impuesto\": \"002\", \"TipoFactor\": \"Tasa\", \"TasaOCuota\": 0.16, \"Importe\": 2400}],
      \"Retenidos\":[{\"Base\" : 15000, \"Impuesto\": \"001\", \"TipoFactor\": \"Tasa\", \"TasaOCuota\": 0.10, \"Importe\": 1500}],
    },
    \"Aduana\":\"06 27 4609 0004321\",
    \"Predial\":\"219845327ee\",
    }],
  \"UsoCFDI\": \"G03\",
  \"Serie\":\"453\",
  \"Sucursal\":\"432\"
  \"FormaPago\":\"03\",
  \"MetodoPago\": \"PUE\",
  \"CondicionesDePago\": \"Pago en 20 dias\",
  \"CfdiRelacionados\": {
  \"TipoRelacion\": \"04\",
    \"UUID\": [
     \"UUID\",
     \"UUD\"
    ]
  },
  \"Moneda\": \"MXN\",
  \"TipoCambio\": 19.89,
  \"NumOrder\": \"MI-Orden-90\",
  \"FechaFromAPI\": \"2018-05-10T10:05:51\",
  \"Comentarios\": \"Comentarios para agregar a la factura PDF\",
  \"EnviarCorreo\": true
}", System.Text.Encoding.Default, "application/json"))
    {
      using (var response = await httpClient.PostAsync("api/v2/cfdi33/create", content))
      {
        string responseData = await response.Content.ReadAsStringAsync();
      }
  }
}
```


```shell
curl --include \
     --request POST \
     --header "Content-Type: application/json" \
     --header "F-API-KEY: Api_Key" \
     --header "F-SECRET-KEY: Secret_Key" \
     --data-binary "{
  \"Receptor\": {
   \"UID\": \"2093208989d99i3\",
   \"ResidenciaFiscal\": \"USA\",
  },
  \"TipoDocumento\":\"factura\",
  \"Conceptos\": [{
    \"ClaveProdServ\":\"93151502\",
    \"NoIdentificacion\": \"SKU-24364\",
    \"Cantidad\":10,
    \"ClaveUnidad\":\"E48\",
    \"Unidad\":\"Unidad de servicio\",
    \"ValorUnitario\":1500,
    \"Descripcion\":\"Diseño de aplicaciones móviles\",
    \"Descuento\":0,
    \"Impuestos\":{
      \"Traslados\":[{\"Base\" : 15000, \"Impuesto\": \"002\", \"TipoFactor\": \"Tasa\", \"TasaOCuota\": 0.16, \"Importe\": 2400}],
      \"Retenidos\":[{\"Base\" : 15000, \"Impuesto\": \"001\", \"TipoFactor\": \"Tasa\", \"TasaOCuota\": 0.10, \"Importe\": 1500}],
    },
    \"Aduana\":\"06 27 4609 0004321\",
    \"Predial\":\"219845327ee\",
    }],
  \"UsoCFDI\": \"G03\",
  \"Serie\":\"453\",
  \"Sucursal\":\"432\"
  \"FormaPago\":\"03\",
  \"MetodoPago\": \"PUE\",
  \"CondicionesDePago\": \"Pago en 20 dias\",
  \"CfdiRelacionados\": {
  \"TipoRelacion\": \"04\",
    \"UUID\": [
     \"UUID\",
     \"UUD\"
    ]
  },
  \"Moneda\": \"MXN\",
  \"TipoCambio\": 19.89,
  \"NumOrder\": \"MI-Orden-90\",
  \"FechaFromAPI\": \"2018-05-10T10:05:51\",
  \"Comentarios\": \"Comentarios para agregar a la factura PDF\",
  \"EnviarCorreo\": true
}" \
'https://api.sweetfact.com/api/v2/cfdi33/create'
```

```javascript
var request = new XMLHttpRequest();

request.open('POST', 'https://api.sweetfact.com/api/v2/cfdi33/create');

request.setRequestHeader('Content-Type', 'application/json');
request.setRequestHeader('F-API-KEY', 'Api_Key');
request.setRequestHeader('F-SECRET-KEY', 'Secret_Key');

request.onreadystatechange = function () {
  if (this.readyState === 4) {
    console.log('Status:', this.status);
    console.log('Headers:', this.getAllResponseHeaders());
    console.log('Body:', this.responseText);
  }
};

var body = {
  'Receptor': {
   'UID': '2093208989d99i3',
   'ResidenciaFiscal': 'USA',
  },
  'TipoDocumento':'factura',
  'Conceptos': [{
    'ClaveProdServ':'93151502',
    'NoIdentificacion': 'SKU-24364',
    'Cantidad':10,
    'ClaveUnidad':'E48',
    'Unidad':'Unidad de servicio',
    'ValorUnitario':1500,
    'Descripcion':'Diseño de aplicaciones móviles',
    'Descuento':0,
    'Impuestos':{
      'Traslados':[{'Base' : 15000, 'Impuesto': '002', 'TipoFactor': 'Tasa', 'TasaOCuota': 0.16, 'Importe': 2400}],
      'Retenidos':[{'Base' : 15000, 'Impuesto': '001', 'TipoFactor': 'Tasa', 'TasaOCuota': 0.10, 'Importe': 1500}],
    },
    'Aduana':'06 27 4609 0004321',
    'Predial':'219845327ee',
    }],
  'UsoCFDI': 'G03',
  'Serie':'453',
  'Sucursal':'432'
  'FormaPago':'03',
  'MetodoPago': 'PUE',
  'CondicionesDePago': 'Pago en 20 dias',
  'CfdiRelacionados': {
  'TipoRelacion': '04',
    'UUID': [
     'UUID',
     'UUD'
    ]
  },
  'Moneda': 'MXN',
  'TipoCambio': 19.89,
  'NumOrder': 'MI-Orden-90',
  'FechaFromAPI': '2018-05-10T10:05:51',
  'Comentarios': 'Comentarios para agregar a la factura PDF',
  'EnviarCorreo': true
};

request.send(JSON.stringify(body));
```

```swift
import Foundation

// NOTE: Uncommment following two lines for use in a Playground
// import PlaygroundSupport
// PlaygroundPage.current.needsIndefiniteExecution = true

let url = URL(string: "https://api.sweetfact.com/api/v2/cfdi33/create")!
var request = URLRequest(url: url)
request.httpMethod = "POST"
request.addValue("application/json", forHTTPHeaderField: "Content-Type")
request.addValue("Api_Key", forHTTPHeaderField: "F-API-KEY")
request.addValue("Secret_Key", forHTTPHeaderField: "F-SECRET-KEY")

request.httpBody = """
{
  \"Receptor\": {
   \"UID\": \"2093208989d99i3\",
   \"ResidenciaFiscal\": \"USA\",
  },
  \"TipoDocumento\":\"factura\",
  \"Conceptos\": [{
    \"ClaveProdServ\":\"93151502\",
    \"NoIdentificacion\": \"SKU-24364\",
    \"Cantidad\":10,
    \"ClaveUnidad\":\"E48\",
    \"Unidad\":\"Unidad de servicio\",
    \"ValorUnitario\":1500,
    \"Descripcion\":\"Diseño de aplicaciones móviles\",
    \"Descuento\":0,
    \"Impuestos\":{
      \"Traslados\":[{\"Base\" : 15000, \"Impuesto\": \"002\", \"TipoFactor\": \"Tasa\", \"TasaOCuota\": 0.16, \"Importe\": 2400}],
      \"Retenidos\":[{\"Base\" : 15000, \"Impuesto\": \"001\", \"TipoFactor\": \"Tasa\", \"TasaOCuota\": 0.10, \"Importe\": 1500}],
    },
    \"Aduana\":\"06 27 4609 0004321\",
    \"Predial\":\"219845327ee\",
    }],
  \"UsoCFDI\": \"G03\",
  \"Serie\":\"453\",
  \"Sucursal\":\"432\"
  \"FormaPago\":\"03\",
  \"MetodoPago\": \"PUE\",
  \"CondicionesDePago\": \"Pago en 20 dias\",
  \"CfdiRelacionados\": {
  \"TipoRelacion\": \"04\",
    \"UUID\": [
     \"UUID\",
     \"UUD\"
    ]
  },
  \"Moneda\": \"MXN\",
  \"TipoCambio\": 19.89,
  \"NumOrder\": \"MI-Orden-90\",
  \"FechaFromAPI\": \"2018-05-10T10:05:51\",
  \"Comentarios\": \"Comentarios para agregar a la factura PDF\",
  \"EnviarCorreo\": true
}
""".data(using: .utf8)

let task = URLSession.shared.dataTask(with: request) { data, response, error in
  if let response = response {
    print(response)

    if let data = data, let body = String(data: data, encoding: .utf8) {
      print(body)
    }
  } else {
    print(error ?? "Unknown error")
  }
}

task.resume()
```

```vb
Dim request = TryCast(System.Net.WebRequest.Create("https://api.sweetfact.com/api/v2/cfdi33/create"), System.Net.HttpWebRequest)

request.Method = "POST"

request.ContentType = "application/json"
request.Headers.Add("f-api-key", "Api_Key")
request.Headers.Add("f-secret-key", "Secret_Key")

Using writer = New System.IO.StreamWriter(request.GetRequestStream())
  Dim byteArray As Byte() = System.Text.Encoding.UTF8.GetBytes("
  \""Receptor\"": {
   \""UID\"": \""2093208989d99i3\"",
   \""ResidenciaFiscal\"": \""USA\"",
  },
  \""TipoDocumento\"":\""factura\"",
  \""Conceptos\"": [{
    \""ClaveProdServ\"":\""93151502\"",
    \""NoIdentificacion\"": \""SKU-24364\"",
    \""Cantidad\"":10,
    \""ClaveUnidad\"":\""E48\"",
    \""Unidad\"":\""Unidad de servicio\"",
    \""ValorUnitario\"":1500,
    \""Descripcion\"":\""Diseño de aplicaciones móviles\"",
    \""Descuento\"":0,
    \""Impuestos\"":{
      \""Traslados\"":[{\""Base\"" : 15000, \""Impuesto\"": \""002\"", \""TipoFactor\"": \""Tasa\"", \""TasaOCuota\"": 0.16, \""Importe\"": 2400}],
      \""Retenidos\"":[{\""Base\"" : 15000, \""Impuesto\"": \""001\"", \""TipoFactor\"": \""Tasa\"", \""TasaOCuota\"": 0.10, \""Importe\"": 1500}],
    },
    \""Aduana\"":\""06 27 4609 0004321\"",
    \""Predial\"":\""219845327ee\"",
    }],
  \""UsoCFDI\"": \""G03\"",
  \""Serie\"":\""453\"",
  \""Sucursal\"":\""432\""
  \""FormaPago\"":\""03\"",
  \""MetodoPago\"": \""PUE\"",
  \""CondicionesDePago\"": \""Pago en 20 dias\"",
  \""CfdiRelacionados\"": {
  \""TipoRelacion\"": \""04\"",
    \""UUID\"": [
     \""UUID\"",
     \""UUD\""
    ]
  },
  \""Moneda\"": \""MXN\"",
  \""TipoCambio\"": 19.89,
  \""NumOrder\"": \""MI-Orden-90\"",
  \""FechaFromAPI\"": \""2018-05-10T10:05:51\"",
  \""Comentarios\"": \""Comentarios para agregar a la factura PDF\"",
  \""EnviarCorreo\"": true
")
  request.ContentLength = byteArray.Length
  writer.Write(byteArray)
  writer.Close()
End Using
Dim responseContent As String
Using response = TryCast(request.GetResponse(), System.Net.HttpWebResponse)
  Using reader = New System.IO.StreamReader(response.GetResponseStream())
    responseContent = reader.ReadToEnd()
  End Using
End Using
```

> Response
```json
200

HEADERS

Content-Type:application/json

BODY
   {
        "status": "success",
        "data": {
            "cadenaOriginalSAT": "||1.1|c63f363b-ad50-40ec-a49c-246e4564fdcf|2018-04-18T21:59:53|AAA010101AAA|MdMcZIC24voTzTqdWDFyoTFnhwWsrompQ2CRXLhvbfFKVAc1VUf/2He/TLoYFOhdGvEaU352tHmZr3sadZkPKzUF9gg/udKdZHauWEaTBCAK4JpBUS2E4yBQhBJ9iOkbT/Y8UummoQhMtvFO2T6N3jWNtvRx+3gejo3iSMp9F78yAycXIz8i4JsSg2QwvvdWuOU6sWWniRsAZsMKtSEDFQTsbJB3pNoLoeZDVs9H3kdfGlye96KI6kqkd9cqWYwX7FUoBxoYenscB8kSq0kD8odGi8E/S/RKAZ3GEefY57IB2WPWcqfO1+sWcxGVPMmOwmELfa5jOuVigov7IB7EXQ==|20001000000300022323||",
            "noCertificadoSAT": 20001000000300000000,
            "noCertificadoCFDI": 1000000408234001,
            "uuid": "c63f363b-ad50-40ec-a49c-246e4564fdcf",
            "selloSAT": "SCj+LGCAYHs52v9tcMmZsBGCVxjoTI17RalR83YlGG64QilypOqIHtvHeWIrLIJrchItwPzOAdfB9TPaVivKufu7KycpOE31bwm/jrLwyOPdC2LVmMr9F/QTBi5GnhP7YAIcs3nR7p7aaH2euyB4RgwKnVnLQ/3MJr8FVaSaFGlK6xl35DNxjccud8jaTL/15+KOYLSiIyUWV6kVIGN2ChvJKenHuEkl1p/ZT5wFph5RuR274VLRbGfMwxf6tkFV+759uZ1lKa2g4+SpHr2Gz3QCsH6NFvf8ZsPHOkEuWu0K2ZkvmnZu3rrLLpX4HbaweyFth0x20plCdmlgmcXR6g==",
            "selloCFDI": "MdMcZIC24voTzTqdWDFyoTFnhwWsrompQ2CRXLhvbfFKVAc1VUf/2He/TLoYFOhdGvEaU352tHmZr3sadZkPKzUF9gg/udKdZHauWEaTBCAK4JpBUS2E4yBQhBJ9iOkbT/Y8UummoQhMtvFO2T6N3jWNtvRx+3gejo3iSMp9F78yAycXIz8i4JsSg2QwvvdWuOU6sWWniRsAZsMKtSEDFQTsbJB3pNoLoeZDVs9H3kdfGlye96KI6kqkd9cqWYwX7FUoBxoYenscB8kSq0kD8odGi8E/S/RKAZ3GEefY57IB2WPWcqfO1+sWcxGVPMmOwmELfa5jOuVigov7IB7EXQ==",
            "fechaTimbrado": "2018-04-18T21:59:53",
            "qrCode": png_base64,
            "cfdi": xml_base64,
            "pdfCfdi": pdf_base64,
            "serie": "F",
            "folio": 1
        }
    }
```

Método para crear un CFDI

<aside class="notice">
Es responsabilidad de cada cliente de API el mandar los valores (precios, cálculo de impuestos, subtotales, etc) de acuerdo a sus necesidades y requerimientos, tales como número de decimales o redondeo. sweetfact.com no se hace responsable por errores de timbrado que correspondan a problemas con las cantidades enviadas por los usuarios
</aside>

### Parametros necesarios

<table>
    <tbody><tr>
        <td> Parámetro </td>
        <td> Tipo </td>    
        <td> Requerido </td>    
        <td> Descripción </td>    
    </tr>
   </tbody><tbody>
        <tr>
            <td> Receptor </td>
            <td> <code>array</code> </td>    
            <td> Si </td>
            <td> Para ver los atributos que puede contener el arreglo, haz clic <a href="#Receptor">aquí</a>. </td>
        </tr>
        <tr>
            <td> TipoDocumento </td>
            <td> <code>string</code> </td>    
            <td> Si </td>
            <td> Debes enviar el tipo de documento, Consulta el catálogo <b>tipo_cfdi</b> <a href="#Tiposcfdi">aquí</a>.</td>
        </tr>
        <tr>
            <td> Conceptos </td>
            <td> <code>array of objects</code> </td>    
            <td> Si </td>
            <td> Para ver los atributos que puede contener un objeto Concepto haz clic <a href="#Conceptos">aquí</a> </td>
        </tr>
        <tr>
            <td> UsoCFDI </td>
            <td> <code>string</code> </td>    
            <td> Si </td>
            <td> Envía el valor estipulado en el catalogo <b>Uso CFDI</b>, también puedes consultarlo <a href="#Catalogos/uso-de-cfdi"> vía Rest</a>.</td>
        </tr>
        <tr>
            <td> Serie </td>
            <td> <code>number</code> </td>    
            <td> Si </td>
            <td> Envía el id de la serie con la que deseas timbrar el documento. también puedes consultarlo <a href="#Series"> vía Rest</a>. </td>
        </tr>
        <tr>
            <td> FormaPago </td>
            <td> <code>string</code> </td>    
            <td> Si </td>
            <td> Envía la forma de pago, misma que puedes consultar en el catalogo <b>Forma Pago</b>, también puedes consultarlo <a href="#Catalogos/formaPago"> vía Rest</a>. </td>
        </tr>
        <tr>
            <td> MetodoPago </td>
            <td> <code>string</code> </td>    
            <td> Si </td>
            <td> Envía el método de pago, mismo que puedes consultar en el catalogo <b>Metodo Pago</b>,  también puedes consultarlo <a href="#Catalogos/metodoPago"> vía Rest</a>. </td>
        </tr>
        <tr>
            <td> CondicionesDePago </td>
            <td> <code>string</code> </td>    
            <td> No </td>
            <td> Enviar las condiciones de pago del CFDI, éstas deben tener una longitud minima de 1 y máxima de 1000 carácteres. </td>
        </tr>
        <tr>
            <td> CfdiRelacionados </td>
            <td> <code>array</code> </td>    
            <td> No </td>
            <td> En caso que tu CFDI vaya relacionado con otro(s), envía un arreglo con el/los UUID's con los que deseas relacionarlo.Para ver los atributos que puede contener haz clic <a href="#Relacionados">aquí</a> </td>
        </tr>
        <tr>
            <td> Moneda </td>
            <td> <code>string</code> </td>    
            <td> Si </td>
            <td> Enviar la clave de la moneda, para ello puedes utilizar catálogo de moneda: <b>Moneda</b>,  también puedes consultarlo <a href="#Catalogos/moneda"> vía Rest</a>. </td>
        </tr>
        <tr>
            <td> TipoCambio </td>
            <td> <code>string</code> </td>    
            <td> No </td>
            <td> En caso que la moneda sea diferente a MXN, indicar el tipo de cambio de la moneda seleccionada. </td>
        </tr>
        <tr>
            <td> NumOrder </td>
            <td> <code>number</code> </td>    
            <td> No </td>
            <td> Número de orden, su función es únicamente para control interno.   </td>
        </tr>
        <tr>
            <td> FechaFromAPI </td>
            <td> <code>string</code> </td>    
            <td> No </td>
            <td> Enviar una fecha válida (Y-m-d\TH:m:s), recuerda que puedes enviar hasta 72 horas de atraso a la fecha actual, pero no fechas futuras.  </td>
        </tr>
        <tr>
            <td> Comentarios </td>
            <td> <code>string</code> </td>    
            <td> No </td>
            <td> Enviar comentarios que solo se agregarán a la factura PDF. </td>
        </tr>
        <tr>
            <td> Cuenta </td>
            <td> <code>string</code> </td>    
            <td> No </td>
            <td> Enviar los últimos 4 dijitos de la tarjeta o cuenta de banco del cliente. </td>
        </tr>
        <tr>
            <td> EnviarCorreo </td>
            <td> <code>bolean</code> </td>    
            <td> No </td>
            <td> Enviar true si deseas que se envíe en automático la factura a tu cliente por correo electrónico. </td>
        </tr>
        <tr>
            <td> Sucursal </td>
            <td> <code>string</code> </td>    
            <td> No </td>
            <td> Enviar el idEmpresaSucursal de la sucursal en la cual quieren expedir el CFDI [si no se envia se toma la dirección de la matriz] también puedes consultarlo <a href="#Sucursales"> vía Rest</a>. </td>
        </tr>
</tbody>
</table>

### Tipos de CFDI

<table>
    <thead>
        <tr>
            <td> Clave </td>
            <td> Tipo de CFDI </td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td> factura </td>
            <td> Factura </td> 
        </tr>
        <tr>
            <td> factura_hotel </td>
            <td> Factura para hoteles </td> 
        </tr>
        <tr>
            <td> honorarios </td>
            <td> Recibo de honorarios </td> 
        </tr>
        <tr>
            <td> nota_cargo </td>
            <td> Nota de cargo </td> 
        </tr>
        <tr>
            <td> donativo </td>
            <td> Donativo </td> 
        </tr>
        <tr>
            <td> arrendamiento </td>
            <td> Recibo de arrendamiento </td> 
        </tr>
        <tr>
            <td> nota_credito </td>
            <td> Nota de crédito </td> 
        </tr>
         <tr>
            <td> nota_devolucion </td>
            <td> Nota de devolución </td> 
        </tr>
        <tr>
            <td> carta_porte </td>
            <td> Carta porte </td> 
        </tr>
    </tbody>
</table>

### Atributos del receptor

<table>
    <thead>
        <tr>
            <td> Parámetro </td>
            <td> Tipo </td>
            <td> Requerido </td>   
            <td> Observaciones </td> 
        </tr>
    </thead>
    <tbody>
        <tr>
            <td> UID </td>
            <td> <code>string</code> </td>   
            <td> Si </td>
            <td> Envía el UID del cliente el cual debe estar en el catálogo de clientes, de lo contrario deberás crearlo antes para poder crearle un documento. <a href="#reference/clientes/crear-cliente">ver cómo crear un cliente.</a>  </td>
        </tr>
        <tr>
            <td> ResidenciaFiscal </td>
            <td> <code>string</code> </td>   
            <td> No </td>
            <td> Se debe registrar cuando el receptor del comprobante sea un residente en el extranjero. </td>
        </tr>
    </tbody>
</table>

### Atributos de cada concepto

<table>
    <thead>
        <tr>
            <td> Parámetro </td>
            <td> Tipo </td>
            <td> Requerido </td>   
            <td> Observaciones </td> 
        </tr>
    </thead>
    <tbody>
        <tr>
            <td> ClaveProdServ </td>
            <td> <code>string</code> </td>   
            <td> Si </td>
            <td> Indica la clave del producto o servicio correspondiete a tu concepto, puedes consultar el catálogo <b>Clave Producto Servicio</b>. <a href="#Catalogos/claveProductoServicio">aqui</a> </td>
        </tr>
        <tr>
            <td> NoIdentificacion </td>
            <td> <code>string</code> </td>   
            <td> No </td>
            <td> Agregar el número de identificación o SKU. </td>
        </tr>
        <tr>
            <td> Cantidad </td>
            <td> <code>number</code> </td>   
            <td> Si </td>
            <td> Cantidad en número entero. </td>
        </tr>
        <tr>
            <td> ClaveUnidad </td>
            <td> <code>string</code> </td>   
            <td> Si </td>
            <td> Indica la clave de la unidad correspondiente a tu concepto, puedes consultar el catálogo <b>Clave Unidad</b>, también puedes consultarlo <a href="#Catalogos/unidadMedida"> vía Rest</a>. </td>
        </tr>
        <tr>
            <td> Unidad </td>
            <td> <code>string</code> </td>   
            <td> Si </td>
            <td> Unidad de medida, ésta corresponde al nodo nombre de la ClaveUnidad elegida, puedes consultar el catálogo <b>Clave Unidad</b>,  también puedes consultarlo <a href="#Catalogos/unidadMedida"> vía Rest</a>. </td>
        </tr>
        <tr>
            <td> ValorUnitario </td>
            <td> <code>float</code> </td>   
            <td> Si </td>
            <td>  Precio Unitario (sin IVA). </td>
        </tr>
        <tr>
            <td> Descripcion </td>
            <td> <code>string</code> </td>   
            <td> Si </td>
            <td> Descripción del concepto. </td>
        </tr>
        <tr>
            <td> Descuento </td>
            <td> <code>string</code> </td>   
            <td> No </td>
            <td> Enviar parámetro sólo si se desea agregar descuento.  </td>
        </tr>
        <tr>
            <td> Impuestos </td>
            <td> <code>objects of arrays</code> </td>   
            <td> No </td>
            <td> Para ver los atributos que puede contener el objeto impuestos haz clic <a href="#Impuestos">aquí</a>  </td>
        </tr>
        <tr>
            <td> Aduana </td>
            <td> <code>string</code> </td>   
            <td> No </td>
            <td> Se debe registrar el número del pedimento correspondiente a la importación del bien, ejemplo: 12  34  3046  0004321  </td>
        </tr>
        <tr>
            <td> Predial </td>
            <td> <code>string</code> </td>   
            <td> No </td>
            <td> Se debe registrar el número de predial.  </td>
        </tr>
    </tbody>
</table>

### Atributos de CfdiRelacionados

<table>
    <thead>
        <tr>
            <td> Parámetro </td>
            <td> Tipo </td>
            <td> Requerido </td>   
            <td> Observaciones </td> 
        </tr>
    </thead>
    <tbody>
        <tr>
            <td> TipoRelacion </td>
            <td> <code>string</code> </td>   
            <td> Si, en caso de enviar el nodo CfdiRelacionado. </td>
            <td> Envíar key del tipo de relación que se vaya a utilizar.</td>
        </tr>
        <tr>
            <td> UUID </td>
            <td> <code>Array</code> </td>   
            <td> Si, en caso de enviar el nodo CfdiRelacionado. </td>
            <td> Enviar el/los UUID's de los documentos con los que desees relacionar tu CFDI. </td>
        </tr>
    </tbody>
</table>

### Atributos de Impuestos

<table>
    <thead>
        <tr>
            <td> Parámetro </td>
            <td> Tipo </td>
            <td> Requerido </td>   
            <td> Observaciones </td> 
        </tr>
    </thead>
    <tbody>
        <tr>
            <td> Traslados </td>
            <td> <code>array of objects</code> </td>   
            <td> Si </td>
            <td> Se deben registrar los impuestos trasladados del concepto, para ver los atributos que puede contener el objeto Traslados haz clic <a href="#Traslados">aquí</a>.</td>
        </tr>
        <tr>
                <td> Retenidos </td>
                <td> <code>array of objects</code> </td>   
                <td> Si </td>
                <td> Se deben registrar los impuestos retenidos del concepto, para ver los atributos que puede contener el objeto Retenidos haz clic <a href="#Retenidos">aquí</a>.</td>
        </tr>
    </tbody>
</table>

### Atributos de nodo Traslados

Dentro de los traslados puedes utilizar IVA y IEPS

<table>
    <thead>
        <tr>
            <td> Parámetro </td>
            <td> Tipo </td>
            <td> Requerido </td>   
            <td> Observaciones </td> 
        </tr>
    </thead>
    <tbody>
        <tr>
            <td> Base </td>
            <td> <code>float</code> </td>   
            <td> Si </td>
            <td> Se debe registrar el valor para el cálculo del impuesto que se traslada, puede contener de cero hasta seis decimales. <br> El valor de este campo debe ser mayor que cero.</td>
        </tr>
        <tr>
            <td> Impuesto </td>
            <td> <code>string</code> </td>   
            <td> Si </td>
            <td> Se debe registrar la clave del tipo de impuesto trasladado aplicable a cada concepto, las cuales se encuentran incluidas en el catálogo <b>Impuesto</b> publicado en el Portal del SAT,  también puedes consultarlo <a href="#Catalogos/impuestos"> vía Rest</a>.</td>
        </tr>
        <tr>
            <td> TipoFactor </td>
            <td> <code>string</code> </td>   
            <td> Si </td>
            <td> Se debe registrar el tipo de factor que se aplica a la base del impuesto, el cual se encuentra incluido en el catálogo <b>Tipo Factor</b> publicado en el Portal del SAT.</td>
        </tr>
        <tr>
            <td> TasaOCuota </td>
            <td> <code>float</code> </td>   
            <td> Si </td>
            <td> Se puede registrar el valor de la tasa o cuota del impuesto que se traslada para cada concepto. Es requerido cuando el campo TipoFactor corresponda a Tasa o Cuota. <br> Los distintos valores para las tasas o cuotas se encuentran incluidos en el catálogo <b>c_TasaOCuota</b> publicado en el Portal del SAT.</td>
        </tr>
        <tr>
            <td> Importe </td>
            <td> <code>float</code> </td>   
            <td> Si </td>
            <td> Se puede registrar el importe del impuesto trasladado que aplica a cada concepto. No se permiten valores negativos. Este campo es requerido cuando en el campo TipoFactor se haya registrado como Tasa o Cuota.</td>
        </tr>
    </tbody>
</table>

### Atributos de nodo Retenidos

Dentro de los retenidos puedes utilizar IVA e ISR

<table>
    <thead>
        <tr>
            <td> Parámetro </td>
            <td> Tipo </td>
            <td> Requerido </td>   
            <td> Observaciones </td> 
        </tr>
    </thead>
    <tbody>
        <tr>
            <td> Base </td>
            <td> <code>float</code> </td>   
            <td> Si </td>
            <td> Se debe registrar el valor para el cálculo del impuesto que se traslada, puede contener de cero hasta seis decimales. <br> El valor de este campo debe ser mayor que cero.</td>
        </tr>
        <tr>
            <td> Impuesto </td>
            <td> <code>string</code> </td>   
            <td> Si </td>
            <td> Se debe registrar la clave del tipo de impuesto trasladado aplicable a cada concepto, las cuales se encuentran incluidas en el catálogo <b>Impuesto</b> publicado en el Portal del SAT,  también puedes consultarlo <a href="#Catalogos/impuesto"> vía Rest</a>.</td>
        </tr>
        <tr>
            <td> TipoFactor </td>
            <td> <code>string</code> </td>   
            <td> Si </td>
            <td> Se debe registrar el tipo de factor que se aplica a la base del impuesto, el cual se encuentra incluido en el catálogo <b>Tipo Factor</b> publicado en el Portal del SAT.</td>
        </tr>
        <tr>
            <td> TasaOCuota </td>
            <td> <code>float</code> </td>   
            <td> Si </td>
            <td> Se puede registrar el valor de la tasa o cuota del impuesto que se retiene para cada concepto. Es requerido cuando el campo TipoFactor corresponda a Tasa o Cuota. <br> Los distintos valores para las tasas o cuotas se encuentran incluidos en el catálogo <b>c_TasaOCuota</b> publicado en el Portal del SAT.</td>
        </tr>
        <tr>
            <td> Importe </td>
            <td> <code>float</code> </td>   
            <td> Si </td>
            <td> Se puede registrar el importe del impuesto trasladado que aplica a cada concepto. No se permiten valores negativos. Este campo es requerido cuando en el campo TipoFactor se haya registrado como Tasa o Cuota.</td>
        </tr>
    </tbody>
</table>


# Kittens

## Get All Kittens

```ruby
require 'hgh'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

