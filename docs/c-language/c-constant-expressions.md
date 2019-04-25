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

Wyrażenie stałe jest obliczane w czasie kompilacji w czasie wykonywania nie i mogą być używane w dowolnym miejscu, można stałą. Stałe wyrażenia musi być stałą, która znajduje się w zakresie reprezentowanych wartości dla tego typu. Argumenty mogą wyrażenie stałe być stałe będące liczbami całkowitymi, stałe znaków, stałych zmiennoprzecinkowych, stałe wyliczeń typu rzutowania **sizeof** wyrażeń i innych wyrażeń stałych.

## <a name="syntax"></a>Składnia

*constant-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*conditional-expression*

*conditional-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR-expression* **?** *wyrażenie* **:** *wyrażenia warunkowego*

*expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie* **,** *wyrażenia przypisania*

*assignment-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*conditional-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unary-expression* *assignment-operator* *assignment-expression*

*operator przypisania*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**=** **&#42;=** **/=** **%=** **+=** **-=** **\<\<=** **>>=** **&=** **^=** **&#124;=**

Zawierać symboli nieterminalnych deklaratora struktury, modułu wyliczającego, bezpośrednie deklaratora, deklaratora abstrakcyjny bezpośrednio i instrukcja labeled *wyrażenie_stałe* nieterminalnych.

Wyrażenie stałe liczby całkowitej musi służyć do określania rozmiaru pola bitowego członka struktury, wartość stałej wyliczenia, rozmiaru tablicy lub wartość **przypadek** stałej.

Wyrażenia stałe używane w dyrektywy preprocesora mogą ulec dodatkowe ograniczenia. W związku z tym są nazywane "ograniczonych wyrażeń stałych." Ograniczone wyrażenie stałe nie może zawierać **sizeof** wyrażenia stałe wyliczeń typ rzutowania do dowolnego typu lub stałe typu zmiennoprzecinkowego. Może jednak zawierać specjalnych wyrażenie stałe **zdefiniowane (** _identyfikator_ **)**.

## <a name="see-also"></a>Zobacz także

- [Operandy i wyrażenia](../c-language/operands-and-expressions.md)
