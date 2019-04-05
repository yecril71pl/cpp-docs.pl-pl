---
title: Interfejsy obiektu polecenia
ms.date: 10/24/2018
helpviewer_keywords:
- command object interfaces [C++]
- command objects [OLE DB]
- OLE DB [C++], command object interfaces
ms.assetid: dacff5ae-252c-4f20-9ad7-4e602cc48536
ms.openlocfilehash: 755c44cf8d0cb5bf5066197bfd0ead3e0f25e1f9
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59032404"
---
# <a name="command-object-interfaces"></a>Interfejsy obiektu polecenia

Obiekt polecenia używa `IAccessor` interfejsu w celu określenia powiązania parametrów. Wywołania konsumenta `IAccessor::CreateAccessor`, przekazanie do niej tablicę `DBBINDING` struktury. `DBBINDING` zawiera informacje dotyczące powiązania kolumny (takie jak typ i długość). Dostawca otrzymuje struktur i określa, jak należy przenieść dane i czy konwersje są niezbędne.

`ICommandText` Interfejs zapewnia sposób, aby określić polecenie tekstu. `ICommandProperties` Interfejs obsługuje wszystkie właściwości polecenia.

## <a name="see-also"></a>Zobacz także

[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
