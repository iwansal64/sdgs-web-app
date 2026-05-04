<script>
      import { splitText } from "animejs/text";
      import { animate, stagger } from "animejs";

      Array.from(document.getElementsByClassName("animejs-homepage-title")).forEach((element) => {
            const { chars } = splitText(element, {
                  chars: { wrap: "clip" },
            });

            animate(chars, {
                  color: [{ to: ["#000"] }, { to: "#fff" }],
                  autoplay: true,
                  ease: "out(3)",
                  delay: stagger(100),
            });
      })

</script>
