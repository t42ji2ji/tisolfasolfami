<template lang="pug">
  .box {{text.message}}
    svg(width='658px' height='182px' viewbox='0 0 658 182' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink')
      // Generator: Sketch 61.2 (89653) - https://sketch.com
      title piano
      desc Created with Sketch.
      g#Page-1(stroke='none' stroke-width='1' fill='none' fill-rule='evenodd')
        g#u(transform='translate(-102.000000, -163.000000)')
          g#piano(transform='translate(102.000000, 163.000000)')
            rect#1(stroke='#000000' stroke-width='4' fill='#FFFFFF' x='2' y='2' width='43' height='178' rx='4')
            rect#2(stroke='#000000' stroke-width='4' fill='#FFFFFF' x='49' y='2' width='43' height='178' rx='4')
            rect#3(stroke='#000000' stroke-width='4' fill='#FFFFFF' x='96' y='2' width='43' height='178' rx='4')
            rect#4(stroke='#000000' stroke-width='4' fill='#FFFFFF' x='143' y='2' width='43' height='178' rx='4')
            rect#5(stroke='#000000' stroke-width='4' fill='#FFFFFF' x='190' y='2' width='43' height='178' rx='4')
            rect#6(stroke='#000000' stroke-width='4' fill='#FFFFFF' x='237' y='2' width='43' height='178' rx='4')
            rect#7(stroke='#000000' stroke-width='4' fill='#FFFFFF' x='284' y='2' width='43' height='178' rx='4')
            rect#8(stroke='#000000' stroke-width='4' fill='#FFFFFF' x='331' y='2' width='43' height='178' rx='4')
            rect#9(stroke='#000000' stroke-width='4' fill='#FFFFFF' x='378' y='2' width='43' height='178' rx='4')
            rect#10(stroke='#000000' stroke-width='4' fill='#FFFFFF' x='425' y='2' width='43' height='178' rx='4')
            rect#11(stroke='#000000' stroke-width='4' fill='#FFFFFF' x='472' y='2' width='43' height='178' rx='4')
            rect#12(stroke='#000000' stroke-width='4' fill='#FFFFFF' x='519' y='2' width='43' height='178' rx='4')
            rect#13(stroke='#000000' stroke-width='4' fill='#FFFFFF' x='566' y='2' width='43' height='178' rx='4')
            rect#14(stroke='#000000' stroke-width='4' fill='#FFFFFF' x='613' y='2' width='43' height='178' rx='4')
            rect(id='1#' fill='#000000' x='30' y='0' width='35' height='102' rx='4')
            rect(id='2#' fill='#000000' x='77' y='0' width='35' height='102' rx='4')
            rect(id='4#' fill='#000000' x='171' y='0' width='35' height='102' rx='4')
            rect(id='5#' fill='#000000' x='218' y='0' width='35' height='102' rx='4')
            rect(id='6#' fill='#000000' x='265' y='0' width='35' height='102' rx='4')
            rect(id='8#' fill='#000000' x='359' y='0' width='35' height='102' rx='4')
            rect(id='9#' fill='#000000' x='406' y='0' width='35' height='102' rx='4')
            rect(id='11#' fill='#000000' x='500' y='0' width='35' height='102' rx='4')
            rect(id='12#' fill='#000000' x='547' y='0' width='35' height='102' rx='4')
            rect(id='13#' fill='#000000' x='594' y='0' width='35' height='102' rx='4')


</template>

<script>
import Tone from "tone";
import * as dat from "dat.gui";

export default {
  name: "piano",
  data() {
    return {
      keyController: "",
      text: {
        message: 0,
      },
    };
  },
  mounted() {
    this.keyController = new Tone.Synth({
      oscillator: {
        type: "fmsquare",
        modulationFrequency: 0.2,
      },
      envelope: {
        attack: this.text.message,
        decay: this.text.message,
        sustain: 0.2,
        release: 0.9,
      },
    }).toMaster();
    this.register_key();
    var gui = new dat.GUI();
    gui.add(this.text, "message");
  },
  methods: {
    register_key() {
      var vm = this;
      let keys = document.querySelectorAll("rect");
      keys.forEach((value) => {
        value.addEventListener("mousedown", (t) => {
          console.log(vm.pianoConvert(t.target.id));
          vm.keyController.triggerAttack(vm.pianoConvert(t.target.id));
        });
        value.addEventListener("mouseup", (t) => {
          console.log(vm.pianoConvert(t.target.id));
          vm.keyController.triggerRelease();
        });
      });

      document.addEventListener("keyup", (e) => {
        let key = e.key.toUpperCase();
        if (key === "A") {
          vm.keyController.triggerRelease();
        } else if (key === "S") {
          vm.keyController.triggerRelease();
        } else if (key === "D") {
          vm.keyController.triggerRelease();
        } else if (key === "F") {
          vm.keyController.triggerRelease();
        } else if (key === "G") {
          vm.keyController.triggerRelease();
        } else if (key === "H") {
          vm.keyController.triggerRelease();
        } else if (key === "J") {
          vm.keyController.triggerRelease();
        } else if (key === "K") {
          vm.keyController.triggerRelease();
        } else if (key === "L") {
          vm.keyController.triggerRelease();
        } else if (key === ":") {
          vm.keyController.triggerRelease();
        } else if (key === '"') {
          vm.keyController.triggerRelease();
        } else if (key === "S") {
          vm.keyController.triggerRelease();
        }
      });
      document.addEventListener("keydown", (e) => {
        let key = e.key.toUpperCase();
        if (key === "A") {
          vm.keyController.triggerAttack(vm.pianoConvert("1"));
        } else if (key === "S") {
          vm.keyController.triggerAttack(vm.pianoConvert("2"));
        } else if (key === "D") {
          vm.keyController.triggerAttack(vm.pianoConvert("3"));
        } else if (key === "F") {
          vm.keyController.triggerAttack(vm.pianoConvert("4"));
        } else if (key === "G") {
          vm.keyController.triggerAttack(vm.pianoConvert("5"));
        } else if (key === "H") {
          vm.keyController.triggerAttack(vm.pianoConvert("6"));
        } else if (key === "J") {
          vm.keyController.triggerAttack(vm.pianoConvert("7"));
        } else if (key === "K") {
          vm.keyController.triggerAttack(vm.pianoConvert("8"));
        } else if (key === "L") {
          vm.keyController.triggerAttack(vm.pianoConvert("9"));
        } else if (key === ":") {
          vm.keyController.triggerAttack(vm.pianoConvert("10"));
        } else if (key === '"') {
          vm.keyController.triggerAttack(vm.pianoConvert("11"));
        } else if (key === "S") {
          vm.keyController.triggerAttack(vm.pianoConvert("12"));
        }
      });
    },
    pianoConvert(t) {
      let temp = t.split("#");
      console.log(temp);

      let sharp = "";
      if (temp[1] != undefined) {
        sharp = "#";
      }

      let pitch = 2 + Math.floor(temp[0] / 8);

      let mark = String.fromCharCode(
        66 + parseInt(temp[0] % 7 == 0 ? 7 : temp[0] % 7)
      );
      if (mark == "H") {
        mark = "A";
      } else if (mark == "I") {
        mark = "B";
      }

      return mark + sharp + pitch;
    },
  },
};
</script>

<style lang="scss" scoped>
.box {
  height: 100%;
}
svg {
  border: 4px solid black;
  background: #000;
  border-radius: 5px;
  height: 100%;
}
rect:hover {
  fill: rgb(255, 189, 83);
}
</style>
