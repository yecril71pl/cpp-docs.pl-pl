---
title: /STD (Określ wersję standardową języka)
ms.date: 06/04/2020
f1_keywords:
- /std
- -std
- VC.Project.VCCLCompilerTool.CppLanguageStandard
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
ms.openlocfilehash: 9755194d70774f27af4c5174151588cc03d5f97a
ms.sourcegitcommit: 65fead53d56d531d71be42216056aca5f44def11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2020
ms.locfileid: "88610962"
---
# <a name="std-specify-language-standard-version"></a>`/std` (Określ wersję standardową języka)

Włącz obsługiwane funkcje języka C++ z określonej wersji standardu języka C++.

## <a name="syntax"></a>Składnia

> **`/std:c++14`**\
> **`/std:c++17`**\
> **`/std:c++latest`**

## <a name="remarks"></a>Uwagi

Ta **`/std`** opcja jest dostępna w programie Visual Studio 2017 i nowszych. Służy do kontrolowania funkcji standardowych języka programowania ISO C++, które są włączone podczas kompilowania kodu. Ta opcja umożliwia wyłączenie obsługi niektórych nowych funkcji języka i biblioteki: te, które mogą spowodować przerwanie istniejącego kodu, który jest zgodny z określoną wersją standardu języka. Domyślnie **`/std:c++14`** jest określona, która wyłącza funkcje języka i biblioteki standardowej dostępne w nowszych wersjach standardu języka C++. Służy  **`/std:c++17`** do włączania funkcji i zachowań specyficznych dla języka c++ 17. Aby jawnie włączyć aktualnie zaimplementowane funkcje kompilatora i biblioteki standardowej proponowane dla następnej wersji Standard, użyj **`/std:c++latest`** . Wszystkie funkcje języka C++ 20 wymagają **`/std:c++latest`** . po zakończeniu implementacji **`/std:c++20`** zostanie włączona Nowa opcja.

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

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Właściwości konfiguracji**, **C/C++** i **Język**.

1. W **standardzie języka C++** wybierz Standard języka, który ma być obsługiwany przez kontrolkę listy rozwijanej, a następnie wybierz przycisk **OK** lub **Zastosuj** , aby zapisać zmiany.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
