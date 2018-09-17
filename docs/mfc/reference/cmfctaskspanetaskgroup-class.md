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
ms.openlocfilehash: 57c7c55ae2214c4123973e93c65f5e189d32b99a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701652"
---
# <a name="cmfctaskspanetaskgroup-class"></a>Klasa CMFCTasksPaneTaskGroup
`CMFCTasksPaneTaskGroup` Klasa jest klasą pomocnika używaną przez [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md) kontroli. Obiekty typu `CMFCTasksPaneTaskGroup` reprezentują *grupy zadań*. Grupa zadań to lista elementów wyświetlanych w osobnym oknie z przyciskiem rozwijania. To pole może mieć opcjonalny podpisem (nazwa grupy). Jeśli grupa jest zwinięta, lista zadań nie jest widoczny.  
  
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
|[CMFCTasksPaneTaskGroup::m_bIsBottom](#m_bisbottom)|Określa, czy grupy zadań jest wyrównane do dolnej części kontrolki okienka zadań.|  
|[CMFCTasksPaneTaskGroup::m_bIsCollapsed](#m_biscollapsed)|Określa, czy jest zwinięte grupy zadań.|  
|[CMFCTasksPaneTaskGroup::m_bIsSpecial](#m_bisspecial)|Określa, czy grupa zadań *specjalne.* Struktura wyświetla specjalny podpisów w innym kolorze.|  
|[CMFCTasksPaneTaskGroup::m_lstTasks](#m_lsttasks)|Zawiera wewnętrzną listę zadań.|  
|[CMFCTasksPaneTaskGroup::m_rect](#m_rect)|Określa prostokąt otaczający podpis grupy.|  
|[CMFCTasksPaneTaskGroup::m_rectGroup](#m_rectgroup)|Określa prostokąt otaczający grupy.|  
|[CMFCTasksPaneTaskGroup::m_strName](#m_strname)|Określa nazwę grupy.|  
  
## <a name="remarks"></a>Uwagi  
 Poniższa ilustracja przedstawia grupę zadań rozszerzonej:  
  
 ![Grupy zadań, rozwinięte](../../mfc/reference/media/nexttaskgrpexpand.png "nexttaskgrpexpand")  
  
 Poniższa ilustracja przedstawia grupę zwinięty zadań:  
  
 ![Grupa zadań zwinięty](../../mfc/reference/media/nexttaskgrpcollapse.png "nexttaskgrpcollapse")  
  
 Na poniższej ilustracji przedstawiono grupy zadań bez podpisu:  
  
 ![Grupy zadań bez podpisu](../../mfc/reference/media/nexttaskgrpnocapt.png "nexttaskgrpnocapt")  
  
 Poniższa ilustracja przedstawia dwa grup zadań. Pierwsza grupa zadania jest oznaczony jako specjalne, ustawiając `m_bIsSpecial` Flaga o wartości TRUE, podczas gdy druga grupa zadań nie jest specjalne. Należy zwrócić uwagę, jak podpis dla pierwszej grupy zadań jest ciemniejsze od drugiej grupy zadań:  
  
 ![Grupa zadań specjalnych](../../mfc/reference/media/nexttaskgrpspecial.png "nexttaskgrpspecial")  
  
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
 *lpszName*  
 Określa nazwę grupy w podpis grupy.  
  
 *bIsBottom*  
 Określa, czy grupy jest wyrównane do dolnej części kontrolki okienka zadań.  
  
 *bIsSpecial*  
 Określa, czy grupa jest wyznaczony jako *specjalne* i w związku z tym, czy podpis grupy jest wypełniana przy użyciu różnych kolorów.  
  
 *bIsCollapsed*  
 Określa, czy grupa jest zwinięta.  
  
 *Strona_fizyczna*  
 Określa strony właściwości, do której należy ta grupa zadaniowa.  
  
 *hIcon*  
 Określa ikonę, która wyświetla napis grupy.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_bisbottom"></a>  CMFCTasksPaneTaskGroup::m_bIsBottom  
 Określa, czy grupy zadań jest wyrównane do dolnej części kontrolki okienka zadań.  
  
```  
BOOL m_bIsBottom;  
```  
  
### <a name="remarks"></a>Uwagi  
 Tylko jedna grupa może być wyrównany do dolnej części kontrolki okienka zadań. Ta grupa zadaniowa musi zostać dodany jako ostatnia. Aby uzyskać więcej informacji, zobacz [CMFCTasksPane::AddGroup](../../mfc/reference/cmfctaskspane-class.md#addgroup).  
  
##  <a name="m_biscollapsed"></a>  CMFCTasksPaneTaskGroup::m_bIsCollapsed  
 Określa, czy jest zwinięte grupy zadań.  
  
```  
BOOL m_bIsCollapsed;  
```  
  
### <a name="remarks"></a>Uwagi  
 Można włączyć lub wyłączyć możliwość zwinąć grupy i w okienku zadań, wywołując [CMFCTasksPane::EnableGroupCollapse](../../mfc/reference/cmfctaskspane-class.md#enablegroupcollapse).  
  
##  <a name="m_bisspecial"></a>  CMFCTasksPaneTaskGroup::m_bIsSpecial  
 Określa, czy grupa zadań *specjalne* i tego, czy podpis dla grupy zadań specjalnych byli definiowani przez inny kolor.  
  
```  
BOOL m_bIsSpecial;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli aplikacja wykorzystuje motyw wizualny Windows XP i `m_bIsSpecial` ma wartość FAŁSZ, struktura wywołuje `DrawThemeBackground` z flagą EBP_NORMALGROUPBACKGROUND. Jeśli `m_bIsSpecial` ma wartość PRAWDA, struktura wywołuje `DrawThemeBackground` z flagą EBP_SPECIALGROUPBACKGROUND.  
  
##  <a name="m_lsttasks"></a>  CMFCTasksPaneTaskGroup::m_lstTasks  
 Zawiera wewnętrzną listę zadań.  
  
```  
CObList m_lstTasks;  
```  
  
### <a name="remarks"></a>Uwagi  
 Aby wypełnić tej listy, należy wywołać [CMFCTasksPane::AddTask](../../mfc/reference/cmfctaskspane-class.md#addtask).  
  
##  <a name="m_rect"></a>  CMFCTasksPaneTaskGroup::m_rect  
 Określa prostokąt otaczający podpis grupy.  
  
```  
CRect m_rect;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta wartość jest obliczana automatycznie przez platformę.  
  
##  <a name="m_rectgroup"></a>  CMFCTasksPaneTaskGroup::m_rectGroup  
 Określa prostokąt otaczający grupy.  
  
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
 Jeśli ta wartość jest pusta, podpis grupy nie jest wyświetlany, i nie może być zwinięte grupy.  
  
##  <a name="setaccdata"></a>  CMFCTasksPaneTaskGroup::SetACCData  
 Określa dane ułatwień dostępu dla bieżącej grupy zadań.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parametry  
*pParent*<br/>
[in] Reprezentuje okno nadrzędne bieżącej grupy zadań.  
  
*Dane*<br/>
[out] Obiekt typu `CAccessibilityData` , jest wypełniana danymi dostępności bieżącej grupy zadań.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli *danych* parametr został pomyślnie wypełnione danymi ułatwień dostępu w bieżącej grupy zadań; w przeciwnym razie FALSE.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)   
 [Klasa CMFCTasksPaneTask](../../mfc/reference/cmfctaskspanetask-class.md)   
 [Klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)   
 [Klasa CObject](../../mfc/reference/cobject-class.md)
