---
title: Makra dla szablonów dostawców OLE DB
ms.date: 02/11/2019
f1_keywords:
- BEGIN_PROPERTY_SET
- BEGIN_PROPERTY_SET_EX
- BEGIN_PROPSET_MAP
- CHAIN_PROPERTY_SET
- END_PROPERTY_SET
- END_PROPSET_MAP
- PROPERTY_INFO_ENTRY
- PROPERTY_INFO_ENTRY_EX
- PROPERTY_INFO_ENTRY_VALUE
- BEGIN_PROVIDER_COLUMN_MAP
- END_PROVIDER_COLUMN_MAP
- PROVIDER_COLUMN_ENTRY
- PROVIDER_COLUMN_ENTRY_FIXED
- PROVIDER_COLUMN_ENTRY_GN
- PROVIDER_COLUMN_ENTRY_LENGTH
- PROVIDER_COLUMN_ENTRY_STR
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH
- PROVIDER_COLUMN_ENTRY_WSTR
- BEGIN_SCHEMA_MAP
- END_SCHEMA_MAP
- SCHEMA_ENTRY
helpviewer_keywords:
- OLE DB provider templates, macros
- macros, OLE DB Provider Templates
- Provider Template macros (OLE DB)
- OLE DB Provider Template macros
- BEGIN_PROPERTY_SET macro
- BEGIN_PROPERTY_SET_EX macro
- BEGIN_PROPSET_MAP macro
- CHAIN_PROPERTY_SET macro
- END_PROPERTY_SET macro
- END_PROPSET_MAP macro
- PROPERTY_INFO_ENTRY macro
- PROPERTY_INFO_ENTRY_EX macro
- PROPERTY_INFO_ENTRY_VALUE macro
- BEGIN_PROVIDER_COLUMN_MAP macro
- END_PROVIDER_COLUMN_MAP macro
- PROVIDER_COLUMN_ENTRY macro
- PROVIDER_COLUMN_ENTRY_FIXED macro
- PROVIDER_COLUMN_ENTRY_GN macro
- PROVIDER_COLUMN_ENTRY_LENGTH macro
- PROVIDER_COLUMN_ENTRY_STR macro
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH macro
- PROVIDER_COLUMN_ENTRY_WSTR macro
- BEGIN_SCHEMA_MAP macro
- END_SCHEMA_MAP macro
- SCHEMA_ENTRY macro
ms.assetid: 909482c5-64ab-4e52-84a9-1c07091db183
ms.openlocfilehash: 2fda4d9f003e84247527d964685e631532d4c366
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210148"
---
# <a name="macros-for-ole-db-provider-templates"></a>Makra dla szablonów dostawców OLE DB

Makra dostawcy szablonów OLE DB oferują funkcje w następujących kategoriach:

## <a name="property-set-map-macros"></a>Makra mapy zestawu właściwości

