---
title: Edytor paska narzędziC++()
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
ms.openlocfilehash: 72c42a06da8276d118c6c204f838ed4b31d142b9
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "69514693"
---
# <a name="toolbar-editor-c"></a>Edytor paska narzędziC++()

**Edytor paska narzędzi** umożliwia tworzenie zasobów paska narzędzi i konwertowanie map bitowych na zasoby paska narzędzi. **Edytor paska narzędzi** używa graficznego obrazu, aby pokazać pasek narzędzi i przyciski, które dokładnie przypominają wygląd gotowej aplikacji.

Okno **Edytor paska narzędzi** pokazuje dwa widoki obrazu przycisku, tak samo jak okno **edytora obrazu** . Pasek podziału oddziela dwa okienka i można przeciągnąć pasek podziału z boku, aby zmienić względne rozmiary okienek. Aktywne okienko wyświetla obramowanie zaznaczenia i powyżej dwa widoki obrazu jest paskiem narzędzi podmiotu.

![Edytor paska narzędzi](../mfc/media/vctoolbareditor.gif "vcToolbarEditor")<br/>
**Edytor paska narzędzi**

**Edytor paska narzędzi** jest podobny do **edytora obrazu** w funkcji, a elementy menu, narzędzia graficzne i siatka mapy bitowej między nimi są takie same. W menu **obraz** znajduje się polecenie menu do przełączania między **edytorem pasków narzędzi** i **edytorem obrazu**. Aby uzyskać więcej informacji na temat korzystania z paska narzędzi **grafiki** , palety **kolorów** lub menu **obrazu** , zobacz [Edytor obrazów](../windows/image-editor-for-icons.md).

Można utworzyć nowy pasek narzędzi w C++ projekcie, konwertując mapę bitową. Grafika z mapy bitowej jest konwertowana na obrazy przycisków dla paska narzędzi. Zwykle Mapa bitowa zawiera kilka obrazów przycisków na jednej mapie bitowej z jednym obrazem dla każdego przycisku. Obrazy mogą być dowolnego rozmiaru, ponieważ domyślnie wynosi 16 pikseli i wysokość obrazu. Możesz określić rozmiar obrazów przycisków w oknie dialogowym **nowy zasób paska narzędzi** , gdy wybierzesz **Edytor paska narzędzi** z menu **obraz** w **Edytorze obrazu**.

Okno dialogowe **nowy zasób paska narzędzi** pozwala określić szerokość i wysokość przycisków, które są dodawane do zasobu paska narzędzi w C++ projekcie. Wartość domyślna to 16 × 15 pikseli.

Mapa bitowa użyta do utworzenia paska narzędzi ma maksymalną szerokość 2048, więc jeśli ustawisz **Szerokość przycisku** na *512*, możesz mieć tylko cztery przyciski. Jeśli ustawisz szerokość na *513*, możesz mieć tylko trzy przyciski.

Okno dialogowe **nowy zasób paska narzędzi** ma następujące właściwości:

|Właściwość|Opis|
|---|---------------|
|**Szerokość przycisku**|Miejsce na wprowadzenie szerokości przycisków paska narzędzi, które są konwertowane z zasobu mapy bitowej na zasób paska narzędzi.|
|**Wysokość przycisku**|Miejsce, w którym można wprowadzić wysokość przycisków paska narzędzi, które są konwertowane z zasobu mapy bitowej na zasób paska narzędzi.|

> [!NOTE]
> Obrazy są przycinane do określonej szerokości i wysokości, a kolory są dostosowywane do standardowych kolorów paska narzędzi (16 kolorów).

Domyślnie przycisk Nowy lub pusty jest wyświetlany na prawym końcu paska narzędzi. Ten przycisk można przenieść przed jego edycją. Po utworzeniu nowego przycisku po prawej stronie przycisku edytowanego pojawia się kolejny pusty przycisk. Po zapisaniu paska narzędzi pusty przycisk nie jest zapisywany.

Przycisk paska narzędzi ma następujące właściwości:

|Właściwość|Opis|
|--------------|-----------------|
|**Identyfikator**|Definiuje identyfikator przycisku. Lista rozwijana zawiera wspólne nazwy **identyfikatorów** .|
|**Szerokość**|Ustawia szerokość przycisku. zalecane jest 16 pikseli.|
|**Proporcj**|Ustawia wysokość przycisku. Wysokość jednego przycisku zmienia wysokość wszystkich przycisków na pasku narzędzi. zalecane 15 pikseli.|
|**Pytać**|Definiuje komunikat wyświetlany na pasku stanu. Dodanie *\n* i nazwy powoduje dodanie **etykietki narzędzia** do tego przycisku paska narzędzi. Aby uzyskać więcej informacji, zobacz [Tworzenie etykietki narzędzia](../windows/creating-a-tool-tip-for-a-toolbar-button.md).|

