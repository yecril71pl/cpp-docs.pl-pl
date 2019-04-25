---
title: Konsumenci i dostawcy OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB providers, OLE DB data architecture
- OLE DB providers
- OLE DB consumers, OLE DB data architecture
- OLE DB consumers
- OLE DB, data model
ms.assetid: 886cb39d-652b-4557-93f0-4b1b0754d8bc
ms.openlocfilehash: f5940ca65e42787c3156a9537cb3f3f6694339c0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62284023"
---
# <a name="ole-db-consumers-and-providers"></a>Konsumenci i dostawcy OLE DB

Architektura OLE DB używa modelu konsumenci i dostawcy. Konsument wysyła żądania dotyczące danych. Dostawca reaguje na te żądania umieszczenia danych w formacie tabelarycznym i przywróceniem go do użytkownika. Każde wywołanie, który użytkownik może zgłaszać muszą zostać zaimplementowane w dostawcy.

Z technicznego punktu widzenia zdefiniowane, odbiorcy jest każdy systemu lub aplikacji kod (niekoniecznie składnik OLE DB) uzyskuje dostęp do danych za pośrednictwem interfejsów OLE DB. Interfejsy są implementowane w dostawcy. Dostawca więc dowolny składnik oprogramowania, który implementuje interfejsy OLE DB hermetyzują dostęp do danych i udostępnić ją do innych obiektów (oznacza to, że konsumenci).

W przypadku ról użytkownik wywołuje metody dla interfejsów OLE DB; Dostawca OLE DB implementuje wymagane interfejsy OLE DB.

OLE DB pozwala uniknąć warunków klienta i serwera, ponieważ te role nie zawsze mają sensu, szczególnie w sytuacji n warstwowej. Ponieważ użytkownik może być składnik na warstwy, która służy inny składnik, jej wywołania klienta składnika byłoby mylące. Ponadto dostawca czasami funkcjonuje bardziej sterownik bazy danych niż serwer.

## <a name="see-also"></a>Zobacz także

[Programowanie OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Omówienie programowania OLE DB](../../data/oledb/ole-db-programming-overview.md)