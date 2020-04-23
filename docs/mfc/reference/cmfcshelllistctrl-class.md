---
title: KLASA CMFCShellListCtrl
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
ms.openlocfilehash: 445556535217b0887a02227a0773c287911922a2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753485"
---
# <a name="cmfcshelllistctrl-class"></a>KLASA CMFCShellListCtrl

Klasa `CMFCShellListCtrl` zapewnia funkcję kontroli listy systemu Windows i rozszerza ją, dołączając możliwość wyświetlania listy elementów powłoki.

## <a name="syntax"></a>Składnia

```
class CMFCShellListCtrl : public CMFCListCtrl
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCShellListCtrl::DisplayFolder](#displayfolder)|Wyświetla listę elementów, które znajdują się w podanym folderze.|
|[CMFCShellListCtrl::DisplayParentFolder](#displayparentfolder)|Wyświetla listę elementów zawartych w folderze, który jest elementem nadrzędnym aktualnie wyświetlanego folderu.|
|[CMFCShellListCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Włącza lub wyłącza menu skrótów.|
|[CMFCShellListCtrl::GetCurrentFolder](#getcurrentfolder)|Pobiera ścieżkę bieżącego folderu.|
|[CMFCShellListCtrl::GetCurrentFolderName](#getcurrentfoldername)|Pobiera nazwę bieżącego folderu.|
|[CMFCShellListCtrl::GetCurrentItemIdList](#getcurrentitemidlist)|Zwraca numer PIDL bieżącego elementu kontrolnego listy.|
|[CMFCShellListCtrl::GetCurrentShellFolder](#getcurrentshellfolder)|Zwraca wskaźnik do bieżącego folderu Powłoki.|
|[CMFCShellListCtrl::GetItemPath](#getitempath)|Zwraca ścieżkę tekstową elementu.|
|[CMFCShellListCtrl::GetItemTypes](#getitemtypes)|Zwraca typy elementów powłoki, które są wyświetlane przez kontrolka listy.|
|[CMFCShellListCtrl::IsDesktop](#isdesktop)|Sprawdza, czy aktualnie wybrany folder jest folderem pulpitu.|
|[CMFCShellListCtrl::OnCompareItems](#oncompareitems)|Struktura wywołuje tę metodę, gdy porównuje dwa elementy. (Zastępuje [CMFCListCtrl::OnCompareItems](../../mfc/reference/cmfclistctrl-class.md#oncompareitems).)|
|[CMFCShellListCtrl::OnFormatFileDate](#onformatfiledate)|Wywoływana, gdy struktura pobiera datę pliku wyświetlaną przez formant listy.|
|[CMFCShellListCtrl::OnFormatFileSize](#onformatfilesize)|Wywoływana, gdy struktura konwertuje rozmiar pliku formantu listy.|
|[CMFCShellListCtrl::OnGetItemicon](#ongetitemicon)|Wywoływana, gdy struktura pobiera ikonę elementu kontroli listy.|
|[CMFCShellListCtrl::OnGetItemText](#ongetitemtext)|Wywoływane, gdy struktura konwertuje tekst elementu kontroli listy.|
|[CMFCShellListCtrl::OnSetColumns](#onsetcolumns)|Wywoływana przez platformę, gdy ustawia nazwy kolumn.|
|[CMFCShellListCtrl::Odśwież](#refresh)|Odświeża i odświeża kontrolki listy.|
|[CMFCShellListCtrl::SetItemTypes](#setitemtypes)|Ustawia typ elementów wyświetlanych przez kontrolka listy.|

## <a name="remarks"></a>Uwagi

Klasa `CMFCShellListCtrl` rozszerza funkcjonalność [CMFCListCtrl Klasy,](../../mfc/reference/cmfclistctrl-class.md) umożliwiając programowi listę elementów powłoki systemu Windows. Używany format wyświetlania jest podobny do formatu widoku listy dla okna Eksploratora.

Obiekt [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) może być skojarzony z obiektem w `CMFCShellListCtrl` celu utworzenia pełnego okna Eksploratora. Następnie wybranie elementu w `CMFCShellTreeCtrl` obiekcie `CMFCShellListCtrl` spowoduje, że obiekt wyświetli listę zawartości zaznaczonego elementu.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCShellListCtrl` utworzyć obiekt klasy i jak wyświetlić folder nadrzędny aktualnie wyświetlanego folderu. Ten fragment kodu jest częścią [przykładu Eksploratora](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#1](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#2](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_2.cpp)]
[!code-cpp[NVC_MFC_Explorer#3](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_3.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Clistctrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

`CMFCShellListCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxshelllistCtrl.h

## <a name="cmfcshelllistctrldisplayfolder"></a><a name="displayfolder"></a>CMFCShellListCtrl::DisplayFolder

Wyświetla listę elementów, które znajdują się w podanym folderze.

```
virtual HRESULT DisplayFolder(LPCTSTR lpszPath);
virtual HRESULT DisplayFolder(LPAFX_SHELLITEMINFO lpItemInfo);
```

### <a name="parameters"></a>Parametry

*lpszPath (lpszPath)*<br/>
[w] Ciąg zawierający ścieżkę folderu.

*lpItemInfo*<br/>
[w] Wskaźnik do `LPAFX_SHELLITEMINFO` struktury opisującej folder do wyświetlenia.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; E_FAIL inaczej.

## <a name="cmfcshelllistctrldisplayparentfolder"></a><a name="displayparentfolder"></a>CMFCShellListCtrl::DisplayParentFolder

Aktualizuje obiekt [CMFCShellListCtrl,](../../mfc/reference/cmfcshelllistctrl-class.md) aby wyświetlić folder nadrzędny aktualnie wyświetlanego folderu.

```
virtual HRESULT DisplayParentFolder();
```

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; E_FAIL inaczej.

## <a name="cmfcshelllistctrlenableshellcontextmenu"></a><a name="enableshellcontextmenu"></a>CMFCShellListCtrl::EnableShellContextMenu

Włącza menu skrótów.

```cpp
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
[w] Wartość logiczna określająca, czy struktura włącza menu skrótów.

## <a name="cmfcshelllistctrlgetcurrentfolder"></a><a name="getcurrentfolder"></a>CMFCShellListCtrl::GetCurrentFolder

Pobiera ścieżkę aktualnie wybranego folderu w [obiekcie CMFCShellListCtrl.](../../mfc/reference/cmfcshelllistctrl-class.md)

```
BOOL GetCurrentFolder(CString& strPath) const;
```

### <a name="parameters"></a>Parametry

*strPath (ścieżka strPath)*<br/>
[na zewnątrz] Odwołanie do parametru ciągu, w którym metoda zapisuje ścieżkę.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; 0 w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Ta metoda kończy się niepowodzeniem, `CMFCShellListCtrl`jeśli w pliku .

## <a name="cmfcshelllistctrlgetcurrentfoldername"></a><a name="getcurrentfoldername"></a>CMFCShellListCtrl::GetCurrentFolderName

Pobiera nazwę aktualnie wybranego folderu w obiekcie [CMFCShellListCtrl.](../../mfc/reference/cmfcshelllistctrl-class.md)

```
BOOL GetCurrentFolderName(CString& strName) const;
```

### <a name="parameters"></a>Parametry

*nazwa strName*<br/>
[na zewnątrz] Odwołanie do parametru ciągu, w którym metoda zapisuje nazwę.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; 0 w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Ta metoda kończy się niepowodzeniem, `CMFCShellListCtrl`jeśli w pliku .

## <a name="cmfcshelllistctrlgetcurrentitemidlist"></a><a name="getcurrentitemidlist"></a>CMFCShellListCtrl::GetCurrentItemIdList

Zwraca numer PIDL aktualnie zaznaczonego towaru.

```
LPITEMIDLIST GetCurrentItemIdList() const;
```

### <a name="return-value"></a>Wartość zwracana

Pidl bieżącego elementu.

## <a name="cmfcshelllistctrlgetcurrentshellfolder"></a><a name="getcurrentshellfolder"></a>CMFCShellListCtrl::GetCurrentShellFolder

Pobiera wskaźnik do aktualnie wybranego elementu w [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiektu.

```
const IShellFolder* GetCurrentShellFolder() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [interfejsu IShellFolder](/windows/win32/api/shobjidl_core/nn-shobjidl_core-ishellfolder) dla wybranego obiektu.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wartość NULL, jeśli żaden obiekt nie jest aktualnie zaznaczony.

## <a name="cmfcshelllistctrlgetitempath"></a><a name="getitempath"></a>CMFCShellListCtrl::GetItemPath

Pobiera ścieżkę dla elementu.

```
BOOL GetItemPath(
    CString& strPath,
    int iItem) const;
```

### <a name="parameters"></a>Parametry

*strPath (ścieżka strPath)*<br/>
[na zewnątrz] Odwołanie do ciągu, który odbiera ścieżkę.

*Iitem*<br/>
[w] Indeks elementu listy.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli się powiedzie; FAŁSZ inaczej.

### <a name="remarks"></a>Uwagi

Indeks dostarczany przez *iItem* jest oparty na elementach aktualnie wyświetlanych przez obiekt [KLASY CMFCShellListCtrl.](../../mfc/reference/cmfcshelllistctrl-class.md)

## <a name="cmfcshelllistctrlgetitemtypes"></a><a name="getitemtypes"></a>CMFCShellListCtrl::GetItemTypes

Zwraca typ elementów wyświetlanych przez [obiekt CMFCShellListCtrl.](../../mfc/reference/cmfcshelllistctrl-class.md)

```
SHCONTF GetItemTypes() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość [SHCONTF](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf) zawierająca typ elementów `CMFCShellListCtrl`wymienionych w pliku .

### <a name="remarks"></a>Uwagi

Aby ustawić typ elementów `CMFCShellListCtrl`wymienionych w , wywołać [CMFCShellListCtrl::SetItemTypes](#setitemtypes).

## <a name="cmfcshelllistctrlisdesktop"></a><a name="isdesktop"></a>CMFCShellListCtrl::IsDesktop

Określa, czy folder, który jest wyświetlany w [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiektu jest folder pulpitu.

```
BOOL IsDesktop() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli wyświetlany folder jest folderem pulpitu; FAŁSZ inaczej.

## <a name="cmfcshelllistctrloncompareitems"></a><a name="oncompareitems"></a>CMFCShellListCtrl::OnCompareItems

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>Parametry

[w] *lParam1*<br/>
[w] *lParam2*<br/>
[w] *iColumn ( iColumn )*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcshelllistctrlonformatfiledate"></a><a name="onformatfiledate"></a>CMFCShellListCtrl::OnFormatFileDate

Struktura wywołuje tę metodę, gdy musi przekonwertować datę skojarzoną z obiektem na ciąg.

```
virtual void OnFormatFileDate(
    const CTime& tmFile,
    CString& str);
```

### <a name="parameters"></a>Parametry

*plik tm*<br/>
[w] Data skojarzona z plikiem.

*Str*<br/>
[na zewnątrz] Ciąg zawierający sformatowaną datę pliku.

### <a name="remarks"></a>Uwagi

Gdy obiekt [KLASY CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) wyświetla datę skojarzoną z plikiem, musi przekonwertować tę datę na format ciągu. Używa `CMFCShellListCtrl` tej metody, aby dokonać tej konwersji. Domyślnie ta metoda używa bieżących ustawień regionalnych do formatowania daty w ciąg.

## <a name="cmfcshelllistctrlonformatfilesize"></a><a name="onformatfilesize"></a>CMFCShellListCtrl::OnFormatFileSize

Struktura wywołuje tę metodę, gdy konwertuje rozmiar obiektu na ciąg.

```
virtual void OnFormatFileSize(
    long lFileSize,
    CString& str);
```

### <a name="parameters"></a>Parametry

*lSize pliku*<br/>
[w] Rozmiar pliku, który będzie wyświetlany w ramach.

*Str*<br/>
[na zewnątrz] Ciąg zawierający rozmiar sformatowanego pliku.

### <a name="remarks"></a>Uwagi

Gdy [obiekt klasy CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) musi wyświetlić rozmiar pliku, musi przekonwertować rozmiar pliku na format ciągu. Używa `CMFCShellListCtrl` tej metody, aby dokonać tej konwersji. Domyślnie ta metoda konwertuje rozmiar pliku z bajtów na kilobajty, a następnie używa bieżących ustawień regionalnych do formatowania rozmiaru na ciąg.

## <a name="cmfcshelllistctrlongetitemicon"></a><a name="ongetitemicon"></a>CMFCShellListCtrl::OnGetItemicon

Struktura wywołuje tę metodę, aby pobrać ikonę skojarzoną z elementem listy powłoki.

```
virtual int OnGetItemIcon(
    int iItem,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Parametry

*Iitem*<br/>
[w] Indeks towaru.

*pItem (własówce)*<br/>
[w] Parametr LPAFX_SHELLITEMINFO opisujący element.

### <a name="return-value"></a>Wartość zwracana

Indeks obrazu ikony, jeśli się powiedzie; -1, jeśli funkcja nie powiedzie się.

### <a name="remarks"></a>Uwagi

Indeks obrazu ikony jest oparty na liście obrazów systemowych.

Domyślnie ta metoda opiera się na *pItem* parametru. Wartość *iItem* nie jest używana w domyślnej implementacji. Za pomocą *programu iItem* można zaimplementować zachowanie niestandardowe.

## <a name="cmfcshelllistctrlongetitemtext"></a><a name="ongetitemtext"></a>CMFCShellListCtrl::OnGetItemText

Struktura wywołuje tę metodę, gdy musi pobrać tekst elementu powłoki.

```
virtual CString OnGetItemText(
    int iItem,
    int iColumn,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Parametry

*Iitem*<br/>
[w] Indeks towaru.

*Icolumn*<br/>
[w] Kolumna zainteresowania.

*pItem (własówce)*<br/>
[w] Parametr LPAFX_SHELLITEMINFO opisujący element.

### <a name="return-value"></a>Wartość zwracana

A, `CString` który zawiera tekst skojarzony z elementem.

### <a name="remarks"></a>Uwagi

Każdy element `CMFCShellListCtrl` w obiekcie może mieć tekst w jednej lub więcej kolumn. Gdy struktura wywołuje tę metodę, określa kolumnę, która jest zainteresowana. Jeśli ta funkcja zostanie wywołana ręcznie, należy również określić kolumnę, która Cię interesuje.

Domyślnie ta metoda opiera się na *pItem parametr,* aby określić, który element do przetworzenia. Wartość *iItem* nie jest używana w domyślnej implementacji.

## <a name="cmfcshelllistctrlonsetcolumns"></a><a name="onsetcolumns"></a>CMFCShellListCtrl::OnSetColumns

Struktura wywołuje tę metodę, gdy ustawia nazwy kolumn.

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>Uwagi

Domyślnie struktura tworzy cztery kolumny `CMFCShellListCtrl` w obiekcie. Nazwy tych kolumn to **Nazwa,** **Rozmiar,** **Typ**i **Zmodyfikowane**. Tę metodę można zastąpić, aby dostosować liczbę kolumn i ich nazwy.

## <a name="cmfcshelllistctrlrefresh"></a><a name="refresh"></a>CMFCShellListCtrl::Odśwież

Odświeża i odświeża [obiekt CMFCShellListCtrl.](../../mfc/reference/cmfcshelllistctrl-class.md)

```
virtual HRESULT Refresh();
```

### <a name="return-value"></a>Wartość zwracana

`S_OK`w przypadku powodzenia; w przeciwnym razie wartość błędu.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby odświeżyć `CMFCShellListCtrl` listę elementów wyświetlanych przez obiekt.

## <a name="cmfcshelllistctrlsetitemtypes"></a><a name="setitemtypes"></a>CMFCShellListCtrl::SetItemTypes

Ustawia typ elementów, które są wymienione w [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiektu.

```cpp
void SetItemTypes(SHCONTF nTypes);
```

### <a name="parameters"></a>Parametry

*nTypy*<br/>
[w] Lista typów elementów, `CMFCShellListCtrl` które obsługuje obiekt.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat listy typów elementów, zobacz [SHCONTF](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf).

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)<br/>
[Klasa CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)
