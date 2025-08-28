# OTA iOS App Distribution на Vercel

Проект для распространения iOS-приложений по воздуху (OTA) через бесплатный хостинг Vercel с автоматическим HTTPS.

## 🚀 Преимущества Vercel

- ✅ **Бесплатный хостинг** - до 100GB трафика в месяц
- ✅ **Автоматический HTTPS** - доверенный SSL-сертификат
- ✅ **Глобальная CDN** - быстрая загрузка по всему миру
- ✅ **Простое развертывание** - через GitHub или CLI
- ✅ **Соответствие требованиям Apple** - HTTPS обязателен для OTA

## 📋 Требования Apple для OTA-установок

Согласно [официальной документации Apple](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Introduction/Introduction.html):

1. **HTTPS обязателен** - Apple требует SSL/TLS сертификат
2. **Правильные MIME-типы**:
   - `.ipa` → `application/octet-stream`
   - `.plist` → `text/xml`
3. **Валидный manifest.plist** - строгая структура XML
4. **Доверенный сертификат** - не самоподписанный

## 🛠️ Установка и развертывание

### Шаг 1: Подготовка файлов

1. **Создайте папку проекта:**
```bash
mkdir ota-ios-server
cd ota-ios-server
```

2. **Скопируйте все файлы из этого проекта**

3. **Замените плейсхолдеры в файлах:**
   - `manifest.plist` - замените `[YOUR_VERCEL_DOMAIN]`, `[BUNDLE_IDENTIFIER]`, `[BUNDLE_VERSION]`, `[APP_TITLE]`
   - `install.html` - замените `[YOUR_VERCEL_DOMAIN]`

### Шаг 2: Установка Vercel CLI

```bash
npm install -g vercel
```

### Шаг 3: Развертывание

```bash
# Войдите в аккаунт Vercel
vercel login

# Разверните проект
vercel

# Для продакшена
vercel --prod
```

### Шаг 4: Настройка домена

После развертывания Vercel даст вам URL вида:
`https://your-project.vercel.app`

Замените `[YOUR_VERCEL_DOMAIN]` на этот URL во всех файлах.

## 📱 Установка на iPhone

1. **Откройте Safari на iPhone**
2. **Перейдите по адресу:** `https://your-project.vercel.app/install.html`
3. **Нажмите "Установить приложение"**
4. **Разрешите установку в диалоге**

## 🔧 Структура проекта

```
/
├── app.ipa              # Ваше iOS приложение
├── manifest.plist       # Манифест для OTA-установки
├── install.html         # Страница установки
├── icon.png            # Иконка приложения (512x512)
├── vercel.json         # Конфигурация Vercel
├── package.json        # Зависимости проекта
└── README_VERCEL.md    # Эта инструкция
```

## 📋 Настройка manifest.plist

Замените следующие плейсхолдеры:

```xml
<key>bundle-identifier</key>
<string>com.yourcompany.yourapp</string>

<key>bundle-version</key>
<string>1.0.0</string>

<key>title</key>
<string>Название вашего приложения</string>

<key>subtitle</key>
<string>Описание приложения</string>
```

## 🔍 Проверка работоспособности

1. **Проверьте HTTPS:** `https://your-project.vercel.app`
2. **Проверьте манифест:** `https://your-project.vercel.app/manifest.plist`
3. **Проверьте IPA:** `https://your-project.vercel.app/app.ipa`

## 🛠️ Устранение неполадок

### Ошибка "Cannot connect to iTunes Store"
- Убедитесь, что manifest.plist доступен по HTTPS
- Проверьте правильность структуры XML
- Убедитесь, что bundle-identifier соответствует вашему приложению

### Приложение не устанавливается
- Проверьте, что у вас есть профиль разработчика
- Настройки → Основные → Управление устройством → Доверьте профилю
- Убедитесь, что IPA-файл подписан правильно

### Ошибки MIME-типов
- Проверьте конфигурацию в `vercel.json`
- Убедитесь, что файлы имеют правильные расширения

## 📊 Мониторинг

Vercel предоставляет:
- Статистику трафика
- Логи ошибок
- Аналитику производительности

## 🔒 Безопасность

- HTTPS шифрование
- Автоматическое обновление сертификатов
- Защита от DDoS-атак
- Глобальная CDN

## 💰 Стоимость

- **Бесплатный план:** 100GB трафика/месяц
- **Pro план:** $20/месяц для большего трафика

## 📞 Поддержка

- [Документация Vercel](https://vercel.com/docs)
- [Документация Apple OTA](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Introduction/Introduction.html)
- [Vercel Community](https://github.com/vercel/vercel/discussions)
