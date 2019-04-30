---
title: 'Instrukcje: Edytowanie obrazu'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.editing
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
ms.openlocfilehash: 849da0d14987a057d39d5f9531e97545b3d4b8cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387959"
---
# <a name="how-to-edit-an-image"></a>Instrukcje: Edytowanie obrazu

Narzędzia wyboru służy do definiowania obszar obrazu, który ma być wycinanie, kopiowanie, wyczyść, zmienić rozmiar, Odwróć lub przenoszenie. Za pomocą **prostokąta zaznaczenia** narzędzie można definiować i wybierz prostokątny obszar obrazu. Za pomocą **kształt** narzędzia można narysować freehand konspektu obszaru, który chcesz wybrać opcjami wycinania, kopiowania lub inna operacja.

> [!NOTE]
> Zobacz **prostokąta zaznaczenia** i **kształt** na schemacie narzędzia [paska narzędzi edytora obrazów](../windows/toolbar-image-editor-for-icons.md) lub wyświetlanie etykietek narzędzi, skojarzone z każdego przycisku w **Edytora obrazów** paska narzędzi.

Można również utworzyć niestandardowy obiekt brush z zaznaczenia. Aby uzyskać więcej informacji, zobacz [Tworzenie pędzla niestandardowego](../windows/creating-a-custom-brush-image-editor-for-icons.md).

## <a name="how-to"></a>Instrukcje

Aby edytować obraz, zobacz jak:

### <a name="to-select-an-image"></a>Aby wybrać obraz

1. Użyj **edytora obrazów** paska narzędzi lub przejdź do menu **obraz** > **narzędzia** i wybierz narzędzie wyboru mają.

1. Przesuń punkt wstawiania do jednego rogu obszaru obrazu, który ma zostać wybrana. Na ekranie są wyświetlane, gdy punkt wstawiania znajduje się na obrazie.

1. Przeciągnij kursor przeciwległego rogu obszaru, który ma zostać wybrana. Prostokąt pokazuje, które piksele zostanie wybrany. Wszystkie piksele w obrębie prostokąta, łącznie z tymi w ramach prostokąt, są uwzględnione w zaznaczeniu.

1. Zwolnij przycisk myszy. Obramowanie wyboru otacza zaznaczonego obszaru.

#### <a name="to-select-an-entire-image"></a>Aby wybrać całego obrazu

Wybierz obraz poza bieżącym zaznaczeniu. Krawędź zaznaczenia zmienia fokus i obejmuje cały obraz jeszcze raz.

### <a name="to-edit-parts-of-an-image"></a>Edytowanie części obrazu

Można wykonywać operacje edycji standard — wycinanie, kopiowanie, czyszczenie i przenoszenie — na [wybór](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)na to, czy zaznaczenie jest całego obrazu lub po prostu jego część. Ponieważ **edytora obrazów** używa **Schowka Windows**, mogą przesyłać obrazy między **edytora obrazów** i inne aplikacje dla Windows.

Ponadto możesz zmienić rozmiar zaznaczenia, czy obejmuje cały obraz lub po prostu części.

#### <a name="to-cut-the-current-selection-and-move-it-to-the-clipboard"></a>Wytnij bieżącego zaznaczenia i przenieś go do Schowka

Przejdź do menu **Edytuj** > **Wytnij**.

#### <a name="to-copy-the-selection"></a>Aby skopiować zaznaczenie

1. Umieść kursor wewnątrz obramowania zaznaczenia lub dowolnego miejsca na nim, z wyjątkiem uchwytów zmiany rozmiaru.

1. Naciśnij i przytrzymaj **Ctrl** klucza jako przeciągnij je do nowej lokalizacji. Obszar oryginalnego zaznaczenia pozostaje niezmieniony.

1. Aby skopiować zaznaczenie do obrazu w jego bieżącej lokalizacji, wybierz poza kursor wyboru.

#### <a name="to-paste-the-clipboard-contents-into-an-image"></a>Wklej zawartość Schowka do obrazu

1. Przejdź do menu **Edytuj** > **Wklej**.

   Zawartość Schowka otoczone obramowaniem zaznaczenia, są wyświetlane w lewym górnym rogu okienka.

1. Umieść kursor w granicach obramowania zaznaczenia, a następnie przeciągnij obraz do żądanej lokalizacji na obrazie.

1. Aby móc zakotwiczyć obrazu w nowej lokalizacji, wybierz poza krawędź zaznaczenia.

#### <a name="to-delete-the-current-selection-without-moving-it-to-the-clipboard"></a>Aby usunąć bieżące zaznaczenie bez przenoszenia go do Schowka

Przejdź do menu **Edytuj** > **Usuń**.

   Oryginalny obszar zaznaczenia jest wypełniany z bieżącym kolorem tła.

> [!NOTE]
> Możesz uzyskać dostęp **Wytnij**, **kopiowania**, **Wklej**, i **Usuń** polecenia, klikając prawym przyciskiem myszy **widok zasobów** okna.

