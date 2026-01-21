# RiotGames-Reversal

Hey there, and welcome to this repository. I'll be using it to document my progress of reversing riot client communication with an older version of valorant.
*please star ⭐* 

## Info
**Valorant Version:** 1.08  
**Riot Client:** Newest (no older version available)

## Let's start
When I first dumped the game into IDA, i realized that the game is packed completely. I needed to use a different method of dumping.

What I did was exploit exceptions, similar to how people currently dump games like Fortnite, The Finals ( i think), and some other games. It got me some useful information, but not enough. Many functions were limited due to timing on the dump, I needed to get past certain aspects of the game before dumping further. I used this dump's strings to find a way to redirect the game's communication to riot client. 

The arguments I found were pretty simple, though they do not bypass SSL.
```
-remoting-auth-token="andr1ww" -remoting-app-port=8888
```
(*There was also one extra one I found: -developer, not sure what it does yet though.*)
