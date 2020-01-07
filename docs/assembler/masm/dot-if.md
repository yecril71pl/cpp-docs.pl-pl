---
title: .IF
ms.date: 11/05/2019
f1_keywords:
- .IF
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
ms.openlocfilehash: 6992ec8b151a83b3f9fa920997845c20caf0476d
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317750"
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

Jeśli [. W przeciwnym](dot-else.md) razie instrukcje są wykonywane, jeśli oryginalny warunek miał wartość false. Należy zauważyć, że warunki są oceniane w czasie wykonywania.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
