---
title: Wyrażenia stałe języka C
ms.date: 06/14/2018
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: d48a6c47-e44c-4be2-9c8b-7944c7ef8de7
ms.openlocfilehash: 38d4eff6cf764a30bf409032ac692189d1300315
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213739"
---
# <a name="c-constant-expressions"></a>Wyrażenia stałe języka C

Wyrażenie stałe jest oceniane w czasie kompilacji, a nie w czasie wykonywania i może być używane w dowolnym miejscu, w którym można użyć stałej. Wyrażenie stałe musi obliczyć stałą, która znajduje się w zakresie wartości, które można reprezentować dla tego typu. Operandy wyrażenia stałej mogą być stałymi całkowitymi, stałymi znakami, stałych zmiennoprzecinkowych, stałymi wyliczenia, rzutowania typów, **`sizeof`** wyrażeniami i innymi wyrażeniami stałymi.

## <a name="syntax"></a>Składnia

*wyrażenie stałe*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie warunkowe*

*wyrażenie warunkowe*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie logiczne OR*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logiczne lub wyrażenie* **?** *wyrażenie* **:** *wyrażenie warunkowe*

*wyrażenie*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*przypisanie — wyrażenie*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie* **,** *przypisanie — wyrażenie*

*przypisanie — wyrażenie*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie warunkowe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;przypisanie *jednoargumentowe* - *wyrażenie* przypisania *operatora*

*przypisanie — operator*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**=****&#42;=** **/=** **%=** **+=** **-=** **\<\<=** **>>=** **&=** **^=** **&#124;=**

Nieterminale dla struktury deklarator, Enumerator, Direct deklarator, Direct-abstract deklarator i labeld zawierają *wyrażenie stałe* bez terminalu.

Aby określić rozmiar elementu członkowskiego pola bitowego struktury, wartość stałej wyliczenia, rozmiar tablicy lub wartość stałej, należy użyć wyrażenia stałej całkowitej **`case`** ...

Wyrażenia stałe używane w dyrektywach preprocesora podlegają dodatkowym ograniczeniom. W związku z tym są one znane jako "wyrażenia stałej z ograniczeniami". Wyrażenie stałej z ograniczeniami nie może zawierać **`sizeof`** wyrażeń, stałych wyliczania, typów rzutowania do dowolnego typu lub typów zmiennoprzecinkowych. Może jednak zawierać specjalne wyrażenie stałe **zdefiniowane (** _Identyfikator_ **)**.

## <a name="see-also"></a>Zobacz także

- [Operandy i wyrażenia](../c-language/operands-and-expressions.md)
