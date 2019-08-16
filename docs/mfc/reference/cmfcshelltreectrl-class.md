---
title: Klasa CMFCShellTreeCtrl
ms.date: 11/04/2016
f1_keywords:
- CMFCShellTreeCtrl
- AFXSHELLTREECTRL/CMFCShellTreeCtrl
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::EnableShellContextMenu
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetFlags
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetItemPath
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetRelatedList
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnChildNotify
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnGetItemIcon
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnGetItemText
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::Refresh
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SelectPath
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SetFlags
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SetRelatedList
helpviewer_keywords:
- CMFCShellTreeCtrl [MFC], EnableShellContextMenu
- CMFCShellTreeCtrl [MFC], GetFlags
- CMFCShellTreeCtrl [MFC], GetItemPath
- CMFCShellTreeCtrl [MFC], GetRelatedList
- CMFCShellTreeCtrl [MFC], OnChildNotify
- CMFCShellTreeCtrl [MFC], OnGetItemIcon
- CMFCShellTreeCtrl [MFC], OnGetItemText
- CMFCShellTreeCtrl [MFC], Refresh
- CMFCShellTreeCtrl [MFC], SelectPath
- CMFCShellTreeCtrl [MFC], SetFlags
- CMFCShellTreeCtrl [MFC], SetRelatedList
ms.assetid: 3d1da715-9554-4ed7-968c-055c48146267
ms.openlocfilehash: 97136342049a54d45af893962025f01eda4366d4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504911"
---
# <a name="cmfcshelltreectrl-class"></a>Klasa CMFCShellTreeCtrl

Klasa rozszerza funkcje [klasy CTreeCtrl](../../mfc/reference/ctreectrl-class.md) , wyświetlając hierarchię elementów powłoki. `CMFCShellTreeCtrl`

Aby uzyskać więcej szczegółów, zobacz kod źródłowy znajdujący się w folderze **VC\\atlmfc\\src\\MFC** instalacji programu Visual Studio.
## <a name="syntax"></a>Składnia

