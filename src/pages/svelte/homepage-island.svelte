<script>
      import { splitText } from "animejs/text";
      import { animate, stagger } from "animejs";

      const { chars } = splitText("#animejs-id-homepage-title", {
            chars: { wrap: "clip" },
      });

      animate(chars, {
            color: [{ to: ["#000"] }, { to: "#fff" }],
            autoplay: true,
            ease: "out(3)",
            delay: stagger(100),
      });
</script>
