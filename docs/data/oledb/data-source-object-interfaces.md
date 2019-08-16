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
ms.openlocfilehash: a615694a9db75cdaf3b187cf6d29248bd26ef978
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501399"
---
# <a name="data-source-object-interfaces"></a>Interfejsy obiektu źródła danych

W poniższej tabeli przedstawiono obowiązkowe i opcjonalne interfejsy zdefiniowane przez OLE DB dla obiektu źródła danych.

|Interface|Wymagany?|Zaimplementowane przez OLE DB szablony?|
|---------------|---------------|--------------------------------------|
|`IDBCreateSession`|Obowiązkowy|Tak|
|`IDBInitialize`|Obowiązkowy|Tak|
|`IDBProperties`|Obowiązkowy|Tak|
|[IPersist](/windows/win32/api/objidl/nn-objidl-ipersist)|Obowiązkowy|Tak|
|[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Optional|Nie|
|`IDBDataSourceAdmin`|Optional|Nie|
|`IDBInfo`|Optional|Nie|
|[IPersistFile](/windows/win32/api/objidl/nn-objidl-ipersistfile)|Optional|Nie|
|`ISupportErrorInfo`|Optional|Nie|

Obiekt źródła danych implementuje `IDBProperties`interfejsy, `IDBInitialize`i `IDBCreateSession` przez dziedziczenie. Możesz wybrać obsługę dodatkowych funkcji, dziedzicząc lub niedziedzicząc z jednej z tych klas implementacji. Jeśli chcesz obsługiwać `IDBDataSourceAdmin` interfejs, musisz dziedziczyć `IDBDataSourceAdminImpl` z klasy.

## <a name="see-also"></a>Zobacz także

[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
