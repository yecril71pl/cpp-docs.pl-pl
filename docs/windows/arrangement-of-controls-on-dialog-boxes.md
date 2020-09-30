---
title: 'Instrukcje: kontrolki układu (C++) | Microsoft Docs'
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
ms.openlocfilehash: ac21096f18b1331759f9bf7dfe613100298b7296
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509663"
---
# <a name="how-to-layout-controls-c"></a>Instrukcje: kontrolki układu (C++)

**Edytor okien dialogowych** udostępnia narzędzia układu, które automatycznie dopasowują i dopasowują rozmiar formantów. W przypadku większości zadań można użyć [paska narzędzi edytora okien dialogowych](./dialog-editor.md). Wszystkie polecenia paska narzędzi **edytora okien dialogowych** są również dostępne w menu **Format** i większość [klawiszy skrótów](./dialog-editor.md).

Wiele poleceń układu okien dialogowych jest dostępnych tylko wtedy, gdy wybrano więcej niż jeden formant. Można wybrać pojedynczą kontrolkę lub wiele kontrolek, po wybraniu więcej niż jednej kontrolki, pierwszy wybierany jest domyślnie formant dominujący.

Położenie, Wysokość i szerokość bieżącego formantu są wyświetlane w prawym dolnym rogu paska stanu. Po wybraniu całego okna dialogowego pasek stanu wyświetla pozycję okna dialogowego jako całość i jego wysokość i szerokość.

## <a name="arrange-controls"></a>Rozmieszczanie kontrolek

Kontrolki można rozmieścić w oknach dialogowych przy użyciu **edytora okien dialogowych** w jednym z trzech różnych stanów:

- Przy użyciu prowadnic i marginesów ustawione jako domyślne.

- Z siatką układu.

- Bez żadnych funkcji przyciągania ani wyrównania.

[Pasek narzędzi edytora okien dialogowych](./dialog-editor.md) zawiera przyciski kontrolujące stan.

- Aby zmienić stan, wybierz odpowiednią ikonę lub przejdź do menu **Formatowanie**  >  **ustawienia przewodnika**.

Okno dialogowe **ustawienia przewodnika** ma następujące właściwości:

|Właściwość|Opis|
|---|---|
|**Prowadnice układu**|Wyświetla ustawienia prowadnic układu.|
|**Brak**|Ukrywa narzędzia układu.|
|**Reguły i prowadnice**|Gdy ta funkcja jest włączona, dodaje do narzędzi układu reguły i umożliwia prowadnice umieszczane w linijkach. Domyślnymi prowadnicami są marginesy.|
|**Siatka**|Tworzy siatkę układu. Nowe kontrolki zostaną automatycznie wyrównane do siatki.|
|**Odstępy siatki**|Wyświetla ustawienia odstępów siatki w jednostkach okna dialogowego (DLU).|
|**Szerokość: DLU**|Ustawia szerokość siatki układu w DLU. DLU poziomy to średnia szerokość czcionki okna dialogowego podzielona przez 4.|
|**Wysokość: DLU**|Ustawia wysokość siatki układu w DLU. Pionowa DLU jest średnią wysokością czcionki okna dialogowego podzieloną przez 8.|

### <a name="guides-and-margins"></a>Prowadnice i marginesy

Bez względu na to, czy przenosisz kontrolki, dodajesz kontrolki, czy zmienisz układ bieżącego układu, prowadnice i marginesy mogą ułatwić wyrównywanie kontrolek w oknie dialogowym.

Po utworzeniu okna dialogowego są dostępne cztery zmodyfikowane prowadnice o nazwie marginesy i pojawiają się jako niebieskie linie kropkowane.

- Aby przenieść marginesy, przeciągnij margines do nowej pozycji.

- Aby ukryć margines, Przenieś margines do pozycji zerowej.

- Aby przywrócić margines, umieść wskaźnik nad pozycją zero marginesu i Przenieś margines do pozycji.

Prowadnice są wyświetlane jako niebieskie linie kropkowane w oknie dialogowym wyświetlanym w edytorze i odpowiadające im strzałki w linijkach u góry i wzdłuż lewej krawędzi **edytora okien dialogowych**. Uchwyty zmiany rozmiarów formantów są przyciągane do prowadnic podczas przenoszenia formantów i są przyciągane do kontrolek, jeśli nie ma żadnych kontrolek, które zostały wcześniej przyłączone do przewodnika. Gdy prowadnica zostanie przeniesiona, formanty, które są przypięte do niej również przenoszone. Zmiany rozmiaru kontrolek przypiętych do więcej niż jednej prowadnicy są zmieniane po przeniesieniu jednego z prowadnic.

