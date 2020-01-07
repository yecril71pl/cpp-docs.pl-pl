---
title: EXTERN (MASM)
ms.date: 12/06/2019
f1_keywords:
- extern
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: 681c4091a3c54a781bed4b01b235dfeb04f552c6
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318101"
---
# <a name="extern"></a>EXTERN

Definiuje co najmniej jedną zmienną zewnętrzną, etykiety lub symbole o nazwie *name* , której typem jest *Typ*.

## <a name="syntax"></a>Składnia

> **Extern** ⟦*Language-Type*⟧ *name* ⟦ __(__ *Altid* __)__ ⟧ __:__ *Type* ⟦ __,__ ⟦*Language-Type*⟧ *name* ⟦ __(__ *Altid* __)__ ⟧ __:__ *Type* ... ⟧

## <a name="remarks"></a>Uwagi

Argument *typu Language* jest prawidłowy tylko w 32-bitowym MASM.

*Typ* może być typem [ABS](operator-abs.md), który importuje *nazwę* jako stałą. Analogicznie jak [EXTRN](extrn.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
