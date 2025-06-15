<template>
  <div class="hello" style="padding: 12px;">

    <small><a target="_blank"
              href="https://github.com/matisiekpl/tkankowa/blob/main/src/assets/questions.json">github</a></small><br/>

    <small>Odpowiedziałeś poprawnie
      <mark>{{ answered_correctly }}/{{ answered }}</mark>
    </small><br/><br/>
    <h5>{{ question['question'] }}</h5>
    <div style="font-size: 18px; margin-bottom: 64px;">

      <div v-if="question['answer_a']!==''">
        <input type="checkbox" id="answer_a" name="answer_a" v-model="answer_a_selected">
        <label for="answer_a"><span :class="{'blue':question['answer_a_correct']&&checking}"
                                    style="margin-right: 12px;">{{
            question['answer_a']
          }}</span>
          <span class="green" v-if="checking&&answer_a_correct">Dobrze</span>
          <span class="red"
                v-if="checking&&!answer_a_correct">Źle</span>
        </label><br>
      </div>

      <div v-if="question['answer_b']!==''">
        <input type="checkbox" id="answer_b" name="answer_b" v-model="answer_b_selected">
        <label for="answer_b"><span :class="{'blue':question['answer_b_correct']&&checking}"
                                    style="margin-right: 12px;">{{
            question['answer_b']
          }}</span>
          <span class="green" v-if="checking&&answer_b_correct">Dobrze</span>
          <span class="red"
                v-if="checking&&!answer_b_correct">Źle</span></label><br>
      </div>

      <div v-if="question['answer_c']!==''">
        <input type="checkbox" id="answer_c" name="answer_c" v-model="answer_c_selected">
        <label for="answer_c"><span :class="{'blue':question['answer_c_correct']&&checking}"
                                    style="margin-right: 12px;">{{
            question['answer_c']
          }}</span> <span class="green"
                          v-if="checking&&answer_c_correct">Dobrze</span>
          <span class="red"
                v-if="checking&&!answer_c_correct">Źle</span></label><br>
      </div>

      <div v-if="question['answer_d']!==''">
        <input type="checkbox" id="answer_d" name="answer_d"
               v-model="answer_d_selected">
        <label for="answer_d"><span :class="{'blue':question['answer_d_correct']&&checking}"
                                    style="margin-right: 12px;">{{
            question['answer_d']
          }}</span>
          <span class="green" v-if="checking&&answer_d_correct">Dobrze</span>
          <span class="red"
                v-if="checking&&!answer_d_correct">Źle</span></label><br>
      </div>

      <div v-if="question['answer_e']!==''">
        <input type="checkbox" id="answer_e" name="answer_e"
               v-model="answer_e_selected">
        <label for="answer_e"><span :class="{'blue':question['answer_e_correct']&&checking}"
                                    style="margin-right: 12px;">{{
            question['answer_e']
          }}</span>
          <span class="green" v-if="checking&&answer_e_correct">Dobrze</span>
          <span class="red"
                v-if="checking&&!answer_e_correct">Źle</span></label><br>
      </div>

      <div v-if="question['answer_f']!==''">
        <input type="checkbox" id="answer_f" name="answer_f"
               v-model="answer_f_selected">
        <label for="answer_f"><span :class="{'blue':question['answer_f_correct']&&checking}"
                                    style="margin-right: 12px;">{{
            question['answer_f']
          }}</span>
          <span class="green" v-if="checking&&answer_f_correct">Dobrze</span>
          <span class="red"
                v-if="checking&&!answer_f_correct">Źle</span></label><br>
      </div>

      <div v-if="question['answer_g']!==''">
        <input type="checkbox" id="answer_g" name="answer_g"
               v-model="answer_g_selected">
        <label for="answer_g"><span :class="{'blue':question['answer_g_correct']&&checking}"
                                    style="margin-right: 12px;">{{
            question['answer_g']
          }}</span>
          <span class="green" v-if="checking&&answer_g_correct">Dobrze</span>
          <span class="red"
                v-if="checking&&!answer_g_correct">Źle</span></label><br>
      </div>

      <div v-if="question['answer_h']!==''">
        <input type="checkbox" id="answer_h" name="answer_h"
               v-model="answer_h_selected">
        <label for="answer_h"><span :class="{'blue':question['answer_h_correct']&&checking}"
                                    style="margin-right: 12px;">{{
            question['answer_h']
          }}</span>
          <span class="green" v-if="checking&&answer_h_correct">Dobrze</span>
          <span class="red"
                v-if="checking&&!answer_h_correct">Źle</span></label><br>
      </div>

      <div v-if="question['answer_i']!==''">
        <input type="checkbox" id="answer_i" name="answer_i"
               v-model="answer_i_selected">
        <label for="answer_i"><span :class="{'blue':question['answer_i_correct']&&checking}"
                                    style="margin-right: 12px;">{{
            question['answer_i']
          }}</span>
          <span class="green" v-if="checking&&answer_i_correct">Dobrze</span>
          <span class="red"
                v-if="checking&&!answer_i_correct">Źle</span></label><br>
      </div>

      <div v-if="question['answer_j']!==''">
        <input type="checkbox" id="answer_j" name="answer_j"
               v-model="answer_j_selected">
        <label for="answer_j"><span :class="{'blue':question['answer_j_correct']&&checking}"
                                    style="margin-right: 12px;">{{
            question['answer_j']
          }}</span>
          <span class="green" v-if="checking&&answer_j_correct">Dobrze</span>
          <span class="red"
                v-if="checking&&!answer_j_correct">Źle</span></label><br>
      </div>

    </div>

    <h1 style="color: green" v-if="answer_a_correct&&answer_b_correct&&answer_c_correct&&answer_d_correct&&answer_e_correct&&answer_f_correct&&answer_g_correct&&answer_h_correct&&answer_i_correct&&answer_j_correct">
      Gratulacje</h1>

    <div class="desktop">
      <button @click="load(-1)" style="font-size: 16px;" class="button ">Wstecz</button>
      <b style="margin-left: 4px; margin-right: 4px;">{{ i + 1 }}</b>
      <button @click="load(1)" style="font-size: 16px;" class="button">Dalej</button>
      <button @click="check" style="font-size: 16px; margin-right: 12px;" class="button style-accent">Sprawdź</button>
    </div>

    <div class="controls mobile">
      <button @click="load(-1)" style="font-size: 16px;" class="button ">Wstecz</button>
      <b style="margin-left: 4px; margin-right: 4px;">{{ i + 1 }}</b>
      <button @click="load(1)" style="font-size: 16px;" class="button">Dalej</button>
      <button @click="check" style="font-size: 16px; margin-right: 12px;" class="button style-accent">Sprawdź</button>
    </div>
  </div>
