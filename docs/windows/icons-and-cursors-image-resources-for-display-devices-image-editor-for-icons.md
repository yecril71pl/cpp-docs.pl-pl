---
title: 'Ikony i kursory: Zasoby obrazów do wyświetlania na urządzeniach (C++ edytor obrazów dla ikon)'
ms.date: 11/04/2016
f1_keywords:
- vc.editors.icon
- vc.editors.newimagetype
- vc.editors.customimage
- vc.editors.opendeviceimage
- vc.editors.image.editing
helpviewer_keywords:
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
ms.assetid: 8f0809a8-0cf0-4da9-b23d-51f28bf15f5b
ms.openlocfilehash: 027c3c0380a73c624432bbe45758b3296732949a
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849948"
---
# <a name="icons-and-cursors-image-resources-for-display-devices-c-image-editor-for-icons"></a>Ikony i kursory: Zasoby obrazów do wyświetlania na urządzeniach (C++ edytor obrazów dla ikon)

Ikony i kursory są zasobów graficznych, które zawiera wiele obrazów o różnych wielkościach i schematów kolorów dla różnych rodzajów wyświetlania na urządzeniach. Kursor ma "punkt aktywny," w lokalizacji Windows używa do śledzenia jego położenie. Ikony i kursory są tworzone oraz edytowane za pomocą **obraz** edytora, jak mapy bitowe i inne obrazy.

Po utworzeniu kursor, lub Nowa ikona **obraz** edytora najpierw tworzy obraz standardowego typu. Obraz, który początkowo jest wypełniony kolorem ekranu (przezroczyste). Jeśli obraz kursora, punkt aktywny jest początkowo lewego górnego rogu (współrzędne 0,0).

Domyślnie **obraz** Edytor obsługuje tworzenie dodatkowych obrazów dla urządzeń z poniższą tabelą. Można utworzyć obrazy w przypadku innych urządzeń, wpisując parametrów szerokości, wysokości i liczba kolorów w [okno dialogowe obrazu niestandardowego](custom-image-dialog-box-image-editor-for-icons.md).

> [!NOTE]
> Za pomocą **edytora obrazów**, można wyświetlać obrazy 32-bitowe, ale nie można ich edytować.

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

## <a name="create-a-device-image-icon-or-cursor"></a>Tworzenie obrazu urządzenia (kursor lub ikonę)

Podczas tworzenia nowej ikony lub zasobu kursora **obraz** edytora najpierw tworzy obraz w określonym stylu (32 x 32, 16 kolorów dla ikony oraz 32 × 32, monochromatyczny liczby kursorów). Można dodać obrazy w różnych rozmiarach i style do początkowego ikony lub kursor i edytowania każdego dodatkowego obrazu zgodnie z potrzebami dla różnych ekranów. Można również edytować obraz przy użyciu operacji kopiowania i wklejania z istniejącego typu obrazu lub mapy bitowej utworzonej w programie graficznym.

Po otwarciu ikony zasobu w [edytora obrazów](../windows/image-editor-for-icons.md), obraz, większość ściśle dopasowując bieżące urządzenie wyświetlające jest domyślnie otwierany.

### <a name="new-ltdevicegt-image-type-dialog-box"></a>Nowe &lt;urządzenia&gt; okno dialogowe typu obrazu

**New &lt;urządzenia&gt; typ obrazu** okno dialogowe umożliwia utworzenie nowego obrazu urządzenia o określonym typie. Aby otworzyć **New \<urządzenia > obraz** okno dialogowe, wybierz opcję **nowy typ obrazu** na **obraz** menu. Następujące właściwości zawarte są **typ obrazu docelowego** i **niestandardowe**.

#### <a name="target-image-type"></a>Docelowy typ obrazu

Wyświetla listę typów dostępnych obrazów. Wybierz typ obrazu, który chcesz otworzyć:

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

#### <a name="custom"></a>Niestandardowe

Otwiera **obrazu niestandardowego** okno dialogowe, w którym można utworzyć nowy obraz niestandardowy rozmiar i liczba kolorów.

**Obrazu niestandardowego** okno dialogowe umożliwia utworzenie nowego obrazu z niestandardowy rozmiar i liczba kolorów. Następujące właściwości zawarte są:

|Właściwość|Opis|
|---|---|
|**Szerokość**|Miejsce na wprowadź szerokość obrazu niestandardowego w pikselach (1-512 limit 2048).|
|**Wysokość**|Miejsce na Wprowadź wysokość obrazu niestandardowego w pikselach (1-512 limit 2048).|
|**Kolory**|Miejsce na wybierz liczbę kolorów dla niestandardowego obrazu: 2, 16 lub 256.|

### <a name="open-ltdevicegt-image-dialog-box"></a>Otwórz &lt;urządzenia&gt; okno dialogowe obrazu

