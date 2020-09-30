---
title: Kontrolki okna dialogowego (C++) | Microsoft Docs
ms.date: 02/15/2019
f1_keywords:
- Custom Control
helpviewer_keywords:
- controls [C++], dialog boxes
- dialog box controls [C++], about dialog box controls
- dialog box controls
- controls [C++], templates
- custom controls [C++], dialog boxes
- custom controls [C++]
- dialog box controls [C++], custom (user) controls
- Dialog Editor [C++], custom controls
ms.assetid: e216c4f9-2fd4-429d-889a-8ebce7bad177
ms.openlocfilehash: 449e60e968916f7741422ca2766375ad29afd062
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505710"
---
# <a name="dialog-box-controls-c"></a>Kontrolki okna dialogowego (C++)

Można dodać kontrolki do okna dialogowego za pomocą karty **edytora okien dialogowych** w [oknie przybornika](/visualstudio/ide/reference/toolbox) , która umożliwia wybranie żądanego formantu i przeciągnięcie go do okna dialogowego. Domyślnie w oknie **przybornika** jest ustawiona wartość Autoukrywanie. Pojawia się jako karta na lewym marginesie rozwiązania, gdy **Edytor okien dialogowych** jest otwarty. Można jednak przypiąć okno **przybornika** do pozycji, wybierając przycisk **Autoukrywanie** w prawym górnym rogu okna. Aby uzyskać więcej informacji na temat sposobu kontrolowania zachowania tego okna, zobacz [Zarządzanie systemem Windows](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Najszybszym sposobem dodawania kontrolek do okna dialogowego, zmiany położenia istniejących kontrolek lub przenoszenia formantów z jednego okna dialogowego do innego, jest użycie metody przeciągania i upuszczania. Położenie kontrolki jest opisane w linii kropkowanej, dopóki nie zostanie porzucone do okna dialogowego. Po dodaniu kontrolki do okna dialogowego z metodą przeciągania i upuszczania formant uzyskuje standardową wysokość odpowiednią do tego typu kontrolki.

Gdy dodasz kontrolkę do okna dialogowego lub zmieniasz jej położenie, końcowe umieszczanie może być określone przez prowadnice lub marginesy albo czy masz włączoną siatkę układu.

Po dodaniu kontrolki do okna dialogowego można zmienić właściwości, takie jak podpis w [oknie właściwości](/visualstudio/ide/reference/properties-window). Możesz również wybrać wiele kontrolek i zmienić ich właściwości jednocześnie.

Aby uzyskać więcej informacji o **edytorze okien dialogowych**, zobacz jak [dodawać, edytować lub usuwać kontrolki](adding-editing-or-deleting-controls.md), [kontrolki układu](../windows/arrangement-of-controls-on-dialog-boxes.md)oraz [definiować dostęp i wartości kontroli](../windows/defining-mnemonics-access-keys.md).

Aby uzyskać więcej informacji na temat kontrolek i okien dialogowych, zobacz [klasy formantów](../mfc/control-classes.md), [klasy okien dialogowych](../mfc/dialog-box-classes.md)i [Style paska przewijania](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles).

Standardowe kontrolki dostępne w **przyborniku** z domyślnymi zdarzeniami są następujące:

|Nazwa kontrolki|Zdarzenie domyślne|
|---|---|
|[Button — formant](../mfc/reference/cbutton-class.md)|BN_CLICKED|
|[Kontrolka pola wyboru](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Kontrolka pola kombi](../mfc/reference/ccombobox-class.md)|CBN_SELCHANGE|
|[Edytuj kontrolkę](../mfc/reference/cedit-class.md)|EN_CHANGE|
|Pole grupy|(nie dotyczy)|
|[Kontrolka pola listy](../mfc/reference/clistbox-class.md)|LBN_SELCHANGE|
|[Kontrolka przycisku radiowego](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Statyczna kontrolka tekstowa](../mfc/reference/cstatic-class.md)|(nie dotyczy)|
|[Kontrolka obrazu](../mfc/reference/cpictureholder-class.md)|(nie dotyczy)|
|[Kontrolka edycji wzbogaconej 2,0](../mfc/using-cricheditctrl.md)|EN_CHANGE|
|[Kontrolka paska przewijania](../mfc/reference/cscrollbar-class.md)|NM_THEMECHANGED|

> [!NOTE]
> Aby uzyskać więcej informacji na temat używania formantu **richedit 1,0** z MFC, zobacz [Używanie kontrolki RichEdit 1,0 z](./adding-editing-or-deleting-controls.md) [przykładami formantów MFC i Rich Edit](../mfc/rich-edit-control-examples.md).

[Formanty standardowe systemu Windows](../mfc/controls-mfc.md) dostępne w **przyborniku** zapewniają zwiększoną funkcjonalność:

|Nazwa kontrolki|Zdarzenie domyślne|
|---|---|
|[suwak](../mfc/slider-control-styles.md)|NM_CUSTOMDRAW|
|[Kontrolka pokrętła](../mfc/using-cspinbuttonctrl.md)|UDN_DELTAPOS|
|[Kontrolka postępu](../mfc/styles-for-the-progress-control.md)|NM_CUSTOMDRAW|
|[Kontrolka klawisza dostępu](../mfc/using-a-hot-key-control.md)|NM_OUTOFMEMORY|
|[Kontrolka listy](../mfc/list-control-and-list-view.md)|LVN_ITEMCHANGE|
|[Kontrolka drzewa](../mfc/tree-control-styles.md)|TVN_SELCHANGE|
|[Kontrolka karta](../mfc/tab-controls-and-property-sheets.md)|TCN_SELCHANGE|
|[Kontrolka animacji](../mfc/using-an-animation-control.md)|ACN_START|
|[Kontrolka selektora daty i godziny](../mfc/creating-the-date-and-time-picker-control.md)|DTN_DATETIMECHANGE|
|[Formant kalendarza miesięcznego](../mfc/month-calendar-control-examples.md)|MCN_SELCHANGE|
|[Kontrola adresów IP](../mfc/reference/cipaddressctrl-class.md)|IPN_FIELDCHANGED|
|[Kontrolka rozszerzonego pola kombi](../mfc/creating-an-extended-combo-box-control.md)||
|Kontrolka niestandardowa|TTN_GETDISPINFO|

## <a name="custom-controls"></a>Formanty niestandardowe

**Edytor okien dialogowych** umożliwia używanie istniejących kontrolek niestandardowych lub użytkownika w szablonie okna dialogowego.

> [!NOTE]
> Kontrolki niestandardowe w tym sensie nie należy mylić z kontrolkami ActiveX. Formanty ActiveX były czasami nazywane kontrolkami niestandardowymi OLE. Ponadto nie należy mylić tych kontrolek z kontrolkami rysowanymi przez właściciela w systemie Windows.

Ta funkcja ma umożliwić korzystanie z kontrolek innych niż dostarczane przez system Windows. W czasie wykonywania kontrolka jest skojarzona z klasą okna (nie taka sama jak Klasa języka C++). Bardziej typowym sposobem wykonania tego samego zadania jest zainstalowanie dowolnej kontrolki, takiej jak kontrolka statyczna, w oknie dialogowym. Następnie w czasie wykonywania w funkcji [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) Usuń tę kontrolkę i Zastąp ją własną kontrolką niestandardową.

> [!NOTE]
> Jest to stara technika. Dzisiaj zaleca się, aby w większości przypadków napisać kontrolkę ActiveX lub podklasę ze wspólną kontrolą systemu Windows.

W przypadku tych kontrolek niestandardowych można:

- Ustawianie lokalizacji w oknie dialogowym.

- Wpisywanie podpisu.

- Identyfikowanie nazwy klasy systemu Windows kontrolki, ponieważ kod aplikacji musi zarejestrować formant według tej nazwy.

- Wpisanie 32-bitowej wartości szesnastkowej, która ustawia styl kontrolki.

- Ustawianie stylu rozszerzonego.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytor okien dialogowych](../windows/dialog-editor.md)

<!--
[Adding Event Handlers for Dialog Box Controls](./adding-editing-or-deleting-controls.md)<br/>
[Dialog Box Controls and Variable Types](../ide/adding-a-member-variable-visual-cpp.md#dialog-box-controls-and-variable-types)<br/>
[Controls](../mfc/controls-mfc.md)<br/>-->
