---
title: Podsumowanie dotyczące instrukcji
ms.date: 11/04/2016
ms.assetid: ce45d2fe-ec0e-459f-afb1-80ab6a7f0239
ms.openlocfilehash: 122c79b53a8af8a384097dec51a14746a090b1cf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220798"
---
# <a name="summary-of-statements"></a>Podsumowanie dotyczące instrukcji

*instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Etykieta — instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukcja złożona*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Expression — instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*SELECT — instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*iteracja — instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*skoku — instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*try-except-Statement*  / \* Specyficzne dla firmy Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*try-finally-Statement*  / \* Specyficzne dla firmy Microsoft\*/

*skok-instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`goto`**  *Identyfikator*  **;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**utrzymać**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Przerwij**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`return`***expression*<sub>wybór</sub> wyrażenia **;**

*instrukcja złożona*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *deklaracji*<sub>opt</sub> *instrukcji SELECT-list*<sub>opt</sub> **}**

*Deklaracja-lista*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*oświadczeń*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Deklaracja *listy deklaracji* *declaration*

*Lista instrukcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Merge*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukcja-list —* *instrukcja*

*wyrażenie-instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression*<sub>wybór</sub> wyrażenia **;**

*iteracja — instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**while (***wyrażenie***)**—*instrukcja*      <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`do`**  *instrukcja*  **while (**  *wyrażenie*  **);**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**for (**<sub>opt</sub> **;** *expression*<sub>opt</sub> *SELECT* **;** *wyrażenie zgody* *; wyrażenie*<sub>zgody</sub> **)**  

*wybór — instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**if (***Expression***)**—*instrukcja*      <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**if (***wyrażenie***)** instrukcja*instrukcji* **`else`** *statement*          <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Switch (***wyrażenie***)**—*instrukcja*      

*etykieta — instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*  **:**  *instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`case`**  *stała — wyrażenie*  **:**  *instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**default:**  *instrukcja*

*try-except-Statement*:/ \* specyficzne dla firmy Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukcja złożonej* instrukcji **__try***złożonej* **__except (***Expression***)**        

*try-finally-Statement*:/ \* specyficzne dla firmy Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__try***compound-statement* **`__finally`** *instrukcja złożonej* instrukcji __try złożonej    

## <a name="see-also"></a>Zobacz także

[Gramatyka struktury frazy](../c-language/phrase-structure-grammar.md)
