<!-- src/views/event/EditView.vue -->
<script setup lang="ts">
import { toRef } from 'vue'
import { type Event } from '@/types'
import { useRouter } from 'vue-router'
import { useMessageStore } from '@/stores/message'

const props = defineProps<{
    event: Event
    id: String
}>()
// eslint-lisable-next-line @typescript-eslint/no-unused-vars
const { event } = toRef(props)
const router = useRouter()
const store = useMessageStore()

const updateEvent = () => {
    store.updateMessage('Event data has been updated')
    setTimeout(() => {
        store.resetMessage()
    }, 3000)
    router.push({ name: 'event-detail-view', params: { id: props.event.id } })
}
</script>

<template>
    <p>Edit event here</p>
    <button @click="updateEvent">Save Changes</button>
</template>
