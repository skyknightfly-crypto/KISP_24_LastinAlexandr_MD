# Обучающее: Использование React Native и Expo

Введение в учебник по React Native о том, как создать универсальное приложение, которое будет работать на Android, iOS и вебе с помощью Expo.

## О React Native и обучающих материалах по Expo

Expo и Expo SDK. В ней будут рассмотрены темы:

Создайте приложение с использованием шаблона по умолчанию с включённым TypeScript
Реализуйте раскладку нижних вкладок с двумя экранами с помощью Expo Router
Разберите макет приложения и реализуйте его с помощью flexbox
Используйте системный интерфейс каждой платформы, чтобы выбрать изображение из медиабиблиотеки
Создайте модаль стикера, используя компоненты и из React Native<Modal><FlatList>
Добавьте жесты касания для взаимодействия с наклейкой
Используйте сторонние библиотеки, чтобы сделать скриншот и сохранить его на диск
Разобраться с различиями платформ между Android, iOS и вебом
Наконец, пройдите процесс настройки строки статуса, заставки и иконки для завершения приложения

Эти темы дают основу для изучения основ создания приложения для Expo. Обучение проходит в собственном темпе и может занять до двух часов.

Чтобы быть удобным для новичков, мы разделили урок на девять глав. Каждая глава содержит необходимые фрагменты кода для выполнения этапов, так что вы можете следить за ним, создавая приложение с нуля или копируя и вставляя его.

В течение учебника любой важный код или код, изменившийся между примерами, будет выделен зелёным цветом. Вы можете навести курсор на выделения (на рабочем столе) или нажать на них (на мобильном), чтобы узнать больше об изменениях. Например, код, выделенный в фрагменте ниже, объясняет, что он делает:

```
import { StyleSheet, Text, View } from 'react-native';
export default function Index() {
  return (
    <View style={styles.container}>
      <Text>Hello world!</Text>
    </View>
  );
}
const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
  },
});
```
## Следующий шаг

# Создайте своё первое приложение

В этой главе давайте узнаем, как создать новый проект Expo и как его запустить.

## Инициализация нового приложения Expo
Мы используем create-expo-app чтобы инициализировать новое приложение Expo. Это командный инструмент для создания нового проекта React Native. Выполните следующую команду в терминале:
```
npx create-expo-app@latest StickerSmash
Select an Expo SDK version > SDK 57
cd StickerSmash
```

Эта команда создаст новую папку проекта под названием StickerSmash, используя шаблон по умолчанию. Этот шаблон содержит необходимый шаблонный код и библиотеки, необходимые для создания нашего приложения, включая Expo Router, и позволяет нам тестировать приложение с установленным Expo Go на наших устройствах. Мы продолжим добавлять новые библиотеки в этом учебнике по мере необходимости.

## Скачать материалы

https://docs.expo.dev/static/images/tutorial/sticker-smash-assets.zip
После скачивания архива:
Распакуйте архив и замените стандартные ассеты в папке your-project-name/assets/images.
Откройте каталог проекта в редакторе кода или IDE.

## Запустить скрипт reset-project
В этом туториале мы создадим приложение с нуля и поймём основы добавления навигации на основе файлов. Давайте запустим скрипт, чтобы удалить шаблонный код:reset-project
```
npm run reset-project
```
После выполнения вышеуказанной команды в папке src/app остаются два файла (index.tsx и _layout.tsx). Предыдущие файлы из каталога src (включая компоненты, константы и крючки) перемещаются внутри папки примера скриптом. По ходу работы мы будем создавать собственные каталоги и компонентные файлы.

## Запустите приложение на мобильных устройствах и вебе

В каталоге проекта выполните следующую команду, чтобы запустить сервер разработки из терминала:
```
npx expo start
```
После выполнения вышеуказанной команды:

Сервер разработки запустится, и вы увидите QR-код внутри окна терминала.
Отсканируйте этот QR-код, чтобы открыть приложение на устройстве. На Android используйте опцию QR-кода Expo Go > Scan. На iOS используйте стандартное приложение камеры.
Чтобы запустить веб-приложение, нажмите в терминале. Веб-приложение откроется в браузере по умолчанию.

## Редактировать экран индекса

Файл src/app/index.tsx определяет текст, отображаемый на экране приложения. Это входная точка нашего приложения и запускается при запуске сервера разработки. Он использует основные компоненты React Native, такие как и для отображения фона и текста.<View><Text>

Стили, применяемые к этим компонентам, используют объекты JavaScript, а не CSS, который используется в вебе. Однако многие свойства будут показаться знакомыми, если вы раньше пользовались CSS в интернете. Большинство компонентов React Native принимают проп, который принимает объект JavaScript в качестве своего значения. Для подробностей см. раздел Стилизация в React Native.style

Давайте изменим экран src/app/index.tsx:

Импортируйте из и создайте объект для определения наших пользовательских стилей.StyleSheetreact-nativestyles
Добавьте свойство с значением . Это меняет цвет фона.styles.container.backgroundColor<View>#25292e
Замените значение по умолчанию на «Главный экран».<Text>
Добавьте свойство с значением (белый) для изменения цвета текста.
```
import { Text, View, StyleSheet } from 'react-native';

export default function Index() {
  return (
    <View style={styles.container}>
      <Text style={styles.text}>Home screen</Text>
    </View>
  );
}
const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#25292e',
    alignItems: 'center',
    justifyContent: 'center',
  },
  text: {
    color: '#fff',
  },
});
```

React Native использует тот же цветовой формат, что и веб. Он поддерживает шестнадцатеричные триплеты (вот что есть), , , и именованные цвета, такие как , , , и . Для получения дополнительной информации см. раздел Colors in React Native.#fffrgbahslredgreenblueperupapayawhip

# Добавить навигацию

В этой главе мы изучим основы Expo Router для создания навигации по стеку и нижней панели вкладок с двумя вкладками.

## Основы Expo Router

Expo Router — это фреймворк маршрутизации на основе файлов для React Native и веб-приложений. Он управляет навигацией между экранами и использует одни и те же компоненты на нескольких платформах. Чтобы начать, нам нужно знать о следующих конвенциях:

Каталог приложений: Специальная директория, содержащая только маршруты и их макеты. Любые файлы, добавленные в эту директорию, становятся экраном внутри нашего нативного приложения и страницей в интернете. В стандартном шаблоне он расположен на src/app.
Корневая верстка: файл src/app/_layout.tsx. Он определяет общие элементы интерфейса, такие как заголовки и панели вкладок, чтобы они были согласованы между разными маршрутами.
Правила имён файлов: Имена индексных файлов, такие как index.tsx, совпадают с родительским каталогом и не добавляют сегмент пути. Например, файл index.tsx в каталоге src/app совпадает с маршрутом./
Файл маршрута экспортирует компонент React в качестве своего значения по умолчанию. Он может использовать либо , , , либо расширение..js.jsx.ts.tsx
Android, iOS и веб имеют единую навигационную структуру.

## Добавьте новый экран в стек

Давайте создадим новый файл с названием about.tsx внутри папки src/app. При навигации пользователя по маршруту отображается имя экрана./about

```
import { Text, View, StyleSheet } from 'react-native';

export default function AboutScreen() {
  return (
    <View style={styles.container}>
      <Text style={styles.text}>About screen</Text>
    </View>
  );
}
const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#25292e',
    justifyContent: 'center',
    alignItems: 'center',
  },
  text: {
    color: '#fff',
  },
});
```
Внутри src/app/_layout.tsx:

Добавьте компонент и проп для обновления названия маршрута.<Stack.Screen />options/about
Обновите название маршрута, добавив проп./indexHomeoptions
```
import { Stack } from 'expo-router';

export default function RootLayout() {
  return (
    <Stack>
      <Stack.Screen name="index" options={{ title: 'Home' }} />
      <Stack.Screen name="about" options={{ title: 'About' }} />
    </Stack>
  );
}
```
## Навигация между экранами
Мы используем компонент Expo Router для навигации от маршрута к маршруту. Это компонент React, который рендерит a с заданным проп.Link/index/about<Text>href

Импортируйте компонент изнутри src/app/index.tsx.Linkexpo-router
Добавляйте компонент за компонентом и пропускайте проп вместе с маршрутом.Link<Text>href/about
Добавьте стиль , и в компонент. Он требует тех же реквизитов, что и компонент.fontSizetextDecorationLinecolorLink<Text>
```
import { Text, View, StyleSheet } from 'react-native';
import { Link } from 'expo-router';

export default function Index() {
  return (
    <View style={styles.container}>
      <Text style={styles.text}>Home screen</Text>
      <Link href="/about" style={styles.button}>
        Go to About screen
      </Link>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#25292e',
    alignItems: 'center',
    justifyContent: 'center',
  },
  text: {
    color: '#fff',
  },
  button: {
    fontSize: 20,
    textDecorationLine: 'underline',
    color: '#fff',
  },
});
```

## Добавьте маршрут, который не найден

Если маршрута нет, мы можем использовать маршрут для отображения экрана запасного варианта. Это полезно, когда мы хотим показывать пользовательский экран при навигации по неправильному маршруту на мобильном устройстве, вместо того чтобы вылетать приложение или отображать ошибку 404 в интернете. Expo Router использует специальный файл +not-found.tsx для обработки этого случая.+not-found

Создайте новый файл с именем +not-found.tsx внутри каталога src/app, чтобы добавить компонент.NotFoundScreen
Добавьте реквизит из кнопки для отображения пользовательского экрана для этого маршрута.optionsStack.Screen
Добавьте компонент для навигации по маршруту, который является нашим запасным маршрутом.Link/
```
import { View, StyleSheet } from 'react-native';
import { Link, Stack } from 'expo-router';

export default function NotFoundScreen() {
  return (
    <>
      <Stack.Screen options={{ title: 'Oops! Not Found' }} />
      <View style={styles.container}>
        <Link href="/" style={styles.button}>
          Go back to Home screen!
        </Link>
      </View>
    </>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#25292e',
    justifyContent: 'center',
    alignItems: 'center',
  },

  button: {
    fontSize: 20,
    textDecorationLine: 'underline',
    color: '#fff',
  },
});
```

## Добавьте навигатор нижней вкладки
На данный момент структура файлов нашего каталога src/app выглядит так:
src ->
   app->
      _layout.tsx               Root layout
      index.tsx            matches route '/'
      about.tsx       matches route '/about'
      +not-found.tsx  matches route any 404 route

