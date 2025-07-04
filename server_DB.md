## Таблица `aggregates`
| Поле | Тип | Описание |
|------|-----|----------|
| aggregate_id | uuid | Уникальный идентификатор агрегата (PK) |
| parent_id | uuid | Идентификатор родительского агрегата (FK) |
| company_id | uuid | Идентификатор компании (FK) |
| unit_code | character varying | Код единицы |
| from_aggregate | boolean | Флаг "из агрегата" (по умолчанию false) |
| status | character varying | Статус |
| report_id | uuid | Идентификатор отчета |
| error_reason | text | Причина ошибки |
| user_id | uuid | Идентификатор пользователя (FK) |
| deletion_mark | boolean | Флаг удаления (по умолчанию false) |
| inserted_at | timestamp | Дата создания записи |
| updated_at | timestamp | Дата обновления записи |
| disaggregated | boolean | Флаг разбора (по умолчанию false) |
| disaggregate_report_id | uuid | Идентификатор отчета о разборе |
| group | boolean | Флаг группы (по умолчанию false) |
| crypto_tail | character varying | Криптохвост |
| crypto_deleted | boolean | Флаг криптоудаления (по умолчанию false) |
| prod_report_id | uuid | Идентификатор производственного отчета (FK) |
| prod_order_id | uuid | Идентификатор производственного заказа (FK) |
| report_status | character varying | Статус отчета |
| weight | integer | Вес |

## Таблица `aggregates_buffer`
| Поле | Тип | Описание |
|------|-----|----------|
| aggregate_id | uuid | Идентификатор агрегата (FK) |
| code | character varying | Код |
| inserted_at | timestamp | Дата создания записи |
| updated_at | timestamp | Дата обновления записи |

## Таблица `codes`
| Поле | Тип | Описание |
|------|-----|----------|
| code_id | uuid | Уникальный идентификатор кода (PK) |
| company_id | uuid | Идентификатор компании (FK) |
| order_id | uuid | Идентификатор заказа (FK) |
| gtin | character varying | GTIN код |
| code | character varying | Код |
| crypto_tail | character varying | Криптохвост |
| crypto_deleted | boolean | Флаг криптоудаления (по умолчанию false) |
| weight | integer | Вес |
| prod_report_id | uuid | Идентификатор производственного отчета (FK) |
| aggregate_id | uuid | Идентификатор агрегата (FK) |
| dropout_id | uuid | Идентификатор выбытия (FK) |
| exp_date | timestamp | Срок годности |
| status | character varying | Статус |
| deletion_mark | boolean | Флаг удаления (по умолчанию false) |
| inserted_at | timestamp | Дата создания записи |
| updated_at | timestamp | Дата обновления записи |

## Таблица `companies`
| Поле | Тип | Описание |
|------|-----|----------|
| company_id | uuid | Уникальный идентификатор компании (PK) |
| name | character varying | Название компании |
| inn | character varying | ИНН |
| gln | character varying | GLN код |
| ca_thumbprint | character varying | Отпечаток сертификата |
| ca_pass | character varying | Пароль сертификата |
| ca_thumbprint_order | character varying | Отпечаток сертификата для заказов |
| ca_pass_order | character varying | Пароль сертификата для заказов |
| oms_connection | uuid | Идентификатор подключения ОМС |
| oms_id | uuid | Идентификатор ОМС |
| next_sscc | integer | Следующий SSCC (по умолчанию 0) |
| exchange | boolean | Флаг обмена (по умолчанию false) |
| deletion_mark | boolean | Флаг удаления (по умолчанию false) |
| inserted_at | timestamp | Дата создания записи |
| updated_at | timestamp | Дата обновления записи |
| mcdn_token | character varying | Токен МЧДН |
| order_id | uuid | Идентификатор заказа (FK) |
| participant_id | character varying | Идентификатор участника |
| kpp | character varying | КПП |
| fias_id | character varying | Идентификатор ФИАС |
| address | character varying | Адрес (по умолчанию '') |
| entities_lifetime | integer | Время жизни сущностей (по умолчанию 0) |

