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
ms.openlocfilehash: 9d0f9993d81c499f67a08e5401c5e56dba7b281c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215257"
---
# <a name="dialog-editor-c"></a>Edytor okien dialogowych (C++)

**Edytor okien** dialogowych umożliwia tworzenie i edytowanie zasobów okien dialogowych.

- Aby otworzyć Edytor, kliknij dwukrotnie plik. RC okna dialogowego w oknie **Widok zasobów** lub przejdź do **widoku** menu > **innych** > **Widok zasobów**.

Jednym z pierwszych kroków w tworzeniu nowego okna dialogowego lub szablonu okna dialogowego jest dodawanie kontrolek. W **edytorze okien dialogowych**można rozmieścić kontrolki tak, aby mieściły się w określonym rozmiarze, kształcie lub wyrównaniu, albo przenieść je do pracy w oknie dialogowym. W łatwy sposób można również usunąć formant.

Okno dialogowe można przechowywać jako szablon w celu ponownego użycia. Można także łatwo przełączyć się między projektowaniem okna dialogowego a edycją kodu, który go implementuje.

Istnieje również możliwość edytowania właściwości jednego lub wielu kontrolek w **edytorze okien dialogowych**. Można zmienić kolejność tabulacji, czyli kolejność, w której formanty uzyskują fokus po naciśnięciu klawisza **Tab** , lub można zdefiniować klawisz dostępu lub kombinację klawiszy, która umożliwia użytkownikom wybranie kontrolki przy użyciu klawiatury.

**Edytor okien dialogowych** umożliwia również korzystanie z kontrolek niestandardowych, w tym kontrolek ActiveX. Możesz również edytować [Widok formularza](../mfc/reference/cformview-class.md), [widoki rekordów](../data/record-views-mfc-data-access.md)lub [paski okien dialogowych](../mfc/dialog-bars.md).

Począwszy od programu Visual Studio 2015, można użyć **edytora okien dialogowych** , aby zdefiniować układy dynamiczne, które określają sposób przenoszenia i zmiany rozmiaru kontrolek, gdy użytkownik zmienia rozmiar okna dialogowego. Aby uzyskać więcej informacji, zobacz [dynamiczny układ](../mfc/dynamic-layout.md).

Aby uzyskać więcej informacji o zasobach, zobacz jak [utworzyć okno dialogowe](../windows/creating-a-new-dialog-box.md) i [kontrolki okna dialogowego](../windows/controls-in-dialog-boxes.md).

> [!TIP]
> Korzystając z **edytora okien dialogowych**, w wielu przypadkach można wybrać przycisk z prawym przyciskiem myszy, aby wyświetlić menu skrótów często używanych poleceń.

## <a name="dialog-editor-toolbar"></a>Pasek narzędzi edytora okien dialogowych

Pasek narzędzi **edytora okien dialogowych** zawiera przyciski służące do organizowania układu kontrolek w oknie dialogowym, na przykład rozmiaru i wyrównania. Przyciski paska narzędzi **edytora okna dialogowego** są zgodne z poleceniami w menu **Format** .

