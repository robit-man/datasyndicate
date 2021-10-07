<script>
import { onMount, getContext} from 'svelte';
import { slide, fade } from 'svelte/transition';
import { address, contract, provider, nfts, balances } from '../store';
import { Swiper, SwiperSlide } from 'swiper/svelte';
import { initProvider, mintPepe } from '../utils';
import "swiper/css/pagination"
import Carousel from 'svelte-carousel'
import {
		Fullpage,
	 	FullpageSection,
		FullpageSlide
	} from 'svelte-fullpage';
	import {
		Container,
		Row,
		Col
	} from 'sveltestrap';
	//Include all titles of your sections, this is also used as number that indicate count of sections
	const sections = [
		'Home',
		'About',
		'Gallery',
		'Process',
		'Mint'
	];
	//Have to set to 0 (or section you wish to display as default), otherwise section will not display
	let activeSection = 0;
	//Same mechanics as in sections
	const slides = [
		'slides',
		'arrows',
		'drag',
	];
	//Also has to be 0 or specific id of slide
	let activeSlide = 0;

  function mintSection() {
		activeSection = 4;
	}
  let addressDisplay = '';
  async function connectEthProvider(reconnect=false) {
        if(!$address) {
            await initProvider(app, reconnect);
            addressDisplay = String($address).slice(0,7)+"..."+String($address).slice(-5);
            $address = $address;
        }
    }
  function connect() {
    connectEthProvider(false);
  }
  function mint() {
    mintPepe();
  }
</script>

