---
title: Klasa CKeyFrame | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9a9e9ff3d6e3e4bcccf8e9ebd46f791f60f1cc37
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33367188"
---
# <a name="ckeyframe-class"></a>Klasa CKeyFrame
Reprezentuje klatek kluczowych animacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CKeyFrame : public CBaseKeyFrame;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CKeyFrame::CKeyFrame](#ckeyframe)|Przeciążone. Tworzy klatki kluczowej, która jest zależna od innych klatki kluczowej.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CKeyFrame::AddToStoryboard](#addtostoryboard)|Dodaje kluczową do scenorysu. (Przesłania [CBaseKeyFrame::AddToStoryboard](../../mfc/reference/cbasekeyframe-class.md#addtostoryboard).)|  
|[CKeyFrame::AddToStoryboardAfterTransition](#addtostoryboardaftertransition)|Dodaje kluczową do scenorysu po przejściu.|  
|[CKeyFrame::AddToStoryboardAtOffset](#addtostoryboardatoffset)|Dodaje kluczową do scenorysu przy przesunięciu.|  
|[CKeyFrame::GetExistingKeyframe](#getexistingkeyframe)|Zwraca wskaźnik do klatki kluczowej, który zależy od tego klatki kluczowej.|  
|[CKeyFrame::GetOffset](#getoffset)|Zwraca przesunięcie od innych klatki kluczowej.|  
|[CKeyFrame::GetTransition](#gettransition)|Zwraca wskaźnik do przejścia, od którego ta klatki kluczowej zależny.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CKeyFrame::m_offset](#m_offset)|Określa przesunięcie to klatki kluczowej z kluczową przechowywane w m_pExistingKeyFrame.|  
|[CKeyFrame::m_pExistingKeyFrame](#m_pexistingkeyframe)|Przechowuje wskaźnik do istniejących keframe. Ta klatki kluczowej jest dodawany do scenorysu z m_offset do istniejących klatki kluczowej.|  
|[CKeyFrame::m_pTransition](#m_ptransition)|Przechowuje wskaźnik do transtion, który rozpoczyna się od tego klatki kluczowej.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa implementuje klatek kluczowych animacji. Kluczową reprezentuje konkretnego momentu w scenorysu i może służyć do określania godzin rozpoczęcia i zakończenia przejść. Kluczową może opierać się na inne klatki kluczowej i mają przesunięcie (w sekundach) z niej, lub mogą być oparte na przejście i reprezentują moment w czasie, gdy kończy się to przejście.  
  
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
 `pStoryboard`  
 Wskaźnik do scenorysu.  
  
 `bDeepAdd`  
 Określa, czy dodać klatki kluczowej lub przejście rekursywnie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli klatki kluczowej został pomyślnie dodany.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda dodaje kluczową do scenorysu. Jeśli zależy on od innych klatki kluczowej lub przejścia i bDeepAdd ma wartość TRUE, ta metoda próbuje dodać je rekursywnie.  
  
##  <a name="addtostoryboardaftertransition"></a>  CKeyFrame::AddToStoryboardAfterTransition  
 Dodaje kluczową do scenorysu po przejściu.  
  
```  
BOOL AddToStoryboardAfterTransition(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDeepAdd);
```  
  
### <a name="parameters"></a>Parametry  
 `pStoryboard`  
 Wskaźnik do scenorysu.  
  
 `bDeepAdd`  
 Określa, czy dodać rekursywnie przejścia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli klatki kluczowej został pomyślnie dodany.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana przez platformę, by dodać kluczową do scenorysu po przejściu.  
  
##  <a name="addtostoryboardatoffset"></a>  CKeyFrame::AddToStoryboardAtOffset  
 Dodaje kluczową do scenorysu przy przesunięciu.  
  
```  
virtual BOOL AddToStoryboardAtOffset(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDeepAdd);
```  
  
### <a name="parameters"></a>Parametry  
 `pStoryboard`  
 Wskaźnik do scenorysu.  
  
 `bDeepAdd`  
 Określa, czy dodać kluczową to klatki kluczowej zależy rekursywnie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli klatki kluczowej został pomyślnie dodany.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana przez platformę, by dodać kluczową do scenorysu przy przesunięciu.  
  
##  <a name="ckeyframe"></a>  CKeyFrame::CKeyFrame  
 Tworzy klatki kluczowej, która jest zależna od przejścia.  
  
```  
CKeyFrame(CBaseTransition* pTransition);

 
CKeyFrame(
    CBaseKeyFrame* pKeyframe,  
    UI_ANIMATION_SECONDS offset = 0.0);
```  
  
### <a name="parameters"></a>Parametry  
 `pTransition`  
 Wskaźnik do przejścia.  
  
 `pKeyframe`  
 Wskaźnik do klatki kluczowej.  
  
 `offset`  
 Przesunięcie w sekundach, z określonym przez pKeyframe klatki kluczowej.  
  
### <a name="remarks"></a>Uwagi  
 Skonstruowane klatki kluczowej będzie reprezentować konkretnego momentu w scenorysu, po zakończeniu przejścia.  
  
##  <a name="getexistingkeyframe"></a>  CKeyFrame::GetExistingKeyframe  
 Zwraca wskaźnik do klatki kluczowej, który zależy od tego klatki kluczowej.  
  
```  
CBaseKeyFrame* GetExistingKeyframe();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nieprawidłowy wskaźnik do klatki kluczowej, lub wartość NULL, jeśli ta klatki kluczowej nie zależy od innych klatki kluczowej.  
  
### <a name="remarks"></a>Uwagi  
 Jest to metoda dostępu do klatki kluczowej, który zależy od tego klatki kluczowej.  
  
##  <a name="getoffset"></a>  CKeyFrame::GetOffset  
 Zwraca przesunięcie od innych klatki kluczowej.  
  
```  
UI_ANIMATION_SECONDS GetOffset();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Przesunięcie w sekundach od innych klatki kluczowej.  
  
### <a name="remarks"></a>Uwagi  
 Tę metodę należy wywoływać ustalenie przesunięcie w sekundach od innych klatki kluczowej.  
  
##  <a name="gettransition"></a>  CKeyFrame::GetTransition  
 Zwraca wskaźnik do przejścia, od którego ta klatki kluczowej zależny.  
  
```  
CBaseTransition* GetTransition();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nieprawidłowy wskaźnik do przejścia lub wartość NULL, jeśli ta klatki kluczowej nie zależy od przejścia.  
  
### <a name="remarks"></a>Uwagi  
 Jest to metoda dostępu do przejścia na zależy od tego klatki kluczowej.  
  
##  <a name="m_offset"></a>  CKeyFrame::m_offset  
 Określa przesunięcie to klatki kluczowej z kluczową przechowywane w m_pExistingKeyFrame.  
  
```  
UI_ANIMATION_SECONDS m_offset;  
```  
  
##  <a name="m_pexistingkeyframe"></a>  CKeyFrame::m_pExistingKeyFrame  
 Przechowuje wskaźnik do istniejących keframe. Ta klatki kluczowej jest dodawany do scenorysu z m_offset do istniejących klatki kluczowej.  
  
```  
CBaseKeyFrame* m_pExistingKeyFrame;  
```  
  
##  <a name="m_ptransition"></a>  CKeyFrame::m_pTransition  
 Przechowuje wskaźnik do transtion, który rozpoczyna się od tego klatki kluczowej.  
  
```  
CBaseTransition* m_pTransition;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
