---
title: Wyrażenia stałe języka C
ms.date: 06/14/2018
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: d48a6c47-e44c-4be2-9c8b-7944c7ef8de7
ms.openlocfilehash: f6984c47ef8acde462a8e92e01b72ef26a61eddc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325744"
---
# <a name="c-constant-expressions"></a>Wyrażenia stałe języka C

Wyrażenie stałe jest oceniane w czasie kompilacji, a nie w czasie wykonywania i może być używane w dowolnym miejscu, w którym można użyć stałej. Wyrażenie stałe musi obliczyć stałą, która znajduje się w zakresie wartości, które można reprezentować dla tego typu. Operandy wyrażenia stałej mogą być stałymi całkowitymi, stałymi znakami, stałych zmiennoprzecinkowych, stałymi wyliczenia, rzutowania typów, wyrażeniami **sizeof** i innymi wyrażeniami stałymi.

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
&nbsp;&nbsp;&nbsp;&nbsp;**=****&#42;** **/=** **%=** = **+=** **-=** **&#124;** = ** \< \< ** **>>=** **&=** **^=**

Nieterminale dla struktury deklarator, Enumerator, Direct deklarator, Direct-abstract deklarator i labeld zawierają *wyrażenie stałe* bez terminalu.

Aby określić rozmiar elementu członkowskiego pola bitowego struktury, wartość stałej wyliczenia, rozmiar tablicy lub wartość stałej **wielkości liter** , należy użyć wyrażenia stałej całkowitej ().

Wyrażenia stałe używane w dyrektywach preprocesora podlegają dodatkowym ograniczeniom. W związku z tym są one znane jako "wyrażenia stałej z ograniczeniami". Wyrażenie stałej z ograniczeniami nie może zawierać wyrażeń **sizeof** , stałych wyliczeniowych, typów rzutowania do dowolnego typu lub typów zmiennoprzecinkowych. Może jednak zawierać specjalne wyrażenie stałe **zdefiniowane (** _Identyfikator_ **)**.

## <a name="see-also"></a>Zobacz też

- [Operandy i wyrażenia](../c-language/operands-and-expressions.md)
