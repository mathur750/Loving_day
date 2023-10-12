# Loving Day

```
개발 툴 : Flutter
개발 언어 : Dart
개발 일시 : 2023-02-07 ~ 2023-02-09
개발자 : Won Chi Hyeon
```

## 앱 개요
```
기능 : 사용자가 직접 원하는 날짜를 선택할 수 있다.
       날짜 선택 시 실시간으로 화면의 D-Day 및 만난 날 업데이트
```

## 앱 최종 화면 및 기능
### [홈 화면]
![image](https://user-images.githubusercontent.com/58906858/217712284-8351bb9f-0b00-41ba-abd9-bcdf5ed7a9f3.png)

### [하트를 눌렀을 때 만난 날짜를 변경하는 기능]
![image](https://user-images.githubusercontent.com/58906858/217712434-cb8759d9-26b9-452b-8533-9b6d57d1051a.png)

### [만난 날짜가 변경된 홈 화면]
![image](https://user-images.githubusercontent.com/58906858/217712504-3725cb4c-d415-46d5-a638-8f291e4715c2.png)


## 필요한 이미지, 폰트 추가하기
[이미지, 폰트 다운로드 사이트](https://github.com/codefactory-co/golden-rabbit-flutter-novice/tree/main/ch09/u_and_i/asset)
```
프로젝트에 필요한 이미지와 폰트를 다운로드하여 추가해줍니다.
pubspec.yaml을 다음과 같이 수정합니다.
```
![image](https://user-images.githubusercontent.com/58906858/217136886-e1c07ce1-6f09-429b-b29c-64b8f7264762.png)

## 홈 화면 위젯을 두 개로 나누고 배치하기
```
Home Screen 화면 위젯 ui를 _DDay와 _CoupleImage stless 클래스 위젯을 생성하여 두 개로 나누고
Column을 사용해서 두 개를 화면의 양 끝으로 배치하였습니다.
```
![image](https://user-images.githubusercontent.com/58906858/217138393-372493d0-7c23-4951-a0ea-a52260d886d9.png)

## 핑크색 배경을 적용하고 _CoupleImage 위젯에 커플 이미지를 추가하기
```
Scaffold의 backgrounㅇ에서 배경색을 핑크색으로 변경하고
_CoupleImage 위젯에 asset/img/middle_image.png 커플 이미지를 Image.asset을 사용하여 추가해주었습니다.
MediaQuery로 MaterialApp의 화면 전체의 반의 크기를 차지하도록 설정하였습니다.
```
![image](https://user-images.githubusercontent.com/58906858/217140807-3b3d4bbd-a4c6-4cf4-baf7-0afdd044b3d6.png)

### [핑크색 배경과 커플 이미지를 적용한 모습]
![image](https://user-images.githubusercontent.com/58906858/217141040-5db7418b-4330-4ece-bd50-4827dded6e0c.png)

## 상단 텍스트 추가
```
앱 상단에는 여러 Text 위젯과 하트 아이콘 위젯으로 이루어져 있습니다.

사귀기 시작한 날짜와 며칠이 지났는지 표시하는 글자는 날짜가 변경될 때마다 
자동으로 바뀌게 코딩해야 하지만 일단은 임의의 글자들을 넣어두었습니다.
```
![image](https://user-images.githubusercontent.com/58906858/217420055-4b96f0b4-ad36-413c-b3a1-19ff2b42ebc1.png)

## Theme을 사용하여 텍스트 스타일 지정하기
```
Text 위젯에 스타일을 Theme을 사용하여 지정할 수 있습니다.

fontFamily : 기본 글씨체를 지정
textTheme : Text 위젯 테마를 지정

headline1, bodyText1, bodyText2, headline2 임의의 스타일명을 지정해주고
각 스타일명에 따라 적용할 스타일을 지정해줍니다.

테마를 불러오고 각 Text위젯에 스타일을 적용해줍니다.
```
### [텍스트 테마 생성]
![image](https://user-images.githubusercontent.com/58906858/217424134-cced2716-507c-4a5a-a4dd-ef001fcbbc24.png)

### [텍스트 테마 적용 (일부)]
![image](https://user-images.githubusercontent.com/58906858/217424345-9e0ffaac-d32f-48e3-8271-0affbf378a7c.png)   
![image](https://user-images.githubusercontent.com/58906858/217424224-bba39329-7d2e-402f-9157-0b1f85ddb6c0.png)

### [테마를 적용한 후]
![image](https://user-images.githubusercontent.com/58906858/217423985-aec5380d-a555-49d6-8587-de738f6497d2.png)

## 다양한 화면의 비율과 해상도에 따른 오버플로 해결하기
```
글자 크기를 변경하는 과정에서 화면의 반이상을 차지하게 되어 밑 공간의 이미지가
화면의 반 MediaQuery.of(context).size.height/2을 차지할 수 없게 되어 화면 밖으로 나가게 되는
overflow 오버플로 현상이 발생하였습니다. 텍스트나 이미지의 크기를 변경하거나 Expanded로 감싸서
문제를 해결할 수 있는 데 Expanded로 이미지의 Center 위젯을 감싸서 문제를 해결하였습니다.
```
### [오버플로 overflow 현상 발생]
![image](https://user-images.githubusercontent.com/58906858/217424813-0f1a2312-d45b-41cb-b137-2642f27b6e68.png)

### [이미지의 Center 위젯을 Expanded로 감싸서 문제 해결]
![image](https://user-images.githubusercontent.com/58906858/217425582-bfb0f7dd-ffc5-4ff4-8caf-9d689a85cb8e.png)

## 하트 아이콘의 콜백 함수 생성
```
setState()를 사용한 상태관리를 하기 위해 HomeScreen을 stless 위젯에서 stful 위젯으로 변환합니다.

하트를 눌렀을 때 날짜를 고를 수 있는 UI가 나오며 날짜가 변경될 때마다 firstDay를 변경하기 위해서
firstDay를 오늘 날짜로 초기화하고 하트 아이콘에 onPressedHeart 함수를 호출하는 데 이를 생성자로 받기 위해서
콜백 함수 형태로 만들었습니다. 하트를 눌렀을 때 클릭이 출력되도록 설정하고 테스트하였습니다.
```
### [하트를 눌렀을 때]
![image](https://user-images.githubusercontent.com/58906858/217429282-cd879d8d-c464-4855-ba32-3b2fe73a2058.png)

## 만나기 시작한 날짜 렌더링
```
만나기 시작한 날짜 firstDay를 생성자로 전달받아서 텍스트 위젯에 Datetime을 년.월.일 형태로 텍스트 바인딩을 사용해서
변경하였습니다.
```
### [만나기 시작한 날짜 (firstDay 오늘 날)
![image](https://user-images.githubusercontent.com/58906858/217430885-633aae93-8621-4342-aa6b-30c16b98a568.png)

## 만난 후 며칠 지났는 지 날짜 출력 (DDay)
```
현재 날짜에서 만난 날 날짜를 빼면 며칠 지났는 지가 나오고 그 기간 차이를 일수로 계산하고 (inDays) 1을 더해주었습니다.
현재 날짜를 now 변수에 저장하고 만난 날 날짜 firstDay의 차이(Difference)를 계산하여 출력하였습니다.
```
![image](https://user-images.githubusercontent.com/58906858/217431636-f9a33307-e473-4557-bd1b-ca86bafb08fc.png)   
![image](https://user-images.githubusercontent.com/58906858/217431687-9478920a-2f36-45ca-86c4-1f628260355b.png)   
![image](https://user-images.githubusercontent.com/58906858/217431762-de25e149-d1f4-441e-a76d-d82fc1b87b81.png)

## 하트에 만난 날짜가 감소하는 기능 추가하기
```
하트를 눌렀을 때(상태변화) setState() 함수가 호출되고 만난 날짜에서 하루가 감소되고
그 영향으로 D-Day가 하루씩 늘어나도록 기능을 추가하였습니다.
```
![image](https://user-images.githubusercontent.com/58906858/217709130-afa57bf3-02ed-4d95-af25-1c1227f78faa.png)
### [하트를 눌렀을 때]
![image](https://user-images.githubusercontent.com/58906858/217709193-19430727-35cd-42a4-a5a2-9cf216ce4873.png)

## 하트에 만난 날짜를 선택하는 쿠퍼티노 다이얼로그 추가
```
하트에 실제로 적용할 기능은 하트를 탭햇을 때 만난 날짜를 설정할 수 있는 다이얼로그를
보여주고 날짜를 탭하고 화면 밖을 탭했을 때 만난 날짜가 설정한 날짜로 수정되도록 하는 기능입니다.

따라서 onHeartPressed 함수에 날짜만 선택할 수 있는 쿠퍼티노 다이얼로그를 생성합니다.
```
![image](https://user-images.githubusercontent.com/58906858/217710778-7db324dd-738c-4178-9fcc-57a69d9a4ed0.png)
### [하트를 눌렀을 때]
![image](https://user-images.githubusercontent.com/58906858/217710804-ac0db7ab-0a0f-429a-b2dd-d51f0656b1db.png)

## 설정한 날짜로 만난 날짜 변경하기
```
하트를 탭햇을 때 상태 관리 setState()를 사용해서 만난 날짜를 선택한 날짜가 되도록 수정하였습니다.
쿠퍼티노 다이얼로그를 변경할 때마다 만난 날짜와 DDay가 새로 업데이트됩니다.
```
![image](https://user-images.githubusercontent.com/58906858/217711280-bd3e1947-7ccf-4034-a4aa-2325ba22f557.png)
