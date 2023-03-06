# Share Your Thumby Game

So you want to share a Thumby game (maybe one you've made) with friends, family, or strangers, but they don't have a Thumby (yet!). You're in luck! Anyone can play a Thumby game using our online Code Editor through the Emulator, but even faster and smartphone-compatible than that is the Thumby Play page that allows you to play on a virtual Thumby loaded with *all* the [**Thumby Arcade**](https://arcade.thumby.us/) games.

---

## Play in the Emulator

If you've been through the [**getting started tutorial**](/Code-Editor/Get-Started/), you already know that the [**Emulator window**](/Code-Editor/Widget-panels/#emulator) in the Thumby Code Editor can be used to play games after selecting them from the Arcade and opening their source code in the 
[**Editor**](/Code-Editor/Widget-panels/#code-editor). This is a great option when editing a game's code to be able to emulate changes quickly, but it's not the most efficient option for playing the games. 

---

### Play Online or On Your Phone

Head on over to the [**Play Emulator page**](https://code.thumby.us/play.html), you can also navigate to this page from the [**Code Editor**](https://code.thumby.us/ "Thumby Online Code Editor") under the **Other Links** button. This page loads an emulated Thumby that's preloaded with every game posted on the [**Thumby Arcade**](https://arcade.thumby.us/) available to play!

If you submitted a game to the [**Thumby Arcade**](https://arcade.thumby.us/), your game will be loaded onto the Play Emulator list of games. And you can share a special link that will load just one game to the online Thumby using the following convention that involves editing the hyperlink:

**Game Name:** <input type="text" value="put_game_title_here" style="border:solid;background-color:#8a8a8a " onkeyup="document.getElementById('pathResult').innerHTML = ('https://code.thumby.us/play.html?game='+this.value)">
<br>
**Share link:** <code class="md-typeset code" id="pathResult"> https://code.thumby.us/play.html?game=put_game_title_here</code>

```
 https://code.thumby.us/play.html?game=put_game_title_here
```

For example, to create a link to the game **Annelid**, type out: 
</br>
[**https://code.thumby.us/play.html?game=Annelid**](https://code.thumby.us/play.html?game=Annelid "Link to Thumby Emulator pre-loaded with the game Annelid")

You can use the link to play Thumby Games in a web browser on your computer, or on your phone:

<center><img width="30%" height="30%" alt="Thumby Code Editor Play Emulator with Annelid game loaded" src="/images/play-emulator-on-phone.png"  />
</center>
<center>*Annelid game on phone*</center> 

---

## Share Game Links!

Here's a list of all the Thumby Games on the Play Emulator that you can share with friends!

<center>
<div id="emuLinks"></div>
<script>
fetch('https://raw.githubusercontent.com/TinyCircuits/TinyCircuits-Thumby-Games/master/url_list.txt').then((r) => {
  var i = j = 0;
  r.text().then((gameList) => {
    var games = []
    while((j = gameList.indexOf("NAME=", i)) !== -1){
      var game = gameList.substring(j+5, gameList.indexOf("\n", j+5));
      games.push('<a href="https://code.thumby.us/play.html?game=' +
        encodeURIComponent(game) + '"><b>' + game + "</b></a>");
       i = j + 1;
    }
    games.sort();
    console.log(games);
    document.getElementById('emuLinks').innerHTML = games.join('<br>');
  });
});
</script>
</center>

**⚠ Note**: *Some games do fancy hardware tricks in MicroPython and might not work on the emulator.*