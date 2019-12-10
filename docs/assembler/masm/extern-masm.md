---
title: EXTERN (MASM)
ms.date: 12/06/2019
f1_keywords:
- extern
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: 38ea50e75f2a8e19a7a99860f691904053b6739a
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74987855"
---
# <a name="extern-masm"></a>EXTERN (MASM)

Definiuje co najmniej jedną zmienną zewnętrzną, etykiety lub symbole o nazwie *name* , której typem jest *Typ*.

## <a name="syntax"></a>Składnia

> **Extern** ⟦*Language-Type*⟧ *name* ⟦ __(__ *Altid* __)__ ⟧ __:__ *Type* ⟦ __,__ ⟦*Language-Type*⟧ *name* ⟦ __(__ *Altid* __)__ ⟧ __:__ *Type* ... ⟧

## <a name="remarks"></a>Uwagi

Argument *typu Language* jest prawidłowy tylko w 32-bitowym MASM.

*Typ* może być typem [ABS](../../assembler/masm/operator-abs.md), który importuje *nazwę* jako stałą. Analogicznie jak [EXTRN](../../assembler/masm/extrn.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)
