---
title: .PUSHREG
ms.date: 08/30/2018
f1_keywords:
- .PUSHREG
helpviewer_keywords:
- .PUSHREG directive
ms.assetid: e0c83758-dfed-40ea-afe6-cb833c8d2d30
ms.openlocfilehash: 2190bd05667de82dada34a63f11647c653f97247
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398035"
---
# <a name="pushreg"></a>.PUSHREG

Generuje `UWOP_PUSH_NONVOL` wpis kodu unwind dla określonego numeru rejestru przy użyciu bieżącego przesunięcia w prologu.

## <a name="syntax"></a>Składnia

> . Rejestr PUSHREG

## <a name="remarks"></a>Uwagi

**. PUSHREG** umożliwia użytkownikom ml64. exe określenie, jak działa funkcja ramki, i jest dozwolona tylko w obrębie prologu, która rozciąga się od deklaracji **Frame** [proces](../../assembler/masm/proc.md) do [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) . Dyrektywy te nie generują kodu; generują one tylko `.xdata` i `.pdata`. **. PUSHREG** powinien być poprzedzony instrukcjami, które faktycznie implementują akcje, które mają być odwiązane. Dobrym sposobem jest Zawijanie dyrektyw unwind i kodu, które są przeznaczone do odwinięcia w makrze w celu zapewnienia zgody.

Aby uzyskać więcej informacji, zobacz [MASM for x64 (ml64. exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="sample"></a>Przykład

### <a name="description"></a>Opis

Poniższy przykład przedstawia sposób wypychania rejestrów nietrwałych.

### <a name="code"></a>Kod

```asm
; ml64 ex1.asm /link /entry:Example1 /SUBSYSTEM:CONSOLE
_text SEGMENT
Example1 PROC FRAME
   push r10
.pushreg r10
   push r15
.pushreg r15
   push rbx
.pushreg rbx
   push rsi
.pushreg rsi
.endprolog
   ; rest of function ...
   ret
Example1 ENDP
_text ENDS
END
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)
