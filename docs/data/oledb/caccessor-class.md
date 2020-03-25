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
ms.openlocfilehash: 2b30cef2baf8c13c5001e44901b984aa1293494d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212306"
---
# <a name="caccessor-class"></a>Klasa CAccessor

Reprezentuje jeden z typów metod dostępu.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
class CAccessor : public CAccessorBase, public T
```

### <a name="parameters"></a>Parametry

*&*<br/>
Klasa rekordu użytkownika.

## <a name="remarks"></a>Uwagi

Jest on używany, gdy rekord jest statycznie powiązany ze źródłem danych. Rekord zawiera bufor. Ta klasa obsługuje wiele metod dostępu w zestawie wierszy.

Użyj tego typu metody dostępu, gdy znasz strukturę i typ bazy danych.

Jeśli metoda dostępu zawiera pola wskazujące na pamięć (na przykład `BSTR` lub interfejs), które muszą zostać zwolnione, wywołaj funkcję członkowską [CAccessorRowset:: FreeRecordMemory](../../data/oledb/caccessorrowset-freerecordmemory.md) przed odczytaniem następnego rekordu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli. h

## <a name="see-also"></a>Zobacz też

[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)
