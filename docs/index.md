<style>
.button {
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 14px;
  margin: 4px 2px;
  cursor: pointer;
  border-radius: 8px;
}

.buy-btn {
  border: 2px solid black;
  background-color: #00aeef;
  border: none;
  padding: 0.5em 1.5em;
  cursor: pointer;
  border-radius: 8px;
}

.disc-btn {
  border: 2px solid black;
  background-color: #5865F2;
  border: none;
  padding: 0.5em 1.5em;
  cursor: pointer;
  border-radius: 8px;
}

/* white outline - useless in light mode 
 .btn {
  border: 4px solid white;
  padding: 0.5em 1em;
  font-size: 16px;
  cursor: pointer;
  border-radius: 8px;
} */

/* Different background on mouse-over */
.buy-btn:hover {
  background-color: #ff9016;
}

.disc-btn:hover {
  background-color: #ff9016;
}

@media (min-height: 400px) {
section {
  -webkit-columns: 2 250px;
     -moz-columns: 2 250px;
          columns: 2 250px;
  -webkit-column-gap: 2em;
     -moz-column-gap: 2em;
          column-gap: 2em;
}
}

/* p {
  margin-bottom: 1.3em;
} */

</style>

<h1>Thumby, a Tiny Playable Keychain by <a href="https://tinycircuits.com/" target="_blank" alt="TinyCircuits main website page"><b>TinyCircuits</b></a></h1>

<section>

<center><img src="/images/Thumby-handful.jpg" style="width:100%" alt="Thumby handful image"></center>

<p>Thumby was funded by <a href="https://www.kickstarter.com/projects/kenburns/thumby-the-tiny-playable-keychain" target="_blank" alt="TinyCircuits Thumby Kickstarter page"><b>4,502 Kickstarter backers</b></a> in 2021, reaching more than 13 times its funding goal.</p>


<p>Thumby™ is an itty-bitty game system at the tips of your thumbs, a best friend for your keys, and an easy learning tool all-in-one. Start playing right away with preloaded games. Download more games and learn to program your own using the <a href="https://code.thumby.us/" target="_blank" alt="TinyCircuits Thumby Web Browser code editor page"><b>Thumby Code Editor</b></a> Website!</p>

<center><button class="buy-btn"><a href="https://www.indiegogo.com/projects/thumby-the-tiny-playable-keychain/x/28495928#/"  style="color: white" target="_blank" alt="TinyCircuits Indiegogo Thumby page"><b>Order Now</b></a></button></center>

<p></p>

<center><button class="disc-btn"><a href="https://discord.gg/vzf3wQXVvm"  style="color: white" target="_blank" alt="TinyCircuits Discord join link"><b>Join us on Discord</b></a></button></center>

</section>

---


<!-- <section> -->

<h2>Play & program using MicroPython</h2>

<a href="https://micropython.org/" target="_blank" alt="MicroPython documentation and site">**MicroPython**</a> is an implementation of Python 3 optimized to run on microcontrollers, like the <a href="https://www.raspberrypi.com/documentation/microcontrollers/rp2040.html" target="_blank" alt="RP2040 processor documentation and site">**Raspberry Pi RP2040**</a> in Thumby! MicroPython is a great way to get started with learning how to program, or to quickly make a new game. 



We created a [**Thumby MicroPython API**](/API/Get-Started/) (application programming interface), to make programming even easier! Using our all-in-one <a href="https://code.thumby.us/" target="_blank" alt="TinyCircuits Thumby Web Browser code editor page">**Thumby Code Editor**</a>, you are just a few tutorials away from creating your own Thumby program or game! The Code Editor also contains the Thumby Arcade where users publish their games for anyone to play and download to their own Thumby. 

Navigate to the [**Code Editor documentation**](/Code-Editor/Get-Started/) to learn more.

<!-- </section> -->

---

## Play & program using Arduino C/C++

Check out our [**documentation for the Arduino C/C++ library**](/CCPP/API-Reference/) created for use with Thumby. 

---


## Thumby Tech Specs

