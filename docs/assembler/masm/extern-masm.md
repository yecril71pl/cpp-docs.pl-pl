---
title: EXTERN (MASM)
ms.date: 08/30/2018
f1_keywords:
- extern
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: 30d1b3ae7c6676aeb97b91c7627da859525b9ce1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497360"
---
# <a name="extern-masm"></a>EXTERN (MASM)

Określa jeden lub więcej zmiennych zewnętrznych, etykiety lub symbole o nazwie *nazwa* o typie *typu*.

## <a name="syntax"></a>Składnia

> EXTERN [[*langtype*]] *nazwa* [[(*altid*)]]: *typu* [[, [[*langtype*]]  *Nazwa* [[(*altid*)]]: *typu*]]...

## <a name="remarks"></a>Uwagi

*Typu* może być [ABS](../../assembler/masm/operator-abs.md), który importuje *nazwa* jako stała. Taki sam jak [extrn —](../../assembler/masm/extrn.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>