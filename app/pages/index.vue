<template lang="pug">
.container
    h1 Algorithmen erklärt und animiert
    |
    br 
    |
    h2 Der Run - Length - Algorithmus
    |
    .input-box
        p Input:
            span#input-string aaabbbcccd
        p Output:
            span#output-string
        .steps
            p#step-description Initialsieere...
        button(@click="startRLE") Starte Animation
</template>


<script lang="ts">
export default defineNuxtComponent({
  setup() {
    const inputString = "aaabbccccd";
    const outputString = ref("");
    const stepDescription = ref("Initialisiere...");
    const steps = ref<any[]>([]); // Schritte für die Animation
    let encoded = "";
    let i = 0;

    function RLE_encode_step(input: string) {
      while (i < input.length) {
        let count = 1;

        // Zähle die Anzahl aufeinanderfolgender gleicher Zeichen
        while (i + 1 < input.length && input[i] === input[i + 1]) {
          count++;
          i++;
        }

        // Füge das Zeichen und die Anzahl dem Ergebnis hinzu
        encoded += input[i] + count;
        i++;

        // Aktuellen Schritt speichern
        steps.value.push({
          currentChar: input[i - 1],
          count: count,
          encodedSoFar: encoded
        });
      }
    }

    // Starte die Animation
    const startRLE = () => {
      // Initialisiere Variablen für neue Animation
      encoded = "";
      i = 0;
      outputString.value = "";
      stepDescription.value = "Starte die Animation...";
      steps.value = [];
      
      RLE_encode_step(inputString);
      animateSteps();
    };

    // Schrittweise Animation
    const animateSteps = () => {
      let stepIndex = 0;

      const interval = setInterval(() => {
        if (stepIndex < steps.value.length) {
          const step = steps.value[stepIndex];
          outputString.value = step.encodedSoFar;
          stepDescription.value = `Verarbeite: '${step.currentChar}' x ${step.count}`;
          stepIndex++;
        } else {
          stepDescription.value = "Fertig!";
          clearInterval(interval);
        }
      }, 1000); // 1 Sekunde pro Schritt
    };

    return {
      inputString,
      outputString,
      stepDescription,
      startRLE
    };
  }
});
</script>


<style lang="less" scoped>

.container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    font-family: Arial, Helvetica, sans-serif;
    background-color: #f9f9f9;
}

.input-box, .output-box {
    margin: 1em;
    padding: 1em;
    background-color: #4CAF50;
    color: white;
    border-radius: 5px;
    width: 300px;
    text-align: center;
}

.steps {
    margin-top: 1em;
    font-size: 1.2em;
}

</style>