---
title: Edytor paska narzędzi (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.toolbar.F1
- vc.editors.toolbar
- vc.editors.newtoolbarresource
helpviewer_keywords:
- resource editors [C++], Toolbar editor
- editors, toolbars
- toolbars [C++], editing
- Toolbar editor
- toolbars [C++], creating
- Toolbar editor [C++], creating new toolbars
- Insert Resource
- bitmaps [C++], converting to toolbars
- Toolbar editor [C++], converting bitmaps
- toolbars [C++], converting bitmaps
- New Toolbar Resource dialog box [C++]
- buttons [C++], custom toolbars
- toolbar buttons [C++], editing
- buttons
- toolbar buttons [C++], creating
- Toolbar editor [C++], creating buttons
- toolbar buttons [C++], button image
- toolbar buttons [C++], creating
- toolbar buttons (in Toolbar editor)
- toolbar buttons [C++], moving
- Toolbar editor [C++], moving buttons
- Toolbar editor [C++], copying buttons
- toolbars [C++], copying buttons
- toolbar buttons [C++], copying
- toolbar buttons [C++], deleting
- Toolbar editor [C++], deleting buttons
- Toolbar editor [C++], spacing toolbar buttons
- toolbar buttons [C++], space between buttons
- toolbar controls [MFC], command ID
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- command IDs, toolbar buttons
- size, toolbar buttons
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- status bars [C++], active toolbar button text
- command IDs, toolbar buttons
- width, toolbar buttons
- tool tips [C++], adding to toolbar buttons
- "\n in tool tip"
- toolbar buttons [C++], tool tips
- buttons [C++], tool tips
- Toolbar editor [C++], creating tool tips
ms.assetid: aa9f0adf-60f6-4f79-ab05-bc330f15ec43
ms.openlocfilehash: 61b4d3ba6fc70e78c6f794528822eb66fb94de7e
ms.sourcegitcommit: 5a7dbd640376e13379f5d5b2cf66c4842e5e737b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55905787"
---
# <a name="toolbar-editor-c"></a>Edytor paska narzędzi (C++)

**Narzędzi** Edytor pozwala na tworzenie zasobów narzędzi języka C++ i konwertowanie map bitowych na zasoby paska narzędzi. **Narzędzi** Edytor używa graficzne przedstawienie, aby pokazać pasek narzędzi i przyciski, które przypominają, jak będzie wyglądać w ukończonej aplikacji.

**Narzędzi** okna edytora wyświetla dwa widoki obrazu przycisku, taka sama jak okno edytora obrazów. Pasek podziału rozdziela dwa okienka. Aby zmieniać względne rozmiary okienek, można przeciągać pasek podziału. Aktywne okienko wyświetla krawędź wyboru. Powyższe dwa widoki obrazu jest narzędzi podmiotu.

![Edytor paska narzędzi](../mfc/media/vctoolbareditor.gif "vcToolbarEditor") Edytor paska narzędzi

**Narzędzi** edytora jest podobny do **obraz** edytora w działaniu. Elementy menu, Narzędzia grafiki i mapy bitowej siatki są takie same jak w **obraz** edytora. Polecenia menu **obraz** menu, aby możliwe było przełączać się między **narzędzi** edytora i **obraz** edytora. Aby uzyskać więcej informacji na temat korzystania z **grafiki** narzędzi **kolory** palety, lub **obraz** menu, zobacz [edytora obrazów](../windows/image-editor-for-icons.md).

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

Za pomocą **narzędzi** edytora, możesz:

## <a name="create-new-toolbars"></a>Tworzenie nowych pasków narzędzi

1. W **zasobów** wyświetlić, kliknij prawym przyciskiem myszy plik .rc, a następnie wybierz **Dodaj zasób** z menu skrótów. (Jeśli masz istniejący pasek narzędzi w pliku .rc, użytkownik może po prostu kliknij prawym przyciskiem myszy **narzędzi** i wybierz polecenie **Wstaw narzędzi** z menu skrótów.)

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. W **Dodaj zasób** okno dialogowe, wybierz opcję **narzędzi** w **typ zasobu** , a następnie wybierz **New**.

   Jeśli znak plus (**+**) pojawia się obok **narzędzi** typ zasobu oznacza że narzędzi szablony są dostępne. Wybierz znak plus, aby rozwinąć listę szablonów, wybierz szablon, a następnie wybierz **New**.

## <a name="convert-bitmaps-to-toolbar-resources"></a>Konwertowanie map bitowych na zasoby paska narzędzi

Aby utworzyć nowy pasek narzędzi w projektu w języku C++, konwertowania mapy bitowej. Konwertuje grafiki z mapy bitowej obrazy przycisków na pasku narzędzi. Zazwyczaj mapy bitowej zawiera kilka obrazów przycisku w postaci bitmapy z jednego obrazu dla każdego przycisku. Jako wartość domyślna to 16 pikseli szerokości i wysokości obrazu, obrazy mogą być dowolnego rozmiaru. Można określić rozmiar obrazów przycisku w **nowy zasób paska narzędzi** okno dialogowe, w przypadku wybrania **Edytor paska narzędzi** z **obraz** menu znajduje się w edytorze obrazu.

**Nowy zasób paska narzędzi** okno dialogowe umożliwia określenie szerokości i wysokości przyciski dodawania zasobu paska narzędzi w projekcie C++. Wartość domyślna to 16 x 15 pikseli.

Mapa bitowa, który jest używany do tworzenia paska narzędzi ma maksymalną szerokość 2048. Jeśli ustawisz **szerokość przycisku** do 512, możesz mieć tylko cztery przyciski. Ustaw szerokość 513, może mieć tylko trzy przyciski.

Okno dialogowe ma następujące właściwości:

|Właściwość|Opis|
|---|---|
|**Szerokość przycisku.**|Miejsce na wprowadź szerokość przycisków paska narzędzi, które konwertowania zasób mapy bitowej do zasobu paska narzędzi. Obrazy są obcinane do szerokości i wysokości określone i kolory są dostosowane by wykorzystywały standardowe kolory paska narzędzi (16 kolorów).|
|**Wysokość przycisku**|Miejsce na Wprowadź wysokość przycisków paska narzędzi, które konwertowania zasób mapy bitowej do zasobu paska narzędzi. Obrazy są obcinane do szerokości i wysokości określone i kolory są dostosowane by wykorzystywały standardowe kolory paska narzędzi (16 kolorów).|

### <a name="to-convert-bitmaps-to-a-toolbar"></a>Aby przekonwertować map bitowych paska narzędzi

1. Otwórz istniejący zasób mapy bitowej w [edytora obrazów](../windows/image-editor-for-icons.md). (Jeśli mapa bitowa nie jest już w pliku .rc, kliknij prawym przyciskiem myszy plik .rc, wybierz polecenie **importu** z menu skrótów, przejdź do mapy bitowej, które chcesz dodać do pliku .rc, a następnie wybierz **Otwórz**.)

1. Z **obraz** menu, wybierz **Edytor paska narzędzi**.

   **Nowy zasób paska narzędzi** pojawi się okno dialogowe. Można zmienić szerokość i wysokość obrazy ikon, aby dopasować mapę bitową. Obraz paska narzędzi są następnie wyświetlane na pasku narzędzi edytora.

1. Aby zakończyć konwersję, zmień polecenie **identyfikator** za pomocą przycisku [okno właściwości](/visualstudio/ide/reference/properties-window). Wpisz nowy **identyfikator** lub wybierz **identyfikator** z listy rozwijanej.

   > [!TIP]
   > **Właściwości** okno zawiera przycisk pinezki na pasku tytułu. Wybranie tego przycisku Włącza lub wyłącza **Autoukrywanie** okna. Aby szybko przechodzić przez wszystkie właściwości przycisku paska narzędzi bez konieczności ponownie otworzyć windows pojedynczej właściwości, należy wyłączyć **Autoukrywanie** wyłączyć tak **właściwości** okna pozostaje stacjonarnych.

Możesz również zmienić identyfikatory poleceń przyciski na nowy pasek narzędzi, za pomocą [okno właściwości](/visualstudio/ide/reference/properties-window).

## <a name="create-move-and-edit-toolbar-buttons"></a>Tworzenie, przenoszenie i edytowanie przycisków paska narzędzi

Można łatwo utworzyć, przenoszenie, kopiowanie i edytowanie przycisków paska narzędzi.

Domyślnie przycisk Nowy lub pusty jest wyświetlany po prawej stronie paska narzędzi. Możesz przenieść ten przycisk, przed jego edycji. Podczas tworzenia nowego przycisku po prawej stronie przycisku edycji pojawi się kolejny przycisk puste. Pasek narzędzi, pusty przycisk nie jest zapisywany.

Właściwości przycisku paska narzędzi są:

|Właściwość|Opis|
|--------------|-----------------|
|**Identyfikator**|Określa identyfikator przycisku. Listy rozwijanej udostępnia typowe **identyfikator** nazwy.|
|**Szerokość**|Określa szerokość przycisku. zalecane jest 16 pikseli.|
|**Wysokość**|Określa wysokość przycisku. Wysokość jednego przycisku zmienia wysokość wszystkie przyciski na pasku narzędzi. Zaleca się 15 pikseli.|
|**wiersz**|Określa komunikat wyświetlany na pasku stanu. Dodawanie \n i nazwę dodaje etykietkę narzędzia do tego przycisku paska narzędzi. Aby uzyskać więcej informacji, zobacz [tworzeniem etykietki narzędzi](../windows/creating-a-tool-tip-for-a-toolbar-button.md).|

**Szerokość** i **wysokość** dotyczą wszystkich przycisków. Mapa bitowa, który jest używany do tworzenia paska narzędzi ma maksymalną szerokość 2048. Dlatego jeśli szerokość przycisku równa 512, może mieć tylko cztery przyciski i jeśli szerokość równa 513, może mieć tylko trzy przyciski.

Zobacz następujące akcje:

### <a name="to-create-a-new-toolbar-button"></a>Aby utworzyć nowego przycisku paska narzędzi

1. W [widok zasobów](../windows/resource-view-window.md) rozwiń folder zasobów (na przykład *Project1.rc*).

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. Rozwiń **narzędzi** folder i wybierz pasek narzędzi do edycji.

1. Identyfikator należy przypisać pusty przycisk po prawej stronie paska narzędzi. Możesz to zrobić, edytując **identyfikator** właściwość [okno właściwości](/visualstudio/ide/reference/properties-window). Na przykład można podać tej samej opcji menu przycisku paska narzędzi. W tym przypadku użyj pola listy rozwijanej, aby wybrać **identyfikator** opcji menu.

   —lub—

   Wybierz pusty przycisk po prawej stronie paska narzędzi (w **pasek narzędzi widoku** okienko) i rozpocząć rysowania. Domyślny przycisk polecenia identyfikator jest przypisywany (ID_BUTTON\<n >).

Można również skopiuj i Wklej obraz jest jako nowego przycisku paska narzędzi.

### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>Aby dodać obraz do paska narzędzi, jak przycisk

1. W [widok zasobów](../windows/resource-view-window.md), Otwórz pasek narzędzi, klikając go dwukrotnie.

1. Następnie otwórz obraz, który chcesz dodać do paska narzędzi.

   > [!NOTE]
   > Jeśli otworzysz go w programie Visual Studio, zostanie on otwarty w **obraz** edytora. Można również otworzyć obrazu w innych programach grafiki.

1. Z **Edytuj** menu, wybierz **kopiowania**.

1. Przejdź do paska narzędzi, wybierając jego kartę w górnej części okna źródła.

1. Z **Edytuj** menu, wybierz **Wklej**.

   Obraz pojawi się na pasku narzędzi jako nowy przycisk.

### <a name="to-move-a-toolbar-button"></a>Aby przenieść przycisk paska narzędzi

W **pasek narzędzi widoku** okienku przeciągnij przycisk, który ma zostać przeniesiony do nowej lokalizacji, na pasku narzędzi.

### <a name="to-copy-buttons-from-a-toolbar"></a>Kopiowanie przycisków z paska narzędzi

1. Naciśnij i przytrzymaj **Ctrl** klucza.

1. W **pasek narzędzi widoku** okienku przeciągnij przycisk do jednej nowej lokalizacji na pasku narzędzi lub do lokalizacji na inny pasek narzędzi.

### <a name="to-delete-a-toolbar-button"></a>Aby usunąć przycisku paska narzędzi

Wybierz przycisk paska narzędzi i przeciągnij go poza pasek narzędzi.

### <a name="to-insert-or-remove-space-between-buttons-on-a-toolbar"></a>Aby wstawić lub usuwanie odstępów między przyciskami na pasku narzędzi

Ogólnie rzecz biorąc Aby wstawić odstęp między przyciskami, przeciągnij je od siebie nawzajem na pasku narzędzi. Aby usunąć przestrzeń, przeciągnij je do siebie nawzajem.

|Akcja|Krok|
|------|------|
|Aby wstawić odstęp przed przycisk, który nie jest następuje spacja|Przeciągnij przycisk po prawej stronie lub w dół do momentu widoczny w połowie o jej nakłada przycisk Dalej.|
|Wstaw spację przed przycisk, który następuje spacja i zachować spacje końcowe|Przeciągnij przycisk, aż do prawej lub dolnej krawędzi zachodzi po prostu przycisk Dalej, lub po prostu nakłada się.|
|Wstaw spację przed przycisk, który następuje spacja i zamknąć tego następujące miejsce|Przeciągnij przycisk po prawej stronie lub w dół do momentu widoczny w połowie o jej nakłada przycisk Dalej.|
|Aby usunąć odstępów między przyciskami na pasku narzędzi|Przeciągnij przycisk na jednej stronie miejsca kierunku przycisku po drugiej stronie miejsca, dopóki nie nakłada się przycisk Następny temat w połowie.|

> [!NOTE]
> Jeśli nie ma już miejsca obok przycisku, który przeciąga opuszczenie i przycisk przeciągnąć ponad połowie ostatnie sąsiadujących przycisku **narzędzi** edytora również jest wstawiana w przeciwną stronę przycisku, który masz przeciąganie.

### <a name="to-change-the-properties-of-a-toolbar-button"></a>Aby zmienić właściwości przycisku paska narzędzi

1. W projekcie w języku C++ kliknij przycisk paska narzędzi.

1. Wpisz nowy identyfikator w **identyfikator** właściwość [okno właściwości](/visualstudio/ide/reference/properties-window), lub użyj listy rozwijanej, aby wybrać nowy **identyfikator**.

### <a name="to-create-a-tool-tip-for-a-toolbar-button"></a>Aby utworzyć etykietki narzędzia dla przycisku kontrolki toolbar

1. Wybierz przycisk paska narzędzi.

1. W [okno właściwości](/visualstudio/ide/reference/properties-window)w **monitu** właściwość pola, Dodaj opis przycisku na pasek stanu; po wiadomości, dodać `\n` i nazwa Porada narzędzia.

Typowym przykładem etykietki narzędzia jest **drukowania** znajdujący się w **WordPad**:

1. Otwórz **WordPad**.

1. Umieść wskaźnik myszy nad **drukowania** przycisku paska narzędzi.

1. Należy zauważyć, że wyraz `Print` teraz zmiennoprzecinkowych pod wskaźnika myszy.

1. Spójrz na pasku stanu (w dolnej części **WordPad** okna)-Zwróć uwagę, że teraz zawiera tekst `Prints the active document`.

`Print` w **kroku 3** nazywa się "narzędzia poradę," i `Prints the active document` z **kroku 4** "Opis przycisk na pasku stanu."

Jeśli chcesz, aby ten efekt przy użyciu **narzędzi** edytorze ustaw **monitu** właściwość `Prints the active document\nPrint`.

> [!NOTE]
> Możesz edytować tekst monitu przy użyciu [okno właściwości](/visualstudio/ide/reference/properties-window).

## <a name="requirements"></a>Wymagania

ATL i MFC

## <a name="see-also"></a>Zobacz także

[Edytory zasobów](../windows/resource-editors.md)<br/>
[Menu i inne zasoby](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)<br/>
[Właściwości przycisku paska narzędzi](../windows/toolbar-button-properties.md)<br/>
