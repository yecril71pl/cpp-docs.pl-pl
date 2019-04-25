---
title: EXTERN (MASM)
ms.date: 08/30/2018
f1_keywords:
- extern
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: 30d1b3ae7c6676aeb97b91c7627da859525b9ce1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62203618"
---
# <a name="extern-masm"></a>EXTERN (MASM)

Określa jeden lub więcej zmiennych zewnętrznych, etykiety lub symbole o nazwie *nazwa* o typie *typu*.

## <a name="syntax"></a>Składnia

> EXTERN [[*langtype*]] *nazwa* [[(*altid*)]]: *typu* [[, [[*langtype*]]  *Nazwa* [[(*altid*)]]: *typu*]]...

## <a name="remarks"></a>Uwagi

*Typu* może być [ABS](../../assembler/masm/operator-abs.md), który importuje *nazwa* jako stała. Taki sam jak [extrn —](../../assembler/masm/extrn.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>