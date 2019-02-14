---
title: Rozmieszczenie kontrolek w oknach dialogowych (C++) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
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
ms.openlocfilehash: 99667898428fe9532d59277bfedafd24927304dc
ms.sourcegitcommit: eb2b34a24e6edafb727e87b138499fa8945f981e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56264884"
---
# <a name="arrangement-of-controls-on-dialog-boxes-c"></a>Rozmieszczenie kontrolek w oknach dialogowych (C++)

**Okna dialogowego** edytor oferuje narzędzia układu, wyrównanie, które automatycznie rozmiaru formantów. W przypadku większości zadań, można użyć [paska narzędzi edytora okien dialogowych](../windows/showing-or-hiding-the-dialog-editor-toolbar.md). Wszystkie **Edytor okien dialogowych** są również dostępne na pasku narzędzi, polecenia **Format** menu, a większość [klawiszy skrótów](../windows/accelerator-keys-for-the-dialog-editor.md).

Wiele poleceń układu dla okien dialogowych są dostępne tylko w przypadku wybrania więcej niż jeden formant. Można wybrać jeden lub wiele kontrolek, a po wybraniu więcej niż jeden formant pierwszej, którą wybierzesz jest domyślnie formant "dominujący". Więcej informacji o dobieraniu, formantów i formant dominujący, zobacz [formanty wybierając](../windows/selecting-controls.md).

Lokalizację, wysokość i szerokość bieżącego formantu są wyświetlane w prawym dolnym rogu paska stanu. Po wybraniu całe okno dialogowe pasek stanu przedstawia położenie okna dialogowego jako całości, a jego wysokość i szerokość.

## <a name="dialog-editor-states-guides-and-grids"></a>Stwierdza, Edytor okien dialogowych (prowadnice i siatki)

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

### <a name="create-and-set-guides-and-margins"></a>Tworzenie i Ustawianie prowadnic i marginesów

Czy przenosisz się formantów, dodawanie formantów, rozmieszczanie bieżący układ, przewodniki może pomóc można wyrównać formanty dokładnie w oknie dialogowym. Przewodniki są wyświetlane jako niebieskie linie kropkowana w oknie dialogowym wyświetlany w edytorze i odpowiednie strzałki w linijki górnej i lewej strony **okna dialogowego** edytora.

Kiedy tworzysz okno dialogowe, znajdują się cztery marginesy. Marginesy są przewodniki zmodyfikowane, pojawiają się jako niebieskie linie dotted.

|Proces|Kroki|
|----------------|----------------|
|Aby utworzyć linię|W ramach linijkę wybierz jeden raz utworzyć linię. (Jednym kliknięciem tworzy nowy przewodnik; dwukrotne kliknięcie powoduje uruchomienie **ustawienia prowadnic** okno dialogowe, w którym można określić ustawienia prowadnic.)|
|Aby ustawić przewodnik|W oknie dialogowym kliknij przewodnika, a następnie przeciągnij go do nowej pozycji. (Możesz również kliknij strzałkę w linijkę, aby przeciągnąć skojarzonego przewodnika).<br/><br/>Współrzędne przewodnika są wyświetlane na pasku stanu w dolnej części okna i linijki. Przesuń wskaźnik nad strzałką znajdującą się w linijkę, aby wyświetlić dokładnego położenia przewodnika.|
|Aby usunąć prowadnicę|Przeciągnij ją z okna dialogowego.<br/><br/>\- lub —<br/><br/>Przeciągnij odpowiednie strzałkę z linijki.|
|Aby przenieść marginesów|Przeciągnij margines do nowej pozycji.<br/><br/>Aby margines zniknąć, należy przenieść margines do pozycji zero. Aby przywrócić margines, umieść wskaźnik na marginesie pozycji zero i przenieść margines w określonej pozycji.|

### <a name="align-controls-on-a-guide"></a>Wyrównywanie kontrolek do prowadnicy

Uchwyty zmiany rozmiaru kontrolek przyciąganie do prowadnic formanty są przenoszone, gdy przewodniki przyciąganie do kontrolek, formanty, nie jest przypięty wcześniej do przewodnika. Po przeniesieniu przewodnik również przenieść formantów, które są wyrównywane do niego. Formanty wyrównywane do więcej niż jeden podręcznik zmieniany jest rozmiar po przeniesieniu jeden z przewodników.

