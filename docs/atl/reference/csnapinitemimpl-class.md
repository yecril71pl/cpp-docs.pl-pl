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
ms.openlocfilehash: a9ebcf8827d79a9613ce14251d361dd607aa6af3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496548"
---
# <a name="csnapinitemimpl-class"></a>Klasa CSnapInItemImpl

Ta klasa dostarcza metody do implementowania obiektu węzła przystawki.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class T, BOOL bIsExtension = FALSE>
class ATL_NO_VTABLE CSnapInItemImpl : public CSnapInItem
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa, która pochodzi od `CSnapInItemImpl`.

*bIsExtension*<br/>
PRAWDA, jeśli obiekt jest rozszerzeniem przystawki; w przeciwnym razie FALSE.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSnapInItemImpl::CSnapInItemImpl](#csnapinitemimpl)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSnapInItemImpl:: AddMenuItems](#addmenuitems)|Dodaje elementy menu do menu kontekstowego.|
|[CSnapInItemImpl:: polecenie](#command)|Wywoływane przez konsolę, gdy zostanie wybrany niestandardowy element menu.|
|[CSnapInItemImpl::CreatePropertyPages](#createpropertypages)|Dodaje strony do arkusza właściwości przystawki.|
|[CSnapInItemImpl::FillData](#filldata)|Kopiuje informacje z obiektu przystawki do określonego strumienia.|
|[CSnapInItemImpl::GetResultPaneInfo](#getresultpaneinfo)|`RESULTDATAITEM` Pobiera strukturę przystawki.|
|[CSnapInItemImpl::GetResultViewType](#getresultviewtype)|Określa typ widoku używanego przez okienko wyników.|
|[CSnapInItemImpl::GetScopePaneInfo](#getscopepaneinfo)|`SCOPEDATAITEM` Pobiera strukturę przystawki.|
|[CSnapInItemImpl:: informowanie](#notify)|Wywoływane przez konsolę, aby powiadomić przystawkę akcji podjętych przez użytkownika.|
|[CSnapInItemImpl::QueryPagesFor](#querypagesfor)|Wywołuje się, by sprawdzić, czy węzeł przystawki obsługuje strony właściwości.|
|[CSnapInItemImpl::SetMenuInsertionFlags](#setmenuinsertionflags)|Modyfikuje flagi wstawiania menu dla obiektu przystawki.|
|[CSnapInItemImpl::SetToolbarButtonInfo](#settoolbarbuttoninfo)|Ustawia informacje o określonym przycisku paska narzędzi.|
|[CSnapInItemImpl::UpdateMenuState](#updatemenustate)|Aktualizuje stan elementu menu kontekstowego.|
|[CSnapInItemImpl::UpdateToolbarButton](#updatetoolbarbutton)|Aktualizuje stan określonego przycisku paska narzędzi.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CSnapInItemImpl::m_bstrDisplayName](#m_bstrdisplayname)|Nazwa obiektu przystawki.|
|[CSnapInItemImpl::m_resultDataItem](#m_resultdataitem)|Struktura systemu `RESULTDATAITEM` Windows używana `CSnapInItemImpl` przez obiekt.|
|[CSnapInItemImpl::m_scopeDataItem](#m_scopedataitem)|Struktura systemu `SCOPEDATAITEM` Windows używana `CSnapInItemImpl` przez obiekt.|

## <a name="remarks"></a>Uwagi

`CSnapInItemImpl`udostępnia podstawową implementację obiektu węzła przystawki, takie jak dodawanie elementów menu i pasków narzędzi i przekazywanie poleceń dla węzła przystawki do odpowiedniej funkcji obsługi. Te funkcje są implementowane przy użyciu kilku różnych interfejsów i typów map. Domyślna implementacja obsługuje powiadomienia wysyłane do obiektu węzła przez określenie poprawnego wystąpienia klasy pochodnej, a następnie przesłanie komunikatu do poprawnego wystąpienia.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CSnapInItem`

`CSnapInItemImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsnap. h

##  <a name="addmenuitems"></a>CSnapInItemImpl:: AddMenuItems

Ta metoda implementuje funkcję Win32 [IExtendContextMenu::](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-addmenuitems)AddMenuItems.

```
AddMenuItems(
    LPCONTEXTMENUCALLBACK piCallback,
    long* pInsertionAllowed,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Parametry

*piCallback*<br/>
podczas Wskaźnik na `IContextMenuCallback` element, który może dodawać elementy do menu kontekstowego.

*pInsertionAllowed*<br/>
[in. out] Identyfikuje program Microsoft Management Console (MMC) — zdefiniowane punkty wstawiania elementów menu, które mogą być używane. Może to być kombinacja następujących flag:

- Elementy CCM_INSERTIONALLOWED_TOP można wstawiać u góry menu kontekstowego.

- Elementy CCM_INSERTIONALLOWED_NEW można wstawiać w podmenu Create New.

- Elementy CCM_INSERTIONALLOWED_TASK można wstawiać w podmenu zadania.

- Elementy CCM_INSERTIONALLOWED_VIEW można wstawiać w menu Widok paska narzędzi lub w podmenu Widok w menu kontekstowym okienka wyników.

*type*<br/>
podczas Określa typ obiektu. Może mieć jedną z następujących wartości:

- Obiekt danych CCT_SCOPE dla kontekstu okienka zakresu.

- Obiekt danych CCT_RESULT dla kontekstu okienka wyników.

- Obiekt danych CCT_SNAPIN_MANAGER dla kontekstu Menedżera przystawek.

- Obiekt danych CCT_UNINITIALIZED ma nieprawidłowy typ.

##  <a name="command"></a>CSnapInItemImpl:: polecenie

Ta metoda implementuje funkcję Win32 [IExtendContextMenu:: Command](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-command).

```
Command(long lCommandID, DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Parametry

*lCommandID*<br/>
podczas Określa identyfikator polecenia elementu menu.

*type*<br/>
podczas Określa typ obiektu. Może mieć jedną z następujących wartości:

- Obiekt danych CCT_SCOPE dla kontekstu okienka zakresu.

- Obiekt danych CCT_RESULT dla kontekstu okienka wyników.

- Obiekt danych CCT_SNAPIN_MANAGER dla kontekstu Menedżera przystawek.

- Obiekt danych CCT_UNINITIALIZED ma nieprawidłowy typ.

##  <a name="createpropertypages"></a>CSnapInItemImpl::CreatePropertyPages

Ta metoda implementuje funkcję Win32 [IExtendPropertySheet:: CreatePropertyPages](/windows/win32/api/mmc/nn-mmc-iextendpropertysheet2).

```
CreatePropertyPages(
    LPPROPERTYSHEETCALLBACK lpProvider,
    long handle,
    IUnknown* pUnk,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Parametry

*lpProvider*<br/>
podczas Wskaźnik do `IPropertySheetCallback` interfejsu.

*uchwyty*<br/>
podczas Określa uchwyt używany do kierowania komunikatu powiadomienia MMCN_PROPERTY_CHANGE do odpowiedniej klasy danych.

*pUnk*<br/>
podczas Wskaźnik do `IExtendPropertySheet` interfejsu obiektu, który zawiera informacje kontekstowe dotyczące węzła.

*type*<br/>
podczas Określa typ obiektu. Może mieć jedną z następujących wartości:

- Obiekt danych CCT_SCOPE dla kontekstu okienka zakresu.

- Obiekt danych CCT_RESULT dla kontekstu okienka wyników.

- Obiekt danych CCT_SNAPIN_MANAGER dla kontekstu Menedżera przystawek.

- Obiekt danych CCT_UNINITIALIZED ma nieprawidłowy typ.

##  <a name="csnapinitemimpl"></a>CSnapInItemImpl::CSnapInItemImpl

Konstruuje `CSnapInItemImpl` obiekt.

```
CSnapInItemImpl();
```

##  <a name="filldata"></a>CSnapInItemImpl::FillData

Ta funkcja jest wywoływana, aby pobrać informacje o elemencie.

```
FillData(CLIPFORMAT cf, LPSTREAM pStream);
```

### <a name="parameters"></a>Parametry

*cf*<br/>
podczas Format (tekst, tekst sformatowany lub tekst sformatowany z elementami OLE) Schowka.

*pStream*<br/>
podczas Wskaźnik do strumienia zawierającego dane obiektu.

### <a name="remarks"></a>Uwagi

Aby poprawnie zaimplementować tę funkcję, skopiuj poprawne informacje do strumienia (*pStream*), w zależności od formatu Schowka wskazanego przez *CF*.

##  <a name="getresultviewtype"></a>CSnapInItemImpl::GetResultViewType

Wywołaj tę funkcję, aby pobrać typ widoku dla okienka wyników obiektu przystawki.

```
GetResultViewType(
    LPOLESTR* ppViewType,
    long* pViewOptions);
```

### <a name="parameters"></a>Parametry

*ppViewType*<br/>
określoną Wskaźnik na adres zwracanego typu widoku.

*pViewOptions*<br/>
określoną Wskaźnik na Wyliczenie MMC_VIEW_OPTIONS, które udostępnia konsolę z opcjami określonymi przez przystawkę będącą właścicielem. Może to być jedna z następujących wartości:

- MMC_VIEW_OPTIONS_NOLISTVIEWS = 0x00000001 instruuje konsolę, aby nie pomógł w menu **Widok** wyświetlić standardowych opcji widoku listy. Umożliwia tej przystawce wyświetlanie własnych widoków niestandardowych tylko w okienku Widok wyników. Jest to jedyna flaga opcji zdefiniowana w tym momencie.

- MMC_VIEW_OPTIONS_NONE = 0 zezwala na Opcje widoku domyślnego.

##  <a name="getscopepaneinfo"></a>CSnapInItemImpl::GetScopePaneInfo

Wywołaj tę funkcję, aby `SCOPEDATAITEM` pobrać strukturę przystawki.

```
GetScopePaneInfo (SCOPEDATAITEM* pScopeDataItem);
```

### <a name="parameters"></a>Parametry

*pScopeDataItem*<br/>
określoną Wskaźnik do `SCOPEDATAITEM` struktury `CSnapInItemImpl` obiektu.

##  <a name="getresultpaneinfo"></a>CSnapInItemImpl::GetResultPaneInfo

Wywołaj tę funkcję, aby `RESULTDATAITEM` pobrać strukturę przystawki.

```
GetResultPaneInfo (RESULTDATAITEM* pResultDataItem);
```

### <a name="parameters"></a>Parametry

*pResultDataItem*<br/>
określoną Wskaźnik do `RESULTDATAITEM` struktury `CSnapInItemImpl` obiektu.

##  <a name="m_bstrdisplayname"></a>CSnapInItemImpl::m_bstrDisplayName

Zawiera ciąg wyświetlany dla elementu węzła.

```
CComBSTR m_bstrDisplayName;
```

##  <a name="m_scopedataitem"></a>CSnapInItemImpl::m_scopeDataItem

`SCOPEDATAITEM` Struktura obiektu danych przystawki.

```
SCOPEDATAITEM m_scopeDataItem;
```

##  <a name="m_resultdataitem"></a>CSnapInItemImpl::m_resultDataItem

Struktura [RESULTDATAITEM](/windows/win32/api/mmc/ns-mmc-resultdataitem) obiektu danych przystawek.

```
RESULTDATAITEM m_resultDataItem;
```

##  <a name="notify"></a>CSnapInItemImpl:: informowanie

Wywoływana, gdy użytkownik podejmuje działania dotyczące obiektu przystawki.

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
podczas Identyfikuje akcję wykonywaną przez użytkownika. Możliwe są następujące powiadomienia:

- MMCN_ACTIVATE wysyłany, gdy okno jest uaktywniane i dezaktywowane.

- MMCN_ADD_IMAGES wysyłany w celu dodania obrazów do okienka wyników.

- MMCN_BTN_CLICK wysyłany, gdy użytkownik kliknie jeden z przycisków paska narzędzi.

- MMCN_CLICK wysyłany, gdy użytkownik kliknie przycisk myszy w elemencie widoku listy.

- MMCN_DBLCLICK wysyłany, gdy użytkownik kliknie dwukrotnie przycisk myszy w elemencie widoku listy.

- MMCN_DELETE wysyłany w celu informowania o tym, że obiekt powinien zostać usunięty.

- MMCN_EXPAND wysyłany, gdy folder musi być rozwinięty lub kontraktowy.

- MMCN_MINIMIZED wysyłany, gdy okno jest zminimalizowane lub zmaksymalizowane.

- MMCN_PROPERTY_CHANGE wysyłany w celu powiadomienia obiektu przystawki, który zostanie zmieniony przez widok obiektu przystawki.

- MMCN_REMOVE_CHILDREN wysyłany, gdy przystawka musi usunąć całe poddrzewo, które zostało dodane poniżej określonego węzła.

- MMCN_RENAME wysyłany po raz pierwszy do zapytania o zmianę nazwy, a druga godzina zmiany nazwy.

- MMCN_SELECT wysyłany, gdy wybrano element z okienka zakres lub widok wyników.

- MMCN_SHOW wysyłany, gdy element zakresu jest wybierany po raz pierwszy.

- MMCN_VIEW_CHANGE wysyłany, gdy przystawka może zaktualizować wszystkie widoki w przypadku wystąpienia zmiany.

*ARG*<br/>
podczas Zależy od typu powiadomienia.

*param*<br/>
podczas Zależy od typu powiadomienia.

*pComponentData*<br/>
określoną Wskaźnik do zaimplementowania `IComponentData`obiektu. Ten parametr ma wartość NULL, jeśli powiadomienia nie są przekazywane z `IComponentData::Notify`programu.

*pComponent*<br/>
określoną Wskaźnik do obiektu, który implementuje `IComponent`. Ten parametr ma wartość NULL, jeśli powiadomienia nie są przekazywane z `IComponent::Notify`programu.

*type*<br/>
podczas Określa typ obiektu. Może mieć jedną z następujących wartości:

- Obiekt danych CCT_SCOPE dla kontekstu okienka zakresu.

- Obiekt danych CCT_RESULT dla kontekstu okienka wyników.

- Obiekt danych CCT_SNAPIN_MANAGER dla kontekstu Menedżera przystawek.

- Obiekt danych CCT_UNINITIALIZED ma nieprawidłowy typ.

##  <a name="querypagesfor"></a>CSnapInItemImpl::QueryPagesFor

Wywołuje się, by sprawdzić, czy węzeł przystawki obsługuje strony właściwości.

```
QueryPagesFor(DATA_OBJECT_TYPES type);
```

##  <a name="setmenuinsertionflags"></a>CSnapInItemImpl::SetMenuInsertionFlags

Wywołaj tę funkcję, aby zmodyfikować flagi wstawiania menu określone przez *pInsertionAllowed*dla obiektu przystawki.

```
void SetMenuInsertionFlags(
    bool bBeforeInsertion,
    long* pInsertionAllowed);
```

### <a name="parameters"></a>Parametry

*bBeforeInsertion*<br/>
podczas Niezerowe, jeśli funkcja powinna zostać wywołana przed dodaniem elementów do menu kontekstowego; w przeciwnym razie 0.

*pInsertionAllowed*<br/>
[in. out] Identyfikuje program Microsoft Management Console (MMC) — zdefiniowane punkty wstawiania elementów menu, które mogą być używane. Może to być kombinacja następujących flag:

- Elementy CCM_INSERTIONALLOWED_TOP można wstawiać u góry menu kontekstowego.

- Elementy CCM_INSERTIONALLOWED_NEW można wstawiać w podmenu Create New.

- Elementy CCM_INSERTIONALLOWED_TASK można wstawiać w podmenu zadania.

- Elementy CCM_INSERTIONALLOWED_VIEW można wstawiać w menu Widok paska narzędzi lub w podmenu Widok w menu kontekstowym okienka wyników.

### <a name="remarks"></a>Uwagi

Jeśli tworzysz przystawkę podstawową, możesz zresetować dowolną flagę wstawiania jako sposób ograniczenia rodzaju elementów menu, które mogą zostać dodane przez rozszerzenie innej firmy. Na przykład, podstawowa przystawka może wyczyścić flagę CCM_INSERTIONALLOWED_NEW, aby zapobiec dodaniu przez rozszerzenia własnych nowych elementów menu.

Nie należy podejmować próby ustawienia bitów w *pInsertionAllowed* , które zostały pierwotnie wyczyszczone. Przyszłe wersje programu MMC mogą korzystać z usługi BITS, która nie jest obecnie zdefiniowana, więc nie należy zmieniać obecnie niezdefiniowanych bitów.

##  <a name="settoolbarbuttoninfo"></a>CSnapInItemImpl::SetToolbarButtonInfo

Wywołaj tę funkcję, aby zmodyfikować wszystkie style przycisków paska narzędzi dla obiektu przystawki przed utworzeniem paska narzędzi.

```
void SetToolbarButtonInfo(
    UINT id,
    BYTE* fsState,
    BYTE* fsType);
```

### <a name="parameters"></a>Parametry

*id*<br/>
podczas Identyfikator przycisku paska narzędzi, który ma zostać ustawiony.

*fsState*<br/>
podczas Flagi stanu przycisku. Może to być jeden lub więcej z następujących elementów:

- TBSTATE_CHECKED przycisk ma styl TBSTYLE_CHECKED i jest nacionięty.

- TBSTATE_ENABLED przycisk akceptuje dane wejściowe użytkownika. Przycisk, który nie ma tego stanu, nie akceptuje danych wejściowych użytkownika i jest wyszarzony.

- TBSTATE_HIDDEN przycisk nie jest widoczny i nie może odbierać danych wejściowych użytkownika.

- TBSTATE_INDETERMINATE przycisk jest szary.

- TBSTATE_PRESSED naciśnięcie przycisku.

- TBSTATE_WRAP podział wiersza po przycisku. Przycisk musi mieć również TBSTATE_ENABLED.

*fsType*<br/>
podczas Flagi stanu przycisku. Może to być jeden lub więcej z następujących elementów:

- TBSTYLE_BUTTON tworzy standardowy przycisk wypychania.

- TBSTYLE_CHECK tworzy przycisk, który przełącza się między naciśniętymi i nienaciśniętymi Stanami przy każdym kliknięciu przez użytkownika. Przycisk ma inny kolor tła, gdy jest w stanie naciśniętym.

- TBSTYLE_CHECKGROUP tworzy przycisk wyboru, który pozostanie wciśnięty do momentu naciśnięcia innego przycisku w grupie.

- TBSTYLE_GROUP tworzy przycisk, który pozostanie wciśnięty do momentu naciśnięcia innego przycisku w grupie.

- TBSTYLE_SEP tworzy separator, dostarczając małą przerwy między grupami przycisków. Przycisk, który ma ten styl nie otrzymuje danych wejściowych użytkownika.

##  <a name="updatemenustate"></a>CSnapInItemImpl::UpdateMenuState

Wywołaj tę funkcję, aby zmodyfikować element menu przed jego wstawieniem do menu kontekstowego obiektu przystawki.

```
void UpdateMenuState(
    UINT id,
    LPTSTR pBuf,
    UINT* flags);
```

### <a name="parameters"></a>Parametry

*id*<br/>
podczas Identyfikator elementu menu, który ma zostać ustawiony.

*pBuf*<br/>
podczas Wskaźnik do ciągu dla elementu menu, który ma zostać zaktualizowany.

*znaczników*<br/>
podczas Określa nowe flagi stanu. Może to być kombinacja następujących flag:

- MF_POPUP określa, że jest podmenu w menu kontekstowym. Elementy menu, punkty wstawiania i dalsze podmenu mogą zostać dodane do tego podmenu przy użyciu `lCommandID` ich `IInsertionPointID`jako.

- MF_BITMAP i MF_OWNERDRAW te flagi są niedozwolone i spowodują zwrócenie wartości E_INVALIDARG.

- MF_SEPARATOR rysuje wiersz podziału w poziomie. Tylko `IContextMenuProvider` elementy menu można dodawać z zestawem MF_SEPARATOR.

- MF_CHECKED umieszcza znacznik wyboru obok elementu menu.

- MF_DISABLED wyłącza element menu, dlatego nie można go wybrać, ale flaga nie jest szara.

- MF_ENABLED włącza element menu, aby można go było wybrać, przywracając go ze stanu szary.

- MF_GRAYED wyłącza element menu, szary go, aby nie można go było wybrać.

- MF_MENUBARBREAK funkcje takie same jak flaga MF_MENUBREAK dla paska menu. W przypadku menu rozwijanego, podmenu lub menu skrótów nowa kolumna jest oddzielona od starej kolumny linią pionową.

- MF_MENUBREAK umieszcza element w nowym wierszu (dla paska menu) lub w nowej kolumnie (menu rozwijane, podmenu lub menu skrótów) bez rozdzielania kolumn.

- MF_UNCHECKED nie umieszcza znacznika wyboru obok elementu (domyślnie).

Następujące grupy flag nie mogą być używane razem:

- MF_DISABLED, MF_ENABLED i MF_GRAYED.

- MF_MENUBARBREAK i MF_MENUBREAK.

- MF_CHECKED i MF_UNCHECKED.

##  <a name="updatetoolbarbutton"></a>CSnapInItemImpl::UpdateToolbarButton

Wywołaj tę funkcję, aby zmodyfikować przycisk paska narzędzi w obiekcie przystawki przed wyświetleniem.

```
BOOL UpdateToolbarButton(UINT id, BYTE fsState);
```

### <a name="parameters"></a>Parametry

*id*<br/>
Określa identyfikator przycisku paska narzędzi, który ma zostać zaktualizowany.

*fsState*<br/>
Określa stan przycisku paska narzędzi. Jeśli ten stan ma być ustawiony, zwróć wartość TRUE. Może to być kombinacja następujących flag:

- Włączenie przycisku akceptuje dane wejściowe użytkownika. Przycisk, który nie ma tego stanu, nie akceptuje danych wejściowych użytkownika i jest wyszarzony.

- SPRAWDZONo, że przycisk ma ZAZNACZONY styl i jest nacionięty.

- UKRYTY przycisk nie jest widoczny i nie może odbierać danych wejściowych użytkownika.

- Nieokreślony przycisk jest wyszarzony.

- BUTTONPRESSED naciśnięcie przycisku.

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)
