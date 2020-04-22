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
ms.openlocfilehash: 04eeba0239789b9f3220b7bfece3eb41dc7f2826
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746425"
---
# <a name="csnapinitemimpl-class"></a>Klasa CSnapInItemImpl

Ta klasa zawiera metody implementacji obiektu węzła przystawki.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class T, BOOL bIsExtension = FALSE>
class ATL_NO_VTABLE CSnapInItemImpl : public CSnapInItem
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa, pochodząca od `CSnapInItemImpl`.

*bIsRozcisknięcie*<br/>
PRAWDA, jeśli obiekt jest rozszerzeniem przystawki; w przeciwnym razie FALSE.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSnapInItemImpl::CSnapInItemImpl](#csnapinitemimpl)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSnapInItemImpl::AddMenuItems](#addmenuitems)|Dodaje elementy menu do menu kontekstowego.|
|[CSnapInItemImpl::Polecenie](#command)|Wywoływana przez konsolę po wybraniu niestandardowego elementu menu.|
|[CSnapInItemImpl::CreatePropertyPages](#createpropertypages)|Dodaje strony do arkusza właściwości przystawki.|
|[CSnapInItemImpl::FillData](#filldata)|Kopiuje informacje o obiekcie przystawek do określonego strumienia.|
|[CSnapInItemImpl::GetResultPaneInfo](#getresultpaneinfo)|Pobiera strukturę `RESULTDATAITEM` przystawki.|
|[CSnapInItemImpl::GetResultViewType](#getresultviewtype)|Określa typ widoku używanego przez okienko wyników.|
|[CSnapInItemImpl::GetScopePaneInfo](#getscopepaneinfo)|Pobiera strukturę `SCOPEDATAITEM` przystawki.|
|[CSnapInItemImpl::Powiadom](#notify)|Wywoływane przez konsolę, aby powiadomić przystawkę o akcjach podjętych przez użytkownika.|
|[CSnapInItemImpl::QueryPagesFor](#querypagesfor)|Wywoływany, aby sprawdzić, czy węzeł przystawki obsługuje strony właściwości.|
|[CSnapInItemImpl::SetMenuInsertionSlags](#setmenuinsertionflags)|Modyfikuje flagi wstawiania menu dla obiektu przystawkowego.|
|[CSnapInItemImpl::SetToolbarButtonInfo](#settoolbarbuttoninfo)|Ustawia informacje o określonym przycisku paska narzędzi.|
|[CSnapInItemImpl::UpdateMenuState](#updatemenustate)|Aktualizuje stan elementu menu kontekstowego.|
|[CSnapInItemImpl::UpdateToolbarButton](#updatetoolbarbutton)|Aktualizuje stan określonego przycisku paska narzędzi.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CSnapInItemImpl::m_bstrDisplayName](#m_bstrdisplayname)|Nazwa obiektu przystawki.|
|[CSnapInItemImpl::m_resultDataItem](#m_resultdataitem)|Struktura `RESULTDATAITEM` systemu Windows `CSnapInItemImpl` używana przez obiekt.|
|[CSnapInItemImpl::m_scopeDataItem](#m_scopedataitem)|Struktura `SCOPEDATAITEM` systemu Windows `CSnapInItemImpl` używana przez obiekt.|

## <a name="remarks"></a>Uwagi

`CSnapInItemImpl`zapewnia podstawową implementację obiektu węzła przystawki, takiego jak dodawanie elementów menu i pasków narzędzi oraz przekazywanie poleceń dla węzła przystawki do odpowiedniej funkcji obsługi. Te funkcje są implementowane przy użyciu kilku różnych interfejsów i typów map. Domyślna implementacja obsługuje powiadomienia wysyłane do obiektu węzła, określając poprawne wystąpienie klasy pochodnej, a następnie przesyłając dalej wiadomość do poprawnego wystąpienia.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CSnapInItem`

`CSnapInItemImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsnap.h

## <a name="csnapinitemimpladdmenuitems"></a><a name="addmenuitems"></a>CSnapInItemImpl::AddMenuItems

Ta metoda implementuje funkcję Win32 [IExtendContextMenu::AddMenuItems](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-addmenuitems).

```
AddMenuItems(
    LPCONTEXTMENUCALLBACK piCallback,
    long* pInsertionAllowed,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Parametry

*piCallback (powrót do systemu)*<br/>
[w] Wskaźnik do `IContextMenuCallback` tego, który można dodać elementy do menu kontekstowego.

*PInsertion Dozwolone*<br/>
[w, na zewnątrz] Identyfikuje zdefiniowane w programie Microsoft Management Console (MMC) punkty wstawiania elementu menu, które mogą być używane. Może to być kombinacja następujących flag:

- CCM_INSERTIONALLOWED_TOP Elementy można wstawić u góry menu kontekstowego.

- CCM_INSERTIONALLOWED_NEW Elementy można wstawić w podmenu Utwórz nowe.

- CCM_INSERTIONALLOWED_TASK Elementy można wstawić w podmenu Zadanie.

- CCM_INSERTIONALLOWED_VIEW Elementy można wstawić w menu widoku paska narzędzi lub w podmenu Widok menu kontekstowego okienka wyników.

*Typu*<br/>
[w] Określa typ obiektu. Może mieć jedną z następujących wartości:

- CCT_SCOPE Data obiektu dla kontekstu okienka zakresu.

- CCT_RESULT Data obiektu dla kontekstu okienka wyników.

- CCT_SNAPIN_MANAGER Data obiektu dla kontekstu menedżera przystawki.

- CCT_UNINITIALIZED Data obiekt ma nieprawidłowy typ.

## <a name="csnapinitemimplcommand"></a><a name="command"></a>CSnapInItemImpl::Polecenie

Ta metoda implementuje funkcję Win32 [IExtendContextMenu::Command](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-command).

```
Command(long lCommandID, DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Parametry

*lKommandid*<br/>
[w] Określa identyfikator polecenia elementu menu.

*Typu*<br/>
[w] Określa typ obiektu. Może mieć jedną z następujących wartości:

- CCT_SCOPE Data obiektu dla kontekstu okienka zakresu.

- CCT_RESULT Data obiektu dla kontekstu okienka wyników.

- CCT_SNAPIN_MANAGER Data obiektu dla kontekstu menedżera przystawki.

- CCT_UNINITIALIZED Data obiekt ma nieprawidłowy typ.

## <a name="csnapinitemimplcreatepropertypages"></a><a name="createpropertypages"></a>CSnapInItemImpl::CreatePropertyPages

Ta metoda implementuje funkcję Win32 [IExtendPropertySheet::CreatePropertyPages](/windows/win32/api/mmc/nn-mmc-iextendpropertysheet2).

```
CreatePropertyPages(
    LPPROPERTYSHEETCALLBACK lpProvider,
    long handle,
    IUnknown* pUnk,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Parametry

*lpProvider*<br/>
[w] Wskaźnik do `IPropertySheetCallback` interfejsu.

*Obsługi*<br/>
[w] Określa dojście używane do kierowania komunikatu powiadomienia MMCN_PROPERTY_CHANGE do odpowiedniej klasy danych.

*Punk*<br/>
[w] Wskaźnik do `IExtendPropertySheet` interfejsu na obiekcie, który zawiera informacje kontekstowe o węźle.

*Typu*<br/>
[w] Określa typ obiektu. Może mieć jedną z następujących wartości:

- CCT_SCOPE Data obiektu dla kontekstu okienka zakresu.

- CCT_RESULT Data obiektu dla kontekstu okienka wyników.

- CCT_SNAPIN_MANAGER Data obiektu dla kontekstu menedżera przystawki.

- CCT_UNINITIALIZED Data obiekt ma nieprawidłowy typ.

## <a name="csnapinitemimplcsnapinitemimpl"></a><a name="csnapinitemimpl"></a>CSnapInItemImpl::CSnapInItemImpl

Konstruuje `CSnapInItemImpl` obiekt.

```
CSnapInItemImpl();
```

## <a name="csnapinitemimplfilldata"></a><a name="filldata"></a>CSnapInItemImpl::FillData

Ta funkcja jest wywoływana w celu pobrania informacji o elemencie.

```
FillData(CLIPFORMAT cf, LPSTREAM pStream);
```

### <a name="parameters"></a>Parametry

*Por*<br/>
[w] Format (tekst, tekst sformatowy lub tekst sformatowy z elementami OLE) Schowka.

*pStream (Strumień)*<br/>
[w] Wskaźnik do strumienia zawierający dane obiektu.

### <a name="remarks"></a>Uwagi

Aby prawidłowo wdrożyć tę funkcję, należy skopiować poprawne informacje do strumienia (*pStream*), w zależności od formatu Schowka wskazanego przez *cf*.

## <a name="csnapinitemimplgetresultviewtype"></a><a name="getresultviewtype"></a>CSnapInItemImpl::GetResultViewType

Wywołanie tej funkcji, aby pobrać typ widoku dla okienka wyników obiektu przystawki.

```
GetResultViewType(
    LPOLESTR* ppViewType,
    long* pViewOptions);
```

### <a name="parameters"></a>Parametry

*ppViewType (Typ widoku)*<br/>
[na zewnątrz] Wskaźnik do adresu powracającego typu widoku.

*pViewOptions*<br/>
[na zewnątrz] Wskaźnik do wyliczenia MMC_VIEW_OPTIONS, który zapewnia konsoli opcje określone przez przystawkę posiadacza. Ta wartość może być jedną z następujących wartości:

- MMC_VIEW_OPTIONS_NOLISTVIEWS = 0x00000001 Informuje konsolę o powstrzymaniu się od przedstawiania standardowych opcji widoku listy w menu **Widok.** Umożliwia przystawce wyświetlanie własnych widoków niestandardowych tylko w okienku widoku wynikowego. Jest to jedyna flaga opcji zdefiniowana w tej chwili.

- MMC_VIEW_OPTIONS_NONE = 0 Umożliwia domyślne opcje widoku.

## <a name="csnapinitemimplgetscopepaneinfo"></a><a name="getscopepaneinfo"></a>CSnapInItemImpl::GetScopePaneInfo

Wywołanie tej funkcji, `SCOPEDATAITEM` aby pobrać strukturę przystawki.

```
GetScopePaneInfo (SCOPEDATAITEM* pScopeDataItem);
```

### <a name="parameters"></a>Parametry

*pScopeDataItem*<br/>
[na zewnątrz] Wskaźnik do `SCOPEDATAITEM` struktury `CSnapInItemImpl` obiektu.

## <a name="csnapinitemimplgetresultpaneinfo"></a><a name="getresultpaneinfo"></a>CSnapInItemImpl::GetResultPaneInfo

Wywołanie tej funkcji, `RESULTDATAITEM` aby pobrać strukturę przystawki.

```
GetResultPaneInfo (RESULTDATAITEM* pResultDataItem);
```

### <a name="parameters"></a>Parametry

*pResultDataItem*<br/>
[na zewnątrz] Wskaźnik do `RESULTDATAITEM` struktury `CSnapInItemImpl` obiektu.

## <a name="csnapinitemimplm_bstrdisplayname"></a><a name="m_bstrdisplayname"></a>CSnapInItemImpl::m_bstrDisplayName

Zawiera ciąg wyświetlany dla elementu węzła.

```
CComBSTR m_bstrDisplayName;
```

## <a name="csnapinitemimplm_scopedataitem"></a><a name="m_scopedataitem"></a>CSnapInItemImpl::m_scopeDataItem

Struktura `SCOPEDATAITEM` obiektu danych przystawki.

```
SCOPEDATAITEM m_scopeDataItem;
```

## <a name="csnapinitemimplm_resultdataitem"></a><a name="m_resultdataitem"></a>CSnapInItemImpl::m_resultDataItem

[Struktura RESULTDATAITEM](/windows/win32/api/mmc/ns-mmc-resultdataitem) obiektu danych przystawki.

```
RESULTDATAITEM m_resultDataItem;
```

## <a name="csnapinitemimplnotify"></a><a name="notify"></a>CSnapInItemImpl::Powiadom

Wywoływane, gdy obiekt przystawki jest działać na przez użytkownika.

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
[w] Identyfikuje akcję podjętą przez użytkownika. Możliwe są następujące powiadomienia:

- MMCN_ACTIVATE wysyłane, gdy okno jest aktywowane i dezaktywowane.

- MMCN_ADD_IMAGES Wysłane, aby dodać obrazy do okienka wyników.

- MMCN_BTN_CLICK wysyłane, gdy użytkownik kliknie jeden z przycisków paska narzędzi.

- MMCN_CLICK wysyłane, gdy użytkownik kliknie przycisk myszy w elemencie widoku listy.

- MMCN_DBLCLICK Wysyłane, gdy użytkownik dwukrotnie kliknie przycisk myszy w elemencie widoku listy.

- MMCN_DELETE Wysłane, aby poinformować przystawkę, że obiekt powinien zostać usunięty.

- MMCN_EXPAND Wysyłane, gdy folder musi zostać rozwinięty lub zakontraktowany.

- MMCN_MINIMIZED wysyłane, gdy okno jest zminimalizowane lub zmaksymalizowane.

- MMCN_PROPERTY_CHANGE Wysłane, aby powiadomić obiekt przystawki, że widok obiektu przystawki ma się zmienić.

- MMCN_REMOVE_CHILDREN Wysłane, gdy przystawka musi usunąć całe poddrzewo, które dodało poniżej określonego węzła.

- MMCN_RENAME Wysłane po raz pierwszy do kwerendy o zmianę nazwy i po raz drugi, aby zrobić zmianę nazwy.

- MMCN_SELECT Wysłane po zaznaczeniu elementu w okienku widoku zakresu lub wyniku.

- MMCN_SHOW Wysyłane, gdy element zakresu jest zaznaczony lub odznaczony po raz pierwszy.

- MMCN_VIEW_CHANGE Wysyłane, gdy przystawka może zaktualizować wszystkie widoki po wystąpieniu zmiany.

*Arg*<br/>
[w] Zależy od typu powiadomienia.

*Param*<br/>
[w] Zależy od typu powiadomienia.

*pComponentData (Dane użytkownika)*<br/>
[na zewnątrz] Wskaźnik do obiektu implementującego `IComponentData`. Ten parametr ma wartość NULL, jeśli `IComponentData::Notify`powiadomienie nie jest przekazywane z pliku .

*pSKlient*<br/>
[na zewnątrz] Wskaźnik do obiektu, który `IComponent`implementuje . Ten parametr ma wartość NULL, jeśli `IComponent::Notify`powiadomienie nie jest przekazywane z pliku .

*Typu*<br/>
[w] Określa typ obiektu. Może mieć jedną z następujących wartości:

- CCT_SCOPE Data obiektu dla kontekstu okienka zakresu.

- CCT_RESULT Data obiektu dla kontekstu okienka wyników.

- CCT_SNAPIN_MANAGER Data obiektu dla kontekstu menedżera przystawki.

- CCT_UNINITIALIZED Data obiekt ma nieprawidłowy typ.

## <a name="csnapinitemimplquerypagesfor"></a><a name="querypagesfor"></a>CSnapInItemImpl::QueryPagesFor

Wywoływany, aby sprawdzić, czy węzeł przystawki obsługuje strony właściwości.

```
QueryPagesFor(DATA_OBJECT_TYPES type);
```

## <a name="csnapinitemimplsetmenuinsertionflags"></a><a name="setmenuinsertionflags"></a>CSnapInItemImpl::SetMenuInsertionSlags

Wywołanie tej funkcji, aby zmodyfikować flagi wstawiania menu, określone przez *pInsertionAllowed*, dla obiektu przystawki.

```cpp
void SetMenuInsertionFlags(
    bool bBeforeInsertion,
    long* pInsertionAllowed);
```

### <a name="parameters"></a>Parametry

*bBeforeInsertion*<br/>
[w] Nonzero, jeśli funkcja powinna być wywoływana przed elementy są dodawane do menu kontekstowego; w przeciwnym razie 0.

*PInsertion Dozwolone*<br/>
[w, na zewnątrz] Identyfikuje zdefiniowane w programie Microsoft Management Console (MMC) punkty wstawiania elementu menu, które mogą być używane. Może to być kombinacja następujących flag:

- CCM_INSERTIONALLOWED_TOP Elementy można wstawić u góry menu kontekstowego.

- CCM_INSERTIONALLOWED_NEW Elementy można wstawić w podmenu Utwórz nowe.

- CCM_INSERTIONALLOWED_TASK Elementy można wstawić w podmenu Zadanie.

- CCM_INSERTIONALLOWED_VIEW Elementy można wstawić w menu widoku paska narzędzi lub w podmenu Widok menu kontekstowego okienka wyników.

### <a name="remarks"></a>Uwagi

Jeśli tworzysz podstawowe przystawki, można zresetować dowolną z flag wstawiania jako sposób ograniczenia rodzaju elementów menu, które rozszerzenie innych firm można dodać. Na przykład podstawowa przystawka może wyczyścić flagę CCM_INSERTIONALLOWED_NEW, aby uniemożliwić rozszerzenia dodawania własnych elementów menu Utwórz nowe.

Nie należy próbować ustawić bity w *pInsertionAllowed,* które zostały pierwotnie wyczyszczone. Przyszłe wersje programu MMC mogą używać bitów nieokreślonych obecnie, więc nie należy zmieniać bitów, które obecnie nie są zdefiniowane.

## <a name="csnapinitemimplsettoolbarbuttoninfo"></a><a name="settoolbarbuttoninfo"></a>CSnapInItemImpl::SetToolbarButtonInfo

Wywołanie tej funkcji, aby zmodyfikować wszystkie style przycisków paska narzędzi, obiektu przystawki, przed utworzeniem paska narzędzi.

```cpp
void SetToolbarButtonInfo(
    UINT id,
    BYTE* fsState,
    BYTE* fsType);
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
[w] Identyfikator przycisku paska narzędzi, który ma zostać ustawiony.

*fsStan*<br/>
[w] Flagi państwowe przycisku. Może być co najmniej jedna z następujących czynności:

- TBSTATE_CHECKED Przycisk ma styl TBSTYLE_CHECKED i jest wciśnięty.

- TBSTATE_ENABLED Przycisk akceptuje dane wejściowe użytkownika. Przycisk, który nie ma tego stanu, nie akceptuje danych wejściowych użytkownika i jest wyszarzony.

- TBSTATE_HIDDEN Przycisk nie jest widoczny i nie może odbierać danych wejściowych użytkownika.

- TBSTATE_INDETERMINATE Przycisk jest wyszarzony.

- TBSTATE_PRESSED Przycisk jest wciśnięty.

- TBSTATE_WRAP Podział wiersza następuje po przycisku. Przycisk musi mieć również TBSTATE_ENABLED.

*fsType (typ)*<br/>
[w] Flagi państwowe przycisku. Może być co najmniej jedna z następujących czynności:

- TBSTYLE_BUTTON Tworzy standardowy przycisk.

- TBSTYLE_CHECK Tworzy przycisk, który przełącza się między stanami wciśnięty i niewciśnięty za każdym razem, gdy użytkownik kliknie go. Przycisk ma inny kolor tła, gdy jest w stanie naciśnięcia.

- TBSTYLE_CHECKGROUP Tworzy przycisk wyboru, który pozostaje naciśnięty do momentu naciśnięcia innego przycisku w grupie.

- TBSTYLE_GROUP Tworzy przycisk, który pozostaje naciśnięty do momentu naciśnięcia innego przycisku w grupie.

- TBSTYLE_SEP Tworzy separator, zapewniając niewielką przerwę między grupami przycisków. Przycisk, który ma ten styl nie odbiera danych wejściowych użytkownika.

## <a name="csnapinitemimplupdatemenustate"></a><a name="updatemenustate"></a>CSnapInItemImpl::UpdateMenuState

Wywołanie tej funkcji, aby zmodyfikować element menu, zanim zostanie wstawiony do menu kontekstowego obiektu przystawki.

```cpp
void UpdateMenuState(
    UINT id,
    LPTSTR pBuf,
    UINT* flags);
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
[w] Identyfikator elementu menu, który ma zostać ustawiony.

*pBuf (ps.*<br/>
[w] Wskaźnik do ciągu dla elementu menu, który ma zostać zaktualizowany.

*flagi*<br/>
[w] Określa nowe flagi państwowe. Może to być kombinacja następujących flag:

- MF_POPUP Określa, że jest to podmenu w menu kontekstowym. Elementy menu, punkty wstawiania i dalsze podmenu mogą `lCommandID` być `IInsertionPointID`dodawane do tego podmenu, używając jego jako swojego .

- MF_BITMAP i MF_OWNERDRAW Flagi te nie są dozwolone i spowoduje wartość zwracaną E_INVALIDARG.

- MF_SEPARATOR Rysuje poziomą linię podziału. Dozwolone `IContextMenuProvider` jest dodawanie tylko elementów menu z MF_SEPARATOR ustawionym.

- MF_CHECKED Umieszcza znacznik wyboru obok elementu menu.

- MF_DISABLED Wyłącza element menu, więc nie można go wybrać, ale flaga nie jest szara.

- MF_ENABLED Włącza element menu, dzięki czemu można go wybrać, przywracając go ze stanu wyszarzone.

- MF_GRAYED Wyłącza element menu, siwie go, aby nie można było go zaznaczyć.

- MF_MENUBARBREAK Funkcje takie same jak flaga MF_MENUBREAK dla paska menu. W przypadku menu rozwijanego, podmenu lub menu skrótów nowa kolumna jest oddzielana od starej kolumny linią pionową.

- MF_MENUBREAK Umieszcza element w nowym wierszu (dla paska menu) lub w nowej kolumnie (dla menu rozwijanego, podmenu lub menu skrótów) bez oddzielania kolumn.

- MF_UNCHECKED Nie umieszcza znacznika wyboru obok elementu (domyślnie).

Następujące grupy flag nie mogą być używane razem:

- MF_DISABLED, MF_ENABLED i MF_GRAYED.

- MF_MENUBARBREAK i MF_MENUBREAK.

- MF_CHECKED i MF_UNCHECKED.

## <a name="csnapinitemimplupdatetoolbarbutton"></a><a name="updatetoolbarbutton"></a>CSnapInItemImpl::UpdateToolbarButton

Wywołanie tej funkcji, aby zmodyfikować przycisk paska narzędzi, obiektu przystawki, zanim zostanie wyświetlony.

```
BOOL UpdateToolbarButton(UINT id, BYTE fsState);
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
Określa identyfikator przycisku przycisku paska narzędzi, który ma zostać zaktualizowany.

*fsStan*<br/>
Określa stan przycisku paska narzędzi. Jeśli ten stan ma być ustawiony, zwraca wartość TRUE. Może to być kombinacja następujących flag:

- WŁĄCZONE Przycisk akceptuje dane wejściowe użytkownika. Przycisk, który nie ma tego stanu, nie akceptuje danych wejściowych użytkownika i jest wyszarzony.

- SPRAWDZONE Przycisk ma styl CHECKED i jest wciśnięty.

- UKRYTE Przycisk nie jest widoczny i nie może odbierać danych wejściowych użytkownika.

- NIEOKREŚLONY Przycisk jest wyszarzony.

- PRZYCISK WCIŚNIĘTY Przycisk jest wciśnięty.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
