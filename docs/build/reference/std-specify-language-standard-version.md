---
title: -std (Określ języka w wersji Standard) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/16/2017
ms.topic: reference
f1_keywords:
- /std
- -std
- VC.Project.VCCLCompilerTool.CppLanguageStandard
dev_langs:
- C++
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7fed80f0f9763b7e988c40a9d9f38f4e0f18eeb1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378850"
---
# <a name="std-specify-language-standard-version"></a>/STD (Określanie języka w wersji Standard)

Włącz obsługiwane funkcje języka C++ z określonej wersji standard języka C++.

## <a name="syntax"></a>Składnia

> /STD: [c ++ 14 | c ++ 17 | c ++ najnowszej]

## <a name="remarks"></a>Uwagi

**/Std** opcja jest używana do sterowania programowania standardowe funkcje językowe, włączone podczas kompilowania kodu C++ ISO określonej wersji. Ta opcja pozwala wyłączyć obsługę niektóre nowe funkcje języka i biblioteki, które mogą być dzielone standardowe istniejący kod zgodnego z określoną wersją języka. Domyślnie **/std:c ++ 14** jest określony, która wyłącza języka i odnaleźć w nowszych wersjach języka C++ standardowe funkcje standardowej biblioteki. Użyj **/std:c ++ 17** do włączenia języka C ++ 17 standard specyficzne i zachowania. Aby jawnie włączyć najnowszych obsługiwanych kompilatora i funkcje standardowej biblioteki, użyj **/std:c ++ najnowsze**.

Wartość domyślna **/std:c ++ 14** opcji udostępnia zestaw funkcji C ++ 14 implementowane przez kompilator języka Visual C++. Ta opcja powoduje wyłączenie kompilator i biblioteki standardowej obsługi funkcji, które zostały zmienione lub nowych w nowszych wersjach języka standard, z wyjątkiem niektórych funkcji C ++ 17 już zaimplementowany w poprzednich wersjach kompilatora Visual C++. Aby uniknąć fundamentalne zmiany dla użytkowników, którzy już zostały zależności na funkcje dostępne począwszy od programu Visual Studio 2015 Update 2, te funkcje pozostać włączone, gdy **/std:c ++ 14** określono opcję:

- [Zasady automatycznego przy nawiasach init list](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)

- [Właściwość TypeName w parametrów szablonu szablonu](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)

- [Usuwanie trigramów](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)

- [Atrybuty przestrzeni nazw i moduły wyliczające](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)

- [literały znaków U8](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)

Aby uzyskać dodatkowe informacje w języku C ++ 14 i C ++ 17 funkcje są włączone podczas **/std:c ++ 14** jest określony, zobacz uwagi w [Visual zgodność języka C++](../../visual-cpp-language-conformance.md).
  
**/Std:c ++ 17** opcja umożliwia pełnego zestawu funkcji C ++ 17 implementowane przez kompilator języka Visual C++. Ta opcja powoduje wyłączenie kompilator i biblioteki standardowej obsługi dla funkcji, które zostały zmienione lub nowego w wersji aktualizacji pracy roboczą i usterką standardu C++ po C ++ 17.  
  
**/Std:c ++ najnowsze** opcja umożliwia zestaw funkcji języka i biblioteki C++ implementowane przez Visual C++ do śledzenia najbardziej najnowsze C ++ 20 pracy roboczą i usterką aktualizacje standardu C++, które nie znajdują się w języku C ++ 17. Użyj tego przełącznika można pobrać post-C ++ 17 języka funkcje obsługiwane przez kompilator i bibliotekę standardową. Aby uzyskać listę obsługiwanych języków i funkcje biblioteki, zobacz [nowości w języku Visual C++](../../what-s-new-for-visual-cpp-in-visual-studio.md). **/Std:c ++ najnowsze** opcja nie obsługuje funkcji chroniony przez **/ eksperymentalne** przełącznika.  
  
**/Std** opcji skutkuje podczas kompilacji C++ mogą być wykrywane przy użyciu [ \_MSVC\_LANG](../../preprocessor/predefined-macros.md) makro preprocesora. Aby uzyskać więcej informacji, zobacz [makra preprocesora](../../preprocessor/predefined-macros.md).

**/Std:c ++ 14** i **/std:c ++ najnowsze** opcje są dostępne począwszy od wersji programu Visual C++ 2015 Update 3. **/Std:c ++ 17** opcja jest dostępne począwszy od wersji programu Visual C++ 2017 wersji 15 ustęp 3. Jak wspomniano powyżej, niektóre standardzie C ++ 17 zachowanie jest włączone przez **/std:c ++ 14** opcja, ale wszystkie inne funkcji C ++ 17 są włączane przez **/std:c ++ 17**.
  
> [!NOTE]
> Zależnie od tego, Visual C++ kompilatora wersji lub aktualizacji, niektórych funkcji C ++ 14 i C ++ 17 mogą nie zostać w pełni zaimplementowana lub pełni zgodność po określeniu **/std:c ++ 14** lub **/std:c ++ 17** opcje. Na przykład kompilatora Visual C++ 2017 RTM nie obsługuje w pełni C ++ 14 zgodność `constexpr`, wyrażenie techniki SFINAE lub wyszukiwanie nazwy fazy 2. Omówienie zgodność języka C++ w programie Visual C++ w wersji, zobacz [Visual zgodność języka C++](../../visual-cpp-language-conformance.md). 
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **właściwości konfiguracji**, **C/C++**, **języka**.  
  
3.  W **języka C++ — standardowe**, wybierz standard języka aby obsługiwać z formantu listy rozwijanej, a następnie wybierz pozycję **OK** lub **Zastosuj** Aby zapisać zmiany.  
  
## <a name="see-also"></a>Zobacz także  
  
[Opcje kompilatora](../../build/reference/compiler-options.md)   
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
