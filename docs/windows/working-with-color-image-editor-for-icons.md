---
title: 'Instrukcje: korzystanie z koloru'
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
ms.openlocfilehash: 3c9134fde9053f57f8848a37b1442728f6111c98
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502947"
---
# <a name="how-to-work-with-color"></a>Instrukcje: korzystanie z koloru

**Edytor obrazów** zawiera wiele funkcji, które w specjalny sposób obsługują i dostosowuje kolory. Możesz ustawić kolor pierwszego planu lub tła, wypełnić obszary ograniczone kolorem lub wybrać kolor obrazu, który ma być używany jako bieżący pierwszy plan lub kolor tła. Możesz użyć narzędzi na [pasku narzędzi edytora obrazu](./image-editor-for-icons.md) wraz z paletą kolory w oknie **kolory** do tworzenia obrazów.

Wszystkie kolory obrazów monochromatycznych i 16-kolorowych są wyświetlane w palecie **kolory** w oknie **kolory** . Wraz z 16 kolorami standardowymi można tworzyć własne kolory niestandardowe. Zmiana dowolnego koloru w palecie natychmiast zmieni odpowiedni kolor w obrazie.

Podczas pracy z ikoną koloru 256 i obrazami kursora Właściwość **Colors** w [okno właściwości](/visualstudio/ide/reference/properties-window) jest używana. Aby uzyskać więcej informacji, zobacz [Creating a 256-kolorowe ikony lub kursora](./creating-an-icon-or-other-image-image-editor-for-icons.md).

Można również tworzyć obrazy o kolorach true. Jednak prawdziwe próbki kolorów nie są wyświetlane w pełnej palecie w oknie **kolory** . są one wyświetlane tylko w obszarze wskaźnika koloru na pierwszym planie lub w tle. Prawdziwe kolory są tworzone za pomocą okna dialogowego **selektora kolorów niestandardowych** .

Możesz zapisać dostosowane palety kolorów na dysku i załadować je ponownie zgodnie z potrzebami. Ostatnio używana paleta kolorów jest zapisywana w rejestrze i automatycznie ładowana przy następnym uruchomieniu programu Visual Studio.

Okno **kolory** ma dwie części:

- **Paleta kolorów**, która jest tablicą próbek kolorów, które reprezentują kolory, których można użyć. Możesz wybrać przykłady do wybierania kolorów pierwszego planu i tła, gdy używasz narzędzi graficznych.

- **Wskaźnik koloru**, który pokazuje kolory pierwszego planu i tła oraz selektory dla koloru ekranu i odwracania.

   ![Okno kolory](../windows/media/vccolorswindow.gif "vcColorsWindow")<br/>
   Okno **kolory**

> [!NOTE]
> Narzędzia **koloru ekranu** i **koloru odwracania** są dostępne tylko dla ikon i kursorów.

Możesz użyć okna **kolory** z [paskiem narzędzi edytora obrazu](./image-editor-for-icons.md).

- Aby wyświetlić okno **kolory** , kliknij prawym przyciskiem myszy w okienku **edytora obrazów** i wybierz polecenie **Pokaż kolory okno**lub przejdź do menu [obraz](./image-editor-for-icons.md)  >  **Pokaż kolory**.

- Aby ukryć okno **kolory** , Odepnij okno (Ta akcja zezwoli na Autoukrywanie okna, gdy nie jest używane) lub wybierz przycisk **Zamknij** .

W palecie **kolory** początkowo są wyświetlane 16 kolorów standardowych. Korzystając z wyświetlanych kolorów, można również tworzyć własne kolory niestandardowe. Następnie można zapisać i załadować dostosowaną paletę kolorów.

Okno dialogowe **selektora kolorów niestandardowych** umożliwia dostosowanie kolorów używanych dla obrazu o następujących właściwościach:

|Właściwość|Opis|
|--------------------------|--------------------------|
|**Wyświetlanie koloru gradientu**|Zmienia wartości wybranego koloru.<br/><br/>Umieść krzyżyk na kolorze, który chcesz zmienić, i przesuń suwak w górę lub w dół, aby zmienić jasność lub RGB koloru.|
|**Pasek jaskrawości**|Ustawia jaskrawość koloru wybraną w polu **wyświetlania koloru gradientu** .<br/><br/>Wybierz i przeciągnij strzałkę w górę, aby zwiększyć jasność lub mniej więcej. W polu **kolor** zostanie wyświetlony wybrany kolor oraz efekt ustawionego jaskrawości.|
|**Kolor**|Wyświetla listę odcienia (wartość koła koloru) definiującego kolor. Wartości mieszczą się w zakresie od 0 do 240, gdzie 0 to Red, 60 jest żółty, 120 jest zielony, 180 jest błękitny, 200 jest amarantowy, a 240 jest niebieska.|
|**Spowoduje**|Wyświetla listę odcienia (wartość koła koloru) definiującego kolor. Wartości mieszczą się w zakresie od 0 do 240, gdzie 0 to Red, 60 jest żółty, 120 jest zielony, 180 jest błękitny, 200 jest amarantowy, a 240 jest niebieska.|
|**Sob**|Określa wartość nasycenia koloru, który jest definiowany. Nasycenie to ilość koloru w określonym odcieniu. Wartości mieszczą się w zakresie od 0 do 240.|
|**Lum**|Wyświetla listę jaskrawości (jasność) definiowanego koloru. Wartości mieszczą się w zakresie od 0 do 240.|
|**Red (Czerwony)**|Określa czerwoną wartość koloru, który definiujesz. Wartości mieszczą się w zakresie od 0 do 255.|
|**Green (Zielony)**|Określa zieloną wartość koloru, który definiujesz. Wartości mieszczą się w zakresie od 0 do 255.|
|**Blue (Niebieski)**|Określa niebieską wartość koloru, który definiujesz. Wartości mieszczą się w zakresie od 0 do 255.|

