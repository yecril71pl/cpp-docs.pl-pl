---
title: Wyrażenia stałe języka C
ms.date: 06/14/2018
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: d48a6c47-e44c-4be2-9c8b-7944c7ef8de7
ms.openlocfilehash: f6984c47ef8acde462a8e92e01b72ef26a61eddc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490535"
---
# <a name="c-constant-expressions"></a>Wyrażenia stałe języka C

Wyrażenie stałe jest obliczane w czasie kompilacji w czasie wykonywania nie i mogą być używane w dowolnym miejscu, można stałą. Stałe wyrażenia musi być stałą, która znajduje się w zakresie reprezentowanych wartości dla tego typu. Argumenty mogą wyrażenie stałe być stałe będące liczbami całkowitymi, stałe znaków, stałych zmiennoprzecinkowych, stałe wyliczeń typu rzutowania **sizeof** wyrażeń i innych wyrażeń stałych.

## <a name="syntax"></a>Składnia

*wyrażenie stałe*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Wyrażenia warunkowego*

*wyrażenia warunkowego*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie logiczne OR*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie logiczne OR* **?** *wyrażenie* **:** *wyrażenia warunkowego*

*wyrażenie*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenia przypisania*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie* **,** *wyrażenia przypisania*

*wyrażenia przypisania*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Wyrażenia warunkowego*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie jednoargumentowe* *operator przypisania* *wyrażenia przypisania*

*operator przypisania*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**=** **&#42;=** **/=** **%=** **+=** **-=** **\< \<=** **>>=** **&=** **^=** **&#124;=**

Zawierać symboli nieterminalnych deklaratora struktury, modułu wyliczającego, bezpośrednie deklaratora, deklaratora abstrakcyjny bezpośrednio i instrukcja labeled *wyrażenie_stałe* nieterminalnych.

Wyrażenie stałe liczby całkowitej musi służyć do określania rozmiaru pola bitowego członka struktury, wartość stałej wyliczenia, rozmiaru tablicy lub wartość **przypadek** stałej.

Wyrażenia stałe używane w dyrektywy preprocesora mogą ulec dodatkowe ograniczenia. W związku z tym są nazywane "ograniczonych wyrażeń stałych." Ograniczone wyrażenie stałe nie może zawierać **sizeof** wyrażenia stałe wyliczeń typ rzutowania do dowolnego typu lub stałe typu zmiennoprzecinkowego. Może jednak zawierać specjalnych wyrażenie stałe **zdefiniowane (** _identyfikator_ **)**.

## <a name="see-also"></a>Zobacz także

- [Operandy i wyrażenia](../c-language/operands-and-expressions.md)
