<script setup lang="ts">
import { NFormItem, NInput, NButton } from 'naive-ui'
import { ref, reactive, toRef, toRefs } from '@vue/reactivity'


let count1 = $ref<number>(0)
let count2 = $(ref<number>(0))

function change() {
    count1++
    count2++
}

function useDollar() {
    let dollar = $ref(1)
    const needMore = () => {
        dollar = dollar * 10
    }

    return $$({
        dollar,
        needMore
    })
}

const { dollar, needMore } = useDollar()

</script>
<template>
    <n-form-item label="Count 1" path="inputValue" label-placement="left">
        <n-input placeholder="Input" :value="count1 + ''" />
    </n-form-item>
    <n-form-item label="Count 2" path="inputValue" label-placement="left">
        <n-input placeholder="Input" :value="count2 + ''" />
    </n-form-item>
    <n-button @click="change">Press Me</n-button>
    <hr />
    <n-form-item label="Dollar" path="inputValue" label-placement="left">
        <n-input placeholder="Input" :value="dollar + ''" />
    </n-form-item>
    <n-button @click="needMore">More Dollars</n-button>
</template>