---
title: Kwestie projektowania architektonicznego OLE DB | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 75d996416e92ded920f45d3352c6478dd8c67a86
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ole-db-architectural-design-issues"></a>Kwestie projektowania architektonicznego OLE DB
Przed uruchomieniem aplikacji OLE DB, należy rozważyć następujące kwestie:  
  
 **Jakie programowania implementacji zostanie użyty do zapisu w aplikacji OLE DB?**  
 Firma Microsoft oferuje kilka bibliotek w tym celu: Biblioteka szablonów OLE DB, atrybuty OLE DB i raw interfejsy OLE DB w OLE DB SDK. Ponadto istnieją kreatorów ułatwiające zapisu programu. Implementacje te są opisane w [szablony OLE DB i atrybuty oraz inne implementacje](../../data/oledb/ole-db-templates-attributes-and-other-implementations.md).  
  
 **Czy trzeba zapisać własnego dostawcę?**  
 Większość deweloperów nie trzeba napisać własne dostawcy. Firma Microsoft udostępnia wielu dostawców. Zawsze, gdy tworzone jest połączenie danych (na przykład podczas dodawania użytkownika do projektu przy użyciu OLE DB Kreator konsumenta ATL), **właściwości Linku danych** listy dostępnych dostawców zarejestrowanych w tym systemie. Jeśli jeden z tych dostawców jest odpowiedni dla swojej aplikacji dostęp do danych, jak magazyn i dane, najłatwiejszym jest Użyj jednego z nich. Jednak jeśli w magazynie danych nie pasuje do jednej z tych kategorii, należy utworzyć własnego dostawcę. Aby uzyskać informacje o tworzeniu dostawców, zobacz [szablony OLE DB Provider](../../data/oledb/ole-db-provider-templates-cpp.md).  
  
 **Jaki poziom obsługi potrzebujesz dla Twojego konsumenta?**  
 Niektórych klientów mogą być bardzo podstawowe; podczas gdy inne mogą być bardzo skomplikowane. Funkcje obiektów OLE DB jest określona przez właściwości. Użycie utworzyć konsumenta lub Kreatora bazy danych dostawcy, aby utworzyć dostawcę OLE DB Kreator konsumenta ATL, ustawia właściwości odpowiedniego obiektu można udzielić użytkownik standardowy zestaw funkcji. Jednak jeśli klasy generowane przez kreatora konsumenta lub dostawca nie obsługują wszystko, co jest to potrzebne, należy odwoływać się do interfejsów dla tych klas w [OLE DB Szablony biblioteki](../../data/oledb/ole-db-templates.md). Te interfejsy zawijać raw interfejsy OLE DB, zapewniając dodatkowe implementacji, aby ułatwić ich użycie za.  
  
 Na przykład, jeśli chcesz zaktualizować danych w zestawie wierszy, ale nie pamiętasz określić podczas tworzenia użytkownika przy użyciu kreatora można określić funkcji po fakcie przez ustawienie **DBPROP_IRowsetChange** i  **DBPROP_UPDATABILITY** właściwości w obiekcie command. Następnie, po utworzeniu zestawu wierszy ma `IRowsetChange` interfejsu.  
  
 **Masz starszą kodu przy użyciu innej technologii dostępu do danych (ADO ODBC i DAO)?**  
 Biorąc pod uwagę możliwe kombinacje technologii (na przykład przy użyciu składników ADO ze składnikami OLE DB i migrację kodu ODBC do OLE DB), obejmujące wszystkie sytuacje wykracza poza zakres dokumentacji Visual C++. Jednak wiele artykułów obejmujących różne scenariusze są dostępne w następujących witrynach sieci Web firmy Microsoft:  
  
-   [Microsoft Pomoc i obsługa techniczna](http://go.microsoft.com/fwlink/p/?linkid=148218)  
  
-   [Omówienie artykuły techniczne na temat dostępu do danych firmy Microsoft](http://go.microsoft.com/fwlink/p/?linkid=148217)  
  
-   [Visual Studio Solution Center](http://go.microsoft.com/fwlink/p/?linkid=148215)  
  
-   [Wyszukaj w witrynie Microsoft.com](http://search.microsoft.com/)  
  
 Podczas wyszukiwania, wprowadź kombinacja słów kluczowych, która najlepiej pasuje do danego scenariusza; na przykład: jeśli były używane obiektów ADO przy użyciu dostawcy OLE DB, spróbuj Wyszukiwanie logiczne z **ADO i "OLE DB"**. Jeśli chcesz przeprowadzić migrację starszego kodu DAO do ODBC, wybierz opcję "wszystkie wyrazy" oraz określić parametry, takie jak **Migrowanie DAO**.  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie OLE DB](../../data/oledb/ole-db-programming.md)   
 [Omówienie programowania OLE DB](../../data/oledb/ole-db-programming-overview.md)