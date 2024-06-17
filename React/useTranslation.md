#useTranslation?
해당 정보를 알기위해선 React-i18next에 대하여 알 필요가 있다

##i18next?
다국어 관리를 위한 프레임워크 
1. 모든 번역과 사용한 언어를 전달함
2. 전달한 번역을 바탕으로 올바른 번역을 반환하고 복수형 및 보간에 대한 값을 제공하는 함수를 호출함

### 사용법?
1. src 폴더에 i18n 폴더 생성
2. 해당 폴더 밑에 index.js 폴더 생성
```
// import React from "react";
// import ReactDOM from "react-dom";
import i18n from "i18next";
import { initReactI18next } from "react-i18next";
import en from './locales/en';
import ko from './locales/ko';

i18n
  .use(initReactI18next) // passes i18n down to react-i18next
  .init({
    // the translations
    // (tip move them in a JSON file and import them,
    // or even better, manage them via a UI: https://react.i18next.com/guides/multiple-translation-files#manage-your-translations-with-a-management-gui)
    resources: {
        en:en,
        ko,ko
    },
    lng: "en", // if you're using a language detector, do not define the lng option
    fallbackLng: "en",
    ns:['page'],
    interpolation: {
      escapeValue: false
    }
  });

  export default i18n
   ```

3. 각 언어에 대한 json 파일 생성
4. 적용할 컴포너트에 `import {useTranslation from react-i18next` 선언
5. 사용은 아래와 같이 사용


```
const { t } = useTranslation();
....
<h2>{t('page:startPage')}</h2>
```


6. 언어변경은 `i18n.changeLanguage(lang)` 이렇게 진행
   
