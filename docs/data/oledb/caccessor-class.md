---
title: Klasa CAccessor | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CAccessor<T>
- ATL::CAccessor
- CAccessor
- ATL::CAccessor<T>
- ATL.CAccessor
dev_langs:
- C++
helpviewer_keywords:
- CAccessor class
ms.assetid: b2ba959f-a686-46f3-8837-176248aef748
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0ac3ad9da312ba1723fd7201b804260e11a64660
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060702"
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

## <a name="see-also"></a>Zobacz też

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)