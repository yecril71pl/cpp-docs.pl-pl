---
title: Tworzenie prostego dostawcy tylko do odczytu
ms.date: 10/26/2018
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
ms.openlocfilehash: 2ac8e45ca06a5566923141adf5a22dc6710eeeab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432607"
---
# <a name="creating-a-simple-read-only-provider"></a>Tworzenie prostego dostawcy tylko do odczytu

Po utworzeniu dostawcy OLE DB przy użyciu **Kreator projektów ATL** i **Kreator biblioteki ATL OLE DB Provider**, można dodać inne funkcje, które mają być obsługiwane. Rozpocznij projektowanie dostawcy, sprawdzając rodzaj danych, które można będzie wysyłania do użytkownika, jak i w jakich okolicznościach. Jest to szczególnie ważne ustalić, czy wymagana jest obsługa polecenia, transakcji i inne opcjonalne obiekty. Na początku dobrego projektowania przyspieszy implementowania i testowania.

Przykład został przedstawiony w dwóch częściach:

- Pierwszy pokazuje części jak [Tworzenie prostego dostawcy tylko do odczytu](../../data/oledb/implementing-the-simple-read-only-provider.md) który odczytuje pary ciągów.

- Drugi pokazuje części jak [zwiększenia prostego dostawcy tylko do odczytu](../../data/oledb/enhancing-the-simple-read-only-provider.md) , dodając `IRowsetLocate` interfejsu.

## <a name="see-also"></a>Zobacz też

[Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)<br/>
