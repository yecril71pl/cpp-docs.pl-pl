---
title: Tworzenie prostego dostawcy tylko do odczytu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: b32517e8254f383e624c5262f3a806e66ed28824
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50056259"
---
# <a name="creating-a-simple-read-only-provider"></a>Tworzenie prostego dostawcy tylko do odczytu

Po utworzeniu dostawcy OLE DB przy użyciu kreator projektów ATL i OLE DB Provider Kreator ATL, możesz dodać inne funkcje, które mają być obsługiwane. Rozpocznij projektowanie dostawcy, sprawdzając rodzaj danych, które będą wysyłane do użytkownika, jak i w jakich okolicznościach. Jest to szczególnie ważne ustalić, czy wymagana jest obsługa polecenia, transakcji i inne opcjonalne obiekty. Na początku dobrego projektowania przyspieszy implementowania i testowania.

Przykład został przedstawiony w dwóch częściach:

- Pierwszy pokazuje części jak [Tworzenie prostego dostawcy tylko do odczytu](../../data/oledb/implementing-the-simple-read-only-provider.md) który odczytuje pary ciągów.

- Drugi pokazuje części jak [zwiększenia prostego dostawcy tylko do odczytu](../../data/oledb/enhancing-the-simple-read-only-provider.md) , dodając `IRowsetLocate` interfejsu.

## <a name="see-also"></a>Zobacz też

[Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)