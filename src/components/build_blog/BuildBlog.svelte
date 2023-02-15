<script>
  export let height=undefined;
  
  export let mobile;
  export let width;


  let base = './images/build_blog/';

  let items = [
    {
      title: 'Build Blog Week 1 (Jan 27th)',
      images: [
        "mould.jpg",
        "packages.jpg",
        "piezo.jpg",
        "machining.jpg"
      ],
      paragraphs:
			['This week, we finalized our BOM, and received our Acetal tube, Teensy microprocessors, electronics, and polyurethane. We machine a prototype acetal tube using a lathe at the engineering machine shop on campus. The end cap mould was 3d printed, ready to be have polyurethane poured into it to seal the pressure vessel. On the software side, we received the teensy microprocessors we intend to use, and are now working on implementing a data collection system for the testing phase in mid February. We also finalized the coding and testing our main algorithms for the project.  We also finalized our testing plan in collaboration with our stakeholder, Deep Trekker']
		},{
      title: 'Build Blog Week 2 (Feb 3)',
      images: [
				'teensy_networking.jpg',
				"tubes.jpg"
      ],
      paragraphs:
			['On the mechanical side, the first potted unit was built to help develop the manufacturing process of the transponder. Milling operations on 2 units (including the main bodies and caps) were completed. Later this week 2 full unit builds will be accomplished and tested for mechanical durability at 50m depth.',
			'On the software side, we got teensy microprocessors set up and tested some algorithms. We were able to run the discrete sliding window fourier transform 3x faster than needed! ']
		},{
      title: 'Build Blog Week 3 (Feb 10)',
      images: [
				"boards.jpg",
      ],
      paragraphs:
			['Electrical systems made a lot of progress this week. All 3 regulators are working, we have DAC sine wave generation, High voltage sine amplification, Input signal filtering and amplification, and the Transmit / receive switching relay. At a higher level, we have 3 out of 4 PCBs under construction, ~50% complete. On the software side we are working on defining all the messages and datatypes, and serializing and deserializing on both the client and server sides.'
			]
		}

  ]

	$: wide = width > 900;

  let blogElement;
  import { onMount } from 'svelte';
  onMount(async => {
    const bar = () => {
      height = blogElement.offsetHeight;
    }
    setTimeout(bar, 10);
  });
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

  img.blog-image-sqr{
    width: 100%;
    object-fit: cover;
  }

</style>

<div id='buildBlog'
  class:mobile
  bind:this={blogElement}
  bind:offsetHeight={height}>
    <h1 class:mobile>Build Blog</h1>
    {#each items as item}
      <div class='vstack' style="flex-flow: {wide?'row nowrap;':'row wrap;'}">
        <div class="card card1">
          <h3>{item.title}</h3>
          {#each item.paragraphs as paragraph}
            <p>
              {paragraph}
            </p>
          {/each}
        </div>
      <div class="card card1" style="display: flex; flex-flow: column nowrap;">
        <h3>Images</h3>
        <!-- {#if wide} -->
        <!-- <div class="hstack"> -->
        <!-- {#each item.images as image} -->
        <!-- <img class='blog-image-sqr' alt='alt' src={base+image}/> -->
        <!-- {/each} -->
        <!-- </div> -->
        <!-- {:else} -->
					<div class="vstack">
						{#each item.images as image}
							<img class='blog-image-sqr' alt='alt' src={base+image}/>
						{/each}
					</div>
          <!-- {/if} -->
			</div>
		</div>
    {/each}
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