**Szerokość** i **wysokość** stosują się do wszystkich przycisków. Mapa bitowa, która jest używana do tworzenia paska narzędzi ma maksymalną szerokość 2048, więc jeśli ustawisz szerokość przycisku na *512*, możesz mieć tylko cztery przyciski, a jeśli ustawisz szerokość na *513*, możesz mieć tylko trzy przyciski.

## <a name="how-to"></a>Instrukcje

**Edytor paska narzędzi** umożliwia:

### <a name="to-create-new-toolbars"></a>Aby utworzyć nowe paski narzędzi

1. W **Widok zasobów**kliknij prawym przyciskiem myszy plik *. RC* , a następnie wybierz polecenie **Dodaj zasób**. Jeśli masz istniejący pasek narzędzi w pliku *. RC* , możesz kliknąć prawym przyciskiem myszy folder **Toolbar** i wybrać polecenie **Wstaw pasek narzędzi**.

1. W oknie dialogowym **Dodawanie zasobu** wybierz pozycję **pasek narzędzi** na liście **Typ zasobu** , a następnie wybierz pozycję **Nowy**.

   Jeśli znak plus ( **+** ) pojawia się obok pozycji Typ zasobu **paska narzędzi** , oznacza to, że szablony paska narzędzi są dostępne. Wybierz znak plus, aby rozwinąć listę szablonów, wybierz szablon i wybierz pozycję **Nowy**.

### <a name="to-convert-bitmaps-to-toolbar-resources"></a>Aby skonwertować mapy bitowe na zasoby paska narzędzi

1. Otwórz istniejący zasób mapy bitowej w [Edytorze obrazu](../windows/image-editor-for-icons.md). Jeśli mapa bitowa nie znajduje się już w pliku *. RC* , kliknij prawym przyciskiem myszy plik *. RC* , a następnie wybierz pozycję **Importuj**, a następnie przejdź do mapy bitowej, którą chcesz dodać do pliku *. RC* , a następnie wybierz polecenie **Otwórz**.

1. Przejdź do**edytora pasków narzędzi** **obrazu** > menu.

   Pojawi się okno dialogowe **nowy zasób paska narzędzi** . Można zmienić szerokość i wysokość obrazów ikon, aby dopasować ją do mapy bitowej. Obraz paska narzędzi jest następnie wyświetlany w **Edytorze paska narzędzi**.

1. Aby zakończyć konwersję, należy zmienić **Identyfikator** polecenia przycisku przy użyciu [okno właściwości](/visualstudio/ide/reference/properties-window). Wpisz nowy *Identyfikator* lub wybierz **Identyfikator** z listy rozwijanej.

   > [!TIP]
   > Okno **Właściwości** zawiera przycisk pinezki na pasku tytułu i wybranie tej opcji włącza lub wyłącza **Autoukrywanie** dla okna. Aby przechodzić przez wszystkie właściwości przycisku paska narzędzi bez konieczności ponownego otwierania poszczególnych okien właściwości, wyłącz **Autoukrywanie** , aby okno **Właściwości** pozostawało nieruchome.

   Możesz również zmienić identyfikatory poleceń przycisków na nowym pasku narzędzi, używając [okno właściwości](/visualstudio/ide/reference/properties-window).

### <a name="to-manage-toolbar-buttons"></a>Aby zarządzać przyciskami paska narzędzi

#### <a name="to-create-a-new-toolbar-button"></a>Aby utworzyć nowy przycisk paska narzędzi

1. W [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources) rozwiń folder zasobów (na przykład *Project1. RC*).

1. Rozwiń folder **Toolbar** i wybierz pasek narzędzi do edycji, a następnie wykonaj jedną z następujących czynności:

   - Przypisz identyfikator do pustego przycisku na prawym końcu paska narzędzi. Można to zrobić, edytując Właściwość **ID** w [oknie właściwości](/visualstudio/ide/reference/properties-window). Na przykład możesz chcieć nadać przyciskowi paska narzędzi ten sam identyfikator jako opcję menu. W takim przypadku użyj pola listy rozwijanej, aby wybrać **Identyfikator** opcji menu.

   - Wybierz przycisk puste na prawym końcu paska narzędzi w okienku **widok paska narzędzi** i Rozpocznij rysowanie. Zostanie przypisany domyślny identyfikator polecenia przycisku (ID_BUTTON\<n >).

#### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>Aby dodać obraz do paska narzędzi jako przycisk

1. W [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources)Otwórz pasek narzędzi, klikając go dwukrotnie.

