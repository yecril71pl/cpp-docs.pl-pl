---
title: Podsumowanie wyrażeń
ms.date: 06/14/2018
ms.assetid: ed448953-687a-4b57-a1cb-12967bd770ea
ms.openlocfilehash: 1660690c6d36aa1dbdc025d6afe92e19ff941463
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220837"
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
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie* **->** przyrostkowe *Identyfikator*    <br/>
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
&nbsp;&nbsp;&nbsp;&nbsp;**`sizeof`**  *wyrażenie jednoargumentowe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**sizeof (**  *Nazwa typu*  **)**

*jednoargumentowy — operator*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**&****&#42;** **+** **-** **~** **!**

*wyrażenie cast*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie-jednoargumentowe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie cast* **(***type-name***)**      

*mnożenia — wyrażenie*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie cast*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*mnożenia —* wyrażenie *rzutowania* **&#42;**    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*mnożenia — wyrażenie* **/** *wyrażenie cast*    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*mnożenia — wyrażenie* **%** *wyrażenie cast*    

*wyrażenie addytywne*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*mnożenia — wyrażenie*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie addytywne* **+** *mnożenia — wyrażenie*    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie addytywne* **-** *mnożenia — wyrażenie*    

*wyrażenie przesunięcia*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie addytywne*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie*   * przesunięcia *shift-expression * dodatek-wyrażenie \<\<**  *additive-expression*<br/> &nbsp; &nbsp; &nbsp; &nbsp; * **>>** *additive-expression*  

*wyrażenie relacyjne*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie przesunięcia*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relacyjne* * * \<**  *shift-expression*<br/> wyrażenie &nbsp; &nbsp; relacyjne &nbsp; — wyrażenie * shift-expression relacyjne * * rerelacyjne wyrażenie * Shift-Expression &nbsp; * **>** *shift-expression* <br/> &nbsp; &nbsp; &nbsp; &nbsp;   ** \<=**  *shift-expression*<br/> &nbsp; &nbsp; &nbsp; &nbsp; * **>=** *shift-expression*    

*wyrażenie równości*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie relacyjne*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie równości* **==** *wyrażenie relacyjne*    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie równości*  **! =**  *wyrażenie relacyjne*

*And-Expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie równości*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*And — wyrażenie* **&** *wyrażenie równości*    

*wyłączne lub wyrażeniu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*AND — wyrażenie*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyłączne lub wyrażeniu* **^** *And — wyrażenie*    

*włącznie — lub-Expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyłączne lub wyrażeniu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;wyrażenie " *włączne" lub "* **&#124;** *wykluczające" lub* "    

*wyrażenie logiczne-and-Expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie włączne-lub-*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie logiczne-and-Expression* **&&** *wyrażenie włączne-lub-*    

*wyrażenie logiczne or*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie logiczne-AND-Expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;wyrażenie *logiczne-and-* Expression **&#124;&#124;** *logiczne i wyrażenie*    

## <a name="see-also"></a>Zobacz także

- [Gramatyka struktury frazy](../c-language/phrase-structure-grammar.md)
