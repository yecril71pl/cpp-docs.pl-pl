---
title: GOTO (MASM)
ms.date: 12/16/2019
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
ms.openlocfilehash: 18f286d8634202b57dea788aa6984755a5afb197
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440792"
---
# <a name="goto"></a>GOTO

Przenosi zestaw do wiersza oznaczonego **:** _macrolabel_.

## <a name="syntax"></a>Składnia

> **Przejdź** do *macrolabel*

## <a name="remarks"></a>Uwagi

**Polecenie goto** jest dozwolone tylko wewnątrz [makra](macro.md), [dla](for-masm.md), [FORC](forc.md), [REPEAT](repeat.md)i [while](while-masm.md) . Wartość docelowa *macrolabel* musi być jedyną dyrektywą w wierszu i musi być poprzedzona znakiem dwukropka.

## <a name="see-also"></a>Zobacz też

[Dokumentacja dyrektyw](directives-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
