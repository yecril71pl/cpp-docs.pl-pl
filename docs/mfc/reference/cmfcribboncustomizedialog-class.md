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
ms.openlocfilehash: d342ec75fd45224dcd36ba3fc17aa1a6f8c12e33
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720658"
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
|`CMFCRibbonCustomizeDialog::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|  
  
## <a name="remarks"></a>Uwagi  
 MFC tworzy wystąpienie tej klasy automatycznie, jeśli nie przetwarzają komunikatów AFX_WM_ON_RIBBON_CUSTOMIZE lub zwracają 0 z obsługi wiadomości.  
  
 Jeśli chcesz użyć tej klasy w aplikacji do wyświetlenia na wstążce **Dostosuj** okna dialogowego pole, po prostu tworzenia jego instancji i wywołania `DoModal` metody.  
  
 Ponieważ ta klasa jest pochodną [klasa CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md), można dodać niestandardowe strony za pomocą `CMFCPropertySheet` interfejsu API.  
  
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
*pWndParent*<br/>
[in] Wskaźnik do nadrzędnego okna (zazwyczaj głównej ramki).  
  
*pRibbon*<br/>
[in] Wskaźnik do `CMFCRibbonBar` który ma zostać dostosowana.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia `CMFCRibbonCustomizeDialog` obiektu.  
  
 [!code-cpp[NVC_MFC_RibbonApp#18](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizedialog-class_1.cpp)]  
  
### <a name="remarks"></a>Uwagi  
 Tworzy konstruktora [klasa CMFCRibbonCustomizePropertyPage](../../mfc/reference/cmfcribboncustomizepropertypage-class.md) obiektu i dodaje go do kolekcji strony arkusza właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)
