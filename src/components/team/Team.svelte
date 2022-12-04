<script>
  export let height=undefined;
  export let bg_color;
  export let mobile;

  let teamElement;
	let members = [{
		"name": "Ahmad Kamal",
		"img": "ahmad_cropped.png",
		"role": "Algorithms Lead",
		"blurb": "Robotics student that's enthusiastic about underwater robotic applications and automation. Experienced with sonar applications and excited to go for a swim."
	},
	{
		"name": "Kat von Friedl",
		"img": "kat.png",
		"role": "Mechanical Design Lead",
		"blurb": "Mechanically leaning mechatronics student who is equally as fascinated with underwater as she is with CAD. Unfortunately fish can't do mech design yet so she's the best next alternative."
	},
	{
		"name": "Krishn Ray",
		"img": "krishn_cropped.png",
		"role": "Electrical Lead",
		"blurb": "Mechatronics student very interested in robotics, especially in rugged terrain. Experienced with mechanical and electrical design. Excited to submerge devices into pools."
	},
	{
		"name": "Zachariah Mears",
		"img": "zach_cropped.jpg",
		"role": "Sensors Lead",
		"blurb": "Very experienced with electromechanical integration and design. Tolerates reading many long complicated datasheets to find the best possible solution. Excited to annoy all the other team members with high pitch acoustic tones."
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
    height: 100%;
    /* background-color: #0B1237; */
    background-color: #031767;
    display: flex;
    flex-flow: column nowrap;
    /* padding: 40px 15px 40px 15px; */
    padding: 70px;
  }
  div#team.mobile{
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
    margin-left: auto;
    margin-right: auto;
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
  .card{
		/* background-color: #f7f5f4; */
		/* background-color: #0B1237; */
		padding: 15px;
		border-radius: 6px;
    box-shadow: 0 16px 38px -12px rgb(0 0 0 / 56%), 0 4px 25px 0px rgb(0 0 0 / 12%), 0 8px 10px -5px rgb(0 0 0 / 20%)
	}
	div.card-dark{
		background-color: #5f5DAB;
		/* background-color: #fefefe; */
		background-color: #0B1237;
    /* background-color: #f7f5f4; */
	}
	div.card-light{
		/* background-color: #fefefe; */
		/* background-color: #0B1237; */
    /* background-color: #f7f5f4; */
		margin-top: 15px;
		background-color: #5f5DAB;
		background-color: #f7f5f4;
	}
  div.vstack-centeritems.member-card{
    margin: 0 25px;
  }
  /* div.vstack-centeritems.member-card > *{ */
    /* margin: 0; */
  /* } */
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
    font-weight: 700;
		font-family: "Roboto Slab" "Times New Roman", serif;
    margin-top: 10px;
    font-size: 20px;
    color: #f7f5f4;
    margin-left: 0;
		margin-bottom: 0;
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
		/* color: #cccccc; */
		margin-top: 16px;
		color: #96BDE6;
    font-weight: 300;
		font-family: "Roboto", "Helvetica", "Arial", sans-serif;
    line-height: 1.25;
    font-size: 16px;
    margin-bottom: 15px;
	}
  /* img.rounded.mobile{ */
    /* width: 100%; */
  /* } */

</style>
<div id='team'
  class:mobile
  bind:this={teamElement}
  bind:offsetHeight={height}>
  <h1 class:mobile>The Team</h1>
	<div class="vstack-centeritems">
		<div class="hstack-overflow" class:mobile>
			{#each members.slice(0,3) as member}
				<div class="vstack-centeritems member-card card card-dark">
					<img class="rounded" src={"images/members/"+member.img}/>
					<h3 class="member-name">{member.name}</h3>
					<h4 class="role">{member.role}</h4>
					<p class="blurb">{member.blurb}</p>
				</div>
			{/each}
		</div>
		<div class="hstack-overflow">
			{#each members.slice(3,) as member}
				<div class="vstack-centeritems member-card card card-dark">
					<img class="rounded" src={"images/members/"+member.img}/>
					<h3 class="member-name">{member.name}</h3>
					<h4 class="role">{member.role}</h4>
          <!-- <div class="card card-light"> -->
						<p class="blurb">{member.blurb}</p>
            <!-- </div> -->
				</div>
			{/each}
		</div>
	</div>
</div>
