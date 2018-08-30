---
title: Klasa CMFCPropertyPage | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage::CMFCPropertyPage
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyPage [MFC], CMFCPropertyPage
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b552417af72b24cddae9055d436a56f771c48743
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43203450"
---
# <a name="cmfcpropertypage-class"></a>Klasa CMFCPropertyPage
`CMFCPropertyPage` Klasa obsługuje wyświetlanie wyskakujących menu na stronie właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCPropertyPage : public CPropertyPage  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCPropertyPage::CMFCPropertyPage](#cmfcpropertypage)|Konstruuje `CMFCPropertyPage` obiektu.|  
|`CMFCPropertyPage::~CMFCPropertyPage`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CMFCPropertyPage::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|  
|`CMFCPropertyPage::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|  
|`CMFCPropertyPage::OnSetActive`|Ta funkcja członkowska jest wywoływana przez platformę, gdy strona jest wybierany przez użytkownika i staje się stroną aktywną. (Przesłania [CPropertyPage::OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).)|  
|`CMFCPropertyPage::PreTranslateMessage`|Wykonuje translację komunikatów okien, zanim zostaną rozesłane do [TranslateMessage](https://msdn.microsoft.com/library/windows/desktop/ms644955) i [DispatchMessage](https://msdn.microsoft.com/library/windows/desktop/ms644934) funkcje Windows. Aby uzyskać więcej informacji i składnia metody, zobacz [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Przesłania `CPropertyPage::PreTranslateMessage`.)|  
  
## <a name="remarks"></a>Uwagi  
 `CMFCPropertyPage` Klasa przedstawia pojedyncze strony arkusza właściwości, znane również jako zakładki okna dialogowego.  
  
 Użyj `CMFCPropertyPage` klasy wraz z [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) klasy. Aby użyć menu na stronie właściwości, należy zastąpić wszystkie wystąpienia `CPropertyPage` klasy `CMFCPropertyPage` klasy.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxpropertypage.h  
  
##  <a name="cmfcpropertypage"></a>  CMFCPropertyPage::CMFCPropertyPage  
 Konstruuje `CMFCPropertyPage` obiektu.  
  
```  
CMFCPropertyPage(
    UINT nIDTemplate,  
    UINT nIDCaption=0);

 
CMFCPropertyPage(
    LPCTSTR lpszTemplateName,  
    UINT nIDCaption=0);
```  
  
### <a name="parameters"></a>Parametry  
 *nIDTemplate*  
 Identyfikator zasobu szablon dla tej strony.  
  
 *nIDCaption*  
 Identyfikator zasobu etykiety, aby umieścić na karcie tej strony. Jeśli jest to 0, nazwa jest uzyskiwana z szablonu okna dialogowego na tej stronie. Wartość domyślna to 0.  
  
 *lpszTemplateName*  
 Wskazuje nazwę szablonu dla tej strony. Nie może mieć wartości NULL.  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat parametrów konstruktora, zobacz [CPropertyPage::CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage).  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)
