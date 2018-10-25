---
title: Interfejsy obiektu źródła danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- data source objects [C++], interfaces
- data source objects [C++]
- interfaces [C++], OLE DB
- interfaces [C++], list of
- OLE DB provider templates [C++], object interfaces
- OLE DB [C++], interfaces
ms.assetid: 929e100c-c08c-4b64-8437-d8d1357226f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6c0d2fa5ef33f744e3d76c0565920ecc27523054
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50056129"
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

[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)