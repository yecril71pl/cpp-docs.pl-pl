---
title: Klasa CHtmlEditView | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHtmlEditView
- AFXHTML/CHtmlEditView
- AFXHTML/CHtmlEditView::CHtmlEditView
- AFXHTML/CHtmlEditView::Create
- AFXHTML/CHtmlEditView::GetDHtmlDocument
- AFXHTML/CHtmlEditView::GetStartDocument
dev_langs: C++
helpviewer_keywords:
- CHtmlEditView [MFC], CHtmlEditView
- CHtmlEditView [MFC], Create
- CHtmlEditView [MFC], GetDHtmlDocument
- CHtmlEditView [MFC], GetStartDocument
ms.assetid: 166c8ba8-3fb5-4dd7-a9ea-5bca662d00f6
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e26ca17d92d30879983351e0a1ebfc2e3883dc65
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="chtmleditview-class"></a>Klasa CHtmlEditView
Udostępnia funkcję edytowania platformy WebBrowser w kontekście architektury dokument/widok MFC.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CHtmlEditView : public CHtmlView, public CHtmlEditCtrlBase<CHtmlEditView>  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHtmlEditView::CHtmlEditView](#chtmleditview)|Konstruuje `CHtmlEditView` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHtmlEditView::Create](#create)|Tworzy nowy obiekt okna.|  
|[CHtmlEditView::GetDHtmlDocument](#getdhtmldocument)|Zwraca **IHTMLDocument2** interfejsu w bieżącym dokumencie.|  
|[CHtmlEditView::GetStartDocument](#getstartdocument)|Pobiera nazwę dokument domyślny dla tego widoku.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cview —](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 [CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)  
  
 [CHtmlView](../../mfc/reference/chtmlview-class.md)  
  
 `CHtmlEditView`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxhtml.h  
  
##  <a name="chtmleditview"></a>CHtmlEditView::CHtmlEditView  
 Konstruuje `CHtmlEditView` obiektu.  
  
```  
CHtmlEditView();
```  
  
##  <a name="create"></a>CHtmlEditView::Create  
 Tworzy nowy obiekt okna.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszClassName,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszClassName`  
 Punkty na ciąg znaków zakończony znakiem null nazwy klasy systemu Windows. Nazwa klasy może być dowolną nazwą zarejestrowany [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) funkcji globalnej lub **RegisterClass** funkcji systemu Windows. Jeśli **NULL**, będzie używana domyślna wstępnie zdefiniowanych [cframewnd —](../../mfc/reference/cframewnd-class.md) atrybutów.  
  
 `lpszWindowName`  
 Wskazuje ciąg znaków zakończony znakiem null, który reprezentuje nazwę okna.  
  
 `dwStyle`  
 Określa atrybuty stylu okna. Domyślnie **ws_visible —** i **ws_child —** ustawiono style systemu Windows.  
  
 `rect`  
 Odwołanie do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) Struktura określająca rozmiar i położenie okna. `rectDefault` Wartość umożliwia systemu Windows określić rozmiar i położenie nowego okna.  
  
 `pParentWnd`  
 Wskaźnik do okno nadrzędne kontrolki.  
  
 `nID`  
 Identyfikator widoku. Domyślnie ustawioną **AFX_IDW_PANE_FIRST**.  
  
 `pContext`  
 Wskaźnik do [CCreateContext](../../mfc/reference/ccreatecontext-structure.md). **Wartość NULL** domyślnie.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda będzie także wywołać zawarte WebBrowser **Nawigacja** metodę, aby załadować dokument domyślny (zobacz [CHtmlEditView::GetStartDocument](#getstartdocument)).  
  
##  <a name="getdhtmldocument"></a>CHtmlEditView::GetDHtmlDocument  
 Zwraca **IHTMLDocument2** interfejsu w bieżącym dokumencie.  
  
```  
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `ppDocument`  
 [IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx) interfejsu.  
  
##  <a name="getstartdocument"></a>CHtmlEditView::GetStartDocument  
 Pobiera nazwę dokument domyślny dla tego widoku.  
  
```  
virtual LPCTSTR GetStartDocument();
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe HTMLEdit](../../visual-cpp-samples.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)


