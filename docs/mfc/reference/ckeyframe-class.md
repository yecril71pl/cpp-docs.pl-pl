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
ms.openlocfilehash: b6ebe5ba78a259014f62bdf04f30e856a57f1aba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451080"
---
# <a name="ckeyframe-class"></a>Klasa CKeyFrame

Przedstawia klatki kluczowe animacji.

## <a name="syntax"></a>Składnia

```
class CKeyFrame : public CBaseKeyFrame;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CKeyFrame::CKeyFrame](#ckeyframe)|Przeciążone. Tworzy ramkę kluczową, który zależy od innych klatki kluczowej.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CKeyFrame::AddToStoryboard](#addtostoryboard)|Dodaje kluczową do scenorysu. (Przesłania [CBaseKeyFrame::AddToStoryboard](../../mfc/reference/cbasekeyframe-class.md#addtostoryboard).)|
|[CKeyFrame::AddToStoryboardAfterTransition](#addtostoryboardaftertransition)|Dodaje kluczową do scenorysu po przejściu.|
|[CKeyFrame::AddToStoryboardAtOffset](#addtostoryboardatoffset)|Dodaje kluczową prezentowania w scenorysach przy przesunięciu.|
|[CKeyFrame::GetExistingKeyframe](#getexistingkeyframe)|Zwraca wskaźnik do ramki kluczowej, od którego zależy ta klatki kluczowej.|
|[CKeyFrame::GetOffset](#getoffset)|Zwraca przesunięcie od innych klatki kluczowej.|
|[CKeyFrame::GetTransition](#gettransition)|Zwraca wskaźnik, do którego nastąpi przejście, od którego zależy ta klatki kluczowej.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CKeyFrame::m_offset](#m_offset)|Określa przesunięcie tej ramki kluczowej z przechowywanych w m_pExistingKeyFrame klatki kluczowej.|
|[CKeyFrame::m_pExistingKeyFrame](#m_pexistingkeyframe)|Przechowuje wskaźnik do istniejących keframe. Ta ramka kluczowa jest dodawany do scenorysu z m_offset do istniejących klatki kluczowej.|
|[CKeyFrame::m_pTransition](#m_ptransition)|Przechowuje wskaźnik do transtion, który rozpoczyna się od tej ramki kluczowej.|

## <a name="remarks"></a>Uwagi

Ta klasa implementuje klatki kluczowe animacji. Kluczową reprezentuje moment w czasie w ramach scenorysu i może służyć do określenia godziny rozpoczęcia i zakończenia przejść. Kluczową może opierać się na inne ramki kluczowej i mają przesunięcie (w sekundach) od niego, lub może opierać się na przejście i reprezentuje moment w czasie, kiedy kończy się tego przejścia.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CBaseKeyFrame](../../mfc/reference/cbasekeyframe-class.md)

[CKeyFrame](../../mfc/reference/ckeyframe-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

##  <a name="addtostoryboard"></a>  CKeyFrame::AddToStoryboard

Dodaje kluczową do scenorysu.

```
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Wskaźnik do scenorysu.

*bDeepAdd*<br/>
Określa, czy należy dodać ramki kluczowej lub przejście cyklicznie.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ramka kluczowa został pomyślnie dodany.

### <a name="remarks"></a>Uwagi

Metoda ta umożliwia dodanie kluczowej prezentowania w scenorysach. Jeśli zależy od innych ramki kluczowej lub przejścia i bDeepAdd ma wartość TRUE, ta metoda próbuje dodać je cyklicznie.

##  <a name="addtostoryboardaftertransition"></a>  CKeyFrame::AddToStoryboardAfterTransition

Dodaje kluczową do scenorysu po przejściu.

