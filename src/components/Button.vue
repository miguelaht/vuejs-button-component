<template>
  <button :class="btnType" :disabled="!isActive">
    <span v-if="startIcon" :class="iconSize">{{ startIcon }}</span>
    <span>Button</span>
    <span v-if="endIcon" :class="iconSize">{{ endIcon }}</span>
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
    isActive: {
      default: true,
      type: Boolean,
    },
    color: {
      default: null,
      type: String,
    },
    startIcon: {
      default: null,
      type: String,
    },
    endIcon: {
      default: null,
      type: String,
    },
    size: {
      default: "md-18",
      type: String,
    },
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
    validSize(): boolean {
      return ["sm", "md", "lg", "xl"].indexOf(this.size) != -1;
    },
    btnSize(): string {
      return this.validSize() ? `btn-${this.size}` : "btn-sm ";
    }
  },
  computed: {
    btnType() {
      if (!this.isActive) return "";

      let classes = "";

      classes += this.btnColor();

      classes += this.btnVariant();

      classes += this.btnHasShadow();

      classes += this.btnSize();
      return classes;
    },
    iconSize() {
      if (this.validSize()) return `material-icons ${this.size}`;

      return "material-icons sm";
    },
  },
})
export default class Button extends Vue {}
</script>

<style scoped>
button {
  padding: 7px 15px;
  border-radius: 5px;
  font-size: 1rem;
  z-index: 1;
  transition: background-color 0.5s;
  transition: transform 0.5s;
}
button:disabled,
button[disabled] {
  color: black;
  background-color: rgba(128, 128, 128, 0.6);
  border: 0;
}
button:focus {
  transform: scale(1.08);
}
span {
  z-index: 2;
}
.btn-shadow {
  box-shadow: 0 2px 3px;
}

.btn-sm {
  font-size: 18px;
}
.btn-md {
  font-size: 24px;
}
.btn-lg {
  font-size: 36px;
}
.btn-xl {
  font-size: 48px;
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
.material-icons {
top: 5px;
  position: relative;
  font-family: "Material Icons";
  font-weight: normal;
  font-style: normal;
  text-transform: none;
  letter-spacing: normal;
  word-wrap: normal;
  white-space: nowrap;

  /* Support for all WebKit browsers. */
  -webkit-font-smoothing: antialiased;
  /* Support for Safari and Chrome. */
  text-rendering: optimizeLegibility;

  /* Support for Firefox. */
  -moz-osx-font-smoothing: grayscale;

  /* Support for IE. */
  font-feature-settings: "liga";
}
.material-icons.sm {
  font-size: 18px;
}
.material-icons.md {
  font-size: 24px;
}
.material-icons.lg {
  font-size: 36px;
}
.material-icons.xl {
  font-size: 48px;
}
</style>
