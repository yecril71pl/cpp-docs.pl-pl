---
title: Klasa CMFCRibbonCustomizeDialog | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonCustomizeDialog [MFC], CMFCRibbonCustomizeDialog
ms.assetid: ce67de7f-5eaa-4c75-9b94-f290f36df073
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d195b2888c47a318369df13c371f85b21cc7bf84
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcribboncustomizedialog-class"></a>Klasa CMFCRibbonCustomizeDialog
Wyświetla wstążki **Dostosuj** strony.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCRibbonCustomizeDialog : public CMFCPropertySheet  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog](#cmfcribboncustomizedialog)|Konstruuje `CMFCRibbonCustomizeDialog` obiektu.|  
|`CMFCRibbonCustomizeDialog::~CMFCRibbonCustomizeDialog`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CMFCRibbonCustomizeDialog::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
  
## <a name="remarks"></a>Uwagi  
 MFC automatycznie tworzy tej klasy, jeśli nie mogą przetwarzać komunikat AFX_WM_ON_RIBBON_CUSTOMIZE lub zwraca 0 z obsługi wiadomości.  
  
 Jeśli chcesz użyć tej klasy w aplikacji do wyświetlenia na wstążce **Dostosuj** okna dialogowego pola, wystarczy utworzyć i wywołać `DoModal` metody.  
  
 Ponieważ ta klasa pochodzi od [klasy CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md), możesz dodać niestandardowe strony przy użyciu `CMFCPropertySheet` interfejsu API.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md)  
  
 [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)  
  
 [CMFCRibbonCustomizeDialog](../../mfc/reference/cmfcribboncustomizedialog-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxribboncustomizedialog.h  
  
##  <a name="cmfcribboncustomizedialog"></a>  CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog  
 Konstruuje `CMFCRibbonCustomizeDialog` obiektu.  
  
```  
CMFCRibbonCustomizeDialog(
    CWnd* pWndParent,  
    CMFCRibbonBar* pRibbon);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pWndParent`  
 Wskaźnik do okna nadrzędnego (zazwyczaj ramki głównej).  
  
 [in] `pRibbon`  
 Wskaźnik do `CMFCRibbonBar` to można dostosować.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia `CMFCRibbonCustomizeDialog` obiektu.  
  
 [!code-cpp[NVC_MFC_RibbonApp#18](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizedialog-class_1.cpp)]  
  
### <a name="remarks"></a>Uwagi  
 Tworzy konstruktora [klasy CMFCRibbonCustomizePropertyPage](../../mfc/reference/cmfcribboncustomizepropertypage-class.md) obiektu i dodaje go do kolekcji strony arkusza właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)
