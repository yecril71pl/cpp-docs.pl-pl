---
title: Pierwotne operacje Pseudo
ms.date: 11/04/2016
ms.assetid: 4def1a0e-ec28-4736-91fb-fac95fba1f36
ms.openlocfilehash: 04dfe4d59c05dfcf22d0e64063fbc4953cbcb2f8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538037"
---
# <a name="raw-pseudo-operations"></a>Pierwotne operacje Pseudo

W tym temacie wymieniono operacje pseudo.

## <a name="remarks"></a>Uwagi

|Operacja pseudo|Opis|
|----------------------|-----------------|
|PROC ramki [: ehandler]|Powoduje, że MASM, można wygenerować funkcji tabeli wpis .pdata i unwind informacje zawarte w .xdata dla funkcji w strukturze wyjątków unwind zachowanie.  Jeśli ehandler jest obecny, ten proces jest wprowadzana w .xdata jako Obsługa określonego języka.<br /><br /> Gdy atrybut ramki jest używany, należy wprowadzić znak. Dyrektywa ENDPROLOG.  Jeśli funkcja jest funkcją typu liść (zgodnie z definicją w [typy funkcji](../build/function-types.md)) atrybut ramki jest zbędne, ponieważ są w pozostałej części te pseudo operacje.|
|. PUSHREG reg|Generuje wpis UWOP_PUSH_NONVOL unwind kodu dla określonego rejestru numeru przy użyciu bieżącego przesunięcie w prologu.<br /><br /> Powinno to można używać tylko z rejestrów nieulotnej liczby całkowitej.  Wypchnięć volatile rejestrów, należy użyć. ALLOCSTACK 8, zamiast tego|
|. Przesunięcie SETFRAME reg|Wypełnienia w klatce zarejestrować pola i przesunięcie unwind informacje przy użyciu określonego rejestru i przesunięcia. Przesunięcie musi być wielokrotnością liczby 16 i mniejsza niż 240. Ta dyrektywa generuje również nazwę UWOP_SET_FPREG unwind kodu dla określonego rejestru za pomocą bieżące przesunięcie prologu.|
|. Rozmiar ALLOCSTACK|Generuje UWOP_ALLOC_SMALL lub UWOP_ALLOC_LARGE o określonym rozmiarze, aby uzyskać bieżące przesunięcie w prologu.<br /><br /> Operand rozmiar musi być wielokrotnością liczby 8.|
|. Przesunięcie SAVEREG reg|Generuje UWOP_SAVE_NONVOL lub wpis UWOP_SAVE_NONVOL_FAR unwind kodu dla określonego rejestru i przesunięcia za pomocą bieżące przesunięcie prologu. MASM wybierze najbardziej efektywny sposób kodowania.<br /><br /> Przesunięcie musi być dodatnia i wielokrotność liczby 8.  Przesunięcie jest określana względem base ramki procedury, która jest zwykle w RSP, lub, jeśli za pomocą wskaźnika ramki, wskaźnik ramki nieskalowanego.|
|. Przesunięcie SAVEXMM128 reg|Generuje UWOP_SAVE_XMM128 lub wpis UWOP_SAVE_XMM128_FAR unwind kodu dla określonego rejestru XMM i przesunięcia za pomocą bieżące przesunięcie prologu. MASM wybierze najbardziej efektywny sposób kodowania.<br /><br /> Przesunięcie musi być dodatnia i wielokrotnością liczby 16.  Przesunięcie jest określana względem base ramki procedury, która jest zwykle w RSP, lub, jeśli za pomocą wskaźnika ramki, wskaźnik ramki nieskalowanego.|
|. PUSHFRAME [kod]|Generuje wpis UWOP_PUSH_MACHFRAME unwind kodu. Jeśli określono opcjonalny kod, wpis kodu unwind otrzymuje modyfikujący 1. W przeciwnym razie modyfikator wynosi 0.|
|.ENDPROLOG|Sygnalizuje koniec deklaracje prologu.  Musi przypadać w pierwsze bajty 255 funkcji.|

Poniżej przedstawiono przykładowe prologu funkcji, z użyciem odpowiednich większości rozkazów:

```
sample PROC FRAME
   db      048h; emit a REX prefix, to enable hot-patching
push rbp
.pushreg rbp
sub rsp, 040h
.allocstack 040h
lea rbp, [rsp+020h]
.setframe rbp, 020h
movdqa [rbp], xmm7
.savexmm128 xmm7, 020h;the offset is from the base of the frame
;not the scaled offset of the frame
mov [rbp+018h], rsi
.savereg rsi, 038h
mov [rsp+010h], rdi
.savereg rdi, 010h; you can still use RSP as the base of the frame
; or any other register you choose
.endprolog

; you can modify the stack pointer outside of the prologue (similar to alloca)
; because we have a frame pointer.
; if we didn’t have a frame pointer, this would be illegal
; if we didn’t make this modification,
; there would be no need for a frame pointer

sub rsp, 060h

; we can unwind from the following AV because of the frame pointer

mov rax, 0
mov rax, [rax] ; AV!

; restore the registers that weren’t saved with a push
; this isn’t part of the official epilog, as described in section 2.5

movdqa xmm7, [rbp]
mov rsi, [rbp+018h]
mov rdi, [rbp-010h]

; Here’s the official epilog

lea rsp, [rbp-020h]
pop rbp
ret
sample ENDP
```

## <a name="see-also"></a>Zobacz też

[Pomocnicy operacji unwind dla MASM](../build/unwind-helpers-for-masm.md)