Możesz zapisać i załadować paletę **kolorów** , która zawiera dostosowane kolory. Domyślnie paleta **kolorów** ostatnio używana jest automatycznie ładowana podczas uruchamiania programu Visual Studio.

> [!TIP]
> Ponieważ **Edytor obrazów** nie ma środków do przywrócenia domyślnej palety **kolorów** , należy zapisać domyślną paletę **kolorów** pod nazwą *Standard. PAL* lub *default. PAL* , aby można było łatwo przywrócić ustawienia domyślne.

Za pomocą okna dialogowego **Załaduj kolory palety** można załadować specjalne palety kolorów do użycia w projekcie języka C++ z następującymi właściwościami:

|Właściwość|Opis|
|-----------------|-----------------|
|**Szukaj w**|Określa lokalizację, w której ma zostać zlokalizowany plik lub folder.<br/><br/>Wybierz strzałkę, aby wybrać inną lokalizację, lub wybierz ikonę folderu na pasku narzędzi, aby przenieść poziomy.|
|**Nazwa pliku**|Miejsce na wpisanie nazwy pliku, który chcesz otworzyć.<br/><br/>Aby szybko znaleźć plik, który został wcześniej otwarty, wybierz nazwę pliku na liście rozwijanej, jeśli jest dostępna.<br/><br/>Jeśli szukasz pliku, możesz użyć gwiazdek (*) jako symboli wieloznacznych. Na przykład można wpisać., \* \* Aby wyświetlić listę wszystkich plików. Możesz również wpisać pełną ścieżkę do pliku, na przykład *C:\Moje Documents\MyColorPalette.PAL* lub * \\ \NetworkServer\MyFolder\MyColorPalette.PAL*.|
|**Pliki typu**|Wyświetla listę typów plików do wyświetlenia.<br/><br/>Paleta (*. PAL) jest domyślnym typem pliku dla palet kolorów.|

## <a name="how-to"></a>Instrukcje

### <a name="to-select-foreground-or-background-colors"></a>Aby wybrać kolory na pierwszym planie lub w tle

Z wyjątkiem **gumki**, narzędzia na pasku narzędzi **edytora obrazów** są rysowane przy użyciu bieżącego pierwszego planu lub koloru tła po naciśnięciu odpowiednio lewego lub prawego przycisku myszy.

- Aby wybrać kolor pierwszego planu, z lewym przyciskiem myszy wybierz odpowiedni kolor w palecie **kolorów** .

- Aby wybrać kolor tła, z prawym przyciskiem myszy wybierz odpowiedni kolor w palecie **kolorów** .

### <a name="to-fill-a-bounded-area-of-an-image-with-a-color"></a>Aby wypełnić ograniczony obszar obrazu kolorem

**Edytor obrazów** udostępnia narzędzie **wypełnienia** służące do wypełniania dowolnego zamkniętego obszaru obrazu bieżącym kolorem rysowania lub bieżącego koloru tła.

### <a name="to-use-the-fill-tool"></a>Aby użyć narzędzia Fill

1. Użyj paska narzędzi **edytora obrazu** lub przejdź do menu **Image**  >  **Narzędzia** obrazu i wybierz narzędzie **wypełnienia** .

1. W razie potrzeby wybierz pozycję Rysowanie kolorów. W [palecie kolorów](./image-editor-for-icons.md)wybierz lewy przycisk myszy, aby wybrać kolor pierwszego planu lub prawy przycisk myszy, aby wybrać kolor tła.

1. Przesuń narzędzie **Fill** do obszaru, który ma zostać wypełniony.

1. Wybierz lewy lub prawy przycisk myszy, aby wypełnić odpowiednio kolorem pierwszego planu lub kolorem tła.

### <a name="to-pick-up-a-color-from-an-image-to-use-elsewhere"></a>Aby pobrać kolor z obrazu do użycia w innym miejscu

