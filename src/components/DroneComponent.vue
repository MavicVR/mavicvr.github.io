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
    data() {
      return {
        mouseX: 0,
        mouseY: 0,
        droneX: 0,
        droneY: 0,
        speed: 0.02,
      };
    },
    methods: {
      constrain(x, min, max) {
        if (x < min) return min;
        else if (x > max) return max;
        return x;
      },
      animate() {
        let distX = this.constrain(this.mouseX, 110, window.innerWidth - 130) - this.droneX;
        let distY = this.constrain(this.mouseY, 50, window.innerHeight - 50) - this.droneY;
  
        this.droneX = this.constrain(this.droneX + distX * this.speed, 110, window.innerWidth - 130);
        this.droneY = this.constrain(this.droneY + distY * this.speed, 50, window.innerHeight - 50);
  
        const drone = document.getElementById("drone-box");
        drone.style.left = this.droneX + "px";
        drone.style.top = this.droneY + "px";
  
        requestAnimationFrame(this.animate);
      },
      moveDrone(event) {
        this.mouseX = event.pageX;
        this.mouseY = event.pageY;
      },
    },
    mounted() {
      this.animate();
    },
  };
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
  }
  
  #drone-box {
    width: 200px;
    position: relative;
    transform: translate(-50%, -50%);
  }
  
  .drone-pic {
    width: 100%;
  }
  
  .left-pic {
    width: 80px;
    top: 0;
    left: -11px;
    position: absolute;
    animation: rotation 0.2s linear infinite;
  }
  
  .right-pic {
    width: 80px;
    top: 0;
    right: -11px;
    position: absolute;
    animation: rotation 0.2s linear infinite;
  }
  
  @keyframes rotation {
    100% {
      transform: rotateY(360deg);
    }
  }

  @media screen and (max-width: 768px) {
    #banner {
      display: none;
    }
    
  }
  </style>
  