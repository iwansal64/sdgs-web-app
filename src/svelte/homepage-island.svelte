<script>
      import { splitText } from "animejs/text";
      import { animate, stagger } from "animejs";

      Array.from(document.getElementsByClassName("animejs-homepage-title")).forEach((element) => {
            const { chars } = splitText(element, {
                  chars: { wrap: "clip" },
            });

            chars.forEach(char => {
                  char.style.position = "relative";
                  char.style.left = "-10px";
                  char.style.opacity = "0";
            })
            
            setTimeout(() => {
                  animate(chars, {
                        left: ["-10px", "0px"],
                        opacity: [0, 1],
                        duration: 500,
                        autoplay: true,
                        ease: "out(3)",
                        delay: stagger(50),
                  });
            }, 2500);
      });

      animate("#animejs-id-homepage-subtitle", {
            left: ["-50px", "0"],
            opacity: [0, 1],
            delay: 3500,
            duration: 1000,
            autoplay: true
      });

</script>
