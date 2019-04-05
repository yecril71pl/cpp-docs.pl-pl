---
title: 'Instrukcje: Układ kontrolki (C++) | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 878b7371dfa77880d68f1001444ed44b84d7240c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037424"
---
# <a name="how-to-layout-controls-c"></a>Instrukcje: Układ kontrolki (C++)

**Edytor okien dialogowych** udostępnia narzędzia układu, które automatycznie rozmiaru kontrolki i wyrównać. W przypadku większości zadań, można użyć [paska narzędzi edytora okien dialogowych](../windows/showing-or-hiding-the-dialog-editor-toolbar.md). Wszystkie **Edytor okien dialogowych** są również dostępne na pasku narzędzi, polecenia **Format** menu, a większość [klawiszy skrótów](../windows/accelerator-keys-for-the-dialog-editor.md).

Wiele poleceń układu dla okien dialogowych są dostępne tylko w przypadku wybrania więcej niż jeden formant. Można wybrać jeden lub wiele kontrolek, a po wybraniu więcej niż jeden formant pierwszej, którą wybierzesz jest domyślnie formantu dominującego.

Lokalizację, wysokość i szerokość bieżącego formantu są wyświetlane w prawym dolnym rogu paska stanu. Po wybraniu całe okno dialogowe pasek stanu przedstawia położenie okna dialogowego jako całości, a jego wysokość i szerokość.

## <a name="arrange-controls"></a>Rozmieszczanie formantów

Można rozmieścić formanty w oknach dialogowych za pomocą **Edytor okien dialogowych** w jednym z trzech różnych stanów:

- Prowadnice i marginesy na Ustaw jako domyślny.

- Przy użyciu siatki układu w.

- Bez żadnych funkcji przyciągania lub wyrównania.

[Paska narzędzi edytora okien dialogowych](../windows/showing-or-hiding-the-dialog-editor-toolbar.md) zawiera przyciski, które sterują stanu.

- Aby zmienić stan, wybierz odpowiednią ikonę lub przejdź do menu **Format** > **ustawienia prowadnic**.

**Ustawienia prowadnic** okno dialogowe ma następujące właściwości:

|Właściwość|Opis|
|---|---|
|**Układ prowadnic**|Wyświetla ustawienia prowadnic układu.|
|**Brak**|Ukrywa narzędzia układu.|
|**Linijki i prowadnice**|Po włączeniu dodaje linijki narzędzia układ, i umożliwia przewodników, które mają być umieszczone w linijki. Przewodniki domyślne są marginesów.|
|**Siatka**|Tworzy siatki układu. Nowe kontrolki automatycznie zostaną wyrównane do siatki.|
|**Odstępy między liniami siatki**|Wyświetla ustawienia odstępy między liniami siatki w jednostkach pola okna dialogowego (Dlu).|
|**Szerokość: Dlu**|Ustawia szerokość siatki układu w Dlu. Poziomy DLU jest średniej szerokości czcionki okno dialogowe podzielona przez 4.|
|**Wysokość: Dlu**|Określa wysokość siatki układu w Dlu. DLU pionowe jest średnią wysokość czcionki okno dialogowe podzielić przez 8.|

### <a name="guides-and-margins"></a>Prowadnic i marginesów

Czy przenosisz się formantów, dodawanie formantów, rozmieszczanie bieżący układ, prowadnic i marginesów może pomóc można wyrównać formanty dokładnie w oknie dialogowym.

Podczas tworzenia okno dialogowe cztery przewodniki zmodyfikowane o nazwie marginesy znajdują się i są wyświetlane jako niebieskie linie przerywana.

- Aby przenieść marginesy, przeciągnij margines do nowej pozycji.

- Aby margines zniknąć, należy przenieść margines do pozycji zero.

- Aby przywrócić margines, umieść wskaźnik na marginesie pozycji zero i przenieść margines w określonej pozycji.

Przewodniki są wyświetlane jako niebieskie linie kropkowana w oknie dialogowym wyświetlany w edytorze i odpowiednie strzałki w linijki górnej i lewej strony **Edytor okien dialogowych**. Uchwyty zmiany rozmiaru kontrolek przyciąganie do prowadnic formanty są przenoszone, gdy przewodniki przyciąganie do kontrolek, formanty, nie jest przypięty wcześniej do przewodnika. Po przeniesieniu przewodnik również przenieść formantów, które są wyrównywane do niego. Formanty wyrównywane do więcej niż jeden podręcznik zmieniany jest rozmiar po przeniesieniu jeden z przewodników.