Znaczniki w linijki, określające odstępów przewodniki i formanty są definiowane przez jednostki okna dialogowego (Dlu). DLU opiera się na rozmiar czcionki okno dialogowe, zwykle 8-punktowy MS Shell Dlg. Poziomy DLU jest średniej szerokości czcionki okno dialogowe podzielona przez cztery. DLU pionowe jest średnią wysokość czcionki podzielić przez 8.

Rozmiar grupy formantów z przewodnikami:

1. Przyciągaj obok kontrolki (lub formantów) do przewodnika.

1. Przeciągnij przewodnika po drugiej stronie kontrolki (lub kontrolki).

   Jeśli to konieczne z wieloma formantami, rozmiar każdego przyciągane do prowadnicy drugiego.

1. Przenieś albo przewodnika, aby rozmiar kontrolki (lub kontrolki).

Aby zmienić interwałów znaczników:

1. Z **Format** menu, wybierz **ustawienia prowadnic**.

1. W **ustawienia prowadnic** dialogowym **odstępy między liniami siatki** określ nową wysokość i szerokość w Dlu.

### <a name="disable-guides"></a>Wyłączanie prowadnic

Klawisze specjalne w połączeniu z myszy umożliwia wyłączanie przyciągania efekt prowadnice. Za pomocą **Alt** klucz wyłącza przyciągania skutki przewodnik wybrane. Przenoszenie Przewodnik z **Shift** klucz uniemożliwia przyciągniętą posuwał się z przewodnikiem.

- Aby wyłączyć przyciąganie efekt prowadnice, przeciągnij formant, przytrzymując naciśnięty **Alt** klucza.

- Aby przenieść przewodniki bez przenoszenia przyciągniętą, przeciągnij przewodnika, przytrzymując naciśnięty **Shift** klucza.

- Aby wyłączyć prowadnice, z **Format** menu, wybierz **ustawienia prowadnic**. Następnie w **ustawienia prowadnic** dialogowego **prowadnic układu**, wybierz opcję **Brak**.

   > [!NOTE]
   > Możesz także dwukrotnie kliknąć na pasku linijkę, aby uzyskać dostęp do **ustawienia prowadnic** okno dialogowe.

> [!TIP]
> Skrót, aby wyłączyć prowadnice znajduje się na **Format** menu, wybierz opcję **Przełącz prowadnice**.

### <a name="modify-the-layout-grid"></a>Modyfikowanie siatki układu

Podczas wprowadzania lub rozmieszczanie formantów w oknie dialogowym, można użyć siatki układu do bardziej precyzyjne pozycjonowania. Po włączeniu siatki "przyciągane do" linii kropkowanej siatki tak, jakby namagnesować pojawiają się formanty. Możesz włączyć tę funkcję "przyciągania do siatki" i wyłączyć i zmienianie rozmiaru komórek siatki układu.

Aby włączyć siatki układu lub wyłączyć:

1. Z **Format** menu, wybierz **ustawienia prowadnic**.

