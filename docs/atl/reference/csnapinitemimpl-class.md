---
title: Klasa CSnapInItemImpl
ms.date: 11/04/2016
f1_keywords:
- CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl::CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl::AddMenuItems
- ATLSNAP/ATL::CSnapInItemImpl::Command
- ATLSNAP/ATL::CSnapInItemImpl::CreatePropertyPages
- ATLSNAP/ATL::CSnapInItemImpl::FillData
- ATLSNAP/ATL::CSnapInItemImpl::GetResultPaneInfo
- ATLSNAP/ATL::CSnapInItemImpl::GetResultViewType
- ATLSNAP/ATL::CSnapInItemImpl::GetScopePaneInfo
- ATLSNAP/ATL::CSnapInItemImpl::Notify
- ATLSNAP/ATL::CSnapInItemImpl::QueryPagesFor
- ATLSNAP/ATL::CSnapInItemImpl::SetMenuInsertionFlags
- ATLSNAP/ATL::CSnapInItemImpl::SetToolbarButtonInfo
- ATLSNAP/ATL::CSnapInItemImpl::UpdateMenuState
- ATLSNAP/ATL::CSnapInItemImpl::UpdateToolbarButton
- ATLSNAP/ATL::CSnapInItemImpl::m_bstrDisplayName
- ATLSNAP/ATL::CSnapInItemImpl::m_resultDataItem
- ATLSNAP/ATL::CSnapInItemImpl::m_scopeDataItem
helpviewer_keywords:
- snap-ins, data items
- snap-ins, ATL support for
- CSnapInItemImpl class
- snap-ins
ms.assetid: 52caefbd-9eae-49b0-add2-d55524271aa7
ms.openlocfilehash: 27f3e8a17a9538a72a6592177a88a9b415b1a27c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57297815"
---
# <a name="csnapinitemimpl-class"></a>Klasa CSnapInItemImpl

Ta klasa dostarcza metody implementacji obiektu przystawki węzła.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template <class T, BOOL bIsExtension = FALSE>
class ATL_NO_VTABLE CSnapInItemImpl : public CSnapInItem
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Z klasą pochodną `CSnapInItemImpl`.

