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
ms.openlocfilehash: a552334adb4963f45388a798eb0723e61c09ec85
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502837"
---
# <a name="csplitbutton-class"></a>Klasa CSplitButton

`CSplitButton` Klasa reprezentuje kontrolkę przycisku podziału. Kontrolka przycisku podziału wykonuje domyślne zachowanie, gdy użytkownik kliknie główną część przycisku, a następnie wyświetla menu rozwijane, gdy użytkownik kliknie strzałkę listy rozwijanej przycisku.

## <a name="syntax"></a>Składnia

```
class CSplitButton : public CButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSplitButton:: CSplitButton](#csplitbutton)|Konstruuje `CSplitButton` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSplitButton:: Create](#create)|Tworzy kontrolkę przycisku podziału z określonymi stylami i dołącza ją do bieżącego `CSplitButton` obiektu.|
|[CSplitButton:: SetDropDownMenu](#setdropdownmenu)|Ustawia menu rozwijane, które jest wyświetlane, gdy użytkownik kliknie strzałkę listy rozwijanej bieżącego przycisku podziału.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CSplitButton:: OnDropDown](#ondropdown)|Obsługuje powiadomienie BCN_DROPDOWN wysyłane przez system, gdy użytkownik kliknie strzałkę listy rozwijanej bieżącego przycisku podziału.|

## <a name="remarks"></a>Uwagi

Klasa pochodzi od klasy CButton. [](../../mfc/reference/cbutton-class.md) `CSplitButton` Kontrolka przycisku podziału jest kontrolką przycisku, której styl jest BS_SPLITBUTTON. Wyświetla niestandardowe menu, gdy użytkownik kliknie strzałkę listy rozwijanej. Aby uzyskać więcej informacji, zobacz Style BS_SPLITBUTTON i BS_DEFSPLITBUTTON w [stylach przycisków](/windows/win32/Controls/button-styles).

Poniższa ilustracja przedstawia okno dialogowe, które zawiera formant modułu stronicowania i kontrolkę (1) przycisk podziału. Strzałka listy rozwijanej (2) została już kliknięta i zostanie wyświetlone podmenu (3).

![Okno dialogowe z kontrolką SplitButton imodułem stronicowania](../../mfc/reference/media/splitbutton_pager.png "Okno dialogowe z kontrolką SplitButton i")

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CSplitButton`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn. h

Ta klasa jest obsługiwana w systemie Windows Vista i nowszych.

Dodatkowe wymagania dotyczące tej klasy zostały opisane w temacie [wymagania dotyczące kompilacji dla wspólnych formantów systemu Windows Vista](../../mfc/build-requirements-for-windows-vista-common-controls.md).

##  <a name="create"></a>CSplitButton:: Create

