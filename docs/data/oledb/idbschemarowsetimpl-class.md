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
ms.openlocfilehash: eea0ebeaf83b9203cf57f7b35fe3dd1ec2d63d81
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844005"
---
# <a name="idbschemarowsetimpl-class"></a>IDBSchemaRowsetImpl — Klasa

Zapewnia implementację zestawów wierszy schematu.

## <a name="syntax"></a>Składnia

```cpp
template <class SessionClass>
class ATL_NO_VTABLE IDBSchemaRowsetImpl : public IDBSchemaRowset
```

### <a name="parameters"></a>Parametry

*SessionClass*<br/>
Klasa, według której `IDBSchemaRowsetImpl` jest dziedziczona. Typowo, ta klasa będzie klasą sesji użytkownika.

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLDB. h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

| Nazwa | Opis |
|-|-|
|[CheckRestrictions](#checkrestrictions)|Sprawdza poprawność ograniczeń względem zestawu wierszy schematu.|
|[CreateSchemaRowset](#createschemarowset)|Implementuje funkcję twórcy obiektów COM dla obiektu określonego przez parametr szablonu.|
|[Setograniczenia](#setrestrictions)|Określa, które ograniczenia są obsługiwane dla określonego zestawu wierszy schematu.|

### <a name="interface-methods"></a>Metody interfejsu

| Nazwa | Opis |
|-|-|
|[GetRowset](#getrowset)|Zwraca zestaw wierszy schematu.|
|[GetSchemas](#getschemas)|Zwraca listę zestawów wierszy schematu dostępnych przez [IDBSchemaRowsetImpl:: GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md).|

## <a name="remarks"></a>Uwagi

Ta klasa implementuje interfejs [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) i funkcję Szablonowana Creator [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md).

OLE DB używa zestawów wierszy schematu, aby zwracać dane dotyczące danych w dostawcy. Takie dane są często nazywane "metadanymi". Domyślnie dostawca musi zawsze obsługiwać `DBSCHEMA_TABLES` , `DBSCHEMA_COLUMNS` , i `DBSCHEMA_PROVIDER_TYPES` , zgodnie z opisem w [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) , w *dokumentacji programisty OLE DB*. Zestawy wierszy schematu są wyznaczeni w mapie schematów. Aby uzyskać informacje na temat wpisów mapy schematu, zobacz [SCHEMA_ENTRY](../../data/oledb/schema-entry.md).

Kreator dostawcy OLE DB w Kreatorze obiektów ATL automatycznie generuje kod dla zestawów wierszy schematu w projekcie. (Domyślnie Kreator obsługuje obowiązkowe wcześniej wymienione zestawy wierszy schematu). Podczas tworzenia konsumenta przy użyciu kreatora obiektów ATL Kreator używa zestawów wierszy schematu, aby powiązać odpowiednie dane z dostawcą. Jeśli zestaw wierszy schematu nie zostanie wdrożony w celu zapewnienia poprawnych metadanych, Kreator nie będzie powiązać prawidłowych danych.

Aby uzyskać informacje na temat obsługi zestawów wierszy schematu w dostawcy, zobacz [Obsługa zestawów wierszy schematu](../../data/oledb/supporting-schema-rowsets.md).

Aby uzyskać więcej informacji na temat zestawów wierszy schematu, zobacz [zestawy wierszy schematu](/previous-versions/windows/desktop/ms712921(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="idbschemarowsetimplcheckrestrictions"></a><a name="checkrestrictions"></a> IDBSchemaRowsetImpl:: CheckRestrictions

Sprawdza poprawność ograniczeń względem zestawu wierszy schematu.

### <a name="syntax"></a>Składnia

```cpp
HRESULT CheckRestrictions(REFGUID rguidSchema,
   ULONG cRestrictions,  const VARIANT rgRestrictions[]);
```

#### <a name="parameters"></a>Parametry

*rguidSchema*<br/>
podczas Odwołanie do żądanego identyfikatora GUID zestawu wierszy schematu (na przykład `DBSCHEMA_TABLES` ).

*cRestrictions*<br/>
podczas Liczba ograniczeń, które konsument przeszedł dla zestawu wierszy schematu.

*rgRestrictions*<br/>
podczas Tablica długości *cRestrictions* wartości ograniczeń, które mają zostać ustawione. Aby uzyskać więcej informacji, zobacz opis parametru *rgRestrictions* w temacie [setograniczenia](../../data/oledb/idbschemarowsetimpl-setrestrictions.md).

### <a name="remarks"></a>Uwagi

Służy `CheckRestrictions` do sprawdzania poprawności ograniczeń dla zestawu wierszy schematu. Sprawdza ograniczenia dotyczące `DBSCHEMA_TABLES` `DBSCHEMA_COLUMNS` zestawów wierszy, i `DBSCHEMA_PROVIDER_TYPES` schematu. Wywołaj tę metodę, aby określić, czy wywołanie odbiorcy `IDBSchemaRowset::GetRowset` jest poprawne. Jeśli chcesz obsługiwać zestawy wierszy schematu inne niż wymienione powyżej, należy utworzyć własną funkcję do wykonania tego zadania.

`CheckRestrictions` Określa, czy odbiorca wywołuje metodę [GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md) z prawidłowym ograniczeniem i poprawnym typem ograniczenia (na przykład VT_BSTR ciągu) obsługiwanego przez dostawcę. Określa również, czy są obsługiwane poprawne liczby ograniczeń. Domyślnie program `CheckRestrictions` poprosił dostawcę za pomocą wywołania [setograniczenia](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) , które ograniczenia obsługuje dla danego zestawu wierszy. Następnie porównuje ograniczenia od konsumenta z tymi obsługiwanymi przez dostawcę i powiedzie się lub zakończy się niepowodzeniem.

Aby uzyskać więcej informacji na temat zestawów wierszy schematu, zobacz [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) w *dokumentacji programisty OLE DB* w Windows SDK.

## <a name="idbschemarowsetimplcreateschemarowset"></a><a name="createschemarowset"></a> IDBSchemaRowsetImpl:: CreateSchemaRowset

Implementuje funkcję twórcy obiektów COM dla obiektu określonego przez parametr szablonu.

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
podczas Zewnętrzny element [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) podczas agregowania, w przeciwnym razie wartość null.

*cRestrictions*<br/>
podczas Liczba ograniczeń zastosowanych do zestawu wierszy schematu.

*rgRestrictions*<br/>
podczas Tablica `cRestrictions` **wariantów**, która ma zostać zastosowana do zestawu wierszy.

*riid*<br/>
podczas Interfejs do [QueryInterface](../../atl/queryinterface.md) dla danych wyjściowych `IUnknown` .

*cPropertySets*<br/>
podczas Liczba zestawów właściwości do ustawienia.

*rgPropertySets*<br/>
podczas Tablica struktur [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) , które określają ustawiane właściwości.

*ppRowset*<br/>
określoną Wychodzące `IUnknown` żądanie *riid*. `IUnknown`Jest to interfejs obiektu zestawu wierszy schematu.

*pSchemaRowset*<br/>
określoną Wskaźnik do wystąpienia klasy zestawu wierszy schematu. Zazwyczaj ten parametr nie jest używany, ale może być używany, jeśli trzeba wykonać więcej pracy na zestawie wierszy schematu przed przekazaniem go do obiektu COM. Okres istnienia *pSchemaRowset* jest związany z *ppRowset*.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Ta funkcja implementuje twórcę ogólnego dla wszystkich typów zestawów wierszy schematu. Zazwyczaj użytkownik nie wywołuje tej funkcji. Jest on wywoływany przez implementację mapy schematu.

## <a name="idbschemarowsetimplsetrestrictions"></a><a name="setrestrictions"></a> IDBSchemaRowsetImpl:: setograniczenia

Określa, które ograniczenia są obsługiwane dla określonego zestawu wierszy schematu.

### <a name="syntax"></a>Składnia

```cpp
void SetRestrictions(ULONG cRestrictions,
   GUID* /* rguidSchema */,
   ULONG* rgRestrictions);
```

#### <a name="parameters"></a>Parametry

*cRestrictions*<br/>
podczas Liczba ograniczeń w tablicy *rgRestrictions* i liczba identyfikatorów GUID w tablicy *rguidSchema* .

*rguidSchema*<br/>
podczas Tablica identyfikatorów GUID zestawów wierszy schematu, dla których mają zostać pobrane ograniczenia. Każdy element tablicy zawiera identyfikator GUID jednego zestawu wierszy schematu (na przykład `DBSCHEMA_TABLES` ).

*rgRestrictions*<br/>
podczas Tablica długości *cRestrictions* wartości ograniczeń, które mają zostać ustawione. Każdy element odnosi się do ograniczeń zestawu wierszy schematu identyfikowanych przez identyfikator GUID. Jeśli dany zestaw wierszy schematu nie jest obsługiwany przez dostawcę, element jest ustawiany na zero. W przeciwnym razie wartość **ULONG** zawiera maskę bitową, która reprezentuje ograniczenia obsługiwane przez ten zestaw wierszy schematu. Aby uzyskać więcej informacji o ograniczeniach odnoszących się do określonego zestawu wierszy schematu, zapoznaj się z tabelą identyfikatorów GUID zestawu wierszy schematu w [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) w *odniesieniu do programisty OLE DB* w Windows SDK.

### <a name="remarks"></a>Uwagi

`IDBSchemaRowset`Obiekt wywołuje, `SetRestrictions` Aby określić, które ograniczenia są obsługiwane w konkretnym zestawie wierszy schematu (wywoływane przez [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md) za pomocą wskaźnika ze wskaźnikiem). Ograniczenia umożliwiają konsumentom pobieranie tylko pasujących wierszy (na przykład Znajdź wszystkie kolumny w tabeli "MyTable"). Ograniczenia są opcjonalne i w przypadku, gdy żaden z nich nie jest obsługiwany (wartość domyślna), wszystkie dane są zawsze zwracane.

Domyślna implementacja tej metody ustawia elementy tablicy *rgRestrictions* na 0. Zastąp wartość domyślną w klasie sesji, aby ustawić ograniczenia inne niż domyślne.

Aby uzyskać informacje na temat implementowania obsługi zestawu wierszy schematu, zobacz [Obsługa zestawów wierszy schematu](../../data/oledb/supporting-schema-rowsets.md).

Aby zapoznać się z przykładem dostawcy, który obsługuje zestawy wierszy schematu, zobacz przykład [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) .

Aby uzyskać więcej informacji na temat zestawów wierszy schematu, zobacz [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) w *dokumentacji programisty OLE DB* w Windows SDK.

## <a name="idbschemarowsetimplgetrowset"></a><a name="getrowset"></a> IDBSchemaRowsetImpl:: GetRowset

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
podczas Element zewnętrzny `IUnknown` podczas agregowania; w przeciwnym razie wartość null.

*rguidSchema*<br/>
podczas Odwołanie do żądanego identyfikatora GUID zestawu wierszy schematu (na przykład `DBSCHEMA_TABLES` ).

*cRestrictions*<br/>
podczas Liczba ograniczeń, które mają zostać zastosowane do zestawu wierszy.

*rgRestrictions*<br/>
podczas Tablica `cRestrictions` **wariantów**, która reprezentuje ograniczenia.

*riid*<br/>
podczas Identyfikator IID żądania nowo utworzonego zestawu wierszy schematu.

*cPropertySets*<br/>
podczas Liczba zestawów właściwości do ustawienia.

*rgPropertySets*<br/>
[we/out] Tablica struktur [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) do ustawienia dla nowo utworzonego zestawu wierszy schematu.

*ppRowset*<br/>
określoną Wskaźnik do żądanego interfejsu dla nowo utworzonego zestawu wierszy schematu.

### <a name="remarks"></a>Uwagi

Ta metoda wymaga, aby użytkownik miał mapę schematu w klasie sesji. Przy użyciu informacji o mapie schematu program `GetRowset` tworzy dany obiekt zestawu wierszy, jeśli parametr *rguidSchema* jest równy jednemu z identyfikatorów GUID wpisów mapy. Aby uzyskać opis wpisu mapy, zobacz [SCHEMA_ENTRY](../../data/oledb/schema-entry.md) .

Zobacz [IDBSchemaRowset:: GetRowset](/previous-versions/windows/desktop/ms722634(v=vs.85)) w Windows SDK.

## <a name="idbschemarowsetimplgetschemas"></a><a name="getschemas"></a> IDBSchemaRowsetImpl:: GetSchemas

Zwraca listę zestawów wierszy schematu dostępnych przez [IDBSchemaRowsetImpl:: GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md).

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (GetSchema s )(ULONG * pcSchemas,
   GUID ** prgSchemas,
   ULONG** prgRest);
```

#### <a name="parameters"></a>Parametry

*pcSchemas*<br/>
określoną Wskaźnik do elementu **ULONG** , który jest wypełniony liczbą schematów.

*prgSchemas*<br/>
określoną Wskaźnik do tablicy identyfikatorów GUID, który jest wypełniony wskaźnikiem do tablicy identyfikatorów GUID zestawu wierszy schematu.

*prgRest*<br/>
określoną Wskaźnik do tablicy **ULONG**s, który ma zostać wypełniony tablicą ograniczeń.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca tablicę wszystkich zestawów wierszy schematu obsługiwanych przez dostawcę. Zobacz [IDBSchemaRowset:: GetSchemas](/previous-versions/windows/desktop/ms719605(v=vs.85)) w Windows SDK.

Implementacja tej funkcji wymaga, aby użytkownik miał mapę schematu w klasie sesji. Korzystając z informacji o mapie schematu, reaguje ona na tablicę identyfikatorów GUID dla schematów na mapie. Reprezentuje schematy obsługiwane przez dostawcę.

## <a name="see-also"></a>Zobacz też

[Klasy zestawów wierszy schematu i klasy typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)<br/>
[Obsługa zestawów wierszy schematu](../../data/oledb/supporting-schema-rowsets.md)<br/>
[SCHEMA_ENTRY](../../data/oledb/schema-entry.md)<br/>
[UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider)
