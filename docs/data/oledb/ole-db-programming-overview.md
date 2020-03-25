---
title: Omówienie programowania OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- Universal Data Access
- OLE DB, about OLE DB
ms.assetid: a5a69730-2793-4277-a67d-6f3c8edab6df
ms.openlocfilehash: 2b855e0917ba9cdbdaa38a92473d7bddb4279101
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210075"
---
# <a name="ole-db-programming-overview"></a>Omówienie programowania OLE DB

OLE DB jest wysoce wydajną technologią bazy danych opartą na modelu COM. Zapewnia to typowy sposób uzyskiwania dostępu do danych niezależnych od formularza, w którym są przechowywane. W typowej sytuacji biznesowej ogromna ilość informacji nie jest przechowywana w firmowych bazach danych. Te informacje znajdują się w systemach plików (takich jak FAT lub NTFS), plikach indeksowanych, osobistych bazach danych (takich jak dostęp), arkuszach (takich jak program Excel), aplikacjach do planowania projektu (takich jak projekt) i poczty e-mail (na przykład Outlook). OLE DB umożliwia dostęp do dowolnego rodzaju magazynu danych w taki sam sposób, o ile magazyn danych ma dostawcę OLE DB.

OLE DB umożliwia tworzenie aplikacji, które uzyskują dostęp do różnorodnych źródeł danych, niezależnie od tego, czy są one w systemie DBMS, czy nie. OLE DB zapewnia uniwersalnego dostępu przy użyciu interfejsów COM, które obsługują odpowiednie funkcje systemu DBMS dla danego źródła danych. Model COM zmniejsza niepotrzebne duplikowanie usług i maksymalizuje współdziałanie nie tylko między źródłami danych, ale również między innymi aplikacjami.

## <a name="benefits-of-com"></a>Zalety modelu COM

Jest to miejsce, w którym znajduje się model COM. OLE DB jest zestawem interfejsów COM. Dzięki dostępowi do danych za pomocą jednolitego zestawu interfejsów, bazę danych można organizować w macierzy współpracujących składników.

W oparciu o specyfikację COM OLE DB definiuje rozszerzalną i utrzymującą kolekcję interfejsów, które będą współczynnikiem i hermetyzować spójne, wielokrotnego użytku fragmenty funkcji systemu DBMS. Te interfejsy definiują granice składników systemu DBMS, takich jak kontenery wierszy, procesory zapytań i Koordynatory transakcji, które umożliwiają jednolity dostęp transakcyjny do różnorodnych źródeł informacji.

## <a name="see-also"></a>Zobacz też

[Programowanie OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Szablony OLE DB](../../data/oledb/ole-db-templates.md)
