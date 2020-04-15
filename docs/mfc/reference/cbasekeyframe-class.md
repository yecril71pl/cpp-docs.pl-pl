---
title: Klasa CBaseKeyFrame
ms.date: 11/04/2016
f1_keywords:
- CBaseKeyFrame
- AFXANIMATIONCONTROLLER/CBaseKeyFrame
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::CBaseKeyFrame
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::AddToStoryboard
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::GetAnimationKeyframe
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::IsAdded
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::IsKeyframeAtOffset
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::m_bAdded
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::m_bIsKeyframeAtOffset
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::m_keyframe
helpviewer_keywords:
- CBaseKeyFrame [MFC], CBaseKeyFrame
- CBaseKeyFrame [MFC], AddToStoryboard
- CBaseKeyFrame [MFC], GetAnimationKeyframe
- CBaseKeyFrame [MFC], IsAdded
- CBaseKeyFrame [MFC], IsKeyframeAtOffset
- CBaseKeyFrame [MFC], m_bAdded
- CBaseKeyFrame [MFC], m_bIsKeyframeAtOffset
- CBaseKeyFrame [MFC], m_keyframe
ms.assetid: 285a2eff-e7c4-43be-b5aa-737727e6866d
ms.openlocfilehash: 3fcd55f6a157f4b837090a3608fb509b870aae5d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352988"
---
# <a name="cbasekeyframe-class"></a>Klasa CBaseKeyFrame

Implementuje podstawowe funkcje klatki kluczowej.

## <a name="syntax"></a>Składnia

```
class CBaseKeyFrame : public CObject;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBaseKeyFrame::CBaseKeyFrame](#cbasekeyframe)|Konstruuje obiekt klatki kluczowej.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBaseKeyFrame::Płyta AddToStory](#addtostoryboard)|Dodaje klatkę kluczową do scenorysu.|
|[CBaseKeyFrame::GetAnimationKeyframe](#getanimationkeyframe)|Zwraca podstawową wartość klatki kluczowej.|
|[CBaseKeyFrame::Isadded](#isadded)|Określa, czy klatka kluczowa została dodana do scenorysu.|
|[CBaseKeyFrame::IsKeyframeAtOffset](#iskeyframeatoffset)|Określa, czy klatka kluczowa ma zostać dodana do scenorysu z przesunięciem, czy po przejściu.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CBaseKeyFrame::m_bAdded](#m_badded)|Określa, czy ta klatka kluczowa została dodana do scenorysu.|
|[CBaseKeyFrame::m_bIsKeyframeAtOffset](#m_biskeyframeatoffset)|Określa, czy ta klatka kluczowa ma zostać dodana do scenorysu z przesunięciem od innej istniejącej klatki kluczowej, czy na końcu niektórych przejść.|
|[CBaseKeyFrame::m_keyframe](#m_keyframe)|Reprezentuje klatkę kluczową interfejsu API animacji systemu Windows. Gdy klatka kluczowa nie jest inicjowana, jest ustawiona na wstępnie zdefiniowaną wartość UI_ANIMATION_KEYFRAME_STORYBOARD_START.|

## <a name="remarks"></a>Uwagi

Hermetyzuje zmienną UI_ANIMATION_KEYFRAME. Służy jako klasa podstawowa dla każdej implementacji klatki kluczowej. Klatka kluczowa reprezentuje moment w czasie w scenorysie i może służyć do określania czasów rozpoczęcia i zakończenia przejść. Istnieją dwa typy klatek kluczowych - klatki kluczowe dodawane do scenorysu z określonym przesunięciem (w czasie) lub klatki kluczowe dodane po określonym przejściu. Ponieważ czas trwania niektórych przejść nie może być znany przed rozpoczęciem animacji, rzeczywiste wartości niektórych klatek kluczowych są określane tylko w czasie wykonywania. Ponieważ klatki kluczowe mogą zależeć od przejść, które z kolei zależą od klatek kluczowych, ważne jest, aby zapobiec nieskończonym powtarzaniom podczas tworzenia łańcuchów klatek kluczowych.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CBaseKeyFrame`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

## <a name="cbasekeyframeaddtostoryboard"></a><a name="addtostoryboard"></a>CBaseKeyFrame::Płyta AddToStory

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
Jeśli ten parametr ma wartość PRAWDA, a dodawana klatka kluczowa zależy od innej klatki kluczowej lub przejścia, ta metoda próbuje najpierw dodać tę klatkę kluczową lub przejście do scenorysu.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli klatka kluczowa została pomyślnie dodana do scenorysu; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana, aby dodać klatkę kluczową do scenorysu.

## <a name="cbasekeyframecbasekeyframe"></a><a name="cbasekeyframe"></a>CBaseKeyFrame::CBaseKeyFrame

Konstruuje obiekt klatki kluczowej.

```
CBaseKeyFrame();
```

## <a name="cbasekeyframegetanimationkeyframe"></a><a name="getanimationkeyframe"></a>CBaseKeyFrame::GetAnimationKeyframe

Zwraca podstawową wartość klatki kluczowej.

```
UI_ANIMATION_KEYFRAME GetAnimationKeyframe() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca klatka kluczowa. Wartość domyślna jest UI_ANIMATION_KEYFRAME_STORYBOARD_START.

### <a name="remarks"></a>Uwagi

Jest to akcesor do podstawowej wartości klatki kluczowej.

## <a name="cbasekeyframeisadded"></a><a name="isadded"></a>CBaseKeyFrame::Isadded

Określa, czy klatka kluczowa została dodana do scenorysu.

```
BOOL IsAdded() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli klatka kluczowa zostanie dodana do scenorysu; otehrwise FALSE.

### <a name="remarks"></a>Uwagi

W klasie podstawowej IsAdded zawsze zwraca true, ale jest zastępowany w klasach pochodnych.

## <a name="cbasekeyframeiskeyframeatoffset"></a><a name="iskeyframeatoffset"></a>CBaseKeyFrame::IsKeyframeAtOffset

Określa, czy klatka kluczowa ma zostać dodana do scenorysu z przesunięciem, czy po przejściu.

```
BOOL IsKeyframeAtOffset() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli klatka kluczowa powinna zostać dodana do scenorysu przy określonym przesunięciu. FAŁSZ, jeśli klatka kluczowa powinna zostać dodana do scenorysu po pewnym przejściu.

### <a name="remarks"></a>Uwagi

Określa, czy klatka kluczowa ma zostać dodana do scenorysu z przesunięciem. Przesunięcie lub przejście musi być określone w klasie pochodnej.

## <a name="cbasekeyframem_badded"></a><a name="m_badded"></a>CBaseKeyFrame::m_bAdded

Określa, czy ta klatka kluczowa została dodana do scenorysu.

```
BOOL m_bAdded;
```

## <a name="cbasekeyframem_biskeyframeatoffset"></a><a name="m_biskeyframeatoffset"></a>CBaseKeyFrame::m_bIsKeyframeAtOffset

Określa, czy ta klatka kluczowa ma zostać dodana do scenorysu z przesunięciem od innej istniejącej klatki kluczowej, czy na końcu niektórych przejść.

```
BOOL m_bIsKeyframeAtOffset;
```

## <a name="cbasekeyframem_keyframe"></a><a name="m_keyframe"></a>CBaseKeyFrame::m_keyframe

Reprezentuje klatkę kluczową interfejsu API animacji systemu Windows. Gdy klatka kluczowa nie jest inicjowana, jest ustawiona na wstępnie zdefiniowaną wartość UI_ANIMATION_KEYFRAME_STORYBOARD_START.

```
UI_ANIMATION_KEYFRAME m_keyframe;
```

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
