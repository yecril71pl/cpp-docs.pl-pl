---
title: Klasa CKeyFrame
ms.date: 11/04/2016
f1_keywords:
- CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboard
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboardAfterTransition
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboardAtOffset
- AFXANIMATIONCONTROLLER/CKeyFrame::GetExistingKeyframe
- AFXANIMATIONCONTROLLER/CKeyFrame::GetOffset
- AFXANIMATIONCONTROLLER/CKeyFrame::GetTransition
- AFXANIMATIONCONTROLLER/CKeyFrame::m_offset
- AFXANIMATIONCONTROLLER/CKeyFrame::m_pExistingKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::m_pTransition
helpviewer_keywords:
- CKeyFrame [MFC], CKeyFrame
- CKeyFrame [MFC], AddToStoryboard
- CKeyFrame [MFC], AddToStoryboardAfterTransition
- CKeyFrame [MFC], AddToStoryboardAtOffset
- CKeyFrame [MFC], GetExistingKeyframe
- CKeyFrame [MFC], GetOffset
- CKeyFrame [MFC], GetTransition
- CKeyFrame [MFC], m_offset
- CKeyFrame [MFC], m_pExistingKeyFrame
- CKeyFrame [MFC], m_pTransition
ms.assetid: d050a562-20f6-4c65-8ce5-ccb3aef1a20e
ms.openlocfilehash: f535503338a82c7cc70455ae6a08cdab0f13c624
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372290"
---
# <a name="ckeyframe-class"></a>Klasa CKeyFrame

Reprezentuje klatkę kluczową animacji.

## <a name="syntax"></a>Składnia

```
class CKeyFrame : public CBaseKeyFrame;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CKeyFrame::CKeyFrame](#ckeyframe)|Przeciążone. Tworzy klatkę kluczową, która zależy od innej klatki kluczowej.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CKeyFrame::Płyta AddToStory](#addtostoryboard)|Dodaje klatkę kluczową do scenorysu. (Zastępuje [CBaseKeyFrame::AddToStoryboard](../../mfc/reference/cbasekeyframe-class.md#addtostoryboard).)|
|[CKeyFrame::AddToStoryboardPotransition](#addtostoryboardaftertransition)|Dodaje klatkę kluczową do scenorysu po przejściu.|
|[CKeyFrame::AddToStoryboardAtOffset](#addtostoryboardatoffset)|Dodaje klatkę kluczową do scenorysu z przesunięciem.|
|[CKeyFrame::GetExistingKeyframe](#getexistingkeyframe)|Zwraca wskaźnik do klatki kluczowej, odkierować klatki kluczowej.|
|[CKeyFrame::GetOffset](#getoffset)|Zwraca przesunięcie z innej klatki kluczowej.|
|[CKeyFrame::GetTransition](#gettransition)|Zwraca wskaźnik do przejścia, od które zależy ta klatka kluczowa.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CKeyFrame::m_offset](#m_offset)|Określa przesunięcie tej klatki kluczowej z klatki kluczowej przechowywanej w m_pExistingKeyFrame.|
|[CKeyFrame::m_pExistingKeyFrame](#m_pexistingkeyframe)|Przechowuje wskaźnik do istniejącego keframe. Ta klatka kluczowa jest dodawana do scenorysu z m_offset do istniejącej klatki kluczowej.|
|[CKeyFrame::m_pTransition](#m_ptransition)|Przechowuje wskaźnik do transcji, który rozpoczyna się w tej klatce kluczowej.|

## <a name="remarks"></a>Uwagi

Ta klasa implementuje klatkę kluczową animacji. Klatka kluczowa reprezentuje moment w czasie w scenorysie i może służyć do określania czasów rozpoczęcia i zakończenia przejść. Klatka kluczowa może być oparta na innej klatce kluczowej i mieć od niej przesunięcie (w sekundach) lub może opierać się na przejściu i przedstawiać moment w czasie, gdy to przejście się kończy.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CBaseKeyFrame (CBaseKeyFrame)](../../mfc/reference/cbasekeyframe-class.md)

[CKeyFrame (Klatka klucza)](../../mfc/reference/ckeyframe-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

## <a name="ckeyframeaddtostoryboard"></a><a name="addtostoryboard"></a>CKeyFrame::Płyta AddToStory

Dodaje klatkę kluczową do scenorysu.

```
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Wskaźnik do scenorysu.

*bDeepAdd*<br/>
Określa, czy klatka kluczowa lub przejście mają być cyklicznie dodane.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli klatka kluczowa została pomyślnie dodana.

### <a name="remarks"></a>Uwagi

Ta metoda dodaje klatkę kluczową do scenorysu. Jeśli zależy to od innej klatki kluczowej lub przejścia, a bDeepAdd ma wartość TRUE, ta metoda próbuje dodać je rekursywnie.

