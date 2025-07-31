<template>
    <div>
        <input
            type="checkbox"
            id="myCheckboxBlue"
            class="checkboxBlue"
            value="blue"
            v-model="options"
        />
        <input
            type="checkbox"
            id="myCheckboxRed"
            class="checkboxRed"
            value="red"
            v-model="options"
        />
        <label for="myCheckbox">
            Check me
        </label>
        <div v-if="isChecked">
            Hello
        </div>
    </div>
</template>

<script>
    export default {
        name: 'CheckBox',
        data() {
            return {
                isChecked: false,
                options: [],
            }
        },
        props: {
            isCheckedParent: Boolean,
        },
        computed: {
            checkboxValue: {
                get() {
                    return this
                        .isCheckedParent
                },
                set(value) {
                    this.$emit(
                        'update:isCheckedParent',
                        value
                    )
                },
            },
        },
    }
</script>

<style scoped>
    .checkboxBlue {
        border: 1px solid blue;
        width: 20px;
    }
    .checkboxRed {
        border: 1px solid red
    }
</style>
