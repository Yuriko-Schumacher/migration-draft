<script>
  import { format } from "d3"
  
  export let regionData;
  export let countryData;
  export let hoveredCountry;

  let countryValue;

  const formatValue = format(",")
  $: if (hoveredCountry !== "") {
    countryValue = countryData.filter(d => d.country == hoveredCountry);
    countryValue = countryValue[0].value;
  }
  
</script>

<div>
<<<<<<< HEAD
  <p class="user-signifier">
=======
  <p>
>>>>>>> 7e49559adfc3d3313de7f55ed7e08b286d025f66
    Select a country to show various ways you can aquire citizenship.
  </p>
  {#if hoveredCountry !== ""}
    {#if hoveredCountry == "Taiwan" | hoveredCountry == "Kosovo"}
      <p>
        The data is missing about the number of migrants in <span style="text-decoration: underline solid {regionData.color} 5px; text-underline-offset: 2px">{hoveredCountry}</span>.
      </p>
    {:else}
      <p>
        <span style="text-decoration: underline solid {regionData.color} 5px; text-underline-offset: 2px">{hoveredCountry}</span> had a total of <span style="text-decoration: underline solid {regionData.color} 5px; text-underline-offset: 2px">{formatValue(countryValue)}</span> migrants.
      </p>
    {/if}
  {:else}
    <p style="color: white;">
      Hover over the country.
    </p>
  {/if}
</div>

<style>
  p {
    line-height: 1.5;
    margin: 0;
  }
  span {
    font-weight: bold;
  }
  div {
    margin-bottom: 50px;
  }
</style>