</template>

<script>
const questions = require('../assets/questions.json');


function shuffleArray(array) {
  for (let i = array.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    const temp = array[i];
    array[i] = array[j];
    array[j] = temp;
  }
}

export default {
  name: 'HelloWorld',
  data() {
    return {
      question: {},
      answer_a_selected: false,
      answer_b_selected: false,
      answer_c_selected: false,
      answer_d_selected: false,
      answer_e_selected: false,
      answer_f_selected: false,
      answer_g_selected: false,
      answer_h_selected: false,
      answer_i_selected: false,
      answer_j_selected: false,
      answer_a_correct: false,
      answer_b_correct: false,
      answer_c_correct: false,
      answer_d_correct: false,
      answer_e_correct: false,
      answer_f_correct: false,
      answer_g_correct: false,
      answer_h_correct: false,
      answer_i_correct: false,
      answer_j_correct: false,
      checking: false,
      questions,
      i: 0,
      answered_correctly: 0,
      answered: 0,
      counted: false
    };
  },
  mounted() {
    shuffleArray(this.questions);
    this.load(0);
    document.title = `Tkankowa Quiz (${this.questions.length} pytania)`;
  },
  methods: {
    load(direction = 1) {
      this.counted = false;
      this.i = Math.max(this.i + direction, 0);
      this.question = questions[this.i];
      const pairs = [];
      this.answer_a_correct = false;
      this.answer_b_correct = false;
      this.answer_c_correct = false;
      this.answer_d_correct = false;
      this.answer_e_correct = false;
      this.answer_f_correct = false;
      this.answer_g_correct = false;
      this.answer_h_correct = false;
      this.answer_i_correct = false;
      this.answer_j_correct = false;
      this.answer_a_selected = false;
      this.answer_b_selected = false;
      this.answer_c_selected = false;
      this.answer_d_selected = false;
      this.answer_e_selected = false;
      this.answer_f_selected = false;
      this.answer_g_selected = false;
      this.answer_h_selected = false;
      this.answer_i_selected = false;
      this.answer_j_selected = false;
      this.checking = false;
      if (this.i > this.questions.length - 1) {
        if (this.answered_correctly < 18) {
          alert('Ojoj! Chyba będzie poprawka...');
        } else {
          alert('Czas na piwo!');
        }
        return;
      }
      
      // Add existing answers to pairs array
      if (this.question['answer_a'] !== undefined) {
        pairs.push([this.question['answer_a'], this.question['answer_a_correct']]);
      } else {
        this.question['answer_a'] = '';
        this.question['answer_a_correct'] = false;
      }
      
      if (this.question['answer_b'] !== undefined) {
        pairs.push([this.question['answer_b'], this.question['answer_b_correct']]);
      } else {
        this.question['answer_b'] = '';
        this.question['answer_b_correct'] = false;
      }
      
      if (this.question['answer_c'] !== undefined) {
        pairs.push([this.question['answer_c'], this.question['answer_c_correct']]);
      } else {
        this.question['answer_c'] = '';
        this.question['answer_c_correct'] = false;
      }
      
      if (this.question['answer_d'] !== undefined) {
        pairs.push([this.question['answer_d'], this.question['answer_d_correct']]);
      } else {
        this.question['answer_d'] = '';
        this.question['answer_d_correct'] = false;
      }
      
      if (this.question['answer_e'] !== undefined) {
        pairs.push([this.question['answer_e'], this.question['answer_e_correct']]);
      } else {
        this.question['answer_e'] = '';
        this.question['answer_e_correct'] = false;
      }
      
      if (this.question['answer_f'] !== undefined) {
        pairs.push([this.question['answer_f'], this.question['answer_f_correct']]);
      } else {
        this.question['answer_f'] = '';
        this.question['answer_f_correct'] = false;
      }
      
      if (this.question['answer_g'] !== undefined) {
        pairs.push([this.question['answer_g'], this.question['answer_g_correct']]);
      } else {
        this.question['answer_g'] = '';
        this.question['answer_g_correct'] = false;
      }
      
      if (this.question['answer_h'] !== undefined) {
        pairs.push([this.question['answer_h'], this.question['answer_h_correct']]);
      } else {
        this.question['answer_h'] = '';
        this.question['answer_h_correct'] = false;
      }
      
      if (this.question['answer_i'] !== undefined) {
        pairs.push([this.question['answer_i'], this.question['answer_i_correct']]);
      } else {
        this.question['answer_i'] = '';
        this.question['answer_i_correct'] = false;
      }
      
      if (this.question['answer_j'] !== undefined) {
        pairs.push([this.question['answer_j'], this.question['answer_j_correct']]);
      } else {
        this.question['answer_j'] = '';
        this.question['answer_j_correct'] = false;
      }
      
      shuffleArray(pairs);
      
      // Assign shuffled answers back to question
      for (let i = 0; i < pairs.length; i++) {
        const letter = String.fromCharCode(97 + i); // 97 is ASCII for 'a'
        this.question[`answer_${letter}`] = pairs[i][0];
        this.question[`answer_${letter}_correct`] = pairs[i][1];
      }
      
      // Set remaining answers to empty
      for (let i = pairs.length; i < 10; i++) {
        const letter = String.fromCharCode(97 + i);
        this.question[`answer_${letter}`] = '';
        this.question[`answer_${letter}_correct`] = false;
      }
    },
    check() {
      this.answer_a_correct = this.answer_a_selected === this.question['answer_a_correct'];
      this.answer_b_correct = this.answer_b_selected === this.question['answer_b_correct'];
      this.answer_c_correct = this.answer_c_selected === this.question['answer_c_correct'];
      this.answer_d_correct = this.answer_d_selected === this.question['answer_d_correct'];
      this.answer_e_correct = this.answer_e_selected === this.question['answer_e_correct'];
      this.answer_f_correct = this.answer_f_selected === this.question['answer_f_correct'];
      this.answer_g_correct = this.answer_g_selected === this.question['answer_g_correct'];
      this.answer_h_correct = this.answer_h_selected === this.question['answer_h_correct'];
      this.answer_i_correct = this.answer_i_selected === this.question['answer_i_correct'];
      this.answer_j_correct = this.answer_j_selected === this.question['answer_j_correct'];
      this.checking = true;
      
      // Check if all answers are correct
      const allCorrect = 
        this.answer_a_correct &&
        this.answer_b_correct &&
        this.answer_c_correct &&
        this.answer_d_correct &&
        this.answer_e_correct &&
        this.answer_f_correct &&
        this.answer_g_correct &&
        this.answer_h_correct &&
        this.answer_i_correct &&
        this.answer_j_correct;
        
      if (allCorrect && !this.counted) {
        this.answered_correctly++;
      }
      
      if (!this.counted) {
        this.answered++;
      }
      
      this.counted = true;
    }
  }
}
</script>

<style>
input[type=checkbox] {
  /*margin-right: 12px;*/
}

.green {
  color: green;
}

.red {
  color: red;
}

.blue {
  color: royalblue;
}

.controls {
  position: fixed;
  bottom: 0;
  right: 0;
  margin-right: 12px;
  margin-bottom: 12px;
  z-index: 100;
}

.mobile {
  display: none;
}

@media only screen and (max-width: 768px) {
  .mobile {
    display: block;
  }
}

.desktop {
  display: none;
}

@media only screen and (min-width: 768px) {
  .desktop {
    display: block;
  }
}
</style>
