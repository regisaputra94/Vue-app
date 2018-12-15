<template>
  <div class="ui-page-home">
    <UiTitleIconComponent
      icon="star"
      title="Starred Boards" />

    <div class="uk-child-width-1-2@s uk-grid-match" uk-grid>
      <UiCardComponent
        v-for="board in StarredBoards"
        v-bind:key="board.id"
        type="default"
        v-bind:title="board.title"
        v-bind:description="board.description" />
    </div>

    <UiTitleIconComponent
      icon="user"
      title="Personal Boards" />

    <div class="uk-child-width-1-2@s uk-grid-match" uk-grid>
      <UiCardComponent
        v-for="board in PersonalBoards"
        v-bind:key="board.id"
        type="default"
        v-bind:title="board.title"
        v-bind:description="board.description" />
    </div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      StarredBoards: [
        {
          id: 1,
          title: 'Hello World 1',
          description: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.'
        },
        {
          id: 2,
          title: 'Hello World 2',
          description: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.'
        },
        {
          id: 3,
          title: 'Hello World 3',
          description: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.'
        },
        {
          id: 4,
          title: 'Hello World 4',
          description: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.'
        }
      ],
      PersonalBoards: [
        {
          id: 1,
          title: 'Hello World 1',
          description: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.'
        },
        {
          id: 2,
          title: 'Hello World 2',
          description: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.'
        },
        {
          id: 3,
          title: 'Hello World 3',
          description: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.'
        },
        {
          id: 4,
          title: 'Hello World 4',
          description: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.'
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
  .uk-heading-bullet {
    font-size: 25px;
  }

  .uk-card-title {
    font-size: 20px;
  }
</style>
