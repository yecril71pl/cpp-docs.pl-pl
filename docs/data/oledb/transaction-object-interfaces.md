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
ms.openlocfilehash: b86064c162dcacfbbc5877614c63d92d0f2bd347
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501241"
---
# <a name="transaction-object-interfaces"></a>Interfejsy obiektu transakcji

Obiekt Transaction definiuje niepodzielną jednostkę pracy w źródle danych i określa, jak te jednostki pracy odnoszą się do siebie. Ten obiekt nie jest bezpośrednio obsługiwany przez szablony dostawcy OLE DB (oznacza to, że należy utworzyć własny obiekt).

W poniższej tabeli przedstawiono obowiązkowe i opcjonalne interfejsy zdefiniowane przez OLE DB dla obiektu Transaction.

|Interface|Wymagany?|Zaimplementowane przez OLE DB szablony?|
|---------------|---------------|--------------------------------------|
|[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Obowiązkowy|Nie|
|[ITransaction](/previous-versions/windows/desktop/ms723053(v=vs.85))|Obowiązkowy|Nie|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816(v=vs.85))|Optional|Nie|

## <a name="see-also"></a>Zobacz także

[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
