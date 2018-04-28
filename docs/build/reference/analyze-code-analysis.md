---
title: -analyze (analiza kodu) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/26/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0f706c3ff32635384766ac2c028cc0e5096118b8
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="analyze-code-analysis"></a>/analyze (analiza kodu)

Włącza opcje analizy kodu i kontroli.

## <a name="syntax"></a>Składnia

```cmd
/analyze[-][:WX-][:log filename][:quiet][:stacksize number][:max_paths number][:only][:ruleset]
```

## <a name="arguments"></a>Argumenty

 /analyze  
 Włącza funkcję analizy w trybie domyślnym. Analizy danych wyjściowych przechodzi do **dane wyjściowe** okna, podobnie jak inne komunikaty o błędach. Użyj **/ analyze-** jawnie wyłączyć analizy.

 /analyze:WX-  
 Określanie **/ analyze: WX -** oznacza, że ostrzeżeń analizy kodu nie są traktowane jako błędy podczas kompilowania przy użyciu **wx**. Aby uzyskać więcej informacji, zobacz [/w, /W0, /W1, /W2, /W3, / W4, /w1, /w2, /w3, / W4, / Wall, /wd, / możemy /wo, /Wv, wx (poziom ostrzegawczy)](../../build/reference/compiler-option-warning-level.md).

 / analyze: dziennika `filename`  
 Analizator szczegółowe wyniki są zapisywane jako XML do pliku określonego przez `filename`.

 /analyze:quiet  
 Wyłącza dane wyjściowe analizatora do **dane wyjściowe** okna.

 / analyze: stacksize `number`  
 `number` Parametr, który jest używany z tą opcją Określa rozmiar w bajtach ramki stosu dla ostrzeżenia, które [C6262](/visualstudio/code-quality/c6262) jest generowany. Jeśli ten parametr nie jest określony, rozmiar ramki stosu to domyślnie 16 KB.

 / analyze: max_paths `number`  
 `number` Parametr, który jest używany z tą opcją określa maksymalną liczbę ścieżek kodu do analizy. Jeśli ten parametr nie jest określony, domyślna liczba to 256. Większe wartości wykonują bardziej szczegółowe sprawdzanie, ale analiza może zająć więcej czasu.

 /analyze:only  
 Zazwyczaj po uruchomieniu analizatora kompilator generuje kod i wykonuje bardziej gruntowne sprawdzanie składni. **/ Analyze: tylko** opcja powoduje wyłączenie tego przebiegu generowania kodu; analizy dzięki temu szybsze, ale nie są emitowane kompilacji błędów i ostrzeżeń, które może być wykryte przez program przebiegu generowania kodu kompilator. Jeśli program nie jest wolny od błędów generowania kodu, wyniki analizy mogą być zawodne; dlatego zaleca się użycie tej opcji tylko wtedy, gdy kod już przechodzi sprawdzanie składni generowania kodu bez błędów.

 / analyze: zestaw reguł `<file_path>.ruleset`  
Można określić reguły, które ustawia do analizy, w tym niestandardowych zestawów reguł, możesz utworzyć samodzielnie. Gdy ta opcja jest ustawiona, aparat reguł jest bardziej wydajne, ponieważ nie obejmuje on niebędących członkami określonej reguły ustawiona przed uruchomieniem. Jeśli przełącznik nie jest ustawiona, aparat sprawdza wszystkie reguły.

Zestawy reguł, które są dostarczane z programem Visual Studio znajdują się w **%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets.**

Następujące przykładowe niestandardowego zestawu reguł informuje aparatu reguł, aby sprawdzić C6001 i C26494. Ten plik można umieścić w dowolnym tak długo, jak długo ma `.ruleset` rozszerzenie i należy wprowadzić pełną ścieżkę w argumencie.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

/ analyze: wtyczki  
Umożliwia określonej wtyczki programu PREfast podczas działania w ramach analizy kodu. LocalEspC.dll jest wtyczkę, która implementuje analizy współbieżności związane z kodu sprawdza się w zakresie C261XX ostrzeżenia. Na przykład [C26100](/visualstudio/code-quality/c26100), [C26101](/visualstudio/code-quality/c26101),..., [C26167](/visualstudio/code-quality/c26167).

Aby uruchomić LocalEspC.dll, użyj tej opcji kompilatora: **/ analyze: dodatek LocalEspC.dll**

Aby uruchomić CppCoreCheck.dll, najpierw uruchom to polecenie z wiersza polecenia developer:

```cmd
set Esp.Extensions=CppCoreCheck.dll
```

Następnie użyj tej opcji kompilatora: **/ analyze: dodatek EspXEngine.dll**.

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [analizy kodu dla C/C++ — omówienie](/visualstudio/code-quality/code-analysis-for-c-cpp-overview) i [analizy kodu dla C/C++ — ostrzeżenia](/visualstudio/code-quality/code-analysis-for-c-cpp-warnings).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Rozwiń węzeł **właściwości konfiguracji** węzła.

1. Rozwiń węzeł **analizy kodu** węzła.

1. Wybierz **ogólne** strony właściwości.

1. Zmodyfikuj jedną lub więcej **analizy kodu** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>.

## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora](../../build/reference/compiler-options.md)
- [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)