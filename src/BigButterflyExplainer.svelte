<script>
  export let isCitizenshipAchieved;
  
</script>

<div class="instructions">
  {#if !isCitizenshipAchieved} 
    <p class="user-signifier">Click buttons
      <svg
        width=18
        height=18
        transform="translate(0, 5)"
      >
        <circle
          cx=9
          cy=9
          r=5
          stroke-width=4
          stroke="black"
          fill="white"
        >
        </circle>
      </svg>
      to answer questions. Paths will light up if there is a country-specific law that allows you to acquire citizenship with your condition.
      <!-- <span class="reset" on:click={handleResetButton}>RESET CONDITIONS</span> -->
    </p>
  {:else}
    <p>
      Congratulations! You are <span>golden!</span> &#127881;
    </p>
  {/if}
</div>

<style>
  .instructions {
    padding: 10px;
    margin: 10px auto;
    max-width: 600px;
    font-size: 18px;
  }
</style>