**Wybierz kolor**lub kolor, aby uzyskać dowolny kolor obrazu bieżący kolor pierwszego planu lub kolor tła, w zależności od tego, czy naciśniesz prawy przycisk myszy. Aby anulować narzędzie **Wybierz kolor** , wybierz inne narzędzie.

1. Użyj paska narzędzi **edytora obrazu** lub przejdź do menu **Image**  >  **Narzędzia** obrazu i wybierz narzędzie **Wybierz kolor** .

1. Wybierz kolor, który chcesz pobrać z obrazu.

   > [!NOTE]
   > Po wybraniu koloru **Edytor obrazów** ponownie aktywuje ostatnio używane narzędzie.

1. Rysuj przy użyciu lewego przycisku myszy dla koloru pierwszego planu lub prawego przycisku myszy dla koloru tła.

### <a name="to-choose-the-background"></a>Aby wybrać tło

Gdy przeniesiesz lub skopiujesz zaznaczenie z obrazu, wszystkie piksele w zaznaczeniu zgodne z bieżącym kolorem tła są domyślnie przezroczyste i nie zasłaniają pikseli w lokalizacji docelowej.

Możesz zmienić tło przezroczyste (domyślne) na tło nieprzezroczyste i ponownie. Gdy używasz narzędzia do zaznaczania, **przezroczyste tło** i **nieprzezroczyste Opcje tła** są wyświetlane w selektorze **opcji** na pasku narzędzi **edytora obrazów** .

![Opcje tła &#45; nieprzezroczyste lub przezroczyste](../windows/media/vcimageeditoropaqtranspback.gif "Opcje tła &#45; nieprzezroczyste lub przezroczyste")<br/>
**Opcje przezroczyste i nieprzezroczyste** na **pasku narzędzi edytora obrazu**

#### <a name="to-switch-between-a-transparent-and-opaque-background"></a>Aby przełączać się między przezroczystym a nieprzezroczystym tłem

Na pasku narzędzi **Edytor obrazów** wybierz selektor **opcji** , a następnie wybierz odpowiednie tło:

- **Tło nieprzezroczyste (O)**: istniejący obraz jest zasłonięty przez wszystkie części zaznaczenia.

- **Przezroczyste tło (T)**: istniejący obraz pokazuje fragmenty zaznaczenia zgodne z bieżącym kolorem tła.

> [!TIP]
> W przypadku skrótu w menu **obraz** wybierz lub wyczyść pole **rysowania nieprzezroczyste**.

Możesz zmienić kolor tła, gdy zaznaczenie już działa, aby zmienić, które części obrazu są przezroczyste.

### <a name="to-invert-the-colors-in-a-selection"></a>Aby odwrócić kolory w zaznaczeniu

**Edytor obrazów** zapewnia wygodny sposób odwrócenia kolorów w zaznaczonej części obrazu, dzięki czemu można określić, jak będzie wyglądać obraz z odwróconymi kolorami.

Aby odwrócić kolory w bieżącym zaznaczeniu, przejdź do menu **obrazu**  >  **Odwróć kolory**.

### <a name="to-customize-or-change-colors-on-the-colors-palette"></a>Aby dostosować lub zmienić kolory na palecie kolorów

1. Przejdź do **obrazu**menu  >  **Dopasuj kolory**.

1. W oknie dialogowym **selektora kolorów niestandardowych** Zdefiniuj kolor, wpisując wartości RGB lub HSL w odpowiednich polach tekstowych lub wybierając kolor w polu **wyświetlanym kolor gradientu** .

1. Ustaw jasność, przesuwając suwak na pasku **jaskrawości** .

1. Wiele kolorów niestandardowych jest rozliczane. Jeśli chcesz, aby kolor kryjący był najbardziej zbliżony do koloru, kliknij dwukrotnie pole **koloru** .

   Jeśli później zdecydujesz się uzyskać kolor, przesuń suwak na pasku **jaskrawym** lub przesuń krzyżyki w polu **kolor gradientu** ponownie, aby przywrócić symulowanie.

1. Wybierz **przycisk OK** , aby dodać nowy kolor.

### <a name="to-save-a-custom-colors-palette"></a>Aby zapisać paletę kolorów niestandardowych

1. Przejdź do menu **obrazu**,  >  **Zapisz paletę**.

1. Przejdź do katalogu, w którym chcesz zapisać paletę, a następnie wpisz nazwę dla palety.

1. Wybierz pozycję **Zapisz**.

### <a name="to-load-a-custom-colors-palette"></a>Aby załadować paletę kolorów niestandardowych

1. Przejdź do menu **Image**wybierz  >  **paletę ładowania**obrazu.

1. W oknie dialogowym **Załaduj paletę kolorów** przejdź do poprawnego katalogu i wybierz paletę, którą chcesz załadować. Palety **kolorów** są zapisywane z rozszerzeniem. PAL.

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)<br/>
[Instrukcje: Tworzenie ikony lub innego obrazu](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Instrukcje: Edytowanie obrazu](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Instrukcje: korzystanie z narzędzia do rysowania](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
