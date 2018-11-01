---
title: Interfejsy obiektu polecenia
ms.date: 10/24/2018
helpviewer_keywords:
- command object interfaces [C++]
- command objects [OLE DB]
- OLE DB [C++], command object interfaces
ms.assetid: dacff5ae-252c-4f20-9ad7-4e602cc48536
ms.openlocfilehash: d9f663d4e857d300e5c0f5783b86445ce824ea8e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598877"
---
# <a name="command-object-interfaces"></a>Interfejsy obiektu polecenia

Obiekt polecenia używa `IAccessor` interfejsu w celu określenia powiązania parametrów. Wywołania konsumenta `IAccessor::CreateAccessor`, przekazanie do niej tablicę `DBBINDING` struktury. `DBBINDING` zawiera informacje dotyczące powiązania kolumny (takie jak typ i długość). Dostawca otrzymuje struktur i określa, jak należy przenieść dane i czy konwersje są niezbędne.

`ICommandText` Interfejs zapewnia sposób, aby określić polecenie tekstu. `ICommandProperties` Interfejs obsługuje wszystkie właściwości polecenia.

## <a name="see-also"></a>Zobacz też

[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
