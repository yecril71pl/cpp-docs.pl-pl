---
title: Tworzenie prostego dostawcy tylko do odczytu
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
ms.openlocfilehash: c0f31818002ce4611926d942b3bc556e31c1ae6f
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524714"
---
# <a name="creating-a-simple-read-only-provider"></a>Tworzenie prostego dostawcy tylko do odczytu

::: moniker range="vs-2019"

Kreator ATL OLE DB Provider nie jest dostępne w programie Visual Studio 2019 r i nowszych wersjach.

::: moniker-end

::: moniker range="vs-2017"

Po utworzeniu dostawcy OLE DB przy użyciu **Kreator projektów ATL** i **Kreator biblioteki ATL OLE DB Provider**, można dodać inne funkcje, które mają być obsługiwane. Rozpocznij projektowanie dostawcy, sprawdzając rodzaj danych, które można będzie wysyłania do użytkownika, jak i w jakich okolicznościach. Jest to szczególnie ważne ustalić, czy wymagana jest obsługa polecenia, transakcji i inne opcjonalne obiekty. Na początku dobrego projektowania przyspieszy implementowania i testowania.

Przykład został przedstawiony w dwóch częściach:

- Pierwszy pokazuje części jak [Tworzenie prostego dostawcy tylko do odczytu](../../data/oledb/implementing-the-simple-read-only-provider.md) który odczytuje pary ciągów.

- Drugi pokazuje części jak [zwiększenia prostego dostawcy tylko do odczytu](../../data/oledb/enhancing-the-simple-read-only-provider.md) , dodając `IRowsetLocate` interfejsu.

::: moniker-end

## <a name="see-also"></a>Zobacz także

[Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)<br/>
