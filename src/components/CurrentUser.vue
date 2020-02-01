<template>
    <span>
        <slot v-bind:user="user">
            {{ user.lastName }}
        </slot>
    </span>
</template>

<script>
export default {
    data() {
        return {
            user: { 
                firstName: 'Jhon',               
                lastName: 'Newman',
                age: 26
            }
        }
  },
}
</script>