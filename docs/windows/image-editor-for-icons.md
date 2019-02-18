---
title: Edytor obrazów dla ikon (C++)
ms.date: 02/15/2019
f1_keywords:
- vc.editors.cursor.F1
- vc.editors.icon.F1
- vc.editors.cursor
- vc.editors.bitmap.F1
- vc.editors.bitmap
- vc.editors.dialog.GridSettings
- vc.editors.gridsettings
- vc.editors.bitmap
- vc.editors.icon
- vc.editors.texttool
- vc.editors.bitmap
- vc.editors.icon
helpviewer_keywords:
- editors, images
- resource editors [C++], graphics
- Image editor [C++]
- resource editors [C++], Image editor
- Image menu
- Grid Settings dialog box [C++]
- Graphics toolbar
- Image editor [C++], toolbar
- Image editor [C++], Option selector
- Properties window
- Option selector, Image editor
- toolbars [C++], showing
- toolbars [C++], hiding
- text, adding to an image
- Text Tool dialog box [C++]
- Text Tool Font dialog box [C++]
- fonts, changing on an image
- text, on images
- graphics editor [C++]
- Image editor [C++], panes
- Image editor [C++], magnification
- grids, pixel
- pixel grid, Image editor
- Image editor [C++], pixel grid
- Image editor [C++], grid settings
- grid settings, Image editor
ms.assetid: 586d2b8b-0348-4883-a85d-1ff0ddbf14dd
ms.openlocfilehash: 782462a4aeba72252c4d6043bd192f6892a3966f
ms.sourcegitcommit: 24592ba0a38c7c996ffd3d55fe1024231a59ccc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2019
ms.locfileid: "56336582"
---
# <a name="image-editor-for-icons-c"></a>Edytor obrazów dla ikon (C++)

Po kliknięciu pliku obrazu (na przykład .ico, bmp, PNG) w Eksploratorze rozwiązań obraz, który zostanie otwarty w edytorze obrazu w taki sam sposób, który otwartych plików kodu w edytorze kodu. Gdy karta edytora obrazów jest aktywna, zostanie wyświetlony pasków narzędzi za pomocą wielu narzędzi do tworzenia i edycji obrazów. Wraz z map bitowych, ikon i kursorów można edytować obrazy w formacie GIF lub JPEG przy użyciu poleceń w **obraz** menu i narzędzi na **edytora obrazów** paska narzędzi.

Zasoby graficzne są obrazy, które należy zdefiniować dla aplikacji. Można narysować freehand lub rysowanie przy użyciu kształtów. Możesz wybrać części obrazu dla edycji lub zmiana rozmiaru i odbijanie lub można utworzyć niestandardowy obiekt brush z wybranej części obrazu i rysowanie za pomocą tego pędzla. Można zdefiniować właściwości obrazu, zapisać obrazy w różnych formatach i konwertowania obrazów z jednego formatu na inny.

Oprócz tworzenia nowych zasobów graficznych, możliwe jest również [importowanie istniejących obrazów](../windows/how-to-import-and-export-resources.md) do edycji i dodać je do projektu. Możesz również otworzyć i edycji obrazów, które nie są częścią projektu dla [edycji obrazów autonomicznej](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md).

> [!NOTE]
> Za pomocą **edytora obrazów**, można wyświetlać obrazy 32-bitowe, ale nie można ich edytować.

Możliwości Edytora obrazów:

- [Praca z kolorami](../windows/working-with-color-image-editor-for-icons.md)

- [Praca z ikony i kursory: Zasoby obrazów do wyświetlania na urządzeniach](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)

- [Korzystanie z klawiszy skrótów dla poleceń edytora obrazów](../windows/accelerator-keys-image-editor-for-icons.md)

**Edytora obrazów** okna wyświetla dwa widoki obrazu, pasek podziału rozdziela dwa okienka. Aby zmieniać względne rozmiary okienek, można przeciągać pasek podziału. Aktywne okienko wyświetla krawędź wyboru.

**Edytora obrazów** okna mogą być dostosowane do potrzeb i preferencji. Możesz [zmienić stopień powiększenia](../windows/changing-the-magnification-factor-image-editor-for-icons.md) i [wyświetlić lub ukryć siatkę pikseli](../windows/displaying-or-hiding-the-pixel-grid-image-editor-for-icons.md).

> [!NOTE]
> Za pomocą **edytora obrazów**, można wyświetlać obrazy 32-bitowe, ale nie można ich edytować.

