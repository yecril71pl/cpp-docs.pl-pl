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
ms.openlocfilehash: c411c4b95fcd3866c897f04b70da7cbb2b48ba28
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66504319"
---
# <a name="image-editor-for-icons-c"></a>Edytor obrazów dla ikon (C++)

Po wybraniu pliku obrazu (na przykład .ico, bmp, PNG) w **Eksploratora rozwiązań**, obraz, który zostanie otwarty w **edytora obrazów** w kodu pliki otwarte w taki sam sposób **Edytor kodu** . Gdy **edytora obrazów** karta jest aktywna, zostanie wyświetlony pasków narzędzi za pomocą wielu narzędzi do tworzenia i edycji obrazów. Wraz z map bitowych, ikon i kursorów można edytować obrazy w formacie GIF lub JPEG przy użyciu poleceń w **obraz** menu i narzędzi na **edytora obrazów** paska narzędzi.

Zasoby graficzne są obrazy, które należy zdefiniować dla aplikacji. Można narysować freehand lub rysowanie przy użyciu kształtów. Możesz wybrać części obrazu dla edycji lub zmiana rozmiaru i odbijanie lub można utworzyć niestandardowy obiekt brush z wybranej części obrazu i rysowanie za pomocą tego pędzla. Można zdefiniować właściwości obrazu, zapisać obrazy w różnych formatach i konwertowania obrazów z jednego formatu na inny.

> [!NOTE]
> Za pomocą **edytora obrazów**, można wyświetlać obrazy 32-bitowe, ale nie można ich edytować.

Można również użyć **edytora obrazów** i [Edytor plików binarnych](binary-editor.md) do pracy z plikami zasobów w projektach zarządzanych. Wszelkie zarządzane zasoby, które chcesz edytować, muszą być powiązanymi zasobami. Edytory zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych.

