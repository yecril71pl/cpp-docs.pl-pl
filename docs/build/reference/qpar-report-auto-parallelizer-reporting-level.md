---
title: /Qpar-raport (Poziom raportowania automatycznej paralelizacji)
ms.date: 11/04/2016
ms.assetid: 562673b9-02da-4bf8-bb64-70bc25ef4651
ms.openlocfilehash: 25732900fa201258331dcb8eee96af9ba97a6def
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319957"
---
# <a name="qpar-report-auto-parallelizer-reporting-level"></a>/Qpar-raport (Poziom raportowania automatycznej paralelizacji)

Włącza funkcję raportowania kompilatora [automatycznego Zrównoleglacza](../../parallel/auto-parallelization-and-auto-vectorization.md) i określa stopień komunikaty informacyjne dla danych wyjściowych, podczas kompilacji.

## <a name="syntax"></a>Składnia

```
/Qpar-report:{1}{2}
```

## <a name="remarks"></a>Uwagi

**/Qpar-report:1**<br/>
Wyświetla komunikat informacyjny dla pętli, które są zrównoleglona.

**/Qpar-report:2**<br/>
Wyświetla komunikat informacyjny dla pętli, które są zrównoleglona, a także dla pętli, które są nie została zrównoleglona, wraz z kod przyczyny.

Komunikaty są zgłaszane do strumienia wyjściowego stdout. Jeśli są zgłaszane nie komunikaty informacyjne, następnie kod zawiera żadne pętle albo poziomu raportowania nie został ustawiony na pętli raportów, które nie została zrównoleglona. Aby uzyskać więcej informacji na temat kodów przyczyn i komunikaty, zobacz [komunikaty Wektoryzatora i Paralelizatora](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).

### <a name="to-set-the-qpar-report-compiler-option-in-visual-studio"></a>Aby ustawić opcję kompilatora /Qpar-report w programie Visual Studio

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, a następnie wybierz **właściwości**.

1. W **stron właściwości** dialogowego **C/C++**, wybierz opcję **wiersza polecenia**.

1. W **dodatkowe opcje** wprowadź `/Qpar-report:1` lub `/Qpar-report:2`.

### <a name="to-set-the-qpar-report-compiler-option-programmatically"></a>Aby programowo ustawić opcję kompilatora /Qpar-report

- Skorzystaj z tego przykładu kodu w <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[/Q Opcje (Operacje na niskim poziomie)](q-options-low-level-operations.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Programowanie równoległe w kodzie natywnym](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/04/12/auto-vectorizer-in-visual-studio-2012-overview/)
