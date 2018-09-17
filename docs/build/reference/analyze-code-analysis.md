---
title: -analyze (analiza kodu) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/26/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.EnablePREfast
- /analyze
- VC.Project.VCCLCompilerTool.PREfastAdditionalOptions
- VC.Project.VCCLCompilerTool.PREfastAdditionalPlugins
dev_langs:
- C++
helpviewer_keywords:
- /analyze compiler option [C++]
- -analyze compiler option [C++]
- analyze compiler option [C++]
ms.assetid: 81da536a-e030-4bd4-be18-383927597d08
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 89f0402eedbe6e49d6ce4095dc8c91ec69e15447
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723609"
---
# <a name="analyze-code-analysis"></a>/analyze (analiza kodu)

Włącza opcje analizy kodu i kontroli.

## <a name="syntax"></a>Składnia

```cmd
/analyze[-][:WX-][:log filename][:quiet][:stacksize number][:max_paths number][:only][:ruleset]
```

## <a name="arguments"></a>Argumenty

/ analyze włącza funkcję analizy w trybie domyślnym. Analiza danych wyjściowych trafia do **dane wyjściowe** okna, podobnie jak inne komunikaty o błędach. Użyj **/ analyze-** Aby jawnie wyłączyć analizę.

/ analyze: WX-określanie **/ analyze: WX -** oznacza, że ostrzeżenia analizy kodu nie są traktowane jako błędy podczas kompilowania przy użyciu **/WX**. Aby uzyskać więcej informacji, zobacz [Wn /W0, / W1, / W2, / W3, / W4, / W1, / W2, / W3, / W4, / Wall / wo, WV, /WX (poziom ostrzegawczy)](../../build/reference/compiler-option-warning-level.md).

/ analyze: log `filename` szczegółowe wyniki analizatora są zapisywane w formacie XML do pliku, który jest określony przez `filename`.

/ analyze: quiet włącza Wyłącz przesyłanie wyjścia analizatora do **dane wyjściowe** okna.

/ analyze: stacksize `number` `number` parametr, który jest używany z tą opcją, określa rozmiar w bajtach ramki stosu, które ostrzeżenia [C6262](/visualstudio/code-quality/c6262) jest generowany. Jeśli ten parametr nie jest określony, rozmiar ramki stosu to domyślnie 16 KB.

/ analyze: max_paths `number` `number` parametr, który jest używany z tą opcją, określa maksymalną liczbę ścieżek kodu do analizy. Jeśli ten parametr nie jest określony, domyślna liczba to 256. Większe wartości wykonują bardziej szczegółowe sprawdzanie, ale analiza może zająć więcej czasu.

/ analyze: tylko zazwyczaj kompilator generuje kod i jest bardziej gruntowne sprawdzanie po uruchomieniu analizatora składni. **/ Analyze: tylko** opcja powoduje wyłączenie tego przebiegu generowania kodu; to sprawia, że analiza szybsze, ale nie są generowane błędy i ostrzeżenia, które mogą być wykryte przez przebieg generowania kodu kompilator kompilacji. Jeśli program nie jest wolny od błędów generowania kodu, wyniki analizy mogą być zawodne; dlatego zaleca się użycie tej opcji tylko wtedy, gdy kod już przechodzi sprawdzanie składni generowania kodu bez błędów.

/ analyze: ruleset `<file_path>.ruleset` można określić reguły, które ustawia w celu analizy, w tym niestandardowych zestawów reguł, można utworzyć samodzielnie. Gdy ta opcja jest ustawiona, aparat reguł jest bardziej wydajne, ponieważ nie obejmuje on niebędących członkami określoną regułą ustawiona przed uruchomieniem. Jeśli przełącznik nie jest ustawiona, aparat sprawdza, czy wszystkie reguły.

Zestawy reguł, które są dostarczane z programem Visual Studio znajdują się w **%VSINSTALLDIR%\Team Tools\Static analizy Tools\Rule zestawów.**

Poniższy przykład niestandardowego zestawu reguł informuje o tym aparat reguł w celu sprawdzenia dostępności C6001 i C26494. Ten plik można umieścić w dowolnym miejscu tak długo, jak przedstawiono w nim `.ruleset` rozszerzenie i możesz podać pełną ścieżkę w argumencie.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

/ analyze: wtyczka umożliwia określona wtyczka PREfast po uruchomieniu część analizy kodu.
LocalEspC.dll to dodatek, który implementuje analizy dotyczące współbieżności kodu sprawdza, czy w zakresie C261XX ostrzeżenia. Na przykład [C26100](/visualstudio/code-quality/c26100), [C26101](/visualstudio/code-quality/c26101),..., [C26167](/visualstudio/code-quality/c26167).

Aby uruchomić LocalEspC.dll, użyj tej opcji kompilatora: **/ analyze: wtyczka LocalEspC.dll**

Aby uruchomić CppCoreCheck.dll, najpierw uruchom następujące polecenie w wierszu polecenia dla deweloperów:

```cmd
set Esp.Extensions=CppCoreCheck.dll
```

Następnie użyj tej opcji kompilatora: **/ analyze: wtyczka EspXEngine.dll**.

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [analiza kodu C/C++ — Przegląd](/visualstudio/code-quality/code-analysis-for-c-cpp-overview) i [Code Analysis for C/C++ — ostrzeżenia](/visualstudio/code-quality/code-analysis-for-c-cpp-warnings).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Rozwiń **właściwości konfiguracji** węzła.

1. Rozwiń **analizy kodu** węzła.

1. Wybierz **ogólne** stronę właściwości.

1. Zmodyfikuj jedną lub więcej **analizy kodu** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>.

## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora](../../build/reference/compiler-options.md)
- [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)