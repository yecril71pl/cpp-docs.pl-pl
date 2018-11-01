---
title: Włączanie i wyłączanie usług dla dostawcy
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
ms.openlocfilehash: ca621b005dd0bad60c70298e4d49abce6fb8d1d7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665455"
---
# <a name="enabling-and-disabling-services-for-a-provider"></a>Włączanie i wyłączanie usług dla dostawcy

Poszczególne usługi OLE DB można włączać lub wyłączać domyślnie dla wszystkich aplikacji uzyskujących dostęp do jednego dostawcy. Jest to realizowane przez dodanie wpisu rejestru OLEDB_SERVICES CLSID dostawcy z `DWORD` wartość określającą usług, aby włączyć lub wyłączyć, jak pokazano w poniższej tabeli.

|Włączone usługi domyślne|Wartość — słowo kluczowe|
|------------------------------|-------------------|
|Wszystkie usługi (ustawienie domyślne)|0xffffffff|
|Wszystkie regiony z wyjątkiem puli i AutoEnlistment|0xFFFFFFFE|
|Wszystkie regiony z wyjątkiem kursor kliencki|0xfffffffb|
|Wszystkie z wyjątkiem buforowanie AutoEnlistment i kursor kliencki|0xfffffff0|
|Brak usług|0x00000000|
|Brak agregacji wszystkie usługi wyłączone|\<Brak klucza >|

## <a name="see-also"></a>Zobacz też

[Włączanie i wyłączanie usług OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)