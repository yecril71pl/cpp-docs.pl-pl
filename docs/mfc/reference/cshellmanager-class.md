---
title: Klasa CShellManager | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1476a59e482cb2ec88b57e4b1b83f5a45afc3790
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426929"
---
# <a name="cshellmanager-class"></a>Klasa CShellManager

Implementuje kilka metod, które umożliwiają użytkownikowi pracować ze wskaźnikami do list identyfikatorów (PIDLs).

## <a name="syntax"></a>Składnia

```
class CShellManager : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CShellManager::CShellManager](#cshellmanager)|Konstruuje `CShellManager` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CShellManager::BrowseForFolder](#browseforfolder)|Wyświetlane jest okno dialogowe, który umożliwia użytkownikowi wybranie folderu powłoki.|
|[CShellManager::ConcatenateItem](#concatenateitem)|Łączy dwa PIDLs.|
|[CShellManager::CopyItem](#copyitem)|Tworzy nowy PIDL i kopiuje PIDL dostarczony do niego.|
|[CShellManager::CreateItem](#createitem)|Tworzy nowy PIDL o określonym rozmiarze.|
|[CShellManager::FreeItem](#freeitem)|Usuwa podany PIDL.|
|[CShellManager::GetItemCount](#getitemcount)|Zwraca liczbę elementów w podanej PIDL.|
|[CShellManager::GetItemSize](#getitemsize)|Zwraca rozmiar PIDL podane.|
|[CShellManager::GetNextItem](#getnextitem)|Zwraca następny element PIDL.|
|[CShellManager::GetParentItem](#getparentitem)|Pobiera element nadrzędny elementu podane.|
|[CShellManager::ItemFromPath](#itemfrompath)|Pobiera PIDL dla elementu identyfikowane przez podana ścieżka.|

## <a name="remarks"></a>Uwagi

Metody `CShellManager` klasy dotyczą wszystkich PIDLs. PIDL jest unikatowy identyfikator obiektu powłoki.

Nie należy tworzyć `CShellManager` obiektu ręcznie. Zostanie on utworzony automatycznie przez strukturę aplikacji. Jednakże, należy wywołać [CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager) podczas procesu inicjowania aplikacji. Aby uzyskać wskaźnik do Menedżera powłoki aplikacji, należy wywołać [CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CShellManager](../../mfc/reference/cshellmanager-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxshellmanager.h

##  <a name="browseforfolder"></a>  CShellManager::BrowseForFolder

Wyświetlane jest okno dialogowe, który umożliwia użytkownikowi wybranie folderu powłoki.

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
[out] Ciąg używany przez metodę do przechowywania ścieżka do wybranego folderu.

*pWndParent*<br/>
[in] Wskaźnik do okna nadrzędnego.

*lplszInitialFolder*<br/>
[in] Ciąg, który zawiera folder, który jest domyślnie wybierany, gdy zostanie wyświetlone okno dialogowe.

*lpszTitle*<br/>
[in] Tytuł okna dialogowego.

*ulFlags*<br/>
[in] Flagi określające opcje dla okna dialogowego. Zobacz [BROWSEINFO](/windows/desktop/api/shlobj_core/ns-shlobj_core-_browseinfoa) szczegółowy opis.

*piFolderImage*<br/>
[out] Wskaźnik do wartości całkowitej, gdzie metoda zapisuje indeks obrazu wybranego folderu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli użytkownik wybierze folder, w oknie dialogowym. w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli chcesz wywołać tę metodę, aplikacja tworzy i wyświetla okno dialogowe, który umożliwia użytkownikowi wybrać folder. Metoda zapisze ścieżkę do folderu *strOutFolder* parametru.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak pobrać odwołanie do `CShellManager` obiektu za pomocą `CWinAppEx::GetShellManager` metody i sposobu używania `BrowseForFolder` metody. Ten fragment kodu jest częścią [Eksplorator kondycji](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#6](../../mfc/reference/codesnippet/cpp/cshellmanager-class_1.cpp)]

##  <a name="concatenateitem"></a>  CShellManager::ConcatenateItem

Tworzy nową listę zawierającą dwa PIDLs.

```
LPITEMIDLIST ConcatenateItem(
    LPCITEMIDLIST pidl1,
    LPCITEMIDLIST pidl2);
