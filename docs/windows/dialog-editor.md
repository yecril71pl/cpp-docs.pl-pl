---
title: Edytor okien dialogowych (C++)
ms.date: 11/04/2016
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
ms.openlocfilehash: 827a7610aa919d5349313346ac0bfa80bd0647b0
ms.sourcegitcommit: eb2b34a24e6edafb727e87b138499fa8945f981e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56264897"
---
# <a name="dialog-editor-c"></a>Edytor okien dialogowych (C++)

**Okna dialogowego** Edytor umożliwia tworzenie i edytowanie zasobów okien dialogowych. Otwórz Edytor okien dialogowych przez dwukrotne kliknięcie pliku .rc okna dialogowego w **widok zasobów** okna (**widoku** > **widok zasobów**). Należy pamiętać, że **widok zasobów** nie jest dostępny w wersji Express.

Jednym z pierwszych kroków w tworzeniu nowego okna dialogowego (lub szablonu okna dialogowego) jest dodanie formantów do okna dialogowego. W **okna dialogowego** edytora, można rozmieścić formanty w celu dopasowania niektórych rozmiaru, kształtu lub wyrównania lub przenosić je około do pracy w oknie dialogowym. W łatwy sposób można również usunąć formant.

Okno dialogowe można przechowywać jako szablon w celu ponownego użycia. Można także łatwo przełączyć się między projektowaniem okna dialogowego a edycją kodu, który go implementuje.

Jest również możliwe edytowanie właściwości jednego lub wielu formantów w edytorze okien dialogowych. Możesz zmienić kolejność tabulacji, czyli kolejność, w której formanty uzyskują Skoncentruj się kiedy **kartę** naciśnięcia klawisza lub zdefiniować klawisza dostępu (kombinację klawiszy), który umożliwia użytkownikom na wybór formantu przy użyciu klawiatury. Aby uzyskać listę predefiniowanych klawiszy dostępu, zobacz [klucze akceleratora dla edytora okien dialogowych](../windows/accelerator-keys-for-the-dialog-editor.md).

**Okna dialogowego** Edytor umożliwia także używanie niestandardowych formantów, w tym formantów ActiveX. Ponadto można edytować [widok formularza](../mfc/reference/cformview-class.md), [widoków rekordów](../data/record-views-mfc-data-access.md), lub [paski dialogowe](../mfc/dialog-bars.md).

Począwszy od programu Visual Studio 2015, służy Edytor okien dialogowych do definiowania dynamicznych układy, które określają, jak formanty, przenoszenie i zmienianie rozmiaru, gdy użytkownik zmienia rozmiar okna dialogowego. Aby uzyskać więcej informacji, zobacz [układ dynamiczny](../mfc/dynamic-layout.md).

- [Tworzenie nowego okna dialogowego](../windows/creating-a-new-dialog-box.md)

- [Tworzenie okna dialogowego, którego nie można zamknąć w czasie wykonywania](../windows/creating-a-dialog-box-that-users-cannot-exit.md)

- [Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)

- [Dodawanie obsługi zdarzeń dla kontrolek okna dialogowego](../windows/adding-event-handlers-for-dialog-box-controls.md)

- [Testowanie okna dialogowego](../windows/testing-a-dialog-box.md)

- [Rozwiązywanie problemów z Edytorem okien dialogowych](../windows/troubleshooting-the-dialog-editor.md)

   > [!TIP]
   > Podczas korzystania z **okna dialogowego** edytora w wielu przypadkach, kliknięcie prawym przyciskiem myszy wyświetli menu skrótów z najczęściej używanymi poleceniami.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="dialog-editor-toolbar"></a>Pasek narzędzi edytora okien dialogowych

Po otwarciu **okna dialogowego** edytora w projekcie w języku C++ **Edytor okien dialogowych** pasek narzędzi pojawia się automatycznie w górnej części rozwiązania.

