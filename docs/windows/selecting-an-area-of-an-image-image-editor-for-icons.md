---
title: 'Instrukcje: Edytowanie obrazu'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.editing
helpviewer_keywords:
- Image editor [C++], image selection
- Image editor [C++], selecting images
- images [C++], selecting
- cursors [C++], selecting areas of
- Image editor [C++], editing images
- Clipboard [C++], pasting
- images [C++], editing
- images [C++], deleting selected parts
- images [C++], copying selected parts
- images [C++], moving selected parts
- images [C++], dragging and replicating selected parts
- images [C++], pasting into
- graphics [C++], editing
- Image editor [C++], flipping and rotating images
- images [C++], flipping
- images [C++], rotating
- Image editor [C++], resizing images
- graphics [C++], resizing
- images [C++], resizing
- resizing images
- size [C++], images
- images [C++], cropping
- images [C++], extending
- Image editor [C++], cropping or extending images
- Image editor [C++], shrinking and stretching images
- images [C++], stretching
- images [C++], shrinking
- bitmaps [C++], shrinking
- bitmaps [C++], stretching
- Image editor [C++], editing images
- images [C++], editing
- images [C++], properties
- Image editor [C++], Properties window
- Properties window, image editor
ms.assetid: 8b6ce4ad-eba1-4ece-86ba-cea92c3edff2
ms.openlocfilehash: 9324e3dc5c6691a7b50f137da1fad446b416e968
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167852"
---
# <a name="how-to-edit-an-image"></a>Instrukcje: Edytowanie obrazu

Narzędzia do zaznaczania umożliwiają definiowanie obszaru obrazu, który ma zostać wycięty, skopiowany, usunięty, zmiana rozmiaru, odwrócenie lub przeniesienie. Za pomocą narzędzia do **zaznaczania prostokąta** można definiować i wybierać prostokątny region obrazu. Za pomocą narzędzia **nieregularnego wyboru** można narysować konspekt odręczny dla obszaru, który ma zostać wybrany dla operacji wycinania, kopiowania lub innej.

> [!NOTE]
> Zobacz **Zaznaczanie prostokątne** i **Narzędzia nieregularnego wyboru** na [pasku narzędzi edytora obrazu](../windows/toolbar-image-editor-for-icons.md) lub Wyświetl etykietki narzędzi skojarzonych z każdym przyciskiem na pasku narzędzi **edytora obrazów** .

Możesz również utworzyć niestandardowy pędzel na podstawie zaznaczenia. Aby uzyskać więcej informacji, zobacz [Tworzenie pędzla niestandardowego](../windows/creating-a-custom-brush-image-editor-for-icons.md).

## <a name="how-to"></a>Instrukcje

Aby edytować obraz, zobacz How to:

### <a name="to-select-an-image"></a>Aby wybrać obraz

1. Użyj paska narzędzi **edytora obrazu** lub przejdź do menu **obrazu** > **Narzędzia** , a następnie wybierz odpowiednie narzędzie do zaznaczania.

1. Przesuń punkt wstawiania do jednego rogu obszaru obrazu, który chcesz wybrać. Krzyżyki są wyświetlane, gdy punkt wstawiania znajduje się na obrazie.

1. Przeciągnij punkt wstawiania do przeciwległego rogu obszaru, który chcesz wybrać. Prostokąt pokazuje, które piksele zostaną wybrane. Wszystkie piksele w obrębie prostokąta, w tym te pod prostokątem, są uwzględniane w zaznaczeniu.

1. Zwolnij przycisk myszy. Obramowanie zaznaczenia obejmuje wybrany obszar.

#### <a name="to-select-an-entire-image"></a>Aby wybrać cały obraz

Wybierz obraz spoza bieżącego zaznaczenia. Obramowanie zaznaczenia zmieni fokus i ponownie obejmie cały obraz.

### <a name="to-edit-parts-of-an-image"></a>Aby edytować części obrazu

Możesz wykonywać standardowe operacje edycji — wycinanie, kopiowanie, czyszczenie i przesuwanie — w [wyborze](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md), niezależnie od tego, czy zaznaczenie jest całym obrazem, czy tylko jego częścią. Ponieważ **Edytor obrazów** używa **Schowka systemu Windows**, można przenieść obrazy między **edytorem obrazów** a innymi aplikacjami dla systemu Windows.

