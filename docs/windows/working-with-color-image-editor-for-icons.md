---
title: 'Instrukcje: Praca z kolorami'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.color
- vc.editors.customcolorselector
- vc.editors.loadcolorpalette
- vc.editors.colorswindow
helpviewer_keywords:
- images [C++], background colors
- Image editor [C++], Colors Palette
- colors [C++], image
- Colors Palette, Image editor
- palettes, Image editor colors
- foreground colors [C++], Image editor
- colors [C++]
- Image editor [C++], colors
- colors [C++], Image editor
- colors [C++], image
- images [C++], colors
- Image editor [C++], colors
- Fill tool
- colors [C++], image
- images [C++], colors
- colors [C++], selection tools
- Image editor [C++], colors
- Select Color tool
- dithered color, Image editor
- Custom Color Selector dialog box [C++]
- Image editor [C++], Colors Palette
- colors [C++], image
- bitmaps [C++], colors
- images [C++], colors
- HSL values
- Colors Palette, Image editor
- RGB color values
- Adjust Colors command [C++]
- Image editor [C++], dithered color
- Image editor [C++], Colors Palette
- Colors Palette, Image editor
- colors [C++], inverting
- colors [C++]
- Color Indicator
- colors [C++], Colors window
- Colors window, hiding colors
- Show Colors Window command
- Colors window, displaying colors
- color palettes [C++]
- palettes
- palettes, Image editor
- colors [C++], Image editor
- Image editor [C++], palettes
- color palettes
- Load Palette Colors dialog box [C++]
- opaque backgrounds [C++]
- colors [C++], image
- Image editor [C++], transparent or opague backgrounds
- images [C++], transparency
- images [C++], opaque background
- colors [C++], image
- Image editor [C++], color inversion
- images [C++], colors
- colors [C++], inverting
ms.assetid: d34ff96f-241d-494f-abdd-13811ada8cd3
ms.openlocfilehash: f50d734ab35968aa107e23b8450d60f316b6002e
ms.sourcegitcommit: b4645761ce5acf8c2fc7a662334dd5a471ea976d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/07/2019
ms.locfileid: "57563150"
---
# <a name="how-to-work-with-color"></a>Instrukcje: Praca z kolorami

**Edytora obrazów** zawiera wiele funkcji, które w szczególności obsługiwać i dostosowywanie kolorów. Można ustawić kolor pierwszego planu i tła, wypełnij obszary ograniczonego kolorem lub wybierz kolor obrazu do użycia jako bieżący kolor pierwszego planu i tła. Możesz użyć narzędzi na [paska narzędzi edytora obrazów](../windows/toolbar-image-editor-for-icons.md) wraz z palety kolorów w **kolory** okna, aby tworzyć obrazy.

Wszystkie kolory monochromatyczny i 16 kolorów obrazów są wyświetlane w **kolory** palety w **kolory** okna. Wraz z 16 kolorów standardowy można utworzyć własne niestandardowe kolory. Dowolne kolory z palety natychmiast zmiana będzie odpowiedni kolor na obrazie.

Podczas pracy z ikony 256 kolorów i obrazy kursora **kolory** właściwość [okno właściwości](/visualstudio/ide/reference/properties-window) jest używany. Aby uzyskać więcej informacji, zobacz [Tworzenie ikony 256 kolorów](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md).

Można również tworzyć obrazy True color. Jednak true koloru próbek nie są wyświetlane w palecie pełnego w **kolory** okna; pojawiają się tylko w obszarze wskaźnik kolor pierwszego planu i tła. Wartość true, kolory są tworzone przy użyciu **selektor kolorów niestandardowych** okno dialogowe.

Można zapisać palety kolorów niestandardowych na dysku i ponownie załaduj je stosownie do potrzeb. Palety kolorów, ostatnio używane jest zapisywane w rejestrze i ładowane automatycznie przy następnym uruchomieniu programu Visual Studio.

**Kolory** okno ma dwie części:

- **Paleta kolorów**, które jest tablicą przykłady kolorów, które reprezentują kolory, można użyć. Możesz wybrać z przykładami, aby wybrać kolory pierwszego planu i tła, podczas korzystania z narzędzi graficznych.

