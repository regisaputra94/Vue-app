<template>
  <div class="ui-page-home">
    <div v-if="listOfFavoriteBoards.length > 0">
      <UiTitleIconComponent
        icon="star"
        title="Starred Boards" />

      <div class="uk-child-width-1-3@s uk-grid-small" uk-grid>
        <UiBoardComponent
          v-for="board in listOfFavoriteBoards"
          type="default"
          v-bind:key="board.id"
          v-bind:board="board"
          v-bind:toggleFavorite="toggleFavorite" />
      </div>
    </div>

    <UiTitleIconComponent
      icon="user"
      title="Personal Boards" />

    <div class="uk-child-width-1-3@s uk-grid-small" uk-grid>
      <UiBoardComponent
        v-for="board in listOfPersonalBoards"
        type="default"
        v-bind:key="board.id"
        v-bind:board="board"
        v-bind:toggleFavorite="toggleFavorite" />
    </div>
  </div>
</template>

<script>
import _filter from 'lodash/filter'

export default {
  methods: {
    toggleFavorite: function (board) {
      let newBoards = []
      let boards = this.Boards

      boards.map(x => {
        let obj = Object.assign({}, x)
        if (obj.id === board.id) {
          obj.isFavorite = !board.isFavorite
        }
        newBoards.push(obj)
      })

      this.Boards = newBoards
    }
  },
  data: function () {
    return {
      Boards: [
        {
          id: 1,
          title: 'Personal Board 1',
          description: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.',
          isFavorite: true
        },
        {
          id: 2,
          title: 'Personal Board 2',
          description: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.',
          isFavorite: false
        },
        {
          id: 3,
          title: 'Personal Board 3',
          description: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.',
          isFavorite: false
        },
        {
          id: 4,
          title: 'Personal Board 4',
          description: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.',
          isFavorite: false
        }
      ]
    }
  },
  computed: {
    listOfPersonalBoards: function () {
      return this.Boards
    },
    listOfFavoriteBoards: function () {
      return _filter(this.Boards, { isFavorite: true })
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
