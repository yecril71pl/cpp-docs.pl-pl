---
title: 'Instrukcje: Tworzenie ikony lub innego obrazu'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
- vc.editors.newimagetype
- vc.editors.customimage
- vc.editors.opendeviceimage
- vc.editors.image.editing
- vc.editors.image.editing
helpviewer_keywords:
- bitmaps [C++]
- images [C++], creating
- resources [C++], creating images
- bitmaps [C++], creating
- graphics [C++], creating
- Image editor [C++], creating images
- cursors [C++], creating
- image resources [C++], display devices
- icons [C++], creating
- cursors [C++], types
- icons [C++]
- Image editor [C++], icons and cursors
- cursors [C++]
- display devices [C++], creating icons for
- cursors [C++], hot spots
- icons [C++], types
- icons [C++], creating
- display devices [C++], creating image
- images [C++], creating for display devices
- icons [C++], inserting
- New <Device> Image Type dialog box [C++]
- Custom Image dialog box [C++]
- Open <Device> Image dialog box [C++]
- New Device Image command
- display devices [C++], adding images
- cursors [C++], adding
- icons, adding
- display devices [C++], copying images
- cursors [C++], copying
- icons, copying
- cursors [C++], deleting
- display devices [C++], deleting device image
- icons, erasing
- icons, deleting
- cursors [C++], undoing changes
- icons, undoing changes
- cursors [C++], screen regions
- inverse colors [C++], device images
- transparent regions, device images
- transparency, device images
- Image editor [C++], device images
- inverse regions, device images
- cursors [C++], transparent regions
- screen colors
- regions, transparent
- icons [C++], transparent regions
- display devices [C++], transparent and screen regions
- transparent regions in devices
- regions, inverse
- colors [C++], Image editor
- device projects [C++], transparent images
- icons [C++], screen regions
- 256-color palette
- cursors [C++], color
- colors [C++], icons
- colors [C++], cursors
- icons, color
- colors [C++], icons and cursors
- color palettes, 256-color
- palettes, 256-color
- cursors [C++], hot spots
- hot spots
- .gif files [C++], saving bitmaps as
- jpg files [C++], saving bitmaps as
- jpeg files [C++], saving bitmaps as
- .jpg files [C++], saving bitmaps as
- Image editor [C++], converting image formats
- gif files [C++], saving bitmaps as
- bitmaps [C++], converting formats
- .jpeg files [C++], saving bitmaps as
- graphics [C++], converting formats
- images [C++], converting formats
- images [C++], stand-alone editing
- Image editor [C++], converting image formats
- graphics [C++], converting formats
- images [C++], converting formats
ms.assetid: 66db3fb2-cfc1-48a2-9bdd-53f61eb7ee30
ms.openlocfilehash: 4191b1bd495a8908610b6e49c3dff676de2304dc
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328496"
---
# <a name="how-to-create-an-icon-or-other-image"></a>Instrukcje: Tworzenie ikony lub innego obrazu

Utwórz nowy obraz, mapy bitowej, ikony, kursor lub narzędzi, a następnie użyj **edytora obrazów** do dostosowania jego wyglądu. Można również tworzyć nowe mapę bitową z deseniem po [szablonu usługi resource](../windows/how-to-use-resource-templates.md).

## <a name="icons-and-cursors-image-resources-for-display-devices"></a>Ikony i kursory: Zasoby obrazów do wyświetlania na urządzeniach

Ikony i kursory są zasobów graficznych, które zawiera wiele obrazów o różnych wielkościach i schematów kolorów dla różnych rodzajów wyświetlania na urządzeniach. Kursor ma również punkt aktywny, używa Windows lokalizacji, aby śledzić jego położenie. Ikony i kursory są tworzone oraz edytowane za pomocą **edytora obrazów**, jak mapy bitowe i inne obrazy.

Po utworzeniu kursor, lub Nowa ikona **edytora obrazów** najpierw tworzy obraz standardowego typu. Obraz, który początkowo jest wypełniony kolorem ekranu (przezroczyste). Jeśli obraz kursora, punkt aktywny jest początkowo lewego górnego rogu współrzędnych `0,0`.

Domyślnie **edytora obrazów** obsługuje tworzenie dodatkowych obrazów dla urządzeń z poniższą tabelą. Można utworzyć obrazy w przypadku innych urządzeń, wpisując parametrów szerokości, wysokości i liczba kolorów w **obraz niestandardowy** okno dialogowe.