- Aby utworzyć prowadnicę w obrębie linijki, wybierz raz, aby utworzyć przewodnik, lub kliknij dwukrotnie, aby uruchomić okno dialogowe **ustawienia przewodnika** , w którym można określić ustawienia przewodnika.

- Aby ustawić przewodnik w oknie dialogowym, zaznacz prowadnicę i przeciągnij ją do nowej pozycji lub wybierz strzałkę na linijce, aby przeciągnąć skojarzoną prowadnicę.

   Współrzędne przewodnika są wyświetlane na pasku stanu u dołu okna i w linijce lub przesuwaj wskaźnik myszy nad strzałką na linijce, aby wyświetlić dokładną pozycję przewodnika.

- Aby usunąć przewodnik, przeciągnij ten przewodnik z okna dialogowego lub przeciągnij odpowiednią strzałkę poza linijkę.

Znaczniki w linijkach, które określają odstępy między prowadnicami i kontrolkami, są definiowane przez jednostki okna dialogowego (DLU). DLU jest oparta na rozmiarze czcionki okna dialogowego, zazwyczaj 8-punktowego okna powłoki MS Shell. DLU poziomy to średnia szerokość czcionki okna dialogowego podzielona przez cztery. Pionowa DLU jest średnią wysokością czcionki podzieloną przez 8.

- Aby zmienić interwały znaczników, przejdź do menu **Formatowanie**  >  **ustawień przewodnika**, a następnie w polu **odstępy siatki** określ nową szerokość i wysokość w DLU.

### <a name="layout-grid"></a>Siatka układu

Gdy umieszczasz lub układasz kontrolki w oknie dialogowym, użyj siatki układu w celu dokładniejszego pozycjonowania. Gdy siatka jest włączona, formanty będą przyciągane do linii kropkowanych siatki, tak jakby były magnesne.

- Aby włączyć lub wyłączyć siatkę układu, przejdź do menu **Formatowanie**  >  **ustawień przewodnika** i wybierz lub wyczyść przycisk **siatki** .

   Można nadal kontrolować siatkę w poszczególnych oknach **edytora okien dialogowych** za pomocą przycisku **Przełącz siatkę** na [pasku narzędzi edytora okien dialogowych](./dialog-editor.md).

- Aby zmienić rozmiar siatki układu, przejdź do **pozycji menu**  >  **ustawienia przewodnika** i wpisz wysokość i szerokość w DLU dla komórek siatki. Minimalna wysokość lub szerokość to 4.

### <a name="disable-guides"></a>Wyłącz przewodniki

Aby wyłączyć efekt przyciągania przewodników, można użyć klawiszy specjalnych w połączeniu z myszą. Użycie klawisza **Alt** powoduje wyłączenie efektów przyciągania wybranego przewodnika. Przeniesienie przewodnika przy użyciu klawisza **SHIFT** uniemożliwia przeniesienie formantów z przewodnika.

- Aby wyłączyć efekt przyciągania przewodników, przeciągnij kontrolkę, trzymając wciśnięty klawisz **Alt** .

- Aby przenieść prowadnice bez przenoszenia przyciągniętych kontrolek, przeciągnij prowadnicę, trzymając wciśnięty klawisz **SHIFT** .

- Aby wyłączyć przewodniki, przejdź do menu **Formatowanie**  >  **ustawienia przewodnika**. Następnie w obszarze **prowadnice układu**wybierz opcję **Brak**.

   > [!TIP]
   > Możesz również użyć skrótu w **formacie**menu  >  **Przełącz prowadnice**.

## <a name="select-controls"></a>Wybierz kontrolki

Wybierz pozycję kontrolki, aby zmienić rozmiar, Wyrównaj, Przenieś, skopiuj lub Usuń, a następnie ukończ żądaną operację. W większości przypadków należy wybrać więcej niż jedną kontrolkę, aby użyć narzędzi do ustalania rozmiarów i wyrównania na [pasku narzędzi edytora okien dialogowych](./dialog-editor.md).

Gdy kontrolka jest zaznaczona, ma zacienione obramowanie wokół niej z pełnymi (aktywnymi) lub pustymi (nieaktywnymi) uchwytami zmiany rozmiarów, małych kwadratów, które pojawiają się w obramowaniu zaznaczenia. Gdy wybrano wiele kontrolek, formant dominujący ma pełne dojścia do rozmiarów i wszystkie pozostałe zaznaczone kontrolki mają puste uchwyty zmiany rozmiarów.

