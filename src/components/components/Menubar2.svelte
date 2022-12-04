<script>
  export let floaty;
  export let sections;
  export let curSection;
  export let mobile=false;
  export let mobileSidebarOpen=false;
  export let y;

  let width;

  import Hamburger from './Hamburger.svelte';
  import { onMount, createEventDispatcher } from 'svelte';
	import { fly } from 'svelte/transition';
  
  const dispatch = createEventDispatcher();
  const dispatcher = (args) => dispatch('move', {args:args});
  
  let src_logo_transparent = './images/pinguins_logo_v5_transparent.png';

  const displayHamburgerHeight = 250;

  let menubarOuterDiv;

  function test(){
    console.log('hi!');
  }

	$: sectionsFiltered = sections.filter(i=>!i.excludeFromMenubar);
  /* $: sectionsRight = sections.slice(1).filter(i=>!i.excludeFromMenubar); */
  /* $: sectionsLeft = sections.slice(0,2).filter(i=>!i.excludeFromMenubar); */
  /* $: sectionsRight = sections.slice(2).filter(i=>!i.excludeFromMenubar); */
  $: floaty = mobile ? y > 250 : floaty;
  /* $: widthLT = Math.ceil(width / 50)*50 */

  function runMoveDispatcher(n){
    dispatcher({n:n});
    if (mobileSidebarOpen){
      mobileSidebarOpen = false;
    }
    /* console.log('move-base'); */
  }

  onMount(() => {
    /* console.log('floaty: '+floaty); */
  });
  
</script>

<style>
  div.menubar{
    width: 100%;
    /* background-color: #081012; */
    /* background-color: orange;  */
		/* background-color: blue; */
		background-color: #759ACE;
		/* orange;  */
      /* #ea8676; */
    height: 80px;
    display: flex;
    margin: 0;
    align-items: center;
    max-width: 100%;
    overflow: hidden;
    box-shadow: 0 16px 38px -12px rgb(0 0 0 / 56%), 0 4px 25px 0px rgb(0 0 0 / 12%), 0 8px 10px -5px rgb(0 0 0 / 20%)
  }

  div#singleButton{
    position:fixed;
    left:13px;
    top:26px;
    z-index: 999;
    width: auto;
    height: auto;
    background-color: #081012;
    padding: 2px 10px;
    opacity: 1;
    animation: fadeIn ease 0.2s;
    -webkit-animation: fadeIn ease 0.2s;
    -moz-animation: fadeIn ease 0.2s;
    -o-animation: fadeIn ease 0.2s;
    -ms-animation: fadeIn ease 0.2s;
  }
  
  div#vertical{
    position:fixed;
    left:0px;
    top:0px;
    z-index: 999;
    height: 100%;
    flex-flow: column nowrap;
  }

  div#mobileMenubar{
    flex-flow: column nowrap;
    /* align-content: center; */
    align-items: center;
    justify-content: space-between;
  }
  
  div.menubar.floaty{
    position: fixed;
    top: 0;
    z-index: 5;
  }

  div.menubar.smaller button{
    font-size: 2.3vw;
  }

  div.group{
    margin: 0;
    padding: 0;
    display: flex;
    flex-flow: row nowrap;
  }

  div.left{
    margin-left: 30px;
    margin-right: auto;
  }

  div.menubar.smaller div.left{
    margin-left: 13px;
  }

  /* div.left.floaty{ */
    /* margin-left: auto; */
    /* margin-right: 0; */
  /* } */
  
  div.menubar.smaller.floaty div.left{
    /* margin-left: auto; */
    /* margin-right: 0; */
  }

  
  div.right{
    margin-left: auto;
    margin-right: 30px;
  }

  /* div.right.floaty{ */
    /* margin-right: auto; */
    /* margin-left: 0; */
  /* } */

  img#logo{
    max-height: 70px;
    margin-bottom: 5px;
  }

  button{
    border: none;
    background: none;
    outline: none;
    cursor: pointer;
    /* color: #50555d; */
    /* color: #100000; */
    color: #f7f5f4;
    text-transform: uppercase;
    font-weight: 500;
    font-size: 16px;
    /* font-family: Montserrat,"Helvetica Neue",Helvetica,Arial,sans-serif; */
    font-family: "Roboto", "Helvetica", "Arial", sans-serif;
    font-weight: 400;
    letter-spacing: 1px;
    /* font-family: "Open Sans", sans-serif; */
    /* font-family: "Helvetica", serif; */
    margin: 0;
    padding: 20px 9px;
    border-radius: 5px;
  }

  div.menubar.smaller button{
    padding: 9px 5px;
  }
  
  div.menubar.floaty.smaller button{
    padding: 9px;
  }

  button:active{
    background: none;
    outline: none;
    background-color: #759ACE;
  }
  
  button:hover{
    /* color: #da9d41; */
    color: #daaa55;
		color: #fffcbf;
		color: #5f5dab;
  }

  button.selected{
    outline: none;
    background-color: #86A8D6;
  }
  button.selected:focus{
    outline: none;
  }

  div.row{
    width: 100%;
    display: flex;
  }

  @keyframes fadeIn {
    0% {opacity:0;}
    100% {opacity:1;}
  }

  @-moz-keyframes fadeIn {
    0% {opacity:0;}
    100% {opacity:1;}
  }

  @-webkit-keyframes fadeIn {
    0% {opacity:0;}
    100% {opacity:1;}
  }

  @-o-keyframes fadeIn {
    0% {opacity:0;}
    100% {opacity:1;}
  }

  @-ms-keyframes fadeIn {
    0% {opacity:0;}
    100% {opacity:1;}
  }
	div.fullscreen-invisible{
		width: 20%;
		height: 80vh;
    margin-top: 35px;
    z-index: 0;
    position: absolute;
    background-color: rgba(0,0,0,0);
    display: flex;
	}
	button#learnMore{
    cursor: pointer;
    border: none;
    background: none;
    outline: none;
    font-weight: 400;
    font-family: "Helvetica", serif;
    font-size:25px;
    text-transform: none;
		width: 300px;
		height: 70px;
    /* color: #000000; */
    color: #ffffff;
    background-color: #86A8D6;
    border-radius: 5px;
    padding: 9px;
		z-index: 20;
    opacity: 100%;
    /* margin: auto; */
    font-family: "Roboto", "Helvetica", "Arial", sans-serif;
    font-weight: 400;
    letter-spacing: 1px;
    /* font-family: "Open Sans", sans-serif; */
    /* font-family: "Helvetica", serif; */
    padding: 20px 9px;
    border-radius: 5px;
		box-shadow: 0 16px 38px -12px rgb(0 0 0 / 56%), 0 4px 25px 0px rgb(0 0 0 / 12%), 0 8px 10px -5px rgb(0 0 0 / 20%);
    /* margin: 35vh auto 0 auto; */
    left: 40%;
		position: absolute;
		z-index: 100;
   -webkit-transform: translateX(-40%);
   -moz-transform: translateX(-40%);
   transform: translateX(-40%);
    top: 40%;
   -webkit-transform: translateY(-40%);
   -moz-transform: translateY(-40%);
   transform: translateY(-40%);
	}
  button#learnMore:active{
    background: none;
    outline: none;
  }
  
  button#learnMore:hover{
    /* color: #f3f5f4; */
		background-color: #759ACE;
  }

  button#learnMore.selected:focus{
    outline: none;
  }