```
class CMFCShellTreeCtrl : public CTreeCtrl
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCShellTreeCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Włącza lub wyłącza menu skrótów.|
|[CMFCShellTreeCtrl:: GetFlags](#getflags)|Zwraca kombinację flag, które są przenoszone do [IShellFolder:: EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects).|
|[CMFCShellTreeCtrl::GetItemPath](#getitempath)|Pobiera ścieżkę do elementu.|
|[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)|Zwraca wskaźnik do obiektu [klasy CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) , który jest używany razem z tym `CMFCShellTreeCtrl` obiektem, aby utworzyć okno podobne do Eksploratora.|
|[CMFCShellTreeCtrl::OnChildNotify](#onchildnotify)|Ta funkcja członkowska jest wywoływana przez okno nadrzędne tego okna, gdy odbierze komunikat z powiadomieniem dotyczący tego okna. (Przesłania [CWnd:: OnChildNotify](../../mfc/reference/cwnd-class.md#onchildnotify).)|
|[CMFCShellTreeCtrl::OnGetItemIcon](#ongetitemicon)||
|[CMFCShellTreeCtrl::OnGetItemText](#ongetitemtext)||
|[CMFCShellTreeCtrl:: Refresh](#refresh)|Odświeża i odmaluje bieżący `CMFCShellTreeCtrl` obiekt.|
|[CMFCShellTreeCtrl::SelectPath](#selectpath)|Wybiera odpowiedni element formantu drzewa na podstawie dostarczonej ścieżki PIDL lub ciągu.|
|[CMFCShellTreeCtrl::SetFlags](#setflags)|Ustawia flagi do filtrowania kontekstu drzewa (podobnie jak flagi używane przez `IShellFolder::EnumObjects`).|
|[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)|Ustawia relację między bieżącym `CMFCShellTreeCtrl` obiektem `CMFCShellListCtrl` a obiektem.|

## <a name="remarks"></a>Uwagi

Ta Klasa rozszerza `CTreeCtrl` klasę, umożliwiając programowi dołączenie elementów powłoki systemu Windows w drzewie. Ta klasa może być skojarzona z `CMFCShellListCtrl` obiektem w celu utworzenia kompletnego okna Eksploratora. Po wybraniu elementu w drzewie zostanie wyświetlona lista elementów powłoki systemu Windows na liście skojarzonej.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)

`CMFCShellTreeCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxshelltreeCtrl. h

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób tworzenia obiektu `CMFCShellTreeCtrl` klasy. Ten fragment kodu jest częścią [przykładu Eksploratora](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#4](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#5](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_2.cpp)]

##  <a name="enableshellcontextmenu"></a>CMFCShellTreeCtrl::EnableShellContextMenu

Włącza menu skrótów.

```
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
podczas Wartość logiczna określająca, czy włączyć menu skrótów.

##  <a name="getflags"></a>CMFCShellTreeCtrl:: GetFlags

Zwraca flagi ustawione dla obiektu [klasy CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) .

```
DWORD GetFlags() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość DWORD, która określa kombinację aktualnie ustawionych flag.

### <a name="remarks"></a>Uwagi

Flagi ustawione w `CMFCShellTreeCtrl` elemencie są wysyłane do metody [IShellFolder:: EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects) za każdym razem, gdy obiekt zostanie odświeżony. Flagi można zmienić za pomocą metody [CMFCShellTreeCtrl::](#setflags) SetFlags.

##  <a name="getitempath"></a>CMFCShellTreeCtrl::GetItemPath

Pobiera ścieżkę elementu w obiekcie [klasy CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) .

```
BOOL GetItemPath(
    CString& strPath,
    HTREEITEM htreeItem = NULL) const;
```

### <a name="parameters"></a>Parametry

*strPath*<br/>
określoną Odwołanie do parametru ciągu. Metoda zapisuje ścieżkę elementu do tego parametru.

*htreeItem*<br/>
podczas Metoda pobiera ścieżkę dla tego elementu kontrolki drzewa.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; 0 w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Jeśli ta metoda zakończy się niepowodzeniem, *strPath* zawiera pusty ciąg.

Jeśli nie określisz *hTreeItem*, ta metoda próbuje uzyskać ciąg dla aktualnie wybranego elementu. Jeśli nie wybrano żadnego elementu i *hTreeItem* ma wartość null, ta metoda zakończy się niepowodzeniem.

##  <a name="getrelatedlist"></a>CMFCShellTreeCtrl::GetRelatedList

Zwraca wskaźnik do obiektu [klasy CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) , który jest skojarzony z tym obiektem [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) .

```
CMFCShellListCtrl* GetRelatedList() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CMFCShellListCtrl` obiektu, który jest skojarzony z tym obiektem kontrolki drzewa.

### <a name="remarks"></a>Uwagi

Używając `CMFCShellListCtrl` obiektu wraz `CMFCShellTreeCtrl` z obiektem, można utworzyć okno podobne do Eksploratora. Użyj metody [CMFCShellTreeCtrl:: SetRelatedList](#setrelatedlist) , aby skojarzyć dwie klasy. Po ich skojarzeniu, struktura automatycznie aktualizuje `CMFCShellListCtrl` zaznaczenie `CMFCShellTreeCtrl` w obszarze zmiany.

##  <a name="onchildnotify"></a>CMFCShellTreeCtrl::OnChildNotify

```
virtual BOOL OnChildNotify(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* pLResult);
```

### <a name="parameters"></a>Parametry

podczas *komunikat*<br/>
podczas *wParam*<br/>
podczas *lParam*<br/>
podczas *pLResult*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="ongetitemicon"></a>CMFCShellTreeCtrl::OnGetItemIcon

```
virtual int OnGetItemIcon(
    LPAFX_SHELLITEMINFO pItem,
    BOOL bSelected);
```

### <a name="parameters"></a>Parametry

podczas *pItem*<br/>
podczas *bSelected*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="ongetitemtext"></a>CMFCShellTreeCtrl::OnGetItemText

```
virtual CString OnGetItemText(LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Parametry

podczas *pItem*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="refresh"></a>CMFCShellTreeCtrl:: Refresh

Odświeża i odmaluje [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md).

```
void Refresh();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby odświeżyć hierarchię elementów wyświetlanych `CMFCShellTreeCtrl`w.

##  <a name="selectpath"></a>CMFCShellTreeCtrl::SelectPath

Wybiera element w [klasie CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) na podstawie podanej ścieżki.

```
BOOL SelectPath(LPCTSTR lpszPath);
BOOL SelectPath(LPCITEMIDLIST lpidl);
```

### <a name="parameters"></a>Parametry

*lpszPath*<br/>
podczas Ciąg określający ścieżkę elementu.

*lpidl*<br/>
podczas PIDL, który określa element

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; W przeciwnym razie.

##  <a name="setflags"></a>CMFCShellTreeCtrl:: SetFlags

Ustawia flagi do filtrowania kontekstu drzewa.

```
void SetFlags(
    DWORD dwFlags,
    BOOL bRefresh = TRUE);
```

### <a name="parameters"></a>Parametry

*flagiDW*<br/>
podczas Flagi do ustawienia.

*bRefresh*<br/>
podczas Wartość logiczna określająca, czy `CMFCShellTreeCtrl` powinny być od razu odświeżane.

### <a name="remarks"></a>Uwagi

Wszystkie flagi passs Set do [IShellFolder:: EnumObjects.](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects) `CMFCShellTreeCtrl` Aby uzyskać więcej informacji na temat wartości różnych flag, zobacz [IShellFolder:: EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects).

##  <a name="setrelatedlist"></a>CMFCShellTreeCtrl::SetRelatedList

Kojarzy obiekt [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) z obiektem [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) .

```
void SetRelatedList(CMFCShellListCtrl* pShellList);
```

### <a name="parameters"></a>Parametry

*pShellList*<br/>
podczas Wskaźnik do `CMFCShellListCtrl` obiektu.

### <a name="remarks"></a>Uwagi

Ta metoda kojarzy `CMFCShellListCtrl` `CMFCShellTreeCtrl`z. Te obiekty mogą być wyświetlane jako okna podobne do Eksploratora: Jeśli użytkownik wybierze obiekt w `CMFCShellTreeCtrl`, skojarzone elementy `CMFCShellListCtrl` w elemencie zostaną automatycznie zaktualizowane.

Użyj metody [CMFCShellTreeCtrl:: GetRelatedList](#getrelatedlist) , aby pobrać `CMFCShellListCtrl` skojarzenie z. `CMFCShellTreeCtrl`

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CTreeCtrl](../../mfc/reference/ctreectrl-class.md)<br/>
[Klasa CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)
