<template>
  <div class="ui-page-board">
    <div class="uk-container">
      <div class="ui-places-task">
        <UiPlaceTaskComponent
          v-for="Place in Places"
          v-bind:key="Place.id" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      Places: [
        {
          id: 1,
          name: 'First Place',
          tasks: []
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
  .ui-page-board {
    padding: 10px 15px;
    position: relative;
    background: url('https://remote.co/wp-content/uploads/2018/05/Remote-Work-More-Than-a-Perk-for-Pros-with-Chronic-Conditions.jpg') center center;
    background-size: cover;
    position: relative;
    overflow: hidden;
    height: 700px;
    padding-top: 50px;

    .ui-places-task {
      width: 100%;
      overflow-x: scroll;
      display: flex;
      flex-direction: row;
    }
  }
</style>
