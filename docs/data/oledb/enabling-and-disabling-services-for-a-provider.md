---
title: Włączanie i wyłączanie usług dla dostawcy
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
ms.openlocfilehash: d91f08accf1a8be69f63d6bbcaa4c620d68c1077
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033034"
---
# <a name="enabling-and-disabling-services-for-a-provider"></a>Włączanie i wyłączanie usług dla dostawcy

Poszczególne usługi OLE DB można włączać lub wyłączać domyślnie dla wszystkich aplikacji uzyskujących dostęp do jednego dostawcy. Odbywa się to przez dodanie wpisu rejestru OLEDB_SERVICES w obszarze CLSID dostawcy o wartości DWORD, określając usług, aby włączyć lub wyłączyć, jak pokazano w poniższej tabeli.

|Włączone usługi domyślne|Wartość — słowo kluczowe|
|------------------------------|-------------------|
|Wszystkie usługi (ustawienie domyślne)|0xffffffff|
|Wszystkie regiony z wyjątkiem puli i AutoEnlistment|0xFFFFFFFE|
|Wszystkie regiony z wyjątkiem kursor kliencki|0xfffffffb|
|Wszystkie z wyjątkiem buforowanie AutoEnlistment i kursor kliencki|0xfffffff0|
|Brak usług|0x00000000|
|Brak agregacji wszystkie usługi wyłączone|\<Brak klucza >|

## <a name="see-also"></a>Zobacz także

[Włączanie i wyłączanie usług OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)