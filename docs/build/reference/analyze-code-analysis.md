---
title: /analyze (Analiza kodu)
description: Składnia i użycie opcji kompilatora języka Microsoft C++.
ms.date: 07/27/2020
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
ms.openlocfilehash: 643d8428e3760926832429db5a4425e078ed776b
ms.sourcegitcommit: 6e55aeb538b1c39af754f82d6f7738a18f5aa031
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/29/2020
ms.locfileid: "87389795"
---
# <a name="analyze-code-analysis"></a>`/analyze`(Analiza kodu)

Włącza opcje analizy kodu i kontroli.

## <a name="syntax"></a>Składnia

::: moniker range=">=vs-2017"

> **`/analyze`**\
> **`/analyze-`**\
> **`/analyze:autolog`**\
> **`/analyze:autolog-`**\
> **`/analyze:autolog:ext`***rozszerzenie*\
> **`/analyze:log`***Nazwa pliku*\
> **`/analyze:max_paths`***Liczba*\
> **`/analyze:only`**\
> **`/analyze:plugin`***wtyczka — Biblioteka DLL*\
> **`/analyze:quiet`**\
> **`/analyze:ruleset`***zestaw reguł*\
> **`/analyze:stacksize`***Liczba*\
> **`/analyze:WX-`**

::: moniker-end
::: moniker range="vs-2015"

> **`/analyze`**\
> **`/analyze-`**\
> **`/analyze:autolog`**\
> **`/analyze:autolog-`**\
> **`/analyze:autolog:ext`***rozszerzenie*\
> **`/analyze:log`***Nazwa pliku*\
> **`/analyze:max_paths`***Liczba*\
> **`/analyze:only`**\
> **`/analyze:plugin`***wtyczka — Biblioteka DLL*\
> **`/analyze:quiet`**\
> **`/analyze:stacksize`***Liczba*\
> **`/analyze:WX-`**

::: moniker-end

## <a name="arguments"></a>Argumenty

**`/analyze`**\
Włącza analizę w trybie domyślnym. Dane wyjściowe analizy przechodzą do konsoli programu lub okna **danych wyjściowych** programu Visual Studio, jak inne komunikaty o błędach. Użyj **`/analyze-`** , aby jawnie wyłączyć analizę.

**`/analyze:autolog`**\
Szczegółowe wyniki analizatora są zapisywane w postaci kodu XML do pliku o tej samej nazwie podstawowej co plik źródłowy i rozszerzenie *`.pftlog`* . **`/analyze:autolog-`** wyłącza ten plik dziennika.

**`/analyze:autolog:ext`***rozszerzenie*\
Szczegółowe wyniki analizatora są zapisywane w postaci kodu XML do pliku o tej samej nazwie podstawowej co plik źródłowy i rozszerzenie *rozszerzenia*.

**`/analyze:log`***Nazwa pliku*\
Szczegółowe wyniki analizatora są zapisywane w formacie XML do pliku, który jest określony przez *filename*.

**`/analyze:max_paths`***Liczba*\
Parametr *Number* , który jest używany z tą opcją, określa maksymalną liczbę ścieżek kodu do przeanalizowania. Jeśli ten parametr nie jest określony, liczba jest domyślnie 256. Większe wartości powodują dokładniejsze sprawdzanie, ale analiza może trwać dłużej.

**`/analyze:only`**\
Zazwyczaj kompilator generuje kod i sprawdza więcej składni po uruchomieniu analizatora. **`/analyze:only`** Opcja powoduje wyłączenie tego przebiegu generowania kodu. Przyspiesza to analizowanie, ale nie emituje błędów kompilatora i ostrzeżeń, które mogą znajdować się w czasie przekazania kompilatora. Jeśli program nie jest wolny od błędów generowania kodu, wyniki analizy mogą być zawodne. Zalecamy użycie tej opcji tylko wtedy, gdy kod już przeszedł sprawdzanie składni generowania kodu bez błędów.

