---
title: Podsumowanie wyrażeń
ms.date: 06/14/2018
ms.assetid: ed448953-687a-4b57-a1cb-12967bd770ea
ms.openlocfilehash: 320baa51d54f00ac4fdb6633922a8bb36cf92a94
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157821"
---
# <a name="summary-of-expressions"></a>Podsumowanie wyrażeń

*primary-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Stałe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*literał ciągu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(***wyrażenie***)**

*expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie***,***wyrażenia przypisania*

*constant-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*conditional-expression*

*conditional-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie logiczne OR***?**  *wyrażenie* **:** *wyrażenia warunkowego*

*assignment-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*conditional-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unary-expression* *assignment-operator* *assignment-expression*

*postfix-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenia podstawowe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **[**  *expression*  **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym* **(** *argument-expression-list*<sub>zoptymalizowany pod kątem</sub> **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym* **.**  *Identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym* **->** *identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym*  **--**

*argument-expression-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*argument-expression-list***,***wyrażenia przypisania*

*wyrażenie jednoargumentowe*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**++**  *wyrażenie jednoargumentowe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**--**  *wyrażenie jednoargumentowe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*operator jednoargumentowy*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cast-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Operator sizeof***jednoargumentowe wyrażenie*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Operator sizeof (***nazwy typu***)**

*operator jednoargumentowy*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**&** **&#42;** **+** **-** **~** **!**

*cast-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie jednoargumentowe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(** *nazwy typu* **)** *wyrażenie cast* 

*multiplicative-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cast-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression*  **&#42;**  *cast-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie mnożenia***/***wyrażenie cast*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie mnożenia***%***wyrażenie cast*

*additive-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Additive-expression***+***wyrażenia mnożenia*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Additive-expression***-***wyrażenia mnożenia*

*shift-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additive-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*SHIFT-expression***\<\<***additive-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*SHIFT-expression***>>***additive-expression*

*relational-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie relacyjne***\<***shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie relacyjne***>***shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie relacyjne***\<=***shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie relacyjne***>=***shift-expression*

*wyrażenie równości*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie równości***==***wyrażenie relacyjne*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie równości***! =***wyrażenie relacyjne*

*AND-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*equality-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Wyrażenia i***&***wyrażenie równości*

*exclusive-OR-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*AND-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*exclusive-OR-expression*  **^**  *AND-expression*

*inclusive-OR-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*exclusive-OR-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*inclusive-OR-expression*  **&#124;**  *exclusive-OR-expression*

*logical-AND-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*inclusive-OR-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-AND-expression*  **&&**  *inclusive-OR-expression*

*logical-OR-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-AND-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR-expression*  **&#124;&#124;**  *logical-AND-expression*

## <a name="see-also"></a>Zobacz także

- [Gramatyka struktury fazy](../c-language/phrase-structure-grammar.md)
