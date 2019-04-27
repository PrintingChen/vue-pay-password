<template>
    <div class="vue-pay-password">
        <ul class="vue-pay-password-ul" @click="onClick">
            <li>
                <i :class="{'is-show': inputValue.length>0}"></i>
            </li>
            <li>
                <i :class="{'is-show': inputValue.length>1}"></i>
            </li>
            <li>
                <i :class="{'is-show': inputValue.length>2}"></i>
            </li>
            <li>
                <i :class="{'is-show': inputValue.length>3}"></i>
            </li>
            <li>
                <i :class="{'is-show': inputValue.length>4}"></i>
            </li>
            <li class="is-last">
                <i :class="{'is-show': inputValue.length>5}"></i>
            </li>
            <span :style="{transform: 'translateX(' + offset + 'px)', visibility: visibility}"></span>
        </ul>
        <input
            ref="my-input"
            class="vue-pay-password-input"
            type="text"
            v-model="inputValue"
            @focus="onFocus"
            @blur="onBlur"
            maxlength="6"
            minlength="6"
            oncontextmenu="return false"
            onpaste="return false"
            oncopy="return false"
            oncut="return false"
            onkeypress="return event.keyCode>=48&&event.keyCode<=57"
        >
    </div>
</template>

<script>
export default {
    name: 'VuePayPassword',
    data() {
        return {
            inputValue: '',
            visibility: 'hidden',
        }
    },
    computed: {
        offset() {
            return 33 * Math.min(this.inputValue.length, 5)
        },
    },
    watch: {
        inputValue(val) {
            this.inputValue = val.replace(/\D/g, '')
        },
    },
    methods: {
        onClick() {
            this.$refs['my-input'].focus()
        },
        onFocus() {
            this.visibility = 'visible'
        },
        onBlur() {
            this.visibility = 'hidden'
        },

        // 外部获取密码
        getPassword() {
            return this.inputValue
        },
    },
}
</script>
<style scoped>
.vue-pay-password {
    display: inline-block;
}

.vue-pay-password-ul {
    list-style: none;
    margin: 0;
    padding: 0;
    overflow: hidden;
}
.vue-pay-password-ul li {
    list-style: none;
    margin: 0;
    padding: 0;
    position: relative;
    float: left;
    width: 32px;
    height: 32px;
    text-align: center;
    border: 1px solid #dedede;
    border-right: none;
}
.vue-pay-password-ul li.is-last {
    border: 1px solid #dedede;
}
.vue-pay-password-ul i {
    visibility: hidden;
    width: 8px;
    height: 8px;
    position: absolute;
    left: 50%;
    top: 50%;
    margin-left: -4px;
    margin-top: -4px;
    background-image: url('data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAAAXNSR0IArs4c6QAAAY1JREFUOBHFkb1LA0EQxe8uR6xSaGGnCVdGCzVfkNIUKjY2FxA7G/8BSxsLEbESwU5BRASjoLUI6a5JtLUxqKk0ajqJuVzib85w5ONSWTjwdua9nZ2dnVWUP5o66Hw6nR5tNBrjsh8Oh+9zuZzjl6v7iaLZtr3YbDaPJC6VSkGcbwFNEvxMVdVKW68Wi0XbL0e0gQW4/U0SKOR6if3Me0I8Hl9rtVpB7NSyrE9N0yqO4yhoXoFEIjEFXwV7dPUoBd0hIqgUeILL0L7BNTefo1/gb+FXQA5O46WrjUKhsCWx20EqlRpBvIHPkDSBz+KzkoDP4ARi7+AO7cNlLH3faJpmkKlPsncJIkDsAOzQ9ovLOpa+IfLfdd4/R06Eriz8F1jRdX2o45wXBryoHSSTyTl+4BDaAPOgChbQMoZhnJTL5Trcs64OmLLB5M/Y1bh9n5YfQqHQLvwZRGu12jHv73p2VwE2l0kc5vBrIBDYJFby+XwNvi4xNkuH0d9wwBqLxZaA2buNtk2HY736//MfzUiXTrGJMDYAAAAASUVORK5CYII=');
    background-repeat: no-repeat;
    background-size: 100% 100%;
    transition: visibility 0.1s;
}
.vue-pay-password-ul i.is-show {
    visibility: visible;
}
.vue-pay-password-ul span {
    position: absolute;
    display: block;
    width: 32px;
    height: 32px;
    border: 1px solid rgba(82, 168, 236, 0.8);
    transform: translateX(0px);
    transition: transform 0.1s;
    box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075),
        0 0 8px rgba(82, 168, 236, 0.6);
}
.vue-pay-password-input {
    position: absolute;
    outline: none;
    margin-left: -999px;
}
</style>

