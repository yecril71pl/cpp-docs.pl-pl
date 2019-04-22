---
title: Edytor okien dialogowych (C++)
ms.date: 02/15/2019
f1_keywords:
- vc.editors.dialog.dialog
- vc.editors.dialog.F1
- vc.editors.dialog
helpviewer_keywords:
- resource editors [C++], Dialog editor
- editors, dialog boxes
- Dialog editor
- dialog boxes [C++], editing
- controls [C++], showing or hiding Dialog editor toolbar
- toolbars [C++], showing
- toolbars [C++], hiding
- Dialog Editor [C++], showing or hiding toolbar
- events [C++], viewing for controls
- Windows messages [C++], controls
- messages [C++], viewing for dialog boxes
- Dialog Editor [C++], accessing code
- code [C++], switching from Dialog Editor
- controls [C++], jumping to code
- Dialog Editor [C++], switching between controls and code
- Dialog Editor [C++], shortcut keys
ms.assetid: d94884ef-2cca-49d8-9b58-775f34848134
ms.openlocfilehash: dc5a823951e07af96efceec52d2aa23552c2d002
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59029489"
---
# <a name="dialog-editor-c"></a>Edytor okien dialogowych (C++)

**Edytor okien dialogowych** pozwala na tworzenie lub edytowanie zasobów okien dialogowych.

- Aby otworzyć Edytor, kliknij dwukrotnie plik .rc okna dialogowego w **widok zasobów** okna lub przejdź do menu **widoku** > **widok zasobów**.

Jedną z pierwszych kroków w tworzeniu nowego okna dialogowego lub szablonu okna dialogowego, jest dodanie formantów. W **Edytor okien dialogowych**, można rozmieścić formanty w celu dopasowania niektórych rozmiaru, kształtu lub wyrównania lub przenosić je około do pracy w oknie dialogowym. W łatwy sposób można również usunąć formant.

Okno dialogowe można przechowywać jako szablon w celu ponownego użycia. Można także łatwo przełączyć się między projektowaniem okna dialogowego a edycją kodu, który go implementuje.

Jest również możliwe edytowanie właściwości jednego lub wielu formantów w **Edytor okien dialogowych**. Możesz zmienić kolejność tabulacji, czyli kolejność, w której formanty uzyskują Skoncentruj się kiedy **kartę** naciśnięcia klawisza lub można zdefiniować klawisz dostępu lub kombinacji klawiszy, który pozwala użytkownikom na wybór formantu przy użyciu klawiatury.

**Edytor okien dialogowych** pozwala również na używanie niestandardowych formantów, w tym formantów ActiveX. Można również edytować [widok formularza](../mfc/reference/cformview-class.md), [rejestrowania widoków](../data/record-views-mfc-data-access.md), lub [paski dialogowe](../mfc/dialog-bars.md).

Począwszy od programu Visual Studio 2015, można użyć **Edytor okien dialogowych** do definiowania dynamicznych układy, które określają, jak przenieść kontrolek i zmienianie rozmiarów, gdy użytkownik zmienia rozmiar okna dialogowego. Aby uzyskać więcej informacji, zobacz [układ dynamiczny](../mfc/dynamic-layout.md).

Aby uzyskać więcej informacji na temat zasobów, zobacz instrukcje [okno dialogowe Tworzenie](../windows/creating-a-new-dialog-box.md) i [formantów okna dialogowego](../windows/controls-in-dialog-boxes.md).

> [!TIP]
> Podczas korzystania z **Edytor okien dialogowych**, w wielu przypadkach można wybrać z prawego przycisku myszy wyświetli menu skrótów z najczęściej używanymi poleceniami.

## <a name="dialog-editor-toolbar"></a>Pasek narzędzi edytora okien dialogowych

**Edytor okien dialogowych** narzędzi zawiera przyciski rozmieszczanie układu kontrolek w oknie dialogowym, na przykład rozmiar i wyrównanie. **Edytor okien dialogowych** przycisków paska narzędzi odpowiadają poleceń na **Format** menu.

