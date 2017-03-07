
# Dark Wave

## Installation
``` wget https://raw.githubusercontent.com/sam0hack/Dark-Wave/master/install/install.sh && bash install.sh ```


## :trident: Know things

#### "Clients are not automatically connected to the fake access point"
This is a social engineering attack and it's pointless to drag clients in automatically. The script relies on the fact that a user should be present in order to enter the wireless credentials.

#### "There's no Internet connectivity in the fake access point"
There shouldn't be one. All of the traffic is being sinkholed to the built in captive portal via a fake DNS responder in order to capture the credentials.

#### "Fake sites don't work"
There might be a problem with lighttpd. The experimental version is tested on lighttpd 1.439-1, anything neweer may break functionality. If you have problems, please use the stable version. For more information check this [fix] (https://github.com/sam0hack/Dark-Wave/wiki/fix) out.

#### "Experimental menu is not responsive"
In the experimental version it will automatically check the handshake. I will fix the menu shortly. If you need a GUI, use the stable version (which doesn't automatically control handshakes).

#### "I need to sign in (on Android)"
This is how the script works. The fake captive portal is set up by the script itself to collect the credentials. Don't freak, it's al okay.

#### "The MAC address of the fake access point differs from the original"
The MAC address of the fake access point differs by one octet from the original in order to prevent Dark-Wave deauthenticating clients from itself during the session. 

## Updates
If you want to submit a feature, do so by labeling your issue as an "enhancement" or submit a PR. I don't have enough time to make daily changes to Dark-Wave, sorry.

## :white_check_mark: Included dependency versions
1. Aircrack : 1:1.2-0~rc4-0parrot0
2. Lighttpd : 1.439-1
3. Hostapd  : 1:2.3-2.3 _If you want to compare this type `dpkg -l | grep "name"`_


## :octocat: Join our Slack channel
!['Slack Channel'] (https://dark-wave.slack.com/)


## :book: How it works
* Scan the networks.
* Capture a handshake (can't be used without a valid handshake, it's necessary to verify the password)
* Use WEB Interface *
* Launch a FakeAP instance to imitate the original access point
* Spawns a MDK3 process, which deauthenticates all users connected to the target network, so they can be lured to connect to the FakeAP and enter the WPA password.
* A fake DNS server is launched in order to capture all DNS requests and redirect them to the host running the script
* A captive portal is launched in order to serve a page, which prompts the user to enter their WPA password
* Each submitted password is verified by the handshake captured earlier
* The attack will automatically terminate, as soon as a correct password is submitted

## :heavy_exclamation_mark: Requirements

A Linux-based operating system. We recommend Kali Linux 2 or Kali 2016.1 rolling. Kali 2 & 2016 support the latest aircrack-ng versions. An external wifi card is recommended.


## Disclaimer

***Dark Wave is intended to be used for legal security purposes only, and you should only use it to protect networks/hosts you own or have permission to test. Any other use is not the responsibility of the developer(s).  Be sure that you understand and are complying with the Dark Wave licenses and laws in your area.***
