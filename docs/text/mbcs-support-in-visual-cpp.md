---
title: Obsługa MBCS w programie Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- tools [C++], MBCS support
- Asian languages [C++]
- Code Editor [C++], MBCS support
- IME [C++]
- Chinese characters [C++]
- Input Method Editor [C++], MBCS
- resource editors [C++], MBCS support
- debugger [C++], MBCS support
- character sets [C++], multibyte
- Japanese characters [C++]
- multibyte characters [C++]
- Kanji character support [C++]
- NMAKE program, MBCS support
- double-byte character sets [C++]
- IME [C++], MBCS
- Input Method Editor [C++]
- MBCS [C++], enabling
ms.assetid: 6179f6b7-bc61-4a48-9267-fb7951223e38
ms.openlocfilehash: b5f2b6dd56d3a755ee73058c024152e12157a6bd
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501945"
---
# <a name="mbcs-support-in-visual-c"></a>Obsługa MBCS w programie Visual C++

W przypadku uruchamiania w systemie Windows z włączoną obsługą MBCS, system C++ programistyczny (w tym Edytor kodu zintegrowanego, debuger i narzędzia wiersza polecenia) jest włączony MBCS, z wyjątkiem okna pamięci.

Okno pamięci nie interpretuje bajtów danych jako znaków MBCS, nawet jeśli można je zinterpretować jako znaki ANSI lub Unicode. Znaki ANSI mają zawsze 1 bajt w rozmiarze, a znaki Unicode mają rozmiar 2 bajtów. W przypadku MBCS znaki mogą mieć rozmiar 1 lub 2 bajtów, a ich interpretacja zależy od tego, która strona kodowa jest używana. W związku z tym trudno jest w oknie pamięci, aby niezawodnie wyświetlać znaki MBCS. Okno pamięci nie może wiedzieć, który bajt jest początkiem znaku. Deweloper może wyświetlić wartości bajtów w oknie pamięci i wyszukać wartość w tabelach, aby określić reprezentację znaku. Jest to możliwe, ponieważ deweloper wie o adresie początkowym ciągu w oparciu o kod źródłowy.

Wizualizacja C++ akceptuje znaki dwubajtowe, wszędzie tam, gdzie jest to odpowiednie. Obejmuje to nazwy ścieżek i nazwy plików w oknach dialogowych i wpisów tekstowych w edytorze C++ zasobów wizualnych (na przykład tekst statyczny w edytorze okien dialogowych i statyczne wpisy tekstowe w edytorze ikon). Ponadto Preprocesor rozpoznaje kilka dyrektyw dwubajtowych — na przykład nazwy plików w `#include` instrukcjach i jako argumenty `code_seg` do dyrektywy i `data_seg` . W edytorze kodu źródłowego znaki dwubajtowe w komentarzach i literałach ciągów są akceptowane, ale nie w elementachC++ języka C (takich jak nazwy zmiennych).

##  <a name="_core_support_for_the_input_method_editor_.28.ime.29"></a>Obsługa edytora Input Method Editor (IME)

Aplikacje przeznaczone dla rynków wschodnioazjatyckich, które używają MBCS (na przykład Japonia), zwykle obsługują Edytor IME systemu Windows do wprowadzania znaków pojedynczej i dwubajtowej. Środowisko programistyczne Visual C++ Environment zawiera pełną obsługę edytora IME.

Klawiatury japońskie nie obsługują bezpośrednio znaków kanji. Edytor IME konwertuje ciąg fonetyczny wprowadzony w jednym z pozostałych alfabetów japońskich (Romaji, katakana lub Hiragana) na możliwe reprezentacje kanji. Jeśli występuje niejednoznaczność, można wybrać jedną z kilku alternatyw. Po wybraniu zamierzonego znaku kanji, Edytor IME przekazuje dwa `WM_CHAR` komunikaty do aplikacji kontrolującej.

Edytor IME, aktywowany przez kombinację klawiszy\` Alt +, pojawia się jako zestaw przycisków (wskaźnik) i okna konwersji. Aplikacja umieszcza okno w punkcie wstawiania tekstu. Aplikacja musi obsługiwać `WM_MOVE` i `WM_SIZE` komunikatów przez zmianę położenia okna konwersji, aby była zgodna z nową lokalizacją lub rozmiarem okna docelowego.

Jeśli chcesz, aby użytkownicy aplikacji mogli wprowadzać znaki kanji, aplikacja musi obsługiwać komunikaty edytora IME systemu Windows. Aby uzyskać więcej informacji na temat programowania edytora IME, zobacz [Input Method Manager](/windows/win32/intl/input-method-manager).

## <a name="visual-c-debugger"></a>Debuger C++ wizualizacji

Debuger wizualizacji C++ umożliwia ustawianie punktów przerwania w komunikatach edytora IME. Ponadto w oknie pamięci można wyświetlić znaki dwubajtowe.

## <a name="command-line-tools"></a>Narzędzia wiersza polecenia

Narzędzia wiersza C++ polecenia wizualne, w tym KOMPILATOR, NMAKE i kompilator zasobów (RC. EXE) jest włączony MBCS. Można użyć/c opcji kompilatora zasobów, aby zmienić domyślną stronę kodową podczas kompilowania zasobów aplikacji.

Aby zmienić domyślne ustawienia regionalne w czasie kompilacji kodu źródłowego, użyj [#pragma](../preprocessor/setlocale.md)setlocale.

## <a name="graphical-tools"></a>Narzędzia graficzne

Narzędzia oparte C++ na systemie Windows, takie jak Spy + + i narzędzia do edycji zasobów, w pełni obsługują ciągi IME.

## <a name="see-also"></a>Zobacz także

[Obsługa zestawów znaków wielobajtowych (zestawy MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
[Porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md)
