---
title: .SAVEXMM128
ms.date: 08/30/2018
f1_keywords:
- .SAVEXMM128
helpviewer_keywords:
- .SAVEXMM128 directive
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
ms.openlocfilehash: 08bc5ab50e15aa59e0c49992d1810c7de20f364e
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397951"
---
# <a name="savexmm128"></a>.SAVEXMM128

Generuje `UWOP_SAVE_XMM128` lub `UWOP_SAVE_XMM128_FAR` wpis kodu unwind dla określonego rejestru XMM i przesunięcia przy użyciu bieżącego przesunięcia prologu. MASM będzie wybierać najbardziej wydajne kodowanie.

## <a name="syntax"></a>Składnia

> **. SAVEXMM128** *xmmreg* , *offset*

## <a name="remarks"></a>Uwagi

**. SAVEXMM128** umożliwia użytkownikom ml64. exe określenie, jak działa funkcja ramki, i jest dozwolona tylko w obrębie prologu, która rozciąga się od deklaracji Frame [proces](../../assembler/masm/proc.md) do [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) . Dyrektywy te nie generują kodu; generują one tylko `.xdata` i `.pdata`. . SAVEXMM128 powinien być poprzedzony instrukcjami, które faktycznie implementują akcje, które mają być odwiązane. Dobrym sposobem jest Zawijanie dyrektyw unwind i kodu, które są przeznaczone do odwinięcia w makrze w celu zapewnienia zgody.

*przesunięcie* musi być wielokrotnością 16.

Aby uzyskać więcej informacji, zobacz [MASM for x64 (ml64. exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)
