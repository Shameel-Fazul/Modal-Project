<template>
    <div class="backdrop" @click.self="closeModal">
        <div class="modal" :class="{ sale: theme === 'sale' }">
          <h1>{{ header }}</h1>
            <p>{{ text }}</p>
            <slot></slot> <!-- The slot (template) sent from the parent component will be registered here -->
            <div class="actions">
              <slot name="links"></slot> <!-- Custom named slots to organize it well in the child component -->
            </div>
        </div>
    </div>
</template>

<script>
export default {
  props: ['header', 'text', 'theme'], // Obtaining the props sent to this component
  methods: {
    closeModal() {
      this.$emit('close') // Emitting Custom Event, which can be listened from the parent component
    }
  }
 }
</script>

<style>
  .modal {
    width: 400px;
    padding: 20px;
    margin: 100px auto;
    background: white;
    border-radius: 10px;
  }
  .backdrop {
    top: 0;
    position: fixed;
    background: rgba(0,0,0,0.5);
    width: 100%;
    height: 100%;
  }
  .modal.sale {
    background: crimson;
    color: white;
  }
  .modal.sale h1 {
    color: white;
  }
  .modal .actions {
    text-align: center;
    margin: 30px 0 10px 0;
  }
  .modal .actions a {
    color: #333;
    padding: 8px;
    border: 1px solid #eee;
    border-radius: 4px;
    text-decoration: none;
    margin: 10px;
  }
  .modal .sale .actions {
    color: white;
  }
  .modal .sale .actions a {
    color: white;
  }
</style>