---
title: Analiza kodu C/C++ — Omówienie
ms.date: 04/28/2018
ms.topic: conceptual
helpviewer_keywords:
- annotations, code analysis
- build integration, code analysis
- C/C++ code analysis
- IDE, code analysis
- pragma directive, code analysis
- code analysis, C/C++
- code analysis tool
- command line, code analysis
- C++, code analysis
- check-in policies, code analysis
- '#pragma directives, code analysis'
- C, code analysis
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
ms.openlocfilehash: f128c9722138f453c72ca97b09cc1a69a737dbf6
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504189"
---
# <a name="code-analysis-for-cc-overview"></a>Analiza kodu C/C++ — Omówienie

Narzędzie do analizy kodu C/C++ zawiera informacje o możliwych defektach w kodzie źródłowym języka C/C++. Typowe błędy kodowania zgłoszone przez narzędzie obejmują przepełnienia buforów, niezainicjowaną pamięć, odnośniki wskaźnika o wartości null oraz przecieki pamięci i zasobów. Narzędzie może również uruchamiać sprawdzenia względem [podstawowe wytyczne dotyczące języka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="ide-integrated-development-environment-integration"></a>Integracja IDE (zintegrowane środowisko programistyczne)

Narzędzie do analizy kodu jest w pełni zintegrowane w środowisku IDE programu Visual Studio.

W trakcie procesu kompilacji wszystkie ostrzeżenia wygenerowane dla kodu źródłowego pojawiają się w Lista błędów. Możesz przejść do kodu źródłowego, który spowodował ostrzeżenie, i można wyświetlić dodatkowe informacje o przyczynie problemu oraz ewentualnych rozwiązaniach.

## <a name="command-line-support"></a>Obsługa wiersza polecenia

Możesz również użyć narzędzia analizy z wiersza polecenia, jak pokazano w następującym przykładzie:

```cmd
C:\>cl /analyze Sample.cpp
```

**Program Visual Studio 2017 w wersji 15,7 lub nowszej:** Narzędzie można uruchomić z wiersza polecenia z dowolnym systemem kompilacji, w tym CMake.

## <a name="pragma-support"></a>Obsługa #pragma

Można użyć `#pragma` dyrektywy do traktowania ostrzeżeń jako błędów, włączania lub wyłączania ostrzeżeń oraz pomijania ostrzeżeń dla poszczególnych wierszy kodu. Aby uzyskać więcej informacji, zobacz [dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md).

## <a name="annotation-support"></a>Obsługa adnotacji

Adnotacje poprawiają dokładność analizy kodu. Adnotacje zawierają dodatkowe informacje na temat parametrów funkcji i typów zwracanych. Aby uzyskać więcej informacji, zobacz [Używanie adnotacji sal w celu zmniejszenia wad kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md).

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Uruchom Narzędzie analizy jako część zasad ewidencjonowania

Można wymagać, aby wszystkie operacje ewidencjonowania kodu źródłowego spełniały określone zasady. W szczególności chcesz upewnić się, że analiza została uruchomiona jako krok ostatniej kompilacji lokalnej. Aby uzyskać więcej informacji na temat włączania zasad zaewidencjonowania analizy kodu, zobacz [Tworzenie zasad ewidencjonowania analizy kodu i korzystanie](/visualstudio/code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies)z nich.

## <a name="team-build-integration"></a>Integracja kompilacji zespołowej

W celu uruchomienia narzędzia do analizy kodu w ramach procesu kompilacji DevOps platformy Azure można użyć zintegrowanych funkcji systemu kompilacji. Aby uzyskać więcej informacji, zobacz [Azure Pipelines](/azure/devops/pipelines/index).

## <a name="see-also"></a>Zobacz też

- [Szybki start: analiza kodu C/C++](quick-start-code-analysis-for-c-cpp.md)
- [Przewodnik: Analizowanie kodu C/C++ pod kątem wad](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [Analiza kodu dla ostrzeżeń C/C++](code-analysis-for-c-cpp-warnings.md)
- [Korzystanie z kontrolerów podstawowych wytycznych dotyczących języka C++](using-the-cpp-core-guidelines-checkers.md)
- [Informacje dotyczące narzędzia do sprawdzania podstawowe wytyczne dotyczące języka C++](code-analysis-for-cpp-corecheck.md)
- [Użyj zestawów reguł, aby określić reguły języka C++ do uruchomienia](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Analizowanie jakości sterowników przy użyciu narzędzi do analizy kodu](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [Analiza kodu dla ostrzeżeń dotyczących sterowników](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)
