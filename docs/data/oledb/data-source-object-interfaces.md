---
title: Interfejsy obiektu źródła danych
ms.date: 10/24/2018
helpviewer_keywords:
- data source objects [C++], interfaces
- data source objects [C++]
- interfaces [C++], OLE DB
- interfaces [C++], list of
- OLE DB provider templates [C++], object interfaces
- OLE DB [C++], interfaces
ms.assetid: 929e100c-c08c-4b64-8437-d8d1357226f6
ms.openlocfilehash: aaa9e90996750b0518999803487fcb39729c76f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519651"
---
# <a name="data-source-object-interfaces"></a>Interfejsy obiektu źródła danych

W poniższej tabeli przedstawiono interfejsów obowiązkowych i opcjonalnych, zdefiniowane przez OLE DB dla obiektu źródła danych.

|Interface|Wymagany?|Implementowany przez Szablony OLE DB?|
|---------------|---------------|--------------------------------------|
|`IDBCreateSession`|Obowiązkowy|Tak|
|`IDBInitialize`|Obowiązkowy|Tak|
|`IDBProperties`|Obowiązkowy|Tak|
|[IPersist](/windows/desktop/api/objidl/nn-objidl-ipersist)|Obowiązkowy|Tak|
|[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Optional|Nie|
|`IDBDataSourceAdmin`|Optional|Nie|
|`IDBInfo`|Optional|Nie|
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Optional|Nie|
|`ISupportErrorInfo`|Optional|Nie|

Źródła danych, obiekt implementuje `IDBProperties`, `IDBInitialize`, i `IDBCreateSession` interfejsów poprzez dziedziczenie. Można obsługiwać dodatkowe funkcje, dziedziczenie lub nie dziedziczy z jednej z tych klasach implementacji. Jeśli chcesz obsługiwać `IDBDataSourceAdmin` interfejs musi dziedziczyć z `IDBDataSourceAdminImpl` klasy.

## <a name="see-also"></a>Zobacz też

[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
