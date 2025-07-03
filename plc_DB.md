# Описание структуры базы данных

## Таблица `aggregates`
| Поле | Тип | Описание |
|------|-----|----------|
| aggregate_id | uuid | Уникальный идентификатор агрегата (PK) |
| parent_id | uuid | Идентификатор родительского агрегата (FK) |
| prod_line_id | uuid | Идентификатор производственной линии (FK) |
| company_id | uuid | Идентификатор компании (FK) |
| unit_code | character varying | Код единицы |
| from_aggregate | boolean | Флаг "из агрегата" (по умолчанию false) |
| status | character varying | Статус (по умолчанию 'NEW') |
| deletion_mark | boolean | Флаг удаления (по умолчанию false) |
| inserted_at | timestamp without time zone | Дата создания записи |
| updated_at | timestamp without time zone | Дата обновления записи |
| group | boolean | Флаг группы (по умолчанию false) |
| prod_order_id | uuid | Идентификатор производственного заказа (FK) |
| lvl | integer | Уровень (по умолчанию 1) |
| tg_name | character varying | Название в системе |
| weight | integer | Вес |

## Таблица `aggregates_buffer`
| Поле | Тип | Описание |
|------|-----|----------|
| code | character varying | Код (PK) |
| inserted_at | timestamp without time zone | Дата создания записи |
| updated_at | timestamp without time zone | Дата обновления записи |
| aggregate_id | uuid | Идентификатор агрегата (FK) |

## Таблица `codes`
| Поле | Тип | Описание |
|------|-----|----------|
| code | character varying | Код (PK) |
| company_id | uuid | Идентификатор компании (FK) |
| gtin | character varying | GTIN код |
| exp_date | timestamp without time zone | Дата истечения срока |
| status | character varying | Статус |
| tg_name | character varying | Название в системе |
| inserted_at | timestamp without time zone | Дата создания записи |
| updated_at | timestamp without time zone | Дата обновления записи |

## Таблица `companies`
| Поле | Тип | Описание |
|------|-----|----------|
| company_id | uuid | Уникальный идентификатор компании (PK) |
| name | character varying | Название компании |
| deletion_mark | boolean | Флаг удаления (по умолчанию false) |
| inserted_at | timestamp without time zone | Дата создания записи |
| updated_at | timestamp without time zone | Дата обновления записи |
| gln | character varying | GLN код |
| participant_id | character varying | Идентификатор участника |

## Таблица `io_bus_models`
| Поле | Тип | Описание |
|------|-----|----------|
| id | uuid | Уникальный идентификатор модели (PK) |
| name | character varying | Название модели |

## Таблица `io_buses`
| Поле | Тип | Описание |
|------|-----|----------|
| id | uuid | Уникальный идентификатор (PK) |
| name | character varying | Название |
| host | character varying | Хост |
| port | integer | Порт |
| external_id | character varying | Внешний идентификатор |
| model_id | uuid | Идентификатор модели (FK) |
| inserted_at | timestamp without time zone | Дата создания записи |
| updated_at | timestamp without time zone | Дата обновления записи |

## Таблица `iterations`
| Поле | Тип | Описание |
|------|-----|----------|
| prod_line_id | uuid | Идентификатор производственной линии (PK, FK) |
| iteration_id | uuid | Идентификатор итерации (PK) |
| iteration_start | timestamp without time zone | Время начала итерации |

## Таблица `labels`
| Поле | Тип | Описание |
|------|-----|----------|
| id | uuid | Уникальный идентификатор (PK) |
| name | character varying | Название |
| printer_model | character varying | Модель принтера |
| scaffold | text | Шаблон (по умолчанию '') |
| fields | ARRAY | Массив полей (по умолчанию пустой массив) |
| inserted_at | timestamp without time zone | Дата создания записи |
| updated_at | timestamp without time zone | Дата обновления записи |

## Таблица `printer_job_values`
| Поле | Тип | Описание |
|------|-----|----------|
| prod_line_id | uuid | Идентификатор производственной линии (PK, FK) |
| printer_job_id | uuid | Идентификатор задания печати (PK, FK) |
| values | jsonb | Значения (по умолчанию '[]') |
| deletion_mark | boolean | Флаг удаления (по умолчанию false) |
| inserted_at | timestamp without time zone | Дата создания записи |
| updated_at | timestamp without time zone | Дата обновления записи |

