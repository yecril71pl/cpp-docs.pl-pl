---
title: / STD (Określ wersję standardu języka)
ms.date: 11/26/2018
f1_keywords:
- /std
- -std
- VC.Project.VCCLCompilerTool.CppLanguageStandard
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
ms.openlocfilehash: de3389a52781f541143268e3ede79eae375ff1d3
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446226"
---
# <a name="std-specify-language-standard-version"></a>/ STD (Określ wersję standardu języka)

Włącz obsługiwane funkcje języka C++ z określonej wersji standard języka C++.

## <a name="syntax"></a>Składnia

> /std:\[c++14\|c++17\|c++latest]

## <a name="remarks"></a>Uwagi

**/STD** opcja jest dostępna w programie Visual Studio 2017 i nowszym. Służy do kontrolowania programowania standardowe funkcje językowe, włączone podczas kompilowania kodu C++ ISO poszczególnym wersjom. Ta opcja umożliwia wyłączanie obsługi protokołu niektóre nowe funkcje języka i biblioteki, które mogą przestać działać istniejący kod, który jest zgodny z określoną wersją języka standard. Domyślnie **/STD: c ++ 14** jest określony, która wyłącza języka i funkcji biblioteki standardowej, które znajdują się w nowszych wersjach języka C++ standard. Użyj **/STD: c ++ 17** do włączenia funkcji C ++ 17 specyficzne dla standardowego i zachowania. Aby jawnie włączyć, obecnie zaimplementowane kompilatora i funkcje biblioteki standardowej, propozycja standardu następny projekt, należy użyć **/STD: c ++ najnowsze**.

Wartość domyślna **/STD: c ++ 14** opcja udostępnia zestaw funkcji C ++ 14 implementowane za pomocą kompilatora MSVC. Ta opcja powoduje wyłączenie kompilatora i biblioteki standardowej obsługi funkcji, które zostały zmienione lub nowych w nowszych wersjach językowych w warstwie standardowa z wyjątkiem niektórych funkcji C ++ 17 już zaimplementowane w poprzednich wersjach kompilatora MSVC. Aby uniknąć istotne zmiany dotyczące użytkowników, którzy już jakieś zależności od funkcji, które są dostępne począwszy od programu Visual Studio 2015 Update 2, te funkcje pozostać włączone, gdy **/STD: c ++ 14** określono opcję:

- [Reguły automatycznej z kopiowaniem list inicjacji](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)

- [Element TypeName za parametrów szablonu szablonu](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)

- [Usuwanie trójznaków](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)

- [Atrybuty dla przestrzeni nazw oraz wyliczeń](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)

- [literały znakowe U8](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)

Aby uzyskać dodatkowe informacje na które funkcji C ++ 14 i C ++ 17 są włączone podczas **/STD: c ++ 14** jest określony, zobacz uwagi w [Visual zgodność języka C++](../../overview/visual-cpp-language-conformance.md).

**/STD: c ++ 17** opcja umożliwia pełny zestaw funkcji C ++ 17 implementowane za pomocą kompilatora MSVC. Ta opcja powoduje wyłączenie kompilatora i biblioteki standardowej obsługi funkcji, które zostały zmienione lub nowych wersjach pracy roboczą i wad aktualizacje C++ Standard po C ++ 17.

**/STD: c ++ najnowsze** opcja umożliwia wpis-C ++ 17 funkcje języka i biblioteki obecnie wdrażany w kompilatorze i bibliotekach. Mogą one zawierać funkcje C ++ 20 pracy roboczą i wad aktualizacji Standard C++, które nie są uwzględnione w C ++ 17, a także eksperymentalne propozycje standardzie roboczym. Aby uzyskać listę obsługiwanych języków i funkcji biblioteki, zobacz [What's New for Visual C++](../../overview/what-s-new-for-visual-cpp-in-visual-studio.md). **/STD: c ++ najnowsze** opcji nie włącza funkcji chroniony przez **/ eksperymentalne** przełącznika, ale może wymagać, aby je włączyć.

> [!IMPORTANT]
> Funkcje kompilatora i biblioteki, włączane przez **/STD: c ++ najnowsze** są dostarczane jako — jest i nie obsługują. Podlegają istotne zmiany lub usunięcia bez powiadomienia. One w wersji zapoznawczej funkcji języka, które mogą się pojawić w następnej wersji standard, ale jest w toku. Użyj **/STD: c ++ 17** korzystać z funkcji najnowszego standardu ISO C++.

**/STD** opcji obowiązuje podczas kompilacji C++ może zostać wykryte przy użyciu [ \_MSVC\_LANG](../../preprocessor/predefined-macros.md) makro preprocesora. Aby uzyskać więcej informacji, zobacz [makra preprocesora](../../preprocessor/predefined-macros.md).

**/STD: c ++ 14** i **/STD: c ++ najnowsze** opcje są dostępne począwszy od wersji programu Visual Studio 2015 Update 3. **/STD: c ++ 17** opcja jest dostępna począwszy od wersji programu Visual Studio 2017 w wersji 15.3. Jak wspomniano powyżej, niektóre standardzie C ++ 17 zachowanie jest włączone **/STD: c ++ 14** opcja, ale wszystkie inne funkcje C ++ 17, są włączane przez **/STD: c ++ 17**.

> [!NOTE]
> MSVC kompilatora wersji lub aktualizacji poziom, niektórych funkcji C ++ 14 i C ++ 17 może nie być w pełni zaimplementowane lub w pełni zgodna po określeniu **/STD: c ++ 14** lub **/STD: c ++ 17** opcje. Na przykład, kompilator programu Visual Studio 2017 RTM nie obsługuje w pełni języka C ++ 14 zgodność `constexpr`, wyrażenie SFINAE lub wyszukiwanie nazwy fazy 2. Omówienie zgodność języka C++ w programie Visual C++ w wersji, zobacz [Visual zgodność języka C++](../../overview/visual-cpp-language-conformance.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji**, **C/C++**, **języka**.

1. W **standardu języka C++**, wybierz standard języka pomocy technicznej z formantu listy rozwijanej, a następnie wybierz pozycję **OK** lub **Zastosuj** Aby zapisać zmiany.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