|Kolor|Szerokość (w pikselach)|Wysokość (w pikselach)|
|-----------|----------------------|-----------------------|
|Monochromatyczny|16|16|
|Monochromatyczny|32|32|
|Monochromatyczny|48|48|
|Monochromatyczny|64|64|
|Monochromatyczny|96|96|
|16|16|16|
|16|32|32|
|16|64|64|
|16|48|48|
|16|96|96|
|256|16|16|
|256|32|32|
|256|48|48|
|256|64|64|
|256|96|96|

### <a name="create-a-device-image-icon-or-cursor"></a>Tworzenie obrazu urządzenia (kursor lub ikonę)

Podczas tworzenia nowej ikony lub zasobu kursora **edytora obrazów** najpierw tworzy obraz w określonym stylu (32 x 32, 16 kolorów dla ikony oraz 32 × 32, monochromatyczny liczby kursorów). Można dodać obrazy w różnych rozmiarach i style do początkowego ikony lub kursor i edytowania każdego dodatkowego obrazu zgodnie z potrzebami dla różnych ekranów. Można również edytować obraz przy użyciu operacji kopiowania i wklejania z istniejącego typu obrazu lub mapy bitowej utworzonej w programie graficznym.

Po otwarciu ikony zasobu w [edytora obrazów](../windows/image-editor-for-icons.md), obraz, większość ściśle dopasowując bieżące urządzenie wyświetlające jest domyślnie otwierany.

> [!NOTE]
> Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

**New &lt;urządzenia&gt; typ obrazu** okno dialogowe umożliwia utworzenie nowego obrazu urządzenia o określonym typie. Aby otworzyć **New \<urządzenia > obraz** okno dialogowe, przejdź do menu **obraz** > **nowy typ obrazu**. Następujące właściwości zawarte są **typ obrazu docelowego** i **niestandardowe**.

**Typ obrazu docelowego** właściwość zawiera listę typów dostępnych obrazów, gdzie wybierz obraz typu, który chcesz otworzyć:

||||
|-|-|-|
|-16 x 16, 16 kolorów|-48 x 48, 16 kolorów|-96 x 96, 16 kolorów|
|-16 x 16, 256 kolorów|-48 x 48, 256 kolorów|-96 x 96, 256 kolorów|
|-16 x 16, monochromatyczny|-48 x 48, monochromatyczny|-96 x 96, monochromatyczny|
|-32 x 32, 16 kolorów|-64 x 64, 16 kolorów||
|-32 x 32, 256 kolorów|-64 x 64, 256 kolorów||
|-32 x 32, monochromatyczny|-64 x 64, monochromatyczny||

> [!NOTE]
> Żadnych istniejących obrazów, nie pojawi się na tej liście.

**Niestandardowe** Otwiera właściwości **obrazu niestandardowego** okno dialogowe, w którym można utworzyć nowy obraz niestandardowy rozmiar i liczba kolorów.

**Obrazu niestandardowego** okno dialogowe umożliwia utworzenie nowego obrazu z niestandardowy rozmiar i liczba kolorów. Następujące właściwości zawarte są:

|Właściwość|Opis|
|---|---|
|**Szerokość**|Miejsce na wprowadź szerokość obrazu niestandardowego w pikselach (1-512 limit 2048).|
|**Wysokość**|Miejsce na Wprowadź wysokość obrazu niestandardowego w pikselach (1-512 limit 2048).|
|**Kolory**|Miejsce na wybierz liczbę kolorów dla niestandardowego obrazu: 2, 16 lub 256.|

Użyj **Otwórz &lt;urządzenia&gt; obraz** okno dialogowe, aby otworzyć obrazach urządzeń w projektach C++. Wyświetla listę istniejących obrazów urządzeń w bieżącym (obrazy, które są częścią bieżącego zasobu). Następująca właściwość włączone jest:

|Właściwość|Opis|
|---|---|
|**Bieżących obrazów**|Wyświetla listę obrazów zawartych w zasobie. Wybierz typ obrazu, który chcesz otworzyć.|

#### <a name="to-create-a-new-icon-or-cursor"></a>Aby utworzyć nową ikonę lub kursora