Oprócz tworzenia nowych zasobów graficznych, możliwe jest również [importowanie istniejących obrazów](../windows/how-to-copy-resources.md#import-and-export-resources) do edycji i dodać je do projektu. Możesz również otworzyć i edycji obrazów, które nie są częścią projektu dla [edycji obrazów autonomicznej](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md).

Instrukcje dotyczące **edytora obrazów**, zobacz instrukcje [Tworzenie ikony lub innego obrazu](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md), [edytować obraz](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md), [Użyj narzędzia do rysowania](../windows/using-a-drawing-tool-image-editor-for-icons.md), [Praca z kolorami](../windows/working-with-color-image-editor-for-icons.md), i [klawiszy](../windows/accelerator-keys-image-editor-for-icons.md).

> [!NOTE]
> Pobierz bezpłatnie **Visual Studio Image Library** zawierającą wiele animacji, bitmap i ikon, których można używać w aplikacjach. Aby uzyskać więcej informacji dotyczących sposobu pobierania biblioteki, zobacz [Visual Studio Image Library](/visualstudio/designers/the-visual-studio-image-library).

## <a name="image-menu"></a>Menu obrazu

**Obraz** menu, która jest wyświetlana tylko wtedy, gdy **edytora obrazów** jest aktywna, zawiera polecenia służące do edycji obrazów, zarządzanie palety kolorów i ustawienie **edytora obrazów** okna Opcje. Ponadto polecenia narzędzia obrazach urządzeń są dostępne podczas pracy z ikony i kursory.

|Polecenie|Opis|
|---|---|
|**Odwróć kolory**|Odwraca kolory.|
|**Przerzuć w poziomie**|Przerzuca obraz lub zaznaczenie w poziomie.|
|**Przerzuć w pionie**|Przerzuca obraz lub zaznaczenie w pionie.|
|**Obrót o 90 stopni**|Obraca obraz lub zaznaczenie o 90 stopni.|
|**Pokaż okno kolorów**|Otwiera **kolory** okna, w którym można wybrać kolory używane dla obrazu.|
|**Użyj zaznaczenia jako pędzla**|Umożliwia tworzenie pędzla niestandardowego na podstawie część obrazu.<br/><br/>Wybór staje się pędzla niestandardowego, który rozdziela kolorów w wyborze między obrazu. Kopiuje zaznaczenie są pozostawiane w ścieżce przeciągania. Przeciągniesz wolniej, większej liczby kopii zostały wprowadzone.|
|**Kopiuj i wybór konspektu**|Tworzy kopię bieżącego zaznaczenia i zakreśla ją.<br/><br/>Jeśli kolor tła znajduje się w bieżącym zaznaczeniu, będzie on wykluczony, jeśli masz przezroczyste wybrane.
|**Adjust Colors**|Otwiera **selektor kolorów niestandardowych**, co pozwala dostosować kolory używane dla obrazu.|
|**Załaduj paletę**|Otwiera **Załaduj paletę kolorów** okno dialogowe, które umożliwia ładowanie kolorów palety wcześniej zapisane w pliku .pal.|
|**Zapisz paletę**|Zapisuje w pliku .pal kolorów palety.|
|**Rysuj nieprzezroczyste**|Po wybraniu sprawia, że bieżące zaznaczenie nieprzezroczystości.<br/><br/>Po wyczyszczeniu, sprawia, że bieżące zaznaczenie przezroczyste.|
|**Edytor paska narzędzi**|Otwiera [okno dialogowe Nowy zasób paska narzędzi](../windows/new-toolbar-resource-dialog-box.md).|
|**Ustawienia siatki**|Otwiera **ustawienia siatki** okno dialogowe, w którym można określić siatki dla obrazu.|
|**Nowy typ obrazu**|Otwiera [New \<urządzenia > okno dialogowe typu obrazu](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md).<br/><br/>Zasób pojedyncza ikona może zawierać kilka obrazów o różnych rozmiarach i system windows może używać rozmiar odpowiednią ikonę w zależności od tego, w jaki sposób będzie mają być wyświetlane. Nowy typ urządzenia nie modyfikuje rozmiar ikony, ale raczej tworzy nowy obraz w ramach ikony. Dotyczy tylko ikony i kursory.|
|**Bieżący typ obrazu ikony/kursora**|Zostanie otwarty podmenu zawiera listę pierwszych dziewięciu dostępne obrazy kursorem lub ikonę. Ostatnie polecenie, w podmenu, **więcej**, otwiera [Otwórz \<urządzenia > okno dialogowe obrazu](../windows/open-device-image-dialog-box-image-editor-for-icons.md).|
|**Usuń typ obrazu**|Usuwa obraz wybranego urządzenia.|
|**Narzędzia**|Uruchamia podmenu, który zawiera wszystkie dostępne narzędzia **edytora obrazów** paska narzędzi.|

**Ustawienia siatki** okno dialogowe umożliwia określenie ustawienia siatki dla obrazu i prezentuje linie siatki edytowanego obrazu. Wiersze są przydatne w przypadku edycji obrazu, ale nie są zapisywane jako część samego obrazu.

|Właściwość|Opis|
|---|---|
|**Siatka pikseli**|Po zaznaczeniu tej opcji, wyświetla siatkę wokół każdego piksela **edytora obrazów**.<br/><br/>Siatka pojawia się tylko na 4 x i wyższych rozdzielczościach.|
|**Siatka**|Po wybraniu Wyświetla siatkę wokół bloki pikseli **edytora obrazów**, określony przez wartości odstępy siatki.|
|**Szerokość**|Określa szerokość każdy blok kafelka.<br/><br/>Ta właściwość jest przydatna, gdy mapy bitowe zawierające wiele obrazów, które są rozmieszczone w regularnych odstępach czasu.|
|**Wysokość**|Określa wysokość każdego bloku kafelka.<br/><br/>Ta właściwość jest przydatna, gdy mapy bitowe zawierające wiele obrazów, które są rozmieszczone w regularnych odstępach czasu.|

## <a name="toolbar"></a>Pasek narzędzi

**Edytora obrazów** narzędzi zawiera narzędzia do rysowania, rysowania, wprowadzania tekstu, wymazywanie i manipulowanie widoków. Zawiera ona także Selektor opcji, za pomocą którego można wybrać opcje dotyczące korzystania z poszczególnych narzędzi. Na przykład można wybierać różne szerokość pędzla, czynniki powiększenia i style linii.

Wszystkie narzędzia dostępne na **edytora obrazów** narzędzi są również dostępne z menu **obraz** > **narzędzia**. Aby użyć **edytora obrazów** narzędzi i **opcji** selektor, wybierz narzędzie lub opcji, które mają.

![Pasek narzędzi edytora obrazów](../mfc/media/vcimageeditortoolbar.gif "vcImageEditorToolbar")<br/>
**Edytor obrazów** paska narzędzi

> [!TIP]
> Etykietki narzędzi są wyświetlane po umieszczeniu kursora na przycisku paska narzędzi. Poniższe wskazówki mogą pomóc w identyfikacji funkcji każdego przycisku.

Ponieważ wiele narzędzi do rysowania są dostępne z [klawiatury](../windows/accelerator-keys-image-editor-for-icons.md), warto czasami Ukryj **edytora obrazów** paska narzędzi.

- Aby wyświetlić lub ukryć **edytora obrazów** narzędzi, przejdź do menu **widoku** > **pasków narzędzi** i wybierz polecenie **edytora obrazów**.

> [!NOTE]
> Elementy z tego paska narzędzi pojawi się niedostępne, gdy plik obrazu z bieżącego projektu lub rozwiązania nie jest otwarty w **edytora obrazów**.

### <a name="option-selector"></a>selektor opcji

Za pomocą **opcji** selektor można określić szerokość linii, pociągnięć i nie tylko. Ikony na **opcji** selektor przycisk zmiany, w zależności od narzędzie, które zostały wybrane.

![Rysowanie&#45;selektor kształt na pasku narzędzi edytora obrazów](../mfc/media/vcimageeditortoolbaroptionselector.gif "vcImageEditorToolbarOptionSelector")<br/>
**Opcja** selektor na **edytora obrazów** paska narzędzi

### <a name="text-tool"></a>Narzędzie tekstowe

Użyj **narzędzie tekstowe** okno dialogowe, aby dodać tekst do kursora, mapa bitowa lub ikona zasobu.

Aby uzyskać dostęp do tego okna dialogowego, otwórz **edytora obrazów** i przejdź do menu **obraz** > **narzędzia**, a następnie wybierz **narzędzie tekstowe** polecenie.

> [!TIP]
> Kliknięciu prawym przyciskiem myszy **narzędzie tekstowe** okno dialogowe, aby dostęp do menu skrótów domyślne, które zawiera listę standardowych poleceń Windows.

Otwórz **narzędzie czcionki tekstu** okno dialogowe, aby zmienić czcionkę, styl lub rozmiar czcionki kursora. Zmiany są stosowane do tekstu wyświetlanego w **tekstu** obszaru.

Aby otworzyć to okno dialogowe, wybierz **czcionki** znajdujący się w **narzędzie tekstowe** okno dialogowe. Są dostępne właściwości:

|Właściwość|Opis|
|---|---|
|**Czcionka**|Wyświetla listę dostępnych czcionek.|
|**Styl czcionki**|Wyświetla listę dostępnych stylów określonej czcionki.|
|**Rozmiar**|Wyświetla listę dostępnych rozmiarów określonej czcionki.|
|**Próbki**|Pokazuje przykładowy wygląd tekstu przy użyciu ustawień określonej czcionki.|
|**Skrypt**|Wyświetla listę dostępnych skryptów językowych dla określonej czcionki.<br/><br/>Po wybraniu inny język skryptu, zestawu znaków języka i udostępnieniu do tworzenia dokumentów w wielu języków.|

#### <a name="to-change-the-font-of-text-on-an-image"></a>Zmiana czcionki tekstu obrazu

Poniżej przedstawiono przykładowy sposób dodawania tekstu do ikony w aplikacji Windows i manipulowania czcionkę tekstu.

1. Tworzenie aplikacji formularzy Windows w języku C++. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie aplikacji z formularzem Windows](/previous-versions/visualstudio/visual-studio-2008/s69bf10x(v%3dvs.90)). *App.ico* plik zostanie dodany do projektu, domyślnie.

1. W **Eksploratora rozwiązań**, kliknij dwukrotnie plik *app.ico*. **Edytora obrazów** zostanie otwarty.

1. Przejdź do menu **obraz** > **narzędzia** i wybierz **narzędzie tekstowe**.

1. W **narzędzie tekstowe** okno dialogowe, typ *C++* w obszarze pusty tekst. Ten tekst będzie wyświetlany w polu o zmiennym rozmiarze, znajduje się w lewym górnym rogu *app.ico* w **edytora obrazów**.

1. W **edytora obrazów**, przeciągnij pole o zmiennych rozmiarach do środka *app.ico* można zwiększyć czytelność tekstu.

1. W **narzędzie tekstowe** okno dialogowe, wybierz opcję **czcionki** przycisku.

1. W **narzędzie czcionki tekstu** okno dialogowe:

   - Wybierz **podzbiory** z listy dostępnych czcionek, które są wymienione w **czcionki** pola listy.

   - Wybierz **Bold** z listy dostępnych style na liście **styl czcionki** pola listy.

   - Wybierz **10** z listy dostępnych punktów rozmiarów wymienionych w **rozmiar** pola listy.

   - Wybierz **OK**. **Narzędzie czcionki tekstu** okno dialogowe zostanie zamknięte i nowe ustawienia czcionek będą stosowane do tekstu.

1. Wybierz **Zamknij** na **narzędzie tekstowe** okno dialogowe. Pole o zmiennym rozmiarze wokół tekstu zniknie z **edytora obrazów**.

Obszar tekstu zawiera tekst, który pojawia się jako część zasobu. Ten obszar jest początkowo pusta.

> [!NOTE]
> Jeśli **przezroczyste tło** jest ustawiona tylko tekst, zostaną umieszczone w obrazie. Jeśli **tło nieprzezroczyste** jest ustawiony, prostokąt otaczający wypełniony kolorem tła, zostaną umieszczone za tekstem.

## <a name="window-panes"></a>Okienka

**Edytora obrazów** okna wyświetla dwa widoki obrazu, pasek podziału rozdziela dwa okienka. Aby zmieniać względne rozmiary okienek, można przeciągać pasek podziału. Aktywne okienko wyświetla krawędź wyboru.

Jeden widok jest rzeczywisty rozmiar, a drugi jest powiększony przez domyślny współczynnik rozszerzenia, 6. Widoki te dwa okienka są automatycznie aktualizowane, wszelkie zmiany wprowadzone w jednym okienku natychmiast są wyświetlane w innym. Dwa okienka ułatwiają pracować nad powiększania widoku obrazu, w którym można odróżnić poszczególnych pikseli i, w tym samym czasie obserwować wpływ swoją pracę na widoku rzeczywisty rozmiar obrazu.

Tyle miejsca, ile potrzeba korzysta z okienka po lewej stronie (do połowy **obraz** okna) aby wyświetlić domyślny widok 1:1 powiększenie obrazu. W okienku po prawej stronie wyświetla domyślny obraz powiększonego powiększenia 6:1. Można zmieniać powiększenie w każdym za pomocą okienka **Magnify** narzędzie **edytora obrazów** paska narzędzi lub za pomocą klawiszy skrótów.

Można powiększyć mniejszych okienku **edytora obrazów** okno i użyj dwa okienka, aby pokazać różnych regionach duży obraz. Wybierz w okienku, aby ją wybrać.

Względne rozmiary okienek można zmienić, ustawiając kursor na pasek podziału i przenoszenie pasek podziału w prawo lub lewo. Pasek podziału można przenieść do dowolnej stronie, aby pracować nad tylko jedno okienko.

Jeśli **edytora obrazów** okienko jest powiększony o 4 lub nowszej, może wyświetlić siatkę pikseli, ograniczającego piksele na obrazie.

### <a name="to-change-the-magnification-factor"></a>Aby zmienić stopień powiększenia

Domyślnie **edytora obrazów** Wyświetla widok w okienku po lewej stronie rzeczywisty rozmiar i widok, w okienku po prawej stronie w rzeczywistym rozmiarze 6 razy. Współczynnika powiększenia (widoczny na pasku stanu w dolnej części obszaru roboczego) jest stosunek między rzeczywisty rozmiar obrazu i wyświetlany rozmiar. Domyślny współczynnik wynosi 6 i zakres jest z zakresu od 1 do 10.

1. Wybierz **edytora obrazów** okienko współczynnika powiększenia, którego chcesz zmienić.

1. Na **edytora obrazów** narzędzi, wybierz strzałkę po prawej stronie **Magnify** narzędzia, a następnie wybierz współczynnika powiększenia z podmenu: **1 X**, **2 X**, **6 X**, lub **8 X**.

   > [!NOTE]
   > Aby wybrać współczynnika powiększenia, inne niż te wymienione w **Magnify** narzędzie, korzystanie z klawiszy skrótów.

### <a name="to-display-or-hide-the-pixel-grid"></a>Aby wyświetlić lub ukryć siatkę pikseli

Dla wszystkich **edytora obrazów** okienka przy użyciu współczynnika powiększenia 4 lub większą, można wyświetlić siatkę ograniczającego piksele na obrazie.

1. Przejdź do menu **obraz** > **ustawienia siatki**.

1. Wybierz **siatkę pikseli** pole wyboru, aby wyświetlić siatkę, lub wyczyść pole, aby ukryć siatkę.

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz także

[Edytory zasobów](../windows/resource-editors.md)<br/>
[Ikony](/windows/desktop/menurc/icons)