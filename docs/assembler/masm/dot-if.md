---
title: . JEŚLI | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .IF
dev_langs:
- C++
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f7bd5ba5821b4dcfb2d088e31816f50540445018
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43691547"
---
# <a name="if"></a>.IF

Generuje kod, który umożliwia sprawdzenie `condition1` (na przykład AX > 7) i wykonuje *instrukcji* Jeśli ten warunek jest prawdziwy.

## <a name="syntax"></a>Składnia

> . Jeśli condition1<br/>
> instrukcje<br/>
> [[. ELSEIF condition2<br/>
> instrukcje]]<br/>
> [[. ELSE<br/>
> instrukcje]]<br/>
> .ENDIF

## <a name="remarks"></a>Uwagi

Jeśli [. ELSE](../../assembler/masm/dot-else.md) obserwowanych jego instrukcje są wykonywane, jeśli oryginalnego warunku był FAŁSZ. Należy pamiętać, że warunki są oceniane w czasie wykonywania.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>