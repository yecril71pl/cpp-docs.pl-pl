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
ms.openlocfilehash: 417aea13518621f775cafa176ff7d74f9704d511
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62178296"
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
.model  flat
MyHandler   proto
.safeseh    MyHandler
end
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>