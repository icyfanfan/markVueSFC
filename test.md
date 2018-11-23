## props

| 属性名          | 描述  | 类型               | 必填    | 默认      |
| ------------ | --- | ---------------- | ----- | ------- |
| type         |     | String           | false | 'text'  |
| value        |     | [String, Number] | false | ''      |
| name         |     | String           | false | /       |
| placeholder  |     | String           | false | '提示性文案' |
| autocomplete |     | String           | false | 'off'   |
| autofocus    |     | Boolean          | false | false   |
| maxlength    |     | Number           | false | /       |
| disabled     |     | Boolean          | false | false   |
| clearable    |     | Boolean          | false | false   |
| readonly     |     | Boolean          | false | false   |
| search       |     | Boolean          | false | false   |
| prependIcon  |     | String           | false | /       |
| appendIcon   |     | String           | false | /       |
| width        |     | String           | false | '200px' |

## methods

| 方法名             | 描述  |
| --------------- | --- |
| setCurrentValue |     |
| handleEnter     |     |
| handleInput     |     |
| focus           |     |
| blur            |     |
| handleFocus     |     |
| handleBlur      |     |
| handleClear     |     |
| handleSearch    |     |

## emits

| 事件名    | 描述  |
| ------ | --- |
| search |     |
| enter  |     |
| input  |     |
| focus  |     |
| blur   |     |

## slots

| 插槽名     | 描述  |
| ------- | --- |
| prepend | /   |
| append  | /   |
| 无       | /   |

    