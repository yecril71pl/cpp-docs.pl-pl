---
title: Klasa CMFCSpinButtonCtrl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl::OnDraw
dev_langs: C++
helpviewer_keywords: CMFCSpinButtonCtrl [MFC], OnDraw
ms.assetid: 8773f259-4d3f-4bca-a71c-09e0c71bc843
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6736be0cca3c7cbd95ca1a81b5dd652da8d5badb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cmfcspinbuttonctrl-class"></a>Klasa CMFCSpinButtonCtrl
`CMFCSpinButtonCtrl` Klasa obsługuje visual menedżera, która rysuje spin button — formant.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCSpinButtonCtrl : public CSpinButtonCtrl  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CMFCSpinButtonCtrl::CMFCSpinButtonCtrl`|Domyślny konstruktor.|  
|`CMFCSpinButtonCtrl::~CMFCSpinButtonCtrl`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCSpinButtonCtrl::OnDraw](#ondraw)|Odświeża bieżący przycisku pokrętła.|  
  
## <a name="remarks"></a>Uwagi  
 Aby użyć Menedżera visual do rysowania spin button — formant w aplikacji, należy zastąpić wszystkie wystąpienia `CSpinButtonCtrl` klasy z `CMFCSpinButtonCtrl` klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób tworzenia obiektu `CMFCSpinButtonCtrl` klasy i używać jej `Create` metody.  
  
 [!code-cpp[NVC_MFC_RibbonApp#25](../../mfc/reference/codesnippet/cpp/cmfcspinbuttonctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CSpinButtonCtrl](../../mfc/reference/cspinbuttonctrl-class.md)  
  
 [CMFCSpinButtonCtrl](../../mfc/reference/cmfcspinbuttonctrl-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxspinbuttonctrl.h  
  
##  <a name="ondraw"></a>CMFCSpinButtonCtrl::OnDraw  
 Odświeża bieżący przycisku pokrętła.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania framework `CMFCSpinButtonCtrl::OnPaint` metody obsługi [CWnd::OnPaint](../../mfc/reference/cwnd-class.md#onpaint) komunikat i czy metoda z kolei wywołuje to `CMFCSpinButtonCtrl::OnDraw` metody. Przesłonić tę metodę w celu dostosowania sposobu, w ramach rysuje przycisku pokrętła.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)
