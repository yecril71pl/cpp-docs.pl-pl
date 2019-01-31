---
title: Stany Edytor okien dialogowych (prowadnice i siatki) (C++)
ms.date: 11/04/2016
helpviewer_keywords:
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
ms.assetid: dbacf9ef-e8b0-4125-a7ce-84911c482e98
ms.openlocfilehash: 52fc19d8a39680c16692177e2758fba78afc7d3a
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484997"
---
# <a name="dialog-editor-states-guides-and-grids-c"></a>Stany Edytor okien dialogowych (prowadnice i siatki) (C++)

Można rozmieścić formanty w oknach dialogowych za pomocą **okna dialogowego** edytora w jednym z trzech różnych stanów:

- Prowadnice i marginesy w (ustawienie domyślne)

- Przy użyciu siatki układu w

- Bez żadnych funkcji przyciągania lub wyrównanie

[Paska narzędzi edytora okien dialogowych](../windows/showing-or-hiding-the-dialog-editor-toolbar.md) zawiera przyciski, które sterują stanu. Aby zmienić stan, kliknij odpowiednią ikonę. Możesz również zmienić stany przy użyciu **ustawienia prowadnic** polecenie **Format** menu.

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

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="create-and-set-guides-and-margins"></a>Tworzenie i Ustawianie prowadnic i marginesów

Czy przenosisz się formantów, dodawanie formantów, rozmieszczanie bieżący układ, przewodniki może pomóc można wyrównać formanty dokładnie w oknie dialogowym. Przewodniki są wyświetlane jako niebieskie linie kropkowana w oknie dialogowym wyświetlany w edytorze i odpowiednie strzałki w linijki górnej i lewej strony **okna dialogowego** edytora.

Kiedy tworzysz okno dialogowe, znajdują się cztery marginesy. Marginesy są przewodniki zmodyfikowane, pojawiają się jako niebieskie linie dotted.

### <a name="to-create-a-guide"></a>Aby utworzyć linię

Na linijce kliknij raz, aby utworzyć linię. (Jednym kliknięciem tworzy nowy przewodnik; dwukrotne kliknięcie powoduje uruchomienie **ustawienia prowadnic** okno dialogowe, w którym można określić ustawienia prowadnic.)

### <a name="to-set-a-guide"></a>Aby ustawić przewodnik

W oknie dialogowym kliknij przewodnika, a następnie przeciągnij go do nowej pozycji. (Możesz również kliknij strzałkę w linijkę, aby przeciągnąć skojarzonego przewodnika).

Współrzędne przewodnika są wyświetlane na pasku stanu w dolnej części okna i linijki. Przesuń wskaźnik nad strzałką znajdującą się w linijkę, aby wyświetlić dokładnego położenia przewodnika.

### <a name="to-delete-a-guide"></a>Aby usunąć prowadnicę

Przeciągnij ją z okna dialogowego.

\- lub —

Przeciągnij odpowiednie strzałkę z linijki.

### <a name="to-move-margins"></a>Aby przenieść marginesów

Przeciągnij margines do nowej pozycji.

Aby margines zniknąć, należy przenieść margines do pozycji zero. Aby przywrócić margines, umieść wskaźnik na marginesie pozycji zero i przenieść margines w określonej pozycji.

## <a name="align-controls-on-a-guide"></a>Wyrównywanie kontrolek do prowadnicy

Uchwyty zmiany rozmiaru kontrolek przyciąganie do prowadnic formanty są przenoszone, gdy przewodniki przyciąganie do kontrolek, formanty, nie jest przypięty wcześniej do przewodnika. Po przeniesieniu przewodnik również przenieść formantów, które są wyrównywane do niego. Formanty wyrównywane do więcej niż jeden podręcznik zmieniany jest rozmiar po przeniesieniu jeden z przewodników.

Znaczniki w linijki, określające odstępów przewodniki i formanty są definiowane przez jednostki okna dialogowego (Dlu). DLU opiera się na rozmiar czcionki okno dialogowe, zwykle 8-punktowy MS Shell Dlg. Poziomy DLU jest średniej szerokości czcionki okno dialogowe podzielona przez cztery. DLU pionowe jest średnią wysokość czcionki podzielić przez 8.

