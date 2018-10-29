{% if book.TargetCountryCode == "KR" %}

| `location` field value | Location details          |
|------------------|------------------|
| `ATTIC`                     | Attic  |
| `BALCONY`                   | Balcony  |
| `BALCONY_IN_LIVING_ROOM`    | Living room balcony  |
| `BALCONY_IN_MAIN_ROOM`      | Master bedroom balcony  |
| `BALCONY_KITCHEN`           | Kitchen balcony  |
| `BATH_ROOM`                 | Small bathroom  |
| `BATH_ROOM_IN_LIVING_ROOM`  | Living room bathroom |
| `BATH_ROOM_IN_MAIN_ROOM`    | Master bathroom |
| `BED_ROOM`                  | Bedroom |
| `BIG_BATH_ROOM`             | Big bathroom  |
| `BIG_CHILD_ROOM`            | Eldest child's room  |
| `BIG_ROOM`                  | Big room  |
| `BOILER_ROOM`               | Boiler room |
| `DINING_ROOM`               | Dining room |
| `DRESS_ROOM`                | Dress room |
| `ENTRANCE`                  | Porch |
| `FAMILY_ROOM`               | Family room  |
| `FATHER_ROOM`               | Father's room |
| `FIFTH_ROOM`                | Room 5  |
| `FIRST_ROOM`                | Room 1 |
| `FOURTH_ROOM`               | Room 4 |
| `HALLWAY`                   | Hallway |
| `KITCHEN`                   | Kitchen |
| `LIBRARY`                   | Library |
| `LIVING_ROOM`               | Living room |
| `MAIN_GATE`                 | Main gate |
| `MAIN_ROOM`                 | Master bedroom |
| `MOTHER_ROOM`               | Mother's room |
| `MY_ROOM`                   | My room  |
| `PARENTS_ROOM`              | Parents' room  |
| `PLAY_ROOM`                 | Play room  |
| `POWDER_ROOM`               | Powder room |
| `ROOM`                      | Room  |
| `SECOND_ROOM`               | Room 2 |
| `SMALL_CHILD_ROOM`          | Youngest child's room |
| `SMALL_LIVING_ROOM`         | Small living room  |
| `SMALL_ROOM`                | Small room |
| `SMALL_KITCHEN`             | Small kitchen  |
| `SMALL_BATH_ROOM`           | Small bathroom |
| `STAIRS`                    | Stairs |
| `THIRD_ROOM`                | Room 3 |
| `UPSTAIRS_ROOM`             | Upstairs room |
| `UTILITY_ROOM`              | Utility room |
| `WAREHOUSE`                 | Warehouse |
| `YARD`                      | Yard |

{% elif book.TargetCountryCode == "JP" %}

{% if book.language == "en" %}

| `location` field value |    Location details       |    Location details(JP)      |
|------------------|------------------|------------------|
| `ATTIC`                     | Attic                      | 屋根裏部屋  |
| `BALCONY`                   | Balcony                    | ベランダ |
| `BATH_ROOM`                 | Bathroom                   | バスルーム |
| `BED_ROOM`                  | Bedroom                    | ベッドルーム |
| `DINING_ROOM`               | Dining room                | ダイニング |
| `ENTRANCE`                  | Entrance                   | 玄関 |
| `FIRST_ROOM`                | First room                 | 部屋1 |
| `HALLWAY`                   | Hallway                    | 廊下 |
| `KITCHEN`                   | Kitchen                    | キッチン |
| `LIBRARY`                   | Library                    | 書斎 |
| `LIVING_ROOM`               | Living room                | リビング |
| `POWDER_ROOM`               | Powder room                | 洗面所 |
| `ROOM`                      | Room                       | 部屋 |
| `SECOND_ROOM`               | Second room                | 部屋2 |
| `SMALL_CHILD_ROOM`          | Younger child's room       | 子供部屋 |
| `SMALL_BATH_ROOM`           | Toilet                     | トイレ |
| `STAIRS`                    | Stairs                     | 階段 |
| `THIRD_ROOM`                | Third room                 | 部屋3 |
| `WAREHOUSE`                 | Warehouse                  | 倉庫 |
| `YARD`                      | Yard                       | 庭 |
| `JAPANESE_STYLE_ROOM`       | Japanese style room        | 和室 |

{% elif book.TargetCountryCode == "JP" %}

| `location` field value | Location details     |
|------------------------|------------------------------|
| `ATTIC`                | Attic |
| `BALCONY`              | Balcony |
| `BATH_ROOM`            | Bathroom |
| `BED_ROOM`             | Bedroom |
| `DINING_ROOM`          | Dining room |
| `ENTRANCE`             | Porch |
| `FIRST_ROOM`           | Room 1 |
| `HALLWAY`              | Hallway |
| `KITCHEN`              | Kitchen |
| `LIBRARY`              | Library |
| `LIVING_ROOM`          | Living room |
| `POWDER_ROOM`          | Powder room |
| `ROOM`                 | Room |
| `SECOND_ROOM`          | Room 2 |
| `SMALL_CHILD_ROOM`     | Child's room |
| `SMALL_BATH_ROOM`      | Small bathroom |
| `STAIRS`               | Stairs |
| `THIRD_ROOM`           | Room 3 |
| `WAREHOUSE`            | Warehouse |
| `YARD`                 | Yard |
| `JAPANESE_STYLE_ROOM`  | Japanese-style room |

{% endif %}

{% endif %}
