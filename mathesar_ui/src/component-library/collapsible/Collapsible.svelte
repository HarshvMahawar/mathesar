<script lang="ts">
  import Icon from '@mathesar-component-library-dir/icon/Icon.svelte';
  import Button from '@mathesar-component-library-dir/button/Button.svelte';
  import { iconExpandDown } from '@mathesar-component-library-dir/common/icons';
  import type { Appearance } from '@mathesar-component-library-dir/commonTypes';

  export let isOpen = false;
  export let triggerAppearance: Appearance = 'default';

  function toggle() {
    isOpen = !isOpen;
  }
</script>

<div class="collapsible">
  <slot name="trigger" {toggle} {isOpen}>
    <Button
      appearance={triggerAppearance}
      class="collapsible-header"
      on:click={toggle}
    >
      <Icon
        {...iconExpandDown}
        size="0.9rem"
        rotate={isOpen ? undefined : 270}
      />
      <div class="collapsible-header-title">
        <slot name="header" />
      </div>
    </Button>
  </slot>
  {#if isOpen}
    <div class="collapsible-content">
      <slot name="content" />
    </div>
  {/if}
</div>