## <a name="image-menu"></a>Menu obrazu

**Obraz** menu, która jest wyświetlana tylko wtedy, gdy **obraz** edytora jest aktywny, zawiera polecenia służące do edycji obrazów, zarządzanie palety kolorów i ustawienie **edytora obrazów** okna Opcje. Ponadto polecenia narzędzia obrazach urządzeń są dostępne podczas pracy z ikony i kursory.

|Polecenie|Opis|
|---|---|
|**Odwróć kolory**|Odwraca kolory. Aby uzyskać więcej informacji, zobacz [odwracanie kolorów w wyborze](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md).|
|**Przerzuć w poziomie**|Przerzuca obraz lub zaznaczenie w poziomie. Aby uzyskać więcej informacji, zobacz [Przerzucanie obrazu](../windows/flipping-an-image-image-editor-for-icons.md).|
|**Przerzuć w pionie**|Przerzuca obraz lub zaznaczenie w pionie. Aby uzyskać więcej informacji, zobacz [Przerzucanie obrazu](../windows/flipping-an-image-image-editor-for-icons.md).|
|**Obrót o 90 stopni**|Obraca obraz lub zaznaczenie o 90 stopni. Aby uzyskać więcej informacji, zobacz [Przerzucanie obrazu](../windows/flipping-an-image-image-editor-for-icons.md).|
|**Pokaż okno kolorów**|Otwiera [okno kolorów](../windows/colors-window-image-editor-for-icons.md), w którym możesz wybrać kolory używane dla obrazu. Aby uzyskać więcej informacji, zobacz [Praca z kolorem](../windows/working-with-color-image-editor-for-icons.md).|
|**Użyj zaznaczenia jako pędzla**|Umożliwia tworzenie pędzla niestandardowego na podstawie część obrazu. Wybór staje się pędzla niestandardowego, który rozdziela kolorów w wyborze między obrazu. Kopiuje zaznaczenie są pozostawiane w ścieżce przeciągania. Przeciągniesz wolniej, większej liczby kopii zostały wprowadzone. Aby uzyskać więcej informacji, zobacz [Tworzenie pędzla niestandardowego](../windows/creating-a-custom-brush-image-editor-for-icons.md).|
|**Kopiuj i wybór konspektu**|Tworzy kopię bieżącego zaznaczenia i zakreśla ją. Jeśli kolor tła znajduje się w bieżącym zaznaczeniu, będzie on wykluczony, jeśli masz [przezroczyste](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md) wybrane.
|**Adjust Colors**|Otwiera [selektor kolorów niestandardowych](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md), co pozwala dostosować kolory używane dla obrazu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie lub zmiana kolorów](../windows/customizing-or-changing-colors-image-editor-for-icons.md).|
|**Załaduj paletę**|Otwiera [Załaduj paletę kolorów, okno dialogowe](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md), co umożliwia ładowanie kolorów palety wcześniej zapisane w pliku .pal.|
|**Zapisz paletę**|Zapisuje w pliku .pal kolorów palety.|
|**Rysuj nieprzezroczyste**|Po wybraniu sprawia, że bieżące zaznaczenie nieprzezroczystości. Po wyczyszczeniu, sprawia, że bieżące zaznaczenie przezroczyste. Aby uzyskać więcej informacji, zobacz [wybierania nieprzezroczyste lub przezroczyste tło](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).|
|**Edytor paska narzędzi**|Otwiera [okno dialogowe Nowy zasób paska narzędzi](../windows/new-toolbar-resource-dialog-box.md).|
|**Ustawienia siatki**|Otwiera **ustawienia siatki** okno dialogowe, w którym można określić siatki dla obrazu.|
|**Nowy typ obrazu**|Otwiera [New \<urządzenia > okno dialogowe typu obrazu](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md). Zasób pojedyncza ikona może zawierać kilka obrazów o różnych rozmiarach i system windows może używać rozmiar odpowiednią ikonę w zależności od tego, w jaki sposób będzie mają być wyświetlane. Nowy typ urządzenia nie modyfikuje rozmiar ikony, ale raczej tworzy nowy obraz w ramach ikony. Dotyczy tylko ikony i kursory.|
|**Bieżący typ obrazu ikony/kursora**|Spowoduje otwarcie podmenu zawierającego pierwszy dostępnych kursorem lub ikonę obrazów (dziewięć pierwszy). Ostatnie polecenie, w podmenu, **więcej...** , otwiera [Otwórz \<urządzenia > okno dialogowe obrazu](../windows/open-device-image-dialog-box-image-editor-for-icons.md).|
|**Usuń typ obrazu**|Usuwa obraz wybranego urządzenia.|
|**Narzędzia**|Uruchamia podmenu, który zawiera wszystkie dostępne narzędzia [paska narzędzi edytora obrazów](../windows/toolbar-image-editor-for-icons.md).|

