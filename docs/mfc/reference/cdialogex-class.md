---
title: Klasa CDialogEx | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDialogEx
- AFXDIALOGEX/CDialogEx
- AFXDIALOGEX/CDialogEx::CDialogEx
- AFXDIALOGEX/CDialogEx::SetBackgroundColor
- AFXDIALOGEX/CDialogEx::SetBackgroundImage
dev_langs:
- C++
helpviewer_keywords:
- CDialogEx [MFC], CDialogEx
- CDialogEx [MFC], SetBackgroundColor
- CDialogEx [MFC], SetBackgroundImage
ms.assetid: a6ed3b1f-aef8-4b66-ac78-2160faf63c13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff365134a9b952b92211418c03d147a65077c66e
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951855"
---
# <a name="cdialogex-class"></a>Klasa CDialogEx
`CDialogEx` Klasa określa kolor tła i obraz tła okna dialogowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDialogEx : public CDialog  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDialogEx::CDialogEx](#cdialogex)|Konstruuje `CDialogEx` obiektu.|  
|`CDialogEx::~CDialogEx`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDialogEx::SetBackgroundColor](#setbackgroundcolor)|Ustawia kolor tła okna dialogowego.|  
|[CDialogEx::SetBackgroundImage](#setbackgroundimage)|Ustawia obraz tła okna dialogowego.|  
  
## <a name="remarks"></a>Uwagi  
 Aby użyć `CDialogEx` klasy, pochodzi z klasy okien dialogowych pole `CDialogEx` klasy zamiast `CDialog` klasy.  
  
 Obrazy — okno dialogowe, są przechowywane w pliku zasobu. Platformę automatycznie usuwa żadnego obrazu, który jest ładowany z pliku zasobów. Aby programowo usunąć bieżący obraz tła, wywołaj [CDialogEx::SetBackgroundImage](#setbackgroundimage) metody lub zaimplementuj `OnDestroy` obsługi zdarzeń. Podczas wywoływania [CDialogEx::SetBackgroundImage](#setbackgroundimage) metody, Przekaż `HBITMAP` parametr jako dojście obrazu. `CDialogEx` Obiekt zostanie przejąć na własność obrazu i usuń go, jeśli `m_bAutoDestroyBmp` flaga jest `TRUE`.  
  
 A `CDialogEx` obiekt może być elementem nadrzędnym [klasy CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) obiektu. [Klasy CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) obiektu wywołania `CDialogEx::SetActiveMenu` — metoda podczas [klasy CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) obiekt zostanie otwarta. W efekcie `CDialogEx` obiektu obsługuje wszystkie zdarzenia menu do [klasy CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) obiekt jest zamknięty.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdialogex.h  
  
##  <a name="cdialogex"></a>  CDialogEx::CDialogEx  
 Konstruuje `CDialogEx` obiektu.  
  
```  
CDialogEx(
    UINT nIDTemplate,  
    CWnd* pParent=NULL);

 
CDialogEx(
    LPCTSTR lpszTemplateName,  
    CWnd* pParentWnd=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nIDTemplate*  
 Identyfikator zasobu szablonu — okno dialogowe.  
  
 [in] *lpszTemplateName*  
 Nazwa zasobu szablonu — okno dialogowe.  
  
 [in] *pParent*  
 Wskaźnik do okna nadrzędnego. Wartość domyślna to `NULL`.  
  
 [in] *pParentWnd*  
 Wskaźnik do okna nadrzędnego. Wartość domyślna to `NULL`.  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setbackgroundcolor"></a>  CDialogEx::SetBackgroundColor  
 Ustawia kolor tła okna dialogowego.  
  
```  
void SetBackgroundColor(
    COLORREF color,  
    BOOL bRepaint=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *kolorów*  
 Wartości kolorów RGB.  
  
 [in] *bRepaint*  
 `TRUE` Aby natychmiast zaktualizować ekranu; w przeciwnym razie `FALSE`. Wartość domyślna to `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setbackgroundimage"></a>  CDialogEx::SetBackgroundImage  
 Ustawia obraz tła okna dialogowego.  
  
```  
void SetBackgroundImage(
    HBITMAP hBitmap,  
    BackgroundLocation location=BACKGR_TILE,  
    BOOL bAutoDestroy=TRUE,  
    BOOL bRepaint=TRUE);

 
BOOL SetBackgroundImage(
    UINT uiBmpResId,  
    BackgroundLocation location=BACKGR_TILE,  
    BOOL bRepaint=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *hBitmap*  
 Dojście do obrazu tła.  
  
 [in] *uiBmpResId*  
 Identyfikator zasobu obrazu tła.  
  
 [in] *lokalizacji*  
 Jeden z `CDialogEx::BackgroundLocation` wartości, które określają lokalizację obrazu. Prawidłowe wartości to BACKGR_TILE, BACKGR_TOPLEFT BACKGR_TOPRIGHT, BACKGR_BOTTOMLEFT i BACKGR_BOTTOMRIGHT. Wartość domyślna to BACKGR_TILE.  
  
 [in] *bAutoDestroy*  
 `TRUE` Aby automatycznie zniszczyć obraz tła; w przeciwnym razie `FALSE`.  
  
 [in] *bRepaint*  
 `TRUE` Aby natychmiast odświeżyć okno dialogowe; w przeciwnym razie `FALSE`.  
  
### <a name="return-value"></a>Wartość zwracana  
 W drugiej metody przeciążenia składni `TRUE` przypadku powodzenia; w przeciwnym razie metody `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Obraz, który określisz nie jest rozciągany tak, aby dopasować obszaru klienckiego — okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)   
 [Klasa CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)
