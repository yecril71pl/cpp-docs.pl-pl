---
title: Zadokowane i przestawne paski narzędzi
ms.date: 11/04/2016
f1_keywords:
- CBRS_SIZE_DYNAMIC
- CBRS_SIZE_FIXED
helpviewer_keywords:
- size [MFC], toolbars
- size
- frame windows [MFC], toolbar docking
- CBRS_ALIGN_ANY constant [MFC]
- palettes, floating
- toolbars [MFC], docking
- CBRS_SIZE_DYNAMIC constant [MFC]
- floating toolbars
- toolbars [MFC], size
- toolbars [MFC], floating
- fixed-size toolbars
- CBRS_SIZE_FIXED constant [MFC]
- toolbar controls [MFC], wrapping
- toolbars [MFC], wrapping
- floating palettes
ms.assetid: b7f9f9d4-f629-47d2-a3c4-2b33fa6b51e4
ms.openlocfilehash: f40d8860f2e514bf3c9e9364a664326250c9627a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615836"
---
# <a name="docking-and-floating-toolbars"></a>Zadokowane i przestawne paski narzędzi

Biblioteka MFC obsługuje paski narzędzi było dokować. Pasek narzędzi było dokować może być dołączany lub zadokowany, po dowolnej stronie jego okna nadrzędnego lub może zostać odłączony lub przepływany w osobnym oknie. W tym artykule wyjaśniono, jak używać pasków narzędzi było dokować w aplikacjach.

Jeśli używasz Kreatora aplikacji do wygenerowania szkieletu aplikacji, zostanie wyświetlony monit z pytaniem, czy chcesz, aby paski narzędzi było dokować. Domyślnie Kreator aplikacji generuje kod, który wykonuje trzy akcje niezbędne do umieszczenia w aplikacji paska narzędzi było dokować:

- [Włącz Dokowanie w oknie ramek](#_core_enabling_docking_in_a_frame_window).

- [Włącz Dokowanie dla paska narzędzi](#_core_enabling_docking_for_a_toolbar).

- [Zadokuj pasek narzędzi (do okna ramki)](#_core_docking_the_toolbar).

Jeśli brakuje któregoś z tych kroków, aplikacja wyświetli standardowy pasek narzędzi. Ostatnie dwa kroki należy wykonać dla każdego paska narzędzi było dokować w aplikacji.

Inne tematy omówione w tym artykule obejmują:

- [Przestawka paska narzędzi](#_core_floating_the_toolbar)

- [Dynamiczne zmienianie rozmiarów paska narzędzi](#_core_dynamically_resizing_the_toolbar)

- [Ustawianie pozycji zawijania dla paska narzędzi o stałym stylu](#_core_setting_wrap_positions_for_a_fixed_style_toolbar)

Przykłady można znaleźć w temacie General Sample [DOCKTOOL](../overview/visual-cpp-samples.md) MFC.

## <a name="enabling-docking-in-a-frame-window"></a><a name="_core_enabling_docking_in_a_frame_window"></a>Włączanie dokowania w oknie ramki

Aby zadokować paski narzędzi do okna ramki, należy włączyć okno ramki (lub miejsce docelowe), aby umożliwić dokowanie. Jest to realizowane przy użyciu funkcji [obiektu CFrameWnd:: EnableDocking](reference/cframewnd-class.md#enabledocking) , która przyjmuje jeden parametr *DWORD* , który jest zestawem bitów w stylu wskazującym, która strona okna ramki akceptuje dokowanie. Jeśli pasek narzędzi ma zostać zadokowany i istnieje wiele stron, do których może zostać zadokowany, strony określone w parametrze przekazana do `EnableDocking` są używane w następującej kolejności: Góra, dół, lewo, prawo. Jeśli chcesz mieć możliwość dokowania pasków sterowania w dowolnym miejscu, Przekaż **CBRS_ALIGN_ANY** do `EnableDocking` .

## <a name="enabling-docking-for-a-toolbar"></a><a name="_core_enabling_docking_for_a_toolbar"></a>Włączanie dokowania dla paska narzędzi

Po przygotowaniu miejsca docelowego do dokowania należy przygotować pasek narzędzi (lub źródło) w podobny sposób. Wywołaj [CControlBar:: EnableDocking](reference/ccontrolbar-class.md#enabledocking) dla każdego z pasków narzędzi, które chcesz zadokować, określając miejsce docelowe strony, do której ma zostać zadokowany pasek narzędzi. Jeśli żadna ze stron określonych w wywołaniu nie `CControlBar::EnableDocking` dopasowuje się do stron z włączoną funkcją dockowania w oknie ramki, pasek narzędzi nie może zostać zadokowany — będzie on przepływał. Gdy zostanie on przestawiony, pozostaje swobodny pasek narzędzi, nie można zadokować do okna ramki.

Jeśli odpowiedni efekt jest trwale swobodny pasek narzędzi, wywołaj `EnableDocking` z parametrem 0. Następnie Wywołaj [obiektu CFrameWnd:: FloatControlBar](reference/cframewnd-class.md#floatcontrolbar). Pasek narzędzi pozostaje swobodny, a na stałe nie można go zadokować w dowolnym miejscu.

## <a name="docking-the-toolbar"></a><a name="_core_docking_the_toolbar"></a>Dokowanie paska narzędzi

Struktura wywołuje [obiektu CFrameWnd::D ockcontrolbar](reference/cframewnd-class.md#dockcontrolbar) , gdy użytkownik próbuje upuścić pasek narzędzi po stronie okna ramki, który umożliwia dokowanie.

Ponadto można wywołać tę funkcję w dowolnym momencie, aby zadokować paski sterowania do okna ramki. Jest to zwykle wykonywane podczas inicjowania. Więcej niż jeden pasek narzędzi można zadokować do określonej strony okna ramki.

## <a name="floating-the-toolbar"></a><a name="_core_floating_the_toolbar"></a>Przestawka paska narzędzi

Odłączanie paska narzędzi było dokować z okna ramki jest nazywane przestawnym paskiem narzędzi. Wywołaj [obiektu CFrameWnd:: FloatControlBar](reference/cframewnd-class.md#floatcontrolbar) , aby to zrobić. Określ pasek narzędzi, który ma zostać przestawiony, miejsce, w którym powinien się znajdować, oraz styl wyrównania, który określa, czy swobodny pasek narzędzi jest poziomy, czy pionowy.

Struktura wywołuje tę funkcję, gdy użytkownik przewinie pasek narzędzi poza jego zadokowaną lokalizację i porzuca go w lokalizacji, w której nie włączono dokowania. Może to być dowolne miejsce wewnątrz lub na zewnątrz okna ramki. Podobnie jak w przypadku `DockControlBar` , można wywołać tę funkcję podczas inicjacji.

Implementacja MFC narzędzi było dokować nie udostępnia niektórych funkcji rozszerzonych dostępnych w niektórych aplikacjach, które obsługują paski narzędzi było dokować. Nie podano takich funkcji, jak paski narzędzi, które można dostosować.

## <a name="dynamically-resizing-the-toolbar"></a><a name="_core_dynamically_resizing_the_toolbar"></a>Dynamiczne zmienianie rozmiarów paska narzędzi

Począwszy od Visual C++ w wersji 4,0, można umożliwić użytkownikom aplikacji dynamiczne Zmienianie rozmiaru przestawnych pasków narzędzi. Zwykle pasek narzędzi ma długi, liniowy kształt, wyświetlany w poziomie. Można jednak zmienić orientację i kształt paska narzędzi. Na przykład gdy użytkownik zadokuje pasek narzędzi względem jednej z pionowych stron okna ramki, kształt zmieni się na układ pionowy. Możliwe jest również Przekształć paska narzędzi w prostokąt z wieloma wierszami przycisków.

Można:

- Określ rozmiar dynamiczny jako charakterystykę paska narzędzi.

- Określ ustalony rozmiar jako charakterystykę paska narzędzi.

Aby zapewnić tę pomoc techniczną, istnieją dwa nowe style pasków narzędzi do użycia w wywołaniach funkcji elementu członkowskiego [CToolBar:: Create](reference/ctoolbar-class.md#create) . Oto one:

- **CBRS_SIZE_DYNAMIC** Pasek sterowania jest dynamiczny.

- **CBRS_SIZE_FIXED** Pasek sterowania został naprawiony.

Styl dynamiczny rozmiar umożliwia użytkownikowi zmianę rozmiaru paska narzędzi, gdy jest on swobodny, ale nie w czasie dokowania. Pasek narzędzi "Otocz", gdy jest to konieczne, aby zmienić kształt w miarę przeciągania jego krawędzi przez użytkownika.

Styl stałego rozmiaru zachowuje Stany zawijania paska narzędzi, ustalając pozycję przycisków w każdej kolumnie. Użytkownik Twojej aplikacji nie może zmienić kształtu paska narzędzi. Pasek narzędzi otacza wskazane miejsca, takie jak lokalizacje separatorów między przyciskami. Zachowuje ten kształt, niezależnie od tego, czy pasek narzędzi jest zadokowany, czy zmiennoprzecinkowy. Efekt to stała paleta z wieloma kolumnami przycisków.

Można również użyć [CToolBar:: Getbutton](reference/ctoolbar-class.md#getbuttonstyle) , aby przywrócić stan i styl przycisków na paskach narzędzi. Styl przycisku określa, jak pojawia się przycisk i jak reaguje na dane wejściowe użytkownika; stan wskazuje, czy przycisk jest w stanie zawiniętym.

## <a name="setting-wrap-positions-for-a-fixed-style-toolbar"></a><a name="_core_setting_wrap_positions_for_a_fixed_style_toolbar"></a>Ustawianie pozycji zawijania dla paska narzędzi o stałym stylu

W przypadku paska narzędzi o stałym stylu rozmiaru wyznaczanie indeksów przycisków paska narzędzi, przy których pasek narzędzi będzie zawijany. Poniższy kod pokazuje, jak to zrobić w przesłonięciu głównego okna ramki `OnCreate` :

[!code-cpp[NVC_MFCDocViewSDI#10](codesnippet/cpp/docking-and-floating-toolbars_1.cpp)]

Ogólne przykładowe [DOCKTOOL](../overview/visual-cpp-samples.md) MFC pokazuje, jak używać funkcji elementów członkowskich klas [CControlBar](reference/ccontrolbar-class.md) i [CToolBar](reference/ctoolbar-class.md) do zarządzania dynamicznym układem paska narzędzi. Zobacz plik EDITBAR. CPP w DOCKTOOL.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Podstawy paska narzędzi](toolbar-fundamentals.md)

- [Wskazówki dotyczące narzędzia paska narzędzi](toolbar-tool-tips.md)

- [Używanie starych pasków narzędzi](using-your-old-toolbars.md)

## <a name="see-also"></a>Zobacz też

[MFC, implementacja paska narzędzi](mfc-toolbar-implementation.md)
