---
title: Makra MASM | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 21410432-72fc-4795-bc93-e78123f9f14f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 403220306a2585b1506a990664eaa2ec8f2ac1a3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="masm-macros"></a>Makra MASM
W celu uproszczenia stosowania [pierwotne operacje Pseudo](../build/raw-pseudo-operations.md), istnieją zestaw makra zdefiniowane w ksamd64.inc, która może służyć do tworzenia typowych procedury prologues i epilogues.  
  
## <a name="remarks"></a>Uwagi  
  
|Macro|Opis|  
|-----------|-----------------|  
|alloc_stack(n)|Przydziela ramka stosu n bajtów (przy użyciu źródło sub n) i emituje unwind odpowiednie informacje (.allocstack — n)|  
|reg save_reg, lokalizacja|Zapisuje reg nieulotnej rejestru na stosie w loc przesunięcia źródło i emituje unwind odpowiednie informacje. (reg .savereg — lokalizacja)|  
|push_reg reg|Wypchnięcia reg nieulotnej rejestru na stosie i emituje unwind odpowiednie informacje. (.pushreg — reg)|  
|rex_push_reg reg|Zapisz nieulotnej rejestru na stosie wypychania 2 byte, a emituje unwind odpowiednie informacje (.pushreg — reg) ta powinna być używana, jeśli wypychania jest pierwsza instrukcja w funkcji w celu zapewnienia hot-patchable funkcji.|  
|reg save_xmm128, lokalizacja|Zapisuje nieulotnej, zarejestruj XMM reg na stosie w loc przesunięcia źródło i emituje odpowiednie unwind informacji (reg .savexmm128 —, lokalizacja)|  
|Przesunięcie set_frame reg|Ustawia reg rejestru ramki do można źródło + przesunięcie (przy użyciu mov lub linie wio) i emituje odpowiednie unwind informacji (.set_frame reg, przesunięcie)|  
|push_eflags|Wypchnięcia eflags z instrukcji pushfq i emituje unwind odpowiednie informacje (.alloc_stack 8)|  
  
 Oto przykładowe prologu funkcji z właściwego użycie makra:  
  
```  
SkFrame struct   
Fill    dq ?; fill to 8 mod 16   
SavedRdi dq ?; saved register RDI   
SavedRsi dq ?; saved register RSI   
SkFrame ends  
  
sampleFrame struct  
Filldq?; fill to 8 mod 16  
SavedRdidq?; Saved Register RDI   
SavedRsi  dq?; Saved Register RSI  
sampleFrame ends  
  
sample2 PROC FRAME  
alloc_stack(sizeof sampleFrame)  
save_reg rdi, sampleFrame.SavedRdi  
save_reg rsi, sampleFrame.SavedRsi  
.end_prolog  
  
; function body  
  
mov rsi, sampleFrame.SavedRsi[rsp]  
mov rdi, sampleFrame.SavedRdi[rsp]  
  
; Here’s the official epilog  
  
add rsp, (sizeof sampleFrame)  
ret  
sample2 ENDP  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Pomocnicy operacji unwind dla MASM](../build/unwind-helpers-for-masm.md)