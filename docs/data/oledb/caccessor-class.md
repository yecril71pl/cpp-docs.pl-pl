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
ms.openlocfilehash: 032274d7dc85aa823cd28cf61e4606903f13ad9e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509560"
---
# <a name="caccessor-class"></a>Klasa CAccessor

Reprezentuje jeden z typów metod dostępu.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
class CAccessor : public CAccessorBase, public T
```

### <a name="parameters"></a>Parametry

*T*<br/>
Klasa rekordu użytkownika.

## <a name="remarks"></a>Uwagi

Jest on używany, gdy rekord jest statycznie powiązany ze źródłem danych. Rekord zawiera bufor. Ta klasa obsługuje wiele metod dostępu w zestawie wierszy.

Użyj tego typu metody dostępu, gdy znasz strukturę i typ bazy danych.

Jeśli metoda dostępu zawiera pola, które wskazują na pamięć (na przykład `BSTR` interfejs lub), które muszą zostać zwolnione, wywołaj funkcję członkowską [CAccessorRowset:: FreeRecordMemory](./caccessorrowset-class.md#freerecordmemory) przed odczytaniem następnego rekordu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli. h

## <a name="see-also"></a>Zobacz też

[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Dokumentacja szablonów klientów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
