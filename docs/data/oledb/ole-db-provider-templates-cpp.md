---
title: "Szablony dostawców OLE DB (C++) | Dokumentacja firmy Microsoft"
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
- OLE DB providers [C++], about providers
- databases [C++], OLE DB templates
- OLE DB provider templates [C++], about OLE DB provider templates
- templates [C++], OLE DB
ms.assetid: fccff85f-2af8-4500-82bd-6312d28a74b8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 255a61d7cff661406da327de79c6a726ffb60bab
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ole-db-provider-templates-c"></a>Szablony dostawców OLE DB (C++)
OLE DB jest ważną częścią strategii uniwersalnej Microsoft Data Access. Projekt OLE DB umożliwia dostęp do danych wysokiej wydajności z dowolnego źródła danych. Wszystkie dane tabelaryczne są widoczne za pośrednictwem OLE DB niezależnie od tego, czy pochodzi z bazy danych. Elastyczność zapewnia szeroką zasilania.  
  
 Zgodnie z objaśnieniem w [konsumentów OLE DB i dostawców](../../data/oledb/ole-db-consumers-and-providers.md), OLE DB korzysta z koncepcji konsumenci i dostawcy. Klient przesyła żądań dotyczących danych; Dostawca zwraca dane w formacie tabelarycznym klientowi. Z punktu widzenia programowania najważniejszych implikacji ten model jest czy dostawca musi implementować każde wywołanie przez klienta.  
  
## <a name="what-is-a-provider"></a>Co to jest dostawcę?  
 Dostawcy OLE DB to zbiór obiektów COM, które służą wywołania interfejsu z obiektu konsumenta, transfer danych w formacie tabelarycznym źródła trwałe (nazywane magazynu danych) do użytkownika.  
  
 Dostawcy mogą być prostymi lub złożonymi. Dostawca może obsługiwać minimalnego czasu funkcji lub dostawca jakości pełnej wersji produkcyjnej implementując kilka interfejsów. Dostawcę można Zwróć tabelę, pozwalają klientowi określają format tej tabeli i wykonywać operacje na danych.  
  
 Każdy dostawca implementuje standardowy zestaw obiektów COM do obsługi żądań od klienta, o znaczeniu standardowe konsumenta OLE DB dostęp do danych z każdego dostawcy, niezależnie od języka (takich jak C++ i podstawowe).  
  
 Każdy obiekt COM zawiera kilka interfejsów, niektóre z nich są wymagane i niektóre z nich są opcjonalne. Zaimplementowanie obowiązkowe interfejsy dostawcę gwarantuje minimalny poziom funkcjonalności (zwane zgodności), który dowolnego klienta powinno być możliwe do użycia. Dostawcę można zaimplementować interfejsów opcjonalne oferowanie dodatkowych funkcji. [OLE DB architektura szablonu dostawcy](../../data/oledb/ole-db-provider-template-architecture.md) opisano te interfejsy szczegółowo. Klient zawsze powinny wywoływać `QueryInterface` do określenia, czy dostawca obsługuje danego interfejsu.  
  
## <a name="ole-db-specification-level-support"></a>Obsługa poziomu specyfikacji OLE DB  
 Szablony dostawców OLE DB obsłużyć specyfikacji wersji 2.7 OLE DB. Szablony dostawców OLE DB można zaimplementować dostawcę zgodne poziom 0. Przykładowe dostawcy, na przykład używa szablonów do implementacji serwer non-MS-DOS polecenia, który wykonuje polecenie DOS DIR zapytania do systemu plików. Przykładowe dostawcy zwraca informacje katalogu w zestawie wierszy przeznaczonym standardowego mechanizmu OLE DB dla zwracania danych tabelarycznych.  
  
 Najprostsza typ dostawcy obsługiwane przez Szablony OLE DB jest dostawcą tylko do odczytu z żadnych poleceń. Dostawców za pomocą polecenia są również obsługiwane, jak możliwość tworzenie zakładek i odczytu/zapisu. Pisanie kodu dodatkowe mogą implementowania dostawcy odczytu/zapisu. Dynamiczne zestawy wierszy i transakcje nie są obsługiwane przez bieżącą wersję, ale można je dodać.  
  
## <a name="when-do-you-need-to-create-an-ole-db-provider"></a>Kiedy należy utworzyć dostawcy OLE DB?  
 Użytkownik nie zawsze jest konieczne do utworzenia własnego dostawcę; Firma Microsoft udostępnia kilka opakowaniach jednostkowych, standardowych dostawców w **właściwości Linku danych** okno dialogowe w programie Visual C++. Głównym celem można utworzyć dostawcy OLE DB jest przeprowadzać strategii Uniwersalny dostęp do danych. Niektóre zalety takiego tak to:  
  
-   Uzyskiwanie dostępu do danych za pomocą dowolnego języka C++, Basic i Visual Basic Scripting Edition. Umożliwia programistom różnych w organizacji dostęp do tych samych danych w taki sam sposób, niezależnie od tego, jakie języka korzystają z.  
  
-   Udostępnianie danych do innych danych źródeł, takich jak SQL Server, Excel i dostępu. Może to być bardzo przydatne w przypadku transferu danych między różne formaty.  
  
-   Uczestniczy w operacjach źródła danych między (heterogenicznych). Może to być bardzo efektywnym sposobem magazynowania danych. Przy użyciu dostawcy OLE DB, można przechowywać dane w formacie native i nadal mogli uzyskać dostępu do prostą operacją.  
  
-   Dodawanie dodatkowych funkcji do danych, takich jak przetwarzanie zapytań.  
  
-   Zwiększanie wydajności uzyskiwania dostępu do danych przez kontrolowanie sposobu zmieniany.  
  
-   Zwiększa niezawodność. Jeśli masz format zastrzeżonych danych mogą uzyskiwać dostęp do tego tylko jeden programisty, są narażeni na ataki. Przy użyciu dostawcy OLE DB, można otworzyć tego formatu zastrzeżonych dla wszystkich sieci programistów.  
  
## <a name="read-only-and-updatable-providers"></a>Dostawcy tylko do odczytu i nadaje się do aktualizacji  
 Dostawców w dużym stopniu złożoności i funkcji. Warto kategoryzowanie dostawców do dostawcy tylko do odczytu i aktualizowalni dostawcy:  
  
-   Visual C++ 6.0 obsługiwane są tylko dostawcy tylko do odczytu. [Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md) omówiono sposób tworzenia dostawcy tylko do odczytu.  
  
-   Visual C++ obsługuje aktualizowalni dostawcy, które można zaktualizować (zapisu) magazynu danych. Aby uzyskać informacji o dostawcach nadaje się do aktualizacji, zobacz [tworzenie aktualizowalnego dostawcy](../../data/oledb/creating-an-updatable-provider.md); [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) próbki jest przykładem aktualizowalnego dostawcy.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)  
  
-   [Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)  
  
-   [Programowanie OLE DB](../../data/oledb/ole-db-programming.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Dostęp do danych](../data-access-in-cpp.md)   
 [Dokumentacja zestawu SDK OLE DB](https://msdn.microsoft.com/en-us/library/ms722784.aspx)   
 [OLE DB Podręcznik programisty](https://msdn.microsoft.com/en-us/library/ms713643.aspx)