1. W [widok zasobów](how-to-create-a-resource-script-file.md#create-resources), kliknij prawym przyciskiem myszy użytkownika *.rc* pliku, a następnie wybierz **Wstaw zasobów**. Jeśli masz już istniejący zasób obrazu swojej *.rc* plików, takich jak kursora, kliknąć prawym przyciskiem myszy **kursora** i wybierz polecenie **wstawiania kursora**.

1. W [Wstaw zasób — okno dialogowe](../windows/add-resource-dialog-box.md), wybierz opcję **ikonę** lub **kursora** i wybierz polecenie **New**. Ikony ta akcja powoduje utworzenie przy użyciu 32 x 32, ikona 16 kolorów zasobu ikony. Dla kursorów, 32 x 32, tworzony jest monochromatyczny obrazu (w kolorze 2).

   Jeśli znak plus (**+**) pojawia się obok typ zasobu obrazu w **Wstaw zasobów** okno dialogowe, oznacza to, narzędzi szablony są dostępne. Wybierz znak plus, aby rozwinąć listę szablonów, wybierz szablon, a następnie wybierz **New**.

### <a name="to-add-an-image-for-a-different-display-device"></a>Aby dodać obraz wyświetlania na różnych urządzeniach

1. Przejdź do menu **obraz** > **nowy obraz urządzenia**, lub kliknij prawym przyciskiem myszy **edytora obrazów** okienka i wybierz polecenie **nowy obraz urządzenia**.

1. Wybierz typ obrazu, który chcesz dodać. Możesz również wybrać **niestandardowe** do utworzenia ikony, którego rozmiar nie jest dostępna na liście domyślnej.

### <a name="to-copy-a-device-image"></a>Aby skopiować obrazu urządzenia

1. Przejdź do menu **obraz** > **Otwieranie obrazu urządzenia** i wybierzesz obraz z bieżącej listy obrazów. Na przykład wybierz 32 x 32, 16 kolorów wersja ikony.

1. Skopiuj obraz aktualnie wyświetlane ikony (**Ctrl**+**C**).

1. Otwórz inny obraz ikony w innym **edytora obrazów** okna. Na przykład otworzyć 16 x 16, 16 kolorów wersja ikony.

1. Wklej obraz ikony (**Ctrl**+**V**) z jednego **edytora obrazów** okna do innego. Jeśli wklejasz większy rozmiar do mniejszego rozmiaru, można użyć uchwytów ikony zmiany rozmiaru obrazu.

### <a name="to-delete-a-device-image"></a>Aby usunąć obrazu urządzenia

Gdy obraz ikony są wyświetlane w **edytora obrazów**, przejdź do menu **obraz** > **usuwanie obrazu urządzenia**. Po usunięciu ostatniego obraz ikony w zasobie zasobu są także usuwane.

> [!NOTE]
> Po naciśnięciu klawisza **Del** klucza, obrazy i kolorów ma być rysowany ikonę są usuwane, ale ikona pozostaje i możesz teraz ponownie zaprojektować go. Jeśli użytkownik naciśnie klawisz **Del** przez pomyłkę, naciśnij klawisz **Ctrl**+**Z** cofnięcie akcji.

### <a name="to-create-transparent-or-inverse-regions-in-device-images"></a>Aby utworzyć przezroczystych lub odwróconych w obrazach urządzeń

W [edytora obrazów](../windows/image-editor-for-icons.md), początkowego obrazu ikony ma atrybut przezroczysty. Mimo że prostokątny znajdują się obrazy ikon i kursorów, wiele nie pojawiają się więc obrazu podstawowego na ekranie przedstawiono za pośrednictwem ikony lub kursora, ponieważ części obrazu są niewidoczne. Podczas przeciągania ikony części obrazu może pojawić się w kolorze odwrócony. Ten efekt, ustawiając kolor ekranu i odwracanie kolorów w [okno kolorów](../windows/colors-window-image-editor-for-icons.md).

Kolory ekranu i odwrotność, można zastosować do ikony i kursory kształt i kolor obrazu pochodnej albo Przypisz odwracanie regionów. Kolory wskazują części obrazu, które mają te atrybuty. Można zmienić kolory, które reprezentują ekranu odwrotność kolorach i atrybuty w edycji. Te zmiany nie wpływają na wygląd ikony lub kursor znajduje się w aplikacji.

> [!NOTE]
> Polecenia menu, zostanie wyświetlony i okien dialogowych mogą różnić się od tych opisanych w **pomocy** w zależności od ustawień aktywnych lub wersji. Aby zmienić swoje ustawienia, przejdź do menu **narzędzia** > **Import i eksport ustawień**. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

#### <a name="to-create-transparent-or-inverse-regions"></a>Aby utworzyć przezroczystych lub odwróconych

1. W **kolory** oknie Wybierz selektor **koloru ekranu** lub **kolor odwrotność**.

1. Zastosuj ekranu lub odwróconych kolorów na obraz przy użyciu narzędzia do rysowania. Aby uzyskać więcej informacji na temat narzędzia do rysowania, zobacz [przy użyciu narzędzia do rysowania](using-a-drawing-tool-image-editor-for-icons.md).

#### <a name="to-change-the-screen-or-inverse-color"></a>Aby zmienić kolor ekranu lub odwrotne

1. Wybierz opcję **koloru ekranu** selektora lub **kolor odwrotność** selektora.

1. Wybierz kolor na podstawie **kolory** palety w **kolory** okna.

   Kolor dopełniający jest przypisywany do innych selektora.

   > [!TIP]
   > Po dwukrotnym kliknięciu **koloru ekranu** lub **kolor odwrotność** selektor [okno dialogowe selektora kolorów niestandardowych](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md) pojawia się.

### <a name="use-the-256-color-palette"></a>Użyj palety 256 kolorów

Za pomocą **edytora obrazów**, ikon i kursorów można wielkości dużych (64 × 64) z palety 256 kolorów, aby wybrać z. Po utworzeniu zasobu stylu obrazu urządzenia jest zaznaczone.

#### <a name="to-create-a-256-color-icon-or-cursor"></a>Tworzenie ikony 256 kolorów lub kursora

1. W [widok zasobów](how-to-create-a-resource-script-file.md#create-resources), kliknij prawym przyciskiem myszy użytkownika *.rc* pliku, a następnie wybierz **Wstaw zasobów**. Jeśli masz już istniejący zasób obrazu swojej *.rc* plików, takich jak kursora, kliknąć prawym przyciskiem myszy **kursora** i wybierz polecenie **wstawiania kursora**.

1. W [Wstaw zasób — okno dialogowe](../windows/add-resource-dialog-box.md), wybierz opcję **ikonę** lub **kursora** i wybierz polecenie **New**.

1. Przejdź do menu **obraz** > **nowy obraz urządzenia** i wybierz żądany styl obrazu 256 kolorów.

#### <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>Aby wybrać kolor z palety 256 kolorów dla dużych ikon

Aby narysować przy zaznaczeniem z palety 256 kolorów, musisz wybrać kolory z **kolory** palety w [okno kolorów](../windows/colors-window-image-editor-for-icons.md).

1. Wybierz kursor lub duże ikony, lub Utwórz nową ikonę dużych lub kursor.

1. Wybierz kolor z 256 kolorów, które są wyświetlane w **kolory** palety w **kolory** okna.

   Kolor wybrany staną się bieżący kolor w **kolory** palety w **kolory** okna.

   > [!NOTE]
   > Pasuje do początkowej palety 256 kolorów obrazów palety zwracany przez `CreateHalftonePalette` interfejsu Windows API. Wszystkie ikony przeznaczone dla powłoki Windows należy używać tej palety, aby zapobiec migotania podczas realizacji palety.

### <a name="to-set-a-cursors-hot-spot"></a>Aby ustawić aktywnego punktu kursora

Aktywnego punktu kursora jest punktem, do której Windows odwołuje się w śledzeniu pozycja kursora. Domyślnie ustawiono punkt aktywny do lewego górnego rogu kursora współrzędnych `0,0`. **Informacji o hotspotach** właściwość [okno właściwości](/visualstudio/ide/reference/properties-window) zawiera współrzędne punktu aktywnego.

1. Na [paska narzędzi edytora obrazów](../windows/toolbar-image-editor-for-icons.md), wybierz **Ustaw punkt aktywny** narzędzia.

1. Wybierz piksel, który ma zostać przypisany jako aktywnego punktu kursora.

   **Informacji o hotspotach** właściwość **właściwości** okno wyświetla nowy współrzędnych.

### <a name="to-create-and-save-a-bitmap-as-a-gif-or-jpeg"></a>Aby utworzyć i zapisać mapy bitowej jako obraz GIF lub JPEG

Gdy tworzysz mapę bitową, obraz jest tworzony w formacie mapy bitowej (bmp). Można jednak zapiszesz obraz GIF lub JPEG lub w innych formatach grafiki.

> [!NOTE]
> Ten proces nie ma zastosowania do ikony i kursory.

1. Przejdź do menu **pliku** > **Otwórz**, a następnie wybierz **pliku**.

1. W **okno dialogowe Nowy plik**, wybierz **Visual C++** folderu, następnie wybierz pozycję **plik mapy bitowej (bmp)** w **szablony** pole, a następnie wybierz  **Otwórz**.

   Mapa bitowa zostanie otwarty w **edytora obrazów**.

1. Wprowadź zmiany do nowej mapy bitowej, zgodnie z potrzebami.

1. Z mapą bitową wciąż otwarty w **edytora obrazów**, przejdź do menu **pliku** > **Zapisz *filename*.bmp jako**.

1. W **Zapisz plik jako** okna dialogowego wpisz nazwę, którą chcesz nadać pliku i rozszerzenie, które określa format pliku, w **nazwy pliku** pole. Na przykład *myfile.gif*.

   > [!NOTE]
   > Należy utworzyć lub otworzyć mapy bitowej spoza projektu, aby można było zapisać go jako pliku w innym formacie. Jeśli tworzysz lub otwórz go w swoim projekcie **Zapisz jako** polecenie jest niedostępne. Aby uzyskać więcej informacji, zobacz [wyświetlania zasobów w zasobu skryptu pliku poza z projektu (autonomicznego)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

1. Wybierz pozycję **Zapisz**.

### <a name="to-convert-an-image-from-one-format-to-another"></a>Aby przekonwertować obrazu z jednego formatu

Możesz otworzyć obrazów GIF lub JPEG w **edytora obrazów** i zapisz je jako map bitowych. Ponadto można otworzyć pliku mapy bitowej i zapisz go jako plik GIF lub JPEG. Pracujesz z obrazów nie muszą być częścią projektu do edycji w środowisku programistycznym (zobacz [edycji obrazów autonomicznej](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md)).

1. Otwórz obraz w **edytora obrazów**.

1. Przejdź do menu **pliku** > **Zapisz *filename* jako**.

1. W **Zapisz plik jako** dialogowym **nazwy pliku** wpisz nazwę pliku i rozszerzenie, które oznacza żądany format.

1. Wybierz pozycję **Zapisz**.

### <a name="to-add-a-new-image-resource-to-an-unmanaged-c-project"></a>Aby dodać nowy zasób obrazu do niezarządzanego projektu C++

1. W [widok zasobów](how-to-create-a-resource-script-file.md#create-resources), kliknij prawym przyciskiem myszy użytkownika *.rc* pliku, a następnie wybierz **Wstaw zasobów**. Jeśli masz już istniejący zasób obrazu swojej *.rc* plików, takich jak kursora, użytkownik może po prostu kliknij prawym przyciskiem myszy **kursora** i wybierz polecenie **wstawiania kursora**.

1. W [Wstaw zasób — okno dialogowe](../windows/add-resource-dialog-box.md), wybierz typ zasobu obrazu, które chcesz utworzyć (**mapy bitowej**, na przykład) wybierz **New**.

   Jeśli znak plus (**+**) pojawia się obok typ zasobu obrazu w **Wstaw zasobów** okno dialogowe, oznacza to, narzędzi szablony są dostępne. Wybierz znak plus, aby rozwinąć listę szablonów, wybierz szablon, a następnie wybierz **New**.

### <a name="to-add-a-new-image-resource-to-a-project-in-a-net-programming-language"></a>Aby dodać nowy zasób obrazu do projektu w języku programowania .NET

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy folder projektu (na przykład *WindowsApplication1*).

1. Z menu skrótów wybierz **Dodaj**, następnie wybierz **Dodaj nowy element**.

1. W **kategorie** okienku rozwiń **lokalne elementy projektu** folderu, wybierz **zasobów**.

1. W **szablony** okienku, wybierz typ zasobu, czy chcesz dodać do projektu.

   Zasób jest dodawany do projektu w **Eksploratora rozwiązań** i zasobów zostanie otwarty w [edytora obrazów](../windows/image-editor-for-icons.md). Teraz można użyć narzędzi dostępnych w ramach **edytora obrazów** Aby zmodyfikować swój obraz. Aby uzyskać więcej informacji na temat dodawania obrazów do projektów zarządzanych, zobacz [podczas ładowania obrazu w czasie projektowania](/dotnet/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms).

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)<br/>
[Instrukcje: Edytowanie obrazu](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Instrukcje: Używanie narzędzia do rysowania](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Instrukcje: Praca z kolorami](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
<!--
[Converting Bitmaps to Toolbars](../windows/converting-bitmaps-to-toolbars.md)<br/>
[Creating New Toolbars](../windows/creating-new-toolbars.md)<br/>
[Icons](/windows/desktop/menurc/icons)<br/>
[Cursors](/windows/desktop/menurc/cursors)<br/>-->