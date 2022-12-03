<script>
  export let height=undefined;
  
  /* let src_gif = './images/gps.gif'; */
  let src_cutaway = './images/cad_cutaway.png';
  export let bg_color;
  export let mobile;

  let aboutElement;
  let text=``
  
  import { onMount } from 'svelte';
  onMount(async => {
    const bar = () => {
      height = aboutElement.offsetHeight;
    }
    setTimeout(bar, 10);
  });
</script>

<style>
  div.row{
    display: flex;
    flex-flow: row wrap;
    align-items: flex-start;
  }

  img#uw-pic{
    margin-top: -30px;
  }
  div#specs{
    width: 100%;
    padding: 70px;
    display: flex;
    flex-flow: column nowrap;
  }
  div#specs.mobile{
    padding: 50px 20px 60px 20px;
  }

	div.hstack-overflow{
		display: flex;
		flex-flow: row wrap;
	}
  
  h3{
    font-size: 28px;
    color: #b3e5e4;
    margin-left: 0;
		margin-bottom: 0;
  }

	ul{
		padding-left: 25px;
	}
	li{
		font-weight: 400;
		font-family: "Helvetica", serif;
		font-size:18px;
		color: #cccccc;

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
  }
  /* p.mobile{ */
    /* text-align: justify; */
    /* width: 100%; */
    /* font-weight: 400; */
    /* font-family: "Helvetica", serif; */
    /* font-size:18px; */
  /* } */

  img{
    width: 30%;
		margin-left: auto;
  }
  img.mobile{
    width: 100%;
  }

</style>
<div id='specs'
  style="background-color: {bg_color}"
  class:mobile
  bind:this={aboutElement}
  bind:offsetHeight={height}>
  <h1 class:mobile>Specifications</h1>
  <div class='hstack-overflow'>
    <div class='vstack'>
      <h3>Operational specs</h3>
      <ul>
        <li>
          Range: 1-50m
        </li>
        <li>
          Accuracy: +/- 1m
        </li>
        <li>
          Positioning Refresh Rate: 10 Hz
        </li>
        <li>
          Calibration Time: 300 seconds
        </li>
        <li>
          Required Support Nodes: 3-6
        </li>
        <li>
          Inter-Nodal Rangefinding: Acoustic Time-of-Flight
        </li>
        <li>
          Inter-Nodal Communication: Acoustic Frequency Shift Modulation
        </li>
        <li>
          Communication to Master node: Ethernet
        </li>
      </ul>
      <h3 style="margin-top: 25px;">Physical specs</h3>
      <ul>
        <li>
          Depth rating: 10m
        </li>
        <li>
          Peak power draw: 15W
        </li>
        <li>
          Input Voltage: 12-24V
        </li>
      </ul>
    </div>
    <img alt='img cutaway' id='cutaway' src={src_cutaway}/>
  </div>
</div>