<ul>
  <li><b>Processor</b>: Raspberry Pi Pico RP2040 Processor</li>
  <li><b>Memory</b> 2MB total storage</li>
  <li><b>Connectivity</b> micro USB for programming & multiplayer using <b>Thumby Link cable</b></li>
  <li><b>Outputs</b> 72x40 Monochrome OLED Display, Piezo Speaker</li>
  <li><b>Inputs</b> 6 tactile buttons (4-way D-pad, 2 action buttons)</li>
  <li><b>Power</b> Power switch, 40mAh Rechargeable LiPo Battery, ~2 hours of gameplay</li>
  <li><b>Dimensions</b> 1.2" X 0.7" X 0.3" (29.5mm x 18mm x 8.5mm) - Sturdy polycarbonate plastic case with a built-in rechargeable battery and buzzer</li>
  <li><b>Programming</b> MicroPython using the Thumby Code Editor or Arduino Code Editor - create your own games! </li>
  <li>Multiplayer support via <b>Thumby Link cable</b></li>
</ul>

---

## Reviews From Users

<style>
#rcorners1 {
  border-radius: 25px;
  padding: 15px;
  background: #373e4e;
  /* display: flex;  */
  /* justify-content: space-between; */
}

#no-padding {
  padding: 0; 
  margin: 5px;
  color: white;
  display: inline;
  /* align-content: stretch; */
}

/* #p2 {
  align: right;
}

.p{
  display: flex;
  align-items: stretch;
} */
</style>

<div id="rcorners1">
  <p id="no-padding"><em>"Even photos of it can’t prepare you for just how small the Thumby is when you first pick it up"</em></p>
  <p align="right" id="no-padding" ><a href="https://gizmodo.com/how-small-is-too-small-for-a-game-boy-the-thumby-might-1847722821" target="_blank" alt="TinyCircuits Thumby Article Blog"><b>-Gizmodo</b></a></p>
</div>

<p></p>
<div id="rcorners1">
  <p id="no-padding"><em>"A fully operational handheld that you could very easily swallow if you're not careful." "That's even cooler than I was expecting it to be."</em> </p>
  <p id="no-padding" align="right"><a href="https://www.youtube.com/watch?v=GCmiKaLnd7M&t=159s" target="_blank" alt="TinyCircuits Thumby Article Blog"><b> -Mrwhosetheboss (YouTuber)</b></a></p>
</div>

<p></p>
<div id="rcorners1">
  <p id="no-padding"><em>"Probably the World's Smallest Game Console"</em> </p>
  <p align="right" id="no-padding"><a href="https://www.nintendolife.com/news/2021/09/random_this_tiny_game_boy_is_probably_the_worlds_smallest_game_console" target="_blank" alt="TinyCircuits Thumby Article Blog"><b>-Nintendo Life</b></a></p>
</div>

<p></p>
<div id="rcorners1">
  <p id="no-padding"><em>"I am squealing at how adorable this is!!"</em> </p>
<a align="right" href="https://www.tiktok.com/@janedstv/video/7021241714434116869?_d=secCgYIASAHKAESPgo8TGbXENYzGNiqF3K0nBAc1ehH4xOSdzAI7FwjTWr2jxHemLq%2FDyrfv5rBGoMn16wyQuF7pMWnU2y%2FeLrEGgA%3D&checksum=d00f34009685dd8622da47f0547e02242088a683a0bd741dfca297e0a605dcd5&language=en&preview_pb=0&sec_user_id=MS4wLjABAAAAQMo5TYLy1syPZfG34wkQLk4ydzIBgKR2yqDiHJIpNzy5mUu7JqPTRBaTbEq2TzIb&share_app_id=1233&share_item_id=7021241714434116869&share_link_id=F5FAB303-713F-4A82-B0F2-277F9AF9491C&source=h5_m&timestamp=1634760282&tt_from=copy&u_code=dahd0hdjhlcmme&user_id=6788356638502208518&utm_campaign=client_share&utm_medium=ios&utm_source=copy&_r=1&is_copy_url=0&is_from_webapp=v1&sender_device=pc&sender_web_id=7006356245049345542" target="_blank" alt="TinyCircuits Thumby TikTok Blog"><b>-janedstv (TikToker)</b></a>
</div>

<p></p>
<div id="rcorners1">
  <p id="no-padding"><em>"How small is this... roughly the size of the D-pad!"</em> </p>
  <p align="right" id="no-padding"><a href="https://nintendowire.com/news/2021/09/22/thumby-the-worlds-smallest-gaming-handheld-headed-to-kickstarter-on-september-28th/" target="_blank" alt="TinyCircuits Thumby Article Blog"><b>-Nintendo Wire</b></a></p>
