---
title: .PUSHFRAME
description: Opisuje. PUSHFRAME MASM, używana do określenia sposobu, w jaki należy odtworzyć funkcję Frame.
ms.date: 12/06/2019
f1_keywords:
- .PUSHFRAME
helpviewer_keywords:
- .PUSHFRAME directive
ms.assetid: 17b123d0-4c6d-4fd2-85eb-798e8ad0a73c
ms.openlocfilehash: 0aaec119d26d87fddb1eba505458da1250a5926e
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317581"
---
# <a name="pushframe"></a>.PUSHFRAME

Generuje wpis kodu unwind `UWOP_PUSH_MACHFRAME`. Jeśli jest określone opcjonalne słowo kluczowe **kodu** , wpis kodu unwind jest przyznany jako modyfikator 1. W przeciwnym razie modyfikator jest równy 0.

## <a name="syntax"></a>Składnia

> **. PUSHFRAME** ⟦**Code**⟧;;

## <a name="remarks"></a>Uwagi

. PUSHFRAME umożliwia użytkownikom ml64. exe określenie sposobu odwinięcia funkcji ramki. Jest on dozwolony tylko w prologu, który rozciąga się od deklaracji Frame [proces](proc.md) do [. ENDPROLOG](dot-endprolog.md) . Te dyrektywy nie generują kodu; generują one tylko `.xdata` i `.pdata`. **. PUSHFRAME** powinien być poprzedzony instrukcjami, które faktycznie implementują akcje, które mają być odwiązane. Dobrym sposobem jest Zawijanie dyrektyw unwind i kodu, które są przeznaczone do odwinięcia w makrze w celu zapewnienia zgody.

Aby uzyskać więcej informacji, zobacz [MASM for x64 (ml64. exe)](masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
