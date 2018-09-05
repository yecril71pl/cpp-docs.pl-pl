---
title: EXTERNDEF — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- EXTERNDEF
dev_langs:
- C++
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d5c3d42cabb88c38ce1d98da24cd2cb4ddec8d5b
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43683664"
---
# <a name="externdef"></a>EXTERNDEF

Określa jeden lub więcej zmiennych zewnętrznych, etykiety lub symbole o nazwie *nazwa* o typie `type`.

## <a name="syntax"></a>Składnia

> Typ: Nazwa externdef — [[langtype]] [[, [[langtype]] Nazwa: typ]]...

## <a name="remarks"></a>Uwagi

Jeśli *nazwa* jest zdefiniowany w module, jest ona traktowana jako [publicznych](../../assembler/masm/public-masm.md). Jeśli *nazwa* o której mowa w module, jest ona traktowana jako [EXTERN](../../assembler/masm/extern-masm.md). Jeśli *nazwa* jest nie odwołania, jest ignorowany. `type` Może być [ABS](../../assembler/masm/operator-abs.md), który importuje *nazwa* jako stała. Zwykle używane Dołącz pliki.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>