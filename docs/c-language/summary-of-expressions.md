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

*wyrażenie podstawowe*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identyfikatora*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*stałego*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*literał ciągu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(**  *wyrażenie*  **)**

*wyrażenie*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*przypisanie — wyrażenie*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie*  **,**  *przypisanie — wyrażenie*

*wyrażenie stałe*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie warunkowe*

*wyrażenie warunkowe*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie logiczne OR*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logiczne lub wyrażenie*  **?**  *wyrażenie*  **:**  *wyrażenie warunkowe*

*przypisanie — wyrażenie*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie warunkowe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;przypisanie *jednoargumentowe* - *wyrażenie* przypisania *operatora*

*wyrażenie przyrostkowe*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie podstawowe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*przyrostk — wyrażenie*  **[**  *wyrażenie*  **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*przyrostkowe wyrażenie***(***opt-expression-list*<sub>opt</sub> **)**    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie przyrostkowe*  **.**  *identyfikatora*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression***->***Identyfikator* wyrażenia przyrostkowego    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie przyrostkowe*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie przyrostkowe*  **--**

*argument-lista wyrażeń*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*przypisanie — wyrażenie*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*argumenty argumentu-list*  **,**  *przypisanie-wyrażenie*

*wyrażenie jednoargumentowe*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie przyrostkowe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**++**  *wyrażenie jednoargumentowe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**--**  *wyrażenie jednoargumentowe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*operator jednoargumentowy*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie cast*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**sizeof**  *— wyrażenie jednoargumentowe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**sizeof (**  *Nazwa typu*  **)**

*jednoargumentowy — operator*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**&****&#42;** **+**&#42;**-** **!** ! **~**

*wyrażenie cast*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie jednoargumentowe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie cast* **(***type-name***)**      

*mnożenia — wyrażenie*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie cast*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*mnożenia —* wyrażenie *rzutowania* **&#42;**    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*mnożenia —***/***wyrażenie rzutowania* wyrażenia    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*mnożenia —***%***wyrażenie rzutowania* wyrażenia    

*wyrażenie addytywne*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*mnożenia — wyrażenie*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*dodatek-***+** Expression*mnożenia-Expression*    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*dodatek-***-** Expression*mnożenia-Expression*    

*wyrażenie przesunięcia*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie addytywne*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*dodatek shift-expression***\<***-Expression*    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*dodatek shift-expression*  **>>**  *-Expression*

*wyrażenie relacyjne*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie przesunięcia*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression*wyrażenie przesunięcia w postaci relacyjnej*shift-expression* **\<**    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression*wyrażenie przesunięcia w postaci relacyjnej*shift-expression* **>**    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression*wyrażenie przesunięcia w postaci relacyjnej*shift-expression* **\<**    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression*wyrażenie przesunięcia w postaci relacyjnej*shift-expression* **>=**    

*wyrażenie równości*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie relacyjne*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie równości wyrażenia***==***relational-expression*    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie równości*  **! =**  *wyrażenie relacyjne*

*And-Expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie równości*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*AND-expression***&***Wyrażenie równości* i wyrażenia    

*wyłączne lub wyrażeniu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*AND — wyrażenie*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyłączne wyrażenie***^** or*i-Expression*    

*włącznie — lub-Expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyłączne lub wyrażeniu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;wyrażenie " *włączne" lub "* **&#124;** *wykluczające" lub* "    

*wyrażenie logiczne-and-Expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie włączne-lub-*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie koniunkcji logicznej i wyrażenia***&&***włącznie z* wyrażeniem or    

*wyrażenie logiczne or*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie logiczne-AND-Expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;wyrażenie *logiczne-and-* Expression **&#124;&#124;** *logiczne i wyrażenie*    

## <a name="see-also"></a>Zobacz też

- [Gramatyka struktury frazy](../c-language/phrase-structure-grammar.md)
