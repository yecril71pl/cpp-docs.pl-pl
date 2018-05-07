---
title: Klasa CCommonDialog | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCommonDialog
- AFXDLGS/CCommonDialog
- AFXDLGS/CCommonDialog::CCommonDialog
dev_langs:
- C++
helpviewer_keywords:
- CCommonDialog [MFC], CCommonDialog
ms.assetid: 1f68d65f-a0fd-4778-be22-ebbe51a95f95
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 19f8c0aa6aaa4980466918eac2649cc246b2e6ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ccommondialog-class"></a>Klasa CCommonDialog
Klasa podstawowa dla klas, które zapewniają funkcje wspólne okna dialogowe systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CCommonDialog : public CDialog  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCommonDialog::CCommonDialog](#ccommondialog)|Konstruuje `CCommonDialog` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Następujące klasy Hermetyzowanie funkcji wspólne okna dialogowe systemu Windows:  
  
- [CFileDialog](../../mfc/reference/cfiledialog-class.md)  
  
- [CFontDialog](../../mfc/reference/cfontdialog-class.md)  
  
- [CColorDialog](../../mfc/reference/ccolordialog-class.md)  
  
- [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)  
  
- [CPrintDialog](../../mfc/reference/cprintdialog-class.md)  
  
- [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md)  
  
- [CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)  
  
- [COleDialog](../../mfc/reference/coledialog-class.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `CCommonDialog`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdlgs.h  
  
##  <a name="ccommondialog"></a>  CCommonDialog::CCommonDialog  
 Konstruuje `CCommonDialog` obiektu.  
  
```  
explicit CCommonDialog(CWnd* pParentWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentWnd`  
 Wskazuje obiekt okna nadrzędnego lub właściciela (typu [CWnd](../../mfc/reference/cwnd-class.md)) do której należy obiektu okna dialogowego. Jeśli jest **NULL**, okna nadrzędnego obiektu okna dialogowego ma ustawioną wartość okna głównego aplikacji.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [CDialog::CDialog](../../mfc/reference/cdialog-class.md#cdialog) pełne informacje.  
  
## <a name="see-also"></a>Zobacz też  
 [Cdialog — klasa](../../mfc/reference/cdialog-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CFileDialog](../../mfc/reference/cfiledialog-class.md)   
 [Klasa CFontDialog](../../mfc/reference/cfontdialog-class.md)   
 [Klasa CColorDialog](../../mfc/reference/ccolordialog-class.md)   
 [Klasa CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)   
 [Klasa CPrintDialog](../../mfc/reference/cprintdialog-class.md)   
 [Klasa CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)   
 [Klasa COleDialog](../../mfc/reference/coledialog-class.md)