Мы добавим навигатор по нижней вкладке в наше приложение и повторно используем существующие экраны «Домой» и «О нас» для создания макета вкладок (распространённый шаблон навигации во многих социальных сетях, таких как X или BlueSky). Мы также используем навигатор стека в корневом макете, чтобы маршрут отображался поверх любых других вложенных навигаторов.+not-found

Внутри каталога src/app добавьте подкаталог (вкладки). Эта специальная директория используется для группировки маршрутов и их отображения в нижней панели вкладок.
Создайте файл (tabs)/_layout.tsx внутри каталога. Он будет использоваться для определения раскладки вкладок, который отличается от корневого макета.
Переместите существующие файлы index.tsx и about.tsx внутри папки (вкладки).
Обновите корневой файл макета, чтобы добавить маршрут:(tabs)
```
import { Stack } from 'expo-router';

export default function RootLayout() {
  return (
    <Stack>
      <Stack.Screen name="(tabs)" options={{ headerShown: false }} />
    </Stack>
  );
}
```

Внутри (tabs)/_layout.tsx добавьте компонент для определения расположения нижней вкладки:Tabs

```
import { Tabs } from 'expo-router';

export default function TabLayout() {
  return (
    <Tabs>
      <Tabs.Screen name="index" options={{ title: 'Home' }} />
      <Tabs.Screen name="about" options={{ title: 'About' }} />
    </Tabs>
  );
}
```
## Установите @expo/vector-icons
Чтобы установить библиотеку, остановите сервер разработки, нажав + в терминале, затем выполните следующую команду:@expo/vector-iconsCtrlC
```
npx expo install @expo/vector-icons
```
После завершения установки запустите сервер разработки заново, запустив .npx expo start
## Обновить внешний вид навигатора в нижней вкладке
Сейчас навигатор нижней вкладки выглядит одинаково на всех платформах, но не соответствует стилю нашего приложения. Например, панель вкладки или заголовок не отображают пользовательский значок, а цвет фона нижней вкладки не совпадает с цветом фона приложения.

Измените файл src/app/(tabs)/_layout.tsx, чтобы добавить значки панели вкладок:

Импортные иконки, установленные из Ionicons@expo/vector-icons — библиотеку, включающую популярные наборы иконок.
Добавьте их в оба маршрута. Эта функция принимает и как параметры и отображает компонент иконок. Из набора иконок мы можем предоставить пользовательские имена иконок.tabBarIconindexaboutfocusedcolor
Добавьте в компонент и установите её значение в . Это меняет цвет значка панели вкладок и метки, когда она активна.screenOptions.tabBarActiveTintColorTabs#ffd33d
```
import { Tabs } from 'expo-router';
import Ionicons from '@expo/vector-icons/Ionicons';

export default function TabLayout() {
  return (
    <Tabs
      screenOptions={{
        tabBarActiveTintColor: '#ffd33d',
      }}
    >
      <Tabs.Screen
        name="index"
        options={{
          title: 'Home',
          tabBarIcon: ({ color, focused }) => (
            <Ionicons name={focused ? 'home-sharp' : 'home-outline'} color={color} size={24} />
          ),
        }}
      />
      <Tabs.Screen
        name="about"
        options={{
          title: 'About',
          tabBarIcon: ({ color, focused }) => (
            <Ionicons name={focused ? 'information-circle' : 'information-circle-outline'} color={color} size={24}/>
          ),
        }}
      />
    </Tabs>
  );
}
```
Давайте также изменим цвет фона панели вкладок и заголовка с помощью пропа:screenOptions
```
<Tabs
  screenOptions={{
    tabBarActiveTintColor: '#ffd33d',
    headerStyle: {
      backgroundColor: '#25292e',
    },
    headerShadowVisible: false,
    headerTintColor: '#fff',
    tabBarStyle: {
      backgroundColor: '#25292e',
    },
  }}
>
```
В приведённом выше коде:

Фон заголовка установлен на использование свойства. Мы также отключили тень заголовка с помощью .#25292e  headerStyle  headerShadowVisible
headerTintColor применяется к метке заголовка #fff
tabBarStyle.backgroundColor применяется к полосе вкладки #25292e

# Постройте экран
В этой главе мы создадим первый экран приложения StickerSmash.
На экране выше отображается изображение и две кнопки. Пользователь приложения может выбрать изображение с помощью одной из двух кнопок. Первая кнопка позволяет пользователю выбрать изображение с устройства. Вторая кнопка позволяет пользователю продолжить с изображением по умолчанию, предоставленным приложением.

После того как пользователь выбирает изображение, он может добавить к нему наклейку. Давайте начнём создавать этот экран.

## Разберите экран
Прежде чем создавать этот экран с помощью кода, давайте разберём его на основные элементы.
Есть два основных элемента:

В центре экрана отображается большое изображение
В нижней части экрана расположены две кнопки
Первая кнопка содержит несколько компонентов. Родительский элемент имеет жёлтую рамку и содержит иконку и текстовые компоненты внутри строки.
Теперь, когда мы разбили интерфейс на более мелкие участки, мы готовы начать программирование.

## Показать изображение
Мы будем использовать библиотеку для отображения изображения в приложении. Он предоставляет кроссплатформенный компонент для загрузки и рендеринга изображения. Он уже включен в стандартный шаблон проекта, который мы используем.expo-image<Image>

Компонент Image принимает источник изображения в качестве своего значения. Исходный код может быть как статическим активом, так и URL. Например, исходный код, требуемый из каталога ассетов/изображений, является статичным. Он также может поступать из сети как объект.uri

Чтобы использовать компонент Image в файле src/app/(tabs)/index.tsx:

Импортируйте из библиотеки.Imageexpo-image
Создайте переменную, чтобы использовать ассеты/изображения/background-image.png файл в качестве проппа компонента. PlaceholderImage source Image
```
import { View, StyleSheet } from 'react-native';
import { Image } from 'expo-image';

const PlaceholderImage = require('@/assets/images/background-image.png');

export default function Index() {
  return (
    <View style={styles.container}>
      <View style={styles.imageContainer}>
        <Image source={PlaceholderImage} style={styles.image} />
      </View>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#25292e',
    alignItems: 'center',
  },
  imageContainer: {
    flex: 1,
  },
  image: {
    width: 320,
    height: 440,
    borderRadius: 18,
  },
});
```

## Разделить компоненты на файлы
Давайте разделим код на несколько файлов по мере добавления новых компонентов на этот экран. В течение этого урока мы будем использовать каталог компонентов для создания пользовательских компонентов.

Создайте каталог компонентов внутри src, а внутри него — файл image-viewer.tsx.
Переместите код, чтобы отображать изображение в этом файле вместе со стилями. image
```
import { ImageSourcePropType, StyleSheet } from 'react-native';
import { Image } from 'expo-image';
type Props = {
  imgSource: ImageSourcePropType;
};
export default function ImageViewer({ imgSource }: Props) {
  return <Image source={imgSource} style={styles.image} />;
}
const styles = StyleSheet.create({
  image: {
    width: 320,
    height: 440,
    borderRadius: 18,
  },
});
```
Импортируйте и используйте его в src/app/(tabs)/index.tsx:ImageViewer
```
import { StyleSheet, View } from 'react-native';

import ImageViewer from '@/components/image-viewer';

const PlaceholderImage = require('@/assets/images/background-image.png');

export default function Index() {
  return (
    <View style={styles.container}>
      <View style={styles.imageContainer}>
        <ImageViewer imgSource={PlaceholderImage} />
      </View>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#25292e',
    alignItems: 'center',
  },
  imageContainer: {
    flex: 1,
  },
});
```
## Создайте кнопки с помощью Pressable
React Native включает несколько различных компонентов для обработки сенсорных событий, но <Pressable> рекомендуется за свою гибкость. Он может обнаруживать одиночные нажатия, долгие нажатия, запускать отдельные события при нажатии и отпускании кнопки и многое другое.

В дизайне нам нужно создать две кнопки. У каждого свой стиль и ярлык. Давайте начнём с создания многоразового компонента для этих кнопок. Создайте файл button.tsx внутри каталога src/components с помощью следующего кода:
```
import { StyleSheet, View, Pressable, Text } from 'react-native';

type Props = {
  label: string;
};

export default function Button({ label }: Props) {
  return (
    <View style={styles.buttonContainer}>
      <Pressable style={styles.button} onPress={() => alert('You pressed a button.')}>
        <Text style={styles.buttonLabel}>{label}</Text>
      </Pressable>
    </View>
  );
}

const styles = StyleSheet.create({
  buttonContainer: {
    width: 320,
    height: 68,
    marginHorizontal: 20,
    alignItems: 'center',
    justifyContent: 'center',
    padding: 3,
  },
  button: {
    borderRadius: 10,
    width: '100%',
    height: '100%',
    alignItems: 'center',
    justifyContent: 'center',
    flexDirection: 'row',
  },
  buttonLabel: {
    color: '#fff',
    fontSize: 16,
  },
});
```
Приложение показывает оповещение при нажатии любой из кнопок на экране. Это происходит из-за призывов к его реквизиту. Давайте импортируем этот компонент в файл src/app/(tabs)/index.tsx и добавим стили, которые инкапсулируют эти кнопки:<Pressable>alert()onPress<View>
```
import { View, StyleSheet } from 'react-native';

import Button from '@/components/button';
import ImageViewer from '@/components/image-viewer';

const PlaceholderImage = require("@/assets/images/background-image.png");

export default function Index() {
  return (
    <View style={styles.container}>
      <View style={styles.imageContainer}>
        <ImageViewer imgSource={PlaceholderImage} />
      </View>
      <View style={styles.footerContainer}>
        <Button label="Choose a photo" />
        <Button label="Use this photo" />
      </View>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#25292e',
    alignItems: 'center',
  },
  imageContainer: {
    flex: 1,
  },
  footerContainer: {
    flex: 1 / 3,
    alignItems: 'center',
  },
});
```

## Улучшите компонент многоразовой кнопки
Кнопка «Выбрать фото» требует другого стиля, чем кнопка «Использовать эту фотографию», поэтому мы добавим новый реквизит для темы кнопок, который позволит применить тему. Эта кнопка также имеет иконку перед этикеткой. Мы используем иконку из библиотеки.primary@expo/vector-icons