Ponadto można zmienić rozmiar zaznaczenia, niezależnie od tego, czy zawiera on cały obraz, czy tylko część.

#### <a name="to-cut-the-current-selection-and-move-it-to-the-clipboard"></a>Aby wyciąć bieżące zaznaczenie i przenieść je do schowka

Przejdź do menu **edytuj** > **Wytnij**.

#### <a name="to-copy-the-selection"></a>Aby skopiować zaznaczenie

1. Umieść wskaźnik wewnątrz obramowania zaznaczenia lub w dowolnym miejscu, z wyjątkiem uchwytów zmiany rozmiarów.

1. Przytrzymaj wciśnięty klawisz **Ctrl** podczas przeciągania zaznaczenia do nowej lokalizacji. Obszar oryginalnego zaznaczenia jest niezmieniony.

1. Aby skopiować zaznaczenie do obrazu w jego bieżącej lokalizacji, wybierz pozycję poza kursorem zaznaczenia.

#### <a name="to-paste-the-clipboard-contents-into-an-image"></a>Aby wkleić zawartość schowka do obrazu

1. Przejdź do menu **edytuj** > **Wklej**.

   Zawartość schowka, otoczona obramowaniem zaznaczenia, pojawia się w lewym górnym rogu okienka.

1. Umieść wskaźnik wewnątrz obramowania zaznaczenia i przeciągnij obraz do odpowiedniej lokalizacji na obrazie.

1. Aby zakotwiczenie obrazu w nowej lokalizacji, wybierz poza obramowaniem zaznaczenia.

#### <a name="to-delete-the-current-selection-without-moving-it-to-the-clipboard"></a>Aby usunąć bieżące zaznaczenie bez przechodzenia do schowka

Przejdź do menu **edytuj** > **Usuń**.

   Oryginalny obszar zaznaczenia jest wypełniony bieżącym kolorem tła.

> [!NOTE]
> Aby uzyskać dostęp do poleceń **wycinania**, **kopiowania**, **wklejania**i **usuwania** , kliknij prawym przyciskiem myszy w oknie **Widok zasobów** .

#### <a name="to-move-the-selection"></a>Aby przenieść zaznaczenie

1. Umieść wskaźnik wewnątrz obramowania zaznaczenia lub w dowolnym miejscu, z wyjątkiem uchwytów zmiany rozmiarów.

1. Przeciągnij zaznaczenie do nowej lokalizacji.

1. Aby zakotwiczenie zaznaczenia w obrazie w nowej lokalizacji, zaznacz poza obramowaniem zaznaczenia.

Aby uzyskać więcej informacji na temat rysowania przy użyciu zaznaczenia, zobacz [Tworzenie pędzla niestandardowego](../windows/creating-a-custom-brush-image-editor-for-icons.md).

### <a name="to-flip-an-image"></a>Aby przerzucić obraz

Możesz przerzucić lub obrócić obraz, aby utworzyć lustrzane odbicie obrazu oryginalnego, obrócić obraz o 180 stopni lub obrócić obraz do prawej strony o 90 ° w danym momencie.

- Aby przerzucić obraz w poziomie (Obraz lustrzany), przejdź do **obrazu** menu > **Przerzuć w poziomie**.

- Aby przerzucić obraz w pionie (obrócić o 180 stopni), przejdź do menu **obraz** > **Przerzuć w pionie**.

- Aby obrócić obraz 90 stopni, przejdź do **obrazu** menu, > **obrócić 90 stopni**.

   > [!NOTE]
   > Możesz również użyć [klawiszy skrótów](../windows/accelerator-keys-image-editor-for-icons.md) dla tych poleceń lub uzyskać dostęp do poleceń z menu skrótów (wybierz poza obrazem w **Edytorze obrazów**).

### <a name="to-resize-an-image"></a>Aby zmienić rozmiar obrazu

Zachowanie **edytora obrazu** podczas zmiany rozmiarów obrazu zależy od tego, czy [wybrano](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) cały obraz, czy jego część.

