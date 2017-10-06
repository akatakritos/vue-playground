<template>
    <div class="outer">
        <div class="inner" :style="innerStyle"></div>
    </div>
</template>

<script>
    export default {
        data() {
            return {

            }
        },
        props: {
            "max" : { type: Number, required: true},
            "current" : { type: Number, required: true, default: 0 }
        },
        computed: {
            innerStyle() {
                return {
                    width: `${this.current / this.max * 100}%`
                }
            }
        }
    }
</script>

<style scoped>
    .outer {
        border: 1px solid black;
    }

    .inner {
        background-color: green;
        height: 25px;
    }
</style>