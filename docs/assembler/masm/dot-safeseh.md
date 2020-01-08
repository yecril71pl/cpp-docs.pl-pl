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
ms.openlocfilehash: 5953ad6bdf1d9d1b0070ce83dd1d764799b7440a
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317568"
---
# <a name="safeseh-32-bit-masm"></a>. SAFESEH (32-bitowy MASM)

Rejestruje funkcję jako program obsługi wyjątków strukturalnych. (tylko 32-bitowy MASM).

## <a name="syntax"></a>Składnia

> **.**  *Identyfikator* SAFESEH

## <a name="remarks"></a>Uwagi

*Identyfikator* musi być identyfikatorem [zdefiniowanego](proc.md) lokalnie procedury lub [EXTRN](extrn.md) . [Etykieta](label-masm.md) jest niedozwolona. Polu. Dyrektywa SAFESEH wymaga opcji wiersza polecenia [/SAFESEH](ml-and-ml64-command-line-reference.md) ml. exe.

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

[Dokumentacja dyrektyw](directives-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
