<script>
// @ts-nocheck
    import { createEventDispatcher } from "svelte";
    import ButtonRow from "./ButtonRow.svelte";
    import ToggleButton from "./ToggleButton.svelte";

    export let title, options, currentOption;

    const dispatch = createEventDispatcher();
    
    function pickOption(option) {
        dispatch('option', {
            option: option
        });
    }
</script>

<div class="control-pane">
    <h2 class="title">
        {title}

        <span class="metadata">
        {options.length} options
        </span>
    </h2>

    <ButtonRow>
    {#each options as option (option.id)}
        <ToggleButton on:click={() => pickOption(option.id)} isSelected={currentOption == option.id} label={option.label} color={option.color}>
            {(option.children != null) ? option.children : ''}
        </ToggleButton>
    {/each}
    </ButtonRow>
</div>

<style>
.control-pane {
  padding: 24px;
  /* Optical centering */
  padding-top: 18px;
  background-color: white;
  border-radius: 8px;
  /*
    HACK: Margin on an outer bound like this is
    a little gross, but we haven't seen the tools
    to deal with it yet!
  */
  margin-bottom: 32px;
}

.title {
  margin: 0;
  /* Optical centering */
  margin-bottom: -4px;
}

.metadata {
  margin-left: 16px;
  font-size: 0.875rem;
  font-weight: 400;
  color: hsl(0deg, 0%, 30%);
}
</style>