## Таблица `printer_jobs`
| Поле | Тип | Описание |
|------|-----|----------|
| printer_job_id | uuid | Уникальный идентификатор задания (PK) |
| name | character varying | Название |
| title | character varying | Заголовок |
| deletion_mark | boolean | Флаг удаления (по умолчанию false) |
| inserted_at | timestamp without time zone | Дата создания записи |
| updated_at | timestamp without time zone | Дата обновления записи |
| fields | jsonb | Поля (по умолчанию '[]') |

## Таблица `printer_models`
| Поле | Тип | Описание |
|------|-----|----------|
| printer_model_id | uuid | Уникальный идентификатор модели (PK) |
| name | character varying | Название модели |

## Таблица `printers`
| Поле | Тип | Описание |
|------|-----|----------|
| printer_id | uuid | Уникальный идентификатор (PK) |
| model_id | uuid | Идентификатор модели (FK) |
| name | character varying | Название |
| host | character varying | Хост |
| port | integer | Порт |
| external_id | character varying | Внешний идентификатор |
| deletion_mark | boolean | Флаг удаления (по умолчанию false) |
| inserted_at | timestamp without time zone | Дата создания записи |
| updated_at | timestamp without time zone | Дата обновления записи |

## Таблица `printings`
| Поле | Тип | Описание |
|------|-----|----------|
| prod_order_id | uuid | Идентификатор производственного заказа (PK, FK) |
| label_id | uuid | Идентификатор этикетки (PK, FK) |
| values | ARRAY | Значения (по умолчанию пустой массив) |
| inserted_at | timestamp without time zone | Дата создания записи |
| updated_at | timestamp without time zone | Дата обновления записи |

## Таблица `prod_line_errors`
| Поле | Тип | Описание |
|------|-----|----------|
| id | uuid | Уникальный идентификатор (PK) |
| prod_line_id | uuid | Идентификатор производственной линии (FK) |
| date | timestamp without time zone | Дата ошибки |
| message | text | Сообщение |
| error | text | Ошибка |
| type | character varying | Тип ошибки |
| iteration_id | uuid | Идентификатор итерации (FK) |

## Таблица `prod_lines`
| Поле | Тип | Описание |
|------|-----|----------|
| prod_line_id | uuid | Уникальный идентификатор линии (PK) |
| external_id | character varying | Внешний идентификатор |
| name | character varying | Название |
| deletion_mark | boolean | Флаг удаления (по умолчанию false) |
| inserted_at | timestamp without time zone | Дата создания записи |
| updated_at | timestamp without time zone | Дата обновления записи |
| stop_delay | integer | Задержка остановки (по умолчанию 0) |

## Таблица `prod_lines_io_bus`
| Поле | Тип | Описание |
|------|-----|----------|
| prod_line_id | uuid | Идентификатор линии (PK, FK) |
| io_bus_id | uuid | Идентификатор IO шины (PK, FK) |
| active | boolean | Флаг активности (по умолчанию false) |
| line_number | integer | Номер линии |
| settings | ARRAY | Настройки (по умолчанию пустой массив) |

## Таблица `prod_lines_printers`
| Поле | Тип | Описание |
|------|-----|----------|
| prod_line_id | uuid | Идентификатор линии (PK, FK) |
| printer_id | uuid | Идентификатор принтера (PK, FK) |
| active | boolean | Флаг активности (по умолчанию false) |
| line_number | integer | Номер линии |
| utils_by_print | boolean | Флаг (по умолчанию false) |

## Таблица `prod_lines_scales`
| Поле | Тип | Описание |
|------|-----|----------|
| prod_line_id | uuid | Идентификатор линии (PK, FK) |
| scale_id | uuid | Идентификатор весов (PK, FK) |
| active | boolean | Флаг активности (по умолчанию false) |
| line_number | integer | Номер линии |
| by_stab | boolean | Флаг (по умолчанию false) |

## Таблица `prod_order_log`
| Поле | Тип | Описание |
|------|-----|----------|
| prod_order_id | uuid | Идентификатор заказа (PK, FK) |
| event | character varying | Событие (PK) |
| timestamp | timestamp without time zone | Временная метка (PK) |
| additional_info | jsonb | Дополнительная информация (по умолчанию '{}') |

