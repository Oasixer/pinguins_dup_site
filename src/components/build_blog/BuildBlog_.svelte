<script>
  import NextButton from './NextButton.svelte';
  import { onMount } from 'svelte';

  export let height=undefined;
  
  export let mobile;
  export let width;

	/* $: wide = width > 800; */

  let blogElement;
  let displayedItem = 0;

  onMount(async => {
    const bar = () => {
      height = blogElement.offsetHeight;
    }
    setTimeout(bar, 10);
  });

  let base = './images/build_blog/';
  let clickingPrev=false;

  let items=[
    {
      title: 'Autonomous Robot Race Winner',
      img: '380.png',
      text: '1st place out of 23 teams'
    },
    {
      title: 'Autonomous Robot Race Winner',
      img: '380.png',
      text: '1st place out of 23 teams'
    },
    {
      title: 'Autonomous Robot Race Winner',
      img: '380.png',
      text: '1st place out of 23 teams'
    },
    {
      title: 'Autonomous Robot Race Winner',
      img: '380.png',
      text: '1st place out of 23 teams'
    },
    {
      title: 'Autonomous Robot Race Winner',
      img: '380.png',
      text: '1st place out of 23 teams'
    },
    {
      title: 'Autonomous Robot Race Winner',
      img: '380.png',
      text: '1st place out of 23 teams'
    },
  ];
</script>

<style>
  div#buildBlog{
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
    flex-flow: row wrap;
    align-items: stretch;
  }

  div.hstack.mobile{
    flex-flow: row wrap;
  }

  div#buildBlog.mobile{
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

 /* uhhh i changed my mind about clip top   */
	.clip-top{
		position: relative;
		/* margin-top: -40px; <-- actual clip-top (img protrudes above its card container; a sort of quirky modern design. Decided I dont like it anymore but leave this for future ref.). */
		margin-top: 20px;
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
		max-width: 400px;
	}
	/* div.card2{ */
		/* background-color: #5f5DAB; */
		/* background-color: #0B1237; */
	/* } */
	div.card2{
		background-color: #5f5DAB;
		background-color: #0B1237;
		max-width: 400px;
	}
	div.card1.wide{
		width: 40vw;
		max-width: 800px;
	}
	div.card2.wide{
		width: 30%;
		max-width: 800px;
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

  h3{
    font-weight: 700;
		font-family: "Roboto Slab" "Times New Roman", serif;
    font-size: 24px;
    color: #031767;
    color: #f7f5f4;
    margin-left: 0;
		margin-bottom: 0;
  }

/* --------------------------- */

  div.displayItem{
    background-color: white;
    z-index: 1000;
    display: flex;
    flex-flow: column nowrap;
    /* align-items: center; */
    padding: 0px 15px 20px 15px;
  }

  div.displayItem.mobile{
    padding: 0px 5px 10px 5px;
  }

  div.displayMain{
    /* position: fixed; */
    /* top: 50%; */
    /* left: 50%; */
    /* transform: translate(-50%, -50%); */
    width: 680px;
    max-width: 90%;
    max-height: 96vh;
    overflow-y: scroll;
    overflow-x: hidden;
  }
  div.displayMain.wider{
    width: 980px;
  }
  .displayText{
    width: 500px;
    margin: 20px 0px 0px 0px;
  }
  .displayText.mobile{
    width: 100%;
  }

  div.displayItem a{
    margin: 10px 0px 0px 0px;
    color: blue;
  }
  div.displayItem a:link{
    color: blue;
  }
  div.displayItem a:visited{
    color: darkblue;
  }
  div.displayItem a:hover{
    color: cyan;
  }
  div.displayItem a.mobile{

  }
  
  /* mobile */
  @media all and (max-width: 850px){
    div.displayMain{
      width: 660px;
    }
  }

  .displayHeader{
    font-family: "Open Sans", sans-serif;
    font-weight: 300;
    margin: 30px 0px;
    margin-right: auto;
    font-size: 25px;
  }
	div.background-fade{
		background: rgba(0,0,0,0.7);
		position: fixed;
		top: 0;
		left: 0;
		bottom: 0;
		right: 0;
		overflow: auto;
		/* background: lime; [> Just to visualize the extent <] */
		z-index: 10;
	}
</style>

<div id='buildBlog'
  class:mobile
  bind:this={blogElement}
  bind:offsetHeight={height}>
    <h1 class:mobile>BuildBlog</h1>
		<div class='vstack'>
			<div class="card card1">
        <h3>Build Blog Week 1 (Jan 27th)</h3>
        <p>
This week, we finalized our BOM, and received our Acetal tube, Teensy microprocessors, electronics, and polyurethane. We machine a prototype acetal tube using a lathe at the engineering machine shop on campus. The end cap mould was 3d printed, ready to be have polyurethane poured into it to seal the pressure vessel. On the software side, we received the teensy microprocessors we intend to use, and are now working on implementing a data collection system for the testing phase in mid February. We also finalized the coding and testing our main algorithms for the project.  We also finalized our testing plan in collaboration with our stakeholder, Deep Trekker
        </p>
			</div>
<NextButton prev={true} on:click={()=>{clickingPrev=displayedItem==1?true:false; displayedItem-=1;}}/>
{#if displayedItem != -1}
      <div class="card card1" style="display: flex; flex-flow: column nowrap;">
        <h3>Images</h3>
        <div class='displayItem displayMain' class:mobile>
          <!-- {#if displayedItem>0 && !mobile} -->
						<NextButton prev={true} on:click={()=>{clickingPrev=displayedItem==1?true:false; displayedItem-=1;}}/>
            <!-- {/if} -->
					<h3 class='displayHeader' class:mobile>{items[displayedItem].title}</h3>
					<!--  <div class='full-img-container'>  -->
					<!--{#if displayedItem.} -->
						<img
							class='full'
							class:mobile
							alt='{items[displayedItem].img}'
							id={'full-'+items[displayedItem].img.slice(0,items[displayedItem].img.length-4)}
							src={base + items[displayedItem].img}
							on:click={()=>{updateDisplayedItem(items[displayedItem].numFromTotal)}}/>
							<!--  </div>  -->
              <p class='displayText' class:mobile>{items[displayedItem].text}</p>
					{#if displayedItem<items.length-1 && !mobile}
						<NextButton prev={false} on:click={()=>{displayedItem+=1}}/>
					{/if}
				</div>
			</div>
{/if}
		</div>
		<!--
    {#if !mobile}
      <div class='hstack' class:mobile>
				<div class='card card1' class:wide>
        {#each text as t}
          <p class:mobile>{t}</p>
        {/each}
        </div>
				<div class='card card2 vstack' class:wide style="margin-left: 40px;">
					<img alt='demo gif' class= "clip-top card" id='demo-gif' src={src_gif}/>
					<img class="clip-top card" style="margin-top: 0;" alt='deep trekker robot' id='deeptrekker' src={src_deeptrekker}/>
				</div>
      </div>
    {:else}
      <p class:mobile>{text}</p>
				<div class='card card2 vstack' class:wide style="margin-left: 40px;">
					<img alt='demo gif' class= "clip-top card" id='demo-gif' src={src_gif}/>
					<img class="clip-top card" style="margin-top: 0;" alt='deep trekker robot' id='deeptrekker' src={src_deeptrekker}/>
				</div>
		{/if} -->
</div>
