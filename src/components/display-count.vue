<template>
  <div v-if="column" class="d-flex flex-column justify-space-between" style="width:50px">
    <div class="d-flex justify-space-between align-center">
      <v-icon left :color="item.readCount ? 'info' : ''">mdi-eye</v-icon>
      <span class="body-2" v-if="item.readCount < 100">{{item.readCount}}</span>
      <span class="body-2" v-else>99+</span>
    </div>
    <div class="d-flex justify-space-between align-center">
      <v-icon left :color="item.commentCount ? 'info' : ''">mdi-comment</v-icon>
      <span class="body-2" v-if="item.commentCount < 100">{{item.commentCount}}</span>
      <span class="body-2" v-else>99+</span>
    </div>
    <div class="d-flex justify-space-between align-center">
      <v-icon left :color="liked(item) ? 'info' : ''">mdi-heart</v-icon>
      <span class="body-2" v-if="item.likeCount < 100">{{item.likeCount}}</span>
      <span class="body-2" v-else>99+</span>
    </div>
  </div>
  <div v-else class="d-flex justify-end align-center">
    <div class="d-flex align-center mr-2">
      <v-icon left :color="item.readCount ? 'info' : ''">mdi-eye</v-icon>
      <span class="body-2" v-if="item.readCount < 100">{{item.readCount}}</span>
      <span class="body-2" v-else>99+</span>
    </div>
    <div class="d-flex align-center mr-2">
      <v-icon left :color="item.commentCount ? 'info' : ''">mdi-comment</v-icon>
      <span class="body-2" v-if="item.commentCount < 100">{{item.commentCount}}</span>
      <span class="body-2" v-else>99+</span>
    </div>
    <div class="d-flex align-center">
      <v-icon left :color="liked(item) ? 'info' : ''">mdi-heart</v-icon>
      <span class="body-2" v-if="item.likeCount < 100">{{item.likeCount}}</span>
      <span class="body-2" v-else>99+</span>
    </div>
  </div>
</template>
<script>
export default {
  props: ['item', 'column'],
  computed: {
    fireUser () {
      return this.$store.state.fireUser
    }
  },
  methods: {
    liked (item) {
      if (!this.fireUser) return false
      if (!item.likeUids) return false
      return item.likeUids.includes(this.fireUser.uid)
    }
  }
}
</script>
