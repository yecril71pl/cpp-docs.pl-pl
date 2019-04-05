---
title: IDBSchemaRowsetImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- IDBSchemaRowsetImpl
- CheckRestrictions
- IDBSchemaRowsetImpl::CheckRestrictions
- IDBSchemaRowsetImpl.CheckRestrictions
- IDBSchemaRowsetImpl::CreateSchemaRowset
- ATL::IDBSchemaRowsetImpl::CreateSchemaRowset
- CreateSchemaRowset
- IDBSchemaRowsetImpl.CreateSchemaRowset
- ATL.IDBSchemaRowsetImpl.CreateSchemaRowset
- IDBSchemaRowsetImpl::SetRestrictions
- SetRestrictions
- IDBSchemaRowsetImpl.SetRestrictions
- ATL::IDBSchemaRowsetImpl::GetRowset
- ATL.IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl<SessionClass>::GetRowset
- IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl::GetRowset
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetRowset
- GetRowset
- ATL::IDBSchemaRowsetImpl::GetSchemas
- GetSchemas
- IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- ATL.IDBSchemaRowsetImpl.GetSchemas
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- IDBSchemaRowsetImpl.GetSchemas
- IDBSchemaRowsetImpl::GetSchemas
helpviewer_keywords:
- IDBSchemaRowsetImpl class
- CheckRestrictions method
- CreateSchemaRowset method
- SetRestrictions method
- GetRowset method
- GetSchemas method
ms.assetid: bd7bf0d7-a1c6-4afa-88e3-cfdbdf560703
ms.openlocfilehash: b764b571aae81f6225028cbe0d052d817d93d183
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024364"
---
# <a name="idbschemarowsetimpl-class"></a>IDBSchemaRowsetImpl — Klasa

Udostępnia implementację dla zestawów wierszy schematu.

## <a name="syntax"></a>Składnia

```cpp
template <class SessionClass>
class ATL_NO_VTABLE IDBSchemaRowsetImpl : public IDBSchemaRowset
```

### <a name="parameters"></a>Parametry

