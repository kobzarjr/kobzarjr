// ========== МАССИВ ВОПРОСОВ (все 200) ==========
const questions = [
    "Какая самая нелепая вещь, которую ты делала, когда думала, что никто не видит?",
    "Если бы ты была героем мультфильма, кем бы ты была?",
    "Твоя самая дурацкая покупка за последний год?",
    // ... и так далее все 200 вопросов (вставьте из предыдущего сообщения)
    "Что бы ты спросила у своей будущей внучки?"
];

// ========== ЛОГИКА ПЕРЕМЕШИВАНИЯ И ВЫДАЧИ ==========
let shuffled = [];
let index = 0;
const questionEl = document.getElementById('question');
const counterEl = document.getElementById('counter');

function shuffleArray(arr) {
    for (let i = arr.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [arr[i], arr[j]] = [arr[j], arr[i]];
    }
    return arr;
}

function reset() {
    shuffled = shuffleArray([...questions]);
    index = 0;
    questionEl.textContent = 'Колода перемешана! Жмите «Получить»';
    questionEl.classList.remove('fade');
    void questionEl.offsetWidth;
    counterEl.textContent = `Осталось: ${shuffled.length}`;
}

function getNext() {
    if (!shuffled.length || index >= shuffled.length) {
        questionEl.textContent = '🎉 Все вопросы кончились! Нажмите «Сброс»';
        counterEl.textContent = 'Осталось: 0';
        questionEl.classList.remove('fade');
        return;
    }
    questionEl.classList.remove('fade');
    void questionEl.offsetWidth;
    questionEl.textContent = shuffled[index];
    questionEl.classList.add('fade');
    index++;
    counterEl.textContent = `Осталось: ${shuffled.length - index}`;
}

// Инициализация
reset();