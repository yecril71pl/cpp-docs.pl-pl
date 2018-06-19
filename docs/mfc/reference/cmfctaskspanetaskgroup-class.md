---
title: Klasa CMFCTasksPaneTaskGroup | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::SetACCData
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsBottom
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsCollapsed
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsSpecial
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_lstTasks
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_rect
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_rectGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_strName
dev_langs:
- C++
helpviewer_keywords:
- CMFCTasksPaneTaskGroup [MFC], CMFCTasksPaneTaskGroup
- CMFCTasksPaneTaskGroup [MFC], SetACCData
- CMFCTasksPaneTaskGroup [MFC], m_bIsBottom
- CMFCTasksPaneTaskGroup [MFC], m_bIsCollapsed
- CMFCTasksPaneTaskGroup [MFC], m_bIsSpecial
- CMFCTasksPaneTaskGroup [MFC], m_lstTasks
- CMFCTasksPaneTaskGroup [MFC], m_rect
- CMFCTasksPaneTaskGroup [MFC], m_rectGroup
- CMFCTasksPaneTaskGroup [MFC], m_strName
ms.assetid: 2111640b-a46e-4b27-b033-29e88632b86a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d51b29f9ea2719f98f263565680ded2360197572
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370848"
---
# <a name="cmfctaskspanetaskgroup-class"></a>Klasa CMFCTasksPaneTaskGroup
`CMFCTasksPaneTaskGroup` Klasa jest używana przez klasę Pomocnika [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md) formantu. Obiekty typu `CMFCTasksPaneTaskGroup` reprezentują *grupy zadań*. Grupy zadań znajduje się lista elementów, które w ramach będzie wyświetlany w osobnym oknie posiadające przycisk Zwiń. Pole może mieć opcjonalnym podpisem (nazwa grupy). Jeśli grupa jest zwinięte, na liście zadań nie jest widoczne.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCTasksPaneTaskGroup : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup](#cmfctaskspanetaskgroup)|Konstruuje `CMFCTasksPaneTaskGroup` obiektu.|  
|`CMFCTasksPaneTaskGroup::~CMFCTasksPaneTaskGroup`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCTasksPaneTaskGroup::SetACCData](#setaccdata)|Określa dane ułatwień dostępu dla bieżącej grupy zadań.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCTasksPaneTaskGroup::m_bIsBottom](#m_bisbottom)|Określa, czy grupy zadań jest wyrównane do dolnej części formant okienka zadań.|  
|[CMFCTasksPaneTaskGroup::m_bIsCollapsed](#m_biscollapsed)|Określa, czy jest zwinięte grupy zadań.|  
|[CMFCTasksPaneTaskGroup::m_bIsSpecial](#m_bisspecial)|Określa, czy grupa zadań *specjalne.* Platformę Wyświetla specjalne podpisów w innym kolorze.|  
|[CMFCTasksPaneTaskGroup::m_lstTasks](#m_lsttasks)|Zawiera wewnętrzną listę zadań.|  
|[CMFCTasksPaneTaskGroup::m_rect](#m_rect)|Określa prostokąt ograniczający podpis grupy.|  
|[CMFCTasksPaneTaskGroup::m_rectGroup](#m_rectgroup)|Określa prostokątem grupy.|  
|[CMFCTasksPaneTaskGroup::m_strName](#m_strname)|Określa nazwę grupy.|  
  
## <a name="remarks"></a>Uwagi  
 Na poniższej ilustracji przedstawiono grupy zadań rozszerzonej:  
  
 ![Grupy zadań, rozwinięty](../../mfc/reference/media/nexttaskgrpexpand.png "nexttaskgrpexpand")  
  
 Poniższa ilustracja przedstawia grupę zwinięte zadań:  
  
 ![Grupy zadań zwinięte](../../mfc/reference/media/nexttaskgrpcollapse.png "nexttaskgrpcollapse")  
  
 Na poniższej ilustracji przedstawiono bez podpisu grupy zadań:  
  
 ![Grupy zadań bez podpisu](../../mfc/reference/media/nexttaskgrpnocapt.png "nexttaskgrpnocapt")  
  
 Na poniższej ilustracji przedstawiono dwie grupy zadań. Pierwsza grupa zadań jest oznaczony jako specjalne przez ustawienie `m_bIsSpecial` flaga `TRUE`, podczas gdy nie jest specjalne drugiej grupy zadań. Należy zwrócić uwagę, jak podpis dla pierwszej grupy zadań jest ciemniejsze od drugiej grupy zadań:  
  
 ![Grupy zadań specjalne](../../mfc/reference/media/nexttaskgrpspecial.png "nexttaskgrpspecial")  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxTasksPane.h  
  
##  <a name="cmfctaskspanetaskgroup"></a>  CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup  
 Konstruuje `CMFCTasksPaneTaskGroup` obiektu.  
  
```  
CMFCTasksPaneTaskGroup(
    LPCTSTR lpszName,  
    BOOL bIsBottom,  
    BOOL bIsSpecial=FALSE,  
    BOOL bIsCollapsed=FALSE,  
    CMFCTasksPanePropertyPage* pPage=NULL,  
    HICON hIcon=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Określa nazwę grupy w nagłówku grupy.  
  
 `bIsBottom`  
 Określa, czy grupa jest wyrównany do dołu formant okienka zadań.  
  
 `bIsSpecial`  
 Określa, czy grupa jest oznaczony jako *specjalne* i w związku z tym, czy podpis grupy jest wypełniana innym kolorem.  
  
 `bIsCollapsed`  
 Określa, czy grupa zostanie zwinięta.  
  
 `pPage`  
 Określa stronę właściwości należącego do tej grupy zadań.  
  
 `hIcon`  
 Określa ikonę, która wyświetla tytuł grupy.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_bisbottom"></a>  CMFCTasksPaneTaskGroup::m_bIsBottom  
 Określa, czy grupy zadań jest wyrównane do dolnej części formant okienka zadań.  
  
```  
BOOL m_bIsBottom;  
```  
  
### <a name="remarks"></a>Uwagi  
 Tylko jedna grupa może być wyrównany do dołu formant okienka zadań. Tej grupy zadań musi zostać dodany jako ostatnie. Aby uzyskać więcej informacji, zobacz [CMFCTasksPane::AddGroup](../../mfc/reference/cmfctaskspane-class.md#addgroup).  
  
##  <a name="m_biscollapsed"></a>  CMFCTasksPaneTaskGroup::m_bIsCollapsed  
 Określa, czy jest zwinięte grupy zadań.  
  
```  
BOOL m_bIsCollapsed;  
```  
  
### <a name="remarks"></a>Uwagi  
 Można włączyć lub wyłączyć możliwość zwinąć grupy w okienku zadań, wywołując [CMFCTasksPane::EnableGroupCollapse](../../mfc/reference/cmfctaskspane-class.md#enablegroupcollapse).  
  
##  <a name="m_bisspecial"></a>  CMFCTasksPaneTaskGroup::m_bIsSpecial  
 Określa, czy grupa zadań jest *specjalne* i określa, czy podpis dla grupy zadań specjalne należy zidentyfikować według różnych kolorów.  
  
```  
BOOL m_bIsSpecial;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli aplikacja używa motyw wizualny systemu Windows XP i `m_bIsSpecial` jest `FALSE`, wywołania framework `DrawThemeBackground` z `EBP_NORMALGROUPBACKGROUND` flagi. Jeśli `m_bIsSpecial` jest `TRUE`, wywołania framework `DrawThemeBackground` z `EBP_SPECIALGROUPBACKGROUND` flagi.  
  
##  <a name="m_lsttasks"></a>  CMFCTasksPaneTaskGroup::m_lstTasks  
 Zawiera wewnętrzną listę zadań.  
  
```  
CObList m_lstTasks;  
```  
  
### <a name="remarks"></a>Uwagi  
 Aby wypełnić tej listy, należy wywołać [CMFCTasksPane::AddTask](../../mfc/reference/cmfctaskspane-class.md#addtask).  
  
##  <a name="m_rect"></a>  CMFCTasksPaneTaskGroup::m_rect  
 Określa prostokąt ograniczający podpis grupy.  
  
```  
CRect m_rect;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta wartość jest obliczana automatycznie przez platformę.  
  
##  <a name="m_rectgroup"></a>  CMFCTasksPaneTaskGroup::m_rectGroup  
 Określa prostokątem grupy.  
  
```  
CRect m_rectGroup;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta wartość jest obliczana automatycznie przez platformę.  
  
##  <a name="m_strname"></a>  CMFCTasksPaneTaskGroup::m_strName  
 Określa nazwę grupy.  
  
```  
CString m_strName;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ta wartość jest pusta, nie jest wyświetlany podpis grupy i grupy nie może zostać zwinięty.  
  
##  <a name="setaccdata"></a>  CMFCTasksPaneTaskGroup::SetACCData  
 Określa dane ułatwień dostępu dla bieżącej grupy zadań.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pParent`  
 Reprezentuje okno nadrzędne bieżącej grupy zadań.  
  
 [out] `data`  
 Obiekt typu `CAccessibilityData` który jest wypełniane przy użyciu danych dostępności bieżącej grupy zadań.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli `data` parametr został pomyślnie wypełnione przy użyciu danych dostępności bieżącej grupy zadań, a w przeciwnym razie `FALSE`.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)   
 [Klasa CMFCTasksPaneTask](../../mfc/reference/cmfctaskspanetask-class.md)   
 [Klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)   
 [Klasa CObject](../../mfc/reference/cobject-class.md)
