---
title: PRZEJDŹ DO (MASM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- goto
dev_langs:
- C++
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b0be678e2d39389cbc551c386c1890f799124b5b
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43691225"
---
# <a name="goto-masm"></a>GOTO (MASM)

Przenosi zaznaczony wiersz zestawu **:**_macrolabel_.

## <a name="syntax"></a>Składnia

> **Przejdź do** *macrolabel*

## <a name="remarks"></a>Uwagi

**Przejdź do** jest dozwolona tylko wewnątrz [— makro](macro.md), [dla](for-masm.md), [FORC](forc.md), [Powtórz](repeat.md), i [podczas](while-masm.md)bloków. *Macrolabel* docelowy musi być jedynym dyrektywy w wierszu i musi być poprzedzony przez wiodących średnikami.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>
