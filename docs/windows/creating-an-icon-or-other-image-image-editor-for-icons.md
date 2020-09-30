---
title: 'Instrukcje: Tworzenie ikony lub innego obrazu'
ms.date: 02/15/2019
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
ms.openlocfilehash: bbaa008d8dac74588fc15bfebbc7cb2611260349
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504558"
---
# <a name="how-to-create-an-icon-or-other-image"></a>Instrukcje: Tworzenie ikony lub innego obrazu

Można utworzyć nowy obraz, mapę bitową, ikonę, kursor lub pasek narzędzi, a następnie użyć **edytora obrazów** , aby dostosować jego wygląd. Po [szablonie zasobu](./how-to-create-a-resource-script-file.md)można także utworzyć nową mapę bitową.

## <a name="icons-and-cursors-image-resources-for-display-devices"></a>Ikony i kursory: zasoby obrazów do wyświetlania na urządzeniach

Ikony i kursory są zasobami graficznymi, które mogą zawierać wiele obrazów w różnych rozmiarach i schematach kolorów dla różnych typów urządzeń wyświetlających. Kursor ma także gorącą lokalizację, której system Windows używa do śledzenia jej pozycji. Obie ikony i kursory są tworzone i edytowane przy użyciu **edytora obrazów**, podobnie jak mapy bitowe i inne obrazy.

Po utworzeniu nowej ikony lub kursora **Edytor obrazu** najpierw tworzy obraz typu standardowego. Obraz jest początkowo wypełniony kolorem ekranu (przezroczystym). Jeśli obraz jest kursorem, punkt aktywny jest początkowo lewym górnym rogu ze współrzędnymi `0,0` .

Domyślnie **Edytor obrazów** obsługuje tworzenie dodatkowych obrazów dla urządzeń przedstawionych w poniższej tabeli. Możesz tworzyć obrazy dla innych urządzeń, wpisując szerokość, Wysokość i parametry liczby kolorów w oknie dialogowym **obrazu niestandardowego** .

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

### <a name="create-a-device-image-icon-or-cursor"></a>Tworzenie obrazu urządzenia (ikona lub kursor)

Po utworzeniu nowego zasobu ikony lub kursora **Edytor obrazu** najpierw tworzy obraz w określonym stylu (32 × 32, 16 kolorów dla ikon i 32 × 32, monochromatyczny dla kursorów). Następnie można dodać obrazy w różnych rozmiarach i stylach do początkowej ikony lub kursora oraz edytować każdy dodatkowy obraz w razie potrzeby dla różnych urządzeń wyświetlających. Możesz również edytować obraz przy użyciu operacji wycinania i wklejania z istniejącego typu obrazu lub z mapy bitowej utworzonej w programie graficznym.

Po otwarciu ikony lub zasobu kursora w [Edytorze obrazów](../windows/image-editor-for-icons.md), obraz najlepiej pasujący do bieżącego urządzenia wyświetlającego jest domyślnie otwierany.

> [!NOTE]
> Jeśli projekt nie zawiera jeszcze pliku. RC, zobacz [Tworzenie nowego pliku skryptu zasobu](../windows/how-to-create-a-resource-script-file.md).

**Nowe okno &lt; dialogowe &gt; Typ obrazu urządzenia** umożliwia utworzenie nowego obrazu urządzenia określonego typu. Aby otworzyć okno dialogowe **Nowy \<Device> obraz** , przejdź do menu **obrazu**  >  **nowy typ obrazu**. Dostępne są następujące właściwości **typu obrazu docelowego** i **niestandardowego**.

Właściwość **Typ obrazu docelowego** zawiera listę dostępnych typów obrazów, w których wybierasz typ obrazu, który chcesz otworzyć:

