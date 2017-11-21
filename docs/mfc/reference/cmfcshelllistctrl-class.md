---
title: Klasa CMFCShellListCtrl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 455ac8911e99843c14cdab80a6c97e243259c5a6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cmfcshelllistctrl-class"></a>Klasa CMFCShellListCtrl
`CMFCShellListCtrl` Klasa udostępnia funkcje sterowania listy systemu Windows i rozszerza się przy tym możliwość wyświetlania listy elementów powłoki.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCShellListCtrl : public CMFCListCtrl  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCShellListCtrl::DisplayFolder](#displayfolder)|Wyświetla listę elementów, które znajdują się w folderze podana.|  
|[CMFCShellListCtrl::DisplayParentFolder](#displayparentfolder)|Wyświetla listę elementów, które znajdują się w folderze, który jest elementem nadrzędnym folderu aktualnie wyświetlany.|  
|[CMFCShellListCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Włącza lub wyłącza menu skrótów.|  
|[CMFCShellListCtrl::GetCurrentFolder](#getcurrentfolder)|Pobiera ścieżkę do bieżącego folderu.|  
|[CMFCShellListCtrl::GetCurrentFolderName](#getcurrentfoldername)|Pobiera nazwę bieżącego folderu.|  
|[CMFCShellListCtrl::GetCurrentItemIdList](#getcurrentitemidlist)|Zwraca PIDL bieżącego elementu kontrolki listy.|  
|[CMFCShellListCtrl::GetCurrentShellFolder](#getcurrentshellfolder)|Zwraca wskaźnik do bieżącego folderu powłoki.|  
|[CMFCShellListCtrl::GetItemPath](#getitempath)|Zwraca ścieżkę tekstowej elementu.|  
|[CMFCShellListCtrl::GetItemTypes](#getitemtypes)|Zwraca typy elementów powłoki, które są wyświetlane przez formant listy.|  
|[CMFCShellListCtrl::IsDesktop](#isdesktop)|Sprawdza, czy obecnie wybrany folder jest folderze pulpit.|  
|[CMFCShellListCtrl::OnCompareItems](#oncompareitems)|Struktura wywołuje tę metodę do porównywania dwóch elementów. (Przesłania [CMFCListCtrl::OnCompareItems](../../mfc/reference/cmfclistctrl-class.md#oncompareitems).)|  
|[CMFCShellListCtrl::OnFormatFileDate](#onformatfiledate)|Wywoływane, gdy w ramach pobiera Data pliku wyświetlany przez formant listy.|  
|[CMFCShellListCtrl::OnFormatFileSize](#onformatfilesize)|Wywoływane, gdy w ramach konwertuje rozmiar kontrolki listy.|  
|[CMFCShellListCtrl::OnGetItemIcon](#ongetitemicon)|Wywoływana, gdy w ramach pobiera ikonę elementu kontrolki listy.|  
|[CMFCShellListCtrl::OnGetItemText](#ongetitemtext)|Wywoływane, gdy w ramach konwertuje tekst elementu kontrolki listy.|  
|[CMFCShellListCtrl::OnSetColumns](#onsetcolumns)|Wywoływane przez platformę, gdy ustawia nazwy kolumn.|  
|[CMFCShellListCtrl::Refresh](#refresh)|Odświeża i odświeża kontrolki listy.|  
|[CMFCShellListCtrl::SetItemTypes](#setitemtypes)|Ustawia typ wyświetlanego przez formant listy elementów.|  
  
## <a name="remarks"></a>Uwagi  
 `CMFCShellListCtrl` Klasa rozszerza funkcjonalność [klasy CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md) przez włączenie programu Windows shell elementy listy. Format wyświetlania, która jest używana przypomina elementu widoku listy dla okna Eksploratora.  
  
 A [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) obiekt może być skojarzony z `CMFCShellListCtrl` obiekt, aby utworzyć pełną okno Eksploratora. Wybierając element `CMFCShellTreeCtrl` spowoduje, że `CMFCShellListCtrl` obiektu na wyświetlanie zawartości wybranego elementu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób tworzenia obiektu `CMFCShellListCtrl` klasy i sposób wyświetlania folderu nadrzędnego folderu aktualnie wyświetlany. Następujący fragment kodu jest częścią [przykładowy Eksplorator](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_Explorer#1](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_1.h)]  
[!code-cpp[NVC_MFC_Explorer#2](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_2.cpp)]  
[!code-cpp[NVC_MFC_Explorer#3](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_3.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListCtrl](../../mfc/reference/clistctrl-class.md)  
  
 [CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)  
  
 `CMFCShellListCtrl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxshelllistCtrl.h  
  
##  <a name="displayfolder"></a>CMFCShellListCtrl::DisplayFolder  
 Wyświetla listę elementów, które znajdują się w folderze podana.  
  
```  
virtual HRESULT DisplayFolder(LPCTSTR lpszPath);
virtual HRESULT DisplayFolder(LPAFX_SHELLITEMINFO lpItemInfo);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszPath`  
 Ciąg, który zawiera ścieżkę do folderu.  
  
 [in]`lpItemInfo`  
 Wskaźnik do `LPAFX_SHELLITEMINFO` strukturę, która opisuje folderu do wyświetlenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 `S_OK`w przypadku powodzenia; `E_FAIL` inaczej.  
  
##  <a name="displayparentfolder"></a>CMFCShellListCtrl::DisplayParentFolder  
 Aktualizacje [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiektu do wyświetlenia folderu nadrzędnego folderu aktualnie wyświetlany.  
  
```  
virtual HRESULT DisplayParentFolder();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `S_OK`w przypadku powodzenia; `E_FAIL` inaczej.  
  
##  <a name="enableshellcontextmenu"></a>CMFCShellListCtrl::EnableShellContextMenu  
 Umożliwia menu skrótów.  
  
```  
void EnableShellContextMenu(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bEnable`  
 Wartość logiczna określająca, czy struktura umożliwia menu skrótów.  
  
##  <a name="getcurrentfolder"></a>CMFCShellListCtrl::GetCurrentFolder  
 Pobiera ścieżkę folderu aktualnie wybranego w [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiektu.  
  
```  
BOOL GetCurrentFolder(CString& strPath) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`strPath`  
 Odwołanie do parametr typu string, którego metoda zapisuje ścieżki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zakończy się niepowodzeniem, jeśli żaden folder wybrany w `CMFCShellListCtrl`.  
  
##  <a name="getcurrentfoldername"></a>CMFCShellListCtrl::GetCurrentFolderName  
 Pobiera nazwę aktualnie wybrany folder w [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiektu.  
  
```  
BOOL GetCurrentFolderName(CString& strName) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`strName`  
 Odwołanie do parametr typu string, gdy metoda zapisuje nazwy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zakończy się niepowodzeniem, jeśli żaden folder wybrany w `CMFCShellListCtrl`.  
  
##  <a name="getcurrentitemidlist"></a>CMFCShellListCtrl::GetCurrentItemIdList  
 Zwraca PIDL obecnie wybranego elementu.  
  
```  
LPITEMIDLIST GetCurrentItemIdList() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 PIDL bieżącego elementu.  
  
##  <a name="getcurrentshellfolder"></a>CMFCShellListCtrl::GetCurrentShellFolder  
 Pobiera wskaźnik do aktualnie zaznaczonego elementu [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiektu.  
  
```  
const IShellFolder* GetCurrentShellFolder() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [IShellFolder interfejsu](http://msdn.microsoft.com/library/windows/desktop/bb775075) dla wybranego obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca `NULL` Jeśli żaden obiekt nie jest aktualnie zaznaczony.  
  
##  <a name="getitempath"></a>CMFCShellListCtrl::GetItemPath  
 Pobiera ścieżkę dla elementu.  
  
```  
BOOL GetItemPath(
    CString& strPath,  
    int iItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`strPath`  
 Odwołanie do ciąg, który odbiera ścieżki.  
  
 [in]`iItem`  
 Indeks elementu listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`w przypadku powodzenia; `FALSE` inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Indeks dostarczony przez `iItem` jest oparta na elementach wyświetlanych przez [klasy CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiektu.  
  
##  <a name="getitemtypes"></a>CMFCShellListCtrl::GetItemTypes  
 Zwraca typ elementów wyświetlanych przez [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiektu.  
  
```  
SHCONTF GetItemTypes() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [SHCONTF](http://msdn.microsoft.com/library/windows/desktop/bb762539) wartości zawierającej typ elementów na liście `CMFCShellListCtrl`.  
  
### <a name="remarks"></a>Uwagi  
 Aby ustawić typ elementów na liście `CMFCShellListCtrl`, wywołaj [CMFCShellListCtrl::SetItemTypes](#setitemtypes).  
  
##  <a name="isdesktop"></a>CMFCShellListCtrl::IsDesktop  
 Określa, czy folder, który jest wyświetlany w [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiekt znajduje się w folderze pulpit.  
  
```  
BOOL IsDesktop() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`w przypadku folderu wyświetlane folderze pulpitu; `FALSE` inaczej.  
  
##  <a name="oncompareitems"></a>CMFCShellListCtrl::OnCompareItems  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int OnCompareItems(
    LPARAM lParam1,  
    LPARAM lParam2,  
    int iColumn);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lParam1`  
 [in]`lParam2`  
 [in]`iColumn`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onformatfiledate"></a>CMFCShellListCtrl::OnFormatFileDate  
 Platformę wywołuje tę metodę, gdy należy przekonwertować daty skojarzona z obiektem na ciąg.  
  
```  
virtual void OnFormatFileDate(
    const CTime& tmFile,  
    CString& str);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`tmFile`  
 Data skojarzonych z plikiem.  
  
 [out]`str`  
 Ciąg, który zawiera datę sformatowanym plikiem.  
  
### <a name="remarks"></a>Uwagi  
 Gdy [klasy CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiektu Wyświetla datę skojarzonych z plikiem, przekonwertuj Data w formacie ciągu. `CMFCShellListCtrl` Używana tej metody, aby zapewnić tym konwersji. Domyślnie ta metoda używa bieżące ustawienia regionalne do formatowania daty na ciąg.  
  
##  <a name="onformatfilesize"></a>CMFCShellListCtrl::OnFormatFileSize  
 Struktura wywołuje tę metodę, podczas konwertowania rozmiar obiektu na ciąg.  
  
```  
virtual void OnFormatFileSize(
    long lFileSize,  
    CString& str);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lFileSize`  
 Rozmiar pliku, która będzie wyświetlana w ramach.  
  
 [out]`str`  
 Ciąg, który zawiera rozmiar sformatowanym plikiem.  
  
### <a name="remarks"></a>Uwagi  
 Gdy [CMFCShellListCtrl klasy](../../mfc/reference/cmfcshelllistctrl-class.md) wymaga obiektu do wyświetlenia rozmiar pliku, należy go przekonwertować rozmiar pliku w formacie ciągu. `CMFCShellListCtrl` Używana tej metody, aby zapewnić tym konwersji. Domyślnie ta metoda konwertuje rozmiar pliku w bajtach na kilobajtów i następnie używa bieżące ustawienia regionalne sformatował rozmiar do ciągu.  
  
##  <a name="ongetitemicon"></a>CMFCShellListCtrl::OnGetItemIcon  
 Struktura wywołuje tę metodę w celu pobrania ikon skojarzonych z elementu listy powłoki.  
  
```  
virtual int OnGetItemIcon(
    int iItem,  
    LPAFX_SHELLITEMINFO pItem);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`iItem`  
 Indeks elementu.  
  
 [in]`pItem`  
 A `LPAFX_SHELLITEMINFO` parametr, który zawiera opis elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks obrazu ikony w przypadku powodzenia; -1, jeśli funkcja nie powiedzie się.  
  
### <a name="remarks"></a>Uwagi  
 Indeks obrazu ikony opiera się na liście obrazu systemu.  
  
 Domyślnie ta metoda polega na `pItem` parametru. Wartość `iItem` nie jest używany w implementacji domyślnej. Można użyć `iItem` do zaimplementowania niestandardowego zachowania.  
  
##  <a name="ongetitemtext"></a>CMFCShellListCtrl::OnGetItemText  
 Platformę wywołuje tę metodę, gdy tekst elementu powłoki muszą zostać pobrane.  
  
```  
virtual CString OnGetItemText(
    int iItem,  
    int iColumn,  
    LPAFX_SHELLITEMINFO pItem);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`iItem`  
 Indeks elementu.  
  
 [in]`iColumn`  
 Kolumna zainteresowań.  
  
 [in]`pItem`  
 A `LPAFX_SHELLITEMINFO` parametr, który zawiera opis elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CString` zawierający tekst skojarzony z elementem.  
  
### <a name="remarks"></a>Uwagi  
 Każdy element `CMFCShellListCtrl` obiekt może mieć tekstu w co najmniej jedną kolumnę. Gdy struktura wywołuje tę metodę, określa kolumny, która jest zainteresowana. Jeśli ręcznie wywołanie tej funkcji, należy także określić kolumnę, którą chcesz.  
  
 Domyślnie ta metoda polega na `pItem` parametr, aby określić, który element do procesu. Wartość `iItem` nie jest używany w implementacji domyślnej.  
  
##  <a name="onsetcolumns"></a>CMFCShellListCtrl::OnSetColumns  
 Struktura wywołuje tę metodę po ustawia nazwy kolumn.  
  
```  
virtual void OnSetColumns();
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie platformę tworzy cztery kolumny w `CMFCShellListCtrl` obiektu. Te kolumny o nazwach `Name`, `Size`, `Type`, i `Modified`. Można zastąpić tę metodę, aby dostosować liczbę kolumn i ich nazw.  
  
##  <a name="refresh"></a>CMFCShellListCtrl::Refresh  
 Odświeża i odświeża [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiektu.  
  
```  
virtual HRESULT Refresh();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `S_OK`w przypadku powodzenia; w przeciwnym razie wartość błędu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody, aby odświeżyć listę elementów wyświetlanych przez `CMFCShellListCtrl` obiektu.  
  
##  <a name="setitemtypes"></a>CMFCShellListCtrl::SetItemTypes  
 Ustawia typ elementów, które są wymienione w [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiektu.  
  
```  
void SetItemTypes(SHCONTF nTypes);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nTypes`  
 Typy listę elementów, które `CMFCShellListCtrl` obiekt obsługuje.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji dotyczących listy typów elementów, zobacz [SHCONTF](http://msdn.microsoft.com/library/windows/desktop/bb762539).  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)   
 [Klasa CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)
