---
title: .PUSHFRAME
description: Opisuje. PUSHFRAME MASM, używana do określenia sposobu, w jaki należy odtworzyć funkcję Frame.
ms.date: 12/06/2019
f1_keywords:
- .PUSHFRAME
helpviewer_keywords:
- .PUSHFRAME directive
ms.assetid: 17b123d0-4c6d-4fd2-85eb-798e8ad0a73c
ms.openlocfilehash: 5f951396291ecb12dab500a364f176106c5daa8b
ms.sourcegitcommit: 2cac0150ab3bc8260f866451019b8e22c7e1ac11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2019
ms.locfileid: "74945855"
---
# <a name="pushframe"></a>.PUSHFRAME

Generuje wpis kodu unwind `UWOP_PUSH_MACHFRAME`. Jeśli jest określone opcjonalne słowo kluczowe **kodu** , wpis kodu unwind jest przyznany jako modyfikator 1. W przeciwnym razie modyfikator jest równy 0.

## <a name="syntax"></a>Składnia

> **. PUSHFRAME** ⟦**Code**⟧;;

## <a name="remarks"></a>Uwagi

. PUSHFRAME umożliwia użytkownikom ml64. exe określenie sposobu odwinięcia funkcji ramki. Jest on dozwolony tylko w prologu, który rozciąga się od deklaracji Frame [proces](../../assembler/masm/proc.md) do [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) . Te dyrektywy nie generują kodu; generują one tylko `.xdata` i `.pdata`. **. PUSHFRAME** powinien być poprzedzony instrukcjami, które faktycznie implementują akcje, które mają być odwiązane. Dobrym sposobem jest Zawijanie dyrektyw unwind i kodu, które są przeznaczone do odwinięcia w makrze w celu zapewnienia zgody.

Aby uzyskać więcej informacji, zobacz [MASM for x64 (ml64. exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)
