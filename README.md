# Alexa Doorbell : AppDaemon App (HASS) :chicken:

<a href="https://www.buymeacoffee.com/ubhits" target="_blank">
<img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png"
     alt="Buy Me A Beer" 
     style="height:41px !important; width:174px !important;" />
</a>

Amazon Alexa will notify you like a doorbell, (thus the name, so creative aren't I!) based on a motion sensor placed on your doorway.

You can also :- 
- add a door sensor (like the [Ecolink Door Sensor](https://www.amazon.com/Aeotec-Window-Contact-sensors-Battery/dp/B07PDDX3K6/ref=sr_1_16?dchild=1&keywords=eco+wave+door+sensor&qid=1587791320&s=electronics&sr=1-16) or any other) to the setup to only ring the bell if the door is currently closed, and has been closed for the last 30 seconds or more. This is so that the bell only rings when someone arrives at your door and not when you step out.
- add an outdoor Alexa to greet your guest with a pleasant message based on the time of day
- add a doorbell (like the [Aeotec Doorbell](https://aeotec.com/z-wave-doorbell/) or any other) to ring when a guest arrives outside your door

Please ⭐ this repo if you like my work and also check out my other repos like
- [Home Assistant 'STEROIDS' Configuration](https://github.com/UbhiTS/ha-config-ataraxis)
- [Alexa Talking Clock](https://github.com/UbhiTS/ad-alexatalkingclock)

Also, if you want to see a walkthrough of my Home Assistant configuration, I have my video walkthrough on youtube below
- [Home Automation on 'STEROIDS' : Video Walkthrough](https://youtu.be/qqktLE9_45A)

## Installation
**NEEDS THE [Alexa Media Player](https://github.com/custom-components/alexa_media_player) HACS Integration from Keaton Taylor and Alan Tse**

Use [HACS](https://github.com/custom-components/hacs) or [download](https://github.com/UbhiTS/ad-alexatalkingclock) the `alexa_doorbell` directory from inside the `apps` directory to your local `apps` directory, then add the configuration to enable the `alexa_doorbell` module.

## App Configuration (config/appdaemon/apps/apps.yaml)

```yaml
alexa_doorbell:
  module: alexa_doorbell
  class: AlexaDoorbell
  door:
    motion_sensor: binary_sensor.main_door_motion
    #sensor: binary_sensor.main_door # optional
    #alexa: media_player.entryway_alexa # optional
  home:
    alexa: media_player.kitchen_alexa
    #doorbell: switch.living_room_doorbell # optional
  time:
    start: "07:00:00" # optional, default 7 AM
    end: "18:00:00" # optional, default 10 PM
```

key | optional | type | default | description
-- | -- | -- | -- | --
`module` | False | string | alexa_doorbell | The module name of the app.
`class` | False | string | AlexaDoorbell | The name of the Class.
`door > motion_sensor` | False | motion_sensor |  | The motion sensor to trigger the app.
`door > sensor` | True | binary_sensor |  | Set to trigger based on door status
`door > alexa` | True | media_player |  | Set to greet your guest with a pleasant greeting
`home > alexa` | False | media_player |  | The Alexa to notify inside the house
`home > doorbell` | True | switch |  | Set to ring this doorbell (or switch on a light) 
`time > start` | True | time | 07:00:00 | The time to enable the service. (24h format)
`time > end` | True | time | 22:00:00 | The time to disable the service. (24h format)

## Thank you!
This app wouldn't be possible without the amazing work done by the developers and community at **[Home Assistant](https://www.home-assistant.io/)**, and of Keaton Taylor and Alan Tse on their **Alexa Media Player integration** for Home Assistant. *https://github.com/custom-components/alexa_media_player*

Ever since we've set this up in our home, we always get praises and surprised looks from our guests when they come. Your home suddenly gets a voice, something like Jarvis ... awesome ! 

If you like my work and feel gracious, you can buy me a beer below ;)

<a href="https://www.buymeacoffee.com/ubhits" target="_blank">
<img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png"
     alt="Buy Me A Beer" 
     style="height:41px !important; width:174px !important;" />
</a>

# License
[Apache-2.0](LICENSE). By providing a contribution, you agree the contribution is licensed under Apache-2.0. This is required for Home Assistant contributions.
