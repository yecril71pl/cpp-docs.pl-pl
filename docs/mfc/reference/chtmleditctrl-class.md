---
title: Klasa CHtmlEditCtrl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::Create
- AFXHTML/CHtmlEditCtrl::GetDHtmlDocument
- AFXHTML/CHtmlEditCtrl::GetStartDocument
dev_langs: C++
helpviewer_keywords:
- CHtmlEditCtrl [MFC], CHtmlEditCtrl
- CHtmlEditCtrl [MFC], Create
- CHtmlEditCtrl [MFC], GetDHtmlDocument
- CHtmlEditCtrl [MFC], GetStartDocument
ms.assetid: 0fc4a238-b05f-4874-9edc-6a6701f064d9
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e18c2b38215e75d6fe12b1c78c93d3d9fe147df9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="chtmleditctrl-class"></a>Klasa CHtmlEditCtrl
Udostępnia funkcje formantu WebBrowser ActiveX w oknie MFC.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CHtmlEditCtrl: public CWnd,   
    public CHtmlEditCtrlBase<CHtmlEditCtrl>  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHtmlEditCtrl::CHtmlEditCtrl](#chtmleditctrl)|Konstruuje `CHtmlEditCtrl` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHtmlEditCtrl::Create](#create)|Tworzy kontrolkę WebBrowser ActiveX i dołącza go do `CHtmlEditCtrl` obiektu. Funkcja ta automatycznie umieszcza formantu WebBrowser ActiveX trybu edycji.|  
|[CHtmlEditCtrl::GetDHtmlDocument](#getdhtmldocument)|Pobiera [IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx) interfejsu w dokumencie załadowanych obecnie do zawartych w niej formant WebBrowser.|  
|[CHtmlEditCtrl::GetStartDocument](#getstartdocument)|Pobiera dokument domyślny adres URL, który ładowania zawartych w niej formant WebBrowser.|  
  
## <a name="remarks"></a>Uwagi  
 Tryb edycji hostowanej przez formant są automatycznie umieszczane w przeglądarce sieci Web, po jego utworzeniu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHtmlEditCtrl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxhtml.h  
  
##  <a name="chtmleditctrl"></a>CHtmlEditCtrl::CHtmlEditCtrl  
 Konstruuje `CHtmlEditCtrl` obiektu.  
  
```  
CHtmlEditCtrl();
```  
  
##  <a name="create"></a>CHtmlEditCtrl::Create  
 Tworzy kontrolkę WebBrowser ActiveX i dołącza go do `CHtmlEditCtrl` obiektu. ActiveX WebBrowser — formant automatycznie przechodzi do dokumentu domyślnego i następnie znajduje się w trybie edycji przez tę funkcję.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    int nID,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszWindowName`  
 Ten parametr nie jest używana.  
  
 `dwStyle`  
 Ten parametr nie jest używana.  
  
 `rect`  
 Określa rozmiar i położenie formantu.  
  
 `pParentWnd`  
 Określa okno nadrzędne kontrolki. Nie może być **NULL**.  
  
 `nID`  
 Określa identyfikator formantu.  
  
 `pContext`  
 Ten parametr nie jest używana.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** w przypadku powodzenia **FALSE** w przypadku awarii.  
  
##  <a name="getdhtmldocument"></a>CHtmlEditCtrl::GetDHtmlDocument  
 Pobiera [IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx) interfejsu w dokumencie załadowanych obecnie do zawartych w niej formantu WebBrowser  
  
```  
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `ppDocument`  
 Interfejs dokumentu.  
  
##  <a name="getstartdocument"></a>CHtmlEditCtrl::GetStartDocument  
 Pobiera dokument domyślny adres URL, który ładowania zawartych w niej formant WebBrowser.  
  
```  
virtual LPCTSTR GetStartDocument();
```  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)

