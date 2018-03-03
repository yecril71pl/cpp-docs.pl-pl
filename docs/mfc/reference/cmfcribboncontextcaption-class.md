---
title: Klasa CMFCRibbonContextCaption | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonContextCaption
- AFXRIBBONBAR/CMFCRibbonContextCaption
- AFXRIBBONBAR/CMFCRibbonContextCaption::GetColor
- AFXRIBBONBAR/CMFCRibbonContextCaption::GetRightTabX
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonContextCaption [MFC], GetColor
- CMFCRibbonContextCaption [MFC], GetRightTabX
ms.assetid: cce2c0a2-8370-4266-997e-f8d0eeb3d616
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fc05d791ad1d9fc51d11947686e0d6b939ef982f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribboncontextcaption-class"></a>Klasa CMFCRibbonContextCaption
Implementuje kolorowe Podpis wyświetlany w górnej części kategoria Wstążki lub kontekstu.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCRibbonContextCaption : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CMFCRibbonContextCaption::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|  
|[CMFCRibbonContextCaption::GetColor](#getcolor)|Zwraca kolor podpis.|  
|[CMFCRibbonContextCaption::GetRightTabX](#getrighttabx)||  
|`CMFCRibbonContextCaption::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa nie można wdrożyć bezpośrednio. [Klasy CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md) klasa korzysta z tej klasy wewnętrznie można dodać do wstążki kategorii koloru.  
  
 Aby ustawić kolor dla kategorii wstążki, należy wywołać [CMFCRibbonCategory::SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor). Aby ustawić kolor dla kategorii kontekstu, wywołaj [CMFCRibbonBar::AddContextCategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonContextCaption](../../mfc/reference/cmfcribboncontextcaption-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxRibbonBar.h  
  
##  <a name="getcolor"></a>CMFCRibbonContextCaption::GetColor  
 Zwraca kolor tła podpisu.  
  
```  
AFX_RibbonCategoryColor GetColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwrócona wartość może być jedną z następujących wartości:  
  
- `AFX_CategoryColor_None`  
  
- `AFX_CategoryColor_Red`  
  
- `AFX_CategoryColor_Orange`  
  
- `AFX_CategoryColor_Yellow`  
  
- `AFX_CategoryColor_Green`  
  
- `AFX_CategoryColor_Blue`  
  
- `AFX_CategoryColor_Indigo`  
  
- `AFX_CategoryColor_Violet`  
  
### <a name="remarks"></a>Uwagi  
 Można ustawić kolor podpis wywołując [CMFCRibbonCategory::SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor) lub [CMFCRibbonBar::AddContextCategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory).  
  
##  <a name="getrighttabx"></a>CMFCRibbonContextCaption::GetRightTabX  
 Pobiera położenie prawej krawędzi kategorii karty wstążki.  
  
```  
int GetRightTabX() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca po prawej stronie X wartość otaczającego prostokąt `CMFCRibbonCategory` obiektu karty Wstążki lub wartość -1, jeśli karcie zostały obcięte.  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)   
 [Klasa CMFCRibbonCategory](../../mfc/reference/cmfcribboncategory-class.md)   
 [Klasa CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)
