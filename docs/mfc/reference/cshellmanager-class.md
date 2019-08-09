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
ms.openlocfilehash: 14e8da573621f712ae9e27647122d305be54b7b0
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916681"
---
# <a name="cshellmanager-class"></a>Klasa CShellManager

Implementuje kilka metod, które umożliwiają współpracę ze wskaźnikami do list identyfikatorów (PIDLs).

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
|[CShellManager::BrowseForFolder](#browseforfolder)|Wyświetla okno dialogowe, które umożliwia użytkownikowi wybranie folderu powłoki.|
|[CShellManager::ConcatenateItem](#concatenateitem)|Łączy dwie PIDLs.|
|[CShellManager::CopyItem](#copyitem)|Tworzy nowy PIDL i kopiuje do niego dostarczoną PIDL.|
|[CShellManager:: GetItem](#createitem)|Tworzy nowy PIDL o określonym rozmiarze.|
|[CShellManager::FreeItem](#freeitem)|Usuwa dostarczoną PIDL.|
|[CShellManager::GetItemCount](#getitemcount)|Zwraca liczbę elementów w podanym PIDL.|
|[CShellManager::GetItemSize](#getitemsize)|Zwraca rozmiar podanej PIDL.|
|[CShellManager::GetNextItem](#getnextitem)|Zwraca następny element z PIDL.|
|[CShellManager::GetParentItem](#getparentitem)|Pobiera element nadrzędny podanego elementu.|
|[CShellManager::ItemFromPath](#itemfrompath)|Pobiera PIDL dla elementu identyfikowanego przez podaną ścieżkę.|

## <a name="remarks"></a>Uwagi

Metody `CShellManager` klasy All zajmują się PIDLs. PIDL jest unikatowym identyfikatorem dla obiektu powłoki.

Nie należy tworzyć `CShellManager` obiektu ręcznie. Zostanie ona utworzona automatycznie przez strukturę aplikacji. Należy jednak wywołać [CWinAppEx:: InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager) podczas procesu inicjowania aplikacji. Aby uzyskać wskaźnik do Menedżera powłoki dla aplikacji, wywołaj [CWinAppEx::](../../mfc/reference/cwinappex-class.md#getshellmanager)GetShellManager.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CShellManager](../../mfc/reference/cshellmanager-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxshellmanager. h

##  <a name="browseforfolder"></a>CShellManager::BrowseForFolder

Wyświetla okno dialogowe, które umożliwia użytkownikowi wybranie folderu powłoki.

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

*strOutFolder*<br/>
określoną Ciąg używany przez metodę do przechowywania ścieżki wybranego folderu.

*pWndParent*<br/>
podczas Wskaźnik do okna nadrzędnego.

*lplszInitialFolder*<br/>
podczas Ciąg, który zawiera folder, który jest wybierany domyślnie po wyświetleniu okna dialogowego.

*lpszTitle*<br/>
podczas Tytuł okna dialogowego.

*ulFlags*<br/>
podczas Flagi określające opcje okna dialogowego. Szczegółowy opis można znaleźć w temacie [BROWSEINFO](/windows/desktop/api/shlobj_core/ns-shlobj_core-browseinfoa) .

*piFolderImage*<br/>
określoną Wskaźnik do wartości całkowitej, w której Metoda zapisuje indeks obrazu wybranego folderu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli użytkownik wybierze folder z okna dialogowego; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Po wywołaniu tej metody aplikacja tworzy i wyświetla okno dialogowe, które umożliwia użytkownikowi wybranie folderu. Metoda zapisze ścieżkę folderu do parametru *strOutFolder* .

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak pobrać odwołanie do `CShellManager` obiektu za `CWinAppEx::GetShellManager` pomocą metody `BrowseForFolder` i jak używać metody. Ten fragment kodu jest częścią [przykładu Eksploratora](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#6](../../mfc/reference/codesnippet/cpp/cshellmanager-class_1.cpp)]

##  <a name="concatenateitem"></a>CShellManager::ConcatenateItem

Tworzy nową listę zawierającą dwie PIDLs.

```
LPITEMIDLIST ConcatenateItem(
    LPCITEMIDLIST pidl1,
    LPCITEMIDLIST pidl2);
```

### <a name="parameters"></a>Parametry

*pidl1*<br/>
podczas Pierwszy element.

*pidl2*<br/>
podczas Drugi element.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do listy nowy element, jeśli funkcja się powiedzie, w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Ta metoda tworzy nowy [ITEMIDLIST](/windows/desktop/api/shtypes/ns-shtypes-itemidlist) wystarczająco duży, aby zawierał zarówno *pidl1* , jak i *pidl2*. Następnie kopiuje *pidl1* i *pidl2* do nowej listy.

##  <a name="copyitem"></a>CShellManager::CopyItem

Kopiuje listę elementów.

```
LPITEMIDLIST CopyItem(LPCITEMIDLIST pidlSource);
```

### <a name="parameters"></a>Parametry

*pidlSource*<br/>
podczas Lista pierwotnych elementów.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowo utworzonego elementu listy, jeśli zakończy się pomyślnie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Lista nowo utworzonych elementów ma taki sam rozmiar jak lista elementów źródłowych.

##  <a name="createitem"></a>CShellManager:: GetItem

Tworzy nowy PIDL.

```
LPITEMIDLIST CreateItem(UINT cbSize);
```

### <a name="parameters"></a>Parametry

*cbSize*<br/>
podczas Rozmiar listy elementów.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do listy utworzony element, jeśli powodzenie; w przeciwnym razie wartość NULL.

##  <a name="cshellmanager"></a>CShellManager::CShellManager

Konstruuje `CShellManager` obiekt.

```
CShellManager();
```

### <a name="remarks"></a>Uwagi

W większości przypadków nie trzeba tworzyć `CShellManager` bezpośredniego. Domyślnie struktura tworzy jedną dla siebie. Aby uzyskać wskaźnik do `CShellManager`, wywołaj [CWinAppEx:: GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager). Jeśli tworzysz `CShellManager` ręcznie, musisz zainicjować go przy użyciu metody [CWinAppEx:: InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager).

##  <a name="freeitem"></a>CShellManager::FreeItem

Usuwa listę elementów.

```
void FreeItem(LPITEMIDLIST pidl);
```

### <a name="parameters"></a>Parametry

*pidl*<br/>
podczas Lista elementów do usunięcia.

##  <a name="getitemcount"></a>CShellManager::GetItemCount

Zwraca liczbę elementów na liście elementów.

```
UINT GetItemCount(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parametry

*pidl*<br/>
podczas Wskaźnik do listy elementów.

### <a name="return-value"></a>Wartość zwracana

Liczba elementów na liście elementów.

##  <a name="getitemsize"></a>CShellManager::GetItemSize

Zwraca rozmiar listy elementów.

```
UINT GetItemSize(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parametry

*pidl*<br/>
podczas Wskaźnik do listy elementów.

### <a name="return-value"></a>Wartość zwracana

Rozmiar listy elementów.

##  <a name="getnextitem"></a>CShellManager::GetNextItem

Pobiera następny element ze wskaźnika do listy identyfikatorów elementów (PIDL).

```
LPITEMIDLIST GetNextItem(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parametry

*pidl*<br/>
podczas Lista elementów do iteracji.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do następnego elementu na liście.

### <a name="remarks"></a>Uwagi

Jeśli na liście nie ma więcej elementów, ta metoda zwraca wartość NULL.

##  <a name="getparentitem"></a>CShellManager::GetParentItem

Pobiera element nadrzędny wskaźnika do listy identyfikatorów elementów (PIDL).

```
int GetParentItem(
    LPCITEMIDLIST lpidl,
    LPITEMIDLIST& lpidlParent);
```

### <a name="parameters"></a>Parametry

*lpidl*<br/>
podczas Element PIDL, którego element nadrzędny zostanie pobrany.

*lpidlParent*<br/>
określoną Odwołanie do elementu PIDL, w którym metoda będzie przechowywać wynik.

### <a name="return-value"></a>Wartość zwracana

Poziom elementu nadrzędnego PIDL.

### <a name="remarks"></a>Uwagi

Poziom elementu PIDL jest względny dla pulpitu. PIDL pulpitu jest traktowany jako mający poziom 0.

##  <a name="itemfrompath"></a>CShellManager::ItemFromPath

Pobiera wskaźnik do listy identyfikatorów elementów (PIDL) z elementu identyfikowanego przez ścieżkę ciągu.

```
HRESULT ItemFromPath(
    LPCTSTR lpszPath,
    LPITEMIDLIST& pidl);
```

### <a name="parameters"></a>Parametry

*lpszPath*<br/>
podczas Ciąg określający ścieżkę dla elementu.

*pidl*<br/>
określoną Odwołanie do elementu PIDL. Metoda używa tego PIDL do przechowywania wskaźnika do jego wartości zwracanej.

### <a name="return-value"></a>Wartość zwracana

Zwraca NOERROR, jeśli pomyślne; zdefiniowana przez OLE wartość błędu.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
