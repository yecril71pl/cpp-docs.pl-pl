---
title: PROC
ms.date: 08/30/2018
f1_keywords:
- PROC
helpviewer_keywords:
- PROC directive
ms.assetid: ee5bb6b6-fa15-4d73-b0cf-e650178539a9
ms.openlocfilehash: e7931c97570c0fefcacb0123d75934867793fba4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62210537"
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