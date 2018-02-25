---
title: "Model obiektów OLE DB | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets, OLE DB object model
- OLE DB, object model
ms.assetid: 1a274a25-c310-4430-a1ec-bd2bd8120eff
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2cd8fb90b7418b45f6bc011e8d4d0db6e04c08df
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ole-db-object-model"></a>Model obiektów OLE DB
Model obiektów OLE DB obejmuje następujące składniki lub obiektów. Pierwsze cztery obiektów lub wymienione składniki (źródeł danych, sesji, poleceń i zestawy wierszy) umożliwiają połączenie ze źródłem danych i go wyświetlać. Rest, począwszy od metody dostępu, odnoszą się do pracy z danymi, gdy jest on wyświetlany.  
  
## <a name="data-sources"></a>Źródła danych  
 Obiekty źródła danych umożliwiają połączenie ze źródłem danych, takich jak pliku lub systemu DBMS. Obiekt źródła danych tworzy i zarządza nimi połączenia oraz zawiera informacje o uprawnienia i uwierzytelnienia (na przykład nazwa użytkownika i hasło). Obiekt źródła danych można utworzyć co najmniej jednej sesji.  
  
## <a name="sessions"></a>Kategoria Sessions  
 Sesja zarządza konkretnej interakcji ze źródłem danych w celu wykonywania zapytań i pobierania danych. Każdej sesji jest pojedynczą transakcję. Transakcja jest jednostka pracy niepodzielnych, zdefiniowany przez test kwasu. Definicję kwasu [transakcji](#vcconoledbcomponents_transactions).  
  
 Sesje wykonywania ważnych zadań, takich jak otwieranie zestawów wierszy i zwraca obiekt źródła danych, który go utworzył. Sesje, można także wrócić metadanych lub informacje o źródle danych (na przykład informacji o tabeli).  
  
 Sesję można utworzyć co najmniej jedno polecenie.  
  
## <a name="commands"></a>Polecenia  
 Polecenie zostanie wykonane poleceniu tekstowym, takich jak instrukcję SQL. Jeśli w poleceniu tekstowym określa zestawu wierszy, np. SQL **wybierz** instrukcji, polecenie tworzy zestaw wierszy.  
  
 Polecenie to po prostu kontener polecenia tekst, który jest ciągiem (np. instrukcja SQL) przekazane z konsumenta do obiektu źródła danych do wykonania przez Magazyn danych dostawcy. Zazwyczaj polecenia tekst jest SQL **wybierz** instrukcji (w takiej sytuacji, ponieważ SQL **wybierz** określa zestawu wierszy polecenia automatycznie tworzy zestawu wierszy).  
  
## <a name="rowsets"></a>Zestawy wierszy  
 Zestawy wierszy ujawniać dane w formacie tabelarycznym. Indeks jest specjalny przypadek zestawu wierszy. Zestawy wierszy można tworzyć z sesją lub polecenie.  
  
### <a name="schema-rowsets"></a>Zestawy wierszy schematu  
 Schematy zawierają metadane (informacje o strukturalnych) dotyczące bazy danych. Zestawy wierszy schematu są zestawy wierszy, które zawierają informacje o schemacie. Niektórzy dostawcy OLE DB dla systemu DBMS obsługuje obiekty zestawu wierszy schematu. Aby uzyskać więcej informacji na temat zestawów wierszy schematu, zobacz [uzyskiwanie metadanych za pomocą zestawów wierszy schematu](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) i [klasy zestawów wierszy schematu i klasy Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).  
  
### <a name="view-objects"></a>Obiekty widoku  
 Wyświetl obiekt definiuje podzbiór wierszy i kolumn w zestawie wierszy. Go nie zawiera danych własnych. Obiekty widoku nie można połączyć dane z wielu zestawów wierszy.  
  
## <a name="accessors"></a>Metody dostępu  
 Tylko OLE DB korzysta z koncepcji metody dostępu. Metody dostępu opisano, jak dane są przechowywane w konsumenta. Zawiera zestaw powiązania (nazywane mapowania kolumn) między polami wierszy (kolumny) i deklaracji w konsumencie elementy członkowskie danych.  
  
##  <a name="vcconoledbcomponents_transactions"></a> Transakcje  
 Obiekty transakcji są używane, gdy zatwierdzanie lub przerywanie transakcji zagnieżdżonych w innych niż względem najniższego poziomu. Transakcja jest jednostka pracy niepodzielnych, zdefiniowany przez test kwasu. KWAS to:  
  
-   Niepodzielność: nie można podzielić na mniejsze jednostki pracy.  
  
-   Współbieżność: więcej niż jedna transakcja może wystąpić w czasie.  
  
-   Izolacja: jedna transakcja ma ograniczoną wiedzą na temat zmiany wprowadzone przez inną.  
  
-   Trwałości: transakcji dokonuje trwałych zmian.  
  
## <a name="enumerators"></a>Modułów wyliczających  
 Moduły wyliczające wyszukiwanie dostępnych źródeł danych i inne moduły wyliczające. Konsumentów, które nie są dostosowane dla źródła danych służy moduły wyliczające do wyszukiwania dla źródła danych do użycia.  
  
 Główny moduł wyliczający, wydane w zestawie SDK dostępu do danych firmy Microsoft, są przesyłane za pośrednictwem rejestru Wyszukiwanie źródła danych i inne moduły wyliczające. Inne moduły wyliczające przechodzenia rejestru lub wyszukiwania w sposób specyficznego dla dostawcy.  
  
## <a name="errors"></a>błędy  
 Wszelkie interfejsu dowolnego obiektu OLE DB mogą generować błędy. Błędy zawierają dodatkowe informacje na temat błędu, w tym obiektu opcjonalne błędów niestandardowych. Te informacje są zawarte w wyniku HRESULT.  
  
## <a name="notifications"></a>Powiadomienia  
 Powiadomienia są używane przez grupy konsumentów współpracujących Udostępnianie zestawu wierszy (gdzie udostępnianie oznacza, że konsumentów uznaje się, że działa w ramach tej samej transakcji). Powiadomienia włączyć zestaw wierszy przeznaczony do udostępniania użytkownikom współpracujących informowany o akcjach na wierszy wykonywane przez ich elementów równorzędnych.  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie OLE DB](../../data/oledb/ole-db-programming.md)   
 [Omówienie programowania OLE DB](../../data/oledb/ole-db-programming-overview.md)