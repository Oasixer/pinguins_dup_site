<script>
  export let height=undefined;
  
  let src_gif = './images/gps.gif';
  export let bg_color;
  export let mobile;

  let teamElement;
	let members = [{
		"name": "Ahmad Kamal",
		"img": "kaelan.jpg",
		"role": "Algorithms Lead",
		"blurb": "He likes long walks on the beach and has a cute smile"
	},
	{
		"name": "Kat von Friedl",
		"img": "kaelan.jpg",
		"role": "Mechanical Design Lead",
		"blurb": "Beer"
	},
	{
		"name": "Krishn Ray",
		"img": "kaelan.jpg",
		"role": "Electrical Lead",
		"blurb": "Enthusiastic to expose his feet in public"
	},
	{
		"name": "Zachariah Mears",
		"img": "kaelan.jpg",
		"role": "Sensors Lead",
		"blurb": "rocketmannnnnnnnnnnnnnnn"
	},
	{
		"name": "Kaelan Moffett",
		"img": "kaelan.jpg",
		"role": "Software Lead",
		"blurb": "Passionate about all software, excited to get better at C this term. I think most robots are cool once you get to know them."
	},
	]  
  import { onMount } from 'svelte';
  onMount(async => {
    const bar = () => {
      height = teamElement.offsetHeight;
    }
    setTimeout(bar, 10);
  });
</script>

<style>
  div#team{
    width: 100%;
    padding: 70px;
    display: flex;
    flex-flow: column nowrap;
  }
  div#team.mobile{
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
  }
  p.mobile{
    text-align: justify;
    width: 100%;
    font-weight: 400;
    font-family: "Helvetica", serif;
    font-size:18px;
  }
  div.hstack-overflow{
    display: flex;
    flex-flow: row wrap;
		margin-bottom: 50px;
		justify-content: space-between;
  }
  /* div.hstack-overflow.mobile{ */
    /* display: flex; */
    /* flex-flow: row wrap; */
  /* } */
  div.vstack-centeritems.member-card{
    margin: 0 8px;
  }
  div.vstack-centeritems.member-card > *{
    margin: 0;
  }
  div.vstack{
    display: flex;
    flex-flow: column nowrap;
  }
  div.vstack-centeritems{
    display: flex;
    flex-flow: column nowrap;
		align-items: center;
  }
	div.member-card{
		width: 300px;
		max-width: 300px;
	}

	img.rounded {
		object-fit: cover;
		border-radius: 50%;
		height: 200px;
		width: 200px;
		max-width: 200px;
	}
	h3.member-name{
    font-weight: 600;
    font-family: "Helvetica", serif;
    font-size:18px;
		color: white;
	}
	h4.role{
    font-weight: 400;
    font-family: "Helvetica", serif;
    font-size:16px;
		font-style: italic;
		color: #cccccc;
	}

	p.blurb{
		text-align: center;
    font-weight: 400;
    font-family: "Helvetica", serif;
    font-size:15px;
		color: #cccccc;
	}
  /* img.rounded.mobile{ */
    /* width: 100%; */
  /* } */

</style>
<div id='team'
  style="background-color: {bg_color}"
  class:mobile
  bind:this={teamElement}
  bind:offsetHeight={height}>
  <h1 class:mobile>The Team</h1>
	<div class="vstack-centeritems">
		<div class="hstack-overflow" class:mobile>
			{#each members.slice(0,3) as member}
				<div class="vstack-centeritems member-card">
					<img class="rounded" src={"images/members/"+member.img}/>
					<h3 class="member-name">{member.name}</h3>
					<h4 class="role">{member.role}</h4>
					<p class="blurb">{member.blurb}</p>
				</div>
			{/each}
		</div>
		<div class="hstack-overflow">
			{#each members.slice(3,) as member}
				<div class="vstack-centeritems member-card">
					<img class="rounded" src={"images/members/"+member.img}/>
					<h3 class="member-name">{member.name}</h3>
					<h4 class="role">{member.role}</h4>
					<p class="blurb">{member.blurb}</p>
				</div>
			{/each}
		</div>
	</div>
</div>
