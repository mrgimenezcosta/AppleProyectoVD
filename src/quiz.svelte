<script>
  let selectedAnswer = '';
  let isCorrect = null;

  const question = "Si hubieras comprado una acción de Apple en 1980, a $22, hoy a cuánto crees que estaría valuada?";
  const answers = [
    { text: "22 dólares", value: "22" },
    { text: "11.234 dólares", value: "11234" },
    { text: "46.368 dólares", value: "46368" }
  ];
  const correctAnswer = "46368";

  function checkAnswer() {
    isCorrect = selectedAnswer === correctAnswer;
  }
</script>

<style>
  .quiz-container {
    position: relative;
    z-index: 1;
    display: inline-block;
    padding: 40px;
    border: 2px solid transparent; 
    border-radius: 15px;
    font-family: Roboto, 'Helvetica', sans-serif;
    font-weight: bold;
    max-width: 600px;
    margin: 20px auto;
  }

  .quiz-container::before {
    content: '';
    position: absolute;
    top: -15px;
    left: -15px;
    right: -15px;
    bottom: -15px;
    border: 2px solid transparent;
    border-color: white;
    z-index: -1;
    border-radius: 15px;
  }

  .question {
    font-size: 24px;
    margin-bottom: 20px;
  }

  .answers {
    margin-bottom: 20px;
  }

  .answers label {
    display: block;
    margin-bottom: 10px;
    font-size: 20px;
  }

  .button {
    display: inline-block;
    padding: 10px 20px;
    font-size: 18px;
    color: #ffffff;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }

  .button:hover {
    background-color: #7706b9;
  }

  .result {
    font-size: 22px;
    font-weight: bold;
    margin-top: 20px;
  }
</style>

<div class="quiz-container">
  <p class="question">{question}</p>
  <div class="answers">
    {#each answers as answer}
      <label>
        <input type="radio" bind:group={selectedAnswer} value={answer.value} />
        {answer.text}
      </label>
    {/each}
  </div>
  <button class="button" on:click={checkAnswer}>Submit</button>
  {#if isCorrect !== null}
    <p class="result">{isCorrect ? '¡Correcto!' : 'Incorrecto. La respuesta correcta es 46.368 dólares.'}</p>
  {/if}
</div>
