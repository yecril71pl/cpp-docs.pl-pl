---
title: Klasa CMFCShellListCtrl
ms.date: 11/04/2016
f1_keywords:
- CMFCShellListCtrl
- AFXSHELLLISTCTRL/CMFCShellListCtrl
- AFXSHELLLISTCTRL/CMFCShellListCtrl::DisplayFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::DisplayParentFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::EnableShellContextMenu
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentFolderName
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentItemIdList
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentShellFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetItemPath
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetItemTypes
- AFXSHELLLISTCTRL/CMFCShellListCtrl::IsDesktop
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnCompareItems
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnFormatFileDate
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnFormatFileSize
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnGetItemIcon
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnGetItemText
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnSetColumns
- AFXSHELLLISTCTRL/CMFCShellListCtrl::Refresh
- AFXSHELLLISTCTRL/CMFCShellListCtrl::SetItemTypes
helpviewer_keywords:
- CMFCShellListCtrl [MFC], DisplayFolder
- CMFCShellListCtrl [MFC], DisplayParentFolder
- CMFCShellListCtrl [MFC], EnableShellContextMenu
- CMFCShellListCtrl [MFC], GetCurrentFolder
- CMFCShellListCtrl [MFC], GetCurrentFolderName
- CMFCShellListCtrl [MFC], GetCurrentItemIdList
- CMFCShellListCtrl [MFC], GetCurrentShellFolder
- CMFCShellListCtrl [MFC], GetItemPath
- CMFCShellListCtrl [MFC], GetItemTypes
- CMFCShellListCtrl [MFC], IsDesktop
- CMFCShellListCtrl [MFC], OnCompareItems
- CMFCShellListCtrl [MFC], OnFormatFileDate
- CMFCShellListCtrl [MFC], OnFormatFileSize
- CMFCShellListCtrl [MFC], OnGetItemIcon
- CMFCShellListCtrl [MFC], OnGetItemText
- CMFCShellListCtrl [MFC], OnSetColumns
- CMFCShellListCtrl [MFC], Refresh
- CMFCShellListCtrl [MFC], SetItemTypes
ms.assetid: ad472958-5586-4c50-aadf-1844c30bf6e7
ms.openlocfilehash: 02d4883c6b5445515d891c5e76ccf10b6bb35bba
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504920"
---
# <a name="cmfcshelllistctrl-class"></a>Klasa CMFCShellListCtrl

`CMFCShellListCtrl` Klasa udostępnia funkcje kontrolki listy systemu Windows i rozszerza ją przez uwzględnienie możliwości wyświetlania listy elementów powłoki.

## <a name="syntax"></a>Składnia

