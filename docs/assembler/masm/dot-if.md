---
title: .IF
ms.date: 11/05/2019
f1_keywords:
- .IF
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
ms.openlocfilehash: 83c9ff588e2fe273e24e1d0b1c16517c5eee3365
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703778"
---
# <a name="if-32-bit-masm"></a>. IF (32-bitowy MASM)

Generuje kod, który testuje `condition1` (na przykład AX > 7) i wykonuje *instrukcje* , jeśli warunek ma wartość true. (tylko 32-bitowy MASM).

## <a name="syntax"></a>Składnia

> . Jeśli condition1<br/>
> instrukcje<br/>
> [[. Condition2 ELSEIF<br/>
> Instrukcje]]<br/>
> [[. PRZEJMI<br/>
> Instrukcje]]<br/>
> .ENDIF

## <a name="remarks"></a>Uwagi

Jeśli [. W przeciwnym](../../assembler/masm/dot-else.md) razie instrukcje są wykonywane, jeśli oryginalny warunek miał wartość false. Należy zauważyć, że warunki są oceniane w czasie wykonywania.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>