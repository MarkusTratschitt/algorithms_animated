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

</script>

<style>

</style>