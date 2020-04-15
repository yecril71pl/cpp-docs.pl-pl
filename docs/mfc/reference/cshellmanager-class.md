---
title: Klasa CShellManager
ms.date: 11/04/2016
f1_keywords:
- CShellManager
- AFXSHELLMANAGER/CShellManager
- AFXSHELLMANAGER/CShellManager::CShellManager
- AFXSHELLMANAGER/CShellManager::BrowseForFolder
- AFXSHELLMANAGER/CShellManager::ConcatenateItem
- AFXSHELLMANAGER/CShellManager::CopyItem
- AFXSHELLMANAGER/CShellManager::CreateItem
- AFXSHELLMANAGER/CShellManager::FreeItem
- AFXSHELLMANAGER/CShellManager::GetItemCount
- AFXSHELLMANAGER/CShellManager::GetItemSize
- AFXSHELLMANAGER/CShellManager::GetNextItem
- AFXSHELLMANAGER/CShellManager::GetParentItem
- AFXSHELLMANAGER/CShellManager::ItemFromPath
helpviewer_keywords:
- CShellManager [MFC], CShellManager
- CShellManager [MFC], BrowseForFolder
- CShellManager [MFC], ConcatenateItem
- CShellManager [MFC], CopyItem
- CShellManager [MFC], CreateItem
- CShellManager [MFC], FreeItem
- CShellManager [MFC], GetItemCount
- CShellManager [MFC], GetItemSize
- CShellManager [MFC], GetNextItem
- CShellManager [MFC], GetParentItem
- CShellManager [MFC], ItemFromPath
ms.assetid: f15c4c1a-6fae-487d-9913-9b7369b33da0
ms.openlocfilehash: cc8aa9216fd0d4dcc169830fb745134ceb5c65fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318415"
---
# <a name="cshellmanager-class"></a>Klasa CShellManager

Implementuje kilka metod, które umożliwiają pracę ze wskaźnikami do list identyfikatorów (PIDLs).

## <a name="syntax"></a>Składnia

```
class CShellManager : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CShellManager::CShellManager](#cshellmanager)|Konstruuje `CShellManager` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CShellManager::BrowseForFolder](#browseforfolder)|Wyświetla okno dialogowe umożliwiające użytkownikowi wybranie folderu powłoki.|
|[CShellManager::ConcatenateItem](#concatenateitem)|Łączy dwa pidl.|
|[CShellManager::CopyItem](#copyitem)|Tworzy nowy pidl i kopiuje dostarczonych PIDL do niego.|
|[CShellManager::CreateItem](#createitem)|Tworzy nowy identyfikator PIDL o określonym rozmiarze.|
|[CShellManager::FreeItem](#freeitem)|Usuwa dostarczony identyfikator PIDL.|
|[CShellManager::GetItemCount](#getitemcount)|Zwraca liczbę towarów w podanym identyfikatorze PIDL.|
|[CShellManager::GetItemSize](#getitemsize)|Zwraca rozmiar dostarczonego identyfikatora PIDL.|
|[CShellManager::GetNextItem](#getnextitem)|Zwraca następny element z identyfikatora PIDL.|
|[CShellManager::GetParentItem](#getparentitem)|Pobiera element nadrzędny dostarczonego towaru.|
|[CShellManager::ItemFromPath](#itemfrompath)|Pobiera identyfikator PIDL dla elementu identyfikowane przez dostarczoną ścieżkę.|

## <a name="remarks"></a>Uwagi

Metody `CShellManager` klasy wszystkie dotyczą pidls. PIDL jest unikatowym identyfikatorem obiektu powłoki.

Obiektu nie należy `CShellManager` tworzyć ręcznie. Zostanie on utworzony automatycznie przez ramy aplikacji. Jednak należy wywołać [CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager) podczas procesu inicjowania aplikacji. Aby uzyskać wskaźnik do menedżera powłoki dla aplikacji, zadzwoń [CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Menedżer CShell](../../mfc/reference/cshellmanager-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxshellmanager.h

## <a name="cshellmanagerbrowseforfolder"></a><a name="browseforfolder"></a>CShellManager::BrowseForFolder

Wyświetla okno dialogowe umożliwiające użytkownikowi wybranie folderu powłoki.

```
BOOL BrowseForFolder(
    CString& strOutFolder,
    CWnd* pWndParent = NULL,
    LPCTSTR lplszInitialFolder = NULL,
    LPCTSTR lpszTitle = NULL,
    UINT ulFlags = BIF_RETURNONLYFSDIRS,
    LPINT piFolderImage = NULL);