*SessionClass*<br/>
Klasa za pomocą którego `IDBSchemaRowsetImpl` jest dziedziczona. Zazwyczaj ta klasa jest klasy sesji użytkownika.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldb.h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Checkrestrictions —](#checkrestrictions)|Sprawdza poprawność ograniczenia względem wierszy schematu.|
|[CreateSchemaRowset](#createschemarowset)|Implementuje funkcji twórcy obiektu COM dla obiektu określonego przez parametr szablonu.|
|[Setrestrictions —](#setrestrictions)|Określa ograniczenia, które obsługują w zestawie wierszy z określonego schematu.|

### <a name="interface-methods"></a>Metody interfejsu

|||
|-|-|
|[GetRowset](#getrowset)|Zwraca zestaw wierszy schematu.|
|[GetSchemas](#getschemas)|Zwraca listę zestawów wierszy schematu jest dostępny za pomocą [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md).|

## <a name="remarks"></a>Uwagi

Ta klasa implementuje [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) interfejsu i funkcja szablonowej twórcy [createschemarowset —](../../data/oledb/idbschemarowsetimpl-createschemarowset.md).

OLE DB używa zestawów wierszy schematu, aby zwrócić dane dotyczące danych dostawcy. Tych danych jest często określany mianem "metadane". Domyślnie dostawca musi obsługiwać zawsze `DBSCHEMA_TABLES`, `DBSCHEMA_COLUMNS`, i `DBSCHEMA_PROVIDER_TYPES`, zgodnie z opisem w [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) w *OLE DB Podręcznik programisty*. Zestawy wierszy schematu są wyznaczone na mapie schematu. Aby uzyskać informacji na temat wpisy mapy schematu, zobacz [SCHEMA_ENTRY](../../data/oledb/schema-entry.md).

OLE DB Provider kreatora, w Kreatorze obiektu ATL automatycznie generuje kod dla zestawów wierszy schematu w projekcie. (Domyślnie Kreator obsługuje zestawów wierszy schematu obowiązkowe, wcześniej wymienione). Podczas tworzenia odbiorcy za pomocą Kreatora obiektu ATL, kreator używa zestawów wierszy schematu można powiązać poprawnych danych dostawcy. Jeśli Twoje zestawów wierszy schematu, aby zapewnić poprawne metadanych nie jest zaimplementowane, Kreator nie zostanie powiązana poprawnych danych.

Aby uzyskać informacje na temat sposobu obsługi zestawów wierszy schematu w dostawcy, zobacz [Obsługa zestawów wierszy schematu](../../data/oledb/supporting-schema-rowsets.md).

Aby uzyskać więcej informacji na temat zestawów wierszy schematu, zobacz [zestawów wierszy schematu](/previous-versions/windows/desktop/ms712921(v=vs.85)) w *OLE DB Podręcznik programisty*.

## <a name="checkrestrictions"></a> IDBSchemaRowsetImpl::CheckRestrictions

Sprawdza poprawność ograniczenia względem wierszy schematu.

### <a name="syntax"></a>Składnia

```cpp
HRESULT CheckRestrictions(REFGUID rguidSchema,
   ULONG cRestrictions,  const VARIANT rgRestrictions[]);
```

#### <a name="parameters"></a>Parametry

*rguidSchema*<br/>
[in] Odwołanie do zestawu wierszy schematu żądanego identyfikatora GUID (na przykład `DBSCHEMA_TABLES`).

*cRestrictions*<br/>
[in] Liczba ograniczeń, które konsumenta przekazywane do zestawu wierszy schematu.

*rgRestrictions*<br/>
[in] Tablicy o długości *cRestrictions* ograniczenie wartości do ustawienia. Aby uzyskać więcej informacji, zobacz opis *rgRestrictions* parametru w [setrestrictions —](../../data/oledb/idbschemarowsetimpl-setrestrictions.md).

### <a name="remarks"></a>Uwagi

Użyj `CheckRestrictions` do sprawdzania poprawności ograniczenia względem wierszy schematu. Sprawdza ograniczenia dotyczące `DBSCHEMA_TABLES`, `DBSCHEMA_COLUMNS`, i `DBSCHEMA_PROVIDER_TYPES` zestawów wierszy schematu. Wywołaj ją do określenia, czy odbiorcy wywołanie `IDBSchemaRowset::GetRowset` jest poprawna. Jeśli chcesz obsługiwać zestawów wierszy schematu innych niż wymienione powyżej, należy utworzyć własną funkcję do wykonania tego zadania.

`CheckRestrictions` Określa, jeśli użytkownik wywołuje [getrowset —](../../data/oledb/idbschemarowsetimpl-getrowset.md) prawidłowe ograniczenie i typ ograniczenia poprawne (na przykład VT_BSTR ciągu), który dostawca obsługuje. Określa również, czy poprawną liczbę ograniczenia są obsługiwane. Domyślnie `CheckRestrictions` będą prosić dostawcy, za pośrednictwem [setrestrictions —](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) wywołanie ograniczenia, które obsługuje on w danym zestawie wierszy. Następnie porównuje ograniczenia od użytkownika z tymi, które jest obsługiwana przez dostawcę i zakończy się pomyślnie lub nie powiedzie się.

Aby uzyskać więcej informacji na temat zestawów wierszy schematu, zobacz [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) w *OLE DB Podręcznik programisty* w zestawie Windows SDK.

## <a name="createschemarowset"></a> IDBSchemaRowsetImpl::CreateSchemaRowset

Implementuje funkcji twórcy obiektu COM dla obiektu określonego przez parametr szablonu.

### <a name="syntax"></a>Składnia

```cpp
template template <class SchemaRowsetClass>
HRESULT CreateSchemaRowset(IUnknown *pUnkOuter,
   ULONG cRestrictions,
   const VARIANT rgRestrictions[],
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown** ppRowset,
   SchemaRowsetClass*& pSchemaRowset);
```

#### <a name="parameters"></a>Parametry

*pUnkOuter*<br/>
[in] Zewnętrzne [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) podczas agregowania, w przeciwnym razie wartość NULL.

*cRestrictions*<br/>
[in] Liczba ograniczenia stosowane do zestawu wierszy schematu.

*rgRestrictions*<br/>
[in] Tablica `cRestrictions` **VARIANT**s ma zostać zastosowany do zestawu wierszy.

*Parametr riid*<br/>
[in] Interfejs do [QueryInterface](../../atl/queryinterface.md) dla dla danych wyjściowych `IUnknown`.

*cPropertySets*<br/>
[in] Ustawia liczbę właściwości do ustawienia.

*rgPropertySets*<br/>
[in] Tablica [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) struktur, które określają właściwości są ustawione.

*ppRowset*<br/>
[out] Wychodzącej `IUnknown` zażądał *riid*. To `IUnknown` stanowi interfejs dla obiektu zestawu wierszy schematu.

*pSchemaRowset*<br/>
[out] Wskaźnik do wystąpienia klasy zestawu wierszy schematu. Zazwyczaj ten parametr nie jest używany, ale może służyć Jeśli należy wykonać więcej pracy na zestaw wierszy schematu przed przekazaniem ich do obiektu COM. Okres istnienia *pSchemaRowset* jest ograniczone przez *ppRowset*.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Ta funkcja implementuje ogólnego twórcy dla wszystkich typów zestawów wierszy schematu. Zazwyczaj użytkownik nie wywołuje tę funkcję. Jest ona wywoływana przez implementację Mapa schematu.

## <a name="setrestrictions"></a> IDBSchemaRowsetImpl::SetRestrictions

Określa ograniczenia, które obsługują w zestawie wierszy z określonego schematu.

### <a name="syntax"></a>Składnia

```cpp
void SetRestrictions(ULONG cRestrictions,
   GUID* /* rguidSchema */,
   ULONG* rgRestrictions);
```

#### <a name="parameters"></a>Parametry

*cRestrictions*<br/>
[in] Liczba ograniczeń w *rgRestrictions* tablicy i liczbę identyfikatory GUID *rguidSchema* tablicy.

*rguidSchema*<br/>
[in] Tablica identyfikatorów GUID zestawów wierszy schematu, dla którego można pobrać ograniczeń. Każdy element tablicy zawiera identyfikator GUID zestawu wierszy schematu jednym (na przykład `DBSCHEMA_TABLES`).

*rgRestrictions*<br/>
[in] Tablicy o długości *cRestrictions* ograniczenie wartości do ustawienia. Każdy element odnosi się do ograniczeń dotyczących identyfikowane przez identyfikator GUID zestawu wierszy schematu. Jeśli zestaw wierszy schematu nie jest obsługiwany przez dostawcę, element jest równa zero. W przeciwnym razie **ULONG** wartość zawiera maska bitowa reprezentujący ograniczenia obsługiwane w tym zestaw wierszy schematu. Aby uzyskać więcej informacji, na którym ograniczenia odpowiadają wierszy określonego schematu, zapoznaj się z tabeli zestaw wierszy schematu identyfikatorów GUID w [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) w *OLE DB Podręcznik programisty* w Windows ZESTAW SDK.

### <a name="remarks"></a>Uwagi

`IDBSchemaRowset` Obiektu wywołania `SetRestrictions` ustalenie, które ograniczeń obsługi w zestawie wierszy z określonego schematu (jest ona wywoływana przez [getschemas —](../../data/oledb/idbschemarowsetimpl-getschemas.md) za pomocą wskaźnika upcasted). Ograniczenia pozwala użytkownikom można pobrać tylko pasujących wierszy (na przykład znaleźć wszystkie kolumny w tabeli "MyTable"). Ograniczenia są opcjonalne, a w przypadku, w których żaden nie jest obsługiwane (ustawienie domyślne), zwracane są wszystkie dane zawsze.

Domyślna implementacja tej metody ustawia *rgRestrictions* elementów na 0 w tablicy. Zastąp domyślną w swojej klasy sesji, aby ustawić ograniczenia innego niż domyślny.

Aby uzyskać informacji dotyczących implementowania Obsługa zestawów wierszy schematu, zobacz [Obsługa zestawów wierszy schematu](../../data/oledb/supporting-schema-rowsets.md).

Na przykład dostawcę, który obsługuje zestawów wierszy schematu zobacz [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) próbki.

Aby uzyskać więcej informacji na temat zestawów wierszy schematu, zobacz [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) w *OLE DB Podręcznik programisty* w zestawie Windows SDK.

## <a name="getrowset"></a> IDBSchemaRowsetImpl::GetRowset

Zwraca zestaw wierszy schematu.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (GetRowset)(IUnknown *pUnkOuter,
   REFGUID rguidSchema,
   ULONG cRestrictions,
   const VARIANT rgRestrictions[],
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown **ppRowset);
```

#### <a name="parameters"></a>Parametry

*pUnkOuter*<br/>
[in] Zewnętrzne `IUnknown` podczas agregacji; w przeciwnym razie wartość NULL.

*rguidSchema*<br/>
[in] Odwołanie do zestawu wierszy schematu żądanego identyfikatora GUID (na przykład `DBSCHEMA_TABLES`).

*cRestrictions*<br/>
[in] Liczba ograniczeń, które mają być stosowane do zestawu wierszy.

*rgRestrictions*<br/>
[in] Tablica `cRestrictions` **VARIANT**s, które reprezentują ograniczenia.

*Parametr riid*<br/>
[in] Identyfikator IID do żądania zestawu wierszy schematu nowo utworzony.

*cPropertySets*<br/>
[in] Ustawia liczbę właściwości do ustawienia.

*rgPropertySets*<br/>
[/ Ściemnianie] Tablica [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) struktur, aby ustawić dla zestawu wierszy schematu nowo utworzony.

*ppRowset*<br/>
[out] Wskaźnik do żądanego interfejsu na zestaw wierszy schematu nowo utworzony.

### <a name="remarks"></a>Uwagi

Ta metoda wymaga od użytkownika posiadania schemat mapowania w klasie sesji. Za pomocą mapy informacji o schemacie `GetRowset` tworzy obiekt danego zestawu wierszy, jeśli *rguidSchema* parametr jest równy jeden z wpisy mapy identyfikatorów GUID. Zobacz [SCHEMA_ENTRY](../../data/oledb/schema-entry.md) opis wpisu mapy.

Zobacz [IDBSchemaRowset::GetRowset](/previous-versions/windows/desktop/ms722634(v=vs.85)) w Windows SDK.

## <a name="getschemas"></a> IDBSchemaRowsetImpl::GetSchemas

Zwraca listę zestawów wierszy schematu jest dostępny za pomocą [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md).

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (GetSchema s )(ULONG * pcSchemas,
   GUID ** prgSchemas,
   ULONG** prgRest);
```

#### <a name="parameters"></a>Parametry

*pcSchemas*<br/>
[out] Wskaźnik do **ULONG** , jest wypełniona liczbą schematów.

*prgSchemas*<br/>
[out] Wskaźnik do tablicy identyfikatorów GUID jest wypełnione za pomocą wskaźnika do tablicy zestaw wierszy schematu identyfikatorów GUID.

*prgRest*<br/>
[out] Wskaźnik do tablicy **ULONG**s, który jest wypełniona tablica ograniczeń.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca tablicę wszystkich zestawów wierszy schematu obsługiwanego przez dostawcę. Zobacz [IDBSchemaRowset::GetSchemas](/previous-versions/windows/desktop/ms719605(v=vs.85)) w Windows SDK.

Implementacja tej funkcji wymaga użytkownik musi mieć schemat mapowania w klasie sesji. Korzystając z informacji Mapa schematu, następnie odpowiadały tablicę identyfikatorów GUID dla schematów w mapie. Reprezentuje schematów obsługiwane przez dostawcę.

## <a name="see-also"></a>Zobacz także

[Klasy zestawów wierszy schematu i klasy Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)<br/>
[Obsługa zestawów wierszy schematu](../../data/oledb/supporting-schema-rowsets.md)<br/>
[SCHEMA_ENTRY](../../data/oledb/schema-entry.md)<br/>
[UpdatePV](https://github.com/Microsoft/VCSamples)