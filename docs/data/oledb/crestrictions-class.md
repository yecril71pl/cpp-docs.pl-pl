---
title: Klasa CRestrictions
ms.date: 11/04/2016
f1_keywords:
- ATL::CRestrictions
- CRestrictions
- ATL.CRestrictions
- CRestrictions.Open
- ATL::CRestrictions::Open
- ATL.CRestrictions.Open
- CRestrictions::Open
helpviewer_keywords:
- CRestrictions class
- Open method
ms.assetid: 0aaa2364-641c-4318-b110-7446aada4b4f
ms.openlocfilehash: 95517931f3156c4850e07c78910ccbffff424faa
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556520"
---
# <a name="crestrictions-class"></a>Klasa CRestrictions

Ogólna klasa, która pozwala określić ograniczenia dla zestawów wierszy schematu.

## <a name="syntax"></a>Składnia

```cpp
template <class T, short nRestrictions, const GUID* pguid>
class CRestrictions :
   public CSchemaRowset <T, nRestrictions>
```

### <a name="parameters"></a>Parametry

*T*<br/>
Klasa, używane do dostępu.

*nRestrictions*<br/>
Liczba kolumn ograniczeń dla zestawu wierszy schematu.

*pguid*<br/>
Wskaźnik do identyfikatora GUID dla schematu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbsch.h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Otwórz](#open)|Zwraca wynik ustawione zgodnie z ograniczeniami dostarczone przez użytkownika.|

## <a name="open"></a> CRestrictions::Open

Zwraca wynik ustawione zgodnie z ograniczeniami dostarczone przez użytkownika.

### <a name="syntax"></a>Składnia

```cpp
HRESULT Open(const CSession& session,
   LPCTSTR lpszParam 1 = NULL,
   LPCTSTR lpszParam 2 = NULL,
   LPCTSTR lpszParam 3 = NULL,
   LPCTSTR lpszParam 4 = NULL,
   LPCTSTR lpszParam 5 = NULL,
   LPCTSTR lpszParam 6 = NULL,
   LPCTSTR lpszParam 7 = NULL,
   bool bBind = true);
```

#### <a name="parameters"></a>Parametry

*Sesji*<br/>
[in] Określa istniejącego obiektu sesji używane do połączenia ze źródłem danych.

*lpszParam*<br/>
[in] Określa ograniczenia na zestaw wierszy schematu.

*bBind*<br/>
[in] Określa, czy należy automatycznie powiązania na mapie kolumny. Wartość domyślna to **true**, co powoduje, że mapa kolumny z oświadczeniem automatycznie. Ustawienie *bBind* do **false** uniemożliwia automatyczne powiązania mapy kolumnę tak, aby można powiązać ręcznie. (Ręczne powiązanie to szczególne znaczenie w odniesieniu do użytkowników OLAP).

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

Można określić maksymalnie siedem ograniczeń w zestawie wierszy schematu.

Zobacz [IDBSchemaRowset](https://docs.microsoft.com/previous-versions/windows/desktop/ms713686(v=vs.85)) informacji o zdefiniowanych ograniczenia na każdy zestaw wierszy schematu.

## <a name="see-also"></a>Zobacz też

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Klasy zestawów wierszy schematu i klasy Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)