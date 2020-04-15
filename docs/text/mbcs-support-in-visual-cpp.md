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
ms.openlocfilehash: 404fcee5e48d8db28e56a005f24f8cac5892240e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375792"
---
# <a name="mbcs-support-in-visual-c"></a>Obsługa MBCS w programie Visual C++

Po uruchomieniu w wersji systemu Windows z obsługą MBCS system programistyczny Visual C++ (w tym zintegrowany edytor kodu źródłowego, debuger i narzędzia wiersza polecenia) jest włączony mbcs, z wyjątkiem okna pamięci.

Okno pamięci nie interpretuje bajtów danych jako znaków MBCS, nawet jeśli może je interpretować jako znaki ANSI lub Unicode. Znaki ANSI mają zawsze rozmiar 1 bajtu, a znaki Unicode mają rozmiar 2 bajtów. W przypadku MBCS znaki mogą mieć rozmiar 1 lub 2 bajtów, a ich interpretacja zależy od używanej strony kodowej. Z tego powodu okno pamięci ma trudności z niezawodnym wyświetlaniem znaków MBCS. Okno pamięci nie wie, który bajt jest początkiem znaku. Deweloper może wyświetlić wartości bajtów w oknie pamięci i wyszukać wartość w tabelach, aby określić reprezentację znaków. Jest to możliwe, ponieważ deweloper zna adres początkowy ciągu na podstawie kodu źródłowego.

Visual C++ akceptuje znaki dwu bajtów wszędzie tam, gdzie jest to właściwe. Obejmuje to nazwy ścieżek i nazw plików w oknach dialogowych i wpisy tekstowe w edytorze zasobów Visual C++ (na przykład tekst statyczny w edytorze okien dialogowych i statyczne wpisy tekstowe w edytorze ikon). Ponadto preprocesor rozpoznaje niektóre dyrektywy dwu bajtów — na przykład `#include` nazwy plików w `code_seg` instrukcjach i jako argumenty do i `data_seg` pragmy. W edytorze kodu źródłowego znaki dwu bajtów w komentarzach i literałach ciągów są akceptowane, chociaż nie w elementach języka C/C++ (takich jak nazwy zmiennych).

## <a name="support-for-the-input-method-editor-ime"></a><a name="_core_support_for_the_input_method_editor_.28.ime.29"></a>Obsługa edytora metod wprowadzania (IME)

Aplikacje napisane dla rynków wschodnioazjatyckich, które używają MBCS (na przykład Japonia) zwykle obsługują ime systemu Windows do wprowadzania znaków jedno- i dwu bajtowych. Środowisko programistyczne Visual C++ zawiera pełną obsługę IME.

Japońskie klawiatury nie obsługują bezpośrednio znaków Kanji. IME konwertuje ciąg fonetyczny, wprowadzony w jednym z innych japońskich alfabetów (Romaji, Katakana lub Hiragana) do jego możliwych reprezentacji Kanji. Jeśli istnieje niejednoznaczność, można wybrać jedną z kilku alternatyw. Po wybraniu zamierzonego znaku Kanji, IME przekazuje dwa `WM_CHAR` komunikaty do aplikacji kontrolującej.

IME, aktywowane przez kombinację klawiszy ALT+,\` pojawia się jako zestaw przycisków (wskaźnik) i okno konwersji. Aplikacja umieszcza okno w punkcie wstawiania tekstu. Aplikacja musi `WM_MOVE` obsługiwać i `WM_SIZE` komunikaty przez zmianę położenia okna konwersji, aby były zgodne z nową lokalizacją lub rozmiarem okna docelowego.

Jeśli chcesz, aby użytkownicy aplikacji mieli możliwość wprowadzania znaków Kanji, aplikacja musi obsługiwać wiadomości IME systemu Windows. Aby uzyskać więcej informacji na temat programowania IME, zobacz [Input Method Manager](/windows/win32/intl/input-method-manager).

## <a name="visual-c-debugger"></a>Debuger języka Visual C++

Debuger Visual C++ zapewnia możliwość ustawiania punktów przerwania w komunikatach IME. Ponadto w oknie Pamięć można wyświetlić znaki dwu bajtowe.

## <a name="command-line-tools"></a>Narzędzia wiersza polecenia

Narzędzia wiersza polecenia Visual C++, w tym kompilator, NMAKE i kompilator zasobów (RC. EXE), są włączone MBCS. Można użyć kompilatora zasobów /c opcja, aby zmienić domyślną stronę kodową podczas kompilowania zasobów aplikacji.

Aby zmienić domyślne ustawienia regionalne w czasie kompilacji kodu źródłowego, użyj [#pragma setlocale](../preprocessor/setlocale.md).

## <a name="graphical-tools"></a>Narzędzia graficzne

Narzędzia oparte na systemie Windows języka Visual C++, takie jak Spy++ i narzędzia do edycji zasobów, w pełni obsługują ciągi IME.

## <a name="see-also"></a>Zobacz też

[Obsługa zestawów znaków wielobajtowych (zestawy MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
[Porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md)
