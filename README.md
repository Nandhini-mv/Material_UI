# Material_UI

## List of Material UI Components

## Sliders

**Material Sliders** allow users to make selections from a range of values. Sliders allow users to view and select a value (or range) from the range along a bar. They’re ideal for adjusting settings such as volume, brightness, for applying image filters or use it for selection in e-commerce application. Changes made with sliders are immediate, allowing the user to make slider adjustments while determining a selection. A Typical Material Slider looks as shown below.

![Slider_Intro](https://user-images.githubusercontent.com/107906555/178949661-78c2fdc1-b00a-4e6a-ac30-712461026997.jpg)

The Library can be referred from [here](https://github.com/Applib-OpenHarmony/MaterialSliders)

## Benefits

* Changes in value is reflected immediately.
* 4 variants are available.
* Slider properties are customisable according to the requirement.

## List of Features
The features of Slider implemented are listed below.

| Feature   | Display | Description |
| -------------| ------------| -----|
|  Reverse Slider  |![Feature1](https://user-images.githubusercontent.com/107906555/179450124-d3aa73c6-97b0-430e-9de6-a625777c99ef.jpg)  |  Slider can be moved in the reverse direction  |
|  Horizontal/Vertical Slider  | ![Feature 2](https://user-images.githubusercontent.com/107906555/179450433-80e84510-2fdd-4fe5-847f-1e6e8465d2da.jpg)  |  Slider can be viewed in the vertical direction as well  |
| Show Tips  |  ![Feature 3](https://user-images.githubusercontent.com/107906555/179450717-c4de0b8b-3ef7-49b4-9155-0d924ad7a1d2.jpg)  |  Tool Tip can be shown to display the percentage of the slider that has been slid  |

## Download and Install

To use MaterialSlider component for OpenHarmony, please use the below instruction

```js
npm i @ohos/MaterialSlider
```

Details about OpenHarmony NPM environment configuration, click [here](https://gitee.com/openharmony-tpc/docs/blob/master/OpenHarmony_npm_usage.md)

## Usage Instructions
Import the Slider Library. Then, access slider attributes through a object of SliderModel and customize the Slider using setter functions and finally pass the object to MaterialSlider.

```js
import { MaterialSlider, SliderModel, SliderType } from '@ohos/materialslider'
```

 Below are list of properties available which can be customized using the SliderModel object (setter methods).
 | Properties   | Description | Type |
 | -------------| ------------| -----|
 | SliderType     |   Defined the type of the Slider         | SliderType Enum (Continue, Discrete)  |
 | SliderStyle |    Defines the style of the Slider       | SliderStyle Enum (InSet, OutSet)  |
 | min, max|    Defines the minimum and maximun values of the Slider       |  number           |
 |  step         |   Step of the slider              |   number    |
 | showSteps  |  Whether to display the current step    |   boolean (Default: false)   |
 | showTips   |  Displays the bubble to indicate the percentage while sliding   | boolean (Default: false)  |
 | showMin, showMax | Displays the minimum and maximum values on the screen  | boolean (Default: false)  |
 |  showValue  | Displays the value of the Slider on the screen  |  boolean (Default: false)  |
 | trackThickness  |  Defines the thickness of the track  |  number   |
 |  reverse   | Whether to display the slider values in reverse  |  boolean (Default: false)  |
 |  direction  |  Defines the direction of the slider (Horizontally or Vertically)  | Axis Enum (Horizontal, Vertical)   |
 | currentValue  |  Current progress of the slider   |  number   |
 |  blockColor   |  Color of the Slider   |  ResourceColor  |
 |  trackColor   |  Background color of the Slider   |  ResourceColor  |
 |  selectedColor   |  Color of the Slider rail that has been slid |  ResourceColor  |
 |           |             |              |
 
 Below is the event that is supported by Material Slider
 | Name   | Description |
 | -------------| ------------|
 | onSliderChange(callback: (value: number, mode: SliderChangeMode) => void)   |  Callback is invoked when the slider slides  <br /> **value** - Current Value of the Slider <br /> **mode** - Dragging state or Mode of the Slider (SliderChangeMode Enum - Begin, Moving, End)    |
 
## Slider Implementation with UseCases

### Continuous Slider

Continuous sliders allow users to make selections that don’t require a specific value. These sliders are often used to adjust brightness or volume. A Pictorial representation of the Continuous Slider with its design parameters is shown below.

<img width="499" alt="1_Continuous_slider_measurements" src="https://user-images.githubusercontent.com/107906555/177693805-b6afbc1c-2367-4921-b110-69999d12b358.PNG">

The image shows the measurement of the Continuous Slider to be followed (i.e.) the Slider diameter and track size (both unselected and selected part). The two variants of Continuous Slider are described below.

##### OutSet

```js
//Creating object of the SliderModel class with Slider type as Continue
private sliderModel: SliderModel = new SliderModel(SliderType.Continue)

//Customization of the SliderModel object and mentioning the SliderStyle as OutSet
aboutToAppear(){
    this.sliderModel.setSliderStyle(SliderStyle.OutSet)
    this.sliderModel.setMin(100)
    this.sliderModel.setMax(1000)
    this.sliderModel.setStep(1)
    this.sliderModel.setCurrentValue(500)
    this.sliderModel.setShowSteps(false)
    this.sliderModel.setShowTips(true)
    this.sliderModel.setTrackThickness(6)
    this.sliderModel.setReverse(false)
    this.sliderModel.setDirection(Axis.Horizontal)
    this.sliderModel.setShowValue(true)
    this.sliderModel.setShowMin(false)
    this.sliderModel.setShowMax(false)
    this.sliderModel.setBlockColor("#ff0477ff")
    this.sliderModel.setTrackColor("#D0D0D0")
    this.sliderModel.setSelectedColor("#ff0477ff")
}    

//Passing SliderModel object to MaterialSlider and defining the Event onSliderChange
MaterialSlider({
      obj: this.sliderModel1,
      onSliderChange:((value: number, mode: SliderChangeMode) => {
           console.log("Value: " + value + " Mode: " + mode);
      })
})
```

![ContinuousOutset](https://user-images.githubusercontent.com/107906555/177507023-7415aa49-1236-4663-b893-fc96d76d5664.jpg)

##### InSet

```js
//Creating object of the SliderModel class with Slider type as Continue 
private sliderModel: SliderModel = new SliderModel(SliderType.Continue)

//Customization of the SliderModel object and mentioning the SliderStyle as InSet
aboutToAppear(){
    this.sliderModel.setSliderSliderStyle(SliderStyle.InSet)
    this.sliderModel.setMin(0)
    this.sliderModel.setMax(100)
    this.sliderModel.setStep(1)
    this.sliderModel.setCurrentValue(40)
    this.sliderModel.setShowSteps(false)
    this.sliderModel.setShowTips(true)
    this.sliderModel.setTrackThickness(6)
    this.sliderModel.setReverse(false)
    this.sliderModel.setDirection(Axis.Horizontal)
    this.sliderModel.setShowValue(true)
    this.sliderModel.setShowMin(false)
    this.sliderModel.setShowMax(false)
    this.sliderModel.setBlockColor(Color.White)
    this.sliderModel.setTrackColor("#D0D0D0")
    this.sliderModel.setSelectedColor("#ff0477ff")
}    

//Passing SliderModel object to MaterialSlider and defining the Event onSliderChange
MaterialSlider({
      obj: this.sliderModel1,
      onSliderChange:((value: number, mode: SliderChangeMode) => {
           console.log("Value: " + value + " Mode: " + mode);
      })
})
```
![ContinuousInset](https://user-images.githubusercontent.com/107906555/177507103-2f7b4bbb-84a6-41ee-ad4d-f36e6f0d2362.jpg)

### Discrete Slider
Discrete sliders display a numeric value label upon pressing the thumb, allowing users to input an exact value. Discrete sliders only allow predefined sets of options or values to be selected. These sliders are often used in scenarios where there are pre-defined values available like choosing shoe size or any clothing size, etc. A Pictorial representation of the Discrete Slider with its design parameters is shown below.

<img width="446" alt="2_Discrete_slider_measurements" src="https://user-images.githubusercontent.com/107906555/177693881-7aaa178c-4da7-4504-b32f-23a2a9191bec.PNG">

The image shows the measurement of the Discrete Slider to be followed (i.e.) the Slider diameter and track size (both unselected and selected part). The two variants of Discrete Slider are described below.

##### OutSet

```js
//Creating object of the SliderModel class with Slider type as Discrete 
private sliderModel: SliderModel = new SliderModel(SliderType.Discrete)

//Customization of the SliderModel object and mentioning the SliderStyle as OutSet
aboutToAppear(){
    this.sliderModel.setSliderStyle(SliderStyle.OutSet)
    this.sliderModel.setMin(1000)
    this.sliderModel.setMax(10000)
    this.sliderModel.setStep(1000)
    this.sliderModel.setCurrentValue(3000)
    this.sliderModel.setShowSteps(true)
    this.sliderModel.setShowTips(true)
    this.sliderModel.setTrackThickness(6)
    this.sliderModel.setReverse(false)
    this.sliderModel.setDirection(Axis.Horizontal)
    this.sliderModel.setShowValue(true)
    this.sliderModel.setShowMin(false)
    this.sliderModel.setShowMax(false)
    this.sliderModel.setBlockColor("#ff0477ff")
    this.sliderModel.setTrackColor("#D0D0D0")
    this.sliderModel.setSelectedColor("#ff0477ff")
}    

//Passing SliderModel object to MaterialSlider and defining the Event onSliderChange
MaterialSlider({
      obj: this.sliderModel1,
      onSliderChange:((value: number, mode: SliderChangeMode) => {
           console.log("Value: " + value + " Mode: " + mode);
      })
})
```
![DiscreteOutset](https://user-images.githubusercontent.com/107906555/177507151-c2e55b30-3e3a-48fc-92b7-20f9cb4be7a8.jpg)

##### InSet

```js
//Creating object of the SliderModel class with Slider type as Discrete 
private sliderModel: SliderModel = new SliderModel(SliderType.Discrete)

//Customization of the SliderModel object and mentioning the SliderStyle as InSet
aboutToAppear(){
    this.sliderModel.setSliderStyle(SliderStyle.InSet)
    this.sliderModel.setMin(0)
    this.sliderModel.setMax(100)
    this.sliderModel.setStep(10)
    this.sliderModel.setCurrentValue(50)
    this.sliderModel.setShowSteps(true)
    this.sliderModel.setShowTips(true)
    this.sliderModel.setTrackThickness(6)
    this.sliderModel.setReverse(false)
    this.sliderModel.setDirection(Axis.Horizontal)
    this.sliderModel.setShowValue(true)
    this.sliderModel.setShowMin(true)
    this.sliderModel.setShowMax(true)
    this.sliderModel.setBlockColor(Color.White)
    this.sliderModel.setTrackColor("#D0D0D0")
    this.sliderModel.setSelectedColor("#ff0477ff")
}    

//Passing SliderModel object to MaterialSlider and defining the Event onSliderChange
MaterialSlider({
      obj: this.sliderModel1,
      onSliderChange:((value: number, mode: SliderChangeMode) => {
           console.log("Value: " + value + " Mode: " + mode);
      })
})           
```
![DiscreteInset](https://user-images.githubusercontent.com/107906555/177507177-f524121a-2845-4914-85c8-6176fe8e4483.jpg)

## Conclusion
Thus, Material Slider can be used for various application/requirement. Material Slider implemented here is in OpenHarmony API version 9 and above. 

## Snackbar
**Snackbars** provide brief messages about app processes at the bottom of the screen. Snackbar informs the user that the application has performed or will be performing certain task. They appear at the bottom of the screen for a brief time. They do not interfere in user experience and do not wait for user input to disappear. A Snackbar can contain a single action that is optional. A typical Snackbar looks as shown below.

![intro](https://user-images.githubusercontent.com/107906555/179459753-d90bc438-340e-4123-8368-c2378e303cfa.jpg)

The Library can be referred from [here](https://github.com/Applib-OpenHarmony/MaterialSnackbar)

## Benefits
* Provides information about the process being performed.
* Helps us to take appropriate action based on the outcome of the process.

## List of Features
The features of Snackbar implemented are listed below.

| Feature   | Display | Description |
| -------------| ------------| -----|
| Customised Action  | ![intro](https://user-images.githubusercontent.com/107906555/179492375-6b43e330-bb27-4cef-97e5-950e61a8a4db.jpg)  | Button can have customised text and action based on the requirement  |
|  Timer  |       |  The time for which Snackbar is visible can be altered  |
|  Opacity  |       |  The opacity of the Snackbar can be customised  |

### Download and Install

To use MaterialSnackbar component for OpenHarmony, please use the below instruction

```js
npm i @ohos/materialsnackbar
```

Details about OpenHarmony NPM environment configuration, click [here](https://gitee.com/openharmony-tpc/docs/blob/master/OpenHarmony_npm_usage.md)

## Usage Instructions
Import the Snackbar Library. Then, access Snackbar attributes through a object of SnackBarModel and customize the Snackbar using setter functionS and finally pass the object to MaterialSnackBar and action associated with optional action button.

```js
import { MaterialSnackBar, SnackBarModel, SnackBarType }  from "@ohos/materialsnackbar"
```

 Below are list of properties available.
 | Properties   | Description | Type |
 | -------------| ------------| -----|
 | snackBarType  | Defines the type of the Snackbar | SnackBarType Enum (SimpleSnack, OneLineActionSnack, TwoLineActionSnack, BigTwoLineActionSnack)  |
 | snacBarText  |  Text associated with the Snackbar  | String  |
 | buttonText  |  Defines the text of the Snackbar button  | String |
 | show   |  Defines the visibility of the Snackbar  |  Visibility Enum (Visible, None) |
 | timer | Defines the number of seconds the Snackbar will be visible | number (Default: 4000ms) |
 | snackBackColor  |  Background Color of the Snackbar  |  ResourceColor  |
 | snackTextColor  |  Defines the color of the Snackbar text  | ResourceColor  |
 | buttonTextColor  | Defines the color of the button text | ResourceColor  |
 | opacity  | Defines the opacity of the Snackbar  |  number (values range from 0-1) |
 |          |               |             |
 
 ## Snackbar implementation with UseCases
 
 ### Simple Snack
 This is a Simple snackbar with just a message. There is no action associated with this type. The Picture describing the design parameters are shown below.
 
 <img width="593" alt="1_Text Snackbar_measurements" src="https://user-images.githubusercontent.com/107906555/177966156-fe97cc87-33a4-4eb9-bbc2-d57c2f623b1f.PNG">

##### Implementation

```js
//Creating SnackBarModel object with the SnackBarType as SimpleSnack
@State snackBarModel1: SnackBarModel = new SnackBarModel(SnackBarType.SimpleSnack)

//Customization of the model object with appropriate values
aboutToAppear(){
    this.snackBarModel1.setSnackBarText("Text associated with SimpleSnack") 
    this.snackBarModel1.setSnackTextColor("#ffffff")
    this.snackBarModel1.setSnackBackColor("#9400D3")
    this.snackBarModel1.setOpacity(1)
    this.snackBarModel1.setTimer(4000)
}

//Passing SnackBarModel object to MaterialSnackBar component
MaterialSnackBar({
    obj : this.snackBarModel1
})
```

![SimpleSnack](https://user-images.githubusercontent.com/107906555/177968379-34ed90a3-cf41-4632-b278-339a397d3890.png)
 
### One Line Action Snackbar
This is a Snackbar with a one line message and a action associated with it. The Picture describing the design parameters are shown below.

<img width="612" alt="2_Text Snackbar_Action_measurements" src="https://user-images.githubusercontent.com/107906555/177967519-b4f4681d-7b51-4f72-a464-51a6846c83ac.PNG">

##### Implementation

```js
//Creating SnackBarModel object with the SnackBarType as OneLineActionSnack
@State snackBarModel2: SnackBarModel = new SnackBarModel(SnackBarType.OneLineActionSnack)

//Defining the Action for the Snackbar Button
  SnackButtonAction: () => void = function () {
    console.log("test")
  }

//Customization of the model object with appropriate values
aboutToAppear(){
    this.snackBarModel2.setSnackBarText("Text of OneLineActionSnack")
    this.snackBarModel2.setSnackTextColor("#ffffff")
    this.snackBarModel2.setSnackBackColor("#9400D3")
    this.snackBarModel2.setOpacity(1)
    this.snackBarModel2.setTimer(4000)
    this.snackBarModel2.setButtonText("ACTION")        
    this.snackBarModel2.setButtonTextColor("#ECD540")
}
//Passing SnackBarModel object to MaterialSnackBar component
MaterialSnackBar({
   obj : this.snackBarModel2,
   func : this.SnackButtonAction
})
```

![OneLineActionSnack](https://user-images.githubusercontent.com/107906555/177968467-3baa3ddc-cd79-42aa-a446-8236f3eda64e.png)

### Two Line Action Snackbar
This is a Snackbar with two line message and an action associated with it. The Picture describing the design parameters are shown below.

<img width="620" alt="3_Two line Text Snackbar_measurements" src="https://user-images.githubusercontent.com/107906555/177990529-d73eae20-5a41-4ac6-8583-99b58f8f1f89.PNG">

##### Implementation

```js
//Creating SnackBarModel object with the SnackBarType as TwoLineActionSnack
@State snackBarModel3: SnackBarModel = new SnackBarModel(SnackBarType.TwoLineActionSnack)

//Defining the Action for the Snackbar Button
  SnackButtonAction: () => void = function () {
    console.log("test")
  }

//Customization of the model object with appropriate values
aboutToAppear(){
    this.snackBarModel3.setSnackBarText("Longer text associated with TwoLineActionSnack") 
    this.snackBarModel3.setSnackTextColor("#ffffff")
    this.snackBarModel3.setSnackBackColor("#9400D3")
    this.snackBarModel3.setOpacity(1)
    this.snackBarModel3.setTimer(4000)
    this.snackBarModel3.setButtonText("ACTION")                                           
    this.snackBarModel3.setButtonTextColor("#ECD540")
}

//Passing SnackBarModel object to MaterialSnackBar component
MaterialSnackBar({
    obj : this.snackBarModel3,
    func : this.SnackButtonAction
})
```
![TwoLineActionSnack](https://user-images.githubusercontent.com/107906555/177991342-4fd7c8e2-c95b-484c-a206-d66dcdde719f.png)

### Big Line Action Snackbar
This is a Snackbar with two line text and a longer action text. The Picture describing the design parameters are shown below.

<img width="616" alt="4_Two line Text Snackbar_Action_measurements" src="https://user-images.githubusercontent.com/107906555/177991701-c8bdd372-4015-4fbd-9857-6792cea92b8c.PNG">

##### Implementation

```js
//Creating SnackBarModel object with the SnackBarType as BigTwoLineActionSnack
@State snackBarModel4: SnackBarModel = new SnackBarModel(SnackBarType.BigTwoLineActionSnack)

//Defining the Action for the Snackbar Button
  SnackButtonAction: () => void = function () {
    console.log("test")
  }

//Customization of the model object with appropriate values
aboutToAppear(){
    this.snackBarModel4.setSnackBarText("Longer text associated with   BigTwoLineActionSnack") 
    this.snackBarModel4.setSnackTextColor("#ffffff")
    this.snackBarModel4.setSnackBackColor("#9400D3")
    this.snackBarModel4.setOpacity(1)
    this.snackBarModel4.setTimer(4000)
    this.snackBarModel4.setButtonText("LONGER ACTION")                                         
    this.snackBarModel4.setButtonTextColor("#ECD540")
}

///Passing SnackBarModel object to MaterialSnackBar component
MaterialSnackBar({
          obj : this.snackBarModel4,
          func : this.SnackButtonAction
        })
```  

![BigTwoLineActionSnack](https://user-images.githubusercontent.com/107906555/177992100-5301e50c-16ce-4498-a97e-0aa3934dc578.png)

## Conclusion
Snackbar, which show brief messages about the process with an optional action, can be implemented in OpenHarmony as shown above. 

## Backdrop
A **backdrop** appears behind all other surfaces in an app, displaying contextual and actionable content. A Backdrop has two surfaces.

1. Back Layer
2. Front Layer

Back layer displays actions and context that controls the Front layer's content. When concealed, the back layer can provide contextual information about the front layer. When revealed, the back layer displays contextual controls that relate to the front layer. Back layer content can be navigational, changing the content displayed on the front layer. A typical Backdrop is shown below.

![intro](https://user-images.githubusercontent.com/107906555/179497409-63047084-4e85-4841-a04d-b1807b737c8e.jpg)

The Library can be referred from [here](https://github.com/Applib-OpenHarmony/MaterialBackdrop)

## Benefits
* Backlayer is persistent that displays controls and content related to front layer.
* Filtering of front layer content made easy
* Focuses attention on one layer at a time.

## List of Features
The features of Backdrop implemented are listed below.

| Feature   |  Description |
| ----------| -----|
| Customisable UI |  The Front Layer and Back Layer can have customisable UI based on the requirements  |
|  Triggering Element  | User can choose the triggering element for revealing and concealing the Backdrop  |

## Download and Install

To use MaterialBackdrop component for OpenHarmony, please use the below instruction

```js
npm i @ohos/materialbackdrop
```

Details about OpenHarmony NPM environment configuration, click [here](https://gitee.com/openharmony-tpc/docs/blob/master/OpenHarmony_npm_usage.md)

## Usage Instructions

Import the Backdrop Library. Create a object of BackdropModel class using appropriate type of Backdrop. Create two UI which will act as front layer and back layer and pass them along with the BackdropModel object to the library.

```js
import { Backdrop, BackdropModel, BackDropState, BackdropType }  from '@ohos/materialbackdrop'
```

Below are list of properties available in BackdropModel
| Properties   | Description | Type |
| -------------| ------------| -----|
| backdropType | Specifies the type of the Backdrop  |  BackdropTyp Enum (Model1, Model2)  |
|  backContentHeight  |  Mentiones the height of the back content | Length |
|   |    |

## Backdrop Implemntation with UseCases

### Model1

Model 1 of Backdrop is where the Front Layer is fully concealed when Back Layer is revealed. The Pictures describing the design parameters are shown below.

<img width="404" alt="1_Back Drop_measurements" src="https://user-images.githubusercontent.com/107906555/179502254-be6bfce2-f2be-485e-82f1-8469257b9c2a.PNG">

<img width="428" alt="2_Back Drop_bottom_measurements" src="https://user-images.githubusercontent.com/107906555/179503006-5ef93aed-3ee3-49fd-94d0-8d725a19b494.PNG">

##### Implementation

```js
//Creating object of BackdropModel
private model: BackdropModel = new BackdropModel(BackdropType.Model1)

//UI for Back layer
@Builder backPage():any {
    .
    .
    triggerringElement(){
        .
        .
        }.onClick(()=>{
            //Change BackDropState
            triggerBackdrop(this.flag)   //pass value of BackdropState
            })
    .
    .
}

//UI for Front layer    
@Builder frontPage():any {
    .
    .
    //Add triggerring element if needed
    .
}   

//Passing parameters to Backdrop component
Backdrop({
        obj: $model,
        backLayout: this.backPage(),
        frontLayout: this.frontPage()
})
```

![4](https://user-images.githubusercontent.com/107906555/179505230-9e204169-d756-4f63-ba67-1c0a34a8505d.gif)

### Model2

Model 2 of Backdrop is where the Front Layer is only half concealed when Back Layer is revealed. 

##### Implementation
Create and pass UIs as mentioned in Model 1. The difference of model 2 can be noticed when the back content height is less than the whole screen height.

```js
//Creating object of BackdropModel
private model: BackdropModel = new BackdropModel(BackdropType.Model2)

//Setting the content height
aboutToAppear() {
  this.backdrop.setBackContentHeight('176vp')
}
  
//UI for Back layer
@Builder backPage():any {
    .
    .
    triggerringElement(){
        .
        .
        }.onClick(()=>{
            //Change BackDropState
            triggerBackdrop(this.flag)   //pass value of BackdropState
            })
    .
    .
}
    
//UI for Front layer
@Builder frontPage():any {
    .
    .
    //Add triggerring element if needed
    .
    .
}   
    
//Passing parameters to Backdrop component
Backdrop({
        obj: $model,
        backLayout: this.backPage(),
        frontLayout: this.frontPage()
})
```

![5](https://user-images.githubusercontent.com/107906555/179506902-f8fbc169-a0da-4f4d-85fb-e267304c7168.gif)

## Conclusion
This library is a solution for applications like e-commerce where the backdrop implementation is much needed for display of products and filter. Material Backdrop implemented here is in OpenHarmony API version 9 and above. 

## Banners
Banners display important message and provides user action to address or dismiss the banner. Banners are displayed at the top of the screen below the app bar. They are persistent, allowing the user to ignore them or interact with them when needed. Only one banner should be displayed at a time. A Typical Material Banner looks as shown below.

![intro](https://user-images.githubusercontent.com/107906555/179958700-18e614b6-aab5-4d1f-99b4-d3b41780ed58.jpg)

The Library can be referred from [here](https://github.com/Applib-OpenHarmony/MaterialBanners)

## Benefits
* Banners contain a single message and subsequent action the user can take. This makes the banner message more clear.

## List of features
The features of Banner implemented are listed below.

| Feature   | Description |
| -------------| -----|
| Banner Type  |  Type of the banner can be changed according to the requirement |
| Visibility | The Visibility can be changed according to the requirement  |

## Download and Install

To use MaterialBanner component for OpenHarmony, please use the below instruction

```js
npm i @ohos/material-banner
```

Details about OpenHarmony NPM environment configuration, click [here](https://gitee.com/openharmony-tpc/docs/blob/master/OpenHarmony_npm_usage.md)

## Usage Instructions
Import the banner library. Access banner attributes using an object of BannerModel and customize the banner using setter functions and finally pass the object to MaterialBanner.

```js
import {MaterialBanner,BannerType,BannerModel} from '@ohos/material-banner'
```

Below are the list of properties available for MaterialBanner.
| Properties   | Description | Type |
| -------------| ------------| -----|
| bannerType  |  Defines the type of the banner  |  BannerType Enum (OneButton, TwoButton, ImageButton)  |
|  bannerMessage  | Specifies the message of the banner  |  string |
|  buttonText1  |  Text associated with 1st button of the Banner  |  string  |
|  buttonText2  |  Text associated with 2nd button of the Banner  |  string  |
|  buttonColor  |  Color of the Banner Button   |  string or ResourceColor  |
|  textSize  | Size of the Banner text  |  string  |
|  textStyle  | Style of the Banner text  | string  |
| image  |  Specifies the url of the image  | Resource  |
| show  |  Defines the Visibility of the Banner  | Visibility  |
|     |      |     |

## Banner Implementation with Usecases

### One Button Banner
This type of Banner has a message and one button associated with it. The picture describing the design parameters are shown below.

<img width="432" alt="1_Banner_one-line_measurements" src="https://user-images.githubusercontent.com/107906555/178465214-31745e76-bf9b-4082-af36-87659cdb9b6f.PNG">

##### Implementation

```js
//Creating object of BannerModel with BannerType as OneButton
private bannerModel1:BannerModel=new BannerModel(BannerType.OneButton)

//Banner Button Function
BannerFunc: () => void= function () {
   console.log("WiFi turned On")
}

//Setting the model object parameters with appropriate values
aboutToAppear(){  
  this.bannerModel1.setBannerMessage("Message Text");  
  this.bannerModel1.setButtonText1("ACTION")  
  this.bannerModel1.setButtonColor("#317AFF")  
  this.bannerModel1.setTextSize('20fp')  
  this.bannerModel1.setTextStyle('calibri')
}

//Passing BannerModel object to MaterialBanner component
MaterialBanner({  
  bModel: this.bannerModel1,  
  buttonAction1: this.BannerFunc  
})
```

![Banner1](https://user-images.githubusercontent.com/107906555/179961870-15335c2d-4d3f-471e-9b3a-ee4bb9fec587.jpg)

### Two Button Banner
This type of Banner has a message and two buttons associated with it. The picture describing the design parameters are shown below.

<img width="424" alt="2_Banner_Two-line_measurements" src="https://user-images.githubusercontent.com/107906555/178469557-2b1a7713-5c5b-4adc-b8b4-7cccd41650fe.PNG">

##### Implementation

```js
//Creating object of BannerModel with BannerType as TwoButton
private bannerModel2:BannerModel=new BannerModel(BannerType.TwoButton)

//Setting Banner Button Functions
BannerFunc1: () => void= function () {
   console.log("Logged in as Guest")
}
BannerFunc2: () => void= function () {
   console.log("Sign in details")
}
  
//Setting the model object parameters with appropriate values
aboutToAppear(){  
  this.bannerModel2.setBannerMessage("Message Text");  
  this.bannerModel2.setButtonText1("ACTION1")  
  this.bannerModel2.setButtonText2("ACTION2")  
  this.bannerModel2.setButtonColor("#317AFF")  
  this.bannerModel2.setTextSize('16fp')  
  this.bannerModel2.setTextStyle('calibri')
}

//Passing BannerModel object to MaterialBanner component
MaterialBanner({  
  bModel: this.bannerModel2,  
  buttonAction1: this.BannerFunc1,  
  buttonAction2: this.BannerFunc2  
})
```

![Banner2](https://user-images.githubusercontent.com/107906555/179962001-283cc473-3662-4647-819a-2a56c3077508.jpg)

### Image Banner
Banner message here is supplemented with a supporting illustration (image). The picture describing the design parameters are shown below.

<img width="423" alt="3_Banner_Two-line_image_measurements" src="https://user-images.githubusercontent.com/107906555/179962315-0b99982e-4b39-4be3-8a57-96f236d1934e.PNG">

##### Implementation

```js
//Creating object of BannerModel with BannerType as TwoButton
private bannerModel3:BannerModel=new BannerModel(BannerType.ImageButton)

//Setting Banner Button Functions
BannerFunc3:()=>void=function(){
  console.log("Learn More")
}
BannerFunc4:()=>void=function(){
  console.log("Fix it")
}
  
//Setting the model object parameters with appropriate values
aboutToAppear(){  
  this.bannerModel2.setBannerMessage("Message Text");  
  this.bannerModel2.setButtonText1("ACTION1")  
  this.bannerModel2.setButtonText2("ACTION2")  
  this.bannerModel2.setButtonColor("#317AFF")  
  this.bannerModel2.setTextSize('16fp')  
  this.bannerModel2.setTextStyle('calibri')
  this.bannerModel3.setImage(this.image)
}

//Passing BannerModel object to MaterialBanner component
MaterialBanner({  
  bModel: this.bannerModel3,  
  buttonAction1: this.BannerFunc3,  
  buttonAction2: this.BannerFunc4  
})
```

![Banner3](https://user-images.githubusercontent.com/107906555/179963136-3cc96df9-3cde-4d85-9f7b-ee24dec967d7.jpg)

## Conclusion
Banners convey messages and related action and are persistent allowing users to ignore them. Here, we have implemented Banners in OpenHarmony API version 9.
