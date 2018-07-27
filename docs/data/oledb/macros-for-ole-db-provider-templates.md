---
title: Makra dla szablonów dostawców OLE DB | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- vc.templates.ole
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a1845f2e2404604aa187a8569954b3cb289ae3ec
ms.sourcegitcommit: e5792fcb89b9ba64c401f90f4f26a8e45d4a2359
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321932"
---
# <a name="macros-for-ole-db-provider-templates"></a>Makra dla szablonów dostawców OLE DB
Makra dostawcy OLE DB szablonów oferty funkcji w następujące kategorie:  
  
## <a name="property-set-map-macros"></a>Makra mapy właściwością.  
  
|||  
|-|-|  
|[BEGIN_PROPERTY_SET](#begin_property_set)|Oznacza początek zestawu właściwości.|  
|[BEGIN_PROPERTY_SET_EX](#begin_property_set_ex)|Oznacza początek zestawu właściwości.|  
|[BEGIN_PROPSET_MAP](#begin_propset_map)|Znaczniki, ustawionych na początek właściwości, które można ukryte lub zdefiniowane poza zakresem dostawcy.|  
|[CHAIN_PROPERTY_SET](#chain_property_set)|Łańcuchy grupy właściwości.|  
|[END_PROPERTY_SET](#end_property_set)|Oznacza koniec zestaw właściwości.|  
|[END_PROPSET_MAP](#end_propset_map)|Oznacza koniec Mapa zestawu właściwości.|  
|[PROPERTY_INFO_ENTRY](#property_info_entry)|Ustawia określoną właściwość we właściwości ustawić wartość domyślną.|  
|[PROPERTY_INFO_ENTRY_EX](#property_info_entry_ex)|Ustawia określoną właściwość we właściwości ustawić wartość podane przez użytkownika. Umożliwia także ustawić flagi i opcje.|  
|[PROPERTY_INFO_ENTRY_VALUE](#property_info_entry_value)|Ustawia określoną właściwość we właściwości ustawić wartość podane przez użytkownika.|  
  
## <a name="column-map-macros"></a>Makra mapy kolumny  
  
|||  
|-|-|  
|[BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)|Oznacza początek wpisy mapy kolumny dostawcy.|  
|[END_PROVIDER_COLUMN_MAP](#end_provider_column_map)|Oznacza koniec wpisy mapy kolumny dostawcy.|  
|[PROVIDER_COLUMN_ENTRY](#provider_column_entry)|Reprezentuje określonej kolumny jest obsługiwana przez dostawcę.|  
|[PROVIDER_COLUMN_ENTRY_FIXED](#provider_column_entry_fixed)|Reprezentuje określonej kolumny jest obsługiwana przez dostawcę. Można określić typ danych kolumny.|  
|[PROVIDER_COLUMN_ENTRY_GN](#provider_column_entry_gn)|Reprezentuje określonej kolumny jest obsługiwana przez dostawcę. Można określić rozmiar, typ danych kolumny, dokładności, skalowania i identyfikatorem GUID zestawu wierszy schematu.|  
|[PROVIDER_COLUMN_ENTRY_LENGTH](#provider_column_entry_length)|Reprezentuje określonej kolumny jest obsługiwana przez dostawcę. Można określić rozmiar kolumny.|  
|[PROVIDER_COLUMN_ENTRY_STR](#provider_column_entry_str)|Reprezentuje określonej kolumny jest obsługiwana przez dostawcę. Założono, że typ kolumny jest ciągiem.|  
|[PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](#provider_column_entry_type_length)|Reprezentuje określonej kolumny jest obsługiwana przez dostawcę. PROVIDER_COLUMN_ENTRY_LENGTH, takich jak, ale również można określić typ danych kolumny, a także rozmiar.|  
|[PROVIDER_COLUMN_ENTRY_WSTR](#provider_column_entry_wstr)|Reprezentuje określonej kolumny jest obsługiwana przez dostawcę. Założono, że typ kolumny jest ciągiem znaków Unicode.|  
  
## <a name="schema-rowset-macros"></a>Makra zestaw wierszy schematu  
  
|||  
|-|-|  
|[BEGIN_SCHEMA_MAP](#begin_schema_map)|Oznacza początek Mapa schematu.|  
|[END_SCHEMA_MAP](#end_schema_map)|Oznacza koniec Mapa schematu.|  
|[SCHEMA_ENTRY](#schema_entry)|Kojarzy identyfikator GUID za pomocą klasy.|  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  

### <a name="begin_property_set"></a> BEGIN_PROPERTY_SET
Znaczniki na początek właściwość, ustaw we właściwości ustaw mapy.  
  
#### <a name="syntax"></a>Składnia  
  
```cpp
BEGIN_PROPERTY_SET(guid)  
  
```  
  
#### <a name="parameters"></a>Parametry  
 *Identyfikator GUID*  
 [in] Właściwość identyfikatora GUID.  
  
#### <a name="example"></a>Przykład  
 Zobacz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  

### <a name="begin_property_set_ex"></a> BEGIN_PROPERTY_SET_EX
Znaczniki na początek właściwość, ustaw we właściwości ustaw mapy.  
  
#### <a name="syntax"></a>Składnia  
  
```cpp
BEGIN_PROPERTY_SET_EX(guid  
, flags )  
```  
  
#### <a name="parameters"></a>Parametry  
 *Identyfikator GUID*  
 [in] Właściwość identyfikatora GUID.  
  
 *flagi*  
 [in] UPROPSET_HIDDEN wszystkie zestawy właściwości, których nie chcesz ujawniać lub UPROPSET_PASSTHROUGH uwidaczniającą właściwości zdefiniowane poza zakresem dostawcy dla dostawcy.  
  
#### <a name="example"></a>Przykład  
 Zobacz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  

### <a name="begin_propset_map"></a> BEGIN_PROPSET_MAP
Znaczniki na początek właściwości ustaw wpisy mapy.  
  
#### <a name="syntax"></a>Składnia  
  
```cpp
BEGIN_PROPSET_MAP(Class)  
  
```  
  
#### <a name="parameters"></a>Parametry  
 *Class*  
 [in] Określono klasy, w którym ta właściwość jest ustawiona. Zestaw właściwości można określić w następujących obiektów OLE DB:  
  
-   [Obiekty źródła danych](https://msdn.microsoft.com/library/ms721278.aspx)  
  
-   [Obiektów sesji](https://msdn.microsoft.com/library/ms711572.aspx)  
  
-   [Polecenia](https://msdn.microsoft.com/library/ms724608.aspx)  
  
#### <a name="example"></a>Przykład  
 W tym miejscu jest mapa zestawu właściwości próbki:  
  
 [!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/cpp/begin-propset-map_1.h)]  

### <a name="chain_property_set"></a> CHAIN_PROPERTY_SET
To makro łańcuchy grupy właściwości.  
  
#### <a name="syntax"></a>Składnia  
  
```cpp
CHAIN_PROPERTY_SET(ChainClass)  
  
```  
  
#### <a name="parameters"></a>Parametry  
 *ChainClass*  
 [in] Nazwa klasy, która ma właściwości łańcucha. To jest klasa wygenerowany przez Kreator projektu ATL, która już zawiera mapę (na przykład sesji, polecenie lub danych źródłowego obiektu klasy).  
  
#### <a name="remarks"></a>Uwagi  
 Możesz połączyć w łańcuch zestaw właściwości z innej klasy własne klasy, a następnie uzyskać dostęp do właściwości bezpośrednio z klasy.  
  
> [!CAUTION]
>  Użyj tego makra rzadko. Niepoprawne użycie może spowodować konsumenta niepowodzenie testów zgodności z OLE DB.  

### <a name="end_property_set"></a> END_PROPERTY_SET
Oznacza koniec zestaw właściwości.  
  
#### <a name="syntax"></a>Składnia  
  
```cpp
END_PROPERTY_SET(guid)  
  
```  
  
#### <a name="parameters"></a>Parametry  
 *Identyfikator GUID*  
 [in] Właściwość identyfikatora GUID.  
  
#### <a name="example"></a>Przykład  
 Zobacz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  

### <a name="end_propset_map"></a> END_PROPSET_MAP
Znaki końca właściwości ustaw wpisy mapy.  
  
#### <a name="syntax"></a>Składnia  
  
```cpp
END_PROPSET_MAP()  
  
```  
  
#### <a name="example"></a>Przykład  
 Zobacz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  

### <a name="property_info_entry"></a> PROPERTY_INFO_ENTRY
Reprezentuje określoną właściwość w zbiorze właściwości.  
  
#### <a name="syntax"></a>Składnia  
  
```cpp
PROPERTY_INFO_ENTRY(dwPropID)  
  
```  
  
#### <a name="parameters"></a>Parametry  
 *dwPropID*  
 [in] A [DBPROPID](https://msdn.microsoft.com/library/ms723882.aspx) wartości, które mogą być używane w połączeniu z właściwością ustawić identyfikator GUID służący do identyfikowania właściwości.  
  
#### <a name="remarks"></a>Uwagi  
 To makro, ustawia wartość właściwości typu `DWORD` wartość domyślną, zdefiniowane w ATLDB. H. Aby ustawić wartość wybranej właściwości, należy użyć [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md). Aby ustawić [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4) i [DBPROPFLAGS](https://msdn.microsoft.com/library/ms724342.aspx) dla właściwości, w tym samym czasie, należy użyć [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).  
  
#### <a name="example"></a>Przykład  
 Zobacz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  

### <a name="property_info_entry_ex"></a> PROPERTY_INFO_ENTRY_EX
Reprezentuje określoną właściwość w zbiorze właściwości.  
  
#### <a name="syntax"></a>Składnia  
  
```cpp
PROPERTY_INFO_ENTRY_EX(dwPropID  
, vt, dwFlags, value, options )  
```  
  
#### <a name="parameters"></a>Parametry  
 *dwPropID*  
 [in] A [DBPROPID](https://msdn.microsoft.com/library/ms723882.aspx) wartości, które mogą być używane w połączeniu z właściwością ustawić identyfikator GUID służący do identyfikowania właściwości.  
  
 *vt*  
 [in] [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4) tego wpisu właściwości.  
  
 *Flagidw*  
 [in] A [DBPROPFLAGS](https://msdn.microsoft.com/library/ms724342.aspx) wartości opisujące ten wpis właściwości.  
  
 *value*  
 [in] Wartość właściwości typu `DWORD`.  
  
 *Opcje*  
 DBPROPOPTIONS_REQUIRED lub DBPROPOPTIONS_SETIFCHEAP. Zwykle dostawcy nie musisz ustawiać *opcje* , ponieważ jest on ustawiony przez użytkownika.  
  
#### <a name="remarks"></a>Uwagi  
 Za pomocą makra, możesz bezpośrednio określić wartość właściwości typu `DWORD` oraz opcje i flagi. Można jedynie ustawić właściwość na wartość domyślną, zdefiniowane w ATLDB. Godz., użyj [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Aby ustawić właściwość na wartość, co pozwala bez konieczności ustawiania opcji lub flagi na ich temat, należy użyć [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md).  
  
#### <a name="example"></a>Przykład  
 Zobacz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  

### <a name="property_info_entry_value"></a> PROPERTY_INFO_ENTRY_VALUE
Reprezentuje określoną właściwość w zbiorze właściwości.  
  
#### <a name="syntax"></a>Składnia  
  
```cpp
PROPERTY_INFO_ENTRY_VALUE(dwPropID  
, value )  
```  
  
#### <a name="parameters"></a>Parametry  
 *dwPropID*  
 [in] A [DBPROPID](https://msdn.microsoft.com/library/ms723882.aspx) wartości, które mogą być używane w połączeniu z właściwością ustawić identyfikator GUID służący do identyfikowania właściwości.  
  
 *value*  
 [in] Wartość właściwości typu `DWORD`.  
  
#### <a name="remarks"></a>Uwagi  
 Za pomocą makra, możesz bezpośrednio określić wartość właściwości typu `DWORD`. Można ustawić właściwości do wartości domyślnej zdefiniowanej w ATLDB. Godz., użyj [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Aby ustawić wartości, flag i opcje dla właściwości, należy użyć [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).  
  
#### <a name="example"></a>Przykład  
 Zobacz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  

### <a name="begin_provider_column_map"></a> BEGIN_PROVIDER_COLUMN_MAP
Oznacza początek wpisy mapy kolumny dostawcy.  
  
#### <a name="syntax"></a>Składnia  
  
```cpp
BEGIN_PROVIDER_COLUMN_MAP(theClass)  
  
```  
  
#### <a name="parameters"></a>Parametry  
 *theClass*  
 [in] Nazwa klasy, do której należy ta mapa.  
  
#### <a name="example"></a>Przykład  
 Oto mapy próbki dostawcy kolumny:  
  
 [!code-cpp[NVC_OLEDB_Provider#4](../../data/oledb/codesnippet/cpp/begin-provider-column-map_1.h)]  

### <a name="end_provider_column_map"></a> END_PROVIDER_COLUMN_MAP
Oznacza koniec wpisy mapy kolumny dostawcy.  
  
#### <a name="syntax"></a>Składnia  
  
```cpp
END_PROVIDER_COLUMN_MAP()  
  
```  
  
#### <a name="example"></a>Przykład  
 Zobacz [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).  

### <a name="provider_column_entry"></a> PROVIDER_COLUMN_ENTRY
Reprezentuje określonej kolumny jest obsługiwana przez dostawcę.  
  
#### <a name="syntax"></a>Składnia  
  
```cpp
PROVIDER_COLUMN_ENTRY (name  
, ordinal, member )  
```  
  
#### <a name="parameters"></a>Parametry  
 *Nazwa*  
 [in] Nazwa kolumny.  
  
 *Liczba porządkowa*  
 [in] Numer kolumny. Chyba że kolumna jest kolumną zakładki, numer kolumny nie może być 0.  
  
 *Element członkowski*  
 [in] Zmiennej składowej w `dataClass` odpowiadający kolumny.  

### <a name="provider_column_entry_fixed"></a> PROVIDER_COLUMN_ENTRY_FIXED
Reprezentuje określonej kolumny jest obsługiwana przez dostawcę.  
  
#### <a name="syntax"></a>Składnia  
  
```cpp
PROVIDER_COLUMN_ENTRY_FIXED(name  
, ordinal, dbtype, member )  
```  
  
#### <a name="parameters"></a>Parametry  
 *Nazwa*  
 [in] Nazwa kolumny.  
  
 *Liczba porządkowa*  
 [in] Numer kolumny. Chyba że kolumna jest kolumną zakładki, numer kolumny nie może być 0.  
  
 *Atrybut DbType*  
 [in] Typ danych w [DBTYPE](https://msdn.microsoft.com/library/ms711251.aspx).  
  
 *Element członkowski*  
 [in] Zmiennej składowej w `dataClass` która przechowuje dane.  
  
#### <a name="remarks"></a>Uwagi  
 Pozwala określić typ danych kolumny.  
  
#### <a name="example"></a>Przykład  
 Zobacz [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).  

### <a name="provider_column_entry_gn"></a> PROVIDER_COLUMN_ENTRY_GN
Reprezentuje określonej kolumny jest obsługiwana przez dostawcę.  
  
#### <a name="syntax"></a>Składnia  
  
```cpp
PROVIDER_COLUMN_ENTRY_GN (name  
, ordinal, flags, colSize, dbtype, precision, scale, guid )  
```  
  
#### <a name="parameters"></a>Parametry  
 *Nazwa*  
 [in] Nazwa kolumny.  
  
 *Liczba porządkowa*  
 [in] Numer kolumny. Chyba że kolumna jest kolumną zakładki, numer kolumny nie może być 0.  
  
 *flagi*  
 [in] Określa, jak dane są zwracane. Zobacz `dwFlags` opis [struktury DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx).  
  
 *colSize*  
 [in] Rozmiar kolumny.  
  
 *Atrybut DbType*  
 [in] Wskazuje typ danych wartości. Zobacz `wType` opis [struktury DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx).  
  
 *Precyzja*  
 [in] Wskazuje dokładności do użycia podczas pobierania danych, jeśli *dbType* DBTYPE_NUMERIC lub DBTYPE_DECIMAL. Zobacz `bPrecision` opis [struktury DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx).  
  
 *Skala*  
 [in] Wskazuje skalowania do użycia podczas pobierania danych, jeśli atrybut dbType jest DBTYPE_NUMERIC lub DBTYPE_DECIMAL. Zobacz `bScale` opis [struktury DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx).  
  
 *Identyfikator GUID*  
 Zestaw wierszy schematu identyfikatora GUID. Zobacz [IDBSchemaRowset](https://msdn.microsoft.com/library/ms713686.aspx) w *OLE DB Podręcznik programisty* Aby uzyskać listę zestawów wierszy schematu i ich identyfikatorów GUID.  
  
#### <a name="remarks"></a>Uwagi  
 Pozwala określić rozmiar, typ danych kolumny, dokładności, skalowania i identyfikatorem GUID zestawu wierszy schematu.  

### <a name="provider_column_entry_length"></a> PROVIDER_COLUMN_ENTRY_LENGTH
Reprezentuje określonej kolumny jest obsługiwana przez dostawcę.  
  
#### <a name="syntax"></a>Składnia  
  
```cpp
PROVIDER_COLUMN_ENTRY_LENGTH(name  
, ordinal, size, member )  
```  
  
#### <a name="parameters"></a>Parametry  
 *Nazwa*  
 [in] Nazwa kolumny.  
  
 *Liczba porządkowa*  
 [in] Numer kolumny. Chyba że kolumna jest kolumną zakładki, numer kolumny nie może być 0.  
  
 *Rozmiar*  
 [in] Rozmiar kolumny w bajtach.  
  
 *Element członkowski*  
 [in] Zmiennej składowej w `dataClass` który przechowuje dane w kolumnie.  
  
#### <a name="remarks"></a>Uwagi  
 Pozwala określić rozmiar kolumny.  
  
#### <a name="example"></a>Przykład  
 Zobacz [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md). 

### <a name="provider_column_entry_str"></a> PROVIDER_COLUMN_ENTRY_STR
Reprezentuje określonej kolumny jest obsługiwana przez dostawcę.  
  
#### <a name="syntax"></a>Składnia  
  
```cpp
PROVIDER_COLUMN_ENTRY_STR(name  
, ordinal, member )  
```  
  
#### <a name="parameters"></a>Parametry  
 *Nazwa*  
 [in] Nazwa kolumny.  
  
 *Liczba porządkowa*  
 [in] Numer kolumny. Chyba że kolumna jest kolumną zakładki, numer kolumny nie może być 0.  
  
 *Element członkowski*  
 [in] Zmiennej elementu członkowskiego w klasie danych, która przechowuje dane.  
  
#### <a name="remarks"></a>Uwagi  
 Użyj tego makra, gdy danych kolumny zakłada się, że [typem DBTYPE_STR](https://msdn.microsoft.com/library/ms711251.aspx).  
  
#### <a name="example"></a>Przykład  
 Zobacz [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).   

### <a name="provider_column_entry_type_length"></a> PROVIDER_COLUMN_ENTRY_TYPE_LENGTH
Reprezentuje określonej kolumny jest obsługiwana przez dostawcę.  
  
#### <a name="syntax"></a>Składnia  
  
```cpp
PROVIDER_COLUMN_ENTRY_TYPE_LENGTH(name  
, ordinal, dbtype, size, member )  
```  
  
#### <a name="parameters"></a>Parametry  
 *Nazwa*  
  
 [in] Nazwa kolumny.  
  
 *Liczba porządkowa*  
 [in] Numer kolumny. Chyba że kolumna jest kolumną zakładki, numer kolumny nie może być 0.  
  
 *Atrybut DbType*  
 [in] Typ danych w [DBTYPE](https://msdn.microsoft.com/library/ms711251.aspx).  
  
 *Rozmiar*  
 [in] Rozmiar kolumny w bajtach.  
  
 *Element członkowski*  
 [in] Zmiennej elementu członkowskiego w klasie danych, która przechowuje dane.  
  
#### <a name="remarks"></a>Uwagi  
 Podobnie jak [PROVIDER_COLUMN_ENTRY_LENGTH](../../data/oledb/provider-column-entry-length.md) , ale również można określić typ danych kolumny, a także rozmiar.  

### <a name="provider_column_entry_wstr"></a> PROVIDER_COLUMN_ENTRY_WSTR
Reprezentuje określonej kolumny jest obsługiwana przez dostawcę.  
  
#### <a name="syntax"></a>Składnia  
  
```cpp
PROVIDER_COLUMN_ENTRY_WSTR(name  
, ordinal, member )  
```  
  
#### <a name="parameters"></a>Parametry  
 *Nazwa*  
 [in] Nazwa kolumny.  
  
 *Liczba porządkowa*  
 [in] Numer kolumny. Chyba że kolumna jest kolumną zakładki, numer kolumny nie może być 0.  
  
 *Element członkowski*  
 [in] Zmiennej elementu członkowskiego w klasie danych, która przechowuje dane.  
  
#### <a name="remarks"></a>Uwagi  
 Użyj tego makra, gdy danych kolumny jest zakończony ciąg znaków Unicode, [DBTYPE_WSTR](https://msdn.microsoft.com/library/ms711251.aspx).  

### <a name="begin_schema_map"></a> BEGIN_SCHEMA_MAP
Oznacza początek Mapa schematu.  
  
#### <a name="syntax"></a>Składnia  
  
```cpp
      BEGIN_SCHEMA_MAP(SchemaClass);  
```  
  
#### <a name="parameters"></a>Parametry  
 *SchemaClass*  
 Klasa, która zawiera MAPĘ. Zazwyczaj są to klasy sesji.  
  
#### <a name="remarks"></a>Uwagi  
 Zobacz [IDBSchemaRowset](https://msdn.microsoft.com/library/ms713686.aspx) w zestawie Windows SDK, aby uzyskać więcej informacji na temat zestawów wierszy schematu.  

### <a name="end_schema_map"></a> END_SCHEMA_MAP
Oznacza koniec Mapa schematu.  
  
#### <a name="syntax"></a>Składnia  
  
```cpp
END_SCHEMA_MAP()  
  
```  
  
#### <a name="see-also"></a>Zobacz też  
 [IDBSchemaRowsetImpl, klasa](../../data/oledb/idbschemarowsetimpl-class.md)

### <a name="schema_entry"></a> SCHEMA_ENTRY
Kojarzy identyfikator GUID za pomocą klasy.  
  
#### <a name="syntax"></a>Składnia  
  
```cpp
      SCHEMA_ENTRY(guid,  
   rowsetClass);   
```  
  
#### <a name="parameters"></a>Parametry  
 *Identyfikator GUID*  
 Zestaw wierszy schematu identyfikatora GUID. Zobacz [IDBSchemaRowset](https://msdn.microsoft.com/library/ms713686.aspx) w *OLE DB Podręcznik programisty* Aby uzyskać listę zestawów wierszy schematu i ich identyfikatorów GUID.  
  
 *RowsetClass*  
 Klasa, która zostanie utworzona do reprezentowania zestawu wierszy schematu.  
  
#### <a name="remarks"></a>Uwagi  
 [Idbschemarowsetimpl —](../../data/oledb/idbschemarowsetimpl-class.md) można następnie zapytania mapę, aby uzyskać listę identyfikatorów GUID lub można utworzyć zestawu wierszy, jeśli jest on podawany identyfikator GUID. Zestaw wierszy schematu `IDBSchemaRowsetImpl` tworzy jest podobna do warstwy standardowa `CRowsetImpl`-pochodne klasy, z wyjątkiem przekazuje `Execute` metody, która ma następujący podpis:  
  
```cpp  
HRESULT Execute (LONG* pcRowsAffected,  
    ULONG cRestrictions,  
    const VARIANT* rgRestrictions);  
```  
  
 To `Execute` funkcja wypełnia zestawu wierszy danych. Tworzy kreator projektów ATL, zgodnie z opisem w [IDBSchemaRowset](https://msdn.microsoft.com/library/ms713686.aspx) w *OLE DB Podręcznik programisty*, trzy początkowej zestawów wierszy schematu w projekcie dla każdego z trzech obowiązkowe schematów OLE DB:  
  
-   DBSCHEMA_TABLES  
  
-   DBSCHEMA_COLUMNS  
  
-   DBSCHEMA_PROVIDER_TYPES  
  
 Kreator dodaje także trzy odpowiednie pozycje w mapie schematu. Zobacz [Tworzenie dostawcy OLE DB szablonu](../../data/oledb/creating-an-ole-db-provider.md) Aby uzyskać więcej informacji na temat za pomocą kreatora Utwórz dostawcę usługi.  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)   
 [OLE DB Provider szablony — dokumentacja](../../data/oledb/ole-db-provider-templates-reference.md)    
 [Makra dla szablonów dostawców OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