Użyj **Otwórz &lt;urządzenia&gt; obraz** okno dialogowe, aby otworzyć obrazach urządzeń w projektach C++. Wyświetla listę istniejących obrazów urządzeń w bieżącym (obrazy, które są częścią bieżącego zasobu). Następująca właściwość włączone jest:

|Właściwość|Opis|
|---|---|
|**Bieżących obrazów**|Wyświetla listę obrazów zawartych w zasobie. Wybierz typ obrazu, który chcesz otworzyć.|

### <a name="to-create-a-new-icon-or-cursor"></a>Aby utworzyć nową ikonę lub kursora

1. W [widok zasobów](../windows/resource-view-window.md), kliknij prawym przyciskiem myszy plik .rc, a następnie wybierz **Wstaw zasobów** z menu skrótów. (Jeśli masz już istniejący zasób obrazu w pliku .rc, takich jak kursora, możesz kliknąć prawym przyciskiem myszy **kursora** i wybierz polecenie **wstawiania kursora** z menu skrótów.)

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. W [Wstaw zasób — okno dialogowe](../windows/add-resource-dialog-box.md), wybierz opcję **ikonę** lub **kursora** i wybierz polecenie **New**. Ikony ta akcja powoduje utworzenie przy użyciu 32 x 32, ikona 16 kolorów zasobu ikony. Dla kursorów, 32 x 32, tworzony jest monochromatyczny obrazu (w kolorze 2).

   Jeśli znak plus (**+**) pojawia się obok typ zasobu obrazu w **Wstaw zasobów** okno dialogowe, oznacza to, narzędzi szablony są dostępne. Wybierz znak plus, aby rozwinąć listę szablonów, wybierz szablon, a następnie wybierz **New**.

## <a name="add-an-image-for-a-different-display-device"></a>Dodawanie obrazu wyświetlania na różnych urządzeniach

1. Na **obraz** menu, wybierz opcję **nowy obraz urządzenia** (lub kliknij prawym przyciskiem myszy **edytora obrazów** okienka i wybierz polecenie **nowy obraz urządzenia** z menu skrótów).

1. Wybierz typ obrazu, który chcesz dodać. Możesz również wybrać **niestandardowe** do utworzenia ikony, którego rozmiar nie jest dostępna na liście domyślnej.

## <a name="copy-a-device-image"></a>Kopiowanie obrazu urządzenia

1. Na **obraz** menu, wybierz opcję **Otwieranie obrazu urządzenia** i wybierzesz obraz z bieżącej listy obrazów. Na przykład wybierz 32 x 32, 16 kolorów wersja ikony.

1. Skopiuj obraz aktualnie wyświetlane ikony (**Ctrl**+**C**).

1. Otwórz inny obraz ikony w innym **edytora obrazów** okna. Na przykład otworzyć 16 x 16, 16 kolorów wersja ikony.

1. Wklej obraz ikony (**Ctrl**+**V**) z jednego **edytora obrazów** okna do innego. Jeśli wklejasz większy rozmiar do mniejszego rozmiaru, można użyć uchwytów ikony zmiany rozmiaru obrazu.

## <a name="delete-a-device-image"></a>Usuwanie obrazu urządzenia

Gdy obraz ikony są wyświetlane w **obraz** edytora, wybierz opcję **usuwanie obrazu urządzenia** z **obraz** menu. Po usunięciu ostatniego obraz ikony w zasobie zasobu są także usuwane.

   > [!NOTE]
   > Po naciśnięciu klawisza **Del** klucza, obrazy i kolorów ma być rysowany ikonę są usuwane, ale pozostaje ikonę; możesz teraz ponownie zaprojektować go. Jeśli użytkownik naciśnie klawisz **Del** przez pomyłkę, możesz nacisnąć przycisk **Ctrl**+**Z** cofnięcie akcji.

## <a name="create-transparent-or-inverse-regions-in-device-images"></a>Tworzenie obszarów przezroczystych lub odwróconych w obrazach urządzeń

W [edytora obrazów](../windows/image-editor-for-icons.md), początkowego obrazu ikony ma atrybut przezroczysty. Mimo że prostokątny znajdują się obrazy ikon i kursorów, wiele nie pojawiają się więc ponieważ przezroczysty; części obrazu Pokazuje obrazu podstawowego na ekranie za pomocą ikony lub kursor. Podczas przeciągania ikony części obrazu może pojawić się w kolorze odwrócony. Ten efekt, ustawiając kolor ekranu i odwracanie kolorów w [okno kolorów](../windows/colors-window-image-editor-for-icons.md).

Kolory ekranu i odwrotność, można zastosować do ikony i kursory kształt i kolor obrazu pochodnej albo Przypisz odwracanie regionów. Kolory wskazują części obrazu, które mają te atrybuty. Można zmienić kolory, które reprezentują ekranu odwrotność kolorach i atrybuty w edycji. Te zmiany nie wpływają na wygląd ikony lub kursor znajduje się w aplikacji.

