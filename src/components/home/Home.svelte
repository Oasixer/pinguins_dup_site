<script>
  export let height=undefined;
  export let bg_color; // unused bc we use a seperate color for home
  export let mobile;

  import { onMount, createEventDispatcher } from 'svelte';

  let src_concept_art = './images/artsy_concept_art.png';
  let src_cad = './images/cad_enclosed.png';
  
  let homeElement;
  let mounted = false;
  onMount(async => {
    const bar = () => {
      height = homeElement.offsetHeight;
    }
    setTimeout(bar, 10);
    mounted = true;
  });
</script>

<style>

/* .row { */
  /* display: flex; */
  /* flex-wrap: wrap; */
  /* padding: 0; */
/* } */

/* [> Create four equal columns that sits next to each other <] */
/* .column { */
  /* [> flex: 0 1 1; <] */
  /* flex: 33.3%; */
  /* max-width: 33.3%; */
  /* padding: 0 4px; */
/* } */

/* .column img { */
  /* margin-top: 8px; */
  /* vertical-align: middle; */
  /* width: 100%; */
/* } */

/* [> Responsive layout - makes a two column-layout instead of four columns <] */
/* @media screen and (max-width: 800px) { */
  /* .column { */
    /* flex: 50%; */
    /* max-width: 50%; */
  /* } */
/* } */

/* [> Responsive layout - makes the two columns stack on top of each other instead of next to each other <] */
/* @media screen and (max-width: 600px) { */
  /* .column { */
    /* flex: 100%; */
    /* max-width: 100%; */
  /* } */
/* } */
  div#home{
    width: 100%;
    height: 100vh;
    /* background-color: #400857; */
    background-color: #000033;
    display: flex;
    flex-flow: column nowrap;
    /* padding: 40px 15px 40px 15px; */
		padding: 0 0 0 0;
  }
  div#home.mobile{
    padding: 15px;
  }

  h1#title{
    margin:0;
    letter-spacing: 4px;
    font-family: "Open Sans", sans-serif;
    text-transform: uppercase;
    font-weight: 800;
    font-size: 50px;
    color: #ffe32e;
    /* position: absolute; */
    /* z-index: 2; */
    /* top: 40px; */
    /* left: 5%; */
    margin: 0;
    padding: 0;
  }
	div.hstack{
		display: flex;
		flex-flow: row nowrap;
	}

	div#filler{
		opacity: 60%;
		background-color: #ffffff;
		width: 100vw;
		height: 100%;
    overflow: hidden;
	}
	img{
		opacity: 60%;
	}
	img#concept-art{
		width: 60%;
		max-width: 60%;
    /* border-radius: 7px; */
	}
	img#cad{
		width: 40%;
		max-width: 40%;
    /* border-radius: 7px; */
	}
	div.fullscreen-invisible{
		width: 100vw;
		height: 100vh;
    position: absolute;
    background-color: rgba(0,0,0,0);
    display: flex;
	}
	button{
    cursor: pointer;
    border: none;
    background: none;
    outline: none;
    font-weight: 400;
    font-family: "Helvetica", serif;
    font-size:35px;
		width: 300px;
		height: 70px;
    background-color: #5599cc;
    /* color: #000000; */
    color: #ffffff;
    border-radius: 5px;
    padding: 9px;
		z-index: 20;
    opacity: 100%;
    margin: 20vh auto 0 auto;
	}
  button:active{
    background: none;
    outline: none;
  }
  
  button:hover{
    /* color: #f3f5f4; */
    background-color: #225599;
  }

  button.selected:focus{
    outline: none;
  }
</style>

<div id='home' class:mobile bind:offsetHeight={height} bind:this={homeElement}>
	<!-- {#if mobile === false && mounted} -->
	<!-- <h1 id='title'>Pinguins</h1> -->
	<!-- {/if} -->
	<!-- <div> -->
	<div class="hstack">
		<img id="concept-art" src={src_concept_art}/>
		<img id="cad" src={src_cad}/>
	</div>
	<div id="filler"></div>

	<!-- </div> -->
  <div class="fullscreen-invisible">
    <button>Learn More</button>
  </div>
</div>
