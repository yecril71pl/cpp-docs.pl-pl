---
title: Ustawianie preferencji C++ kodowania w programie Visual Studio
ms.description: Customize C++ formatting, colors, layout, line numbers, menus and more in the Visual Studio IDE.
ms.topic: overview
ms.date: 09/27/2019
ms.openlocfilehash: 90c9f39135b90a2c5015861a78dd8760b9a8aeed
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686888"
---
# <a name="set-your-c-coding-preferences-in-visual-studio"></a>Ustawianie preferencji C++ kodowania w programie Visual Studio

Dzięki personalizacji programu C++ Visual Studio można bardziej wygodnie pracować z kodowaniem, produktywność i Pleasurable. Możesz dostosować menu i paski narzędzi, rozmieścić układ okna, ustawić motywy koloru, określić C++ reguły formatowania, w tym kilka typów ClangFormat, i utworzyć niestandardowe skróty klawiaturowe. Możesz synchronizować swoje preferencje na wielu maszynach i tworzyć i przechowywać wiele zestawów preferencji oraz udostępniać je członkom zespołu. Można zainstalować rozszerzenia z Visual Studio Marketplace, które zapewniają dodatkowe zachowanie niestandardowe. Wiele z tych opcji jest udokumentowanych w obszarze [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="arrange-window-layout"></a>Rozmieść układ okna

W oknie programu Visual Studio miejsce jest podzielona na menu główne, pasek narzędzi, Edytor kodu (lub okno dokumentu) oraz okna narzędzi (**Eksplorator rozwiązań**, **Lista błędów**itd.). Niektóre okna nakładają się na siebie w tym samym położeniu. Na przykład **Eksplorator rozwiązań**, **Widok klasy**, **Widok zasobów**i **Eksploator kontroli źródła** wszystkie współdzielą tę samą pozycję domyślną. Możesz przełączać się między nimi, klikając karty w dolnej części ramki. Aby dwa lub więcej okien było widocznych w tym samym czasie, po prostu przeciągnij jeden z nich na pasek tytułu do nowej pozycji. Można go zadokować do jednego z obramowań okna głównego programu Visual Studio lub można go wystawić. Na poniższej ilustracji przedstawiono okno **Team Explorer** w procesie przeciągania z położenia domyślnego do nowej pozycji zadokowanej po lewej stronie edytora kodu. Niebieski zacieniony obszar pokazuje, gdzie okno zostanie umieszczone po wydaniu przycisku myszy.

![Modyfikowanie układu okna](media/window-layout-move-team-explorer.png)

W oknie dokumentu każdy otwarty plik jest zawarty w ramce z kartami. Można przestawiać lub blokować te karty podobnie jak okna narzędzi. Aby uzyskać więcej informacji, zobacz [Dostosowywanie układów okien w programie Visual Studio](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Aby ukryć wszystkie okna narzędzi i zmaksymalizować okno edytora kodu, naciśnij klawisz **Alt** + **SHIFT** + **Enter** , aby przełączyć *tryb pełnoekranowy*.

## <a name="set-c-coding-styles-and-formatting"></a>Ustawianie C++ stylów i formatowania kodowania

Można określić wiele opcji formatowania kodu, takich jak wcięcia i położenie nawiasów klamrowych, przechodząc do **narzędzi** > **Options** > **Edytor tekstu** > **C/C++** @no__t **-8 (** lub typ **Ctrl + Q** i wyszukaj "formatowanie"). Alternatywnie można określić jeden ze stylów [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) (lub własny niestandardowy styl ClangFormat):

![Opcje ClangFormat](media/clang-format-ide.png)

Aby uzyskać więcej informacji na temat wszystkich opcji formatowania, zobacz [Opcje, Edytor tekstu, CC++/, formatowanie](/visualstudio/ide/reference/options-text-editor-c-cpp-formatting).

## <a name="set-the-color-theme"></a>Ustawianie motywu kolorów

Aby ustawić jasne lub ciemne tło, wpisz **Ctrl + Q** i wyszukaj "motyw koloru". Możesz również uzyskać dostęp za pomocą **narzędzi** > **Options** > **środowisko** i wybrać **motyw kolorów**:

![Motywy kolorów](media/tools-options-color-theme.png)

Na poniższej ilustracji przedstawiono motyw ciemny:

![Motyw ciemny](media/tools-options-dark-theme.png)

## <a name="customize-code-colorization"></a>Dostosuj kolorowanie kodu

W programie Visual Studio 2019 można wybierać spośród trzech wstępnie zdefiniowanych *schematów kolorów* , które określają sposób kolorowania elementów kodu w edytorze. Aby wybrać motyw, przejdź do **menu Narzędzia** > **Options** > **Edytor tekstu** > **C/C++**  > **Widok** i wybierz **schemat kolorów**:

![C++Schematy kolorów](media/color-schemes.png)

W schemacie kolorów **programu Visual Studio 2017** większość elementów kodu jest po prostu czarna. W **zaawansowanym** schemacie kolorów funkcje, zmienne lokalne, makra i inne elementy są kolorami. W schemacie **rozszerzonym (Globals vs. Members)** funkcje i zmienne globalne są kolorowe w celu odróżnienia od elementów członkowskich klasy. Tryb domyślny jest **ulepszony** i wygląda następująco:

![Ulepszony schemat kolorów](media/color-scheme-enhanced.png)

Niezależnie od tego, który motyw lub schemat kolorów jest aktywny, można dostosować czcionkę i kolory poszczególnych elementów kodu, przechodząc do **narzędzi** > **Options** > **środowisko** > **czcionek i kolorów** (lub typu  **Naciśnij klawisze CTRL + Q** i wyszukaj ciąg "Fonts" (czcionki). Przewiń w dół listę elementów wyświetlanych do momentu wyświetlenia C++ opcji:

![C++Opcje czcionek i kolorów](media/tools-options-cpp-colors.png)

Kolory ustawione w tym miejscu zastępują wartości zdefiniowane dla schematów kolorów. Należy ustawić kolor z powrotem na **domyślny** , jeśli został zmieniony, ale chce użyć domyślnych kolorów dla schematu kolorów.

## <a name="customize-the-toolbars"></a>Dostosuj paski narzędzi

Paski narzędzi zapewniają wygodny sposób na wydawanie poleceń za pomocą pojedynczego kliknięcia myszą zamiast używania menu lub skrótów klawiaturowych. Program Visual Studio zawiera standardowy zestaw pasków narzędzi. W przypadku C++ programowania standardowego najbardziej przydatne paski narzędzi są prawdopodobnie standardowe, Edytor tekstu, kompilacja, debugowanie, kontrola źródła i ewentualnie porównane pliki. W przypadku projektowania systemu Windows Edytor okien dialogowych i Edytor obrazów są przydatne do układania okien dialogowych i edytowania ikon.

Umieść kursor nad ikonami na pasku narzędzi, aby zobaczyć, które polecenie reprezentuje:

![Pasek narzędzi sekcji szybkich informacji](media/toolbar-mouse-hover.png)

Możesz dodawać lub usuwać polecenia lub tworzyć niestandardowe paski narzędzi, klikając strzałkę w dół. Aby przenieść pasek narzędzi do nowej lokalizacji, przeciągnij go przez kropkowany pasek po lewej stronie:

![Dostosowywanie lub przenoszenie paska narzędzi](media/toolbar-move-edit.png).

Aby uzyskać więcej informacji, zobacz [How to: Dostosowywanie menu i pasków narzędzi w programie Visual Studio](/visualstudio/ide/how-to-customize-menus-and-toolbars-in-visual-studio).

## <a name="show-or-hide-line-numbers"></a>Pokaż lub Ukryj numery wierszy

Aby określić, czy numery wierszy mają być wyświetlane po lewej stronie okna edytora, przejdź do pozycji i zaznacz pole wyboru **numery wierszy**:

![Numery wierszy](media/tools-options-line-numbers.png)

## <a name="create-keyboard-shortcuts"></a>Utwórz skróty klawiaturowe

Wszystkie polecenia w programie Visual Studio można wykonać za pomocą skrótów klawiaturowych przy użyciu różnych kombinacji klawiszy z klawiszami Ctrl, Alt i Shift. Możesz tworzyć własne skróty, przechodząc do **narzędzi** > **Options** > **środowiska** > **Klawiatura** (lub wpisz **Ctrl + Q** i wyszukaj frazę "skróty"). Aby uzyskać więcej informacji, zobacz [Identyfikowanie i Dostosowywanie skrótów klawiaturowych w programie Visual Studio](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).