- Aby wybrać kontrolki, w [oknie Przybornik](/visualstudio/ide/reference/toolbox)wybierz narzędzie **wskaźnik** i wykonaj jedną z następujących czynności, aby dokonać wyboru:

  - Przeciągnij wskaźnik, aby narysować pole zaznaczenia wokół kontrolek, które chcesz wybrać w oknie dialogowym. Po zwolnieniu przycisku myszy zostaną zaznaczone wszystkie kontrolki wewnątrz i przecinające się pole wyboru.

  - Naciśnij i przytrzymaj klawisz **SHIFT** , a następnie wybierz kontrolki, które chcesz uwzględnić w zaznaczeniu.

  - Naciśnij i przytrzymaj klawisz **Ctrl** , a następnie wybierz kontrolki, które chcesz uwzględnić w zaznaczeniu.

- Aby dodać lub usunąć formant z grupy wybranych kontrolek, przytrzymaj wciśnięty klawisz **SHIFT** i wybierz kontrolkę, którą chcesz dodać lub usunąć.

### <a name="dominant-controls"></a>Kontrolki dominujące

Gdy zmieniasz rozmiar lub wyrównujesz wiele kontrolek, **Edytor okien dialogowych** używa kontrolki dominującej, aby określić, jak inne kontrolki są skalowane lub wyrównane. Domyślnie formant dominujący jest pierwszą wybraną kontrolką.

- Aby określić formant dominujący, przytrzymaj wciśnięty klawisz **Ctrl** i wybierz kontrolkę, której chcesz użyć do zmiany rozmiaru lub lokalizacji *innych kontrolek*. Przytrzymanie klawisza **Ctrl** i wybranie kontrolki w zaznaczeniu spowoduje również kontrolowanie kontrolki dominującej w tym wyborze.

- Aby zmienić formant dominujący, wyczyść bieżące zaznaczenie, zaznaczając poza wszystkimi aktualnie zaznaczonymi kontrolkami i powtórz powyższą procedurę, zaznaczając *najpierw*inną kontrolkę.

> [!NOTE]
> Uchwyty zmiany rozmiarów kontrolki dominującej są trwałe, podczas gdy uchwyty formantów podrzędnych są puste. Wszystkie dalsze zmiany rozmiarów lub wyrównywania opierają się na formancie dominującym.

## <a name="size-controls"></a>Kontrolki rozmiaru

Użyj uchwytów rozmiaru, aby zmienić rozmiar kontrolki. Gdy wskaźnik jest ustawiony na uchwycie zmiany rozmiaru, zmienia kształt, aby wskazać kierunki, w których można zmienić rozmiar kontrolki. Aktywne uchwyty zmiany rozmiaru są trwałe i jeśli uchwyt zmiany rozmiaru jest pusty, nie można zmienić rozmiaru kontrolki wzdłuż tej osi.

- Aby zmienić rozmiar kontrolki, zaznacz kontrolkę i przeciągnij uchwyty rozmiaru w celu zmiany rozmiaru.

  - Uchwyty rozmiaru w górnej części strony zmieniają rozmiar poziomy lub pionowy.

  - Uchwyty rozmiaru w rogach zmieniają się zarówno w poziomie, jak i w pionie.

   > [!TIP]
   > Można zmienić rozmiar kontrolki pojedynczej jednostki okna dialogowego (DLU), trzymając wciśnięty klawisz **SHIFT** i używając klawiszy Strzałka w **prawo** i **w dół** .

- Aby automatycznie dopasować rozmiar formantu do tekstu w nim, przejdź do menu **Format** lub kliknij prawym przyciskiem myszy kontrolkę, a następnie wybierz pozycję **rozmiar do zawartości**.

- Aby kontrolować ten sam rozmiar, wybierz kontrolki, które chcesz zmienić, a następnie przejdź do **formatu**menu  >  **Make Same Size**, a następnie wybierz jedną z **opcji**, **wysokość**lub **Szerokość**.

   Zmiana rozmiaru grupy kontrolek zależy od rozmiaru kontrolki dominującej, która jest wybierana w pierwszej kolejności w serii. Końcowy rozmiar kontrolek w grupie zależy od rozmiaru kontrolki dominującej.

- Aby zmienić rozmiar grupy formantów przy użyciu prowadnic, przyciągnąć po stronie kontrolki (lub kontrolki) do prowadnicy, a następnie przeciągnij prowadnicę do drugiej strony kontrolki (lub kontrolki). Teraz można przenieść dowolny przewodnik, aby zmienić rozmiar kontrolki (lub kontrolek).

   Jeśli jest to konieczne z wieloma kontrolkami, rozmiar każdego z nich można przyciągnąć do drugiego przewodnika.

### <a name="other-controls"></a>Inne kontrolki

