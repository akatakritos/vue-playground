<template>
    <div class="outer vr_2">
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

<style lang="scss" scoped>
    $radius: 5px;

    .outer {
        border: 1px solid #35495e;
        border-radius: $radius;
    }

    .inner {
        background-color: #41b883;
        height: 25px;
        border-right: 1px solid darken(#41b883, 25%);
        transition: width 500ms ease-out;
        border-radius: $radius 0 0 $radius;
    }

    .vr_2 {
        margin-bottom: 20px;
    }
</style>

