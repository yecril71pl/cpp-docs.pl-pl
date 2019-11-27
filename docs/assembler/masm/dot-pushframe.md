---
title: .PUSHFRAME
ms.date: 08/30/2018
f1_keywords:
- .PUSHFRAME
helpviewer_keywords:
- .PUSHFRAME directive
ms.assetid: 17b123d0-4c6d-4fd2-85eb-798e8ad0a73c
ms.openlocfilehash: b0f047278f6250d5ef359f7992df4ea23f4bbd9b
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398045"
---
# <a name="pushframe"></a>.PUSHFRAME

Generuje wpis kodu unwind `UWOP_PUSH_MACHFRAME`. W przypadku określenia opcjonalnego *kodu* , wpis kodu unwind jest przyznany jako modyfikator 1. W przeciwnym razie modyfikator jest równy 0.

## <a name="syntax"></a>Składnia

> **. PUSHFRAME** ⟦*Code*⟧;;

## <a name="remarks"></a>Uwagi

. PUSHFRAME umożliwia użytkownikom ml64. exe określenie sposobu odwinięcia funkcji ramki i jest dozwolony tylko w obrębie prologu, który rozciąga się od deklaracji Frame [proces](../../assembler/masm/proc.md) do [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) . Dyrektywy te nie generują kodu; generują one tylko `.xdata` i `.pdata`. **. PUSHFRAME** powinien być poprzedzony instrukcjami, które faktycznie implementują akcje, które mają być odwiązane. Dobrym sposobem jest Zawijanie dyrektyw unwind i kodu, które są przeznaczone do odwinięcia w makrze w celu zapewnienia zgody.

Aby uzyskać więcej informacji, zobacz [MASM for x64 (ml64. exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)
