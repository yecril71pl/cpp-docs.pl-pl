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
ms.openlocfilehash: 850ce46f524d9069609c1e5809c091c18bd58ee4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618247"
---
# <a name="cbasekeyframe-class"></a>Klasa CBaseKeyFrame

Implementuje podstawowe funkcje ramek kluczowych.

## <a name="syntax"></a>Składnia

```
class CBaseKeyFrame : public CObject;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBaseKeyFrame::CBaseKeyFrame](#cbasekeyframe)|Tworzy obiekt klatki kluczowej.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBaseKeyFrame::AddToStoryboard](#addtostoryboard)|Dodaje kluczową prezentowania w scenorysach.|
|[CBaseKeyFrame::GetAnimationKeyframe](#getanimationkeyframe)|Zwraca podstawową wartość klatki kluczowej.|
|[CBaseKeyFrame::IsAdded](#isadded)|Informuje, czy kluczową została dodana do scenorysu.|
|[CBaseKeyFrame::IsKeyframeAtOffset](#iskeyframeatoffset)|Określa, czy ramka kluczowa powinny zostać dodane do scenorysu, offset lub po przejściu.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CBaseKeyFrame::m_bAdded](#m_badded)|Określa, czy ta ramka kluczowa zostały dodane do scenorysu.|
|[CBaseKeyFrame::m_bIsKeyframeAtOffset](#m_biskeyframeatoffset)|Określa, czy ta ramka kluczowa powinny zostać dodane do scenorysu na przesunięcie od innego istniejącego ramki kluczowej lub na końcu niektóre przejścia.|
|[CBaseKeyFrame::m_keyframe](#m_keyframe)|Reprezentuje ramkę kluczową interfejs API animacji Windows. Gdy ramka kluczowa nie został zainicjowany. ustawiono wstępnie zdefiniowaną wartość UI_ANIMATION_KEYFRAME_STORYBOARD_START.|

## <a name="remarks"></a>Uwagi

Hermetyzuje UI_ANIMATION_KEYFRAME zmiennej. Służy jako klasa bazowa dla implementacji klatki kluczowej. Kluczową reprezentuje moment w czasie w ramach scenorysu i może służyć do określenia godziny rozpoczęcia i zakończenia przejść. Istnieją dwa rodzaje ramek kluczowych - klatki kluczowe dodane do scenorysu od określonego przesunięcia (w czasie) lub klatki kluczowe dodane po przejścia. Ponieważ czasów trwania niektóre przejścia nie może być znane, przed uruchomieniem animacji, rzeczywiste wartości niektórych klatki kluczowe są określane w czasie wykonywania tylko. Ponieważ klatki kluczowe może zależeć od przejścia, co ich zależą od ramkami kluczowymi, jest ważne, aby zapobiec nieskończonej rekursje podczas tworzenia łańcuchów klatki kluczowej.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CBaseKeyFrame`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

##  <a name="addtostoryboard"></a>  CBaseKeyFrame::AddToStoryboard

Dodaje kluczową prezentowania w scenorysach.

```
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Wskaźnik do scenorysu.

*bDeepAdd*<br/>
Jeśli ten parametr ma wartość TRUE, a ramki kluczowej dodawany zależy od innych ramki kluczowej lub przejścia, ta metoda próbuje dodać tej ramki kluczowej lub przejście do scenorysu najpierw.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ramka kluczowa została dodana do scenorysu pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana, aby dodać kluczową prezentowania w scenorysach.

##  <a name="cbasekeyframe"></a>  CBaseKeyFrame::CBaseKeyFrame

Tworzy obiekt klatki kluczowej.

```
CBaseKeyFrame();
```

##  <a name="getanimationkeyframe"></a>  CBaseKeyFrame::GetAnimationKeyframe

Zwraca podstawową wartość klatki kluczowej.

```
UI_ANIMATION_KEYFRAME GetAnimationKeyframe() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca ramka kluczowa. Wartość domyślna to UI_ANIMATION_KEYFRAME_STORYBOARD_START.

### <a name="remarks"></a>Uwagi

Jest to metoda dostępu do podstawowej wartości ramki kluczowej.

##  <a name="isadded"></a>  CBaseKeyFrame::IsAdded

Informuje, czy kluczową została dodana do scenorysu.

```
BOOL IsAdded() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ramka kluczowa jest dodawany do scenorysu; otehrwise wartość FALSE.

### <a name="remarks"></a>Uwagi

W klasie bazowej IsAdded zawsze zwraca wartość PRAWDA, ale zostanie on przesłonięty w klasach pochodnych.

##  <a name="iskeyframeatoffset"></a>  CBaseKeyFrame::IsKeyframeAtOffset

Określa, czy ramka kluczowa powinny zostać dodane do scenorysu, offset lub po przejściu.

```
BOOL IsKeyframeAtOffset() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ramka kluczowa powinny zostać dodane do scenorysu w niektórych określonego przesunięcia. Wartość FALSE, jeśli ramka kluczowa powinny zostać dodane do scenorysu po niektórych przejścia.

### <a name="remarks"></a>Uwagi

Określa, czy ramka kluczowa powinny zostać dodane do scenorysu przy przesunięciu. Przesunięcie lub przejścia należy określić w klasie pochodnej.

##  <a name="m_badded"></a>  CBaseKeyFrame::m_bAdded

Określa, czy ta ramka kluczowa zostały dodane do scenorysu.

```
BOOL m_bAdded;
```

##  <a name="m_biskeyframeatoffset"></a>  CBaseKeyFrame::m_bIsKeyframeAtOffset

Określa, czy ta ramka kluczowa powinny zostać dodane do scenorysu na przesunięcie od innego istniejącego ramki kluczowej lub na końcu niektóre przejścia.

```
BOOL m_bIsKeyframeAtOffset;
```

##  <a name="m_keyframe"></a>  CBaseKeyFrame::m_keyframe

Reprezentuje ramkę kluczową interfejs API animacji Windows. Gdy ramka kluczowa nie został zainicjowany. ustawiono wstępnie zdefiniowaną wartość UI_ANIMATION_KEYFRAME_STORYBOARD_START.

```
UI_ANIMATION_KEYFRAME m_keyframe;
```

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
