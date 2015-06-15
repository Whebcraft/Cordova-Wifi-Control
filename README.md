# Cordova-Wifi-Control
Sets, gets, toggles wifi service.  Enables broadcast listener returning wifi signal strength.  Pass success name as a String.

This Plugin Requires https://github.com/Whebcraft/System_api.git

Install https://github.com/Whebcraft/Cordova-Wifi-Control.git

## com.webcraft.wificontrols

Wifi Controls plugin has a dual purpose, control the Wifi state and return the signal strength value.

The plugin adds a phoneStateListener returning the current wifi level when the level changes.  When a change occurs the plugin uses 'this.webView.sendJavascript()' to trigger the passed function.  

Notice that the triggered function is passed as a string.  This is because the sendJavascript builds the function call and then is evaluated once inside the webview.


## **Enable:** 

`@return - String, 'enabled'`<br>
`@callback - String, function name when listener fires.`<br>
`window.wificontrols.enable({callback:'wifiSignal', success:wifiEnabled});`

---

## **Disabled:** 

`@return - String, 'disabled'`<br>
`@callback - String, function name when listener fires.`<br>
`window.wificontrols.disable({callback:'wifiSignal', success:wifiDisabled});`

---

## **Toggle:** 

`@return - String, 'enabled/disabled'`<br>
`@callback - String, function name when listener fires.`<br>
`window.wificontrols.toggle({callback:'wifiSignal', success:wifiDisabled});`

---

## **Stop:** 

`window.wificontrols.stop({});`

---

## **Check:** 

`@return - String, 'enabled/disabled'`<br>
`@callback - String, function name when listener fires.`<br>
`window.wificontrols.check({callback:'wifiSignal', success:wifiDisabled});`

---

## **Wifi Level Conversion:**

As to negate any issues, the wifi level is not passed converted to an easily managed scale. This allows for custom changes if there are any qualms with the level conversion. 

`function wifiSignal(returnVal){`<br>
	`var maxStrength = -50;` <br>
	`var minStrength = -120;` <br>
	`var percentage = Math.round(100 - Math.max(0, Math.min((returnVal - maxStrength) / (minStrength - maxStrength), 1) * 100));`<br>
	`$('#wifiSignal h3').text(percentage+'%');`<br>
`}`<br>