## Таблица `company_service_providers`
| Поле | Тип | Описание |
|------|-----|----------|
| company_id | uuid | Идентификатор компании (FK, PK) |
| service_provider_id | uuid | Идентификатор поставщика услуг (FK, PK) |

## Таблица `dropouts`
| Поле | Тип | Описание |
|------|-----|----------|
| dropout_id | uuid | Уникальный идентификатор выбытия (PK) |
| company_id | uuid | Идентификатор компании (FK) |
| reason | character varying | Причина выбытия |
| status | character varying | Статус |
| report_id | uuid | Идентификатор отчета |
| error_reason | text | Причина ошибки |
| user_id | uuid | Идентификатор пользователя (FK) |
| deletion_mark | boolean | Флаг удаления (по умолчанию false) |
| inserted_at | timestamp | Дата создания записи |
| updated_at | timestamp | Дата обновления записи |
| report_status | character varying | Статус отчета |
| successfull_uploaded_date | timestamp | Дата успешной загрузки |

## Таблица `dropouts_buffer`
| Поле | Тип | Описание |
|------|-----|----------|
| code | character varying | Код (PK) |
| company_id | uuid | Идентификатор компании (FK) |
| reason | character varying | Причина |
| user_id | uuid | Идентификатор пользователя (FK) |
| inserted_at | timestamp | Дата создания записи |
| updated_at | timestamp | Дата обновления записи |

## Таблица `emitted_codes`
| Поле | Тип | Описание |
|------|-----|----------|
| company_id | uuid | Идентификатор компании (FK) |
| order_id | uuid | Идентификатор заказа (FK) |
| gtin | character varying | GTIN код |
| code | character varying | Код |
| crypto_tail | character varying | Криптохвост |
| exp_date | timestamp | Срок годности |
| inserted_at | timestamp | Дата создания записи |
| updated_at | timestamp | Дата обновления записи |

## Таблица `labels`
| Поле | Тип | Описание |
|------|-----|----------|
| label_id | uuid | Уникальный идентификатор этикетки (PK) |
| name | character varying | Название |
| content | text | Содержимое |
| package_level | character varying | Уровень упаковки |
| common | boolean | Общая этикетка (по умолчанию false) |
| printer_model_id | uuid | Идентификатор модели принтера (FK) |
| inserted_at | timestamp | Дата создания записи |
| updated_at | timestamp | Дата обновления записи |

## Таблица `orders`
| Поле | Тип | Описание |
|------|-----|----------|
| order_id | uuid | Уникальный идентификатор заказа (PK) |
| report_id | uuid | Идентификатор отчета |
| status | character varying | Статус |
| products | jsonb[] | Массив продуктов |
| company_id | uuid | Идентификатор компании (FK) |
| service_provider_id | uuid | Идентификатор поставщика услуг (FK) |
| user_id | uuid | Идентификатор пользователя (FK) |
| deletion_mark | boolean | Флаг удаления (по умолчанию false) |
| inserted_at | timestamp | Дата создания записи |
| updated_at | timestamp | Дата обновления записи |
| expected_complete_time | timestamp | Ожидаемое время завершения |
| uploaded_at | timestamp | Дата загрузки (по умолчанию '1970-01-01 00:00:00') |

## Таблица `orders_buffers`
| Поле | Тип | Описание |
|------|-----|----------|
| order_id | uuid | Идентификатор заказа (FK) |
| gtin | character varying | GTIN код |
| status | character varying | Статус |
| available_codes | integer | Доступные коды |
| left_in_buffer | integer | Осталось в буфере |
| total_codes | integer | Всего кодов |
| passed_codes | integer | Переданные коды |
| rejection_reason | text | Причина отказа |
| last_block_id | uuid | Идентификатор последнего блока |
| inserted_at | timestamp | Дата создания записи |
| updated_at | timestamp | Дата обновления записи |
| exp_date | timestamp | Срок годности (по умолчанию '1970-01-01 00:00:00') |

## Таблица `packages`
| Поле | Тип | Описание |
|------|-----|----------|
| id | uuid | Уникальный идентификатор (PK) |
| product_id | uuid | Идентификатор продукта (FK) |
| gtin | character varying | GTIN код |
| name | character varying | Название |
| level | character varying | Уровень |
| multiplier | integer | Множитель |
| inserted_at | timestamp | Дата создания записи |
| updated_at | timestamp | Дата обновления записи |
| print_quantity | integer | Количество печатей (по умолчанию 1) |
| inner_gtin | character varying | Внутренний GTIN |

