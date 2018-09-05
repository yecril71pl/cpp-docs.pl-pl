---
title: . SETFRAME | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .SETFRAME
dev_langs:
- C++
helpviewer_keywords:
- .SETFRAME directive
ms.assetid: eaa9b5ed-4daa-4f1e-bdb6-100758007ab3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 956a49e40c38310819d66e89fa6bf4492443a29c
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43691292"
---
# <a name="setframe"></a>.SETFRAME

Wypełnienia w klatce zarejestrować pola i przesunięcie w informacje unwind przy użyciu określonego rejestru (`reg`) i przesunięcia (`offset`). Przesunięcie musi być wielokrotnością liczby 16 i mniejsza niż 240. Ta dyrektywa generuje również `UWOP_SET_FPREG` unwind wejścia kodu dla określonego zarejestrować się przy użyciu bieżące przesunięcie prologu.

## <a name="syntax"></a>Składnia

> . Przesunięcie SETFRAME reg

## <a name="remarks"></a>Uwagi

. SETFRAME umożliwia użytkownikom ml64.exe określające, jak funkcja ramki rozwija i jest dozwolone tylko w prologu, który rozciąga się od [PROC](../../assembler/masm/proc.md) deklaracji ramki [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) dyrektywy. Te dyrektywy nie generują kodu. tylko generują `.xdata` i `.pdata`. . SETFRAME powinien być poprzedzony instrukcji, które faktycznie wykonania akcji, które mają być rozwinięty. Jest dobrą praktyką jest opakowywanie dyrektywy unwind i kodu, które są przeznaczone do rozwinięcie makra do zapewnienia umowy.

Aby uzyskać więcej informacji, zobacz [MASM x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="sample"></a>Przykład

### <a name="description"></a>Opis

Poniższy przykład pokazuje, jak za pomocą wskaźnika ramki:

### <a name="code"></a>Kod

```asm
; ml64 frmex2.asm /link /entry:frmex2 /SUBSYSTEM:CONSOLE
_text SEGMENT
frmex2 PROC FRAME
   push rbp
.pushreg rbp
   sub rsp, 010h
.allocstack 010h
   mov rbp, rsp
.setframe rbp, 0
.endprolog
   ; modify the stack pointer outside of the prologue (similar to alloca)
   sub rsp, 060h

   ; we can unwind from the following AV because of the frame pointer
   mov rax, 0
   mov rax, [rax] ; AV!

   add rsp, 060h
   add rsp, 010h
   pop rbp
   ret
frmex2 ENDP
_text ENDS
END
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>