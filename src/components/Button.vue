<template>
  <button id="btn" :class="btnType">
    <span>Default</span>
  </button>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";

@Options({
  props: {
    variant: {
      default: null,
      type: String,
    },
    hasShadow: {
      default: true,
      type: Boolean,
    },
    isEnabled: {
      default: true,
      type: Boolean,
    },
    color: {
      default: null,
      type: String,
    },
    startIcon: "",
    endIcon: "",
    size: "",
  },
  methods: {
    btnVariant(): string {
      if (this.variant == "text") return "btn-text ";
      if (this.variant == "outline") return "btn-outline ";

      return "btn-default ";
    },
    btnColor(): string {
      if (this.color != null) return `btn-${this.color} `;

      return " ";
    },
    btnHasShadow(): string {
      if (this.hasShadow && this.variant != "text") return "btn-shadow ";

      return " ";
    },
  },
  computed: {
    btnType() {
      let classes = "";

      classes += this.btnColor();

      classes += this.btnVariant();

      classes += this.btnHasShadow();

      return classes;
    },
  },
})
export default class Button extends Vue {}
</script>

<style scoped>
#btn {
  padding: 7px 15px;
  border-radius: 5px;
  font-size: 1rem;
  z-index: 1;
  transition: background-color 0.5s;
}
span {
  z-index: 2;
}
.btn-shadow {
  box-shadow: 0 2px 3px;
}

/* */
.btn-default {
  color: black;
  background-color: rgba(128, 128, 128, 0.6);
  border: 0;
}
.btn-default:hover {
  background-color: rgba(128, 128, 128, 1);
}

/* */
.btn-primary {
  color: white;
  background-color: rgba(127, 127, 255, 0.6);
  border: 0;
}
.btn-primary:hover {
  background-color: rgba(127, 127, 255, 1);
}

/* */
.btn-secondary {
  color: white;
  background-color: rgba(64, 64, 64, 0.6);
  border: 0;
}
.btn-secondary:hover {
  background-color: rgba(64, 64, 64, 1);
}

/* */
.btn-danger {
  color: white;
  background-color: rgba(255, 0, 0, 1);
  border: 0;
}
.btn-danger:hover {
  background-color: rgba(142, 0, 0, 1);
}

/* */
.btn-outline {
  color: blue;
  background-color: rgba(127, 127, 255, 0);
  border: 1px solid black;
  border-color: blue;
}
.btn-outline:hover {
  background-color: rgba(127, 127, 255, 0.2);
}

/* */
.btn-text {
  color: blue;
  border: 0;
  background-color: rgba(0, 0, 0, 0);
}
.btn-text:hover {
  background-color: rgba(127, 127, 255, 0.2);
}
</style>
