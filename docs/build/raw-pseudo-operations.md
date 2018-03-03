---
title: Pierwotne operacje Pseudo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 4def1a0e-ec28-4736-91fb-fac95fba1f36
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 52ce7fb4455f87001bcfe87e1368ed0c09cda6b0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="raw-pseudo-operations"></a>Pierwotne operacje Pseudo
W tym temacie wymieniono operacje pseudo.  
  
## <a name="remarks"></a>Uwagi  
  
|Operacja pseudo|Opis|  
|----------------------|-----------------|  
|PROC ramki [: ehandler]|Przyczyny MASM do generowania funkcji tabeli wpisu w polu .pdata i unwind informacji w .xdata dla funkcji przez strukturę zachowanie unwind obsługi wyjątków.  Jeśli ehandler jest obecny, ten proces jest wprowadzana w .xdata jako Obsługa określonego języka.<br /><br /> W przypadku atrybutu ramki musi następować przez. Dyrektywa ENDPROLOG.  Jeśli funkcja jest funkcją typu liść (zgodnie z definicją w [typy funkcji](../build/function-types.md)) atrybut RAMEK nie jest konieczne, są w pozostałej części te pseudo operacje.|  
|. PUSHREG reg|Generuje wpis UWOP_PUSH_NONVOL unwind kodu dla numeru rejestru określony przy użyciu bieżącego przesunięcie w prologu.<br /><br /> To należy używać tylko z rejestrów nieulotnej liczby całkowitej.  Wypchnięcia volatile rejestrów, można użyć. ALLOCSTACK 8, zamiast niego|  
|. Przesunięcie SETFRAME reg|Wypełnienia ramki zarejestrować pola i przesunięcie w informacjach dotyczących unwind przy użyciu określonego rejestru i przesunięcie. Przesunięcie musi być wielokrotnością 16 i mniejsza niż 240. Ta dyrektywa również generuje wpis UWOP_SET_FPREG unwind kod dla określonego rejestru przy użyciu bieżącego przesunięcie prologu.|  
|. Rozmiar ALLOCSTACK|Generuje UWOP_ALLOC_SMALL lub UWOP_ALLOC_LARGE o określonym rozmiarze bieżącego przesunięcia w prologu.<br /><br /> Operand rozmiar musi być wielokrotnością liczby 8.|  
|. Przesunięcie SAVEREG reg|Generuje UWOP_SAVE_NONVOL lub wpis UWOP_SAVE_NONVOL_FAR unwind kod dla określonego rejestru i przesunięcie przy użyciu bieżącego przesunięcie prologu. MASM wybierze najbardziej efektywne kodowanie.<br /><br /> Przesunięcie musi być dodatnia i wielokrotnością liczby 8.  Przesunięcie jest określana względem base ramki procedury, która jest zazwyczaj źródło, lub, jeśli przy użyciu wskaźnika ramki, wskaźnika ramki nieskalowanego.|  
|. Przesunięcie SAVEXMM128 reg|Generuje UWOP_SAVE_XMM128 lub wpis UWOP_SAVE_XMM128_FAR unwind kod dla określonego rejestru XMM i przesunięcie przy użyciu bieżącego przesunięcie prologu. MASM wybierze najbardziej efektywne kodowanie.<br /><br /> Przesunięcie musi być dodatnia i wielokrotnością 16.  Przesunięcie jest określana względem base ramki procedury, która jest zazwyczaj źródło, lub, jeśli przy użyciu wskaźnika ramki, wskaźnika ramki nieskalowanego.|  
|. PUSHFRAME [kod]|Generuje wpis UWOP_PUSH_MACHFRAME unwind kodu. Jeśli określono opcjonalny kodu, wpis kodu unwind otrzymuje modyfikator 1. W przeciwnym razie modyfikator to 0.|  
|.ENDPROLOG|Sygnalizuje koniec deklaracje prologu.  Musi występować w pierwszych bajtów 255 funkcji.|  
  
 Oto przykładowe prologu funkcji z użyciem prawidłowego większości opcodes:  
  
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