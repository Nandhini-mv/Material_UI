# Material_UI

## List of Material UI Components

### Sliders

Sliders allow users to make selections from a range of values. We can adjust volume, brightness or use it for selection in e-commerce application. Lets see how to create Slider.

##### Import
```js
import { MaterialSlider, SliderModel, SliderType } from '@ohos/materialslider'
```

##### Usage
Access slider attributes through a object of SliderModel and customize the slider(if needed) using setter functions and finally pass the object to MaterialSlider.

 Below are list of properties available.
 | Properties   | Description | Type |
 | -------------| ------------| -----|
 | SliderType     |   Defined the type of the Slider         | SliderType Enum (Continue, Discrete)
 | SliderStyle |    Defines the style of the Slider       | SliderStyle Enum (InSet, OutSet)
 | min, max|    Defines the minimum and maximun values of the Slider       |  number           |
 |  step         |   Step of the slider              |   number    |
 | showSteps  |  Whether to display the current step    |   boolean    |
