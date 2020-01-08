---
title: .ALLOCSTACK
ms.date: 12/17/2019
f1_keywords:
- .ALLOCSTACK
helpviewer_keywords:
- .ALLOCSTACK directive
ms.assetid: 9801594b-7ac2-4df2-a49d-07d9dd9af99e
ms.openlocfilehash: bcc94619dfa24ab5c8b5d23a60825641290ef176
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75314188"
---
# <a name="allocstack"></a>.ALLOCSTACK

Generuje **UWOP_ALLOC_SMALL** lub **UWOP_ALLOC_LARGE** o określonym rozmiarze dla bieżącego przesunięcia w prologu.

## <a name="syntax"></a>Składnia

> **.**  *Rozmiar* ALLOCSTACK

## <a name="remarks"></a>Uwagi

MASM będzie wybierać najbardziej wydajne kodowanie dla danego rozmiaru.

**. ALLOCSTACK** umożliwia użytkownikom ml64. exe określenie sposobu odwinięcia funkcji ramki i jest dozwolony tylko w obrębie prologu, który rozciąga się od deklaracji Frame [proces](proc.md) do [. ENDPROLOG](dot-endprolog.md) . Dyrektywy te nie generują kodu; generują one tylko `.xdata` i `.pdata`. **. ALLOCSTACK** powinien być poprzedzony instrukcjami, które faktycznie implementują akcje, które mają być odwiązane. Dobrym sposobem jest Zawijanie dyrektyw unwind i kodu, które są przeznaczone do odwinięcia w makrze w celu zapewnienia zgody.

Operand *rozmiaru* musi być wielokrotnością liczby 8.

Aby uzyskać więcej informacji, zobacz [MASM for x64 (ml64. exe)](masm-for-x64-ml64-exe.md).

## <a name="sample"></a>Przykład

Poniższy przykład pokazuje, jak określić procedurę obsługi operacji unwindy/wyjątek:

```asm
; ml64 ex3.asm /link /entry:Example1  /SUBSYSTEM:Console
text SEGMENT
PUBLIC Example3
PUBLIC Example3_UW
Example3_UW PROC NEAR
   ; exception/unwind handler body

   ret 0

Example3_UW ENDP

Example3 PROC FRAME : Example3_UW

   sub rsp, 16
.allocstack 16

.endprolog

   ; function body
    add rsp, 16
   ret 0

Example3 ENDP
text ENDS
END
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
