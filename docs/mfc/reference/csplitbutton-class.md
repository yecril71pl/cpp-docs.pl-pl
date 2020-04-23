---
title: Klasa CSplitButton
ms.date: 11/19/2018
f1_keywords:
- CSplitButton
- AFXCMN/CSplitButton
- AFXCMN/CSplitButton::CSplitButton
- AFXCMN/CSplitButton::Create
- AFXCMN/CSplitButton::SetDropDownMenu
- AFXCMN/CSplitButton::OnDropDown
helpviewer_keywords:
- CSplitButton [MFC], CSplitButton
- CSplitButton [MFC], Create
- CSplitButton [MFC], SetDropDownMenu
- CSplitButton [MFC], OnDropDown
ms.assetid: 6844d0a9-6408-4e44-9b5f-57628ed8bad6
ms.openlocfilehash: 38fceed1cc42ca0aac2e6ddaf145db273c95771d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753129"
---
# <a name="csplitbutton-class"></a>Klasa CSplitButton

Klasa `CSplitButton` reprezentuje formant przycisku podziału. Formant przycisku podziału wykonuje domyślne zachowanie, gdy użytkownik kliknie główną część przycisku i wyświetla menu rozwijane, gdy użytkownik kliknie strzałkę rozwijaną przycisku.

## <a name="syntax"></a>Składnia

```
class CSplitButton : public CButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSplitButton::CSplitButton](#csplitbutton)|Konstruuje `CSplitButton` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSplitButton::Utwórz](#create)|Tworzy formant przycisku podziału z określonymi `CSplitButton` stylami i dołącza go do bieżącego obiektu.|
|[CSplitButton::SetDropDownMenu](#setdropdownmenu)|Ustawia menu rozwijane wyświetlane po kliknięciu przez użytkownika strzałki rozwijanej bieżącego przycisku podziału.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CSplitButton::OnDropDown](#ondropdown)|Obsługuje powiadomienie BCN_DROPDOWN, które system wysyła, gdy użytkownik kliknie strzałkę rozwijaną bieżącego formantu przycisku podziału.|

## <a name="remarks"></a>Uwagi

Klasa `CSplitButton` jest pochodną [CButton](../../mfc/reference/cbutton-class.md) klasy. Formant przycisku podziału jest formantem przycisku, którego styl jest BS_SPLITBUTTON. Wyświetla niestandardowe menu, gdy użytkownik kliknie strzałkę listy rozwijanej. Aby uzyskać więcej informacji, zobacz style BS_SPLITBUTTON i BS_DEFSPLITBUTTON w obszarze [Style przycisków](/windows/win32/Controls/button-styles).

Na poniższej ilustracji przedstawiono okno dialogowe zawierające kontrolkę pagera i (1) sterowanie przyciskiem podziału. Strzałka rozwijana (2) została już kliknięta i zostanie wyświetlona podmenu (3).

![Okno dialogowe z kontrolką splitbutton i pager.](../../mfc/reference/media/splitbutton_pager.png "Okno dialogowe z kontrolką splitbutton i pager.")

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cbutton](../../mfc/reference/cbutton-class.md)

`CSplitButton`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn.h

Ta klasa jest obsługiwana w systemie Windows Vista i nowszych.

Dodatkowe wymagania dla tej klasy są opisane w [wymagania dotyczące kompilacji dla wspólnych formantów systemu Windows Vista](../../mfc/build-requirements-for-windows-vista-common-controls.md).

## <a name="csplitbuttoncreate"></a><a name="create"></a>CSplitButton::Utwórz

Tworzy formant przycisku podziału z określonymi `CSplitButton` stylami i dołącza go do bieżącego obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Dwstyle*|[w] Bitowe połączenie (OR) stylów, które mają być stosowane do formantu. Aby uzyskać więcej informacji, zobacz [Style przycisków](../../mfc/reference/styles-used-by-mfc.md#button-styles).|
|*Rect*|[w] Odwołanie do [struktury RECT,](/windows/win32/api/windef/ns-windef-rect) która zawiera położenie i rozmiar formantu.|
|*pParentWnd*|[w] Wskaźnik inny niż null do [obiektu CWnd,](../../mfc/reference/cwnd-class.md) który jest nadrzędnym oknem formantu.|
|*Nid*|[w] Identyfikator formantu.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

## <a name="csplitbuttoncsplitbutton"></a><a name="csplitbutton"></a>CSplitButton::CSplitButton

Konstruuje `CSplitButton` obiekt. Parametry konstruktora określają podmenu, które jest wyświetlane, gdy użytkownik kliknie strzałkę rozwijaną formantu przycisku podziału.

```
CSplitButton();

CSplitButton(
    UINT nMenuId,
    UINT nSubMenuId)
CSplitButton(CMenu* pMenu)
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*nMenuId*|[w] Identyfikator zasobu paska menu.|
|*nMenuid nSubMenuId*|[w] Identyfikator zasobu podmenu.|
|*pMenu*|[w] Wskaźnik do obiektu [CMenu,](../../mfc/reference/cmenu-class.md) który określa podmenu. Obiekt `CSplitButton` usuwa `CMenu` obiekt i skojarzony z nim `CSplitButton` HMENU, gdy obiekt wykracza poza zakres.|

### <a name="remarks"></a>Uwagi