|Ikona|Znaczenie|Ikona|Znaczenie|
|----------|-------------|----------|-------------|
|![Przycisk okna dialogowego test](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|Okno dialogowe testu|![Miejsce na przycisku](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|Między|
|![Przycisk wej wyrównania](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|Wyrównaj wej|![Przycisk miejsce w dół](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|W dół|
|![Przycisk praw wyrównania](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|Wyrównaj prawa|![Przycisk tej samej szerokości upewnij](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|Taka sama szerokość|
|![Wyrównaj górne krawędzie przycisk](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|Wyrównaj górne krawędzie|![Marka sama wysokość przycisku](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|Taka sama wysokość|
|![Wyrównaj do dołu przycisk](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|Wyrównaj do dołu|![Utwórz ten sam rozmiar przycisku](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|Taki sam rozmiar|
|![Center Vertical button](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|W pionie|![Przełącz przycisk siatki](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|Przełączanie siatki|
|![Środkowy przycisk poziomy](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|Poziome|![Przełącz prowadnice przycisk](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|Przełącz prowadnice|

**Edytor okien dialogowych** narzędzi zawiera przyciski rozmieszczanie układu kontrolek w oknie dialogowym, na przykład rozmiar i wyrównanie. **Edytor okien dialogowych** przycisków paska narzędzi odpowiadają poleceń na **Format** menu.

Podczas pracy w **okna dialogowego** edytora, można przełączać wyświetlanie **Edytor okien dialogowych** narzędzi, wybierając je z listy dostępnych pasków narzędzi i okien.

- Aby pokazać lub ukryć pasek narzędzi edytora okna dialogowego na **widoku** menu, wybierz opcję **pasków narzędzi**, następnie wybierz **Edytor okien dialogowych** z podmenu.

   > [!NOTE]
   > **Edytor okien dialogowych** pasek narzędzi jest wyświetlany domyślnie po otwarciu okna dialogowego pole zasobu w edytorze okien dialogowych; jednak jeśli pasek narzędzi jest jawnie zamknięty, należy wywołać ją przy następnym otwarciu zasobów okno dialogowe.

## <a name="switch-between-dialog-box-controls-and-code"></a>Przełączanie między kontrolkami okna dialogowego i kodem

W aplikacjach MFC można kliknąć dwukrotnie na formantów okna dialogowego, aby przejść do swój kod procedury obsługi lub szybko utworzyć szkieletu funkcje obsługi.

Dzięki nim wybrany jakiś formant, kliknij przycisk **ControlEvents** przycisk lub **wiadomości** znajdujący się w [okno właściwości](/visualstudio/ide/reference/properties-window) Aby wyświetlić pełną listę Windows komunikaty i zdarzenia dostępne dla wybranego elementu. Wybierz z listy, aby utworzyć lub edytować funkcje programu obsługi.

- Aby przejść do kodu z edytora okien dialogowych, kliknij dwukrotnie formantu w oknie dialogowym, aby przejść do deklaracji pod kątem komunikat ostatnio zaimplementowano funkcji obsługi. (Dla oparty na bibliotece ATL klasy okien dialogowych, możesz zawsze przejść do definicji konstruktora.)

- Aby wyświetlić zdarzenia dla kontrolki z wybraniu formantu wybierz **ControlEvents** znajdujący się w [okno właściwości](/visualstudio/ide/reference/properties-window).

   > [!NOTE]
   > Wybieranie **ControlEvents** przycisk, kiedy *okno dialogowe* ma fokus udostępnia listę wszystkich kontrolek w oknie dialogowym, które można następnie rozszerzyć do zdarzeń dla poszczególnych formantów edycji.

   Gdy jeden formant ma fokus w oknie dialogowym, można go prawym przyciskiem myszy i wybrać **dodać program obsługi zdarzeń** z menu skrótów. Dzięki temu można określić klasę, do którego jest dodawany program obsługi. Aby uzyskać więcej informacji, zobacz [Dodawanie obsługi zdarzeń](../ide/adding-an-event-handler-visual-cpp.md).

- Aby wyświetlić wiadomości dla okna dialogowego za pomocą okna dialogowego z wybraniu wybierz **wiadomości** znajdujący się w [okno właściwości](/visualstudio/ide/reference/properties-window).

## <a name="accelerator-keys"></a>Klawisze skrótów

Poniżej przedstawiono domyślną klawiszy skrótów dla poleceń edytora okna dialogowego. Aby zmienić klawisze skrótów, wybierz **opcje** na **narzędzia** menu, wybierz **klawiatury** w obszarze **środowiska** folderu. Aby uzyskać więcej informacji, zobacz [określenie i dostosowywanie skrótów klawiaturowych](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

> [!NOTE]
> Dostępne opcje w oknach dialogowych i nazwy i lokalizacje poleceń menu, który zostanie wyświetlony, mogą różnić się od opisanych w pomocy, w zależności od ustawień aktywnych lub wersji. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

|Polecenie|klucze|Opis|
|-------------|----------|-----------------|
|Format.AlignBottoms|**CTRL** + **Shift** + **strzałkę w dół**|Wyrównuje dolną krawędzią z wybranych kontrolek z kontrolki dominującej|
|Format.AlignCenters|**Shift** + **F9**|Wyrównuje centra pionowe z wybranych kontrolek z kontrolki dominującej|
|Format.AlignLefts|**CTRL** + **Shift** + **Strzałka w lewo**|Wyrównuje lewe krawędzie wybranych kontrolek z kontrolki dominującej|
|Format.AlignMiddles|**F9**|Wyrównuje Centra poziome z wybranych kontrolek z kontrolki dominującej|
|Format.AlignRights|**CTRL** + **Shift** + **Strzałka w prawo**|Wyrównuje prawe krawędzie wybranych kontrolek z kontrolki dominującej|
|Format.AlignTops|**CTRL** + **Shift** + **Strzałka w górę**|Wyrównuje górne krawędzie wybranych kontrolek z kontrolki dominującej|
|Format.ButtonBottom|**Ctrl** + **B**|Umieszcza wybranego przyciski wzdłuż dolnej środek okno dialogowe|
|Format.ButtonRight|**Ctrl** + **R**|Umieszcza wybranego przycisków w prawym górnym rogu okna dialogowego|
|Format.CenterHorizontal|**Ctrl** + **Shift** + **F9**|Centra kontrolki w poziomie w oknie dialogowym|
|Format.CenterVertical|**CTRL** + **F9**|Centra kontrolki w pionie w oknie dialogowym|
|Format.CheckMnemonics|**Ctrl** + **M**|Sprawdzanie unikatowości klawiszy skrótu|
|Format.SizeToContent|**SHIFT** + **F7**|Zmienia rozmiar wybranych kontrolkach w celu dopasowania do tekstu transkrypcji|
|Format.SpaceAcross|**ALT** + **Strzałka w lewo**|Równomiernie poziomo spacje wybranych kontrolek|
|Format.SpaceDown|**ALT** + **strzałkę w dół**|Równomierne rozmieszczenie w pionie wybranych kontrolek|
|Format.TabOrder|**Ctrl** + **D**|Ustawia kolejność formantów w oknie dialogowym|
|Format.TestDialog|**CTRL** + **T**|Uruchamia okno dialogowe, aby przetestować wygląd i zachowanie|
|Format.ToggleGuides|**Ctrl** + **G**|Przełączanie między nie siatki, wskazówek i siatki do okna dialogowego edycji|

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Edytory zasobów](../windows/resource-editors.md)<br/>
[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
[Instrukcje: tworzenie zasobu](../windows/how-to-create-a-resource.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)<br/>
[Klasy kontrolek](../mfc/control-classes.md)<br/>
[Klasy okien dialogowych](../mfc/dialog-box-classes.md)<br/>
[Kontrolki okna dialogowego i typy zmiennych](../ide/dialog-box-controls-and-variable-types.md)