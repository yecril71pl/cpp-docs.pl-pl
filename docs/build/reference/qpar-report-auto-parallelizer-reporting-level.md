---
title: -Qpar-raport (poziom raportowania automatycznej Paralelizacji) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 562673b9-02da-4bf8-bb64-70bc25ef4651
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ab72225287eab71180e80a059bc320829c24b5f7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419272"
---
# <a name="qpar-report-auto-parallelizer-reporting-level"></a>/Qpar-raport (Poziom raportowania automatycznej paralelizacji)

Włącza funkcję raportowania kompilatora [automatycznego Zrównoleglacza](../../parallel/auto-parallelization-and-auto-vectorization.md) i określa stopień komunikaty informacyjne dla danych wyjściowych, podczas kompilacji.

## <a name="syntax"></a>Składnia

```
/Qpar-report:{1}{2}
```

## <a name="remarks"></a>Uwagi

**/ Qpar-report: 1**<br/>
Wyświetla komunikat informacyjny dla pętli, które są zrównoleglona.

**/ Qpar-report: 2**<br/>
Wyświetla komunikat informacyjny dla pętli, które są zrównoleglona, a także dla pętli, które są nie została zrównoleglona, wraz z kod przyczyny.

Komunikaty są zgłaszane do strumienia wyjściowego stdout. Jeśli są zgłaszane nie komunikaty informacyjne, następnie kod zawiera żadne pętle albo poziomu raportowania nie został ustawiony na pętli raportów, które nie została zrównoleglona. Aby uzyskać więcej informacji na temat kodów przyczyn i komunikaty, zobacz [komunikaty Wektoryzatora i Paralelizatora](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).

### <a name="to-set-the-qpar-report-compiler-option-in-visual-studio"></a>Aby ustawić opcję kompilatora /Qpar-report w programie Visual Studio

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, a następnie wybierz **właściwości**.

1. W **stron właściwości** dialogowego **C/C++**, wybierz opcję **wiersza polecenia**.

1. W **dodatkowe opcje** wprowadź `/Qpar-report:1` lub `/Qpar-report:2`.

### <a name="to-set-the-qpar-report-compiler-option-programmatically"></a>Aby programowo ustawić opcję kompilatora /Qpar-report

- Skorzystaj z tego przykładu kodu w <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[/Q Opcje (Operacje na niskim poziomie)](../../build/reference/q-options-low-level-operations.md)<br/>
[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[Programowanie równoległe w kodzie natywnym](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/04/12/auto-vectorizer-in-visual-studio-2012-overview/)