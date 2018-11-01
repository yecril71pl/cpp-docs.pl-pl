---
title: .SAVEXMM128
ms.date: 08/30/2018
f1_keywords:
- .SAVEXMM128
helpviewer_keywords:
- .SAVEXMM128 directive
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
ms.openlocfilehash: c29ec47170c5e0f46f02d53f23ab477a79bbdc32
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507906"
---
# <a name="savexmm128"></a>.SAVEXMM128

Generuje albo `UWOP_SAVE_XMM128` lub `UWOP_SAVE_XMM128_FAR` unwind wejścia kodu dla określonego rejestru XMM i przesunięcie, przy użyciu bieżące przesunięcie prologu. MASM wybierze najbardziej efektywny sposób kodowania.

## <a name="syntax"></a>Składnia

> .savexmm128 — xmmreg, przesunięcie

## <a name="remarks"></a>Uwagi

. SAVEXMM128 umożliwia użytkownikom ml64.exe określające, jak funkcja ramki rozwija i jest dozwolone tylko w prologu, który rozciąga się od [PROC](../../assembler/masm/proc.md) deklaracji ramki [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) dyrektywy. Te dyrektywy nie generują kodu. tylko generują `.xdata` i `.pdata`. . SAVEXMM128 powinien być poprzedzony instrukcji, które faktycznie wykonania akcji, które mają być rozwinięty. Jest dobrą praktyką jest opakowywanie dyrektywy unwind i kodu, które są przeznaczone do rozwinięcie makra do zapewnienia umowy.

*Przesunięcie* musi być wielokrotnością liczby 16.

Aby uzyskać więcej informacji, zobacz [MASM x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>