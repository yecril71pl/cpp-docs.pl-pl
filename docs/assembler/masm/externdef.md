---
title: EXTERNDEF
ms.date: 08/30/2018
f1_keywords:
- EXTERNDEF
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
ms.openlocfilehash: 23d34af470e825a8535de8cb28645a7bfb4c4d1b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619768"
---
# <a name="externdef"></a>EXTERNDEF

Określa jeden lub więcej zmiennych zewnętrznych, etykiety lub symbole o nazwie *nazwa* o typie `type`.

## <a name="syntax"></a>Składnia

> Typ: Nazwa externdef — [[langtype]] [[, [[langtype]] Nazwa: typ]]...

## <a name="remarks"></a>Uwagi

Jeśli *nazwa* jest zdefiniowany w module, jest ona traktowana jako [publicznych](../../assembler/masm/public-masm.md). Jeśli *nazwa* o której mowa w module, jest ona traktowana jako [EXTERN](../../assembler/masm/extern-masm.md). Jeśli *nazwa* jest nie odwołania, jest ignorowany. `type` Może być [ABS](../../assembler/masm/operator-abs.md), który importuje *nazwa* jako stała. Zwykle używane Dołącz pliki.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>