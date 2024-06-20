vite 는 다운로드 `npm create vite@latest`



1. Cesium 및 Resium 다운로드



`npm install cesium`

`npm install resium`


2. vite config 파일 설정
```
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';
import { viteStaticCopy } from 'vite-plugin-static-copy';

export default defineConfig({
  plugins: [
    react(),
    viteStaticCopy({
      targets: [
        {
          src: 'node_modules/cesium/Build/Cesium/Assets',
          dest: 'cesium'
        },
        {
          src: 'node_modules/cesium/Build/Cesium/Widgets',
          dest: 'cesium'
        },
        {
          src: 'node_modules/cesium/Build/Cesium/Workers',
          dest: 'cesium'
        },
        {
          src: 'node_modules/cesium/Build/Cesium/ThirdParty',
          dest: 'cesium'
        }
      ]
    })
  ],
  build: {
    rollupOptions: {
      output: {
        format: 'esm'
      }
    }
  }
});

```

3. 테스트 파일 생성
```
// eslint-disable-next-line @typescript-eslint/no-explicit-any
import { Viewer  ,Entity  } from 'resium';
import * as Cesium from 'cesium';
import 'cesium/Build/Cesium/Widgets/widgets.css';

window.CESIUM_BASE_URL = '/cesium';

Cesium.Camera.DEFAULT_VIEW_RECTANGLE = Cesium.Rectangle.fromDegrees(124.3188, 33, 132.3386, 38.64966);

Cesium.Ion.defaultAccessToken = '본인 ion 개인키 넣기';


export const CesiumView = () => {


  return (
    <Viewer 
        baseLayerPicker={false} //상단의 아이콘
        sceneModePicker={false} //상단의 지구본모양(모드바꾸는)
        timeline={false}//하단의 타임라인
        animation={false} //하단의 시간 표출하는거
        fullscreenButton={false} //하단의 전체화면 버튼
        geocoder={false} //상단의 검색창
        homeButton={false} //상단의 홈버튼
        navigationHelpButton={false} //상단의 도움말
        skyAtmosphere={false}
        infoBox={false}
        selectionIndicator={false}
        shouldAnimate
        // terrainProvider={terrainProvider}
        full
    >
        <Entity
          name="test"
          description="test!!"
          position={Cesium.Cartesian3.fromDegrees(-74.0707383, 40.7117244, 100)}
          point={{ pixelSize: 10 }}
        >      
      </Entity>
    </Viewer>
    )
}
```




