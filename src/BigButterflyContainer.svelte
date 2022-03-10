<script>
  import { afterUpdate } from 'svelte';
<<<<<<< HEAD
  import { select, selectAll, scaleOrdinal, mode } from "d3";
  import {uniqueArray, findRegionColor, getQuestionWithCountryName, createPossibleQuestions, createUnnecessaryQuestions, clickContainer, highlightPath} from "./helper.js"
  import Documentation from './Documentation.svelte'
  import regions from './regions.js'
  import { each } from 'svelte/internal';
=======
  import { select, selectAll } from "d3";
  import {uniqueArray, findRegionColor} from "./helper.js"
  import Documentation from './Documentation.svelte'
  import regions from './regions.js'
import { each } from 'svelte/internal';
>>>>>>> 9b63aa831e91eae383934752794fd60b82b23c37

  export let selectedRegion;
  export let selectedCountry;
  export let definitions;
  export let warnings;
  export let questions;
  export let acqMode;
  export let questionToMode;
  export let butterflies;
<<<<<<< HEAD
  export let modeA06a;

  let w, trueMode;
=======

  let w;
>>>>>>> 9b63aa831e91eae383934752794fd60b82b23c37
  let selectedColor = findRegionColor(selectedRegion)
  let availableMode = // paths available based on the butterflyPath.svg
    ["A06f", "A07", "A01a", "A02a", "A02b", "A09",
    "A14", "A10", "A08", "A11", "A12a", "A12b", "A13", "A21", "A06e",
    "A06d", "A06a", "A06b", "A06c", "A25", "A26", "A24", "A23", "A22",
    "A19", "A18", "A16"] 

<<<<<<< HEAD
  let allQuestions = uniqueArray(questionToMode, "question");

  $: h = w * 74 / 91;

  $: if (selectedCountry !== "") {

    let acqModeFiltered = acqMode.filter(d => d.country == selectedCountry);
    let possibleModes = uniqueArray(acqModeFiltered, "mode_id");

    let possibleQuestions = createPossibleQuestions(possibleModes, questionToMode);
    let unnecessaryQuestions = createUnnecessaryQuestions(allQuestions, possibleQuestions);


    // console.log(modeA06a);
    let a06aValue = modeA06a.filter(d => d.country == selectedCountry)[0].values;

    let clicks = new clickContainer(possibleQuestions, possibleModes, a06aValue);
    // console.log(clicks);

    // console.log("possibleModes", possibleModes);
    // console.log("allQuestions", allQuestions);
    // console.log("possibleQuestions", possibleQuestions);
    // console.log("unnecessaryQuestions", unnecessaryQuestions);

    // filter and see what modes are available
    let filteredAvailableMode = availableMode.filter(m => possibleModes.includes(m));
    // console.log("filteredAvailableMode", filteredAvailableMode);
    // console.log(filteredAvailableMode);
=======
  $: h = w * 74 / 91;

  $: if (selectedCountry !== "") {
    // filter and see what modes are available
    let selectedAcqMode = acqMode.filter(d => d.country == selectedCountry)
    selectedAcqMode = uniqueArray(selectedAcqMode, "mode_id")
    let filteredAvailableMode = availableMode.filter(m => selectedAcqMode.includes(m));
    let unnecessaryQuestion = questionToMode.filter(q => !selectedAcqMode.includes(q.mode_id))
    unnecessaryQuestion = uniqueArray(unnecessaryQuestion, "question")
    let necessaryQuestion = questionToMode.filter(q => selectedAcqMode.includes(q.mode_id))
    necessaryQuestion = uniqueArray(necessaryQuestion, "question")
    unnecessaryQuestion = unnecessaryQuestion.filter(q => necessaryQuestion.indexOf(q) == -1);
>>>>>>> 9b63aa831e91eae383934752794fd60b82b23c37

    afterUpdate(() => {
      // set default colors of the big butterfly
      let butterflySel = select("#butterfly-path")
<<<<<<< HEAD

      butterflySel
        .select("#butterfly__wings")
        .attr("fill", selectedColor.light);

      butterflySel
        .select("#butterfly__head")
        .attr("fill", "#977B67");

      let butterflyPathsG = butterflySel
        .select("#butterfly__paths");

=======
      butterflySel
        .select("#butterfly__wings")
        .attr("fill", selectedColor.light)
      butterflySel
        .select("#butterfly__head")
        .attr("fill", "#977B67")
      let butterflyPathsG = butterflySel
        .select("#butterfly__paths")
>>>>>>> 9b63aa831e91eae383934752794fd60b82b23c37
      butterflyPathsG
        .selectAll("path")
        .attr("fill", "none")
        .attr("stroke", "#ffffff")
        .attr("stroke-width", 5)
        .attr("data-available", "true")
<<<<<<< HEAD
        .attr("data-active", "false");

=======
        .attr("data-active", "false")
>>>>>>> 9b63aa831e91eae383934752794fd60b82b23c37
      butterflyPathsG
        .selectAll("path")
        .each(function() {
          let id = select(this).attr("id")
          if (!filteredAvailableMode.includes(id)) {
            select(this)
              .attr("data-available", "false")
              .style("opacity", 0.1);
          }
<<<<<<< HEAD
        });

      let butterflyCirclesG = butterflySel
        .select("#butterfly__circles");

=======
        })
      let butterflyCirclesG = butterflySel
        .select("#butterfly__circles")
>>>>>>> 9b63aa831e91eae383934752794fd60b82b23c37
      butterflyCirclesG
        .selectAll("circle")
        .attr("fill", "white")
        .attr("stroke", "#000000")
        .attr("stroke-width", 4.5)
        .attr("data-available", "true")
        .attr("data-answer", "no")
<<<<<<< HEAD
        .style("cursor", "pointer");

=======
        .style("cursor", "pointer")
>>>>>>> 9b63aa831e91eae383934752794fd60b82b23c37
      butterflyCirclesG
        .selectAll("circle")
        .each(function() {
          let id = select(this).attr("id")
<<<<<<< HEAD
          if(unnecessaryQuestions.includes(id)) {
            select(this).attr("data-available", "false").style("opacity", 0.1)
          }
        });
=======
          if(unnecessaryQuestion.includes(id)) {
            select(this).attr("data-available", "false").style("opacity", 0.1)
          }
        })
