<script>
  export let height=undefined;
  
  /* let src_gif = './images/gps.gif'; */
  let src_cutaway = './images/cad_cutaway.png';
  let src_fourier = './images/fourier.gif';
  export let bg_color;
  export let mobile;
  export let width;

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
  div#specifications{
    width: 100%;
    height: 100%;
    /* background-color: #0B1237; */
    background-color: #031767;
    display: flex;
    flex-flow: column nowrap;
    /* padding: 40px 15px 40px 15px; */
    padding: 70px;
  }
  div#specifications.mobile{
    padding: 50px 20px 60px 20px;
  }

  div.row{
    display: flex;
    flex-flow: row wrap;
    align-items: flex-start;
  }
  div.hstack{
    display: flex;
    flex-flow: row nowrap;
    align-items: stretch;
  }
  div.hstack.mobile{
    flex-flow: row wrap;
  }

	div.hstack-overflow{
		display: flex;
		flex-flow: row wrap;
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

	ul{
		padding-left: 25px;
	}
	li{
		color: #0B1237;
    color: #f7f5f4;
    width: 70%;
    font-weight: 300;
		font-family: "Roboto", "Helvetica", "Arial", sans-serif;
    line-height: 1.65;
    font-size: 19px;
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
  
  .card{
		/* background-color: #f7f5f4; */
		/* background-color: #0B1237; */
		padding: 15px;
		border-radius: 6px;
    box-shadow: 0 16px 38px -12px rgb(0 0 0 / 56%), 0 4px 25px 0px rgb(0 0 0 / 12%), 0 8px 10px -5px rgb(0 0 0 / 20%)
	}
	div.card-light{
    /* background-color: #f7f5f4; */
		/* background-color: #5f5DAB; */
		background-color: #0B1237;
	}


  /* p.mobile{ */
    /* text-align: justify; */
    /* width: 100%; */
    /* font-weight: 400; */
    /* font-family: "Helvetica", serif; */
    /* font-size:18px; */
  /* } */
	div.card2{
		/* background-color: #5f5DAB; */
		background-color: #0B1237;
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
  }
	.clip-top{
		position: relative;
		margin-top: 10px;
	}
</style>
<div id='specifications'
  class:mobile
  bind:this={aboutElement}
  bind:offsetHeight={height}>
  <h1 class:mobile>Specifications</h1>
  <div class='hstack'>
    <div class='vstack card card-light'>
      <h3>Operational Specs</h3>
      <ul>
        <li>
          Range: 1-50m
        </li>
        <li>
          Accuracy: +/- 1m
        </li>
        <li>
          Position Refresh Rate: 10 Hz
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
          Communication with Master Node: Ethernet
        </li>
        <li>
          Mounting: Custom 3D Printed Bracket Tailored to Customer Requirements
        </li>
        <li>
          Transponder Dimensions: 2" (Diameter), 6.5" (Length)
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
          Average power draw: 5W
        </li>
        <li>
          Input Voltage: 12-24V
        </li>
      </ul>
    </div>
      <div class='card card2 vstack' style="margin-left: 40px; max-width: 35%;">
        <img alt='fourier gif' class= "clip-top card" id='fourier-gif' src={src_fourier}/>
        <img class="clip-top card" style="margin-top: 0;" alt='deep trekker robot' id='cutaway' src={src_cutaway}/>
      </div>
  </div>
</div>