Pole kombi można zmienić po dodaniu go do okna dialogowego. Możesz również określić rozmiar pola listy rozwijanej. Aby uzyskać więcej informacji, zobacz [Dodawanie wartości do kontrolki pola kombi](./defining-mnemonics-access-keys.md).

1. Wybierz przycisk strzałki listy rozwijanej z prawej strony pola kombi.

   ![Strzałka w polu kombi w projekcie MFC](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   Kontur kontrolki zmieni się, aby pokazać rozmiar pola kombi z rozszerzonym obszarem listy rozwijanej.

1. Użyj dolnego uchwytu zmiany rozmiaru, aby zmienić początkowy rozmiar obszaru listy rozwijanej.

   ![Wymiarowanie pola&#45;kombi w projekcie MFC](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. Ponownie wybierz strzałkę listy rozwijanej, aby zamknąć część listy rozwijanej pola kombi.

> [!NOTE]
> Po dodaniu pola listy z poziomym paskiem przewijania do okna dialogowego przy użyciu MFC pasek przewijania nie będzie automatycznie wyświetlany w aplikacji.
>
> Ustaw maksymalną szerokość dla najszerszego elementu przez wywołanie [CListBox:: SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent) w kodzie. Bez tego zestawu wartości pasek przewijania nie zostanie wyświetlony, nawet gdy elementy w polu listy są szersze niż pole.

## <a name="align-controls"></a>Wyrównywanie kontrolek

- Aby wyrównać kontrolki, wybierz kontrolki, które chcesz wyrównać. Przejdź do pozycji menu **Format**  >  **Wyrównaj** i wybierz jedno z następujących wyrównania:

   |Wyrównanie|Opis|
   |-----|-----------|
   |**Do lewej**|Wyrównuje zaznaczone kontrolki wzdłuż ich lewej krawędzi.|
   |**Umieszcza**|Wyrównuje zaznaczone kontrolki w poziomie wzdłuż ich punktów centralnych.|
   |**Rights**|Wyrównuje zaznaczone kontrolki wzdłuż odpowiednich stron.|
   |**Krawędzi**|Wyrównuje zaznaczone kontrolki wzdłuż ich górnych krawędzi.|
   |**Dka**|Wyrównuje zaznaczone kontrolki w pionie wzdłuż ich punktów środkowych.|
   |**Do dołu**|Wyrównuje zaznaczone kontrolki wzdłuż ich dolnych krawędzi.|

   Upewnij się, że wybierasz kontrolkę, która ma być pierwszą osobą dominującą, lub ustaw ją jako formant dominujący przed wykonaniem polecenia wyrównania lub zmiany rozmiarów, gdy końcowa pozycja grupy kontrolek zależy od pozycji kontrolki dominującej.

- Aby równomiernie przemieścić kontrolki, wybierz kontrolki, które chcesz zmienić. Przejdź do pozycji **menu**  >  **Space Evenly** , a następnie wybierz jedno z następujących wyrównania odstępów:

   |Odstępy|Opis|
   |---|---|
   |**Całą**|Kontrolki odstępu są równomiernie dostępne między skrajną lewą i prawą wybraną kontrolką.|
   |**W dół**|Kontrolki odstępu są równomiernie dostępne między górną i najniższej zaznaczonej kontrolki.|

- Aby wyśrodkować kontrolki, zaznacz kontrolkę lub kontrolki, które chcesz zmienić. Przejdź do menu **Format**  >  **centrum w oknie dialogowym** , a następnie wybierz jedną z następujących czynności:

   |Szkic|Opis|
   |---|---|
   |**Pionowa**|Wyśrodkuj kontrolki w pionie w oknie dialogowym.|
   |**Układ**|Wyśrodkuj kontrolki w poziomie w oknie dialogowym.|

- Aby wyrównać przyciski push, wybierz jeden lub więcej przycisków wypychania. Przejdź do menu **Format**  >  **Rozmieść przyciski**, a następnie wybierz jedną z następujących czynności:

   |Szkic|Opis|
   |---|---|
   |**Kliknij**|Wyrównuje przyciski push wzdłuż prawej krawędzi okna dialogowego.|
   |**Dolne**|Wyrównuje przyciski push wzdłuż dolnej krawędzi okna dialogowego.|

   Jeśli wybierzesz kontrolkę inną niż przycisk push, jej pozycja nie ma żadnego oddziaływania.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Zarządzanie kontrolkami okien dialogowych](controls-in-dialog-boxes.md)<br/>
[Instrukcje: Dodawanie, edytowanie lub usuwanie kontrolek](adding-editing-or-deleting-controls.md)<br/>
[Instrukcje: definiowanie dostępu i wartości kontroli](defining-mnemonics-access-keys.md)<br/>
