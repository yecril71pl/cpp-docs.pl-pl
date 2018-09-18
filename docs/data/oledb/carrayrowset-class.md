---
title: Carrayrowset — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CArrayRowset<TAccessor>
- ATL.CArrayRowset
- CArrayRowset
- ATL::CArrayRowset
- ATL::CArrayRowset<TAccessor>
- ATL::CArrayRowset::CArrayRowset
- CArrayRowset.CArrayRowset
- ATL.CArrayRowset.CArrayRowset
- ATL.CArrayRowset<TAccessor>.CArrayRowset
- CArrayRowset::CArrayRowset
- CArrayRowset
- CArrayRowset<TAccessor>::CArrayRowset
- ATL::CArrayRowset<TAccessor>::CArrayRowset
- CArrayRowset<TAccessor>.Snapshot
- ATL::CArrayRowset::Snapshot
- Snapshot
- CArrayRowset<TAccessor>::Snapshot
- ATL.CArrayRowset.Snapshot
- ATL.CArrayRowset<TAccessor>.Snapshot
- ATL::CArrayRowset<TAccessor>::Snapshot
- CArrayRowset::Snapshot
- CArrayRowset.Snapshot
- CArrayRowset::operator[]
- CArrayRowset.operator[]
- ATL::CArrayRowset::m_nRowsRead
- ATL::CArrayRowset<TAccessor>::m_nRowsRead
- CArrayRowset<TAccessor>::m_nRowsRead
- ATL.CArrayRowset<TAccessor>.m_nRowsRead
- CArrayRowset.m_nRowsRead
- m_nRowsRead
- ATL.CArrayRowset.m_nRowsRead
- CArrayRowset::m_nRowsRead
dev_langs:
- C++
helpviewer_keywords:
- CArrayRowset class
- CArrayRowset class, constructor
- Snapshot method
- operator [], arrays
- '[] operator'
- operator[], arrays
- m_nRowsRead
ms.assetid: 511427e1-73ca-4fd8-9ba1-ae9463557cb6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e13f262b90ff46955d6ba63fb83a941d712b017a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087880"
---
# <a name="carrayrowset-class"></a>CArrayRowset — Klasa

Uzyskuje dostęp do elementów zestawu wierszy, za pomocą składni tablicy.  
  
## <a name="syntax"></a>Składnia

```cpp
template < class TAccessor >  
class CArrayRowset : 
   public CVirtualBuffer <TAccessor>, 
   protected CBulkRowset <TAccessor>  
```  
  
### <a name="parameters"></a>Parametry  

*TAccessor*<br/>
Typ metody dostępu klasę zestawu wierszy do użycia.  

## <a name="requirements"></a>Wymagania  

**Nagłówek:** atldbcli.h  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CArrayRowset](#carrayrowset)|Konstruktor.|  
|[Migawka](#snapshot)|Odczytuje całego zestawu wierszy do pamięci.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[Operator&#91;&#93;](#operator)|Uzyskuje dostęp do elementu zestawu wierszy.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|[CArrayRowset::m_nRowsRead](#nrowsread)|Liczba wierszy, które znasz.|  
  
## <a name="carrayrowset"></a> CArrayRowset::CArrayRowset

Tworzy nową `CArrayRowset` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
CArrayRowset(int nMax = 100000);  
```  
  
#### <a name="parameters"></a>Parametry  

*nmaks.*<br/>
[in] Maksymalna liczba wierszy w zestawie wierszy. 

## <a name="snapshot"></a> CArrayRowset::Snapshot

Odczytuje całego zestawu wierszy do pamięci, tworzenia obrazu lub migawkę go.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Snapshot() throw();  
```  

## <a name="operator"></a> CArrayRowset::operator

Udostępnia składni tablicy do uzyskiwania dostępu do wierszy w zestawie wierszy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
TAccessor & operator[](int nrow);  
```  
  
#### <a name="parameters"></a>Parametry  

*TAccessor*<br/>
Oparte na szablonach parametr, który określa typ metody dostępu przechowywane w zestawie wierszy.  
  
*nRow*<br/>
[in] Numer wiersza (element tablicy), po którym chcesz uzyskać dostęp.  
  
### <a name="return-value"></a>Wartość zwracana  

Zawartość żądanych wierszy.  
  
### <a name="remarks"></a>Uwagi  

Jeśli *nRow* przekracza liczbę wierszy w zestawie wierszy, zgłaszany jest wyjątek.  

## <a name="nrowsread"></a> CArrayRowset::m_nRowsRead

Zawiera liczbę wierszy w zestawie wierszy, które już przeczytana.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
ULONG m_nRowsRead;  
```  
  
## <a name="see-also"></a>Zobacz też  

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CRowset, klasa](../../data/oledb/crowset-class.md)