---
title: PROC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- PROC
dev_langs:
- C++
helpviewer_keywords:
- PROC directive
ms.assetid: ee5bb6b6-fa15-4d73-b0cf-e650178539a9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ee26e181f0f40126c86a36889c43405f0b40f5e
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680849"
---
# <a name="proc"></a>PROC

Oznacza początek i koniec bloku procedury, nazywane *etykiety*. Instrukcje w bloku mogą zostać wywołany z **WYWOŁANIA** instrukcji lub [INVOKE](../../assembler/masm/invoke.md) dyrektywy.

## <a name="syntax"></a>Składnia

> *Etykieta* PROC [[*odległość*]] [[*langtype*]] [[*widoczność*]] [[\<*prologuearg*>]] [[ UŻYWA *reglist*]] [[, *parametru* [[:*tag*]]]...<br/>
> [[Ramki [[:*ehandler adres*]]]]<br/>
> *Instrukcje*<br/>
> *Etykieta* endp —

## <a name="remarks"></a>Uwagi

[[Ramki [[:*ehandler adres*]]]] jest prawidłowa tylko z ml64.exe i powoduje, że MASM generowanie wpisu tabeli funkcji w .pdata i unwind informacje zawarte w .xdata dla funkcji w strukturze wyjątków unwind zachowanie.

Gdy **ramki** atrybut jest używany, należy wprowadzić znak [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) dyrektywy.

Zobacz [MASM x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md) Aby uzyskać więcej informacji na temat korzystania z ml64.exe.

## <a name="example"></a>Przykład

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

Powyższy kod będzie emitować w poniższej tabeli funkcji i operacji unwind informacji:

```Output
FileHeader->Machine 34404
Dumping Unwind Information for file ex2.exe

.pdata entry 1 0x00001000 0x00001023

  Unwind data: 0x00002000

    Unwind version: 1
    Unwind Flags: None
    Size of prologue: 0x08
    Count of codes: 3
    Frame register: rbp
    Frame offset: 0x0
    Unwind codes:

      Code offset: 0x08, SET_FPREG, register=rbp, offset=0x00
      Code offset: 0x05, ALLOC_SMALL, size=0x10
      Code offset: 0x01, PUSH_NONVOL, register=rbp
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>