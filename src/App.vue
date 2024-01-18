<template>
  <div class="container">
    <h1>選挙サイト</h1>

    <!-- 候補者リスト -->
    <div class="candidates-list">
      <div
        class="candidate-card"
        v-for="candidate in candidates"
        :key="candidate.id"
        @click="selectCandidate(candidate)"
      >
        <img :src="candidate.image" alt="候補者" class="candidate-image" />
        <h5 class="mt-2">{{ candidate.name }}</h5>
      </div>
    </div>

    <!-- 投票フォーム -->
    <div v-if="selectedCandidate" class="vote-form mt-4">
      <h3>選択された候補者: {{ selectedCandidate.name }}</h3>
      <form @submit.prevent="submitVote">
        <div class="form-group">
          <label for="studentId">学生ID</label>
          <input
            type="text"
            class="form-control"
            id="studentId"
            placeholder="学生IDを入力"
            v-model="studentId"
          />
        </div>
        <div class="form-group">
          <label for="password">パスワード</label>
          <input
            type="password"
            class="form-control"
            id="password"
            placeholder="パスワードを入力"
            v-model="password"
          />
        </div>
        <button class="voting-button" type="submit">投票</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      candidates: [
        // ここに候補者データを追加
        { id: 1, name: "候補者1", image: "path/to/test.jpg" },
        { id: 2, name: "候補者2", image: "path/to/test.jpg" },
      ],
      selectedCandidate: null,
      studentId: "",
      password: "",
    };
  },
  methods: {
    selectCandidate(candidate) {
      this.selectedCandidate = candidate;
    },
    submitVote() {
      // 投票のロジックをここに実装
      alert("あなたの投票が完了しました！");
    },
  },
};
</script>

<style>
.voting-button {
  background-color: #00bfff;
  border-radius: 10px;
  color: #fff;
  font-size: 20px;
  margin: 10px;
  padding: 10px 20px;
  border: none;
  cursor: pointer;
  transition: background-color 0.3s, box-shadow 0.3s;

  &:hover {
    background-color: #009fdd;
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.2);
  }

  &:focus {
    outline: none;
    box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.2);
  }
}

.container {
  text-align: center;
  padding-top: 20px;
}

.candidates-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 15px; /* 候補者カード間の隙間を調整 */
}

.candidate-card {
  border: 1px solid #ddd;
  border-radius: 4px;
  width: 200px;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  flex-direction: column;
  align-items: center; /* 内容を中央揃えに */
}

.candidate-card:hover {
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
}

.candidate-image {
  width: 100%;
  height: auto;
  border-bottom: 1px solid #ddd;
}

.vote-form {
  max-width: 400px;
  margin: auto;
  padding: 20px; /* フォーム内の隙間を追加 */
}

@media (max-width: 768px) {
  .candidate-card {
    width: 100%; /* モバイル表示の際にはカードの幅を調整 */
  }
}
</style>
```
