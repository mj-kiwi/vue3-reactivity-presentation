<script setup lang="ts">
import { NFormItem, NInput, NButton } from 'naive-ui'
import { customRef, toRef, toRefs } from '@vue/reactivity'

interface Counter {
    counter: {
        number: number
    }
}

function useDebouncedRef<T>(value: T, delay = 500) {
    let timeout: NodeJS.Timeout

    return customRef((track, trigger) => {
        return {
            get() {
                track()
                return value
            },
            set(newValue: T) {
                clearTimeout(timeout)
                timeout = setTimeout(() => {
                    value = newValue
                    trigger()
                }, delay)
            }
        }
    })
}

const count1 = useDebouncedRef<number>(0)
const count2 = useDebouncedRef<Counter>({ counter: { number: 0 } })
const count3 = useDebouncedRef<Counter>({ counter: { number: 0 } })



function change() {

    count1.value++
    // Update the attribuet in the object
    count2.value.counter.number = ++count2.value.counter.number

    // Assign a new object to the count3
    count3.value = {
        counter: {
            number: ++count3.value.counter.number
        }
    }
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
    <n-button @click="change">Press Me</n-button>
</template>