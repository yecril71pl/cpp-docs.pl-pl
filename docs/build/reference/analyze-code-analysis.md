---
title: /analyze (Analiza kodu)
ms.date: 10/15/2019
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
ms.openlocfilehash: c0cebe1cbd160bdec257a960f90039c1af3bfee2
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416053"
---
# <a name="analyze-code-analysis"></a>/analyze (Analiza kodu)

Włącza opcje analizy kodu i kontroli.

## <a name="syntax"></a>Składnia

> **/analyze**[-] [ **: WX-** ] [ **: log** *Nazwa pliku*] [ **: Quiet**] **[: STACKSIZE** *numer*] [ **: max_paths** *numer*] [ **: tylko**] [ **: zestaw** *reguł] [* **:p lugin** *wtyczka-dll*]

## <a name="arguments"></a>Argumenty

**/analyze**\
Włącza funkcję analizy w trybie domyślnym. Dane wyjściowe analizy przechodzą do okna **danych wyjściowych** , jak inne komunikaty o błędach. Użyj **/analyze-** , aby jawnie wyłączyć analizę.

**/analyze: WX-** \
Ostrzeżenia analizy kodu nie są traktowane jako błędy podczas kompilowania za pomocą **/WX**. Aby uzyskać więcej informacji, zobacz [/WX (poziom ostrzeżeń)](compiler-option-warning-level.md).

**/analyze: log** *filename*\
Szczegółowe wyniki analizatora są zapisywane w formacie XML do pliku, który jest określony przez *filename*.

**/analyze: quiet**\
Wyłącza dane wyjściowe analizatora w oknie **danych wyjściowych** .

**/analyze: STACKSIZE** *Number*\
Parametr *Number* , który jest używany z tą opcją, określa rozmiar (w bajtach) ramki stosu, dla której jest generowane ostrzeżenie [C6262](/cpp/code-quality/c6262) . Spacja przed *liczbą* jest opcjonalna. Jeśli ten parametr nie jest określony, rozmiar ramki stosu jest domyślnie 16 KB.

**/analyze: max_paths** *numer*\
Parametr *Number* , który jest używany z tą opcją, określa maksymalną liczbę ścieżek kodu do przeanalizowania. Jeśli ten parametr nie jest określony, liczba jest domyślnie 256. Większe wartości powodują dokładniejsze sprawdzanie, ale analiza może trwać dłużej.

**/analyze: tylko**\
Zazwyczaj po uruchomieniu analizatora kompilator generuje kod i wykonuje bardziej gruntowne sprawdzanie składni. Opcja **/analyze: Only** powoduje wyłączenie tego przebiegu generowania kodu. Przyspiesza to analizowanie, ale błędy kompilacji i ostrzeżenia, które mogą znajdować się w czasie przekazania kompilatora, nie są emitowane. Jeśli program nie jest wolny od błędów generowania kodu, wyniki analizy mogą być zawodne. Zalecamy użycie tej opcji tylko wtedy, gdy kod już przeszedł sprawdzanie składni generowania kodu bez błędów.

**/analyze: zestaw reguł** *FILE_PATH. zestaw reguł*\
Pozwala określić, które zestawy reguł mają być analizowane, łącznie z zestawami reguł niestandardowych, które można utworzyć samodzielnie. Gdy ten przełącznik jest ustawiony, aparat reguł jest bardziej wydajny, ponieważ wyklucza nie należący do określonego zestawu reguł przed uruchomieniem. W przeciwnym razie aparat sprawdza wszystkie reguły.

Zestawy reguł dostarczane z programem Visual Studio znajdują się w *zestawach%VSInstallDir%\Team Tools\Static Analysis Tools\Rule.*

Następujący przykładowy zestaw reguł niestandardowych Instruuje aparat reguł, aby sprawdzał C6001 i C26494. Ten plik można umieścić w dowolnym miejscu, tak długo, jak ma rozszerzenie `.ruleset` i podać pełną ścieżkę w argumencie.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

**/analyze:** wtyczka wtyczki *-dll*\
Włącza określoną preszybką wtyczkę w ramach przebiegów analizy kodu.

::: moniker range="<=vs-2017"

LocalEspC. dll jest wtyczką implementującą testy analizy kodu powiązane z współbieżnością w zakresie ostrzeżeń C261XX. Na przykład [C26100](/cpp/code-quality/c26100), [C26101](/cpp/code-quality/c26101),..., [C26167](/cpp/code-quality/c26167).

Aby uruchomić LocalEspC. dll, Użyj tej opcji kompilatora: **/analyze: plugin LocalEspC. dll**

::: moniker-end
::: moniker range=">=vs-2019"

ConcurrencyCheck. dll implementuje testy analizy kodu dotyczące współbieżności w zakresie ostrzeżeń C261XX. Na przykład [C26100](/cpp/code-quality/c26100), [C26101](/cpp/code-quality/c26101),..., [C26167](/cpp/code-quality/c26167).

Aby uruchomić ConcurrencyCheck. dll, najpierw uruchom to polecenie w wierszu polecenia dewelopera:

```cmd
set Esp.Extensions=ConcurrencyCheck.dll
```

Następnie użyj tej opcji kompilatora: **/analyze: plugin EspXEngine. dll**.

::: moniker-end

Aby uruchomić CppCoreCheck. dll, najpierw uruchom to polecenie w wierszu polecenia dewelopera:

```cmd
set Esp.Extensions=CppCoreCheck.dll
```

Następnie użyj tej opcji kompilatora: **/analyze: plugin EspXEngine. dll**.

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Analiza kodu dla cC++ /Overview](/cpp/code-quality/code-analysis-for-c-cpp-overview) i [Analiza kodu dla cC++ /](/cpp/code-quality/code-analysis-for-c-cpp-warnings)Warnings.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Właściwości konfiguracji** > stronie właściwości **Ogólne** > **Analiza kodu** .

1. Zmodyfikuj co najmniej jedną właściwość **analizy kodu** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

1. Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)\
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
