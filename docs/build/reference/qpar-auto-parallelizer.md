---
title: /Qpar (Automatyczny paralelizator)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableParallelCodeGeneration
ms.assetid: 33ecf49d-c0d5-4f34-bce3-84ff03f38918
ms.openlocfilehash: effe1ad7799022ea85184513de1dc48c72d6bfcb
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839442"
---
# <a name="qpar-auto-parallelizer"></a>/Qpar (Automatyczny paralelizator)

Włącza funkcję [autoparalelizacji](../../parallel/auto-parallelization-and-auto-vectorization.md) kompilatora, aby automatycznie zrównoleglanie pętle w kodzie.

## <a name="syntax"></a>Składnia

```
/Qpar
```

## <a name="remarks"></a>Uwagi

Gdy kompilator automatycznie parallelizes pętle w kodzie, rozłożenie obliczeń na wiele rdzeni procesora. Pętla jest równoległa tylko wtedy, gdy kompilator ustali, że jest to dozwolone, i że przetwarzanie równoległe zwiększy wydajność.

`#pragma loop()`Dostępne są te dyrektywy, które ułatwiają optymalizatorom zrównoleglanie określonych pętli. Aby uzyskać więcej informacji, zobacz [Pętla](../../preprocessor/loop.md).

Aby uzyskać informacje o sposobie włączania komunikatów wyjściowych dla autoparalelizacji, zobacz [/Qpar-report (na poziomie raportowania autoparalelizacji)](qpar-report-auto-parallelizer-reporting-level.md).

### <a name="to-set-the-qpar-compiler-option-in-visual-studio"></a>Aby ustawić opcję kompilatora/Qpar w programie Visual Studio

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz polecenie **Właściwości**.

1. W oknie dialogowym **strony właściwości** w obszarze **C/C++** wybierz pozycję **wiersz polecenia**.

1. W polu **dodatkowe opcje** wprowadź wartość `/Qpar` .

### <a name="to-set-the-qpar-compiler-option-programmatically"></a>Aby programowo ustawić opcję kompilatora/Qpar

- Użyj przykładu kodu w <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> .

## <a name="see-also"></a>Zobacz też

[/Q opcje (operacje na niskim poziomie)](q-options-low-level-operations.md)<br/>
[/Qpar-report (poziom raportowania autoparalelizacji)](qpar-report-auto-parallelizer-reporting-level.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Pętla #pragma ()](../../preprocessor/loop.md)<br/>
[Kod natywny wektoryzacji w programie Visual Studio](/archive/blogs/nativeconcurrency/auto-vectorizer-in-visual-studio-2012-overview)
