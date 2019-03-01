---
title: Edytor paska narzędzi (C++)
ms.date: 02/14/2019
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
ms.openlocfilehash: 5aadb00e6e010467ee9c70dc357916d3c4f81853
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57211085"
---
# <a name="toolbar-editor-c"></a>Edytor paska narzędzi (C++)

**Edytor paska narzędzi** pozwala na tworzenie zasobów narzędzi i konwertowanie map bitowych na zasoby paska narzędzi. **Edytor paska narzędzi** wykorzystuje graficzny widok, aby pokazać pasek narzędzi i przyciski, które przypominają, jak będzie wyglądać w ukończonej aplikacji.

**Edytor paska narzędzi** okna wyświetla dwa widoki obrazu przycisku, taka sama jak **edytora obrazów** okna. Pasek podziału rozdziela dwa okienka, a następnie można przeciągnąć pasek podziału ze strony, aby zmieniać względne rozmiary okienek. Aktywne okienko Wyświetla krawędź wyboru i ponad dwa widoki obrazu jest narzędzi podmiotu.

![Edytor paska narzędzi](../mfc/media/vctoolbareditor.gif "vcToolbarEditor")<br/>
**Edytor paska narzędzi**

**Edytor paska narzędzi** przypomina **edytora obrazów** w funkcje i elementy menu Narzędzia grafiki i siatki mapy bitowej między nimi są takie same. W znajduje się polecenie menu **obraz** menu, aby przełączać się między **Edytor paska narzędzi** i **edytora obrazów**. Aby uzyskać więcej informacji na temat korzystania z **grafiki** narzędzi **kolory** palety, lub **obraz** menu, zobacz [edytora obrazów](../windows/image-editor-for-icons.md).

Aby utworzyć nowy pasek narzędzi w projektu w języku C++, konwertowania mapy bitowej. Konwertuje grafiki z mapy bitowej obrazy przycisków na pasku narzędzi. Zazwyczaj mapy bitowej zawiera kilka obrazów przycisku w postaci bitmapy z jednego obrazu dla każdego przycisku. Jako wartość domyślna to 16 pikseli szerokości i wysokości obrazu, obrazy mogą być dowolnego rozmiaru. Można określić rozmiar obrazów przycisku w **nowy zasób paska narzędzi** okno dialogowe, w przypadku wybrania **Edytor paska narzędzi** z **obraz** menu podczas  **Edytor obrazów**.

**Nowy zasób paska narzędzi** okno dialogowe umożliwia określenie szerokości i wysokości przyciski dodawania zasobu paska narzędzi w projekcie C++. Wartość domyślna to 16 x 15 pikseli.

Mapa bitowa, który jest używany do tworzenia paska narzędzi ma maksymalną szerokość 2048, więc jeśli ustawisz **szerokość przycisku** do *512*, może mieć tylko cztery przyciski. Jeśli równa szerokości *513*, może mieć tylko trzy przyciski.

**Nowy zasób paska narzędzi** okno dialogowe ma następujące właściwości:

|Właściwość|Opis|
|---|---------------|
|**Szerokość przycisku.**|Miejsce na wprowadź szerokość przycisków paska narzędzi, które konwertowania zasób mapy bitowej do zasobu paska narzędzi.|
|**Wysokość przycisku**|Miejsce na Wprowadź wysokość przycisków paska narzędzi, które konwertowania zasób mapy bitowej do zasobu paska narzędzi.|

> [!NOTE]
> Obrazy są obcinane do szerokości i wysokości określone i kolory są dostosowane by wykorzystywały standardowe kolory paska narzędzi (16 kolorów).

Domyślnie przycisk Nowy lub pusty jest wyświetlany po prawej stronie paska narzędzi. Możesz przenieść ten przycisk, przed jego edycji. Podczas tworzenia nowego przycisku po prawej stronie przycisku edycji pojawi się kolejny przycisk puste. Pasek narzędzi, pusty przycisk nie jest zapisywany.

Przycisk paska narzędzi ma następujące właściwości:

|Właściwość|Opis|
|--------------|-----------------|
|**Identyfikator**|Określa identyfikator przycisku. Listy rozwijanej udostępnia typowe **identyfikator** nazwy.|
|**Szerokość**|Określa szerokość przycisku. zalecane jest 16 pikseli.|
|**Wysokość**|Określa wysokość przycisku. Wysokość jednego przycisku zmienia wysokość wszystkie przyciski na pasku narzędzi. Zaleca się 15 pikseli.|
|**wiersz**|Określa komunikat wyświetlany na pasku stanu. Dodawanie *\n* i dodaje nazwę **etykietki narzędzia** do tego przycisku paska narzędzi. Aby uzyskać więcej informacji, zobacz [tworzeniem etykietki narzędzi](../windows/creating-a-tool-tip-for-a-toolbar-button.md).|

