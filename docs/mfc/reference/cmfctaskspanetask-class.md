---
title: Klasa CMFCTasksPaneTask | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCTasksPaneTask
- AFXTASKSPANE/CMFCTasksPaneTask
- AFXTASKSPANE/CMFCTasksPaneTask::CMFCTasksPaneTask
- AFXTASKSPANE/CMFCTasksPaneTask::SetACCData
- AFXTASKSPANE/CMFCTasksPaneTask::m_bAutoDestroyWindow
- AFXTASKSPANE/CMFCTasksPaneTask::m_bIsBold
- AFXTASKSPANE/CMFCTasksPaneTask::m_dwUserData
- AFXTASKSPANE/CMFCTasksPaneTask::m_hwndTask
- AFXTASKSPANE/CMFCTasksPaneTask::m_nIcon
- AFXTASKSPANE/CMFCTasksPaneTask::m_nWindowHeight
- AFXTASKSPANE/CMFCTasksPaneTask::m_pGroup
- AFXTASKSPANE/CMFCTasksPaneTask::m_rect
- AFXTASKSPANE/CMFCTasksPaneTask::m_strName
- AFXTASKSPANE/CMFCTasksPaneTask::m_uiCommandID
dev_langs:
- C++
helpviewer_keywords:
- CMFCTasksPaneTask [MFC], CMFCTasksPaneTask
- CMFCTasksPaneTask [MFC], SetACCData
- CMFCTasksPaneTask [MFC], m_bAutoDestroyWindow
- CMFCTasksPaneTask [MFC], m_bIsBold
- CMFCTasksPaneTask [MFC], m_dwUserData
- CMFCTasksPaneTask [MFC], m_hwndTask
- CMFCTasksPaneTask [MFC], m_nIcon
- CMFCTasksPaneTask [MFC], m_nWindowHeight
- CMFCTasksPaneTask [MFC], m_pGroup
- CMFCTasksPaneTask [MFC], m_rect
- CMFCTasksPaneTask [MFC], m_strName
- CMFCTasksPaneTask [MFC], m_uiCommandID
ms.assetid: c5a7513b-cd8f-4e2e-b16f-650e1fe30954
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 041a207af69ac65646e1b30672250b84aa3a5d36
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853972"
---
# <a name="cmfctaskspanetask-class"></a>Klasa CMFCTasksPaneTask
`CMFCTasksPaneTask` Klasy jest pomocnikiem klasy, która reprezentuje zadania związane z formantem panelu zadań ( [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)). Obiekt zadania przedstawia element w grupie zadań ( [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)). Każde zadanie może mieć polecenie, które wykonuje szablon, gdy użytkownik kliknie ikonę która pojawia się na lewo od nazwy zadania i zadania.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCTasksPaneTask : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCTasksPaneTask::CMFCTasksPaneTask](#cmfctaskspanetask)|Tworzy i inicjuje `CMFCTasksPaneTask` obiektu.|  
|`CMFCTasksPaneTask::~CMFCTasksPaneTask`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCTasksPaneTask::SetACCData](#setaccdata)|Określa dane ułatwień dostępu dla bieżącego zadania.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCTasksPaneTask::m_bAutoDestroyWindow](#m_bautodestroywindow)|Określa, czy okno zadań automatycznie zostanie zniszczony.|  
|[CMFCTasksPaneTask::m_bIsBold](#m_bisbold)|Określa, czy struktury rysuje etykieta zadania pogrubioną czcionką.|  
|[CMFCTasksPaneTask::m_dwUserData](#m_dwuserdata)|Zawiera dane zdefiniowane przez użytkownika struktura zostanie skojarzony z zadaniem. Jeśli zadanie nie ma skojarzonych danych, należy ustawić na zero.|  
|[CMFCTasksPaneTask::m_hwndTask](#m_hwndtask)|Dojście do okna zadań.|  
|[CMFCTasksPaneTask::m_nIcon](#m_nicon)|Indeks obrazu, w ramach wyświetlany obok zadanie na liście obrazów.|  
|[CMFCTasksPaneTask::m_nWindowHeight](#m_nwindowheight)|Wysokość okna zadań. Jeśli zadanie nie ma żadnego okna zadań, ta wartość wynosi zero.|  
|[CMFCTasksPaneTask::m_pGroup](#m_pgroup)|Wskaźnik do `CMFCTasksPaneTaskGroup` , której należy to zadanie.|  
|[CMFCTasksPaneTask::m_rect](#m_rect)|Określa prostokąt otaczający zadania.|  
|[CMFCTasksPaneTask::m_strName](#m_strname)|Nazwa zadania.|  
|[CMFCTasksPaneTask::m_uiCommandID](#m_uicommandid)|Określa identyfikator polecenia polecenia, które wykonuje szablon, gdy użytkownik kliknie zadania. Jeśli ta wartość nie jest Identyfikatorem prawidłowe polecenie, zadanie jest traktowany jako etykieta proste.|  
  
## <a name="remarks"></a>Uwagi  
 Na poniższej ilustracji przedstawiono grupy zadań, która zawiera trzy zadania:  
  
 ![Grupy zadań, rozwinięte](../../mfc/reference/media/nexttaskgrpexpand.png "nexttaskgrpexpand")  
  
> [!NOTE]
>  Jeśli zadanie nie ma Identyfikatora prawidłowe polecenie, jest ona traktowana jako etykieta proste.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCTasksPaneTask](../../mfc/reference/cmfctaskspanetask-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxTasksPane.h  
  
##  <a name="cmfctaskspanetask"></a>  CMFCTasksPaneTask::CMFCTasksPaneTask  
 Tworzy i inicjuje `CMFCTasksPaneTask` obiektu.  
  
```  
CMFCTasksPaneTask(
    CMFCTasksPaneTaskGroup* pGroup,  
    LPCTSTR lpszName,  
    int nIcon,  
    UINT uiCommandID,  
    DWORD dwUserData = 0,  
    HWND hwndTask = NULL,  
    BOOL bAutoDestroyWindow = FALSE,  
    int nWindowHeight = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *pGroup*  
 Określa [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md) do którego należy zadanie.  
  
 *lpszName*  
 Określa nazwę zadania.  
  
 *nIcon*  
 Określa indeks obrazu tego zadania na liście obrazów.  
  
 *uiCommandID*  
 Określa identyfikator polecenia polecenia, który jest wykonywany po kliknięciu zadania.  
  
 *dwUserData*  
 Dane zdefiniowane przez użytkownika.  
  
 *hwndTask*  
 Określa dojścia do okna zadań.  
  
 *bAutoDestroyWindow*  
 W przypadku opcji TRUE okno zadań będzie automatycznie zniszczone.  
  
 *nWindowHeight*  
 Określa wysokość okna zadań.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_bautodestroywindow"></a>  CMFCTasksPaneTask::m_bAutoDestroyWindow  
 Określa, czy okno zadań automatycznie zostanie zniszczony.  
  
```  
BOOL m_bAutoDestroyWindow;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ustaw wartość true, aby określić, że okno zadań ( [CMFCTasksPaneTask::m_hwndTask](#m_hwndtask)) należy zniszczyć automatycznie; w przeciwnym razie wartość FALSE.  
  
##  <a name="m_bisbold"></a>  CMFCTasksPaneTask::m_bIsBold  
 Określa, czy etykieta zadania jest rysowana pogrubioną czcionką.  
  
```  
BOOL m_bIsBold;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ustaw ten element na wartość true, ekran pogrubioną tekst etykiety zadań.  
  
##  <a name="m_dwuserdata"></a>  CMFCTasksPaneTask::m_dwUserData  
 Zawiera dane zdefiniowanych przez użytkownika, który jest skojarzony z zadaniem. Jeśli żadne dane nie są skojarzone z zadaniem, należy ustawić na zero.  
  
```  
DWORD m_dwUserData;  
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_hwndtask"></a>  CMFCTasksPaneTask::m_hwndTask  
 Dojście do okna zadań.  
  
```  
HWND m_hwndTask;  
```  
  
### <a name="remarks"></a>Uwagi  
 Aby dodać okno zadań, należy wywołać [CMFCTasksPane::AddWindow](../../mfc/reference/cmfctaskspane-class.md#addwindow).  
  
##  <a name="m_nicon"></a>  CMFCTasksPaneTask::m_nIcon  
 Pozycja indeksu w listy obrazów, który identyfikuje obraz, który jest wyświetlany obok określonego zadania.  
  
```  
int m_nIcon;  
```  
  
### <a name="remarks"></a>Uwagi  
 Lista obrazów jest ustawiana przez [CMFCTasksPane::SetIconsList](../../mfc/reference/cmfctaskspane-class.md#seticonslist).  
  
 Ustaw `m_nIcon` na -1, jeśli chcesz wyświetlić zadania bez obrazu.  
  
##  <a name="m_nwindowheight"></a>  CMFCTasksPaneTask::m_nWindowHeight  
 Wysokość okna zadań. Jeśli zadanie nie ma żadnego okna zadań, ta wartość wynosi zero.  
  
```  
int m_nWindowHeight;  
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_pgroup"></a>  CMFCTasksPaneTask::m_pGroup  
 Wskaźnik do [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md) do którego należy to zadanie.  
  
```  
CMFCTasksPaneTaskGroup* m_pGroup;  
```  
  
### <a name="remarks"></a>Uwagi  
 Każde zadanie musi mieć grupę nadrzędną. Dodaj grupy do okienka zadań, wywołując [CMFCTasksPane::AddGroup](../../mfc/reference/cmfctaskspane-class.md#addgroup).  
  
##  <a name="m_rect"></a>  CMFCTasksPaneTask::m_rect  
 Określa prostokąt otaczający zadania.  
  
```  
CRect m_rect;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta wartość jest obliczana przez platformę, gdy zadanie jest rysowana.  
  
##  <a name="m_strname"></a>  CMFCTasksPaneTask::m_strName  
 Nazwa zadania.  
  
```  
CString m_strName;  
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_uicommandid"></a>  CMFCTasksPaneTask::m_uiCommandID  
 Określa identyfikator polecenia polecenia, który jest wykonywany, gdy użytkownik kliknie zadania. Jeśli ta wartość nie jest Identyfikatorem prawidłowe polecenie, zadanie jest traktowany jako etykieta proste.  
  
```  
UINT m_uiCommandID;  
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setaccdata"></a>  CMFCTasksPaneTask::SetACCData  
 Określa dane ułatwień dostępu dla bieżącego zadania.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pParent*  
 Reprezentuje okna nadrzędnego bieżącego zadania.  
  
 [out] *danych*  
 Obiekt typu `CAccessibilityData` , jest wypełniana danymi ułatwień dostępu do bieżącego zadania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli *danych* parametr został pomyślnie wypełnione danymi ułatwień dostępu do bieżącego zadania; w przeciwnym razie FALSE.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CObject](../../mfc/reference/cobject-class.md)
