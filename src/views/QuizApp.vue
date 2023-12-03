<template>
  <h1>Vue クイズ</h1>
  <div class="app" v-for="(quiznumber, i) in quizzes" v-bind:key="i">
    <h2>Q. {{ quiztext }}</h2>
    <img class="quiz-image" v-bind:src="quizImagePath" />
    <div>
      <li>{{ choice1 }}</li>
      <li>{{ choice2 }}</li>
      <li>{{ choice3 }}</li>
    </div>
    <div class="button-container">
      <button
        v-for="(sentaku, i) in quiznumber.choices"
        v-bind:key="i"
        v-on:click="choiced(sentaku)"
      >
        {{ sentaku.buttontext }}
      </button>
    </div>
    <div>{{ feedback }}</div>
    <button class="next-button" v-on:click="quizload(quiznumber)">次へ</button>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      quiznumber: 0,
      feedback: "",
      quizzes: [
        {
          text: "チーム名に含まれる「dlbia」はイギリスのバンドOasisによる「Don't Look Back In Anger」の略称です。この英文の意味は？",
          image: "oasis_morningglory.jpg",
          choices: [
            {
              buttontext: "A",
              question: "A:振り向くな、感じろ",
              isCorrect: false,
              feedback: "残念！",
            },
            {
              buttontext: "B",
              question: "B:怒りを持って背中を睨まないで",
              isCorrect: false,
              feedback: "残念！",
            },
            {
              buttontext: "C",
              question: "C:怒りに任せて過去を振り向かないで",
              isCorrect: true,
              feedback:
                "正解！意訳は「変わらない過去より未来に目を向けろ」だよ！ロックだね！",
            },
          ],
        },
        {
          text: "イギリスのバンド「Oasis」の主要メンバー2人の関係性は？",
          image: "gallagherbros.jpeg",
          choices: [
            {
              buttontext: "A",
              question: "A:大学で出会った親友",
              isCorrect: false,
              feedback: "残念！",
            },
            {
              buttontext: "B",
              question: "B:兄弟",
              isCorrect: true,
              feedback: "正解！眉毛がそっくりだよ！",
            },
            {
              buttontext: "C",
              question: "C:ネットで出会った友人",
              isCorrect: false,
              feedback: "残念！",
            },
          ],
        },
      ],
    }
  },
  methods: {
    quizload: function (quiznumber) {
      quiznumber += 1
      this.quiztext = "Q. " + this.quiznumber.text
      this.choice1 = quiznumber.choices[0].question
      this.choice2 = quiznumber.choices[1].question
      this.choice3 = quiznumber.choices[2].question
      this.feedback = ""
    },
    choiced: function (sentaku) {
      this.feedback = sentaku.feedback
    },
  },
  computed: {
    quizImagePath() {
      return require("@/assets/" + this.quiznumber.image)
    },
  },
}
</script>

<style scoped>
.app {
  display: flex;
  width: 100%;
  flex-direction: column;
  align-items: center;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.quiz-image {
  height: 200px;
  width: 200px;
  margin-bottom: 1em;
  object-fit: contain;
}

.next-button {
  width: 3.5em;
}
li {
  list-style: none;
}
.button-container {
  display: flex;
  height: 1.8em;
  width: 150px;
  padding: 1em;
  justify-content: space-around;
}
</style>