Чтобы загрузить и отобразить значок на кнопке, давайте воспользуемся из библиотеки. Измените src/components/button.tsx, чтобы добавить следующий фрагмент кода:FontAwesome
```
import { StyleSheet, View, Pressable, Text } from 'react-native';
import FontAwesome from '@expo/vector-icons/FontAwesome';

type Props = {
  label: string;
  theme?: 'primary';
};

export default function Button({ label, theme }: Props) {
  if (theme === 'primary') {
  return (
      <View
        style={[
          styles.buttonContainer,
          { borderWidth: 4, borderColor: '#ffd33d', borderRadius: 18 },
        ]}>
        <Pressable
          style={[styles.button, { backgroundColor: '#fff' }]}
          onPress={() => alert('You pressed a button.')}>
          <FontAwesome name="picture-o" size={18} color="#25292e" style={styles.buttonIcon} />
          <Text style={[styles.buttonLabel, { color: '#25292e' }]}>{label}</Text>
        </Pressable>
      </View>
    );
  }

  return (
    <View style={styles.buttonContainer}>
      <Pressable style={styles.button} onPress={() => alert('You pressed a button.')}>
        <Text style={styles.buttonLabel}>{label}</Text>
      </Pressable>
    </View>
  );
}

const styles = StyleSheet.create({
  buttonContainer: {
    width: 320,
    height: 68,
    marginHorizontal: 20,
    alignItems: 'center',
    justifyContent: 'center',
    padding: 3,
  },
  button: {
    borderRadius: 10,
    width: '100%',
    height: '100%',
    alignItems: 'center',
    justifyContent: 'center',
    flexDirection: 'row',
  },
  buttonIcon: {
    paddingRight: 8,
  },
  buttonLabel: {
    color: '#fff',
    fontSize: 16,
  },
});
```
Давайте узнаем, что делает вышеуказанный код:

Кнопка основной темы использует встроенные стили, которые переопределяют стили, определённые в предмете, непосредственно передающем в реквизит.StyleSheet.create()style
Компонент в основной теме использует свойство с значением, чтобы задать фон кнопки белым. Если добавить это свойство к , значение цвета фона будет установлено как для основной, так и для нестилизованной.<Pressable>backgroundColor#fffstyles.button
Встроенные стили используют JavaScript и переопределяют стандартные стили для определённого значения.
Теперь измените файл src/app/(tabs)/index.tsx, чтобы использовать проп на первой кнопке.theme="primary"
```
import { View, StyleSheet } from 'react-native';

import Button from '@/components/button';
import ImageViewer from '@/components/image-viewer';

const PlaceholderImage = require('@/assets/images/background-image.png');

export default function Index() {
  return (
    <View style={styles.container}>
      <View style={styles.imageContainer}>
        <ImageViewer imgSource={PlaceholderImage} />
      </View>
      <View style={styles.footerContainer}>
        <Button theme="primary" label="Choose a photo" />
        <Button label="Use this photo" />
      </View>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#25292e',
    alignItems: 'center',
  },
  imageContainer: {
    flex: 1,
  },
  footerContainer: {
    flex: 1 / 3,
    alignItems: 'center',
  },
});
```
# Используйте набор изображений
React Native предоставляет встроенные компоненты в качестве стандартных строительных блоков, такие как , , и . Мы создаём функцию для выбора изображения из медиагалереи устройства. Это невозможно с основными компонентами, и нам понадобится библиотека, чтобы добавить эту функцию в наше приложение.<View><Text><Pressable>

Мы используем expo-image-picker, библиотека от Expo SDK.

## Установка expo-image-picker
Чтобы установить библиотеку, остановите сервер разработки, нажав + в терминале, затем выполните следующую команду:expo-image-picker Ctrl+C
```
npx expo install expo-image-picker
```
The npx expo install Команда установит библиотеку и добавит её в зависимости проекта в package.json.
## Выберите изображение из медиабиблиотеки устройства
expo-image-picker предоставляет способ отображения системного интерфейса путём выбора изображения или видео из медиатеки устройства. Мы используем основную тематическую кнопку, созданную в предыдущей главе, чтобы выбрать изображение из медиабиблиотеки устройства и создать функцию запуска библиотеки изображений устройства для реализации этой функции.launchImageLibraryAsync()

В src/app/(tabs)/index.tsx импортируйте библиотеку и создайте функцию внутри компонента:expo-image-picker pickImageAsync() Index
```
// ...rest of the import statements remain unchanged
import * as ImagePicker from 'expo-image-picker';

export default function Index() {
  const pickImageAsync = async () => {
    let result = await ImagePicker.launchImageLibraryAsync({
      mediaTypes: ['images'],
      allowsEditing: true,
      quality: 1,
    });

    if (!result.canceled) {
      console.log(result);
    } else {
      alert('You did not select any image.');
    }
  };

  // ...rest of the code remains same
}
```
Давайте узнаем, что делает вышеуказанный код:

Он получает объект для указания различных опций. Этот объект — это launchImageLibraryAsync()ImagePickerOptions Объект, который мы проходим при вызове метода.
При установке на , пользователь может обрезать изображение во время выбора на Android и iOS.allowsEditing true

## Обновить компонент кнопок
При нажатии основной кнопки мы вызовем функцию компонента. Обновите проп компонента в src/components/button.tsx: pickImageAsync() Button onPress Button
```
import { StyleSheet, View, Pressable, Text } from 'react-native';
import FontAwesome from '@expo/vector-icons/FontAwesome';

type Props = {
  label: string;
  theme?: 'primary';
  onPress?: () => void;
};

export default function Button({ label, theme, onPress }: Props) {
  if (theme === 'primary') {
    return (
      <View
        style={[
          styles.buttonContainer,
          { borderWidth: 4, borderColor: '#ffd33d', borderRadius: 18 },
        ]}>
        <Pressable style={[styles.button, { backgroundColor: '#fff' }]} onPress={onPress}>
          <FontAwesome name="picture-o" size={18} color="#25292e" style={styles.buttonIcon} />
          <Text style={[styles.buttonLabel, { color: '#25292e' }]}>{label}</Text>
        </Pressable>
      </View>
    );
  }

  return (
    <View style={styles.buttonContainer}>
      <Pressable style={styles.button} onPress={() => alert('You pressed a button.')}>
        <Text style={styles.buttonLabel}>{label}</Text>
      </Pressable>
    </View>
  );
}

const styles = StyleSheet.create({
  buttonContainer: {
    width: 320,
    height: 68,
    marginHorizontal: 20,
    alignItems: 'center',
    justifyContent: 'center',
    padding: 3,
  },
  button: {
    borderRadius: 10,
    width: '100%',
    height: '100%',
    alignItems: 'center',
    justifyContent: 'center',
    flexDirection: 'row',
  },
  buttonIcon: {
    paddingRight: 8,
  },
  buttonLabel: {
    color: '#fff',
    fontSize: 16,
  },
});
```
В src/app/(tabs)/index.tsx добавьте функцию в проп на первом. ```pickImageAsync() onPress <Button>```
```
import { View, StyleSheet } from 'react-native';
import * as ImagePicker from 'expo-image-picker';

import Button from '@/components/button';
import ImageViewer from '@/components/image-viewer';

const PlaceholderImage = require('@/assets/images/background-image.png');

export default function Index() {
  const pickImageAsync = async () => {
    let result = await ImagePicker.launchImageLibraryAsync({
      mediaTypes: ['images'],
      allowsEditing: true,
      quality: 1,
    });

    if (!result.canceled) {
      console.log(result);
    } else {
      alert('You did not select any image.');
    }
  };

  return (
    <View style={styles.container}>
      <View style={styles.imageContainer}>
        <ImageViewer imgSource={PlaceholderImage} />
      </View>
      <View style={styles.footerContainer}>
        <Button theme="primary" label="Choose a photo" onPress={pickImageAsync} />
        <Button label="Use this photo" />
      </View>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#25292e',
    alignItems: 'center',
  },
  imageContainer: {
    flex: 1,
  },
  footerContainer: {
    flex: 1 / 3,
    alignItems: 'center',
  },
});
```
Функция вызывает и затем обрабатывает результат. Метод возвращает объект с информацией о выбранном изображении.pickImageAsync() ImagePicker.launchImageLibraryAsync() launchImageLibraryAsync()

Вот пример объекта и свойств, которые он содержит:result
```
{
  "assets": [
    {
      "assetId": null,
      "base64": null,
      "duration": null,
      "exif": null,
      "fileName": "ea574eaa-f332-44a7-85b7-99704c22b402.jpeg",
      "fileSize": 4513577,
      "height": 4570,
      "mimeType": "image/jpeg",
      "rotation": null,
      "type": "image",
      "uri": "file:///data/user/0/host.exp.exponent/cache/ExperienceData/%2540anonymous%252FStickerSmash-13f21121-fc9d-4ec6-bf89-bf7d6165eb69/ImagePicker/ea574eaa-f332-44a7-85b7-99704c22b402.jpeg",
      "width": 2854
    }
  ],
  "canceled": false
}
```
## Используйте выбранное изображение
Объект предоставляет массив выбранного изображения. Давайте возьмём это значение из picker изображений и используем его, чтобы показать выбранное изображение в приложении.result assets uri
Измените файл src/app/(tabs)/index.tsx:

Объявим переменную состояния, вызванную с помощью selectedImageuseState крючок от React. Мы используем эту переменную состояния, чтобы сохранить URI выбранного изображения.
Обновите функцию, чтобы сохранить URI изображения в переменной состояния.pickImageAsync()selectedImage
Передайте его как реквизит компоненту.selectedImage ImageViewer
```
import { View, StyleSheet } from 'react-native';
import * as ImagePicker from 'expo-image-picker';
import { useState } from 'react';

import Button from '@/components/button';
import ImageViewer from '@/components/image-viewer';

const PlaceholderImage = require('@/assets/images/background-image.png');

export default function Index() {
  const [selectedImage, setSelectedImage] = useState<string | undefined>(undefined);

  const pickImageAsync = async () => {
    let result = await ImagePicker.launchImageLibraryAsync({
      mediaTypes: ['images'],
      allowsEditing: true,
      quality: 1,
    });

    if (!result.canceled) {
      setSelectedImage(result.assets[0].uri);
    } else {
      alert('You did not select any image.');
    }
  };

  return (
    <View style={styles.container}>
      <View style={styles.imageContainer}>
        <ImageViewer imgSource={PlaceholderImage} selectedImage={selectedImage} />
      </View>
      <View style={styles.footerContainer}>
        <Button theme="primary" label="Choose a photo" onPress={pickImageAsync} />
        <Button label="Use this photo" />
      </View>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#25292e',
    alignItems: 'center',
  },
  imageContainer: {
    flex: 1,
  },
  footerContainer: {
    flex: 1 / 3,
    alignItems: 'center',
  },
});
```
Передайте реквизит компоненту, чтобы отобразить выбранное изображение вместо временного изображения.selectedImage ImageViewer

