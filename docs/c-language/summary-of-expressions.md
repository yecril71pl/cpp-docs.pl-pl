---
title: Podsumowanie wyrażeń
ms.date: 06/14/2018
ms.assetid: ed448953-687a-4b57-a1cb-12967bd770ea
ms.openlocfilehash: 320baa51d54f00ac4fdb6633922a8bb36cf92a94
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543497"
---
# <a name="summary-of-expressions"></a>Podsumowanie wyrażeń

*wyrażenia podstawowe*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Stałe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*literał ciągu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(***wyrażenie***)** 

*wyrażenie*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenia przypisania*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie***,***wyrażenia przypisania* 

*wyrażenie stałe*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Wyrażenia warunkowego*

*wyrażenia warunkowego*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie logiczne OR*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie logiczne OR***?**   *wyrażenie***:***wyrażenia warunkowego*

*wyrażenia przypisania*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Wyrażenia warunkowego*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie jednoargumentowe* *operator przypisania* *wyrażenia przypisania*

*wyrażeniem przyrostkowym*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenia podstawowe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym***[***wyrażenie***]** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym***(***argument-expression-list*<sub>zoptymalizowany pod kątem</sub> **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym***.**  *Identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym***->***identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym*  **--**

*argument-expression-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenia przypisania*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*argument-expression-list***,***wyrażenia przypisania* 

*wyrażenie jednoargumentowe*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**++**  *wyrażenie jednoargumentowe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**--**  *wyrażenie jednoargumentowe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*operator jednoargumentowy*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie CAST*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Operator sizeof***jednoargumentowe wyrażenie* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Operator sizeof (***nazwy typu***)** 

*operator jednoargumentowy*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**&** **&#42;****+** **-** **~** **!**

*wyrażenie CAST*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie jednoargumentowe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(***nazwy typu***)***wyrażenie cast*

*wyrażenie mnożenia*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie CAST*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie mnożenia***&#42;***wyrażenie cast* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie mnożenia***/***wyrażenie cast* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie mnożenia***%***wyrażenie cast* 

*Additive-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie mnożenia*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Additive-expression***+***wyrażenia mnożenia* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Additive-expression***-***wyrażenia mnożenia* 

*SHIFT-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Additive-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*SHIFT-expression***\<\<***additive-expression* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*SHIFT-expression***>>***additive-expression* 

*wyrażenie relacyjne*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*SHIFT-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie relacyjne***\<***shift-expression* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie relacyjne***>***shift-expression* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie relacyjne***\<=***shift-expression* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie relacyjne***>=***shift-expression* 

*wyrażenie równości*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie relacyjne*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie równości***==***wyrażenie relacyjne* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie równości***! =***wyrażenie relacyjne* 

*I wyrażenie*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie równości*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Wyrażenia i***&***wyrażenie równości* 

*wyłączny OR wyrażenia*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Wyrażenia AND*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyłączny OR wyrażenia***^***wyrażenia AND* 

*wyrażenie włączny OR*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyłączny OR wyrażenia*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie włączny OR***&#124;***wyłączny OR wyrażenia* 

*i wyrażenie logiczne*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie włączny OR*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*i wyrażenie logiczne***&&***włącznie wyrażenie OR* 

*wyrażenie logiczne OR*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*i wyrażenie logiczne*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie logiczne OR***&#124;&#124;***-i wyrażenie logiczne* 

## <a name="see-also"></a>Zobacz także

- [Gramatyka struktury fazy](../c-language/phrase-structure-grammar.md)