- **Wskaźnik koloru**, który przedstawia kolory pierwszego planu i tła i selektorów koloru ekranu i odwrotność.

   ![Okno kolory](../windows/media/vccolorswindow.gif "vcColorsWindow")<br/>
   **Kolory** okna

> [!NOTE]
> **Koloru ekranu** i **kolor odwrotność** narzędzia są dostępne tylko dla ikony i kursory.

Możesz użyć **kolory** okno z [paska narzędzi edytora obrazów](../windows/toolbar-image-editor-for-icons.md).

- Aby wyświetlić **kolory** okna, kliknij prawym przyciskiem myszy w **edytora obrazów** okienka i wybierz polecenie **Pokaż okno kolorów**, lub przejdź do menu [obrazu](../windows/image-menu-image-editor-for-icons.md)  >  **Pokaż okno kolorów**.

- Aby ukryć **kolory** okna, Odepnij okna (Ta akcja pozwoli okna ukryte automatycznie, gdy nie jest używany) lub wybierz **Zamknij** przycisku.

**Kolory** palety początkowo wyświetlane są kolory standardowe 16. Z wyświetlonej kolorów można również utworzyć kolory niestandardowe. Następnie można zapisywać i załaduj paletę kolorów niestandardowych.

**Selektor kolorów niestandardowych** okno dialogowe umożliwia dostosowanie kolorów, użyj dla obrazu z następującymi właściwościami:

|Właściwość|Opis|
|--------------------------|--------------------------|
|**Wyświetlanie kolor gradientu**|Umożliwia zmianę wartości wybrany kolor.<br/><br/>Umieść krzyżyk na kolor, który chcesz zmienić i przesuń suwak w górę lub w dół do Zmień jasność lub wartości RGB koloru.|
|**Jasność paska**|Ustawia jasność koloru w **gradientu wyświetlania kolorów** pole.<br/><br/>Wybierz i przeciągnij białe Strzałka w górę paska dla jasności większy lub w dół za niższą cenę. **Kolor** polu jest wyświetlana Kolor wybrano i efekt jasność ustawisz.|
|**Kolor**|Wyświetla listę aplikacji hue (wartość koło kolorów) kolor, który jest definiowany. Wartości z zakresu od 0 do 240, gdzie 0 jest czerwony, 60 jest żółty, 120 jest zielony, 180 jest błękitny, 200 jest amarantowy i 240 ma kolor niebieski.|
|**HUE**|Wyświetla listę aplikacji hue (wartość koło kolorów) kolor, który jest definiowany. Wartości z zakresu od 0 do 240, gdzie 0 jest czerwony, 60 jest żółty, 120 jest zielony, 180 jest błękitny, 200 jest amarantowy i 240 ma kolor niebieski.|
|**NAS.**|Określa wartość nasycenie koloru, który jest definiowany. Nasycenie jest ilość koloru w określonym odcieniu. Wartości z zakresu od 0 do 240.|
|**Jaskr.**|Wyświetla listę jasności (jasność) kolor, który jest definiowany. Wartości z zakresu od 0 do 240.|
|**Czerwony**|Określa wartość czerwony kolor, który jest definiowany. Wartości z zakresu od 0 do 255.|
|**Zielony**|Określa wartość zielony kolor, który jest definiowany. Wartości z zakresu od 0 do 255.|
|**Niebieski**|Określa wartość niebieskiego kolor, który jest definiowany. Wartości z zakresu od 0 do 255.|

Można zapisać i załadować **kolory** paletę zawierającą kolorów niestandardowych. Domyślnie **kolory** palety ostatnio używane jest automatycznie ładowany podczas uruchamiania programu Visual Studio.

> [!TIP]
> Ponieważ **edytora obrazów** nie posiada Aby przywrócić domyślne **kolory** palety, należy zapisać domyślne **kolory** palety w obszarze nazwy, takie jak  *Standard.PAL* lub *default.pal* tak, aby można je łatwo przywrócić ustawienia domyślne.