<Fullpage bind:activeSection arrows drag> 
	<FullpageSection style="background:#111!important;"  center>
		<Container style="display:flex;flex-flow:row;justify-content:center;" class="text-center">
      <div class="container-child-wrapper" >
				<div class="hero-title" >
          <div class="row ">
            <Col style="display:flex;flex-flow:column;justify-content:center;width:auto;">
              <div class="pagenumber">
              <p class="bigfont" style="font-weight:400;margin:unset;">01</p>
              <div class="underline"></div>
              <div class="page-name">Home</div>
            </div>
            </Col>
            <Col style="width:auto;">
            <div transition:fade class="rotate-title">
              <h5 style="margin:unset;margin-bottom:1rem;margin-left:0.25rem;">COLLECTION : 100 UNIQUE FORMS</h5>
              <p class="bigfont" style="font-weight:100;margin:unset!important;line-height: 5rem;">GEOMETRIC</p>
              <p class="bigfont" style="font-weight:900;color:#ee0530;margin:unset!important;line-height: 5rem;"><b>FORMS</b></p>
            </div>
            </Col>
              
          </div>
        </div>
        <div class="iframe-wrap">
          <iframe src="/strings.html" class="geometry-container" frameborder="0"></iframe>
          <button on:click={mintSection} class="button-padding"> SKIP TO MINTING</button>

        </div>
      </div>
		</Container>
	</FullpageSection>	
  
	<FullpageSection style="background:#ee0530!important;"  center>
    <Container style="display:flex;flex-flow:row;justify-content:center;" class="text-center">
      <div class="container-child-wrapper" >
				<div class="container-child-wrapper-padding" >
          <div class="row half">
            <Col style="display:flex;flex-flow:column;justify-content:center;width:auto;">
              <div class="pagenumber">
              <p class="bigfont">02</p>
              <div class="underline"></div>
              <div class="page-name">About</div>
            </div>
            </Col>
            <Col style="width:auto;">
            <div transition:slide class="description">
              <p style="font-size:3rem;font-weight:100;margin:unset!important;">GENERATIVE</p>
              <p style="font-size:3rem;font-weight:900;margin:unset!important;"><b>GEOMETRY</b></p>
              <p>GEOMETRIC FORMS is a collection of 100 unique FORM NFTs - a digital version of generative geometry and post processed colour found in mathematics and art.
                <br><br>
                With only 100 NFTs created, the symmetry, geometry, lines, and colour of the artwork yield a subjective rarity. Stored as an ERC-721 token, on thje Ethereum blockchain for immutable history and decentralized ownership.
              </p>
            </div>
            </Col>
              
          </div>
        </div>
        <div class="second-container">
          <div class="img-effect">
            <img transition:fade src="/imgs/forms/line-000363.png" style="z-index:2;position:relative;" alt="">
            <div class="imgbox"></div>
          </div>
        </div>
      </div>
		</Container>
	</FullpageSection>
	<FullpageSection style="background:#111!important;"  center>
    <Container style="display:flex;flex-flow:row;justify-content:center;" class="text-center">
      <div class="container-child-wrapper" >
				<div class="slider-wrap" >
          <div class="row half">
            <Col style="display:flex;flex-flow:column;justify-content:center;width:auto;">
              <div class="pagenumber">
              <p class="bigfont">03</p>
              <div class="underline"></div>
              <div class="page-name">Gallery</div>
            </div>
            </Col>
            <Col style="width:auto;">
           
            </Col>
              
          </div>
        </div>
        <div class="nobox" style="display: flex;justify-content: center;flex-flow:column;">
          <Carousel class="test"
          particlesToShow={4}
          particlesToScroll={2}
        >
        {#each $nfts as nft}
          <div class="nft-card">
            <div class="nft-card-inner">
              <img transition:fade src="/forms/{nft['image']}" style="z-index:2;position:relative;width:256px" alt="">
            </div>
          </div>
        {/each}

        </Carousel>
        </div>
      </div>
		</Container>
	</FullpageSection>
	<FullpageSection style="background:#ee0530!important;"  center>
    <Container style="display:flex;flex-flow:row;justify-content:center;" class="text-center">
      <div class="container-child-wrapper" >
				<div class="container-child-wrapper-padding" >
          <div class="row half">
            <Col style="display:flex;flex-flow:column;justify-content:center;width:auto;">
              <div class="pagenumber">
              <p class="bigfont">04</p>
              <div class="underline"></div>
              <div class="page-name">Process</div>
            </div>
            </Col>
            <Col style="width:auto;">
            <div transition:slide class="description">

              <div class="img-effect">

              <Carousel>
                
                <img transition:fade src="/imgs/forms/line-000346.png" style="z-index:2;position:relative;width:256px" alt="">
                <img transition:fade src="/imgs/forms/line-000234.png" style="z-index:2;position:relative;width:256px" alt="">
                <img transition:fade src="/imgs/forms/line-000382.png" style="z-index:2;position:relative;width:256px" alt="">
               
              </Carousel>   

            </div>
          </div>
            </Col>
              
          </div>
        </div>
        <div style="padding:4rem 2rem; width:auto;display: flex;justify-content: center;flex-flow:column;">
          <div transition:slide class="description">
            <p style="font-size:3rem;font-weight:100;margin:unset!important;">PURCHASING</p>
            <p style="font-size:3rem;font-weight:900;margin:unset!important;"><b>INFORMATION</b></p>
            <p> <b>Purchasing a Geometric Form will cost 0.5 ETH each</b>
              <br><br>
              Owning a FORM will grant you access to monthly art raffles air dropping from Geometric Curated Collections, and minters who hold until 2022 are eligible to claim a high quality physically framed art print out mailed for free.
            </p>
          </div>
        </div>
      </div>
		</Container>
	</FullpageSection>
	<FullpageSection id="mint" style="background:#111!important;"  center>
    <Container style="display:flex;flex-flow:row;justify-content:center;" class="text-center">
      <div class="container-child-wrapper" >
				<div class="container-child-wrapper-padding" >
          <div class="row half">
            <Col style="display:flex;flex-flow:column;justify-content:center;width:auto;">
              <div class="pagenumber">
              <p class="bigfont">05</p>
              <div class="underline"></div>
              <div class="page-name">Mint</div>
            </div>
            </Col>
            <Col style="width:auto;">
            
              <div transition:slide class="description">
                <p style="font-size:3rem;font-weight:100;margin:unset!important;">GEOMETRIC</p>
                <p style="font-size:3rem;font-weight:900;margin:unset!important;"><b>FORMS</b></p>
                <p><b>Here's how to mint</b>
                  <br><br>
                  Click the fox and confirm with metamask
                  <br><br>
                  Click mint, and claim your unique ERC-721 Geometric FORM!
                  <br><br>
                </p>
                {#if !$address}
                  <button on:click={connect} style="margin-left:unset;" class="button-padding">CONNECT WALLET</button>
                {:else}
                  <button on:click={mint} style="margin-left:unset;" class="button-padding">MINT A FORM</button>
                  <br />{addressDisplay}  
                {/if}                
                

              </div>
            </Col>
              
          </div>
        </div>
        <div class="second-container">
      <iframe src="/metamask.html" class="metamask-container" frameborder="0"></iframe>
        </div>
      </div>
		</Container>
	</FullpageSection>
  <!--
	<FullpageSection {slides} class="bg-info" arrows>
		<FullpageSlide center>
			<Container class="text-center">
				<Row>
					<Col>
						<h1>Slides</h1>
						<p>
							There is also component for slides as you can see.
							Try to drag/swipe right or left, also you can use arrows.
						</p>
					</Col>
				</Row>
			</Container>
		</FullpageSlide>
		<FullpageSlide class="bg-danger" center>
			<Container class="text-center">
				<Row>
					<Col>
						<h1>Another slide</h1>
						<p>
							You can style every individual slide, notice background change.
						</p>
					</Col>
				</Row>
			</Container>
		</FullpageSlide>
		<FullpageSlide class="bg-success" center>
			<Container class="text-center">
				<Row>
					<Col>
						<h1>Embeds</h1>
						<p>
							svelte-fullpage supports also embeds and iframes, scroll down to see example, you will see
							page but loaded using embed. Scrolling on embaded page is enabled, but also fulpage
							scrolling is still working, try to scroll hovering over fullpage section indicator (grey dots).
						</p>
					</Col>
				</Row>
			</Container>
		</FullpageSlide>
	</FullpageSection>-->


</Fullpage>

<style type="text/scss">
.container-child-wrapper{width:100vw;height:100vh;display:flex;flex-flow:row;justify-content:flex-start;}
.img-effect{display: flex;height:512px;width:512px;position:relative;margin:auto;}
 .rotate-title{transform:rotate(-90deg);text-align:left;width:min-content;
}.imgbox{max-height:504px;max-width:504px;position:absolute;width:504px;height:504px;margin-left:1rem;margin-top:-1rem;border:4px solid white;}
.description{text-align:left;margin-left:8rem;width:512px;}
.half{width:auto;}
.hero-title{padding-left: 4rem;padding-top:4rem;padding-bottom:4rem;width:512px;height:calc(100vh - 8rem);display:flex;flex-flow:column;justify-content:center;background:#333!important;}
.logo-container-2{height:512px;width:512px;}
.nobox{width:calc(100vw - 18rem);}
.underline{height:1px;margin-bottom:1rem;background-color:white;}
.button-padding{padding:1rem;margin-bottom:2rem;margin-right:2rem;}
.row{display:flex;flex-flow:row;}
.nft-card{display: flex;
flex-flow: row;
justify-content: center;background-color:#111;width:calc(256px + 2rem);height:512px;transition:all 0.2s ease;}
.nft-card-inner{padding-top:1.75rem;background-color:black;width:320px;height:512px;transition:all 0.2s ease;}
.nft-card-inner > img {border-radius:256px;}
.nft-card-inner:hover{background-color:#ee0530;}
.container-child-wrapper-padding{
  padding-left: 4rem;
  padding-top:4rem;
  padding-bottom:4rem;
  width:auto;
  height:calc(100vh - 8rem);
  display:flex;
  flex-flow:column;
  justify-content:center;}
  .bigfont{font-size:5rem;}
  .geometry-container{width:800px;height:800px;border-radius:400px;margin:auto;}
  .col-mod{display:flex;flex-flow:column;justify-content:center;width:auto;}
  .iframe-wrap{padding:4rem 8rem; width:100%;display: flex;justify-content: flex-end;}
  .metamask-container{overflow:hidden;height:512px;width:512px;border:unset;}
  .second-container{padding:4rem 8rem; width:100%;display: flex;justify-content: center;flex-flow:column;}
  .slider-wrap{padding-right: 4rem;padding-left: 4rem;padding-top:4rem;padding-bottom:4rem;width:auto;height:calc(100vh - 8rem);display:flex;flex-flow:column;justify-content:center;}
@media screen and (max-width:1600px){
  .slider-wrap{
    padding-right: 4rem;
    padding-left: 4rem;
    padding-top:4rem;
    padding-bottom:4rem;
    width:auto;
    height:calc(100vh - 8rem);
    display:flex;
    flex-flow:column;
    justify-content:center;}
    .img-effect{display: flex;height:300px;width:300px;position:relative;margin:auto;}
    .imgbox{max-height:292px;max-width:292px;position:absolute;width:292px;height:292px;margin-left:1rem;margin-top:-1rem;border:4px solid white;}
    .second-container{padding:2rem 2rem; width:auto;display: flex;justify-content: center;flex-flow:column;}
    .bigfont{font-size:3rem;line-height: 3rem!important;}

  .container-child-wrapper{
    width:100vw;
    margin-top:100px;
    height:100vh;
    display:flex;
    flex-flow:column;
    justify-content:flex-start;}   
 
    .iframe-wrap{padding:2rem 2rem; width:calc(100% - 4rem);display: flex;flex-flow:column;justify-content: flex-end;height:70%;}
    .geometry-container{width:400px;height:400px;border-radius:400px;margin:auto;}
    .svelte-fp-indicator{width:4rem!important;}
    .container-child-wrapper-padding{
  padding-left: 2rem;
  padding-top:2rem;
  padding-bottom:2rem;
  padding-right:2rem;
  width:auto;
  height:50%;
  display:flex;
  flex-flow:column;
  justify-content:center;}
  .col-mod{display:flex;flex-flow:column;justify-content:center;width:auto;height:100vh;}

    .rotate-title{margin-left:2rem;transform:rotate(0deg);text-align:left;width:100vw; }

    .description{text-align:left;margin-left:0px;width:auto;padding-right:0px;}

    .hero-title{margin-top: -100px;padding-left: 2rem;padding-top:2rem;padding-bottom:2rem;width:100vw;height:30%;display:flex;flex-flow:column;justify-content:center;background:#333!important;}

}
@media screen and (max-width:900px){

}
</style>
