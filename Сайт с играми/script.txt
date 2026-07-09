// Простое логирование для отладки
console.log('🏠 Главное меню игр для пары');
console.log('Доступны игры: "Это или то?" и "200 вопросов"');

// Можно добавить обработку кликов для аналитики (необязательно)
document.querySelectorAll('.card').forEach(card => {
    card.addEventListener('click', function(e) {
        // Не мешаем переходу по ссылке
        const gameName = this.querySelector('h2')?.textContent || 'неизвестная игра';
        console.log(`🕹️ Выбрана игра: ${gameName}`);
    });
});