:::row:::
   :::column span="":::
      16 x 16, 16 kolorów \
      32 x 32, 16 kolorów \
      48 x 48, 16 kolorów \
      64 x 64, 16 kolorów \
      96 x 96, 16 kolorów
   :::column-end:::
   :::column span="":::
      16 x 16, 256 kolorów \
      32 x 32, 256 kolory \
      48 x 48, 256 kolory \
      64 x 64, 256 kolory \
      96 x 96, 256 kolory
   :::column-end:::
   :::column span="":::
      16 x 16, Monochromatycznie \
      32 x 32, Monochromatycznie \
      48 x 48, Monochromatycznie \
      64 x 64, Monochromatycznie \
      96 x 96, Monochromatycznie
   :::column-end:::
:::row-end:::

> [!NOTE]
> Wszystkie istniejące obrazy nie będą wyświetlane na tej liście.

Właściwość **Custom** otwiera okno dialogowe **obrazu niestandardowego** , w którym można utworzyć nowy obraz z niestandardowym rozmiarem i liczbą kolorów.

Okno dialogowe **obraz niestandardowy** umożliwia tworzenie nowego obrazu z niestandardowym rozmiarem i liczbą kolorów. Dostępne są następujące właściwości:

|Właściwość|Opis|
|---|---|
|**Szerokość**|Miejsce na wprowadzenie szerokości obrazu niestandardowego w pikselach (1-512, limit 2048).|
|**Proporcj**|Miejsce, w którym można wprowadzić wysokość obrazu niestandardowego w pikselach (1-512, limit 2048).|
|**Kolory**|Miejsce, w którym można wybrać liczbę kolorów obrazu niestandardowego: 2, 16 lub 256.|

Za pomocą okna dialogowego **Otwórz &lt; &gt; obraz urządzenia** można otworzyć obrazy urządzeń w projektach języka C++. Wyświetla listę istniejących obrazów urządzeń w bieżącym zasobie (obrazy, które są częścią bieżącego zasobu). Uwzględniona jest następująca Właściwość:

|Właściwość|Opis|
|---|---|
|**Bieżące obrazy**|Wyświetla listę obrazów zawartych w zasobie. Wybierz typ obrazu, który chcesz otworzyć.|

#### <a name="to-create-a-new-icon-or-cursor"></a>Aby utworzyć nową ikonę lub kursor

1. W [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources)kliknij prawym przyciskiem myszy plik *. RC* , a następnie wybierz polecenie **Wstaw zasób**. Jeśli masz już istniejący zasób obrazu w pliku *. RC* , taki jak kursor, kliknij prawym przyciskiem myszy folder **kursor** i wybierz polecenie **Wstaw kursor**.

1. W [oknie dialogowym Wstawianie zasobu](./how-to-create-a-resource-script-file.md)wybierz **ikonę** lub **kursor** i wybierz pozycję **Nowy**. W przypadku ikon ta akcja powoduje utworzenie zasobu ikony z ikoną 32 × 32, 16-kolorową. W przypadku kursorów tworzony jest obraz 32 × 32 i monochromatyczny (2-kolorowe).

   Jeśli znak plus ( **+** ) pojawia się obok pola Typ zasobu obrazu w oknie dialogowym **Wstawianie zasobu** , oznacza to, że dostępne są szablony paska narzędzi. Wybierz znak plus, aby rozwinąć listę szablonów, wybierz szablon i wybierz pozycję **Nowy**.

### <a name="to-add-an-image-for-a-different-display-device"></a>Aby dodać obraz dla innego urządzenia wyświetlającego

1. Przejdź do menu **obrazu**  >  **nowy obraz urządzenia**lub kliknij prawym przyciskiem myszy w **okienku Edytora obrazów** i wybierz polecenie **nowy obraz urządzenia**.

1. Wybierz typ obrazu, który chcesz dodać. Możesz również wybrać opcję **niestandardowe** , aby utworzyć ikonę, której rozmiar nie jest dostępny na liście domyślnej.

### <a name="to-copy-a-device-image"></a>Aby skopiować obraz urządzenia

1. Przejdź do menu **obraz**,  >  **Otwórz obraz urządzenia** i wybierz obraz z listy bieżące obrazy. Na przykład wybierz 32 × 32, 16-kolorową wersję ikony.

