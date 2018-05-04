---
title: ASP, Kreator składników stron ASP ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.asp.asp
dev_langs:
- C++
helpviewer_keywords:
- ATL Active Server Page Component Wizard, ASP
ms.assetid: 4d8cafd6-5e12-4461-8911-29288896af3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dfe27a64a2086f08c5a29e2961d069771fdbc4e6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="asp-atl-active-server-page-component-wizard"></a>ASP, Kreator składników stron ASP ATL
Ta strona ATL Active Server strona kreatora składników umożliwia określenie ustawienia opcjonalne obsługi informacji i stanu dotyczące składnika ASP.  
  
 **Opcjonalny metody**  
 Dodaje metody opcjonalne ASP **OnStartPage** i **OnEndPage**, z obiektem. Należy wybrać tę opcję, aby ustawić wszystkie obiekty wewnętrzne środowiska Active Server Pages. Domyślnie jest zaznaczone.  
  
-   **Metoda OnStartPage/OnEndPage** [OnStartPage](https://msdn.microsoft.com/library/ms691624.aspx) jest wywoływana po raz pierwszy próbuje uzyskać dostęp do obiektu skryptu. **Metoda OnEndPage** jest wywoływana po zakończeniu operacji obiektu przetwarzanie skryptu.  
  
 **Obiektu wewnętrznego**  
 Musisz wybrać **OnStartPage/OnEndPage** opcję, aby określić wszystkie obiekty wewnętrzne środowiska ASP.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Żądanie**|Zapewnia dostęp do strony ASP wewnętrzne **żądania** obiektu. Obiekt żądania jest używany do przekazania żądania HTTP.|  
|**Odpowiedź**|Zapewnia dostęp do strony ASP wewnętrzne **odpowiedzi** obiektu. W odpowiedzi na żądanie obiekt odpowiedzi wysyła informacje do przeglądarki, aby wyświetlić dla użytkownika.|  
|**Sesja**|Zapewnia dostęp do strony ASP wewnętrzne **sesji** obiektu. **Sesji** obiekt przechowuje informacje o bieżącej sesji użytkownika, w tym przechowywania i pobierania informacji o stanie.|  
|**Aplikacja**|Zapewnia dostęp do strony ASP wewnętrzne **aplikacji** obiektu. **Aplikacji** obiektu zarządza stanem, który jest współużytkowany przez wiele obiektów ASP.|  
|**Serwer**|Zapewnia dostęp do strony ASP wewnętrzne **serwera** obiektu. **Serwera** obiektu pozwala tworzyć inne obiekty ASP.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator składników stron ASP ATL](../../atl/reference/atl-active-server-page-component-wizard.md)   
 [Składnik strony Active Server ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)

