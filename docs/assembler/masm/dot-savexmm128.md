---
title: .SAVEXMM128
ms.date: 12/17/2019
f1_keywords:
- .SAVEXMM128
helpviewer_keywords:
- .SAVEXMM128 directive
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
ms.openlocfilehash: 6402b75c10b1400d56923116621f00b4d0908822
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318257"
---
# <a name="savexmm128"></a>.SAVEXMM128

Generuje `UWOP_SAVE_XMM128` lub `UWOP_SAVE_XMM128_FAR` wpis kodu unwind dla określonego rejestru XMM i przesunięcia przy użyciu bieżącego przesunięcia prologu. MASM będzie wybierać najbardziej wydajne kodowanie.

## <a name="syntax"></a>Składnia

> **. SAVEXMM128** *xmmreg* , *offset*

## <a name="remarks"></a>Uwagi

**. SAVEXMM128** umożliwia użytkownikom ml64. exe określenie, jak działa funkcja ramki, i jest dozwolona tylko w obrębie prologu, która rozciąga się od deklaracji Frame [proces](proc.md) do [. ENDPROLOG](dot-endprolog.md) . Dyrektywy te nie generują kodu; generują one tylko `.xdata` i `.pdata`. . SAVEXMM128 powinien być poprzedzony instrukcjami, które faktycznie implementują akcje, które mają być odwiązane. Dobrym sposobem jest Zawijanie dyrektyw unwind i kodu, które są przeznaczone do odwinięcia w makrze w celu zapewnienia zgody.

*przesunięcie* musi być wielokrotnością 16.

Aby uzyskać więcej informacji, zobacz [MASM for x64 (ml64. exe)](masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
