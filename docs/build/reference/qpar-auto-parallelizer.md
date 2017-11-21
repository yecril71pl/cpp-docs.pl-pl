---
title: -Qpar (automatyczny Paralelizator) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VC.Project.VCCLCompilerTool.EnableParallelCodeGeneration
dev_langs: C++
ms.assetid: 33ecf49d-c0d5-4f34-bce3-84ff03f38918
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 82f33d178799f56465f0d1a9794dacad7c01c77a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="qpar-auto-parallelizer"></a>/Qpar (Automatyczny paralelizator)
Umożliwia [zrównoleglenia automatycznego](../../parallel/auto-parallelization-and-auto-vectorization.md) funkcji kompilator, aby automatycznie parallelize pętli w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Qpar  
```  
  
## <a name="remarks"></a>Uwagi  
 Gdy kompilator automatycznie parallelizes pętli w kodzie, rozprzestrzenia obliczeń na wiele rdzeni procesora. Pętla jest zarządzana z przetwarzaniem tylko wtedy, gdy kompilator Określa, czy dozwolone w tym celu i że paralelizacja może poprawić wydajność.  
  
 `#pragma loop()` Dyrektywy dostępnych Optymalizator parallelize określonych pętle. Aby uzyskać więcej informacji, zobacz [pętli](../../preprocessor/loop.md).  
  
 Aby uzyskać informacje o sposobie włączania komunikaty wyjściowe do automatycznej paralelizacji, zobacz [/Qpar-report (poziom raportowania automatycznej Paralelizacji)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md).  
  
### <a name="to-set-the-qpar-compiler-option-in-visual-studio"></a>Ustawianie opcji kompilatora /Qpar w programie Visual Studio  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, a następnie wybierz pozycję **właściwości**.  
  
2.  W **strony właściwości** okna dialogowego, w obszarze **C/C++**, wybierz pozycję **wiersza polecenia**.  
  
3.  W **dodatkowe opcje** wprowadź `/Qpar`.  
  
### <a name="to-set-the-qpar-compiler-option-programmatically"></a>Aby ustawić programowo /Qpar — opcja kompilatora  
  
-   Użyj przykładowy kod z <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [/Q opcje (operacje na niskim poziomie)](../../build/reference/q-options-low-level-operations.md)   
 [/ Qpar raport (automatyczny Paralelizator poziom raportowania)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [#pragma loop()](../../preprocessor/loop.md)   
 [Programowanie równoległe w kodzie natywnym](http://go.microsoft.com/fwlink/?LinkId=263662)