1. Następnie otwórz obraz, który chcesz dodać do paska narzędzi.

   > [!NOTE]
   > Jeśli otworzysz obraz w programie Visual Studio, zostanie on otwarty w **Edytorze obrazu**. Możesz również otworzyć obraz w innych programach graficznych.

1. Przejdź do menu **Edycja** > **Kopiuj**.

1. Przejdź do paska narzędzi, wybierając jego kartę w górnej części okna źródłowego.

1. Przejdź do menu **Edycja** > **Wklej**.

   Obraz zostanie wyświetlony na pasku narzędzi jako nowy przycisk.

#### <a name="to-move-a-toolbar-button"></a>Aby przenieść przycisk paska narzędzi

W okienku **widok paska narzędzi** przeciągnij przycisk, który ma zostać przeniesiony do nowej lokalizacji na pasku narzędzi.

- Aby skopiować przyciski z paska narzędzi, przytrzymaj wciśnięty klawisz **Ctrl** i w okienku **widok paska narzędzi** , przeciągnij przycisk do nowej lokalizacji na pasku narzędzi lub do lokalizacji na innym pasku narzędzi.

- Aby usunąć przycisk paska narzędzi, wybierz przycisk paska narzędzi i przeciągnij go poza pasek narzędzi.

- Aby wstawić lub usunąć odstęp między przyciskami na pasku narzędzi, przeciągnij je z zewnątrz lub do innego na pasku narzędzi.

|Akcja|Krok|
|------|------|
|Aby wstawić spację przed przyciskiem, który nie poprzedza spacji|Przeciągnij przycisk w prawo lub w dół do momentu, aż nastąpi przejście na następny przycisk o połowie.|
|Aby wstawić spację przed przyciskiem, po którym następuje spacja i zachować końcowy obszar|Przeciągnij przycisk do momentu, gdy prawą lub dolną krawędzią jest tylko dotknięcie przycisku Dalej lub po prostu nakłada się na niego.|
|Aby wstawić spację przed przyciskiem, po którym następuje spacja, a następnie zamknij następujące miejsce|Przeciągnij przycisk w prawo lub w dół do momentu, aż nastąpi przejście na następny przycisk o połowie.|
|Aby usunąć odstęp między przyciskami na pasku narzędzi|Przeciągnij przycisk znajdujący się po lewej stronie miejsca na przycisk po drugiej stronie miejsca do momentu, aż znajdzie się na następnym przycisku około połowy.|

> [!NOTE]
> Jeśli po stronie przycisku nie ma miejsca, z którego przeciągniesz i przeciągasz przycisk więcej niż w połowie obok sąsiadującego przycisku, **Edytor paska narzędzi** wstawia miejsce na przeciwległej stronie przycisku, który jest przeciągany.

#### <a name="to-change-the-properties-of-a-toolbar-button"></a>Aby zmienić właściwości przycisku paska narzędzi

1. W C++ projekcie, wybierz przycisk paska narzędzi.

1. Wpisz nowy identyfikator we właściwości **ID** w [oknie właściwości](/visualstudio/ide/reference/properties-window)lub Użyj listy rozwijanej, aby wybrać nowy **Identyfikator**.

#### <a name="to-create-a-tool-tip-for-a-toolbar-button"></a>Aby utworzyć etykietkę narzędzia dla przycisku paska narzędzi

1. Wybierz przycisk paska narzędzi.

1. W [oknie właściwości](/visualstudio/ide/reference/properties-window)w polu **monitu** Dodaj opis przycisku dla paska stanu, a następnie po wiadomości, Dodaj `\n` i nazwę etykietki narzędzia.

Na przykład, aby wyświetlić etykietkę narzędzia dla przycisku **Drukuj** w programie **WordPad**:

1. Otwórz program **WordPad**.

1. Umieść wskaźnik myszy nad przyciskiem paska narzędzi **Drukowanie** i Zauważ, że `Print` wyraz teraz jest przepływany pod wskaźnikiem myszy.

1. Spójrz na pasek stanu u dołu okna programu **WordPad** i zwróć uwagę na to, że teraz jest wyświetlany tekst `Prints the active document`.

`Print`jest nazwą etykietki narzędzia i `Prints the active document` jest opisem przycisku dla paska stanu.

Jeśli chcesz ten efekt przy użyciu **edytora paska narzędzi**, ustaw właściwość **monit** na `Prints the active document\nPrint`.

## <a name="requirements"></a>Wymagania

MFC lub ATL

## <a name="see-also"></a>Zobacz także

[Menu edytorów](../windows/resource-editors.md)
zasobów[i inne zasoby](/windows/win32/menurc/resources)<br/>
[Właściwości przycisku paska narzędzi](../windows/toolbar-button-properties.md)<br/>
