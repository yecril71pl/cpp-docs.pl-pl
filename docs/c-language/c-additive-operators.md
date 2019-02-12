---
title: Operatory dodawania języka C
ms.date: 10/18/2018
helpviewer_keywords:
- usual arithmetic conversions
- operators [C], addition
- + operator, additive operators
- additive operators
- arithmetic operators [C++], additive operators
ms.assetid: bb8ac205-b061-41fc-8dd4-dab87c8b900c
ms.openlocfilehash: 29bea87e56aa90a8deab7ad7280b3fbdfb45c82b
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151198"
---
# <a name="c-additive-operators"></a>Operatory dodawania języka C

Operatory addytywne, przeprowadzić Dodawanie (**+**) i odejmowania (**-**).

## <a name="syntax"></a>Składnia

*additive-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Additive-expression* **+** *wyrażenia mnożenia*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Additive-expression* **-** *wyrażenia mnożenia*

> [!NOTE]
> Mimo że składnia *additive-expression* obejmuje *wyrażenia mnożenia*, oznacza to, że wyrażenia mnożenia są wymagane. Zapoznać się ze składnią w [podsumowanie dotyczące składni języka C](../c-language/c-language-syntax-summary.md), aby uzyskać *wyrażenia mnożenia*, *wyrażenie cast*, i *jednoargumentowe wyrażenie*.

Argumenty operacji może być typu całkowitego lub zmiennoprzecinkowego wartości. Niektóre operacje dodawania można również przeprowadzić na wartościach wskaźnika, zgodnie z opisem w obszarze dyskusji każdy operator.

Operatory dodawania przeprowadzania zwykle konwersje arytmetyczne operandów całkowite i zmiennoprzecinkowe. Typ wyniku jest typem operandu po konwersji. Ponieważ konwersje wykonywane przez operatory dodawania są oferowane warunków przepełnienia lub niedomiaru, informacje mogą zostać utracone, jeśli wynik operacji dodawania nie może być przedstawiony w typie operandów po konwersji.

## <a name="see-also"></a>Zobacz także

[Operatory dodawania: + i -](../cpp/additive-operators-plus-and.md)