#### <a name="to-move-the-selection"></a>Aby przenieść zaznaczenie

1. Umieść kursor wewnątrz obramowania zaznaczenia lub dowolnego miejsca na nim, z wyjątkiem uchwytów zmiany rozmiaru.

1. Przeciągnij zaznaczenie do nowej lokalizacji.

1. Aby móc zakotwiczyć zaznaczenia w obrazie w nowej lokalizacji, wybierz poza krawędź zaznaczenia.

Aby uzyskać więcej informacji na temat rysowanie przy zaznaczeniem, zobacz [Tworzenie pędzla niestandardowego](../windows/creating-a-custom-brush-image-editor-for-icons.md).

### <a name="to-flip-an-image"></a>Aby przerzucić obraz

Można obracać lub obraz, aby utworzyć obraz lustrzany oryginał, nogami obrazu lub obrócić obraz w prawo o 90 stopni w danym momencie.

- Aby przerzucić obraz w poziomie (obraz), przejdź do menu **obraz** > **Przerzuć w poziomie**.

- Aby przerzucić obraz w pionie (nogami), przejdź do menu **obraz** > **Przerzuć w pionie**.

- Aby obrócić obraz o 90 stopni, przejdź do menu **obraz** > **Obrót o 90 stopni**.

   > [!NOTE]
   > Można również użyć [klawisze skrótów (skrót)](../windows/accelerator-keys-image-editor-for-icons.md) dla tych poleceń lub uzyskać dostęp do poleceń menu skrótów (Wybierz poza obrazu podczas w **edytora obrazów**).

### <a name="to-resize-an-image"></a>Zmiana rozmiaru obrazu

Zachowanie **edytora obrazów** podczas zmiany rozmiaru obrazu zależy od tego, czy masz [wybranego](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) całego obrazu lub jego część.

Jeśli zaznaczenie obejmuje tylko część obrazu, **edytora obrazów** zmniejsza zaznaczenie przy usuwaniu wierszy lub kolumn pikseli i wypełniania opuszczonych regionów z bieżącym kolorem tła. Można również rozciągać zaznaczenie zduplikowane wiersze lub kolumny w pikselach.

Jeśli zaznaczenie obejmuje cały obraz **edytora obrazów** albo zmniejsza rozciąga obrazu lub przycina i rozszerza je.

Istnieją dwa mechanizmy do zmiany rozmiaru obrazu: uchwytów zmiany rozmiaru i [okno właściwości](/visualstudio/ide/reference/properties-window). Przeciągnij uchwyty zmiany rozmiaru, aby zmienić rozmiar wszystkich lub część obrazu. Uchwyty zmiany rozmiaru, które można przeciągać są wypełnione. Nie można przeciągnąć uchwyty, które są puste. Użyj **właściwości** okna, aby zmienić rozmiar całego tylko obraz nie jest częścią wybrane.

