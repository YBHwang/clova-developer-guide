# CarRoute template
Provides route directions by driving. It is used to display driving routes on a screen.

<div class="note">
<p><strong>Note!</strong></p>
<p>To display driving routes with this template, you must understand how to use the {{book.OrientedService}} map API. Use data returned from the template together with the {{book.OrientedService}} map API to display directions on a map. See <a href="https://navermaps.github.io/maps.js/docs/">{{book.OrientedService}} map API documentation</a> for more details on the NAVER map API. See <a href="#UIExample">Screen UI example</a> for an example of how route directions are displayed.</p>
</div>

## Template field

| Field name  | Type  | Field description  | Required |
|---------------|---------|-----------------------------|---------|
| `appLinkUrl`  | [URLObject](/CIC/References/ContentTemplates/Shared_Objects.md#URLObject)  | An object containing a URL which directs users to a map app  | Yes |
| `boundary`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object representing a rectangular area (MBR, Minimum Bounding Rectangle) that includes all of interpolated points, in the form of "left,top,right,bottom" string | Yes |
| `linkUrl`  | [URLObject](/CIC/References/ContentTemplates/Shared_Objects.md#URLObject)  | An object containing a URL which directs users to a web map  | Yes |
| `pathList`  | [LocationObject](/CIC/References/ContentTemplates/Shared_Objects.md#LocationObject) | An object array containing road segment points along the route | Yes |
| `summary`  | object | An object containing summary of driving routes | Yes |
| `summary.distance`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing a travel distance from a departure point to a destination point. Unit is meter. | Yes |
| `summary.destination`  | object | An object containing information of the destination point | Yes |
| `summary.destination.lat`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing the latitude of the destination point | Yes |
| `summary.destination.lon`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing the longitude of the destination point | Yes |
| `summary.destination.name`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing the name of the destination point | Yes |
| `summary.roadSummary[]`  | object array | An object array containing summary of roads along the route | Yes |
| `summary.roadSummary[].length`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing the length of the road segment. Unit is meter. | Yes |
| `summary.roadSummary[].name`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing the name of the road | Yes |
| `summary.roadSummary[].point`  | object | An object containing coordinates of the road entry point | Yes |
| `summary.roadSummary[].point.x`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing the X coordinate of the road entry point on the NAVER map | Yes |
| `summary.roadSummary[].point.y`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing the Y coordinate of the road entry point on the NAVER map | Yes |
| `summary.roadSummary[].roadCongestion` | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing traffic conditions on the road. `summary.roadSummary.roadCongestion.value` can have the following values. <ul><li><strong>"0"</strong>: Data was not received</li><li><strong>"1"</strong>: Smooth</li><li><strong>"2"</strong>: Slow</li><li><strong>"3"</strong>: Stagnant</li><li><strong>"4"</strong>: Stopped</li></ul> | Yes |
| `summary.roadSummary[].speed`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing an average driving speed of the road segment | Yes |
| `summary.start`  | object | An object containing information of the departure point | Yes |
| `summary.start.lat`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing the latitude of the departure point | Yes |
| `summary.start.lon`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing the longitude of the departure point | Yes |
| `summary.start.name`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing the name of the departure point | Yes |
| `summary.time`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) | An object containing the estimated travel time. Unit is minute. | Yes |
| `type`  | string | A content template delimiter. The value is always **"CarRoute"**. | Yes |

## Template Example

{% raw %}
```json
{
  "type" : "CarRoute",
  "summary" : {
    "distance" : {
      "type" : "string",
      "value" : "62526"
    },
    "time" : {
      "type" : "string",
      "value" : "4526"
    },
    "start" : {
      "lon" : {
        "type" : "string",
        "value" : "349541687"
      },
      "lat" : {
        "type" : "string",
        "value" : "149420527"
      },
      "name" : {
        "type" : "string",
        "value" : "사당역 2호선"
      }
    },
    "destination" : {
      "lon" : {
        "type" : "string",
        "value" : "349541687"
      },
      "lat" : {
        "type" : "string",
        "value" : "149420527"
      },
      "name" : {
        "type" : "string",
        "value" : "사당역 2호선"
      }
    },
    "roadSummary" : [
      {
        "name" : {
          "type" : "string",
          "value" : "과천대로"
        },
        "length" : {
          "type" : "string",
          "value" : "6199"
        },
       "point" : {
         "x" : {
           "type" : "string",
           "value" : "349556545"
         },
         "y" : {
           "type" : "string",
           "value" : "149363287"
         }
       },
       "speed" : {
         "type" : "string",
         "value" : "72"
       },
       "roadCongestion" : {
         "type" : "string",
         "value" : "1"
       }
      }
    ]
  },
  "pathList" : [
    {
      "type" : "location",
      "value" : "349668603.0,149410368.0"
    },
    {
      "type" : "location",
      "value" : "349668603.0,149410368.0"
    }
  ],
  "boundary" : {
    "type" : "string",
    "value" : "349435089,149420518,349561008,149213590"
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
The following example shows how the CarRoute template is presented in the Clova mobile app distributed by {{ book.OrientedService }}.
<div class="midAlign"><img style="width: 300px !important" src="/CIC/Resources/Images/Content-Template-CarRoute.png" /></div>

## See also
* [TransportationRoute](/CIC/References/ContentTemplates/TransportationRoute.md)