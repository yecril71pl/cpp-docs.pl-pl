---
title: Klasa CMFCTasksPaneTask
ms.date: 11/19/2018
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
ms.openlocfilehash: 49fccdf161da7deb1fd88a12a107df40bafdae92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375865"
---
# <a name="cmfctaskspanetask-class"></a>Klasa CMFCTasksPaneTask

Klasa `CMFCTasksPaneTask` jest klasą pomocniczą reprezentującą zadania dla formantu okienka zadań ( [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)). Obiekt zadania reprezentuje element w grupie zadań ( [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)). Każde zadanie może mieć polecenie, które wykonuje framework, gdy użytkownik kliknie zadanie i ikonę, która pojawia się po lewej stronie nazwy zadania.

## <a name="syntax"></a>Składnia

```
class CMFCTasksPaneTask : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCTasksPaneTask::CMFCTasksPaneTask](#cmfctaskspanetask)|Tworzy i inicjuje `CMFCTasksPaneTask` obiekt.|
|`CMFCTasksPaneTask::~CMFCTasksPaneTask`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCTasksPaneTask::SetACCData](#setaccdata)|Określa dane ułatwień dostępu dla bieżącego zadania.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMFCTasksPaneTask::m_bAutoDestroyWindow](#m_bautodestroywindow)|Określa, czy okno zadania jest automatycznie niszczone.|
|[CMFCTasksPaneTask::m_bIsBold](#m_bisbold)|Określa, czy struktura rysuje etykietę zadania pogrubioną czcionką.|
|[CMFCTasksPaneTask::m_dwUserData](#m_dwuserdata)|Zawiera dane zdefiniowane przez użytkownika, które struktura kojarzy z zadaniem. Ustaw wartość zero, jeśli zadanie nie ma skojarzonych danych.|
|[CMFCTasksPaneTask::m_hwndTask](#m_hwndtask)|Dojście do okna zadania.|
|[CMFCTasksPaneTask::m_nIcon](#m_nicon)|Indeks na liście obrazów, które struktura wyświetla obok zadania.|
|[CMFCTasksPaneTask::m_nWindowHeight](#m_nwindowheight)|Wysokość okna zadania. Jeśli zadanie nie ma okna zadania, ta wartość wynosi zero.|
|[CMFCTasksPaneTask::m_pGroup](#m_pgroup)|Wskaźnik do `CMFCTasksPaneTaskGroup` tego zadania należy.|
|[CMFCTasksPaneTask::m_rect](#m_rect)|Określa prostokąt obwiedniowy zadania.|
|[CMFCTasksPaneTask::m_strName](#m_strname)|Nazwa zadania.|
|[CMFCTasksPaneTask::m_uiCommandID](#m_uicommandid)|Określa identyfikator polecenia polecenia, które wykonuje framework, gdy użytkownik kliknie zadanie. Jeśli ta wartość nie jest prawidłowym identyfikatorem polecenia, zadanie jest traktowane jako etykieta prosta.|

## <a name="remarks"></a>Uwagi

Na poniższej ilustracji przedstawiono grupę zadań zawierającą trzy zadania:

![Grupa zadań, rozwinięta](../../mfc/reference/media/nexttaskgrpexpand.png "Grupa zadań, rozwinięta")

> [!NOTE]
> Jeśli zadanie nie ma prawidłowego identyfikatora polecenia, jest traktowane jako etykieta prosta.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCTasksPaneTask](../../mfc/reference/cmfctaskspanetask-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxTasksPane.h

## <a name="cmfctaskspanetaskcmfctaskspanetask"></a><a name="cmfctaskspanetask"></a>CMFCTasksPaneTask::CMFCTasksPaneTask

Tworzy i inicjuje `CMFCTasksPaneTask` obiekt.

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

*pGrupa*<br/>
Określa [CMFCTasksPaneTaskGroup,](../../mfc/reference/cmfctaskspanetaskgroup-class.md) do której należy zadanie.

*Lpszname*<br/>
Określa nazwę zadania.

*nIcon (własówce)*<br/>
Określa indeks obrazu zadania na liście obrazów.

*identyfikator uiCommandID*<br/>
Określa identyfikator polecenia polecenia wykonywanego po kliknięciu zadania.

*dwUserData*<br/>
Dane zdefiniowane przez użytkownika.

*hwndTask*<br/>
Określa dojście do okna zadania.

*bAutoDestroyWindow*<br/>
Jeśli true, okno zadania zostanie zniszczone automatycznie.

*nWindowHeight (Jeśli Niem.*<br/>
Określa wysokość okna zadania.

### <a name="remarks"></a>Uwagi

## <a name="cmfctaskspanetaskm_bautodestroywindow"></a><a name="m_bautodestroywindow"></a>CMFCTasksPaneTask::m_bAutoDestroyWindow

Określa, czy okno zadania jest automatycznie niszczone.

```
BOOL m_bAutoDestroyWindow;
```

### <a name="remarks"></a>Uwagi

Ustaw wartość TRUE, aby określić, że okno zadania ( [CMFCTasksPaneTask::m_hwndTask](#m_hwndtask)) powinno zostać automatycznie zniszczone; w przeciwnym razie FALSE.

## <a name="cmfctaskspanetaskm_bisbold"></a><a name="m_bisbold"></a>CMFCTasksPaneTask::m_bIsBold

Określa, czy etykieta zadania jest rysowana pogrubioną czcionką.

```
BOOL m_bIsBold;
```

### <a name="remarks"></a>Uwagi

Ustaw ten element członkowski na WARTOŚĆ PRAWDA, aby wyświetlić pogrubiony tekst etykiety zadania.

## <a name="cmfctaskspanetaskm_dwuserdata"></a><a name="m_dwuserdata"></a>CMFCTasksPaneTask::m_dwUserData

Zawiera dane zdefiniowane przez użytkownika, które są skojarzone z zadaniem. Ustaw wartość zero, jeśli z zadaniem nie są skojarzone żadne dane.

```
DWORD m_dwUserData;
```

### <a name="remarks"></a>Uwagi

## <a name="cmfctaskspanetaskm_hwndtask"></a><a name="m_hwndtask"></a>CMFCTasksPaneTask::m_hwndTask

Dojście do okna zadania.

```
HWND m_hwndTask;
```

### <a name="remarks"></a>Uwagi

Aby dodać okno zadania, zadzwoń do [CMFCTasksPane::AddWindow](../../mfc/reference/cmfctaskspane-class.md#addwindow).

## <a name="cmfctaskspanetaskm_nicon"></a><a name="m_nicon"></a>CMFCTasksPaneTask::m_nIcon

Pozycja indeksu na liście obrazów identyfikującej obraz wyświetlany obok określonego zadania.

```
int m_nIcon;
```

### <a name="remarks"></a>Uwagi

Lista obrazów jest ustawiana przez [CMFCTasksPane::SetIconsList](../../mfc/reference/cmfctaskspane-class.md#seticonslist).

Ustaw `m_nIcon` wartość -1, jeśli chcesz wyświetlić zadanie bez obrazu.

## <a name="cmfctaskspanetaskm_nwindowheight"></a><a name="m_nwindowheight"></a>CMFCTasksPaneTask::m_nWindowHeight

Wysokość okna zadania. Jeśli zadanie nie ma okna zadania, ta wartość wynosi zero.

```
int m_nWindowHeight;
```

### <a name="remarks"></a>Uwagi

## <a name="cmfctaskspanetaskm_pgroup"></a><a name="m_pgroup"></a>CMFCTasksPaneTask::m_pGroup

Wskaźnik do [CMFCTasksPaneTaskGroup,](../../mfc/reference/cmfctaskspanetaskgroup-class.md) do którego należy to zadanie.

```
CMFCTasksPaneTaskGroup* m_pGroup;
```

### <a name="remarks"></a>Uwagi

Każde zadanie musi mieć grupę nadrzędną. Grupy są dodawanye do okienka zadań przez wywołanie [polecenia CMFCTasksPane::AddGroup](../../mfc/reference/cmfctaskspane-class.md#addgroup).

## <a name="cmfctaskspanetaskm_rect"></a><a name="m_rect"></a>CMFCTasksPaneTask::m_rect

Określa prostokąt obwiedniowy zadania.

```
CRect m_rect;
```

### <a name="remarks"></a>Uwagi

Ta wartość jest obliczana przez platformę podczas rysowania zadania.

## <a name="cmfctaskspanetaskm_strname"></a><a name="m_strname"></a>CMFCTasksPaneTask::m_strName

Nazwa zadania.

```
CString m_strName;
```

### <a name="remarks"></a>Uwagi

## <a name="cmfctaskspanetaskm_uicommandid"></a><a name="m_uicommandid"></a>CMFCTasksPaneTask::m_uiCommandID

Określa identyfikator polecenia polecenia wykonywanego po kliknięciu zadania przez użytkownika. Jeśli ta wartość nie jest prawidłowym identyfikatorem polecenia, zadanie jest traktowane jako etykieta prosta.

```
UINT m_uiCommandID;
```

### <a name="remarks"></a>Uwagi

## <a name="cmfctaskspanetasksetaccdata"></a><a name="setaccdata"></a>CMFCTasksPaneTask::SetACCData

Określa dane ułatwień dostępu dla bieżącego zadania.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parametry

*pRoczysz*<br/>
[w] Reprezentuje okno nadrzędne bieżącego zadania.

*Danych*<br/>
[na zewnątrz] Obiekt typu, `CAccessibilityData` który jest wypełniany danymi dostępności bieżącego zadania.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli parametr *danych* został pomyślnie wypełniony danymi dostępności bieżącego zadania; w przeciwnym razie FALSE.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)
