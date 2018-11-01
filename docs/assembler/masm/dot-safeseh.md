---
title: .SAFESEH
ms.date: 08/30/2018
f1_keywords:
- .SAFESEH
helpviewer_keywords:
- registering functions as exception handlers
- SAFESEH directive
- .SAFESEH directive
ms.assetid: 6eaac8c4-c46f-47ae-8a66-f5cfeb267e43
ms.openlocfilehash: adfb9106095de3d15bafb67172b001d0f4597418
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649855"
---
# <a name="safeseh"></a>.SAFESEH

Rejestruje funkcję jako program obsługi wyjątków strukturalnych.

## <a name="syntax"></a>Składnia

> . Identyfikator SAFESEH

## <a name="remarks"></a>Uwagi

*Identyfikator* musi być Identyfikatorem dla zdefiniowanej lokalnie [PROC](../../assembler/masm/proc.md) lub [extrn —](../../assembler/masm/extrn.md) obrady A [etykiety](../../assembler/masm/label-masm.md) jest niedozwolone. . SAFESEH — dyrektywa wymaga [opcja/SAFESEH](../../assembler/masm/ml-and-ml64-command-line-reference.md) ml.exe opcji wiersza polecenia.

Aby uzyskać więcej informacji na temat obsługi wyjątków strukturalnych, zobacz [opcja/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md).

Na przykład aby zarejestrować program obsługi wyjątków bezpiecznych, Utwórz nowy plik MASM (jak pokazano poniżej), możesz korzystać z opcja/SAFESEH i dodać go do powiązane obiekty.

```asm
.386
.model  flat
MyHandler   proto
.safeseh    MyHandler
end
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>