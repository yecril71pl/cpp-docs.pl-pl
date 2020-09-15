---
title: /STD (Określ wersję standardową języka)
description: Opcja kompilatora MSVC/STD określa Standard języka C lub C++ obsługiwany przez kompilator.
ms.date: 09/11/2020
f1_keywords:
- /std
- -std
- /std:c++14
- /std:c++17
- /std:c11
- /std:c17
- VC.Project.VCCLCompilerTool.CppLanguageStandard
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
ms.openlocfilehash: 82f37377dc223bfe3f5e578e1c7f390da91752a1
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2020
ms.locfileid: "90075832"
---
# <a name="std-specify-language-standard-version"></a>`/std` (Określ wersję standardową języka)

Włącz obsługiwane funkcje języka C i C++ z określonej wersji standardu języka C lub C++.

## <a name="syntax"></a>Składnia

> **`/std:c++14`**\
> **`/std:c++17`**\
> **`/std:c++latest`**\
> **`/std:c11`**\
> **`/std:c17`**

## <a name="remarks"></a>Uwagi

Ta **`/std`** opcja jest dostępna w programie Visual Studio 2017 i nowszych. Służy do kontrolowania funkcji standardowego języka programowania ISO C lub C++, które są włączone podczas kompilowania kodu. Ta opcja umożliwia wyłączenie obsługi niektórych nowych funkcji języka i biblioteki: te, które mogą spowodować przerwanie istniejącego kodu, który jest zgodny z określoną wersją standardu języka.

### <a name="c-standards-support"></a>Obsługa standardów języka C++

Domyślnie **`/std:c++14`** jest określona, która wyłącza funkcje języka i biblioteki standardowej dostępne w nowszych wersjach standardu języka C++. Służy  **`/std:c++17`** do włączania funkcji i zachowań specyficznych dla języka c++ 17. Aby jawnie włączyć aktualnie zaimplementowane funkcje kompilatora i biblioteki standardowej proponowane dla następnej wersji Standard, użyj **`/std:c++latest`** . Wszystkie funkcje języka C++ 20 wymagają **`/std:c++latest`** . po zakończeniu implementacji **`/std:c++20`** zostanie włączona Nowa opcja.

Opcja domyślna **`/std:c++14`** włącza zestaw funkcji języka c++ 14 implementowanych przez KOMPILATOR MSVC. Ta opcja powoduje wyłączenie obsługi biblioteki kompilatora i standardowej dla funkcji, które są zmieniane lub nowe w nowszych wersjach standardu językowego. Nie powoduje wyłączenia niektórych funkcji języka C++ 17 już zaimplementowanych w poprzednich wersjach kompilatora MSVC. Aby uniknąć istotnej zmiany dla użytkowników, którzy już korzystali z funkcji dostępnych w programie lub przed aktualizacją Update 2 programu Visual Studio 2015, te funkcje pozostaną włączone po **`/std:c++14`** określeniu opcji:

