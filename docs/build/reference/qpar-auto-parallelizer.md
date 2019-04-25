---
title: /Qpar (Automatyczny paralelizator)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableParallelCodeGeneration
ms.assetid: 33ecf49d-c0d5-4f34-bce3-84ff03f38918
ms.openlocfilehash: c1ddea73c5aa8d3e7e70b45834cb04154bf3b4bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319229"
---
# <a name="qpar-auto-parallelizer"></a>/Qpar (Automatyczny paralelizator)

Włącza [automatycznego Zrównoleglacza](../../parallel/auto-parallelization-and-auto-vectorization.md) funkcji kompilator, aby automatycznie zrównoleglenia pętli w kodzie.

## <a name="syntax"></a>Składnia

```
/Qpar
```

## <a name="remarks"></a>Uwagi

Gdy kompilator automatycznie parallelizes pętli w kodzie, się obliczenia na wiele rdzeni procesora. Pętla jest zrównoleglona tylko wtedy, gdy kompilator Określa, że jest legalne, aby to zrobić i że przetwarzania równoległego mogłyby poprawić wydajność.

`#pragma loop()` Dyrektywy są do dyspozycji Optymalizator zrównoleglenia pętli określonych. Aby uzyskać więcej informacji, zobacz [pętli](../../preprocessor/loop.md).

Aby uzyskać informacje o sposobie włączania komunikaty wyjściowe do automatycznego zrównoleglacza, zobacz [/Qpar-report (poziom raportowania automatycznej Paralelizacji)](qpar-report-auto-parallelizer-reporting-level.md).

### <a name="to-set-the-qpar-compiler-option-in-visual-studio"></a>Aby ustawić opcję kompilatora /Qpar w programie Visual Studio

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, a następnie wybierz **właściwości**.

1. W **stron właściwości** dialogowego **C/C++**, wybierz opcję **wiersza polecenia**.

1. W **dodatkowe opcje** wprowadź `/Qpar`.

### <a name="to-set-the-qpar-compiler-option-programmatically"></a>Aby programowo ustawić opcję kompilatora /Qpar

- Skorzystaj z tego przykładu kodu w <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[/Q Opcje (Operacje na niskim poziomie)](q-options-low-level-operations.md)<br/>
[/Qpar-raport (Poziom raportowania automatycznej paralelizacji)](qpar-report-auto-parallelizer-reporting-level.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[#pragma loop()](../../preprocessor/loop.md)<br/>
[Programowanie równoległe w kodzie natywnym](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/04/12/auto-vectorizer-in-visual-studio-2012-overview/)
