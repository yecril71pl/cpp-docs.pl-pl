---
title: .IF
ms.date: 08/30/2018
f1_keywords:
- .IF
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
ms.openlocfilehash: cf9c594d843c937dd2191bee2a7cebadbc615c82
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62185270"
---
# <a name="if"></a>.IF

Generuje kod, który umożliwia sprawdzenie `condition1` (na przykład AX > 7) i wykonuje *instrukcji* Jeśli ten warunek jest prawdziwy.

## <a name="syntax"></a>Składnia

> . Jeśli condition1<br/>
> instrukcje<br/>
> [[. ELSEIF condition2<br/>
> instrukcje]]<br/>
> [[.ELSE<br/>
> instrukcje]]<br/>
> .ENDIF

## <a name="remarks"></a>Uwagi

Jeśli [. ELSE](../../assembler/masm/dot-else.md) obserwowanych jego instrukcje są wykonywane, jeśli oryginalnego warunku był FAŁSZ. Należy pamiętać, że warunki są oceniane w czasie wykonywania.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>