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
ms.openlocfilehash: 5d29b2548102b056a21ebfccb037af3a766788ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369808"
---
# <a name="macros-for-ole-db-provider-templates"></a>Makra dla szablonów dostawców OLE DB

Makra dostawcy szablonów OLE DB oferują funkcje w następujących kategoriach:

## <a name="property-set-map-macros"></a>Makra mapy zestawu właściwości

|||
|-|-|
|[BEGIN_PROPERTY_SET](#begin_property_set)|Oznacza początek zestawu właściwości.|
|[BEGIN_PROPERTY_SET_EX](#begin_property_set_ex)|Oznacza początek zestawu właściwości.|
|[BEGIN_PROPSET_MAP](#begin_propset_map)|Oznacza początek zestawu właściwości, które mogą być ukryte lub zdefiniowane poza zakresem dostawcy.|
|[CHAIN_PROPERTY_SET](#chain_property_set)|Łańcuchy grup właściwości razem.|
|[END_PROPERTY_SET](#end_property_set)|Oznacza koniec zestawu właściwości.|
|[END_PROPSET_MAP](#end_propset_map)|Oznacza koniec mapy zestawu właściwości.|
|[PROPERTY_INFO_ENTRY](#property_info_entry)|Ustawia określoną właściwość we właściwości ustawionej na wartość domyślną.|
|[PROPERTY_INFO_ENTRY_EX](#property_info_entry_ex)|Ustawia określoną właściwość w zestawie właściwości na wartość dostarczoną przez Ciebie. Umożliwia również ustawienie flag i opcji.|
|[PROPERTY_INFO_ENTRY_VALUE](#property_info_entry_value)|Ustawia określoną właściwość w zestawie właściwości na wartość dostarczoną przez Ciebie.|

## <a name="column-map-macros"></a>Makra mapy kolumn

|||
|-|-|
|[BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)|Oznacza początek wpisów mapy kolumny dostawcy.|
|[END_PROVIDER_COLUMN_MAP](#end_provider_column_map)|Oznacza koniec wpisów mapy kolumny dostawcy.|
|[PROVIDER_COLUMN_ENTRY](#provider_column_entry)|Reprezentuje określoną kolumnę obsługiwaną przez dostawcę.|
|[PROVIDER_COLUMN_ENTRY_FIXED](#provider_column_entry_fixed)|Reprezentuje określoną kolumnę obsługiwaną przez dostawcę. Można określić typ danych kolumny.|
|[PROVIDER_COLUMN_ENTRY_GN](#provider_column_entry_gn)|Reprezentuje określoną kolumnę obsługiwaną przez dostawcę. Można określić identyfikator GUID rozmiaru, typu danych, precyzji, skali i zestawu wierszy schematu.|
|[PROVIDER_COLUMN_ENTRY_LENGTH](#provider_column_entry_length)|Reprezentuje określoną kolumnę obsługiwaną przez dostawcę. Można określić rozmiar kolumny.|
|[PROVIDER_COLUMN_ENTRY_STR](#provider_column_entry_str)|Reprezentuje określoną kolumnę obsługiwaną przez dostawcę. Przyjęto założenie, że typ kolumny jest ciągiem.|
|[PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](#provider_column_entry_type_length)|Reprezentuje określoną kolumnę obsługiwaną przez dostawcę. Podobnie jak PROVIDER_COLUMN_ENTRY_LENGTH, ale umożliwia również określenie typu danych kolumny, a także rozmiaru.|
|[PROVIDER_COLUMN_ENTRY_WSTR](#provider_column_entry_wstr)|Reprezentuje określoną kolumnę obsługiwaną przez dostawcę. Przyjęto założenie, że typ kolumny jest ciągiem znaków Unicode.|

## <a name="schema-rowset-macros"></a>Makra wiersza schematu

|||
|-|-|
|[BEGIN_SCHEMA_MAP](#begin_schema_map)|Oznacza początek mapy schematu.|
|[END_SCHEMA_MAP](#end_schema_map)|Oznacza koniec mapy schematu.|
|[SCHEMA_ENTRY](#schema_entry)|Kojarzy identyfikator GUID z klasą.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldb.h

### <a name="begin_property_set"></a><a name="begin_property_set"></a>BEGIN_PROPERTY_SET

Oznacza początek właściwości ustawionej na mapie zestawu właściwości.

#### <a name="syntax"></a>Składnia

```cpp
BEGIN_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>Parametry

*Identyfikator guid*<br/>
[w] Identyfikator GUID właściwości.

#### <a name="example"></a>Przykład

Zobacz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="begin_property_set_ex"></a><a name="begin_property_set_ex"></a>BEGIN_PROPERTY_SET_EX

Oznacza początek właściwości ustawionej na mapie zestawu właściwości.

#### <a name="syntax"></a>Składnia

```cpp
BEGIN_PROPERTY_SET_EX(guid, flags)
```

#### <a name="parameters"></a>Parametry

*Identyfikator guid*<br/>
[w] Identyfikator GUID właściwości.

*flagi*<br/>
[w] UPROPSET_HIDDEN dla wszystkich zestawów właściwości, które nie chcesz udostępniać, lub UPROPSET_PASSTHROUGH dla dostawcy ujawniającego właściwości zdefiniowane poza zakresem dostawcy.

#### <a name="example"></a>Przykład

Zobacz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="begin_propset_map"></a><a name="begin_propset_map"></a>BEGIN_PROPSET_MAP

Oznacza początek wpisów mapy zestawu właściwości.

#### <a name="syntax"></a>Składnia

```cpp
BEGIN_PROPSET_MAP(Class)
```

#### <a name="parameters"></a>Parametry

*Klasa*<br/>
[w] Klasa, w której określono ten zestaw właściwości. Zestaw właściwości można określić w następujących obiektach OLE DB:

- [Obiekty źródła danych](/previous-versions/windows/desktop/ms721278(v=vs.85))

- [Obiekty sesji](/previous-versions/windows/desktop/ms711572(v=vs.85))

- [Polecenia](/previous-versions/windows/desktop/ms724608(v=vs.85))

#### <a name="example"></a>Przykład

Oto przykładowa mapa zestawu właściwości:

[!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/cpp/begin-propset-map_1.h)]

### <a name="chain_property_set"></a><a name="chain_property_set"></a>CHAIN_PROPERTY_SET

To makro grupuje właściwości razem.

#### <a name="syntax"></a>Składnia

```cpp
CHAIN_PROPERTY_SET(ChainClass)
```

#### <a name="parameters"></a>Parametry

*Klasa łańcucha*<br/>
[w] Nazwa klasy do właściwości łańcucha dla. Jest to klasa generowana przez Kreatora projektu ATL, która zawiera już mapę (na przykład klasę obiektu sesyjnego, polecenia lub obiektu źródła danych).

#### <a name="remarks"></a>Uwagi

Można łańcuch zestaw właściwości z innej klasy do własnej klasy, a następnie uzyskać dostęp do właściwości bezpośrednio z klasy.

> [!CAUTION]
> Użyj tego makra oszczędnie. Niewłaściwe użycie może spowodować, że konsument nie testów zgodności OLE DB.

### <a name="end_property_set"></a><a name="end_property_set"></a>END_PROPERTY_SET

Oznacza koniec zestawu właściwości.

#### <a name="syntax"></a>Składnia

```cpp
END_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>Parametry

*Identyfikator guid*<br/>
[w] Identyfikator GUID właściwości.

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

*dwPropID (dwPropID)*<br/>
[w] Wartość [DBPROPID,](/previous-versions/windows/desktop/ms723882(v=vs.85)) która może być używana w połączeniu z identyfikatorem GUID zestawu właściwości do identyfikowania właściwości.

#### <a name="remarks"></a>Uwagi

To makro ustawia wartość `DWORD` właściwości typu na wartość domyślną zdefiniowaną w atldb. H. Aby ustawić właściwość na wybraną wartość, użyj [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md). Aby ustawić `VARTYPE` i [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85)) dla właściwości w tym samym czasie, należy użyć [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).

#### <a name="example"></a>Przykład

Zobacz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="property_info_entry_ex"></a><a name="property_info_entry_ex"></a>PROPERTY_INFO_ENTRY_EX

Reprezentuje określoną właściwość w zestawie właściwości.

#### <a name="syntax"></a>Składnia

```cpp
PROPERTY_INFO_ENTRY_EX(dwPropID, vt, dwFlags, value, options)
```

#### <a name="parameters"></a>Parametry

*dwPropID (dwPropID)*<br/>
[w] Wartość [DBPROPID,](/previous-versions/windows/desktop/ms723882(v=vs.85)) która może być używana w połączeniu z identyfikatorem GUID zestawu właściwości do identyfikowania właściwości.

*Vt*<br/>
[w] Ten `VARTYPE` wpis właściwości. (Zdefiniowane w wtypes.h)

*Dwflags*<br/>
[w] Wartość [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85)) opisująca ten wpis właściwości.

*value*<br/>
[w] Wartość właściwości typu `DWORD`.

*Opcje*<br/>
DBPROPOPTIONS_REQUIRED lub DBPROPOPTIONS_SETIFCHEAP. Zwykle dostawca nie musi ustawiać *opcji,* ponieważ jest on ustawiany przez konsumenta.

#### <a name="remarks"></a>Uwagi

Za pomocą tego makra można bezpośrednio określić wartość właściwości typu, `DWORD` a także opcje i flagi. Aby jedynie ustawić właściwość na wartość domyślną zdefiniowaną w ATLDB. H, użyj [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Aby ustawić właściwość na wybraną wartość, bez ustawiania opcji lub flag, użyj [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md).

#### <a name="example"></a>Przykład

Zobacz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="property_info_entry_value"></a><a name="property_info_entry_value"></a>PROPERTY_INFO_ENTRY_VALUE

Reprezentuje określoną właściwość w zestawie właściwości.

#### <a name="syntax"></a>Składnia

```cpp
PROPERTY_INFO_ENTRY_VALUE(dwPropID, value)
```

#### <a name="parameters"></a>Parametry

*dwPropID (dwPropID)*<br/>
[w] Wartość [DBPROPID,](/previous-versions/windows/desktop/ms723882(v=vs.85)) która może być używana w połączeniu z identyfikatorem GUID zestawu właściwości do identyfikowania właściwości.

*value*<br/>
[w] Wartość właściwości typu `DWORD`.

#### <a name="remarks"></a>Uwagi

Za pomocą tego makra można bezpośrednio określić wartość właściwości typu `DWORD`. Aby ustawić właściwość na wartość domyślną zdefiniowaną w ATLDB. H, użyj [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Aby ustawić wartość, flagi i opcje właściwości, użyj [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).

#### <a name="example"></a>Przykład

Zobacz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="begin_provider_column_map"></a><a name="begin_provider_column_map"></a>BEGIN_PROVIDER_COLUMN_MAP

Oznacza początek wpisów mapy kolumny dostawcy.

#### <a name="syntax"></a>Składnia

```cpp
BEGIN_PROVIDER_COLUMN_MAP(theClass)
```

#### <a name="parameters"></a>Parametry

*klasa*<br/>
[w] Nazwa klasy, do której należy mapa.

#### <a name="example"></a>Przykład

Oto przykładowa mapa kolumn dostawcy:

[!code-cpp[NVC_OLEDB_Provider#4](../../data/oledb/codesnippet/cpp/begin-provider-column-map_1.h)]

### <a name="end_provider_column_map"></a><a name="end_provider_column_map"></a>END_PROVIDER_COLUMN_MAP

Oznacza koniec wpisów mapy kolumny dostawcy.

#### <a name="syntax"></a>Składnia

```cpp
END_PROVIDER_COLUMN_MAP()
```

#### <a name="example"></a>Przykład

Zobacz [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry"></a><a name="provider_column_entry"></a>PROVIDER_COLUMN_ENTRY

Reprezentuje określoną kolumnę obsługiwaną przez dostawcę.

#### <a name="syntax"></a>Składnia

```cpp
PROVIDER_COLUMN_ENTRY (name, ordinal, member)
```

#### <a name="parameters"></a>Parametry

*Nazwa*<br/>
[w] Nazwa kolumny.

*Porządkowych*<br/>
[w] Numer kolumny. Jeśli kolumna nie jest kolumną Zakładka, numer kolumny nie może wynosić 0.

*Członkowskich*<br/>
[w] Zmienna elementu `dataClass` członkowskiego odpowiadająca kolumnie.

### <a name="provider_column_entry_fixed"></a><a name="provider_column_entry_fixed"></a>PROVIDER_COLUMN_ENTRY_FIXED

Reprezentuje określoną kolumnę obsługiwaną przez dostawcę.

#### <a name="syntax"></a>Składnia

```cpp
PROVIDER_COLUMN_ENTRY_FIXED(name, ordinal, dbtype, member)
```

#### <a name="parameters"></a>Parametry

*Nazwa*<br/>
[w] Nazwa kolumny.

*Porządkowych*<br/>
[w] Numer kolumny. Jeśli kolumna nie jest kolumną Zakładka, numer kolumny nie może wynosić 0.

*Dbtype*<br/>
[w] Typ danych w [DBTYPE](/previous-versions/windows/desktop/ms711251(v=vs.85)).

*Członkowskich*<br/>
[w] Zmienna elementu `dataClass` członkowskiego w tym przechowuje dane.

#### <a name="remarks"></a>Uwagi

Umożliwia określenie typu danych kolumny.

#### <a name="example"></a>Przykład

Zobacz [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry_gn"></a><a name="provider_column_entry_gn"></a>PROVIDER_COLUMN_ENTRY_GN

Reprezentuje określoną kolumnę obsługiwaną przez dostawcę.

#### <a name="syntax"></a>Składnia

```cpp
PROVIDER_COLUMN_ENTRY_GN (name, ordinal, flags, colSize, dbtype, precision, scale, guid)
```

#### <a name="parameters"></a>Parametry

*Nazwa*<br/>
[w] Nazwa kolumny.

*Porządkowych*<br/>
[w] Numer kolumny. Jeśli kolumna nie jest kolumną Zakładka, numer kolumny nie może wynosić 0.

*flagi*<br/>
[w] Określa sposób zwracania danych. Zobacz `dwFlags` opis w [DBBINDING Structures](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*colSize (rozmiar)*<br/>
[w] Rozmiar kolumny.

*Dbtype*<br/>
[w] Wskazuje typ danych wartości. Zobacz `wType` opis w [DBBINDING Structures](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*Precyzji*<br/>
[w] Wskazuje dokładność do użycia podczas uzyskiwania danych, jeśli *dbType* jest DBTYPE_NUMERIC lub DBTYPE_DECIMAL. Zobacz `bPrecision` opis w [DBBINDING Structures](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*Skali*<br/>
[w] Wskazuje skalę, która ma być używana podczas uzyskiwania danych, jeśli dbType jest DBTYPE_NUMERIC lub DBTYPE_DECIMAL. Zobacz `bScale` opis w [DBBINDING Structures](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*Identyfikator guid*<br/>
Identyfikator GUID zestawu wierszy schematu. Zobacz [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) w *ole DB Programator odwołania* listy zestawów wierszy schematu i ich identyfikatorów GUID.

#### <a name="remarks"></a>Uwagi

Umożliwia określenie identyfikatora GUID rozmiaru, typu danych, precyzji, skali i zestawu wierszy schematu.

### <a name="provider_column_entry_length"></a><a name="provider_column_entry_length"></a>PROVIDER_COLUMN_ENTRY_LENGTH

Reprezentuje określoną kolumnę obsługiwaną przez dostawcę.

#### <a name="syntax"></a>Składnia

```cpp
PROVIDER_COLUMN_ENTRY_LENGTH(name, ordinal, size, member)
```

#### <a name="parameters"></a>Parametry

*Nazwa*<br/>
[w] Nazwa kolumny.

*Porządkowych*<br/>
[w] Numer kolumny. Jeśli kolumna nie jest kolumną Zakładka, numer kolumny nie może wynosić 0.

*Rozmiar*<br/>
[w] Rozmiar kolumny w bajtach.

*Członkowskich*<br/>
[w] Zmienna elementu `dataClass` członkowskiego w tym przechowuje dane kolumny.

#### <a name="remarks"></a>Uwagi

Umożliwia określenie rozmiaru kolumny.

#### <a name="example"></a>Przykład

Zobacz [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry_str"></a><a name="provider_column_entry_str"></a>PROVIDER_COLUMN_ENTRY_STR

Reprezentuje określoną kolumnę obsługiwaną przez dostawcę.

#### <a name="syntax"></a>Składnia

```cpp
PROVIDER_COLUMN_ENTRY_STR(name, ordinal, member)
```

#### <a name="parameters"></a>Parametry

*Nazwa*<br/>
[w] Nazwa kolumny.

*Porządkowych*<br/>
[w] Numer kolumny. Jeśli kolumna nie jest kolumną Zakładka, numer kolumny nie może wynosić 0.

*Członkowskich*<br/>
[w] Zmienna elementu członkowskiego w klasie danych, która przechowuje dane.

#### <a name="remarks"></a>Uwagi

Użyj tego makra, gdy przyjmuje się, że dane kolumny [są DBTYPE_STR](/previous-versions/windows/desktop/ms711251(v=vs.85)).

#### <a name="example"></a>Przykład

Zobacz [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry_type_length"></a><a name="provider_column_entry_type_length"></a>PROVIDER_COLUMN_ENTRY_TYPE_LENGTH

Reprezentuje określoną kolumnę obsługiwaną przez dostawcę.

#### <a name="syntax"></a>Składnia

```cpp
PROVIDER_COLUMN_ENTRY_TYPE_LENGTH(name, ordinal, dbtype, size, member)
```

#### <a name="parameters"></a>Parametry

*Nazwa*<br/>
[w] Nazwa kolumny.

*Porządkowych*<br/>
[w] Numer kolumny. Jeśli kolumna nie jest kolumną Zakładka, numer kolumny nie może wynosić 0.

*Dbtype*<br/>
[w] Typ danych w [DBTYPE](/previous-versions/windows/desktop/ms711251(v=vs.85)).

*Rozmiar*<br/>
[w] Rozmiar kolumny w bajtach.

*Członkowskich*<br/>
[w] Zmienna elementu członkowskiego w klasie danych, która przechowuje dane.

#### <a name="remarks"></a>Uwagi

Podobnie [jak PROVIDER_COLUMN_ENTRY_LENGTH](../../data/oledb/provider-column-entry-length.md) ale umożliwia również określenie typu danych kolumny, a także rozmiaru.

### <a name="provider_column_entry_wstr"></a><a name="provider_column_entry_wstr"></a>PROVIDER_COLUMN_ENTRY_WSTR

Reprezentuje określoną kolumnę obsługiwaną przez dostawcę.

#### <a name="syntax"></a>Składnia

```cpp
PROVIDER_COLUMN_ENTRY_WSTR(name, ordinal, member)
```

#### <a name="parameters"></a>Parametry

*Nazwa*<br/>
[w] Nazwa kolumny.

*Porządkowych*<br/>
[w] Numer kolumny. Jeśli kolumna nie jest kolumną Zakładka, numer kolumny nie może wynosić 0.

*Członkowskich*<br/>
[w] Zmienna elementu członkowskiego w klasie danych, która przechowuje dane.

#### <a name="remarks"></a>Uwagi

Użyj tego makra, gdy dane kolumny są ciągiem znaków Unicode zakończonym wartością null, [DBTYPE_WSTR](/previous-versions/windows/desktop/ms711251(v=vs.85)).

### <a name="begin_schema_map"></a><a name="begin_schema_map"></a>BEGIN_SCHEMA_MAP

Oznacza początek mapy schematu.

#### <a name="syntax"></a>Składnia

```cpp
BEGIN_SCHEMA_MAP(SchemaClass);
```

#### <a name="parameters"></a>Parametry

*Klasa schematu*<br/>
Klasa, która zawiera MAP. Zazwyczaj będzie to klasa sesji.

#### <a name="remarks"></a>Uwagi

Zobacz [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) w zestawie Windows SDK, aby uzyskać więcej informacji na temat zestawów wierszy schematu.

### <a name="end_schema_map"></a><a name="end_schema_map"></a>END_SCHEMA_MAP

Oznacza koniec mapy schematu.

#### <a name="syntax"></a>Składnia

```cpp
END_SCHEMA_MAP()
```

#### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [IDBSchemaRowsetImpl Class](../../data/oledb/idbschemarowsetimpl-class.md).

### <a name="schema_entry"></a><a name="schema_entry"></a>SCHEMA_ENTRY

Kojarzy identyfikator GUID z klasą.

#### <a name="syntax"></a>Składnia

```cpp
SCHEMA_ENTRY(guid,
   rowsetClass);
```

#### <a name="parameters"></a>Parametry

*Identyfikator guid*<br/>
Identyfikator GUID zestawu wierszy schematu. Zobacz [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) w *ole DB Programator odwołania* listy zestawów wierszy schematu i ich identyfikatorów GUID.

*klasa zestawu wierszy*<br/>
Klasa, która zostanie utworzona w celu reprezentowania zestawu wierszy schematu.

#### <a name="remarks"></a>Uwagi

[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) może następnie zbadać mapę dla listy identyfikatorów GUID lub może utworzyć zestaw wierszy, jeśli zostanie podany identyfikator GUID. Tworzy zestaw wierszy `IDBSchemaRowsetImpl` schematu jest `CRowsetImpl`podobny do klasy standardowej, `Execute` z tą różnicą, że musi dostarczyć metodę, która ma następujący podpis:

```cpp
HRESULT Execute (LONG* pcRowsAffected,
    ULONG cRestrictions,
    const VARIANT* rgRestrictions);
```

Ta `Execute` funkcja wypełnia dane zestawu wierszy. Kreator projektów ATL tworzy, zgodnie z opisem w [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) w *odwołaniu programisty OLE DB,* trzy początkowe zestawy wierszy schematu w projekcie dla każdego z trzech obowiązkowych schematów OLE DB:

- Dbschema_tables

- Dbschema_columns

- Dbschema_provider_types

Kreator dodaje również trzy odpowiednie wpisy na mapie schematu. Aby uzyskać więcej informacji na temat tworzenia dostawcy dostawcy [szablonów ole db, zobacz Tworzenie dostawcy szablonów ole db.](../../data/oledb/creating-an-ole-db-provider.md)

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Tworzenie dostawcy ole db](../../data/oledb/creating-an-ole-db-provider.md)<br/>
[Odwołanie do szablonów dostawców OLE DB](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[Makra dla szablonów dostawców OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)
