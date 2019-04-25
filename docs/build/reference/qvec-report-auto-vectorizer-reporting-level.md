---
title: /Qvec-raport (Poziom raportowania automatycznej wektoryzacji)
ms.date: 11/04/2016
ms.assetid: 4778c9a3-0692-4085-9b05-1bfeadf4c74a
ms.openlocfilehash: 655be3581eee4b23a8d0f2bcfaea7d07c8b1b07c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319255"
---
# <a name="qvec-report-auto-vectorizer-reporting-level"></a>/Qvec-raport (Poziom raportowania automatycznej wektoryzacji)

Włącza funkcję raportowania kompilatora [Auto-Vectorizer](../../parallel/auto-parallelization-and-auto-vectorization.md) i określa stopień komunikaty informacyjne dla danych wyjściowych, podczas kompilacji.

## <a name="syntax"></a>Składnia

```
/Qvec-report:{1}{2}
```

## <a name="remarks"></a>Uwagi

**/Qvec-report:1**<br/>
Wyświetla komunikat informacyjny dla pętli, które są zwektoryzowana.

**/Qvec-report:2**<br/>
Wyświetla komunikat informacyjny dla pętli, które są wektoryzowana i pętli, które są nie jest zwektoryzowana, wraz z kod przyczyny.

Aby uzyskać informacji na temat kodów przyczyn i komunikaty, zobacz [komunikaty Wektoryzatora i Paralelizatora](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).

### <a name="to-set-the-qvec-report-compiler-option-in-visual-studio"></a>Aby ustawić opcję kompilatora /Qvec-report w programie Visual Studio

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, a następnie wybierz **właściwości**.

1. W **stron właściwości** dialogowego **C/C++**, wybierz opcję **wiersza polecenia**.

1. W **dodatkowe opcje** wprowadź `/Qvec-report:1` lub `/Qvec-report:2`.

### <a name="to-set-the-qvec-report-compiler-option-programmatically"></a>Aby programowo ustawić opcję kompilatora /Qvec-report

- Skorzystaj z tego przykładu kodu w <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[/Q Opcje (Operacje na niskim poziomie)](q-options-low-level-operations.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Programowanie równoległe w kodzie natywnym](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/04/12/auto-vectorizer-in-visual-studio-2012-overview/)
