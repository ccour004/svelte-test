<script>
	let buffer = "";
	let numbers = [
		"0","1","2","3","4","5","6","7","8","9"
	]
	let operators = [
		"+","-","/","*"
	]

	function evaluate(){
		let sum = 0
		if(buffer.includes("+"))
			buffer.split("+").forEach((item)=>{
				sum += parseInt(item)
			})
		if(buffer.includes("-"))
			buffer.split("-").forEach((item)=>{
				sum -= parseInt(item)
			})
		buffer = sum
	}
</script>

<h2>({buffer})</h2>

{#each numbers as number}
	<button on:click={()=>{if(!(number === "0" && buffer === "")) buffer += number}}>{number}</button>
{/each}

{#each operators as operator}
	<button on:click={()=>{buffer += operator}}>{operator}</button>
{/each}

<button on:click={()=>{evaluate()}}>=</button>
<button on:click={()=>{buffer = ""}}>CLEAR</button>

<style>
	button {
		font-family: inherit;
		font-size: inherit;
		padding: 1em 2em;
		color: #ff3e00;
		background-color: rgba(255, 62, 0, 0.1);
		border-radius: 2em;
		border: 2px solid rgba(255, 62, 0, 0);
		outline: none;
		width: 200px;
		font-variant-numeric: tabular-nums;
	}

	button:focus {
		border: 2px solid #ff3e00;
	}

	button:active {
		background-color: rgba(255, 62, 0, 0.2);
	}
</style>