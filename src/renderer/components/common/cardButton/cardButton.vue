<template>
    <div class="card-button"
         v-bind:style="{color:color, width:outerWidth, height:outerHeight, borderColor:color}"
         v-on:click="$emit('click-button')">
        <div>
            <Icon v-bind:type="type" v-bind:size="size" v-bind:color="color"/>
        </div>
        <div class="card-text">
            <span>{{text}}</span>
        </div>
    </div>
</template>
<script>
    export default {
      props: ['type', 'size', 'color', 'text'],
      data() {
        return {
          data: 0,
        };
      },
      computed: {
        outerWidth: function () {
          return `${parseInt(this.size) + 18}px`;
        },
        outerHeight: function () {
          return `${parseInt(this.size) + 18}px`;
        }
      },
    };
</script>
<style>
    .ivu-icon:before,
    .ivu-icon:after {
        font-family: Ionicons !important;
    }
    .card-button {
        width:60px;
        height:60px;
        border-radius: 50%;
        border:2px solid pink;
        text-align: center;
        cursor: pointer;
    }
    .card-button:hover {
        background-color: rgba(50, 80, 90, 0.1);
        transition: all .2s ease-in-out;
    }
    .card-text {
        margin-top:-5px;
    }
</style>