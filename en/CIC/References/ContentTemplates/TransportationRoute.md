# TransportationRoute template
Provides route directions for public transportations. It is used to display public transportation routes on a screen. TransportationRoute has routes types as follows. For each route type, the `trafficType` object has different field configuration.

| Section type  | Type description  | `subPath` object fields  |
|---------------------|---------------------------------------------|-----------------------------|
| Subway section(1)  | Displays routes that use subways only.  | `lane`, `name`, `endID`, `endName`, `endX`, `endY`, `startID`, `startName`, `startX`, `startY`, `subwayCode` |
| Bus section(2)  | Displays routes that use buses only.  | `busID`, `busNo`, `endID`, `endName`, `endX`, `endY`, `startID`, `startName`, `startX`, `startY`, `type`  |
| Walking section(3)  | Displays routes that use both subways and buses. | `distance`, `sectionTime`  |

<div class="note">
<p><strong>Note!</strong></p>
<p>To display public transportation routes with this template, you must understand how to use the {{book.OrientedService}} map API. Use data returned from the template together with the {{book.OrientedService}} map API to display directions on a map. See <a href="https://navermaps.github.io/maps.js/docs/">{{book.OrientedService}} map API documentation</a> for more details on the NAVER map API. See <a href="#UIExample">Screen UI example</a> for an example of how route directions are displayed.</p>
</div>

## Template field

