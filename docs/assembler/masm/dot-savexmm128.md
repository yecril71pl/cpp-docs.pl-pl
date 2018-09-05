---
title: . SAVEXMM128 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .SAVEXMM128
dev_langs:
- C++
helpviewer_keywords:
- .SAVEXMM128 directive
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d44855d3449000c588f7e840753bd734af4b1af
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43689910"
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