</style>
<svelte:window bind:outerWidth={width}/>
{#if !floaty}
  <!-- <div class="fullscreen-invisible"> -->
	<button id="learnMore"
				 on:click={()=>runMoveDispatcher(1)}>Learn More
	</button>
  <!-- </div> -->
{/if}
<div class='menubar'
     class:floaty
     class:smaller={width<950 && !mobile}
     id={mobile?mobileSidebarOpen?'vertical':y>displayHamburgerHeight?'singleButton':'mobileMenubar':'desktopMenubar'}
     transition:fly="{floaty?{y:-100, duration: 200}:''}">
  {#if mobile}
    <div style="{(mobileSidebarOpen || !floaty)?'position: absolute; left: 20px; top: 26px;':''}">
      <Hamburger bind:open={mobileSidebarOpen}/>
    </div>
    {#if y<displayHamburgerHeight || mobileSidebarOpen}
      <!-- <button class='selected' style='font-size: 20px; font-weight: bold; margin-left: 0; padding-top: 27px;' on:click={()=>runMoveDispatcher(0)}> -->
      <!-- Kaelan Moffett -->
      <!-- </button> -->
    {/if}
    {#if mobileSidebarOpen}
      {#each [...sectionsLeft, ...sectionsRight] as section, n}
        <button
          class:selected={curSection==n}
          style="{n===0?'margin-top:25px;':n===sectionsLeft.length+sectionsRight.length-1?'padding-bottom: 27px':''}"
          on:click={()=>runMoveDispatcher(n)}>
          {section.name}
        </button>
      {/each}
    {/if}
  {:else} <!-- non mobile -->
    <div class='group left' class:floaty>
      <img id='logo' src={src_logo_transparent}/>
		</div>
    <!-- {#each sectionsFiltered as section, n} -->
        <!--
        <button
          class:selected={curSection==n}
          on:click={()=>runMoveDispatcher(n)}>
          {section.name}
        </button>
        -->
        <!-- {/each} -->
        <!-- </div> -->
    <!-- {#if !floaty} -->
    <!-- <button class='selected' on:click={()=>runMoveDispatcher(0)}> -->
    <!-- Kaelan Moffett -->
    <!-- </button> -->
    <!-- {/if} -->
    <div class='group right' class:floaty>
      {#if !mobile}
        {#each sectionsFiltered as section, n}
          <button
            class:selected={curSection==n}
            on:click={()=>runMoveDispatcher(n)}>
            {section.name}
          </button>
        {/each}
      {/if}
    </div>
  {/if}
</div>