</div>



<!-- <p></p>
<div id="rcorners1">
  <p id="no-padding"><em>""</em> </p>
  <p align="right" id="no-padding"><a href="" target="_blank" alt="TinyCircuits Thumby Article Blog"><b> - </b></a></p>
</div>
 -->

<!-- * <a href="https://www.tiktok.com/@jookstogo/video/7021251678821158170?is_copy_url=0&is_from_webapp=v1&sender_device=pc&sender_web_id=7006356245049345542" target="_blank" alt="TinyCircuits Thumby TikTok">**TikToker jookstogo**</a> unboxing a Thumby prototype -->



<center>
![Thumby bee animation](/images/thumby-bee.gif)
</center>
<center>*"Bzzz, Bzzz, Bzzz"* - Fred, the Carpenter Bee at The University of Akron Blackledge Lab</center>


## YouTube Reviews

<style>
.row {
  display: -ms-flexbox; /* IE 10 */
  display: flex;
  -ms-flex-wrap: wrap; /* IE 10 */
  flex-wrap: wrap;
  padding: 0 4px;
}

/* Create two equal columns that sits next to each other */
.column {
  -ms-flex: 50%; /* IE 10 */
  flex: 50%;
  padding: 0 4px;
}

.column img {
  margin-top: 8px;
  vertical-align: middle;
}

.image {
  opacity: 1;
  display: block;
  width: 100%;
  height: auto;
  transition: .5s ease;
  backface-visibility: hidden;
}

.container:hover .image {
  /* opacity: 0.2; */
  box-shadow: 0 0 2px 8px #f68d28;
}
</style>


 <!-- Download thumbnail picture - https://www.softr.io/tools/download-youtube-thumbnail -->

<div class="row"> 
  <div class="column">
    <div class="container">
      <a href="https://www.youtube.com/watch?v=Fa7OxjpXLjQ" target="_blank" alt="Thumby YouTube video"><img src="/images/youtube-LGR-Blerbs.jpg" style="width:100%" class="image"></a>
    </div>
    <div class="container">
      <a href="https://www.youtube.com/watch?v=E01VPCe4U-c" target="_blank" alt="Thumby YouTube video"><img src="/images/youtube-The-Retro-Future.jpg" style="width:100%" class="image"></a>
    </div>
    <div class="container">
      <a href="https://www.youtube.com/watch?v=3JsQ5FkIWRI" target="_blank" alt="Thumby YouTube video"><img src="/images/youtube-3DSage.jpg" style="width:100%" class="image"></a>
    </div>
    <div class="container">
      <a href="https://www.youtube.com/watch?v=dEVXW3sdPtM" target="_blank" alt="Thumby YouTube video"><img src="/images/youtube-LowSpecGamer.jpg" style="width:100%" class="image"></a>
    </div>
    <div class="container">
      <a href="https://www.youtube.com/watch?v=s1EU-Ib1cVs" target="_blank" alt="Thumby YouTube video">
    <img src="/images/youtube-Retro-Game-Corps.jpg" style="width:100%" class="image"></a>
    </div>

  </div>

  <div class="column">
  <div class="container">
      <a href="https://www.youtube.com/watch?v=1S8InR9V6xU" target="_blank" alt="Thumby YouTube video">
    <img src="/images/youtube-Adam-Savage-Tested.jpg" style="width:100%" class="image"></a>
    </div>
    <div class="container">
      <a href="https://www.youtube.com/watch?v=wwPwlYxOb8k" target="_blank" alt="Thumby YouTube video">
    <img src="/images/youtube-MK-V.jpg" style="width:100%" class="image"></a>
    </div>
    <div class="container">
      <a href="https://www.youtube.com/watch?v=4MuQfzmPXts" target="_blank" alt="Thumby YouTube video">
    <img src="/images/youtube-Inkbox.jpg" style="width:100%" class="image"></a>
    </div>
    <div class="container">
      <a href="https://www.youtube.com/watch?v=yLdz76MTk5A" target="_blank" alt="Thumby YouTube video"><img src="/images/youtube-Macho-Nacho-Productions.jpg" style="width:100%" class="image"></a>
    </div>
  </div>  
</div>

--- 








