---
title: "Omówienie programowania OLE DB | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Universal Data Access
- OLE DB, about OLE DB
ms.assetid: a5a69730-2793-4277-a67d-6f3c8edab6df
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1f3d97dda514b3cdb0773adb3d7830e611bca3d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ole-db-programming-overview"></a>Omówienie programowania OLE DB
OLE DB to technologia wysokiej wydajności, oparte na modelu COM bazy danych. Zapewnia to często stosowana metoda dostępu do danych niezależnie od tego formularza, w której jest przechowywany. W przypadku typowych godzin pracy ogromnych ilości informacji znajduje się poza baz danych firmowych. Te informacje znajdują się w systemie plików (np. FAT lub NTFS), pliki indeksowane sekwencji, osobiste bazy danych (takich jak dostęp) arkuszy kalkulacyjnych (takich jak program Excel), aplikacje planowania projektu (na przykład projekt) i wiadomości e-mail (np. Outlook). OLE DB umożliwia dostęp do dowolnego rodzaju magazynu danych w taki sam sposób, dopóki magazyn danych ma dostawcy OLE DB.
  
 OLE DB służy do opracowywania aplikacji, które uzyskują dostęp do danych z różnych źródeł, czy są one DBMS lub nie. OLE DB umożliwia uniwersalnych praw dostępu za pomocą interfejsów modelu COM, które obsługuje odpowiedniej funkcji DBMS dla źródła danych danego. COM zmniejsza niepotrzebnego dublowania usług i zmaksymalizowane współdziałanie nie tylko między źródłami danych, ale również między innymi aplikacjami.  
  
## <a name="benefits-of-com"></a>Korzyści wynikające z modelu COM  
 Jest to, gdzie COM jest dostarczany. OLE DB to zestaw interfejsów COM. Uzyskując dostęp do danych za pośrednictwem jednolitego zestaw interfejsów, bazy danych można organizować w macierzy współpracujących składników.  
  
 Oparte na specyfikacji modelu COM, OLE DB definiuje extensible i łatwy w obsłudze zbiór interfejsów, które współczynnika i Hermetyzowanie stałą, wielokrotnego użytku zestawy funkcji systemu DBMS. Te interfejsy należy zdefiniować granice DBMS składniki, takie jak kontenery wiersza, procesory zapytania i koordynatora transakcji, które umożliwiają uniform transakcyjne dostęp do informacji o różnych źródeł.  
 
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie OLE DB](../../data/oledb/ole-db-programming.md)   
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Szablony OLE DB](../../data/oledb/ole-db-templates.md)