---
title: Serwery automatyzacji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Automation servers
- COM components, Automation servers
- dispatch maps [MFC], Automation servers
- servers, Automation
ms.assetid: 523fd155-51ce-4f91-b986-b74bdbdd7d92
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a33cf8113825804ac831b518e371c4150f2620ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="automation-servers"></a>Serwery automatyzacji
Automatyzacja umożliwia aplikacji do modyfikowania obiektów w innej aplikacji lub na uwidocznienie obiektów, więc można manipulować. Serwer automatyzacji to aplikacja, która udostępnia obiekty programowalny (nazywane obiektami automatyzacji) do innych aplikacji (nazywane [klientów automatyzacji](../mfc/automation-clients.md)). Serwery automatyzacji są nazywane składniki automatyzacji.  
  
 Udostępnianie obiektów automatyzacji umożliwia klientom zautomatyzować niektóre procedury bezpośredni dostęp do obiektów i udostępnia funkcje serwera. Udostępnianie obiektów w ten sposób jest przydatne, gdy aplikacji zawiera funkcje, które są przydatne w przypadku innych aplikacji. Na przykład edytor tekstów może narazić jego działanie sprawdzania pisowni, aby można go używać innych programów. Narażenia obiektów w związku z tym umożliwia dostawcom zwiększające funkcjonalność swoich aplikacji przy użyciu funkcji gotowe do użycia z innych aplikacji.  
  
 Te obiekty automatyzacji mają właściwości i metod ich zewnętrznego interfejsu. Właściwości są nazywane atrybutów obiektu automatyzacji. Właściwości są podobne do elementów członkowskich danych klasy C++. Metody są funkcje, które działają na obiekty automatyzacji. Metody są podobne do funkcji publicznego elementu członkowskiego klasy C++.  
  
> [!NOTE]
>  Mimo że właściwości są podobne elementy członkowskie danych języka C++, nie są bezpośrednio dostępne. Zapewnienie przezroczysty dostęp, skonfiguruj zmiennej wewnętrznej w obiekcie automatyzacji przy użyciu pary funkcji Członkowskich get/set, aby uzyskiwać do nich dostęp.  
  
 W przypadku wystawianego funkcjonalność aplikacji za pośrednictwem wspólnego interfejsu dobrze zdefiniowany, automatyzacji umożliwia tworzenie aplikacji w jednym ogólne języku programowania takich jak Microsoft Visual Basic zamiast w różnych, specyficzne dla aplikacji — makro Języki.  
  
##  <a name="_core_support_for_automation_servers"></a>Obsługa serwerów automatyzacji  
 Visual C++ i MFC framework zapewniają obsługę szeroką gamę serwery automatyzacji. Obsługują wiele koszty związane z wprowadzeniem serwera automatyzacji, dzięki czemu można skoncentrować wysiłków na funkcje aplikacji.  
  
 Mechanizm podmiotu zabezpieczeń w ramach obsługi automatyzacji jest mapy wysyłania, zbiór makra rozwija na deklaracje i wywołania potrzebne do udostępnienia właściwości i metody dla OLE. Mapy wysyłania typowe wygląda następująco:  
  
 [!code-cpp[NVC_MFCAutomation#1](../mfc/codesnippet/cpp/automation-servers_1.cpp)]  
  
 Okno właściwości i widoku klas pomagają w utrzymaniu mapy wysyłania. Po dodaniu nowej metody lub właściwości do klasy Visual C++ dodaje odpowiadający `DISP_FUNCTION` lub `DISP_PROPERTY` z parametrami wskazujący nazwę klasy, nazwy wewnętrzne i zewnętrzne typu metody lub właściwości i danych.  
  
 **Dodaj klasę** okno dialogowe upraszcza deklaracji klasy automatyzacji i zarządzania ich właściwości i operacji. Korzystając z okna dialogowego Dodawanie klasy do dodania do projektu klasę, należy określić swojej klasy podstawowej. Jeśli klasa podstawowa umożliwia automatyzację, okno dialogowe Dodaj klasę Wyświetla formantów, które służy do określania, czy nowa klasa powinna obsługiwać automatyzacji, czy jest ono "OLE możliwość utworzenia" (oznacza to, czy klasy można było tworzyć obiekty na żądanie od klienta COM) i zewnętrzną nazwę klienta COM do użycia.  
  
 **Dodaj klasę** okno dialogowe tworzy następnie deklaracji klasy, takich jak makra odpowiednie funkcje OLE określono. Dodano również szkielet kodu dla implementacji funkcji Członkowskich swojej klasy.  
  
 Kreator aplikacji MFC upraszcza etapy pobieranie aplikacji serwera automatyzacji poza podstaw. W przypadku wybrania **automatyzacji** pola wyboru z **funkcje zaawansowane** strony, Kreator aplikacji MFC dodaje do aplikacji `InitInstance` funkcji wywołania wymagane do zarejestrowania użytkownika automatyzacji obiekty i uruchom aplikację jako serwer automatyzacji.  
  
### <a name="what-do-you-want-to-do"></a>Co chcesz zrobić  
  
-   [Dowiedz się więcej o klienci automatyzacji](../mfc/automation-clients.md)  
  
-   [Dowiedz się więcej o CCmdTarget — klasa](../mfc/reference/ccmdtarget-class.md)  
  
-   [Dowiedz się więcej na temat klasy COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Automatyzacja](../mfc/automation.md)   
 [Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md)

