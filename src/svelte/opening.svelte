<script lang="ts">
      import { animate } from "animejs";

      $effect(() => {
            const animejsOpening = document.getElementsByClassName("animejs-class-opening")[0];

            if (animejsOpening) {
                  animate(animejsOpening, {
                        "--radial-size": ["0", "100%"],
                        "--radial-blur-scale": ["0", "2%"],
                        delay: 1000,
                        duration: 4000,
                        ease: "outQuad",
                        autoplay: false,
                        onComplete: () => {
                              animejsOpening.parentElement?.removeChild(animejsOpening);
                        },
                  }).play();
            }
      });
</script>

<div class="animejs-class-opening fixed top-0 left-0 w-screen h-screen z-100"></div>

<style>
      @property --radial-size {
            inherits: false;
            initial-value: 0%;
      }

      @property --radial-blur-scale {
            inherits: false;
            initial-value: 0%;
      }

      .animejs-class-opening {
            /* background-image: radial-gradient(circle var(--radial-size), #000f, #fff0); */
            /* background: radial-gradient(circle 50% at 50% 50%, #000f, #fff0); */
            background-image: radial-gradient(circle, transparent var(--radial-size), white calc(var(--radial-size) + (var(--radial-size) + var(--radial-blur-scale))));
      }
</style>
