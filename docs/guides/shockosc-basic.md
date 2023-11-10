# ShockOsc - Basic Setup

!!! Warning
    **Don't wear the shocker somewhere near your neck or your heart.**  
    Check out [Safety](../safety/safety-rules.md) for more information.  
    
## What you need

- [Fully setup shocker](openshock-first-setup.md)
- [Newest ShockOSC](https://github.com/OpenShock/ShockOsc/releases)
- Text Editor, [Notepad++](https://notepad-plus-plus.org/) for example

## Setup ShockOSC
1. Download and store the ``ShockOsc.exe`` file at your desired location on your PC.  
   (at the moment there are two ShockOsc.exe files to download, you only need the ``OpenShock.ShockOsc.exe``)  
2. Start the .exe for the first time, this will generate a ``config.json`` file in the same location as the .exe, press any button to close the window again.
3. Now open ``config.json`` in a text editor, we need to configure two things , your ``API Token`` and your ``Shocker ID``.  
Both can be found in your account on [Shocklink.net](https://shocklink.net/)

!!! Info "Configure the API Token"

    <details>
      On the Shocklink page go to <code>API Tokens</code>.<br>
      <img src="../../static/guides/shockosc/finds_apitokens.png" alt="find api token"><br>
      <br></br>
      Press the <code>green plus</code> at the bottom.<br>
      <img src="../../static/guides/shockosc/green_plus.png" alt="create api token"><br>
      <br></br>
      Give it a name, for example "ShockOSC" and set no expiry date, after that click create.<br>
      <img src="../../static/guides/shockosc/create_APIToken.png" alt="create api token 2"><br>
      <br></br>
      Copy the API Token and paste it into the config at <code>"ApiToken":</code>, after that it should look like this:<br>
      <code>"ApiToken": "0W3ybn7bHuF2SUwAZ8YZexRMejzTcUzJJT3cBSf4FWK7ryLhRT2wikFh8qZGYpiY"</code>.<br>
      <img src="../../static/guides/shockosc/API_Token.png" alt="copy api token"><br>
    </details>


!!! Info "Configure the Shocker ID"

    <details>
      On the Shocklink page, go to <code>Shockers</code><br>
      <img src="../../static/guides/shockosc/find_shockers.png" alt="find shockers"><br>
      <br></br>
      Open the context menu of the shocker you want to use<br>
      <img src="../../static/guides/shockosc/find_shockerid.png" alt="find shocker id"><br>
      <br></br>
      Click on edit, and copy the ID<br>
      <img src="../../static/guides/shockosc/find_shockerid2.png" alt="find shocker id 2"><br>
      In your config you have to create a list for your shockers, there you have to paste your Shocker ID<br>
      It should look something like this at the end:<br>
    <code>
      <pre>
          "Shockers": {
            "SHOCKERNAME": "18b1d0e6a-f9a0-4e93-9812-241eae9271791"
          }
      </pre>
    </code>
    In this example the <code>SHOCKERNAME</code> can be replaced by your own name for your shocker <code>leg</code> for example the name doesn't need to match the name on the website, the name is later used to create a trigger parameter on your avatar.<br>
    <br></br>
    You can also add multiple shockers or just one, make sure you don't use the same ID twice, this doesn't work.<br>
    <code>
      <pre>
          "Shockers": {
            "leftleg": "18b1d0e6a-f9a0-4e93-9812-241eae9271791", 
            "rightleg": "28b1d0e6a-f9a0-4e93-9812-241eae9271792,
            "nose": "38b1d0e6a-f9a0-4e93-9812-241eae9271793"
          }
      </pre>
    </code>
    </details>

## Configure Limits
You can also set limits in ShockOsc. 
!!! Tip
    Time is set in milliseconds  
    1 second = 1000 milliseconds  
    
    ShockOsc counts from 0  
    Strenght = 0 is 1% and 101 is 100%

### Random strenght and duration
This way you will be shocked for a random strenght and/or random duration or both when someone triggers your ShockOsc.  

1. Open your ``config.json``.
2. Make sure ``RandomIntensity`` and/or ``RandomDuration`` is set to ``true``, you can configure these individually. 
3. Edit the ``IntensityRange`` and ``DurationRange``.
4. Save the config file, you are done!

### Fixed strenght and duration
This way you will be shocked for a fixed strenght or duration or both when someone triggers you ShockOsc.  

1. Open your ``config.json``.
2. Set ``RandomIntensity`` and/or ``RandomDuration`` is set to ``false``, you can configure these individually. 
3. Edit the ``FixedIntensity`` and/or ``FixedDuration`` to the fixed value you want.
4. Save the config file, you are done! 🎉  

## Example Config
!!! Info "Example Config"  
    After following this guide your config should look something like this:  

    <pre>
      <code>
        "Osc": {
            "Chatbox": true,
            "Hoscy": false,
            "SendPort": 9000,
            "HoscySendPort": 9001
          },
          "Behaviour": {
            "RandomIntensity": true,
            "RandomDuration": true,
            "RandomDurationStep": 1000,
            "DurationRange": {
              "Min": 1000,
              "Max": 5000
            },
            "IntensityRange": {
              "Min": 1,
              "Max": 30
            },
            "FixedIntensity": 50,
            "FixedDuration": 2000,
            "HoldTime": 250,
            "CooldownTime": 5000,
            "WhileBoneHeld": "Vibrate",
            "DisableWhileAfk": true,
            "ForceUnmute": false
          },
          "ShockLink": {
            "ApiToken": "0W3ybn7bHuF2SUwAZ8YZexRMejzTcUzJJT3cBSf4FWK7ryLhRT2wikFh8qZGYpiY",
            "Shockers": {
            "leftleg": "8b1d0e6a-f9a0-4e93-9812-241eae927179"
            }
          },
          "Chatbox": {
            "DisplayRemoteControl": true,
            "HoscyType": "Message"
          }
        }
      </code>
    </pre>


!!! Warning "Advanced Configuration"
    On the [ShockOSC repository](https://github.com/OpenShock/ShockOsc) you can see additional configuration examples, but that would go beyond the limits of this simple guide  
