<template>
  <div class="ui-page-home">
    <div v-if="StarredBoards.length > 0">
      <UiTitleIconComponent
        icon="star"
        title="Starred Boards" />

      <div class="uk-child-width-1-3@s uk-grid-small" uk-grid>
        <UiBoardComponent
          v-for="board in StarredBoards"
          type="default"
          v-bind:key="board.id"
          v-bind:board="board"
          v-bind:toggleFavorite="toggleFavorite"
          isFavorite />
      </div>
    </div>

    <UiTitleIconComponent
      icon="user"
      title="Personal Boards" />

    <div class="uk-child-width-1-3@s uk-grid-small" uk-grid>
      <UiBoardComponent
        v-for="board in PersonalBoards"
        type="default"
        v-bind:key="board.id"
        v-bind:board="board"
        v-bind:toggleFavorite="toggleFavorite" />
    </div>
  </div>
</template>

<script>
import _find from 'lodash/find'
import _filter from 'lodash/filter'
import _isUndefined from 'lodash/isUndefined'

export default {
  methods: {
    toggleFavorite: function (board) {
      const boardExist = _find(this.StarredBoards, { id: board.id })
      if (_isUndefined(boardExist)) {
        this.StarredBoards.push(board)
      } else {
        this.StarredBoards = _filter(this.StarredBoards, (x) => {
          return x.id !== board.id
        })
      }
    }
  },
  data: function () {
    return {
      StarredBoards: [
        {
          id: 1,
          title: 'Starred Board 1',
          description: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.'
        },
        {
          id: 2,
          title: 'Starred Board 2',
          description: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.'
        }
      ],
      PersonalBoards: [
        {
          id: 1,
          title: 'Personal Board 1',
          description: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.'
        },
        {
          id: 2,
          title: 'Personal Board 2',
          description: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.'
        },
        {
          id: 3,
          title: 'Personal Board 3',
          description: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.'
        },
        {
          id: 4,
          title: 'Personal Board 4',
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
