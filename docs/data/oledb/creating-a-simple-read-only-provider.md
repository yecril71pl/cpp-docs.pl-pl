---
title: Tworzenie prostego dostawcy tylko do odczytu
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
ms.openlocfilehash: 466530cb8c2ebca7f1c87370389309d3a0486e26
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707610"
---
# <a name="creating-a-simple-read-only-provider"></a>Tworzenie prostego dostawcy tylko do odczytu

::: moniker range="vs-2019"

Kreator ATL OLE DB Provider nie jest dostępne w programie Visual Studio 2019 r i nowszych wersjach.

::: moniker-end

::: moniker range="<=vs-2017"

Po utworzeniu dostawcy OLE DB przy użyciu **Kreator projektów ATL** i **Kreator biblioteki ATL OLE DB Provider**, można dodać inne funkcje, które mają być obsługiwane. Rozpocznij projektowanie dostawcy, sprawdzając rodzaj danych, które można będzie wysyłania do użytkownika, jak i w jakich okolicznościach. Jest to szczególnie ważne ustalić, czy wymagana jest obsługa polecenia, transakcji i inne opcjonalne obiekty. Na początku dobrego projektowania przyspieszy implementowania i testowania.

Przykład został przedstawiony w dwóch częściach:

- Pierwszy pokazuje części jak [Tworzenie prostego dostawcy tylko do odczytu](../../data/oledb/implementing-the-simple-read-only-provider.md) który odczytuje pary ciągów.

- Drugi pokazuje części jak [zwiększenia prostego dostawcy tylko do odczytu](../../data/oledb/enhancing-the-simple-read-only-provider.md) , dodając `IRowsetLocate` interfejsu.

::: moniker-end

## <a name="see-also"></a>Zobacz także

[Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)<br/>
