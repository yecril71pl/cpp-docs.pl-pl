---
title: 'Instrukcje: Rozmieścić formanty (C++) | Dokumentacja firmy Microsoft'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.dialog.grouping
- vc.editors.dialog.combo
helpviewer_keywords:
- controls [C++], positioning
- dialog box controls [C++], placement
- Dialog Editor [C++], arranging controls
- Dialog Editor [C++], guides and margins
- guides, clearing
- guides
- dialog box controls [C++], placement
- controls [C++], guides and margins
- guides, creating
- guides, moving
- margins, moving
- DLUs (dialog units)
- controls [C++], aligning
- Dialog Editor [C++], snap to guides
- guides, tick mark interval
- dialog box controls [C++], placement
- guides, aligning controls
- dialog units (DLUs)
- snap to guides (Dialog editor)
- controls [C++], sizing
- tick mark interval in Dialog editor
- controls [C++], snap to guides/grid
- guides, disabling snapping
- controls [C++], snap to guides/grid
- controls [C++], layout grid
- snap to layout grid
- grids, turning on or off
- layout grid in Dialog Editor
- grids, changing size
- grid spacing
- guides, settings
- layout grid in Dialog Editor
- controls [C++], snap to guides/grid
- Guide Settings dialog box (Dialog editor)
- controls [C++], aligning
- controls [C++], positioning
- Space Evenly command
- dialog box controls [C++], placement
- Center in Dialog command
- Arrange Buttons command
- buttons, arranging push buttons in dialog boxes
- push buttons
- member variables, adding to radio button groups
- variables, dialog box control member variables
- dialog box controls [C++], grouping radio buttons
- grouping controls
- radio buttons [C++], grouping on dialog boxes
- controls [C++], tab order
- focus, tab order
- tab controls [C++], tab order
- Tabstop property for controls
- controls [C++], focus
- dialog box controls [C++], tab order
- Dialog Editor [C++], selecting controls
- dominant controls
- dialog box controls [C++], selecting in editor
- controls [C++], selecting
- size, controls
- controls [C++], dominant
- controls [C++], removing from groups
- Dialog Editor [C++], dominant control
- Size to Content command
- size, controls
- text, autosizing controls to fit text
- controls [C++], sizing
- Make Same Size command
- combo boxes, sizing
- list controls [C++], scroll bar width
- CListBox::SetHorizontalExtent
- controls [C++], scroll bar
- scroll bars [C++], displaying in controls
- horizontal scroll bar width
- CListBox class, scroll bar width
- scroll bars [C++], width
ms.assetid: 832491cf-98af-42e5-a854-2cb135fd45c6
ms.openlocfilehash: d9bd73c9cc81b113f222bbc090c62200c93554b2
ms.sourcegitcommit: 24592ba0a38c7c996ffd3d55fe1024231a59ccc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2019
ms.locfileid: "56336634"
---
# <a name="how-to-arrange-controls-c"></a>Instrukcje: Rozmieścić formanty (C++)

**Okna dialogowego** edytor oferuje narzędzia układu, wyrównanie, które automatycznie rozmiaru formantów. W przypadku większości zadań, można użyć [paska narzędzi edytora okien dialogowych](../windows/showing-or-hiding-the-dialog-editor-toolbar.md). Wszystkie **Edytor okien dialogowych** są również dostępne na pasku narzędzi, polecenia **Format** menu, a większość [klawiszy skrótów](../windows/accelerator-keys-for-the-dialog-editor.md).

Wiele poleceń układu dla okien dialogowych są dostępne tylko w przypadku wybrania więcej niż jeden formant. Można wybrać jeden lub wiele kontrolek, a po wybraniu więcej niż jeden formant pierwszej, którą wybierzesz jest domyślnie formant "dominujący". Więcej informacji o dobieraniu, formantów i formant dominujący, zobacz [formanty wybierając](../windows/selecting-controls.md).

Lokalizację, wysokość i szerokość bieżącego formantu są wyświetlane w prawym dolnym rogu paska stanu. Po wybraniu całe okno dialogowe pasek stanu przedstawia położenie okna dialogowego jako całości, a jego wysokość i szerokość.

## <a name="guides-and-grids"></a>Prowadnice i siatki

Można rozmieścić formanty w oknach dialogowych za pomocą **okna dialogowego** edytora w jednym z trzech różnych stanów:

- Prowadnice i marginesy w (ustawienie domyślne)

- Przy użyciu siatki układu w