## Таблица `plc`
| Поле | Тип | Описание |
|------|-----|----------|
| plc_id | uuid | Уникальный идентификатор ПЛК (PK) |
| name | character varying | Название |
| external_id | character varying | Внешний идентификатор |
| host | character varying | Хост |
| port | integer | Порт |
| deletion_mark | boolean | Флаг удаления (по умолчанию false) |
| inserted_at | timestamp | Дата создания записи |
| updated_at | timestamp | Дата обновления записи |

## Таблица `plc_lines`
| Поле | Тип | Описание |
|------|-----|----------|
| prod_line_id | uuid | Идентификатор линии (FK, PK) |
| plc_id | uuid | Идентификатор ПЛК (FK, PK) |
| active | boolean | Флаг активности (по умолчанию false) |
| line_number | integer | Номер линии |

## Таблица `plc_typography_codes`
| Поле | Тип | Описание |
|------|-----|----------|
| plc_id | uuid | Идентификатор ПЛК (FK, PK) |
| gtin | character varying | GTIN код (PK) |
| status | character varying | Статус |

## Таблица `printer_job_values`
| Поле | Тип | Описание |
|------|-----|----------|
| prod_line_id | uuid | Идентификатор линии (FK, PK) |
| printer_job_id | uuid | Идентификатор задания печати (FK, PK) |
| values | jsonb | Значения (по умолчанию '[]') |
| deletion_mark | boolean | Флаг удаления (по умолчанию false) |
| inserted_at | timestamp | Дата создания записи |
| updated_at | timestamp | Дата обновления записи |

## Таблица `printer_jobs`
| Поле | Тип | Описание |
|------|-----|----------|
| printer_job_id | uuid | Уникальный идентификатор задания (PK) |
| name | character varying | Название |
| title | character varying | Заголовок |
| deletion_mark | boolean | Флаг удаления (по умолчанию false) |
| inserted_at | timestamp | Дата создания записи |
| updated_at | timestamp | Дата обновления записи |
| fields | jsonb | Поля (по умолчанию '[]') |

## Таблица `printers`
| Поле | Тип | Описание |
|------|-----|----------|
| printer_id | uuid | Уникальный идентификатор (PK) |
| model_id | uuid | Идентификатор модели (FK) |
| name | character varying | Название |
| external_id | character varying | Внешний идентификатор |
| host | character varying | Хост |
| port | integer | Порт |
| deletion_mark | boolean | Флаг удаления (по умолчанию false) |
| print_delay | integer | Задержка печати |

## Таблица `printers_models`
| Поле | Тип | Описание |
|------|-----|----------|
| printer_model_id | uuid | Уникальный идентификатор модели (PK) |
| name | character varying | Название модели |

## Таблица `prod_lines`
| Поле | Тип | Описание |
|------|-----|----------|
| prod_line_id | uuid | Уникальный идентификатор линии (PK) |
| name | character varying | Название |
| external_id | character varying | Внешний идентификатор |
| user_id | uuid | Идентификатор пользователя (FK) |
| inserted_at | timestamp | Дата создания записи |
| updated_at | timestamp | Дата обновления записи |

## Таблица `prod_lines_printers`
| Поле | Тип | Описание |
|------|-----|----------|
| prod_line_id | uuid | Идентификатор линии (FK, PK) |
| printer_id | uuid | Идентификатор принтера (FK, PK) |
| active | boolean | Флаг активности (по умолчанию false) |
| line_number | integer | Номер линии |
| utils_by_print | boolean | Флаг (по умолчанию false) |

## Таблица `prod_lines_scales`
| Поле | Тип | Описание |
|------|-----|----------|
| prod_line_id | uuid | Идентификатор линии (FK, PK) |
| scale_id | uuid | Идентификатор весов (FK, PK) |
| active | boolean | Флаг активности (по умолчанию false) |
| line_number | integer | Номер линии |