Użyj **ładowanie kolorów palety** okno dialogowe, aby załadować palety kolorów specjalne do użycia w projekcie języka C++ z następującymi właściwościami:

|Właściwość|Opis|
|-----------------|-----------------|
|**Szukaj w**|Określa lokalizację, w którym chcesz zlokalizować pliku lub folderu.<br/><br/>Wybierz strzałkę, aby wybrać inną lokalizację lub wybierz ikonę folderu, na pasku narzędzi, aby przenieść poziomów.|
|**Nazwa pliku**|Miejsce na wpisanie nazwy pliku, który chcesz otworzyć.<br/><br/>Aby szybko znaleźć plik, który poprzednio otwarty, wybierz nazwę pliku na liście rozwijanej, jeśli jest dostępny.<br/><br/>Jeśli szukasz pliku można użyć gwiazdki (*) jako symboli wieloznacznych. Na przykład można wpisać \*.\* umożliwia wyświetlenie listy wszystkich plików. Można również wpisz pełną ścieżkę pliku, na przykład *C:\My Documents\MyColorPalette.pal* lub  *\\\NetworkServer\MyFolder\MyColorPalette.pal*.|
|**Typy plików**|Zawiera listę typów plików do wyświetlenia.<br/><br/>Paleta (* .pal) jest typem pliku domyślnej palety kolorów.|

## <a name="how-to"></a>Instrukcje

### <a name="to-select-foreground-or-background-colors"></a>Aby wybrać pierwszego planu lub kolorów tła

Z wyjątkiem **Gumka**, narzędzia na **edytora obrazów** rysowania narzędzi bieżącym kolorem pierwszego planu i tła po naciśnięciu przycisku myszy w lewo lub w prawo, odpowiednio.

- Aby wybrać kolor pierwszego planu, za pomocą lewego przycisku myszy, wybierz żądany kolor na **kolory** palety.

- Aby zmienić kolor tła, za pomocą prawym przyciskiem myszy, wybierz żądany kolor na **kolory** palety.

### <a name="to-fill-a-bounded-area-of-an-image-with-a-color"></a>Aby wypełnić kolorem ograniczonego obszaru obrazu

**Edytora obrazów** zapewnia **wypełnienia** narzędzie do wypełniania dowolne ujęte obszar obrazu z bieżącym kolorem rysowania lub bieżący kolor tła.

### <a name="to-use-the-fill-tool"></a>Aby użyć narzędzia wypełnienia

1. Użyj **edytora obrazów** paska narzędzi lub przejdź do menu **obraz** > **narzędzia** i wybierz **wypełnienia** narzędzia.

1. Jeśli to konieczne, należy wybrać kolory do rysowania. W [paleta kolorów](../windows/colors-window-image-editor-for-icons.md), wybierz przycisk myszy po lewej stronie, aby wybrać kolor pierwszego planu lub prawego przycisku myszy, aby zmienić kolor tła.

1. Przenieś **wypełnienia** narzędzie do obszaru, który chcesz wypełnić.

1. Wybierz przycisk myszy w lewo lub w prawo, aby wypełnić kolor pierwszego planu lub kolorów tła, odpowiednio.

### <a name="to-pick-up-a-color-from-an-image-to-use-elsewhere"></a>Aby wybrać kolor z obrazu do użycia w innym miejscu

**Wybierz kolor**, lub kolor odbiór, narzędzie sprawia, że każdy kolor na obrazku bieżący kolor pierwszego planu lub kolorów tła, w zależności od tego, czy naciśnięciu lewego lub prawego przycisku myszy. Aby anulować **wybierz kolor** narzędzia, wybranie innego narzędzia.

1. Użyj **edytora obrazów** paska narzędzi lub przejdź do menu **obraz** > **narzędzia** i wybierz **wybierz kolor** narzędzia.

1. Wybierz kolor, który chcesz wczytać z obrazu.

   > [!NOTE]
   > Po pobraniu kolor, **edytora obrazów** uaktywnia ponownie ostatnio używane narzędzia.

1. Rysowanie za pomocą lewego przycisku myszy kolor pierwszego planu lub prawego przycisku myszy kolor tła.