- Bez żadnych funkcji przyciągania lub wyrównanie

[Paska narzędzi edytora okien dialogowych](../windows/showing-or-hiding-the-dialog-editor-toolbar.md) zawiera przyciski, które sterują stanu. Aby zmienić stan, wybierz odpowiednią ikonę. Możesz również zmienić stany przy użyciu **ustawienia prowadnic** polecenie **Format** menu.

**Ustawienia prowadnic** okno dialogowe ma następujące właściwości:

|Właściwość|Opis|
|---|---|
|**Układ prowadnic**|Wyświetla ustawienia prowadnic układu.|
|**Brak**|Ukrywa narzędzia układu.|
|**Linijki i prowadnice**|Po włączeniu narzędzia układ; dodaje linijki linie pomocnicze można umieścić w linijki. Przewodniki domyślne są marginesy, które można przenosić, przeciągając. Wybierz linijki umieścić przewodnik. Formanty "przyciągana" do przewodników po przeniesieniu kontroli nad lub obok nich. Formanty również przechodzić z przewodnikiem po są dołączone do niego. Formant jest dołączony do przewodnika po każdej stronie, gdy wskazówki są przenoszone, zmienia rozmiar kontrolki.|
|**Siatka**|Tworzy siatki układu. Nowe kontrolki automatycznie zostaną wyrównane do siatki.|
|**Odstępy między liniami siatki**|Wyświetla ustawienia odstępy między liniami siatki w jednostkach pola okna dialogowego (Dlu).|
|**Szerokość: Dlu**|Ustawia szerokość siatki układu w Dlu. Poziomy DLU jest średniej szerokości czcionki okno dialogowe podzielona przez cztery.|
|**Wysokość: Dlu**|Określa wysokość siatki układu w Dlu. DLU pionowe jest średnią wysokość czcionka pola okna dialogowego podzielić przez 8.|

### <a name="to-create-edit-and-delete-guides-and-margins"></a>Do tworzenia, edytowania i usuwania prowadnic i marginesów

Czy przenosisz się formantów, dodawanie formantów, rozmieszczanie bieżący układ, przewodniki może pomóc można wyrównać formanty dokładnie w oknie dialogowym. Przewodniki są wyświetlane jako niebieskie linie kropkowana w oknie dialogowym wyświetlany w edytorze i odpowiednie strzałki w linijki górnej i lewej strony **okna dialogowego** edytora.

Kiedy tworzysz okno dialogowe, znajdują się cztery marginesy. Marginesy są przewodniki zmodyfikowane, pojawiają się jako niebieskie linie dotted. Zobacz następujące akcje:

- Aby utworzyć linię w ramach linijkę, wybierz jeden raz utworzyć linię. (Jednym kliknięciem tworzy nowy przewodnik; dwukrotne kliknięcie powoduje uruchomienie **ustawienia prowadnic** okno dialogowe, w którym można określić ustawienia prowadnic.)

- Aby ustawić przewodnik, okno dialogowe, wybierz przewodnika i przeciągnij go do nowej pozycji. (Możesz również wybrać strzałkę na linijce przeciągnij skojarzonego przewodnika.) Współrzędne przewodnika są wyświetlane na pasku stanu w dolnej części okna i linijki. Przesuń wskaźnik nad strzałką znajdującą się w linijkę, aby wyświetlić dokładnego położenia przewodnika.

- Aby przenieść marginesy, przeciągnij margines do nowej pozycji. Aby margines zniknąć, należy przenieść margines do pozycji zero. Aby przywrócić margines, umieść wskaźnik na marginesie pozycji zero i przenieść margines w określonej pozycji.

- Aby usunąć wskazówki, przeciągnij ją z okna dialogowego lub przeciągnij strzałkę odpowiedniego z linijki.

### <a name="to-align-controls-on-a-guide"></a>Dopasowanie kontrolek do prowadnicy

Uchwyty zmiany rozmiaru kontrolek przyciąganie do prowadnic formanty są przenoszone, gdy przewodniki przyciąganie do kontrolek, formanty, nie jest przypięty wcześniej do przewodnika. Po przeniesieniu przewodnik również przenieść formantów, które są wyrównywane do niego. Formanty wyrównywane do więcej niż jeden podręcznik zmieniany jest rozmiar po przeniesieniu jeden z przewodników.

