# Weather Reminder

## Overview

After the impact Hurricane Ida had on the United States' east coast, I thought it may be a good idea to receive daily weather alerts to ensure readiness.

## Technology Stack

* [Python](https://www.python.org/)
* [AWS Lambda](https://aws.amazon.com/lambda/)
* [AWS Eventbridge](https://aws.amazon.com/eventbridge/)
* [AWS SES](https://aws.amazon.com/ses/)
* [OpenWeatherMap API](https://openweathermap.org/api)

## Setup

**AWS**

* Configure the [aws cli](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html)
* [Verify email addresses to send/receive email while in sandbox mode](https://docs.aws.amazon.com/ses/latest/DeveloperGuide/verify-email-addresses.html)
* Sign up for the [OpenWeatherMap API](https://openweathermap.org/appid) and use the provided API key to set an `OPEN_WEATHER_MAP_API` environment variable
* Create a lambda function called `weather-reminder`. Note: if your lambda is called something different, rename instances of `weather-reminder` to your lambda function name. This especially applies to build and deploy shell scripts in the `scripts` directory.
* Provide values for all environment variables mentioned in `.env.template` to the lambda function
* [Configure AWS Eventbridge to trigger the lambda function](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-run-lambda-schedule.html)

**Local**

* Setup a virtual environment, `python3 -m venv .venv`
* Run `pip install -r requirements.txt` to install dependencies
* Run `python lambda_function.py` to test locally
    * Note: Either populate a `.env` file and [load its contents for local development](https://github.com/theskumar/python-dotenv) or manually replace environment variables used in the code with values while testing locally.

## Deployment

* Run `./scripts/build-deploy.sh` to build and deploy the lambda to AWS
* Run `./aws/scripts/ses-create-weather-reminder-template.sh` to create the `WeatherReminderTemplate` email template in SES
* Run `./aws/scripts/ses-update-template-weather-reminder.sh` to update the `WeatherReminderTemplate` email templae in SES

## Impact of Hurricane Ida

* [NPR](https://www.npr.org/2021/09/13/1036665971/two-weeks-after-hurricane-ida-tens-of-thousands-in-louisiana-are-still-without-p)
* [Reuters](https://www.reuters.com/world/us/new-york-city-mayor-declares-state-emergency-after-record-breaking-rain-2021-09-02/)
* [Associated Press (AP News)](https://apnews.com/article/northeast-us-new-york-new-jersey-weather-60327279197e14b9d17632ea0818f51c)# AWS_Lambda_Weather_Notifier
