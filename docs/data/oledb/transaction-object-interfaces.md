---
title: Interfejsy obiektu transakcji
ms.date: 10/24/2018
helpviewer_keywords:
- interfaces, OLE DB
- transaction object interfaces
- OLE DB, interfaces
- OLE DB providers, transaction support
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: d2ce99ce-6f7a-4ff9-bc6e-acda3633d5c8
ms.openlocfilehash: 177f66222a054c3305418ffcd0acdda5c82ccf43
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556182"
---
# <a name="transaction-object-interfaces"></a>Interfejsy obiektu transakcji

Obiekt transakcji definiuje pojedynczej Atomowej jednostki pracy w źródle danych i określa, jak te jednostki pracy odnoszą się do siebie nawzajem. Ten obiekt nie jest bezpośrednio obsługiwany przez Szablony dostawców OLE DB (oznacza to, należy utworzyć własny obiektu).

W poniższej tabeli przedstawiono interfejsów obowiązkowych i opcjonalnych, zdefiniowane przez OLE DB dla obiektu transakcji.

|Interface|Wymagany?|Implementowany przez Szablony OLE DB?|
|---------------|---------------|--------------------------------------|
|[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Obowiązkowy|Nie|
|[Metody ITransaction](https://docs.microsoft.com/previous-versions/windows/desktop/ms723053(v=vs.85))|Obowiązkowy|Nie|
|[Interfejs ISupportErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/ms715816(v=vs.85))|Optional|Nie|

## <a name="see-also"></a>Zobacz też

[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