```

### <a name="parameters"></a>Parametry

*strOutFolder (StrOutFolder)*<br/>
[na zewnątrz] Ciąg używany przez metodę do przechowywania ścieżki wybranego folderu.

*pWndRodziciela*<br/>
[w] Wskaźnik do okna nadrzędnego.

*lplszInitialFolder*<br/>
[w] Ciąg zawierający folder wybrany domyślnie podczas wyświetlania okna dialogowego.

*lpszTitle (lpszTitle)*<br/>
[w] Tytuł okna dialogowego.

*ulFlags*<br/>
[w] Flagi określające opcje okna dialogowego. Zobacz [BROWSEINFO](/windows/win32/api/shlobj_core/ns-shlobj_core-browseinfow) szczegółowy opis.

*piFolderImage (Obraz)*<br/>
[na zewnątrz] Wskaźnik do wartości całkowitej, w której metoda zapisuje indeks obrazu wybranego folderu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli użytkownik wybierze folder z okna dialogowego; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Po wywołaniu tej metody aplikacja tworzy i pokazuje okno dialogowe, które umożliwia użytkownikowi wybranie folderu. Metoda zapisze ścieżkę folderu do *strOutFolder* parametru.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CShellManager` pobrać odwołanie `CWinAppEx::GetShellManager` do obiektu przy `BrowseForFolder` użyciu metody i jak używać metody. Ten fragment kodu jest częścią [przykładu Eksploratora](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#6](../../mfc/reference/codesnippet/cpp/cshellmanager-class_1.cpp)]

## <a name="cshellmanagerconcatenateitem"></a><a name="concatenateitem"></a>CShellManager::ConcatenateItem

Tworzy nową listę zawierającą dwa pidl.

```
LPITEMIDLIST ConcatenateItem(
    LPCITEMIDLIST pidl1,
    LPCITEMIDLIST pidl2);
```

### <a name="parameters"></a>Parametry

*pidl1*<br/>
[w] Pierwszy element.

*pidl2*<br/>
[w] Drugi element.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowej listy elementów, jeśli funkcja powiedzie się, w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Ta metoda tworzy nowy [ITEMIDLIST](/windows/win32/api/shtypes/ns-shtypes-itemidlist) wystarczająco duży, aby zawierać zarówno *pidl1* i *pidl2*. Następnie kopiuje *pidl1* i *pidl2* do nowej listy.

## <a name="cshellmanagercopyitem"></a><a name="copyitem"></a>CShellManager::CopyItem

Kopiuje listę elementów.

```
LPITEMIDLIST CopyItem(LPCITEMIDLIST pidlSource);
```

### <a name="parameters"></a>Parametry

*pidlŹródło*<br/>
[w] Oryginalna lista elementów.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowo utworzonej listy elementów, jeśli zakończy się pomyślnie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Nowo utworzona lista elementów ma taki sam rozmiar jak lista elementów źródłowych.

## <a name="cshellmanagercreateitem"></a><a name="createitem"></a>CShellManager::CreateItem

Tworzy nowy pidl.

```
LPITEMIDLIST CreateItem(UINT cbSize);
```

### <a name="parameters"></a>Parametry

*rozmiar cbSize*<br/>
[w] Rozmiar listy elementów.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do utworzonej listy elementów, jeśli się powiedzie; w przeciwnym razie NULL.

## <a name="cshellmanagercshellmanager"></a><a name="cshellmanager"></a>CShellManager::CShellManager

Konstruuje `CShellManager` obiekt.

```
CShellManager();
```

### <a name="remarks"></a>Uwagi

W większości przypadków nie trzeba tworzyć `CShellManager` bezpośrednio. Domyślnie struktura tworzy jeden dla Ciebie. Aby uzyskać wskaźnik `CShellManager`do , wywołać [CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager). Jeśli utworzysz `CShellManager` ręcznie, należy go zainicjować za pomocą metody [CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager).

## <a name="cshellmanagerfreeitem"></a><a name="freeitem"></a>CShellManager::FreeItem

Usuwa listę elementów.

```
void FreeItem(LPITEMIDLIST pidl);
```

### <a name="parameters"></a>Parametry

*pidl*<br/>
[w] Lista elementów do usunięcia.

## <a name="cshellmanagergetitemcount"></a><a name="getitemcount"></a>CShellManager::GetItemCount

Zwraca liczbę elementów na liście towarów.

```
UINT GetItemCount(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parametry

*pidl*<br/>
[w] Wskaźnik do listy elementów.

### <a name="return-value"></a>Wartość zwracana

Liczba elementów na liście elementów.

## <a name="cshellmanagergetitemsize"></a><a name="getitemsize"></a>CShellManager::GetItemSize

Zwraca rozmiar listy towarów.

```
UINT GetItemSize(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parametry

*pidl*<br/>
[w] Wskaźnik do listy elementów.

### <a name="return-value"></a>Wartość zwracana

Rozmiar listy elementów.

## <a name="cshellmanagergetnextitem"></a><a name="getnextitem"></a>CShellManager::GetNextItem

Pobiera następny element ze wskaźnika do listy identyfikatorów elementów (PIDL).

```
LPITEMIDLIST GetNextItem(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parametry

*pidl*<br/>
[w] Lista elementów do iteracji.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do następnego elementu na liście.

### <a name="remarks"></a>Uwagi

Jeśli na liście nie ma więcej elementów, ta metoda zwraca wartość NULL.

## <a name="cshellmanagergetparentitem"></a><a name="getparentitem"></a>CShellManager::GetParentItem

Pobiera element nadrzędny wskaźnika do listy identyfikatorów elementów (PIDL).

```
int GetParentItem(
    LPCITEMIDLIST lpidl,
    LPITEMIDLIST& lpidlParent);
```

### <a name="parameters"></a>Parametry

*lpidl*<br/>
[w] Pidl, którego element nadrzędny zostanie pobrany.

*lpidlRosz*<br/>
[na zewnątrz] Odwołanie do PIDL, gdzie metoda będzie przechowywać wynik.

### <a name="return-value"></a>Wartość zwracana

Poziom nadrzędnego PIDL.

### <a name="remarks"></a>Uwagi

Poziom pidl jest względem pulpitu. Kod PIDL pulpitu jest uważany za poziom 0.

## <a name="cshellmanageritemfrompath"></a><a name="itemfrompath"></a>CShellManager::ItemFromPath

Pobiera wskaźnik do listy identyfikatorów elementów (PIDL) z elementu identyfikowanego przez ścieżkę ciągu.

```
HRESULT ItemFromPath(
    LPCTSTR lpszPath,
    LPITEMIDLIST& pidl);
```

### <a name="parameters"></a>Parametry

*lpszPath (lpszPath)*<br/>
[w] Ciąg określający ścieżkę dla elementu.

*pidl*<br/>
[na zewnątrz] Odwołanie do pidl. Metoda używa tego PIDL do przechowywania wskaźnika do jego wartości zwracanej.

### <a name="return-value"></a>Wartość zwracana

Zwraca NOERROR, jeśli zakończy się pomyślnie; wartość błędu zdefiniowanego przez OLE.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
