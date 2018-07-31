---
title: OLE DB kwestie projektowania architektonicznego problemów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB, application design considerations
ms.assetid: 8caa7d99-d2bb-42c9-8884-74f228bb6ecc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5b080945309732bec06c63eb665bbf6dd5f4acb5
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340566"
---
# <a name="ole-db-architectural-design-issues"></a>Kwestie projektowania architektonicznego OLE DB
Przed uruchomieniem aplikacji OLE DB, należy rozważyć następujące kwestie:  
  
 **Jakie programowania implementacja będzie używać do pisania aplikacji OLE DB?**  
 Firma Microsoft oferuje kilka bibliotek w tym celu: Biblioteka szablonów OLE DB, atrybuty OLE DB i raw interfejsy OLE DB OLE DB zestawu SDK. Ponadto istnieją kreatorów ułatwiające pisanie programu. Te implementacje są opisane w [szablony OLE DB i atrybuty oraz inne implementacje](../../data/oledb/ole-db-templates-attributes-and-other-implementations.md).  
  
 **Czy trzeba zapisać własnego dostawcę?**  
 Większość programistów nie potrzebuje napisać własne dostawcy. Firma Microsoft udostępnia kilku dostawców. Zawsze, gdy tworzysz połączenie danych (na przykład Dodaj odbiorcę do projektu przy użyciu OLE DB Kreator konsumenta ATL), **właściwości Linku danych** okno dialogowe wyświetla listę wszystkich dostępnych dostawców zarejestrowanych w systemie. Jeśli jeden z tych dostawców jest odpowiedni dla swojej aplikacji dostęp do danych, jak magazyn i dane, najłatwiejszym jest użyj jednej z nich. Jednakże jeśli magazyn danych nie pasuje do jednej z tych kategorii, należy utworzyć własnego dostawcę. Aby dowiedzieć się, jak tworzenie dostawców, zobacz [szablony OLE DB Provider](../../data/oledb/ole-db-provider-templates-cpp.md).  
  
 **Jaki poziom pomocy technicznej potrzebnych dla konsumentów?**  
 Niektóre konsumentów mogą być bardzo podstawowe; podczas gdy inne mogą być bardzo złożone. Funkcje obiektów OLE DB jest określany przez właściwości. Użycie utworzyć odbiorcę lub Kreatora dostawcy bazy danych, aby utworzyć dostawcę OLE DB Kreator konsumenta ATL, ustawia właściwości odpowiedniego obiektu umożliwiają standardowy zestaw funkcji. Jednak jeśli klasy generowane przez kreatora konsumenta lub dostawca obsługuje wszystko, czego potrzebujesz, jest to, należy do odwoływania się do interfejsów dla tych klas w [OLE DB szablony Biblioteka](../../data/oledb/ole-db-templates.md). Te interfejsy opakować pierwotne interfejsy OLE DB, zapewniając dodatkowe implementacji, aby ułatwić korzystanie z nich należy.  
  
 Na przykład, jeśli chcesz zaktualizować dane w zestawie wierszy, ale nie pamiętam określić, to podczas tworzenia odbiorcy za pomocą kreatora, możesz można określić funkcji w późniejszym czasie, ustawiając `DBPROP_IRowsetChange` i `DBPROP_UPDATABILITY` właściwości w obiekcie command. Następnie, po utworzeniu zestawu wierszy ma `IRowsetChange` interfejsu.  
  
 **Czy masz starszego kodu przy użyciu innej technologii dostępu do danych (ADO ODBC i DAO)?**  
 Biorąc pod uwagę możliwe kombinacje technologii (na przykład ze składnikami OLE DB przy użyciu składników ADO i migracja kodu ODBC do OLE DB), obejmujące wszystkich sytuacjach wykracza poza zakres z dokumentacji języka Visual C++. Wiele artykułów obejmujących różne scenariusze są jednak dostępne w następujących witrynach sieci Web firmy Microsoft:  
  
-   [I pomocy technicznej firmy Microsoft](http://go.microsoft.com/fwlink/p/?linkid=148218)  
  
-   [Omówienie artykuły techniczne dotyczące dostępu do danych firmy Microsoft](http://go.microsoft.com/fwlink/p/?linkid=148217)  
  
-   [Visual Studio Solution Center](http://go.microsoft.com/fwlink/p/?linkid=148215)  
  
-   [Wyszukaj w witrynie Microsoft.com](http://search.microsoft.com/)  
  
 Podczas wykonywania wyszukiwania wprowadź kombinacja słów kluczowych, która najlepiej pasuje do danego scenariusza; na przykład: Jeśli była używana obiektów ADO przy użyciu dostawcy OLE DB, spróbuj Wyszukiwanie logiczne z **ADO i "OLE DB"**. Jeśli chcesz migrować starszego kodu DAO do ODBC, wybierz pozycję "wszystkie słowa" i określić parametry, takie jak **Migrowanie DAO**.  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie OLE DB](../../data/oledb/ole-db-programming.md)   
 [Omówienie programowania OLE DB](../../data/oledb/ole-db-programming-overview.md)