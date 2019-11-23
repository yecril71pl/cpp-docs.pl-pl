---
title: Ustawianie preferencji C++ kodowania w programie Visual Studio
ms.description: Customize C++ formatting, colors, layout, line numbers, and menus in the Visual Studio IDE.
ms.topic: overview
ms.date: 09/27/2019
ms.openlocfilehash: f1d222dc38720ea897cfbf2fb9fa0dd2727e7720
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816350"
---
# <a name="set-your-c-coding-preferences-in-visual-studio"></a>Ustawianie preferencji C++ kodowania w programie Visual Studio

Dzięki personalizacji programu C++ Visual Studio możesz zwiększyć komfort, produktywność i Pleasurable środowiska programistycznego. Możesz:

- Dostosuj menu i paski narzędzi.
- Rozmieść układ okna.
- Ustawianie motywów kolorów.
- Określ C++ reguły formatowania, w tym kilka stylów ClangFormat.
- Utwórz niestandardowe skróty klawiaturowe.

Możesz synchronizować swoje preferencje na wielu maszynach i tworzyć i przechowywać wiele zestawów preferencji oraz udostępniać je członkom zespołu. Można zainstalować rozszerzenia z Visual Studio Marketplace, oferując dodatkowe opcje dostosowywania zachowań. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="arrange-window-layout"></a>Rozmieść układ okna

W oknie programu Visual Studio miejsce jest podzielona na menu główne, pasek narzędzi, Edytor kodu (lub okno dokumentu) oraz okna narzędzi (takie jak Eksplorator rozwiązań i Lista błędów). Niektóre okna nakładają się na siebie w tym samym położeniu. Na przykład Eksplorator rozwiązań, Widok klasy, Widok zasobów i Eksploator kontroli źródła wszystkie współdzielą tę samą pozycję domyślną. Możesz przełączać się między nimi, wybierając karty w dolnej części ramki. Aby dwa lub więcej okien było widocznych w tym samym czasie, po prostu przeciągnij jeden z nich na pasek tytułu do nowej pozycji. Można go zadokować do jednego z obramowań okna głównego programu Visual Studio lub można go wystawić.

Poniższy zrzut ekranu przedstawia okno **Team Explorer** przeciągane z jego domyślnego położenia do nowej, zadokowanej pozycji po lewej stronie edytora kodu. Niebieski zacieniony obszar pokazuje, gdzie okno zostanie umieszczone po wydaniu przycisku myszy.

![Zrzut ekranu okna Team Explorer programu Visual Studio z wyróżnioną pozycją zmiany układu](media/window-layout-move-team-explorer.png)

