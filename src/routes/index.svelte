<script>
  import Home from '../components/home/Home.svelte';
  import Overview from '../components/overview/Overview.svelte';
  /* import Portfolio from '../components/portfolio/Portfolio.svelte'; */
	import Menubar from '../components/components/Menubar2.svelte';
	import Specifications from '../components/specifications/Specifications.svelte';
	import Team from '../components/team/Team.svelte';
  /* import WorkExperiencePage from '../components/resume/WorkExperiencePage.svelte'; */
  /* import ResumePage from '../components/resume/ResumePage.svelte'; */
	import BuildBlog from '../components/build_blog/BuildBlog.svelte';
  import BackToTop from '../components/components/BackToTop.svelte';
  import Hamburger from '../components/components/Hamburger.svelte';
  import HamburgerModal from '../components/components/HamburgerModal.svelte';
  import MobileMenubarModal from '../components/components/MobileMenubarModal.svelte';

  import { onMount } from 'svelte';

  let y;
  let width;
  let height;
  let curSection = 0;
  let mounted = false;
  let maxMobileWidth = 500;
  let hamburgerOpen = false;
  let hamburgerModal;
  let mobileSidebarOpen = false;
  let mobileSidebarModal;

  $: curSection = getCurrentSection(y);

	onMount(async () => {
    mounted = true;
	});

  let sections = [
    {component: Home, name:'Home', excludeFromMenubar: false},
    {component: Overview, name:'Overview', excludeFromMenubar: false},
    {component: Specifications, name:'Specs', excludeFromMenubar: false},
		{component: BuildBlog, name: 'Build Blog', excludeFromMenubar: false},
    {component: Team, name:'Team', excludeFromMenubar: false},
    /* {component: WorkExperiencePage, name:'Work Experience', excludeFromMenubar: false}, */
    /* {component: SkillsPage, name:'Skills', excludeFromMenubar: false}, */
    /* {component: Portfolio, name:'Portfolio', excludeFromMenubar: false}, */
    /* {component: ResumePage, name:'Resume', excludeFromMenubar: false}, */
    /* {component: Contact, name:'Contact', excludeFromMenubar: false}, */
    {component: BackToTop, excludeFromMenubar: true}
  ];

  function move(event){
    /* console.log('move-app'); */
    /* console.log(event); */
    let n=event.detail.args.n;
		console.log(n);
    let y_temp=0;
    console.log(sections);
    for(let i=0; i<n; i++){
      console.log(`sections[i]: ${sections[i]}`);
      y_temp += sections[i].height;
    }
    y = y_temp;
  }
  
  $: scrolledFarEnoughToDisplayHamburger = y>250;

  const getCurrentSection = (y) => {
    let y_temp = y;
    for (let n=0;n<sections.length; n++){
      let i=sections[n];
      if (y_temp < i.height - 40){
        return n;
      }
      else{
        y_temp -= i.height;
      }
    } 
  }

  const getColor = (section, n) =>{
    /* console.log('hi'); */
    return n % 2 ? '#202020' : '#161a28';
  }
</script>

<style>
  :global(body){
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    min-width: 450px;
  }
  :global(*){
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  :global(html){
    scroll-behavior: smooth;
  }

  /* :global(main){ */
    /* display: flex; */
    /* flex-flow: column nowrap; */
    /* background-color: #FFFFFF; */
    /* margin: 0px; */
    /* padding: 0px; */
  /* } */
</style>
<!--  <svelte:head>
<link href="//db.onlinewebfonts.com/c/69dbc1186412d7831b88d8a78a360360?family=DIN+Condensed+Web" rel="stylesheet" type="text/css"/>
<link href="//db.onlinewebfonts.com/c/84d8d4c49f66a6a5abe1e0608ba764a2?family=Source+Sans+Pro" rel="stylesheet" type="text/css"/>
<link href="//db.onlinewebfonts.com/c/36c361ac34f216ed98000d61fa8ac996?family=Futura+PT+Web+Light" rel="stylesheet" type="text/css"/>
<link href="//db.onlinewebfonts.com/c/6e390d15863032277a741e08a6b18ce2?family=Futura+Std+Medium" rel="stylesheet" type="text/css"/>
</svelte:head>  -->
<title>Pinguins</title>

<svelte:window bind:scrollY={y} bind:outerWidth={width} bind:outerHeight={height}/>

{#if mounted}
  {#if width > maxMobileWidth}
    <Menubar floaty={false} {sections} {curSection} on:move={move}/>

    {#if curSection>0}
    <Menubar floaty={true} {sections} {curSection} on:move={move}/>
    {/if}
  {:else}
    {#if scrolledFarEnoughToDisplayHamburger}
      <div style='width:100%; height: 80px;'>
      </div>
    {/if}
    <Menubar mobile={true} bind:mobileSidebarOpen {y} {sections} {curSection} on:move={move}/>
      <!-- <MobileMenubarModal on:close="{() => mobileSidebarOpen = false}" bind:this={mobileSidebarModal}> -->
      <!-- <Menubar {y} {sections} {curSection} bind:mobileSidebarOpen mobile={true}/> -->
      <!-- </MobileMenubarModal> -->
      <!-- <Hamburger bind:open={mobileSidebarOpen}/> -->
      <!-- <div style='position:fixed; left:25px; top:25px; z-index: 999; background-color: #081012; padding: 2px 10px;'> -->
      <!-- blah -->
      <!-- <Hamburger bind:open={mobileSidebarOpen}/> -->
      <!-- >{#if mobileSidebarOpen} -->
      <!-- >{/if} -->
      <!-- </div> -->
      <!-- >{:else} -->
    <!-- <Hamburger fixed={true} bind:open={mobileSidebarOpen} modal={hamburgerModal}/> -->
    <!-- {/if} -->
  {/if}
{/if}

  {#each sections as section, n}
    <svelte:component this={section.component} bind:height={section.height} bind:width={width} bg_color={getColor(section, n)} on:move={move} mobile={width<=maxMobileWidth}/>
  {/each}
  
