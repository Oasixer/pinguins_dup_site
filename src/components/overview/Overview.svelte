<script>
  export let height=undefined;
  
  let src_gif = './images/gps.gif';
  export let bg_color;
  export let mobile;

  let overviewElement;
  /* let text=`I'm a fourth year Mechatronics Engineering student at the University of Waterloo. I'm currently looking for full time opportunities, now that I've finished my 6 internships. I love to design algorithms that solve difficult tasks, and I live for the satisfaction of closing a hundred chrome tabs when the test cases finally pass. I was a competitive climber from age 10-18, and I love all kinds of rock climbing, especially outdoor bouldering.` */

  /* - i like to keep up with the latest tech, languages, etc */
  /* - I like to automate anything that can be automated (and some things that probably shouldn't be automated) so I can focus */
  /* - 3d printing? */
  let text=[`Our product is called Distributed Underwater Positioning (DUP). DUP allows robots underwater to determine their position in 3D space through a system of triangulation relative to fixed beacons, much like how GPS works above water.`,
    "The need for this tech was brought to our attention by our stakeholder, Deep Trekker, who found that existing solutions in this domain didn't meet the requirements for positioning of their Remotely Operated underwater Vehicle (ROV) as it performs tasks. We're now working with Deep Trekker to design a module that can be affixed to the ROV, to perform precise positioning relative to fixed beacons that will be affixed underwater nearby."
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
  div.hstack{
    display: flex;
    flex-flow: row nowrap;
    align-items: center;
  }
  div.hstack.mobile{
    flex-flow: row wrap;
  }

  img#uw-pic{
    margin-top: -30px;
  }
  div#overview{
    width: 100%;
    padding: 70px;
    display: flex;
    flex-flow: column nowrap;
  }
  div#overview.mobile{
    padding: 50px 20px 60px 20px;
  }

  h1{
    font-size: 70px;
    text-transform: uppercase;
    color: #f3f5f4;
    font-weight: 100;
    font-family: "DIN Condensed Web", "Open Sans", "Helvetica", sans-serif;
    margin-bottom: 25px;
  }

  h1.mobile{
    font-size:24px;
    font-weight: 500;
    max-width:100%;
    overflow-wrap: normal;
  }

  p{
    color: #c3c4c5;
    width: 70%;
    font-family: "Source Sans Pro", "Helvetica", sans-serif;
    font-weight: 300;
    line-height: 1.65;
    font-size: 20px;
    margin-bottom: 15px;
  }
  p.mobile{
    text-align: justify;
    width: 100%;
    font-weight: 400;
    font-family: "Helvetica", serif;
    font-size:18px;
  }

  img{
    width: 30%;
  }
  img.mobile{
    width: 100%;
  }

</style>
<div id='overview'
  style="background-color: {bg_color}"
  class:mobile
  bind:this={overviewElement}
  bind:offsetHeight={height}>
  <h1 class:mobile>Overview</h1>
    {#if !mobile}
      <div class='hstack' class:mobile>
        <div>
        {#each text as t}
          <p class:mobile>{t}</p>
        {/each}
        </div>
        <img alt='demo gif' id='demo-gif' src={src_gif}/>
      </div>
    {:else}
      <p class:mobile>{text}</p>
    {/if}
</div>
