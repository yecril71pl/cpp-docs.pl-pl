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
&nbsp;&nbsp;&nbsp;&nbsp;*labeled-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*złożonej instrukcji*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Expression-instrukcji*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyboru — instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*iteracji-instrukcji*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*skoku-instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*try-except-statement* /\* specyficzne dla firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*try-finally-Statement* /\* specyficzne dla firmy Microsoft \*/

*skok-instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Przejdź do** *identyfikator* **;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Kontynuuj;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**rozbicie;**<br/>
&nbsp;&nbsp;&nbsp;, &nbsp;zwrócić *wyrażenie*<sub></sub> **zwrotne** **;**

*instrukcja złożona*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;instrukcji **{** *Deklaracja-list*<sub>opt</sub> *-list*<sub>opt</sub> **}**

*Deklaracja-lista*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklaracji*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja list*

*Lista instrukcji*:<br/>
&nbsp;&nbsp; *&nbsp;&nbsp;*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukcji list*

*wyrażenie-instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;*wyrażenie*<sub></sub> &nbsp;

*iteracja — instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**gdy (**  *wyrażenie*  **)**  *instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**czy** *instrukcji* **podczas (** *wyrażenie* **);**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Aby uzyskać (** *wyrażenie*<sub>zoptymalizowany pod kątem</sub> **;** *wyrażenie*<sub>zoptymalizowany pod kątem</sub> **;** *wyrażenie*<sub>zoptymalizowany pod kątem</sub> **)** *— instrukcja*

*wybór — instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Jeśli (** *wyrażenie* **)** *— instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Jeśli (** *wyrażenie* **)** *instrukcji* **else** *— instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Przełącz (** *wyrażenie* **)** *— instrukcja*

*etykieta — instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator* **:** *— instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**przypadek** *wyrażenie_stałe* **:** *— instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**domyślne:** *— instrukcja*

*try-except-Statement*:/\* \*specyficzny dla firmy Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__try** *compound-statement* **__except (** *wyrażenie* **)** *compound-statement*

*try-finally-Statement*:/\* \*specyficznych dla firmy Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__try** *compound-statement* **__finally** *compound-statement*

## <a name="see-also"></a>Zobacz także

[Gramatyka struktury fazy](../c-language/phrase-structure-grammar.md)
