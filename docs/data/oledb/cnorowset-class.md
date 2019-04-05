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
ms.openlocfilehash: 6193e2d461761c53fb05e5c16b3914c56d545173
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035679"
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

## <a name="see-also"></a>Zobacz także

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — kompendium](../../data/oledb/ole-db-consumer-templates-reference.md)