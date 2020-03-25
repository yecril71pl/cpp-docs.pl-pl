---
title: CNoRowset — Klasa
ms.date: 11/04/2016
f1_keywords:
- ATL.CNoRowset
- ATL::CNoRowset<TAccessor>
- CNoRowset
- ATL.CNoRowset<TAccessor>
- ATL::CNoRowset
helpviewer_keywords:
- CNoRowset class
ms.assetid: 55c6c7a4-9e3a-4775-a2dd-c8b333012fa6
ms.openlocfilehash: 19a1e01fd29c74cf1c44081c24bf384704cf2acd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211475"
---
# <a name="cnorowset-class"></a>CNoRowset — Klasa

Może służyć jako argument szablonu (`TRowset`) dla [CCommand](../../data/oledb/ccommand-class.md) lub [CTable](../../data/oledb/ctable-class.md).

## <a name="syntax"></a>Składnia

```cpp
template <class TAccessor = CAccessorBase>
class CNoRowset
```

### <a name="parameters"></a>Parametry

*TAccessor*<br/>
Klasa akcesora. Wartość domyślna to `CAccessorBase`.

## <a name="remarks"></a>Uwagi

Użyj `CNoRowset` jako argumentu szablonu, jeśli polecenie nie zwraca zestawu wierszy.

`CNoRowset` implementuje następujące metody zastępcze, z których każdy odpowiada innym metodom klasy metody dostępu:

- `BindFinished` — wskazuje, kiedy wiązanie jest kompletne (zwraca `S_OK`).

- `Close` — zwalnia wiersze i bieżący interfejs IRowset.

- `GetIID` — Pobiera identyfikator interfejsu punktu połączenia.

- `GetInterface` — pobiera interfejs.

- `GetInterfacePtr` — pobiera zhermetyzowany wskaźnik interfejsu.

- `SetAccessor` — ustawia wskaźnik na metodę dostępu.

- `SetupOptionalRowsetInterfaces` — konfiguruje opcjonalne interfejsy dla zestawu wierszy.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli. h

## <a name="see-also"></a>Zobacz też

[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)
