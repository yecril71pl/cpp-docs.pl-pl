---
title: Klasa CDCRenderTarget | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::Attach
- AFXRENDERTARGET/CDCRenderTarget::BindDC
- AFXRENDERTARGET/CDCRenderTarget::Create
- AFXRENDERTARGET/CDCRenderTarget::Detach
- AFXRENDERTARGET/CDCRenderTarget::GetDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::m_pDCRenderTarget
dev_langs:
- C++
helpviewer_keywords:
- CDCRenderTarget [MFC], CDCRenderTarget
- CDCRenderTarget [MFC], Attach
- CDCRenderTarget [MFC], BindDC
- CDCRenderTarget [MFC], Create
- CDCRenderTarget [MFC], Detach
- CDCRenderTarget [MFC], GetDCRenderTarget
- CDCRenderTarget [MFC], m_pDCRenderTarget
ms.assetid: aa8059c9-08e6-49e4-9b8c-00fa54077a61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 36f8a038cd282ddf233fe2cf15a134c52962ebff
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953704"
---
# <a name="cdcrendertarget-class"></a>Klasa CDCRenderTarget
Otoka dla ID2D1DCRenderTarget.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDCRenderTarget : public CRenderTarget;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDCRenderTarget::CDCRenderTarget](#cdcrendertarget)|Tworzy obiekt CDCRenderTarget.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDCRenderTarget::Attach](#attach)|Dołącza istniejących renderowania interfejsu docelowych do obiektu|  
|[CDCRenderTarget::BindDC](#binddc)|Wiąże kontekst urządzenia, do którego on wydaje polecenia rysowania obiektu docelowego renderowania|  
|[CDCRenderTarget::Create](#create)|Tworzy CDCRenderTarget.|  
|[CDCRenderTarget::Detach](#detach)|Odłącza interfejs docelowy renderowania z obiektu|  
|[CDCRenderTarget::GetDCRenderTarget](#getdcrendertarget)|Zwraca interfejs ID2D1DCRenderTarget|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDCRenderTarget::operator ID2D1DCRenderTarget *](#operator_id2d1dcrendertarget_star)|Zwraca interfejs ID2D1DCRenderTarget|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDCRenderTarget::m_pDCRenderTarget](#m_pdcrendertarget)|Wskaźnik do obiektu ID2D1DCRenderTarget.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
 [CDCRenderTarget](../../mfc/reference/cdcrendertarget-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxrendertarget.h  
  
##  <a name="attach"></a>  CDCRenderTarget::Attach  
 Dołącza istniejących renderowania interfejsu docelowych do obiektu  
  
```  
void Attach(ID2D1DCRenderTarget* pTarget);
```  
  
### <a name="parameters"></a>Parametry  
 *pTarget*  
 Istniejący interfejs docelowego renderowania. Nie może mieć wartości NULL  
  
##  <a name="binddc"></a>  CDCRenderTarget::BindDC  
 Wiąże kontekst urządzenia, do którego on wydaje polecenia rysowania obiektu docelowego renderowania  
  
```  
BOOL BindDC(
    const CDC& dc,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Parametry  
 *Kontroler domeny*  
 Kontekst urządzenia, do którego obiektu docelowego renderowania wydaje polecenia rysowania  
  
 *Rect*  
 Wymiary dojścia do kontekstu urządzenia (elementu HDC), z którym powiązany jest obiektu docelowego renderowania  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.  
  
##  <a name="cdcrendertarget"></a>  CDCRenderTarget::CDCRenderTarget  
 Tworzy obiekt CDCRenderTarget.  
  
```  
CDCRenderTarget();
```  
  
##  <a name="create"></a>  CDCRenderTarget::Create  
 Tworzy CDCRenderTarget.  
  
```  
BOOL Create(const D2D1_RENDER_TARGET_PROPERTIES& props);
```  
  
### <a name="parameters"></a>Parametry  
 *właściwości*  
 Tryb renderowania, format piksela opcje remoting, DPI informacji i minimalna obsługa DirectX wymagane do renderowania sprzętowego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.  
  
##  <a name="detach"></a>  CDCRenderTarget::Detach  
 Odłącza interfejs docelowy renderowania z obiektu  
  
```  
ID2D1DCRenderTarget* Detach();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do odłączonego renderowania interfejs docelowy.  
  
##  <a name="getdcrendertarget"></a>  CDCRenderTarget::GetDCRenderTarget  
 Zwraca interfejs ID2D1DCRenderTarget  
  
```  
ID2D1DCRenderTarget* GetDCRenderTarget();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu ID2D1DCRenderTarget lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
##  <a name="m_pdcrendertarget"></a>  CDCRenderTarget::m_pDCRenderTarget  
 Wskaźnik do obiektu ID2D1DCRenderTarget.  
  
```  
ID2D1DCRenderTarget* m_pDCRenderTarget;  
```  
  
##  <a name="operator_id2d1dcrendertarget_star"></a>  CDCRenderTarget::operator ID2D1DCRenderTarget *  
 Zwraca interfejs ID2D1DCRenderTarget  
  
```  
operator ID2D1DCRenderTarget*();
```   
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu ID2D1DCRenderTarget lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