```
BOOL AddToStoryboardAfterTransition(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Wskaźnik do scenorysu.

*bDeepAdd*<br/>
Określa, czy Dodaj cyklicznie przejścia.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ramka kluczowa został pomyślnie dodany.

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana przez platformę, by dodać kluczową do scenorysu po przejściu.

##  <a name="addtostoryboardatoffset"></a>  CKeyFrame::AddToStoryboardAtOffset

Dodaje kluczową prezentowania w scenorysach przy przesunięciu.

```
virtual BOOL AddToStoryboardAtOffset(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Wskaźnik do scenorysu.

*bDeepAdd*<br/>
Określa, czy można dodać kluczową tej ramki kluczowej zależy cyklicznie.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ramka kluczowa został pomyślnie dodany.

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana przez platformę, by dodać kluczową prezentowania w scenorysach przy przesunięciu.

##  <a name="ckeyframe"></a>  CKeyFrame::CKeyFrame

Tworzy ramkę kluczową, który zależy od przejścia.

```
CKeyFrame(CBaseTransition* pTransition);

CKeyFrame(
    CBaseKeyFrame* pKeyframe,
    UI_ANIMATION_SECONDS offset = 0.0);
```

### <a name="parameters"></a>Parametry

*pTransition*<br/>
Wskaźnik do przejścia.

*pKeyframe*<br/>
Wskaźnik do ramki kluczowej.

*offset*<br/>
Przesunięcie w ciągu kilku sekund z określonego przez pKeyframe klatki kluczowej.

### <a name="remarks"></a>Uwagi

Zbudowany ramka kluczowa będzie reprezentować moment w czasie w ramach scenorysu po zakończeniu przejścia.

##  <a name="getexistingkeyframe"></a>  CKeyFrame::GetExistingKeyframe

Zwraca wskaźnik do ramki kluczowej, od którego zależy ta klatki kluczowej.

```
CBaseKeyFrame* GetExistingKeyframe();
```

### <a name="return-value"></a>Wartość zwracana

Nieprawidłowy wskaźnik do ramki kluczowej lub wartość NULL, jeśli ta ramka kluczowa nie zależy od innych klatki kluczowej.

### <a name="remarks"></a>Uwagi

Jest to metoda dostępu do klatki kluczowej, od którego zależy ta klatki kluczowej.

##  <a name="getoffset"></a>  CKeyFrame::GetOffset

Zwraca przesunięcie od innych klatki kluczowej.

```
UI_ANIMATION_SECONDS GetOffset();
```

### <a name="return-value"></a>Wartość zwracana

Przesunięcie w ciągu kilku sekund od innych klatki kluczowej.

### <a name="remarks"></a>Uwagi

Ta metoda powinna być wywoływana, aby określić przesunięcie w ciągu kilku sekund od innych klatki kluczowej.

##  <a name="gettransition"></a>  CKeyFrame::GetTransition

Zwraca wskaźnik, do którego nastąpi przejście, od którego zależy ta klatki kluczowej.

```
CBaseTransition* GetTransition();
```

### <a name="return-value"></a>Wartość zwracana

Nieprawidłowy wskaźnik do przejścia lub wartość NULL, jeśli ta ramka kluczowa nie zależy od przejścia.

### <a name="remarks"></a>Uwagi

Jest to metoda dostępu, do którego nastąpi przejście, od którego zależy ta ramka kluczowa.

##  <a name="m_offset"></a>  CKeyFrame::m_offset

Określa przesunięcie tej ramki kluczowej z przechowywanych w m_pExistingKeyFrame klatki kluczowej.

```
UI_ANIMATION_SECONDS m_offset;
```

##  <a name="m_pexistingkeyframe"></a>  CKeyFrame::m_pExistingKeyFrame

Przechowuje wskaźnik do istniejących keframe. Ta ramka kluczowa jest dodawany do scenorysu z m_offset do istniejących klatki kluczowej.

```
CBaseKeyFrame* m_pExistingKeyFrame;
```

##  <a name="m_ptransition"></a>  CKeyFrame::m_pTransition

Przechowuje wskaźnik do transtion, który rozpoczyna się od tej ramki kluczowej.

```
CBaseTransition* m_pTransition;
```

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