| Field name  | Type  | Field description  | Required |
|---------------|---------|-----------------------------|---------|
| `appLinkUrl`  | [URLObject](/CIC/References/ContentTemplates/Shared_Objects.md#URLObject)  | An object containing a URL which directs users to a map app  | Yes |
| `boundary`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object representing a rectangular area (MBR, Minimum Bounding Rectangle) that includes all of interpolated points, in the form of "left,top,right,bottom" sting. | Yes |
| `busStationCount`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | The total number of stations to pass through when traveling by bus | Yes |
| `end`  | [LocationObject](/CIC/References/ContentTemplates/Shared_Objects.md#LocationObject) | An object containing coordinates of the destination point | Yes |
| `endName`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing the name of the destination point | Yes |
| `linkUrl`  | [URLObject](/CIC/References/ContentTemplates/Shared_Objects.md#URLObject)  | An object containing a URL which directs users to a web map  | Yes |
| `lanes[]`  | object array | An object containing interpolated points on all routes found | Yes |
| `lanes[].create`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object that decides the type of its `section` field. <ul><li><strong>If this field does not exist,</strong> the <code>section</code> field contains interpolated points for drawing bus/subway sections.</li><li><strong>If this field does exist and <code>create.value</code> is set to "1",</strong> the <code>section</code> field contains interpolated points for drawing polylines.</ul> | No |
| `lanes[].section[]`  | [LocationObject](/CIC/References/ContentTemplates/Shared_Objects.md#LocationObject) array | An object array containing interpolated points for drawing bus/subway sections or polylines between sections. | No |
| `pathType`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing the route type of the direction. The `pathType.value` field has the following values. <ul><li><strong>"1"</strong>: Routes that use subways only</li><li><strong>"2"</strong>: Routes that use buses only</li><li><strong>"3"</strong>: Routes that use both subways and buses</li></ul>| Yes |
| `start`  | [LocationObject](/CIC/References/ContentTemplates/Shared_Objects.md#LocationObject) | An object containing coordinates of the departure point | Yes |
| `startName`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject)  | An object containing the place name of the departure point | Yes |
| `subPath[]`  | object array | An object array containing information of sections on each route | Yes |
| `subPath[].distance`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing a travel distance of a given section. This field shows information on walking sections (When the `subPath[].trafficType.value` field is set to **"3"**). | No |
| `subPath[].endID`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing IDs of subway stations/bus stops to get off in a given section. This field shows information on subway or bus sections (When the `subPath[].trafficType.value` field is set to **"1"** or **"2"**). | No |
| `subPath[].endName`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing names of subway stations/bus stops to get off in a given section. This field shows information on subway or bus sections (When the `subPath[].trafficType.value` field is set to **"1"** or **"2"**). | No |
| `subPath[].endX`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing X coordinates of subway stations/bus stops to get off in a given section. This field shows information on subway or bus sections (When the `subPath[].trafficType.value` field is set to **"1"** or **"2"**). | No |
| `subPath[].endY`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing Y coordinates of subway stations/bus stops to get off in a given section. This field shows information on subway or bus sections (When the `subPath[].trafficType.value` field is set to **"1"** or **"2"**). | No |
| `subPath[].lane`  | object | An object containing information on lanes in a given section. This field shows information on subway or bus sections (When the `subPath[].trafficType.value` field is set to **"1"** or **"2"**). | No |
| `subPath[].lane.busID`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing bus IDs. This field shows information on bus sections (When the `subPath[].trafficType.value` field is set to **"2"**). | No |
| `subPath[].lane.busNo`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing bus numbers. This field shows information on bus sections (When the `subPath[].trafficType.value` field is set to **"2"**). | No |
| `subPath[].lane.name`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing information on subway lanes. This field shows information on subway sections (When the `subPath[].trafficType.value` field is set to **"1"**). | No |
| `subPath[].lane.subwayCode` | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing [subway codes](#CodeReference). This field shows information on subway sections (When the `subPath[].trafficType.value` field is set to **"1"**). | No |
| `subPath[].lane.type`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing [bus types](#CodeReference). This field shows information on bus sections (When the `subPath[].trafficType.value` field is set to **"2"**). | No |
| `subPath[].sectionTime`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing an estimated travel time at a given section. Unit is minute. This field shows information on walking sections (When the `subPath[].trafficType.value` field is set to **"3"**). | No |
| `subPath[].startID`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing IDs of subway stations/bus stops to get on in a given section. This field shows information on subway or bus sections (When the `subPath[].trafficType.value` field is set to **"1"** or **"2"**). | No |
| `subPath[].startName`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing names of subway stations/bus stops to get on in a given section. This field shows information on subway or bus sections (When the `subPath[].trafficType.value` field is set to **"1"** or **"2"**). | No |
| `subPath[].startX`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing X coordinates of subway stations/bus stops to get on in a given section. This field shows information on subway or bus sections (When the `subPath[].trafficType.value` field is set to **"1"** or **"2"**). | No |
| `subPath[].startY`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing Y coordinates of subway stations/bus stops to get on in a given section. This field shows information on subway or bus sections (When the `subPath[].trafficType.value` field is set to **"1"** or **"2"**). | No |
| `subPath[].trafficType`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | Section type. It is an identifier for distinguishing travel methods at a given section. Depending on the value of this field, configuration of sub objects in the `subPath` field can change. Available values are: <ul><li><strong>"1"</strong>: Subway section</li><li><strong>"2"</strong>: Bus section</li><li><strong>"3"</strong>: Walking section</li></ul> | No |
| `SubwayStationCount`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing the total number of subway stations to pass through when traveling by subway | Yes |
| `totalDistance`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing a total travel distance. Unit is meter. | Yes |
| `totalStationCount`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing the total number of bus stops and subway stations to pass through when traveling by bus and subway | Yes |
| `totalTime`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing an estimated total travle time. Unit is minute. | Yes |
| `type`  | string | A content template delimiter. The value is always **"TransportationRoute"** | Yes |


## Subway line codes and bus type codes {#CodeReference}

| Subway line code | Description  | Bus type code  | Description  |
|--------------|---------------|--------------|--------------|
| 1	 | 수도권_1호선  | 1  | 일반  |
| 2  | 수도권_2호선  | 2  | 좌석  |
| 3  | 수도권_3호선  | 3  | 마을  |
| 4  | 수도권_4호선  | 4  | 직행좌석  |
| 5  | 수도권_5호선  | 5  | 공항  |
| 6  | 수도권_6호선  | 6  | 간선급행  |
| 7  | 수도권_7호선  | 10  | 외곽  |
| 8  | 수도권_8호선  | 11  | 간선  |
| 9  | 수도권_9호선  | 12  | 지선  |
| 21  | 인천_1호선  | 13  | 순환  |
| 31  | 대전_1호선  | 14  | 광역  |
| 41  | 대구_1호선  | 15  | 급행  |
| 42  | 대구_2호선  | 20  | 농어촌  |
| 51  | 광주_1호선  | 21  | 제주시외  |
| 71  | 부산_1호선  | 22  | 시외  |
| 72  | 부산_2호선  | 26  | 급행간선  |
| 73  | 부산_3호선  |  |  |
| 74  | 부산_4호선  |  |  |
| 78  | 부산_동해선  |  |  |
| 79  | 부산_부산김해경전철 |  |  |
| 100  | 분당선  |  |  |
| 101  | 공항철도  |  |  |
| 103  | 중앙선  |  |  |
| 104  | 경의선  |  |  |
| 107  | 에버라인  |  |  |
| 108  | 경춘선  |  |  |
| 109  | 신분당선  |  |  |
| 110  | 의정부경전철  |  |  |
| 111  | 수인선  |  |  |


## Template Example

{% raw %}
```json
{
  "type" : "TransportationRoute",
  "pathType" : {
    "type" : "string",
    "value" : "3"
  },
  "subPath" : [
    {
      "trafficType" : {
        "type" : "string",
        "value" : "3"
      },
      "distance" : {
        "type" : "string",
        "value" : "179"
      },
      "sectionTime" : {
        "type" : "string",
        "value" : "3"
      }
    },
    {
      "trafficType" : {
        "type" : "string",
        "value" : "1"
      },
      "lane" : {
        "name" : {
          "type" : "string",
          "value" : "5호선"
        },
        "subwayCode" : {
          "type" : "string",
          "value" : "5"
        }
      },
      "startX" : {
        "type" : "string",
        "value" : "126.9764454"
      },
      "startY" : {
        "type" : "string",
        "value" : "37.5716197"
      },
      "startID" : {
        "type" : "string",
        "value" : "533"
      },
      "startName" : {
        "type" : "string",
        "value" : "광화문"
      },
      "endX" : {
        "type" : "string",
        "value" : "127.0053025"
      },
      "endY" : {
        "type" : "string",
        "value" : "37.5646938"
      },
      "endID" : {
        "type" : "string",
        "value" : "536"
      },
      "endName" : {
        "type" : "string",
        "value" : "동대문역사문화공원"
      }
    },
    {
      "trafficType" : {
        "type" : "string",
        "value" : "3"
      },
      "distance" : {
        "type" : "string",
        "value" : "26"
      },
      "sectionTime" : {
        "type" : "string",
        "value" : "1"
      }
    },
    {
      "trafficType" : {
        "type" : "string",
        "value" : "2"
      },
      "lane" : {
        "busNo" : {
          "type" : "string",
          "value" : "301"
        },
        "type" : {
          "type" : "string",
          "value" : "11"
        },
        "busID" : {
          "type" : "string",
          "value" : "1006"
        }
      },
      "startX" : {
        "type" : "string",
        "value" : "127.0072774"
      },
      "startY" : {
        "type" : "string",
        "value" : "37.5651429"
      },
      "startID" : {
        "type" : "string",
        "value" : "105343"
      },
      "startName" : {
        "type" : "string",
        "value" : "광희동"
      },
      "endX" : {
        "type" : "string",
        "value" : "127.0611357"
      },
      "endY" : {
        "type" : "string",
        "value" : "37.511781"
      },
      "endID" : {
        "type" : "string",
        "value" : "123460"
      },
      "endName" : {
        "type" : "string",
        "value" : "무역센타"
      }
    },
    {
      "trafficType" : {
        "type" : "string",
        "value" : "3"
      },
      "distance" : {
        "type" : "string",
        "value" : "373"
      },
      "sectionTime" : {
        "type" : "string",
        "value" : "6"
      }
    }
  ],
  "busStationCount" : {
    "type" : "string",
    "value" : "17"
  },
  "subwayStationCount" : {
    "type" : "string",
    "value" : "3"
  },
  "totalStationCount" : {
    "type" : "string",
    "value" : "20"
  },
  "totalTime" : {
    "type" : "string",
    "value" : "55"
  },
  "totalDistance" : {
    "type" : "string",
    "value" : "13284"
  },
  "lanes" : [
    {
      "create" : {
        "type" : "string",
        "value" : "1"
      },
      "section" : [
        {
          "type" : "location",
          "value" : "349538037, 149527412"
        },
        {
          "type" : "location",
          "value" : "349543351, 149521660"
        }
      ]
    },
    {
      "section" : [
        {
          "type" : "location",
          "value" : "349543351, 149521660"
        },
        {
          "type" : "location",
          "value" : "349543376, 149522540"
        },
        {
          "type" : "location",
          "value" : "349543354, 149522879"
        },
        {
          "type" : "location",
          "value" : "349543478, 149524090"
        },
        {
          "type" : "location",
          "value" : "349543584, 149524790"
        }
      ]
    },
    {
      "create" : {
        "type" : "string",
        "value" : "1"
      },
      "section" : [
        {
          "type" : "location",
          "value" : "349600453, 149466463"
        },
        {
          "type" : "location",
          "value" : "349610861, 149458583"
        }
      ]
    }
  ],
  "boundary" : {
    "type" : "string",
    "value" : "349532874,149530952,349610861,149451998"
  },
  "start" : {
    "type" : "location",
    "value" : "349538036,149527412"
  },
  "startName" : {
    "type" : "string",
    "value" : "광화문삼거리"
  },
  "end" : {
    "type" : "location",
    "value" : "349610861,149458582"
  },
  "endName" : {
    "type" : "string",
    "value" : "코엑스"
  },
  "linkUrl" : {
    "type" : "url",
    "value" : "https://..."
  },
  "appLinkUrl" : {
    "type" : "url",
    "value" : "https://..."
  }
}
```
{% endraw %}

## Screen UI example {#UIExample}
The following example shows how the TransportationRoute template is presented for each type in the Clova mobile app distributed by {{ book.OrientedService }}.

| Using subway | Using bus |
|----------|---------|
| <div class="midAlign"><img style="width: 300px !important" src="/CIC/Resources/Images/Content-Template-TransportationRoute-Use_Only_Subway.png" /></div> | <div class="midAlign"><img style="width: 300px !important" src="/CIC/Resources/Images/Content-Template-TransportationRoute-Use_Only_Bus.png" /></div> |

## See also
* [CarRoute](/CIC/References/ContentTemplates/CarRoute.md)