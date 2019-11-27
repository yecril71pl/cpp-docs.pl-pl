---
title: .SAVEREG
ms.date: 08/30/2018
f1_keywords:
- .SAVEREG
helpviewer_keywords:
- .SAVEREG directive
ms.assetid: 1dbc2ef6-a197-40e7-9e55-fddcae8cef29
ms.openlocfilehash: 324cf0e70a7ad619e5741c9acc18c24a72f54d13
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397970"
---
# <a name="savereg"></a>.SAVEREG

Generuje `UWOP_SAVE_NONVOL` lub `UWOP_SAVE_NONVOL_FAR` wpis kodu unwind dla określonego rejestru (*reg*) i przesunięcia (*przesunięcie*) przy użyciu bieżącego przesunięcia prologu. MASM będzie wybierać najbardziej wydajne kodowanie.

## <a name="syntax"></a>Składnia

> **. SAVEREG** *reg* __,__ *przesunięcie*

## <a name="remarks"></a>Uwagi

**. SAVEREG**umożliwia użytkownikom ml64. exe określenie sposobu odwinięcia funkcji ramki i jest dozwolony tylko w obrębie prologu, który rozciąga się od deklaracji Frame [proces](../../assembler/masm/proc.md) do [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) . Dyrektywy te nie generują kodu; generują one tylko `.xdata` i `.pdata`. **. SAVEREG** powinien być poprzedzony instrukcjami, które faktycznie implementują akcje, które mają być odwiązane. Dobrym sposobem jest Zawijanie dyrektyw unwind i kodu, które są przeznaczone do odwinięcia w makrze w celu zapewnienia zgody.

Aby uzyskać więcej informacji, zobacz [MASM for x64 (ml64. exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)