1. Skopiuj aktualnie wyświetlany obraz ikony (**Ctrl** + **C**).

1. Otwórz inny obraz ikony w innym oknie **edytora obrazu** . Na przykład Otwórz 16 x 16, 16-kolorowe wersje ikon.

1. Wklej obraz ikony (**Ctrl** + **V**) z jednego okna **edytora obrazu** do drugiego. Jeśli wklejasz większy rozmiar do mniejszego rozmiaru, możesz użyć uchwytów ikon, aby zmienić rozmiar obrazu.

### <a name="to-delete-a-device-image"></a>Aby usunąć obraz urządzenia

Gdy obraz ikony jest wyświetlany w **Edytorze obrazów**, przejdź do menu **obrazu**  >  **Usuń obraz urządzenia**. Usunięcie ostatniego obrazu ikony w zasobie spowoduje również usunięcie tego zasobu.

> [!NOTE]
> Po naciśnięciu klawisza **del** obrazy i kolory rysowane na ikonie zostaną usunięte, ale ikona pozostanie i będzie można ją ponownie zaprojektować. Jeśli naciśniesz klawisz **del** przez pomyłkę, naciśnij klawisz **Ctrl** + **z** , aby cofnąć akcję.

### <a name="to-create-transparent-or-inverse-regions-in-device-images"></a>Aby utworzyć regiony przezroczyste lub odwrotne w obrazach urządzeń

W [Edytorze obrazu](../windows/image-editor-for-icons.md)ikona początkowa lub obraz kursora ma atrybut przezroczysty. Chociaż obrazy ikon i kursorów są prostokątne, wiele nie pojawia się, ponieważ części obrazu są przezroczyste i obraz podstawowy na ekranie pokazuje ikonę lub kursor. Po przeciągnięciu ikony części obrazu mogą pojawić się w kolorze odwróconym. Ten efekt można utworzyć, ustawiając kolor ekranu i kolor odwrotny w [oknie kolory](./image-editor-for-icons.md).

Kolory ekranu i odwracania stosowane do ikon i kursorów mają kształt i kolor obrazu pochodnego lub do przypisywania regionów odwrotnych. Kolory wskazują części obrazu, które mają te atrybuty. Można zmienić kolory, które reprezentują atrybuty koloru ekranu i koloru odwrotnego w edycji. Zmiany te nie wpływają na wygląd ikony lub kursora w aplikacji.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w **pomocy** , w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, przejdź do menu **Narzędzia**  >  **Opcje importowania i eksportowania ustawień**. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

#### <a name="to-create-transparent-or-inverse-regions"></a>Aby utworzyć regiony przezroczyste lub odwrotne

1. W oknie **kolory** wybierz ekran selektora **— kolor** lub **kolor odwrotny**.

1. Zastosuj kolor ekranu lub odwrotnie do obrazu przy użyciu narzędzia do rysowania. Aby uzyskać więcej informacji na temat narzędzi do rysowania, zobacz [Korzystanie z narzędzia do rysowania](using-a-drawing-tool-image-editor-for-icons.md).

#### <a name="to-change-the-screen-or-inverse-color"></a>Aby zmienić kolor ekranu lub odwrotnie

1. Wybierz selektor **kolorów ekranu** lub selektor **koloru odwrotnego** .

1. Wybierz kolor z palety **kolorów** w oknie **kolory** .

   Kolor uzupełniania jest automatycznie przypisywany dla innego selektora.

   > [!TIP]
   > W przypadku dwukrotnego kliknięcia selektora kolorów **ekranu** lub **odwracania koloru** zostanie wyświetlone okno [dialogowe selektor kolorów niestandardowych](./image-editor-for-icons.md) .

### <a name="use-the-256-color-palette"></a>Korzystanie z palety kolorów 256

Korzystając z **edytora obrazów**, ikony i kursory mogą mieć duży rozmiar (64 × 64) z paletą 256 kolorów do wyboru. Po utworzeniu zasobu jest wybierany styl obrazu urządzenia.

