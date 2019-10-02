---
title: /analyze (analiza kodu)
ms.date: 10/01/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.EnablePREfast
- /analyze
- VC.Project.VCCLCompilerTool.PREfastAdditionalOptions
- VC.Project.VCCLCompilerTool.PREfastAdditionalPlugins
helpviewer_keywords:
- /analyze compiler option [C++]
- -analyze compiler option [C++]
- analyze compiler option [C++]
ms.assetid: 81da536a-e030-4bd4-be18-383927597d08
ms.openlocfilehash: d647045d76dc32544f8146424b220547890b0943
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816333"
---
# <a name="analyze-code-analysis"></a>/analyze (analiza kodu)

Włącza opcje analizy kodu i kontroli.

## <a name="syntax"></a>Składnia

```cmd
/analyze[-][:WX-][:log filename][:quiet][:stacksize number][:max_paths number][:only][:ruleset]
```

## <a name="arguments"></a>Argumenty

/analyze włącza analizę w trybie domyślnym. Dane wyjściowe analizy przechodzą do okna **danych wyjściowych** , jak inne komunikaty o błędach. Użyj **/analyze-** , aby jawnie wyłączyć analizę.

/analyze: WX-Określanie **/analyze: WX-** oznacza, że ostrzeżenia analizy kodu nie są traktowane jako błędy podczas kompilowania przy użyciu **/WX**. Aby uzyskać więcej informacji, zobacz [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/wo,/WV,/WX (poziom ostrzeżeń)](compiler-option-warning-level.md).

/analyze: log `filename` szczegółowe wyniki analizatora są zapisywane jako XML do pliku, który jest określony przez `filename`.

/analyze: Quiet wyłącza dane wyjściowe analizatora w oknie **danych wyjściowych** .

/analyze: STACKSIZE `number` parametr `number`, który jest używany z tą opcją określa rozmiar (w bajtach) ramki stosu, dla której jest generowane ostrzeżenie [C6262](/visualstudio/code-quality/c6262) . Spacja przed `number` jest opcjonalna. Jeśli ten parametr nie jest określony, rozmiar ramki stosu to domyślnie 16 KB.

/analyze: max_paths `number` parametr `number`, który jest używany z tą opcją, określa maksymalną liczbę ścieżek kodu do przeanalizowania. Jeśli ten parametr nie jest określony, domyślna liczba to 256. Większe wartości wykonują bardziej szczegółowe sprawdzanie, ale analiza może zająć więcej czasu.

/analyze: zazwyczaj kompilator generuje kod i sprawdza więcej składni po uruchomieniu analizatora. Opcja **/analyze: Only** powoduje wyłączenie tego przebiegu generowania kodu; przyspiesza to analizę, ale błędy kompilacji i ostrzeżenia, które mogły zostać wykryte przez przebieg generowania kodu kompilatora nie są emitowane. Jeśli program nie jest wolny od błędów generowania kodu, wyniki analizy mogą być zawodne; dlatego zaleca się użycie tej opcji tylko wtedy, gdy kod już przechodzi sprawdzanie składni generowania kodu bez błędów.

/analyze: zestaw reguł `<file_path>.ruleset` pozwala określić, które zestawy reguł mają być analizowane, łącznie z zestawami reguł niestandardowych, które można utworzyć samodzielnie. Gdy ten przełącznik jest ustawiony, aparat reguł jest bardziej wydajny, ponieważ wyklucza nie należący do określonego zestawu reguł przed uruchomieniem. Gdy przełącznik nie jest ustawiony, aparat sprawdza wszystkie reguły.

Zestawy reguł dostarczane z programem Visual Studio znajdują się w **zestawach%VSInstallDir%\Team Tools\Static Analysis Tools\Rule.**

Następujący przykładowy zestaw reguł niestandardowych Instruuje aparat reguł, aby sprawdzał C6001 i C26494. Ten plik można umieścić w dowolnym miejscu, o ile ma rozszerzenie `.ruleset` i podaje pełną ścieżkę w argumencie.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

/analyze: wtyczka włącza określoną, preszybką wtyczkę w ramach przebiegów analizy kodu.
LocalEspC. dll jest wtyczką implementującą testy analizy kodu powiązane z współbieżnością w zakresie ostrzeżeń C261XX. Na przykład [C26100](/visualstudio/code-quality/c26100), [C26101](/visualstudio/code-quality/c26101),..., [C26167](/visualstudio/code-quality/c26167).

Aby uruchomić LocalEspC. dll, Użyj tej opcji kompilatora: **/analyze: plugin LocalEspC. dll**

Aby uruchomić CppCoreCheck. dll, najpierw uruchom to polecenie w wierszu polecenia dewelopera:

```cmd
set Esp.Extensions=CppCoreCheck.dll
```

Następnie użyj tej opcji kompilatora: **/analyze: plugin EspXEngine. dll**.

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Analiza kodu dla cC++ /Overview](/visualstudio/code-quality/code-analysis-for-c-cpp-overview) i [Analiza kodu dla cC++ /](/visualstudio/code-quality/code-analysis-for-c-cpp-warnings)Warnings.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Rozwiń węzeł **Właściwości konfiguracji** .

1. Rozwiń węzeł **Analiza kodu** .

1. Wybierz stronę właściwości **Ogólne** .

1. Zmodyfikuj co najmniej jedną właściwość **analizy kodu** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>.

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora MSVC](compiler-options.md)
- [Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