**Szerokość** i **wysokość** dotyczą wszystkich przycisków. Mapa bitowa, który jest używany do tworzenia paska narzędzi ma maksymalną szerokość 2048, więc jeśli równa szerokość przycisku *512*, może mieć tylko czterech przycisków i Ustaw szerokość na *513*, może mieć tylko trzy przyciski.

## <a name="how-to"></a>Instrukcje

**Edytor paska narzędzi** umożliwia:

### <a name="to-create-new-toolbars"></a>Aby utworzyć nowych pasków narzędzi

1. W **zasobów** wyświetlić, kliknij prawym przyciskiem myszy plik .rc i wybierz **Dodaj zasób**. Jeśli masz istniejący pasek narzędzi w pliku .rc, możesz kliknąć prawym przyciskiem myszy **narzędzi** i wybierz polecenie **Wstaw narzędzi**.

1. W **Dodaj zasób** okno dialogowe, wybierz opcję **narzędzi** w **typ zasobu** , a następnie wybierz **New**.

   Jeśli znak plus (**+**) pojawia się obok **narzędzi** typ zasobu oznacza że narzędzi szablony są dostępne. Wybierz znak plus, aby rozwinąć listę szablonów, wybierz szablon, a następnie wybierz **New**.

### <a name="to-convert-bitmaps-to-toolbar-resources"></a>Aby przekonwertować mapy bitowe zasoby paska narzędzi

1. Otwórz istniejący zasób mapy bitowej w [edytora obrazów](../windows/image-editor-for-icons.md). Jeśli mapa bitowa nie jest już w pliku .rc, kliknij prawym przyciskiem myszy plik .rc i wybierz polecenie **importu**, a następnie przejdź do mapy bitowej, aby dodać do pliku .rc, a następnie wybierz pozycję **Otwórz**.

1. Przejdź do menu **obraz** > **Edytor paska narzędzi**.

   **Nowy zasób paska narzędzi** pojawi się okno dialogowe. Można zmienić szerokość i wysokość obrazy ikon, aby dopasować mapę bitową. Obraz paska narzędzi są następnie wyświetlane na **Edytor paska narzędzi**.

1. Aby zakończyć konwersję, zmień polecenie **identyfikator** za pomocą przycisku [okno właściwości](/visualstudio/ide/reference/properties-window). Wpisz nowy *identyfikator* lub wybierz **identyfikator** z listy rozwijanej.

   > [!TIP]
   > **Właściwości** okno zawiera przycisk pinezki na pasku tytułu, a wybranie tej włącza lub wyłącza **Autoukrywanie** okna. Aby przechodzić między wszystkie właściwości przycisku paska narzędzi, bez konieczności ponownie otworzyć windows pojedynczej właściwości, należy wyłączyć **Autoukrywanie** wyłączyć tak **właściwości** okna pozostaje stacjonarnych.

   Możesz również zmienić identyfikatory poleceń przyciski na nowy pasek narzędzi, za pomocą [okno właściwości](/visualstudio/ide/reference/properties-window).

### <a name="to-manage-toolbar-buttons"></a>Aby zarządzać przycisków paska narzędzi

Aby utworzyć nowego przycisku paska narzędzi:

1. W [widok zasobów](../windows/resource-view-window.md) rozwiń folder zasobów (na przykład *Project1.rc*).

1. Rozwiń **narzędzi** folder i wybierz pasek narzędzi do edytowania, wykonaj jedną z następujących czynności:

   - Identyfikator należy przypisać pusty przycisk po prawej stronie paska narzędzi. Możesz to zrobić, edytując **identyfikator** właściwość [okno właściwości](/visualstudio/ide/reference/properties-window). Na przykład można podać tej samej opcji menu przycisku paska narzędzi. W tym przypadku użyj pola listy rozwijanej, aby wybrać **identyfikator** opcji menu.

   - Wybierz pusty przycisk po prawej stronie paska narzędzi (w **pasek narzędzi widoku** okienko) i rozpocząć rysowania. Domyślny przycisk polecenia identyfikator jest przypisywany (ID_BUTTON\<n >).

Można również skopiuj i Wklej obraz jest jako nowego przycisku paska narzędzi.

Aby dodać obraz do paska narzędzi, jak przycisk:

