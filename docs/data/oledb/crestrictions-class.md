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
ms.openlocfilehash: 9fb911b469497a007550c042ade97b5a463e78fe
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220447"
---
# <a name="crestrictions-class"></a>Klasa CRestrictions

Klasa ogólna, która umożliwia określenie ograniczeń dla zestawów wierszy schematu.

## <a name="syntax"></a>Składnia

```cpp
template <class T, short nRestrictions, const GUID* pguid>
class CRestrictions :
   public CSchemaRowset <T, nRestrictions>
```

### <a name="parameters"></a>Parametry

*T*<br/>
Klasa używana dla metody dostępu.

*nRestrictions*<br/>
Liczba kolumn ograniczeń dla zestawu wierszy schematu.

*pguid*<br/>
Wskaźnik do identyfikatora GUID schematu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbsch. h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Otwórz](#open)|Zwraca zestaw wyników zgodnie z ograniczeniami wprowadzonymi przez użytkownika.|

## <a name="crestrictionsopen"></a><a name="open"></a>CRestrictions:: Open

Zwraca zestaw wyników zgodnie z ograniczeniami wprowadzonymi przez użytkownika.

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

*obrad*<br/>
podczas Określa istniejący obiekt sesji używany do nawiązywania połączenia ze źródłem danych.

*lpszParam*<br/>
podczas Określa ograniczenia dotyczące zestawu wierszy schematu.

*bBind*<br/>
podczas Określa, czy automatycznie powiązać mapę kolumn. Wartość domyślna to **`true`** , co powoduje automatyczne powiązanie mapy kolumn. Ustawienie *bBind* **`false`** uniemożliwia automatyczne wiązanie mapy kolumn, aby można było utworzyć powiązanie ręcznie. (Ręczne powiązanie ma szczególne znaczenie dla użytkowników OLAP).

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

W zestawie wierszy schematu można określić maksymalnie siedem ograniczeń.

Zobacz [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) , aby uzyskać informacje o zdefiniowanych ograniczeniach dla każdego zestawu wierszy schematu.

## <a name="see-also"></a>Zobacz także

[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Dokumentacja szablonów klientów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Klasy zestawów wierszy schematu i klasy typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)