|Ikona|Znaczenie|Ikona|Znaczenie|
|----------|-------------|----------|-------------|
|![Przycisk okna dialogowego test](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|Okno dialogowe testu|![Miejsce na przycisku](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|Między|
|![Przycisk wej wyrównania](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|Wyrównaj wej|![Przycisk miejsce w dół](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|W dół|
|![Przycisk praw wyrównania](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|Wyrównaj prawa|![Przycisk tej samej szerokości upewnij](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|Taka sama szerokość|
|![Wyrównaj górne krawędzie przycisk](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|Wyrównaj górne krawędzie|![Marka sama wysokość przycisku](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|Taka sama wysokość|
|![Wyrównaj do dołu przycisk](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|Wyrównaj do dołu|![Utwórz ten sam rozmiar przycisku](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|Taki sam rozmiar|
|![Center Vertical button](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|W pionie|![Przełącz przycisk siatki](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|Przełączanie siatki|
|![Środkowy przycisk poziomy](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|Poziome|![Przełącz prowadnice przycisk](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|Przełącz prowadnice|

- Aby pokazać lub ukryć **Edytor okien dialogowych** narzędzi, przejdź do menu **widoku** > **pasków narzędzi** > **Edytor okien dialogowych**.

Po otwarciu **Edytor okien dialogowych** w projekcie w języku C++ **Edytor okien dialogowych** pasek narzędzi pojawia się automatycznie w górnej części rozwiązania, jednak jeśli pasek narzędzi jest jawnie zamknięty, należy wywołać go Gdy następnym razem otworzysz **Edytor okien dialogowych**. Można przełączać wyświetlanie, wybierając je z listy dostępnych pasków narzędzi i okien.

## <a name="switch-between-dialog-box-controls-and-code"></a>Przełączanie między kontrolkami okna dialogowego i kodem

W aplikacjach MFC można kliknąć dwukrotnie na formantów okna dialogowego, aby przejść do swój kod procedury obsługi lub szybko utworzyć szkieletu funkcje obsługi.

Dzięki nim wybrany jakiś formant, wybierz **ControlEvents** przycisk lub **wiadomości** znajdujący się w [okno właściwości](/visualstudio/ide/reference/properties-window) Aby wyświetlić pełną listę Windows komunikaty i zdarzenia dostępne dla wybranego elementu. Wybierz z listy, aby utworzyć lub edytować funkcje programu obsługi.

- Aby przejść do kodu z **Edytor okien dialogowych**, kliknij dwukrotnie ikonę kontrolki w oknie dialogowym, aby przejść do deklaracji pod kątem komunikat ostatnio zaimplementowano funkcji obsługi.

   Dla oparty na bibliotece ATL klasy okien dialogowych możesz zawsze przejść do definicji konstruktora.

- Aby wyświetlić zdarzenia dla kontrolki z wybraniu formantu wybierz **ControlEvents** znajdujący się w **właściwości** okna.

   Gdy jeden formant ma fokus w oknie dialogowym, można kliknąć prawym przyciskiem myszy i wybrać **dodać program obsługi zdarzeń**. Dzięki temu można określić klasę, do którego jest dodawany program obsługi. Aby uzyskać więcej informacji, zobacz [Dodawanie obsługi zdarzeń](../ide/adding-an-event-handler-visual-cpp.md).

   > [!NOTE]
   > Wybieranie **ControlEvents** przycisku, gdy okno dialogowe ma fokus przedstawia listę wszystkich kontrolek w oknie dialogowym, które można następnie rozszerzyć do zdarzeń dla poszczególnych formantów edycji.

- Aby wyświetlić wiadomości dla okna dialogowego za pomocą okna dialogowego z wybraniu wybierz **wiadomości** znajdujący się w **właściwości** okna.

## <a name="accelerator-keys"></a>Klawisze skrótów

Poniżej przedstawiono domyślną klawiszy skrótów dla **Edytor okien dialogowych** poleceń.  

|Polecenie|klucze|Opis|
|-------------|----------|-----------------|
|Format.AlignBottoms|**CTRL** + **Shift** + **strzałkę w dół**|Wyrównuje dolną krawędzią zaznaczonych formantów z formantu dominującego.|
|Format.AlignCenters|**Shift** + **F9**|Wyrównuje centra pionowe zaznaczonych formantów z formantu dominującego.|
|Format.AlignLefts|**CTRL** + **Shift** + **Strzałka w lewo**|Wyrównuje lewe krawędzie zaznaczonych formantów z formantu dominującego.|
|Format.AlignMiddles|**F9**|Wyrównuje Centra poziome z wybranych kontrolek za pomocą formantu dominującego.|
|Format.AlignRights|**CTRL** + **Shift** + **Strzałka w prawo**|Wyrównuje prawe krawędzie zaznaczonych formantów z formantu dominującego.|
|Format.AlignTops|**CTRL** + **Shift** + **Strzałka w górę**|Wyrównuje górne krawędzie zaznaczonych formantów z formantu dominującego.|
|Format.ButtonBottom|**Ctrl** + **B**|Powoduje umieszczenie wybranego przyciski wzdłuż dolnej środek okno dialogowe.|
|Format.ButtonRight|**Ctrl** + **R**|Przełącza wybranego przycisków w prawym górnym rogu okna dialogowego.|
|Format.CenterHorizontal|**Ctrl** + **Shift** + **F9**|Centra kontrolki w poziomie w oknie dialogowym.|
|Format.CenterVertical|**CTRL** + **F9**|Centra kontrolki w pionie w oknie dialogowym.|
|Format.CheckMnemonics|**Ctrl** + **M**|Sprawdza unikatowość klawiszy skrótu.|
|Format.SizeToContent|**SHIFT** + **F7**|Zmienia rozmiar wybranych kontrolkach w celu dopasowania do tekstu transkrypcji.|
|Format.SpaceAcross|**ALT** + **Strzałka w lewo**|Równomiernie spacje wybranych kontrolek w poziomie.|
|Format.SpaceDown|**ALT** + **strzałkę w dół**|Równomierne rozmieszczenie w pionie wybrane formanty.|
|Format.TabOrder|**Ctrl** + **D**|Ustawia kolejność formantów w oknie dialogowym.|
|Format.TestDialog|**CTRL** + **T**|Uruchamia okno dialogowe, aby przetestować wygląd i zachowanie.|
|Format.ToggleGuides|**Ctrl** + **G**|Przełączanie między nie siatki, wskazówek i siatki do okna dialogowego edycji.|

- Aby zmienić klawisze skrótów, przejdź do menu **narzędzia** > **opcje**i wybierz polecenie **klawiatury** w obszarze **środowiska** folderu.

   Aby uzyskać więcej informacji, zobacz [określenie i dostosowywanie skrótów klawiaturowych](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

- Aby zmienić swoje ustawienia, przejdź do menu **narzędzia** > **Import i eksport ustawień**.

   Dostępne opcje w oknach dialogowych i nazwy i lokalizacje poleceń menu, zostanie wyświetlony, mogą się różnić od opisanych w **pomocy** w zależności od ustawień aktywnych lub wersji.  Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Edytory zasobów](../windows/resource-editors.md)<br/>
[Instrukcje: Tworzenie okna dialogowego](../windows/creating-a-new-dialog-box.md)<br/>
[Kontrolki okna dialogowego](../windows/controls-in-dialog-boxes.md)<br/>
<!--
[Controls](../mfc/controls-mfc.md)<br/>
[Control Classes](../mfc/control-classes.md)<br/>
[Dialog Box Classes](../mfc/dialog-box-classes.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)-->