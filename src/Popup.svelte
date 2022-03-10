<script>
  import {max, min} from "d3"
  import CountryCardContainer from './CountryCardContainer.svelte';
  import BigButterflyContainer from './BigButterflyContainer.svelte';
  import regions from "./regions"
  
  export let selectedRegion;
  export let selectedCountry;
  export let datasets;
  export let butterflies;
<<<<<<< HEAD

  // region data for country cards
  let selectedRegionValue = datasets[0].filter(d => d.properties.SUBREGION == selectedRegion)
  selectedRegionValue = selectedRegionValue[0].properties.VALUE
  let selectedRegionColor = regions.filter(d => d.name == selectedRegion)[0].color
  let selectedRegionData = { value: selectedRegionValue, color: selectedRegionColor }
</script>

<CountryCardContainer bind:selectedRegion={selectedRegion} bind:selectedCountry={selectedCountry} countryData={datasets[1]} regionData={selectedRegionData}/>
<BigButterflyContainer bind:selectedCountry={selectedCountry} bind:selectedRegion={selectedRegion} warnings={datasets[2]} definitions={datasets[3]} questions={datasets[4]} acqMode={datasets[5]} questionToMode={datasets[7]} butterflies={butterflies} modeA06a={datasets[8]}/>
=======
</script>

<CountryCardContainer bind:selectedRegion={selectedRegion} bind:selectedCountry={selectedCountry} data={datasets[0]}/>
<BigButterflyContainer bind:selectedCountry={selectedCountry} bind:selectedRegion={selectedRegion} warnings={datasets[1]} definitions={datasets[2]} questions={datasets[3]} acqMode={datasets[4]} questionToMode={datasets[5]} butterflies={butterflies}/>
>>>>>>> 9b63aa831e91eae383934752794fd60b82b23c37