1. W **ustawienia prowadnic** okno dialogowe, zaznacz lub wyczyść **siatki** przycisku.

   Możesz nadal kontrolować siatki w poszczególnych **okna dialogowego** okna edytora za pomocą **Przełącz siatkę** znajdujący się na [paska narzędzi edytora okien dialogowych](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

Aby zmienić rozmiar siatki układu:

1. Z **Format** menu, wybierz **ustawienia prowadnic**.

1. W **ustawienia prowadnic** okna dialogowego wpisz wysokość i szerokość w Dlu komórek w siatce. Minimalna wysokość lub szerokość jest Dlu 4.

## <a name="selecting-controls"></a>Zaznaczanie kontrolek

Zaznacz formanty do rozmiaru, wyrównanie, przenieść, skopiować, lub je usunąć, a następnie ukończ operację, którą chcesz. W większości przypadków należy wybrać więcej niż jeden formant na korzystanie z narzędzia określania rozmiaru i wyrównanie [paska narzędzi edytora okien dialogowych](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

Po wybraniu formantu, ma przyciemnione obramowanie wokół niej z niezawodnej (aktywny) lub pusty (nieaktywny) "uchwytów," małe kwadraty, są wyświetlane w krawędź zaznaczenia. Po wybraniu wielu formantów formantu dominującego ma uchwyty zmiany rozmiaru stałych i wszystkich innych wybranych kontrolek mają uchwyty zmiany rozmiaru pusty.

Podczas zmiany rozmiaru lub wyrównywanie formantów wielu **okna dialogowego** Edytor używa "formantu dominującego" Aby określić, jak rozmiar lub wyrównane do innych kontrolek. Domyślnie formant dominujący jest pierwszy formant wybrane.

### <a name="to-select-multiple-controls"></a>Aby wybrać wiele formantów

1. W [okno przybornika](/visualstudio/ide/reference/toolbox), wybierz opcję **wskaźnik** narzędzia.

1. Można dokonać wyboru, użyj jednej z następujących czynności:

   - Przeciągnij wskaźnik, aby narysować pole zaznaczenia wokół formanty, które chcesz zaznaczyć w oknie dialogowym. Po zwolnieniu przycisku myszy kontroluje wszystkie wewnątrz i przecinające się są zaznaczone pola wyboru.

   - Naciśnij i przytrzymaj **Shift** klucza, a następnie wybierz kontrolki, czy chcesz uwzględnić w zaznaczeniu.

   - Naciśnij i przytrzymaj **Ctrl** klucza, a następnie wybierz kontrolki, czy chcesz uwzględnić w zaznaczeniu.

### <a name="to-remove-a-control-from-a-group-of-selected-controls-or-to-add-a-control-to-a-group-of-selected-controls"></a>Aby usunąć formant z grupą wybranych kontrolek lub dodać kontrolkę z grupą wybranych kontrolek

Z grupą wybrano kontrolki, naciśnij i przytrzymaj **Shift** klucza, a następnie wybierz kontrolkę, która do usuwania lub Dodaj do istniejącego zaznaczenia.

   > [!NOTE]
   > Przytrzymanie **Ctrl** klucza i wybierając polecenie Kontrolki wyboru spowoduje, że, które kontrolują formantu dominującego w ramach tego zaznaczenia.

### <a name="to-specify-the-dominant-control"></a>Aby określić formant dominujący

Naciśnij i przytrzymaj **Ctrl** klucza i wybierz formant, którego chcesz użyć do wywierania wpływu na rozmiar lub lokalizację innych formantów *pierwszy*.

> [!NOTE]
> Uchwyty zmiany rozmiaru formantu dominującego są stałe, podczas gdy uchwyty kontrolek podrzędnych są puste. Dalsze zmiany rozmiaru lub wyrównanie opiera się na formant dominujący.

### <a name="to-change-the-dominant-control"></a>Aby zmienić kontrolki dominującej

1. Wyczyść bieżący wybór, klikając poza wszystkie obecnie wybrane formanty.

1. Powtórz poprzedniej procedury, wybierając najpierw innej kontrolki.

## <a name="sizing-controls"></a>Formanty rozmiaru

Zmień rozmiar kontrolki za pomocą uchwytów zmiany rozmiaru. Po umieszczeniu wskaźnika na uchwyt zmiany rozmiaru, zmienia kształt, aby wskazać kierunki, w których kontrolki można zmienić rozmiar. Uchwyty zmiany rozmiaru Active są wypełnione; Jeśli uchwyt zmiany rozmiaru jest pusty, formant nie można zmienić rozmiaru na tej osi.

Możesz również zmienić rozmiar formantu przez przyciągania formant do prowadnic i marginesów lub przenosząc jeden przypięty kontroli i przewodnik od innego.

### <a name="to-size-an-individual-control"></a>Rozmiar poszczególnych kontrolek

1. Zaznacz formant.

1. Przeciągnij uchwyty zmiany rozmiaru, aby zmienić rozmiar formantu:

   - Uchwyty zmiany rozmiaru u góry i strony Zmień rozmiar poziomej lub pionowej.

   - Uchwyty zmiany rozmiaru w rogach Zmień rozmiar zarówno w poziomie, jak i w pionie.

   > [!TIP]
   > Możesz zmienić rozmiar formantu jednostki jednego okna dialogowego (DLU) w danym momencie, przytrzymując **Shift** kluczy i korzystać z funkcji **Strzałka w prawo** i **strzałkę w dół** kluczy.

### <a name="to-automatically-size-a-control-to-fit-the-text-within-it"></a>Aby automatycznie rozmiar formantu do tekstu w nim

Wybierz **rozmiar do zawartości** z **Format** menu lub kliknij prawym przyciskiem myszy formant i wybierz pozycję **rozmiar do zawartości** z menu skrótów.

### <a name="to-make-controls-the-same-width-height-or-size"></a>Aby wprowadzić kontroluje tej samej szerokości, wysokości lub rozmiar

Można zmienić rozmiar grupy formantów, w zależności od rozmiaru formantu dominującego.

1. Zaznacz formanty, które chcesz zmienić.

   Wcześniej w tej serii jest dominującym kontrolka. Końcowe rozmiaru formantów w grupie zależy od rozmiaru formantu dominującego.

1. Z **Format** menu, wybierz **Wyrównaj rozmiar**, następnie wybierz **zarówno**, **wysokość**, lub **szerokość**.

### <a name="to-set-the-size-of-the-combo-box-and-its-drop-down-list"></a>Aby ustawić rozmiar kombi pola i jego listy rozwijanej

Po dodaniu do okna dialogowego, można rozmiar pola kombi. Można również określić rozmiar pola listy rozwijanej. Aby uzyskać więcej informacji, zobacz [dodanie wartości do kontrolki pola kombi](../windows/adding-values-to-a-combo-box-control.md).

#### <a name="to-size-a-combo-box"></a>Rozmiar pola kombi

1. Zaznacz formant pola kombi w oknie dialogowym.

   Początkowo tylko uchwyty zmiany rozmiaru lewej i prawej są aktywne.

1. Ustaw szerokość pola kombi za pomocą uchwytów zmiany rozmiaru.

Można również ustawić pionowy rozmiar część rozwijana pola kombi.

#### <a name="to-set-the-size-of-the-combo-box-drop-down-list"></a>Aby ustawić rozmiar kombi pole listy rozwijanej

1. Wybierz przycisk ze strzałką listy rozwijanej z prawej strony pola kombi.

   ![Strzałka na pola kombi w projekcie MFC](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   Zarys zmian kontroli do wyświetlenia rozmiaru pola kombi z listy rozwijanej obszarem rozszerzony.

1. Użyj dolnej uchwyt zmiany rozmiaru, aby zmienić początkowy rozmiar obszaru listy rozwijanej.

   ![Pole kombi&#45;rozmiaru pola w projekcie MFC](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. Wybierz strzałkę ponownie, aby zamknąć część listy rozwijanej pola kombi.

### <a name="to-set-the-width-of-a-horizontal-scroll-bar-and-make-it-appear"></a>Ustawianie szerokości poziomego paska przewijania i są wyświetlane

Po dodaniu pola listy z poziomy pasek przewijania w oknie dialogowym przy użyciu klas MFC pasek przewijania nie będzie automatycznie wyświetlane w aplikacji.

Ustaw maksymalną szerokość elementu najszerszego, wywołując [CListBox::SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent) w kodzie.

   Bez ustawienia tej wartości pasek przewijania nie będzie wyświetlane, nawet jeśli elementy w polu listy są większe niż okno.

## <a name="group-radio-buttons-on-a-dialog-box"></a>Grupa przycisków radiowych w oknie dialogowym

Po dodaniu przycisków radiowych w oknie dialogowym je traktować jako grupa, ustawiając **grupy** właściwość **właściwości** okna dla pierwszego przycisku w grupie. Pojawi się w polu Identyfikator kontrolki, dla tego przycisku radiowego [Kreator dodawania zmiennej składowej](../ide/add-member-variable-wizard.md), co pozwala dodać zmienną członkowską, grupy przycisków radiowych.

Może mieć więcej niż jedna grupa przycisków radiowych w oknie dialogowym, a każda grupa powinny zostać dodane, korzystając z następującej procedury.

### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>Aby dodać grupę przycisków radiowych w oknie dialogowym

1. Zaznacz formant przycisku radiowego w [okno przybornika](/visualstudio/ide/reference/toolbox) i wybierz lokalizację znajdującą się w oknie dialogowym, które chcesz umieścić kontrolkę.

1. Powtórz krok 1, aby dodać dowolną liczbę przyciski radiowe, ile potrzebujesz. Upewnij się, że przyciski radiowe w grupie są następujących po sobie w kolejności tabulacji.

1. W [okno właściwości](/visualstudio/ide/reference/properties-window)ustaw **grupy** właściwość *pierwszy* przycisku radiowego w kolejności tabulacji na **True**.

   Zmiana **grupy** właściwości **True** dodaje WS_GROUP styl do przycisku wpis obiektu okna dialogowego skryptu zasobu i gwarantuje, że użytkownik może wybrać tylko jeden przycisk radiowy jednocześnie przycisku grupy (po kliknięciu przycisku radiowego co inne osoby w grupie zostaną wyczyszczone).

   > [!NOTE]
   > Tylko pierwszy przycisk radiowy w grupie powinny mieć **grupy** właściwością **True**. Jeśli masz dodatkowe formanty, które nie są częścią grupy przycisk, ustaw **grupy** właściwość pierwszy formant *jest spoza grupy* do **True** także. Pierwszy formant spoza grupy można szybko określić, naciskając klawisz **Ctrl**+**D** Aby wyświetlić kolejność tabulacji.

### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>Aby dodać zmiennej składowej w grupie przycisków radiowych

1. Kliknij prawym przyciskiem myszy pierwszą kontrolkę przycisku radiowego w kolejności tabulacji (formant dominujący i z **grupy** właściwość ustawioną na wartość True).

1. Wybierz **Dodaj zmienną** z menu skrótów.

1. W [Kreator dodawania zmiennej składowej](../ide/add-member-variable-wizard.md), wybierz opcję **zmienna sterująca** pole wyboru, a następnie wybierz **wartość** przycisku radiowego.

1. W **nazwa zmiennej** wpisz nazwę dla nowej zmiennej elementu członkowskiego.

1. W **typ zmiennej** pola listy, wybierz opcję **int** lub typ `int`.

1. Teraz można edytować swój kod, aby określić, który przycisk radiowy powinien zostaną wyświetlone jako zaznaczone. Na przykład `m_radioBox1 = 0;` wybiera pierwszy przycisk radiowy w grupie.

## <a name="to-align-groups-of-controls"></a>Dopasowanie grup formantów

1. Zaznacz formanty, które mają zostać wyrównane. Pamiętaj o wybraniu formantu, który ma być formantu dominującego najpierw lub ustaw go jako formant dominujący przed przystąpieniem do wykonywania wyrównanie lub zmiany rozmiaru polecenia.

   Ostateczne stanowisko grupy formantów, zależy od położenie formantu dominującego. Aby uzyskać więcej informacji dotyczących zaznaczania formantu dominującego zobacz [Określanie formantu dominującego](../windows/specifying-the-dominant-control.md).

1. Z **Format** menu, wybierz **Wyrównaj**, a następnie wybierz jedną z następujących wyrównanie:

   |Wartość|Opis|
   |-----|-----------|
   |`Lefts`|Wyrównuje wybranych kontrolek wzdłuż ich po lewej stronie.|
   |`Centers`|Wyrównuje wybranych kontrolek w poziomie wzdłuż ich punkty Centrum.|
   |`Rights`|Wyrównuje wybranych kontrolek wzdłuż jego prawej stronie.|
   |`Tops`|Wyrównuje wybranych kontrolek wzdłuż górnej krawędzi.|
   |`Middles`|Wyrównuje wybranych kontrolek w pionie wzdłuż punktom środkowej.|
   |`Bottoms`|Wyrównuje wybranych kontrolek wzdłuż dolnej krawędzi.|

### <a name="to-even-the-spacing-between-controls"></a>Nawet odstępów między formantami

**Okna dialogowego** Edytor umożliwia utworzenie formanty równomiernie między peryferyjnych wybrano kontrolki.

1. Wybierz kontrolki, które chcesz zmienić.

1. Z **Format** menu, wybierz **Rozmieść równomiernie**, a następnie wybierz jedną z następujących wyrównanie odstępy:

   - `Across`: miejsce formantów równomiernie między najdalej z lewej strony i wybraną kontrolkę po prawej stronie.

   - `Down`: miejsce formantów równomiernie między najwyższego poziomu i znajdujących się najniżej wybraną kontrolkę.

### <a name="to-center-controls-in-a-dialog-box"></a>Aby wyśrodkować formantów w oknie dialogowym

1. Wybierz formantów, które chcesz zmienić.

1. Z **Format** menu, wybierz **Centrum w oknie dialogowym**, a następnie wybierz jedną z następujących procedur:

   - `Vertical`: Centrum kontrolki w pionie w oknie dialogowym.

   - `Horizontal`: Centrum kontrolki w poziomie w oknie dialogowym.

### <a name="to-arrange-push-buttons-along-the-right-or-bottom-of-a-dialog-box"></a>Aby rozmieścić przyciski poleceń po prawej stronie lub u dołu okna dialogowego

1. Wybierz jeden lub więcej przycisków.

1. Z **Format** menu, wybierz **Rozmieść przyciski**, a następnie wybierz jedną z następujących procedur:

   - `Right`: wyrównuje przycisków wzdłuż prawej krawędzi okna dialogowego.

   - `Bottom`: wyrównuje przycisków wzdłuż dolnej krawędzi okna dialogowego.

       Wybranie kontrolki niż przycisku polecenia, nie ma wpływu na jego położenie.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)