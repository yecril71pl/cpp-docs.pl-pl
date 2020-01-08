---
title: GOTO (MASM)
ms.date: 12/16/2019
f1_keywords:
- goto
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
ms.openlocfilehash: f198658f9a4b85e0b5ec9b7a0c122241e57286f6
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317282"
---
# <a name="goto"></a>GOTO

Przenosi zestaw do wiersza oznaczonego **:** _macrolabel_.

## <a name="syntax"></a>Składnia

> **Przejdź** do *macrolabel*

## <a name="remarks"></a>Uwagi

**Polecenie goto** jest dozwolone tylko wewnątrz [makra](macro.md), [dla](for-masm.md), [FORC](forc.md), [REPEAT](repeat.md)i [while](while-masm.md) . Wartość docelowa *macrolabel* musi być jedyną dyrektywą w wierszu i musi być poprzedzona znakiem dwukropka.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
