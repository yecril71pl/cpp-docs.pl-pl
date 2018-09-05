---
title: . SAFESEH | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .SAFESEH
dev_langs:
- C++
helpviewer_keywords:
- registering functions as exception handlers
- SAFESEH directive
- .SAFESEH directive
ms.assetid: 6eaac8c4-c46f-47ae-8a66-f5cfeb267e43
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d10f3c751fe05c118203bb5eeff6c5cba6ec1c8b
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693171"
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