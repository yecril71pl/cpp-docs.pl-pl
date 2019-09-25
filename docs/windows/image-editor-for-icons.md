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
ms.openlocfilehash: 0f8fe228b804538b6a0d0377f05d79c34e787587
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "69514218"
---
# <a name="image-editor-for-icons-c"></a>Edytor obrazów dla ikon (C++)

Po wybraniu pliku obrazu (takiego jak ICO, BMP, PNG) w **Eksplorator rozwiązań**obraz zostanie otwarty w **Edytorze obrazów** w taki sam sposób, jak pliki kodu otwierają się w **edytorze kodu**. Gdy karta **Edytor obrazu** jest aktywna, są wyświetlane paski narzędzi z wieloma narzędziami do tworzenia i edytowania obrazów. Oprócz map bitowych, ikon i kursorów można edytować obrazy w formacie GIF lub JPEG przy użyciu poleceń z menu **obraz** i narzędzi na pasku narzędzi **edytora obrazu** .

Zasoby graficzne to obrazy zdefiniowane dla aplikacji. Możesz rysować odręczne lub rysować przy użyciu kształtów. Można wybrać fragmenty obrazu do edycji, odwrócenia lub zmiany rozmiarów lub można utworzyć niestandardowy pędzel z wybranej części obrazu i rysować z tym pędzlem. Można definiować właściwości obrazu, zapisywać obrazy w różnych formatach i konwertować obrazy z jednego formatu na inny.

> [!NOTE]
> Korzystając z **edytora obrazów**, można wyświetlać obrazy 32-bitowe, ale nie można ich edytować.

Można również użyć **edytora obrazów** i [edytora binarnego](binary-editor.md) do pracy z plikami zasobów w projektach zarządzanych. Wszelkie zarządzane zasoby, które chcesz edytować, muszą być powiązanymi zasobami. Edytory zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych.

