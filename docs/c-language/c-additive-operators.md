---
title: Operatory dodawania języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- usual arithmetic conversions
- operators [C], addition
- + operator, additive operators
- additive operators
- arithmetic operators [C++], additive operators
ms.assetid: bb8ac205-b061-41fc-8dd4-dab87c8b900c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 339904e3fe75c712254f3a7802fc76a0e283c8e5
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808358"
---
# <a name="c-additive-operators"></a>Operatory dodawania języka C

Operatory addytywne, przeprowadzić Dodawanie (**+**) i odejmowania (**-**).

## <a name="syntax"></a>Składnia

*Additive-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie mnożenia*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Additive-expression* **+** *wyrażenia mnożenia*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Additive-expression* **-** *wyrażenia mnożenia*

> [!NOTE]
> Mimo że składnia *additive-expression* obejmuje *wyrażenia mnożenia*, oznacza to, że wyrażenia mnożenia są wymagane. Zapoznać się ze składnią w [podsumowanie dotyczące składni języka C](../c-language/c-language-syntax-summary.md), aby uzyskać *wyrażenia mnożenia*, *wyrażenie cast*, i *jednoargumentowe wyrażenie*.

Argumenty operacji może być typu całkowitego lub zmiennoprzecinkowego wartości. Niektóre operacje dodawania można również przeprowadzić na wartościach wskaźnika, zgodnie z opisem w obszarze dyskusji każdy operator.

Operatory dodawania przeprowadzania zwykle konwersje arytmetyczne operandów całkowite i zmiennoprzecinkowe. Typ wyniku jest typem operandu po konwersji. Ponieważ konwersje wykonywane przez operatory dodawania są oferowane warunków przepełnienia lub niedomiaru, informacje mogą zostać utracone, jeśli wynik operacji dodawania nie może być przedstawiony w typie operandów po konwersji.

## <a name="see-also"></a>Zobacz też

[Operatory dodawania: + i -](../cpp/additive-operators-plus-and.md)