Gdy zaznaczenie zawiera tylko część obrazu, **Edytor obrazów** zmniejsza zaznaczenie, usuwając wiersze lub kolumny pikseli i wypełniając regiony opuszczone bieżącym kolorem tła. Może również rozciągnąć zaznaczenie poprzez duplikowanie wierszy lub kolumn pikseli.

Gdy zaznaczenie zawiera cały obraz, **Edytor obrazów** zmniejsza i rozciąga obraz albo przycina i rozszerza.

Istnieją dwa mechanizmy zmiany rozmiarów obrazu: uchwyty zmiany rozmiarów i [okno właściwości](/visualstudio/ide/reference/properties-window). Przeciągając uchwyty rozmiaru, można zmienić rozmiar całości lub części obrazu. Rozmiary uchwytów, które można przeciągać, są trwałe. Nie można przeciągać uchwytów, które są puste. Użyj okna **Właściwości** , aby zmienić rozmiar całego obrazu, a nie na wybraną część.

![Uchwyty zmiany rozmiarów mapy bitowej](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")<br/>
Uchwyty zmiany rozmiarów

> [!NOTE]
> Jeśli opcja **Siatka kafelków** została wybrana w [oknie dialogowym Ustawienia siatki](../windows/grid-settings-dialog-box-image-editor-for-icons.md), zmiany rozmiarów są przyciągane do następnej linii siatki kafelków. Jeśli wybrano tylko opcję **Siatka pikseli** (ustawienie domyślne), zmiany rozmiarów są przyciągane do następnego dostępnego piksela.

#### <a name="to-resize-an-entire-image-using-the-properties-window"></a>Aby zmienić rozmiar całego obrazu przy użyciu okna właściwości

1. Otwórz obraz, którego właściwości chcesz zmienić.

1. W polach **Szerokość** i **wysokość** w [okno właściwości](/visualstudio/ide/reference/properties-window)wpisz żądane wymiary.

   W przypadku zwiększenia rozmiaru obrazu **Edytor obrazów** rozszerza obraz z prawej strony, w dół lub w dół i wypełnia nowy region bieżącym kolorem tła. Obraz nie jest rozciągany.

   W przypadku skrócenia rozmiaru obrazu **Edytor obrazów** przycina obraz do prawej lub dolnej krawędzi lub obu tych elementów.

   > [!NOTE]
   > Właściwości **Width** i **Height** można użyć do zmiany rozmiaru tylko całego obrazu, a nie do zmiany rozmiaru częściowego zaznaczenia.

#### <a name="to-crop-or-extend-an-entire-image"></a>Aby przyciąć lub zwiększyć cały obraz

1. Zaznacz cały obraz.

   Jeśli część obrazu jest obecnie zaznaczona i chcesz zaznaczyć cały obraz, zaznacz dowolne miejsce w obrazie poza bieżącym obramowaniem zaznaczenia.

1. Przeciągnij uchwyt zmiany rozmiaru do momentu, gdy obraz będzie miał właściwy rozmiar.

Zwykle **Edytor obrazów** przycina lub powiększa obraz, gdy zmieniasz jego rozmiar, przenosząc uchwyt zmiany rozmiaru. Jeśli przytrzymasz klawisz **SHIFT** podczas przenoszenia uchwytu zmiany rozmiaru, **Edytor obrazów** zmniejsza lub rozciąga obraz.

#### <a name="to-shrink-or-stretch-an-entire-image"></a>Aby zmniejszyć lub rozciągnąć cały obraz

1. Zaznacz cały obraz.

   Jeśli część obrazu jest obecnie zaznaczona i chcesz zaznaczyć cały obraz, zaznacz dowolne miejsce w obrazie poza bieżącym obramowaniem zaznaczenia.

1. Przytrzymaj wciśnięty klawisz **SHIFT** i przeciągnij uchwyt zmiany rozmiaru do momentu, gdy obraz będzie prawidłowym rozmiarem.

#### <a name="to-shrink-or-stretch-part-of-an-image"></a>Aby zmniejszyć lub rozciągnąć część obrazu

1. Zaznacz część obrazu, którego rozmiar chcesz zmienić. Aby uzyskać więcej informacji, zobacz [Zaznaczanie obszaru obrazu](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md).

1. Przeciągnij jeden z uchwytów rozmiaru do momentu, aż wybór będzie prawidłowym rozmiarem.

### <a name="to-edit-an-image-outside-of-a-project"></a>Aby edytować obraz poza projektem

Możesz otwierać i edytować obrazy w środowisku deweloperskim tak samo jak w przypadku dowolnej aplikacji graficznej, na przykład otwierając mapę bitową do edycji autonomicznej. Obrazy, z którymi pracujesz, nie muszą być częścią projektu programu Visual Studio.

1. Przejdź do **pliku** menu, > **Otwórz**.

1. W polu **Pliki typu** wybierz pozycję **wszystkie pliki**.

1. Zlokalizuj i Otwórz obraz, który chcesz edytować.

### <a name="to-change-image-properties"></a>Aby zmienić właściwości obrazu

Można ustawić lub zmodyfikować właściwości obrazu przy użyciu [okno właściwości](/visualstudio/ide/reference/properties-window).

1. Otwórz obraz w **Edytorze obrazu**.

1. W oknie **Właściwości** zmień dowolne lub wszystkie właściwości obrazu.

   |Właściwość|Opis|
   |--------------|-----------------|
   |**Kolory**|Określa schemat kolorów obrazu. Wybierz opcję **monochromatyczna**, **16**lub **256**lub **True Color**.<br/><br/>Jeśli obraz został już narysowany z 16-kolorową paletą, wybranie opcji **monochromatyczny** powoduje, że dla kolorów na obrazie są nastawiane elementy czarno-białe. Kontrast nie jest zawsze utrzymywany: na przykład przyległe obszary czerwone i zielone są konwertowane na czerń.|
   |**Nazwa pliku**|Określa nazwę pliku obrazu.<br/><br/>Domyślnie program Visual Studio przypisuje podstawową nazwę pliku utworzoną przez usunięcie pierwszych czterech znaków ("IDB_") z domyślnego identyfikatora zasobu (IDB_BITMAP1) i dodanie odpowiedniego rozszerzenia. Nazwa pliku obrazu w tym przykładzie byłaby *BITMAP1. bmp*. Można zmienić nazwę *MYBITMAP1. bmp*.|
   |**Proporcj**|Ustawia wysokość obrazu (w pikselach). Wartość domyślna to 48.<br/><br/>Obraz zostanie przycięty lub zostanie dodane miejsce poniżej istniejącego obrazu.|
   |**Identyfikator**|Ustawia identyfikator zasobu.<br/><br/>W przypadku obrazu Microsoft Visual Studio domyślnie przypisuje następny dostępny identyfikator w serii: IDB_BITMAP1, IDB_BITMAP2 i tak dalej. Podobne nazwy są używane dla ikon i kursorów.|
   |**Palety**|Zmienia właściwości koloru.<br/><br/>Kliknij dwukrotnie, aby wybrać kolor i wyświetlić [okno dialogowe selektora kolorów niestandardowych](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md). Zdefiniuj kolor, wpisując wartości RGB lub HSL w odpowiednich polach tekstowych.|
   |**SaveCompressed**|Wskazuje, czy obraz jest w formacie skompresowanym. Ta właściwość jest tylko do odczytu.<br/><br/>Program Visual Studio nie pozwala na zapisywanie obrazów w skompresowanym formacie, dlatego w przypadku obrazów utworzonych w programie Visual Studio ta właściwość będzie **fałszywa**. W przypadku otwarcia skompresowanego obrazu (utworzonego w innym programie) w programie Visual Studio ta właściwość będzie **prawdziwa**. Jeśli zapiszesz skompresowany obraz przy użyciu programu Visual Studio, zostanie on zdekompresowany i zostanie przywrócona **wartość false**.|
   |**Szerokość**|Ustawia szerokość obrazu (w pikselach). Wartość domyślna dla map bitowych to 48.<br/><br/>Obraz zostanie przycięty lub puste miejsce jest dodawane z prawej strony istniejącego obrazu.|

## <a name="requirements"></a>Wymagania

None

## <a name="see-also"></a>Zobacz też

[Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)<br/>
[Instrukcje: Tworzenie ikony lub innego obrazu](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Instrukcje: korzystanie z narzędzia do rysowania](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Instrukcje: korzystanie z koloru](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
