---
title: .IF
ms.date: 11/05/2019
f1_keywords:
- .IF
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
ms.openlocfilehash: e8213052dce8d84d62f90d4bc2653435c2b31434
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398226"
---
# <a name="if-32-bit-masm"></a>. IF (32-bitowy MASM)

Generuje kod, który testuje *condition1* (na przykład AX > 7) i wykonuje *instrukcje* , jeśli warunek ma wartość true. (tylko 32-bitowy MASM).

## <a name="syntax"></a>Składnia

> **. Jeśli** *condition1*\
> *instrukcje*\
> ⟦ **.\ ELSEIF** *condition2*
> *instrukcje*⟧ \
> ⟦ **. ELSE**\
> *instrukcje*⟧ \
> **.ENDIF**

## <a name="remarks"></a>Uwagi

Jeśli [. W przeciwnym](../../assembler/masm/dot-else.md) razie instrukcje są wykonywane, jeśli oryginalny warunek miał wartość false. Należy zauważyć, że warunki są oceniane w czasie wykonywania.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)
