# Большая языковая модель для рекомендации лекарств при помощи дистилляции знаний

"Large Language Model Distilling Medication Recommendation Model".

1. Приготовить модель LLaMA-7B: установить все файлы модели и переместить их в 'resources/llama-7b/'
2. Подготовить данные: получить данные с официального сайта https://mimic.mit.edu/ и разместить их в `data/mimic3/raw/` и `data/mimic4/` соответственно.
3. Запустить скрипт `construction.ipynb` для обработки данных
4. Установить необходимые пакеты, с помощью команды:
   ```bash
   pip install -r requirements.txt
   ```
5. Обучить большую языковую модель для медицинских рекомендаций:
   ```bash
   bash experiments/llm_cls.bash
   ```
6. Запустить процесс дистилляции знаний:
   ```bash
   bash experiments/mimic3/online_distill.bash
   bash experiments/mimic4/online_distill.bash
   ```
7. Для длительной дистилляции можно предварительно сохранить скрытые состояния из LLM. 
Для этого необходимо запустить тест в файле train, и скрытые состояния будут автоматически сохранены в результатах с помощью нашего "llm_cls.bash`. 
Затем поместите файл результатов в "mimic3/handled/" или "mimic4/handled/", а затем запустите KD в течение двух часов!
   ```bash
   bash experiments/mimic3/offline_distill.bash
   bash experiments/mimic4/offline_distill.bash
   ```
experiments/mimic4/offline_distill.bash
   ```