## Таблица `prod_order_iterations`
| Поле | Тип | Описание |
|------|-----|----------|
| prod_order_id | uuid | Идентификатор заказа (FK, PK) |
| iteration_id | uuid | Идентификатор итерации (PK) |
| start_date | timestamp | Дата начала |
| finish_date | timestamp | Дата завершения |
| errors | jsonb[] | Ошибки (по умолчанию пустой массив) |
| errors_count | integer | Количество ошибок |

## Таблица `prod_order_log`
| Поле | Тип | Описание |
|------|-----|----------|
| prod_order_id | uuid | Идентификатор заказа (FK) |
| context | character varying | Контекст |
| event | character varying | Событие |
| timestamp | timestamp | Временная метка |
| additional_info | jsonb | Дополнительная информация (по умолчанию '{}') |

## Таблица `prod_orders`
| Поле | Тип | Описание |
|------|-----|----------|
| prod_order_id | uuid | Уникальный идентификатор заказа (PK) |
| company_id | uuid | Идентификатор компании (FK) |
| company_owner_id | uuid | Идентификатор компании-владельца (FK) |
| release_date | timestamp | Дата выпуска |
| start_date | timestamp | Дата начала |
| finish_date | timestamp | Дата завершения |
| prod_date | timestamp | Дата производства |
| prod_date_utc | timestamp | Дата производства (UTC) |
| product_id | uuid | Идентификатор продукта (FK) |
| quantity | integer | Количество |
| exp_date | timestamp | Срок годности |
| exp_date_utc | timestamp | Срок годности (UTC) |
| exp_72 | boolean | Флаг 72 часов (по умолчанию false) |
| batch | character varying | Партия |
| vet_cert | character varying | Ветсертификат |
| status | character varying | Статус |
| user_id | uuid | Идентификатор пользователя (FK) |
| deletion_mark | boolean | Флаг удаления (по умолчанию false) |
| inserted_at | timestamp | Дата создания записи |
| updated_at | timestamp | Дата обновления записи |
| plc | boolean | Флаг ПЛК (по умолчанию false) |
| typography | boolean | Флаг типографии (по умолчанию false) |
| certificate_data | jsonb | Данные сертификата |
| shift | character varying | Смена |
| licence_data | jsonb | Данные лицензии |
| type | character varying | Тип |
| successfull_uploaded_date | timestamp | Дата успешной загрузки |
| comment | character varying | Комментарий (по умолчанию '') |
| alcohol_volume | character varying | Объем алкоголя |
| origin_doc_number | character varying | Номер документа происхождения |
| origin_doc_date | timestamp | Дата документа происхождения |
| upload_variant | character varying | Вариант загрузки (по умолчанию 'AUTOMATIC') |
| label_id | uuid | Идентификатор этикетки (FK) |

## Таблица `prod_orders_buffer`
| Поле | Тип | Описание |
|------|-----|----------|
| code | character varying | Код (PK) |
| prod_order_id | uuid | Идентификатор заказа (FK) |
| inserted_at | timestamp | Дата создания записи |
| updated_at | timestamp | Дата обновления записи |
| weight | integer | Вес |

## Таблица `prod_orders_lines`
| Поле | Тип | Описание |
|------|-----|----------|
| prod_order_id | uuid | Идентификатор заказа (FK, PK) |
| prod_line_id | uuid | Идентификатор линии (FK, PK) |
| line_number | integer | Номер линии (PK) |

## Таблица `prod_orders_packages`
| Поле | Тип | Описание |
|------|-----|----------|
| prod_order_id | uuid | Идентификатор заказа (FK, PK) |
| package_id | uuid | Идентификатор упаковки (FK, PK) |
| line_number | integer | Номер линии (PK) |
| stream | boolean | Флаг потока (по умолчанию false) |
| label_id | uuid | Идентификатор этикетки (FK) |

## Таблица `prod_processing`
| Поле | Тип | Описание |
|------|-----|----------|
| prod_line_id | uuid | Идентификатор линии (FK, PK) |
| prod_order_id | uuid | Идентификатор заказа (FK, PK) |