Модифицируйте файл src/components/image-viewer.tsx, чтобы он принял проп.selectedImage
Источник изображения становится длинным, поэтому давайте также переместим его в отдельную переменную под названием .imageSource
Передайте как значение пропеллера на компоненте.imageSource source Image
```
import { ImageSourcePropType, StyleSheet } from 'react-native';
import { Image } from 'expo-image';

type Props = {
  imgSource: ImageSourcePropType;
  selectedImage?: string;
};

export default function ImageViewer({ imgSource, selectedImage }: Props) {
  const imageSource = selectedImage ? { uri: selectedImage } : imgSource;

  return <Image source={imageSource} style={styles.image} />;
}

const styles = StyleSheet.create({
  image: {
    width: 320,
    height: 440,
    borderRadius: 18,
  },
});
```
В приведённом выше фрагменте компонент Image использует условный оператор для загрузки исходного источника изображения. Выбранное изображение — это uri Строка, а не локальный актив, как заполняющее изображение.

# Создайте модаль
React Native предоставляет <Modal> Компонент Это представляет контент выше остального вашего приложения. В целом, модальные методы используются для привлечения внимания пользователя к критически важной информации или для того, чтобы помочь ему принять меры. Например, в третьей главе, после нажатия кнопки, мы показывали какой-то временный текст. Так модальный компонент отображает наложение. alert()

## Объявить переменную состояния для отображения кнопок
Перед внедрением модала мы добавим три новые кнопки. Эти кнопки видны после того, как пользователь выбирает изображение из медиабиблиотеки или использует заполняющее изображение. Одна из этих кнопок запускает модаль отбора эмодзи.
В src/app/(tabs)/index.tsx:

Объявите переменную булевого состояния, , чтобы показать или скрыть кнопки, открывающие модаль, а также несколько других опций. Когда экран приложения загружается, мы устанавливаем так, чтобы опции не отображались перед выбором изображения. Когда пользователь выбирает изображение или использует заполнительное изображение, мы устанавливаем его на .showAppOptionsfalsetrue
Обновите функцию, чтобы установить значение в после выбора изображения.pickImageAsync()showAppOptionstrue
Обновите кнопку без темы, добавив реквизит со следующим значением.onPress
```
import { View, StyleSheet } from 'react-native';
import * as ImagePicker from 'expo-image-picker';
import { useState } from 'react';

import Button from '@/components/button';
import ImageViewer from '@/components/image-viewer';

const PlaceholderImage = require('@/assets/images/background-image.png');

export default function Index() {
  const [selectedImage, setSelectedImage] = useState<string | undefined>(undefined);
  const [showAppOptions, setShowAppOptions] = useState<boolean>(false);

  const pickImageAsync = async () => {
    let result = await ImagePicker.launchImageLibraryAsync({
      mediaTypes: ['images'],
      allowsEditing: true,
      quality: 1,
    });

    if (!result.canceled) {
      setSelectedImage(result.assets[0].uri);
      setShowAppOptions(true);
    } else {
      alert('You did not select any image.');
    }
  };

  return (
    <View style={styles.container}>
      <View style={styles.imageContainer}>
        <ImageViewer imgSource={PlaceholderImage} selectedImage={selectedImage} />
      </View>
      {showAppOptions ? (
        <View />
      ) : (
        <View style={styles.footerContainer}>
          <Button theme="primary" label="Choose a photo" onPress={pickImageAsync} />
          <Button label="Use this photo" onPress={() => setShowAppOptions(true)} />
        </View>
      )}
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#25292e',
    alignItems: 'center',
  },
  imageContainer: {
    flex: 1,
  },
  footerContainer: {
    flex: 1 / 3,
    alignItems: 'center',
  },
});
```
В приведённом выше фрагменте мы рендерим компонент на основе значения и перемещаем кнопки в блоке тернарного оператора. Когда значение равен , отобразите пустую компоненту. Мы рассмотрим это состояние на следующем этапе.```Button showAppOptions showAppOptions true <View>```

Теперь мы можем удалить на компоненте и обновить проп при рендеринге второй кнопки в src/components/button.tsx: alert Button onPress
```
<Pressable style={styles.button} onPress={onPress}>
```
## Добавить кнопки
Давайте разберём расположение кнопок опций, которые мы реализуем в этой главе. Дизайн выглядит так:
Он содержит родителя с тремя выровненными в ряду кнопками. Кнопка посередине с иконкой плюса (+) открывает модаль и оформлена иначе, чем две другие кнопки.

Внутри каталога src/components создайте новый файл circle-button.tsx с следующим кодом:
```
import { View, Pressable, StyleSheet } from 'react-native';
import MaterialIcons from '@expo/vector-icons/MaterialIcons';

type Props = {
  onPress: () => void;
};

export default function CircleButton({ onPress }: Props) {
  return (
    <View style={styles.circleButtonContainer}>
      <Pressable style={styles.circleButton} onPress={onPress}>
        <MaterialIcons name="add" size={38} color="#25292e" />
      </Pressable>
    </View>
  );
}

const styles = StyleSheet.create({
  circleButtonContainer: {
    width: 84,
    height: 84,
    marginHorizontal: 60,
    borderWidth: 4,
    borderColor: '#ffd33d',
    borderRadius: 42,
    padding: 3,
  },
  circleButton: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    borderRadius: 42,
    backgroundColor: '#fff',
  },
});
```
Для отображения значка плюса эта кнопка использует иконки, установленные из библиотеки.<MaterialIcons>@expo/vector-icons

Две другие кнопки также используются для отображения вертикально выровненных текстовых меток и иконок. Создайте файл с именем icon-button.tsx внутри каталога src/components. Этот компонент принимает три реквизита:<MaterialIcons>

icon: название, соответствующее иконке библиотеки.MaterialIcons
label: текстовая метка, отображаемая на кнопке.
onPress: эта функция вызывается, когда пользователь нажимает кнопку.
```
import { Pressable, StyleSheet, Text } from 'react-native';
import MaterialIcons from '@expo/vector-icons/MaterialIcons';

type Props = {
  icon: keyof typeof MaterialIcons.glyphMap;
  label: string;
  onPress: () => void;
};

export default function IconButton({ icon, label, onPress }: Props) {
  return (
    <Pressable style={styles.iconButton} onPress={onPress}>
      <MaterialIcons name={icon} size={24} color="#fff" />
      <Text style={styles.iconButtonLabel}>{label}</Text>
    </Pressable>
  );
}

const styles = StyleSheet.create({
  iconButton: {
    justifyContent: 'center',
    alignItems: 'center',
  },
  iconButtonLabel: {
    color: '#fff',
    marginTop: 12,
  },
});
```
Внутри src/app/(tabs)/index.tsx:

Импортируйте компоненты и для их отображения.CircleButtonIconButton
Добавьте три временных функции для этих кнопок. Функция срабатывает при нажатии кнопки сброса, вызывая повторное появление кнопки выбора изображения. Функционал для остальных двух функций мы добавим позже. onReset()
```
import { View, StyleSheet } from 'react-native';
import * as ImagePicker from 'expo-image-picker';
import { useState } from 'react';

import Button from '@/components/button';
import ImageViewer from '@/components/image-viewer';
import IconButton from '@/components/icon-button';
import CircleButton from '@/components/circle-button';

const PlaceholderImage = require('@/assets/images/background-image.png');

export default function Index() {
  const [selectedImage, setSelectedImage] = useState<string | undefined>(undefined);
  const [showAppOptions, setShowAppOptions] = useState<boolean>(false);

  const pickImageAsync = async () => {
    let result = await ImagePicker.launchImageLibraryAsync({
      mediaTypes: ['images'],
      allowsEditing: true,
      quality: 1,
    });

    if (!result.canceled) {
      setSelectedImage(result.assets[0].uri);
      setShowAppOptions(true);
    } else {
      alert('You did not select any image.');
    }
  };

  const onReset = () => {
    setShowAppOptions(false);
  };

  const onAddSticker = () => {
    // we will implement this later
  };

  const onSaveImageAsync = async () => {
    // we will implement this later
  };

  return (
    <View style={styles.container}>
      <View style={styles.imageContainer}>
        <ImageViewer imgSource={PlaceholderImage} selectedImage={selectedImage} />
      </View>
      {showAppOptions ? (
        <View style={styles.optionsContainer}>
          <View style={styles.optionsRow}>
            <IconButton icon="refresh" label="Reset" onPress={onReset} />
            <CircleButton onPress={onAddSticker} />
            <IconButton icon="save-alt" label="Save" onPress={onSaveImageAsync} />
          </View>
        </View>
      ) : (
        <View style={styles.footerContainer}>
          <Button theme="primary" label="Choose a photo" onPress={pickImageAsync} />
          <Button label="Use this photo" onPress={() => setShowAppOptions(true)} />
        </View>
      )}
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#25292e',
    alignItems: 'center',
  },
  imageContainer: {
    flex: 1,
  },
  footerContainer: {
    flex: 1 / 3,
    alignItems: 'center',
  },
  optionsContainer: {
    position: 'absolute',
    bottom: 80,
  },
  optionsRow: {
    alignItems: 'center',
    flexDirection: 'row',
  },
});
```
## Создать модаль с отбором эмодзи
Модаль позволяет пользователю выбрать эмодзи из списка доступных эмодзи. Создайте файл emoji-picker.tsx внутри каталога src/components. Этот компонент принимает три реквизита:

isVisible: булев показатель для определения состояния видимости модаля.
onClose: функция для закрытия модаля.
children: позже использовался для отображения списка эмодзи.
```
import { Modal, View, Text, Pressable, StyleSheet } from 'react-native';
import { PropsWithChildren } from 'react';
import MaterialIcons from '@expo/vector-icons/MaterialIcons';

type Props = PropsWithChildren<{
  isVisible: boolean;
  onClose: () => void;
}>;

export default function EmojiPicker({ isVisible, children, onClose }: Props) {
  return (
    <View>
      <Modal animationType="slide" transparent={true} visible={isVisible}>
        <View style={styles.modalContent}>
          <View style={styles.titleContainer}>
            <Text style={styles.title}>Choose a sticker</Text>
            <Pressable onPress={onClose}>
              <MaterialIcons name="close" color="#fff" size={22} />
            </Pressable>
          </View>
          {children}
        </View>
      </Modal>
    </View>
  );
}

const styles = StyleSheet.create({
  modalContent: {
    height: '25%',
    width: '100%',
    backgroundColor: '#25292e',
    borderTopRightRadius: 18,
    borderTopLeftRadius: 18,
    position: 'absolute',
    bottom: 0,
  },
  titleContainer: {
    height: '16%',
    backgroundColor: '#464C55',
    borderTopRightRadius: 10,
    borderTopLeftRadius: 10,
    paddingHorizontal: 20,
    flexDirection: 'row',
    alignItems: 'center',
    justifyContent: 'space-between',
  },
  title: {
    color: '#fff',
    fontSize: 16,
  },
});
```
Давайте узнаем, что делает вышеуказанный код:

