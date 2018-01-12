---
title: Klasa CShellManager | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3e1e3fcff06b2937df8218ce1ab32b91ddf22a7d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cshellmanager-class"></a>Klasa CShellManager
Implementuje kilka metod, które umożliwiają pracę z wskaźniki do listy identyfikator (PIDLs).  
  
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
|[CShellManager::BrowseForFolder](#browseforfolder)|Wyświetla okno dialogowe, które umożliwia użytkownikowi wybranie folderu powłoki.|  
|[CShellManager::ConcatenateItem](#concatenateitem)|Łączy dwa PIDLs.|  
|[CShellManager::CopyItem](#copyitem)|Tworzy nowy PIDL i kopiuje PIDL dostarczony do niego.|  
|[CShellManager::CreateItem](#createitem)|Tworzy nowy PIDL o określonym rozmiarze.|  
|[CShellManager::FreeItem](#freeitem)|Usuwa podany PIDL.|  
|[CShellManager::GetItemCount](#getitemcount)|Zwraca liczbę elementów w PIDL dostarczony.|  
|[CShellManager::GetItemSize](#getitemsize)|Zwraca rozmiar podany PIDL.|  
|[CShellManager::GetNextItem](#getnextitem)|Zwraca następny element PIDL.|  
|[CShellManager::GetParentItem](#getparentitem)|Pobiera element nadrzędny dostarczonego elementu.|  
|[CShellManager::ItemFromPath](#itemfrompath)|Pobiera PIDL dla elementu identyfikowana na podstawie podanej ścieżki.|  
  
## <a name="remarks"></a>Uwagi  
 Metody `CShellManager` klasy dotyczą wszystkich PIDLs. PIDL jest unikatowym identyfikatorem dla obiekt powłoki.  
  
 Nie należy tworzyć `CShellManager` obiekt ręcznie. Go zostaną utworzone automatycznie w ramach aplikacji. Jednak należy wywołać [CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager) podczas procesu inicjowania aplikacji. Aby uzyskać wskaźnika shell manager dla aplikacji, należy wywołać [CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CShellManager](../../mfc/reference/cshellmanager-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxshellmanager.h  
  
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
 [out]`strOutFolder`  
 Ciąg używany przez metodę do przechowywania ścieżkę do wybranego folderu.  
  
 [in]`pWndParent`  
 Wskaźnik do okna nadrzędnego.  
  
 [in]`lplszInitialFolder`  
 Ciąg, który zawiera folder, który jest domyślnie zaznaczona, gdy zostanie wyświetlone okno dialogowe.  
  
 [in]`lpszTitle`  
 Tytuł okna dialogowego.  
  
 [in]`ulFlags`  
 Flag określając opcje w oknie dialogowym. Zobacz [BROWSEINFO](http://msdn.microsoft.com/library/windows/desktop/bb773205) szczegółowy opis.  
  
 [out]`piFolderImage`  
 Wskaźnik do wartości całkowitej, gdy metoda zapisuje indeks obrazu wybranego folderu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli użytkownik wybierze folder z okna dialogowego; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Gdy ta metoda jest wywoływana, aplikacja tworzy i wyświetla okno dialogowe, które umożliwia użytkownikowi wybranie folderu. Metoda zapisze ścieżkę folderu w `strOutFolder` parametru.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak pobrać odwołanie do `CShellManager` obiektu za pomocą `CWinAppEx::GetShellManager` — metoda i sposobu użycia `BrowseForFolder` metody. Następujący fragment kodu jest częścią [przykładowy Eksplorator](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_Explorer#6](../../mfc/reference/codesnippet/cpp/cshellmanager-class_1.cpp)]  
  
##  <a name="concatenateitem"></a>CShellManager::ConcatenateItem  
 Tworzy nową listę zawierającą PIDLs dwa.  
  
```  
LPITEMIDLIST ConcatenateItem(
    LPCITEMIDLIST pidl1,  
    LPCITEMIDLIST pidl2);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pidl1`  
 Pierwszy element.  
  
 [in]`pidl2`  
 Drugi element.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nowego listy element, jeśli funkcja zakończy się powodzeniem, w przeciwnym razie `NULL`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda tworzy nowy [ITEMIDLIST](http://msdn.microsoft.com/library/windows/desktop/bb773321) wystarczająco duże, aby obie zawierają `pidl1` i `pidl2`. Następnie kopiuje `pidl1` i `pidl2` na nową listę.  
  
##  <a name="copyitem"></a>CShellManager::CopyItem  
 Kopiuje listy elementów.  
  
```  
LPITEMIDLIST CopyItem(LPCITEMIDLIST pidlSource);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pidlSource`  
 Oryginalnej listy elementów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nowo utworzonego elementu listy w przypadku powodzenia; w przeciwnym razie `NULL`.  
  
### <a name="remarks"></a>Uwagi  
 Lista nowo utworzonego elementu ma taki sam rozmiar jak listy elementów źródła.  
  
##  <a name="createitem"></a>CShellManager::CreateItem  
 Tworzy nowy PIDL.  
  
```  
LPITEMIDLIST CreateItem(UINT cbSize);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`cbSize`  
 Rozmiar listy elementów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do utworzonego elementu listy w przypadku powodzenia; w przeciwnym razie `NULL`.  
  
##  <a name="cshellmanager"></a>CShellManager::CShellManager  
 Konstruuje `CShellManager` obiektu.  
  
```  
CShellManager();
```  
  
### <a name="remarks"></a>Uwagi  
 W większości przypadków, nie trzeba tworzyć `CShellManager` bezpośrednio. Domyślnie platformę tworzy ją. Aby uzyskać wskaźnik do `CShellManager`, wywołaj [CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager). Jeśli utworzysz `CShellManager` ręcznie, należy go zainicjować z metodą [CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager).  
  
##  <a name="freeitem"></a>CShellManager::FreeItem  
 Usuwa listy elementów.  
  
```  
void FreeItem(LPITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pidl`  
 Listy elementów do usunięcia.  
  
##  <a name="getitemcount"></a>CShellManager::GetItemCount  
 Zwraca liczbę elementów na liście elementów.  
  
```  
UINT GetItemCount(LPCITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pidl`  
 Wskaźnik do listy elementów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów na liście elementów.  
  
##  <a name="getitemsize"></a>CShellManager::GetItemSize  
 Zwraca rozmiar listy elementów.  
  
```  
UINT GetItemSize(LPCITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pidl`  
 Wskaźnik do listy elementów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar listy elementów.  
  
##  <a name="getnextitem"></a>CShellManager::GetNextItem  
 Pobiera element dalej ze wskaźnika do listy (identyfikatorów elementów PIDL).  
  
```  
LPITEMIDLIST GetNextItem(LPCITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pidl`  
 Na liście elementów w celu wykonania iteracji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do następnego elementu na liście.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli istnieje więcej elementów na liście, ta metoda zwraca `NULL`.  
  
##  <a name="getparentitem"></a>CShellManager::GetParentItem  
 Pobiera element nadrzędny wskaźnik do listy (identyfikatorów elementów PIDL).  
  
```  
int GetParentItem(
    LPCITEMIDLIST lpidl,  
    LPITEMIDLIST& lpidlParent);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpidl`  
 PIDL, których elementem nadrzędnym zostaną pobrane.  
  
 [out]`lpidlParent`  
 Odwołanie do PIDL, na której metoda będzie przechowywać wynik.  
  
### <a name="return-value"></a>Wartość zwracana  
 Poziom elementu nadrzędnego PIDL.  
  
### <a name="remarks"></a>Uwagi  
 Poziom PIDL jest określana względem pulpitu. Pulpitu PIDL została uznana za poziom 0.  
  
##  <a name="itemfrompath"></a>CShellManager::ItemFromPath  
 Pobiera wskaźnik do listy (identyfikatorów elementów PIDL) z elementu identyfikowana na podstawie ciągu ścieżki.  
  
```  
HRESULT ItemFromPath(
    LPCTSTR lpszPath,  
    LPITEMIDLIST& pidl);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszPath`  
 Ciąg, który określa ścieżkę do elementu.  
  
 [out]`pidl`  
 Odwołanie do PIDL. Metoda używa tego PIDL do przechowywania wskaźnik do jego wartości zwracanej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `NOERROR` w przypadku powodzenia; wartość zdefiniowana OLE błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)
