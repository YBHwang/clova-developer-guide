# Atmosphere Template
The Atmosphere template is used in providing atmosphere information for the client to display on the client screen. The type of atmosphere information provided includes information on fine dust, ultrafine dust, ozone, UV rays, and yellow dust.

<div class="note">
<p><strong>Note!</strong></p>
<p>See a <a href="#UIExample">UI example</a> for the Atmosphere template used in the display.</p>
</div>

## Template fields

| Field name       | Data type    | Description                     |
|---------------|---------|-----------------------------|
| `announcementOfAtmosphere`   | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | Contains a statement on the forecast. This field is omitted when showing the current atmosphere information. When omitted, the `value` field of this object has an empty string (`""`). |
| `bgClipUrl`     | [URLObject](/CIC/References/ContentTemplates/Shared_Objects.md#URLObject) | The URL of the video file to play in the background. <div class="danger"><p><strong>Caution!</strong></p><p>Due to a license issue, you are not permitted to use this URL.</p></div> |
| `concentrationOfAtmosphere` | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | The current level of air quality. This field is omitted when forecasting. When omitted, the `value` field of this object has an empty string (`""`). |
| `contentProviderText`       | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | The information of the content provider. An empty string (`""`) indicates that no content is to be displayed.  |
| `halfDayAtmosphereList[]`             | object array | The object array that has multiple atmosphere information in half day (morning/afternoon) units.                                    |
| `halfDayAtmosphereList[].atmosphereImageUrl` | [URLObject](/CIC/References/ContentTemplates/Shared_Objects.md#URLObject) | The URL to the image associated with the atmosphere information specified by the `halfDayAtmosphereList[].durationHalfDay` field. |
| `halfDayAtmosphereList[].concentrationOfAtmosphere`   | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | The level of air quality for the time specified by the `halfDayAtmosphereList[].durationHalfDay` field.  |
| `halfDayAtmosphereList[].durationHalfDay`   | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | The time scope for the associated atmosphere information. Available values are: `Tomorrow morning`, `Tomorrow afternoon`, `Morning in two days' time`, `Afternoon in two days' time`  |
| `lastUpdate`                | [DateTimeObject](/CIC/References/ContentTemplates/Shared_Objects.md#DateTimeObject) | The last update time of the weather information. An empty string (`""`) indicates that no content is to be displayed. |
| `linkUrl`       | [URLObject](/CIC/References/ContentTemplates/Shared_Objects.md#URLObject) | The URL of the content. An empty string (`""`) indicates that no content is to be displayed.  |
| `location`      | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | The information on the region. |
| `referenceText`             | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | The information of the referred service. An empty string (`""`) indicates that no content is to be displayed.  |
| `referenceUrl`              | [URLObject](/CIC/References/ContentTemplates/Shared_Objects.md#URLObject)       | The information on the usage result URL of the referred service. An empty string (`""`) indicates that no content is to be displayed.   |
| `temperatureCode`      | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | The information on the [weather code](#WeatherCode). An empty string (`""`) indicates that no content is to be displayed.  |
| `type`          | string | The type of this template. The value is always `"Atmosphere"`. |
| `valueOfAtmosphere`         | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | The current air quality index. The unit of the index is included. An empty string (`""`) indicates that no content is to be displayed. |

## Template example

{% raw %}
```json
// Current atmosphere information
{
  "announcementOfAtmosphere": {
    "type": "string",
    "value": ""
  },
  "bgClipUrl": {
    "type": "url",
    "value": "https://ssl.pstatic.net/static/clova/service/weather/bg_clean_daytime.mp4"
  },
  "concentrationOfAtmosphere": {
    "type": "string",
    "value": "Good"
  },
  "contentProviderText" : {
    "type" : "string",
    "value": "National weather service"
  },
  "failureMessage": {
    "type": "string",
    "value": "The fine dust level for today in Shinjuku is good"
  },
  "halfDayAtmosphereList": [
    {
      "atmosphereImageUrl": {
        "type": "url",
        "value": "http://static.contentproviderdomain.net/clova/service/weather/air_icon_02.png"
      },
      "concentrationOfAtmosphere": {
        "type": "string",
        "value": "Normal"
      },
      "durationHalfDay": {
        "type": "string",
        "value": "Tomorrow morning"
      }
    },
    {
      "atmosphereImageUrl": {
        "type": "url",
        "value": "http://static.contentproviderdomain.net/clova/service/weather/air_icon_02.png"
      },
      "concentrationOfAtmosphere": {
        "type": "string",
        "value": "Normal"
      },
      "durationHalfDay": {
        "type": "string",
        "value": "Tomorrow afternoon"
      }
    },
    {
      "atmosphereImageUrl": {
        "type": "url",
        "value": "http://static.contentproviderdomain.net/clova/service/weather/air_icon_02.png"
      },
      "concentrationOfAtmosphere": {
        "type": "string",
        "value": "Normal"
      },
      "durationHalfDay": {
        "type": "string",
        "value": "Morning in two days’ time"
      }
    },
    {
      "atmosphereImageUrl": {
        "type": "url",
        "value": "http://static.contentproviderdomain.net/clova/service/weather/air_icon_02.png"
      },
      "concentrationOfAtmosphere": {
        "type": "string",
        "value": "Normal"
      },
      "durationHalfDay": {
        "type": "string",
        "value": "Afternoon in two days’ time"
      }
    }
  ],
  "location": {
    "type": "string",
    "value": "Jeongja1-dong"
  },
  "meta": {
    "version": {
      "type": "string",
      "value": "v0.1"
    }
  },
  "lastUpdate" : {
    "type" : "datetime",
    "value" : "2018-02-05T06:29:09Z"
  },
  "referenceText" : {
    "type" : "string",
    "value": "NAVER weather"
  },
  "referenceUrl" : {
    "type" : "url",
    "value" : "http://weather.contentproviderdomain.com/"
  },
  "temperatureCode": {
    "type": "string",
    "value": "5"
  },
  "type": "Atmosphere",
  "valueOfAtmosphere": {
    "type": "number",
    "value": "27㎍/㎥"
  }
}

// Atmosphere information for tomorrow
{
  "announcementOfAtmosphere": {
    "type": "string",
    "value": "Here is tomorrow's fine dust level"
  },
  "bgClipUrl": {
    "type": "url",
    "value": "https://ssl.pstatic.net/static/clova/service/weather/bg_cloud_daytime.mp4"
  },
  "concentrationOfAtmosphere": {
    "type": "string",
    "value": ""
  },
  "failureMessage": {
    "type": "string",
    "value": "The fine dust level for tomorrow in Shinjuku is average"
  },
  "halfDayAtmosphereList": [
    {
      "atmosphereImageUrl": {
        "type": "url",
        "value": "http://static.contentproviderdomain.net/clova/service/weather/air_icon_02.png"
      },
      "concentrationOfAtmosphere": {
        "type": "string",
        "value": "Normal"
      },
      "durationHalfDay": {
        "type": "string",
        "value": "Tomorrow morning"
      }
    },
    {
      "atmosphereImageUrl": {
        "type": "url",
        "value": "http://static.contentproviderdomain.net/clova/service/weather/air_icon_02.png"
      },
      "concentrationOfAtmosphere": {
        "type": "string",
        "value": "Normal"
      },
      "durationHalfDay": {
        "type": "string",
        "value": "Tomorrow afternoon"
      }
    },
    {
      "atmosphereImageUrl": {
        "type": "url",
        "value": "http://static.contentproviderdomain.net/clova/service/weather/air_icon_02.png"
      },
      "concentrationOfAtmosphere": {
        "type": "string",
        "value": "Normal"
      },
      "durationHalfDay": {
        "type": "string",
        "value": "Morning in two days’ time"
      }
    },
    {
      "atmosphereImageUrl": {
        "type": "url",
        "value": "http://static.contentproviderdomain.net/clova/service/weather/air_icon_02.png"
      },
      "concentrationOfAtmosphere": {
        "type": "string",
        "value": "Normal"
      },
      "durationHalfDay": {
        "type": "string",
        "value": "Afternoon in two days’ time"
      }
    }
  ],
  "location": {
    "type": "string",
    "value": "Jeongja1-dong"
  },
  "meta": {
    "version": {
      "type": "string",
      "value": "v0.1"
    }
  },
  "type": "Atmosphere",
  "valueOfAtmosphere": {
    "type": "number",
    "value": ""
  }
}
```
{% endraw %}

## UI example {#UIExample}
The following examples show how the Atmosphere template is used on the Clova app distributed by {{ book.OrientedService }}.

| Atmosphere state now | Atmosphere state tomorrow |
|-------------|------------|
| ![Now](/CIC/Resources/Images/Content-Template-Atmosphere_Now.png) | ![Original](/CIC/Resources/Images/Content-Template-Atmosphere_Tomorrow.png) |

## See also
* [Humidity](/CIC/References/ContentTemplates/Humidity.md)
* [TodayWeather](/CIC/References/ContentTemplates/TodayWeather.md)
* [TomorrowWeather](/CIC/References/ContentTemplates/TomorrowWeather.md)
* [WeeklyWeather](/CIC/References/ContentTemplates/WeeklyWeather.md)
* [WindSpeed](/CIC/References/ContentTemplates/WindSpeed.md)