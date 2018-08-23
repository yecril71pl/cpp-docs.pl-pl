---
title: Szablony dostawców OLE DB (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers [C++], about providers
- databases [C++], OLE DB templates
- OLE DB provider templates [C++], about OLE DB provider templates
- templates [C++], OLE DB
ms.assetid: fccff85f-2af8-4500-82bd-6312d28a74b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4983234cdbc64f4ca8364c5afcc2d8e735ba2d01
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464943"
---
# <a name="ole-db-provider-templates-c"></a>Szablony dostawców OLE DB (C++)
OLE DB stanowi ważną część strategii Microsoft Universal Data Access. Konstrukcja OLE DB umożliwia dostęp do danych o wysokiej wydajności z dowolnego źródła danych. Wszelkie dane tabelaryczne są widoczne w OLE DB, niezależnie od tego, czy pochodzi z bazy danych. Elastyczność daje ogromne ilości mocy.  
  
 Jak wyjaśniono w [konsumentów OLE DB i dostawców](../../data/oledb/ole-db-consumers-and-providers.md), OLE DB korzysta z koncepcji konsumenci i dostawcy. Konsument wysyła żądania dotyczące danych. Dostawca zwraca dane w formacie tabelarycznym konsumenta. Z punktu widzenia programowania najważniejszych domniemanie tego modelu jest, czy dostawca musi implementować wybranego przez konsumenta w ten sposób wywołania.  
  
## <a name="what-is-a-provider"></a>Co to jest dostawca?  
 Dostawcy OLE DB to zestaw obiektów COM, które obsługują interfejs wywołania z obiektu konsumenta, transfer danych w formacie tabelarycznym z trwałe źródła (nazywane magazynu danych), do konsumenta.  
  
 Dostawców może być proste lub złożone. Dostawca może obsługiwać minimalnego czasu funkcji lub dostawcy jakości produkcji całego implementując kilka interfejsów. Dostawcę można zwracają tabelę, umożliwia klientowi określenie format tabeli i wykonywać operacje na tych danych.  
  
 Każdy dostawca implementuje zestaw standardowych obiektów COM może obsługiwać żądania od klienta, za pomocą standardowych znaczenie każdy konsument OLE DB dostęp do danych z dowolnego dostawcę, niezależnie od języka (takie jak C++ i podstawowa).  
  
 Każdy obiekt COM, zawiera kilka interfejsów, niektóre z nich są wymagane, a niektóre z nich są opcjonalne. Poprzez implementację interfejsów obowiązkowe, dostawca gwarantuje minimalny poziom funkcjonalności (o nazwie zgodności), który dowolny klient powinien mieć możliwość użycia. Dostawcę można zaimplementować interfejsów opcjonalne oferowanie dodatkowych funkcji. [OLE DB architektura szablonu dostawcy](../../data/oledb/ole-db-provider-template-architecture.md) w tym artykule opisano te interfejsy szczegółowo. Klient zawsze powinna wywołać `QueryInterface` do określenia, czy dostawca obsługuje danego interfejsu.  
  
## <a name="ole-db-specification-level-support"></a>Obsługa poziomu specyfikacji OLE DB  
 Szablony dostawców OLE DB obsługuje specyfikację wersji 2.7 OLE DB. Szablony dostawców OLE DB można zaimplementować dostawcę zgodne poziom 0. Przykład dostawcy, na przykład używa szablonów do wdrożenia serwera non-MS-DOS polecenia, który wykonuje polecenie DOS DIR do wykonywania zapytań w systemie plików. Przykład dostawcy zwraca informacje katalogu w zestawie wierszy, czyli standardowego mechanizmu OLE DB dla zwracania danych tabelarycznych.  
  
 Najprostszy typ dostawcy obsługiwanego przez Szablony OLE DB jest dostawcy tylko do odczytu, za pomocą nie poleceń. Dostawcy za pomocą poleceń są również obsługiwane, jakie są możliwości zakładek i odczytu/zapisu. Aby zaimplementować dostawcę odczytu/zapisu, tworzenia dodatkowego kodu. Dynamiczne zestawy wierszy i transakcje nie są obsługiwane przez bieżącą wersję, ale można je dodać.  
  
## <a name="when-do-you-need-to-create-an-ole-db-provider"></a>Kiedy należy utworzyć dostawcy OLE DB?  
 Nie zawsze należy utworzyć własnego dostawcę; Firma Microsoft udostępnia kilka to wstępnie spakowane zestawy, standardowych dostawców **właściwości Linku danych** okno dialogowe w programie Visual C++. Głównym powodem tworzenia dostawcy OLE DB jest korzystanie z zalet strategii Uniwersalny dostęp do danych. Niektóre zalety spowoduje więc to:  
  
-   Uzyskiwanie dostępu do danych za pomocą dowolnego języka, takich jak C++, Basic i Visual Basic Scripting Edition. Umożliwia ona różnych ekspertów w programowaniu w Twojej organizacji uzyskiwanie dostępu do tych samych danych w taki sam sposób niezależnie od tego, jakiego języka korzystają.  
  
-   Udostępnianie danych z innymi danymi źródeł, takich jak SQL Server, programu Excel i Access. Może to być bardzo przydatne, jeśli chcesz przesyłać dane między różne formaty.  
  
-   Uczestniczy w operacjach źródła danych dla wielu (heterogenicznych). Może to być bardzo skuteczny sposób magazynowania danych. Za pomocą dostawcy OLE DB, możesz przechowywać dane w formacie natywnym i nadal mogli uzyskać do niego dostęp przy użyciu prostych operacji.  
  
-   Dodawanie dodatkowych możliwości na dane, takie jak przetwarzanie zapytań.  
  
-   Zwiększa wydajność dostępu do danych przez kontrolowanie sposobu jest przetwarzany.  
  
-   Zwiększanie niezawodności. Jeśli ma format zastrzeżonych danych mogą uzyskiwać dostęp do tego tylko jeden programisty, są zagrożone. Przy użyciu dostawcy OLE DB, możesz otworzyć ten własnościowego formatu programistom wszystkie usługi.  
  
## <a name="read-only-and-updatable-providers"></a>Dostawcy tylko do odczytu i nadaje się do aktualizacji  
 Dostawców może się znacznie różnić złożoności i funkcji. Warto kategoryzowanie dostawcy do dostawcy tylko do odczytu i aktualizowalni dostawcy:  
  
-   Visual C++ 6.0 obsługiwane są tylko dostawcy tylko do odczytu. [Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md) w tym artykule omówiono sposób tworzenia dostawcy tylko do odczytu.  
-   Visual C++ obsługuje aktualizowalni dostawcy, które można zaktualizować (zapisu) do magazynu danych. Aby uzyskać informacji o dostawcach nadaje się do aktualizacji, zobacz [tworzenie aktualizowalnego dostawcy](../../data/oledb/creating-an-updatable-provider.md); [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) przykładowe dane stanowią przykład aktualizowalnego dostawcy.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)  
  
-   [Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)  
  
-   [Programowanie OLE DB](../../data/oledb/ole-db-programming.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Dostęp do danych](../data-access-in-cpp.md)   
 [Dokumentacja zestawu SDK usługi OLE DB](/previous-versions/windows/desktop/ms722784\(v=vs.85\))   
 [Dokumentacja dotycząca OLE DB](/previous-versions/windows/desktop/ms713643\(v=vs.85\))