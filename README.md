# slimer-example-heroku

An example of running [Slimer](https://github.com/codenamev/slimer) on Heroku.

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy)

## Setup

1. Deploy to Heroku using the button above.
2. Visit your new app on heroku `https://slimer-example.herokuapp.com/status` and verify Slimer responds with `Ok`.
3. Generate an API key: `heroku run bundle exec rake slimer:api_keys:generate`, and enter a name for the key when it asks.

## Consuming substances

Using the API key you generated above, you can tell Slimer to consume any
substance in one of two ways. Replace any `API_KEY` in the URLs below with the
API key you generated  in the Setup above. Also, replace `slimer-example` in any
of the URLs with the name of your new Heroku app.

**Consume via GET request**

`curl https://slimer-example.herokuapp.com/API_KEY/consume?store_this=this&and_that=that`

The above request will create a substance with a `payload` of:

```json
{
  "store_this": "this",
  "and_that": "that"
}
```

**Consume via POST request

The same request above can be made as a `POST` request:

```bash
curl -X POST -H "Content-Type: application/json" \
  -d '{"store_this": "this", "and_that": "that"}' \
  https://slimer-example.herokuapp.com/API_KEY/consume
```

** Metadata **

Substances can be stored with metadata to describe the data being stored.
Simply provide a `metadata` parameter in your payload and this will be stored
separately.

## Upgrading

The upgrade process is as simple as:

1. Upgrade Slimer: `bundle update`
2. Re-deploy to Heroku: `git push heroku main`