Tworzy kontrolkę przycisku podziału z określonymi stylami i dołącza ją do bieżącego `CSplitButton` obiektu.

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
|*dwStyle*|podczas Kombinacja bitowa (lub) stylów do zastosowania do kontrolki. Aby uzyskać więcej informacji, zobacz [style przycisków](../../mfc/reference/styles-used-by-mfc.md#button-styles).|
|*cinania*|podczas Odwołanie do struktury [Rect](/previous-versions/dd162897\(v=vs.85\)) , która zawiera położenie i rozmiar kontrolki.|
|*pParentWnd*|podczas Wskaźnik o wartości innej niż null do obiektu [CWnd](../../mfc/reference/cwnd-class.md) , który jest oknem nadrzędnym formantu.|
|*nID*|podczas Identyfikator kontrolki.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

##  <a name="csplitbutton"></a>CSplitButton:: CSplitButton

Konstruuje `CSplitButton` obiekt. Parametry konstruktora określają podmenu, które jest wyświetlane, gdy użytkownik kliknie strzałkę listy rozwijanej kontrolki przycisku podziału.

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
|*nMenuId*|podczas Identyfikator zasobu paska menu.|
|*nSubMenuId*|podczas Identyfikator zasobu podmenu.|
|*pMenu*|podczas Wskaźnik do obiektu [CMenu](../../mfc/reference/cmenu-class.md) , który określa podmenu. Obiekt usuwa obiekt i`CSplitButton` jego skojarzony HMENU, gdy obiekt wykracza poza zakres. `CMenu` `CSplitButton`|

### <a name="remarks"></a>Uwagi

Użyj metody [CSplitButton:: Create](#create) , aby utworzyć kontrolkę przycisku podziału i dołączyć ją do `CSplitButton` obiektu.

##  <a name="ondropdown"></a>CSplitButton:: OnDropDown

Obsługuje powiadomienie BCN_DROPDOWN wysyłane przez system, gdy użytkownik kliknie strzałkę listy rozwijanej bieżącego przycisku podziału.

```
afx_msg void OnDropDown(
    NMHDR* pNMHDR,
    LRESULT* pResult);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pNMHDR*|podczas Wskaźnik na strukturę [NMHDR](/windows/win32/api/richedit/ns-richedit-nmhdr) , która zawiera informacje o powiadomieniu [BCN_DROPDOWN](/windows/win32/Controls/bcn-dropdown) .|
|*pResult*|określoną (Nieużywane; nie jest zwracana żadna wartość). Wartość zwracana powiadomienia [BCN_DROPDOWN](/windows/win32/Controls/bcn-dropdown) .|

### <a name="remarks"></a>Uwagi

Gdy użytkownik kliknie strzałkę listy rozwijanej w formancie przycisku podziału, System wyśle komunikat powiadomienia BCN_DROPDOWN, który `OnDropDown` obsługuje metodę. `CSplitButton` Jednak obiekt nie przekazuje powiadomienia BCN_DROPDOWN do formantu, który zawiera kontrolkę przycisku podziału. W związku z tym, zawiera formant nie obsługuje akcji niestandardowej w odpowiedzi na powiadomienie.

Aby zaimplementować akcję niestandardową obsługiwaną przez formant, użyj obiektu [CButton](../../mfc/reference/cbutton-class.md) z stylem BS_SPLITBUTTON zamiast `CSplitButton` obiektu. Następnie Zaimplementuj procedurę obsługi dla powiadomienia BCN_DROPDOWN w `CButton` obiekcie. Aby uzyskać więcej informacji, zobacz [style przycisków](../../mfc/reference/styles-used-by-mfc.md#button-styles).

Aby zaimplementować akcję niestandardową, która jest obsługiwana przez formant przycisku podziału, użyj [odbicia komunikatów](../../mfc/tn062-message-reflection-for-windows-controls.md). Utwórz własną klasę z `CSplitButton` klasy i nadaj jej nazwę, na przykład CMySplitButton. Następnie Dodaj następującą mapę komunikatów do aplikacji, aby obsłużyć powiadomienie BCN_DROPDOWN:

```
BEGIN_MESSAGE_MAP(CMySplitButton,
    CSplitButton)
    ON_NOTIFY_REFLECT(BCN_DROPDOWN, &CMySplitButton::OnDropDown)
END_MESSAGE_MAP()
```

##  <a name="setdropdownmenu"></a>CSplitButton:: SetDropDownMenu

Ustawia menu rozwijane, które jest wyświetlane, gdy użytkownik kliknie strzałkę listy rozwijanej bieżącego przycisku podziału.

```
void SetDropDownMenu(
    UINT nMenuId,
    UINT nSubMenuId);

void SetDropDownMenu(CMenu* pMenu);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*nMenuId*|podczas Identyfikator zasobu paska menu.|
|*nSubMenuId*|podczas Identyfikator zasobu podmenu.|
|*pMenu*|podczas Wskaźnik do obiektu [CMenu](../../mfc/reference/cmenu-class.md) , który określa podmenu. Obiekt usuwa obiekt i`CSplitButton` jego skojarzony HMENU, gdy obiekt wykracza poza zakres. `CMenu` `CSplitButton`|

### <a name="remarks"></a>Uwagi

Parametr *nMenuId* określa pasek menu, który jest poziomą listą elementów paska menu. Parametr *nSubMenuId* jest numerem indeksu liczonym od zera, który identyfikuje podmenu, czyli listę rozwijaną elementów menu skojarzonych z każdym elementem paska menu. Na przykład typowa aplikacja ma menu, które zawiera elementy paska menu, "plik", "Edytuj" i "pomoc". Element paska menu "plik" ma podmenu zawierające elementy menu, "Otwórz", "Zamknij" i "Zakończ". Gdy zostanie kliknięta strzałka listy rozwijanej kontrolki Split-Button, kontrolka wyświetli określone podmenu, a nie pasek menu.

Poniższa ilustracja przedstawia okno dialogowe, które zawiera formant modułu stronicowania i kontrolkę (1) przycisk podziału. Strzałka listy rozwijanej (2) została już kliknięta i zostanie wyświetlone podmenu (3).

![Okno dialogowe z kontrolką SplitButton imodułem stronicowania](../../mfc/reference/media/splitbutton_pager.png "Okno dialogowe z kontrolką SplitButton i")

### <a name="example"></a>Przykład

Pierwsza instrukcja w poniższym przykładzie kodu demonstruje metodę [CSplitButton:: SetDropDownMenu](#setdropdownmenu) . Utworzyliśmy menu za pomocą edytora zasobów programu Visual Studio, który automatycznie nosi nazwę paska menu IDR_MENU1. *NSubMenuId* parametr, który jest zerem, odnosi się do jedynego podmenu paska menu.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/csplitbutton-class_1.cpp)]

## <a name="see-also"></a>Zobacz także

[Klasa CSplitButton](../../mfc/reference/csplitbutton-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CButton](../../mfc/reference/cbutton-class.md)