Znaczniki w linijki, określające odstępów przewodniki i formanty są definiowane przez jednostki okna dialogowego (Dlu). DLU opiera się na rozmiar czcionki okno dialogowe, zwykle 8-punktowy MS Shell Dlg. Poziomy DLU jest średniej szerokości czcionki okno dialogowe podzielona przez cztery. DLU pionowe jest średnią wysokość czcionki podzielić przez 8.

#### <a name="to-size-a-group-of-controls-with-guides"></a>Rozmiar grupy formantów z liniami

1. Przyciągaj obok kontrolki (lub formantów) do przewodnika.

1. Przeciągnij przewodnika po drugiej stronie kontrolki (lub kontrolki).

   Jeśli to konieczne z wieloma formantami, rozmiar każdego przyciągane do prowadnicy drugiego.

1. Przenieś albo przewodnika, aby rozmiar kontrolki (lub kontrolki).

#### <a name="to-change-the-intervals-of-the-tick-marks"></a>Aby zmienić interwałów znaczników

Z **Format** menu, wybierz **ustawienia prowadnic**, a następnie w obszarze **odstępy między liniami siatki** określ nową wysokość i szerokość w Dlu.

### <a name="to-disable-guides"></a>Aby wyłączyć prowadnice

Klawisze specjalne w połączeniu z myszy umożliwia wyłączanie przyciągania efekt prowadnice. Za pomocą **Alt** klucz wyłącza przyciągania skutki przewodnik wybrane. Przenoszenie Przewodnik z **Shift** klucz uniemożliwia przyciągniętą posuwał się z przewodnikiem.

- Aby wyłączyć przyciąganie efekt prowadnice, przeciągnij formant, przytrzymując naciśnięty **Alt** klucza.

- Aby przenieść przewodniki bez przenoszenia przyciągniętą, przeciągnij przewodnika, przytrzymując naciśnięty **Shift** klucza.

- Aby wyłączyć prowadnice, z **Format** menu, wybierz **ustawienia prowadnic**. Następnie w **ustawienia prowadnic** dialogowego **prowadnic układu**, wybierz opcję **Brak**.

   > [!NOTE]
   > Możesz także dwukrotnie kliknąć na pasku linijkę, aby uzyskać dostęp do **ustawienia prowadnic** okno dialogowe.

> [!TIP]
> Skrót, aby wyłączyć prowadnice znajduje się na **Format** menu, wybierz opcję **Przełącz prowadnice**.

### <a name="to-modify-the-layout-grid"></a>Aby zmodyfikować siatki układu

Podczas wprowadzania lub rozmieszczanie formantów w oknie dialogowym, można użyć siatki układu do bardziej precyzyjne pozycjonowania. Po włączeniu siatki "przyciągane do" linii kropkowanej siatki tak, jakby namagnesować pojawiają się formanty. Możesz włączyć tę funkcję "przyciągania do siatki" i wyłączyć i zmienianie rozmiaru komórek siatki układu.

