<template>
    Hello, {{ fullName }}!

    <div v-for="user in users" :key="user.id">
        {{ user.name }}
    </div>

    <button @click="changeName">
        Change name
    </button>
</template>

<script>
    import { ref, computed } from 'vue'

    export default {
        setup(props, { emit })
        {
            const firstName = ref('Martins')
            const lastName = ref('Zeltins')
            const users = ref([
                { id: 1, name: 'John' },
                { id: 2, name: 'Martin' },
                { id: 3, name: 'Bob' },
            ])

            const fullName = computed(() => {
                return firstName.value + ' ' + lastName.value
            })

            function changeName()
            {
                firstName.value = 'Gatis'
                lastName.value = 'Eisans'

                emit('some-event')
            }

            return {
                firstName, lastName, users, changeName, fullName
            }
        }
    }
</script>

<style>
    
</style>