## <a name="ckeyframeaddtostoryboardaftertransition"></a><a name="addtostoryboardaftertransition"></a>CKeyFrame::AddToStoryboardPotransition

Dodaje klatkę kluczową do scenorysu po przejściu.

```
BOOL AddToStoryboardAfterTransition(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Wskaźnik do scenorysu.

*bDeepAdd*<br/>
Określa, czy przejście ma być cyklicznie dodawany.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli klatka kluczowa została pomyślnie dodana.

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana przez platformę, aby dodać klatkę kluczową do scenorysu po przejściu.

## <a name="ckeyframeaddtostoryboardatoffset"></a><a name="addtostoryboardatoffset"></a>CKeyFrame::AddToStoryboardAtOffset

Dodaje klatkę kluczową do scenorysu z przesunięciem.

```
virtual BOOL AddToStoryboardAtOffset(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Wskaźnik do scenorysu.

*bDeepAdd*<br/>
Określa, czy klatka kluczowa, od których ma być dodana klatka kluczowa, zależy rekursywnie.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli klatka kluczowa została pomyślnie dodana.

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana przez platformę, aby dodać klatkę kluczową do scenorysu z przesunięciem.

## <a name="ckeyframeckeyframe"></a><a name="ckeyframe"></a>CKeyFrame::CKeyFrame

Tworzy klatkę kluczową, która zależy od przejścia.

```
CKeyFrame(CBaseTransition* pTransition);

CKeyFrame(
    CBaseKeyFrame* pKeyframe,
    UI_ANIMATION_SECONDS offset = 0.0);
```

### <a name="parameters"></a>Parametry

*pTransition (tłumaczenie na pTransition)*<br/>
Wskaźnik do przejścia.

*pKeyframe (klatka klucza)*<br/>
Wskaźnik do klatki kluczowej.

*Przesunięcie*<br/>
Przesunięcie w sekundach z klatki kluczowej określonej przez pKeyframe.

### <a name="remarks"></a>Uwagi

Skonstruowana klatka kluczowa będzie reprezentować moment w czasie w czas w scenorysu po zakończeniu określonego przejścia.

## <a name="ckeyframegetexistingkeyframe"></a><a name="getexistingkeyframe"></a>CKeyFrame::GetExistingKeyframe

Zwraca wskaźnik do klatki kluczowej, odkierować klatki kluczowej.

```
CBaseKeyFrame* GetExistingKeyframe();
```

### <a name="return-value"></a>Wartość zwracana

Prawidłowy wskaźnik do klatki kluczowej lub NULL, jeśli ta klatka kluczowa nie zależy od innej klatki kluczowej.

### <a name="remarks"></a>Uwagi

Jest to akcesor do klatki kluczowej, odkierować ta klatka kluczowa.

## <a name="ckeyframegetoffset"></a><a name="getoffset"></a>CKeyFrame::GetOffset

Zwraca przesunięcie z innej klatki kluczowej.

```
UI_ANIMATION_SECONDS GetOffset();
```

### <a name="return-value"></a>Wartość zwracana

Przesunięcie w sekundach od innej klatki kluczowej.

### <a name="remarks"></a>Uwagi

Ta metoda powinna być wywoływana w celu określenia odsunięcia w sekundach od innej klatki kluczowej.

## <a name="ckeyframegettransition"></a><a name="gettransition"></a>CKeyFrame::GetTransition

Zwraca wskaźnik do przejścia, od które zależy ta klatka kluczowa.

```
CBaseTransition* GetTransition();
```

### <a name="return-value"></a>Wartość zwracana

Prawidłowy wskaźnik do przejścia lub NULL, jeśli ta klatka kluczowa nie zależy od przejścia.

### <a name="remarks"></a>Uwagi

Jest to akcesor do przejścia, od które zależy ta klatka kluczowa.

## <a name="ckeyframem_offset"></a><a name="m_offset"></a>CKeyFrame::m_offset

Określa przesunięcie tej klatki kluczowej z klatki kluczowej przechowywanej w m_pExistingKeyFrame.

```
UI_ANIMATION_SECONDS m_offset;
```

## <a name="ckeyframem_pexistingkeyframe"></a><a name="m_pexistingkeyframe"></a>CKeyFrame::m_pExistingKeyFrame

Przechowuje wskaźnik do istniejącego keframe. Ta klatka kluczowa jest dodawana do scenorysu z m_offset do istniejącej klatki kluczowej.

```
CBaseKeyFrame* m_pExistingKeyFrame;
```

## <a name="ckeyframem_ptransition"></a><a name="m_ptransition"></a>CKeyFrame::m_pTransition

Przechowuje wskaźnik do transcji, który rozpoczyna się w tej klatce kluczowej.

```
CBaseTransition* m_pTransition;
```

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
