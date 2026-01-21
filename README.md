# RiotGames-Reversal

Hey there, and welcome to this repository. I'll be using it to document my progress of reversing riot client communication with an older version of valorant.
<br></br>
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

## Communication
Now, this is present time. I currently have a very small bit of knowledege on how Riot's communication works. Though, i managed to get the first request they call to redirect to my server. The first request they call is 
**GET /system/v1/builds**
**Response: **

```json
{
  "builds": [
    {
      "branch": "main",
      "branchFull": "refs/heads/main",
      "codeBuildId": 12345,
      "contentBuildId": 67890,
      "gameBranch": "game-main",
      "gameBranchFull": "refs/heads/game-main",
      "gameDataBuildId": 54321,
      "patchline": "stable",
      "patchlineVisibleName": "Stable",
      "version": "1.0.0"
    }
  ]
}
```
**It ended up working!** (Img below)
<img width="1383" height="46" alt="image" src="https://github.com/user-attachments/assets/23d442aa-d7ca-4a5a-9371-61ddd4c7e904" />

After I got here, im now where i currently am which is stuck on the socket connection for riot client, I'm still trying to figure out exactly what is sent / requested and also how to get past SSL pinning. For the http request i used fidlder to get past SSL.
<br></br>
<img width="1003" height="167" alt="image" src="https://github.com/user-attachments/assets/f785e901-0c30-4191-a2b1-39bee41e62cf" />
