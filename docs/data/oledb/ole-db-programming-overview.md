---
title: Omówienie programowania OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- Universal Data Access
- OLE DB, about OLE DB
ms.assetid: a5a69730-2793-4277-a67d-6f3c8edab6df
ms.openlocfilehash: 68ada06514defe0f7f5332288ad8e91a7d8d9351
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59035533"
---
# <a name="ole-db-programming-overview"></a>Omówienie programowania OLE DB

OLE DB jest technologią bazy danych o wysokiej wydajności, oparte na modelu COM. Zapewnia popularny sposób uzyskania dostępu do danych, niezależnie od postaci, w którym są przechowywane. W przypadku typowych godzin pracy ogromna ilość informacji nie są przechowywane w bazach danych firmowych. Te informacje znajdują się w systemach plików (np. FAT lub NTFS), pliki indeksowane sekwencji, osobiste bazy danych (np. dostępu), arkuszy kalkulacyjnych (np. Excel), aplikacje planowania projektu (na przykład projekt) i poczty e-mail (np. Outlook). OLE DB pozwala na uzyskiwanie dostępu do dowolnego rodzaju magazynu danych w taki sam sposób, tak długo, jak magazyn danych ma dostawcy OLE DB.

OLE DB pozwala tworzyć aplikacje, które uzyskują dostęp do danych z różnych źródeł, czy są one bazami danych, czy nie. OLE DB pozwala uniwersalnych praw dostępu za pomocą interfejsów COM, obsługujące poprawne działanie systemu DBMS dla danego źródła danych. COM zmniejsza niepotrzebne duplikacji usług i zmaksymalizowane współdziałanie nie tylko wśród źródeł danych, ale także wśród innych aplikacji.

## <a name="benefits-of-com"></a>Korzyści z modelu COM

Jest to, gdzie jest oferowana w modelu COM. OLE DB to zbiór interfejsów COM. Uzyskując dostęp do danych za pomocą jednolitego zestawu interfejsów, można organizować bazy danych w macierzy, współpracujących składników.

Oparte na specyfikacji modelu COM, OLE DB definiuje rozszerzalny i łatwego w utrzymaniu zbiór interfejsów, które wziąć pod uwagę i hermetyzacji spójny, wielokrotnego użytku części funkcjonalności systemu DBMS. Niniejsze interfejsy określają granice DBMS składników, takich jak kontenery wiersza, procesory zapytań i transakcji koordynatorów, umożliwiających jednolity transakcyjnych dostęp do informacji z różnych źródeł.

## <a name="see-also"></a>Zobacz także

[Programowanie OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Szablony OLE DB](../../data/oledb/ole-db-templates.md)