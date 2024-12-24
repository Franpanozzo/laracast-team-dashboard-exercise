<script setup>
import Modal from '@/components/Modal.vue'
import { ref } from 'vue'
import {useTeamStore} from '@/stores/TeamStore';

let team = useTeamStore();

let showModal = ref(false);

</script>

<template>
  <button
    :disabled="! team.spotsRemaining"
    @click="showModal = true"
    class="bg-green-500 hover:bg-green-600 text-white px-4 py-2 rounded disabled:bg-gray-400"
  >
    Add Member ({{ team.spotsRemaining }} Spots Left)
  </button>

  <Teleport to="body">
    <Modal :show="showModal" @close="showModal = false">
      <p>Need to add a new member to your team?</p>

      <form class="mt-6">
        <div class="flex gap-2">
          <input type="email" placeholder="Email address..." class="flex-1">
          <button> Add </button>
        </div>
      </form>
    </Modal>
  </Teleport>
</template>
