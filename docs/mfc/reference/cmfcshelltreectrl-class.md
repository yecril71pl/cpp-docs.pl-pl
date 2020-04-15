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
ms.openlocfilehash: 41d9a14e379c566f001eda8b10b2669b95beb171
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376144"
---
# <a name="cmfcshelltreectrl-class"></a>Klasa CMFCShellTreeCtrl

Klasa `CMFCShellTreeCtrl` rozszerza funkcje [klasy CTreeCtrl,](../../mfc/reference/ctreectrl-class.md) wyświetlając hierarchię elementów powłoki.

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

## <a name="syntax"></a>Składnia

```
class CMFCShellTreeCtrl : public CTreeCtrl
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCShellTreeCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Włącza lub wyłącza menu skrótów.|
|[CMFCShellTreeCtrl::GetFlags](#getflags)|Zwraca kombinację flag, które są przekazywane do [IShellFolder::EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects).|
|[CMFCShellTreeCtrl::GetItemPath](#getitempath)|Pobiera ścieżkę do elementu.|
|[CMFCShellTreeCtrl::Lista powiązanych](#getrelatedlist)|Zwraca wskaźnik do [CMFCShellListCtrl Class](../../mfc/reference/cmfcshelllistctrl-class.md) obiektu, który `CMFCShellTreeCtrl` jest używany wraz z tym obiektem do tworzenia okna explorer-like.|
|[CMFCShellTreeCtrl::OnChildNotify](#onchildnotify)|Ta funkcja elementu członkowskiego jest wywoływana przez okno nadrzędne tego okna po odebraniu komunikatu powiadomienia, który ma zastosowanie do tego okna. (Zastępuje [CWnd::OnChildNotify](../../mfc/reference/cwnd-class.md#onchildnotify).)|
|[CMFCShellTreeCtrl::OnGetItemicon](#ongetitemicon)||
|[CMFCShellTreeCtrl::OnGetItemText](#ongetitemtext)||
|[CMFCShellTreeCtrl::Odśwież](#refresh)|Odświeża i odświeża bieżący `CMFCShellTreeCtrl` obiekt.|
|[CMFCShellTreeCtrl::SelectPath](#selectpath)|Wybiera odpowiedni element formantu drzewa na podstawie dołączonej ścieżki PIDL lub ciągu.|
|[CMFCShellTreeCtrl::SetFlags](#setflags)|Ustawia flagi do filtrowania kontekstu drzewa `IShellFolder::EnumObjects`(podobne do flag używanych przez ).|
|[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)|Ustawia relację między `CMFCShellTreeCtrl` bieżącym `CMFCShellListCtrl` obiektem a obiektem.|

## <a name="remarks"></a>Uwagi

Ta klasa rozszerza `CTreeCtrl` klasę, umożliwiając programowi dołączanie elementów powłoki systemu Windows do drzewa. Tę klasę można skojarzyć z obiektem, `CMFCShellListCtrl` aby utworzyć kompletne okno Eksploratora. Następnie wybranie elementu w drzewie spowoduje wyświetlenie listy elementów powłoki systemu Windows na skojarzonej liście.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Ctreectrl](../../mfc/reference/ctreectrl-class.md)

`CMFCShellTreeCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxshelltreeCtrl.h

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCShellTreeCtrl` utworzyć obiekt klasy. Ten fragment kodu jest częścią [przykładu Eksploratora](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#4](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#5](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_2.cpp)]

## <a name="cmfcshelltreectrlenableshellcontextmenu"></a><a name="enableshellcontextmenu"></a>CMFCShellTreeCtrl::EnableShellContextMenu

Włącza menu skrótów.

```
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
[w] Wartość logiczna określająca, czy włączyć menu skrótów.

## <a name="cmfcshelltreectrlgetflags"></a><a name="getflags"></a>CMFCShellTreeCtrl::GetFlags

Zwraca flagi ustawione dla [obiektu CMFCShellTreeCtrl Class.](../../mfc/reference/cmfcshelltreectrl-class.md)

```
DWORD GetFlags() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość DWORD określająca kombinację aktualnie ustawionych flag.

### <a name="remarks"></a>Uwagi

Flagi ustawione w `CMFCShellTreeCtrl` są wysyłane do metody [IShellFolder::EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects) każdym razem, gdy obiekt jest odświeżany. Flagi można zmienić za pomocą [METODY CMFCShellTreeCtrl::SetFlags.](#setflags)

## <a name="cmfcshelltreectrlgetitempath"></a><a name="getitempath"></a>CMFCShellTreeCtrl::GetItemPath

Pobiera ścieżkę elementu w [CMFCShellTreeCtrl Class](../../mfc/reference/cmfcshelltreectrl-class.md) obiektu.

```
BOOL GetItemPath(
    CString& strPath,
    HTREEITEM htreeItem = NULL) const;
