---
title: .REPEAT
ms.date: 11/05/2019
f1_keywords:
- .REPEAT
helpviewer_keywords:
- .REPEAT directive
ms.assetid: cb8ad8c6-587b-42f9-a0ad-b5316a24918c
ms.openlocfilehash: 0533397c60c83f22b10c84ec72aa6eb65a71e4c0
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703570"
---
# <a name="repeat-32-bit-masm"></a>. Powtórz (32-bitowy MASM)

Generuje kod, który powtarza wykonywanie bloku *instrukcji* do momentu, `condition` zostanie spełniony. [. UNTILCXZ](../../assembler/masm/dot-untilcxz.md), który ma wartość true, jeśli CX wynosi zero, może zostać zastąpiony przez [. DO](../../assembler/masm/dot-until.md). `condition` jest opcjonalne z **. UNTILCXZ**. (tylko 32-bitowy MASM).

## <a name="syntax"></a>Składnia

> .REPEAT<br/>
> instrukcje<br/>
> . UNTIL — warunek

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>