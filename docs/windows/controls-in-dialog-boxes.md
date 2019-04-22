---
title: Formanty okna dialogowego (C++) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 563cf73299c00413889ada2520b1bf4fcd86f2be
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59023701"
---
# <a name="dialog-box-controls-c"></a>Formanty okna dialogowego (C++)

Formanty można dodać za pomocą okno dialogowe **Edytor okien dialogowych** karcie [okno przybornika](/visualstudio/ide/reference/toolbox) który umożliwia wybranie kontrolki ma i przeciągnij go do okna dialogowego. Domyślnie **przybornika** okna jest ustawiona na automatyczne ukrywanie. Będzie ono wyświetlane jako karty na lewym marginesie rozwiązania podczas **Edytor okien dialogowych** jest otwarty. Jednakże, możesz przypiąć **przybornika** okna w miejscu, wybierając **Autoukrywanie** przycisk w prawym górnym rogu okna. Aby uzyskać więcej informacji na temat sposobu kontrolowania zachowania tego okna, zobacz [Zarządzanie oknem](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Najszybszym sposobem na dodawanie formantów do okna dialogowego, zmienianie położenia istniejących kontrolek lub przenoszenie formantów w oknie dialogowym do innego, jest metodą przeciągania i upuszczania. Położenie kontrolki jest opisany w linia kropkowana, dopóki nie zostanie usunięte w oknie dialogowym. Po dodaniu kontrolki do okna dialogowego za pomocą metody przeciągania i upuszczania kontrolki otrzymuje standardową wysokość odpowiednie dla tego typu kontrolki.

Podczas dodawania kontrolki do okna dialogowego lub zmienić jej położenie, jego położenie końcowego może zależeć od prowadnice i marginesy, czy należy wprowadzić jakieś siatki układu włączona.

Po dodaniu kontrolki do okna dialogowego, można zmienić właściwości, takie jak jego podpis w [okno właściwości](/visualstudio/ide/reference/properties-window). Można również wybrać kilka formantów i zmiany ich właściwości wszystkie na raz.

Aby uzyskać więcej informacji na temat **Edytor okien dialogowych**, zobacz instrukcje [Dodawanie, edytowanie lub usuwanie kontrolek](adding-editing-or-deleting-controls.md), [układu kontrolek](../windows/arrangement-of-controls-on-dialog-boxes.md), i [wartościidefiniowaniekontrolidostępu](../windows/defining-mnemonics-access-keys.md).

Aby uzyskać więcej informacji o oknach dialogowych i formantów, zobacz [klasy kontrolek](../mfc/control-classes.md), [klasy okien dialogowych](../mfc/dialog-box-classes.md), i [Style paska przewijania](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles).

Formanty standardowe dostępne w **przybornika** z domyślną zdarzenia są:

|Nazwa kontrolki|Domyślne zdarzenia|
|---|---|
|[Kontrolka przycisku](../mfc/reference/cbutton-class.md)|BN_CLICKED|
|[Kontrolka pola wyboru](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Kontrolka pola kombi](../mfc/reference/ccombobox-class.md)|CBN_SELCHANGE|
|[Edytuj kontrolkę](../mfc/reference/cedit-class.md)|EN_CHANGE|
|Pole grupy|(nie dotyczy)|
|[Kontrolka pola listy](../mfc/reference/clistbox-class.md)|LBN_SELCHANGE|
|[Kontrolka przycisku radiowego](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Kontrolka tekstu statycznego](../mfc/reference/cstatic-class.md)|(nie dotyczy)|
|[Formant obrazu](../mfc/reference/cpictureholder-class.md)|(nie dotyczy)|
|[Kontrolka 2.0 edycji wzbogaconej](../mfc/using-cricheditctrl.md)|EN_CHANGE|
|[Pasek przewijania](../mfc/reference/cscrollbar-class.md)|NM_THEMECHANGED|

> [!NOTE]
> Aby uzyskać więcej informacji na temat korzystania z **RichEdit 1.0** kontrolką MFC, zobacz [używanie formantu RichEdit 1.0 z MFC](../windows/using-the-richedit-1-0-control-with-mfc.md) i [przykłady formantów edycji wzbogaconej](../mfc/rich-edit-control-examples.md).

[Wspólnych formantów Windows](../mfc/controls-mfc.md) dostępne w **przybornika** aby zapewnić większą funkcjonalność są:

|Nazwa kontrolki|Domyślne zdarzenia|
|---|---|
|[Kontrolka suwaka](../mfc/slider-control-styles.md)|NM_CUSTOMDRAW|
|[Kontrolki pokrętła](../mfc/using-cspinbuttonctrl.md)|UDN_DELTAPOS|
|[Kontrolki postępu](../mfc/styles-for-the-progress-control.md)|NM_CUSTOMDRAW|
|[Formantu klawisza dostępu](../mfc/using-a-hot-key-control.md)|NM_OUTOFMEMORY —|
|[Kontrolka listy](../mfc/list-control-and-list-view.md)|LVN_ITEMCHANGE|
|[Kontrolka drzewa](../mfc/tree-control-styles.md)|TVN_SELCHANGE|
|[Kontrolki karty](../mfc/tab-controls-and-property-sheets.md)|TCN_SELCHANGE|
|[Kontrolki animacji](../mfc/using-an-animation-control.md)|ACN_START|
|[Kontrolka czasu selektora daty](../mfc/creating-the-date-and-time-picker-control.md)|DTN_DATETIMECHANGE|
|[Kontrolowanie kalendarza miesięcznego](../mfc/month-calendar-control-examples.md)|MCN_SELCHANGE|
|[Formant adresu IP](../mfc/reference/cipaddressctrl-class.md)|IPN_FIELDCHANGED|
|[Rozszerzone formant pola kombi](../mfc/creating-an-extended-combo-box-control.md)||
|Kontrolka niestandardowa|TTN_GETDISPINFO|

## <a name="custom-controls"></a>Formanty niestandardowe

**Edytor okien dialogowych** umożliwia Użyj istniejącej niestandardowej lub kontrolki użytkownika w szablonu okna dialogowego.

> [!NOTE]
> Niestandardowe formanty w tym sensie są nie należy mylić z kontrolkami ActiveX. Kontrolki ActiveX były nazywane niestandardowych formantów OLE. Ponadto nie należy mylić tych kontrolek z kontrolki rysowane przez właściciela z Windows.

Ta funkcja jest przeznaczona do umożliwiają używanie kontrolek w inne niż te dostarczone przez Windows. W czasie wykonywania kontrolka jest skojarzony z klasy okna (nie taka sama jak klasa C++). Jest bardziej typowym sposobem wykonania tego samego zadania do zainstalowania dowolnej kontrolki, takie jak formant statyczny w oknie dialogowym. Następnie w czasie wykonywania w [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) funkcji, Usuń tę kontrolkę i zastąp go własny niestandardowy formant.

> [!NOTE]
> Jest to technika stary. Obecnie zaleca w większości przypadków można zapisać formantu ActiveX lub podklasy formantu wspólnego Windows.

W przypadku kontrolek niestandardowych są ograniczone do:

- Ustawianie lokalizacji w oknie dialogowym.

- Wpisywanie podpisu.

- Identyfikowanie nazwę formantu Windows klasy, ponieważ kod aplikacji należy go zarejestrować przy użyciu tej nazwy.

- Wpisując wartość szesnastkową 32-bitowe i ustawia styl formantu.

- Ustawianie rozszerzonego stylu.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Edytor okien dialogowych](../windows/dialog-editor.md)<br/>

<!--
[Adding Event Handlers for Dialog Box Controls](../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)<br/>
[Controls](../mfc/controls-mfc.md)<br/>-->