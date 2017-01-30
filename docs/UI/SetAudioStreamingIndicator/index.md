## SetAudioStreamingIndicator

Type
: Function

Sender
: SDL

Purpose
: Set the icon properly to the current audio playback of the application.

### Description

The Play/Pause button of the media application shall be able to show one of the following icons:
   - Play/Pause (currently used icon);   
   - Play (a play only icon);   
   - Pause (a pause only icon).   

The default icon for the Play/Pause button shall be the Play/Pause icon (PLAY_PAUSE).
The default icon must be set to the button, when the media application:
   - is newly registered on the head unit (after _RegisterAppInterface_).
   - was closed by the user (Application enters HMI_NONE)."
   
The request may arrive in both cases when the application is active or in background on HMI (depends on Policy Table permissions applicable to mobile application request, by default allowed to operate in all HMI levels except of NONE).

### Request
#### Behavior

The icon of the Play/Pause button shall be modifiable by the media application by sending a RPC Request called _audioStreamingIndicator_.

_**Note:**_    
_SDL must transfer _SetAudioStreamingIndicator_request_ from mobile application to HMI in case no any failures._   
_SDL must transfer HMI's response to mobile application._ 

#### Parameters

|Name|Type|Mandatory|
|:---|:---|:--------|
|audioStreamingIndicator|[Common.AudioStreamingIndicator]|true|
[Common.AudioStreamingIndicator]: https://github.com/DrachenkoAnastasiia/sdl_hmi_integration_guidelines/blob/new_setaudiostreamingindicator/docs/Common/Enums/index.md#audiostreamingindicator

### Response

_SetAudioStreamingIndicator_Response_ must return:   
    - SUCCESS when the Play/Pause button is set to the desired icon;   
    - IGNORED when the Play/Pause button was already set to the desired icon;   
    - DISALLOWED when the RPC is used in an invalid HMI level.   

#### Parameters

This RPC has no additional parameter requirements.

### Sequence Diagrams

_SetAudioStreamingIndicator_ for active application with _AudioStreamingIndicator_.   

![SetAudioStreamingIndicator](./assets/setAudioStreamInd_Gen.png)

### Example Request

```
{
  "id": 29,
  "jsonrpc":"2.0",
  "method" : “UI.SetAudioStreamingIndicator",
  "params":{ "audioStreamingIndicator" : "PLAY"}
}

```

### Example Response
```
{
  "id":29,
  "jsonrpc":"2.0", 
  "result":{"method":" UI.SetAudioStreamingIndicator ",
  "code":0}
}
```