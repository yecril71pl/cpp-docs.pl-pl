---
title: OPTION (MASM)
ms.date: 12/17/2019
f1_keywords:
- option
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
ms.openlocfilehash: bd50ac2e051db7f02ac077054e5856524745df54
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318751"
---
# <a name="option"></a>OPTION

Włącza i wyłącza funkcje asemblera.

## <a name="syntax"></a>Składnia

> **Opcja** *OptionList*

## <a name="remarks"></a>Uwagi

Dostępne opcje to:

|||||
|-|-|-|-|
|**CASEMAP**|**DOTNAME**|**NODOTNAME**|**WZORCA**|
|**NOEMULATOR**|**EPILOGU**|**EXPR16**|**EXPR32**|
|**JĘZYKOWE**|**LJMP**|**NOLJMP**|**M510**|
|**NOM510**|**NOKEYWORD**|**NOSIGNEXTEND**|**Przesunięcie**|
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|
|**PROC**|**PROLOGU**|**TRYBIE**|**Nie tylko do odczytu**|
|**ZAKRESIE**|**NOSCOPED**|**SEGMENT**|**SETIF2**.|

Składnia języka jest **językiem opcji:** <em>x</em>, gdzie *x* , syscall, stdcall, Pascal, Pascal lub Basic.  SYSCALL, PASCAL, Pascal i BASIC nie są obsługiwane w programie [. MODEL](dot-model.md) płaski.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
