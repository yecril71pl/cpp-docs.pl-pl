---
title: .SAVEREG
ms.date: 08/30/2018
f1_keywords:
- .SAVEREG
helpviewer_keywords:
- .SAVEREG directive
ms.assetid: 1dbc2ef6-a197-40e7-9e55-fddcae8cef29
ms.openlocfilehash: cac7aa7f2bdbf6b60831d2beb062f86559ec0358
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472826"
---
# <a name="savereg"></a>.SAVEREG

Generuje albo `UWOP_SAVE_NONVOL` lub `UWOP_SAVE_NONVOL_FAR` unwind wejścia kodu dla określonego rejestru (`reg`) i przesunięcia (`offset`) za pomocą bieżące przesunięcie prologu. MASM wybierze najbardziej efektywny sposób kodowania.

## <a name="syntax"></a>Składnia

> . Przesunięcie SAVEREG reg

## <a name="remarks"></a>Uwagi

. SAVEREG umożliwia użytkownikom ml64.exe określić, jak funkcja ramki rozwija i jest dozwolone tylko w prologu, który rozciąga się od [PROC](../../assembler/masm/proc.md) deklaracji ramki [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) dyrektywy. Te dyrektywy nie generują kodu. tylko generują `.xdata` i `.pdata`. . SAVEREG powinien być poprzedzony instrukcji, które faktycznie wykonania akcji, które mają być rozwinięty. Jest dobrą praktyką jest opakowywanie dyrektywy unwind i kodu, które są przeznaczone do rozwinięcie makra do zapewnienia umowy.

Aby uzyskać więcej informacji, zobacz [MASM x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>