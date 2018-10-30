---
title: Tworzenie prostego dostawcy tylko do odczytu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/26/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c8fd4e5eb25ab1e8e6b20b576a0688da7b5aa2ef
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216399"
---
# <a name="creating-a-simple-read-only-provider"></a>Tworzenie prostego dostawcy tylko do odczytu

Po utworzeniu dostawcy OLE DB przy użyciu **Kreator projektów ATL** i **Kreator biblioteki ATL OLE DB Provider**, można dodać inne funkcje, które mają być obsługiwane. Rozpocznij projektowanie dostawcy, sprawdzając rodzaj danych, które można będzie wysyłania do użytkownika, jak i w jakich okolicznościach. Jest to szczególnie ważne ustalić, czy wymagana jest obsługa polecenia, transakcji i inne opcjonalne obiekty. Na początku dobrego projektowania przyspieszy implementowania i testowania.

Przykład został przedstawiony w dwóch częściach:

- Pierwszy pokazuje części jak [Tworzenie prostego dostawcy tylko do odczytu](../../data/oledb/implementing-the-simple-read-only-provider.md) który odczytuje pary ciągów.

- Drugi pokazuje części jak [zwiększenia prostego dostawcy tylko do odczytu](../../data/oledb/enhancing-the-simple-read-only-provider.md) , dodając `IRowsetLocate` interfejsu.

## <a name="see-also"></a>Zobacz też

[Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)<br/>
