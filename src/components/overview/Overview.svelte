<script>
  export let height=undefined;
  
  let src_gif = './images/gps.gif';
  let src_deeptrekker = './images/deep_trekker_cropped.jpg';
  export let mobile;

  let overviewElement;
  let text=[`Our product is called Distributed Underwater Positioning (DUP). DUP allows robots underwater to determine their position in 3D space through a system of multilateration relative to fixed beacons, much like how GPS works above water.`,
    "The need for this tech was brought to our attention by our stakeholder, Deep Trekker, who found that existing solutions in this domain didn't meet the requirements for positioning of their Remotely Operated underwater Vehicle (ROV) as it performs tasks. We're now working with Deep Trekker to design a module that can be affixed to the ROV, to perform precise positioning relative to fixed beacons that will be affixed underwater nearby.",
    "The DUP system will consist of a transponder node attached to the mobile ROV and several stationary transponder nodes. The ROV and the stationary nodes will send acoustic signals back and forth. The time of flight of these signals will be used to determine the position of the ROV."
  ]
  
  import { onMount } from 'svelte';
  onMount(async => {
    const bar = () => {
      height = overviewElement.offsetHeight;
    }
    setTimeout(bar, 10);
  });
</script>

<style>
  div#overview{
    width: 100%;
    height: 100%;
    /* background-color: #0B1237; */
    background-color: #031767;
    display: flex;
    flex-flow: column nowrap;
    /* padding: 40px 15px 40px 15px; */
    padding: 70px;
  }
  div.dark-container{
    background-color: #0B1237;
    border-radius: 5px;
  }

	div.vstack{
		display: flex;
		flex-flow: column nowrap;
		padding: 10px 40px;
	}

  div.hstack{
    display: flex;
    flex-flow: row nowrap;
    align-items: stretch;
  }
  div.hstack.mobile{
    flex-flow: row wrap;
  }

  div#overview.mobile{
    padding: 50px 20px 60px 20px;
  }

  h1{
    font-size: 50px;
    /* text-transform: uppercase; */
    color: #f7f5f4;
    font-weight: 700;
		font-family: "Roboto Slab" "Times New Roman", serif;
    /* font-family: "DIN Condensed Web", "Open Sans", "Helvetica", sans-serif; */
    margin-bottom: 25px;
  }

  h1.mobile{
    font-size:24px;
    font-weight: 500;
    max-width:100%;
    overflow-wrap: normal;
  }

	.clip-top{
		position: relative;
		margin-top: -40px;
	}

  .card{
		/* background-color: #f7f5f4; */
		/* background-color: #0B1237; */
		padding: 15px;
		border-radius: 6px;
    box-shadow: 0 16px 38px -12px rgb(0 0 0 / 56%), 0 4px 25px 0px rgb(0 0 0 / 12%), 0 8px 10px -5px rgb(0 0 0 / 20%)
	}
	div.card1{
		/* background-color: #f7f5f4; */
		background-color: #5f5DAB;
		/* background-color: #fefefe; */
		background-color: #0B1237;
	}
	div.card2{
		background-color: #5f5DAB;
		background-color: #0B1237;
	}

  p{
    /* color: #c3c4c5; */
    width: 100%;
		color: #0B1237;
		color: #f7f5f4;
    /* font-family: "Source Sans Pro", "Helvetica", sans-serif; */
    font-weight: 300;
		font-family: "Roboto", "Helvetica", "Arial", sans-serif;
    line-height: 1.65;
    font-size: 19px;
    margin-bottom: 15px;
  }
  p.mobile{
    text-align: justify;
    width: 100%;
    font-weight: 400;
    font-family: "Helvetica", serif;
    font-size:18px;
  }

  img.card{
		padding: 0px;
    width: 100%;
		opacity: 1;
		margin-left: 70px;
		margin-right: auto;
		margin-left: auto;
		margin-bottom: 25px;

		/* box-shadow: 16px 38px -12px rgb(0,0,0) */
    box-shadow: 0 16px 38px -12px rgb(0 0 0 / 56%), 0 4px 25px 0px rgb(0 0 0 / 12%), 0 8px 10px -5px rgb(0 0 0 / 20%)
  }
  img.mobile{
    width: 100%;
		border-radius: 10px;
  }

</style>
<div id='overview'
  class:mobile
  bind:this={overviewElement}
  bind:offsetHeight={height}>
    <h1 class:mobile>Overview</h1>
    {#if !mobile}
      <div class='hstack' class:mobile>
        <div class='card card1'>
        {#each text as t}
          <p class:mobile>{t}</p>
        {/each}
        </div>
				<div class='card card2 vstack' style="margin-left: 40px;">
					<img alt='demo gif' class= "clip-top card" id='demo-gif' src={src_gif}/>
					<img class="clip-top card" style="margin-top: 0;" alt='deep trekker robot' id='deeptrekker' src={src_deeptrekker}/>
				</div>
      </div>
    {:else}
      <p class:mobile>{text}</p>
    {/if}
</div>
