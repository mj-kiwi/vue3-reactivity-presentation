<script setup lang="ts">
import { NFormItem, NInput, NButton } from 'naive-ui'
import { ref, reactive, toRef, toRefs } from '@vue/reactivity'

interface Counter {
    counter: {
        number: number
    }
}
const count1 = ref<number>(0)
const count2 = reactive<Counter>({ counter: { number: 0 } })
const count3 = reactive<Counter>({ counter: { number: 0 } })
const number1 = toRef(count2, 'counter')
const number2 = toRef(count3, 'counter')
const { counter: number3 } = toRefs(count2)
const { counter: number4 } = toRefs(count3)

function change() {

    count1.value++
    // Update the attribuet in the object
    count2.counter.number++

    // Assign a new object to the reactive object
    Object.assign(count3, {
        counter: {
            number: count3.counter.number + 1
        }
    })
}

</script>
<template>
    <n-form-item label="Count 1" path="inputValue" label-placement="left">
        <n-input placeholder="Input" :value="count1 + ''" />
    </n-form-item>
    <n-form-item label="Count 2" path="inputValue" label-placement="left">
        <n-input placeholder="Input" :value="count2.counter.number + ''" />
    </n-form-item>
    <n-form-item label="Count 3" path="inputValue" label-placement="left">
        <n-input placeholder="Input" :value="count3.counter.number + ''" />
    </n-form-item>
    <n-form-item label="Number 1" path="inputValue" label-placement="left">
        <n-input placeholder="Input" :value="number1.number + ''" />
    </n-form-item>
    <n-form-item label="Number 2" path="inputValue" label-placement="left">
        <n-input placeholder="Input" :value="number2.number + ''" />
    </n-form-item>
    <n-form-item label="Number 3" path="inputValue" label-placement="left">
        <n-input placeholder="Input" :value="number3.number + ''" />
    </n-form-item>
    <n-form-item label="Number 4" path="inputValue" label-placement="left">
        <n-input placeholder="Input" :value="number4.number + ''" />
    </n-form-item>
    <n-button @click="change">Press Me</n-button>
</template>