- Włączenia siatki układu lub wyłączona, z **Format** menu, wybierz **ustawienia prowadnic**następnie zaznacz lub wyczyść **siatki** przycisku.

   Możesz nadal kontrolować siatki w poszczególnych **okna dialogowego** okna edytora za pomocą **Przełącz siatkę** znajdujący się na [paska narzędzi edytora okien dialogowych](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

- Aby zmienić rozmiar siatki układu z **Format** menu, wybierz **ustawienia prowadnic**, następnie wpisz wysokość i szerokość Dlu komórek w siatce. Minimalna wysokość lub szerokość jest Dlu 4.

## <a name="select-controls"></a>Zaznaczanie formantów

Zaznacz formanty do rozmiaru, wyrównanie, przenieść, skopiować, lub je usunąć, a następnie ukończ operację, którą chcesz. W większości przypadków należy wybrać więcej niż jeden formant na korzystanie z narzędzia określania rozmiaru i wyrównanie [paska narzędzi edytora okien dialogowych](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

Po wybraniu formantu, ma przyciemnione obramowanie wokół niej z niezawodnej (aktywny) lub pusty (nieaktywny) "uchwytów," małe kwadraty, są wyświetlane w krawędź zaznaczenia. Po wybraniu wielu formantów formantu dominującego ma uchwyty zmiany rozmiaru stałych i wszystkich innych wybranych kontrolek mają uchwyty zmiany rozmiaru pusty.

Podczas zmiany rozmiaru lub wyrównywanie formantów wielu **okna dialogowego** Edytor używa "formantu dominującego" Aby określić, jak rozmiar lub wyrównane do innych kontrolek. Domyślnie formant dominujący jest pierwszy formant wybrane.

### <a name="to-select-controls"></a>Aby wybrać formantów

1. W [okno przybornika](/visualstudio/ide/reference/toolbox), wybierz opcję **wskaźnik** narzędzia.

1. Można dokonać wyboru, użyj jednej z następujących czynności:

   - Przeciągnij wskaźnik, aby narysować pole zaznaczenia wokół formanty, które chcesz zaznaczyć w oknie dialogowym. Po zwolnieniu przycisku myszy kontroluje wszystkie wewnątrz i przecinające się są zaznaczone pola wyboru.

   - Naciśnij i przytrzymaj **Shift** klucza, a następnie wybierz kontrolki, czy chcesz uwzględnić w zaznaczeniu.

   - Naciśnij i przytrzymaj **Ctrl** klucza, a następnie wybierz kontrolki, czy chcesz uwzględnić w zaznaczeniu.

1. Aby dodać lub usunąć formant z grupy wybranych kontrolek, przytrzymaj wciśnięty **Shift** klucza, a następnie wybierz kontrolkę, aby dodać lub usunąć.

> [!NOTE]
> Przytrzymanie **Ctrl** klucza i wybierając polecenie Kontrolki wyboru spowoduje, że, które kontrolują formantu dominującego w ramach tego zaznaczenia.

### <a name="to-select-a-dominant-control"></a>Aby zaznaczyć formant dominujący

- Aby określić formant dominujący, przytrzymaj wciśnięty **Ctrl** klucza i wybierz formant, którego chcesz użyć do wywierania wpływu na rozmiar lub lokalizację innych formantów *pierwszy*.

- Formant dominujący, wyczyścić bieżącego zaznaczenia, wybierając poza wszystkie aktualnie wybranej kontrolki i powtórzyć poprzednią procedurę, wybierając najpierw innej kontrolki.

> [!NOTE]
> Uchwyty zmiany rozmiaru formantu dominującego są stałe, podczas gdy uchwyty kontrolek podrzędnych są puste. Dalsze zmiany rozmiaru lub wyrównanie opiera się na formant dominujący.

## <a name="size-controls"></a>Formanty rozmiaru

Zmień rozmiar kontrolki za pomocą uchwytów zmiany rozmiaru. Po umieszczeniu wskaźnika na uchwyt zmiany rozmiaru, zmienia kształt, aby wskazać kierunki, w których kontrolki można zmienić rozmiar. Uchwyty zmiany rozmiaru Active są stałe, a Jeśli uchwyt zmiany rozmiaru jest pusty, formant nie można zmienić rozmiaru na tej osi.

> [!TIP]
> Możesz również zmienić rozmiar formantu przez przyciągania formant do prowadnic i marginesów lub przenosząc jeden przypięty kontroli i przewodnik od innego.

### <a name="to-size-a-control"></a>Rozmiar kontrolki

1. Zaznacz formant.

1. Przeciągnij uchwyty zmiany rozmiaru, aby zmienić rozmiar formantu:

   - Uchwyty rozmiaru u góry i strony Zmień rozmiar poziomej lub pionowej.

   - Obsługuje rozmiar w rogach Zmień rozmiar zarówno w poziomie, jak i w pionie.

   > [!TIP]
   > Możesz zmienić rozmiar formantu jednostki jednego okna dialogowego (DLU) w danym momencie, przytrzymując **Shift** kluczy i korzystać z funkcji **po prawej stronie** i **dół** klawiszy strzałek.

> [!TIP]
> Aby automatycznie rozmiar formantu do tekstu w nim, otwórz **Format** menu lub kliknij prawym przyciskiem myszy formant i wybierz pozycję **rozmiar do zawartości**.

### <a name="to-make-controls-the-same-size"></a>Aby mieć ten sam rozmiar kontrolki

Można zmienić rozmiar grupy formantów, w zależności od rozmiaru formantu dominującego.

1. Zaznacz formanty, które chcesz zmienić.

   Wcześniej w tej serii jest dominującym kontrolka. Końcowe rozmiaru formantów w grupie zależy od rozmiaru formantu dominującego.

1. Z **Format** menu, wybierz **Wyrównaj rozmiar**, następnie wybierz **zarówno**, **wysokość**, lub **szerokość**.

### <a name="combo-box"></a>pole kombi

Po dodaniu do okna dialogowego, można rozmiar pola kombi. Można również określić rozmiar pola listy rozwijanej. Aby uzyskać więcej informacji, zobacz [dodanie wartości do kontrolki pola kombi](../windows/adding-values-to-a-combo-box-control.md).

1. Wybierz przycisk ze strzałką listy rozwijanej z prawej strony pola kombi.

   ![Strzałka na pola kombi w projekcie MFC](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   Zarys zmian kontroli do wyświetlenia rozmiaru pola kombi z listy rozwijanej obszarem rozszerzony.

1. Użyj dolnej uchwyt zmiany rozmiaru, aby zmienić początkowy rozmiar obszaru listy rozwijanej.

   ![Pole kombi&#45;rozmiaru pola w projekcie MFC](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. Wybierz strzałkę ponownie, aby zamknąć część listy rozwijanej pola kombi.

### <a name="horizontal-scroll-bar"></a>Poziomy pasek przewijania

Po dodaniu pola listy z poziomy pasek przewijania w oknie dialogowym przy użyciu klas MFC pasek przewijania nie będzie automatycznie wyświetlane w aplikacji.

Ustaw maksymalną szerokość elementu najszerszego, wywołując [CListBox::SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent) w kodzie. Bez ustawienia tej wartości pasek przewijania nie będzie wyświetlane, nawet jeśli elementy w polu listy są większe niż okno.

## <a name="align-controls"></a>Wyrównywanie formantów

1. Zaznacz formanty, które mają zostać wyrównane. Pamiętaj o wybraniu formantu, który ma być najpierw dominujący lub ustaw go jako formant dominujący przed przystąpieniem do wykonywania wyrównanie lub zmiany rozmiaru polecenia.

   Ostateczne stanowisko grupy formantów, zależy od położenie formantu dominującego.

1. Z **Format** menu, wybierz **Wyrównaj**, a następnie wybierz jedną z następujących wyrównanie:

   |Wyrównanie|Opis|
   |-----|-----------|
   |`Lefts`|Wyrównuje wybranych kontrolek wzdłuż ich po lewej stronie.|
   |`Centers`|Wyrównuje wybranych kontrolek w poziomie wzdłuż ich punkty Centrum.|
   |`Rights`|Wyrównuje wybranych kontrolek wzdłuż jego prawej stronie.|
   |`Tops`|Wyrównuje wybranych kontrolek wzdłuż górnej krawędzi.|
   |`Middles`|Wyrównuje wybranych kontrolek w pionie wzdłuż punktom środkowej.|
   |`Bottoms`|Wyrównuje wybranych kontrolek wzdłuż dolnej krawędzi.|

### <a name="to-even-spacing-between-controls"></a>Nawet odstępów między formantami

**Okna dialogowego** Edytor umożliwia utworzenie formanty równomiernie między peryferyjnych wybrano kontrolki.

1. Wybierz kontrolki, które chcesz zmienić.

1. Z **Format** menu, wybierz **Rozmieść równomiernie**, a następnie wybierz jedną z następujących wyrównanie odstępy:

   |Odstępy|Opis|
   |---|---|
   |`Across`|Formanty równomiernie między najdalej z lewej strony i wybraną kontrolkę po prawej stronie.|
   |`Down`|Formanty równomiernie między najwyższego poziomu i znajdujących się najniżej wybraną kontrolkę.|

### <a name="to-center-controls"></a>Aby wyśrodkować formantów

1. Wybierz formantów, które chcesz zmienić.

1. Z **Format** menu, wybierz **Centrum w oknie dialogowym**, a następnie wybierz jedną z następujących procedur:

   |Rozmieszczenie|Opis|
   |---|---|
   |`Vertical`|Środka kontrolki w pionie w oknie dialogowym.|
   |`Horizontal`|Centrum kontrolki w poziomie w oknie dialogowym.|

### <a name="to-arrange-push-buttons"></a>Aby rozmieścić przyciskach

1. Wybierz jeden lub więcej przycisków.

1. Z **Format** menu, wybierz **Rozmieść przyciski**, a następnie wybierz jedną z następujących procedur:

   |Rozmieszczenie|Opis|
   |---|---|
   |`Right`|Wyrównuje przycisków wzdłuż prawej krawędzi okna dialogowego.|
   |`Bottom`|Wyrównuje przycisków wzdłuż dolnej krawędzi okna dialogowego.|

   Wybranie kontrolki niż przycisku polecenia, nie ma wpływu na jego położenie.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)