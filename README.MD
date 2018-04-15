# Getty Image Viewer

### 개발환경

* macOS Sierra 10.12 or Later
* XCode 9.0

### 목표 운영체제

* iOS 9.0 or later

## 구현 조건

* Getty Image Gallery의 이미지 목록을 받아와 썸네일 이미지를 터치하면 사진의 상세 정보를 표시하는 화면으로 이동.
* 메모리 캐시와 디스크 캐시를 구현해야 함.

## 구현내용

* 캐시 구현내용
  * HomeImageObject.swift의 loadImage 함수를 통해 확인할 수 있음.
  * 이미지를 호출할 경우 캐시, 로컬, 다운로드[^1] 의 순서로 이미지를 확인함.
  * 다운로드가 완료될 경우 캐시와 로컬에 각각 저장한다.
* 이미지 목록 뷰어
  * 네트워크 연결이 되지 않을 경우 오류 팝업을 띄우도록 구현
  * UICollectionView를 이용하여 그리드 형태의 이미지 목록 뷰어를 작성
  * 좌측 상단의 버튼 혹은 콜렉션 뷰를 아래로 당겨 리로드 할 수 있도록 함.
* 이미지 상세화면
  * 기저장된 이미지가 없을 경우 썸네일을 먼저 노출하고 이미지를 다운로드하여 교체하여 표시하도록 함.
  * 1회 터치할 경우 네비게이션과 툴바가 감춰지고, 핀치 줌/아웃 또는 더블 탭을 이용해 이미지를 줌 할 수 있도록 함.
  * 스와이프를 할 경우 이전 또는 다음 이미지로 이동할 수 있도록 함.
  * 하단 메뉴바를 이용하여 이미지를 저장하거나, 이미지의 정보를 표시할 수 있도록 함.
* 설정 화면
  * 현재 이미지가 저장된 디렉토리의 총 용량을 표시하도록 함.
  * 해당 셀을 터치할 경우 저장된 이미지를 삭제하여 기기의 저장공간을 확보함.
* 기타
  * 다국어(영어/한국어) 적용.

[^1]: 원본 이미지의 다운로드가 필요할 경우, 우선 썸네일 이미지를 반환하여 미리 보이고, 다운로드가 완료된 후 교체하여 원본 이미지를 표시하도록 함.

## 사용 라이브러리

* CocoaPods (MIT)
* RxSwift (MIT)
* RxAlamofire (MIT)
* fastlane (MIT)
* HTMLReader (Public domain)
* HTMLString (MIT)
* KRProgressHUD (MIT)
* ReachabilitySwift (MIT)