- Aby utworzyć linię w ramach linijkę, wybierz jeden raz, aby utworzyć linię lub kliknij dwukrotnie, aby uruchomić **ustawienia prowadnic** okno dialogowe, w którym można określić ustawienia prowadnic.

- Aby ustawić przewodnik w oknie dialogowym, wybierz przewodnika i przeciągnij go do nowej pozycji lub wybierz strzałkę w linijkę, aby przeciągnąć skojarzonego przewodnika.

   Współrzędne przewodnika są wyświetlane na pasku stanu w dolnej części okna i na linijce lub Przesuń wskaźnik nad strzałką znajdującą się w linijkę, aby wyświetlić dokładnego położenia przewodnika.

- Aby usunąć wskazówki, przeciągnij ją z okna dialogowego lub przeciągnij strzałkę odpowiedniego z linijki.

Znaczniki w linijki, określające odstępów przewodniki i formanty są definiowane przez jednostki okna dialogowego (Dlu). DLU opiera się na rozmiar czcionki okno dialogowe, zwykle 8-punktowy MS Shell Dlg. Poziomy DLU jest średniej szerokości czcionki okno dialogowe podzielona przez cztery. DLU pionowe jest średnią wysokość czcionki podzielić przez 8.

- Aby zmienić interwałów znaczników, przejdź do menu **Format** > **ustawienia prowadnic**, a następnie w obszarze **odstępy między liniami siatki** określ nową wysokość i szerokość w Dlu.

### <a name="layout-grid"></a>Siatka układu

Jeśli chcesz umieścić lub rozmieszczanie formantów w oknie dialogowym, użyj siatki układu do bardziej precyzyjne pozycjonowania. Po włączeniu siatki, tak, jakby namagnesować kontrolki spowoduje przyciąganie do linii kropkowanej siatki.