### <a name="to-size-a-group-of-controls-with-guides"></a>Rozmiar grupy formantów z liniami

1. Przyciągaj obok kontrolki (lub formantów) do przewodnika.

1. Przeciągnij przewodnika po drugiej stronie kontrolki (lub kontrolki).

   Jeśli to konieczne z wieloma formantami, rozmiar każdego przyciągane do prowadnicy drugiego.

1. Przenieś albo przewodnika, aby rozmiar kontrolki (lub kontrolki).

### <a name="to-change-the-intervals-of-the-tick-marks"></a>Aby zmienić interwałów znaczników

1. Z **Format** menu, wybierz **ustawienia prowadnic**.

1. W **ustawienia prowadnic** dialogowym **odstępy między liniami siatki** określ nową wysokość i szerokość w Dlu.

## <a name="disable-guides"></a>Wyłączanie prowadnic

Klawisze specjalne w połączeniu z myszy umożliwia wyłączanie przyciągania efekt prowadnice. Za pomocą **Alt** klucz wyłącza przyciągania skutki przewodnik wybrane. Przenoszenie Przewodnik z **Shift** klucz uniemożliwia przyciągniętą posuwał się z przewodnikiem.

### <a name="to-disable-the-snapping-effect-of-the-guides"></a>Aby wyłączyć przyciąganie efekt prowadnice

Przeciągnij formant, przytrzymując naciśnięty **Alt** klucza.

### <a name="to-move-guides-without-moving-the-snapped-controls"></a>Aby przenieść przewodniki bez przenoszenia przyciągniętą

Przeciągnij przewodnika, przytrzymując naciśnięty **Shift** klucza.

### <a name="to-turn-off-the-guides"></a>Aby wyłączyć prowadnice

1. Z **Format** menu, wybierz **ustawienia prowadnic**.

1. W **ustawienia prowadnic** dialogowego **prowadnic układu**, wybierz opcję **Brak**.

   > [!NOTE]
   > Możesz także dwukrotnie kliknąć na pasku linijkę, aby uzyskać dostęp do **ustawienia prowadnic** okno dialogowe.

\- lub —

Na **Format** menu, wybierz opcję **Przełącz prowadnice**.

## <a name="modify-the-layout-grid"></a>Modyfikowanie siatki układu

Podczas wprowadzania lub rozmieszczanie formantów w oknie dialogowym, można użyć siatki układu do bardziej precyzyjne pozycjonowania. Po włączeniu siatki "przyciągane do" linii kropkowanej siatki tak, jakby namagnesować pojawiają się formanty. Możesz włączyć tę funkcję "przyciągania do siatki" i wyłączyć i zmienianie rozmiaru komórek siatki układu.

### <a name="to-turn-the-layout-grid-on-or-off"></a>Aby włączyć siatki układu lub wyłączyć

1. Z **Format** menu, wybierz **ustawienia prowadnic**.

1. W **ustawienia prowadnic** okno dialogowe, zaznacz lub wyczyść **siatki** przycisku.

   Możesz nadal kontrolować siatki w poszczególnych **okna dialogowego** okna edytora za pomocą **Przełącz siatkę** znajdujący się na [paska narzędzi edytora okien dialogowych](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

### <a name="to-change-the-size-of-the-layout-grid"></a>Aby zmienić rozmiar siatki układu

1. Z **Format** menu, wybierz **ustawienia prowadnic**.

1. W **ustawienia prowadnic** okna dialogowego wpisz wysokość i szerokość w Dlu komórek w siatce. Minimalna wysokość lub szerokość jest Dlu 4. Aby uzyskać więcej informacji na temat Dlu, zobacz [rozmieszczenie kontrolek w oknach dialogowych](../windows/arrangement-of-controls-on-dialog-boxes.md).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)<br/>
[Kontrolki (MFC)](../mfc/controls-mfc.md)<br/>
