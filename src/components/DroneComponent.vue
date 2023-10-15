<template>
    <div id="banner" @mousemove="moveDrone">
        <div id="drone-box">
            <img src="https://i.postimg.cc/XJHDYkJZ/drone.png" class="drone-pic">
            <img src="https://i.postimg.cc/PJCVpvpS/drone-left.png" class="left-pic">
            <img src="https://i.postimg.cc/j2Bgzqyt/drone-right.png" class="right-pic">
        </div>
    </div>
</template>

<script>
export default {
    name: 'DroneComponent',
    methods: {
        moveDrone(event) {
            const moveX = (event.pageX * -1/2) + 300;
            const moveY = (event.pageY * -1/3) + 120;
            const droneBox = document.getElementById('drone-box');
            // const maxX = window.innerWidth - droneBox.offsetWidth + 100;
            // const maxY = window.innerHeight - droneBox.offsetHeight + 100;
            // const x = Math.min(Math.max(moveX, 0), maxX);
            // const y = Math.min(Math.max(moveY, 0), maxY);
            droneBox.style.transform = `translate3d(${moveX}px, ${moveY}px, 0)`;
        }
    }
}
</script>

<style>
* {
    margin: 0;
    padding: 0;
}

#banner {
    width: 100%;
    height: 100vh;
    position: absolute;
    background-position: center;
    background-size: cover;
}

#drone-box {
    margin: 150px auto;
    transition: 2s;
    width: 200px;
    position: relative;
    transition: 2s;
}

.drone-pic {
    width: 100%;
}

.left-pic {
    width: 80px;
    top: 0;
    left: -11px;
    position: absolute;
    animation: rotation .2s linear infinite;
}

.right-pic {
    width: 80px;
    top: 0;
    right: -11px;
    position: absolute;
    animation: rotation .2s linear infinite;
}

@keyframes rotation {
    100% {
        transform: rotateY(360deg);
    }
}

@media  screen and (max-width: 768px) {
    
    #drone-box {
        display: none;
    }
    
}
</style>