|||
|-|-|
|[BEGIN_PROPERTY_SET](#begin_property_set)|Oznacza początek zestawu właściwości.|
|[BEGIN_PROPERTY_SET_EX](#begin_property_set_ex)|Oznacza początek zestawu właściwości.|
|[BEGIN_PROPSET_MAP](#begin_propset_map)|Oznacza początek zestawu właściwości, który może być ukryty lub zdefiniowany poza zakresem dostawcy.|
|[CHAIN_PROPERTY_SET](#chain_property_set)|Tworzy łańcuch grup właściwości.|
|[END_PROPERTY_SET](#end_property_set)|Oznacza koniec zestawu właściwości.|
|[END_PROPSET_MAP](#end_propset_map)|Oznacza koniec mapy zestawu właściwości.|
|[PROPERTY_INFO_ENTRY](#property_info_entry)|Ustawia określoną właściwość we właściwości jako wartość domyślną.|
|[PROPERTY_INFO_ENTRY_EX](#property_info_entry_ex)|Ustawia określoną właściwość we właściwości jako wartość dostarczoną przez użytkownika. Umożliwia także ustawianie flag i opcji.|
|[PROPERTY_INFO_ENTRY_VALUE](#property_info_entry_value)|Ustawia określoną właściwość we właściwości jako wartość dostarczoną przez użytkownika.|

## <a name="column-map-macros"></a>Makra mapy kolumn

|||
|-|-|
|[BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)|Oznacza początek wpisów mapowania kolumn dostawcy.|
|[END_PROVIDER_COLUMN_MAP](#end_provider_column_map)|Oznacza koniec wpisów mapowania kolumn dostawcy.|
|[PROVIDER_COLUMN_ENTRY](#provider_column_entry)|Reprezentuje konkretną kolumnę obsługiwaną przez dostawcę.|
|[PROVIDER_COLUMN_ENTRY_FIXED](#provider_column_entry_fixed)|Reprezentuje konkretną kolumnę obsługiwaną przez dostawcę. Można określić typ danych kolumny.|
|[PROVIDER_COLUMN_ENTRY_GN](#provider_column_entry_gn)|Reprezentuje konkretną kolumnę obsługiwaną przez dostawcę. Można określić rozmiar kolumny, typ danych, dokładność, skalę i identyfikator GUID zestawu wierszy schematu.|
|[PROVIDER_COLUMN_ENTRY_LENGTH](#provider_column_entry_length)|Reprezentuje konkretną kolumnę obsługiwaną przez dostawcę. Możesz określić rozmiar kolumny.|
|[PROVIDER_COLUMN_ENTRY_STR](#provider_column_entry_str)|Reprezentuje konkretną kolumnę obsługiwaną przez dostawcę. Przyjęto założenie, że typ kolumny jest ciągiem.|
|[PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](#provider_column_entry_type_length)|Reprezentuje konkretną kolumnę obsługiwaną przez dostawcę. Podobnie jak PROVIDER_COLUMN_ENTRY_LENGTH, ale pozwala także określić typ danych kolumny i rozmiar.|
|[PROVIDER_COLUMN_ENTRY_WSTR](#provider_column_entry_wstr)|Reprezentuje konkretną kolumnę obsługiwaną przez dostawcę. Przyjęto założenie, że typ kolumny jest ciągiem znaków Unicode.|

## <a name="schema-rowset-macros"></a>Makra zestawu wierszy schematu

|||
|-|-|
|[BEGIN_SCHEMA_MAP](#begin_schema_map)|Oznacza początek mapy schematu.|
|[END_SCHEMA_MAP](#end_schema_map)|Oznacza koniec mapy schematu.|
|[SCHEMA_ENTRY](#schema_entry)|Kojarzy identyfikator GUID z klasą.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLDB. h

### <a name="begin_property_set"></a><a name="begin_property_set"></a>BEGIN_PROPERTY_SET

Oznacza początek zestawu właściwości w mapie zestawu właściwości.

#### <a name="syntax"></a>Składnia

```cpp
BEGIN_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>Parametry

*ident*<br/>
podczas Identyfikator GUID właściwości.

#### <a name="example"></a>Przykład

Zobacz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="begin_property_set_ex"></a><a name="begin_property_set_ex"></a>BEGIN_PROPERTY_SET_EX

Oznacza początek zestawu właściwości w mapie zestawu właściwości.

#### <a name="syntax"></a>Składnia

```cpp
BEGIN_PROPERTY_SET_EX(guid, flags)
```

#### <a name="parameters"></a>Parametry

*ident*<br/>
podczas Identyfikator GUID właściwości.

*znaczników*<br/>
podczas UPROPSET_HIDDEN dla dowolnych zestawów właściwości, których nie chcesz ujawniać, lub UPROPSET_PASSTHROUGH, aby uzyskać właściwości, które są zdefiniowane poza zakresem dostawcy.

#### <a name="example"></a>Przykład

Zobacz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="begin_propset_map"></a><a name="begin_propset_map"></a>BEGIN_PROPSET_MAP

Oznacza początek wpisów mapy zestawu właściwości.

#### <a name="syntax"></a>Składnia

```cpp
BEGIN_PROPSET_MAP(Class)
```

#### <a name="parameters"></a>Parametry

*Określonej*<br/>
podczas Klasa, w której określono ten zestaw właściwości. Zestaw właściwości można określić w następujących OLE DB obiektów:

- [Obiekty źródła danych](/previous-versions/windows/desktop/ms721278(v=vs.85))

- [Obiekty sesji](/previous-versions/windows/desktop/ms711572(v=vs.85))

- [Polecenia](/previous-versions/windows/desktop/ms724608(v=vs.85))

#### <a name="example"></a>Przykład

Oto przykładowa Mapa zestawu właściwości:

[!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/cpp/begin-propset-map_1.h)]

### <a name="chain_property_set"></a><a name="chain_property_set"></a>CHAIN_PROPERTY_SET

To makro umożliwia łączenie grup właściwości.

#### <a name="syntax"></a>Składnia

```cpp
CHAIN_PROPERTY_SET(ChainClass)
```

#### <a name="parameters"></a>Parametry

*ChainClass*<br/>
podczas Nazwa klasy, dla której mają zostać wyszukane właściwości. Jest to Klasa wygenerowana przez Kreatora projektu ATL, który zawiera już mapę (taką jak sesja, polecenie lub Klasa obiektu źródła danych).

#### <a name="remarks"></a>Uwagi

Można utworzyć łańcuch zestawu właściwości z innej klasy do własnej klasy, a następnie uzyskać dostęp do właściwości bezpośrednio z klasy.

> [!CAUTION]
>  Używaj tego makra oszczędnie. Niewłaściwe użycie może spowodować niepowodzenie przez konsumenta testów zgodności OLE DB.

### <a name="end_property_set"></a><a name="end_property_set"></a>END_PROPERTY_SET

Oznacza koniec zestawu właściwości.

#### <a name="syntax"></a>Składnia

```cpp
END_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>Parametry

*ident*<br/>
podczas Identyfikator GUID właściwości.

#### <a name="example"></a>Przykład

Zobacz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="end_propset_map"></a><a name="end_propset_map"></a>END_PROPSET_MAP

Oznacza koniec wpisów mapy zestawu właściwości.

#### <a name="syntax"></a>Składnia

```cpp
END_PROPSET_MAP()
```

#### <a name="example"></a>Przykład

Zobacz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="property_info_entry"></a><a name="property_info_entry"></a>PROPERTY_INFO_ENTRY

Reprezentuje określoną właściwość w zestawie właściwości.

#### <a name="syntax"></a>Składnia

```cpp
PROPERTY_INFO_ENTRY(dwPropID)
```

#### <a name="parameters"></a>Parametry

*dwPropID*<br/>
podczas Wartość [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) , która może być używana w połączeniu z identyfikatorem GUID zestawu właściwości do identyfikowania właściwości.

#### <a name="remarks"></a>Uwagi

To makro ustawia wartość właściwości typu `DWORD` na wartość domyślną zdefiniowaną w ATLDB. C. Aby ustawić właściwość na wybraną wartość, użyj [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md). Aby ustawić `VARTYPE` i [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85)) dla właściwości w tym samym czasie, użyj [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).

#### <a name="example"></a>Przykład

Zobacz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="property_info_entry_ex"></a><a name="property_info_entry_ex"></a>PROPERTY_INFO_ENTRY_EX

Reprezentuje określoną właściwość w zestawie właściwości.

#### <a name="syntax"></a>Składnia

```cpp
PROPERTY_INFO_ENTRY_EX(dwPropID, vt, dwFlags, value, options)
```

#### <a name="parameters"></a>Parametry

*dwPropID*<br/>
podczas Wartość [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) , która może być używana w połączeniu z identyfikatorem GUID zestawu właściwości do identyfikowania właściwości.

*VT*<br/>
podczas `VARTYPE` tego wpisu właściwości. (Zdefiniowane w wtypes. h)

*flagiDW*<br/>
podczas Wartość [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85)) opisująca ten wpis właściwości.

*value*<br/>
podczas Wartość właściwości typu `DWORD`.

*Opcje*<br/>
DBPROPOPTIONS_REQUIRED lub DBPROPOPTIONS_SETIFCHEAP. Zwykle dostawca nie musi ustawiać *opcji* , ponieważ jest ustawiony przez konsumenta.

#### <a name="remarks"></a>Uwagi

Za pomocą tego makra można bezpośrednio określić wartość właściwości typu `DWORD`, a także opcje i flagi. Aby tylko ustawić właściwość na wartość domyślną zdefiniowaną w ATLDB. H, użyj [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Aby ustawić właściwość na wybraną wartość, bez ustawiania dla niej opcji lub flag, użyj [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md).

#### <a name="example"></a>Przykład

Zobacz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="property_info_entry_value"></a><a name="property_info_entry_value"></a>PROPERTY_INFO_ENTRY_VALUE

Reprezentuje określoną właściwość w zestawie właściwości.

#### <a name="syntax"></a>Składnia

```cpp
PROPERTY_INFO_ENTRY_VALUE(dwPropID, value)
```

#### <a name="parameters"></a>Parametry

*dwPropID*<br/>
podczas Wartość [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) , która może być używana w połączeniu z identyfikatorem GUID zestawu właściwości do identyfikowania właściwości.

*value*<br/>
podczas Wartość właściwości typu `DWORD`.

#### <a name="remarks"></a>Uwagi

Za pomocą tego makra można bezpośrednio określić wartość właściwości typu `DWORD`. Aby ustawić wartość domyślną dla właściwości zdefiniowanej w ATLDB. H, użyj [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Aby ustawić wartość, flagi i opcje właściwości, użyj [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).

#### <a name="example"></a>Przykład

Zobacz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="begin_provider_column_map"></a><a name="begin_provider_column_map"></a>BEGIN_PROVIDER_COLUMN_MAP

Oznacza początek wpisów mapowania kolumn dostawcy.

#### <a name="syntax"></a>Składnia

```cpp
BEGIN_PROVIDER_COLUMN_MAP(theClass)
```

#### <a name="parameters"></a>Parametry

*theClass*<br/>
podczas Nazwa klasy, do której należy ta mapa.

#### <a name="example"></a>Przykład

Oto przykładowa Mapa kolumn dostawcy:

[!code-cpp[NVC_OLEDB_Provider#4](../../data/oledb/codesnippet/cpp/begin-provider-column-map_1.h)]

### <a name="end_provider_column_map"></a><a name="end_provider_column_map"></a>END_PROVIDER_COLUMN_MAP

Oznacza koniec wpisów mapowania kolumn dostawcy.

#### <a name="syntax"></a>Składnia

```cpp
END_PROVIDER_COLUMN_MAP()
```

#### <a name="example"></a>Przykład

Zobacz [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry"></a><a name="provider_column_entry"></a>PROVIDER_COLUMN_ENTRY

Reprezentuje konkretną kolumnę obsługiwaną przez dostawcę.

#### <a name="syntax"></a>Składnia

```cpp
PROVIDER_COLUMN_ENTRY (name, ordinal, member)
```

#### <a name="parameters"></a>Parametry

*Nazwij*<br/>
podczas Nazwa kolumny.

*liczbą*<br/>
podczas Numer kolumny. Jeśli kolumna nie jest kolumną zakładki, numer kolumny nie może być równy 0.

*członkiem*<br/>
podczas Zmienna członkowska w `dataClass` odpowiadająca kolumnie.

### <a name="provider_column_entry_fixed"></a><a name="provider_column_entry_fixed"></a>PROVIDER_COLUMN_ENTRY_FIXED

Reprezentuje konkretną kolumnę obsługiwaną przez dostawcę.

#### <a name="syntax"></a>Składnia

```cpp
PROVIDER_COLUMN_ENTRY_FIXED(name, ordinal, dbtype, member)
```

#### <a name="parameters"></a>Parametry

*Nazwij*<br/>
podczas Nazwa kolumny.

*liczbą*<br/>
podczas Numer kolumny. Jeśli kolumna nie jest kolumną zakładki, numer kolumny nie może być równy 0.

*DbType*<br/>
podczas Typ danych w elemencie [DbType](/previous-versions/windows/desktop/ms711251(v=vs.85)).

*członkiem*<br/>
podczas Zmienna członkowska w `dataClass`, która przechowuje dane.

#### <a name="remarks"></a>Uwagi

Pozwala określić typ danych kolumny.

#### <a name="example"></a>Przykład

Zobacz [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry_gn"></a><a name="provider_column_entry_gn"></a>PROVIDER_COLUMN_ENTRY_GN

Reprezentuje konkretną kolumnę obsługiwaną przez dostawcę.

#### <a name="syntax"></a>Składnia

```cpp
PROVIDER_COLUMN_ENTRY_GN (name, ordinal, flags, colSize, dbtype, precision, scale, guid)
```

#### <a name="parameters"></a>Parametry

*Nazwij*<br/>
podczas Nazwa kolumny.

*liczbą*<br/>
podczas Numer kolumny. Jeśli kolumna nie jest kolumną zakładki, numer kolumny nie może być równy 0.

*znaczników*<br/>
podczas Określa sposób, w jaki dane są zwracane. Zobacz opis `dwFlags` w [strukturach DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*colSize*<br/>
podczas Rozmiar kolumny.

*DbType*<br/>
podczas Wskazuje typ danych wartości. Zobacz opis `wType` w [strukturach DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*dokładne*<br/>
podczas Wskazuje precyzję, która ma być używana podczas pobierania danych, jeśli *DbType* jest DBTYPE_NUMERIC lub DBTYPE_DECIMAL. Zobacz opis `bPrecision` w [strukturach DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*zasięgu*<br/>
podczas Wskazuje skalę używaną podczas pobierania danych, jeśli dbType jest DBTYPE_NUMERIC lub DBTYPE_DECIMAL. Zobacz opis `bScale` w [strukturach DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*ident*<br/>
Identyfikator GUID zestawu wierszy schematu. Aby uzyskać listę zestawów wierszy schematu i ich identyfikatorów GUID, zobacz [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) w *dokumentacji programisty programu OLE DB* .

#### <a name="remarks"></a>Uwagi

Pozwala określić rozmiar kolumny, typ danych, dokładność, skalę i identyfikator GUID zestawu wierszy schematu.

### <a name="provider_column_entry_length"></a><a name="provider_column_entry_length"></a>PROVIDER_COLUMN_ENTRY_LENGTH

Reprezentuje konkretną kolumnę obsługiwaną przez dostawcę.

#### <a name="syntax"></a>Składnia

```cpp
PROVIDER_COLUMN_ENTRY_LENGTH(name, ordinal, size, member)
```

#### <a name="parameters"></a>Parametry

*Nazwij*<br/>
podczas Nazwa kolumny.

*liczbą*<br/>
podczas Numer kolumny. Jeśli kolumna nie jest kolumną zakładki, numer kolumny nie może być równy 0.

*zmienia*<br/>
podczas Rozmiar kolumny w bajtach.

*członkiem*<br/>
podczas Zmienna członkowska w `dataClass`, która przechowuje dane kolumn.

#### <a name="remarks"></a>Uwagi

Pozwala określić rozmiar kolumny.

#### <a name="example"></a>Przykład

Zobacz [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry_str"></a><a name="provider_column_entry_str"></a>PROVIDER_COLUMN_ENTRY_STR

Reprezentuje konkretną kolumnę obsługiwaną przez dostawcę.

#### <a name="syntax"></a>Składnia

```cpp
PROVIDER_COLUMN_ENTRY_STR(name, ordinal, member)
```

#### <a name="parameters"></a>Parametry

*Nazwij*<br/>
podczas Nazwa kolumny.

*liczbą*<br/>
podczas Numer kolumny. Jeśli kolumna nie jest kolumną zakładki, numer kolumny nie może być równy 0.

*członkiem*<br/>
podczas Zmienna członkowska w klasie danych, która przechowuje dane.

#### <a name="remarks"></a>Uwagi

Użyj tego makra, gdy przyjmuje się, że dane kolumny mają być [DBTYPE_STR](/previous-versions/windows/desktop/ms711251(v=vs.85)).

#### <a name="example"></a>Przykład

Zobacz [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry_type_length"></a><a name="provider_column_entry_type_length"></a>PROVIDER_COLUMN_ENTRY_TYPE_LENGTH

Reprezentuje konkretną kolumnę obsługiwaną przez dostawcę.

#### <a name="syntax"></a>Składnia

```cpp
PROVIDER_COLUMN_ENTRY_TYPE_LENGTH(name, ordinal, dbtype, size, member)
```

#### <a name="parameters"></a>Parametry

*Nazwij*<br/>
podczas Nazwa kolumny.

*liczbą*<br/>
podczas Numer kolumny. Jeśli kolumna nie jest kolumną zakładki, numer kolumny nie może być równy 0.

*DbType*<br/>
podczas Typ danych w elemencie [DbType](/previous-versions/windows/desktop/ms711251(v=vs.85)).

*zmienia*<br/>
podczas Rozmiar kolumny w bajtach.

*członkiem*<br/>
podczas Zmienna członkowska w klasie danych, która przechowuje dane.

#### <a name="remarks"></a>Uwagi

Podobnie jak w przypadku [PROVIDER_COLUMN_ENTRY_LENGTH](../../data/oledb/provider-column-entry-length.md) , ale pozwala także określić typ danych kolumny i rozmiar.

### <a name="provider_column_entry_wstr"></a><a name="provider_column_entry_wstr"></a>PROVIDER_COLUMN_ENTRY_WSTR

Reprezentuje konkretną kolumnę obsługiwaną przez dostawcę.

#### <a name="syntax"></a>Składnia

```cpp
PROVIDER_COLUMN_ENTRY_WSTR(name, ordinal, member)
```

#### <a name="parameters"></a>Parametry

*Nazwij*<br/>
podczas Nazwa kolumny.

*liczbą*<br/>
podczas Numer kolumny. Jeśli kolumna nie jest kolumną zakładki, numer kolumny nie może być równy 0.

*członkiem*<br/>
podczas Zmienna członkowska w klasie danych, która przechowuje dane.

#### <a name="remarks"></a>Uwagi

To makro jest używane, gdy dane kolumny są zakończono wartością null ciągu znaków Unicode, [DBTYPE_WSTR](/previous-versions/windows/desktop/ms711251(v=vs.85)).

### <a name="begin_schema_map"></a><a name="begin_schema_map"></a>BEGIN_SCHEMA_MAP

Wskazuje początek mapy schematu.

#### <a name="syntax"></a>Składnia

```cpp
BEGIN_SCHEMA_MAP(SchemaClass);
```

#### <a name="parameters"></a>Parametry

*SchemaClass*<br/>
Klasa, która zawiera mapę. Zwykle jest to Klasa sesji.

#### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat zestawów wierszy schematu, zobacz [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) w Windows SDK.

### <a name="end_schema_map"></a><a name="end_schema_map"></a>END_SCHEMA_MAP

Wskazuje koniec mapy schematu.

#### <a name="syntax"></a>Składnia

```cpp
END_SCHEMA_MAP()
```

#### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Klasa IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md).

### <a name="schema_entry"></a><a name="schema_entry"></a>SCHEMA_ENTRY

Kojarzy identyfikator GUID z klasą.

#### <a name="syntax"></a>Składnia

```cpp
SCHEMA_ENTRY(guid,
   rowsetClass);
```

#### <a name="parameters"></a>Parametry

*ident*<br/>
Identyfikator GUID zestawu wierszy schematu. Aby uzyskać listę zestawów wierszy schematu i ich identyfikatorów GUID, zobacz [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) w *dokumentacji programisty programu OLE DB* .

*rowsetClass*<br/>
Klasa, która zostanie utworzona w celu reprezentowania zestawu wierszy schematu.

#### <a name="remarks"></a>Uwagi

[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) może następnie wykonać zapytanie dotyczące mapy dla listy identyfikatorów GUID lub utworzyć zestaw wierszy, jeśli ma on identyfikator GUID. Zestaw wierszy schematu `IDBSchemaRowsetImpl` tworzony jest podobny do standardowej klasy `CRowsetImpl`-pochodnej, z tą różnicą, że musi dostarczyć metodę `Execute`, która ma następujący podpis:

```cpp
HRESULT Execute (LONG* pcRowsAffected,
    ULONG cRestrictions,
    const VARIANT* rgRestrictions);
```

Ta funkcja `Execute` wypełnia dane zestawu wierszy. Kreator projektu ATL tworzy, zgodnie z opisem w [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) OLE DB w *dokumentacji programisty*, trzy początkowe zestawy wierszy schematu w projekcie dla każdego z trzech obowiązkowych schematów OLE DB:

- DBSCHEMA_TABLES

- DBSCHEMA_COLUMNS

- DBSCHEMA_PROVIDER_TYPES

Kreator dodaje również trzy odpowiednie wpisy do mapy schematów. Aby uzyskać więcej informacji na temat tworzenia dostawcy, zobacz [Tworzenie dostawcy szablonów OLE DB](../../data/oledb/creating-an-ole-db-provider.md) .

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)<br/>
[Szablony dostawców OLE DB — dokumentacja](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[Makra dla szablonów dostawców OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)