> [!NOTE]
> Polecenia menu, zostanie wyświetlony i okien dialogowych mogą różnić się od tych opisanych w **pomocy** w zależności od ustawień aktywnych lub wersji. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

### <a name="to-create-transparent-or-inverse-regions"></a>Aby utworzyć przezroczystych lub odwróconych

1. W **kolory** wybierz **koloru ekranu** selektora lub **kolor odwrotność** selektora.

1. Zastosuj ekranu lub odwróconych kolorów na obraz przy użyciu narzędzia do rysowania. Aby uzyskać więcej informacji na temat narzędzia do rysowania, zobacz [przy użyciu narzędzia do rysowania](using-a-drawing-tool-image-editor-for-icons.md).

### <a name="to-change-the-screen-or-inverse-color"></a>Aby zmienić kolor ekranu lub odwrotne

1. Wybierz opcję **koloru ekranu** selektora lub **kolor odwrotność** selektora.

1. Wybierz kolor na podstawie **kolory** palety w **kolory** okna.

   Kolor dopełniający jest przypisywany do innych selektora.

   > [!TIP]
   > Po dwukrotnym kliknięciu **koloru ekranu** lub **kolor odwrotność** selektor [okno dialogowe selektora kolorów niestandardowych](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md) pojawia się.

## <a name="use-the-256-color-palette"></a>Użyj palety 256 kolorów

Za pomocą **obraz** edytora, ikon i kursorów można wielkości dużych (64 × 64) z palety 256 kolorów do wyboru. Po utworzeniu zasobu stylu obrazu urządzenia jest zaznaczone.

### <a name="to-create-a-256-color-icon-or-cursor"></a>Tworzenie ikony 256 kolorów lub kursora

1. W [widok zasobów](../windows/resource-view-window.md), kliknij prawym przyciskiem myszy plik .rc, a następnie wybierz **Wstaw zasobów** z menu skrótów. (Jeśli masz już istniejący zasób obrazu w pliku .rc, takich jak kursora, możesz kliknąć prawym przyciskiem myszy **kursora** i wybierz polecenie **wstawiania kursora** z menu skrótów.)

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. W [Wstaw zasób — okno dialogowe](../windows/add-resource-dialog-box.md), wybierz opcję **ikonę** lub **kursora** i wybierz polecenie **New**.

1. Na **obraz** menu, wybierz opcję **nowy obraz urządzenia**.

1. Wybierz żądany styl obrazu 256 kolorów.

### <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>Aby wybrać kolor z palety 256 kolorów dla dużych ikon

Aby narysować przy zaznaczeniem z palety 256 kolorów, musisz wybrać kolory z **kolory** palety w [okno kolorów](../windows/colors-window-image-editor-for-icons.md).

1. Wybierz kursor lub duże ikony, lub Utwórz nową ikonę dużych lub kursor.

1. Wybierz kolor z 256 kolorów, które są wyświetlane w **kolory** palety w **kolory** okna.

   Kolor wybrany staną się bieżący kolor w **kolory** palety w **kolory** okna.

   > [!NOTE]
   > Pasuje do początkowej palety 256 kolorów obrazów palety zwracany przez `CreateHalftonePalette` interfejsu Windows API. Wszystkie ikony przeznaczone dla powłoki Windows należy używać tej palety, aby zapobiec migotania podczas realizacji palety.

## <a name="set-a-cursor39s-hot-spot"></a>Ustaw kursor&#39;s aktywny

Aktywnego punktu kursora jest punktem, do której Windows odwołuje się w śledzeniu pozycja kursora. Domyślnie ustawiono punkt aktywny w lewym górnym rogu kursora (współrzędne 0,0). **Informacji o hotspotach** właściwość [okno właściwości](/visualstudio/ide/reference/properties-window) zawiera współrzędne punktu aktywnego.

### <a name="to-set-a-cursors-hot-spot"></a>Aby ustawić aktywnego punktu kursora

1. Na [paska narzędzi edytora obrazów](../windows/toolbar-image-editor-for-icons.md), wybierz **Ustaw punkt aktywny** narzędzia.

1. Wybierz piksel, który ma zostać przypisany jako aktywnego punktu kursora.

   **Informacji o hotspotach** właściwość **właściwości** okno wyświetla nowy współrzędnych.

   > [!TIP]
   > Etykietki narzędzi są wyświetlane po umieszczeniu kursora na przycisku paska narzędzi. Poniższe wskazówki mogą pomóc w identyfikacji funkcji każdego przycisku.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz także

[Menu obrazu](../windows/image-menu-image-editor-for-icons.md)<br/>
[Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)<br/>
[Ikony](/windows/desktop/menurc/icons)<br/>
[Kursory](/windows/desktop/menurc/cursors)<br/>
[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