*bIsExtension*<br/>
Wartość TRUE, jeśli obiekt jest rozszerzeniem przystawki; w przeciwnym razie wartość FALSE.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSnapInItemImpl::CSnapInItemImpl](#csnapinitemimpl)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSnapInItemImpl::AddMenuItems](#addmenuitems)|Dodaje elementy menu do menu kontekstowego.|
|[CSnapInItemImpl::Command](#command)|Metoda wywoływana przez konsolę, po wybraniu elementu menu niestandardowe.|
|[CSnapInItemImpl::CreatePropertyPages](#createpropertypages)|Dodaje strony do arkusza właściwości przystawki.|
|[CSnapInItemImpl::FillData](#filldata)|Kopiuje informacje obiektu przystawki do określonego strumienia.|
|[CSnapInItemImpl::GetResultPaneInfo](#getresultpaneinfo)|Pobiera `RESULTDATAITEM` struktury przystawki.|
|[CSnapInItemImpl::GetResultViewType](#getresultviewtype)|Określa typ widoku użytego w okienku wyników.|
|[CSnapInItemImpl::GetScopePaneInfo](#getscopepaneinfo)|Pobiera `SCOPEDATAITEM` struktury przystawki.|
|[CSnapInItemImpl::Notify](#notify)|Metoda wywoływana przez konsolę, aby powiadomić przystawki akcji podjętych przez użytkownika.|
|[CSnapInItemImpl::QueryPagesFor](#querypagesfor)|Wywołuje się, by sprawdzić, czy węzeł w przystawce obsługuje strony właściwości.|
|[CSnapInItemImpl::SetMenuInsertionFlags](#setmenuinsertionflags)|Modyfikuje flagi wstawiania menu dla obiektu przystawki.|
|[CSnapInItemImpl::SetToolbarButtonInfo](#settoolbarbuttoninfo)|Ustawia informacje o przycisku określonego paska narzędzi.|
|[CSnapInItemImpl::UpdateMenuState](#updatemenustate)|Aktualizuje stan element menu kontekstowego.|
|[CSnapInItemImpl::UpdateToolbarButton](#updatetoolbarbutton)|Aktualizuje stan przycisku określonego paska narzędzi.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CSnapInItemImpl::m_bstrDisplayName](#m_bstrdisplayname)|Nazwa obiektu przystawki.|
|[CSnapInItemImpl::m_resultDataItem](#m_resultdataitem)|Windows `RESULTDATAITEM` struktury używane przez `CSnapInItemImpl` obiektu.|
|[CSnapInItemImpl::m_scopeDataItem](#m_scopedataitem)|Windows `SCOPEDATAITEM` struktury używane przez `CSnapInItemImpl` obiektu.|

## <a name="remarks"></a>Uwagi

`CSnapInItemImpl` udostępnia podstawową implementację obiektu przystawki węzła, takie jak dodawanie elementów menu i paski narzędzi i przesyłania poleceń dla węzła przystawki do funkcji odpowiedni program obsługi. Te funkcje są implementowane przy użyciu kilku różnych interfejsów i mapowania typów. Domyślna implementacja obsługuje powiadomień wysyłanych do obiektu węzła przez określenie poprawne wystąpienie klasy pochodnej, a następnie przekazywania wiadomości do wystąpienia jest poprawny.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CSnapInItem`

`CSnapInItemImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsnap.h

##  <a name="addmenuitems"></a>  CSnapInItemImpl::AddMenuItems

Ta metoda implementuje funkcję Win32 [IExtendContextMenu::AddMenuItems](/windows/desktop/api/mmc/nf-mmc-iextendcontextmenu-addmenuitems).

```
AddMenuItems(
    LPCONTEXTMENUCALLBACK piCallback,
    long* pInsertionAllowed,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Parametry

*piCallback*<br/>
[in] Wskaźnik do `IContextMenuCallback` , można dodać elementy do menu kontekstowego.

*pInsertionAllowed*<br/>
[out w] Identyfikuje programu Microsoft Management Console MMC zdefiniowane przez element menu punkty wstawienia, które mogą być używane. Może to być kombinacją następujących flag:

- CCM_INSERTIONALLOWED_TOP elementy mogą być wstawiane w górnej części menu kontekstowego.

- CCM_INSERTIONALLOWED_NEW elementy mogą być wstawiane w podmenu Utwórz nową.

- CCM_INSERTIONALLOWED_TASK elementy mogą być wstawiane w podmenu zadania.

- W menu Widok paska narzędzi lub w podmenu Wyświetl menu kontekstowe w okienku wyników można wstawiać CCM_INSERTIONALLOWED_VIEW elementów.

*type*<br/>
[in] Określa typ obiektu. Może mieć jedną z następujących wartości:

- Obiekt danych CCT_SCOPE zakresu okienka kontekstu.

- Obiekt danych CCT_RESULT kontekstu w okienku wyników.

- Obiekt danych CCT_SNAPIN_MANAGER przystawki Menedżer kontekstu.

- Obiekt danych CCT_UNINITIALIZED typ jest nieprawidłowy.

##  <a name="command"></a>  CSnapInItemImpl::Command

Ta metoda implementuje funkcję Win32 [IExtendContextMenu::Command](/windows/desktop/api/mmc/nf-mmc-iextendcontextmenu-command).

```
Command(long lCommandID, DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Parametry

*lCommandID*<br/>
[in] Określa identyfikator polecenia elementu menu.

*type*<br/>
[in] Określa typ obiektu. Może mieć jedną z następujących wartości:

- Obiekt danych CCT_SCOPE zakresu okienka kontekstu.

- Obiekt danych CCT_RESULT kontekstu w okienku wyników.

- Obiekt danych CCT_SNAPIN_MANAGER przystawki Menedżer kontekstu.

- Obiekt danych CCT_UNINITIALIZED typ jest nieprawidłowy.

##  <a name="createpropertypages"></a>  CSnapInItemImpl::CreatePropertyPages

Ta metoda implementuje funkcję Win32 [IExtendPropertySheet::CreatePropertyPages](/windows/desktop/api/mmc/nn-mmc-iextendpropertysheet2).

```
CreatePropertyPages(
    LPPROPERTYSHEETCALLBACK lpProvider,
    long handle,
    IUnknown* pUnk,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Parametry

*lpProvider*<br/>
[in] Wskaźnik do `IPropertySheetCallback` interfejsu.

*handle*<br/>
[in] Określa dojście przekierowywać MMCN_PROPERTY_CHANGE komunikatu powiadomienia do klasy odpowiednie dane.

*pUnk*<br/>
[in] Wskaźnik do `IExtendPropertySheet` interfejsu na obiekt, który zawiera informacje o kontekście dotyczące węzła.

*type*<br/>
[in] Określa typ obiektu. Może mieć jedną z następujących wartości:

- Obiekt danych CCT_SCOPE zakresu okienka kontekstu.

- Obiekt danych CCT_RESULT kontekstu w okienku wyników.

- Obiekt danych CCT_SNAPIN_MANAGER przystawki Menedżer kontekstu.

- Obiekt danych CCT_UNINITIALIZED typ jest nieprawidłowy.

##  <a name="csnapinitemimpl"></a>  CSnapInItemImpl::CSnapInItemImpl

Konstruuje `CSnapInItemImpl` obiektu.

```
CSnapInItemImpl();
```

##  <a name="filldata"></a>  CSnapInItemImpl::FillData

Ta funkcja jest wywoływana, aby pobrać informacje o elemencie.

```
FillData(CLIPFORMAT cf, LPSTREAM pStream);
```

### <a name="parameters"></a>Parametry

*cf*<br/>
[in] Format (tekst, tekst sformatowany lub tekstu sformatowanego przy użyciu elementów OLE) ze Schowka.

*pStream*<br/>
[in] Wskaźnik do strumienia, zawierający dane obiektu.

### <a name="remarks"></a>Uwagi

Aby prawidłowo zaimplementować tę funkcję, należy skopiować poprawnych informacji w strumieniu (*pStream*), w zależności od formatu Schowka wskazywanym przez *cf*.

##  <a name="getresultviewtype"></a>  CSnapInItemImpl::GetResultViewType

Wywołaj tę funkcję, aby pobrać od typu widoku dla okienka wyników przystawki obiektu.

```
GetResultViewType(
    LPOLESTR* ppViewType,
    long* pViewOptions);
```

### <a name="parameters"></a>Parametry

*ppViewType*<br/>
[out] Wskaźnik na adres typu zwracanego widoku.

*pViewOptions*<br/>
[out] Wskaźnik do wyliczenia MMC_VIEW_OPTIONS zapewnia opcje określone przez właściciela przystawkę konsoli. Ta wartość może być jedną z następujących czynności:

- MMC_VIEW_OPTIONS_NOLISTVIEWS = 0x00000001 nakazuje konsoli Powstrzymaj się od prezentacji opcji widoku listy standardowych w **widoku** menu. Umożliwia wyświetlić swoje własne widoki niestandardowe tylko w okienku widoku wyników przystawki. Jest to tylko flagi opcji zdefiniowane w tej chwili.

- MMC_VIEW_OPTIONS_NONE = 0 umożliwia domyślne opcje widoku.

##  <a name="getscopepaneinfo"></a>  CSnapInItemImpl::GetScopePaneInfo

Wywołaj tę funkcję, aby pobrać `SCOPEDATAITEM` struktury przystawki.

```
GetScopePaneInfo (SCOPEDATAITEM* pScopeDataItem);
```

### <a name="parameters"></a>Parametry

*pScopeDataItem*<br/>
[out] Wskaźnik do `SCOPEDATAITEM` struktury `CSnapInItemImpl` obiektu.

##  <a name="getresultpaneinfo"></a>  CSnapInItemImpl::GetResultPaneInfo

Wywołaj tę funkcję, aby pobrać `RESULTDATAITEM` struktury przystawki.

```
GetResultPaneInfo (RESULTDATAITEM* pResultDataItem);
```

### <a name="parameters"></a>Parametry

*pResultDataItem*<br/>
[out] Wskaźnik do `RESULTDATAITEM` struktury `CSnapInItemImpl` obiektu.

##  <a name="m_bstrdisplayname"></a>  CSnapInItemImpl::m_bstrDisplayName

Zawiera ciąg wyświetlany dla elementu węzła.

```
CComBSTR m_bstrDisplayName;
```

##  <a name="m_scopedataitem"></a>  CSnapInItemImpl::m_scopeDataItem

`SCOPEDATAITEM` Strukturę obiektu danych przystawki.

```
SCOPEDATAITEM m_scopeDataItem;
```

##  <a name="m_resultdataitem"></a>  CSnapInItemImpl::m_resultDataItem

[RESULTDATAITEM](/windows/desktop/api/mmc/ns-mmc-resultdataitem) strukturę obiektu danych przystawki.

```
RESULTDATAITEM m_resultDataItem;
```

##  <a name="notify"></a>  CSnapInItemImpl::Notify

Wywołuje się, gdy obiekt przystawki jest podjęte przez użytkownika.

```
STDMETHOD(Notify)(
    MMC_NOTIFY_TYPE event,
    long arg,
    long param,
    IComponentData* pComponentData,
    IComponent* pComponent,
    DATA_OBJECT_TYPES type) = 0;
```

### <a name="parameters"></a>Parametry

*event*<br/>
[in] Określa akcję podejmowaną przez użytkownika. Możliwe są następujące powiadomienia:

- MMCN_ACTIVATE wysyłane, gdy okno jest aktywowane i dezaktywowane.

- MMCN_ADD_IMAGES wysyłane dodać obrazy do okienka wyników.

- MMCN_BTN_CLICK wysyłany, gdy użytkownik kliknie jeden z przycisków paska narzędzi.

- MMCN_CLICK wysyłany, gdy użytkownik kliknie przycisk myszy elementu widoku listy.

- MMCN_DBLCLICK wysyłany, gdy użytkownik dwukrotnie kliknie przycisk myszy elementu widoku listy.

- MMCN_DELETE wysyłane do informowania przystawki, który obiekt powinien zostać usunięty.

- MMCN_EXPAND wysyłany, gdy folder musi być rozwinięty lub zaistniałych.

- MMCN_MINIMIZED wysyłane, gdy okno jest zminimalizowane lub zmaksymalizowane.

- MMCN_PROPERTY_CHANGE wysyłane, aby powiadomić obiekt przystawki, który widok przystawki obiektu ma zostać zmieniona.

- MMCN_REMOVE_CHILDREN wysyłany, gdy ta przystawka należy usunąć całe poddrzewo, dodane poniżej określonego węzła.

- MMCN_RENAME wysyłane przy pierwszym zapytaniem umożliwiającego zmianę nazwy i po raz drugi w celu zmiany nazwy.

- MMCN_SELECT wysyłane po wybraniu elementu w zakresie lub wynik w okienku widoku.

- MMCN_SHOW wysyłany, gdy wybierana lub wyłączona po raz pierwszy element zakresu.

- MMCN_VIEW_CHANGE wysyłany, gdy ta przystawka można zaktualizować wszystkich widoków po wprowadzeniu zmiany.

*ARG*<br/>
[in] Zależy od typu powiadomienia.

*param*<br/>
[in] Zależy od typu powiadomienia.

*pComponentData*<br/>
[out] Wskaźnik do obiektu implementującego `IComponentData`. Ten parametr ma wartość NULL, jeśli powiadomienia nie są przekazywane z `IComponentData::Notify`.

*pComponent*<br/>
[out] Wskaźnik do obiektu, który implementuje `IComponent`. Ten parametr ma wartość NULL, jeśli powiadomienia nie są przekazywane z `IComponent::Notify`.

*type*<br/>
[in] Określa typ obiektu. Może mieć jedną z następujących wartości:

- Obiekt danych CCT_SCOPE zakresu okienka kontekstu.

- Obiekt danych CCT_RESULT kontekstu w okienku wyników.

- Obiekt danych CCT_SNAPIN_MANAGER przystawki Menedżer kontekstu.

- Obiekt danych CCT_UNINITIALIZED typ jest nieprawidłowy.

##  <a name="querypagesfor"></a>  CSnapInItemImpl::QueryPagesFor

Wywołuje się, by sprawdzić, czy węzeł w przystawce obsługuje strony właściwości.

```
QueryPagesFor(DATA_OBJECT_TYPES type);
```

##  <a name="setmenuinsertionflags"></a>  CSnapInItemImpl::SetMenuInsertionFlags

Wywołaj tę funkcję do modyfikowania flag wstawiania menu, określony przez *pInsertionAllowed*, dla obiektu przystawki.

```
void SetMenuInsertionFlags(
    bool bBeforeInsertion,
    long* pInsertionAllowed);
```

### <a name="parameters"></a>Parametry

*bBeforeInsertion*<br/>
[in] Wartość różną od zera, jeśli funkcja powinna być wywoływana przed elementy są dodawane do menu kontekstowego. w przeciwnym razie 0.

*pInsertionAllowed*<br/>
[out w] Identyfikuje programu Microsoft Management Console MMC zdefiniowane przez element menu punkty wstawienia, które mogą być używane. Może to być kombinacją następujących flag:

- CCM_INSERTIONALLOWED_TOP elementy mogą być wstawiane w górnej części menu kontekstowego.

- CCM_INSERTIONALLOWED_NEW elementy mogą być wstawiane w podmenu Utwórz nową.

- CCM_INSERTIONALLOWED_TASK elementy mogą być wstawiane w podmenu zadania.

- W menu Widok paska narzędzi lub w podmenu Wyświetl menu kontekstowe w okienku wyników można wstawiać CCM_INSERTIONALLOWED_VIEW elementów.

### <a name="remarks"></a>Uwagi

Jeśli tworzysz Przystawka podstawowa, możesz zresetować dowolne flagi wstawiania jako sposób ograniczyć rodzaj elementy menu, które można dodać rozszerzenia innych firm. Na przykład Przystawka podstawowa wyczyścić flagę CCM_INSERTIONALLOWED_NEW, aby uniemożliwić dodawanie własnych tworzenie nowych elementów menu rozszerzeń.

Nie należy próbować ustawić bity *pInsertionAllowed* który początkowo zostały wyczyszczone. Przyszłych wersjach programu MMC może używać usługi bits nie jest obecnie zdefiniowana, więc nie należy zmieniać bitów, które są aktualnie nie zdefiniowane.

##  <a name="settoolbarbuttoninfo"></a>  CSnapInItemImpl::SetToolbarButtonInfo

Wywołaj tę funkcję, aby zmodyfikować style do przycisku paska narzędzi, obiektu przystawki, przed utworzeniem paska narzędzi.

```
void SetToolbarButtonInfo(
    UINT id,
    BYTE* fsState,
    BYTE* fsType);
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Identyfikator przycisku paska narzędzi, należy ustawić.

*fsState*<br/>
[in] Flagi stanu przycisku. Może być co najmniej jeden z następujących czynności:

- TBSTATE_CHECKED przycisku styl TBSTYLE_CHECKED i jest naciskana.

- TBSTATE_ENABLED przycisku akceptuje dane wejściowe użytkownika. Przycisk, który nie ma w tym stanie nie akceptuje dane wejściowe użytkownika i jest niedostępna.

- TBSTATE_HIDDEN przycisk nie jest widoczna i nie może odbierać dane wejściowe użytkownika.

- TBSTATE_INDETERMINATE przycisk jest niedostępny.

- Jest naciskana TBSTATE_PRESSED przycisku.

- Podział wiersza A TBSTATE_WRAP poniżej przycisku. Przycisk musi mieć również TBSTATE_ENABLED.

*fsType*<br/>
[in] Flagi stanu przycisku. Może być co najmniej jeden z następujących czynności:

- TBSTYLE_BUTTON tworzy standardowy przycisku polecenia.

- Tworzy TBSTYLE_CHECK przycisk, który włącza/wyłącza między Stanami zostanie wciśnięty lub naciśnięcia nie zawsze użytkownik klika go. Ten przycisk ma inny kolor tła, gdy jest ona w stanie po naciśnięciu.

- Tworzy TBSTYLE_CHECKGROUP, który naciśnięty przycisk wyboru, która pozostaje, dopóki nie zostanie naciśnięty inny przycisk w grupie.

- Tworzy TBSTYLE_GROUP, który naciśnięty przycisk, który pozostaje, dopóki nie zostanie naciśnięty inny przycisk w grupie.

- TBSTYLE_SEP tworzy separator, zapewniając mały odstęp między grupami przycisku. Przycisk, który ma ten styl nie odbiera danych wejściowych użytkownika.

##  <a name="updatemenustate"></a>  CSnapInItemImpl::UpdateMenuState

Wywołaj tę funkcję, aby zmodyfikować element menu, zanim zostanie wstawiony do menu kontekstowego obiektu przystawki.

```
void UpdateMenuState(
    UINT id,
    LPTSTR pBuf,
    UINT* flags);
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Identyfikator elementu menu, należy ustawić.

*pBuf*<br/>
[in] Wskaźnik do ciągu dla elementu menu aktualizacji.

*flagi*<br/>
[in] Określa nowy stan flagi. Może to być kombinacją następujących flag:

- MF_POPUP Określa, że jest to podmenu w menu kontekstowym. Elementy menu, punkty wstawienia i dalsze podmenu, które mogą być dodawane do tego podmenu przy użyciu jego `lCommandID` jako ich `IInsertionPointID`.

- MF_BITMAP i MF_OWNERDRAW te flagi są niedozwolone i będą powodować zwracana wartość wynosząca E_INVALIDARG.

- MF_SEPARATOR rysuje poziomej linii podziału. Tylko `IContextMenuProvider` można dodawać elementów menu za pomocą zestawu MF_SEPARATOR.

- MF_CHECKED umieszcza znacznik wyboru obok pozycji menu.

- Wyłącza MF_DISABLED elementu menu, więc nie może zostać wybrana, ale flagi nie szary go.

- MF_ENABLED umożliwia elementu menu, dzięki czemu można ją wybrać, przywracając go ze stanu wygaszone.

- MF_GRAYED elementu menu powoduje wyłączenie go graying, więc nie może zostać wybrana.

- Funkcje MF_MENUBARBREAK taka sama jak MF_MENUBREAK flagę dla paska menu. Menu rozwijane, podmenu lub menu skrótów nowej kolumny, która jest oddzielone z kolumny stare pionowym wierszem.

- MF_MENUBREAK umieszcza elementu w nowym wierszu (na pasku menu) lub w nowej kolumnie (w przypadku podmenu, menu rozwijane lub menu skrótów) bez oddzielenie kolumn.

- MF_UNCHECKED nie umieszcza znacznik wyboru obok pozycji (ustawienie domyślne).

Nie można używać następujących grup flagi razem:

- MF_DISABLED MF_ENABLED i MF_GRAYED.

- MF_MENUBARBREAK i MF_MENUBREAK.

- MF_CHECKED i MF_UNCHECKED.

##  <a name="updatetoolbarbutton"></a>  CSnapInItemImpl::UpdateToolbarButton

Wywołaj tę funkcję, aby zmodyfikować przycisku paska narzędzi, obiektu przystawki, przed wyświetleniem.

```
BOOL UpdateToolbarButton(UINT id, BYTE fsState);
```

### <a name="parameters"></a>Parametry

*id*<br/>
Określa identyfikator przycisku przycisku paska narzędzi do zaktualizowania.

*fsState*<br/>
Określa stan przycisku paska narzędzi. Zwraca wartość TRUE, jeśli ten stan do ustawienia. Może to być kombinacją następujących flag:

- WŁĄCZONO przycisku akceptuje dane wejściowe użytkownika. Przycisk, który nie ma w tym stanie nie akceptuje dane wejściowe użytkownika i jest niedostępna.

- SPRAWDZANE, ten przycisk ma stylu ZAZNACZENIA i jest naciskana.

- UKRYTY przycisk nie jest widoczna i nie może odbierać dane wejściowe użytkownika.

- Nieokreślony przycisk jest niedostępny.

- Jest naciskana BUTTONPRESSED przycisku.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../../atl/atl-class-overview.md)