```
class CMFCShellListCtrl : public CMFCListCtrl
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCShellListCtrl::DisplayFolder](#displayfolder)|Wyświetla listę elementów, które są zawarte w podanym folderze.|
|[CMFCShellListCtrl::D isplayParentFolder](#displayparentfolder)|Wyświetla listę elementów znajdujących się w folderze, który jest elementem nadrzędnym aktualnie wyświetlanego folderu.|
|[CMFCShellListCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Włącza lub wyłącza menu skrótów.|
|[CMFCShellListCtrl::GetCurrentFolder](#getcurrentfolder)|Pobiera ścieżkę do bieżącego folderu.|
|[CMFCShellListCtrl::GetCurrentFolderName](#getcurrentfoldername)|Pobiera nazwę bieżącego folderu.|
|[CMFCShellListCtrl::GetCurrentItemIdList](#getcurrentitemidlist)|Zwraca PIDL bieżącego elementu formantu listy.|
|[CMFCShellListCtrl::GetCurrentShellFolder](#getcurrentshellfolder)|Zwraca wskaźnik do bieżącego folderu powłoki.|
|[CMFCShellListCtrl::GetItemPath](#getitempath)|Zwraca ścieżkę tekstową elementu.|
|[CMFCShellListCtrl::GetItemTypes](#getitemtypes)|Zwraca typy elementów powłoki, które są wyświetlane przez formant listy.|
|[CMFCShellListCtrl:: isdesktop](#isdesktop)|Sprawdza, czy aktualnie wybrany folder jest folderem pulpitu.|
|[CMFCShellListCtrl::OnCompareItems](#oncompareitems)|Struktura wywołuje tę metodę, gdy porównuje dwa elementy. (Przesłania [CMFCListCtrl:: OnCompareItems](../../mfc/reference/cmfclistctrl-class.md#oncompareitems).)|
|[CMFCShellListCtrl::OnFormatFileDate](#onformatfiledate)|Wywołuje się, gdy struktura pobiera datę pliku wyświetlanego przez kontrolkę listy.|
|[CMFCShellListCtrl::OnFormatFileSize](#onformatfilesize)|Wywołuje się, gdy struktura konwertuje rozmiar pliku kontrolki listy.|
|[CMFCShellListCtrl::OnGetItemIcon](#ongetitemicon)|Wywołuje się, gdy struktura Pobiera ikonę elementu kontrolki listy.|
|[CMFCShellListCtrl::OnGetItemText](#ongetitemtext)|Wywołuje się, gdy struktura konwertuje tekst elementu kontrolki listy.|
|[CMFCShellListCtrl::OnSetColumns](#onsetcolumns)|Wywoływane przez platformę, gdy ustawia nazwy kolumn.|
|[CMFCShellListCtrl:: Refresh](#refresh)|Odświeża i ponownie maluje formant listy.|
|[CMFCShellListCtrl::SetItemTypes](#setitemtypes)|Ustawia typ elementów wyświetlanych przez formant listy.|

## <a name="remarks"></a>Uwagi

Klasa rozszerza funkcjonalność [klasy CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md) , umożliwiając programowi Wyświetlanie listy elementów powłoki systemu Windows. `CMFCShellListCtrl` Używany format wyświetlania przypomina widok listy dla okna Eksploratora.

Obiekt [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) można skojarzyć z `CMFCShellListCtrl` obiektem w celu utworzenia kompletnego okna Eksploratora. Po `CMFCShellTreeCtrl` wybraniu elementu w `CMFCShellListCtrl` obiekcie zostanie wystawiona zawartość wybranego elementu.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak utworzyć obiekt `CMFCShellListCtrl` klasy i jak wyświetlić folder nadrzędny aktualnie wyświetlanego folderu. Ten fragment kodu jest częścią [przykładu Eksploratora](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#1](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#2](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_2.cpp)]
[!code-cpp[NVC_MFC_Explorer#3](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_3.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

`CMFCShellListCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxshelllistCtrl. h

##  <a name="displayfolder"></a>CMFCShellListCtrl::D isplayFolder

Wyświetla listę elementów, które znajdują się w podanym folderze.

```
virtual HRESULT DisplayFolder(LPCTSTR lpszPath);
virtual HRESULT DisplayFolder(LPAFX_SHELLITEMINFO lpItemInfo);
```

### <a name="parameters"></a>Parametry

*lpszPath*<br/>
podczas Ciąg, który zawiera ścieżkę do folderu.

*lpItemInfo*<br/>
podczas Wskaźnik do `LPAFX_SHELLITEMINFO` struktury opisującej folder do wyświetlenia.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; W przeciwnym razie.

##  <a name="displayparentfolder"></a>CMFCShellListCtrl::D isplayParentFolder

Aktualizuje obiekt [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) , aby wyświetlić folder nadrzędny aktualnie wyświetlanego folderu.

```
virtual HRESULT DisplayParentFolder();
```

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; W przeciwnym razie.

##  <a name="enableshellcontextmenu"></a>CMFCShellListCtrl::EnableShellContextMenu

Włącza menu skrótów.

```
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
podczas Wartość logiczna określająca, czy struktura włącza menu skrótów.

##  <a name="getcurrentfolder"></a>CMFCShellListCtrl::GetCurrentFolder

Pobiera ścieżkę aktualnie wybranego folderu w obiekcie [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
BOOL GetCurrentFolder(CString& strPath) const;
```

### <a name="parameters"></a>Parametry

*strPath*<br/>
określoną Odwołanie do parametru ciągu, w którym Metoda zapisuje ścieżkę.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; 0 w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Ta metoda kończy się niepowodzeniem, `CMFCShellListCtrl`Jeśli nie wybrano folderu.

##  <a name="getcurrentfoldername"></a>CMFCShellListCtrl::GetCurrentFolderName

