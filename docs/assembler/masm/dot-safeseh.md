---
title: .SAFESEH
ms.date: 11/05/2019
f1_keywords:
- .SAFESEH
helpviewer_keywords:
- registering functions as exception handlers
- SAFESEH directive
- .SAFESEH directive
ms.assetid: 6eaac8c4-c46f-47ae-8a66-f5cfeb267e43
ms.openlocfilehash: 4577bd5d76949dfb777a359c80d91814f1c45fe2
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703946"
---
# <a name="safeseh-32-bit-masm"></a>. SAFESEH (32-bitowy MASM)

Rejestruje funkcję jako program obsługi wyjątków strukturalnych. (tylko 32-bitowy MASM).

## <a name="syntax"></a>Składnia

> . Identyfikator SAFESEH

## <a name="remarks"></a>Uwagi

*Identyfikator* musi być identyfikatorem [zdefiniowanego](../../assembler/masm/proc.md) lokalnie procedury lub [EXTRN](../../assembler/masm/extrn.md) . [Etykieta](../../assembler/masm/label-masm.md) jest niedozwolona. Polu. Dyrektywa SAFESEH wymaga opcji wiersza polecenia [/SAFESEH](../../assembler/masm/ml-and-ml64-command-line-reference.md) ml. exe.

Aby uzyskać więcej informacji na temat obsługi wyjątków strukturalnych, zobacz [/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md).

Na przykład, aby zarejestrować bezpieczną procedurę obsługi wyjątków, Utwórz nowy plik MASM (w następujący sposób), złóż z/SAFESEH i dodaj go do połączonych obiektów.

```asm
.386
.model  flat
MyHandler   proto
.safeseh    MyHandler
end
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>