Компонент отображает заголовок и кнопку закрытия.<Modal>
Его пропеллер принимает значение и определяет, открыт ли модаль или закрыт.visibleisVisible
Его проп — булево значение, которое определяет, заполняет ли модаль весь обзор.transparent
Его реквизит определяет, как он входит и выходит из экрана. В данном случае он скользит снизу экрана.animationType
Наконец, при нажатии кнопки закрытия пользователь вызывает проп.<EmojiPicker>onClose<Pressable>
Теперь давайте изменим src/app/(tabs)/index.tsx:

Импортируйте компонент.<EmojiPicker>
Создайте переменную состояния с помощью этого хука. Его стандартное значение — , которое скрывает модаль до тех пор, пока пользователь не нажмёт кнопку для его открытия.isModalVisibleuseStatefalse
Замените комментарий в функции, чтобы обновить переменную до момента, когда пользователь нажимает кнопку. Это откроет отбор эмодзи.onAddSticker()isModalVisibletrue
Создайте функцию для обновления переменной состояния.onModalClose()isModalVisible
Разместите компонент внизу компонента.<EmojiPicker>Index
```
import { View, StyleSheet } from 'react-native';
import * as ImagePicker from 'expo-image-picker';
import { useState } from 'react';

import Button from '@/components/button';
import ImageViewer from '@/components/image-viewer';
import IconButton from '@/components/icon-button';
import CircleButton from '@/components/circle-button';
import EmojiPicker from '@/components/emoji-picker';

const PlaceholderImage = require('@/assets/images/background-image.png');

export default function Index() {
  const [selectedImage, setSelectedImage] = useState<string | undefined>(undefined);
  const [showAppOptions, setShowAppOptions] = useState<boolean>(false);
  const [isModalVisible, setIsModalVisible] = useState<boolean>(false);

  const pickImageAsync = async () => {
    let result = await ImagePicker.launchImageLibraryAsync({
      mediaTypes: ['images'],
      allowsEditing: true,
      quality: 1,
    });

    if (!result.canceled) {
      setSelectedImage(result.assets[0].uri);
      setShowAppOptions(true);
    } else {
      alert('You did not select any image.');
    }
  };

  const onReset = () => {
    setShowAppOptions(false);
  };

  const onAddSticker = () => {
    setIsModalVisible(true);
  };

  const onModalClose = () => {
    setIsModalVisible(false);
  };

  const onSaveImageAsync = async () => {
    // we will implement this later
  };

  return (
    <View style={styles.container}>
      <View style={styles.imageContainer}>
        <ImageViewer imgSource={PlaceholderImage} selectedImage={selectedImage} />
      </View>
      {showAppOptions ? (
        <View style={styles.optionsContainer}>
          <View style={styles.optionsRow}>
            <IconButton icon="refresh" label="Reset" onPress={onReset} />
            <CircleButton onPress={onAddSticker} />
            <IconButton icon="save-alt" label="Save" onPress={onSaveImageAsync} />
          </View>
        </View>
      ) : (
        <View style={styles.footerContainer}>
          <Button theme="primary" label="Choose a photo" onPress={pickImageAsync} />
          <Button label="Use this photo" onPress={() => setShowAppOptions(true)} />
        </View>
      )}
      <EmojiPicker isVisible={isModalVisible} onClose={onModalClose}>
        {/* Emoji list component will go here */}
      </EmojiPicker>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#25292e',
    alignItems: 'center',
  },
  imageContainer: {
    flex: 1,
  },
  footerContainer: {
    flex: 1 / 3,
    alignItems: 'center',
  },
  optionsContainer: {
    position: 'absolute',
    bottom: 80,
  },
  optionsRow: {
    alignItems: 'center',
    flexDirection: 'row',
  },
});
```
## Показать список эмодзи
Давайте добавим горизонтальный список эмодзи в содержимое модаля. Мы используем <FlatList> компонент от React Native для этого.

Создайте файл emoji-list.tsx внутри каталога src/components и добавьте следующий код:
```
import { useState } from 'react';
import { ImageSourcePropType, StyleSheet, FlatList, Platform, Pressable } from 'react-native';
import { Image } from 'expo-image';

type Props = {
  onSelect: (image: ImageSourcePropType) => void;
  onCloseModal: () => void;
};

export default function EmojiList({ onSelect, onCloseModal }: Props) {
  const [emoji] = useState<ImageSourcePropType[]>([
    require("@/assets/images/emoji1.png"),
    require("@/assets/images/emoji2.png"),
    require("@/assets/images/emoji3.png"),
    require("@/assets/images/emoji4.png"),
    require("@/assets/images/emoji5.png"),
    require("@/assets/images/emoji6.png"),
  ]);

  return (
    <FlatList
      horizontal
      showsHorizontalScrollIndicator={Platform.OS === 'web'}
      data={emoji}
      contentContainerStyle={styles.listContainer}
      renderItem={({ item, index }) => (
        <Pressable
          onPress={() => {
            onSelect(item);
            onCloseModal();
          }}>
          <Image source={item} key={index} style={styles.image} />
        </Pressable>
      )}
    />
  );
}

const styles = StyleSheet.create({
  listContainer: {
    borderTopRightRadius: 10,
    borderTopLeftRadius: 10,
    paddingHorizontal: 20,
    flexDirection: 'row',
    alignItems: 'center',
    justifyContent: 'space-between',
  },
  image: {
    width: 100,
    height: 100,
    marginRight: 20,
  },
});
```
Давайте узнаем, что делает вышеуказанный код:

Компонент выше отображает все изображения эмодзи с помощью компонента, обёрнутого . Позже мы улучшим её, чтобы пользователь мог нажать на эмодзи на экране, чтобы он выглядел как стикер на изображении.<FlatList>Image<Pressable>
Он также принимает массив элементов, предоставленных переменной массива, в качестве значения пропа. Реквизит забирает предмет из и возвращает его из списка. Наконец, мы добавили компоненты для отображения этого предмета.emojidatarenderItemdataImage<Pressable>
Реквизит отображает список горизонтально, а не вертикально. Он использует модуль React Native для проверки значения и отображения горизонтальной полоски прокрутки на вебе.horizontalshowsHorizontalScrollIndicatorPlatform
Теперь обновите src/app/(tabs)/index.tsx, чтобы импортировать компонент, и заменить комментарии внутри компонента следующим фрагментом кода:<EmojiList><EmojiPicker>
```
import { ImageSourcePropType, View, StyleSheet } from 'react-native';
import * as ImagePicker from 'expo-image-picker';
import { useState } from 'react';

import Button from '@/components/button';
import ImageViewer from '@/components/image-viewer';
import IconButton from '@/components/icon-button';
import CircleButton from '@/components/circle-button';
import EmojiPicker from '@/components/emoji-picker';
import EmojiList from '@/components/emoji-list';

const PlaceholderImage = require('@/assets/images/background-image.png');

export default function Index() {
  const [selectedImage, setSelectedImage] = useState<string | undefined>(undefined);
  const [showAppOptions, setShowAppOptions] = useState<boolean>(false);
  const [isModalVisible, setIsModalVisible] = useState<boolean>(false);
  const [pickedEmoji, setPickedEmoji] = useState<ImageSourcePropType | undefined>(undefined);

  const pickImageAsync = async () => {
    let result = await ImagePicker.launchImageLibraryAsync({
      mediaTypes: ['images'],
      allowsEditing: true,
      quality: 1,
    });

    if (!result.canceled) {
      setSelectedImage(result.assets[0].uri);
      setShowAppOptions(true);
    } else {
      alert('You did not select any image.');
    }
  };

  const onReset = () => {
    setShowAppOptions(false);
  };

  const onAddSticker = () => {
    setIsModalVisible(true);
  };

  const onModalClose = () => {
    setIsModalVisible(false);
  };

  const onSaveImageAsync = async () => {
    // we will implement this later
  };

  return (
    <View style={styles.container}>
      <View style={styles.imageContainer}>
        <ImageViewer imgSource={PlaceholderImage} selectedImage={selectedImage} />
      </View>
      {showAppOptions ? (
        <View style={styles.optionsContainer}>
          <View style={styles.optionsRow}>
            <IconButton icon="refresh" label="Reset" onPress={onReset} />
            <CircleButton onPress={onAddSticker} />
            <IconButton icon="save-alt" label="Save" onPress={onSaveImageAsync} />
          </View>
        </View>
      ) : (
        <View style={styles.footerContainer}>
          <Button theme="primary" label="Choose a photo" onPress={pickImageAsync} />
          <Button label="Use this photo" onPress={() => setShowAppOptions(true)} />
        </View>
      )}
      <EmojiPicker isVisible={isModalVisible} onClose={onModalClose}>
        <EmojiList onSelect={setPickedEmoji} onCloseModal={onModalClose} />
      </EmojiPicker>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#25292e',
    alignItems: 'center',
  },
  imageContainer: {
    flex: 1,
  },
  footerContainer: {
    flex: 1 / 3,
    alignItems: 'center',
  },
  optionsContainer: {
    position: 'absolute',
    bottom: 80,
  },
  optionsRow: {
    alignItems: 'center',
    flexDirection: 'row',
  },
});
```

## Показать выбранные эмодзи
Теперь наклеим наклейку с эмодзи на изображение. Создайте новый файл в каталоге src/components и назовите его emoji-sticker.tsx. Затем добавьте следующий код:
```
import { ImageSourcePropType, View } from 'react-native';
import { Image } from 'expo-image';

type Props = {
  imageSize: number;
  stickerSource: ImageSourcePropType;
};

export default function EmojiSticker({ imageSize, stickerSource }: Props) {
  return (
    <View style={{ top: -350 }}>
      <Image source={stickerSource} style={{ width: imageSize, height: imageSize }} />
    </View>
  );
}
```
Этот компонент получает две характеристики:

