**System design социальной сети для путешественников для курса System Design**
gfhgfghfhghg
ФТ:

- публикация постов из путешествий с фотографиями, небольшим описанием и привязкой к конкретному месту путешествия;
- оценка и комментарии постов других путешественников;
- подписка на других путешественников, чтобы следить за их активностью;
- поиск популярных мест для путешествий и просмотр постов с этих мест в виде ТОПа мест по странам и городам;
- общение с другими путешественниками в личных сообщениях;
- просмотр ленты других путешественников;

НФТ:
10 000 000 DAU

1 пользователь 1 пост в день создает
1 пользователь смотрит 30 постов в день
Запись к чтению = 1 к 30 (пост)

1 пользователь пишет 10 сообщений в день
1 пользователь читает 20 сообщений в день (чат/под постом)


публикация за 1 секунду
доступность 99,95%
география СНГ (*на зарубежный рынок выходить планов нет*)
надежность
удобно взаимодействовать, используя мобильные устройства и браузер
данные храним всегда / срок хранения публикации бессрочно
сезонность, пик отпусков - лето



Расчеты
Расчет RPS (чтение)
RPS = dau * avg_requests_per_day_by_user / 86 400 
RPS = 10 000 000 * (30 + 20)  / 86 400  ~ 6 000 RPS
/**Вопрос** = как можно предположить сколько запросов генерирует пользователь? он может смотреть фотки каждую минуту, а может создавать пост 1 раз в день. какую цифру брать? 

Расчет трафика
Traffic = rps * avg_request_size = 6 000 RPS * 10 МБ = 60 000 МБ/с

/**Вопрос** = как считать средний размер запроса? если это просто запрос посомтреть публиакцию? а если сохранить публикацию?а елси поделиться, то другой размер? или например, общение это совсем другой размер запроса. публикация = это картинка + текст + коммнетарии + тег страна. Пост/сообщение или публикация?. Возьмем пост, у которого есть комментарий и сообщение = 10МБ. Тут считаем на запись или на чтение?

Расчет одновременных соединений
Connections = dau * 0.1 = 10 000 000 *  0.1 = 1 000 000

**Вопрос:**
почему в примере в расечтах етсь учет "Service operation time = 5 лет"? а также расчет памяти "Required memory:"?
а в формулах нет https://eminent-gondola-98d.notion.site/ad659278b5304431b57b5791af1b25cd?


Расчет дисков, для хранения постов на ближайший год


