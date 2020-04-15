---
title: Klasa CMouseManager
ms.date: 11/04/2016
f1_keywords:
- CMouseManager
- AFXMOUSEMANAGER/CMouseManager
- AFXMOUSEMANAGER/CMouseManager::AddView
- AFXMOUSEMANAGER/CMouseManager::GetViewDblClickCommand
- AFXMOUSEMANAGER/CMouseManager::GetViewIconId
- AFXMOUSEMANAGER/CMouseManager::GetViewIdByName
- AFXMOUSEMANAGER/CMouseManager::GetViewNames
- AFXMOUSEMANAGER/CMouseManager::LoadState
- AFXMOUSEMANAGER/CMouseManager::SaveState
- AFXMOUSEMANAGER/CMouseManager::SetCommandForDblClk
helpviewer_keywords:
- CMouseManager [MFC], AddView
- CMouseManager [MFC], GetViewDblClickCommand
- CMouseManager [MFC], GetViewIconId
- CMouseManager [MFC], GetViewIdByName
- CMouseManager [MFC], GetViewNames
- CMouseManager [MFC], LoadState
- CMouseManager [MFC], SaveState
- CMouseManager [MFC], SetCommandForDblClk
ms.assetid: a4d05017-4e44-4a40-8b57-4ece0de20481
ms.openlocfilehash: d05a2e186f001a69310e99cec013193a4d1bff3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319721"
---
# <a name="cmousemanager-class"></a>Klasa CMouseManager

Umożliwia użytkownikowi skojarzenie różnych poleceń z określonym obiektem [CView,](../../mfc/reference/cview-class.md) gdy użytkownik kliknie dwukrotnie wewnątrz tego widoku.

## <a name="syntax"></a>Składnia

```
class CMouseManager : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMouseManager::AddView](#addview)|Dodaje `CView` obiekt do okna dialogowego **Dostosowywanie.** Okno dialogowe **Dostosowywanie** umożliwia użytkownikowi skojarzenie dwukrotnego kliknięcia z poleceniem dla każdego z wymienionych widoków.|
|[CMouseManager::GetViewDblClickCommand](#getviewdblclickcommand)|Zwraca polecenie, które jest wykonywane, gdy użytkownik kliknie dwukrotnie wewnątrz podanego widoku.|
|[CMouseManager::GetViewIconId](#getviewiconid)|Zwraca ikonę skojarzoną z podanym identyfikatorem widoku.|
|[CMouseManager::GetViewIdByName](#getviewidbyname)|Zwraca identyfikator widoku skojarzony z podana nazwą widoku.|
|[CMouseManager::GetViewNames](#getviewnames)|Pobiera listę wszystkich dodanych nazw widoków.|
|[CMouseManager::Stan obciążenia](#loadstate)|Ładuje `CMouseManager` stan z rejestru systemu Windows.|
|[CMouseManager::Stan zapisu](#savestate)|Zapisuje `CMouseManager` stan do rejestru systemu Windows.|
|[CMouseManager::SetCommandForDblClk](#setcommandfordblclk)|Kojarzy podane polecenie i podany widok.|

## <a name="remarks"></a>Uwagi

Klasa `CMouseManager` przechowuje kolekcję `CView` obiektów. Każdy widok jest identyfikowany przez nazwę i identyfikator. Widoki te są wyświetlane w oknie dialogowym **Dostosowywanie.** Użytkownik może zmienić polecenie skojarzone z dowolnym widokiem za pośrednictwem okna dialogowego **Dostosowywanie.** Skojarzone polecenie jest wykonywane, gdy użytkownik kliknie dwukrotnie w tym widoku. Aby obspożyć to z punktu widzenia kodowania, należy przetworzyć komunikat WM_LBUTTONDBLCLK i wywołać [CWinAppEx::OnViewDoubleClick](../../mfc/reference/cwinappex-class.md#onviewdoubleclick) funkcji w kodzie dla tego `CView` obiektu..

Obiektu nie należy `CMouseManager` tworzyć ręcznie. Zostanie on utworzony przez ramy aplikacji. Zostanie również automatycznie zniszczone, gdy użytkownik zakończy działanie aplikacji. Aby uzyskać wskaźnik do menedżera myszy dla aplikacji, zadzwoń [CWinAppEx::GetMouseManager](../../mfc/reference/cwinappex-class.md#getmousemanager).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CMouseManager`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxmousemanager.h