imageSize: значение, определённое внутри компонента. Мы используем это значение в следующей главе, чтобы масштабировать размер изображения при нажатии.Index
stickerSource: источник выбранного эмодзи.
Импортируйте этот компонент в файл src/app/(tabs)/index.tsx и обновите компонент, чтобы на изображении отображалась наклейка эмодзи. Мы проверим, если состояние не является :Index pickedEmoji undefined
```
import { ImageSourcePropType, View, StyleSheet } from 'react-native';
import * as ImagePicker from 'expo-image-picker';
import { useState } from 'react';

import Button from '@/components/button';
import ImageViewer from '@/components/image-viewer';
import IconButton from '@/components/icon-button';
import CircleButton from '@/components/circle-button';
import EmojiPicker from '@/components/emoji-picker';
import EmojiList from '@/components/emoji-list';
import EmojiSticker from '@/components/emoji-sticker';

const PlaceholderImage = require('@/assets/images/background-image.png');

export default function Index() {
  const [selectedImage, setSelectedImage] = useState<string | undefined>(undefined);
  const [showAppOptions, setShowAppOptions] = useState<boolean>(false);
  const [isModalVisible, setIsModalVisible] = useState<boolean>(false);
  const [pickedEmoji, setPickedEmoji] = useState<ImageSourcePropType | undefined>(undefined);


  const pickImageAsync = async () => {
    let result = await ImagePicker.launchImageLibraryAsync({
      mediaTypes: ['images'],
      allowsEditing: true,
      quality: 1,
    });

    if (!result.canceled) {
      setSelectedImage(result.assets[0].uri);
      setShowAppOptions(true);
    } else {
      alert('You did not select any image.');
    }
  };

  const onReset = () => {
    setShowAppOptions(false);
  };

  const onAddSticker = () => {
    setIsModalVisible(true);
  };

  const onModalClose = () => {
    setIsModalVisible(false);
  };

  const onSaveImageAsync = async () => {
    // we will implement this later
  };

  return (
    <View style={styles.container}>
      <View style={styles.imageContainer}>
        <ImageViewer imgSource={PlaceholderImage} selectedImage={selectedImage} />
        {pickedEmoji && <EmojiSticker imageSize={40} stickerSource={pickedEmoji} />}
      </View>
      {showAppOptions ? (
        <View style={styles.optionsContainer}>
          <View style={styles.optionsRow}>
            <IconButton icon="refresh" label="Reset" onPress={onReset} />
            <CircleButton onPress={onAddSticker} />
            <IconButton icon="save-alt" label="Save" onPress={onSaveImageAsync} />
          </View>
        </View>
      ) : (
        <View style={styles.footerContainer}>
          <Button theme="primary" label="Choose a photo" onPress={pickImageAsync} />
          <Button label="Use this photo" onPress={() => setShowAppOptions(true)} />
        </View>
      )}
      <EmojiPicker isVisible={isModalVisible} onClose={onModalClose}>
        <EmojiList onSelect={setPickedEmoji} onCloseModal={onModalClose} />
      </EmojiPicker>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#25292e',
    alignItems: 'center',
  },
  imageContainer: {
    flex: 1,
  },
  footerContainer: {
    flex: 1 / 3,
    alignItems: 'center',
  },
  optionsContainer: {
    position: 'absolute',
    bottom: 80,
  },
  optionsRow: {
    alignItems: 'center',
    flexDirection: 'row',
  },
});
```
# Добавить жесты
Жесты — отличный способ обеспечить интуитивно понятный пользовательский опыт в приложении. Библиотека React Native Gesture Handler предоставляет встроенные компоненты, способные обрабатывать жесты. Он распознаёт панорамирование, нажатие, вращение и другие жесты с помощью встроенной системы сенсорного управления платформой. В этой главе мы добавим два разных жеста с помощью этой библиотеки:

Дважды нажимайте, чтобы масштабировать размер наклейки эмодзи, и уменьшайте масштаб при повторном нажатии.
Панорамируйте, чтобы переместить наклейку по экрану, чтобы пользователь мог разместить наклейку в любом месте на изображении.
Мы также будем использовать библиотеку Reanimated для анимации между состояниями жестов.

## Add GestureHandlerRootView
Чтобы взаимодействие жестов работало в приложении, мы рендерим сверху компонента. Замените компонент корневого уровня в src/app/(tabs)/index.tsx на .<GestureHandlerRootView>react-native-gesture-handlerIndex<View><GestureHandlerRootView>
```
// ... rest of the import statements remain same
import { GestureHandlerRootView } from 'react-native-gesture-handler';

export default function Index() {
  return (
    <GestureHandlerRootView style={styles.container}>
      {/* ...rest of the code remains */}
    </GestureHandlerRootView>
  )
}
```
## Используйте анимированные компоненты
Компонент смотрит на проп компонента и определяет, какие значения анимировать, а также применять обновления для создания анимации. Reanimated экспортирует анимированные компоненты, такие как , , или . Мы применим анимации к компоненту, чтобы двойной нажатие работало.Animatedstyle<Animated.View><Animated.Text><Animated.ScrollView><Animated.Image>

Откройте файл emoji-sticker.tsx в каталоге src/components. Внутри него импортируйте из библиотеки для использования анимированных компонентов.Animatedreact-native-reanimated
Замените компонент на .Image<Animated.Image>
```
import { ImageSourcePropType, View } from 'react-native';
import Animated from 'react-native-reanimated';

type Props = {
  imageSize: number;
  stickerSource: ImageSourcePropType;
};

export default function EmojiSticker({ imageSize, stickerSource }: Props) {
  return (
    <View style={{ top: -350 }}>
      <Animated.Image
        source={stickerSource}
        resizeMode="contain"
        style={{ width: imageSize, height: imageSize }}
      />
    </View>
  );
}
```
## Добавьте жест нажатия
React Native Gesture Handler позволяет добавлять поведение при обнаружении касания, например, при двойном нажатии.

В файле src/components/emoji-sticker.tsx:

Импорт и от .GestureGestureDetectorreact-native-gesture-handler
Чтобы распознать нажатие наклейки, импортировать , , и от — анимировать стиль .useAnimatedStyleuseSharedValuewithSpringreact-native-reanimated<Animated.Image>
Внутри компонента создайте ссылку, вызванную с помощью крючка. Он возьмёт значение в качестве начального значения.EmojiStickerscaleImageuseSharedValue()imageSize
```
// ...rest of the import statements remain same
import { Gesture, GestureDetector } from 'react-native-gesture-handler';
import Animated, { useAnimatedStyle, useSharedValue, withSpring } from 'react-native-reanimated';

export default function EmojiSticker({ imageSize, stickerSource }: Props) {
  const scaleImage = useSharedValue(imageSize);

  return (
    // ...rest of the code remains same
  )
}
```
Создание общей ценности с помощью крючка имеет множество преимуществ. Это помогает изменять данные и запускать анимации на основе текущего значения. Мы можем получить доступ и изменить общую ценность с помощью этого свойства. Мы создадим объект для масштабирования начального значения и анимации перехода при масштабировании изображения стикера. Чтобы определить количество требуемых отжиманий, добавим .useSharedValue().valuedoubleTapGesture.Tap()numberOfTaps()

Создайте следующий объект в компоненте:EmojiSticker
```
const doubleTap = Gesture.Tap()
  .numberOfTaps(2)
  .onStart(() => {
    if (scaleImage.value !== imageSize * 2) {
      scaleImage.value = scaleImage.value * 2;
    } else {
      scaleImage.value = Math.round(scaleImage.value / 2);
    }
  });
```
Чтобы анимировать переход, давайте используем пружинную анимацию. Это сделает игру живой, потому что она основана на реальной физике пружины. Мы будем использовать функцию, предоставляемую .withSpring()react-native-reanimated

На изображение наклейки мы используем крючок для создания объекта стиля. Это поможет нам обновлять стили, используя общие значения во время анимации. Мы также масштабируем размер изображения, изменяя свойства и. Начальные значения этих свойств устанавливаются как .useAnimatedStyle()widthheightimageSize

Создайте переменную и добавьте её в компонент:imageStyleEmojiSticker
```
const imageStyle = useAnimatedStyle(() => {
  return {
    width: withSpring(scaleImage.value),
    height: withSpring(scaleImage.value),
  };
});
```
Далее обмотайте компонент с помощью и измените проп на , чтобы пропустить .<Animated.Image><GestureDetector>style<Animated.Image>imageStyle
```
import { ImageSourcePropType, View } from 'react-native';
import { Gesture, GestureDetector } from 'react-native-gesture-handler';
import Animated, { useAnimatedStyle, useSharedValue, withSpring } from 'react-native-reanimated';

type Props = {
  imageSize: number;
  stickerSource: ImageSourcePropType;
};

export default function EmojiSticker({ imageSize, stickerSource }: Props) {
  const scaleImage = useSharedValue(imageSize);

  const doubleTap = Gesture.Tap()
    .numberOfTaps(2)
    .onStart(() => {
      if (scaleImage.value !== imageSize * 2) {
        scaleImage.value = scaleImage.value * 2;
      } else {
        scaleImage.value = Math.round(scaleImage.value / 2);
      }
    });

  const imageStyle = useAnimatedStyle(() => {
    return {
      width: withSpring(scaleImage.value),
      height: withSpring(scaleImage.value),
    };
  });

  return (
    <View style={{ top: -350 }}>
      <GestureDetector gesture={doubleTap}>
        <Animated.Image
          source={stickerSource}
          resizeMode="contain"
          style={[{ width: imageSize, height: imageSize }, imageStyle]}
        />
      </GestureDetector>
    </View>
  );
}
```
В приведённом выше фрагменте реквизит принимает значение для запуска жеста, когда пользователь дважды нажимает на изображение наклейки.gesture doubleTap

## Добавьте жест панорамы

Чтобы распознать жест перетаскивания на наклейке и отслеживать его движение, мы используем жест панорамы. В src/components/emoji-sticker.tsx:

Создайте две новые общие ценности: и .translateXtranslateY
Замените их на компонент.<View><Animated.View>
```
export default function EmojiSticker({ imageSize, stickerSource }: Props) {
  const scaleImage = useSharedValue(imageSize);
  const translateX = useSharedValue(0);
  const translateY = useSharedValue(0);
  // ...rest of the code remains same

  return (
    <Animated.View style={{ top: -350 }}>
      <GestureDetector gesture={doubleTap}>
        {/* ...rest of the code remains same */}
      </GestureDetector>
    </Animated.View>
  );
}
```
Давайте узнаем, что делает вышеуказанный код:

Определённые значения перевода будут перемещать стикер по экрану. Поскольку наклейка движется по обеим осям, нужно отслеживать значения X и Y.
В крючках мы установили обе переменные трансляции так, чтобы они имели начальное положение . Это начальное положение наклейки и отправная точка. Это значение задаёт начальное положение стикера при начале жеста.useSharedValue()0
На предыдущем этапе мы активировали обратный вызов для жеста tap, привязанного к методу. Для жеста панорамирования укажите обратный вызов, который выполняется, когда жест активен и движется.onStart()Gesture.Tap()onChange()

