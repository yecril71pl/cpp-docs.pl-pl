---
title: . SAVEREG | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .SAVEREG
dev_langs:
- C++
helpviewer_keywords:
- .SAVEREG directive
ms.assetid: 1dbc2ef6-a197-40e7-9e55-fddcae8cef29
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e7010664cd2e80841d9e35d8fcf72d195cecf796
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43688992"
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