W oknie dokumentu każdy otwarty plik jest zawarty w ramce z kartami. Można przestawiać lub blokować te karty, podobnie jak okna narzędzi. Aby uzyskać więcej informacji, zobacz [dostosowywanie układów okien w programie Visual Studio](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Aby ukryć wszystkie okna narzędzi i zmaksymalizować okno edytora kodu, naciśnij klawisz **Alt** + **SHIFT** + **Enter** , aby przełączyć *tryb pełnoekranowy*.

## <a name="set-c-coding-styles-and-formatting"></a>Ustawianie C++ stylów i formatowania kodowania

Można określić wiele opcji formatowania kodu, takich jak wcięcia i położenie nawiasów klamrowych. Aby to zrobić, przejdź do pozycji **Narzędzia** > **Opcje** > **edytorze tekstów** > **Formatowanie** **C/C++**  > (lub wpisz ciąg **Ctrl + Q** i wyszukaj "formatowanie"). Alternatywnie można określić jeden ze stylów [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) (lub własny niestandardowy styl ClangFormat).

![Zrzut ekranu opcji ClangFormat](media/clang-format-ide.png)

Aby uzyskać więcej informacji na temat wszystkich opcji formatowania, zobacz [Opcje, Edytor tekstu, CC++/, formatowanie](/visualstudio/ide/reference/options-text-editor-c-cpp-formatting).

## <a name="set-the-color-theme"></a>Ustaw motyw kolorów

Aby ustawić jasne lub ciemne tło, wpisz **Ctrl + Q** i wyszukaj "motyw koloru". Można je również znaleźć, przechodząc do opcji **narzędzia** > **Opcje** > **środowisku**i wybierając pozycję **motyw kolorów**.

![Zrzut ekranu przedstawiający Motywy kolorów](media/tools-options-color-theme.png)

Na przykład poniżej przedstawiono motyw ciemny:

![Zrzut ekranu przedstawiający program Visual Studio z motywem ciemnego koloru](media/tools-options-dark-theme.png)

## <a name="customize-code-colorization"></a>Dostosuj kolorowanie kodu

W programie Visual Studio 2019 można wybierać spośród trzech wstępnie zdefiniowanych *schematów kolorów*. Określają sposób kolorowania elementów kodu w edytorze. Aby wybrać motyw, przejdź do pozycji **Narzędzia** > **Opcje** > **Edytor tekstu** > **C/C++**  > **Widok**i wybierz **schemat kolorów**:

![Zrzut ekranu C++ opcji schematów kolorów z rozszerzonymi wyróżnionymi](media/color-schemes.png)

W schemacie kolorów o nazwie **Visual Studio 2017**większość elementów kodu jest po prostu czarna. W **zaawansowanym** schemacie kolorów funkcje, zmienne lokalne, makra i inne elementy są kolorami. W schemacie **rozszerzonym (Globals vs. Members)** funkcje i zmienne globalne są kolorowe w celu odróżnienia od elementów członkowskich klasy. Tryb domyślny jest **ulepszony**i wygląda następująco:

![Zrzut ekranu przedstawiający udoskonalony schemat kolorów](media/color-scheme-enhanced.png)

Niezależnie od tego, który motyw lub schemat kolorów jest aktywny, można dostosować czcionkę i kolory poszczególnych elementów kodu. W tym celu przejdź do pozycji **narzędzia** > **opcje** > **środowisko** > **czcionki i kolory** (lub **naciśnij klawisze CTRL + Q** i wyszukaj ciąg "Fonts"). Przewiń w dół listę elementów wyświetlanych, aby wyświetlić C++ opcje.

![Zrzut ekranu C++ przedstawiający opcje czcionek i kolorów](media/tools-options-cpp-colors.png)

Kolory ustawione w tym miejscu zastępują wartości zdefiniowane dla schematów kolorów. Jeśli chcesz wrócić do domyślnych kolorów schematu kolorów, Ustaw kolor z powrotem na **domyślny**.

## <a name="customize-the-toolbars"></a>Dostosuj paski narzędzi

Paski narzędzi zapewniają wygodny sposób na wydawanie poleceń jednym kliknięciem, a nie za pomocą menu lub skrótów klawiaturowych. Program Visual Studio zawiera standardowy zestaw pasków narzędzi. W przypadku C++ programowania standardowego najbardziej przydatne paski narzędzi są prawdopodobnie standardowe, Edytor tekstu, kompilacja, debugowanie, kontrola źródła i porównywanie plików. W przypadku projektowania systemu Windows Edytor okien dialogowych i Edytor obrazów są przydatne do układania okien dialogowych i edytowania ikon.

Umieść kursor nad ikonami na pasku narzędzi, aby zobaczyć, które polecenie reprezentuje:

![Zrzut ekranu ikon paska narzędzi z przykładem informacji o poleceniu dostępnych na aktywowaniu](media/toolbar-mouse-hover.png)

Możesz dodawać lub usuwać polecenia lub tworzyć niestandardowe paski narzędzi, wybierając strzałkę w dół. Aby przenieść pasek narzędzi do nowej lokalizacji, przeciągnij go przez kropkowany pasek po lewej stronie.

![Zrzut ekranu przedstawiający pasek narzędzi z wyróżnionym strzałką w dół i kropkowanym paskiem](media/toolbar-move-edit.png).

Aby uzyskać więcej informacji, zobacz [How to: Dostosowywanie menu i pasków narzędzi w programie Visual Studio](/visualstudio/ide/how-to-customize-menus-and-toolbars-in-visual-studio).

## <a name="show-or-hide-line-numbers"></a>Pokaż lub Ukryj numery wierszy

Możesz określić, czy numery wierszy mają być wyświetlane po lewej stronie okna edytora. W obszarze **Opcje**, w obszarze **C/C++** , wybierz pozycję **Ogólne**. W sekcji **Ustawienia** wybierz lub wyczyść **numery wierszy**, w zależności od preferencji.

![Zrzut ekranu przedstawiający Opcje ogólne z wyróżnionymi numerami wierszy](media/tools-options-line-numbers.png)

## <a name="create-keyboard-shortcuts"></a>Utwórz skróty klawiaturowe

Wiele poleceń w programie Visual Studio ma *skróty klawiaturowe*, kombinacje klawiszy z klawiszem Ctrl, Alt i Shift. Można modyfikować te skróty klawiaturowe lub tworzyć nowe własne w programie Visual Studio. Przejdź do pozycji **narzędzia** > **opcje** > **środowisku** > **klawiaturą** (lub **naciśnij klawisze CTRL + Q** i wyszukaj frazę "skróty"). Aby uzyskać więcej informacji, zobacz [Identyfikowanie i Dostosowywanie skrótów klawiaturowych w programie Visual Studio](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).
