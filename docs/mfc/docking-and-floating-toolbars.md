---
title: Zadokowane i przestawne paski narzędzi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CBRS_SIZE_DYNAMIC
- CBRS_SIZE_FIXED
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 430af2344888696e3cbf053677ef59c7249b50bd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="docking-and-floating-toolbars"></a>Zadokowane i przestawne paski narzędzi
Microsoft Foundation Class Library obsługuje dokującego pasków narzędzi. Dokującego paska narzędzi można dołączyć, i zadokowane do dowolnej krawędzi okna nadrzędnego, lub można odłączyć, lub przestawione w osobnym oknie mini ramki. W tym artykule opisano sposób używania dokującego paski narzędzi w aplikacji.  
  
 Jeśli używasz Kreatora aplikacji do wygenerowania szkielet aplikacji, zostanie wyświetlona prośba o można wybrać dokującego pasków narzędzi. Domyślnie Kreator aplikacja generuje kod, który wykonuje trzy czynności niezbędna do umieszczenia dokującego paska narzędzi w aplikacji:  
  
-   [Włącz dokowanie w oknie ramowym](#_core_enabling_docking_in_a_frame_window).  
  
-   [Włącz Dokowanie paska narzędzi](#_core_enabling_docking_for_a_toolbar).  
  
-   [Dokowanie paska narzędzi (w celu okno ramowe)](#_core_docking_the_toolbar).  
  
 Jeśli dowolny z tych kroków, aplikacja wyświetli standardowym pasku narzędzi. Ostatnie dwa kroki należy wykonać dla każdego dokującego paska narzędzi w aplikacji.  
  
 Omówione w tym artykule inne tematy obejmują:  
  
-   [Liczby zmiennoprzecinkowe paska narzędzi](#_core_floating_the_toolbar)  
  
-   [Dynamiczne zmiany rozmiaru paska narzędzi](#_core_dynamically_resizing_the_toolbar)  
  
-   [Ustawienia zawijania stanowisk dla stałej stylu paska narzędzi](#_core_setting_wrap_positions_for_a_fixed_style_toolbar)  
  
 Ogólne MFC przykładu [DOCKTOOL](../visual-cpp-samples.md) przykłady.  
  
##  <a name="_core_enabling_docking_in_a_frame_window"></a> Włączanie dokowanie w oknie ramowym  
 Aby dokowania pasków narzędzi do ramki okna, okno ramowe (lub docelowego) musi być włączony umożliwia dokowania. Jest to realizowane przy użyciu [CFrameWnd::EnableDocking](../mfc/reference/cframewnd-class.md#enabledocking) funkcji, która przyjmuje jeden `DWORD` parametr, który jest zestawem styl bits wskazujące, której stronie okno ramowe akceptuje dokowania. Jeśli ma być dokowany pasek narzędzi i istnieje wiele stron, które może być zadokowane, boków wskazane parametr przekazany do `EnableDocking` są używane w następującej kolejności: Góra, dół, lewo, prawo. Jeśli chcesz można było do formantu dokowania pasków dowolnego miejsca, należy przekazać `CBRS_ALIGN_ANY` do `EnableDocking`.  
  
##  <a name="_core_enabling_docking_for_a_toolbar"></a> Włączanie Dokowanie paska narzędzi  
 Po przygotowaniu miejsca docelowego dla dokowania, należy przygotować paska narzędzi (lub źródła) w podobny sposób. Wywołanie [CControlBar::EnableDocking](../mfc/reference/ccontrolbar-class.md#enabledocking) dla poszczególnych narzędzi chcesz dock określania miejsca docelowego bokach powinien Dokowanie paska narzędzi. Jeśli żadna stron określone w wywołaniu `CControlBar::EnableDocking` stron dla dokowanie w oknie ramowym włączone są zgodne, nie Dokowanie paska narzędzi — przesunie się. Po zostały przestawione, pozostaje swobodny pasek narzędzi, nie można dock do ramki okna.  
  
 Jeśli ma efekt jest trwale swobodny pasek narzędzi, wywołanie `EnableDocking` z parametrem 0. Następnie wywołaj [CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar). Pasek narzędzi pozostaje przestawne, trwale mógł dock w dowolnym miejscu.  
  
##  <a name="_core_docking_the_toolbar"></a> Dokowanie paska narzędzi  
 Wywołania framework [CFrameWnd::DockControlBar](../mfc/reference/cframewnd-class.md#dockcontrolbar) gdy użytkownik próbuje upuścić na pasku narzędzi na stronie okno ramowe, który umożliwia dokowania.  
  
 Ponadto można wywołać tej funkcji w dowolnym momencie dokowania pasków sterowania do ramki okna. Zwykle odbywa się podczas inicjowania. Więcej niż jeden pasek narzędzi może być zadokowany do konkretnej strony ramkę okna.  
  
##  <a name="_core_floating_the_toolbar"></a> Liczby zmiennoprzecinkowe paska narzędzi  
 Odłączanie dokującego paska narzędzi z okno ramowe nosi nazwę zmiennoprzecinkowych na pasku narzędzi. Wywołanie [CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar) w tym celu. Określ narzędzi, aby być przestawione, punkt, w którym mają zostać umieszczone i wyrównanie styl, który określa, czy swobodny pasek narzędzi jest pozioma lub pionowa.  
  
 Struktura wywołuje tej funkcji, gdy użytkownik przeciąga pasek narzędzi poza jego zadokowanych lokalizacji i porzuca go w lokalizacji, gdzie dokowanie nie jest włączone. Może być dowolnym wewnątrz lub na zewnątrz ramkę okna. Jak `DockControlBar`, tej funkcji można również wywołać podczas inicjowania.  
  
 Implementacja MFC dokującego pasków narzędzi nie zawiera niektóre z funkcji rozszerzonej w niektórych aplikacjach, które obsługują dokującego paski narzędzi. Nie podano funkcje, takie jak dostosowywalnych pasków narzędzi.  
  
##  <a name="_core_dynamically_resizing_the_toolbar"></a> Dynamiczne zmiany rozmiaru paska narzędzi  
 Począwszy od programu Visual C++ w wersji 4.0 możesz można umożliwić użytkownikom aplikacji w celu dynamicznie Zmień rozmiar przestawne paski narzędzi. Paska narzędzi ma zwykle długie, liniowego kształtu wyświetlane w poziomie. Ale można zmienić orientację na pasku narzędzi i jego kształtu. Na przykład gdy użytkownik stacje dokujące narzędzi względem jednej strony pionowy okno ramowe, kształtu zmienia układ pionowy. Istnieje również możliwość Przekształć w prostokąt z wielu wierszy przycisków paska narzędzi.  
  
 Można:  
  
-   Określ dynamicznej zmiany rozmiaru jako właściwość paska narzędzi.  
  
-   Określ stały rozmiar jako właściwość paska narzędzi.  
  
 Aby zapewnić tę obsługę, istnieją dwa nowe style paska narzędzi do użycia w wywołaniami [CToolBar::Create](../mfc/reference/ctoolbar-class.md#create) funkcję elementu członkowskiego. Są to:  
  
-   **Cbrs_size_dynamic —** pasek sterowania jest dynamiczny.  
  
-   **Cbrs_size_fixed —** pasek sterowania został rozwiązany.  
  
 Styl dynamiczne rozmiar umożliwia użytkownikowi zmienianie rozmiaru na pasku narzędzi, gdy jest on zmiennoprzecinkową, ale nie jest zadokowany. Pasek narzędzi "opakowuje" w razie potrzeby można zmienić kształtu jako użytkownik przeciąga jego krawędzi.  
  
 Rozmiar stały styl zachowuje stanów zawijania paska narzędzi, ustalania pozycji przycisków w każdej kolumnie. Użytkownik aplikacji nie może zmienić kształtu paska narzędzi. Opakowuje paska narzędzi w wyznaczonym miejscach, takie jak lokalizacje separatora między przyciskami. Przechowuje ten kształt, czy pasek narzędzi jest zadokowany lub zmiennoprzecinkową. Efekt jest stały palety z wieloma kolumnami przycisków.  
  
 Można również użyć [CToolBar::GetButtonStyle](../mfc/reference/ctoolbar-class.md#getbuttonstyle) zwraca stan i styl przycisków na paski narzędzi. Styl przycisku określa wygląd przycisku i sposobu odpowiedzi na dane wejściowe użytkownika; Stan informuje, czy przycisk jest w stanie opakowana.  
  
##  <a name="_core_setting_wrap_positions_for_a_fixed_style_toolbar"></a> Ustawienia zawijania stanowisk dla stałej stylu paska narzędzi  
 Dla paska narzędzi o rozmiarze stałym styl wyznaczyć narzędzi przycisk indeksów, na których będzie zawijany pasku narzędzi. Poniższy kod przedstawia, jak to zrobić w oknie głównym ramki `OnCreate` zastąpienia:  
  
 [!code-cpp[NVC_MFCDocViewSDI#10](../mfc/codesnippet/cpp/docking-and-floating-toolbars_1.cpp)]  
  
 Przykładowe ogólne MFC [DOCKTOOL](../visual-cpp-samples.md) przedstawia sposób użycia funkcji Członkowskich klas [ccontrolbar —](../mfc/reference/ccontrolbar-class.md) i [ctoolbar —](../mfc/reference/ctoolbar-class.md) do zarządzania dynamiczne Układ paska narzędzi. Znajduje się w pliku EDITBAR. CPP w DOCKTOOL.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Podstawowe informacje na temat narzędzi](../mfc/toolbar-fundamentals.md)  
  
-   [Etykietki narzędzi paska narzędzi](../mfc/toolbar-tool-tips.md)  
  
-   [Używanie swoich starych pasków narzędzi](../mfc/using-your-old-toolbars.md)  
  
## <a name="see-also"></a>Zobacz też  
 [MFC, implementacja paska narzędzi](../mfc/mfc-toolbar-implementation.md)

