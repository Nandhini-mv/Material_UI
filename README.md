# Material_UI

## List of Material UI Components

### Sliders

Sliders allow users to make selections from a range of values. We can adjust volume, brightness or use it for selection in e-commerce application. Lets see how to create Slider.

![MaterialSlider](https://user-images.githubusercontent.com/107906555/177477579-f558e7ee-9740-44a2-8788-aa4742e75f86.gif)


#### Import
```js
import { MaterialSlider, SliderModel, SliderType } from '@ohos/materialslider'
```

#### Usage
Access slider attributes through a object of SliderModel and customize the slider(if needed) using setter functions and finally pass the object to MaterialSlider.

 Below are list of properties available.
 | Properties   | Description | Type |
 | -------------| ------------| -----|
 | SliderType     |   Defined the type of the Slider         | SliderType Enum (Continue, Discrete)  |
 | SliderStyle |    Defines the style of the Slider       | SliderStyle Enum (InSet, OutSet)  |
 | min, max|    Defines the minimum and maximun values of the Slider       |  number           |
 |  step         |   Step of the slider              |   number    |
 | showSteps  |  Whether to display the current step    |   boolean (Default: false)   |
 | showTips   |  Displays the bubble to indicate the percentage while sliding   | boolean (Default: false)  |
 | showMin, showMax | Displays the minimum and maximum values on the screen  | boolean   |
 |  showValue  | Displays the value of the Slider on the screen  |  boolean  |
 | trackThickness  |  Defines the thickness of the track  |  number   |
 |  reverse   | Whether to display the slider values in reverse  |  boolean (Default: false)  |
 |  direction  |  Defines the direction of the slider (Horizontally or Vertically)  | Axis Enum (Horizontal, Vertical)   |
 | currentValue  |  Current progress of the slider   |  number   |
 |  blockColor   |  Color of the Slider   |  ResourceColor  |
 |  trackColor   |  Background color of the Slider   |  ResourceColor  |
 |  selectedColor   |  Color of the Slider rail that has been slid |  ResourceColor  |
 |           |             |              |
 
 Below are the events that are supported by Slider
| Name   | Description |
 | onSliderChange(callback: (value: number, mode: SliderChangeMode) => void)   |  Callback is invoked when the slider slides  <br /> **value** - Current Value of the Slider <br /> **mode** - Dragging state or Mode of the Slider (SliderChangeMode Enum - Begin, Moving, End)    |
 
#### Continuous Slider - Usage

##### Inset

```ets
//Creating object 
private sliderModel: SliderModel = new SliderModel(SliderType.Continue)
```

```ets
//Customization 
aboutToAppear(){
    this.sliderModel.setSliderStyle(SliderStyle.OutSet)
    this.sliderModel.setMin(100)
    this.sliderModel.setMax(1000)
    this.sliderModel.setStep(1)
    this.sliderModel.setCurrentValue(500)
    this.sliderModel.setShowSteps(false)
    this.sliderModel.setShowTips(true)
    this.sliderModel.setTrackThickness(8)
    this.sliderModel.setReverse(false)
    this.sliderModel.setDirection(Axis.Horizontal)
    this.sliderModel.setShowValue(true)
    this.sliderModel.setShowMin(false)
    this.sliderModel.setShowMax(false)
    this.sliderModel.setBlockColor("#ff0477ff")
    this.sliderModel.setTrackColor("#D0D0D0")
    this.sliderModel.setSelectedColor("#ff0477ff")
}    
```

```ets
//Passing parameters to MaterialSlider
MaterialSlider({
    obj : this.sliderModel,
    onCheckChange: this.onCheckChange
})
```
