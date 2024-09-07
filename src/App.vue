<script setup>
</script>

<template>
  <div class="d-flex upper-bg-frame">
    <div class="d-flex flex-column content-container">
      <h1 class="header-text">ToDo List Scloud</h1>
      <div class="d-flex flex-row current-task-n-add-task-block">
        <div class="d-flex flex-column current-task-block">
          <div class="current-task-n-add-task-text">
            Текущие задачи
          </div>
          <div class="d-flex flex-row open-in-progress-closed-task-block">
            <div class="d-flex flex-row open-in-progress-closed-task-item">
              <img class="open-in-progress-closed-task-item-img" src="/blue-info.svg" alt="info_icon">
              <div class="open-in-progress-closed-task-item-text">Открыто - x</div>
            </div>
            <div class="d-flex flex-row open-in-progress-closed-task-item">
              <img class="open-in-progress-closed-task-item-img" src="/orange-info.svg" alt="info_icon">
              <div class="open-in-progress-closed-task-item-text">В работе - x</div>
            </div>
            <div class="d-flex flex-row open-in-progress-closed-task-item">
              <img class="open-in-progress-closed-task-item-img" src="/green-info.svg" alt="info_icon">
              <div class="open-in-progress-closed-task-item-text">Закрыто - x</div>
            </div>
          </div>
        </div>
        <div class="d-flex flex-column add-task-block">
          <div class="current-task-n-add-task-text">
            Добавить задачу
          </div>
          <div class="d-flex flex-row add-task-n-task-input-block">
            <button class="d-flex add-task-button">
              <img class="add-task-button-img" src="/add-task-cross.svg" alt="cross_icon">
            </button>
            <input class="add-task-input" type="search" placeholder="Текст">
          </div>
        </div>
      </div>
      <div class="d-flex flex-column task-n-status-block">
        <div class="d-flex flex-row task-n-status-block-head-text">
          <div>Задачи</div>
          <div>Статус</div>
        </div>
        <div class="d-flex flex-column task-n-status-list-block">
          <div class="d-flex flex-row task-n-status-list-text-n-button-block">
            <div class="task-n-status-list-text">Проснуться, улыбнуться, сделать отжимания, слетать на Марс и прочитать книгу</div>
            <div class="d-flex task-n-status-list-button-wrapper">
              <button class="task-n-status-list-button">
                Открыт
              </button>
            </div>
          </div>
          <div class="task-n-status-list-separator"></div>
          <div class="d-flex flex-row task-n-status-list-text-n-button-block">
            <div class="task-n-status-list-text">Проснуться, улыбнуться, сделать отжимания, слетать на Марс и прочитать книгу</div>
            <div class="d-flex task-n-status-list-button-wrapper">
              <button class="task-n-status-list-button">
                Закрыт
              </button>
            </div>
          </div>
          <div class="task-n-status-list-separator"></div>
          <div class="d-flex flex-row task-n-status-list-text-n-button-block">
            <div class="task-n-status-list-text">Проснуться, улыбнуться, сделать отжимания, слетать на Марс и прочитать книгу</div>
            <div class="d-flex task-n-status-list-button-wrapper">
              <button class="task-n-status-list-button">
                В работе
              </button>
            </div>
          </div>
          <div class="task-n-status-list-separator"></div>
          <div class="d-flex flex-row task-n-status-list-text-n-button-block">
            <div class="task-n-status-list-text">Проснуться, улыбнуться, сделать отжимания, слетать на Марс и прочитать книгу</div>
            <div class="d-flex task-n-status-list-button-wrapper">
              <button class="task-n-status-list-button">
                В работе
              </button>
            </div>
          </div>
          <div class="task-n-status-list-separator"></div>
          <div class="d-flex flex-row task-n-status-list-text-n-button-block">
            <div class="task-n-status-list-text">Проснуться, улыбнуться, сделать отжимания, слетать на Марс и прочитать книгу</div>
            <div class="d-flex task-n-status-list-button-wrapper">
              <button class="task-n-status-list-button">
                В работе
              </button>
            </div>
          </div>
        </div>
      </div>
      <button class="d-flex flex-row show-more-tasks-button">
        Показать ещё
        <img class="show-icon" src="/show-hide-icon.svg" alt="show_hide_icon">
      </button>
    </div>
  </div>
  <div class="d-flex flex-column content-container">
    <h2 class="header-text">Доска задач</h2>
    <div class="d-flex flex-row task-desk-block">
      <div class="d-flex flex-column task-desk-item-block">
        <div class="d-flex task-desk-item-label">Открыто</div>
        <div class="d-flex flex-column task-desk-item-list-block">
          <div class="task-desk-item-in-list" draggable="true">
            Проснуться, улыбнуться, сделать отжимания, слетать на Марс и прочитать книгу
          </div>
          <div class="task-desk-item-in-list" draggable="true">
            Проснуться, улыбнуться, сделать отжимания, слетать на Марс и прочитать книгу
          </div>
          <div class="task-desk-item-in-list" draggable="true">
            Проснуться, улыбнуться, сделать отжимания, слетать на Марс и прочитать книгу
          </div>
        </div>
      </div>
      <div class="d-flex flex-column task-desk-item-block">
        <div class="d-flex task-desk-item-label">В работе</div>
        <div class="d-flex flex-column task-desk-item-list-block">
          <div class="task-desk-item-in-list" draggable="true">
            Проснуться, улыбнуться, сделать отжимания, слетать на Марс и прочитать книгу
          </div>
          <div class="task-desk-item-in-list" draggable="true">
            Проснуться, улыбнуться, сделать отжимания, слетать на Марс и прочитать книгу
          </div>
        </div>
      </div>
      <div class="d-flex flex-column task-desk-item-block">
        <div class="d-flex task-desk-item-label">Закрыто</div>
        <div class="d-flex flex-column task-desk-item-list-block">
          <div class="task-desk-item-in-list" draggable="true">
            Проснуться, улыбнуться, сделать отжимания, слетать на Марс и прочитать книгу
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="footer-block"></div>
</template>
