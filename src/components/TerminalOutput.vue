<template>
  <div id="base">
    <div class="terminal-command-group">
      <TerminalPrompt></TerminalPrompt>
      <span>{{cmd.fullCommand}}</span>
    </div>
    <p v-if="cmd.showAsRawHTML" v-html="$props.cmd.output" v-bind:style="cmd.additionalStyling" v-bind:class="{error: cmd.additionalClass === 'error'}"></p>
    <p v-else v-bind:style="cmd.additionalStyling" v-bind:class="{error: cmd.additionalClass === 'error'}">{{$props.cmd.output}}</p>
  </div>
</template>

<script lang="ts">
import TerminalPrompt from "@/components/TerminalPrompt.vue";
import {defineComponent, PropType} from "vue";
import {CommandResponse} from "@/scripts/command";

export default defineComponent({
  name: "TerminalOutput",
  components: {TerminalPrompt},
  props: {
    cmd: {
      type: (Object as PropType<CommandResponse>),
      required: true
    }
  }
});

</script>

<style lang="sass">
//@import "@/styles"


</style>