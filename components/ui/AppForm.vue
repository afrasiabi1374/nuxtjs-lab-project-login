<template>
  <validation-observer v-slot="{ handleSubmit }" ref="validation">
    <form @submit.prevent="handleSubmit(onSubmit)">
        <slot>

        </slot>
    </form>
  </validation-observer>
</template>

<script>
import { ValidationObserver } from 'vee-validate'
export default {
    name: 'AppForm',
    components: {
        ValidationObserver
    },
    props: {
        onSubmit: {
            type: Function,
            required: true
        }
    },
    methods: {
        reset(){
            this.$refs.validation.reset()
        },
        addError(key, value){
            this.$refs.validation.setErrors({
                [key]: value
            })
        }
    }
}
</script>

<style scoped>

</style>