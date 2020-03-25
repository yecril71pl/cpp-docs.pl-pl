---
title: CNoAccessor — Klasa
ms.date: 11/04/2016
f1_keywords:
- ATL::CNoAccessor
- CNoAccessor
- ATL.CNoAccessor
helpviewer_keywords:
- CNoAccessor class
ms.assetid: eb669ae5-0a56-49a3-9646-c4ae6239da31
ms.openlocfilehash: c82d756690c6c2a719cb03f458c471aa44e3d5b5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211734"
---
# <a name="cnoaccessor-class"></a>CNoAccessor — Klasa

Może służyć jako argument szablonu (`TAccessor`) dla klas szablonu, takich jak `CCommand` i `CTable`, które wymagają argumentu klasy metody dostępu.

## <a name="syntax"></a>Składnia

```cpp
class CNoAccessor
```

## <a name="remarks"></a>Uwagi

Użyj `CNoAccessor` jako argumentu szablonu, gdy nie chcesz, aby Klasa obsługiwała parametry lub kolumny wyjściowe.

`CNoAccessor` implementuje następujące metody zastępcze, z których każdy odpowiada innym metodom klasy metody dostępu:

- `BindColumns` — wiąże kolumny z dostępem do metod dostępu.

- `BindParameters` — tworzy powiązanie utworzonych parametrów z kolumnami.

- `Bind` — tworzy powiązania.

- `Close` — zamyka metodę dostępu.

- `ReleaseAccessors` — zwalnia metody dostępu utworzone przez klasę.

- `FreeRecordMemory` — zwalnia wszystkie kolumny w bieżącym rekordzie, które muszą zostać zwolnione.

- `GetColumnInfo` — pobiera informacje o kolumnie z otwartego zestawu wierszy.

- `GetNumAccessors` — Pobiera liczbę metod dostępu utworzonych przez klasę.

- `IsAutoAccessor`-zwraca wartość true, jeśli podczas operacji przenoszenia dane są pobierane automatycznie.

- `GetHAccessor` — Pobiera dojście metody dostępu do określonego akcesora.

- `GetBuffer` — Pobiera wskaźnik do buforu zakładek.

- `NoBindOnNullRowset` — uniemożliwia powiązanie danych z pustymi zestawami wierszy.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli. h

## <a name="see-also"></a>Zobacz też

[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)