**Ustawienia siatki** okno dialogowe umożliwia określenie ustawienia siatki dla obrazu i prezentuje linie siatki edytowanego obrazu. Wiersze są przydatne w przypadku edycji obrazu, ale nie są zapisywane jako część samego obrazu.

|Właściwość|Opis|
|---|---|
|**Siatka pikseli**|Po zaznaczeniu tej opcji, wyświetla siatkę wokół każdego piksela w edytorze obrazu. Siatka pojawia się tylko na 4 x i wyższych rozdzielczościach.|
|**Siatka**|Po wybraniu Wyświetla siatkę wokół bloki pikseli w edytorze obrazu, określony przez wartości odstępy siatki.|
|**Szerokość**|Określa szerokość każdy blok kafelka. Ta właściwość jest przydatna, gdy mapy bitowe zawierające wiele obrazów, które są rozmieszczone w regularnych odstępach czasu.|
|**Wysokość**|Określa wysokość każdego bloku kafelka. Ta właściwość jest przydatna, gdy mapy bitowe zawierające wiele obrazów, które są rozmieszczone w regularnych odstępach czasu.|

## <a name="toolbar"></a>Pasek narzędzi

**Edytora obrazów** narzędzi zawiera narzędzia do rysowania, rysowania, wprowadzania tekstu, wymazywanie i manipulowanie widoków. Zawiera ona także Selektor opcji, za pomocą którego można wybrać opcje dotyczące korzystania z poszczególnych narzędzi. Na przykład można wybierać różne szerokość pędzla, czynniki powiększenia i style linii.

> [!NOTE]
> Wszystkie narzędzia dostępne na **edytora obrazów** narzędzi są także dostępne z **obraz** menu (w obszarze **narzędzia** polecenie).

![Pasek narzędzi edytora obrazów](../mfc/media/vcimageeditortoolbar.gif "vcImageEditorToolbar") paska narzędzi edytora obrazów

Aby użyć **edytora obrazów** narzędzi i **opcji** selektor, wybierz narzędzie lub opcji, które mają.

> [!TIP]
> Etykietki narzędzi są wyświetlane po umieszczeniu kursora na przycisku paska narzędzi. Poniższe wskazówki mogą pomóc w identyfikacji funkcji każdego przycisku.

Za pomocą **opcji** selektor można określić szerokość linii, pociągnięć i nie tylko. Ikony na **opcji** selektor przycisk zmiany, w zależności od narzędzie, które zostały wybrane.

