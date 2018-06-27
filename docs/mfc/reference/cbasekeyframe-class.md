---
title: Klasa CBaseKeyFrame | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3de348131dded63794e818d40c0ac5aeae910b03
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956711"
---
# <a name="cbasekeyframe-class"></a>Klasa CBaseKeyFrame
Implementuje podstawowych funkcji kluczową.  
  
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
|[CBaseKeyFrame::AddToStoryboard](#addtostoryboard)|Dodaje kluczową do scenorysu.|  
|[CBaseKeyFrame::GetAnimationKeyframe](#getanimationkeyframe)|Zwraca wartość klatki kluczowej podstawowej.|  
|[CBaseKeyFrame::IsAdded](#isadded)|Informuje, czy kluczową został dodany do scenorysu.|  
|[CBaseKeyFrame::IsKeyframeAtOffset](#iskeyframeatoffset)|Określa, czy kluczową powinny zostać dodane do scenorysu przy przesunięciu lub po przejściu.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CBaseKeyFrame::m_bAdded](#m_badded)|Określa, czy ten klatki kluczowej został dodany do scenorysu.|  
|[CBaseKeyFrame::m_bIsKeyframeAtOffset](#m_biskeyframeatoffset)|Określa, czy ten klatki kluczowej powinny zostać dodane do scenorysu przy przesunięciu z innego istniejącego klatki kluczowej, lub na końcu niektóre przejścia.|  
|[CBaseKeyFrame::m_keyframe](#m_keyframe)|Reprezentuje kluczową interfejsu API systemu Windows animacji. Nie zainicjowano kluczową jest ustawiona do wstępnie zdefiniowanych wartości UI_ANIMATION_KEYFRAME_STORYBOARD_START.|  
  
## <a name="remarks"></a>Uwagi  
 Hermetyzuje UI_ANIMATION_KEYFRAME zmiennej. Służy jako klasę podstawową dla implementacji klatki kluczowej. Kluczową reprezentuje konkretnego momentu w scenorysu i może służyć do określania godzin rozpoczęcia i zakończenia przejść. Istnieją dwa typy klatek - kluczowych dodane do scenorysu od wskazanego przesunięcia (w czasie) lub kluczowych dodane po przejścia. Ponieważ czasów trwania niektóre przejścia nie może być znane przed rozpoczęciem animacji, rzeczywiste wartości niektóre z kluczowych są określane w czasie wykonywania tylko. Ponieważ kluczowych może zależeć od przejścia, które z kolei ich zależą od klatek, jest ważne, aby zapobiec nieskończonej rekursji podczas tworzenia łańcuchów klatki kluczowej.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CBaseKeyFrame`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxanimationcontroller.h  
  
##  <a name="addtostoryboard"></a>  CBaseKeyFrame::AddToStoryboard  
 Dodaje kluczową do scenorysu.  
  
```  
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDeepAdd);
```  
  
### <a name="parameters"></a>Parametry  
 *pStoryboard*  
 Wskaźnik do scenorysu.  
  
 *bDeepAdd*  
 Jeśli ten parametr ma wartość TRUE, a kluczowej dodawany zależy od innych klatki kluczowej lub przejścia, ta metoda próbuje dodać ten klatki kluczowej lub przejście do scenorysu najpierw.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli klatki kluczowej został dodany do scenorysu pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana, aby dodać kluczową do scenorysu.  
  
##  <a name="cbasekeyframe"></a>  CBaseKeyFrame::CBaseKeyFrame  
 Tworzy obiekt klatki kluczowej.  
  
```  
CBaseKeyFrame();
```  
  
##  <a name="getanimationkeyframe"></a>  CBaseKeyFrame::GetAnimationKeyframe  
 Zwraca wartość klatki kluczowej podstawowej.  
  
```  
UI_ANIMATION_KEYFRAME GetAnimationKeyframe() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Kluczową bieżącej. Wartość domyślna to UI_ANIMATION_KEYFRAME_STORYBOARD_START.  
  
### <a name="remarks"></a>Uwagi  
 Jest to metoda dostępu do wartości klatki kluczowej podstawowej.  
  
##  <a name="isadded"></a>  CBaseKeyFrame::IsAdded  
 Informuje, czy kluczową został dodany do scenorysu.  
  
```  
BOOL IsAdded() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli kluczową zostanie dodany do scenorysu; otehrwise wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 W klasie podstawowej IsAdded zawsze zwraca wartość TRUE, ale jest on przesłaniany w klasach pochodnych.  
  
##  <a name="iskeyframeatoffset"></a>  CBaseKeyFrame::IsKeyframeAtOffset  
 Określa, czy kluczową powinny zostać dodane do scenorysu przy przesunięciu lub po przejściu.  
  
```  
BOOL IsKeyframeAtOffset() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli kluczową powinny zostać dodane do scenorysu w niektórych wskazanego przesunięcia. Wartość FALSE, jeśli kluczową powinny zostać dodane do scenorysu po niektóre przejścia.  
  
### <a name="remarks"></a>Uwagi  
 Określa, czy kluczową powinny zostać dodane do scenorysu przy przesunięciu. Przesunięcie lub przejścia należy określić w klasie pochodnej.  
  
##  <a name="m_badded"></a>  CBaseKeyFrame::m_bAdded  
 Określa, czy ten klatki kluczowej został dodany do scenorysu.  
  
```  
BOOL m_bAdded;  
```  
  
##  <a name="m_biskeyframeatoffset"></a>  CBaseKeyFrame::m_bIsKeyframeAtOffset  
 Określa, czy ten klatki kluczowej powinny zostać dodane do scenorysu przy przesunięciu z innego istniejącego klatki kluczowej, lub na końcu niektóre przejścia.  
  
```  
BOOL m_bIsKeyframeAtOffset;  
```  
  
##  <a name="m_keyframe"></a>  CBaseKeyFrame::m_keyframe  
 Reprezentuje kluczową interfejsu API systemu Windows animacji. Nie zainicjowano kluczową jest ustawiona do wstępnie zdefiniowanych wartości UI_ANIMATION_KEYFRAME_STORYBOARD_START.  
  
```  
UI_ANIMATION_KEYFRAME m_keyframe;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