## <a name="cmousemanageraddview"></a><a name="addview"></a>CMouseManager::AddView

Rejestruje [obiekt CView](../../mfc/reference/cview-class.md) z [CMouseManager Klasy](../../mfc/reference/cmousemanager-class.md) do obsługi niestandardowego zachowania myszy.

```
BOOL AddView(
    int iViewId,
    UINT uiViewNameResId,
    UINT uiIconId = 0);

BOOL AddView(
    int iId,
    LPCTSTR lpszViewName,
    UINT uiIconId = 0);
```

### <a name="parameters"></a>Parametry

*Identyfikator iViewId*<br/>
[w] Identyfikator widoku.

*interfejs użytkownika uiViewNameResId*<br/>
[w] Identyfikator ciągu zasobu, który odwołuje się do nazwy widoku.

*interfejs użytkownika*<br/>
[w] Identyfikator ikony widoku.

*Iid*<br/>
[w] Identyfikator widoku.

*lpszViewName (nazwa widokowa)*<br/>
[w] Nazwa widoku.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby obsługiwać niestandardowe zachowanie myszy, widok `CMouseManager` musi być zarejestrowany w obiekcie. Każdy obiekt pochodzący `CView` z klasy można zarejestrować w menedżerze myszy. Ciąg i ikona skojarzona z widokiem są wyświetlane na karcie **Mysz** w oknie dialogowym **Dostosowywanie.**

Programator jest odpowiedzialny za tworzenie i utrzymywanie identyfikatorów widoku, takich jak *iViewId* i *iId.*

Aby uzyskać więcej informacji na temat zapewniania niestandardowego zachowania myszy, zobacz [Dostosowywanie klawiatury i myszy](../../mfc/keyboard-and-mouse-customization.md).

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMouseManager` pobrać wskaźnik `CWinAppEx::GetMouseManager` do obiektu `AddView` przy `CMouseManager` użyciu metody i metody w klasie. Ten fragment kodu jest częścią [próbki kolekcji stanu](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StateCollection#4](../../mfc/reference/codesnippet/cpp/cmousemanager-class_1.cpp)]

## <a name="cmousemanagergetviewdblclickcommand"></a><a name="getviewdblclickcommand"></a>CMouseManager::GetViewDblClickCommand

Zwraca polecenie, które jest wykonywane, gdy użytkownik kliknie dwukrotnie wewnątrz podanego widoku.

```
UINT GetViewDblClickCommand(int iId) const;
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[w] Identyfikator widoku.

### <a name="return-value"></a>Wartość zwracana

Identyfikator polecenia, jeśli widok jest skojarzony z poleceniem; w przeciwnym razie 0.

## <a name="cmousemanagergetviewiconid"></a><a name="getviewiconid"></a>CMouseManager::GetViewIconId

Pobiera ikonę skojarzoną z identyfikatorem widoku.

```
UINT GetViewIconId(int iViewId) const;
```

### <a name="parameters"></a>Parametry

*Identyfikator iViewId*<br/>
[w] Identyfikator widoku.

### <a name="return-value"></a>Wartość zwracana

