---
title: Klasa CHwndRenderTarget | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::Attach
- AFXRENDERTARGET/CHwndRenderTarget::CheckWindowState
- AFXRENDERTARGET/CHwndRenderTarget::Create
- AFXRENDERTARGET/CHwndRenderTarget::Detach
- AFXRENDERTARGET/CHwndRenderTarget::GetHwnd
- AFXRENDERTARGET/CHwndRenderTarget::GetHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::ReCreate
- AFXRENDERTARGET/CHwndRenderTarget::Resize
- AFXRENDERTARGET/CHwndRenderTarget::m_pHwndRenderTarget
dev_langs:
- C++
helpviewer_keywords:
- CHwndRenderTarget [MFC], CHwndRenderTarget
- CHwndRenderTarget [MFC], Attach
- CHwndRenderTarget [MFC], CheckWindowState
- CHwndRenderTarget [MFC], Create
- CHwndRenderTarget [MFC], Detach
- CHwndRenderTarget [MFC], GetHwnd
- CHwndRenderTarget [MFC], GetHwndRenderTarget
- CHwndRenderTarget [MFC], ReCreate
- CHwndRenderTarget [MFC], Resize
- CHwndRenderTarget [MFC], m_pHwndRenderTarget
ms.assetid: aa65b69f-7202-46ea-af81-ef325da0b840
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d83765309f6df860b190d3ea2114e7e0fd35724
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33367636"
---
# <a name="chwndrendertarget-class"></a>Klasa CHwndRenderTarget
Otoka dla ID2D1HwndRenderTarget.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CHwndRenderTarget : public CRenderTarget;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHwndRenderTarget::CHwndRenderTarget](#chwndrendertarget)|Tworzy obiekt CHwndRenderTarget z HWND.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHwndRenderTarget::Attach](#attach)|Dołącza istniejących renderowania interfejsu docelowych do obiektu|  
|[CHwndRenderTarget::CheckWindowState](#checkwindowstate)|Wskazuje, czy jest zamknięte HWND skojarzone z tego obiektu docelowego renderowania.|  
|[CHwndRenderTarget::Create](#create)|Tworzy obiektu docelowego renderowania skojarzony z oknem|  
|[CHwndRenderTarget::Detach](#detach)|Odłącza interfejs docelowy renderowania z obiektu|  
|[CHwndRenderTarget::GetHwnd](#gethwnd)|Zwraca HWND skojarzony z tym elementem docelowym renderowania.|  
|[CHwndRenderTarget::GetHwndRenderTarget](#gethwndrendertarget)|Zwraca interfejs ID2D1HwndRenderTarget.|  
|[CHwndRenderTarget::ReCreate](#recreate)|Ponownie tworzy obiektu docelowego renderowania skojarzony z oknem|  
|[CHwndRenderTarget::Resize](#resize)|Zmienia rozmiar obiektu docelowego renderowania do rozmiaru określonego pikseli|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHwndRenderTarget::operator ID2D1HwndRenderTarget *](#operator_id2d1hwndrendertarget_star)|Zwraca interfejs ID2D1HwndRenderTarget.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHwndRenderTarget::m_pHwndRenderTarget](#m_phwndrendertarget)|Wskaźnik do obiektu ID2D1HwndRenderTarget.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
 [CHwndRenderTarget](../../mfc/reference/chwndrendertarget-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxrendertarget.h  
  
##  <a name="attach"></a>  CHwndRenderTarget::Attach  
 Dołącza istniejących renderowania interfejsu docelowych do obiektu  
  
```  
void Attach(ID2D1HwndRenderTarget* pTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `pTarget`  
 Istniejący interfejs docelowego renderowania. Nie może mieć wartości NULL  
  
##  <a name="checkwindowstate"></a>  CHwndRenderTarget::CheckWindowState  
 Wskazuje, czy jest zamknięte HWND skojarzone z tego obiektu docelowego renderowania.  
  
```  
D2D1_WINDOW_STATE CheckWindowState() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość wskazująca, czy HWND skojarzony z tym elementem docelowym renderowania jest zamknięte.  
  
##  <a name="chwndrendertarget"></a>  CHwndRenderTarget::CHwndRenderTarget  
 Tworzy obiekt CHwndRenderTarget z HWND.  
  
```  
CHwndRenderTarget(HWND hwnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `hwnd`  
 HWND skojarzony z tym elementem docelowym renderowania  
  
##  <a name="create"></a>  CHwndRenderTarget::Create  
 Tworzy obiektu docelowego renderowania skojarzony z oknem  
  
```  
BOOL Create(HWND hWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `hWnd`  
 HWND skojarzony z tym elementem docelowym renderowania  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE  
  
##  <a name="detach"></a>  CHwndRenderTarget::Detach  
 Odłącza interfejs docelowy renderowania z obiektu  
  
```  
ID2D1HwndRenderTarget* Detach();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do odłączonego renderowania interfejs docelowy.  
  
##  <a name="gethwnd"></a>  CHwndRenderTarget::GetHwnd  
 Zwraca HWND skojarzony z tym elementem docelowym renderowania.  
  
```  
HWND GetHwnd() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 HWND skojarzony z tym elementem docelowym renderowania.  
  
##  <a name="gethwndrendertarget"></a>  CHwndRenderTarget::GetHwndRenderTarget  
 Zwraca interfejs ID2D1HwndRenderTarget.  
  
```  
ID2D1HwndRenderTarget* GetHwndRenderTarget();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu ID2D1HwndRenderTarget lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
##  <a name="m_phwndrendertarget"></a>  CHwndRenderTarget::m_pHwndRenderTarget  
 Wskaźnik do obiektu ID2D1HwndRenderTarget.  
  
```  
ID2D1HwndRenderTarget* m_pHwndRenderTarget;  
```  
  
##  <a name="operator_id2d1hwndrendertarget_star"></a>  CHwndRenderTarget::operator ID2D1HwndRenderTarget *  
 Zwraca interfejs ID2D1HwndRenderTarget.  
  
```  
operator ID2D1HwndRenderTarget*();
```   
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu ID2D1HwndRenderTarget lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
##  <a name="recreate"></a>  CHwndRenderTarget::ReCreate  
 Ponownie tworzy obiektu docelowego renderowania skojarzony z oknem  
  
```  
BOOL ReCreate(HWND hWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `hWnd`  
 HWND skojarzony z tym elementem docelowym renderowania  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.  
  
##  <a name="resize"></a>  CHwndRenderTarget::Resize  
 Zmienia rozmiar obiektu docelowego renderowania do rozmiaru określonego pikseli  
  
```  
BOOL Resize(const CD2DSizeU& size);
```  
  
### <a name="parameters"></a>Parametry  
 `size`  
 Nowy rozmiar obiektu docelowego renderowania w pikselach urządzenia  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
