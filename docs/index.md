# Billingo API v2 Usage

Current version: **2.1**

## API URL

This API enables subscribers of Billingo to connect third-party applications (ie. their e-commerce site)
and generate electronic or traditional invoices automatically.

The Billingo API is available at the following URL: `https://www.billingo.hu/api`

## Libraries

We are working hard on providing easy to use libraries for different languages and frameworks.


### Billingo API Connector

- Packagist: [https://packagist.org/packages/voov/billingo-api-connector](https://packagist.org/packages/voov/billingo-api-connector)
- GitHub: [https://github.com/voov/Billingo-API-Connector](https://github.com/voov/Billingo-API-Connector)

Built on top of Guzzle and the Firebase JWT library, it provides you an easy to use PHP library to connect to the Billingo API services.

### Billingo Connector for Laravel

- Packagist: [https://packagist.org/packages/voov/billingo-api-laravel](https://packagist.org/packages/voov/billingo-api-laravel)
- GitHub: [https://github.com/voov/Billingo-API-Laravel](https://github.com/voov/Billingo-API-Laravel)

A service provider and facade for the Laravel Framework 5+

### Billingo for WooCommerce

- WordPress Plugin Directory: [https://wordpress.org/plugins/billingo/](https://wordpress.org/plugins/billingo/)

Create and send your invoices directly from WooCommerce with the help of this plugin.

<u>Our libraries are available under the permissive MIT license:</u>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

*THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.*

## Third-party libraries

Libraries created by third parties.

### Billingo Node.JS

- GitHub: [https://github.com/ghostmonitor/node-billingo](https://github.com/ghostmonitor/node-billingo)

Created by [GhostMonitor.com](https://ghostmonitor.com/)



## JSON Schema

We are using [JSON Schema](http://json-schema.org/) (draft v4.) which describe the JSON objects you should send with
`POST` and `PUT` requests.
The link to the schemas are found below, at their appropriate places.



## Successful responses

When a request is successful, the response is always a JSON object. Every response contains a `success` attribute which
can be either `true` or `false`.

- `GET`, `POST`, `PUT` requests:
    - `type`: The type name for the response, for example a call on `/clients` will return `clients`
    - `data`: An array with the response object(s)
- `DELETE` request only contains `success` attribute.


## Errors

Besides the HTTP error code, we return a JSON object in the response body with the
following attributes:

- `success`: always `false` on error
- `error`: Textual representation of the error

If failing to insert or update objects (when JSON schema is otherwise valid), we
also return a `errors` array with the failures.