**`/analyze:plugin`***wtyczka — Biblioteka DLL*\
Włącza określoną preszybką wtyczkę w ramach przebiegów analizy kodu.

::: moniker range="<=vs-2017"

LocalEspC.dll jest wtyczką implementującą testy analizy kodu związane z współbieżnością w zakresie ostrzeżeń C261XX. Na przykład [C26100](/cpp/code-quality/c26100), [C26101](/cpp/code-quality/c26101),..., [C26167](/cpp/code-quality/c26167).

Aby uruchomić LocalEspC.dll, Użyj tej opcji kompilatora:**`/analyze:plugin LocalEspC.dll`**

::: moniker-end
::: moniker range=">=vs-2019"

ConcurrencyCheck.dll implementuje testy analizy kodu związane z współbieżnością w zakresie ostrzeżeń C261XX. Na przykład [C26100](/cpp/code-quality/c26100), [C26101](/cpp/code-quality/c26101),..., [C26167](/cpp/code-quality/c26167).

Aby uruchomić ConcurrencyCheck.dll, najpierw uruchom to polecenie z poziomu wiersza polecenia dewelopera:

```cmd
set Esp.Extensions=ConcurrencyCheck.dll
```

Następnie użyj tej opcji kompilatora: **`/analyze:plugin EspXEngine.dll`** .

Aby uruchomić CppCoreCheck.dll, najpierw uruchom to polecenie z poziomu wiersza polecenia dewelopera:

```cmd
set Esp.Extensions=CppCoreCheck.dll
```

Następnie użyj tej opcji kompilatora: **`/analyze:plugin EspXEngine.dll`** .

::: moniker-end

**`/analyze:quiet`**\
Wyłącza dane wyjściowe analizatora w oknie **danych wyjściowych** konsoli lub programu Visual Studio.

::: moniker range=">=vs-2017"

**`/analyze:ruleset`***FILE_PATH. zestaw reguł*\
Pozwala określić, które zestawy reguł mają być analizowane, łącznie z zestawami reguł niestandardowych, które można utworzyć samodzielnie. Gdy ten przełącznik jest ustawiony, aparat reguł jest bardziej wydajny, ponieważ wyklucza nie należący do określonego zestawu reguł przed uruchomieniem. W przeciwnym razie aparat sprawdza wszystkie reguły.

Zestaw reguł, które są dostarczane z programem Visual Studio, znajduje się w temacie *`%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets`* .

Następujący przykładowy zestaw reguł niestandardowych Instruuje aparat reguł, aby sprawdzał C6001 i C26494. Ten plik można umieścić w dowolnym miejscu, o ile ma *`.ruleset`* rozszerzenie i podać pełną ścieżkę w argumencie.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description="New rules to apply." ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

::: moniker-end

**`/analyze:stacksize`***Liczba*\
Parametr *Number* , który jest używany z tą opcją, określa rozmiar (w bajtach) ramki stosu, dla której jest generowane ostrzeżenie [C6262](/cpp/code-quality/c6262) . Spacja przed *liczbą* jest opcjonalna. Jeśli ten parametr nie jest określony, rozmiar ramki stosu jest domyślnie 16 KB.

**`/analyze:WX-`**\
Ostrzeżenia analizy kodu nie są traktowane jako błędy podczas kompilowania za pomocą programu **`/WX`** . Aby uzyskać więcej informacji, zobacz [ `/WX` (poziom ostrzeżenia)](compiler-option-warning-level.md).

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Analiza kodu dla c/C++ — Omówienie](/cpp/code-quality/code-analysis-for-c-cpp-overview) i [Analiza kodu dla ostrzeżeń c/c++](/cpp/code-quality/code-analysis-for-c-cpp-warnings).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości Konfiguracja ogólna**Analiza kodu**właściwości  >  **General** .

1. Zmodyfikuj co najmniej jedną właściwość **analizy kodu** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

1. Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)\
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
