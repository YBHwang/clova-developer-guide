# WeeklyWeather template
Provides weather forecasts for the week. It is used to display weekly weather on a screen.

<div class="note">
<p><strong>Note!</strong></p>
<p>See <a href="#UIExample">Screen UI example</a> for an example of displaying weekly weather.</p>
</div>

## Template field

| Field name  | Type  | Field description  | Required |
|---------------|---------|-----------------------------|---------|
| `bgClipUrl`  | [URLObject](/CIC/References/ContentTemplates/Shared_Objects.md#URLObject) | An object containing a URL of the background sound file | Yes |
| `dailyWeatherList[]`  | object array | An object array containing daily weather | Yes |
| `dailyWeatherList[].date`  | [DateObject](/CIC/References/ContentTemplates/Shared_Objects.md#Datebject) | An object containing the date of the day | Yes |
| `dailyWeatherList[].highTemperature` | [TemperatureCObject](/CIC/References/ContentTemplates/Shared_Objects.md#TemperatureCObject) | An object containing the highest temperature in the afternoon of the day | Yes |
| `dailyWeatherList[].iconImageCode` | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing [weather code](#WeatherCode) for hourly weather | Yes |
| `dailyWeatherList[].iconImageUrl` | [URLObject](/CIC/References/ContentTemplates/Shared_Objects.md#URLObject) | An object containing a URL of the image icon for displaying weather of the day | Yes |
| `dailyWeatherList[].lowTemperature`  |  [TemperatureCObject](/CIC/References/ContentTemplates/Shared_Objects.md#TemperatureCObject) | An object containing the lowest temperature in the morning of the day | Yes |
| `description`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing a brief explanation that this is weekly weather forecasts  | Yes |
| `linkUrl`  | [URLObject](/CIC/References/ContentTemplates/Shared_Objects.md#URLObject) | An object containing a link path to the content  | No |
| `location`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing location information | Yes |
| `type`  | string | A content template delimiter. The value is always **"WeeklyWeather"**. | Yes |

{% include "./Shared_Weather_Code.md" %}

## Template Example

{% raw %}
```json
{
  "bgImageUrl": {
    "type": "url",
    "value": "https://ssl.pstatic.net/static/clova/service/weather/bg_cloud_daytime.mp4"
  },
  "dailyWeatherList": [
    {
      "date": {
        "type": "date",
        "value": "20170726"
      },
      "highTemperature": {
        "type": "temperature-c",
        "value": "33"
      },
      "iconImageCode": {
        "type": "string",
        "value": "3"
      },
      "iconImageUrl": {
        "type": "url",
        "value": "https://ssl.pstatic.net/static/clova/service/weather/icon_03.png"
      },
      "lowTemperature": {
        "type": "temperature-c",
        "value": "23"
      }
    },
    {
      "date": {
        "type": "date",
        "value": "20170727"
      },
      "highTemperature": {
        "type": "temperature-c",
        "value": "32"
      },
      "iconImageCode": {
        "type": "string",
        "value": "5"
      },
      "iconImageUrl": {
        "type": "url",
        "value": "https://ssl.pstatic.net/static/clova/service/weather/icon_05.png"
      },
      "lowTemperature": {
        "type": "temperature-c",
        "value": "23"
      }
    },
    {
      "date": {
        "type": "date",
        "value": "20170728"
      },
      "highTemperature": {
        "type": "temperature-c",
        "value": "31"
      },
      "iconImageCode": {
        "type": "string",
        "value": "9"
      },
      "iconImageUrl": {
        "type": "url",
        "value": "https://ssl.pstatic.net/static/clova/service/weather/icon_09.png"
      },
      "lowTemperature": {
        "type": "temperature-c",
        "value": "24"
      }
    },
    {
      "date": {
        "type": "date",
        "value": "20170729"
      },
      "highTemperature": {
        "type": "temperature-c",
        "value": "29"
      },
      "iconImageCode": {
        "type": "string",
        "value": "22"
      },
      "iconImageUrl": {
        "type": "url",
        "value": "https://ssl.pstatic.net/static/clova/service/weather/icon_22.png"
      },
      "lowTemperature": {
        "type": "temperature-c",
        "value": "24"
      }
    },
    {
      "date": {
        "type": "date",
        "value": "20170730"
      },
      "highTemperature": {
        "type": "temperature-c",
        "value": "29"
      },
      "iconImageCode": {
        "type": "string",
        "value": "5"
      },
      "iconImageUrl": {
        "type": "url",
        "value": "https://ssl.pstatic.net/static/clova/service/weather/icon_05.png"
      },
      "lowTemperature": {
        "type": "temperature-c",
        "value": "23"
      }
    },
    {
      "date": {
        "type": "date",
        "value": "20170731"
      },
      "highTemperature": {
        "type": "temperature-c",
        "value": "29"
      },
      "iconImageCode": {
        "type": "string",
        "value": "5"
      },
      "iconImageUrl": {
        "type": "url",
        "value": "https://ssl.pstatic.net/static/clova/service/weather/icon_05.png"
      },
      "lowTemperature": {
        "type": "temperature-c",
        "value": "23"
      }
    },
    {
      "date": {
        "type": "date",
        "value": "20170801"
      },
      "highTemperature": {
        "type": "temperature-c",
        "value": "30"
      },
      "iconImageCode": {
        "type": "string",
        "value": "5"
      },
      "iconImageUrl": {
        "type": "url",
        "value": "https://ssl.pstatic.net/static/clova/service/weather/icon_05.png"
      },
      "lowTemperature": {
        "type": "temperature-c",
        "value": "22"
      }
    }
  ],
  "description": {
    "type": "string",
    "value": "주간 날씨예요"
  },
  "location": {
    "type": "string",
    "value": "정자1동"
  },
  "type": "WeeklyWeather"
}
```
{% endraw %}

## Screen UI example {#UIExample}
The following example shows how the WeeklyWeather template is presented in the Clova mobile app distributed by {{ book.OrientedService }}.
<div class="midAlign"><img style="width: 300px !important" src="/CIC/Resources/Images/Content-Template-WeeklyWeather.png" /></div>

## See also
* [TodayWeather](/CIC/References/ContentTemplates/TodayWeather.md)
* [TomorrowWeather](/CIC/References/ContentTemplates/TomorrowWeather.md)
* [Humidity](/CIC/References/ContentTemplates/Humidity.md)
* [WindSpeed](/CIC/References/ContentTemplates/WindSpeed.md)