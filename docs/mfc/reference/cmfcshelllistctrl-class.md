---
title: Klasa CMFCShellListCtrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b2ae5b321ce9de1e834119e764a65df638d97e10
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721191"
---
# <a name="cmfcshelllistctrl-class"></a>Klasa CMFCShellListCtrl
`CMFCShellListCtrl` Klasa oferuje funkcję formantu listy Windows i rozszerza ją przez uwzględnienie możliwości wyświetlenia listy elementów powłoki.  
  
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
|[CMFCShellListCtrl::GetCurrentFolder](#getcurrentfolder)|Pobiera ścieżkę bieżącego folderu.|  
|[CMFCShellListCtrl::GetCurrentFolderName](#getcurrentfoldername)|Pobiera nazwę bieżącego folderu.|  
|[CMFCShellListCtrl::GetCurrentItemIdList](#getcurrentitemidlist)|Zwraca PIDL do bieżącego elementu listy kontroli.|  
|[CMFCShellListCtrl::GetCurrentShellFolder](#getcurrentshellfolder)|Zwraca wskaźnik do bieżącego folderu powłoki.|  
|[CMFCShellListCtrl::GetItemPath](#getitempath)|Zwraca ścieżkę tekstowej elementu.|  
|[CMFCShellListCtrl::GetItemTypes](#getitemtypes)|Zwraca typy elementów powłoki, które są wyświetlane przez formant listy.|  
|[CMFCShellListCtrl::IsDesktop](#isdesktop)|Sprawdza, czy aktualnie wybranego folderu w folderze pulpit.|  
|[CMFCShellListCtrl::OnCompareItems](#oncompareitems)|Struktura wywołuje tę metodę do porównywania dwóch elementów. (Przesłania [CMFCListCtrl::OnCompareItems](../../mfc/reference/cmfclistctrl-class.md#oncompareitems).)|  
|[CMFCShellListCtrl::OnFormatFileDate](#onformatfiledate)|Wywołuje się, gdy w ramach pobiera datę plik wyświetlany przez kontrolkę listy.|  
|[CMFCShellListCtrl::OnFormatFileSize](#onformatfilesize)|Wywołuje się, gdy w ramach konwertuje rozmiar kontrolki listy.|  
|[CMFCShellListCtrl::OnGetItemIcon](#ongetitemicon)|Wywołuje się, gdy w ramach pobiera ikonę element formantu listy.|  
|[CMFCShellListCtrl::OnGetItemText](#ongetitemtext)|Wywołuje się, gdy w ramach konwertuje tekst element formantu listy.|  
|[CMFCShellListCtrl::OnSetColumns](#onsetcolumns)|Wywoływane przez platformę, gdy ustawia nazwy kolumn.|  
|[CMFCShellListCtrl::Refresh](#refresh)|Odświeża i odświeża kontrolki listy.|  
|[CMFCShellListCtrl::SetItemTypes](#setitemtypes)|Ustawia typ elementów wyświetlanych przez kontrolki listy.|  
  
## <a name="remarks"></a>Uwagi  
 `CMFCShellListCtrl` Klasa rozszerza funkcjonalność [klasa CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md) przez włączenie programu Windows shell elementy listy. Format wyświetlania, która jest używana jest podobne do widoku listy do okna Eksploratora.  
  
 A [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) obiekt może być skojarzony z `CMFCShellListCtrl` obiekt, aby utworzyć pełną okno Eksploratora. Następnie, wybierając element `CMFCShellTreeCtrl` spowoduje, że `CMFCShellListCtrl` obiektu, aby wyświetlić listę zawartości wybranego elementu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób tworzenia obiektu `CMFCShellListCtrl` klasy i sposób wyświetlania folderu nadrzędnego obecnie wyświetlany folderu. Ten fragment kodu jest częścią [Eksplorator kondycji](../../visual-cpp-samples.md).  
  
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
 **Nagłówek:** afxshelllistCtrl.h  
  
##  <a name="displayfolder"></a>  CMFCShellListCtrl::DisplayFolder  
 Wyświetla listę elementów, które znajdują się w folderze podana.  
  
```  
virtual HRESULT DisplayFolder(LPCTSTR lpszPath);
virtual HRESULT DisplayFolder(LPAFX_SHELLITEMINFO lpItemInfo);
```  
  
### <a name="parameters"></a>Parametry  
*lpszPath*<br/>
[in] Ciąg, który zawiera ścieżkę do folderu.  
  
*lpItemInfo*<br/>
[in] Wskaźnik do `LPAFX_SHELLITEMINFO` strukturę, która opisuje folder, aby wyświetlić.  
  
### <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; W przeciwnym razie E_FAIL.  
  
##  <a name="displayparentfolder"></a>  CMFCShellListCtrl::DisplayParentFolder  
 Aktualizacje [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiektu, aby wyświetlić folder nadrzędny folder aktualnie wyświetlany.  
  
```  
virtual HRESULT DisplayParentFolder();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; W przeciwnym razie E_FAIL.  
  
##  <a name="enableshellcontextmenu"></a>  CMFCShellListCtrl::EnableShellContextMenu  
 Umożliwia menu skrótów.  
  
```  
void EnableShellContextMenu(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
*bWłączenie*<br/>
[in] Wartość logiczna określająca, czy struktura umożliwia menu skrótów.  
  
##  <a name="getcurrentfolder"></a>  CMFCShellListCtrl::GetCurrentFolder  
 Pobiera ścieżkę do aktualnie wybranego folderu w [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiektu.  
  
```  
BOOL GetCurrentFolder(CString& strPath) const;  
```  
  
### <a name="parameters"></a>Parametry  
*strPath*<br/>
[out] Odwołanie do parametru ciągu, którego metoda zapisuje ścieżki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda kończy się niepowodzeniem, jeśli żaden folder wybrany w `CMFCShellListCtrl`.  
  
##  <a name="getcurrentfoldername"></a>  CMFCShellListCtrl::GetCurrentFolderName  
 Pobiera nazwę aktualnie wybranego folderu w [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiektu.  
  
```  
BOOL GetCurrentFolderName(CString& strName) const;  
```  
  
### <a name="parameters"></a>Parametry  
*strName*<br/>
[out] Odwołanie do parametru ciągu, którego metoda zapisuje nazwę.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda kończy się niepowodzeniem, jeśli żaden folder wybrany w `CMFCShellListCtrl`.  
  
##  <a name="getcurrentitemidlist"></a>  CMFCShellListCtrl::GetCurrentItemIdList  
 Zwraca PIDL aktualnie wybranego elementu.  
  
```  
LPITEMIDLIST GetCurrentItemIdList() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 PIDL bieżącego elementu.  
  
##  <a name="getcurrentshellfolder"></a>  CMFCShellListCtrl::GetCurrentShellFolder  
 Pobiera wskaźnik do aktualnie wybranego elementu w [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiektu.  
  
```  
const IShellFolder* GetCurrentShellFolder() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [interfejsu IShellFolder](https://msdn.microsoft.com/library/windows/desktop/bb775075) dla wybranego obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca wartość NULL, jeśli żaden obiekt nie jest aktualnie wybrany.  
  
##  <a name="getitempath"></a>  CMFCShellListCtrl::GetItemPath  
 Pobiera ścieżkę dla elementu.  
  
```  
BOOL GetItemPath(
    CString& strPath,  
    int iItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
*strPath*<br/>
[out] Odwołanie do ciągu, który odbiera ścieżki.  
  
*Towaru*<br/>
[in] Indeks elementu listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli to się powiedzie; Wartość FALSE w przeciwnym razie.  
  
### <a name="remarks"></a>Uwagi  
 Indeks dostarczony przez *towaru* opiera się na elementach wyświetlanych przez [klasa CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiektu.  
  
##  <a name="getitemtypes"></a>  CMFCShellListCtrl::GetItemTypes  
 Zwraca typ elementów wyświetlanych przez [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiektu.  
  
```  
SHCONTF GetItemTypes() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [SHCONTF](/windows/desktop/api/shobjidl_core/ne-shobjidl_core-_shcontf) wartość, która zawiera typ elementów na liście `CMFCShellListCtrl`.  
  
### <a name="remarks"></a>Uwagi  
 Aby ustawić automatyczny typ elementów na liście `CMFCShellListCtrl`, wywołaj [CMFCShellListCtrl::SetItemTypes](#setitemtypes).  
  
##  <a name="isdesktop"></a>  CMFCShellListCtrl::IsDesktop  
 Określa, czy folder, jest wyświetlany w [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiekt znajduje się w folderze pulpit.  
  
```  
BOOL IsDesktop() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli folder wyświetlany jest folder Pulpit; Wartość FALSE w przeciwnym razie.  
  
##  <a name="oncompareitems"></a>  CMFCShellListCtrl::OnCompareItems  
 Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.  
  
```  
virtual int OnCompareItems(
    LPARAM lParam1,  
    LPARAM lParam2,  
    int iColumn);
```  
  
### <a name="parameters"></a>Parametry  
*lParam1*<br/>
[in] [in] *lParam2*  
 [in] *iColumn*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onformatfiledate"></a>  CMFCShellListCtrl::OnFormatFileDate  
 Struktura wywołuje tę metodę, gdy muszą być konwertowane datę skojarzoną z obiektem w ciąg.  
  
```  
virtual void OnFormatFileDate(
    const CTime& tmFile,  
    CString& str);
```  
  
### <a name="parameters"></a>Parametry  
*tmFile*<br/>
[in] Data skojarzonych z plikiem.  
  
*str*<br/>
[out] Ciąg, który zawiera datę sformatowanym plikiem.  
  
### <a name="remarks"></a>Uwagi  
 Gdy [klasa CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiekt wyświetla datę skojarzonych z plikiem, przekonwertuj tej daty do formatu ciągu. `CMFCShellListCtrl` Używa tej metody, aby tej konwersji. Domyślnie ta metoda używa bieżących ustawień regionalnych do formatowania daty w ciągu.  
  
##  <a name="onformatfilesize"></a>  CMFCShellListCtrl::OnFormatFileSize  
 Struktura wywołuje tę metodę, gdy konwertuje rozmiar obiektu na ciąg.  
  
```  
virtual void OnFormatFileSize(
    long lFileSize,  
    CString& str);
```  
  
### <a name="parameters"></a>Parametry  
*lFileSize*<br/>
[in] Rozmiar pliku który będzie wyświetlany w ramach.  
  
*str*<br/>
[out] Ciąg, który zawiera rozmiar sformatowanym plikiem.  
  
### <a name="remarks"></a>Uwagi  
 Gdy [klasa CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiektu wymaganych, aby wyświetlić rozmiar pliku, należy ją przekonwertować rozmiar pliku w formacie ciągu. `CMFCShellListCtrl` Używa tej metody, aby tej konwersji. Domyślnie ta metoda konwertuje rozmiar pliku w bajtach na kilobajtów, a następnie używa bieżących ustawień regionalnych w celu sformatowania rozmiar jako ciąg.  
  
##  <a name="ongetitemicon"></a>  CMFCShellListCtrl::OnGetItemIcon  
 Struktura wywołuje tę metodę w celu pobrania ikony skojarzone z elementem listy powłoki.  
  
```  
virtual int OnGetItemIcon(
    int iItem,  
    LPAFX_SHELLITEMINFO pItem);
```  
  
### <a name="parameters"></a>Parametry  
*Towaru*<br/>
[in] Indeks elementu.  
  
*pItem*<br/>
[in] Parametr LPAFX_SHELLITEMINFO, który zawiera opis elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks obrazu ikony, jeśli to się powiedzie; -1, jeśli funkcja kończy się niepowodzeniem.  
  
### <a name="remarks"></a>Uwagi  
 Indeks obrazu ikony opiera się na liście obrazu systemu.  
  
 Domyślnie ta metoda polega na *pItem* parametru. Wartość *towaru* nie jest używana domyślna implementacja. Możesz użyć *towaru* do zaimplementowania niestandardowe zachowanie.  
  
##  <a name="ongetitemtext"></a>  CMFCShellListCtrl::OnGetItemText  
 Struktura wywołuje tę metodę, gdy tekst elementu powłoki muszą zostać pobrane.  
  
```  
virtual CString OnGetItemText(
    int iItem,  
    int iColumn,  
    LPAFX_SHELLITEMINFO pItem);
```  
  
### <a name="parameters"></a>Parametry  
*Towaru*<br/>
[in] Indeks elementu.  
  
*iColumn*<br/>
[in] Kolumna zainteresowania.  
  
*pItem*<br/>
[in] Parametr LPAFX_SHELLITEMINFO, który zawiera opis elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Element `CString` zawierający tekst skojarzony z elementem.  
  
### <a name="remarks"></a>Uwagi  
 Każdy element na `CMFCShellListCtrl` obiekt może mieć tekstu w co najmniej jedną kolumnę. Gdy struktura wywołuje tę metodę, określa kolumnę, która jest zainteresowany. Jeśli chcesz ręcznie wywołać tę funkcję, należy także określić kolumnę, która Cię interesuje.  
  
 Domyślnie ta metoda polega na *pItem* parametru do określenia, który element do procesu. Wartość *towaru* nie jest używana domyślna implementacja.  
  
##  <a name="onsetcolumns"></a>  CMFCShellListCtrl::OnSetColumns  
 Struktura wywołuje tę metodę, gdy ustawia nazwy kolumn.  
  
```  
virtual void OnSetColumns();
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie szablon tworzy cztery kolumny w `CMFCShellListCtrl` obiektu. Nazwy te kolumny są **nazwa**, **rozmiar**, **typu**, i **zmodyfikowane**. Można zastąpić tę metodę, aby dostosować liczbę kolumn i ich nazw.  
  
##  <a name="refresh"></a>  CMFCShellListCtrl::Refresh  
 Odświeża i odświeża [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiektu.  
  
```  
virtual HRESULT Refresh();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `S_OK` Jeśli to się powiedzie; w przeciwnym razie wartość błędu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby odświeżyć listę elementów wyświetlanych przez `CMFCShellListCtrl` obiektu.  
  
##  <a name="setitemtypes"></a>  CMFCShellListCtrl::SetItemTypes  
 Ustawia typ elementów, które są wymienione w [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiektu.  
  
```  
void SetItemTypes(SHCONTF nTypes);
```  
  
### <a name="parameters"></a>Parametry  
*nTypes*<br/>
[in] Lista elementów typy, które `CMFCShellListCtrl` obiekt obsługuje.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji dotyczących listy typów elementów, zobacz [SHCONTF](/windows/desktop/api/shobjidl_core/ne-shobjidl_core-_shcontf).  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)   
 [Klasa CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)
