<template>
  <div class="backdrop" @click.self="collapseModal">
    <div class="modal" :class="{ sale: theme === 'sale' }">
      <slot>
        <h1>Epic Give-Away</h1>
        <p>All deals now 50% off</p>
      </slot>
      <div class="actions">
        <slot name="links"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["theme"],
  methods: {
    collapseModal() {
      this.$emit("collapse");
    },
  },
};
</script>

<style>
.modal {
  width: 600px;
  padding: 30px;
  margin: 100px auto;
  background-color: #fff;
  border-radius: 10px;
  box-shadow: 0 0 50px rgba(0, 0, 0, 0.6);
}
.backdrop {
  top: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0.4);
  width: 100vw;
  height: 100vh;
}
.modal h1 {
  color: blueviolet;
  border: none;
  padding: 0;
}

.modal p {
  font-size: 1.5rem;
}
.modal.sale {
  background: crimson;
  color: #fff;
}
.modal.sale h1 {
  color: #fff;
}
.modal .actions {
  text-align: center;
  margin: 30px 0 10px 0;
}
.modal .actions a {
  color: #333;
  padding: 8px;
  border: 1px solid #333;
  border-radius: 4px;
  text-decoration: none;
  margin: 10px;
}
.modal.sale .actions {
  color: #fff;
}
.modal.sale .actions a {
  color: #fff;
  border: 1px solid #fff;
}
</style>
