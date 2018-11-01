---
title: Podsumowanie dotyczące instrukcji
ms.date: 11/04/2016
ms.assetid: ce45d2fe-ec0e-459f-afb1-80ab6a7f0239
ms.openlocfilehash: ac5452e4b7e3faeff364d9f03ec7b87b3b82bd36
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491975"
---
# <a name="summary-of-statements"></a>Podsumowanie dotyczące instrukcji

*Instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*etykietą instrukcji*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Compound-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Instrukcja wyrażeń*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Wybór — instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukcji iteracji*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Instrukcja skoku*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukcji z wyjątkiem try*  / \* Specific firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Spróbuj na koniec instrukcji*  / \* Specific firmy Microsoft \*/

*Instrukcja skoku*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Przejdź do***identyfikator***;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Kontynuuj;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Przerwij;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Zwróć** *wyrażenie*<sub>zoptymalizowany pod kątem</sub> **;**

*Compound-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *lista deklaracji*<sub>zoptymalizowany pod kątem</sub> *listy instrukcji*<sub>zoptymalizowany pod kątem</sub> **}**

*Lista deklaracji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista deklaracji* *deklaracji*

*Lista instrukcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista instrukcji* *— instrukcja*

*Instrukcja wyrażeń*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie*<sub>zoptymalizowany pod kątem</sub> **;**

*instrukcji iteracji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**gdy (***wyrażenie***)***— instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**czy***instrukcji***podczas (***wyrażenie***);**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Aby uzyskać (***wyrażenie*<sub>zoptymalizowany pod kątem</sub> **;** *wyrażenie*<sub>zoptymalizowany pod kątem</sub> **;** *wyrażenie*<sub>zoptymalizowany pod kątem</sub> **)** *— instrukcja*

*Wybór instrukcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Jeśli (***wyrażenie***)***— instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Jeśli (***wyrażenie***)***instrukcji***else***— instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Przełącz (***wyrażenie***)***— instrukcja*

*etykietą instrukcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator***:***— instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**przypadek***wyrażenie_stałe***:***— instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**domyślne:***— instrukcja*

*instrukcji z wyjątkiem try*: /\* Specific firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__try***compound-statement* **__except (***wyrażenie***)***compound-statement* 

*Spróbuj na koniec instrukcji*: /\* Specific firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__try***compound-statement* **__finally***compound-statement* 

## <a name="see-also"></a>Zobacz też

[Gramatyka struktury fazy](../c-language/phrase-structure-grammar.md)