<template>
    <div id="loader" class="loader"></div>
</template>

<script setup>

</script>

<style scoped>
.loader {
    background-color: black;
    border: 1px solid rgb(134, 96, 96);
    margin:   auto;
    width: 94%;
    height: 80%;
    position: relative;
    display: block; 

}
/*LOADER*/

.loader:after {
    content: " ";
    display: block;
    border-radius: 50%;
    width: 0;
    height: 0;
    margin: 8px auto;
    box-sizing: border-box;
    border: 132px solid chartreuse;
    border-color: red transparent aquamarine;
    animation: loader 1.2s infinite;
}

@keyframes loader {
    0% {
        transform: rotate(0);
        animation-timing-function: cubic-bezier(0.55, 0.055, 0.675, 0.19);
    }

    50% {
        transform: rotate(900deg);
        animation-timing-function: cubic-bezier(0.215, 0.61, 0.355, 1);
    }

    100% {
        transform: rotate(1800deg);
    }
}
</style>