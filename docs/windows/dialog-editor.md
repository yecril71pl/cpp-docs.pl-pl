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
ms.openlocfilehash: f1544d3a8e14f9373e21b77d888860d24ab1ed6a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370294"
---
# <a name="dialog-editor-c"></a>Edytor okien dialogowych (C++)

**Edytor okien dialogowych** umożliwia tworzenie lub edytowanie zasobów okna dialogowego.

- Aby otworzyć edytor, kliknij dwukrotnie plik rc okna dialogowego w oknie **Widok zasobów** lub przejdź do menu **Wyświetl** > inny**widok zasobów**systemu**Windows** > .

Jednym z pierwszych kroków tworzenia nowego okna dialogowego lub szablonu okna dialogowego jest dodawanie formantów. W **Edytorze okien dialogowych**można rozmieścić formanty, aby pasowały do określonego rozmiaru, kształtu lub wyrównania, lub można je przenosić, aby pracować w oknie dialogowym. W łatwy sposób można również usunąć formant.

Okno dialogowe można przechowywać jako szablon w celu ponownego użycia. Można także łatwo przełączyć się między projektowaniem okna dialogowego a edycją kodu, który go implementuje.

Istnieje również możliwość edytowania właściwości pojedynczych lub wielu formantów w **Edytorze dialogów**. Można zmienić kolejność tabulacji, czyli kolejność, w jakiej formanty zyskują fokus po **naciśnięciu klawisza Tab,** lub można zdefiniować kombinację klawiszy dostępu lub klawiszy, która umożliwia użytkownikom wybranie formantu za pomocą klawiatury.

**Edytor dialogów** umożliwia również używanie formantów niestandardowych, w tym formantów ActiveX. Można również edytować [widok formularza,](../mfc/reference/cformview-class.md) [widoki nagrywania](../data/record-views-mfc-data-access.md)lub [paski dialogowe](../mfc/dialog-bars.md).

Począwszy od programu Visual Studio 2015, można użyć **Edytora okien dialogowych** do definiowania układów dynamicznych, które określają, jak formanty przenieść i zmienić rozmiar, gdy użytkownik zmienić rozmiar okna dialogowego. Aby uzyskać więcej informacji, zobacz [Układ dynamiczny](../mfc/dynamic-layout.md).

Aby uzyskać więcej informacji na temat zasobów, zobacz jak [utworzyć okno dialogowe](../windows/creating-a-new-dialog-box.md) i [formanty okna dialogowego](../windows/controls-in-dialog-boxes.md).

> [!TIP]
> Podczas korzystania z **Edytora dialogów**w wielu przypadkach można wybrać prawym przyciskiem myszy, aby wyświetlić menu skrótów często używanych poleceń.

## <a name="dialog-editor-toolbar"></a>Pasek narzędzi Edytor okien dialogowych

Pasek narzędzi **Edytor okien dialogowych** zawiera przyciski służące do rozmieszczania układu formantów w oknie dialogowym, na przykład rozmiaru i wyrównania. Przyciski paska narzędzi **Edytora okien** odpowiadają poleceńom w menu **Format.**

