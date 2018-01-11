---
title: Klasa CUserToolsManager | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager::CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager::CreateNewTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::FindTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetArgumentsMenuID
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetDefExt
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetFilter
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetInitialDirMenuID
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetMaxTools
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetToolsEntryCmd
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetUserTools
- AFXUSERTOOLSMANAGER/CUserToolsManager::InvokeTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::IsUserToolCmd
- AFXUSERTOOLSMANAGER/CUserToolsManager::LoadState
- AFXUSERTOOLSMANAGER/CUserToolsManager::MoveToolDown
- AFXUSERTOOLSMANAGER/CUserToolsManager::MoveToolUp
- AFXUSERTOOLSMANAGER/CUserToolsManager::RemoveTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::SaveState
- AFXUSERTOOLSMANAGER/CUserToolsManager::SetDefExt
- AFXUSERTOOLSMANAGER/CUserToolsManager::SetFilter
dev_langs: C++
helpviewer_keywords:
- CUserToolsManager [MFC], CUserToolsManager
- CUserToolsManager [MFC], CreateNewTool
- CUserToolsManager [MFC], FindTool
- CUserToolsManager [MFC], GetArgumentsMenuID
- CUserToolsManager [MFC], GetDefExt
- CUserToolsManager [MFC], GetFilter
- CUserToolsManager [MFC], GetInitialDirMenuID
- CUserToolsManager [MFC], GetMaxTools
- CUserToolsManager [MFC], GetToolsEntryCmd
- CUserToolsManager [MFC], GetUserTools
- CUserToolsManager [MFC], InvokeTool
- CUserToolsManager [MFC], IsUserToolCmd
- CUserToolsManager [MFC], LoadState
- CUserToolsManager [MFC], MoveToolDown
- CUserToolsManager [MFC], MoveToolUp
- CUserToolsManager [MFC], RemoveTool
- CUserToolsManager [MFC], SaveState
- CUserToolsManager [MFC], SetDefExt
- CUserToolsManager [MFC], SetFilter
ms.assetid: bdfa37ae-efca-4616-abb5-9d0dcd2d335b
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d92e0ffa11ea07331704bfcd91798c50c48dabac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cusertoolsmanager-class"></a>Klasa CUserToolsManager
Zapewnia zbiór [klasy CUserTool](../../mfc/reference/cusertool-class.md) obiektów w aplikacji. Narzędzie użytkownika jest element menu uruchomionym aplikacji zewnętrznej. `CUserToolsManager` Obiektu umożliwia użytkownika lub deweloperem, aby dodać nowe narzędzia użytkownika do aplikacji. Obsługuje wykonywanie polecenia powiązane z narzędzi użytkownika, a także zapisuje informacje o narzędziach użytkownika w rejestrze systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CUserToolsManager : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CUserToolsManager::CUserToolsManager](#cusertoolsmanager)|Konstruuje `CUserToolsManager`.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CUserToolsManager::CreateNewTool](#createnewtool)|Tworzy nowe narzędzie użytkownika.|  
|[CUserToolsManager::FindTool](#findtool)|Zwraca wskaźnik do `CMFCUserTool` obiekt, który jest skojarzony z identyfikatorem określonego polecenia.|  
|[CUserToolsManager::GetArgumentsMenuID](#getargumentsmenuid)|Zwraca identyfikator zasobu, który jest skojarzony z **argumenty** menu **narzędzia** karcie **Dostosuj** okno dialogowe.|  
|[CUserToolsManager::GetDefExt](#getdefext)|Zwraca domyślne rozszerzenie, które **Otwórz plik** okno dialogowe ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) używa w **polecenia** na **narzędzia** karty **Dostosuj** okno dialogowe.|  
|[CUserToolsManager::GetFilter](#getfilter)|Zwraca filtr plików, który **Otwórz plik** okno dialogowe ( [klasy CFileDialog](../../mfc/reference/cfiledialog-class.md)) używa w **polecenia** na **narzędzia** karty **Dostosuj** okno dialogowe.|  
|[CUserToolsManager::GetInitialDirMenuID](#getinitialdirmenuid)|Zwraca identyfikator zasobu, który jest skojarzony z **katalog początkowy** menu **narzędzia** karcie **Dostosuj** okno dialogowe.|  
|[CUserToolsManager::GetMaxTools](#getmaxtools)|Zwraca maksymalną liczbę narzędzi użytkownika, które mogą być przydzielone w aplikacji.|  
|[CUserToolsManager::GetToolsEntryCmd](#gettoolsentrycmd)|Zwraca identyfikator polecenia symbol zastępczy elementu menu dla użytkownika narzędzia.|  
|[CUserToolsManager::GetUserTools](#getusertools)|Zwraca odwołanie do listy użytkownika narzędzia.|  
|[CUserToolsManager::InvokeTool](#invoketool)|Wykonuje aplikacji skojarzonej z narzędziem użytkownika, który ma identyfikator określonego polecenia.|  
|[CUserToolsManager::IsUserToolCmd](#isusertoolcmd)|Określa, czy identyfikator polecenia jest skojarzony z narzędziem do użytkownika.|  
|[CUserToolsManager::LoadState](#loadstate)|Ładuje informacje o narzędziach użytkownika z rejestru systemu Windows.|  
|[CUserToolsManager::MoveToolDown](#movetooldown)|Umożliwia przeniesienie narzędzia określonego użytkownika w dół listę narzędzi użytkownika.|  
|[CUserToolsManager::MoveToolUp](#movetoolup)|Zostanie przesunięty narzędzia określonego użytkownika na liście użytkownika narzędzia.|  
|[CUserToolsManager::RemoveTool](#removetool)|Usuwa określonego użytkownika narzędzia z aplikacji.|  
|[CUserToolsManager::SaveState](#savestate)|Przechowuje informacje dotyczące narzędzi użytkownika w rejestrze systemu Windows.|  
|[CUserToolsManager::SetDefExt](#setdefext)|Określa domyślne rozszerzenie który **Otwórz plik** okno dialogowe ( [klasy CFileDialog](../../mfc/reference/cfiledialog-class.md)) używa w **polecenia** na **narzędzia** kartę z **Dostosuj** okno dialogowe.|  
|[CUserToolsManager::SetFilter](#setfilter)|Określa plik filtru, który **Otwórz plik** okno dialogowe ( [klasy CFileDialog](../../mfc/reference/cfiledialog-class.md)) używa w **polecenia** na **narzędzia** karty **Dostosuj** okno dialogowe.|  
  
## <a name="remarks"></a>Uwagi  
 Aby dołączyć narzędzia użytkownika do aplikacji, należy:  
  
 1. Zarezerwować element menu i identyfikator skojarzone polecenie wpisu menu Narzędzia użytkownika.  
  
 2. Zarezerwować Identyfikatora kolejne polecenia dla narzędzia każdego użytkownika, zdefiniowanego przez użytkownika w aplikacji.  
  
 3. Wywołanie [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) — metoda i podać następujące parametry: menu Identyfikator polecenia, pierwszy identyfikator polecenia narzędzia użytkownika i ostatniego użytkownika narzędzia do identyfikatora polecenia.  
  
 Powinien istnieć tylko jedną globalnego `CUserToolsManager` obiektu na aplikację.  
  
 Na przykład użytkownik narzędzia Zobacz VisualStudioDemo przykładowy projekt.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak pobrać odwołanie do `CUserToolsManager` obiektu oraz sposobu tworzenia nowych narzędzi do użytkownika. Następujący fragment kodu jest częścią [programu Visual Studio przykład](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#38](../../mfc/codesnippet/cpp/cusertoolsmanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CUserToolsManager`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxusertoolsmanager.h  
  
##  <a name="createnewtool"></a>CUserToolsManager::CreateNewTool  
 Tworzy nowe narzędzie użytkownika.  
  
```  
CUserTool* CreateNewTool();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do narzędzia nowo utworzonego użytkownika lub `NULL` jeśli przekracza maksymalną liczbę narzędzi użytkownika. Zwrócony typ jest taki sam jak typ, który jest przekazywany do `CWinAppEx::EnableUserTools` jako `pToolRTC` parametru.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda znajduje pierwszy identyfikator polecenia menu dostępne w zakresie, która jest dostarczana w wywołaniu [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) i przypisuje narzędzia użytkownika tego identyfikatora.  
  
 Metoda kończy się niepowodzeniem, jeśli osiągnięto maksymalną liczbę narzędzi. Dzieje się tak, gdy wszystkie identyfikatory poleceń w zakresie są przypisane do użytkownika narzędzia. Maksymalna liczba narzędzia można pobrać przez wywołanie metody [CUserToolsManager::GetMaxTools](#getmaxtools). Możesz uzyskać dostęp do listy narzędzia wywołując [CUserToolsManager::GetUserTools](#getusertools) metody.  
  
##  <a name="cusertoolsmanager"></a>CUserToolsManager::CUserToolsManager  
 Konstruuje `CUserToolsManager`. Każda aplikacja musi mieć co najwyżej jednego Menedżera narzędzi użytkownika.  
  
```  
CUserToolsManager();

 
CUserToolsManager(
    const UINT uiCmdToolsDummy,  
    const UINT uiCmdFirst,  
    const UINT uiCmdLast,  
    CRuntimeClass* pToolRTC=RUNTIME_CLASS(CUserTool),  
    UINT uArgMenuID=0,  
    UINT uInitDirMenuID=0);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiCmdToolsDummy`  
 Liczba całkowita bez znaku używanego przez platformę jako symbol zastępczy dla Identyfikatora polecenia w menu Narzędzia użytkownika.  
  
 [in]`uiCmdFirst`  
 Identyfikator polecenia dla pierwszego polecenia narzędzia użytkownika.  
  
 [in]`uiCmdLast`  
 Identyfikator polecenia dla ostatniego polecenia narzędzia użytkownika.  
  
 [in]`pToolRTC`  
 Klasa który [CUserToolsManager::CreateNewTool](#createnewtool) tworzy. Za pomocą tej klasy, można użyć typu pochodnego [klasy CUserTool](../../mfc/reference/cusertool-class.md) zamiast w implementacji domyślnej.  
  
 [in]`uArgMenuID`  
 Identyfikator zasobu menu menu podręcznego argumentów.  
  
 [in]`uInitDirMenuID`  
 Identyfikator zasobu menu menu podręcznego początkowy katalog.  
  
### <a name="remarks"></a>Uwagi  
 Nie wywołuj tego konstruktora. Zamiast tego wywołać [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) Włącz użytkownika narzędzia i wywołanie [CWinAppEx::GetUserToolsManager](../../mfc/reference/cwinappex-class.md#getusertoolsmanager) uzyskać wskaźnik do `CUserToolsManager`. Aby uzyskać więcej informacji, zobacz [narzędzia zdefiniowane przez użytkownika](../../mfc/user-defined-tools.md).  
  
##  <a name="findtool"></a>CUserToolsManager::FindTool  
 Zwraca wskaźnik do [klasy CUserTool](../../mfc/reference/cusertool-class.md) obiekt, który jest skojarzony z identyfikatorem określonego polecenia.  
  
```  
CUserTool* FindTool(UINT uiCmdId) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiCmdId`  
 Identyfikator polecenia menu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [klasy CUserTool](../../mfc/reference/cusertool-class.md) lub `CUserTool`-pochodnych obiektu, jeśli Powodzenie; w przeciwnym razie `NULL`.  
  
### <a name="remarks"></a>Uwagi  
 Gdy `FindTool` jest powodzenia zwrócony typ jest taki sam jak typ `pToolRTC` parametr [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).  
  
##  <a name="getargumentsmenuid"></a>CUserToolsManager::GetArgumentsMenuID  
 Zwraca identyfikator zasobu, który jest skojarzony z **argumenty** menu **narzędzia** karcie **Dostosuj** okno dialogowe.  
  
```  
UINT GetArgumentsMenuID() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator zasobu menu.  
  
### <a name="remarks"></a>Uwagi  
 `uArgMenuID` Parametr [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) Określa identyfikator zasobu.  
  
##  <a name="getdefext"></a>CUserToolsManager::GetDefExt  
 Zwraca domyślne rozszerzenie, które **Otwórz plik** okno dialogowe ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) używa w **polecenia** na **narzędzia** karty **Dostosuj** okno dialogowe.  
  
```  
const CString& GetDefExt() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do `CString` obiekt, który zawiera rozszerzenia.  
  
##  <a name="getfilter"></a>CUserToolsManager::GetFilter  
 Zwraca filtr plików, który **Otwórz plik** okno dialogowe ( [klasy CFileDialog](../../mfc/reference/cfiledialog-class.md)) używa w **polecenia** na **narzędzia** karty **Dostosuj** okno dialogowe.  
  
```  
const CString& GetFilter() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do `CString` obiekt, który zawiera filtr.  
  
##  <a name="getinitialdirmenuid"></a>CUserToolsManager::GetInitialDirMenuID  
 Zwraca identyfikator zasobu, który jest skojarzony z **katalog początkowy** menu **narzędzia** karcie **Dostosuj** okno dialogowe.  
  
```  
UINT GetInitialDirMenuID() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator zasobu menu.  
  
### <a name="remarks"></a>Uwagi  
 Zwrócony identyfikator jest określony w `uInitDirMenuID` parametr [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).  
  
##  <a name="getmaxtools"></a>CUserToolsManager::GetMaxTools  
 Zwraca maksymalną liczbę narzędzi użytkownika, które mogą być przydzielone w aplikacji.  
  
```  
int GetMaxTools() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Maksymalna liczba użytkowników narzędzia, które mogą być przydzielone.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby pobrać maksymalną liczbę narzędzia, które mogą być przydzielone w aplikacji. Ta liczba jest liczba identyfikatorów w zakresie od `uiCmdFirst` za pośrednictwem `uiCmdLast` parametry przekazywane do [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).  
  
##  <a name="gettoolsentrycmd"></a>CUserToolsManager::GetToolsEntryCmd  
 Zwraca identyfikator polecenia symbol zastępczy elementu menu dla użytkownika narzędzia.  
  
```  
UINT GetToolsEntryCmd() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator polecenia symbol zastępczy.  
  
### <a name="remarks"></a>Uwagi  
 Aby włączyć narzędzia użytkownika, należy wywołać [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools). `uiCmdToolsDummy` Parametr określa identyfikator polecenia polecenie wpisu narzędzia. Ta metoda zwraca identyfikator narzędzia wpis polecenia. Wszędzie tam, gdzie ten identyfikator jest używany w menu, po wyświetleniu menu jest zastępowany przez listę narzędzi użytkownika.  
  
##  <a name="getusertools"></a>CUserToolsManager::GetUserTools  
 Zwraca odwołanie do listy użytkownika narzędzia.  
  
```  
const CObList& GetUserTools() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stała odwołanie do [klasy CObList](../../mfc/reference/coblist-class.md) obiekt, który zawiera listę narzędzi użytkownika.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody, aby pobrać listę użytkownika narzędzi, które [CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md) obiekt zachowuje. Narzędzie każdego użytkownika jest reprezentowana przez obiekt typu [klasy CUserTool](../../mfc/reference/cusertool-class.md) lub typ pochodzący od `CUserTool`. Typ jest określany przez `pToolRTC` parametr podczas wywoływania [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) Aby włączyć narzędzia użytkownika.  
  
##  <a name="invoketool"></a>CUserToolsManager::InvokeTool  
 Wykonuje aplikacji skojarzonej z narzędziem użytkownika, który ma identyfikator określonego polecenia.  
  
```  
BOOL InvokeTool(UINT uiCmdId);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiCmdId`  
 Identyfikator polecenia menu skojarzony z narzędzia użytkownika.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli polecenie skojarzone z narzędzia użytkownika zostało wykonane pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie narzędzia tę metodę w celu wykonania aplikacji skojarzonych z użytkownikiem, który ma określony przez identyfikator polecenia `uiCmdId`.  
  
##  <a name="isusertoolcmd"></a>CUserToolsManager::IsUserToolCmd  
 Określa, czy identyfikator polecenia jest skojarzony z narzędziem do użytkownika.  
  
```  
BOOL IsUserToolCmd(UINT uiCmdId) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiCmdId`  
 Identyfikator polecenia elementu menu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli dane polecenie identyfikator jest skojarzony z narzędziem użytkownika; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda sprawdza, czy identyfikator polecenia jest w zasięgu Identyfikatora polecenia. Określ zakres podczas wywoływania [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) Aby włączyć narzędzia użytkownika.  
  
##  <a name="loadstate"></a>CUserToolsManager::LoadState  
 Ładuje informacje o narzędziach użytkownika z rejestru systemu Windows.  
  
```  
BOOL LoadState(LPCTSTR lpszProfileName=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszProfileName`  
 Ścieżka klucza rejestru systemu Windows.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli stan został załadowany pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda ładuje stan `CUserToolsManager` obiektu z rejestru systemu Windows.  
  
 Zazwyczaj nie ta metoda jest wywoływana bezpośrednio. [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate) wywołuje go jako część procesu inicjalizacji obszaru roboczego.  
  
##  <a name="movetooldown"></a>CUserToolsManager::MoveToolDown  
 Umożliwia przeniesienie narzędzia określonego użytkownika w dół listę narzędzi użytkownika.  
  
```  
BOOL MoveToolDown(CUserTool* pTool);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pTool`  
 Określa narzędzie użytkownika, aby przenieść.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli narzędzie użytkownika został pomyślnie; przenieść w dół w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Metoda kończy się niepowodzeniem, jeśli narzędzie który `pTool` określa nie jest na liście wewnętrznych lub jeśli narzędzie to jest ostatni na liście.  
  
##  <a name="movetoolup"></a>CUserToolsManager::MoveToolUp  
 Zostanie przesunięty narzędzia określonego użytkownika na liście użytkownika narzędzia.  
  
```  
BOOL MoveToolUp(CUserTool* pTool);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pTool`  
 Określa narzędzie użytkownika, aby przenieść.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli narzędzie użytkownika została przeniesiona pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Metoda kończy się niepowodzeniem, jeśli narzędzie który `pTool` określa parametr nie jest na liście wewnętrznych lub jeśli narzędzie to jest pierwszy element narzędzia na liście.  
  
##  <a name="removetool"></a>CUserToolsManager::RemoveTool  
 Usuwa określonego użytkownika narzędzia z aplikacji.  
  
```  
BOOL RemoveTool(CUserTool* pTool);
```  
  
### <a name="parameters"></a>Parametry  
 [w, out]`pTool`  
 Wskaźnik do narzędzia użytkownika do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli narzędzie został pomyślnie usunięty. W przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli narzędzie została pomyślnie usunięta, ta metoda usuwa `pTool`.  
  
##  <a name="savestate"></a>CUserToolsManager::SaveState  
 Przechowuje informacje dotyczące narzędzi użytkownika w rejestrze systemu Windows.  
  
```  
BOOL SaveState(LPCTSTR lpszProfileName=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszProfileName`  
 Ścieżka do klucza rejestru systemu Windows.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli stan został zapisany pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Metoda zapisuje bieżący stan `CUserToolsManager` obiektu w rejestrze systemu Windows.  
  
 Zwykle nie trzeba wywołać tę metodę bezpośrednio, [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate) wywołuje ona automatycznie jako część procesu serializacji obszaru roboczego aplikacji.  
  
##  <a name="setdefext"></a>CUserToolsManager::SetDefExt  
 Określa domyślne rozszerzenie który **Otwórz plik** okno dialogowe ( [klasy CFileDialog](../../mfc/reference/cfiledialog-class.md)) używa w **polecenia** na **narzędzia** kartę z **Dostosuj** okno dialogowe.  
  
```  
void SetDefExt(const CString& strDefExt);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`strDefExt`  
 Ciąg tekstowy, który zawiera domyślne rozszerzenie nazwy pliku.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody, aby określić domyślne rozszerzenie nazwy pliku w **Otwórz plik** okno dialogowe, które jest wyświetlane, gdy użytkownik wybierze aplikacji do skojarzenia z narzędzia użytkownika. Wartość domyślna to "exe".  
  
##  <a name="setfilter"></a>CUserToolsManager::SetFilter  
 Określa plik filtru, który **Otwórz plik** okno dialogowe ( [klasy CFileDialog](../../mfc/reference/cfiledialog-class.md)) używa w **polecenia** na **narzędzia** karty **Dostosuj** okno dialogowe.  
  
```  
void SetFilter(const CString& strFilter);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`strFilter`  
 Określa filtr.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)   
 [Klasa CUserTool](../../mfc/reference/cusertool-class.md)
