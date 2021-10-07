<script>
    import { Router, Route, Link } from "svelte-routing";
    import Home from "./pages/Home.svelte";
    import Mint from "./pages/Mint.svelte";
    import About from "./pages/About.svelte";
    import Four from "./pages/Four.svelte";
    import MyPepes from "./pages/MyPepes.svelte"
    export let url = '';
    import { setContext } from 'svelte';
    import { writable } from 'svelte/store';
    import { fade } from 'svelte/transition';
    import { Audio, Video } from 'svelte-audio-video'
 
  const track = {
    attach: (element, _track) => {
      // when fired, do whatever is needed to attach the track
      // Note: `this` refers to the `track` object
    },
 
    detach: (element, _track) => {
      // when fired, do whatever is needed to detach the track
      // Note: `this` refers to the `track` object
    },
  }
    const app = writable({});
    //export const innerHeight = writable(1000)
    //export const innerWidth = writable(1000) Any use for these
    setContext('app', app);
    console.log(window.location.href);
</script>

<div class="main">
    <Audio controls={false}>
        <source
          src="/"
          type="audio/mp3" />
      </Audio>
	<header>
        <div class="nav-row">
          <div class="icon-box">
            <div class="dot-row">
            <div class="icon-dot"></div>
            <div class="icon-dot"></div>
            <div class="icon-dot"></div>
          </div>
          <div class="dot-row">
            <div class="icon-dot"></div>
            <div class="icon-dot"></div>
          </div>
        </div>
          <p style="margin-top: 1rem;font-weight:100;font-size: 2rem;line-height:2rem;">GEOMETRIC<b style="font-weight:900;">FORMS</b></p>
        </div>
      </header>

      
    <Router url="{url}">
        
        <Route path="/"><Home /></Route>
        <Route path="/mint" component={Mint}><Mint /></Route>
        <Route path="/mint"><Mint /></Route>
        <Route path="/about" component={About}><About /></Route>
        <Route path="/mypepes" component={MyPepes}></Route>
        <Route path="/*"><Four /></Route>

    </Router>

    <script type="text/javascript" src="/script.js"></script>

</div>
<style>
	.main {
		text-align: center;
		padding: 0rem;
		margin: 0 auto;
	}
    .nav-row{
      position: relative;
      height:100px;top:0px;
      width:calc(100vw - 4rem);
      display:flex;
      flex-flow:row;
      justify-content: center;
      margin:auto;padding:1rem 2rem;
}
.icon-box{
  display:flex;flex-flow:column;
  position:fixed;left:4rem;top:2rem;
}
.wrapper{    
  position: relative;
  height: 100vh;
    display: flex;
}
.pepebottom{
    width:100vw;text-align:center;font-size:5rem;
}
button{margin:1rem;}
header{z-index:5;position:relative;}
@media only screen and (max-width: 1600px) {
    .pepebottom{
      width:100vw;
      text-align:center;
      font-size:3rem;
    }
.icon-box{
  display:none;flex-flow:column;
  position:fixed;left:2rem;top:2rem;
}
}
footer{
  position:relative;
  display:flex;
  flex-flow:row;
  justify-content:center;
  bottom:0px;
  left:0px;
  width:100vw;
  height:auto;
}
.icon-dot{
  height:4px;width:4px;border-radius:2px;margin:0.5rem;background:white;
}
.dot-row{display:flex;flex-flow:row;}

.mint{
    transition: transform 0.2s ease;
}
.mint:hover{
  transform:scale(1.1);
}
</style>
