<template>
    <button @click="OnClick()" :class="'btn btn-'+color">
        {{ text }}
    </button>
</template>
<script>
export default {
    name:'ButtonComponent',
    props: {
        text: {
            type: String,
            required: true
        },
        color: {
            type: String,
            required: true
        }
    },
    methods: {
        OnClick() {
            this.$emit('toggle-show');
        }
    }
}
</script>
