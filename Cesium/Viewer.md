<h2> Viewer </h2> 
애플리케이션 구축을 위한 기본 위젯, 모든 표준 세슘 위젯을 하나의 재사용 가능한 패키지로 통합합니다. <br>
다양한 애플리케이션에 유용한 기능을 추가하는 믹스인을 사용하여 위젯을 확장시킬 수 있습니다.<br>

<h3>Member</h3>

|이름|유형|기본값|설명|
|:---:|:---:|:--:|:-----:|
|animation|boolean|true|false로 설정시, 애니메이션 위젯이 생성되지 않습니다.|
|baseLayerPicker|boolean|true|false로 설정시, baseLayerPicker 위젯이 생성되지 않습니다.|
|fullscreenButton|boolean|true|false로 설정시, fullscreenButton 위젯이 생성되지 않습니다.|
|vrButton|boolean|false|false로 설정시, vrButton 위젯이 생성되지 않습니다.|
|geocoder|boolean|true|false로 설정시, geocoder 위젯이 생성되지 않습니다.|
|homeButton|boolean|true|false로 설정시, homeButton 위젯이 생성되지 않습니다.|
|infoBox|boolean|true|false로 설정시, infoBox 위젯이 생성되지 않습니다.|
|sceneModePicker|boolean|true|false로 설정시, sceneModePicker 위젯이 생성되지 않습니다.|
|selectionIndicator|boolean|true|false로 설정시, selectionIndicator 위젯이 생성되지 않습니다.|
|timeline|boolean|true|false로 설정시, timeline 위젯이 생성되지 않습니다.|
|navigationHelpButton|boolean|true|false로 설정시, 탐색 도움말 버튼이 생성되지 않습니다.|
|navigationInstructionsInitiallyVisible|true|boolean|탐색 지침이 처음에 표시되어야하면 true, 사용자가 버튼을 명시적으로 클릭할 때 까지 표시되지 않아야하면 false 입니다.|
|scene3DOnly|boolean|false|true 이면 각 geometry instancesms GPU 메모리 절약을 위해 3D로만 렌더링 됩니다. |
|shouldAnimate|boolean|false|true 시계가 기본적으로 시뮬레이션 시간을 앞당기려고 시도해야하는경우, false 이옵션은 설정보다 우선|
|clockViewModel|boolean|new ClockViewModel(clock)|햔제시간을 제어하는데 사용하는 시계보기 모|
|selectedImageryProviderViewModel|boolean||현재 기본 이미지 레이어에 대한 뷰 모델이 제공되지 않은 경우, 사용가능한 첫번째 레이어가 사용됩니다. 이값은 'baseLayerPicker'가 true로 설정된 경우에만 유효합니다.|
|imageryProviderViewModels|boolean|createDefaultImageryProviderViewModels()|BaseLayerPicker에서 선택할 수 있는 ProviderViewModel 배열입니다. 이 값은 'baseLayerPicker'가 true로 설정된 경우에만 유효합니다.|
|selectedTerrainProviderViewModel|boolean|true|현재 기본 지형 레이어에 대한 뷰 모델이 제공되지 않은 경우 사용 가능한 첫 번째 기본 레이어가 사용됩니다. 이 값은 'baseLayerPicker'가 true로 설정된 경우에만 유효합니다.|

