---
title: Klasa COleResizeBar | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleResizeBar
- AFXOLE/COleResizeBar
- AFXOLE/COleResizeBar::COleResizeBar
- AFXOLE/COleResizeBar::Create
dev_langs: C++
helpviewer_keywords:
- COleResizeBar [MFC], COleResizeBar
- COleResizeBar [MFC], Create
ms.assetid: 56a708d9-28c5-4eb0-9404-77b688d91c63
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3369ef30758b687c94c97e5fb0cf18bb7565ea83
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="coleresizebar-class"></a>Klasa COleResizeBar
Typ pasków sterowania, który obsługuje zmienianie rozmiaru w miejscu elementy OLE.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COleResizeBar : public CControlBar  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleResizeBar::COleResizeBar](#coleresizebar)|Konstruuje `COleResizeBar` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleResizeBar::Create](#create)|Tworzy i inicjuje okno podrzędne systemu Windows i kojarzy ją do `COleResizeBar` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `COleResizeBar`obiekty są wyświetlane jako [crecttracker —](../../mfc/reference/crecttracker-class.md) z kreskowanym obramowaniem i zewnętrznych uchwyty zmiany rozmiaru.  
  
 `COleResizeBar`obiekty są zwykle osadzonych członkami okno ramowe obiektów pochodzących od [COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md) klasy.  
  
 Aby uzyskać więcej informacji, zobacz artykuł [aktywacji](../../mfc/activation-cpp.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Ccontrolbar —](../../mfc/reference/ccontrolbar-class.md)  
  
 `COleResizeBar`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxole.h  
  
##  <a name="coleresizebar"></a>COleResizeBar::COleResizeBar  
 Konstruuje `COleResizeBar` obiektu.  
  
```  
COleResizeBar();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie **Utwórz** można utworzyć obiektu pasek zmiany rozmiaru.  
  
##  <a name="create"></a>COleResizeBar::Create  
 Tworzy okno podrzędne i kojarzy ją z `COleResizeBar` obiektu.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,  
    UINT nID = AFX_IDW_RESIZE_BAR);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentWnd`  
 Wskaźnik do okno nadrzędne paska zmiany rozmiaru.  
  
 `dwStyle`  
 Określa [styl okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) atrybutów.  
  
 `nID`  
 Identyfikator pasek zmiany rozmiaru okna podrzędnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli utworzono pasek; w przeciwnym razie 0.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC SUPERPAD](../../visual-cpp-samples.md)   
 [Ccontrolbar — klasa](../../mfc/reference/ccontrolbar-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleServerDoc](../../mfc/reference/coleserverdoc-class.md)
