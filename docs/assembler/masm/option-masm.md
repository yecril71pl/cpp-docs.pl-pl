---
title: OPTION (MASM)
ms.date: 08/30/2018
f1_keywords:
- option
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
ms.openlocfilehash: 0f90ab0115c3dde894d468bbbe60ffa0193b8336
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74395166"
---
# <a name="option-masm"></a>OPTION (MASM)

Włącza i wyłącza funkcje asemblera.

## <a name="syntax"></a>Składnia

> **Opcja** *OptionList*

## <a name="remarks"></a>Uwagi

Dostępne opcje to:

|||||
|-|-|-|-|
|**CASEMAP**|**DOTNAME**|**NODOTNAME**|**WZORCA**|
|**Noemulator**|**EPILOGU**|**EXPR16**|**EXPR32**|
|**JĘZYKOWE**|**LJMP**|**NOLJMP**|**M510**|
|**NOM510**|**No— słowo kluczowe**|**NOSIGNEXTEND**|**Przesunięcie**|
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|
|**PROC**|**PROLOGU**|**TRYBIE**|**Nie tylko do odczytu**|
|**ZAKRESIE**|**Brak zakresu**|**SEGMENT**|**SETIF2**.|

Składnia języka jest **językiem opcji:** <em>x</em>, gdzie *x* , syscall, stdcall, Pascal, Pascal lub Basic.  SYSCALL, PASCAL, Pascal i BASIC nie są obsługiwane w programie [. MODEL](../../assembler/masm/dot-model.md) płaski.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)
