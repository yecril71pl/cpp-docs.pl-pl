---
title: EXTERN (MASM)
ms.date: 12/06/2019
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: 2674f358fe22f74c5272d90a0d8cbff234ddcd11
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440888"
---
# <a name="extern"></a>EXTERN

Definiuje co najmniej jedną zmienną zewnętrzną, etykiety lub symbole o nazwie *name* , której typem jest *Typ*.

## <a name="syntax"></a>Składnia

> **Extern** ⟦*Language-Type*⟧ *name* ⟦ __(__ *Altid* __)__ ⟧ __:__ *Type* ⟦ __,__ ⟦*Language-Type*⟧ *name* ⟦ __(__ *Altid* __)__ ⟧ __:__ *Type* ... ⟧

## <a name="remarks"></a>Uwagi

Argument *typu Language* jest prawidłowy tylko w 32-bitowym MASM.

*Typ* może być typem [ABS](operator-abs.md), który importuje *nazwę* jako stałą. Analogicznie jak [EXTRN](extrn.md).

## <a name="see-also"></a>Zobacz też

[Dokumentacja dyrektyw](directives-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
