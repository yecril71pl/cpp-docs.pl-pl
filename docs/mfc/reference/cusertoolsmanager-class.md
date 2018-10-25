---
title: Klasa CUserToolsManager | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4fdc79325fcf05eda37399a9e913c79a03f6da5d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054590"
---
# <a name="cusertoolsmanager-class"></a>Klasa CUserToolsManager

Przechowuje kolekcję [klasa CUserTool](../../mfc/reference/cusertool-class.md) obiektów w aplikacji. Narzędzie użytkownika jest element menu, który uruchamia aplikację zewnętrzną. `CUserToolsManager` Obiekt umożliwia użytkownikowi lub programiście Dodawanie nowych narzędzi użytkownika do aplikacji. Obsługuje wykonywanie poleceń związanych z narzędziami użytkownika, a także zapisuje informacje o narzędziach użytkownika w rejestrze systemu Windows.

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
|[CUserToolsManager::FindTool](#findtool)|Zwraca wskaźnik do `CMFCUserTool` obiektu, który jest skojarzony z identyfikatorem określonego polecenia.|
|[CUserToolsManager::GetArgumentsMenuID](#getargumentsmenuid)|Zwraca identyfikator zasobu, który jest skojarzony z **argumenty** menu **narzędzia** karcie **Dostosuj** okno dialogowe.|
|[CUserToolsManager::GetDefExt](#getdefext)|Zwraca wartość domyślnym rozszerzeniem **Otwórz plik** okno dialogowe ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) używa w **polecenia** na **narzędzia** karty **Dostosuj** okno dialogowe.|
|[CUserToolsManager::GetFilter](#getfilter)|Zwraca filtr plików, który **Otwórz plik** okno dialogowe ( [klasa CFileDialog](../../mfc/reference/cfiledialog-class.md)) używa w **polecenia** na **narzędzia** karty **Dostosuj** okno dialogowe.|
|[CUserToolsManager::GetInitialDirMenuID](#getinitialdirmenuid)|Zwraca identyfikator zasobu, który jest skojarzony z **Czątkowy katalog** menu **narzędzia** karcie **Dostosuj** okno dialogowe.|
|[CUserToolsManager::GetMaxTools](#getmaxtools)|Zwraca maksymalną liczbę narzędzi użytkownika, które mogą być przydzielone w aplikacji.|
|[CUserToolsManager::GetToolsEntryCmd](#gettoolsentrycmd)|Zwraca identyfikator polecenia symbol zastępczy element menu narzędzi użytkownika.|
|[CUserToolsManager::GetUserTools](#getusertools)|Zwraca odwołanie do listy narzędzi użytkownika.|
|[CUserToolsManager::InvokeTool](#invoketool)|Wykonuje aplikacji skojarzonej z narzędzia użytkownika, który ma identyfikator określonego polecenia.|
|[CUserToolsManager::IsUserToolCmd](#isusertoolcmd)|Określa, czy identyfikator polecenia jest skojarzony z narzędziem do użytkownika.|
|[CUserToolsManager::LoadState](#loadstate)|Ładuje informacje o narzędziach użytkownika w rejestrze systemu Windows.|
|[CUserToolsManager::MoveToolDown](#movetooldown)|Przenosi narzędzie określonego użytkownika w dół na liście narzędzi użytkownika.|
|[CUserToolsManager::MoveToolUp](#movetoolup)|Zostanie przesunięty narzędzie określonego użytkownika na liście narzędzi użytkownika.|
|[CUserToolsManager::RemoveTool](#removetool)|Usuwa narzędzie określonego użytkownika z aplikacji.|
|[CUserToolsManager::SaveState](#savestate)|Przechowuje informacje o narzędziach użytkownika w rejestrze systemu Windows.|
|[CUserToolsManager::SetDefExt](#setdefext)|Określa domyślne rozszerzenie, **Otwórz plik** okno dialogowe ( [klasa CFileDialog](../../mfc/reference/cfiledialog-class.md)) używa w **polecenia** na **narzędzia** kartę z **Dostosuj** okno dialogowe.|
|[CUserToolsManager::SetFilter](#setfilter)|Określa plik filtru, który **Otwórz plik** okno dialogowe ( [klasa CFileDialog](../../mfc/reference/cfiledialog-class.md)) używa w **polecenia** na **narzędzia** karty **Dostosuj** okno dialogowe.|

## <a name="remarks"></a>Uwagi

Aby dołączyć narzędzi użytkownika do aplikacji, musisz mieć:

1. Zarezerwuj element menu i polecenia skojarzony identyfikator wpisu menu Narzędzia użytkownika.

2. Zarezerwuj Identyfikatora kolejne polecenie dla każdego z narzędzi użytkownika zdefiniowanego przez użytkownika w aplikacji.

3. Wywołaj [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) metody i podać następujące parametry: menu Identyfikator polecenia, pierwszy identyfikator polecenia narzędzia użytkownika i ostatniego użytkownika narzędzia komendy.

Powinien istnieć tylko jeden globalnego `CUserToolsManager` obiektu na aplikację.

Na przykład narzędzi użytkownika Zobacz VisualStudioDemo przykładowy projekt.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak pobrać odwołanie do `CUserToolsManager` obiektu oraz sposobu tworzenia nowych narzędzi użytkownika. Ten fragment kodu jest częścią [Visual Studio przykład](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#38](../../mfc/codesnippet/cpp/cusertoolsmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CUserToolsManager`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxusertoolsmanager.h

##  <a name="createnewtool"></a>  CUserToolsManager::CreateNewTool

Tworzy nowe narzędzie użytkownika.

```
CUserTool* CreateNewTool();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowo utworzonego użytkownika narzędzia lub wartość NULL, jeśli liczba narzędzi użytkownika przekroczyła maksymalną. Zwracany typ jest taki sam jak typ, który jest przekazywany do `CWinAppEx::EnableUserTools` jako *pToolRTC* parametru.

### <a name="remarks"></a>Uwagi

Ta metoda znajdzie pierwszy dostępny Identyfikatorem polecenia menu w zakresie, który jest dostarczany w wywołaniu [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) i przypisuje narzędzie użytkownika tego identyfikatora.

Metoda kończy się niepowodzeniem, jeśli osiągnięto maksymalnej liczby narzędzi. Dzieje się tak, gdy wszystkie identyfikatory poleceń w zakresie są przypisane do użytkownika narzędzia. Maksymalna liczba narzędzia można pobrać przez wywołanie metody [CUserToolsManager::GetMaxTools](#getmaxtools). Możesz uzyskać dostęp do listy narzędzi, wywołując [CUserToolsManager::GetUserTools](#getusertools) metody.

##  <a name="cusertoolsmanager"></a>  CUserToolsManager::CUserToolsManager

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

*uiCmdToolsDummy*<br/>
[in] Liczba całkowita bez znaku środowisko wykorzystuje jako symbol zastępczy dla Identyfikatora polecenia menu Narzędzia użytkownika.

*uiCmdFirst*<br/>
[in] Identyfikator polecenia dla polecenia narzędzia pierwszego użytkownika.

*uiCmdLast*<br/>
[in] Identyfikator polecenia dla polecenia narzędzia ostatniego użytkownika.

*pToolRTC*<br/>
[in] Klasa, [CUserToolsManager::CreateNewTool](#createnewtool) tworzy. Za pomocą tej klasy, można użyć typem pochodnym [klasa CUserTool](../../mfc/reference/cusertool-class.md) zamiast Domyślna implementacja.

*uArgMenuID*<br/>
[in] Identyfikator zasobu menu z menu podręcznego argumentów.

*uInitDirMenuID*<br/>
[in] Identyfikator zasobu menu z menu podręcznego wstępnego katalogu.

### <a name="remarks"></a>Uwagi

Nie wywołuj tego konstruktora. Zamiast tego należy wywołać [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) Włącz narzędzi użytkownika w celu wywołania [CWinAppEx::GetUserToolsManager](../../mfc/reference/cwinappex-class.md#getusertoolsmanager) uzyskać wskaźnik do `CUserToolsManager`. Aby uzyskać więcej informacji, zobacz [narzędzia zdefiniowane przez użytkownika](../../mfc/user-defined-tools.md).

##  <a name="findtool"></a>  CUserToolsManager::FindTool

Zwraca wskaźnik do [klasa CUserTool](../../mfc/reference/cusertool-class.md) obiektu, który jest skojarzony z identyfikatorem określonego polecenia.

```
CUserTool* FindTool(UINT uiCmdId) const;
```

### <a name="parameters"></a>Parametry

*uiCmdId*<br/>
[in] Identyfikator polecenia menu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [klasa CUserTool](../../mfc/reference/cusertool-class.md) lub `CUserTool`-pochodnych obiektu, jeśli Powodzenie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Gdy `FindTool` to się powiedzie, zwracany typ jest taki sam jak typ *pToolRTC* parametr [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).

##  <a name="getargumentsmenuid"></a>  CUserToolsManager::GetArgumentsMenuID

Zwraca identyfikator zasobu, który jest skojarzony z **argumenty** menu **narzędzia** karcie **Dostosuj** okno dialogowe.

```
UINT GetArgumentsMenuID() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator zasobu menu.

### <a name="remarks"></a>Uwagi

*UArgMenuID* parametru [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) Określa identyfikator zasobu.

##  <a name="getdefext"></a>  CUserToolsManager::GetDefExt

Zwraca wartość domyślnym rozszerzeniem **Otwórz plik** okno dialogowe ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) używa w **polecenia** na **narzędzia** karty **Dostosuj** okno dialogowe.

```
const CString& GetDefExt() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `CString` obiekt, który zawiera rozszerzenie.

##  <a name="getfilter"></a>  CUserToolsManager::GetFilter

Zwraca filtr plików, który **Otwórz plik** okno dialogowe ( [klasa CFileDialog](../../mfc/reference/cfiledialog-class.md)) używa w **polecenia** na **narzędzia** karty **Dostosuj** okno dialogowe.

```
const CString& GetFilter() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `CString` obiekt, który zawiera filtr.

##  <a name="getinitialdirmenuid"></a>  CUserToolsManager::GetInitialDirMenuID

Zwraca identyfikator zasobu, który jest skojarzony z **Czątkowy katalog** menu **narzędzia** karcie **Dostosuj** okno dialogowe.

```
UINT GetInitialDirMenuID() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator zasobu menu.

### <a name="remarks"></a>Uwagi

Zwrócony identyfikator jest określony w *uInitDirMenuID* parametru [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).

##  <a name="getmaxtools"></a>  CUserToolsManager::GetMaxTools

Zwraca maksymalną liczbę narzędzi użytkownika, które mogą być przydzielone w aplikacji.

```
int GetMaxTools() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna liczba narzędzi użytkownika, które mogą być przydzielone.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby pobrać maksymalną liczbę narzędzia, które mogą być przydzielone w aplikacji. Ta liczba jest liczba identyfikatorów w zakresie od *uiCmdFirst* za pośrednictwem *uiCmdLast* parametry przekazywane do [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).

##  <a name="gettoolsentrycmd"></a>  CUserToolsManager::GetToolsEntryCmd

Zwraca identyfikator polecenia symbol zastępczy element menu narzędzi użytkownika.

```
UINT GetToolsEntryCmd() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator polecenia symbolu zastępczego.

### <a name="remarks"></a>Uwagi

Aby włączyć narzędzia użytkownika, należy wywołać [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools). *UiCmdToolsDummy* parametr określa identyfikator polecenia narzędzia polecenia zapisu. Ta metoda zwraca identyfikator narzędzia wpis polecenia. Wszędzie tam, gdzie ten identyfikator jest używany w menu, po wyświetleniu menu jest zastępowany przez listę narzędzi użytkownika.

##  <a name="getusertools"></a>  CUserToolsManager::GetUserTools

Zwraca odwołanie do listy narzędzi użytkownika.

```
const CObList& GetUserTools() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie typu const [klasa CObList](../../mfc/reference/coblist-class.md) obiektu, który zawiera listę narzędzi użytkownika.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody można pobrać listy użytkownika narzędzia, które [CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md) obiekt zachowuje. Każde narzędzie użytkownika jest reprezentowana przez obiekt typu [klasa CUserTool](../../mfc/reference/cusertool-class.md) lub typ pochodzący od `CUserTool`. Właściwość type jest określona przez *pToolRTC* parametru podczas wywoływania [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) umożliwiające narzędzi użytkownika.

##  <a name="invoketool"></a>  CUserToolsManager::InvokeTool

Wykonuje aplikacji skojarzonej z narzędzia użytkownika, który ma identyfikator określonego polecenia.

```
BOOL InvokeTool(UINT uiCmdId);
```

### <a name="parameters"></a>Parametry

*uiCmdId*<br/>
[in] Identyfikator polecenia menu skojarzony z narzędzia użytkownika.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli polecenie skojarzone z narzędzia do użytkowników została wykonana pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołanie narzędzia tę metodę w celu wykonywania aplikacji skojarzonych z użytkownikiem, który ma określony przez identyfikator polecenia *uiCmdId*.

##  <a name="isusertoolcmd"></a>  CUserToolsManager::IsUserToolCmd

Określa, czy identyfikator polecenia jest skojarzony z narzędziem do użytkownika.

```
BOOL IsUserToolCmd(UINT uiCmdId) const;
```

### <a name="parameters"></a>Parametry

*uiCmdId*<br/>
[in] Identyfikator polecenia elementu menu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli dane polecenie identyfikator jest skojarzony z narzędziem użytkownika; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda sprawdza, czy identyfikator polecenia znajduje się w zakresie Identyfikatora polecenia. Określ zakres podczas wywoływania [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) umożliwiające narzędzi użytkownika.

##  <a name="loadstate"></a>  CUserToolsManager::LoadState

Ładuje informacje o narzędziach użytkownika w rejestrze systemu Windows.

```
BOOL LoadState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[in] Ścieżka do klucza rejestru Windows.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli stan został załadowany pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda ładuje stan `CUserToolsManager` obiektu z rejestru Windows.

Zazwyczaj nie zostanie wywołana metoda ta bezpośrednio. [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate) określa je jako część procesu inicjowania obszaru roboczego.

##  <a name="movetooldown"></a>  CUserToolsManager::MoveToolDown

Przenosi narzędzie określonego użytkownika w dół na liście narzędzi użytkownika.

```
BOOL MoveToolDown(CUserTool* pTool);
```

### <a name="parameters"></a>Parametry

*pTool*<br/>
[in] Określa narzędzie użytkowników, aby przenieść.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli narzędzie do użytkowników została przeniesiona pomyślnie; w dół w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Metoda kończy się niepowodzeniem, jeśli narzędzie, *pTool* określa nie ma na liście wewnętrznych, czy narzędzie to jest ostatnia na liście.

##  <a name="movetoolup"></a>  CUserToolsManager::MoveToolUp

Zostanie przesunięty narzędzie określonego użytkownika na liście narzędzi użytkownika.

```
BOOL MoveToolUp(CUserTool* pTool);
```

### <a name="parameters"></a>Parametry

*pTool*<br/>
[in] Określa narzędzie użytkowników, aby przenieść.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli narzędzie do użytkowników została przeniesiona pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Metoda kończy się niepowodzeniem, jeśli narzędzie, *pTool* parametr określa, nie ma na liście wewnętrznych, czy narzędzie to jest pierwszy element narzędzia na liście.

##  <a name="removetool"></a>  CUserToolsManager::RemoveTool

Usuwa narzędzie określonego użytkownika z aplikacji.

```
BOOL RemoveTool(CUserTool* pTool);
```

### <a name="parameters"></a>Parametry

*pTool*<br/>
[out w] Wskaźnik do narzędzie użytkownika do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli narzędzie został pomyślnie usunięty. W przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Jeśli narzędzie zostanie pomyślnie usunięty, ta metoda usuwa *pTool*.

##  <a name="savestate"></a>  CUserToolsManager::SaveState

Przechowuje informacje o narzędziach użytkownika w rejestrze systemu Windows.

```
BOOL SaveState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[in] Ścieżka do klucza rejestru Windows.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli stan został zapisany pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Metoda zapisuje bieżący stan `CUserToolsManager` obiektu w rejestrze systemu Windows.

Zazwyczaj nie trzeba bezpośrednio wywołać tę metodę [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate) wywołuje on automatycznie jako część procesu serializacji obszaru roboczego aplikacji.

##  <a name="setdefext"></a>  CUserToolsManager::SetDefExt

Określa domyślne rozszerzenie, **Otwórz plik** okno dialogowe ( [klasa CFileDialog](../../mfc/reference/cfiledialog-class.md)) używa w **polecenia** na **narzędzia** kartę z **Dostosuj** okno dialogowe.

```
void SetDefExt(const CString& strDefExt);
```

### <a name="parameters"></a>Parametry

*strDefExt*<br/>
[in] Ciąg tekstowy, który zawiera domyślne rozszerzenie nazwy pliku.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby określić domyślne rozszerzenie nazwy pliku w **Otwórz plik** okno dialogowe, które jest wyświetlane, gdy użytkownik wybierze aplikacji do skojarzenia z narzędzia użytkownika. Wartość domyślna to "exe".

##  <a name="setfilter"></a>  CUserToolsManager::SetFilter

Określa plik filtru, który **Otwórz plik** okno dialogowe ( [klasa CFileDialog](../../mfc/reference/cfiledialog-class.md)) używa w **polecenia** na **narzędzia** karty **Dostosuj** okno dialogowe.

```
void SetFilter(const CString& strFilter);
```

### <a name="parameters"></a>Parametry

*strFilter*<br/>
[in] Określa filtr.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)<br/>
[Klasa CUserTool](../../mfc/reference/cusertool-class.md)
