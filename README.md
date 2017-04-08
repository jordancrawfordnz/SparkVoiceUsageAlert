# Spark Voice Usage Alert

## What is this?
I found that on Spark NZ (cell phone provider), a post paid monthly plan wouldn't stop incuring additional charges when I run out of minutes and it wouldn't notify me if I did use too many minutes!

After a painful bill, I made this to prevent it happening again.

This:

* Logs into the Spark website with your mobile account details.
* Determines how many minutes of your allowance has been used.
* At 80%, 90%, 100% and 110% usage this sends a text message to warn you (via Plivo).

## Requirements

* A Redis server. This is used to keep track of the last alert sent so you don't get repeated alerts.
* A Plivo account with credit. This is used to send you a text.
* NodeJS installed on your server.


## Environment Variables
### `SPARK_MOBILE_NUMBER`
This is the Spark mobile number to check. This number is mentioned in the alert text message and is used as the username for authentication with Spark.

### `SPARK_PASSWORD`
This is your Spark password.

### `REDIS_HOST`
This is the hostname for your Redis server to store details about the last check (to prevent repeated alerts).

### `PLIVO_AUTH_ID`
This is your Plivo auth ID. You can get this by signing up at [plivo.com](https://www.plivo.com/).

### `PLIVO_AUTH_TOKEN`
This is your Plivo auth token. You can get this by signing up at [plivo.com](https://www.plivo.com/).

### `PLIVO_DESTINATION_NUMBER`
This is the number to send text messages to. This includes the country code, e.g.: `642XXXXXXXX`.

### `PLIVO_SOURCE_NUMBER`
The number to send the text from. Apparently this can be anything but I used `14154847489` which was used by the Plivo dashboard.

### `JOB_COMPLETE_URL` (optional)
This is a URL to hit after the job completes successfully. Use this with something like [healthchecks.io](https://healthchecks.io/) to get notified if something breaks.

## Setting it up

1. Clone the repository.
2. Run `npm install` to grab dependencies.
3. Configure the environment variables with your options.
4. Configure `node start.js` to run on a schedule with a CRON job.

## Setting it up with Docker
<!-- TODO -->

## Note
This is not endorsed by Spark at all and these API end points are unofficial.