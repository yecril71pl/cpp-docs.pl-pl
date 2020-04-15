---
title: Klasa CMFCRibbonQuickAccessToolBarDefaultState
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::AddCommand
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll
helpviewer_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CMFCRibbonQuickAccessToolBarDefaultState
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], AddCommand
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CopyFrom
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], RemoveAll
ms.assetid: eca99200-b87b-47ba-b2e8-2f3f2444b176
ms.openlocfilehash: 56219e8ed1833f4b448ec6ffd3c16e9db3c66ada
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368871"
---
# <a name="cmfcribbonquickaccesstoolbardefaultstate-class"></a>Klasa CMFCRibbonQuickAccessToolBarDefaultState

Klasa pomocnika, która zarządza domyślnym stanem paska narzędzi Szybki dostęp, który znajduje się na pasku wstążki [(CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md)).

## <a name="syntax"></a>Składnia

```
class CMFCRibbonQuickAccessToolBarDefaultState
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState](#cmfcribbonquickaccesstoolbardefaultstate)|Konstruuje `CMFCRibbonQuickAccessToolbarDefaultState` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand)|Dodaje polecenie do stanu domyślnego paska narzędzi Szybki dostęp. Nie powoduje to zmiany samego paska narzędzi.|
|[CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom](#copyfrom)|Kopiuje właściwości jednego paska narzędzi Szybki dostęp do drugiego.|
|[CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll](#removeall)|Usuwa wszystkie polecenia z paska narzędzi Szybki dostęp. Nie powoduje to zmiany samego paska narzędzi.|

## <a name="remarks"></a>Uwagi

Po utworzeniu paska narzędzi Szybki dostęp w aplikacji zaleca się ustawienie jego stanu domyślnego przez wywołanie [CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate). Ten stan domyślny jest przywracany, gdy użytkownik kliknie przycisk **Resetowanie** na **stronie** Okno dialogowe **Opcje** aplikacji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CMFCRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCRibbonQuickAccessToolbarDefaultState` skonstruować obiekt klasy i jak dodać polecenie do stanu domyślnego paska narzędzi Szybki dostęp.

[!code-cpp[NVC_MFC_RibbonApp#21](../../mfc/reference/codesnippet/cpp/cmfcribbonquickaccesstoolbardefaultstate-class_1.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxribbonquickaccesstoolbar.h

## <a name="cmfcribbonquickaccesstoolbardefaultstateaddcommand"></a><a name="addcommand"></a>CMFCRibbonQuickAccessToolBarDefaultState::AddCommand

Dodaje polecenie do stanu domyślnego paska narzędzi Szybki dostęp.

```
void AddCommand(
    UINT uiCmd,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Parametry

*[w] uiCmd*<br/>
Określa identyfikator polecenia.

*[w] bIsVisible*<br/>
Ustawia widoczność polecenia, gdy pasek narzędzi Szybki dostęp jest w stanie domyślnym.

### <a name="remarks"></a>Uwagi

Dodanie polecenia do CMFCRibbonQuickAccessToolBarDefaultState osiąga trzy wyniki. Najpierw każde dodane polecenie jest wyświetlane na liście rozwijanej po prawej stronie paska narzędzi Szybki dostęp. W ten sposób użytkownik może łatwo dodać lub usunąć to polecenie z paska narzędzi Szybki dostęp. Po drugie, pasek narzędzi Szybki dostęp jest resetowany, aby wyświetlić tylko te polecenia, które są wyświetlane jako widoczne w stanie domyślnym, gdy użytkownik kliknie przycisk **Reset w** oknie dialogowym **Dostosowywanie.** Po trzecie, jeśli nie zostały wywołane [CMFCRibbonBar::SetQuickAccessCommands](../../mfc/reference/cmfcribbonbar-class.md#setquickaccesscommands), pasek narzędzi Szybki dostęp używa widocznych poleceń z tej listy jako domyślne polecenia widoczne przy pierwszym uruchomieniu aplikacji przez użytkownika. Po dodaniu wszystkich poleceń, które chcesz, wywołaj [CMFCRibbonBar::SetQuickAccessDefaultState,](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate) aby ustawić to wystąpienie jako stan domyślny dla paska narzędzi Szybki dostęp tego paska wstążki.

## <a name="cmfcribbonquickaccesstoolbardefaultstatecopyfrom"></a><a name="copyfrom"></a>CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom

Kopiuje właściwości jednego paska narzędzi Szybki dostęp do drugiego.

```
void CopyFrom(const CMFCRibbonQuickAccessToolBarDefaultState& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
[w] Odwołanie do obiektu `CMFCRibbonQuickAccessToolBarDefaultState` źródłowego do skopiowania z.

### <a name="remarks"></a>Uwagi

Ta metoda kopiuje każde `CMFCRibbonQuickAccessToolBarDefaultState` polecenie z obiektu źródłowego do tego obiektu przy użyciu [metody CMFCRibbonQuickAccessToolBarDefaultState::AddCommand.](#addcommand)

## <a name="cmfcribbonquickaccesstoolbardefaultstatecmfcribbonquickaccesstoolbardefaultstate"></a><a name="cmfcribbonquickaccesstoolbardefaultstate"></a>CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState

Konstruuje domyślny obiekt stanu paska narzędzi Szybki dostęp.

```
CMFCRibbonQuickAccessToolBarDefaultState();
```

### <a name="remarks"></a>Uwagi

Domyślnie lista poleceń, które zawiera nowe wystąpienie [CMFRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md) jest pusta.

## <a name="cmfcribbonquickaccesstoolbardefaultstateremoveall"></a><a name="removeall"></a>CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll

Czyści listę poleceń domyślnych na pasku narzędzi Szybki dostęp.

```
void RemoveAll();
```

### <a name="remarks"></a>Uwagi

Ta funkcja usuwa z tego wystąpienia wszystkie polecenia, które poprzednie wywołania [CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand) dodał.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)