```

### <a name="parameters"></a>Parametry

*strPath (ścieżka strPath)*<br/>
[na zewnątrz] Odwołanie do parametru ciągu. Metoda zapisuje ścieżkę elementu do tego parametru.

*htreeItem (polski)*<br/>
[w] Metoda pobiera ścieżkę dla tego elementu kontroli drzewa.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; 0 w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Jeśli ta metoda nie powiedzie się, *strPath* zawiera pusty ciąg.

Jeśli nie określisz *hTreeItem*, ta metoda próbuje uzyskać ciąg dla aktualnie wybranego elementu. Jeśli nie jest zaznaczony żaden element i *hTreeItem* jest NULL, ta metoda kończy się niepowodzeniem.

## <a name="cmfcshelltreectrlgetrelatedlist"></a><a name="getrelatedlist"></a>CMFCShellTreeCtrl::Lista powiązanych

Zwraca wskaźnik do [obiektu CMFCShellListCtrl Class,](../../mfc/reference/cmfcshelllistctrl-class.md) który jest skojarzony z tym obiektem [CMFCShellTreeCtrl.](../../mfc/reference/cmfcshelltreectrl-class.md)

```
CMFCShellListCtrl* GetRelatedList() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CMFCShellListCtrl` obiektu skojarzonego z tym obiektem sterującym drzewa.

### <a name="remarks"></a>Uwagi

Za pomocą `CMFCShellListCtrl` obiektu wraz `CMFCShellTreeCtrl` z obiektem, można utworzyć okno podobne do Eksploratora. Użyj metody [CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist) skojarzyć dwie klasy. Po ich skojarzeniu, ramy automatycznie `CMFCShellListCtrl` aktualizuje, jeśli `CMFCShellTreeCtrl` wybór w zmianach.

## <a name="cmfcshelltreectrlonchildnotify"></a><a name="onchildnotify"></a>CMFCShellTreeCtrl::OnChildNotify

```
virtual BOOL OnChildNotify(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* pLResult);
```

### <a name="parameters"></a>Parametry

[w] *wiadomość*<br/>
[w] *wParam*<br/>
[w] *lParam*<br/>
[w] *pLResult (Wyniki)*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcshelltreectrlongetitemicon"></a><a name="ongetitemicon"></a>CMFCShellTreeCtrl::OnGetItemicon

```
virtual int OnGetItemIcon(
    LPAFX_SHELLITEMINFO pItem,
    BOOL bSelected);
```

### <a name="parameters"></a>Parametry

[w] *pItem (własówce)*<br/>
[w] *bWybrany*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcshelltreectrlongetitemtext"></a><a name="ongetitemtext"></a>CMFCShellTreeCtrl::OnGetItemText

```
virtual CString OnGetItemText(LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Parametry

[w] *pItem (własówce)*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcshelltreectrlrefresh"></a><a name="refresh"></a>CMFCShellTreeCtrl::Odśwież

Odświeża i odświeża [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md).

```
void Refresh();
```

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby odświeżyć hierarchię elementów wyświetlanych w . `CMFCShellTreeCtrl`

## <a name="cmfcshelltreectrlselectpath"></a><a name="selectpath"></a>CMFCShellTreeCtrl::SelectPath

Wybiera element w [CMFCShellTreeCtrl klasy](../../mfc/reference/cmfcshelltreectrl-class.md) na podstawie podanej ścieżki.

```
BOOL SelectPath(LPCTSTR lpszPath);
BOOL SelectPath(LPCITEMIDLIST lpidl);
```

### <a name="parameters"></a>Parametry

*lpszPath (lpszPath)*<br/>
[w] Ciąg określający ścieżkę elementu.

*lpidl*<br/>
[w] Pidl, który określa element

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; E_FAIL inaczej.

## <a name="cmfcshelltreectrlsetflags"></a><a name="setflags"></a>CMFCShellTreeCtrl::SetFlags

Ustawia flagi do filtrowania kontekstu drzewa.

```
void SetFlags(
    DWORD dwFlags,
    BOOL bRefresh = TRUE);
```

### <a name="parameters"></a>Parametry

*Dwflags*<br/>
[w] Flagi do ustawionego.

*bRefresh*<br/>
[w] Wartość logiczna określająca, `CMFCShellTreeCtrl` czy należy natychmiast odświeżyć.

### <a name="remarks"></a>Uwagi

Wszystkie `CMFCShellTreeCtrl` flagi zestawu przechodzą do [IShellFolder::EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects). Aby uzyskać więcej informacji na temat wartości różnych flag, zobacz [IShellFolder::EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects).

## <a name="cmfcshelltreectrlsetrelatedlist"></a><a name="setrelatedlist"></a>CMFCShellTreeCtrl::SetRelatedList

Kojarzy [obiekt CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) z obiektem [CMFCShellTreeCtrl.](../../mfc/reference/cmfcshelltreectrl-class.md)

```
void SetRelatedList(CMFCShellListCtrl* pShellList);
```

### <a name="parameters"></a>Parametry

*pShellList (Lista)*<br/>
[w] Wskaźnik do `CMFCShellListCtrl` obiektu.

### <a name="remarks"></a>Uwagi

Ta metoda kojarzy `CMFCShellListCtrl` `CMFCShellTreeCtrl`a z . Obiekty te mogą być wyświetlane jako okno podobne do Eksploratora: jeśli użytkownik wybierze obiekt w `CMFCShellTreeCtrl`, skojarzone elementy w zostaną `CMFCShellListCtrl` automatycznie zaktualizowane.

Użyj metody [CMFCShellTreeCtrl::GetRelatedList,](#getrelatedlist) aby `CMFCShellListCtrl` pobrać skojarzone z `CMFCShellTreeCtrl`.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CTreeCtrl](../../mfc/reference/ctreectrl-class.md)<br/>
[KLASA CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)
