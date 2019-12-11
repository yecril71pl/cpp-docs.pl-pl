---
title: EXTERNDEF
ms.date: 12/06/2019
f1_keywords:
- EXTERNDEF
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
ms.openlocfilehash: e757781151bd1bb57940e5c54f7333a5daa93c74
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74987899"
---
# <a name="externdef"></a>EXTERNDEF

Definiuje co najmniej jedną zmienną zewnętrzną, etykiety lub symbole o nazwie *name* , której typem jest *Typ*.

## <a name="syntax"></a>Składnia

> **EXTERNDEF** ⟦*Language-Type*⟧ __:__ *Type* ⟦ __,__ ⟦*Language-Type*⟧ *name* __:__ *Type* ... ⟧

## <a name="remarks"></a>Uwagi

Argument *typu Language* jest prawidłowy tylko w 32-bitowym MASM.

Jeśli *Nazwa* jest zdefiniowana w module, jest traktowana jako [publiczna](../../assembler/masm/public-masm.md). Jeśli *Nazwa* jest przywoływana w module, jest traktowana jako [extern](../../assembler/masm/extern-masm.md). Jeśli *Nazwa* nie jest przywoływana, zostanie zignorowana. *Typ* może być typem [ABS](../../assembler/masm/operator-abs.md), który importuje *nazwę* jako stałą. Zwykle używane w plikach include.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)
