---
title: .SAVEREG
ms.date: 12/16/2019
f1_keywords:
- .SAVEREG
helpviewer_keywords:
- .SAVEREG directive
ms.assetid: 1dbc2ef6-a197-40e7-9e55-fddcae8cef29
ms.openlocfilehash: 18cb6e563084e8c5357bec2a8052a2b38fcdffee
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317555"
---
# <a name="savereg"></a>.SAVEREG

Generuje `UWOP_SAVE_NONVOL` lub `UWOP_SAVE_NONVOL_FAR` wpis kodu unwind dla określonego rejestru (*reg*) i przesunięcia (*przesunięcie*) przy użyciu bieżącego przesunięcia prologu. MASM będzie wybierać najbardziej wydajne kodowanie.

## <a name="syntax"></a>Składnia

> **. SAVEREG** *reg* __,__ *przesunięcie*

## <a name="remarks"></a>Uwagi

**. SAVEREG** umożliwia użytkownikom ml64. exe określenie sposobu odwinięcia funkcji ramki i jest dozwolony tylko w obrębie prologu, który rozciąga się od deklaracji Frame [proces](proc.md) do [. ENDPROLOG](dot-endprolog.md) . Dyrektywy te nie generują kodu; generują one tylko `.xdata` i `.pdata`. **. SAVEREG** powinien być poprzedzony instrukcjami, które faktycznie implementują akcje, które mają być odwiązane. Dobrym sposobem jest Zawijanie dyrektyw unwind i kodu, które są przeznaczone do odwinięcia w makrze w celu zapewnienia zgody.

Aby uzyskać więcej informacji, zobacz [MASM for x64 (ml64. exe)](masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
