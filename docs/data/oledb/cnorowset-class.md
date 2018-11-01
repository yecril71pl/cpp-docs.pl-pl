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
ms.openlocfilehash: 513e393bbc782d87b37dab108428f2970fbb92e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644460"
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
Klasa metody dostępu. Wartość domyślna to `CAccessorBase`.

## <a name="remarks"></a>Uwagi

Użyj `CNoRowset` jako argument szablonu, jeśli polecenie nie zwraca zestawu wierszy.

`CNoRowset` implementuje następujących metod klasy zastępczej, z których każdy odnoszą się do innych metod klasy dostępu:

- `BindFinished` — Wskazuje, kiedy powiązania jest ukończone (zwraca `S_OK`).

- `Close` -Zwalnia wierszy i bieżącego interfejsu IRowset.

- `GetIID` -Pobiera identyfikator interfejsu punktu połączenia.

- `GetInterface` -Pobiera interfejs.

- `GetInterfacePtr` -Pobiera wskaźnik zhermetyzowany interfejsu.

- `SetAccessor` -Ustawia wskaźnik akcesor.

- `SetupOptionalRowsetInterfaces` -Konfiguruje interfejsy opcjonalne dla zestawu wierszy.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli.h

## <a name="see-also"></a>Zobacz też

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)