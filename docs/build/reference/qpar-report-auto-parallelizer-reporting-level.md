---
title: -Qpar-raport (poziom raportowania automatycznej Paralelizacji) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 562673b9-02da-4bf8-bb64-70bc25ef4651
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 70ae055d69341cc773b8b40ed1111b65ba5683cf
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="qpar-report-auto-parallelizer-reporting-level"></a>/Qpar-raport (Poziom raportowania automatycznej paralelizacji)
Włącza funkcję raportowania kompilatora [automatycznej Paralelizacji](../../parallel/auto-parallelization-and-auto-vectorization.md) i określa poziom komunikaty informacyjne dla danych wyjściowych podczas kompilowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Qpar-report:{1}{2}  
```  
  
## <a name="remarks"></a>Uwagi  
 **/ Qpar-report: 1**  
 Wyświetla komunikat informacyjny dla pętli, które są zarządzana z przetwarzaniem.  
  
 **/ Qpar-report: 2**  
 Wyświetla komunikat informacyjny dla pętli, które są zarządzana z przetwarzaniem, a także dla pętli, które są nie została zrównoleglona, wraz z kod przyczyny.  
  
 Komunikaty są zgłaszane do stdout. Jeśli są zgłaszane nie komunikaty informacyjne, następnie kod zawiera żadne pętle albo poziom raportowania nie został ustawiony na pętle raportów, które nie została zrównoleglona. Aby uzyskać więcej informacji na temat Kody przyczyn i komunikaty, zobacz [komunikaty Wektoryzatora i Paralelizatora](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).  
  
### <a name="to-set-the-qpar-report-compiler-option-in-visual-studio"></a>Ustawianie opcji kompilatora /Qpar-report w programie Visual Studio  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, a następnie wybierz pozycję **właściwości**.  
  
2.  W **strony właściwości** okna dialogowego, w obszarze **C/C++**, wybierz pozycję **wiersza polecenia**.  
  
3.  W **dodatkowe opcje** wprowadź `/Qpar-report:1` lub `/Qpar-report:2`.  
  
### <a name="to-set-the-qpar-report-compiler-option-programmatically"></a>Aby ustawić programowo /Qpar-report — opcja kompilatora  
  
-   Użyj przykładowy kod z <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [/Q opcje (operacje na niskim poziomie)](../../build/reference/q-options-low-level-operations.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [Programowanie równoległe w kodzie natywnym](http://go.microsoft.com/fwlink/p/?linkid=263662)