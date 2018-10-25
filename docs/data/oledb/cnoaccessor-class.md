---
title: Cnoaccessor — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CNoAccessor
- CNoAccessor
- ATL.CNoAccessor
dev_langs:
- C++
helpviewer_keywords:
- CNoAccessor class
ms.assetid: eb669ae5-0a56-49a3-9646-c4ae6239da31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 97cfefc679391cb54ff40f38285f22f40d068553
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063838"
---
# <a name="cnoaccessor-class"></a>CNoAccessor — Klasa

Może służyć jako argument szablonu (`TAccessor`) dla klasy szablonów, takich jak `CCommand` i `CTable`, który wymaga argumentu klasy dostępu.

## <a name="syntax"></a>Składnia

```cpp
class CNoAccessor
```

## <a name="remarks"></a>Uwagi

Użyj `CNoAccessor` jako argument szablonu, jeśli nie chcesz, aby klasy, która ma obsługiwać parametry lub kolumny wyjściowe.

`CNoAccessor` implementuje następujących metod klasy zastępczej, z których każdy odnoszą się do innych metod klasy dostępu:

- `BindColumns` — Wiąże kolumn metod dostępu.

- `BindParameters` — Wiąże parametry utworzonych kolumn.

- `Bind` -Tworzy wiązania.

- `Close` -Zamyka akcesor.

- `ReleaseAccessors` -Zwalnia Akcesory utworzone przez klasę.

- `FreeRecordMemory` -Zwalnia żadnej kolumny w bieżącym rekordzie, które muszą zostać uwolniona.

- `GetColumnInfo` — Pobiera informacje o kolumnach z otwartego zestawu wierszy.

- `GetNumAccessors` -Pobiera liczbę metod dostępu tworzone przez klasę.

- `IsAutoAccessor` — Zwraca wartość PRAWDA, jeśli dane są automatycznie pobierane dla metody dostępu podczas operacji przenoszenia.

- `GetHAccessor` -Pobiera dojście metody dostępu określonej metody dostępu.

- `GetBuffer` -Pobiera wskaźnik do buforu zakładki.

- `NoBindOnNullRowset` -Zapobiega powiązania danych na pusty zestawów wierszy.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli.h

## <a name="see-also"></a>Zobacz też

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)