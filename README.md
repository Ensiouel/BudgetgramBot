#PSQL Генераторы
- b_categories
- b_chat_settings
- b_subcategories
- b_transactions
- b_user_actions

# Таблица `b_categories`
```
CREATE TABLE b_categories (
    id      SERIAL PRIMARY KEY, -- Идентификатор категории
    chat_id BIGINT,             -- Идентификатор чата
    "limit" BIGINT,             -- Лимит категории
    type    INTEGER,            -- Тип категории
    title   TEXT,               -- Название категории
    icon    TEXT,               -- Ярлык категории
    UNIQUE (chat_id, title)
);
```

# Таблица `b_chat_settings`
```
CREATE TABLE b_chat_settings (
    chat_id BIGINT, -- Идентификатор чата
    lang_code TEXT, -- Код языка локализации
    curr_code TEXT, -- Код валюты
    UNIQUE (chat_id)
);
```

# Таблица `b_subcategories`
```
CREATE TABLE b_subcategories (
    id          SERIAL PRIMARY KEY, -- Идентификатор подкатегории
    chat_id     BIGINT,             -- Идентификатор чата
    category_id INTEGER,            -- Идентификатор категории
    title       TEXT,               -- Название подкатегории
    UNIQUE (chat_id, title)
);
```

# Таблица `b_transactions`
```
CREATE TABLE b_transactions (
    id          SERIAL PRIMARY KEY, -- Идентификатор транзакции
    chat_id     BIGINT,             -- Идентификатор чата
    category_id INTEGER,            -- Идентификатор категории
    amount      BIGINT,             -- Сумма транзакции
    date        DATE,               -- Дата транзакции
    comment     TEXT                -- Комментарий к транзакции
);
```

# Таблица `b_user_actions`
```
CREATE TABLE b_user_actions (
    chat_id        BIGINT,  -- Идентификатор чата
    user_id        BIGINT,  -- Идентификатор пользователя
    callback_data  TEXT,    -- Данные, переданные через Сallback пользователем
    waiting_action BOOLEAN, -- Ожидает ли пользователь обработки Сallback
    UNIQUE (chat_id, user_id)
);
```