>>>>>>> 9b63aa831e91eae383934752794fd60b82b23c37

      // populate questions
      if (!butterflyCirclesG.empty()) {
        selectAll(".butterfly__questions__question").remove();
        questions.forEach(q => {
          let id = q.question_id;
<<<<<<< HEAD
          if (!unnecessaryQuestions.includes(id)) {
=======
          if (!unnecessaryQuestion.includes(id)) {
>>>>>>> 9b63aa831e91eae383934752794fd60b82b23c37
            let text = q.question;
            let side = {
              h: q.h_side,
              v: q.v_side
            };
<<<<<<< HEAD

=======
>>>>>>> 9b63aa831e91eae383934752794fd60b82b23c37
            let node = butterflyCirclesG.select(`#${id}`);
            if (q.visibility == "hidden") {
              node
                .attr("stroke", "lightgray")
                .style("cursor", "default")
            }
<<<<<<< HEAD

=======
>>>>>>> 9b63aa831e91eae383934752794fd60b82b23c37
            let position = [+node.attr("cx"), +node.attr("cy")]

            select("#butterfly__questions")
              .append("foreignObject")
              .html(getQuestionWithCountryName(selectedCountry, text))
              .classed("butterfly__questions__question", true)
              .attr("data-question-id", id)
              .attr("x", side.h == "left" ? position[0] - 170 - 20 : position[0] + 20)
              .attr("y", side.v == "upper" ? position[1] - 30 : side.v == "middle" ? position[1] - 15 : position[1] + 10)
              .attr("width", 170)
              .attr("height", 170)
<<<<<<< HEAD
              // .style("opacity", q.visibility == "hidden" ? 0 : 1)
=======
              .style("opacity", q.visibility == "hidden" ? 0 : 1)
>>>>>>> 9b63aa831e91eae383934752794fd60b82b23c37
              .style("text-shadow", "-2px -2px 0 rgba(255, 255, 255, 0.7), 2px -2px 0 rgba(255, 255, 255, 0.7), -2px 2px 0 rgba(255, 255, 255, 0.7), 2px 2px 0 rgba(255, 255, 255, 0.7)")          
              .style("font-size", "0.8rem")
              .style("text-align", side.h == 'left' ? "right" : "left")
              .style("line-height", 1)
              .style("transition", "all 0.2s ease")     
            }
        })
      }

      // circles on click event
      butterflyCirclesG.selectAll("circle").on("mouseover", function() {
<<<<<<< HEAD
        let id = select(this).attr("id");
        if (!unnecessaryQuestions.includes(id)) {
          select(this)
          .transition(200)
          .attr("r", 10)
          .attr("stroke-width", 7.8)
        }
=======
        select(this).transition(200).attr("r", 10).attr("stroke-width", 7.8)
        let id = select(this).attr("id")
>>>>>>> 9b63aa831e91eae383934752794fd60b82b23c37
        select(`foreignObject[data-question-id=${id}]`).style("font-weight", "bold")
      })

      butterflyCirclesG.selectAll("circle").on("mouseleave", function() {
        select(this).transition(200).attr("r", 5.8).attr("stroke-width", 4.5)
        let id = select(this).attr("id")
        select(`foreignObject[data-question-id=${id}]`).style("font-weight", "normal")
      })

      butterflyCirclesG.selectAll("circle").on("click", function() {
<<<<<<< HEAD
        let id = select(this).property("id");
        let status = true;
        clicks.updateClick(id, status);
        if (id === "Q23") {
          status = "blah";
        }
        // if (status) {
          highlightPath(clicks, butterflyPathsG);
        // }
        
        if (status) {
          select(this).attr("data-answer", "yes").attr("fill", "black")
        } 
        // else {
        //   status = true;
        //   select(this).attr("data-answer", "no").attr("fill", "white")
        // }
        
        // *NOTE* for now, to set up the Documentation.svelte, setting this variable to a mode that's related to the question, not the actual mode that turns to "true". needs updates here.
        // trueMode = [...clicks.modes].filter(m => m[1] == true)[0][0]
      })
    })
