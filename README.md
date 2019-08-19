Node.js api gateway to the Amazon Giftcard On Demand Web service
============

## Install
`npm install agcod`

## Configuration

This clients expects the following environment variables to be present.

- `AWS_ACCESS_KEY_ID` – Specifies an AWS access key associated with an IAM user or role.
- `AWS_SECRET_ACCESS_KEY` – Specifies the secret key associated with the access key. This is essentially the "password" for the access key.
- `AGCOD_PARTNERID` - A unique identifier (CASE SENSITIVE, 1st letter is capitalized and the next four are lower case) provided by the Amazon GC team. This value is part of the Payload of every AGCOD Gateway request.
- `AGCOD_ENV` - production (default) or sandbox. Determines hosts used for connecting to the endpoints.

```
env          NA                         EU                            FE
production   agcod-v2.amazon.com        agcod-v2-eu.amazon.com        agcod-v2-fe.amazon.com
development  agcod-v2-gamma.amazon.com  agcod-v2-eu-gamma.amazon.com  agcod-v2-fe-gamma.amazon.com
```

## Usage
```javascript
const Client = require('agcod')
const client = new Client()

client.createGiftCard('NA', 123, 'USD', (error, result) => {
  console.log('client.createGiftCard response', error, result)
})
```

## Tests
During tests requests are intercepted by nock and responds with a desired response code and contents.
- https://davidwalsh.name/nock
- https://github.com/node-nock/nock

## Nota Bene
- This client needs to operate under TLS 1.2 or after June 30th, 2018 API requests will cease to work

## Other clients
For reference purposes, here's a list of resources that talk about agcod clients.
- https://github.com/larafale/agcod
- https://stackoverflow.com/questions/25007760/having-trouble-in-generating-amazon-aws-signature-with-php/25027843#25027843
- https://github.com/aws/aws-sdk-core-ruby/issues/113
- https://twitter.com/awsforphp/status/715337682096787457?lang=en
- https://forums.aws.amazon.com/thread.jspa?threadID=113404