Pobiera nazwę aktualnie wybranego folderu w obiekcie [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
BOOL GetCurrentFolderName(CString& strName) const;
```

### <a name="parameters"></a>Parametry

*strName*<br/>
określoną Odwołanie do parametru ciągu, w którym Metoda zapisuje nazwę.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; 0 w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Ta metoda kończy się niepowodzeniem, `CMFCShellListCtrl`Jeśli nie wybrano folderu.

##  <a name="getcurrentitemidlist"></a>CMFCShellListCtrl::GetCurrentItemIdList

Zwraca PIDL aktualnie wybranego elementu.

```
LPITEMIDLIST GetCurrentItemIdList() const;
```

### <a name="return-value"></a>Wartość zwracana

PIDL bieżącego elementu.

##  <a name="getcurrentshellfolder"></a>CMFCShellListCtrl::GetCurrentShellFolder

Pobiera wskaźnik do aktualnie wybranego elementu w obiekcie [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
const IShellFolder* GetCurrentShellFolder() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [interfejsu IShellFolder](/windows/win32/api/shobjidl_core/nn-shobjidl_core-ishellfolder) dla wybranego obiektu.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wartość NULL, jeśli żaden obiekt nie jest aktualnie wybrany.

##  <a name="getitempath"></a>CMFCShellListCtrl::GetItemPath

Pobiera ścieżkę dla elementu.

```
BOOL GetItemPath(
    CString& strPath,
    int iItem) const;
```

### <a name="parameters"></a>Parametry

*strPath*<br/>
określoną Odwołanie do ciągu, który odbiera ścieżkę.

*iItem*<br/>
podczas Indeks elementu listy.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli powodzenie; W przeciwnym razie zwraca wartość FALSE.

### <a name="remarks"></a>Uwagi

Indeks dostarczony przez *iItem* jest oparty na elementach aktualnie wyświetlanych przez obiekt [klasy CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

##  <a name="getitemtypes"></a>CMFCShellListCtrl::GetItemTypes

Zwraca typ elementów wyświetlanych przez obiekt [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
SHCONTF GetItemTypes() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość [SHCONTF](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf) , która zawiera typ elementów wymienionych w `CMFCShellListCtrl`.

### <a name="remarks"></a>Uwagi

Aby ustawić typ elementów wymienionych w `CMFCShellListCtrl`, wywołaj [CMFCShellListCtrl:: SetItemTypes](#setitemtypes).

##  <a name="isdesktop"></a>CMFCShellListCtrl:: isdesktop

Określa, czy folder, który jest wyświetlany w obiekcie [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) jest folderem pulpitu.

```
BOOL IsDesktop() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli wyświetlany folder jest folderem pulpitu; W przeciwnym razie zwraca wartość FALSE.

##  <a name="oncompareitems"></a>CMFCShellListCtrl::OnCompareItems

Aby uzyskać więcej szczegółów, zobacz kod źródłowy znajdujący się w folderze **VC\\atlmfc\\src\\MFC** instalacji programu Visual Studio.

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>Parametry

podczas *lParam1*<br/>
podczas *lParam2*<br/>
podczas *IColumn*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="onformatfiledate"></a>CMFCShellListCtrl::OnFormatFileDate

Struktura wywołuje tę metodę, gdy musi skonwertować datę skojarzoną z obiekt na ciąg.

```
virtual void OnFormatFileDate(
    const CTime& tmFile,
    CString& str);
```

### <a name="parameters"></a>Parametry

*tmFile*<br/>
podczas Data skojarzona z plikiem.

*str*<br/>
określoną Ciąg zawierający datę sformatowanego pliku.

### <a name="remarks"></a>Uwagi

Gdy obiekt [klasy CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) wyświetla datę skojarzoną z plikiem, musi przekonwertować tę datę na format ciągu. `CMFCShellListCtrl` Używa tej metody do dokonania konwersji. Domyślnie ta metoda używa bieżących ustawień regionalnych do formatowania daty w ciągu.

##  <a name="onformatfilesize"></a>CMFCShellListCtrl::OnFormatFileSize

Struktura wywołuje tę metodę, gdy konwertuje rozmiar obiektu na ciąg.

```
virtual void OnFormatFileSize(
    long lFileSize,
    CString& str);
```

### <a name="parameters"></a>Parametry

*lFileSize*<br/>
podczas Rozmiar pliku, który będzie wyświetlany w strukturze.

*str*<br/>
określoną Ciąg, który zawiera sformatowany rozmiar pliku.

### <a name="remarks"></a>Uwagi

Gdy obiekt [klasy CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) musi wyświetlić rozmiar pliku, musi przekonwertować rozmiar pliku na format ciągu. `CMFCShellListCtrl` Używa tej metody do dokonania konwersji. Domyślnie ta metoda konwertuje rozmiar pliku z bajtów na kilobajty, a następnie używa bieżących ustawień regionalnych do formatowania rozmiaru w postaci ciągu.

##  <a name="ongetitemicon"></a>CMFCShellListCtrl::OnGetItemIcon

Struktura wywołuje tę metodę, aby pobrać ikonę skojarzoną z elementem listy powłoki.

```
virtual int OnGetItemIcon(
    int iItem,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Parametry

*iItem*<br/>
podczas Indeks elementu.

*pItem*<br/>
podczas Parametr LPAFX_SHELLITEMINFO, który opisuje element.

### <a name="return-value"></a>Wartość zwracana

Indeks obrazu ikony, jeśli się powiedzie; -1, jeśli funkcja się nie powiedzie.

### <a name="remarks"></a>Uwagi

Indeks obrazu ikony jest oparty na liście obrazów systemowych.

Domyślnie ta metoda polega na parametrze *pItem* . Wartość *iItem* nie jest używana w implementacji domyślnej. Możesz użyć *iItem* , aby zaimplementować zachowanie niestandardowe.

##  <a name="ongetitemtext"></a>CMFCShellListCtrl::OnGetItemText

Struktura wywołuje tę metodę, gdy musi pobrać tekst elementu powłoki.

```
virtual CString OnGetItemText(
    int iItem,
    int iColumn,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Parametry

*iItem*<br/>
podczas Indeks elementu.

*iColumn*<br/>
podczas Kolumna zainteresowania.

*pItem*<br/>
podczas Parametr LPAFX_SHELLITEMINFO, który opisuje element.

### <a name="return-value"></a>Wartość zwracana

A `CString` , który zawiera tekst skojarzony z elementem.

### <a name="remarks"></a>Uwagi

Każdy element w `CMFCShellListCtrl` obiekcie może mieć tekst w co najmniej jednej kolumnie. Gdy struktura wywołuje tę metodę, określa kolumnę, którą interesują. W przypadku ręcznego wywołania tej funkcji należy również określić kolumnę, która Cię interesuje.

Domyślnie ta metoda polega na parametrze *pItem* w celu określenia, który element należy przetworzyć. Wartość *iItem* nie jest używana w implementacji domyślnej.

##  <a name="onsetcolumns"></a>CMFCShellListCtrl::OnSetColumns

Struktura wywołuje tę metodę, gdy ustawia nazwy kolumn.

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>Uwagi

Domyślnie struktura tworzy cztery kolumny w `CMFCShellListCtrl` obiekcie. Nazwy tych kolumn to **Nazwa**, **rozmiar**, **Typ**i **zmodyfikowano**. Można zastąpić tę metodę, aby dostosować liczbę kolumn i ich nazw.

##  <a name="refresh"></a>CMFCShellListCtrl:: Refresh

Odświeża i odmaluje obiekt [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
virtual HRESULT Refresh();
```

### <a name="return-value"></a>Wartość zwracana

`S_OK`Jeśli powodzenie; w przeciwnym razie wartość błędu.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby odświeżyć listę elementów wyświetlanych `CMFCShellListCtrl` przez obiekt.

##  <a name="setitemtypes"></a>CMFCShellListCtrl::SetItemTypes

Ustawia typ elementów, które są wymienione w obiekcie [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
void SetItemTypes(SHCONTF nTypes);
```

### <a name="parameters"></a>Parametry

*nTypes*<br/>
podczas Lista typów elementów obsługiwanych przez `CMFCShellListCtrl` obiekt.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat listy typów elementów, zobacz [SHCONTF](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf).

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)<br/>
[Klasa CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)
