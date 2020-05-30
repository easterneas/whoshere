# Who's Here - An automatic "In/Out" board for UniFi networks

Forked from https://github.com/batesta/whoshere

I volunteer my IT skills at a local church (Redemption Church - Gateway, in Mesa, AZ) and we currently use UniFi network gear.

One of the issues with our new, larger campus is we're not always sure who's on campus at the end of the evening, when it's time to arm the alarms.

Because of it, I wrote "Who's Here".

![The working example of Who's Here](/whoshere-screenshot.png)

## What is Who's Here?

Who's Here, is an automatic In/Out board for UniFi networks, which queries the UniFi controller to "search" for specified MAC address of respective device(s). When the MAC address is "Active", it will display which hotspot the user is connected to, and display it. Otherwise, it will query the last time the user was last seen, and display it.

## Prerequisites

1. The UniFi API - (https://github.com/Art-of-WiFi/UniFi-API-client) 
2. MAC addresses of devices you would like to track, in the file users.txt in the format:
   ```
   Thomas Bates  00:00:00:00:00:00 {Notice *2* spaces after the username to display and the MAC address)
   ```
3. A user on the UnFi controller 
   ```
   Username: "whoshere"
   Password: {Make a note of it, and recommend making it hard}
   Role: Read Only
   Permissions:
   - Allow System Stat access
   - Allow Read Only Access to all sites
   ```

## Configuration
               
In the file, edit the following:

```
$controller_user = "whoshere";  # Username you used
$controller_password = "password"; #Password you used
$controller_url = "https://192.168.1.5:8443"; #URL You use to connect to UniFi controller
$site_id = "abc123"; # Site Code used to access users you want to monitor.  Get this by going to the site in UniFi and copying from the URL.
$controller_version = "5.10.21.0";

date_default_timezone_set('America/Phoenix'); # Timezone you want to use
```
