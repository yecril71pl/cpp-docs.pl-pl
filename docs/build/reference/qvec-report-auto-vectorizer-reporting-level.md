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
ms.openlocfilehash: 85f9d1c63f41b28982018bbe4507ff6bf87158fb
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685856"
---
# <a name="qvec-report-auto-vectorizer-reporting-level"></a>/Qvec-raport (Poziom raportowania automatycznej wektoryzacji)
Włącza funkcję raportowania kompilatora [Auto-Vectorizer](../../parallel/auto-parallelization-and-auto-vectorization.md) i określa stopień komunikaty informacyjne dla danych wyjściowych, podczas kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Qvec-report:{1}{2}  
```  
  
## <a name="remarks"></a>Uwagi  
 **/ Qvec-report: 1**  
 Wyświetla komunikat informacyjny dla pętli, które są zwektoryzowana.  
  
 **/ Qvec-report: 2**  
 Wyświetla komunikat informacyjny dla pętli, które są wektoryzowana i pętli, które są nie jest zwektoryzowana, wraz z kod przyczyny.  
  
 Aby uzyskać informacji na temat kodów przyczyn i komunikaty, zobacz [komunikaty Wektoryzatora i Paralelizatora](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).  
  
### <a name="to-set-the-qvec-report-compiler-option-in-visual-studio"></a>Aby ustawić opcję kompilatora /Qvec-report w programie Visual Studio  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, a następnie wybierz **właściwości**.  
  
2.  W **stron właściwości** dialogowego **C/C++**, wybierz opcję **wiersza polecenia**.  
  
3.  W **dodatkowe opcje** wprowadź `/Qvec-report:1` lub `/Qvec-report:2`.  
  
### <a name="to-set-the-qvec-report-compiler-option-programmatically"></a>Aby programowo ustawić opcję kompilatora /Qvec-report  
  
-   Skorzystaj z tego przykładu kodu w <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [/Q opcje (operacje na niskim poziomie)](../../build/reference/q-options-low-level-operations.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [Programowanie równoległe w kodzie natywnym](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/04/12/auto-vectorizer-in-visual-studio-2012-overview/)