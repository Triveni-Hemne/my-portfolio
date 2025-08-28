<template>
  <button
    :class="[
      'px-6 py-2 rounded-full',
      variant === 'see-my-work' ? 'bg-cyan-600 text-white hover:bg-cyan-700 transition' : '',
      variant === 'secondary' ? 'bg-slate-100 hover:bg-slate-200 text-slate-800' : '',
      variant === 'outline' ? 'border border-cyan-600 text-sky-600 hover:bg-cyan-50' : '',
      disabled ? 'opacity-50 cursor-not-allowed' : ''
    ]"
    :disabled="disabled"
  >
    <slot />
  </button>
</template>

<script>
export default {
  name: 'BaseButton',
  props: {
    variant: {
      type: String,
      default: 'primary' // Options: 'primary', 'secondary', 'outline'
    },
    disabled: {
      type: Boolean,
      default: false
    }
  }
}
</script>
