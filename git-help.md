# RMP_KISP_24_Lastin_MD

курс: Рзаработка мобильных приложений (очное) для групп КИСП

<!-- https://github.com/ -->

# Основы git 

# **1. Создать аккаунт или Авторизоватся в git

2. Создать репозиторий для предмета РазрМобильПрилож

# **Пример:**

      -RMP_KISP_24_Lastin_MD
# **3. Клонировать репозиторий к себе на компьютер** 

```git clone ссылка на репозиторий тип https```

# **4. Сделать первый коммит в репозиторий и отправить изменения в репозиторий в README.md**

``` -Проверить в терминале находитесь ли вы в своей директории 

    ``` cd [путь к папке склонированного репозитория] ```

- git status - просмотр статуса на изменения 
- git add [путь к изменению файлу] - добавить на коммит определенный файл
- git add . -добавить на коммит все изменения

-git commit -m "Some message" - Коммит добавленных файлов на отправку
- git push origin main - Отправка коммита на определенную ветку
- git push - отправка изменений в текущую ветку 
```

# **5. Отправить в репозиторий файл .gitignore**

# See https://help.github.com/articles/ignoring-files/ for more about ignoring files.


# dependencies
/node_modules
/.pnp
.pnp.js


# testing
/coverage


# next.js
/.next/
/out/


# production
/build


# misc
.DS_Store
*.pem


# debug
npm-debug.log*
yarn-debug.log*
yarn-error.log*


# local env files
.env*.local
.env


# vercel
.vercel


# typescript
*.tsbuildinfo
next-env.d.ts

# Node.js (зависимости и логи)
package-lock.json
yarn.lock
pnpm-lock.yaml

# Архивы и файлы сборки React Native
.expo/
.metro/
dist/

# Android-специфичные файлы
android/app/build/
android/.gradle/
android/local.properties
android/generated/
*.iml
.idea/

# iOS-специфичные файлы
ios/build/
ios/DerivedData/
ios/Pods/
ios/.xcode.env.local
*.xcworkspace
*.xcuserstate
*.lock

# Конфиденциальные данные и ключи (ВАЖНО)
*.keystore
*.jks
google-services.json
GoogleService-Info.plist

# Операционная система
Thumbs.db
