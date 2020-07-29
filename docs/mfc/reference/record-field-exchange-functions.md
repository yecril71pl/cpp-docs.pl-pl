---
title: Funkcje wymiany pól rekordów
ms.date: 09/17/2019
f1_keywords:
- AFXDB/RFX_Binary
- AFXDB/RFX_Bool
- AFXDB/RFX_Byte
- AFXDB/RFX_Date
- AFXDB/RFX_Double
- AFXDB/RFX_Int
- AFXDB/RFX_Long
- AFXDB/RFX_LongBinary
- AFXDB/RFX_Single
- AFXDB/RFX_Text
- AFXDB/RFX_Binary_Bulk
- AFXDB/RFX_Bool_Bulk
- AFXDB/RFX_Byte_Bulk
- AFXDB/RFX_Date_Bulk
- AFXDB/RFX_Double_Bulk
- AFXDB/RFX_Int_Bulk
- AFXDB/RFX_Long_Bulk
- AFXDB/RFX_Single_Bulk
- AFXDB/RFX_Text_Bulk
- AFXDB/DFX_Binary
- AFXDB/DFX_Bool
- AFXDB/DFX_Byte
- AFXDB/DFX_Currency
- AFXDB/DFX_DateTime
- AFXDB/DFX_Double
- AFXDB/DFX_Long
- AFXDB/DFX_LongBinary
- AFXDB/DFX_Short
- AFXDB/DFX_Single
- AFXDB/DFX_Text
helpviewer_keywords:
- DAO (Data Access Objects), record field exchange (DFX)
- ODBC, bulk RFX data exchange functions [MFC]
- RFX (record field exchange), ODBC classes
- DFX (DAO record field exchange), data exchange functions [MFC]
- DFX functions [MFC]
- bulk RFX functions [MFC]
- DFX (DAO record field exchange)
- RFX (record field exchange), DAO classes
- ODBC, RFX
- RFX (record field exchange), data exchange functions [MFC]
- RFX (record field exchange)
ms.assetid: 6e4c5c1c-acb7-4c18-bf51-bf7959a696cd
ms.openlocfilehash: f4f1b12795252b91a2c14877822e221ca86ab39e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214038"
---
# <a name="record-field-exchange-functions"></a>Funkcje wymiany pól rekordów

W tym temacie wymieniono funkcje wymiany pól rekordów (RFX, bulk RFX i DFX) używane do automatyzowania transferu danych między obiektem zestawu rekordów i jego źródłem danych oraz do wykonywania innych operacji na danych.

Jeśli używasz klas opartych na ODBC i zaimplementowano pobieranie wierszy zbiorczych, musisz ręcznie przesłonić `DoBulkFieldExchange` funkcję członkowską `CRecordset` przez wywołanie funkcji RFX zbiorczych dla każdego elementu członkowskiego danych odpowiadającego kolumnie źródła danych.

Jeśli nie zaimplementowano pobierania wierszy zbiorczych w klasach opartych na ODBC lub jeśli używasz klas opartych na DAO (przestarzałe), ClassWizard przesłoni `DoFieldExchange` funkcję członkowską `CRecordset` lub `CDaoRecordset` przez wywołanie funkcji RFX (dla klas ODBC) lub funkcji DFX (dla klas DAO) dla każdego elementu członkowskiego danych pola w zestawie rekordów.

Funkcja wymiany pól rekordu przenosi dane za każdym razem, gdy struktura wywołuje `DoFieldExchange` lub `DoBulkFieldExchange` . Każda funkcja przenosi określony typ danych.

Aby uzyskać więcej informacji na temat sposobu korzystania z tych funkcji, zobacz artykuł [Rejestrowanie pól rekordów: jak działa RFX (ODBC)](../../data/odbc/record-field-exchange-how-rfx-works.md). Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

