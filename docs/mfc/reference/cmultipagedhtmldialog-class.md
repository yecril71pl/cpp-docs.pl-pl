---
title: Klasa CMultiPageDHtmlDialog | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog::CMultiPageDHtmlDialog
dev_langs:
- C++
helpviewer_keywords:
- CMultiPageDHtmlDialog [MFC], CMultiPageDHtmlDialog
ms.assetid: 971accc1-824d-4df4-b4c1-b1a20e0f7e4f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 26f7b2e504738839b965dcdbc9a2a9835250fa8b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmultipagedhtmldialog-class"></a>Klasa CMultiPageDHtmlDialog
Wielostronicowe okna dialogowego sekwencyjnie zawiera wiele stron HTML i obsługuje zdarzenia z każdej strony.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMultiPageDHtmlDialog : public CDHtmlDialog  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMultiPageDHtmlDialog::CMultiPageDHtmlDialog](#cmultipagedhtmldialog)|Tworzy obiekt wielostronicowe okna dialogowego DHTML (stylu kreatora).|  
|[CMultiPageDHtmlDialog:: ~ CMultiPageDHtmlDialog](#cmultipagedhtmldialog__~cmultipagedhtmldialog)|Niszczy obiekt wielostronicowe okna dialogowego DHTML.|  
  
## <a name="remarks"></a>Uwagi  
 Mechanizm ten jest [mapy zdarzeń DHTML i adres URL](dhtml-event-maps.md), który zawiera osadzone mapy zdarzeń dla każdej strony.  
  
## <a name="example"></a>Przykład  
 Wielostronicowe okna dialogowego przyjmuje trzy zasoby HTML definiujące proste funkcje podręczne. Pierwsza strona ma `Next` przycisku, drugi **Prev** i `Next` przycisk, a trzeci **poprzedni** przycisku. Po naciśnięciu jeden z przycisków, wywołań funkcji obsługi [CDHtmlDialog::LoadFromResource](../../mfc/reference/cdhtmldialog-class.md#loadfromresource) można załadować odpowiedniego nowej strony.  
  
 Odpowiednich części deklaracji klasy (w CMyMultiPageDlg.h):  
  
 [!code-cpp[NVC_MFCDocView#181](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_1.h)]  
  
 Odpowiednich części implementacji klasy (w CMyMultipageDlg.cpp):  
  
 [!code-cpp[NVC_MFCDocView#182](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDHtmlSinkHandlerBase2`  
  
 `CDHtmlSinkHandlerBase1`  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDHtmlSinkHandler`  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDHtmlEventSink`  
  
 [Cdialog —](../../mfc/reference/cdialog-class.md)  
  
 [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)  
  
 `CMultiPageDHtmlDialog`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdhtml.h  
  
##  <a name="cmultipagedhtmldialog"></a>CMultiPageDHtmlDialog::CMultiPageDHtmlDialog  
 Tworzy obiekt wielostronicowe okna dialogowego DHTML (stylu kreatora).  
  
```  
CMultiPageDHtmlDialog(
    LPCTSTR lpszTemplateName,  
    LPCTSTR szHtmlResID = NULL,  
    CWnd* pParentWnd = NULL);

 
CMultiPageDHtmlDialog(
    UINT nIDTemplate,  
    UINT nHtmlResID = 0,  
    CWnd* pParentWnd = NULL);  
  
CMultiPageDHtmlDialog();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszTemplateName`  
 Ciąg zerem to nazwa zasobu szablon okno dialogowe.  
  
 `szHtmlResID`  
 Ciąg zerem to nazwa zasobu HTML.  
  
 `pParentWnd`  
 Wskaźnik do obiektu okna nadrzędnego lub właściciela (typu [CWnd](../../mfc/reference/cwnd-class.md)) do której należy obiektu okna dialogowego. Jeśli jest **NULL**, okna nadrzędnego obiektu okna dialogowego ma ustawioną wartość okna głównego aplikacji.  
  
 `nIDTemplate`  
 Zawiera identyfikator zasobu szablon okno dialogowe.  
  
 `nHtmlResID`  
 Zawiera identyfikator zasobu HTML.  
  
##  <a name="_dtorcmultipagedhtmldialog"></a>CMultiPageDHtmlDialog:: ~ CMultiPageDHtmlDialog  
 Niszczy obiekt wielostronicowe okna dialogowego DHTML.  
  
```  
virtual ~CMultiPageDHtmlDialog();
```  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)