|Ikona|Znaczenie|Ikona|Znaczenie|
|----------|-------------|----------|-------------|
|![Przycisk Okno dialogowe testu](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|Okno dialogowe testu|![Przycisk Spacja w poprzek](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|W poprzek|
|![Przycisk Wyrównaj do lewej](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignUłe")|Wyrównaj do lewej|![Przycisk Spacja w dół](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|W dół|
|![Przycisk Wyrównaj prawa](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|Wyrównaj prawa|![Przycisk Zrób tę samą szerokość](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|Zrób tę samą szerokość|
|![Przycisk Wyrównaj wierzchołki](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|Wyrównaj wierzchołki|![Przycisk Zrób tę samą wysokość](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|Zrób tę samą wysokość|
|![Przycisk Wyrównaj dolne](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|Wyrównaj dolne|![Przycisk Zrób ten sam rozmiar](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|Zrób ten sam rozmiar|
|![Przycisk Wyśrodkuj pionową](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorWertyk")|Pionowa|![Przycisk Przełącz siatkę](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|Przełączanie siatki|
|![Przycisk Wyśrodkuj poziome](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|Pozioma|![Przycisk Przełącz linie pomocnicze](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuty")|Przełączanie prowadnic|

- Aby wyświetlić lub ukryć pasek narzędzi **Edytor okien dialogowych,** przejdź do menu **Widok** > **pasków narzędzi** > **Edytora dialogów**.

Po **otwarciu Edytora okien dialogowych** w projekcie języka C++ pasek narzędzi **Edytor dialogów** automatycznie pojawia się u góry rozwiązania, jednak jeśli jawnie zamkniesz pasek narzędzi, musisz wywołać go przy następnym otwarciu **Edytora okien dialogowych**. Można przełączyć jego wyświetlanie, wybierając go z listy dostępnych pasków narzędzi i okien.

## <a name="switch-between-dialog-box-controls-and-code"></a>Przełączanie między formantami okna dialogowego a kodem

W aplikacjach MFC można dwukrotnie kliknąć formanty okna dialogowego, aby przejść do ich kodu obsługi lub szybko utworzyć funkcje programu obsługi skrótowej.

Po wybraniu formantu wybierz przycisk **ControlEvents** lub przycisk **Wiadomości** w [oknie Właściwości,](/visualstudio/ide/reference/properties-window) aby wyświetlić pełną listę wiadomości i zdarzeń systemu Windows dostępnych dla wybranego elementu. Wybierz z listy, aby utworzyć lub edytować funkcje obsługi.

- Aby przejść do kodu z **Edytora okien dialogowych,** kliknij dwukrotnie formant w oknie dialogowym, aby przejść do deklaracji dla ostatnio zaimplementowanej funkcji obsługi wiadomości.

   Dla klas dialogowych opartych na atl zawsze przejść do definicji konstruktora.

- Aby wyświetlić zdarzenia dla formantu, z zaznaczonym formantem, wybierz przycisk **ControlEvents** w oknie **Właściwości.**

   Gdy pojedynczy formant ma fokus w oknie dialogowym, można kliknąć prawym przyciskiem myszy i wybrać polecenie **Dodaj program obsługi zdarzeń**. Dzięki temu można określić klasę, do której jest dodawany program obsługi. Aby uzyskać więcej informacji, zobacz [Dodawanie programu obsługi zdarzeń](../ide/adding-an-event-handler-visual-cpp.md).

   > [!NOTE]
   > Wybranie przycisku **ControlEvents,** gdy okno dialogowe ma fokus, udostępnia listę wszystkich formantów w oknie dialogowym, które można następnie rozwinąć, aby edytować zdarzenia dla poszczególnych formantów.

- Aby wyświetlić wiadomości dla okna dialogowego, z zaznaczonym oknem dialogowym wybierz przycisk **Wiadomości** w oknie **Właściwości.**

## <a name="accelerator-keys"></a>Klawisze skrótów

Poniżej znajdują się domyślne klawisze akceleratora dla poleceń **Edytora okien.**  

|Polecenie|Klucze|Opis|
|-------------|----------|-----------------|
|Format.AlignBottoms|**Ctrl** + **Strzałka** z przesunięciem w dół**ctrl** + |Wyrównuje dolne krawędzie wybranych formantów z formantem dominującym.|
|Format.AlignCenters|**Przesunięcie** + **F9**|Wyrównuje pionowe środki wybranych formantów z formantem dominującym.|
|Format.AlignLefts|**Ctrl** + **Strzałka** w lewo**z przesunięciem ctrl** + |Wyrównuje lewe krawędzie wybranych formantów z formantem dominującym.|
|Format.AlignMiddles|**F9**|Wyrównuje poziome środki wybranych formantów z formantem dominującym.|
|Format.AlignRights|**Ctrl** + **Strzałka** w prawo**z przesunięciem ctrl** + |Wyrównuje prawe krawędzie wybranych formantów z kontrolką dominującą.|
|Format.AlignTops|**Ctrl** + **Strzałka** z przesunięciem w górę**ctrl** + |Wyrównuje górne krawędzie wybranych formantów z kontrolką dominującą.|
|Format.ButtonBottom|**Ctrl** + **B**|Umieszcza wybrane przyciski wzdłuż dolnej części okna dialogowego.|
|Format.ButtonRight|**Ctrl** + **R**|Umieszcza wybrane przyciski w prawym górnym rogu okna dialogowego.|
|Format.CenterHorizontal|**Ctrl** + **Shift**Przesunięcie + ctrl**F9**|Wyśrodkowuje formanty poziomo w oknie dialogowym.|
|Format.CenterVertical|**Ctrl** + **F9**|Wyśrodkowuje formanty w pionie w oknie dialogowym.|
|Format.CheckMnemonics|**Ctrl** + **M**|Sprawdza wyjątkowość mnemonics.|
|Format.SizeToContent|**Przesunięcie** + **F7**|Rozmiary zaznaczonych formantów są odpowiednie do tekstu podpisu.|
|Format.SpaceAcross|**Alt** + **strzałka w lewo**|Równomiernie rozmieszczane formanty w poziomie.|
|Format.SpaceDown|**Alt** + **Strzałka w dół**|Równomiernie rozmieszczane formanty w pionie.|
|Format.TabOrder|**Ctrl** + **D**|Ustawia kolejność formantów w oknie dialogowym.|
|Format.TestDialog|**Ctrl** + **T (ctrl t)**|Uruchamia okno dialogowe, aby przetestować wygląd i zachowanie.|
|Format.ToggleGuides|**Ctrl** + **G**|Cykle między siatką, wytycznymi i siatką do edycji dialogów dialogowych.|

- Aby zmienić klawisze skrótów, przejdź do menu**Opcje** **narzędzi** > i wybierz **pozycję Klawiatura** w folderze **Środowisko.**

   Aby uzyskać więcej informacji, zobacz [Identyfikowanie i dostosowywanie skrótów klawiaturowych](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

- Aby zmienić ustawienia, przejdź do menu Narzędzia > **Importuj i eksportuj ustawienia**. **Tools**

   Opcje dostępne w oknach dialogowych oraz nazwy i lokalizacje wyświetlonych poleceń menu mogą różnić się od opisanych w **Pomocy** w zależności od aktywnych ustawień lub wersji.  Aby uzyskać więcej informacji, zobacz [Personalizowanie ide programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytory zasobów](../windows/resource-editors.md)<br/>
[Jak: Tworzenie okna dialogowego](../windows/creating-a-new-dialog-box.md)<br/>
[Kontrolki okna dialogowego](../windows/controls-in-dialog-boxes.md)<br/>
<!--
[Controls](../mfc/controls-mfc.md)<br/>
[Control Classes](../mfc/control-classes.md)<br/>
[Dialog Box Classes](../mfc/dialog-box-classes.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)-->