- [Reguły dla `auto` z nawiasami klamrowymi-list init](https://wg21.link/n3922)

- [`typename` w szablonie szablonu — parametry](https://wg21.link/n4051)

- [Usuwanie trigraphs](https://wg21.link/n4086)

- [Atrybuty dla przestrzeni nazw i modułów wyliczających](https://wg21.link/n4266)

- [literały znaków U8](https://wg21.link/n4267)

Lista funkcji, które są włączone w języku C++ 14 i C++ 17, gdy **`/std:c++14`** jest dostępna. Aby uzyskać więcej informacji, zobacz uwagi w [tabeli zgodność języka Microsoft C++](../../overview/visual-cpp-language-conformance.md).

**`/std:c++17`** Opcja włącza pełen zestaw funkcji języka c++ 17 implementowanych przez KOMPILATOR MSVC. Ta opcja wyłącza obsługę bibliotek kompilator i Standard dla funkcji, które są nowe lub zmienione po C++ 17. Obejmuje to po wprowadzeniu zmian w wersjach roboczych i niewymagających aktualizacji programu dla języka C++.

**`/std:c++latest`** Opcja włącza funkcje języka i biblioteki programu post-C + + 17 aktualnie zaimplementowane w kompilatorze i bibliotekach. Te funkcje mogą obejmować zmiany z roboczej wersji języka C++ 20, aktualizacje usterek, które nie są zawarte w języku C++ 17, i eksperymentalne propozycje dotyczące wersji Standard. Aby zapoznać się z listą obsługiwanych języków i funkcji biblioteki, zobacz [co nowego w Visual C++](../../overview/what-s-new-for-visual-cpp-in-visual-studio.md). **`/std:c++latest`** Opcja nie włącza funkcji chronionych przez **`/experimental`** przełącznik, ale może być wymagana do ich włączenia.

> [!IMPORTANT]
> Funkcje kompilatora i biblioteki włączane przez **`/std:c++latest`** program przedstawiają funkcje, które mogą być wyświetlane w przyszłym standardzie c++, a także w przypadku zaakceptowanych funkcji języka c++ 20. Funkcje, które nie zostały zatwierdzone, podlegają istotnym zmianom lub usunięciu bez powiadomienia i są udostępniane na bieżąco.

**`/std`** Opcja obowiązująca w trakcie kompilacji języka C++ może zostać wykryta przy użyciu makra preprocesora [ \_ MSVC \_ lang](../../preprocessor/predefined-macros.md) . Aby uzyskać więcej informacji, zobacz [makra preprocesora](../../preprocessor/predefined-macros.md).

**`/std:c++14`** Opcje i **`/std:c++latest`** są dostępne, zaczynając od programu Visual Studio 2015 Update 3. Ta **`/std:c++17`** opcja jest dostępna, zaczynając od programu Visual Studio 2017 w wersji 15,3. Jak wspomniano powyżej, niektóre standardowe zachowanie języka C++ 17 jest włączane przez **`/std:c++14`** opcję, ale wszystkie inne funkcje języka c++ 17 są włączane przez program **`/std:c++17`** . Funkcje języka c++ 20 są włączane, **`/std:c++latest`** dopóki implementacja nie zostanie zakończona.

> [!NOTE]
> W zależności od wersji kompilatora MSVC lub poziomu aktualizacji funkcje języka C++ 17 mogą nie być w pełni zaimplementowane lub w pełni zgodne po określeniu **`/std:c++17`** opcji. Aby zapoznać się z omówieniem zgodności języka C++ w Visual C++ przez wydanie wersji, zobacz [tabela zgodność języka Microsoft C++](../../overview/visual-cpp-language-conformance.md).

### <a name="c-standards-support"></a>Obsługa standardów języka C

Domyślnie, gdy kod jest kompilowany jako C, kompilator MSVC nie jest zgodny z konkretnym standardem C. Implementuje ANSI C89 z kilkoma rozszerzeniami firmy Microsoft, które są częścią ISO C99. Niektóre rozszerzenia firmy Microsoft można wyłączyć przy użyciu [`/Za`](za-ze-disable-language-extensions.md) opcji kompilatora, ale inne pozostają w mocy. Nie można określić ścisłej zgodności c89.

Począwszy od programu Visual Studio 2019 w wersji 16,8, możesz określić **`/std:c11`** lub **`/std:c17`** dla kodu skompilowanego jako C. Te opcje określają tryby zgodności zgodne z ISO C11 i ISO C17. Ponieważ nowy preprocesor jest wymagany do obsługi tych standardów, **`/std:c11`** Opcje kompilatora i są **`/std:c17`** ustawiane [`/Zc:preprocessor`](zc-preprocessor.md) automatycznie. Jeśli chcesz korzystać z tradycyjnego preprocesora (starszej wersji) dla C11 lub C17, musisz **`/Zc:preprocessor-`** jawnie ustawić opcję kompilatora. Ustawienie **`/Zc:preprocessor-`** opcji może prowadzić do nieoczekiwanego zachowania i nie jest zalecane.

> [!NOTE]
> W momencie wydania najnowsze biblioteki Windows SDK i UCRT nie obsługują jeszcze kodu C11 i C17. Wymagana jest wersja wstępna Windows SDK i UCRT. Aby uzyskać więcej informacji i instrukcje dotyczące instalacji, zobacz [Install C11 and C17 Support in Visual Studio](../../overview/install-c17-support.md).

Po określeniu **`/std:c11`** lub **`/std:c17`** , MSVC obsługuje wszystkie funkcje wymagane przez C11 i C17. Opcje kompilatora umożliwiają obsługę tych funkcji:

- **`_Pragma`**

- **`restrict`**

- **`_Noreturn`** lub \<stdnoreturn.h>

- **`_Alignas`****`_Alignof`** i\<stdalign.h>

- **`_Generic`** lub \<tgmath.h>

- **`_Static_assert`**

IDE używa ustawień języka C dla funkcji IntelliSense i wyróżniania kodu, gdy pliki źródłowe mają *`.c`* rozszerzenie pliku lub gdy określisz [`/TC`](tc-tp-tc-tp-specify-source-file-type.md) opcję kompilatora. Obecnie wyróżnianie funkcji IntelliSense jest dostępne tylko dla słów kluczowych, a nie makr wprowadzonych przez standardowe nagłówki.

Ponieważ C17 jest w dużym stopniu wydaniem poprawki ISO C11, obsługa MSVC dla C11 zawiera już wszystkie odpowiednie raporty wad. Obecnie nie ma żadnych różnic między wersjami C11 i C17, z wyjątkiem `__STDC_VERSION__` makra. Rozszerza ona do `201112L` C11 i `201710L` C17.

Kompilator nie obsługuje żadnych opcjonalnych funkcji ISO C11. Niektóre z tych opcjonalnych funkcji C11 były funkcjami C99, które MSVC nie zostały zaimplementowane ze względu na architekturę. Można użyć makr testów funkcji, takich jak `__STDC_NO_VLA__` do wykrywania poziomów obsługi kompilatora dla poszczególnych funkcji. Aby uzyskać więcej informacji na temat wstępnie zdefiniowanych makr specyficznych dla języka C, zobacz [wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md).

- Brak zgodności z obsługą wielowątkowości, niepodzielnych lub złożonych liczb w wersji 16,8 programu Visual Studio 2019.

- `aligned_alloc` Brak obsługi z powodu implementacji sterty systemu Windows. Alternatywą jest użycie [`_aligned_malloc`](../../c-runtime-library/reference/aligned-malloc.md) .

- Obsługa DR 400 jest obecnie niezaimplementowana dla programu `realloc` , ponieważ ta zmiana spowodowałaby uszkodzenie ABI.

- Obsługa tablicy o zmiennej długości (VLA) nie jest zaplanowana. Tablice o zmiennej długości są często mniej wydajne niż porównywalne tablice o stałym rozmiarze. Są one również niewydajne w porównaniu z równoważnymi alokacjami pamięci sterty, bezpiecznie i bezpiecznie wdrożone. VLAs zapewniają wektory ataków porównywalne z `gets()` , które są przestarzałe i planowane do usunięcia.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Właściwości konfiguracji**, **C/C++** i **Język**.

1. W **standardzie języka C++** (lub w **standardzie języka**c, c) wybierz Standard języka do obsługi z kontrolki menu rozwijanego, a następnie wybierz przycisk **OK** lub **Zastosuj** , aby zapisać zmiany.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
