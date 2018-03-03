---
title: Klasa CMFCStandardColorsPropertyPage | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CMFCStandardColorsPropertyPage class [MFC]
ms.assetid: b84b7cfb-bb24-4c65-804a-5b642cb64400
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 60deb16628802e61ac411d576558a8659a638410
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcstandardcolorspropertypage-class"></a>Klasa CMFCStandardColorsPropertyPage
Reprezentuje użytkowników umożliwia wybranie standardowe kolory w oknie dialogowym kolor strony właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCStandardColorsPropertyPage : public CPropertyPage  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|||  
|-|-|  
|Nazwa|Opis|  
|`CMFCStandardColorsPropertyPage::CMFCStandardColorsPropertyPage`|Domyślny konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|||  
|-|-|  
|Nazwa|Opis|  
|`CMFCStandardColorsPropertyPage::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|  
|`CMFCStandardColorsPropertyPage::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
  
### <a name="remarks"></a>Uwagi  
 `CMFCColorDialog` Klasa korzysta z tej klasy do wyświetlenia strony właściwości Kolor standardowy. Aby uzyskać więcej informacji na temat `CMFCColorDialog`, zobacz [CMFCColorDialog klasy](../../mfc/reference/cmfccolordialog-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cdialog —](../../mfc/reference/cdialog-class.md)  
  
 [Cpropertypage —](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCStandardColorsPropertyPage](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxstandardcolorspropertypage.h  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)   
 [Klasa CMFCCustomColorsPropertyPage](../../mfc/reference/cmfccustomcolorspropertypage-class.md)