#### <a name="to-create-a-256-color-icon-or-cursor"></a>Aby utworzyć 256-lub ikonę koloru

1. W [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources)kliknij prawym przyciskiem myszy plik *. RC* , a następnie wybierz polecenie **Wstaw zasób**. Jeśli masz już istniejący zasób obrazu w pliku *. RC* , taki jak kursor, kliknij prawym przyciskiem myszy folder **kursor** i wybierz polecenie **Wstaw kursor**.

1. W [oknie dialogowym Wstawianie zasobu](./how-to-create-a-resource-script-file.md)wybierz **ikonę** lub **kursor** i wybierz pozycję **Nowy**.

1. Przejdź do menu **obrazu**  >  **nowy obraz urządzenia** i wybierz żądany styl obrazu 256.

#### <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>Aby wybrać kolor z palety kolorów 256 dla dużych ikon

Aby narysować zaznaczenie z palety kolorów 256, należy wybrać kolory z palety **kolorów** w [oknie kolory](./image-editor-for-icons.md).

1. Wybierz dużą ikonę lub kursor lub Utwórz nową dużą ikonę lub kursor.

1. Wybierz kolor z 256 kolorów wyświetlanych w palecie **kolorów** w oknie **kolory** .

   Wybrany kolor stanie się bieżącym kolorem w palecie **kolorów** w oknie **kolory** .

   > [!NOTE]
   > Początkowa paleta używana na potrzeby obrazów kolorowych 256 jest zgodna z paletą zwróconą przez `CreateHalftonePalette` interfejs API systemu Windows. Wszystkie ikony przeznaczone dla powłoki systemu Windows powinny używać tej palety, aby zapobiec migotaniu podczas realizacji palety.

### <a name="to-set-a-cursors-hot-spot"></a>Aby ustawić punkt aktywny kursora

Gorąca plamka kursora to punkt, do którego odnoszą się okna, śledząc położenie kursora. Domyślnie punkt aktywny jest ustawiany w lewym górnym rogu kursora ze współrzędnymi `0,0` . Właściwość **hotspot** w [okno właściwości](/visualstudio/ide/reference/properties-window) pokazuje współrzędne punktu aktywnego.

1. Na [pasku narzędzi edytora obrazu](./image-editor-for-icons.md)wybierz narzędzie **Ustaw punkt aktywny** .

1. Wybierz piksel, który chcesz przypisać jako punkt aktywny kursora.

   Właściwość **hotspot** w oknie **Właściwości** wyświetla nowe współrzędne.

### <a name="to-create-and-save-a-bitmap-as-a-gif-or-jpeg"></a>Aby utworzyć i zapisać mapę bitową w formacie GIF lub JPEG

Podczas tworzenia mapy bitowej obraz jest tworzony w formacie mapy bitowej (. bmp). Można jednak zapisać obraz jako plik GIF lub JPEG albo w innym formacie graficznym.

> [!NOTE]
> Ten proces nie dotyczy ikon i kursorów.

1. Przejdź do **pliku**menu  >  **Otwórz**, a następnie wybierz pozycję **plik**.

1. W **oknie dialogowym Nowy plik**wybierz folder **Visual C++** , a następnie wybierz pozycję **plik mapy bitowej (. bmp)** w polu **Szablony** i wybierz pozycję **Otwórz**.

   Mapa bitowa zostanie otwarta w **Edytorze obrazu**.

1. Wprowadź zmiany w nowej mapie bitowej zgodnie z potrzebami.

1. Gdy mapa bitowa jest nadal otwarta w **Edytorze obrazów**, przejdź do pozycji menu **plik**  >  **Zapisz *NazwaPliku*. bmp jako**.

