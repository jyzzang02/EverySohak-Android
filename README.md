# 에브리소학 (EverySohak)

학생회 구성원의 일정, 예산, 회계 및 행사 관련 업무를 한 곳에서 관리하기 위해 개발한 **Kotlin 기반 Android 팀 프로젝트**입니다.

> 한국항공대학교 팀 프로젝트  
> 팀원: 강민재 · 권아영 · 김재영

---

## 주요 기능

- 학생회 일정 및 할 일 관리
- 예산 항목 등록·수정·삭제
- 회계 내역 관리
- 행사 및 장소 관련 정보 관리
- Firebase 기반 데이터 저장 및 조회
- Google Maps API를 활용한 위치 기능

---

## Tech Stack

- **Language**: Kotlin
- **IDE**: Android Studio
- **Architecture**: MVVM
- **Android Jetpack**: ViewModel, LiveData, Fragment, Navigation
- **Data**: Firebase Realtime Database, Firebase Storage
- **API**: Google Maps API
- **Collaboration**: Git, GitHub, Pull Request

---

## MVVM Architecture

화면과 데이터 처리 로직의 결합도를 낮추기 위해 **MVVM 패턴**을 적용했습니다.

```text
View (Fragment)
      ↓
ViewModel
      ↓
Repository
      ↓
Firebase Realtime Database
```

예산 관리 기능은 다음과 같이 역할을 분리했습니다.

- **View**: `BudgetFragment`
  - 사용자 입력 처리
  - ViewModel의 LiveData 관찰
  - RecyclerView 화면 갱신

- **ViewModel**: `BudgetViewModel`
  - UI에 필요한 상태 관리
  - Repository에 데이터 작업 요청
  - LiveData를 통해 View에 데이터 전달

- **Repository**: `BudgetRepository`
  - Firebase Realtime Database 접근
  - 예산 데이터 등록·조회·수정·삭제 처리

캘린더와 회계 기능에서도 ViewModel과 Repository를 분리해 화면 로직과 데이터 처리 로직을 나누었습니다.

---

## 적용 예시

### Budget

```text
BudgetFragment
      ↓
BudgetViewModel
      ↓
BudgetRepository
      ↓
Firebase
```

`BudgetViewModel`에서 `LiveData`와 `MutableLiveData`로 예산 목록 상태를 관리하고, 실제 Firebase 접근은 `BudgetRepository`에서 처리하도록 구성했습니다.

### Calendar

`CalendarViewModel`에서 선택 날짜와 일정 목록을 LiveData로 관리하고, `CalendarTaskRepository`를 통해 Firebase 데이터 저장 및 조회를 수행합니다.

---

## Git Collaboration

GitHub를 이용해 기능별 작업을 나누고 Pull Request 기반으로 협업했습니다.

1. 각자 브랜치에서 기능 개발
2. Pull Request 작성 후 팀원에게 공유
3. 코드 확인 및 의견 교환
4. 합의 후 develop 브랜치에 merge

프로젝트 후반에는 기존 코드를 MVVM 구조에 맞게 리팩터링하고 Repository 계층을 추가해 Firebase 접근 로직을 분리했습니다.

관련 커밋 예시:
- `MVVM, FireBase 완성`
- `MVVM을 위해 repository 추가`
- `BudgetRepository 추가`
- `Cash MVVM 수정`

---

## What I Learned

이 프로젝트를 통해 Android 앱에서 **View · ViewModel · Repository의 역할을 분리해 화면 로직과 데이터 처리 로직을 나누는 방식**을 경험했습니다.

또한 GitHub Pull Request를 기반으로 팀원들과 기능별 작업을 나누고, 기존 코드를 MVVM 구조에 맞게 리팩터링하는 과정을 경험했습니다.