Użyj [CSplitButton::Create](#create) metody, aby utworzyć formant przycisku podziału i dołączyć go do `CSplitButton` obiektu.

## <a name="csplitbuttonondropdown"></a><a name="ondropdown"></a>CSplitButton::OnDropDown

Obsługuje powiadomienie BCN_DROPDOWN, które system wysyła, gdy użytkownik kliknie strzałkę rozwijaną bieżącego formantu przycisku podziału.

```
afx_msg void OnDropDown(
    NMHDR* pNMHDR,
    LRESULT* pResult);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pNMHDR*|[w] Wskaźnik do struktury [NMHDR,](/windows/win32/api/richedit/ns-richedit-nmhdr) który zawiera informacje o [powiadomieniu BCN_DROPDOWN.](/windows/win32/Controls/bcn-dropdown)|
|*Presult*|[na zewnątrz] (Nieużyno; zwracana jest żadna wartość). Zwraca wartość powiadomienia [BCN_DROPDOWN.](/windows/win32/Controls/bcn-dropdown)|

### <a name="remarks"></a>Uwagi

Gdy użytkownik kliknie strzałkę listy rozwijanej na formancie przycisku podziału, `OnDropDown` system wysyła komunikat powiadomienia BCN_DROPDOWN, który obsługuje metoda. Jednak `CSplitButton` obiekt nie przekazuje powiadomienia BCN_DROPDOWN do formantu, który zawiera formant podziału przycisku. W związku z tym formant zawierający nie może obsługiwać akcji niestandardowej w odpowiedzi na powiadomienie.

Aby zaimplementować akcję niestandardową, która obsługuje formant zawierający, należy użyć [CButton](../../mfc/reference/cbutton-class.md) obiektu o stylu BS_SPLITBUTTON zamiast `CSplitButton` obiektu. Następnie zaimplementuj program obsługi `CButton` dla powiadomienia BCN_DROPDOWN w obiekcie. Aby uzyskać więcej informacji, zobacz [Style przycisków](../../mfc/reference/styles-used-by-mfc.md#button-styles).

Aby zaimplementować akcję niestandardową, którą obsługuje sama kontrola przycisku podziału, użyj [odbicia wiadomości](../../mfc/tn062-message-reflection-for-windows-controls.md). Wywodź własną `CSplitButton` klasę z klasy i nazwij ją, na przykład CMySplitButton. Następnie dodaj następującą mapę wiadomości do aplikacji, aby obsłużyć powiadomienie BCN_DROPDOWN:

```
BEGIN_MESSAGE_MAP(CMySplitButton,
    CSplitButton)
    ON_NOTIFY_REFLECT(BCN_DROPDOWN, &CMySplitButton::OnDropDown)
END_MESSAGE_MAP()
```

## <a name="csplitbuttonsetdropdownmenu"></a><a name="setdropdownmenu"></a>CSplitButton::SetDropDownMenu

Ustawia menu rozwijane wyświetlane po kliknięciu przez użytkownika strzałki rozwijanej bieżącego przycisku podziału.

```cpp
void SetDropDownMenu(
    UINT nMenuId,
    UINT nSubMenuId);

void SetDropDownMenu(CMenu* pMenu);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*nMenuId*|[w] Identyfikator zasobu paska menu.|
|*nMenuid nSubMenuId*|[w] Identyfikator zasobu podmenu.|
|*pMenu*|[w] Wskaźnik do obiektu [CMenu,](../../mfc/reference/cmenu-class.md) który określa podmenu. Obiekt `CSplitButton` usuwa `CMenu` obiekt i skojarzony z nim `CSplitButton` HMENU, gdy obiekt wykracza poza zakres.|

### <a name="remarks"></a>Uwagi

Parametr *nMenuId* identyfikuje pasek menu, który jest poziomą listą elementów paska menu. Parametr *nSubMenuId* jest zerowym numerem indeksu identyfikującym podmenu, który jest rozwijaną listą elementów menu skojarzonych z każdym elementem paska menu. Na przykład typowa aplikacja ma menu, które zawiera elementy paska menu, "Plik", "Edytuj" i "Pomoc". Pozycja paska menu "Plik" ma podmenu, które zawiera elementy menu, "Otwórz", "Zamknij" i "Zakończ". Po kliknięciu strzałki rozwijanej formantu z przyciskiem podziału formant wyświetla określone podmenu, a nie pasek menu.

Na poniższej ilustracji przedstawiono okno dialogowe zawierające kontrolkę pagera i (1) sterowanie przyciskiem podziału. Strzałka rozwijana (2) została już kliknięta i zostanie wyświetlona podmenu (3).

![Okno dialogowe z kontrolką splitbutton i pager.](../../mfc/reference/media/splitbutton_pager.png "Okno dialogowe z kontrolką splitbutton i pager.")

### <a name="example"></a>Przykład

Pierwsza instrukcja w poniższym przykładzie kodu pokazuje [CSplitButton::SetDropDownMenu](#setdropdownmenu) metody. Stworzyliśmy menu za pomocą edytora zasobów programu Visual Studio, który automatycznie nazwał identyfikator paska menu IDR_MENU1. Parametr *nSubMenuId,* który wynosi zero, odnosi się do jedynego podmenu paska menu.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/csplitbutton-class_1.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa CSplitButton](../../mfc/reference/csplitbutton-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CButton](../../mfc/reference/cbutton-class.md)
