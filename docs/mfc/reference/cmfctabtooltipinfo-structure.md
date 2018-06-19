---
title: Struktura CMFCTabToolTipInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCTabToolTipInfo
dev_langs:
- C++
helpviewer_keywords:
- CMFCTabToolTipInfo struct
ms.assetid: 9c3b3fb9-1497-4d59-932b-0da9348dd5e2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb2d1a139a5bc61d665a28f21ab10979802045b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373732"
---
# <a name="cmfctabtooltipinfo-structure"></a>Struktura CMFCTabToolTipInfo
Ta struktura zawiera informacje dotyczące użytkownika znajduje się na karcie MDI.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct CMFCTabToolTipInfo  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCTabToolTipInfo::m_nTabIndex](#m_ntabindex)|Określa indeks formantu karty.|  
|[CMFCTabToolTipInfo::m_pTabWnd](#m_ptabwnd)|Wskaźnik do formantu karty.|  
|[CMFCTabToolTipInfo::m_strText](#m_strtext)|Tekst etykietki narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 Wskaźnik do `CMFCTabToolTipInfo` struktury jest przekazywana jako parametr `AFX_WM_ON_GET_TAB_TOOLTIP` wiadomości. Ten komunikat jest wyświetlany, gdy kart MDI są włączone i użytkownik jest przesuwany nad formantem karty.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono sposób `CMFCTabToolTipInfo` jest używany w [MDITabsDemo próbki: aplikacji z kartami MDI MFC](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CMFCTabToolTipInfo](../../mfc/reference/cmfctabtooltipinfo-structure.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxbasetabctrl.h  
  
##  <a name="m_ntabindex"></a>  CMFCTabToolTipInfo::m_nTabIndex  
 Określa indeks formantu karty.  
  
```  
int m_nTabIndex;  
```  
  
### <a name="remarks"></a>Uwagi  
 Indeks kartę, w którym znajduje się użytkownik.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono sposób `m_nTabIndex` jest używany w [MDITabsDemo próbki: aplikacji z kartami MDI MFC](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]  
  
##  <a name="m_ptabwnd"></a>  CMFCTabToolTipInfo::m_pTabWnd  
 Wskaźnik do formantu karty.  
  
```  
CMFCBaseTabCtrl* m_pTabWnd;  
```  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono sposób `m_pTabWnd` jest używany w [MDITabsDemo próbki: aplikacji z kartami MDI MFC](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]  
  
##  <a name="m_strtext"></a>  CMFCTabToolTipInfo::m_strText  
 Tekst etykietki narzędzia.  
  
```  
CString m_strText;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ciąg jest pusty, nie jest wyświetlana etykietka narzędzia.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono sposób `m_strText` jest używany w [MDITabsDemo próbki: aplikacji z kartami MDI MFC](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)
