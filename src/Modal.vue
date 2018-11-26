<template>
  <transition name="modal-fade">
    <div class="modal-backdrop">
      <div class="modal">
        <div class="container">
          <div class="row">
            <div class="view-info">
              <h2 class="view-caption">View Details</h2>

              <div class="id">
                <span>ID:</span> 
                {{item.id}}
              </div>

              <div class="userId">
                <span>Name:</span> 
                {{item.name}}
              </div>

              <div class="title">
                <span>Description:</span> 
                {{item.desc}}
              </div>

              <div class="body">
                <span>Body:</span> 
                {{item.tagline}}
              </div>
            </div>
          </div>
          
          <button
            type="button"
            class="btn-close"
            @click="close"
            aria-label="Close modal"
          >
            x
          </button>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  props: {
    item: {}
  },
  data(){
    return {
    }
  },
  methods:{
   close() {
      this.$emit("close");
   }
  }
}
</script>
<style>
.modal-backdrop {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0.3);
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal {
  background: #ffffff;
  box-shadow: 2px 2px 20px 1px;
  overflow-x: auto;
  display: flex;
  flex-direction: column;
  width: 540px;
  height: calc(100% - 40vh);
  margin: auto;
}

.btn-close {
  border: none;
  font-size: 20px;
  padding: 20px;
  cursor: pointer;
  font-weight: bold;
  color: #4aae9b;
  background: transparent;
  position: absolute;
  right: 10px;
  top: 5px
}

.btn {
  color: white;
  background: #4aae9b;
  border: 1px solid #4aae9b;
  border-radius: 2px;
}

.modal-fade-enter,
.modal-fade-leave-active {
  opacity: 0;
}

.modal-fade-enter-active,
.modal-fade-leave-active {
  transition: opacity 0.5s ease;
}
.view-info {
  padding: 20px;
}
.view-info span{
  font-size: 20px;
  font-weight: 700;
}
.view-caption {
  text-align: center;
}
</style>