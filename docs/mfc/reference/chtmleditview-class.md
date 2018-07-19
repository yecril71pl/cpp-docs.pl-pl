---
title: Klasa CHtmlEditView | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CHtmlEditView
- AFXHTML/CHtmlEditView
- AFXHTML/CHtmlEditView::CHtmlEditView
- AFXHTML/CHtmlEditView::Create
- AFXHTML/CHtmlEditView::GetDHtmlDocument
- AFXHTML/CHtmlEditView::GetStartDocument
dev_langs:
- C++
helpviewer_keywords:
- CHtmlEditView [MFC], CHtmlEditView
- CHtmlEditView [MFC], Create
- CHtmlEditView [MFC], GetDHtmlDocument
- CHtmlEditView [MFC], GetStartDocument
ms.assetid: 166c8ba8-3fb5-4dd7-a9ea-5bca662d00f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0519373a46e1c25feda7a3130b420c565a96eece
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37339546"
---
# <a name="chtmleditview-class"></a>Klasa CHtmlEditView
Oferuje funkcje platformy edycji WebBrowser w kontekście architektury dokumentu/widoku MFC.  
  
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
|[CHtmlEditView::GetDHtmlDocument](#getdhtmldocument)|Zwraca `IHTMLDocument2` interfejsu do bieżącego dokumentu.|  
|[CHtmlEditView::GetStartDocument](#getstartdocument)|Pobiera nazwę dokument domyślny dla tego widoku.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 [CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)  
  
 [CHtmlView](../../mfc/reference/chtmlview-class.md)  
  
 `CHtmlEditView`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxhtml.h  
  
##  <a name="chtmleditview"></a>  CHtmlEditView::CHtmlEditView  
 Konstruuje `CHtmlEditView` obiektu.  
  
```  
CHtmlEditView();
```  
  
##  <a name="create"></a>  CHtmlEditView::Create  
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
 *lpszClassName*  
 Wskazuje ciąg znaków zakończony znakiem null, że nazwy klas Windows. Nazwa klasy może być dowolna nazwa, zarejestrowane w usłudze [afxregisterwndclass —](application-information-and-management.md#afxregisterwndclass) funkcja globalna lub `RegisterClass` funkcji Windows. Jeśli ma wartość NULL, używa wstępnie zdefiniowanego domyślnego [CFrameWnd](../../mfc/reference/cframewnd-class.md) atrybutów.  
  
 *lpszWindowName*  
 Wskazuje ciąg znaków zakończony znakiem null, który reprezentuje nazwę okna.  
  
 *dwStyle*  
 Określa atrybuty stylu okna. WS_VISIBLE oraz Windows WS_CHILD style są domyślnie.  
  
 *Rect*  
 Odwołanie do [Prostokąt](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, określając rozmiar i położenie okna. *RectDefault* zezwala na wartość Windows określić rozmiar i położenie w nowym oknie.  
  
 *pParentWnd*  
 Wskaźnik do okno nadrzędne kontrolki.  
  
 *nID*  
 Numer identyfikacyjny widoku. Domyślnie Ustaw AFX_IDW_PANE_FIRST.  
  
 *pContext*  
 Wskaźnik do [CCreateContext](../../mfc/reference/ccreatecontext-structure.md). Wartość NULL, domyślnie.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda również wywoła zawartej WebBrowser `Navigate` metodę, aby załadować dokument domyślny (zobacz [CHtmlEditView::GetStartDocument](#getstartdocument)).  
  
##  <a name="getdhtmldocument"></a>  CHtmlEditView::GetDHtmlDocument  
 Zwraca `IHTMLDocument2` interfejsu do bieżącego dokumentu.  
  
```  
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *ppDocument*  
 [IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx) interfejsu.  
  
##  <a name="getstartdocument"></a>  CHtmlEditView::GetStartDocument  
 Pobiera nazwę dokument domyślny dla tego widoku.  
  
```  
virtual LPCTSTR GetStartDocument();
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe HTMLEdit](../../visual-cpp-samples.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)


