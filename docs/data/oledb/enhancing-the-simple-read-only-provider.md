---
title: Udoskonalanie prostego dostawcy tylko do odczytu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- read-only poviders [C++]
- IRowsetLocate class
- IRowsetLocate class, adding to OLE DB template providers
- simple read-only poviders [C++]
ms.assetid: cba0e09f-44c1-41c1-9456-332aa13dc158
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dc899314070f10c0b10cd959af57a7230a406ac3
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50069714"
---
# <a name="enhancing-the-simple-read-only-provider"></a>Udoskonalanie prostego dostawcy tylko do odczytu

W tej sekcji pokazano, jak poprawić [prostego dostawcy tylko do odczytu](../../data/oledb/implementing-the-simple-read-only-provider.md) utworzony w poprzedniej sekcji. `IRowsetLocateImpl` Tworzy implementację `IRowsetLocate` interfejs i dodaje obsługę zakładki dla Ciebie.

W przypadku dostawcy pracy można poprawić, aby aktualizacji dostawcy, Obsługa transakcji i zwiększyć wydajność algorytmu pobieranie z wiersza. Większość dostawcy ulepszenia obejmują dodawanie interfejsu do istniejącego obiektu COM.

Przykład w następujących tematach zwiększa mechanizm pobieranie z wiersza, dodając `IRowsetLocate` współpracować w celu `CAgentRowset`. Tematy dowiesz się, jak do:

- [Wprowadź RCustomRowset dziedziczyć irowsetlocate —](../../data/oledb/modifying-the-inheritance-of-rmyproviderrowset.md).

- [Dynamiczne określanie kolumn zwracanych do konsumenta](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).

## <a name="see-also"></a>Zobacz też

[Tworzenie prostego dostawcy tylko do odczytu](../../data/oledb/creating-a-simple-read-only-provider.md)