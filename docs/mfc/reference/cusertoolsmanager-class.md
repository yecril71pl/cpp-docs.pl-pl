---
title: Klasa CUserToolsManager
ms.date: 11/04/2016
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
ms.openlocfilehash: c1f14657350c08679868299ce4878cca2ae10eec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373223"
---
# <a name="cusertoolsmanager-class"></a>Klasa CUserToolsManager

Utrzymuje kolekcję [CUserTool Class](../../mfc/reference/cusertool-class.md) obiektów w aplikacji. Narzędzie użytkownika jest elementem menu, który uruchamia aplikację zewnętrzną. Obiekt `CUserToolsManager` umożliwia użytkownikowi lub deweloperowi dodawanie nowych narzędzi użytkownika do aplikacji. Obsługuje wykonywanie poleceń skojarzonych z narzędziami użytkownika, a także zapisuje informacje o narzędziach użytkownika w rejestrze systemu Windows.

## <a name="syntax"></a>Składnia

```
class CUserToolsManager : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CUserToolsManager::CUserToolsManager](#cusertoolsmanager)|Konstruuje `CUserToolsManager`plik .|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CUserToolsManager::CreateNewTool](#createnewtool)|Tworzy nowe narzędzie użytkownika.|
|[CUserToolsManager::FindTool](#findtool)|Zwraca wskaźnik do `CMFCUserTool` obiektu skojarzonego z określonym identyfikatorem polecenia.|
|[CUserToolsManager::GetArgumentsMenuID](#getargumentsmenuid)|Zwraca identyfikator zasobu skojarzony z menu **Argumenty** na karcie **Narzędzia** w oknie dialogowym **Dostosowywanie.**|
|[CUserToolsManager::GetDefExt](#getdefext)|Zwraca domyślne rozszerzenie używane przez okno dialogowe **Otwieranie plików** [(CFileDialog)](../../mfc/reference/cfiledialog-class.md#cfiledialog)w polu **Polecenie** na karcie **Narzędzia** w oknie dialogowym **Dostosowywanie.**|
|[CUserToolsManager::GetFilter](#getfilter)|Zwraca filtr plików używany w polu **Polecenie** na karcie **Narzędzia** okna dialogowego Dostosowywanie używane przez okno dialogowe **Otwieranie** **pliku** [(CFileDialog Class).](../../mfc/reference/cfiledialog-class.md)|
|[CUserToolsManager::GetInitialDirMenuID](#getinitialdirmenuid)|Zwraca identyfikator zasobu **skojarzony** z menu Katalog początkowy na karcie **Narzędzia** w oknie dialogowym **Dostosowywanie.**|
|[CUserToolsManager::GetMaxTools](#getmaxtools)|Zwraca maksymalną liczbę narzędzi użytkownika, które można przydzielić w aplikacji.|
|[CUserToolsManager::GetToolsEntryCmd](#gettoolsentrycmd)|Zwraca identyfikator polecenia symbolu zastępczego elementu menu dla narzędzi użytkownika.|
|[CUserToolsManager::GetUserTools](#getusertools)|Zwraca odwołanie do listy narzędzi użytkownika.|
|[CUserToolsManager::InvokeTool](#invoketool)|Wykonuje aplikację skojarzoną z narzędziem użytkownika o określonym identyfikatorze polecenia.|
|[CUserToolsManager::IsUserToolCmd](#isusertoolcmd)|Określa, czy identyfikator polecenia jest skojarzony z narzędziem użytkownika.|
|[CUserToolsManager::LoadState](#loadstate)|Ładuje informacje o narzędziach użytkownika z rejestru systemu Windows.|
|[CUserToolsManager::MoveToolDown](#movetooldown)|Przenosi określone narzędzie użytkownika w dół na liście narzędzi użytkownika.|
|[CUserToolsManager::MoveToolUp](#movetoolup)|Przenosi określone narzędzie użytkownika w górę na liście narzędzi użytkownika.|
|[CUserToolsManager::RemoveTool](#removetool)|Usuwa określone narzędzie użytkownika z aplikacji.|
|[CUserToolsManager::Zapisz](#savestate)|Przechowuje informacje o narzędziach użytkownika w rejestrze systemu Windows.|
|[CUserToolsManager::SetDefExt](#setdefext)|Określa domyślne rozszerzenie używane przez okno dialogowe **Otwieranie pliku** [(CFileDialog Class)](../../mfc/reference/cfiledialog-class.md)w polu **Polecenie** na karcie **Narzędzia** w oknie dialogowym **Dostosowywanie.**|
|[CUserToolsManager::SetFilter](#setfilter)|Określa filtr plików używany w polu **Polecenie** na karcie **Narzędzia** okna dialogowego Dostosowywanie używane przez okno dialogowe **Otwieranie** **pliku** [(CFileDialog Class).](../../mfc/reference/cfiledialog-class.md)|

## <a name="remarks"></a>Uwagi

Aby włączyć narzędzia użytkownika do aplikacji, należy:

1. Zarezerwuj element menu i skojarzony identyfikator polecenia dla wpisu menu narzędzia użytkownika.

2. Zarezerwuj sekwencyjny identyfikator polecenia dla każdego narzędzia użytkownika, które użytkownik może zdefiniować w aplikacji.

3. Wywołanie [metody CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) i podanie następujących parametrów: identyfikator polecenia menu, identyfikator polecenia pierwszego narzędzia użytkownika i identyfikator polecenia narzędzia ostatniego użytkownika.

Powinna istnieć tylko `CUserToolsManager` jeden obiekt globalny na aplikację.

Na przykład narzędzi użytkownika, zobacz VisualStudioDemo przykładowy projekt.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CUserToolsManager` pobrać odwołanie do obiektu i jak utworzyć nowe narzędzia użytkownika. Ten fragment kodu jest częścią [przykładu demo programu Visual Studio.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_VisualStudioDemo#38](../../mfc/codesnippet/cpp/cusertoolsmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CUserToolsManager`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxusertoolsmanager.h

## <a name="cusertoolsmanagercreatenewtool"></a><a name="createnewtool"></a>CUserToolsManager::CreateNewTool

Tworzy nowe narzędzie użytkownika.

```
CUserTool* CreateNewTool();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowo utworzonego narzędzia użytkownika lub NULL, jeśli liczba narzędzi użytkownika przekroczyła wartość maksymalną. Zwracany typ jest taki sam jak `CWinAppEx::EnableUserTools` typ, który jest przekazywany jako parametr *pToolRTC.*

### <a name="remarks"></a>Uwagi

Ta metoda znajduje pierwszy dostępny identyfikator polecenia menu w zakresie, który jest dostarczany w wywołaniu [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) i przypisuje narzędzie użytkownika ten identyfikator.

Metoda kończy się niepowodzeniem, jeśli liczba narzędzi osiągnęła maksymalną wartość. Dzieje się tak, gdy wszystkie identyfikatory poleceń w zakresie są przypisane do narzędzi użytkownika. Maksymalną liczbę narzędzi można pobrać, dzwoniąc do [CUserToolsManager::GetMaxTools](#getmaxtools). Dostęp do listy narzędzi można uzyskać, wywołując metodę [CUserToolsManager::GetUserTools.](#getusertools)

## <a name="cusertoolsmanagercusertoolsmanager"></a><a name="cusertoolsmanager"></a>CUserToolsManager::CUserToolsManager

Konstruuje `CUserToolsManager`plik . Każda aplikacja musi mieć co najwyżej jeden menedżer narzędzi użytkownika.

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
[w] Niepodpisana liczba całkowita, której struktura używa jako symbolu zastępczego dla identyfikatora polecenia menu narzędzi użytkownika.

*uiCmdPierwsz*<br/>
[w] Identyfikator polecenia dla pierwszego polecenia narzędzia użytkownika.

*uiCmdLast*<br/>
[w] Identyfikator polecenia dla ostatniego polecenia narzędzia użytkownika.

*pToolRTC*<br/>
[w] Klasa, którą tworzy [CUserToolsManager::CreateNewTool.](#createnewtool) Za pomocą tej klasy, można użyć typu pochodnego [CUserTool Class](../../mfc/reference/cusertool-class.md) zamiast domyślnej implementacji.

*uArgMenuID*<br/>
[w] Identyfikator zasobu menu podręcznego argumenty.

*uInitDirMenuID*<br/>
[w] Identyfikator zasobu menu początkowego menu podręcznego katalogu.

### <a name="remarks"></a>Uwagi

Nie należy wywoływać tego konstruktora. Zamiast tego zadzwoń [do CWinAppEx::EnableUserTools,](../../mfc/reference/cwinappex-class.md#enableusertools) aby włączyć narzędzia użytkownika i zadzwoń [do CWinAppEx::GetUserToolsManager,](../../mfc/reference/cwinappex-class.md#getusertoolsmanager) aby uzyskać wskaźnik do `CUserToolsManager`. Aby uzyskać więcej informacji, zobacz [Narzędzia zdefiniowane przez użytkownika](../../mfc/user-defined-tools.md).

## <a name="cusertoolsmanagerfindtool"></a><a name="findtool"></a>CUserToolsManager::FindTool

Zwraca wskaźnik do obiektu [CUserTool Class,](../../mfc/reference/cusertool-class.md) który jest skojarzony z określonym identyfikatorem polecenia.

```
CUserTool* FindTool(UINT uiCmdId) const;
```

### <a name="parameters"></a>Parametry

*identyfikator uiCmdId*<br/>
[w] Identyfikator polecenia menu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CUserTool](../../mfc/reference/cusertool-class.md) Klasy `CUserTool`lub -pochodne obiektu, jeśli powodzenie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Po `FindTool` pomyślnym, zwracany typ jest taki sam jak typ parametru *pToolRTC* do [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).

## <a name="cusertoolsmanagergetargumentsmenuid"></a><a name="getargumentsmenuid"></a>CUserToolsManager::GetArgumentsMenuID

Zwraca identyfikator zasobu skojarzony z menu **Argumenty** na karcie **Narzędzia** w oknie dialogowym **Dostosowywanie.**

```
UINT GetArgumentsMenuID() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator zasobu menu.

### <a name="remarks"></a>Uwagi

Parametr *uArgMenuID* [języka CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) określa identyfikator zasobu.

## <a name="cusertoolsmanagergetdefext"></a><a name="getdefext"></a>CUserToolsManager::GetDefExt

Zwraca domyślne rozszerzenie używane przez okno dialogowe **Otwieranie plików** [(CFileDialog)](../../mfc/reference/cfiledialog-class.md#cfiledialog)w polu **Polecenie** na karcie **Narzędzia** w oknie dialogowym **Dostosowywanie.**

```
const CString& GetDefExt() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `CString` obiektu, który zawiera rozszerzenie.

## <a name="cusertoolsmanagergetfilter"></a><a name="getfilter"></a>CUserToolsManager::GetFilter

Zwraca filtr plików używany w polu **Polecenie** na karcie **Narzędzia** okna dialogowego Dostosowywanie używane przez okno dialogowe **Otwieranie** **pliku** [(CFileDialog Class).](../../mfc/reference/cfiledialog-class.md)

```
const CString& GetFilter() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `CString` obiektu, który zawiera filtr.

## <a name="cusertoolsmanagergetinitialdirmenuid"></a><a name="getinitialdirmenuid"></a>CUserToolsManager::GetInitialDirMenuID

Zwraca identyfikator zasobu **skojarzony** z menu Katalog początkowy na karcie **Narzędzia** w oknie dialogowym **Dostosowywanie.**

```
UINT GetInitialDirMenuID() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator zasobu menu.

### <a name="remarks"></a>Uwagi

Zwrócony identyfikator jest określony w parametrze *uInitDirMenuID* [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).

## <a name="cusertoolsmanagergetmaxtools"></a><a name="getmaxtools"></a>CUserToolsManager::GetMaxTools

Zwraca maksymalną liczbę narzędzi użytkownika, które można przydzielić w aplikacji.

```
int GetMaxTools() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna liczba narzędzi użytkownika, które można przydzielić.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby pobrać maksymalną liczbę narzędzi, które mogą być przydzielone w aplikacji. Ta liczba jest liczbą identyfikatorów w zakresie od *uiCmdFirst* przez *parametry uiCmdLast,* które są przekazywane do [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).

## <a name="cusertoolsmanagergettoolsentrycmd"></a><a name="gettoolsentrycmd"></a>CUserToolsManager::GetToolsEntryCmd

Zwraca identyfikator polecenia symbolu zastępczego elementu menu dla narzędzi użytkownika.

```
UINT GetToolsEntryCmd() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator polecenia symbolu zastępczego.

### <a name="remarks"></a>Uwagi

Aby włączyć narzędzia użytkownika, należy wywołać [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools). Parametr *uiCmdToolsDummy* określa identyfikator polecenia polecenia wpisu narzędzi. Ta metoda zwraca identyfikator polecenia wpisu narzędzi. Wszędzie tam, gdzie ten identyfikator jest używany w menu, jest on zastępowany przez listę narzędzi użytkownika, gdy pojawi się menu.

## <a name="cusertoolsmanagergetusertools"></a><a name="getusertools"></a>CUserToolsManager::GetUserTools

Zwraca odwołanie do listy narzędzi użytkownika.

```
const CObList& GetUserTools() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie const do [CObList Class](../../mfc/reference/coblist-class.md) obiektu, który zawiera listę narzędzi użytkownika.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby pobrać listę narzędzi użytkownika, które [CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md) obiekt utrzymuje. Każde narzędzie użytkownika jest reprezentowane przez obiekt typu [CUserTool](../../mfc/reference/cusertool-class.md) `CUserTool`Class lub typ pochodzący z . Typ jest określony przez parametr *pToolRTC* podczas wywoływania [CWinAppEx::EnableUserTools,](../../mfc/reference/cwinappex-class.md#enableusertools) aby włączyć narzędzia użytkownika.

## <a name="cusertoolsmanagerinvoketool"></a><a name="invoketool"></a>CUserToolsManager::InvokeTool

Wykonuje aplikację skojarzoną z narzędziem użytkownika o określonym identyfikatorze polecenia.

```
BOOL InvokeTool(UINT uiCmdId);
```

### <a name="parameters"></a>Parametry

*identyfikator uiCmdId*<br/>
[w] Identyfikator polecenia menu skojarzony z narzędziem użytkownika.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli polecenie skojarzone z narzędziem użytkownika zostało wykonane pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby wykonać aplikację skojarzoną z narzędziem użytkownika, który ma identyfikator polecenia określony przez *uiCmdId*.

## <a name="cusertoolsmanagerisusertoolcmd"></a><a name="isusertoolcmd"></a>CUserToolsManager::IsUserToolCmd

Określa, czy identyfikator polecenia jest skojarzony z narzędziem użytkownika.

```
BOOL IsUserToolCmd(UINT uiCmdId) const;
```

### <a name="parameters"></a>Parametry

*identyfikator uiCmdId*<br/>
[w] Identyfikator polecenia elementu menu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli dany identyfikator polecenia jest skojarzony z narzędziem użytkownika; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda sprawdza, czy podany identyfikator polecenia znajduje się w zakresie identyfikatora polecenia. Określ zakres podczas wywoływania [CWinAppEx::EnableUserTools,](../../mfc/reference/cwinappex-class.md#enableusertools) aby włączyć narzędzia użytkownika.

## <a name="cusertoolsmanagerloadstate"></a><a name="loadstate"></a>CUserToolsManager::LoadState

Ładuje informacje o narzędziach użytkownika z rejestru systemu Windows.

```
BOOL LoadState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[w] Ścieżka klucza rejestru systemu Windows.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli stan został załadowany pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda ładuje stan `CUserToolsManager` obiektu z rejestru systemu Windows.

Zazwyczaj nie należy wywoływać tej metody bezpośrednio. [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate) wywołuje go jako część procesu inicjowania obszaru roboczego.

## <a name="cusertoolsmanagermovetooldown"></a><a name="movetooldown"></a>CUserToolsManager::MoveToolDown

Przenosi określone narzędzie użytkownika w dół na liście narzędzi użytkownika.

```
BOOL MoveToolDown(CUserTool* pTool);
```

### <a name="parameters"></a>Parametry

*pTool (pTool)*<br/>
[w] Określa narzędzie użytkownika do przeniesienia.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli narzędzie użytkownika zostało pomyślnie przeniesione w dół; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Metoda kończy się niepowodzeniem, jeśli narzędzie, które określa *pTool* nie znajduje się na liście wewnętrznej lub jeśli narzędzie jest ostatnio na liście.

## <a name="cusertoolsmanagermovetoolup"></a><a name="movetoolup"></a>CUserToolsManager::MoveToolUp

Przenosi określone narzędzie użytkownika w górę na liście narzędzi użytkownika.

```
BOOL MoveToolUp(CUserTool* pTool);
```

### <a name="parameters"></a>Parametry

*pTool (pTool)*<br/>
[w] Określa narzędzie użytkownika do przeniesienia.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli narzędzie użytkownika zostało przeniesione pomyślnie w górę; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Metoda kończy się niepowodzeniem, jeśli narzędzie, które określa parametr *pTool,* nie znajduje się na liście wewnętrznej lub jeśli narzędzie jest pierwszym elementem narzędzia na liście.

## <a name="cusertoolsmanagerremovetool"></a><a name="removetool"></a>CUserToolsManager::RemoveTool

Usuwa określone narzędzie użytkownika z aplikacji.

```
BOOL RemoveTool(CUserTool* pTool);
```

### <a name="parameters"></a>Parametry

*pTool (pTool)*<br/>
[w, na zewnątrz] Wskaźnik do narzędzia użytkownika do usunięcia.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli narzędzie zostało pomyślnie usunięte. W przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli narzędzie zostanie pomyślnie usunięte, ta metoda usuwa *pTool*.

## <a name="cusertoolsmanagersavestate"></a><a name="savestate"></a>CUserToolsManager::Zapisz

Przechowuje informacje o narzędziach użytkownika w rejestrze systemu Windows.

```
BOOL SaveState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[w] Ścieżka do klucza rejestru systemu Windows.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli stan został pomyślnie zapisany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Metoda przechowuje bieżący `CUserToolsManager` stan obiektu w rejestrze systemu Windows.

Zazwyczaj nie trzeba wywoływać tej metody bezpośrednio, [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate) wywołuje ją automatycznie jako część procesu serializacji obszaru roboczego aplikacji.

## <a name="cusertoolsmanagersetdefext"></a><a name="setdefext"></a>CUserToolsManager::SetDefExt

Określa domyślne rozszerzenie używane przez okno dialogowe **Otwieranie pliku** [(CFileDialog Class)](../../mfc/reference/cfiledialog-class.md)w polu **Polecenie** na karcie **Narzędzia** w oknie dialogowym **Dostosowywanie.**

```
void SetDefExt(const CString& strDefExt);
```

### <a name="parameters"></a>Parametry

*strDefExt (strDefExt)*<br/>
[w] Ciąg tekstowy zawierający domyślne rozszerzenie nazwy pliku.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby określić domyślne rozszerzenie nazwy pliku w oknie dialogowym **Otwieranie pliku,** które jest wyświetlane, gdy użytkownik wybierze aplikację do skojarzenia z narzędziem użytkownika. Wartość domyślna to "exe".

## <a name="cusertoolsmanagersetfilter"></a><a name="setfilter"></a>CUserToolsManager::SetFilter

Określa filtr plików używany w polu **Polecenie** na karcie **Narzędzia** okna dialogowego Dostosowywanie używane przez okno dialogowe **Otwieranie** **pliku** [(CFileDialog Class).](../../mfc/reference/cfiledialog-class.md)

```
void SetFilter(const CString& strFilter);
```

### <a name="parameters"></a>Parametry

*strFilter (filtr strFilter)*<br/>
[w] Określa filtr.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)<br/>
[Klasa CUserTool](../../mfc/reference/cusertool-class.md)
