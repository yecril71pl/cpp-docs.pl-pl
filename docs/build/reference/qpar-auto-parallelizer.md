---
title: -Qpar (automatyczny Paralelizator) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableParallelCodeGeneration
dev_langs:
- C++
ms.assetid: 33ecf49d-c0d5-4f34-bce3-84ff03f38918
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 24c3501422a0bfbaba8aea0e45c102f63948b7db
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43684508"
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
  
 Aby uzyskać informacje o sposobie włączania komunikaty wyjściowe do automatycznego zrównoleglacza, zobacz [/Qpar-report (poziom raportowania automatycznej Paralelizacji)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md).  
  
### <a name="to-set-the-qpar-compiler-option-in-visual-studio"></a>Aby ustawić opcję kompilatora /Qpar w programie Visual Studio  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, a następnie wybierz **właściwości**.  
  
2.  W **stron właściwości** dialogowego **C/C++**, wybierz opcję **wiersza polecenia**.  
  
3.  W **dodatkowe opcje** wprowadź `/Qpar`.  
  
### <a name="to-set-the-qpar-compiler-option-programmatically"></a>Aby programowo ustawić opcję kompilatora /Qpar  
  
-   Skorzystaj z tego przykładu kodu w <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [/Q opcje (operacje na niskim poziomie)](../../build/reference/q-options-low-level-operations.md)   
 [/ Qpar raport (raportowania automatycznej Paralelizacji poziomu)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [#pragma loop()](../../preprocessor/loop.md)   
 [Programowanie równoległe w kodzie natywnym](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/04/12/auto-vectorizer-in-visual-studio-2012-overview/)