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
ms.openlocfilehash: 07af26c78cc3316dbfcd33a5b28e5230a82a2e10
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445100"
---
# <a name="cmfcribbonquickaccesstoolbardefaultstate-class"></a>Klasa CMFCRibbonQuickAccessToolBarDefaultState

Klasa pomocnika, która zarządza domyślny stan dla paska narzędzi szybkiego dostępu, który jest umieszczony w pasku wstążki ( [klasa CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)).

## <a name="syntax"></a>Składnia

```
class CMFCRibbonQuickAccessToolBarDefaultState
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState](#cmfcribbonquickaccesstoolbardefaultstate)|Konstruuje `CMFCRibbonQuickAccessToolbarDefaultState` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand)|Umożliwia dodanie polecenia do stanu domyślnego dla paska narzędzi Szybki dostęp. Nie zmienia się pasek narzędzi.|
|[CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom](#copyfrom)|Kopiuje właściwości jednego paska narzędzi Szybki dostęp do innej lokalizacji.|
|[CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll](#removeall)|Usuwa wszystkie polecenia z paska narzędzi Szybki dostęp. Nie zmienia się pasek narzędzi.|

## <a name="remarks"></a>Uwagi

Po utworzeniu paska narzędzi Szybki dostęp do aplikacji, zaleca się Ustaw domyślny stan przez wywołanie metody [CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate). Ten stan domyślny przywróceniu, gdy użytkownik kliknie **resetowania** znajdujący się na **Dostosuj** strony aplikacji **opcje** okno dialogowe.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CMFCRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCRibbonQuickAccessToolbarDefaultState` klasy oraz sposób dodać polecenie do stanu domyślnego dla paska narzędzi Szybki dostęp.

[!code-cpp[NVC_MFC_RibbonApp#21](../../mfc/reference/codesnippet/cpp/cmfcribbonquickaccesstoolbardefaultstate-class_1.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxribbonquickaccesstoolbar.h

##  <a name="addcommand"></a>  CMFCRibbonQuickAccessToolBarDefaultState::AddCommand

Umożliwia dodanie polecenia do stanu domyślnego dla paska narzędzi Szybki dostęp.

```
void AddCommand(
    UINT uiCmd,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Parametry

*[in] uiCmd*<br/>
Określa identyfikator polecenia.

*[in] bIsVisible*<br/>
Ustawia wartość określającą polecenie gdy paska narzędzi Szybki dostęp, jest w stanie domyślnym.

### <a name="remarks"></a>Uwagi

Dodawanie polecenia do CMFCRibbonQuickAccessToolBarDefaultState w ramach trzech wyników. Po pierwsze każde polecenie dodano znajduje się na liście rozwijanej po prawej stronie paska narzędzi Szybki dostęp. W ten sposób użytkownik może łatwo dodać lub usunąć to polecenie z paska narzędzi Szybki dostęp. Po drugie, paska narzędzi szybkiego dostępu jest resetowany do wyświetlenia tylko tych poleceń, które są wymienione jako widoczny w stanie domyślnym kiedy użytkownik kliknie **resetowania** znajdujący się w **Dostosuj** okno dialogowe. Trzeci, jeśli nie wywołano [CMFCRibbonBar::SetQuickAccessCommands](../../mfc/reference/cmfcribbonbar-class.md#setquickaccesscommands), paska narzędzi szybkiego dostępu używa widocznych poleceń z tej listy jako domyślne polecenia widoczny użytkownik uruchamia aplikację po raz pierwszy. Po dodaniu wszystkich poleceń, które chcesz wywołać [CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate) można ustawić tego wystąpienia jako domyślny stan dla paska narzędzi Szybki dostęp z tego paska wstążki.

##  <a name="copyfrom"></a>  CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom

Kopiuje właściwości jednego paska narzędzi Szybki dostęp do innej lokalizacji.

```
void CopyFrom(const CMFCRibbonQuickAccessToolBarDefaultState& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
[in] Odwołanie do źródła `CMFCRibbonQuickAccessToolBarDefaultState` obiektu do skopiowania.

### <a name="remarks"></a>Uwagi

Ta metoda kopiuje każdego polecenia ze źródła `CMFCRibbonQuickAccessToolBarDefaultState` obiektu do tego obiektu przy użyciu [CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand) metody.

##  <a name="cmfcribbonquickaccesstoolbardefaultstate"></a>  CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState

Tworzy obiekt stanu domyślnego paska narzędzi Szybki dostęp.

```
CMFCRibbonQuickAccessToolBarDefaultState();
```

### <a name="remarks"></a>Uwagi

Domyślnie lista poleceń, nowe wystąpienie klasy [CMFRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md) zawiera jest pusty.

##  <a name="removeall"></a>  CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll

Czyści listę domyślnych poleceń w paska narzędzi Szybki dostęp.

```
void RemoveAll();
```

### <a name="remarks"></a>Uwagi

Ta funkcja spowoduje usunięcie wszystkich poleceń z tego wystąpienia, poprzedniego wywołania [CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand) dodane.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)