## Таблица `prod_reports`
| Поле | Тип | Описание |
|------|-----|----------|
| prod_report_id | uuid | Уникальный идентификатор отчета (PK) |
| prod_order_id | uuid | Идентификатор заказа (FK) |
| status | character varying | Статус |
| error_reason | text | Причина ошибки |
| utils_report_id | uuid | Идентификатор служебного отчета |
| introduce_report_id | uuid | Идентификатор вводного отчета |
| send_at | timestamp | Дата отправки |
| deletion_mark | boolean | Флаг удаления (по умолчанию false) |
| inserted_at | timestamp | Дата создания записи |
| updated_at | timestamp | Дата обновления записи |

## Таблица `product_docs`
| Поле | Тип | Описание |
|------|-----|----------|
| product_id | uuid | Идентификатор продукта (FK) |
| type | character varying | Тип документа |
| cert_type | character varying | Тип сертификата |
| number | character varying | Номер |
| date | timestamp | Дата |
| manual | boolean | Ручной ввод (по умолчанию true) |

## Таблица `products`
| Поле | Тип | Описание |
|------|-----|----------|
| product_id | uuid | Уникальный идентификатор продукта (PK) |
| name | character varying | Название |
| gtin | character varying | GTIN код |
| status | character varying | Статус |
| brand | character varying | Бренд |
| company_id | uuid | Идентификатор компании (FK) |
| deletion_mark | boolean | Флаг удаления (по умолчанию false) |
| inserted_at | timestamp | Дата создания записи |
| updated_at | timestamp | Дата обновления записи |
| cert_missing | boolean | Отсутствие сертификата (по умолчанию true) |
| exp_date | character varying | Срок годности |
| need_vetis | boolean | Требуется ВетИС (по умолчанию false) |
| tnved | character varying | ТН ВЭД |
| variable_weight | boolean | Переменный вес (по умолчанию false) |
| tg_name | character varying | Название в системе |
| is_keg | boolean | Флаг кега (по умолчанию false) |
| volume | character varying | Объем |
| need_lic | boolean | Требуется лицензия (по умолчанию false) |
| autoset_permit_docs | boolean | Автоустановка разрешительных документов (по умолчанию false) |

## Таблица `scales`
| Поле | Тип | Описание |
|------|-----|----------|
| scale_id | uuid | Уникальный идентификатор весов (PK) |
| model_id | uuid | Идентификатор модели (FK) |
| name | character varying | Название |
| external_id | character varying | Внешний идентификатор |
| host | character varying | Хост |
| port | integer | Порт |
| deletion_mark | boolean | Флаг удаления (по умолчанию false) |
| by_stab | boolean | Флаг (по умолчанию false) |

## Таблица `scales_models`
| Поле | Тип | Описание |
|------|-----|----------|
| scale_model_id | uuid | Уникальный идентификатор модели (PK) |
| name | character varying | Название модели |

## Таблица `schema_migrations`
| Поле | Тип | Описание |
|------|-----|----------|
| version | bigint | Версия миграции (PK) |
| inserted_at | timestamp | Дата применения миграции |

## Таблица `service_providers`
| Поле | Тип | Описание |
|------|-----|----------|
| service_provider_id | uuid | Уникальный идентификатор поставщика (PK) |
| name | character varying | Название |
| external_id | character varying | Внешний идентификатор |
| address | character varying | Адрес |
| deletion_mark | boolean | Флаг удаления (по умолчанию false) |
| inserted_at | timestamp | Дата создания записи |
| updated_at | timestamp | Дата обновления записи |

## Таблица `users`
| Поле | Тип | Описание |
|------|-----|----------|
| user_id | uuid | Уникальный идентификатор пользователя (PK) |
| username | character varying | Логин |
| first_name | character varying | Имя |
| last_name | character varying | Фамилия |
| company_id | uuid | Идентификатор компании (FK) |
| password_hash | character varying | Хэш пароля |
| api | boolean | API доступ (по умолчанию false) |
| api_token | character varying | API токен |
| prod_line | boolean | Доступ к линии (по умолчанию false) |
| inserted_at | timestamp | Дата создания записи |
| updated_at | timestamp | Дата обновления записи |
| role | character varying | Роль (по умолчанию 'USER') |