Identyfikator zasobu ikony, jeśli zakończy się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda zakończy się niepowodzeniem, jeśli widok nie jest po raz pierwszy zarejestrowany przy użyciu [CMouseManager::AddView](#addview).

## <a name="cmousemanagergetviewidbyname"></a><a name="getviewidbyname"></a>CMouseManager::GetViewIdByName

Pobiera identyfikator widoku skojarzony z nazwą widoku.

```
int GetViewIdByName(LPCTSTR lpszName) const;
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
[w] Nazwa widoku.

### <a name="return-value"></a>Wartość zwracana

Identyfikator widoku, jeśli zakończy się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda przeszukuje widoki zarejestrowane przy użyciu [programu CMouseManager::AddView](#addview).

## <a name="cmousemanagergetviewnames"></a><a name="getviewnames"></a>CMouseManager::GetViewNames

Pobiera listę wszystkich zarejestrowanych nazw widoków.

```
void GetViewNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>Parametry

*nazwa listy*<br/>
[na zewnątrz] Odwołanie do `CStringList` obiektu.

### <a name="remarks"></a>Uwagi

Ta metoda wypełnia `listOfNames` parametr nazwami wszystkich widoków zarejestrowanych przy użyciu [programu CMouseManager::AddView](#addview).

## <a name="cmousemanagerloadstate"></a><a name="loadstate"></a>CMouseManager::Stan obciążenia

Ładuje stan [CMouseManager Klasy](../../mfc/reference/cmousemanager-class.md) z rejestru.

```
BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[w] Ścieżka klucza rejestru.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Informacje o stanie załadowane z rejestru obejmują zarejestrowane widoki, identyfikatory widoku i skojarzone polecenia. Jeśli *parametrem lpszProfileName* jest NULL, `CMouseManager` ta funkcja ładuje dane z domyślnej lokalizacji rejestru kontrolowanej przez [klasę CWinAppEx](../../mfc/reference/cwinappex-class.md).

W większości przypadków nie trzeba wywoływać tej funkcji bezpośrednio. Jest wywoływana jako część procesu inicjowania obszaru roboczego. Aby uzyskać więcej informacji na temat procesu inicjowania obszaru roboczego, zobacz [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate).

## <a name="cmousemanagersavestate"></a><a name="savestate"></a>CMouseManager::Stan zapisu

Zapisuje stan [CMouseManager Klasy](../../mfc/reference/cmousemanager-class.md) do rejestru.

```
BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[w] Ścieżka klucza rejestru.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Informacje o stanie zapisane w rejestrze obejmują wszystkie zarejestrowane widoki, identyfikatory widoku i skojarzone polecenia. Jeśli *parametrem lpszProfileName* jest NULL, `CMouseManager` ta funkcja zapisuje dane do domyślnej lokalizacji rejestru kontrolowanej przez [klasę CWinAppEx](../../mfc/reference/cwinappex-class.md).

W większości przypadków nie trzeba wywoływać tej funkcji bezpośrednio. Jest wywoływana jako część procesu serializacji obszaru roboczego. Aby uzyskać więcej informacji na temat procesu serializacji obszaru roboczego, zobacz [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate).

## <a name="cmousemanagersetcommandfordblclk"></a><a name="setcommandfordblclk"></a>CMouseManager::SetCommandForDblClk

Kojarzy niestandardowe polecenie z widokiem, który jest najpierw zarejestrowany w menedżerze myszy.

```
void SetCommandForDblClk(
    int iViewId,
    UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*Identyfikator iViewId*<br/>
[w] Identyfikator widoku.

*Uicmd*<br/>
[w] Identyfikator polecenia.

### <a name="remarks"></a>Uwagi

Aby skojarzyć polecenie niestandardowe z widokiem, należy najpierw zarejestrować widok przy użyciu [programu CMouseManager::AddView](#addview). Metoda `AddView` wymaga identyfikatora widoku jako parametru wejściowego. Po zarejestrowaniu widoku można `CMouseManager::SetCommandForDblClk` wywołać z tym samym parametrem `AddView`wejściowym identyfikatora widoku, który został podany do . Następnie, gdy użytkownik dwukrotnie kliknie mysz w widoku zarejestrowanym, aplikacja wykona polecenie wskazane przez *uiCmd.* Aby obsługiwać niestandardowe zachowanie myszy, należy również dostosować widok zarejestrowany w menedżerze myszy. Aby uzyskać więcej informacji na temat niestandardowego zachowania myszy, zobacz [Dostosowywanie klawiatury i myszy](../keyboard-and-mouse-customization.md).

Jeśli *uiCmd* jest ustawiona na 0, określony widok nie jest już skojarzony z poleceniem.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)<br/>
[Dostosowywanie klawiatury i myszy](../../mfc/keyboard-and-mouse-customization.md)