1. W oknie dialogowym **Zapisywanie pliku jako** wpisz nazwę, która ma zostać przypisana do pliku, a rozszerzenie, które określa format pliku, w polu **Nazwa pliku** . Na przykład *myfile.gif*.

   > [!NOTE]
   > Należy utworzyć lub otworzyć mapę bitową poza projektem, aby zapisać ją w innym formacie. Jeśli utworzysz lub otworzysz go w ramach projektu, polecenie **Zapisz jako** będzie niedostępne. Aby uzyskać więcej informacji, zobacz [Wyświetlanie zasobów w pliku skryptu zasobu poza projektem (autonomicznym)](./how-to-create-a-resource-script-file.md).

1. Wybierz pozycję **Zapisz**.

### <a name="to-convert-an-image-from-one-format-to-another"></a>Aby skonwertować obraz z jednego formatu do innego

Obrazy GIF lub JPEG można otwierać w **Edytorze obrazów** i zapisywać je jako mapy bitowe. Ponadto można otworzyć plik mapy bitowej i zapisać go jako plik GIF lub JPEG. Obrazy, z którymi pracujesz, nie muszą być częścią projektu do edycji w środowisku programistycznym (zobacz [samodzielne Edytowanie obrazu](./selecting-an-area-of-an-image-image-editor-for-icons.md)).

1. Otwórz obraz w **Edytorze obrazu**.

1. Przejdź do **pliku**menu  >  **Zapisz *nazwę pliku* jako**.

1. W oknie dialogowym **Zapisz plik jako** w polu **Nazwa pliku** wpisz nazwę pliku i rozszerzenie, które oznacza żądany format.

1. Wybierz pozycję **Zapisz**.

### <a name="to-add-a-new-image-resource-to-an-unmanaged-c-project"></a>Aby dodać nowy zasób obrazu do niezarządzanego projektu C++

1. W [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources)kliknij prawym przyciskiem myszy plik *. RC* , a następnie wybierz polecenie **Wstaw zasób**. Jeśli masz już istniejący zasób obrazu w pliku *. RC* , taki jak kursor, możesz po prostu kliknąć prawym przyciskiem myszy folder **kursor** i wybrać polecenie **Wstaw kursor**.

1. W [oknie dialogowym Wstawianie zasobu](./how-to-create-a-resource-script-file.md)wybierz typ zasobu obrazu, który chcesz utworzyć (na przykład**Mapa bitowa**), a następnie wybierz pozycję **Nowy**.

   Jeśli znak plus ( **+** ) pojawia się obok pola Typ zasobu obrazu w oknie dialogowym **Wstawianie zasobu** , oznacza to, że dostępne są szablony paska narzędzi. Wybierz znak plus, aby rozwinąć listę szablonów, wybierz szablon i wybierz pozycję **Nowy**.

### <a name="to-add-a-new-image-resource-to-a-project-in-a-net-programming-language"></a>Aby dodać nowy zasób obrazu do projektu w języku programowania .NET

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy folder projektu (na przykład *WindowsApplication1*).

1. W menu skrótów wybierz polecenie **Dodaj**, a następnie wybierz polecenie **Dodaj nowy element**.

1. W okienku **Kategorie** rozwiń folder **elementy projektu lokalnego** , a następnie wybierz **zasoby**.

1. W okienku **Szablony** wybierz typ zasobu, który chcesz dodać do projektu.

   Zasób zostanie dodany do projektu w **Eksplorator rozwiązań** , a zasób zostanie otwarty w [Edytorze obrazu](../windows/image-editor-for-icons.md). Teraz można użyć wszystkich narzędzi dostępnych w **Edytorze obrazów** do modyfikacji obrazu. Aby uzyskać więcej informacji na temat dodawania obrazów do zarządzanego projektu, zobacz [ładowanie obrazu w czasie projektowania](/dotnet/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms).

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)<br/>
[Instrukcje: Edytowanie obrazu](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Instrukcje: korzystanie z narzędzia do rysowania](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Instrukcje: korzystanie z koloru](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
<!--
[Converting Bitmaps to Toolbars](./toolbar-editor.md)<br/>
[Creating New Toolbars](./toolbar-editor.md)<br/>
[Icons](/windows/win32/menurc/icons)<br/>
[Cursors](/windows/win32/menurc/cursors)<br/>-->
