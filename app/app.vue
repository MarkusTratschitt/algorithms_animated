<template lang="pug">
div
    NuxtRouteAnnouncer 
    NuxtLayout
    NuxtPage
</template>


<script lang="ts">

</script>   


<style lang="less">

:rooot {
    font-size: calc(1vw + 1vh + .5vmin);
}


html {
    box-sizing: border-box;
    font: 1rem/1.6 sans-serif;
}


input[type="text"],
input[type="number"],
select,
textarea {
    font-size: 16px;
}


*, 
*::before, 
*::after {
    box-sizing: inherit;
}


.button {
    margin-top: 1em;
    padding: .6em 1.2em;
    background-color: #ACAF50;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s ease;

    &:hover {
        background-color: #45a049;
    }
}
</style>