---
title: Klienci automatyzacji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- clients, Automation
- Automation clients
- type libraries, Automation clients
- clients
ms.assetid: 84e34a79-06f6-4752-a33b-ae0ede1d8ecf
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9cfb6aae5c947d1f36019e548c72b22a3304aa12
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="automation-clients"></a>Klienci automatyzacji
Automatyzacja umożliwia aplikacji do modyfikowania obiektów w innej aplikacji lub na uwidocznienie obiektów, więc można manipulować. Klient automatyzacji to aplikacja, który będzie obsługiwał widocznych obiektów należących do innej aplikacji. Aplikacja, która udostępnia obiekty nosi nazwę serwera automatyzacji. Klienta manipuluje obiektów aplikacji serwera, uzyskując dostęp do właściwości tych obiektów i funkcji.  
  
### <a name="types-of-automation-clients"></a>Typy klientów automatyzacji  
 Istnieją dwa typy klientów automatyzacji:  
  
-   Klienci, którzy dynamicznie (w czasie wykonywania) uzyskania informacji na temat właściwości i operacji serwera.  
  
-   Klienci, którzy posiadają statyczne (udostępniane w czasie kompilacji) informacja, czy właściwości i operacji serwera.  
  
 Klienci pierwszego rodzaju uzyskania informacji na temat metody i właściwości serwera badając systemu OLE `IDispatch` mechanizmu. Chociaż jest odpowiednie do użycia na potrzeby klientów dynamicznych `IDispatch` jest trudny do wykorzystania dla klientów statycznych, gdzie obiekty prowadzone musi być znane na czas kompilacji. Dla static powiązany klientów, podaj Microsoft Foundation classes [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md) klasy.  
  
 Statycznych powiązanych klientów za pomocą klasy serwera proxy, statycznie połączonej aplikacji klienckiej. Ta klasa udostępnia hermetyzacji C++ bezpieczny, właściwości i operacji aplikacji serwera.  
  
 Klasa `COleDispatchDriver` zawiera główną obsługę po stronie klienta automatyzacji. Przy użyciu `Add New Item` okno dialogowe, Utwórz klasę pochodzącą od `COleDispatchDriver`.  
  
 Następnie możesz określić plik biblioteki typów opisujące właściwości i funkcje obiektu aplikacji serwera. Okno dialogowe Dodawanie elementu odczytuje ten plik i tworzy `COleDispatchDriver`-klasy z funkcji elementów członkowskich, które aplikacji można wywołać w celu dostępu do obiektów aplikacji serwera w języku C++ w bezpieczny sposób. Dodatkowe funkcje odziedziczone `COleDispatchDriver` upraszcza proces wywoływania właściwego serwera automatyzacji.  
  
### <a name="handling-events-in-automation-clients"></a>Obsługa zdarzeń w klientach automatyzacji  
 Do obsługi zdarzeń na kliencie automatyzacji, należy dodać interfejs ujścia. MFC zapewnia obsługę kreatora Dodawanie zbiornika interfejsów dla formantów ActiveX, ale nie jest obsługiwana dla innych serwerów COM. Aby uzyskać informacje na temat dodawania interfejsu zbiornika w kliencie MFC dla interfejsów źródła opisanego przez serwery COM, zobacz porady: Tworzenie interfejsu zbiornika w MFC-Based klient modelu COM (KB 181845) na [http://support.microsoft.com/default.aspxscid=kb;en-us; 181845](http://support.microsoft.com/default.aspxscid=kb;en-us;181845).  
  
## <a name="see-also"></a>Zobacz też  
 [Klienci automatyzacji: Korzystanie z bibliotek typów](../mfc/automation-clients-using-type-libraries.md)   
 [Automatyzacja](../mfc/automation.md)   
 [Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md)