![Uchwytów na mapę bitową](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")<br/>
Uchwyty zmiany rozmiaru

> [!NOTE]
> Jeśli masz **Kafelek siatki** opcji wybranej w [okno dialogowe Ustawienia siatki](../windows/grid-settings-dialog-box-image-editor-for-icons.md), następnie zmiany rozmiaru przyciąganie do następnego wiersza siatki kafelka. Jeśli tylko **siatkę pikseli** opcja jest zaznaczone (ustawienie domyślne), zmiana rozmiaru przyciąganie do następnego dostępne pikseli.

#### <a name="to-resize-an-entire-image-using-the-properties-window"></a>Zmiana rozmiaru całego obrazu w oknie właściwości

1. Otwórz obraz, którego właściwości chcesz zmienić.

1. W **szerokość** i **wysokość** pola [okno właściwości](/visualstudio/ide/reference/properties-window), wpisz wymiary, które mają.

   Jeśli masz zwiększenie rozmiaru obrazu, **edytora obrazów** rozszerza obraz w prawo, dół, i / lub i wypełnia nowego regionu z bieżącym kolorem tła. Obraz, który nie jest rozciągana.

   Jeśli skrócić rozmiar obrazu, **edytora obrazów** Przycina obraz w prawo lub dolnej krawędzi i / lub.

   > [!NOTE]
   > Możesz użyć **szerokość** i **wysokość** właściwości, aby zmienić rozmiar tylko całego obrazu, nie można zmienić rozmiar częściowy wybór.

#### <a name="to-crop-or-extend-an-entire-image"></a>Przycinanie lub rozszerzanie całego obrazu

1. Wybierz obraz.

   Jeśli część obrazu jest aktualnie zaznaczona, a chcesz wybrać całego obrazu, wybierz dowolne miejsce dla obrazu spoza bieżącego zaznaczenia.

1. Przeciągnij uchwyt zmiany rozmiaru, do momentu zilustrowano wielkości.

Zwykle **edytora obrazów** Przycina lub powiększenie obrazu, gdy jej rozmiar, przenosząc uchwyt zmiany rozmiaru. Przytrzymanie **Shift** kluczy po przeniesieniu uchwyt zmiany rozmiaru **edytora obrazów** zmniejsza lub obraz jest rozciągany tak.

#### <a name="to-shrink-or-stretch-an-entire-image"></a>Aby zmniejszanie i rozciąganie całego obrazu

1. Wybierz obraz.

   Jeśli chcesz wybrać całego obrazu część obrazu jest aktualnie zaznaczona, wybierz dowolne miejsce dla obrazu spoza bieżącego zaznaczenia.

1. Naciśnij i przytrzymaj **Shift** klucza, a następnie przeciągnij uchwyt zmiany rozmiaru, do momentu zilustrowano wielkości.

#### <a name="to-shrink-or-stretch-part-of-an-image"></a>Aby zmniejszanie i rozciąganie części obrazu

1. Wybierz część obrazu, który chcesz zmienić. Aby uzyskać więcej informacji, zobacz [Zaznaczanie obszaru obrazu](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md).

1. Przeciągnij jeden z uchwytów zmiany rozmiaru, dopóki nie obowiązuje wielkości.

### <a name="to-edit-an-image-outside-of-a-project"></a>Edytowanie obrazu spoza projektu

Możesz otwierać i edytować obrazy w środowisku programistycznym, tak samo jak w dowolnej aplikacji grafiki, na przykład otwierając mapę bitową do edycji autonomicznych. Obrazów, z którymi pracujesz nie muszą być częścią projektu programu Visual Studio.

1. Przejdź do menu **pliku** > **Otwórz**.

1. W **pliki typu** wybierz opcję **wszystkie pliki**.

1. Znajdź i Otwórz obraz, który chcesz edytować.

### <a name="to-change-image-properties"></a>Aby zmienić właściwości obrazu

Można ustawić lub zmodyfikować właściwości obrazu, użyj [okno właściwości](/visualstudio/ide/reference/properties-window).

1. Otwórz obraz w **edytora obrazów**.

1. W **właściwości** okna, zmiana dowolnych lub wszystkich właściwości dla obrazu.

   |Właściwość|Opis|
   |--------------|-----------------|
   |**Kolory**|Określa schemat kolorów dla obrazu. Wybierz **monochromatyczny**, **16**, lub **256**, lub **True Color**.<br/><br/>Jeśli została już rysowania obrazu z paletę 16 kolorów, wybranie opcji **monochromatyczny** powoduje, że podstawienia białe kolorów na obrazie. Kontrast nie jest zawsze utrzymywane: na przykład obszarami pokrewnymi czerwonego i zielonego są zarówno konwertowane na czarny.|
   |**Nazwa pliku**|Określa nazwę pliku obrazu.<br/><br/>Domyślnie program Visual Studio przypisuje podstawowej nazwy pliku tworzone przez usunięcie pierwsze cztery znaki ("IDB_") z domyślnego identyfikatora zasobu (IDB_BITMAP1) i dodawanie odpowiedniego rozszerzenia. Nazwa pliku obrazu, w tym przykładzie byłaby *BITMAP1.bmp*. Można zmienić jego nazwę *MYBITMAP1.bmp*.|
   |**Wysokość**|Określa wysokość obrazu (w pikselach). Wartość domyślna to 48.<br/><br/>Obraz zostanie przycięty lub puste miejsce jest dodawana poniżej istniejącego obrazu.|
   |**Identyfikator**|Ustawia identyfikator zasobu.<br/><br/>Obraz programu Microsoft Visual Studio domyślnie przypisuje następny dostępny identyfikator w serii: IDB_BITMAP1 IDB_BITMAP2 i tak dalej. Podobne nazwy są używane do ikony i kursory.|
   |**Paleta**|Zmiany kolorów właściwości.<br/><br/>Kliknij dwukrotnie, aby wybrać kolor i wyświetlić [okno dialogowe selektora kolorów niestandardowych](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md). Zdefiniuj kolor, wpisując wartości RGB lub HSL w odpowiednich polach.|
   |**SaveCompressed**|Wskazuje, czy obraz jest w formacie skompresowanym. Ta właściwość jest tylko do odczytu.<br/><br/>Visual Studio nie zezwala na zapisywanie obrazów w formacie skompresowany, więc wszystkie obrazy utworzone w programie Visual Studio, ta właściwość będzie miał **False**. Jeśli otworzysz skompresowanego obrazu (utworzonym w innym programie) w programie Visual Studio, ta właściwość będzie miał **True**. Jeśli zapiszesz skompresowanego obrazu za pomocą programu Visual Studio, będzie ona bez kompresji i ta właściwość zostanie przywrócona do **False**.|
   |**Szerokość**|Ustawia szerokość obrazu (w pikselach). Wartość domyślna dla map bitowych to 48.<br/><br/>Obraz zostanie przycięty lub puste miejsce zostanie dodany do istniejącego obrazu po prawej stronie.|

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz także

[Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)<br/>
[Instrukcje: Tworzenie ikony lub innego obrazu](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Instrukcje: Używanie narzędzia do rysowania](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Instrukcje: Praca z kolorami](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)<br/>