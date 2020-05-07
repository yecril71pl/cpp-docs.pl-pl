---
title: Podsumowanie dotyczące instrukcji
ms.date: 11/04/2016
ms.assetid: ce45d2fe-ec0e-459f-afb1-80ab6a7f0239
ms.openlocfilehash: 1a230ca7d998316d2ec96e76b54ac60575acd2ee
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856998"
---
# <a name="summary-of-statements"></a>Podsumowanie dotyczące instrukcji

*instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Etykieta — instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukcja złożona*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Expression — instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*SELECT — instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*iteracja — instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*skoku — instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*try-except-Statement*  / \* -swoisty dla firmy Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Wypróbuj instrukcję*  / \* finally dla firmy Microsoft\*/

*skok-instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Przejdź**do*identyfikatora***;**    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**utrzymać**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Przerwij**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<sub>wybór</sub> *wyrażenia* **zwrotu** **;**

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
&nbsp;&nbsp;&nbsp;&nbsp;**Wykonaj**  *instrukcję*  **while (**  *wyrażenie*  **);**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**for (**<sub>opt</sub> **;** *expression*<sub>opt</sub> *SELECT* **;** *wyrażenie zgody* *; wyrażenie*<sub>zgody</sub> **)**  

*wybór — instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**if (***Expression***)**—*instrukcja*      <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**if (***wyrażenie***)***instrukcja***else***statement*          <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Switch (***wyrażenie***)**—*instrukcja*      

*etykieta — instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*  **:**  *instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;stała **przypadku***— wyrażenie***:***instrukcja*      <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**default:**  *instrukcja*

*try-except-Statement*:/\* specyficzne dla firmy Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukcja złożonej* instrukcji **__try***złożonej* **__except (***Expression***)**        

*try-finally-Statement*:/\* specyficzne dla firmy Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__try**  *złożonej instrukcji* **__finally**  *instrukcji złożonej*

## <a name="see-also"></a>Zobacz też

[Gramatyka struktury frazy](../c-language/phrase-structure-grammar.md)