![Rysowanie&#45;selektor kształt na pasku narzędzi edytora obrazów](../mfc/media/vcimageeditortoolbaroptionselector.gif "vcImageEditorToolbarOptionSelector") Selektor opcji na pasku narzędzi edytora obrazów

### <a name="use-the-text-tool-dialog-box"></a>Użyj okna dialogowego narzędzie tekstowe

Użyj **narzędzie tekstowe** okno dialogowe, aby dodać tekst do kursora, mapa bitowa lub ikona zasobu.

Aby uzyskać dostęp do tego okna dialogowego, otwórz [edytora obrazów](../windows/window-panes-image-editor-for-icons.md). Wybierz **narzędzia** z **obraz** menu, a następnie wybierz pozycję **narzędzie tekstowe** polecenia.

#### <a name="font-button"></a>Przycisk Czcionka

Otwiera **narzędzie czcionki tekstu** okno dialogowe, w którym można zmienić czcionki, styl i rozmiar czcionki kursora. Zmiany są stosowane do tekstu wyświetlanego w **tekstu** obszaru.

Aby otworzyć to okno dialogowe, wybierz **czcionki** znajdujący się w **narzędzie tekstowe** okno dialogowe. Są dostępne właściwości:

|Właściwość|Opis|
|---|---|
|**Czcionka**|Wyświetla listę dostępnych czcionek.|
|**Styl czcionki**|Wyświetla listę dostępnych stylów określonej czcionki.|
|**Rozmiar**|Wyświetla listę dostępnych rozmiarów określonej czcionki.|
|**Próbki**|Pokazuje przykładowy wygląd tekstu przy użyciu ustawień określonej czcionki.|
|**Skrypt**|Wyświetla listę dostępnych skryptów językowych dla określonej czcionki. Po wybraniu inny język skryptu, zestawu znaków języka i udostępnieniu do tworzenia dokumentów w wielu języków.|

Zmiana czcionki tekstu obrazu:

Poniższa procedura to przykład sposobu dodawania tekstu do ikony w aplikacji Windows i manipulowania czcionkę tekstu.

1. Tworzenie aplikacji formularzy Windows w języku C++. Aby uzyskać więcej informacji, zobacz [Tworzenie projektu aplikacji Windows](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5). *App.ico* plik zostanie dodany do projektu, domyślnie.

1. W **Eksploratora rozwiązań**, kliknij dwukrotnie plik *app.ico*. [Edytora obrazów](../windows/image-editor-for-icons.md) zostanie otwarty.

1. Z **obraz** menu, wybierz opcję **narzędzia** , a następnie wybierz **narzędzie tekstowe**. **Narzędzie tekstowe** zostanie wyświetlone okno dialogowe.

1. W **narzędzie tekstowe** okno dialogowe, typ *C++* w obszarze pusty tekst. Ten tekst będzie wyświetlany w polu o zmiennym rozmiarze, znajduje się w lewym górnym rogu *app.ico*w **edytora obrazów**.

1. W **edytora obrazów**, przeciągnij pole o zmiennych rozmiarach do środka app.ico można zwiększyć czytelność tekstu.

1. W **narzędzie tekstowe** okno dialogowe, wybierz opcję **czcionki** przycisku. **Narzędzie czcionki tekstu** zostanie wyświetlone okno dialogowe.

1. W **narzędzie czcionki tekstu** okno dialogowe, wybierz opcję **podzbiory** z listy dostępnych czcionek, które są wymienione w **czcionki** pola listy.

1. Wybierz **Bold** z listy dostępnych style na liście **styl czcionki** pola listy.

1. Wybierz **10** z listy dostępnych punktów rozmiarów wymienionych w **rozmiar** pola listy.

1. Wybierz przycisk **OK**. **Narzędzie czcionki tekstu** okno dialogowe zostanie zamknięte i nowe ustawienia czcionek będą stosowane do tekstu.

1. Wybierz **Zamknij** znajdujący się na **narzędzie tekstowe** okno dialogowe. Pole o zmiennym rozmiarze wokół tekstu zniknie z **edytora obrazów**.

#### <a name="text-area"></a>Obszar tekstu

Wyświetla tekst, który pojawia się jako część zasobu. Ten obszar jest początkowo pusta.

> [!NOTE]
> Jeśli **przezroczyste tło** jest ustawiona tylko tekst, zostaną umieszczone w obrazie. Jeśli **tło nieprzezroczyste** ustawiono prostokąt otaczający wypełnione [kolor tła](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md), zostaną umieszczone za tekstem. Aby uzyskać więcej informacji, zobacz [wybierając nieprzezroczystych i tło przezroczyste](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

Kliknięciu prawym przyciskiem myszy **narzędzie tekstowe** okno dialogowe, aby dostęp do menu skrótów domyślne, które zawiera listę standardowych poleceń Windows.

### <a name="to-display-or-hide-the-image-editor-toolbar"></a>Aby wyświetlić lub ukryć pasek narzędzi edytora obrazów

Ponieważ wiele narzędzi do rysowania są dostępne z [klawiatury](../windows/accelerator-keys-image-editor-for-icons.md), warto czasami Ukryj **edytora obrazów** paska narzędzi.

Na **widoku** menu, wybierz opcję **pasków narzędzi** wybierz **edytora obrazów**.

   > [!NOTE]
   > Elementy z tego paska narzędzi pojawi się niedostępne, gdy plik obrazu z bieżącego projektu lub rozwiązania nie jest otwarty w **edytora obrazów**. Zobacz [Tworzenie ikony lub innego obraz](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md), aby uzyskać informacje dotyczące dodawania plików obrazów do swoich projektów.

## <a name="window-panes"></a>Okienka

**Edytora obrazów** okna zwykle wyświetla obraz na dwa okienka rozdzielone pasek podziału. Jeden widok jest rzeczywisty rozmiar, a druga powiększenia (domyślny współczynnik rozszerzenia jest 6). Widoki te dwa okienka są automatycznie aktualizowane: zmiany wprowadzone w jednym okienku natychmiast są wyświetlane w innym. Dwa okienka ułatwiają pracować nad powiększania widoku obrazu, w którym można odróżnić poszczególnych pikseli i, w tym samym czasie obserwować wpływ swoją pracę na widoku rzeczywisty rozmiar obrazu.

Tyle miejsca, ile potrzeba korzysta z okienka po lewej stronie (do połowy **obraz** okna) do wyświetlenia widoku powiększeniem 1:1 (opcja domyślna) obrazu. W okienku po prawej stronie wyświetla powiększonego (6:1 powiększenie domyślnie). Możesz zmienić powiększenia w każdym za pomocą okienka **Magnify** narzędzie [paska narzędzi edytora obrazów](../windows/toolbar-image-editor-for-icons.md) lub za pomocą klawiszy skrótów.

Można powiększyć mniejszych okienku **edytora obrazów** okno i użyj dwa okienka, aby pokazać różnych regionach duży obraz. Wybierz w okienku, aby ją wybrać.

Względne rozmiary okienek można zmienić, ustawiając kursor na pasek podziału i przenoszenie pasek podziału w prawo lub lewo. Pasek podziału można przenieść do dowolnej stronie, aby pracować nad tylko jedno okienko.

Jeśli **edytora obrazów** okienko jest powiększony o 4 lub nowszej, może wyświetlić siatkę pikseli, ograniczającego piksele na obrazie.

### <a name="to-change-the-magnification-factor"></a>Aby zmienić stopień powiększenia

Domyślnie **obraz** wyświetlania widoku w okienku po lewej stronie w rzeczywistym rozmiarze w edytorze i widok, w okienku po prawej stronie 6 razy rzeczywisty rozmiar. Współczynnika powiększenia (widoczny na pasku stanu w dolnej części obszaru roboczego) jest stosunek między rzeczywisty rozmiar obrazu i wyświetlany rozmiar. Domyślny współczynnik wynosi 6 i zakres jest z zakresu od 1 do 10.

1. Wybierz **edytora obrazów** okienko współczynnika powiększenia, którego chcesz zmienić.

1. Na [paska narzędzi edytora obrazów](../windows/toolbar-image-editor-for-icons.md), wybierz strzałkę po prawej stronie [narzędzie Powiększenie](../windows/toolbar-image-editor-for-icons.md) i wybierz współczynnika powiększenia z podmenu: **1 X**, **2 X**, **6 X**, lub **8 X**.

   > [!NOTE]
   > Aby wybrać współczynnika powiększenia, inne niż te wymienione w **Magnify** narzędzie, korzystanie z klawiszy skrótów.

### <a name="to-display-or-hide-the-pixel-grid"></a>Aby wyświetlić lub ukryć siatkę pikseli

Dla wszystkich **edytora obrazów** okienka przy użyciu współczynnika powiększenia 4 lub większą, można wyświetlić siatkę ograniczającego piksele na obrazie.

1. Na **obraz** menu, wybierz opcję **ustawienia siatki**.

1. Wybierz **siatkę pikseli** pole wyboru, aby wyświetlić siatkę, lub wyczyść pole, aby ukryć siatkę.

> [!TIP]
> Etykietki narzędzi są wyświetlane po umieszczeniu kursora na przycisku paska narzędzi. Poniższe wskazówki mogą pomóc w identyfikacji funkcji każdego przycisku.

## <a name="visual-studio-image-library"></a>Biblioteka obrazów programu Visual Studio

Możesz pobrać bezpłatnie **Visual Studio Image Library** zawierającą wiele animacji, bitmap i ikon, których można używać w aplikacjach. Aby uzyskać więcej informacji dotyczących sposobu pobierania biblioteki, zobacz [Biblioteka programu Visual Studio obraz](/visualstudio/designers/the-visual-studio-image-library).

## <a name="managed-resources"></a>Zarządzane zasoby

Możesz użyć **obraz** edytora i [edytorze binarnym](binary-editor.md) do pracy z plikami zasobów w projektach zarządzanych. Wszelkie zarządzane zasoby, które chcesz edytować, muszą być powiązanymi zasobami. Edytory zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych.

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Edytory zasobów](../windows/resource-editors.md)<br/>
[Ikony](https://msdn.microsoft.com/library/windows/desktop/ms646973.aspx)