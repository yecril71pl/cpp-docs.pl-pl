---
title: Klasa CAccessor
ms.date: 11/04/2016
f1_keywords:
- ATL.CAccessor<T>
- ATL::CAccessor
- CAccessor
- ATL::CAccessor<T>
- ATL.CAccessor
helpviewer_keywords:
- CAccessor class
ms.assetid: b2ba959f-a686-46f3-8837-176248aef748
ms.openlocfilehash: cfc91f971fc975bcdd2c8ae37d798ff2f5a1cab0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039205"
---
# <a name="caccessor-class"></a>Klasa CAccessor

Reprezentuje jeden z typów dostępu.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
class CAccessor : public CAccessorBase, public T
```

### <a name="parameters"></a>Parametry

*T*<br/>
Klasa rekordu użytkownika.

## <a name="remarks"></a>Uwagi

Jest używany, gdy rekord statycznie jest powiązana ze źródłem danych. Rekord zawiera buforu. Ta klasa obsługuje wielu metod dostępu w zestawie wierszy.

Użyj tego typu dostępu wiadomo, struktury i typ bazy danych.

Jeśli metoda dostępu do sieci zawiera pola, które wskazują na pamięci (takie jak `BSTR` lub interfejsu) który musi być zwolniona, wywołaj funkcję elementu członkowskiego [CAccessorRowset::FreeRecordMemory](../../data/oledb/caccessorrowset-freerecordmemory.md) przed następnego rekordu jest do odczytu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli.h

## <a name="see-also"></a>Zobacz także

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — kompendium](../../data/oledb/ole-db-consumer-templates-reference.md)