```

### <a name="parameters"></a>Parametry

*pidl1*<br/>
[in] Pierwszy element.

*pidl2*<br/>
[in] Drugi element.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowej listy elementów, jeśli funkcja się powiedzie, w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Ta metoda tworzy nowy [ITEMIDLIST](/windows/desktop/api/shtypes/ns-shtypes-_itemidlist) wystarczająco duży, aby zawierać równocześnie *pidl1* i *pidl2*. Następnie kopiuje *pidl1* i *pidl2* do nowej listy.

##  <a name="copyitem"></a>  CShellManager::CopyItem

Kopiuje listy elementów.

```
LPITEMIDLIST CopyItem(LPCITEMIDLIST pidlSource);
```

### <a name="parameters"></a>Parametry

*pidlSource*<br/>
[in] Oryginalna lista elementów.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowo utworzonego elementu listy, jeśli to się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Lista nowo utworzony element ma taki sam rozmiar jak listy elementów źródła.

##  <a name="createitem"></a>  CShellManager::CreateItem

Tworzy nowy PIDL.

```
LPITEMIDLIST CreateItem(UINT cbSize);
```

### <a name="parameters"></a>Parametry

*elementu cbSize*<br/>
[in] Rozmiar listy elementów.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do listy utworzonego elementu, jeśli to się powiedzie; w przeciwnym razie wartość NULL.

##  <a name="cshellmanager"></a>  CShellManager::CShellManager

Konstruuje `CShellManager` obiektu.

```
CShellManager();
```

### <a name="remarks"></a>Uwagi

W większości przypadków nie trzeba tworzyć `CShellManager` bezpośrednio. Domyślnie struktura utworzy go dla Ciebie. Aby uzyskać wskaźnik do `CShellManager`, wywołaj [CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager). Jeśli tworzysz `CShellManager` ręcznie, należy go zainicjować za pomocą metody [CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager).

##  <a name="freeitem"></a>  CShellManager::FreeItem

Usuwa listy elementów.

```
void FreeItem(LPITEMIDLIST pidl);
```

### <a name="parameters"></a>Parametry

*PIDL*<br/>
[in] Listy elementów do usunięcia.

##  <a name="getitemcount"></a>  CShellManager::GetItemCount

Zwraca liczbę elementów na liście elementów.

```
UINT GetItemCount(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parametry

*PIDL*<br/>
[in] Wskaźnik do listy elementów.

### <a name="return-value"></a>Wartość zwracana

Liczba elementów na liście elementów.

##  <a name="getitemsize"></a>  CShellManager::GetItemSize

Zwraca rozmiar listy elementów.

```
UINT GetItemSize(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parametry

*PIDL*<br/>
[in] Wskaźnik do listy elementów.

### <a name="return-value"></a>Wartość zwracana

Rozmiar listy elementów.

##  <a name="getnextitem"></a>  CShellManager::GetNextItem

Pobiera następny element ze wskaźnika do listy (identyfikatorów elementów PIDL).

```
LPITEMIDLIST GetNextItem(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parametry

*PIDL*<br/>
[in] Lista elementów do iteracji.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do następnego elementu na liście.

### <a name="remarks"></a>Uwagi

Jeśli istnieje więcej elementów na liście, ta metoda zwraca wartość NULL.

##  <a name="getparentitem"></a>  CShellManager::GetParentItem

Pobiera element nadrzędny wskaźnik do listy (identyfikatorów elementów PIDL).

```
int GetParentItem(
    LPCITEMIDLIST lpidl,
    LPITEMIDLIST& lpidlParent);
```

### <a name="parameters"></a>Parametry

*lpidl*<br/>
[in] PIDL, których elementem nadrzędnym, które mają zostać pobrane.

*lpidlParent*<br/>
[out] Odwołanie do PIDL, której metody będą przechowywać wynik.

### <a name="return-value"></a>Wartość zwracana

Poziom elementu nadrzędnego PIDL.

### <a name="remarks"></a>Uwagi

Poziom PIDL jest określana względem pulpitu. Aby uzyskać odpowiedni poziom 0 uznaje się PIDL pulpitu.

##  <a name="itemfrompath"></a>  CShellManager::ItemFromPath

Pobiera wskaźnik do listy (identyfikatorów elementów PIDL) z elementu identyfikowane przez ciąg ścieżki.

```
HRESULT ItemFromPath(
    LPCTSTR lpszPath,
    LPITEMIDLIST& pidl);
```

### <a name="parameters"></a>Parametry

*lpszPath*<br/>
[in] Ciąg, który określa ścieżkę do elementu.

*PIDL*<br/>
[out] Odwołanie do PIDL. Metoda używa tego PIDL do przechowywania wskaźnika do wartości zwracanej.

### <a name="return-value"></a>Wartość zwracana

Zwraca brak błędu, jeśli to się powiedzie; wartość błędu zdefiniowany OLE.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
