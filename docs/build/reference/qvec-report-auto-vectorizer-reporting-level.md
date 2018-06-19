---
title: -Qvec-raport (poziom raportowania automatycznej Wektoryzacji) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4778c9a3-0692-4085-9b05-1bfeadf4c74a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ddbb68c20ade9f66215d3a60f2db7ea545409a1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377489"
---
# <a name="qvec-report-auto-vectorizer-reporting-level"></a>/Qvec-raport (Poziom raportowania automatycznej wektoryzacji)
Włącza funkcję raportowania kompilatora [Wektoryzowania automatycznego](../../parallel/auto-parallelization-and-auto-vectorization.md) i określa poziom komunikaty informacyjne dla danych wyjściowych podczas kompilowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Qvec-report:{1}{2}  
```  
  
## <a name="remarks"></a>Uwagi  
 **/ Qvec-report: 1**  
 Wyświetla komunikat informacyjny dla pętli, które są Przekształcono.  
  
 **/ Qvec-report: 2**  
 Wyświetla komunikat informacyjny dla pętli, które są Przekształcono i dla pętli, które nie są Przekształcono wraz z kod przyczyny.  
  
 Uzyskać informacji o kody przyczyn i komunikaty, zobacz [komunikaty Wektoryzatora i Paralelizatora](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).  
  
### <a name="to-set-the-qvec-report-compiler-option-in-visual-studio"></a>Ustawianie opcji kompilatora /Qvec-report w programie Visual Studio  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, a następnie wybierz pozycję **właściwości**.  
  
2.  W **strony właściwości** okna dialogowego, w obszarze **C/C++**, wybierz pozycję **wiersza polecenia**.  
  
3.  W **dodatkowe opcje** wprowadź `/Qvec-report:1` lub `/Qvec-report:2`.  
  
### <a name="to-set-the-qvec-report-compiler-option-programmatically"></a>Aby ustawić programowo /Qvec-report — opcja kompilatora  
  
-   Użyj przykładowy kod z <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [/Q opcje (operacje na niskim poziomie)](../../build/reference/q-options-low-level-operations.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [Programowanie równoległe w kodzie natywnym](http://go.microsoft.com/fwlink/p/?linkid=263662)