- Aby włączyć siatki układu lub wyłączyć, przejdź do menu **Format** > **ustawienia prowadnic** i zaznacz lub wyczyść **siatki** przycisku.

   Możesz nadal kontrolować siatki w poszczególnych **Edytor okien dialogowych** systemu windows za pomocą **Przełącz siatkę** znajdujący się na [paska narzędzi edytora okien dialogowych](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

- Aby zmienić rozmiar siatki układu, przejdź do menu **Format** > **ustawienia prowadnic** i wpisać wysokość i szerokość Dlu komórek w siatce. Minimalna wysokość lub szerokość jest 4.

### <a name="disable-guides"></a>Wyłączanie prowadnic

Klawisze specjalne w połączeniu z myszy umożliwia wyłączanie przyciągania efekt prowadnice. Za pomocą **Alt** klucz wyłącza przyciągania skutki przewodnik wybrane. Przenoszenie Przewodnik z **Shift** klucz uniemożliwia przyciągniętą posuwał się z przewodnikiem.

- Aby wyłączyć przyciąganie efekt prowadnice, przeciągnij formant, przytrzymując naciśnięty **Alt** klucza.

- Aby przenieść przewodniki bez przenoszenia przyciągniętą, przeciągnij przewodnika, przytrzymując naciśnięty **Shift** klucza.

- Aby wyłączyć prowadnice, przejdź do menu **Format** > **ustawienia prowadnic**. Następnie w obszarze **prowadnic układu**, wybierz opcję **Brak**.

   > [!TIP]
   > Można również użyć skrótu w menu **Format** > **Przełącz prowadnice**.

## <a name="select-controls"></a>Zaznaczanie formantów

Zaznacz formanty do rozmiaru, wyrównanie, przenieść, skopiować, lub je usunąć, a następnie ukończ operację, którą chcesz. W większości przypadków należy wybrać więcej niż jeden formant na korzystanie z narzędzia określania rozmiaru i wyrównanie [paska narzędzi edytora okien dialogowych](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

Po wybraniu kontrolki w nim przyciemnione obramowanie z niezawodnej (aktywny) lub pusty (nieaktywny) uchwytów małe kwadraty, które pojawiają się na krawędź zaznaczenia. Po wybraniu wielu formantów formantu dominującego ma uchwyty zmiany rozmiaru stałych i wszystkich innych wybranych kontrolek mają uchwyty zmiany rozmiaru pusty.

- Wybierz kontrolki, [okno przybornika](/visualstudio/ide/reference/toolbox), wybierz opcję **wskaźnik** narzędzia i umożliwia wybór przez jedną z następujących czynności:

  - Przeciągnij wskaźnik, aby narysować pole zaznaczenia wokół formanty, które chcesz zaznaczyć w oknie dialogowym. Po zwolnieniu przycisku myszy kontroluje wszystkie wewnątrz i przecinające się są zaznaczone pola wyboru.

  - Naciśnij i przytrzymaj **Shift** klucza, a następnie wybierz kontrolki, czy chcesz uwzględnić w zaznaczeniu.

  - Naciśnij i przytrzymaj **Ctrl** klucza, a następnie wybierz kontrolki, czy chcesz uwzględnić w zaznaczeniu.

- Aby dodać lub usunąć formant z grupy wybranych kontrolek, przytrzymaj wciśnięty **Shift** klucza, a następnie wybierz kontrolkę, aby dodać lub usunąć.

### <a name="dominant-controls"></a>Formanty dominujące

Podczas zmiany rozmiaru lub wyrównywanie formantów wielu **Edytor okien dialogowych** używa formantu dominującego, aby określić, jak rozmiar lub wyrównane do innych kontrolek. Domyślnie formant dominujący jest pierwszy formant wybrane.

- Aby określić formant dominujący, przytrzymaj wciśnięty **Ctrl** klucza i wybierz formant, którego chcesz użyć do wywierania wpływu na rozmiar lub lokalizację innych formantów *pierwszy*. Przytrzymanie **Ctrl** klucza i wybierając polecenie Kontrolki wyboru spowoduje również, że, które kontrolują formantu dominującego w ramach tego zaznaczenia.

- Formant dominujący, wyczyścić bieżącego zaznaczenia, wybierając poza wszystkie aktualnie wybranej kontrolki i powtórzyć powyższą procedurę, wybranie innej kontrolki *pierwszy*.

> [!NOTE]
> Uchwyty zmiany rozmiaru formantu dominującego są stałe, podczas gdy uchwyty kontrolek podrzędnych są puste. Dalsze zmiany rozmiaru lub wyrównanie opiera się na formant dominujący.

## <a name="size-controls"></a>Formanty rozmiaru

Zmień rozmiar kontrolki za pomocą uchwytów zmiany rozmiaru. Po umieszczeniu wskaźnika na uchwyt zmiany rozmiaru, zmienia kształt, aby wskazać kierunki, w których kontrolki można zmienić rozmiar. Uchwyty zmiany rozmiaru Active są stałe, a Jeśli uchwyt zmiany rozmiaru jest pusty, formant nie można zmienić rozmiaru na tej osi.

- Aby rozmiar kontrolki, wybierz kontrolkę, a następnie przeciągnij uchwyty zmiany rozmiaru, aby zmienić rozmiar.

  - Uchwyty rozmiaru u góry i strony Zmień rozmiar poziomej lub pionowej.

  - Obsługuje rozmiar w rogach Zmień rozmiar zarówno w poziomie, jak i w pionie.

   > [!TIP]
   > Możesz zmienić rozmiar formantu jednostki jednego okna dialogowego (DLU) w danym momencie, przytrzymując **Shift** kluczy i korzystać z funkcji **po prawej stronie** i **dół** klawiszy strzałek.

- Aby automatycznie rozmiar formantu do tekstu w nim, przejdź do menu **Format** lub kliknij prawym przyciskiem myszy formant i wybierz pozycję **rozmiar do zawartości**.

- Aby formantów taki sam rozmiar, wybierz kontrolki, aby zmienić rozmiar, a następnie przejdź do menu **Format** > **Wyrównaj rozmiar**, następnie wybierz **zarówno**, **Wysokość**, lub **szerokość**.

   Możesz zmienić rozmiar grupy formantów na podstawie rozmiaru formantu dominującego jest formantem wcześniej z tej serii. Końcowe rozmiaru formantów w grupie zależy od rozmiaru formantu dominującego.

- Aby rozmiar grupy formantów z liniami, przyciąganie obok kontrolki (lub formantów) w przewodniku, a następnie przeciągnij przewodnika po drugiej stronie kontrolki (lub kontrolki). Teraz możesz przenieść albo przewodnika, aby rozmiar kontrolki (lub kontrolki).

   Jeśli to konieczne z wieloma formantami, rozmiar każdego przyciągane do prowadnicy drugiego.

### <a name="other-controls"></a>Inne kontrolki

Po dodaniu do okna dialogowego, można rozmiar pola kombi. Można również określić rozmiar pola listy rozwijanej. Aby uzyskać więcej informacji, zobacz [dodanie wartości do kontrolki pola kombi](../windows/adding-values-to-a-combo-box-control.md).

1. Wybierz przycisk ze strzałką listy rozwijanej z prawej strony pola kombi.

   ![Strzałka na pola kombi w projekcie MFC](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   Zarys zmian kontroli do wyświetlenia rozmiaru pola kombi z listy rozwijanej obszarem rozszerzony.

1. Użyj dolnej uchwyt zmiany rozmiaru, aby zmienić początkowy rozmiar obszaru listy rozwijanej.

   ![Pole kombi&#45;rozmiaru pola w projekcie MFC](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. Wybierz strzałkę ponownie, aby zamknąć część listy rozwijanej pola kombi.

> [!NOTE]
> Po dodaniu pola listy przy użyciu paska przewijania w poziomie do okna dialogowego za pomocą MFC pasek przewijania nie będzie automatycznie wyświetlane w aplikacji.
>
> Ustaw maksymalną szerokość elementu najszerszego, wywołując [CListBox::SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent) w kodzie. Bez ustawienia tej wartości pasek przewijania nie będzie wyświetlane, nawet jeśli elementy w polu listy są większe niż okno.

## <a name="align-controls"></a>Wyrównywanie formantów

- Aby wyrównać formanty, zaznacz formanty, które mają zostać wyrównane. Przejdź do menu **Format** > **Wyrównaj** i wybierz jedną z następujących wyrównanie:

   |Wyrównanie|Opis|
   |-----|-----------|
   |**Wej**|Wyrównuje wybranych kontrolek wzdłuż ich po lewej stronie.|
   |**Centra**|Wyrównuje wybranych kontrolek w poziomie wzdłuż ich punkty Centrum.|
   |**Prawa**|Wyrównuje wybranych kontrolek wzdłuż jego prawej stronie.|
   |**Górne krawędzie**|Wyrównuje wybranych kontrolek wzdłuż górnej krawędzi.|
   |**Lewych**|Wyrównuje wybranych kontrolek w pionie wzdłuż punktom środkowej.|
   |**Dołu**|Wyrównuje wybranych kontrolek wzdłuż dolnej krawędzi.|

   Pamiętaj o wybraniu formantu, który ma być najpierw dominujący lub ustaw go jako formant dominujący przed przystąpieniem do wykonywania wyrównanie lub zmiany rozmiaru polecenia, ponieważ ostatecznego stanowiska grupy formantów zależy od położenie formantu dominującego.

- Aby równomiernie miejsca na kontrolki zaznacz formanty, które chcesz zmienić. Przejdź do menu **Format** > **Rozmieść równomiernie** i wybierz jedną z następujących wyrównanie odstępy:

   |Odstępy|Opis|
   |---|---|
   |**Między**|Formanty równomiernie między najdalej z lewej strony i wybraną kontrolkę po prawej stronie.|
   |**W dół**|Formanty równomiernie między najwyższego poziomu i znajdujących się najniżej wybraną kontrolkę.|

- Aby wyśrodkować formantów, wybierz formantów, które chcesz zmienić. Przejdź do menu **Format** > **Centrum w oknie dialogowym** i wybierz jedną z następujących procedur:

   |Rozmieszczenie|Opis|
   |---|---|
   |**W pionie**|Środka kontrolki w pionie w oknie dialogowym.|
   |**Poziome**|Centrum kontrolki w poziomie w oknie dialogowym.|

- Aby zorganizować projekt przycisków, wybierz jeden lub więcej przycisków. Przejdź do menu **Format** > **Rozmieść przyciski**, a następnie wybierz jedno z następujących procedur:

   |Rozmieszczenie|Opis|
   |---|---|
   |**Prawe**|Wyrównuje przycisków wzdłuż prawej krawędzi okna dialogowego.|
   |**dolny**|Wyrównuje przycisków wzdłuż dolnej krawędzi okna dialogowego.|

   Wybranie kontrolki niż przycisku polecenia, nie ma wpływu na jego położenie.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Zarządzanie formantów okna dialogowego](controls-in-dialog-boxes.md)<br/>
[Instrukcje: Dodawanie, edytowanie lub usuwanie kontrolek](adding-editing-or-deleting-controls.md)<br/>
[Instrukcje: Definiowanie wartości i kontrola dostępu](defining-mnemonics-access-keys.md)<br/>