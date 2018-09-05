---
title: EXTERN (MASM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- extern
dev_langs:
- C++
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a9008e8c1153c0a9b06530b14e661436f7e62a9
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693673"
---
# <a name="extern-masm"></a>EXTERN (MASM)

Określa jeden lub więcej zmiennych zewnętrznych, etykiety lub symbole o nazwie *nazwa* o typie *typu*.

## <a name="syntax"></a>Składnia

> EXTERN [[*langtype*]] *nazwa* [[(*altid*)]]: *typu* [[, [[*langtype*]]  *Nazwa* [[(*altid*)]]: *typu*]]...

## <a name="remarks"></a>Uwagi

*Typu* może być [ABS](../../assembler/masm/operator-abs.md), który importuje *nazwa* jako stała. Taki sam jak [extrn —](../../assembler/masm/extrn.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>