1. W [widok zasobów](../windows/resource-view-window.md), Otwórz pasek narzędzi, klikając go dwukrotnie.

1. Następnie otwórz obraz, który chcesz dodać do paska narzędzi.

   > [!NOTE]
   > Jeśli otworzysz go w programie Visual Studio, zostanie on otwarty w **obraz** edytora. Można również otworzyć obrazu w innych programach grafiki.

1. Z **Edytuj** menu, wybierz **kopiowania**.

1. Przejdź do paska narzędzi, wybierając jego kartę w górnej części okna źródła.

1. Z **Edytuj** menu, wybierz **Wklej**.

   Obraz pojawi się na pasku narzędzi jako nowy przycisk.

Aby przenieść przycisk paska narzędzi:

W **pasek narzędzi widoku** okienku przeciągnij przycisk, który ma zostać przeniesiony do nowej lokalizacji, na pasku narzędzi.

Aby skopiować przycisków z paska narzędzi, przytrzymaj wciśnięty **Ctrl** klucza i w **pasek narzędzi widoku** okienku przeciągnij przycisk do jednej nowej lokalizacji na pasku narzędzi lub do lokalizacji na inny pasek narzędzi.

Usuwanie przycisku paska narzędzi, wybierz przycisk paska narzędzi i przeciągnij go poza pasek narzędzi.

Aby wstawić lub usuwanie odstępów między przyciskami na pasku narzędzi, przeciągnij je do siebie lub od na pasku narzędzi.

|Akcja|Krok|
|------|------|
|Aby wstawić odstęp przed przycisk, który nie jest następuje spacja|Przeciągnij przycisk po prawej stronie lub w dół do momentu widoczny w połowie o jej nakłada przycisk Dalej.|
|Wstaw spację przed przycisk, który następuje spacja i zachować spacje końcowe|Przeciągnij przycisk, aż do prawej lub dolnej krawędzi zachodzi po prostu przycisk Dalej, lub po prostu nakłada się.|
|Wstaw spację przed przycisk, który następuje spacja i zamknąć tego następujące miejsce|Przeciągnij przycisk po prawej stronie lub w dół do momentu widoczny w połowie o jej nakłada przycisk Dalej.|
|Aby usunąć odstępów między przyciskami na pasku narzędzi|Przeciągnij przycisk na jednej stronie miejsca kierunku przycisku po drugiej stronie miejsca, dopóki nie nakłada się przycisk Następny temat w połowie.|

> [!NOTE]
> Jeśli nie ma już miejsca obok przycisku, który przeciąga opuszczenie i przycisk przeciągnąć ponad połowie ostatnie sąsiadujących przycisku **Edytor paska narzędzi** jest wstawiana w przeciwną stronę przycisku, który jest przeciągania.

Aby zmienić właściwości przycisku paska narzędzi:

1. W projekcie w języku C++ kliknij przycisk paska narzędzi.

1. Wpisz nowy identyfikator w **identyfikator** właściwość [okno właściwości](/visualstudio/ide/reference/properties-window), lub użyj listy rozwijanej, aby wybrać nowy **identyfikator**.

Aby utworzyć etykietki narzędzia dla przycisku paska narzędzi:

1. Wybierz przycisk paska narzędzi.

1. W [okno właściwości](/visualstudio/ide/reference/properties-window)w **monitu** pola, Dodaj opis przycisku na pasku stanu i po wiadomości, dodać `\n` i nazwa Porada narzędzia.

Na przykład zobacz etykietki narzędzia dla **drukowania** znajdujący się w **WordPad**:

1. Otwórz **WordPad**.

1. Umieść wskaźnik myszy nad **drukowania** przycisku paska narzędzi i zwróć uwagę, wyraz `Print` teraz zmiennoprzecinkowych pod wskaźnika myszy.

1. Przyjrzyj się pasek stanu u dołu **WordPad** okna i zwróć uwagę, że teraz zawiera tekst `Prints the active document`.

`Print` jest nazwą Porada narzędzia i `Prints the active document` znajduje się opis przycisk na pasku stanu.

Jeśli chcesz, aby ten efekt przy użyciu **Edytor paska narzędzi**ustaw **monitu** właściwość `Prints the active document\nPrint`.

## <a name="requirements"></a>Wymagania

ATL i MFC

## <a name="see-also"></a>Zobacz też

[Edytory zasobów](../windows/resource-editors.md)
<!--
[Menus and Other Resources](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)<br/>
[Toolbar Button Properties](../windows/toolbar-button-properties.md)<br/>-->