Создайте объект, который будет обрабатывать жест панорамирования. Обратный вызов принимается как параметр. и свойства сохраняют изменение положения с момента последнего события и обновляют значения, хранящиеся в и .dragonChange()eventchangeXchangeYtranslateXtranslateY
Определите объект с помощью крючка. Он вернёт массив преобразований. Для компонента нужно установить свойство значения и . Это меняет положение наклейки, когда жест активен.containerStyleuseAnimatedStyle()<Animated.View>transformtranslateXtranslateY
```
const drag = Gesture.Pan().onChange(event => {
  translateX.value += event.changeX;
  translateY.value += event.changeY;
});

const containerStyle = useAnimatedStyle(() => {
  return {
    transform: [
      {
        translateX: translateX.value,
      },
      {
        translateY: translateY.value,
      },
    ],
  };
});
```
Далее, внутри кода JSX:

Обновите компонент так, чтобы он стал компонентом верхнего уровня.<EmojiSticker><GestureDetector>
Добавьте на компонент, чтобы применить стили трансформации.containerStyle<Animated.View>
```
import { Gesture, GestureDetector } from 'react-native-gesture-handler';
import Animated, { useAnimatedStyle, useSharedValue, withSpring } from 'react-native-reanimated';
import { ImageSourcePropType } from 'react-native';

type Props = {
  imageSize: number;
  stickerSource: ImageSourcePropType;
};

export default function EmojiSticker({ imageSize, stickerSource }: Props) {
  const scaleImage = useSharedValue(imageSize);
  const translateX = useSharedValue(0);
  const translateY = useSharedValue(0);

  const doubleTap = Gesture.Tap()
    .numberOfTaps(2)
    .onStart(() => {
      if (scaleImage.value !== imageSize * 2) {
        scaleImage.value = scaleImage.value * 2;
      } else {
        scaleImage.value = Math.round(scaleImage.value / 2);
      }
    });

  const imageStyle = useAnimatedStyle(() => {
    return {
      width: withSpring(scaleImage.value),
      height: withSpring(scaleImage.value),
    };
  });

  const drag = Gesture.Pan().onChange(event => {
    translateX.value += event.changeX;
    translateY.value += event.changeY;
  });

  const containerStyle = useAnimatedStyle(() => {
    return {
      transform: [
        {
          translateX: translateX.value,
        },
        {
          translateY: translateY.value,
        },
      ],
    };
  });

  return (
    <GestureDetector gesture={drag}>
      <Animated.View style={[containerStyle, { top: -350 }]}>
        <GestureDetector gesture={doubleTap}>
          <Animated.Image
            source={stickerSource}
            resizeMode="contain"
            style={[{ width: imageSize, height: imageSize }, imageStyle]}
          />
        </GestureDetector>
      </Animated.View>
    </GestureDetector>
  );
}
```

# Сделайте скриншот
В этой главе мы узнаем, как сделать скриншот с помощью сторонней библиотеки и сохранить его в медиатеке устройства. Мы используем react-native-view-shot сделать скриншот и expo-media-library чтобы сохранить изображение в медиабиблиотеке устройства.
## Библиотеки установки
Для установки и запустите следующие команды:react-native-view-shotexpo-media-library
```
npx expo install react-native-view-shot expo-media-library
```

## Запрос на разрешения
Приложение, требующее конфиденциальной информации, например, доступ к медиатеке устройства, должно запросить разрешение на разрешение или отказ в доступе. Используя hook from , мы можем использовать разрешение и метод для запроса доступа. Этот крючок запрашивает как разрешения на чтение, так и на запись, что включает выбор изображений из библиотеки и сохранение скриншотов в неё.useMediaLibraryPermissions()expo-image-pickerpermissionResponserequestPermission()

Когда приложение загружается впервые, и статус разрешения не предоставлен и не отклонён, значение этого приложения равно . При запросе разрешения пользователь может либо предоставить разрешение, либо отказать в нём. Мы можем добавить условие, чтобы проверить, если оно не исполняется. Если не разрешено, активируйте метод. После получения доступа значение изменяется на .permissionResponsenullrequestPermission()permissionResponsegranted

Добавьте следующий фрагмент кода внутри src/app/(tabs)/index.tsx:

```
import { useEffect, useState } from 'react';
import * as ImagePicker from 'expo-image-picker';

// ...rest of the code remains same

export default function Index() {
  const [permissionResponse, requestPermission] = ImagePicker.useMediaLibraryPermissions();
  // ...rest of the code remains same

  useEffect(() => {
    if (!permissionResponse?.granted) {
      requestPermission();
    }
  }, []);

  // ...rest of the code remains same
}
```

## Создайте ссылку для сохранения текущего вида
Мы используем его, чтобы пользователь мог сделать скриншот внутри приложения. Эта библиотека запечатлевает скриншот изображения с помощью этого метода. Он возвращает URI файла с изображением скриншота.react-native-view-shot<View>captureRef()

Импорт из React и обратно.captureRefreact-native-view-shotuseRef
Создайте эталонную переменную для хранения ссылки на запечатлено изображение скриншота.imageRef
Оберните компоненты и внутри a и затем передайте ей опорную переменную.<ImageViewer><EmojiSticker><View>
```
import { useState, useRef } from 'react';
import { captureRef } from 'react-native-view-shot';

export default function Index() {
  const imageRef = useRef<View>(null);

  // ...rest of the code remains same

  return (
    <GestureHandlerRootView style={styles.container}>
      <View style={styles.imageContainer}>
        <View ref={imageRef} collapsable={false}>
          <ImageViewer imgSource={PlaceholderImage} selectedImage={selectedImage} />
          {pickedEmoji && <EmojiSticker imageSize={40} stickerSource={pickedEmoji} />}
        </View>
      </View>
      {/* ...rest of the code remains same */}
    </GestureHandlerRootView>
  );
}
```
В приведённом выше фрагменте реквизит установлен на . Это позволяет компоненту делать скриншоты только фонового изображения и наклейки эмодзи.collapsable
## Сделайте скриншот и сохраните его
Мы можем сделать скриншот представления, вызвав метод изнутри функции. Он принимает опциональный аргумент, при котором мы можем передать и области для захвата скриншотов. Подробнее о доступных вариантах можно прочитать в документации библиотеки.captureRef()react-native-view-shotonSaveImageAsync()widthheight

Метод также возвращает обещание, которое выполняет URI скриншота. Мы передадим этот URI в качестве параметра captureRef()MediaLibrary.saveToLibraryAsync() и сохранить скриншот в медиабиблиотеке устройства.

Внутри src/app/(tabs)/index.tsx обновите функцию следующим кодом:onSaveImageAsync()
import * as ImagePicker from 'expo-image-picker';
import * as MediaLibrary from 'expo-media-library';
import { useEffect, useRef, useState } from 'react';
import { ImageSourcePropType, StyleSheet, View } from 'react-native';
import { GestureHandlerRootView } from 'react-native-gesture-handler';
import { captureRef } from 'react-native-view-shot';

import Button from '@/components/button';
import CircleButton from '@/components/circle-button';
import EmojiList from '@/components/emoji-list';
import EmojiPicker from '@/components/emoji-picker';
import IconButton from '@/components/icon-button';
import ImageViewer from '@/components/image-viewer';

import EmojiSticker from '@/components/emoji-sticker';

const PlaceholderImage = require('@/assets/images/background-image.png');

export default function Index() {
  const [selectedImage, setSelectedImage] = useState<string | undefined>(
    undefined
  );
  const [showAppOptions, setShowAppOptions] = useState<boolean>(false);
  const [isModalVisible, setIsModalVisible] = useState<boolean>(false);
  const [pickedEmoji, setPickedEmoji] = useState<
    ImageSourcePropType | undefined
  >(undefined);
  const [permissionResponse, requestPermission] = ImagePicker.useMediaLibraryPermissions();
  const imageRef = useRef<View>(null);

  useEffect(() => {
    if (!permissionResponse?.granted) {
      requestPermission();
    }
  }, []);

  const pickImageAsync = async () => {
    let result = await ImagePicker.launchImageLibraryAsync({
      mediaTypes: ['images'],
      allowsEditing: true,
      quality: 1,
    });

    if (!result.canceled) {
      setSelectedImage(result.assets[0].uri);
      setShowAppOptions(true);
    } else {
      alert('You did not select any image.');
    }
  };

  const onReset = () => {
    setShowAppOptions(false);
  };

  const onAddSticker = () => {
    setIsModalVisible(true);
  };

  const onModalClose = () => {
    setIsModalVisible(false);
  };

  const onSaveImageAsync = async () => {
    try {
      const localUri = await captureRef(imageRef, {
        height: 440,
        quality: 1,
      });

      await MediaLibrary.saveToLibraryAsync(localUri);
      if (localUri) {
        alert('Saved!');
      }
    } catch (e) {
      console.log(e);
    }
  };

  return (
    <GestureHandlerRootView style={styles.container}>
      <View style={styles.imageContainer}>
        <View ref={imageRef} collapsable={false}>
          <ImageViewer imgSource={PlaceholderImage} selectedImage={selectedImage} />
          {pickedEmoji && <EmojiSticker imageSize={40} stickerSource={pickedEmoji} />}
        </View>
      </View>
      {showAppOptions ? (
        <View style={styles.optionsContainer}>
          <View style={styles.optionsRow}>
            <IconButton icon="refresh" label="Reset" onPress={onReset} />
            <CircleButton onPress={onAddSticker} />
            <IconButton icon="save-alt" label="Save" onPress={onSaveImageAsync} />
          </View>
        </View>
      ) : (
        <View style={styles.footerContainer}>
          <Button theme="primary" label="Choose a photo" onPress={pickImageAsync} />
          <Button label="Use this photo" onPress={() => setShowAppOptions(true)} />
        </View>
      )}
      <EmojiPicker isVisible={isModalVisible} onClose={onModalClose}>
        <EmojiList onSelect={setPickedEmoji} onCloseModal={onModalClose} />
      </EmojiPicker>
    </GestureHandlerRootView>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#25292e',
    alignItems: 'center',
  },
  imageContainer: {
    flex: 1,
  },
  footerContainer: {
    flex: 1 / 3,
    alignItems: 'center',
  },
  optionsContainer: {
    position: 'absolute',
    bottom: 80,
  },
  optionsRow: {
    alignItems: 'center',
    flexDirection: 'row',
  },
});
# Различия по платформам управления
Android, iOS и веб имеют разные возможности. В нашем случае и Android, и iOS могут сделать скриншот с помощью библиотеки. Однако веб-браузеры не могут.react-native-view-shot