W przypadku kolumn danych, które są powiązane dynamicznie, można również wywołać funkcje RFX lub DFX samodzielnie, jak wyjaśniono w [zestawie rekordów artykułów: dynamiczne łączenie kolumn danych (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md). Ponadto można napisać własne niestandardowe procedury RFX lub DFX, zgodnie z opisem w uwagach technicznych [43](../../mfc/tn043-rfx-routines.md) (dla ODBC) i uwagach technicznych [53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) (dla DAO).

Aby zapoznać się z przykładem funkcji RFX i bulk RFX, które są wyświetlane w `DoFieldExchange` `DoBulkFieldExchange` funkcjach i, zobacz [RFX_Text](#rfx_text) i [RFX_Text_Bulk] #rfx_text_bulk). Funkcje DFX są bardzo podobne do funkcji RFX.

### <a name="rfx-functions-odbc"></a>Funkcje RFX (ODBC)

|||
|-|-|
|[RFX_Binary](#rfx_binary)|Przenosi tablice bajtów typu [CByteArray](cbytearray-class.md).|
|[RFX_Bool](#rfx_bool)|Przesyła dane logiczne.|
|[RFX_Byte](#rfx_byte)|Przesyła pojedynczy bajt danych.|
|[RFX_Date](#rfx_date)|Przesyła dane daty i godziny przy użyciu [CTime](../../atl-mfc-shared/reference/ctime-class.md) lub TIMESTAMP_STRUCT.|
|[RFX_Double](#rfx_double)|Przesyła dane zmiennoprzecinkowe o podwójnej precyzji.|
|[RFX_Int](#rfx_int)|Przesyła dane całkowite.|
|[RFX_Long](#rfx_long)|Przesyła dane Long Integer.|
|[RFX_LongBinary](#rfx_longbinary)|Przesyła dane binarne obiektów binarnych (BLOB) do obiektu klasy [CLongBinary](clongbinary-class.md) .|
|[RFX_Single](#rfx_single)|Przesyła dane zmiennoprzecinkowe.|
|[RFX_Text](#rfx_text)|Przesyła dane ciągów.|

### <a name="bulk-rfx-functions-odbc"></a>Funkcje Bulk RFX (ODBC)

|||
|-|-|
|[RFX_Binary_Bulk](#rfx_binary_bulk)|Przesyła tablice danych bajtowych.|
|[RFX_Bool_Bulk](#rfx_bool_bulk)|Przesyła tablice danych logicznych.|
|[RFX_Byte_Bulk](#rfx_byte_bulk)|Przenosi tablice pojedynczych bajtów.|
|[RFX_Date_Bulk](#rfx_date_bulk)|Przesyła tablice danych typu TIMESTAMP_STRUCT.|
|[RFX_Double_Bulk](#rfx_double_bulk)|Przesyła tablice o podwójnej precyzji danych zmiennoprzecinkowych.|
|[RFX_Int_Bulk](#rfx_int_bulk)|Przesyła tablice danych liczb całkowitych.|
|[RFX_Long_Bulk](#rfx_long_bulk)|Przesyła tablice długich danych całkowitych.|
|[RFX_Single_Bulk](#rfx_single_bulk)|Przesyła tablice danych zmiennoprzecinkowych.|
|[RFX_Text_Bulk](#rfx_text_bulk)|Przesyła tablice danych typu LPSTR.|

### <a name="dfx-functions-dao"></a>Funkcje DFX (DAO)

|||
|-|-|
|[DFX_Binary](#dfx_binary)|Przenosi tablice bajtów typu [CByteArray](cbytearray-class.md).|
|[DFX_Bool](#dfx_bool)|Przesyła dane logiczne.|
|[DFX_Byte](#dfx_byte)|Przesyła pojedynczy bajt danych.|
|[DFX_Currency](#dfx_currency)|Przesyła dane walutowe typu [COleCurrency](colecurrency-class.md).|
|[DFX_DateTime](#dfx_datetime)|Przesyła dane dotyczące daty i godziny, typu [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md).|
|[DFX_Double](#dfx_double)|Przesyła dane zmiennoprzecinkowe o podwójnej precyzji.|
|[DFX_Long](#dfx_long)|Przesyła dane Long Integer.|
|[DFX_LongBinary](#dfx_longbinary)|Przesyła dane binarne dużego obiektu (BLOB) do obiektu `CLongBinary` klasy. W przypadku obiektów DAO zaleca się używanie [DFX_Binary](#dfx_binary) zamiast tego.|
|[DFX_Short](#dfx_short)|Przesyła dane z krótkich liczb całkowitych.|
|[DFX_Single](#dfx_single)|Przesyła dane zmiennoprzecinkowe.|
|[DFX_Text](#dfx_text)|Przesyła dane ciągów.|

=============================================

## <a name="rfx_binary"></a><a name="rfx_binary"></a>RFX_Binary

Przenosi tablice bajtów między elementami członkowskimi danych pola `CRecordset` a kolumnami rekordu w źródle danych typu ODBC SQL_BINARY, SQL_VARBINARY lub SQL_LONGVARBINARY.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Binary(
   CFieldExchange* pFX,
   const char* szName,
   CByteArray& value,
   int nMaxLength = 255);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` , które można określić w obiekcie, zobacz [: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*wartościami*<br/>
Wartość przechowywana we wskazanym elemencie członkowskim danych — wartość do przeniesienia. W przypadku transferu z zestawu rekordów do źródła danych wartość typu [CByteArray](cbytearray-class.md)jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zestawu rekordów wartość jest przechowywana w określonym elemencie członkowskim danych.

*nMaxLength*<br/>
Maksymalna dozwolona długość przesyłanego ciągu lub tablicy. Wartość domyślna *nMaxLength* to 255. Wartości prawne są od 1 do INT_MAX. Struktura przydziela ilość miejsca na dane. Aby uzyskać najlepszą wydajność, należy przekazać wartość wystarczająco duża, aby pomieścić największy element danych, który jest oczekiwany.

### <a name="remarks"></a>Uwagi

Dane w źródle danych tego typu są mapowane do i z typu `CByteArray` w zestawie rekordów.

### <a name="example"></a>Przykład

Zobacz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDB. h

## <a name="rfx_bool"></a><a name="rfx_bool"></a>RFX_Bool

Przesyła dane logiczne między elementami członkowskimi danych pola `CRecordset` a kolumnami rekordu w źródle danych typu ODBC SQL_BIT.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Bool(
   CFieldExchange* pFX,
   const char* szName,
   BOOL& value);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` , które można określić w obiekcie, zobacz [: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*wartościami*<br/>
Wartość przechowywana we wskazanym elemencie członkowskim danych — wartość do przeniesienia. W przypadku transferu z zestawu rekordów do źródła danych wartość typu BOOL jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zestawu rekordów wartość jest przechowywana w określonym elemencie członkowskim danych.

### <a name="example"></a>Przykład

Zobacz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDB. h

## <a name="rfx_byte"></a><a name="rfx_byte"></a>RFX_Byte

Przenosi pojedyncze bajty między elementami członkowskimi danych pola `CRecordset` a kolumnami rekordu w źródle danych typu ODBC SQL_TINYINT.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Byte(
   CFieldExchange* pFX,
   const char* szName,
   BYTE& value);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` , które można określić w obiekcie, zobacz [: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*wartościami*<br/>
Wartość przechowywana we wskazanym elemencie członkowskim danych — wartość do przeniesienia. W przypadku transferu z zestawu rekordów do źródła danych wartość typu BYTE jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zestawu rekordów wartość jest przechowywana w określonym elemencie członkowskim danych.

### <a name="example"></a>Przykład

Zobacz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDB. h

## <a name="rfx_date"></a><a name="rfx_date"></a>RFX_Date

Przenosi `CTime` lub TIMESTAMP_STRUCT dane między elementami członkowskimi danych pola `CRecordset` a kolumnami rekordu w źródle danych typu ODBC SQL_DATE, SQL_TIME lub SQL_TIMESTAMP.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Date(
   CFieldExchange* pFX,
   const char* szName,
   CTime& value);

void RFX_Date(
   CFieldExchange* pFX,
   const char* szName,
   TIMESTAMP_STRUCT& value);

void RFX_Date(
   CFieldExchange* pFX,
   const char* szName,
   COleDateTime& value);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` , które można określić w obiekcie, zobacz [: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*wartościami*<br/>
Wartość przechowywana we wskazanej składowej danych; wartość, która ma zostać przeniesiona. Różne wersje funkcji mają różne typy danych dla wartości:

Pierwsza wersja funkcji przyjmuje odwołanie do obiektu [CTime](../../atl-mfc-shared/reference/ctime-class.md) . W przypadku transferu z zestawu rekordów do źródła danych ta wartość jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zestawu rekordów wartość jest przechowywana w określonym elemencie członkowskim danych.

Druga wersja funkcji przyjmuje odwołanie do `TIMESTAMP_STRUCT` struktury. Tę strukturę należy skonfigurować samodzielnie przed wywołaniem. Dla tej wersji nie jest dostępna żadna obsługa wymiany danych (DDX) ani Obsługa kreatora kodu. Trzecia wersja funkcji działa podobnie jak w przypadku pierwszej wersji, z tą różnicą, że pobiera odwołanie do obiektu [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) .

### <a name="remarks"></a>Uwagi

`CTime`Wersja funkcji nakłada obciążenie pewnego przetwarzania pośredniego i ma nieco ograniczony zakres. Jeśli okaże się, że oba te czynniki są zbyt ograniczone, użyj drugiej wersji funkcji. Zwróć uwagę na to, że nie ma kreatora kodu i pomocy technicznej DDX oraz wymaganie, aby samodzielnie skonfigurować strukturę.

### <a name="example"></a>Przykład

Zobacz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDB. h

## <a name="rfx_double"></a><a name="rfx_double"></a>RFX_Double

Przenosi **podwójne dane zmiennoprzecinkowe** między elementami członkowskimi danych pola `CRecordset` a kolumnami rekordu w źródle danych typu ODBC SQL_DOUBLE.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Double(
   CFieldExchange* pFX,
   const char* szName,
   double& value);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` , które można określić w obiekcie, zobacz [: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*wartościami*<br/>
Wartość przechowywana we wskazanym elemencie członkowskim danych — wartość do przeniesienia. W przypadku transferu z zestawu rekordów do źródła danych wartość typu **`double`** jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zestawu rekordów wartość jest przechowywana w określonym elemencie członkowskim danych.

### <a name="example"></a>Przykład

Zobacz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDB. h

## <a name="rfx_int"></a><a name="rfx_int"></a>RFX_Int

Przenosi dane całkowite między elementami członkowskimi danych pola `CRecordset` a kolumnami rekordu w źródle danych typu ODBC SQL_SMALLINT.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` , które można określić w obiekcie, zobacz [: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*wartościami*<br/>
Wartość przechowywana we wskazanym elemencie członkowskim danych — wartość do przeniesienia. W przypadku transferu z zestawu rekordów do źródła danych wartość typu **`int`** jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zestawu rekordów wartość jest przechowywana w określonym elemencie członkowskim danych.

### <a name="example"></a>Przykład

Zobacz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDB. h

## <a name="rfx_long"></a><a name="rfx_long"></a>RFX_Long

Przesyła dane typu Long-Integer między elementami członkowskimi danych pola `CRecordset` a kolumnami rekordu w źródle danych o typie ODBC SQL_INTEGER.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Long(
   CFieldExchange* pFX,
   const char* szName,
   LONG&
value );
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` , które można określić w obiekcie, zobacz [: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*wartościami*<br/>
Wartość przechowywana we wskazanym elemencie członkowskim danych — wartość do przeniesienia. W przypadku transferu z zestawu rekordów do źródła danych wartość typu **`long`** jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zestawu rekordów wartość jest przechowywana w określonym elemencie członkowskim danych.

### <a name="example"></a>Przykład

Zobacz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDB. h

## <a name="rfx_longbinary"></a><a name="rfx_longbinary"></a>RFX_LongBinary

Przesyła dane binarne obiektów binarnych (BLOB) przy użyciu klasy [CLongBinary](clongbinary-class.md) między elementami członkowskimi danych pola `CRecordset` a kolumnami rekordu w źródle danych typu ODBC SQL_LONGVARBINARY lub SQL_LONGVARCHAR.

### <a name="syntax"></a>Składnia

```cpp
void RFX_LongBinary(
   CFieldExchange* pFX,
   const char* szName,
   CLongBinary& value);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` , które można określić w obiekcie, zobacz [: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*wartościami*<br/>
Wartość przechowywana we wskazanym elemencie członkowskim danych — wartość do przeniesienia. W przypadku transferu z zestawu rekordów do źródła danych wartość typu `CLongBinary` jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zestawu rekordów wartość jest przechowywana w określonym elemencie członkowskim danych.

### <a name="example"></a>Przykład

Zobacz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDB. h

## <a name="rfx_single"></a><a name="rfx_single"></a>RFX_Single

Przesyła dane zmiennoprzecinkowe między elementami członkowskimi danych pola `CRecordset` a kolumnami rekordów w źródle danych typu ODBC SQL_REAL.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Single(
   CFieldExchange* pFX,
   const char* szName,
   float& value);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` , które można określić w obiekcie, zobacz [: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*wartościami*<br/>
Wartość przechowywana we wskazanym elemencie członkowskim danych — wartość do przeniesienia. W przypadku transferu z zestawu rekordów do źródła danych wartość typu **`float`** jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zestawu rekordów wartość jest przechowywana w określonym elemencie członkowskim danych.

### <a name="example"></a>Przykład

Zobacz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDB. h

## <a name="rfx_text"></a><a name="rfx_text"></a>RFX_Text

Przesyła `CString` dane między elementami członkowskimi danych pola `CRecordset` obiektu a kolumnami rekordu w źródle danych typu ODBC SQL_LONGVARCHAR, SQL_CHAR, SQL_VARCHAR, SQL_DECIMAL lub Sql_Numeric.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Text(
   CFieldExchange* pFX,
   const char* szName,
   CString& value,
   int nMaxLength = 255,
   int nColumnType = SQL_VARCHAR,
   short nScale = 0);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu klasy `CFieldExchange` . Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` , które można określić w obiekcie, zobacz [: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*wartościami*<br/>
Wartość przechowywana we wskazanym elemencie członkowskim danych — wartość do przeniesienia. W przypadku transferu z zestawu rekordów do źródła danych wartość typu `CString` jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zestawu rekordów wartość jest przechowywana w określonym elemencie członkowskim danych.

*nMaxLength*<br/>
Maksymalna dozwolona długość przesyłanego ciągu lub tablicy. Wartość domyślna *nMaxLength* to 255. Wartości prawne są od 1 do INT_MAX). Struktura przydziela ilość miejsca na dane. Aby uzyskać najlepszą wydajność, należy przekazać wartość wystarczająco duża, aby pomieścić największy element danych, który jest oczekiwany.

*nColumnType*<br/>
Używane głównie do parametrów. Liczba całkowita wskazująca typ danych parametru. Typ jest typem danych ODBC formularza **SQL_XXX**.

*nScale*<br/>
Określa skalę dla wartości typu ODBC SQL_DECIMAL lub SQL_NUMERIC. *nScale* jest przydatne tylko w przypadku ustawiania wartości parametrów. Aby uzyskać więcej informacji, zobacz temat "precyzja, skala, długość i rozmiar wyświetlania" w dodatku D odwołania do *zestawu ODBC SDK*.

### <a name="remarks"></a>Uwagi

Dane w źródle danych wszystkich typów są mapowane do i z `CString` w zestawie rekordów.

### <a name="example"></a>Przykład

Ten przykład pokazuje kilka wywołań `RFX_Text` . Zwróć również uwagę na dwa wywołania `CFieldExchange::SetFieldType` . Dla parametrów należy napisać wywołanie do `SetFieldType` i jego wywołanie RFX. Wywołanie kolumny wyjściowej i skojarzone z nią wywołania RFX są zwykle zapisywane przez kreatora kodu.

```cpp
void CCustomer::DoFieldExchange(CFieldExchange* pFX)
{
   pFX->SetFieldType(CFieldExchange::outputColumn);
   // Macros such as RFX_Text() and RFX_Int() are dependent on the
   // type of the member variable, not the type of the field in the database.
   // ODBC will try to automatically convert the column value to the requested type
   RFX_Long(pFX, _T("[CustomerID]"), m_CustomerID);
   RFX_Text(pFX, _T("[ContactFirstName]"), m_ContactFirstName);
   RFX_Text(pFX, _T("[PostalCode]"), m_PostalCode);
   RFX_Text(pFX, _T("[L_Name]"), m_L_Name);
   RFX_Long(pFX, _T("[BillingID]"), m_BillingID);

   pFX->SetFieldType(CFieldExchange::inputParam);
   RFX_Text(pFX, _T("Param"), m_strParam);
}
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDB. h

## <a name="rfx_binary_bulk"></a><a name="rfx_binary_bulk"></a>RFX_Binary_Bulk

Przesyła wiele wierszy danych typu Byte z kolumny źródła danych ODBC do odpowiedniej tablicy w `CRecordset` obiekcie pochodnym.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Binary_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BYTE** prgByteVals,
   long** prgLengths,
   int nMaxLength);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu [CFieldExchange](cfieldexchange-class.md) . Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*prgByteVals*<br/>
Wskaźnik do tablicy wartości bajtów. Ta tablica będzie przechowywać dane, które mają zostać przesłane ze źródła danych do zestawu rekordów.

*prgLengths*<br/>
Wskaźnik do tablicy długich liczb całkowitych. Ta tablica będzie przechowywać długość w bajtach każdej wartości w tablicy wskazywanej przez *prgByteVals*. Należy zauważyć, że wartość SQL_NULL_DATA będzie przechowywana, jeśli odpowiedni element danych zawiera wartość null. Aby uzyskać więcej informacji, zobacz Funkcja ODBC API `SQLBindCol` w *dokumentacji programisty zestawu ODBC SDK*.

*nMaxLength*<br/>
Maksymalna dozwolona długość wartości przechowywanych w tablicy wskazywanej przez *prgByteVals*. Aby upewnić się, że dane nie będą obcinane, należy przekazać wartość wystarczająco duża, aby pomieścić największe oczekiwane elementy danych.

### <a name="remarks"></a>Uwagi

Kolumna źródła danych może mieć typ ODBC SQL_BINARY, SQL_VARBINARY lub SQL_LONGVARBINARY. Zestaw rekordów musi definiować element członkowski danych pola typu wskaźnik do BYTE.

Jeśli zainicjujesz *prgByteVals* i *prgLengths* do wartości null, tablice, do których wskazują, zostaną przyliczone automatycznie, o rozmiarach równych rozmiarowi zestawu wierszy.

> [!NOTE]
> Wymiana pól rekordów zbiorczych transferuje tylko dane ze źródła danych do obiektu zestawu rekordów. Aby można było zaktualizować zestaw rekordów, należy użyć funkcji ODBC API `SQLSetPos` .

Aby uzyskać więcej informacji, zobacz [zestaw rekordów artykułów: pobieranie rekordów w zbiorczej (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Przykład

Zobacz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDB. h

## <a name="rfx_bool_bulk"></a><a name="rfx_bool_bulk"></a>RFX_Bool_Bulk

Przenosi wiele wierszy danych logicznych z kolumny źródła danych ODBC do odpowiedniej tablicy w `CRecordset` obiekcie pochodnym.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Bool_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BOOL** prgBoolVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu [CFieldExchange](cfieldexchange-class.md) . Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*prgBoolVals*<br/>
Wskaźnik do tablicy wartości BOOL. Ta tablica będzie przechowywać dane, które mają zostać przesłane ze źródła danych do zestawu rekordów.

*prgLengths*<br/>
Wskaźnik do tablicy długich liczb całkowitych. Ta tablica będzie przechowywać długość w bajtach każdej wartości w tablicy wskazywanej przez *prgBoolVals*. Należy zauważyć, że wartość SQL_NULL_DATA będzie przechowywana, jeśli odpowiedni element danych zawiera wartość null. Aby uzyskać więcej informacji, zobacz Funkcja ODBC API `SQLBindCol` w *dokumentacji programisty zestawu ODBC SDK*.

### <a name="remarks"></a>Uwagi

Kolumna źródła danych musi mieć typ ODBC SQL_BIT. Zestaw rekordów musi definiować element członkowski danych pola typu wskaźnik do wartości LOGICZNEj.

Jeśli zainicjujesz *prgBoolVals* i *prgLengths* do wartości null, tablice, do których wskazują, zostaną przyliczone automatycznie, o rozmiarach równych rozmiarowi zestawu wierszy.

> [!NOTE]
> Wymiana pól rekordów zbiorczych transferuje tylko dane ze źródła danych do obiektu zestawu rekordów. Aby zestaw rekordów był aktualizowalny, należy użyć funkcji ODBC API `SQLSetPos` .

Aby uzyskać więcej informacji, zobacz [zestaw rekordów artykułów: pobieranie rekordów w zbiorczej (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Przykład

Zobacz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDB. h

## <a name="rfx_byte_bulk"></a><a name="rfx_byte_bulk"></a>RFX_Byte_Bulk

Transferuje wiele wierszy z pojedynczej liczby bajtów z kolumny źródła danych ODBC do odpowiedniej tablicy w `CRecordset` obiekcie pochodnym.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Byte_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BYTE** prgByteVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu [CFieldExchange](cfieldexchange-class.md) . Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*prgByteVals*<br/>
Wskaźnik do tablicy wartości bajtów. Ta tablica będzie przechowywać dane, które mają zostać przesłane ze źródła danych do zestawu rekordów.

*prgLengths*<br/>
Wskaźnik do tablicy długich liczb całkowitych. Ta tablica będzie przechowywać długość w bajtach każdej wartości w tablicy wskazywanej przez *prgByteVals*. Należy zauważyć, że wartość SQL_NULL_DATA będzie przechowywana, jeśli odpowiedni element danych zawiera wartość null. Aby uzyskać więcej informacji, zobacz Funkcja ODBC API `SQLBindCol` w *dokumentacji programisty zestawu ODBC SDK*.

### <a name="remarks"></a>Uwagi

Kolumna źródła danych musi mieć typ ODBC SQL_TINYINT. Zestaw rekordów musi definiować element członkowski danych pola typu wskaźnik do BYTE.

Jeśli zainicjujesz *prgByteVals* i *prgLengths* do wartości null, tablice, do których wskazują, zostaną przyliczone automatycznie, o rozmiarach równych rozmiarowi zestawu wierszy.

> [!NOTE]
> Wymiana pól rekordów zbiorczych transferuje tylko dane ze źródła danych do obiektu zestawu rekordów. Aby zestaw rekordów był aktualizowalny, należy użyć funkcji ODBC API `SQLSetPos` .

Aby uzyskać więcej informacji, zobacz [zestaw rekordów artykułów: pobieranie rekordów w zbiorczej (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Przykład

Zobacz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDB. h

## <a name="rfx_date_bulk"></a><a name="rfx_date_bulk"></a>RFX_Date_Bulk

Przesyła wiele wierszy danych TIMESTAMP_STRUCT z kolumny źródła danych ODBC do odpowiedniej tablicy w `CRecordset` obiekcie pochodnym.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Date_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   TIMESTAMP_STRUCT** prgTSVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu [CFieldExchange](cfieldexchange-class.md) . Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*prgTSVals*<br/>
Wskaźnik do tablicy wartości TIMESTAMP_STRUCT. Ta tablica będzie przechowywać dane, które mają zostać przesłane ze źródła danych do zestawu rekordów. Aby uzyskać więcej informacji na temat typu danych TIMESTAMP_STRUCT, zobacz temat "typy danych C" w dodatku D odwołania do *zestawu ODBC SDK*.

*prgLengths*<br/>
Wskaźnik do tablicy długich liczb całkowitych. Ta tablica będzie przechowywać długość w bajtach każdej wartości w tablicy wskazywanej przez *prgTSVals*. Należy zauważyć, że wartość SQL_NULL_DATA będzie przechowywana, jeśli odpowiedni element danych zawiera wartość null. Aby uzyskać więcej informacji, zobacz Funkcja ODBC API `SQLBindCol` w *dokumentacji programisty zestawu ODBC SDK*.

### <a name="remarks"></a>Uwagi

Kolumna źródła danych może mieć typ ODBC SQL_DATE, SQL_TIME lub SQL_TIMESTAMP. Zestaw rekordów musi definiować element członkowski danych pola typu wskaźnik do TIMESTAMP_STRUCT.

Jeśli zainicjujesz *prgTSVals* i *prgLengths* do wartości null, tablice, do których wskazują, zostaną przyliczone automatycznie, o rozmiarach równych rozmiarowi zestawu wierszy.

> [!NOTE]
> Wymiana pól rekordów zbiorczych transferuje tylko dane ze źródła danych do obiektu zestawu rekordów. Aby zestaw rekordów był aktualizowalny, należy użyć funkcji ODBC API `SQLSetPos` .

Aby uzyskać więcej informacji, zobacz [zestaw rekordów artykułów: pobieranie rekordów w zbiorczej (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Przykład

Zobacz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDB. h

## <a name="rfx_double_bulk"></a><a name="rfx_double_bulk"></a>RFX_Double_Bulk

Transferuje wiele wierszy danych o podwójnej precyzji z kolumny ze źródła danych ODBC do odpowiedniej tablicy w `CRecordset` obiekcie pochodnym.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Double_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   double** prgDblVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu [CFieldExchange](cfieldexchange-class.md) . Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*prgDblVals*<br/>
Wskaźnik do tablicy **`double`** wartości. Ta tablica będzie przechowywać dane, które mają zostać przesłane ze źródła danych do zestawu rekordów.

*prgLengths*<br/>
Wskaźnik do tablicy długich liczb całkowitych. Ta tablica będzie przechowywać długość w bajtach każdej wartości w tablicy wskazywanej przez *prgDblVals*. Należy zauważyć, że wartość SQL_NULL_DATA będzie przechowywana, jeśli odpowiedni element danych zawiera wartość null. Aby uzyskać więcej informacji, zobacz Funkcja ODBC API `SQLBindCol` w *dokumentacji programisty zestawu ODBC SDK*.

### <a name="remarks"></a>Uwagi

Kolumna źródła danych musi mieć typ ODBC SQL_DOUBLE. Zestaw rekordów musi definiować element członkowski danych pola typu wskaźnik do **`double`** .

Jeśli zainicjujesz *prgDblVals* i *prgLengths* do wartości null, tablice, do których wskazują, zostaną przyliczone automatycznie, o rozmiarach równych rozmiarowi zestawu wierszy.

> [!NOTE]
> Wymiana pól rekordów zbiorczych transferuje tylko dane ze źródła danych do obiektu zestawu rekordów. Aby zestaw rekordów był aktualizowalny, należy użyć funkcji ODBC API `SQLSetPos` .

Aby uzyskać więcej informacji, zobacz [zestaw rekordów artykułów: pobieranie rekordów w zbiorczej (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Przykład

Zobacz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDB. h

## <a name="rfx_int_bulk"></a><a name="rfx_int_bulk"></a>RFX_Int_Bulk

Przenosi dane całkowite między elementami członkowskimi danych pola `CRecordset` a kolumnami rekordu w źródle danych typu ODBC SQL_SMALLINT.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` , które można określić w obiekcie, zobacz [: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*wartościami*<br/>
Wartość przechowywana we wskazanym elemencie członkowskim danych — wartość do przeniesienia. W przypadku transferu z zestawu rekordów do źródła danych wartość typu **`int`** jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zestawu rekordów wartość jest przechowywana w określonym elemencie członkowskim danych.

### <a name="example"></a>Przykład

Zobacz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDB. h

## <a name="rfx_long_bulk"></a><a name="rfx_long_bulk"></a>RFX_Long_Bulk

Przesyła wiele wierszy danych long Integer z kolumny źródła danych ODBC do odpowiedniej tablicy w `CRecordset` obiekcie pochodnym.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Long_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   long** prgLongVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu [CFieldExchange](cfieldexchange-class.md) . Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*prgLongVals*<br/>
Wskaźnik do tablicy długich liczb całkowitych. Ta tablica będzie przechowywać dane, które mają zostać przesłane ze źródła danych do zestawu rekordów.

*prgLengths*<br/>
Wskaźnik do tablicy długich liczb całkowitych. Ta tablica będzie przechowywać długość w bajtach każdej wartości w tablicy wskazywanej przez *prgLongVals*. Należy zauważyć, że wartość SQL_NULL_DATA będzie przechowywana, jeśli odpowiedni element danych zawiera wartość null. Aby uzyskać więcej informacji, zobacz Funkcja ODBC API `SQLBindCol` w *dokumentacji programisty zestawu ODBC SDK*.

### <a name="remarks"></a>Uwagi

Kolumna źródła danych musi mieć typ ODBC SQL_INTEGER. Zestaw rekordów musi definiować element członkowski danych pola typu wskaźnik do **`long`** .

Jeśli zainicjujesz *prgLongVals* i *prgLengths* do wartości null, tablice, do których wskazują, zostaną przyliczone automatycznie, o rozmiarach równych rozmiarowi zestawu wierszy.

> [!NOTE]
> Wymiana pól rekordów zbiorczych transferuje tylko dane ze źródła danych do obiektu zestawu rekordów. Aby zestaw rekordów był aktualizowalny, należy użyć funkcji ODBC API `SQLSetPos` .

Aby uzyskać więcej informacji, zobacz [zestaw rekordów artykułów: pobieranie rekordów w zbiorczej (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Przykład

Zobacz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDB. h

## <a name="rfx_single_bulk"></a><a name="rfx_single_bulk"></a>RFX_Single_Bulk

Przesyła wiele wierszy danych zmiennoprzecinkowych z kolumny źródła danych ODBC do odpowiedniej tablicy w `CRecordset` obiekcie pochodnym.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Single_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   float** prgFltVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu [CFieldExchange](cfieldexchange-class.md) . Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*prgFltVals*<br/>
Wskaźnik do tablicy **`float`** wartości. Ta tablica będzie przechowywać dane, które mają zostać przesłane ze źródła danych do zestawu rekordów.

*prgLengths*<br/>
Wskaźnik do tablicy długich liczb całkowitych. Ta tablica będzie przechowywać długość w bajtach każdej wartości w tablicy wskazywanej przez *prgFltVals*. Należy zauważyć, że wartość SQL_NULL_DATA będzie przechowywana, jeśli odpowiedni element danych zawiera wartość null. Aby uzyskać więcej informacji, zobacz Funkcja ODBC API `SQLBindCol` w *dokumentacji programisty zestawu ODBC SDK*.

### <a name="remarks"></a>Uwagi

Kolumna źródła danych musi mieć typ ODBC SQL_REAL. Zestaw rekordów musi definiować element członkowski danych pola typu wskaźnik do **`float`** .

Jeśli zainicjujesz *prgFltVals* i *prgLengths* do wartości null, tablice, do których wskazują, zostaną przyliczone automatycznie, o rozmiarach równych rozmiarowi zestawu wierszy.

> [!NOTE]
> Wymiana pól rekordów zbiorczych transferuje tylko dane ze źródła danych do obiektu zestawu rekordów. Aby zestaw rekordów był aktualizowalny, należy użyć funkcji ODBC API `SQLSetPos` .

Aby uzyskać więcej informacji, zobacz [zestaw rekordów artykułów: pobieranie rekordów w zbiorczej (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Przykład

Zobacz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDB. h

## <a name="rfx_text_bulk"></a><a name="rfx_text_bulk"></a>RFX_Text_Bulk

Przesyła wiele wierszy danych znakowych z kolumny źródła danych ODBC do odpowiedniej tablicy w `CRecordset` obiekcie pochodnym.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Text_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   LPSTR* prgStrVals,
   long** prgLengths,
   int nMaxLength);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu [CFieldExchange](cfieldexchange-class.md) . Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*prgStrVals*<br/>
Wskaźnik do tablicy wartości LPSTR. Ta tablica będzie przechowywać dane, które mają zostać przesłane ze źródła danych do zestawu rekordów. Należy pamiętać, że z bieżącą wersją ODBC, te wartości nie mogą być w formacie Unicode.

*prgLengths*<br/>
Wskaźnik do tablicy długich liczb całkowitych. Ta tablica będzie przechowywać długość w bajtach każdej wartości w tablicy wskazywanej przez *prgStrVals*. Ta długość wyklucza znak zakończenia o wartości null. Należy zauważyć, że wartość SQL_NULL_DATA będzie przechowywana, jeśli odpowiedni element danych zawiera wartość null. Aby uzyskać więcej informacji, zobacz Funkcja ODBC API `SQLBindCol` w *dokumentacji programisty zestawu ODBC SDK*.

*nMaxLength*<br/>
Maksymalna dozwolona długość wartości przechowywanych w tablicy wskazywanych przez *prgStrVals*, w tym znak zakończenia o wartości null. Aby upewnić się, że dane nie będą obcinane, należy przekazać wartość wystarczająco duża, aby pomieścić największe oczekiwane elementy danych.

### <a name="remarks"></a>Uwagi

Kolumna źródła danych może mieć typ ODBC SQL_LONGVARCHAR, SQL_CHAR, SQL_VARCHAR, SQL_DECIMAL lub SQL_NUMERIC. Zestaw rekordów musi definiować element członkowski danych pola typu LPSTR.

Jeśli zainicjujesz *prgStrVals* i *prgLengths* do wartości null, tablice, do których wskazują, zostaną przyliczone automatycznie, o rozmiarach równych rozmiarowi zestawu wierszy.

> [!NOTE]
> Wymiana pól rekordów zbiorczych transferuje tylko dane ze źródła danych do obiektu zestawu rekordów. Aby zestaw rekordów był aktualizowalny, należy użyć funkcji ODBC API `SQLSetPos` .

Aby uzyskać więcej informacji, zobacz [zestaw rekordów artykułów: pobieranie rekordów w zbiorczej (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Przykład

Należy ręcznie pisać wywołania w `DoBulkFieldExchange` przesłonięciu. W tym przykładzie pokazano wywołanie `RFX_Text_Bulk` , a także wywołanie do `RFX_Long_Bulk` , w celu transferu danych. Te wywołania są poprzedzone wywołaniem metody [CFieldExchange:: SetFieldType](cfieldexchange-class.md#setfieldtype). Należy pamiętać, że w przypadku parametrów należy wywołać funkcje RFX zamiast funkcji RFX BULK.

```cpp
void CMultiCustomer::DoBulkFieldExchange(CFieldExchange* pFX)
{
   pFX->SetFieldType(CFieldExchange::outputColumn);
   RFX_Long_Bulk(pFX, _T("[CustomerID]"), &m_pCustomerID, &m_pcCustomerID);
   RFX_Text_Bulk(pFX, _T("[ContactFirstName]"), &m_pContactFirstName, &m_pcContactFirstName, 50);
   RFX_Text_Bulk(pFX, _T("[PostalCode]"), &m_pPostalCode, &m_pcPostalCode, 50);
   RFX_Text_Bulk(pFX, _T("[L_Name]"), &m_pL_Name, &m_pcL_Name, 50);
   RFX_Long_Bulk(pFX, _T("[BillingID]"), &m_pBillingID, &m_pcBillingID);

   pFX->SetFieldType(CFieldExchange::inputParam);
   RFX_Text(pFX, _T("Param"), m_strParam);
}
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDB. h

## <a name="dfx_binary"></a><a name="dfx_binary"></a>DFX_Binary

Przenosi tablice bajtów między elementami członkowskimi danych pola obiektu [CDaoRecordset](cdaorecordset-class.md) a kolumnami rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI DFX_Binary(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CByteArray& value,
   int nPreAllocSize = AFX_DAO_BINARY_DEFAULT_SIZE,
   DWORD dwBindOptions = 0);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji.

*szName*<br/>
Nazwa kolumny danych.

*wartościami*<br/>
Wartość przechowywana we wskazanym elemencie członkowskim danych — wartość do przeniesienia. W przypadku transferu z zestawu rekordów do źródła danych wartość typu [CByteArray](cbytearray-class.md)jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zestawu rekordów wartość jest przechowywana w określonym elemencie członkowskim danych.

*nPreAllocSize*<br/>
Platforma wstępnie przydzieli tę ilość pamięci. Jeśli dane są większe, struktura przydzieli więcej miejsca w miarę potrzeb. Aby zapewnić lepszą wydajność, ustaw ten rozmiar na wystarczająco dużą wartość, aby zapobiec ponownym alokacjom. Domyślny rozmiar jest zdefiniowany w AFXDAO. H plik jako AFX_DAO_BINARY_DEFAULT_SIZE.

*dwBindOptions*<br/>
Opcja umożliwiająca korzystanie z mechanizmu podwójnego buforowania MFC w celu wykrywania pól zestawu rekordów, które uległy zmianie. Wartość domyślna, AFX_DAO_DISABLE_FIELD_CACHE, nie używa podwójnego buforowania i należy wywołać [SetFieldDirty](cdaorecordset-class.md#setfielddirty) i [SetFieldNull](cdaorecordset-class.md#setfieldnull) . Druga możliwa wartość, AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania i nie trzeba wykonywać dodatkowej pracy, aby oznaczyć pola jako zanieczyszczone lub puste. Ze względu na wydajność i pamięć należy unikać tej wartości, chyba że dane binarne są stosunkowo małe.

> [!NOTE]
> Możesz kontrolować, czy dane są domyślnie buforowane dla wszystkich pól, ustawiając [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Dane są mapowane między typu DAO_BYTES w DAO i Type [CByteArray](cbytearray-class.md) w zestawie rekordów.

### <a name="example"></a>Przykład

Zobacz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao. h

## <a name="dfx_bool"></a><a name="dfx_bool"></a>DFX_Bool

Przenosi dane logiczne między elementami członkowskimi danych pola obiektu [CDaoRecordset](cdaorecordset-class.md) i kolumnami rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI DFX_Bool(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BOOL& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji.

*szName*<br/>
Nazwa kolumny danych.

*wartościami*<br/>
Wartość przechowywana we wskazanym elemencie członkowskim danych — wartość do przeniesienia. W przypadku transferu z zestawu rekordów do źródła danych wartość typu BOOL jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zestawu rekordów wartość jest przechowywana w określonym elemencie członkowskim danych.

*dwBindOptions*<br/>
Opcja umożliwiająca korzystanie z mechanizmu podwójnego buforowania MFC w celu wykrywania pól zestawu rekordów, które uległy zmianie. Wartość domyślna AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania. Druga możliwa wartość to AFX_DAO_DISABLE_FIELD_CACHE. Jeśli określisz tę wartość, MFC nie sprawdza tego pola. Musisz wywołać `SetFieldDirty` i `SetFieldNull` samodzielnie.

> [!NOTE]
> Można kontrolować, czy dane są domyślnie buforowane, przez ustawienie [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Dane są mapowane między DAO_BOOL typu w DAO i Type BOOL w zestawie rekordów.

### <a name="example"></a>Przykład

Zobacz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao. h

## <a name="dfx_byte"></a><a name="dfx_byte"></a>DFX_Byte

Przenosi pojedyncze bajty między elementami członkowskimi danych pola obiektu [CDaoRecordset](cdaorecordset-class.md) a kolumnami rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI DFX_Byte(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BYTE& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji.

*szName*<br/>
Nazwa kolumny danych.

*wartościami*<br/>
Wartość przechowywana we wskazanym elemencie członkowskim danych — wartość do przeniesienia. W przypadku transferu z zestawu rekordów do źródła danych wartość typu BYTE jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zestawu rekordów wartość jest przechowywana w określonym elemencie członkowskim danych.

*dwBindOptions*<br/>
Opcja umożliwiająca korzystanie z mechanizmu podwójnego buforowania MFC w celu wykrywania pól zestawu rekordów, które uległy zmianie. Wartość domyślna AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania. Druga możliwa wartość to AFX_DAO_DISABLE_FIELD_CACHE. Jeśli określisz tę wartość, MFC nie sprawdza tego pola. Musisz wywołać `SetFieldDirty` i `SetFieldNull` samodzielnie.

> [!NOTE]
> Można kontrolować, czy dane są domyślnie buforowane, przez ustawienie [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Dane są mapowane między typu DAO_BYTES w DAO i Type BYTE w zestawie rekordów.

### <a name="example"></a>Przykład

Zobacz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao. h

## <a name="dfx_currency"></a><a name="dfx_currency"></a>DFX_Currency

Przenosi dane walutowe między elementami członkowskimi danych pola obiektu [CDaoRecordset](cdaorecordset-class.md) a kolumnami rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI DFX_Currency(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleCurrency& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji.

*szName*<br/>
Nazwa kolumny danych.

*wartościami*<br/>
Wartość przechowywana we wskazanym elemencie członkowskim danych — wartość do przeniesienia. W przypadku transferu z zestawu rekordów do źródła danych ta wartość jest pobierana z określonego elementu członkowskiego danych typu [COleCurrency](colecurrency-class.md). W przypadku transferu ze źródła danych do zestawu rekordów wartość jest przechowywana w określonym elemencie członkowskim danych.

*dwBindOptions*<br/>
Opcja umożliwiająca korzystanie z mechanizmu podwójnego buforowania MFC w celu wykrywania pól zestawu rekordów, które uległy zmianie. Wartość domyślna AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania. Druga możliwa wartość to AFX_DAO_DISABLE_FIELD_CACHE. Jeśli określisz tę wartość, MFC nie sprawdza tego pola. Musisz wywołać `SetFieldDirty` i `SetFieldNull` samodzielnie.

> [!NOTE]
> Można kontrolować, czy dane są domyślnie buforowane, przez ustawienie [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Dane są mapowane między typu DAO_CURRENCY w DAO i Type [COleCurrency](colecurrency-class.md) w zestawie rekordów.

### <a name="example"></a>Przykład

Zobacz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao. h

## <a name="dfx_datetime"></a><a name="dfx_datetime"></a>DFX_DateTime

Przenosi dane dotyczące czasu i daty między elementami członkowskimi danych pola obiektu [CDaoRecordset](cdaorecordset-class.md) i kolumnami rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI DFX_DateTime(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleDateTime& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji.

*szName*<br/>
Nazwa kolumny danych.

*wartościami*<br/>
Wartość przechowywana we wskazanym elemencie członkowskim danych — wartość do przeniesienia. Funkcja przyjmuje odwołanie do obiektu [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) . W przypadku transferu z zestawu rekordów do źródła danych ta wartość jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zestawu rekordów wartość jest przechowywana w określonym elemencie członkowskim danych.

*dwBindOptions*<br/>
Opcja umożliwiająca korzystanie z mechanizmu podwójnego buforowania MFC w celu wykrywania pól zestawu rekordów, które uległy zmianie. Wartość domyślna AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania. Druga możliwa wartość to AFX_DAO_DISABLE_FIELD_CACHE. Jeśli określisz tę wartość, MFC nie sprawdza tego pola. Musisz wywołać `SetFieldDirty` i `SetFieldNull` samodzielnie.

> [!NOTE]
> Można kontrolować, czy dane są domyślnie buforowane, przez ustawienie [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Dane są mapowane między typu DAO_DATE w DAO i Type [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) w zestawie rekordów.

> [!NOTE]
> `COleDateTime`zastępuje [CTime](../../atl-mfc-shared/reference/ctime-class.md) i TIMESTAMP_STRUCT w tym celu w klasach DAO. `CTime`i TIMESTAMP_STRUCT są nadal używane dla klas dostępu do danych opartych na ODBC.

### <a name="example"></a>Przykład

Zobacz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao. h

## <a name="dfx_double"></a><a name="dfx_double"></a>DFX_Double

Przenosi **podwójne dane zmiennoprzecinkowe** między elementami członkowskimi danych pola obiektu [CDaoRecordset](cdaorecordset-class.md) a kolumnami rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI DFX_Double(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   double& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji.

*szName*<br/>
Nazwa kolumny danych.

*wartościami*<br/>
Wartość przechowywana we wskazanym elemencie członkowskim danych — wartość do przeniesienia. W przypadku transferu z zestawu rekordów do źródła danych wartość typu **`double`** jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zestawu rekordów wartość jest przechowywana w określonym elemencie członkowskim danych.

*dwBindOptions*<br/>
Opcja umożliwiająca korzystanie z mechanizmu podwójnego buforowania MFC w celu wykrywania pól zestawu rekordów, które uległy zmianie. Wartość domyślna AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania. Druga możliwa wartość to AFX_DAO_DISABLE_FIELD_CACHE. Jeśli określisz tę wartość, MFC nie sprawdza tego pola. Musisz wywołać `SetFieldDirty` i `SetFieldNull` samodzielnie.

> [!NOTE]
> Można kontrolować, czy dane są domyślnie buforowane, przez ustawienie [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Dane są mapowane między DAO_R8 typu w DAO i typu **Double zmiennoprzecinkowe** w zestawie rekordów.

### <a name="example"></a>Przykład

Zobacz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao. h

## <a name="dfx_long"></a><a name="dfx_long"></a>DFX_Long

Przesyła dane typu Long Integer między elementami członkowskimi danych pola obiektu [CDaoRecordset](cdaorecordset-class.md) i kolumnami rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI DFX_Long(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   long& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji.

*szName*<br/>
Nazwa kolumny danych.

*wartościami*<br/>
Wartość przechowywana we wskazanym elemencie członkowskim danych — wartość do przeniesienia. W przypadku transferu z zestawu rekordów do źródła danych wartość typu **`long`** jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zestawu rekordów wartość jest przechowywana w określonym elemencie członkowskim danych.

*dwBindOptions*<br/>
Opcja umożliwiająca korzystanie z mechanizmu podwójnego buforowania MFC w celu wykrywania pól zestawu rekordów, które uległy zmianie. Wartość domyślna AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania. Druga możliwa wartość to AFX_DAO_DISABLE_FIELD_CACHE. Jeśli określisz tę wartość, MFC nie sprawdza tego pola. Musisz wywołać `SetFieldDirty` i `SetFieldNull` samodzielnie.

> [!NOTE]
> Można kontrolować, czy dane są domyślnie buforowane, przez ustawienie [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Dane są mapowane między typu DAO_I4 w DAO i Type **`long`** w zestawie rekordów.

### <a name="example"></a>Przykład

Zobacz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao. h

## <a name="dfx_longbinary"></a><a name="dfx_longbinary"></a>DFX_LongBinary

**Ważne** Zaleca się używanie [DFX_Binary](#dfx_binary) zamiast tej funkcji.

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI DFX_LongBinary(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CLongBinary& value,
   DWORD dwPreAllocSize = AFX_DAO_LONGBINARY_DEFAULT_SIZE,
   DWORD dwBindOptions = 0);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji.

*szName*<br/>
Nazwa kolumny danych.

*wartościami*<br/>
Wartość przechowywana we wskazanym elemencie członkowskim danych — wartość do przeniesienia. W przypadku transferu z zestawu rekordów do źródła danych wartość typu [CLongBinary](clongbinary-class.md)jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zestawu rekordów wartość jest przechowywana w określonym elemencie członkowskim danych.

*dwPreAllocSize*<br/>
Platforma wstępnie przydzieli tę ilość pamięci. Jeśli dane są większe, struktura przydzieli więcej miejsca w miarę potrzeb. Aby zapewnić lepszą wydajność, ustaw ten rozmiar na wystarczająco dużą wartość, aby zapobiec ponownym alokacjom.

*dwBindOptions*<br/>
Opcja umożliwiająca korzystanie z mechanizmu podwójnego buforowania MFC w celu wykrywania pól zestawu rekordów, które uległy zmianie. Wartość domyślna, AFX_DISABLE_FIELD_CACHE, nie używa podwójnego buforowania. Druga możliwa wartość to AFX_DAO_ENABLE_FIELD_CACHE. Używa podwójnego buforowania i nie trzeba wykonywać dodatkowej pracy, aby oznaczyć pola jako zanieczyszczone lub zerowe. Ze względu na wydajność i pamięć należy unikać tej wartości, chyba że dane binarne są stosunkowo małe.

> [!NOTE]
> Można kontrolować, czy dane są domyślnie buforowane, przez ustawienie [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

`DFX_LongBinary`zapewnia zgodność z klasami MFC ODBC. `DFX_LongBinary`Funkcja przesyła dane binarne obiektów binarnych (BLOB) przy użyciu klasy `CLongBinary` między elementami członkowskimi danych pola obiektu [CDaoRecordset](cdaorecordset-class.md) a kolumnami rekordów rekordu w źródle danych. Dane są mapowane między typu DAO_BYTES w DAO i Type [CLongBinary](clongbinary-class.md) w zestawie rekordów.

### <a name="example"></a>Przykład

Zobacz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao. h

## <a name="dfx_short"></a><a name="dfx_short"></a>DFX_Short

Przenosi krótkie dane całkowite między elementami członkowskimi danych pola obiektu [CDaoRecordset](cdaorecordset-class.md) a kolumnami rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI DFX_Short(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   short& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji.

*szName*<br/>
Nazwa kolumny danych.

*wartościami*<br/>
Wartość przechowywana we wskazanym elemencie członkowskim danych — wartość do przeniesienia. W przypadku transferu z zestawu rekordów do źródła danych wartość typu **`short`** jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zestawu rekordów wartość jest przechowywana w określonym elemencie członkowskim danych.

*dwBindOptions*<br/>
Opcja umożliwiająca korzystanie z mechanizmu podwójnego buforowania MFC w celu wykrywania pól zestawu rekordów, które uległy zmianie. Wartość domyślna AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania. Druga możliwa wartość to AFX_DAO_DISABLE_FIELD_CACHE. Jeśli określisz tę wartość, MFC nie sprawdza tego pola. Musisz wywołać `SetFieldDirty` i `SetFieldNull` samodzielnie.

> [!NOTE]
> Można kontrolować, czy dane są domyślnie buforowane, przez ustawienie [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Dane są mapowane między typu DAO_I2 w DAO i Type **`short`** w zestawie rekordów.

> [!NOTE]
> `DFX_Short`jest równoważne [RFX_Int](#rfx_int) dla klas opartych na ODBC.

### <a name="example"></a>Przykład

Zobacz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao. h

## <a name="dfx_single"></a><a name="dfx_single"></a>DFX_Single

Przesyła dane zmiennoprzecinkowe między elementami członkowskimi danych pola obiektu [CDaoRecordset](cdaorecordset-class.md) a kolumnami rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI DFX_Single(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   float& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji.

*szName*<br/>
Nazwa kolumny danych.

*wartościami*<br/>
Wartość przechowywana we wskazanym elemencie członkowskim danych — wartość do przeniesienia. W przypadku transferu z zestawu rekordów do źródła danych wartość typu **`float`** jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zestawu rekordów wartość jest przechowywana w określonym elemencie członkowskim danych.

*dwBindOptions*<br/>
Opcja umożliwiająca korzystanie z mechanizmu podwójnego buforowania MFC w celu wykrywania pól zestawu rekordów, które uległy zmianie. Wartość domyślna AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania. Druga możliwa wartość to AFX_DAO_DISABLE_FIELD_CACHE. Jeśli określisz tę wartość, MFC nie sprawdza tego pola. Musisz wywołać `SetFieldDirty` i `SetFieldNull` samodzielnie.

> [!NOTE]
> Można kontrolować, czy dane są domyślnie buforowane, przez ustawienie [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Dane są mapowane między typu DAO_R4 w DAO i Type **`float`** w zestawie rekordów.

### <a name="example"></a>Przykład

Zobacz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao. h

## <a name="dfx_text"></a><a name="dfx_text"></a>DFX_Text

Przesyła `CString` dane między elementami członkowskimi danych pola obiektu [CDaoRecordset](cdaorecordset-class.md) i kolumnami rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI DFX_Text(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CString& value,
   int nPreAllocSize = AFX_DAO_TEXT_DEFAULT_SIZE,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje służące do definiowania kontekstu dla każdego wywołania funkcji.

*szName*<br/>
Nazwa kolumny danych.

*wartościami*<br/>
Wartość przechowywana we wskazanym elemencie członkowskim danych — wartość do przeniesienia. W przypadku transferu z zestawu rekordów do źródła danych wartość typu [CString](../../atl-mfc-shared/reference/cstringt-class.md)jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zestawu rekordów wartość jest przechowywana w określonym elemencie członkowskim danych.

*nPreAllocSize*<br/>
Platforma wstępnie przydzieli tę ilość pamięci. Jeśli dane są większe, struktura przydzieli więcej miejsca w miarę potrzeb. Aby zapewnić lepszą wydajność, ustaw ten rozmiar na wystarczająco dużą wartość, aby zapobiec ponownym alokacjom.

*dwBindOptions*<br/>
Opcja umożliwiająca korzystanie z mechanizmu podwójnego buforowania MFC w celu wykrywania pól zestawu rekordów, które uległy zmianie. Wartość domyślna AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania. Druga możliwa wartość to AFX_DAO_DISABLE_FIELD_CACHE. Jeśli określisz tę wartość, MFC nie sprawdza tego pola. Musisz samodzielnie wywołać [SetFieldDirty](cdaorecordset-class.md#setfielddirty) i [SetFieldNull](cdaorecordset-class.md#setfieldnull) .

> [!NOTE]
> Można kontrolować, czy dane są domyślnie buforowane, przez ustawienie [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Dane są mapowane między DAO_CHAR typu w elemencie DAO (lub, jeśli symbol _UNICODE jest zdefiniowany, DAO_WCHAR) i wpisz [CString](../../atl-mfc-shared/reference/cstringt-class.md) w zestawie rekordów.  n

### <a name="example"></a>Przykład

Ten przykład pokazuje kilka wywołań `DFX_Text` . Zwróć również uwagę na dwa wywołania [CDaoFieldExchange:: SetFieldType](cdaofieldexchange-class.md#setfieldtype). Należy napisać pierwsze wywołanie do `SetFieldType` i jego wywołanie **DFX** . Drugie wywołanie i powiązane z nim wywołania **DFX** są zwykle zapisywane przez kreatora kodu, który wygenerował klasę.

```cpp
void CCustSet::DoFieldExchange(CDaoFieldExchange* pFX)
{
   pFX->SetFieldType(CDaoFieldExchange::param);
   DFX_Text(pFX, _T("Param"), m_strParam);
   pFX->SetFieldType(CDaoFieldExchange::outputColumn);
   DFX_Short(pFX, _T("EmployeeID"), m_EmployeeID);
   DFX_Text(pFX, _T("LastName"), m_LastName);
   DFX_Short(pFX, _T("Age"), m_Age);
   DFX_DateTime(pFX, _T("hire_date"), m_hire_date);
   DFX_DateTime(pFX, _T("termination_date"), m_termination_date);

   CDaoRecordset::DoFieldExchange(pFX);
}
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao. h

## <a name="see-also"></a>Zobacz także

[Makra i Globals](mfc-macros-and-globals.md)<br/>
[CRecordset::D oFieldExchange](crecordset-class.md#dofieldexchange)<br/>
[CRecordset::D oBulkFieldExchange](crecordset-class.md#dobulkfieldexchange)<br/>
[CDaoRecordset::D oFieldExchange](cdaorecordset-class.md#dofieldexchange)