Oprócz tworzenia nowych zasobów graficznych można [zaimportować istniejące obrazy](../windows/how-to-copy-resources.md#import-and-export-resources) do edycji, a następnie dodać je do projektu. Możesz również otwierać i edytować obrazy, które nie są częścią projektu, na potrzeby [edycji obrazów](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md)autonomicznych.

Aby uzyskać informacje na temat **edytora obrazów**, zobacz jak [utworzyć ikonę lub inny obraz](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md), [edytować obraz](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md), [użyć narzędzia do rysowania](../windows/using-a-drawing-tool-image-editor-for-icons.md), [pracy z kolorem](../windows/working-with-color-image-editor-for-icons.md)i [klawiszy skrótów](../windows/accelerator-keys-image-editor-for-icons.md).

> [!NOTE]
> Pobierz bez kosztów **Biblioteka obrazów programu Visual Studio** , która zawiera wiele animacji, map bitowych i ikon, których możesz używać w aplikacjach. Aby uzyskać więcej informacji dotyczących sposobu pobierania biblioteki, zobacz [Biblioteka obrazów programu Visual Studio](/visualstudio/designers/the-visual-studio-image-library).

## <a name="image-menu"></a>Menu obrazu

Menu **obraz** , które pojawia się tylko wtedy, gdy **Edytor obrazu** jest aktywny, zawiera polecenia służące do edytowania obrazów, zarządzania paletami kolorów oraz ustawiania opcji okna **edytora obrazu** . Ponadto polecenia dotyczące korzystania z obrazów urządzeń są dostępne podczas pracy z ikonami i kursorami.

|Polecenie|Opis|
|---|---|
|**Odwróć kolory**|Odwraca kolory.|
|**Przerzuć w poziomie**|Przerzuca obraz lub zaznaczenie w poziomie.|
|**Przerzuć w pionie**|Przerzuca obraz lub zaznaczenie w pionie.|
|**Obróć o 90 stopni**|Obraca obraz lub zaznaczenie o 90 stopni.|
|**Pokaż okno kolorów**|Otwiera okno **kolory** , w którym można wybrać kolory do użycia w obrazie.|
|**Użyj zaznaczenia jako pędzla**|Umożliwia utworzenie pędzla niestandardowego na podstawie fragmentu obrazu.<br/><br/>Wybór zostanie przekształcony w niestandardowy Pędzel, który dystrybuuje kolory w zaznaczeniu na obrazie. Kopie zaznaczenia są pozostawiane wzdłuż ścieżki przeciągania. Im wolniej przeciągniesz, tym więcej kopii jest wykonanych.|
|**Kopiuj i zaznacz konspekt**|Tworzy kopię bieżącego zaznaczenia i zawiera jej obramowanie.<br/><br/>Jeśli kolor tła jest zawarty w bieżącym zaznaczeniu, zostanie on wykluczony, jeśli wybrano opcję przezroczysty.
|**Dostosuj kolory**|Otwiera **Selektor niestandardowego koloru**, który pozwala na dostosowanie kolorów używanych dla obrazu.|
|**Załaduj paletę**|Otwiera okno dialogowe **paleta kolorów** , dzięki któremu można załadować kolory palety wcześniej zapisane w pliku. PAL.|
|**Zapisz paletę**|Zapisuje kolory palety w pliku. PAL.|
|**Rysuj nieprzezroczyste**|Gdy ta opcja jest zaznaczona, bieżące zaznaczenie staje się nieprzezroczyste.<br/><br/>Gdy jest wyczyszczone, sprawia, że bieżące zaznaczenie jest przezroczyste.|
|**Edytor paska narzędzi**|Otwiera [okno dialogowe Nowy zasób paska narzędzi](../windows/new-toolbar-resource-dialog-box.md).|
|**Ustawienia siatki**|Otwiera okno dialogowe **Ustawienia siatki** , w którym można określić siatki dla obrazu.|
|**Nowy typ obrazu**|Otwiera [okno dialogowe \<nowe urządzenie > typ obrazu](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md).<br/><br/>Zasób o pojedynczej ikonie może zawierać kilka obrazów o różnych rozmiarach, a system Windows może użyć odpowiedniego rozmiaru ikony w zależności od tego, jak ma być wyświetlana. Nowy typ urządzenia nie modyfikuje rozmiaru ikony, ale zamiast tego tworzy nowy obraz w obrębie ikony. Dotyczy tylko ikon i kursorów.|
|**Bieżąca ikona/typ obrazu kursora**|Otwiera podmenu, w którym znajduje się lista pierwszych dziewięciu dostępnych obrazów kursorów lub ikon. Ostatnie polecenie w podmenu, **więcej**, otwiera okno [dialogowe Otwórz \<urządzenie > obrazu](../windows/open-device-image-dialog-box-image-editor-for-icons.md).|
|**Usuń typ obrazu**|Usuwa wybrany obraz urządzenia.|
|**Narzędzia**|Uruchamia podmenu, które zawiera wszystkie narzędzia dostępne na pasku narzędzi **edytora obrazu** .|

Okno dialogowe **Ustawienia siatki** umożliwia określenie ustawień siatki obrazu i wyświetla linie siatki na edytowanym obrazie. Linie są przydatne do edycji obrazu, ale nie są zapisywane jako część obrazu.

|Właściwość|Opis|
|---|---|
|**Siatka pikseli**|Po zaznaczeniu tej opcji wyświetlana jest siatka dookoła każdego piksela w **Edytorze obrazu**.<br/><br/>Siatka pojawia się tylko na 4 × i wyższych rozdzielczościach.|
|**Siatka kafelków**|Po wybraniu Wyświetla siatkę dookoła bloków pikseli w **Edytorze obrazu**, określoną przez wartości odstępów siatki.|
|**Szerokość**|Określa szerokość każdego bloku kafelków.<br/><br/>Ta właściwość jest przydatna podczas rysowania map bitowych zawierających wiele obrazów, które są ułożone w regularnych odstępach czasu.|
|**Proporcj**|Określa wysokość każdego bloku kafelków.<br/><br/>Ta właściwość jest przydatna podczas rysowania map bitowych zawierających wiele obrazów, które są ułożone w regularnych odstępach czasu.|

## <a name="toolbar"></a>Pasek narzędzi

Pasek narzędzi **edytora obrazów** zawiera narzędzia do rysowania, malowania, wprowadzania tekstu, wymazywania i manipulowania widokami. Zawiera również selektor opcji, za pomocą którego można wybrać opcje używania poszczególnych narzędzi. Można na przykład wybrać różne szerokości pędzla, współczynniki powiększenia i style linii.

Wszystkie narzędzia dostępne na pasku narzędzi **edytora obrazów** są również dostępne w**narzędziach** **obrazu** > menu. Aby użyć paska narzędzi **edytora obrazów** i selektora **opcji** , wybierz odpowiednie narzędzie lub opcję.

![Pasek narzędzi edytora obrazów](../mfc/media/vcimageeditortoolbar.gif "vcImageEditorToolbar")<br/>
Pasek narzędzi **edytora obrazów**

> [!TIP]
> Etykietki narzędzi są wyświetlane po umieszczeniu wskaźnika myszy na przycisku paska narzędzi. Te porady mogą ułatwić identyfikację funkcji poszczególnych przycisków.

Ponieważ wiele narzędzi do rysowania jest dostępnych na [klawiaturze](../windows/accelerator-keys-image-editor-for-icons.md), czasami warto ukryć pasek narzędzi **edytora obrazu** .

- Aby wyświetlić lub ukryć pasek narzędzi **edytora obrazów** , przejdź do **widoku** > menu**paski narzędzi** i wybierz **Edytor obrazów**.

> [!NOTE]
> Elementy z tego paska narzędzi będą wyświetlane jako niedostępne, gdy plik obrazu z bieżącego projektu lub rozwiązania nie zostanie otwarty w **Edytorze obrazu**.

### <a name="option-selector"></a>selektor opcji

Za pomocą selektora **opcji** można określić szerokość linii, pociągnięcia pędzla i inne. Ikona przycisku selektora **opcji** zmienia się w zależności od wybranego narzędzia.

![Selektor&#45;kształtu rysowania na pasku narzędzi edytora obrazów](../mfc/media/vcimageeditortoolbaroptionselector.gif "vcImageEditorToolbarOptionSelector")<br/>
Selektor **opcji** na pasku narzędzi **edytora obrazów**

### <a name="text-tool"></a>Narzędzie tekstowe

Za pomocą okna dialogowego **Narzędzie tekstowe** można dodać tekst do kursora, mapy bitowej lub zasobu ikony.

Aby uzyskać dostęp do tego okna dialogowego, **Otwórz Edytor obrazów** i przejdź do menu**Narzędzia** **obrazu** > , a następnie wybierz polecenie **tekst narzędzia** .

> [!TIP]
> Możesz kliknąć prawym przyciskiem myszy okno dialogowe **narzędzia tekstowe** , aby uzyskać dostęp do domyślnego menu skrótów zawierającego listę standardowych poleceń systemu Windows.

Otwórz okno dialogowe **czcionka narzędzia tekstowe** , aby zmienić czcionkę, styl lub rozmiar czcionki kursora. Zmiany są stosowane do tekstu wyświetlanego w obszarze **tekstu** .

Aby uzyskać dostęp do tego okna dialogowego, wybierz przycisk **czcionki** w oknie dialogowym **narzędzia tekstowe** . Dostępne są następujące właściwości:

|Właściwość|Opis|
|---|---|
|**Czcionka**|Wyświetla listę dostępnych czcionek.|
|**Styl czcionki**|Wyświetla listę dostępnych stylów dla określonej czcionki.|
|**Zmienia**|Wyświetla listę dostępnych rozmiarów punktów dla określonej czcionki.|
|**Northwind**|Pokazuje przykład sposobu wyświetlania tekstu z określonymi ustawieniami czcionki.|
|**Skrypt**|Wyświetla listę dostępnych skryptów języka dla określonej czcionki.<br/><br/>Po wybraniu innego skryptu języka zestaw znaków dla tego języka będzie dostępny do tworzenia dokumentów wielojęzycznych.|

#### <a name="to-change-the-font-of-text-on-an-image"></a>Aby zmienić czcionkę tekstu w obrazie

Oto przykład sposobu dodawania tekstu do ikony w aplikacji systemu Windows i manipulowania czcionką tekstu.

1. Utwórz aplikację C++ Windows Formsową. Aby uzyskać szczegółowe informacje [, zobacz How to: Utwórz aplikacje](/previous-versions/visualstudio/visual-studio-2008/s69bf10x(v%3dvs.90))Windows Forms. Plik *. ico aplikacji* jest domyślnie dodawany do projektu.

1. W **Eksplorator rozwiązań**kliknij dwukrotnie plik *App. ico*. Zostanie otwarty **Edytor obrazów** .

1. Przejdź do menu**Narzędzia** **obrazu** > i wybierz **Narzędzie Tekst**.

1. W oknie dialogowym **Narzędzie tekstowe** wpisz *C++* pusty obszar tekstu. Ten tekst będzie widoczny w polu o zmiennym rozmiarze znajdującym się w lewym górnym rogu *aplikacji App. ico* w **Edytorze obrazu**.

1. W **Edytorze obrazów**przeciągnij pole o zmiennym rozmiarze do centrum *App. ico* , aby zwiększyć czytelność tekstu.

1. W oknie dialogowym **Narzędzie tekstowe** wybierz przycisk **czcionka** .

1. W oknie dialogowym **czcionka narzędzia tekstowego** :

   - Wybierz pozycję **Times New Roman** z listy dostępnych czcionek, które są wymienione w polu listy **czcionka** .

   - Wybierz pozycję **pogrubienie** z listy dostępnych stylów czcionki w polu listy **styl czcionki** .

   - Wybierz pozycję **10** z listy dostępnych rozmiarów punktów wymienionych w polu listy **rozmiar** .

   - Wybierz **OK**. Zostanie zamknięte okno dialogowe **czcionka narzędzia tekstowego** i nowe ustawienia czcionki zostaną zastosowane do tekstu.

1. Wybierz **Zamknij** w oknie dialogowym **Narzędzie tekstowe** . Pole o zmiennym rozmiarze wokół tekstu zniknie z **edytora obrazu**.

W obszarze tekstowym zostanie wyświetlony tekst wyświetlany jako część zasobu. Początkowo ten obszar jest pusty.

> [!NOTE]
> W przypadku ustawienia **przezroczystego tła** tylko tekst zostanie umieszczony w obrazie. W przypadku ustawienia **tła nieprzezroczystego** prostokąt ograniczenia wypełniony kolorem tła zostanie umieszczony za tekstem.

## <a name="window-panes"></a>Okienka

W oknie **Edytor obrazów** są wyświetlane dwa widoki obrazu z paskiem podziału rozdzielającym dwa okienka. Aby zmieniać względne rozmiary okienek, można przeciągać pasek podziału. Aktywne okienko wyświetla krawędź wyboru.

Jeden widok jest rzeczywistym rozmiarem, a drugi jest powiększony przez domyślny współczynnik powiększenia 6. Widoki w tych dwóch okienkach są aktualizowane automatycznie. wszystkie zmiany wprowadzone w jednym okienku są natychmiast wyświetlane w drugim. Dwa okienka ułatwiają pracy nad powiększonym widokiem obrazu, w którym można odróżnić poszczególne piksele i, w tym samym czasie, obserwować efekt pracy na widoku rzeczywistego obrazu.

W okienku po lewej stronie jest używane tyle miejsca, ile jest to konieczne (do połowy okna **obrazu** ), aby wyświetlić domyślny widok powiększenia 1:1 obrazu. W okienku po prawej stronie jest wyświetlany domyślny obraz powiększenia o powiększeniu 6:1. Powiększenie można zmienić w każdym okienku przy użyciu narzędzia **Powiększ** na pasku narzędzi **edytora obrazu** lub przy użyciu klawiszy skrótów.

Możesz powiększyć mniejsze okienko okna **edytora obrazów** i użyć dwóch okienek, aby pokazać różne regiony dużego obrazu. Wybierz wewnątrz okienka, aby je wybrać.

Względne rozmiary okienek można zmienić, umieszczając wskaźnik na pasku podziału i przesuwając pasek podziału w prawo lub w lewo. Pasek podziału może poruszać się po obu stronach, jeśli chcesz korzystać tylko z jednego okienka.

Jeśli okienko **edytora obrazu** zostanie powiększone o współczynnik 4 lub większy, można wyświetlić siatkę pikseli, która ogranicza poszczególne piksele w obrazie.

### <a name="to-change-the-magnification-factor"></a>Aby zmienić współczynnik powiększenia

Domyślnie **Edytor obrazów** wyświetla widok w okienku po lewej stronie w rzeczywistym rozmiarze i widok w okienku po prawej stronie o 6 razy większym rozmiarze. Współczynnik powiększenia (widoczny na pasku stanu w dolnej części obszaru roboczego) jest stosunkiem między rzeczywistym rozmiarem obrazu a wyświetlanym rozmiarem. Domyślnym czynnikiem jest 6, a zakresem jest z zakresu od 1 do 10.

1. Wybierz okienko **edytora obrazu** , którego współczynnik powiększenia chcesz zmienić.

1. Na pasku narzędzi **edytora obrazu** wybierz strzałkę po prawej stronie narzędzia **Powiększ** i wybierz współczynnik powiększenia z podmenu: **1x**, **2x**, **6X**lub **8x**.

   > [!NOTE]
   > Aby wybrać współczynnik powiększenia inny niż wymienione w narzędziu **Powiększ** , użyj klawiszy skrótów.

### <a name="to-display-or-hide-the-pixel-grid"></a>Aby wyświetlić lub ukryć siatkę pikseli

Dla wszystkich okienek **edytora obrazu** o współczynniku powiększenia równym 4 lub większym, można wyświetlić siatkę, która ogranicza poszczególne piksele w obrazie.

1. Przejdź do pozycji menu**Ustawienia siatki** **obrazu** > .

1. Zaznacz pole wyboru **Siatka pikseli** , aby wyświetlić siatkę, lub wyczyść pole, aby ukryć siatkę.

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz także

[Edytory zasobów](../windows/resource-editors.md)<br/>
[Ikony](/windows/win32/menurc/icons)