### <a name="to-choose-the-background"></a>Aby wybrać tło

Podczas przenoszenia lub skopiowane z obrazu wszystkie piksele w zaznaczeniu, które odpowiadają bieżącym kolorem tła, są domyślnie, przejrzyste i nie mogą zasłaniać pikseli w lokalizacji docelowej.

Możesz przełączyć się z przezroczystym tłem (ustawienie domyślne) tło nieprzezroczyste i z powrotem. Korzystając z narzędzia zaznaczania **przezroczyste tło** i **tło nieprzezroczyste** opcje są wyświetlane na **opcji** selektor na **edytora obrazów** paska narzędzi.

![Opcje w tle &#45; przezroczystości](../windows/media/vcimageeditoropaqtranspback.gif "opcje w tle &#45; przezroczystości")<br/>
**Opcje przezroczystości i nieprzezroczyste** na **paska narzędzi edytora obrazów**

#### <a name="to-switch-between-a-transparent-and-opaque-background"></a>Aby przełączać się między tło przezroczyste i nieprzezroczyste

W **edytora obrazów** narzędzi, wybierz opcję **opcji** selektor, a następnie wybierz odpowiednią tła:

- **Tło nieprzezroczyste (O)**: Istniejący obraz jest zasłonięte przez wszystkie części zaznaczenia.

- **Tło przezroczyste (T)**: Istniejący obraz pokazuje fragmenty zaznaczenia, które odpowiadają bieżącym kolorem tła.

> [!TIP]
> W przypadku skrótu na **obraz** menu, zaznacz lub wyczyść **Rysowanie nieprzezroczystych**.

Możesz zmienić kolor tła zaznaczenia już w trakcie efekt zmiany, które części obrazu są niewidoczne.

### <a name="to-invert-the-colors-in-a-selection"></a>Aby odwrócić kolorów w wyborze

**Edytora obrazów** zapewnia wygodny sposób Odwróć kolory, w wybranych część obrazu, dzięki czemu można sprawdzić, jak obraz zostanie wyświetlone z odwróconą kolorów.

Aby Odwróć kolory w bieżącym zaznaczeniu, przejdź do menu **obraz** > **Odwróć kolory**.

### <a name="to-customize-or-change-colors-on-the-colors-palette"></a>Dostosowywanie lub zmiana kolorów palety kolorów

1. Przejdź do menu **obraz** > **Dopasuj kolory**.

1. W **selektor kolorów niestandardowych** okna dialogowego pole, Zdefiniuj kolor, wpisując wartości RGB lub HSL w odpowiednie pola tekstowe lub wybierz kolor w **gradientu wyświetlania kolorów** pole.

1. Ustaw jasność za pomocą suwaka **jasność** paska.

1. Wiele kolorów niestandardowych są symulowane. Pełny kolor najbliżej kolor symulowany, kliknij dwukrotnie **kolor** pole.

   Jeśli później zdecydujesz, ma kolor symulowany, przesuń suwak **jasność** pasek lub przenieść krzyżyka **gradientu wyświetlania kolorów** okno ponownie, aby przywrócić symulowania kolorów.

1. Wybierz **OK** Aby dodać nowy kolor.

### <a name="to-save-a-custom-colors-palette"></a>Aby zapisać palety kolorów niestandardowych

1. Przejdź do menu **obraz** > **Zapisz paletę**.

1. Przejdź do katalogu, w którym chcesz zapisać palety, a następnie wpisz nazwę palety.

1. Wybierz pozycję **Zapisz**.

### <a name="to-load-a-custom-colors-palette"></a>Aby załadować palety kolorów niestandardowych

1. Przejdź do menu **obraz** > **Załaduj paletę**.

1. W **Załaduj paletę kolorów** okna dialogowego pole, przejdź do katalogu poprawny i wybierz paletę chcesz załadować. **Kolor** palet są zapisywane wraz z rozszerzeniem pliku .pal.

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)<br/>
[Instrukcje: Tworzenie ikony lub innego obrazu](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Instrukcje: Edytowanie obrazu](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Instrukcje: Używanie narzędzia do rysowania](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
