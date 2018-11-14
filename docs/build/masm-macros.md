---
title: Makra MASM
ms.date: 11/04/2016
ms.assetid: 21410432-72fc-4795-bc93-e78123f9f14f
ms.openlocfilehash: 8a00852a3a763aae5fda34d7e0fde664997a0bdb
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328828"
---
# <a name="masm-macros"></a>Makra MASM

Aby uprościć używanie [pierwotne operacje Pseudo](../build/raw-pseudo-operations.md), zestaw makra, zdefiniowane w ksamd64.inc, która może służyć do tworzenia Typowa procedura prologues i epilogues.

## <a name="remarks"></a>Uwagi

|Macro|Opis|
|-----------|-----------------|
|alloc_stack(n)|Przydziela ramkę stosu w bajtach n (przy użyciu sub rsp, n) i emituje odpowiednie unwind informacji (.allocstack — n)|
|reg save_reg, lokalizacja|Zapisuje reg nieulotnej rejestru na stosie przy przesunięciu loc RSP i emituje odpowiednie informacje o operacji unwind. (reg .savereg — lokalizacja)|
|push_reg reg|Wypycha reg nieulotnej rejestru na stosie i emituje odpowiednie informacje o operacji unwind. (.pushreg — reg)|
|rex_push_reg reg|Zapisz nieulotnej rejestru na stosie, za pomocą wypychania 2 bajtów, a następnie emituje odpowiednie informacje (.pushreg — reg), ta powinna być używana w przypadku wypychania pierwsza instrukcja w funkcji do upewnij się, że funkcja hot-patchable operacji unwind.|
|reg save_xmm128, lokalizacja|Zapisuje nieulotnej, zarejestruj XMM reg na stosie przy przesunięciu loc RSP i emituje odpowiednie unwind informacji (reg .savexmm128 —, lokalizacja)|
|Przesunięcie set_frame reg|Ustawia reg rejestru ramki do być RSP + przesunięcie (przy użyciu mov lub linie wio) i emituje odpowiednie unwind informacji (.set_frame reg, przesunięcie)|
|push_eflags|Wypycha eflags za pomocą instrukcji pushfq i emituje odpowiednie unwind informacji (.alloc_stack 8)|

Poniżej przedstawiono przykładowe prologu funkcji, z użyciem odpowiednich makr:

```asm
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