|Ikona|Znaczenie|Ikona|Znaczenie|
|----------|-------------|----------|-------------|
|![Przycisk okna dialogowego testu](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|Okno dialogowe testu|![Odstępy między przyciskami](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|Całą|
|![Przycisk wyrównany do lewej](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|Wyrównaj do lewej|![Przycisk odstępu w dół](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|W dół|
|![Przycisk Wyrównaj prawa](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|Wyrównaj prawa|![Przycisk Wyrównaj Szerokość](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|Wyrównaj Szerokość|
|![Przycisk Wyrównaj do góry](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|Wyrównaj do góry|![Przycisk Wyrównaj wysokość](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|Wyrównaj wysokość|
|![Przycisk Wyrównaj do dołu](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|Wyrównaj do dołu|![Przycisk Utwórz ten sam rozmiar](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|Wyrównaj rozmiar|
|![Przycisk Wyśrodkuj w pionie](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|Pionow|![Przycisk przełączania siatki](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|Przełączanie siatki|
|![Przycisk Wyśrodkuj w poziomie](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|Układ|![Przycisk przełączania prowadnic](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|Przełącz prowadnice|

- Aby pokazać lub ukryć pasek narzędzi **edytora okien dialogowych** , przejdź do **widoku** menu, > **paski narzędzi** > **edytorze okien dialogowych**.

Po otwarciu **edytora okien dialogowych** w C++ projekcie pasek narzędzi **edytora okien dialogowych** automatycznie pojawia się u góry rozwiązania, jednak jeśli jawnie zamknięto ten pasek narzędzi, należy wywołać go przy następnym otwarciu **edytora okien dialogowych**. Możesz przełączać jej wyświetlanie, wybierając ją z listy dostępnych pasków narzędzi i okien.

## <a name="switch-between-dialog-box-controls-and-code"></a>Przełączanie między kontrolkami okna dialogowego i kodem

W aplikacjach MFC można dwukrotnie kliknąć kontrolki okna dialogowego, aby przejść do kodu obsługi lub szybko utworzyć funkcje procedury obsługi.

Po wybraniu kontrolki wybierz przycisk **ControlEvents** lub przycisk **komunikaty** w [okno właściwości](/visualstudio/ide/reference/properties-window) , aby wyświetlić pełną listę komunikatów i zdarzeń systemu Windows dostępnych dla wybranego elementu. Wybierz z listy, aby utworzyć lub edytować funkcje obsługi.

- Aby przejść do kodu z **edytora okien dialogowych**, kliknij dwukrotnie formant w oknie dialogowym, aby przejść do deklaracji najbardziej ostatnio zaimplementowanej funkcji obsługi komunikatów.

   Dla klas okien dialogowych opartych na ATL, zawsze przeskakuje do definicji konstruktora.

- Aby wyświetlić zdarzenia dla kontrolki, z wybraną kontrolką, wybierz przycisk **ControlEvents** w oknie **Właściwości** .

   Gdy pojedynczy formant ma fokus w oknie dialogowym, możesz kliknąć prawym przyciskiem myszy i wybrać polecenie **Dodaj obsługę zdarzeń**. Pozwala to określić klasę, do której zostanie dodana procedura obsługi. Aby uzyskać więcej informacji, zobacz [Dodawanie programu obsługi zdarzeń](../ide/adding-an-event-handler-visual-cpp.md).

   > [!NOTE]
   > Wybranie przycisku **ControlEvents** , gdy okno dialogowe ma fokus, uwidacznia listę wszystkich kontrolek w oknie dialogowym, które następnie można rozwinąć, aby edytować zdarzenia dla poszczególnych kontrolek.

- Aby wyświetlić komunikaty dla okna dialogowego, z wybranym oknem dialogowym, w oknie **Właściwości** wybierz przycisk **komunikaty** .

## <a name="accelerator-keys"></a>Klawisze skrótów

Poniżej znajdują się domyślne klawisze skrótów dla poleceń **edytora okien dialogowych** .  

|Polecenie|Klucze|Opis|
|-------------|----------|-----------------|
|Format.AlignBottoms|**Ctrl** + **SHIFT** + **Strzałka w dół**|Wyrównuje dolne krawędzie zaznaczonych kontrolek z kontrolką dominującą.|
|Format.AlignCenters|**Shift** + **F9**|Wyrównuje Pionowe centra zaznaczonych kontrolek z kontrolką dominującą.|
|Format.AlignLefts|**Ctrl** + **SHIFT** + **Strzałka w lewo**|Wyrównuje Lewe krawędzie zaznaczonych kontrolek z kontrolką dominującą.|
|Format.AlignMiddles|**F9**|Wyrównuje poziome centra wybranych kontrolek z kontrolką dominującą.|
|Format.AlignRights|**Ctrl** + **SHIFT** + **Strzałka w prawo**|Wyrównuje prawej krawędzi zaznaczonych kontrolek z kontrolką dominującą.|
|Format.AlignTops|**Ctrl** + **SHIFT** + **Strzałka w górę**|Wyrównuje górne krawędzie zaznaczonych kontrolek z kontrolką dominującą.|
|Format.ButtonBottom|**Ctrl** + **B**|Umieszcza wybrane przyciski wzdłuż środka okna dialogowego.|
|Format.ButtonRight|**Ctrl** + **R**|Umieszcza wybrane przyciski w prawym górnym rogu okna dialogowego.|
|Format.CenterHorizontal|**Ctrl** + **SHIFT** + **F9**|Ustawia poziomy formantów w poziomie okna dialogowego.|
|Format.CenterVertical|**Ctrl** + **F9**|Ustawia kontrolki w pionie wewnątrz okna dialogowego.|
|Format.CheckMnemonics|**Ctrl** + **M**|Sprawdza unikatowość symboli.|
|Format. SizeToContent|**Shift** + **F7**|Zmienia rozmiar zaznaczonych kontrolek w celu dopasowania do tekstu podpisu.|
|Format.SpaceAcross|**Alt** + **Strzałka w lewo**|Równo zaznaczaj zaznaczone kontrolki w poziomie.|
|Format.SpaceDown|**Alt** + **strzałkę w dół**|Równo zaznaczaj zaznaczone kontrolki w pionie.|
|Format.TabOrder|**Ctrl** + **D**|Ustawia kolejność formantów w oknie dialogowym.|
|Format.TestDialog|**Ctrl** + **t**|Uruchamia okno dialogowe, aby przetestować wygląd i zachowanie.|
|Format.ToggleGuides|**Ctrl** + **G**|Przełączanie między nie siatką, wskazówkami i siatką w celu edytowania okna dialogowego.|

- Aby zmienić klawisze skrótów, przejdź do menu **Narzędzia** , > **Opcje**, a następnie wybierz pozycję **Klawiatura** w obszarze folder **środowiska** .

   Aby uzyskać więcej informacji, zobacz [Identyfikowanie i Dostosowywanie skrótów klawiaturowych](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

- Aby zmienić ustawienia, przejdź do menu **narzędzia** > **Importuj i Eksportuj ustawienia**.

   Opcje dostępne w oknach dialogowych oraz nazwy i lokalizacje poleceń menu, które są widoczne, mogą się różnić od tego, co opisano w **pomocy** , w zależności od ustawień aktywnych lub wydania.  Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytory zasobów](../windows/resource-editors.md)<br/>
[Instrukcje: Tworzenie okna dialogowego](../windows/creating-a-new-dialog-box.md)<br/>
[Kontrolki okna dialogowego](../windows/controls-in-dialog-boxes.md)<br/>
<!--
[Controls](../mfc/controls-mfc.md)<br/>
[Control Classes](../mfc/control-classes.md)<br/>
[Dialog Box Classes](../mfc/dialog-box-classes.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)-->
