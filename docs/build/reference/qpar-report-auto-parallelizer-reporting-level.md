---
title: /Qpar-raport (Poziom raportowania automatycznej paralelizacji)
ms.date: 11/04/2016
ms.assetid: 562673b9-02da-4bf8-bb64-70bc25ef4651
ms.openlocfilehash: 3a154bdf50e951ee932173cdb65f9e1514011245
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839416"
---
# <a name="qpar-report-auto-parallelizer-reporting-level"></a>/Qpar-raport (Poziom raportowania automatycznej paralelizacji)

Włącza funkcję raportowania [autoparalelizacji](../../parallel/auto-parallelization-and-auto-vectorization.md) kompilatora i określa poziom komunikatów informacyjnych dla danych wyjściowych podczas kompilacji.

## <a name="syntax"></a>Składnia

```
/Qpar-report:{1}{2}
```

## <a name="remarks"></a>Uwagi

**/Qpar-report: 1**<br/>
Wyświetla komunikat informacyjny dotyczący równoległych pętli.

**/Qpar-report: 2**<br/>
Wyświetla komunikat informacyjny dla pętli, które są równoległe, a także dla pętli, które nie są równoległe, wraz z kodem przyczyny.

Komunikaty są raportowane do stdout. Jeśli nie zgłoszono żadnych komunikatów informacyjnych, kod nie zawiera żadnych pętli lub poziom raportowania nie został ustawiony na pętle raportów, które nie są równoległe. Aby uzyskać więcej informacji na temat kodów przyczyn i komunikatów, zobacz [wektoryzator i paralelizacji messages](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).

### <a name="to-set-the-qpar-report-compiler-option-in-visual-studio"></a>Aby ustawić opcję kompilatora/Qpar-report w programie Visual Studio

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz polecenie **Właściwości**.

1. W oknie dialogowym **strony właściwości** w obszarze **C/C++** wybierz pozycję **wiersz polecenia**.

1. W polu **dodatkowe opcje** wpisz `/Qpar-report:1` lub `/Qpar-report:2` .

### <a name="to-set-the-qpar-report-compiler-option-programmatically"></a>Aby programowo ustawić opcję kompilatora/Qpar-report

- Użyj przykładu kodu w <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> .

## <a name="see-also"></a>Zobacz też

[/Q opcje (operacje na niskim poziomie)](q-options-low-level-operations.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Kod natywny wektoryzacji w programie Visual Studio](/archive/blogs/nativeconcurrency/auto-vectorizer-in-visual-studio-2012-overview)
