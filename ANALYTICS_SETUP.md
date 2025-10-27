# 📊 Google Analytics Setup Instructions

## Крок 1: Створи Google Analytics обліковий запис

1. Зайди на https://analytics.google.com/
2. Увійди зі своїм Google акаунтом
3. Натисни **"Start measuring"** або **"Admin"** → **"Create Property"**

## Крок 2: Налаштуй Property

1. **Account name**: Portfolio (або будь-яка назва)
2. **Property name**: Denys Shtoma Portfolio
3. **Reporting time zone**: Ukraine
4. **Currency**: USD або UAH
5. Натисни **"Next"**

## Крок 3: Налаштуй Data Stream

1. Вибери платформу: **Web**
2. **Website URL**: `https://www.denysshtoma.tech`
3. **Stream name**: Portfolio Website
4. Натисни **"Create stream"**

## Крок 4: Отримай Measurement ID

Після створення побачиш екран з деталями:

```
Measurement ID: G-XXXXXXXXXX
Stream URL: https://www.denysshtoma.tech
```

**Скопіюй Measurement ID!** Він виглядає як `G-ABC123XYZ`

## Крок 5: Додай ID в код

Відкрий файл `index.html` і знайди рядки 11 та 16:

```html
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());
    gtag('config', 'G-XXXXXXXXXX');
</script>
```

**Заміни обидва `G-XXXXXXXXXX` на свій справжній Measurement ID.**

Наприклад, якщо твій ID: `G-ABC123XYZ`, то має вийти:

```html
<script async src="https://www.googletagmanager.com/gtag/js?id=G-ABC123XYZ"></script>
<script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());
    gtag('config', 'G-ABC123XYZ');
</script>
```

## Крок 6: Задеплой зміни

```bash
git add index.html
git commit -m "Add Google Analytics tracking"
git push
```

Почекай 2-3 хвилини поки GitHub Pages оновиться.

## Крок 7: Перевір чи працює

1. Зайди на свій сайт: https://www.denysshtoma.tech
2. Відкрий Google Analytics: https://analytics.google.com/
3. Перейди в **Reports** → **Realtime**
4. Маєш побачити себе як активного користувача!

---

## 📈 Що будеш бачити в Analytics:

- **Кількість відвідувачів** (денних, тижневих, місячних)
- **Звідки приходять** (Google, LinkedIn, прямі заходи)
- **Які сторінки переглядають**
- **Як довго сидять** на сайті
- **З яких країн** заходять
- **З яких пристроїв** (Desktop, Mobile, Tablet)
- **Браузери та ОС**

## 🎯 Корисні звіти:

- **Realtime** - хто зараз на сайті
- **Acquisition** - звідки приходять люди
- **Engagement** - які сторінки найпопулярніші
- **Demographics** - вік, стать, країна, місто

---

## 🆓 Альтернативи (якщо не хочеш Google Analytics):

### Microsoft Clarity (мій улюблений для візуалізації)
- https://clarity.microsoft.com/
- Безкоштовний
- Теплові карти + записи сесій
- Код інтеграції простіший

### Cloudflare Web Analytics
- https://www.cloudflare.com/web-analytics/
- Без cookies
- Privacy-friendly
- Дуже простий

---

Готово! Після заміни ID та деплою — статистика почне збиратися автоматично.
