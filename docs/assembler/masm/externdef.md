---
title: EXTERNDEF
ms.date: 08/30/2018
f1_keywords:
- EXTERNDEF
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
ms.openlocfilehash: 469b49832c171ee78336a0c457f0d269acd3b59d
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397540"
---
# <a name="externdef"></a>EXTERNDEF

Definiuje co najmniej jedną zmienną zewnętrzną, etykiety lub symbole o nazwie *name* , której typem jest *Typ*.

## <a name="syntax"></a>Składnia

> **EXTERNDEF** ⟦*Language-Type*⟧ __:__ *Type* ⟦ __,__ ⟦*Language-Type*⟧ *name* __:__ *Type* ... ⟧

## <a name="remarks"></a>Uwagi

Jeśli *Nazwa* jest zdefiniowana w module, jest traktowana jako [publiczna](../../assembler/masm/public-masm.md). Jeśli *Nazwa* jest przywoływana w module, jest traktowana jako [extern](../../assembler/masm/extern-masm.md). Jeśli *Nazwa* nie jest przywoływana, zostanie zignorowana. *Typ* może być typem [ABS](../../assembler/masm/operator-abs.md), który importuje *nazwę* jako stałą. Zwykle używane w plikach include.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)