=======
        let answerStatus = select(this).attr("data-answer")
        if (answerStatus == "no") {
          select(this).attr("data-answer", "yes").attr("fill", "black")
        } else {
          select(this).attr("data-answer", "no").attr("fill", "white")
        }
        console.log(select(this))
      })
    })

      acqMode = acqMode.filter(function(d) {
        return d.country === selectedCountry;
      });

      let showDef = uniqueArray(acqMode, "definition")[0];
      let showWarn = uniqueArray(acqMode, "restriction_warning")[0];

      if (showDef !== "NA") {
        definitions = definitions.filter(function(d) {
          d.definition_id === showDef;
        });

        // let def = definitions.definition[0];
      }

      if (showWarn !== "NA") {
        warnings = warnings.filter(function(d) {
          d.restriction_warning === showWarn;
        });
        // let warn = warnings.message[0];
      }

    // if (selectedRegion !== "") {
    //   let color = colorScale(selectedRegion);
    // }
  }

  function getQuestionWithCountryName(selectedCountry, question) {
    let words = question.split(/[\s}]+/)
    let index = words.findIndex(w => w == "{cntry")
    if (index !== -1) {
      words[index] = selectedCountry
    }
    words = words.join(" ").replace(/\s+(\W)/g, "$1")
    return words
>>>>>>> 9b63aa831e91eae383934752794fd60b82b23c37
  }

</script>

<section id="big-butterfly__container" bind:clientWidth="{w}">
  {#if selectedCountry !== ""}
<<<<<<< HEAD
    <h1 class="title">
      Paths to acquire citizenship in <span class="country-highlight" style="background-color: {selectedColor.vivid}">{selectedCountry}</span>
    </h1>
    <div class="instructions">
      Click
        <svg width=27 height=18>
=======
    <h1>
      Paths to acquire citizenship in <span class="country-highlight" style="background-color: {selectedColor.vivid}">{selectedCountry}</span>
    </h1>
      Click nodes
        <svg
          width=18
          height=18
        >
>>>>>>> 9b63aa831e91eae383934752794fd60b82b23c37
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
<<<<<<< HEAD
      to answer questions. Paths will light up if there is a country-specific law that allows you to acquire citizenship with your condition.</div>
=======
      to answer questions, see if there's a law that allows you to aquire citizenship with your condition.
>>>>>>> 9b63aa831e91eae383934752794fd60b82b23c37
    {#if w !== undefined}
      <div id="citizenship-paths" style="height: {h}">
        <div id="butterfly__graphic">
          {@html butterflies[2]}
        </div>
      </div>
<<<<<<< HEAD
      {#if trueMode !== undefined}
        <Documentation selectedCountry={selectedCountry} bind:trueMode={trueMode} acqMode={acqMode} warnings={warnings} definitions={definitions}/>
      {/if}
=======
      <Documentation />
>>>>>>> 9b63aa831e91eae383934752794fd60b82b23c37
    {/if}
  {/if}
</section>

<style>
  #big-butterfly__container {
    margin-top: 7rem;
  }
  .country-highlight {
    color: white;
    padding: 0.3em 0.5em;
    border-radius: 8px;
  }
<<<<<<< HEAD
  .instructions {
    padding: 10px;
    margin: 10px auto;
    max-width: 800px;
=======
  #documentation {
    display: flex;
    flex-direction: row;
  }
  #documentation div {
    background: rgb(211, 211, 211);
    max-height: 75px;
>>>>>>> 9b63aa831e91eae383934752794fd60b82b23c37
  }
</style>