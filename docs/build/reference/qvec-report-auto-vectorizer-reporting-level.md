---
title: /Qvec-raport (Poziom raportowania automatycznej wektoryzacji)
ms.date: 11/04/2016
ms.assetid: 4778c9a3-0692-4085-9b05-1bfeadf4c74a
ms.openlocfilehash: 260cf89d50110f960eb6f320dccbb4a1d80f65bc
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373817"
---
# <a name="qvec-report-auto-vectorizer-reporting-level"></a>/Qvec-raport (Poziom raportowania automatycznej wektoryzacji)

Włącza funkcję raportowania [wektoryzator](../../parallel/auto-parallelization-and-auto-vectorization.md) kompilatora i określa poziom komunikatów informacyjnych dla danych wyjściowych podczas kompilacji.

## <a name="syntax"></a>Składnia

```
/Qvec-report:{1}{2}
```

## <a name="remarks"></a>Uwagi

**/Qvec-Report: 1**<br/>
Wyświetla komunikat informacyjny dla pętli, które są wektorowe.

**/Qvec-Report: 2**<br/>
Wyświetla komunikat informacyjny dla pętli, które są wektorowe i dla pętli, które nie są wektorowe, wraz z kodem przyczyny.

Aby uzyskać informacje na temat kodów przyczyn i komunikatów, zobacz [wektoryzator i paralelizacji messages](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).

### <a name="to-set-the-qvec-report-compiler-option-in-visual-studio"></a>Aby ustawić opcję kompilatora/Qvec-Report w programie Visual Studio

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz polecenie **Właściwości**.

1. W oknie dialogowym **strony właściwości** w obszarze **C/C++** wybierz pozycję **wiersz polecenia**.

1. W polu **dodatkowe opcje** wpisz `/Qvec-report:1` lub `/Qvec-report:2` .

### <a name="to-set-the-qvec-report-compiler-option-programmatically"></a>Aby programowo ustawić opcję kompilatora/Qvec-Report

- Użyj przykładu kodu w <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> .

## <a name="see-also"></a>Zobacz też

[/Q opcje (operacje na niskim poziomie)](q-options-low-level-operations.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Kod natywny wektoryzacji w programie Visual Studio](https://docs.microsoft.com/archive/blogs/nativeconcurrency/auto-vectorizer-in-visual-studio-2012-overview)