## Таблица `prod_order_next`
| Поле | Тип | Описание |
|------|-----|----------|
| prod_line_id | uuid | Идентификатор линии (PK, FK) |
| prod_order_id | uuid | Идентификатор следующего заказа (FK) |
| line_number | integer | Номер линии |

## Таблица `prod_orders`
| Поле | Тип | Описание |
|------|-----|----------|
| prod_order_id | uuid | Уникальный идентификатор заказа (PK) |
| release_date | timestamp without time zone | Дата выпуска |
| prod_date | timestamp without time zone | Дата производства |
| exp_date | timestamp without time zone | Срок годности |
| start_date | timestamp without time zone | Дата начала |
| finish_date | timestamp without time zone | Дата завершения |
| status | character varying | Статус |
| quantity | integer | Количество |
| inserted_at | timestamp without time zone | Дата создания записи |
| updated_at | timestamp without time zone | Дата обновления записи |
| typography | boolean | Флаг типографии (по умолчанию false) |
| company_id | uuid | Идентификатор компании (FK) |
| batch | character varying | Партия |
| packages | ARRAY | Упаковки (по умолчанию пустой массив) |
| iteration_id | uuid | Идентификатор итерации (FK) |
| iteration_start | timestamp without time zone | Начало итерации |
| shift | character varying | Смена |
| type | character varying | Тип |
| gtin | character varying | GTIN код |
| comment | character varying | Комментарий (по умолчанию '') |
| label | jsonb | Этикетка |

## Таблица `prod_orders_buffer`
| Поле | Тип | Описание |
|------|-----|----------|
| code | character varying | Код (PK) |
| prod_order_id | uuid | Идентификатор заказа (FK) |
| inserted_at | timestamp without time zone | Дата создания записи |
| updated_at | timestamp without time zone | Дата обновления записи |
| weight | integer | Вес |

## Таблица `prod_orders_lines`
| Поле | Тип | Описание |
|------|-----|----------|
| prod_order_id | uuid | Идентификатор заказа (PK, FK) |
| prod_line_id | uuid | Идентификатор линии (PK, FK) |
| line_number | integer | Номер линии |

## Таблица `prod_processing`
| Поле | Тип | Описание |
|------|-----|----------|
| prod_line_id | uuid | Идентификатор линии (PK, FK) |
| prod_order_id | uuid | Идентификатор заказа (PK, FK) |

## Таблица `products`
| Поле | Тип | Описание |
|------|-----|----------|
| name | character varying | Название (PK) |
| gtin | character varying | GTIN код |
| deletion_mark | boolean | Флаг удаления (по умолчанию false) |
| inserted_at | timestamp without time zone | Дата создания записи |
| updated_at | timestamp without time zone | Дата обновления записи |
| brand | character varying | Бренд |
| variable_weight | boolean | Флаг переменного веса (по умолчанию false) |
| is_keg | boolean | Флаг кега (по умолчанию false) |
| volume | character varying | Объем |
| tg_name | character varying | Название в системе (по умолчанию 'not_set') |

## Таблица `scale_models`
| Поле | Тип | Описание |
|------|-----|----------|
| scale_model_id | uuid | Уникальный идентификатор модели (PK) |
| name | character varying | Название модели |

## Таблица `scales`
| Поле | Тип | Описание |
|------|-----|----------|
| scale_id | uuid | Уникальный идентификатор (PK) |
| model_id | uuid | Идентификатор модели (FK) |
| name | character varying | Название |
| external_id | character varying | Внешний идентификатор |
| host | character varying | Хост |
| port | integer | Порт |
| by_stab | boolean | Флаг (по умолчанию false) |
| deletion_mark | boolean | Флаг удаления (по умолчанию false) |
| inserted_at | timestamp without time zone | Дата создания записи |
| updated_at | timestamp without time zone | Дата обновления записи |

## Таблица `settings`
| Поле | Тип | Описание |
|------|-----|----------|
| slug | character varying | Идентификатор (PK) |
| type | character varying | Тип |
| value | jsonb | Значение |

## Таблица `schema_migrations`
| Поле | Тип | Описание |
|------|-----|----------|
| version | bigint | Версия миграции (PK) |
| inserted_at | timestamp without time zone | Дата применения миграции |