В этой главе мы узнаем, как справляться с получением скриншотов для веб-браузеров, чтобы наше приложение имело одинаковую функциональность на всех платформах.
## Установка и импорт dom-to-image
Чтобы сделать скриншот в интернете и сохранить его как изображение, мы используем стороннюю библиотеку под названием dom-to-image. Он делает скриншот любого узла DOM и превращает его в векторное (SVG) или растровое (PNG или JPEG) изображение.

Остановите сервер разработки и выполните следующую команду для установки библиотеки:
```
npm install dom-to-image
```
После установки обязательно перезагрузите сервер разработки и нажмите в терминале.
## Добавить код, специфичный для платформы
Используя модуль из React Native, мы можем реализовать поведение, специфичное для платформы. Внутри src/app/(tabs)/index.tsx:Platform

Импортируйте модуль из .Platformreact-native
Импортируйте библиотеку из .domtoimagedom-to-image
Обновите функцию, чтобы проверить, связана ли текущая платформа с этим свойством. Если это так, мы используем метод для преобразования и захвата тока в формате JPEG-изображения. В противном случае мы продолжим использовать ту же логику, что и для нативных платформ.onSaveImageAsync()'web'Platform.OS'web'domtoimage.toJpeg()<View>
```
import * as ImagePicker from 'expo-image-picker';
import * as MediaLibrary from 'expo-media-library';
import { useEffect, useRef, useState } from 'react';
import { ImageSourcePropType, View, StyleSheet, Platform } from 'react-native';
import { GestureHandlerRootView } from 'react-native-gesture-handler';
import { captureRef } from 'react-native-view-shot';
import domtoimage from 'dom-to-image';

import Button from '@/components/button';
import ImageViewer from '@/components/image-viewer';
import IconButton from '@/components/icon-button';
import CircleButton from '@/components/circle-button';
import EmojiPicker from '@/components/emoji-picker';
import EmojiList from '@/components/emoji-list';
import EmojiSticker from '@/components/emoji-sticker';

const PlaceholderImage = require('@/assets/images/background-image.png');

export default function Index() {
  const [selectedImage, setSelectedImage] = useState<string | undefined>(undefined);
  const [showAppOptions, setShowAppOptions] = useState<boolean>(false);
  const [isModalVisible, setIsModalVisible] = useState<boolean>(false);
  const [pickedEmoji, setPickedEmoji] = useState<ImageSourcePropType | undefined>(undefined);
  const [permissionResponse, requestPermission] = ImagePicker.useMediaLibraryPermissions();
  const imageRef = useRef<View>(null);

  useEffect(() => {
    if (!permissionResponse?.granted) {
      requestPermission();
    }
  }, []);

  const pickImageAsync = async () => {
    let result = await ImagePicker.launchImageLibraryAsync({
      mediaTypes: ['images'],
      allowsEditing: true,
      quality: 1,
    });

    if (!result.canceled) {
      setSelectedImage(result.assets[0].uri);
      setShowAppOptions(true);
    } else {
      alert('You did not select any image.');
    }
  };

  const onReset = () => {
    setShowAppOptions(false);
  };

  const onAddSticker = () => {
    setIsModalVisible(true);
  };

  const onModalClose = () => {
    setIsModalVisible(false);
  };

  const onSaveImageAsync = async () => {
    if (Platform.OS !== 'web') {
      try {
        const localUri = await captureRef(imageRef, {
          height: 440,
          quality: 1,
        });

        await MediaLibrary.saveToLibraryAsync(localUri);
        if (localUri) {
          alert('Saved!');
        }
      } catch (e) {
        console.log(e);
      }
    } else {
      try {
        const dataUrl = await domtoimage.toJpeg(imageRef.current, {
          quality: 0.95,
          width: 320,
          height: 440,
        });

        let link = document.createElement('a');
        link.download = 'sticker-smash.jpeg';
        link.href = dataUrl;
        link.click();
      } catch (e) {
        console.log(e);
      }
    }
  };

  return (
    <GestureHandlerRootView style={styles.container}>
      <View style={styles.imageContainer}>
        <View ref={imageRef} collapsable={false}>
          <ImageViewer imgSource={PlaceholderImage} selectedImage={selectedImage} />
          {pickedEmoji && <EmojiSticker imageSize={40} stickerSource={pickedEmoji} />}
        </View>
      </View>
      {showAppOptions ? (
        <View style={styles.optionsContainer}>
          <View style={styles.optionsRow}>
            <IconButton icon="refresh" label="Reset" onPress={onReset} />
            <CircleButton onPress={onAddSticker} />
            <IconButton icon="save-alt" label="Save" onPress={onSaveImageAsync} />
          </View>
        </View>
      ) : (
        <View style={styles.footerContainer}>
          <Button theme="primary" label="Choose a photo" onPress={pickImageAsync} />
          <Button label="Use this photo" onPress={() => setShowAppOptions(true)} />
        </View>
      )}
      <EmojiPicker isVisible={isModalVisible} onClose={onModalClose}>
        <EmojiList onSelect={setPickedEmoji} onCloseModal={onModalClose} />
      </EmojiPicker>
    </GestureHandlerRootView>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#25292e',
    alignItems: 'center',
  },
  imageContainer: {
    flex: 1,
  },
  footerContainer: {
    flex: 1 / 3,
    alignItems: 'center',
  },
  optionsContainer: {
    position: 'absolute',
    bottom: 80,
  },
  optionsRow: {
    alignItems: 'center',
    flexDirection: 'row',
  },
});
```

# Настройте строку статуса, заставку и иконку приложения
В этой главе мы рассмотрим некоторые детали приложения перед развертыванием приложения в магазине приложений, такие как оформление строки статуса, настройка значка приложения и заставка.
## Настройте строку статуса
expo-status-bar Библиотека предустановленна в каждом проекте, созданном с использованием . Эта библиотека предоставляет компонент для настройки стиля строки статуса приложения.create-expo-appStatusBar
Внутри src/app/_layout.tsx:

Импортировать из .StatusBarexpo-status-bar
Сгруппируйте существующие компоненты с компонентом Fragment от React.StatusBarStack
```
import { Stack } from 'expo-router';
import { StatusBar } from 'expo-status-bar';

export default function RootLayout() {
  return (
    <>
      <Stack>
        <Stack.Screen name="(tabs)" options={{ headerShown: false }} />
      </Stack>
      <StatusBar style="light" />
    </>
  );
}
```

## Иконка приложения
Внутри проекта есть icon.png файл в папке ассетов и изображений. Это иконка нашего приложения. Это изображение размером 1024 пикселей на 1024 пикселей, и оно выглядит так.
Как и изображение заставки, свойство в файле app.json настраивает путь иконки приложения. По умолчанию новый проект Expo определяет правильный путь к . Нам не нужно ничего менять."icon"
Иконку можно увидеть в разных местах Expo Go. 
## Заставка
Перед загрузкой контента приложения отображается заставка. Он использует меньшее изображение, например иконку приложения, которая расположена по центру. Он скрывается, когда содержимое приложения готово к отображению.

The expo-splash-screen Плагин уже предустановлен в каждом проекте, созданном с использованием . Эта библиотека предоставляет конфигурационный плагин для настройки заставочного экрана.create-expo-app

В app.json году плагин уже настроен так, чтобы использовать иконку приложения в качестве изображения заставки (предоставленного в загружаемых ассетах) с следующим фрагментом, так что нам не нужно ничего менять:expo-splash-screen
```
{
  "plugins": [
    ... 
    [
      "expo-splash-screen", { "image": "./assets/images/splash-icon.png"
        ... 
      }
    ]
  ]
}
```
Однако для тестирования заставки мы не можем использовать Expo Go или билд для разработки. Чтобы проверить, нам нужно создать превью или производственную версию нашего приложения. Рекомендуем ознакомиться с следующими ресурсами, чтобы узнать больше о конфигурации заставки и способах её протестировать:

Создайте руководство по иконкам splash screen, чтобы узнать, как настраивается иконка splash screen.
Чтобы узнать, как создать предварительную сборку, ознакомьтесь с руководством по внутреннему распространению в EAS Tutorial, а чтобы создавать производственные сборки — в руководствах для Android и iOS.

# Учебные материалы
Теперь, когда примерное приложение готово, давайте узнаем больше о технологиях, которые мы использовали для его создания.
## Введите свой проект в приложение
Чтобы начать создавать новое приложение на вашем компьютере, вы можете последовательно использовать и настраивать среду разработки.npx create-expo-app@latest
## Рекомендуемые ресурсы
После создания нового проекта вы сможете узнать больше о различных инструментах и концепциях, которые помогут вам на пути разработки приложений:

Инструменты разработки: Справочник по инструментам Expo, которые помогут вам на различных этапах процесса создания приложений.
Сборки для разработки: использование сборки позволяет получить полный контроль над процессом создания приложения и тестировать его на устройстве или симуляторе.
Обзор разработки: Это общий обзор, который содержит подробную информацию о ключевых концепциях разработки приложения с Expo и процессе основного цикла разработки.
Expo Router: Мы изучили основы Expo Router и реализовали навигатор по вкладкам. Ознакомьтесь с документацией, чтобы узнать больше о библиотеке.
Иконка приложения и заставочный экран: вы можете узнать больше о том, как настраивать иконку приложения и инструкции по заставке. Также посмотрите ссылку на конфигурацию приложения на свойства, которые можно настроить в app.json файле.
Распространение и отправка приложений в магазины приложений: Прочитайте эти ресурсы, чтобы узнать больше о том, как выпустить и отправить приложение в магазины приложений, когда оно будет готово к отправке.
Отладка: Иногда что-то идёт не так, и когда это происходит, можно использовать инструменты отладки, чтобы найти и исправить ошибки.
## Обучение
### React
Мы использовали компоненты и API React. Глубокое понимание React крайне важно для использования Expo для создания вашего приложения. Рекомендуем ознакомиться с разделом Quick Start документации React и разделом Hooks.
### React Native
При разработке обучающего приложения мы активно использовали React Native. Вы можете начать с руководства по основам React Native, чтобы узнать больше. Также посмотрите следующие документы:

Просмотр ссылки API
Ссылка на текстовый API
Код, специфичный для платформы
Представление данных в списке
Мы использовали Flexbox для раскладки компонентов. Ознакомьтесь со следующими рекомендациями, чтобы узнать об этом больше:
Высота и ширина
Компоновка с Flexbox
### Жесты и анимации
Чтобы узнать больше о реализации различных типов жестов и анимации, мы рекомендуем следующую документацию:
Обработчик жестов React Native
React Native Reanimated