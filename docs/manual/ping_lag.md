---
layout: default
tab: Manual
---

# ezQuake Manual - Ping and lag
(automatic conversion from internal help - last edited Thu 07-Oct-2004)

## Ping and lag

Ping and lag are the archenemies of each online player because they affect gameplay more than anything else. Between the QW client and server information is exchanged by dividing this information into small packets which are then send to each other over the internet. On their way they have to pass a series of hops until they reach their final destination. The time in milliseconds the packets need to get from their source to their destination is called "ping". The lower your ping is the better. How low or high your ping is depends on what kind of connection you have (cable, DSL, ISDN, modem, etc), how many hops there are in between your client and the server and how good the equipment of your internet service provider and the hops is.

As soon as the ping gets too high to be playable we call this "lag". QW is a real time game and the more you lag, that is the longer you are behind the action taking place the less playable and the less fun it is. It depends a lot on your personal preference though what you call lag and what kind of ping you find acceptable. While a modemer might be happy to play with a ping of less than 200 ms someone else might complain about anything higher than 30. QW plays very good even with pings as high as 200 but the lower the ping is the better and if you really want to play competetive, you you will need constant ping times of ~60 milliseconds and lower.

Another problem affecting every Quake player is "packetloss". If for some reason a packet is lost in between the client and the server the continuous flow of information between the two becomes interrupted and the client has to makes guesses upon what is happening in the game world. The more packets are lost, the more have to be predicted but prediction works only good if only few packets are lost. Thus larger packetloss makes the game unplayable and has to be avoided.

QW displays both ping and packetloss in the scoreboard. If you type showscores (by default it is bound to the tab key) you will see each players ping in milliseconds as well as their packetloss in percent. There is another command which lets you examine packetloss further.

If you type r_netgraph 1 in the console a graph will appear in the lower left corner of the screen. It can be turned off by typing r_netgraph 0. When turned on a series of colored bars will start to move from left to right. These bars represent the packets currently being recieved and what happens to them. The height of the white line shows the latency of recieved packets, that means the higher it is the higher your ping is. The red lines represent lost packets. The more red lines the more packets were lost in between. You can't do anything about them but look for a better server where you have less packetloss. The yellow lines also respresent lost packets but these were intentionally dropped by the client and this can be tweaked. Blue lines are very bad, they mean your provider suck. Go look for another one.
## Tweaking your lag

You can tweak your lag a bit by using the_rate_,_pushlatency_and_cl_maxfps_commands

The rate command determines how many bytes per second are received by your client and also caps your fps. The higher the rate setting the more data you will receive and the more fps you will have (both is good). The problem is that the amount of data received is limited by the bandwidth of your connection. If you receive more data than your connection can handle the data gets stuffed resulting in higher ping and lag. The rate can range from a minimum of 500 to a maximum of 10000. With a 33k modem you should not use anything much higher than 2500 (caps the fps at 30), with ISDN you could use up to 6000 (caps fps at the maximum of 72) and on LAN or with a better connection you can use up to 10000. If you use Qizmo compression you can use higher values without the fear of your connection getting stuffed. With an ISDN connection a rate of 10000 works fine with Qizmo compresion turned on and if you are lucky and you have a good ISP you can even use such a high rate on a modem connection.

You can override the fps cap determined by the rate command with the cl_maxfps command. Allowed values reach from 0 (which means no limit) to whatever your cpmputer and connection can handle. Note that the maximum fps are also capped server side! Most servers do not allow more than 77fps. So you can have higher fps than your rate usually allows (for example 40 fps at a rate of 2500).

Another important command regarding lag is pushlatency. It determines how much time into the game will be predicted by your client when it loses contact to the server (=packetloss). Experience has shown that the best value (default is -50) is the exact negative of your average pingtime (for example -140 of your ping is at 140ms). You can also set it to -999. This value is said to adjust the pushlatency dynamically according to your ping but this is not documented. It seems to work very good on connections with rather stable ping times though. Note that the pushlatency command cannot be used in the current version of ezQuake where it got hardcoded to the value of -999.
