---
title: EXTERN (MASM)
ms.date: 08/30/2018
f1_keywords:
- extern
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: fc66338d90b54ecb12ef3ab1aa56214fb445cb13
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397567"
---
# <a name="extern-masm"></a>EXTERN (MASM)

Definiuje co najmniej jedną zmienną zewnętrzną, etykiety lub symbole o nazwie *name* , której typem jest *Typ*.

## <a name="syntax"></a>Składnia

> **Extern** ⟦*Language-Type*⟧ *name* ⟦ __(__ *Altid* __)__ ⟧ __:__ *Type* ⟦ __,__ ⟦*Language-Type*⟧ *name* ⟦ __(__ *Altid* __)__ ⟧ __:__ *Type* ... ⟧

## <a name="remarks"></a>Uwagi

*Typ* może być typem [ABS](../../assembler/masm/operator-abs.md), który importuje *nazwę* jako stałą. Analogicznie jak [EXTRN](../../assembler/masm/extrn.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)
