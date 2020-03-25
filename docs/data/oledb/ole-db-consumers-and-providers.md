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
ms.openlocfilehash: d57ded9d084971c3562fc7f22e6a1a12a4e3368d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210083"
---
# <a name="ole-db-consumers-and-providers"></a>Konsumenci i dostawcy OLE DB

Architektura OLE DB korzysta z modelu odbiorców i dostawców. Odbiorca wysyła żądania dotyczące danych. Dostawca reaguje na te żądania przez umieszczenie danych w formacie tabelarycznym i zwrócenie go do konsumenta. Każde wywołanie, które może zostać wykonane przez konsumenta, musi zostać zaimplementowane w dostawcy.

Zdefiniowane technicznie, konsument to dowolny system lub kod aplikacji (niekoniecznie składnik OLE DB), który uzyskuje dostęp do danych za pomocą interfejsów OLE DB. Interfejsy są zaimplementowane w dostawcy. Dostawca jest dowolnym składnikiem oprogramowania, który implementuje interfejsy OLE DB, aby hermetyzować dostęp do danych i uwidaczniać je innym obiektom (czyli konsumentom).

W przypadku ról odbiorca wywołuje metody dotyczące interfejsów OLE DB; Dostawca OLE DB implementuje wymaganych interfejsów OLE DB.

OLE DB unika warunków klienta i serwera, ponieważ te role nie zawsze mają sens, szczególnie w przypadku n-warstwowa. Ze względu na to, że konsument może być składnikiem w warstwie, która obsługuje inny składnik, aby wywołać go, składnik klienta mógłby być mylący. Ponadto dostawca czasami działa podobnie jak w przypadku sterownika bazy danych niż serwer.

## <a name="see-also"></a>Zobacz też

[Programowanie OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Omówienie programowania OLE DB](../../data/oledb/ole-db-programming-overview.md)
