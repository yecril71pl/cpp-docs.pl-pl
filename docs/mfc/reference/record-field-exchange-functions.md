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
ms.openlocfilehash: bfd3ba64a33547b8a27e0f3bc896f39c94486464
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372981"
---
# <a name="record-field-exchange-functions"></a>Funkcje wymiany pól rekordów

W tym temacie wymieniono funkcje wymiany pól rekordów (RFX, bulk RFX i DFX) używane do automatyzacji przesyłania danych między obiektem zestawie rekordów a jego źródłem danych oraz do wykonywania innych operacji na danych.

Jeśli używasz klas opartych na ODBC i zaimplementowano pobieranie wiersza `DoBulkFieldExchange` zbiorczego, `CRecordset` należy ręcznie zastąpić funkcję elementu członkowskiego, wywołując funkcje RFX luzem dla każdego elementu członkowskiego danych odpowiadającego kolumnie źródła danych.

Jeśli pobieranie wierszy zbiorczych nie zostało zaimplementowane w klasach opartych na odbc lub jeśli są używane klasy `DoFieldExchange` oparte `CRecordset` na `CDaoRecordset` DAO (przestarzałe), następnie ClassWizard zastąpi funkcję elementu członkowskiego lub wywołując funkcje RFX (dla klas ODBC) lub DFX (dla klas DAO) dla każdego elementu członkowskiego danych pola w zbiorze rekordów.

Funkcje wymiany pól rekordu przesyłają `DoFieldExchange` dane `DoBulkFieldExchange`za każdym razem, gdy wywoła ją framework lub . Każda funkcja przesyła określony typ danych.

Aby uzyskać więcej informacji na temat sposobu ich wykorzystania, zobacz artykuły [Record Field Exchange: How RFX Works (ODBC)](../../data/odbc/record-field-exchange-how-rfx-works.md). Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

W przypadku kolumn danych, które wiążą się dynamicznie, można również wywołać funkcje RFX lub DFX samodzielnie, jak wyjaśniono w artykułach [Zestaw rekordów: Dynamicznie wiążące kolumny danych (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md). Ponadto można napisać własne niestandardowe procedury RFX lub DFX, jak wyjaśniono w notatce technicznej [43](../../mfc/tn043-rfx-routines.md) (dla ODBC) i notach technicznych [53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) (dla DAO).

Na przykład rfx i luzem RFX funkcje pojawiające się w `DoFieldExchange` i `DoBulkFieldExchange` funkcje, zobacz [RFX_Text](#rfx_text) i [RFX_Text_Bulk]#rfx_text_bulk). Funkcje DFX są bardzo podobne do funkcji RFX.

### <a name="rfx-functions-odbc"></a>Funkcje RFX (ODBC)

|||
|-|-|
|[RFX_Binary](#rfx_binary)|Przenosi tablice bajtów typu [CByteArray](cbytearray-class.md).|
|[RFX_Bool](#rfx_bool)|Przesyła dane logiczne.|
|[RFX_Byte](#rfx_byte)|Przesyła pojedynczy bajt danych.|
|[RFX_Date](#rfx_date)|Przesyła dane o czasie i dacie za pomocą [CTime](../../atl-mfc-shared/reference/ctime-class.md) lub TIMESTAMP_STRUCT.|
|[RFX_Double](#rfx_double)|Przesyła dane float o podwójnej precyzji.|
|[RFX_Int](#rfx_int)|Przesyła dane całkowite.|
|[RFX_Long](#rfx_long)|Przesyła długie dane całkowite.|
|[RFX_LongBinary](#rfx_longbinary)|Przesyła dane dużego obiektu binarnego (BLOB) z obiektem klasy [CLongBinary.](clongbinary-class.md)|
|[RFX_Single](#rfx_single)|Przesyła dane float.|
|[RFX_Text](#rfx_text)|Przesyła dane ciągu.|

### <a name="bulk-rfx-functions-odbc"></a>Zbiorcze funkcje RFX (ODBC)

|||
|-|-|
|[RFX_Binary_Bulk](#rfx_binary_bulk)|Przesyła tablice danych bajtów.|
|[RFX_Bool_Bulk](#rfx_bool_bulk)|Przesyła tablice danych logicznych.|
|[RFX_Byte_Bulk](#rfx_byte_bulk)|Przesyła tablice pojedynczych bajtów.|
|[RFX_Date_Bulk](#rfx_date_bulk)|Przesyła tablice danych typu TIMESTAMP_STRUCT.|
|[RFX_Double_Bulk](#rfx_double_bulk)|Przesyła tablice danych zmiennoprzecinkowych o podwójnej precyzji.|
|[RFX_Int_Bulk](#rfx_int_bulk)|Przesyła tablice danych całkowitych.|
|[RFX_Long_Bulk](#rfx_long_bulk)|Przesyła tablice długich danych całkowitych.|
|[RFX_Single_Bulk](#rfx_single_bulk)|Przesyła tablice danych zmiennoprzecinkowych.|
|[RFX_Text_Bulk](#rfx_text_bulk)|Przesyła tablice danych typu LPSTR.|

### <a name="dfx-functions-dao"></a>Funkcje DFX (DAO)

|||
|-|-|
|[DFX_Binary](#dfx_binary)|Przenosi tablice bajtów typu [CByteArray](cbytearray-class.md).|
|[DFX_Bool](#dfx_bool)|Przesyła dane logiczne.|
|[DFX_Byte](#dfx_byte)|Przesyła pojedynczy bajt danych.|
|[DFX_Currency](#dfx_currency)|Przekazuje dane walutowe typu [COleCurrency](colecurrency-class.md).|
|[DFX_DateTime](#dfx_datetime)|Przesyła dane o czasie i dacie typu [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md).|
|[DFX_Double](#dfx_double)|Przesyła dane float o podwójnej precyzji.|
|[DFX_Long](#dfx_long)|Przesyła długie dane całkowite.|
|[DFX_LongBinary](#dfx_longbinary)|Przesyła dane dużego obiektu binarnego (BLOB) z obiektem `CLongBinary` klasy. W przypadku DAO zaleca się używanie [DFX_Binary.](#dfx_binary)|
|[DFX_Short](#dfx_short)|Przesyła krótkie dane całkowite.|
|[DFX_Single](#dfx_single)|Przesyła dane float.|
|[DFX_Text](#dfx_text)|Przesyła dane ciągu.|

=============================================

## <a name="rfx_binary"></a><a name="rfx_binary"></a>RFX_Binary

Przesyła tablice bajtów między elementami `CRecordset` elementów członkowskich danych pola obiektu a kolumnami rekordu w źródle danych typu ODBC SQL_BINARY, SQL_VARBINARY lub SQL_LONGVARBINARY.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Binary(
   CFieldExchange* pFX,
   const char* szName,
   CByteArray& value,
   int nMaxLength = 255);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji `CFieldExchange` na temat operacji, które obiekt może określić, zobacz artykuł [Wymiana pól rekordu: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*Szname*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana we wskazanym człowianym danych — wartość, która ma zostać przeniesiona. Dla transferu z zestawu rekordów do źródła danych wartość typu [CByteArray](cbytearray-class.md)jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zbioru rekordów wartość jest przechowywana w określonym elementów członkowskich danych.

*nMaxLength*<br/>
Maksymalna dozwolona długość ciągu lub tablicy, która jest przesyłana. Domyślna wartość *nMaxLength* wynosi 255. Wartości prawne to od 1 do INT_MAX. Struktura przydziela tę ilość miejsca dla danych. Aby uzyskać najlepszą wydajność, przekaż wartość wystarczająco dużą, aby pomieścić największy element danych, którego oczekujesz.

### <a name="remarks"></a>Uwagi

Dane w źródle danych tych typów są mapowane do i od typu `CByteArray` w zbiorze rekordów.

### <a name="example"></a>Przykład

Zobacz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_bool"></a><a name="rfx_bool"></a>RFX_Bool

Przesyła dane logiczne między elementami `CRecordset` elementów członkowskich danych pola obiektu a kolumnami rekordu w źródle danych typu ODBC SQL_BIT.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Bool(
   CFieldExchange* pFX,
   const char* szName,
   BOOL& value);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji `CFieldExchange` na temat operacji, które obiekt może określić, zobacz artykuł [Wymiana pól rekordu: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*Szname*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana we wskazanym człowianym danych — wartość, która ma zostać przeniesiona. W przypadku transferu z zestawu rekordów do źródła danych wartość typu BOOL jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zbioru rekordów wartość jest przechowywana w określonym elementów członkowskich danych.

### <a name="example"></a>Przykład

Zobacz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_byte"></a><a name="rfx_byte"></a>RFX_Byte

Przesyła pojedyncze bajty między elementami członkowskich danych pola `CRecordset` obiektu a kolumnami rekordu w źródle danych typu ODBC SQL_TINYINT.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Byte(
   CFieldExchange* pFX,
   const char* szName,
   BYTE& value);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji `CFieldExchange` na temat operacji, które obiekt może określić, zobacz artykuł [Wymiana pól rekordu: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*Szname*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana we wskazanym człowianym danych — wartość, która ma zostać przeniesiona. W przypadku transferu z zestawu rekordów do źródła danych wartość typu BYTE jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zbioru rekordów wartość jest przechowywana w określonym elementów członkowskich danych.

### <a name="example"></a>Przykład

Zobacz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_date"></a><a name="rfx_date"></a>RFX_Date

Przesyła `CTime` lub TIMESTAMP_STRUCT dane między elementami elementów członkowskich danych pola `CRecordset` obiektu a kolumnami rekordu w źródle danych typu ODBC SQL_DATE, SQL_TIME lub SQL_TIMESTAMP.

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

*Pfx*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji `CFieldExchange` na temat operacji, które obiekt może określić, zobacz artykuł [Wymiana pól rekordu: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*Szname*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana we wskazanym człowiańce danych; wartości, która ma zostać przeniesiona. Różne wersje funkcji przyjmują różne typy danych dla wartości:

Pierwsza wersja funkcji przyjmuje odwołanie do [CTime](../../atl-mfc-shared/reference/ctime-class.md) obiektu. W przypadku transferu z zestawu rekordów do źródła danych ta wartość jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zbioru rekordów wartość jest przechowywana w określonym elementów członkowskich danych.

Druga wersja funkcji przyjmuje odwołanie do `TIMESTAMP_STRUCT` struktury. Należy skonfigurować tę strukturę samodzielnie przed wywołaniem. Dla tej wersji nie jest dostępna obsługa wymiany danych dialogowych (DDX), ani obsługa kreatora kodu. Trzecia wersja funkcji działa podobnie do pierwszej wersji, z tą różnicą, że przyjmuje odwołanie do [obiektu COleDateTime.](../../atl-mfc-shared/reference/coledatetime-class.md)

### <a name="remarks"></a>Uwagi

Wersja `CTime` funkcji nakłada obciążenie niektórych przetwarzania pośredniego i ma nieco ograniczony zakres. Jeśli którykolwiek z tych czynników jest zbyt ograniczający, użyj drugiej wersji funkcji. Należy jednak pamiętać, że jego brak kreatora kodu i obsługi DDX i wymóg, aby skonfigurować strukturę samodzielnie.

### <a name="example"></a>Przykład

Zobacz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_double"></a><a name="rfx_double"></a>RFX_Double

Przesyła **dane dwuskładników zmiennoprzecrzeń** między elementami elementów członkowskich danych pola `CRecordset` obiektu a kolumnami rekordu w źródle danych typu ODBC SQL_DOUBLE.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Double(
   CFieldExchange* pFX,
   const char* szName,
   double& value);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji `CFieldExchange` na temat operacji, które obiekt może określić, zobacz artykuł [Wymiana pól rekordu: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*Szname*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana we wskazanym człowianym danych — wartość, która ma zostać przeniesiona. Dla transferu z zestawu rekordów do źródła danych wartość typu **double**, jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zbioru rekordów wartość jest przechowywana w określonym elementów członkowskich danych.

### <a name="example"></a>Przykład

Zobacz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_int"></a><a name="rfx_int"></a>RFX_Int

Przesyła dane całkowite między elementami elementów członkowskich danych pola `CRecordset` obiektu a kolumnami rekordu w źródle danych typu ODBC SQL_SMALLINT.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji `CFieldExchange` na temat operacji, które obiekt może określić, zobacz artykuł [Wymiana pól rekordu: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*Szname*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana we wskazanym człowianym danych — wartość, która ma zostać przeniesiona. Dla transferu z zestawu rekordów do źródła danych wartość typu **int**jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zbioru rekordów wartość jest przechowywana w określonym elementów członkowskich danych.

### <a name="example"></a>Przykład

Zobacz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_long"></a><a name="rfx_long"></a>RFX_Long

Przesyła długie dane całkowite między elementami `CRecordset` elementów członkowskich danych pola obiektu a kolumnami rekordu w źródle danych typu ODBC SQL_INTEGER.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Long(
   CFieldExchange* pFX,
   const char* szName,
   LONG&
value );
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji `CFieldExchange` na temat operacji, które obiekt może określić, zobacz artykuł [Wymiana pól rekordu: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*Szname*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana we wskazanym człowianym danych — wartość, która ma zostać przeniesiona. W przypadku transferu z zestawu rekordów do źródła danych wartość typu **long**jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zbioru rekordów wartość jest przechowywana w określonym elementów członkowskich danych.

### <a name="example"></a>Przykład

Zobacz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_longbinary"></a><a name="rfx_longbinary"></a>RFX_LongBinary

Przesyła dane dużego obiektu binarnego (BLOB) przy użyciu klasy `CRecordset` [CLongBinary](clongbinary-class.md) między elementami elementów członkowskich danych pola obiektu a kolumnami rekordu w źródle danych typu ODBC SQL_LONGVARBINARY lub SQL_LONGVARCHAR.

### <a name="syntax"></a>Składnia

```cpp
void RFX_LongBinary(
   CFieldExchange* pFX,
   const char* szName,
   CLongBinary& value);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji `CFieldExchange` na temat operacji, które obiekt może określić, zobacz artykuł [Wymiana pól rekordu: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*Szname*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana we wskazanym człowianym danych — wartość, która ma zostać przeniesiona. Dla transferu z zestawu rekordów do źródła `CLongBinary`danych, wartość typu , jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zbioru rekordów wartość jest przechowywana w określonym elementów członkowskich danych.

### <a name="example"></a>Przykład

Zobacz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_single"></a><a name="rfx_single"></a>RFX_Single

Przesyła dane zmiennoprzecinkowe między `CRecordset` elementami elementów członkowskich danych pola obiektu a kolumnami rekordu w źródle danych typu ODBC SQL_REAL.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Single(
   CFieldExchange* pFX,
   const char* szName,
   float& value);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji `CFieldExchange` na temat operacji, które obiekt może określić, zobacz artykuł [Wymiana pól rekordu: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*Szname*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana we wskazanym człowianym danych — wartość, która ma zostać przeniesiona. Dla transferu z zestawu rekordów do źródła danych wartość **typu float**, jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zbioru rekordów wartość jest przechowywana w określonym elementów członkowskich danych.

### <a name="example"></a>Przykład

Zobacz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_text"></a><a name="rfx_text"></a>RFX_Text

Przesyła `CString` dane między elementami `CRecordset` elementów członkowskich danych pola obiektu i kolumnami rekordu w źródle danych typu ODBC SQL_LONGVARCHAR, SQL_CHAR, SQL_VARCHAR, SQL_DECIMAL lub SQL_NUMERIC.

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

*Pfx*<br/>
Wskaźnik do obiektu klasy `CFieldExchange`. Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji `CFieldExchange` na temat operacji, które obiekt może określić, zobacz artykuł [Wymiana pól rekordu: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*Szname*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana we wskazanym człowianym danych — wartość, która ma zostać przeniesiona. Dla transferu z zestawu rekordów do źródła `CString`danych, wartość typu , jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zbioru rekordów wartość jest przechowywana w określonym elementów członkowskich danych.

*nMaxLength*<br/>
Maksymalna dozwolona długość ciągu lub tablicy, która jest przesyłana. Domyślna wartość *nMaxLength* wynosi 255. Wartości prawne to od 1 do INT_MAX). Struktura przydziela tę ilość miejsca dla danych. Aby uzyskać najlepszą wydajność, przekaż wartość wystarczająco dużą, aby pomieścić największy element danych, którego oczekujesz.

*nColumnType*<br/>
Używany głównie do parametrów. Liczba całkowita wskazująca typ danych parametru. Typ jest typem danych ODBC formularza **SQL_XXX**.

*nSkada*<br/>
Określa skalę dla wartości typu ODBC SQL_DECIMAL lub SQL_NUMERIC. *nSkala* jest przydatna tylko przy ustawianiu wartości parametrów. Aby uzyskać więcej informacji, zobacz temat "Precyzja, skala, długość i rozmiar ekranu" w dodatku D *odwołania programisty SDK ODBC*.

### <a name="remarks"></a>Uwagi

Dane w źródle danych wszystkich tych typów są `CString` mapowane do i z w akuli.

### <a name="example"></a>Przykład

W tym przykładzie `RFX_Text`przedstawiono kilka wywołań do . Zwróć również uwagę `CFieldExchange::SetFieldType`na dwa połączenia do . Dla parametrów, które `SetFieldType` należy napisać wywołanie i jego wywołanie RFX. Wywołanie kolumny wyjściowej i skojarzone z nim wywołania RFX są zwykle zapisywane przez kreatora kodu.

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

**Nagłówek:** afxdb.h

## <a name="rfx_binary_bulk"></a><a name="rfx_binary_bulk"></a>RFX_Binary_Bulk

Przenosi wiele wierszy danych bajtów z kolumny źródła danych ODBC `CRecordset`do odpowiedniej tablicy w obiekcie pochodnym.

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

*Pfx*<br/>
Wskaźnik do [obiektu CFieldExchange.](cfieldexchange-class.md) Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [Wymiana pól rekordu: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*Szname*<br/>
Nazwa kolumny danych.

*prgByteVals (Równy zw.*<br/>
Wskaźnik do tablicy wartości BYTE. Ta tablica będzie przechowywać dane, które mają być przesyłane ze źródła danych do zestawu rekordów.

*PrgLengths (Środki na zm.*<br/>
Wskaźnik do tablicy długich liczby całkowitych. Ta tablica będzie przechowywać długość w bajtach każdej wartości w tablicy wskazywalnej przez *prgByteVals*. Należy zauważyć, że wartość SQL_NULL_DATA będą przechowywane, jeśli odpowiedni element danych zawiera wartość Null. Aby uzyskać więcej informacji, zobacz `SQLBindCol` funkcję INTERFEJSU API ODBC w *odwołaniu programisty SDK ODBC*.

*nMaxLength*<br/>
Maksymalna dozwolona długość wartości przechowywanych w tablicy wskazywalnej przez *prgByteVals*. Aby upewnić się, że dane nie zostaną obcięty, przekazać wartość wystarczająco duże, aby pomieścić największy element danych, których oczekujesz.

### <a name="remarks"></a>Uwagi

Kolumna źródła danych może mieć typ ODBC SQL_BINARY, SQL_VARBINARY lub SQL_LONGVARBINARY. Zestaw rekordów musi definiować element członkowski danych pola wskaźnika typu do BYTE.

Jeśli zainicjować *prgByteVals* i *prgLengths* do NULL, a następnie tablice, które wskazują na zostaną przydzielone automatycznie, o rozmiarach równych rozmiarze zestawu wierszy.

> [!NOTE]
> Zbiorcza wymiana pól rekordów przenosi tylko dane ze źródła danych do obiektu zestaw rekordów. Aby można było zaktualizować swój plik recordset, należy `SQLSetPos`użyć funkcji INTERFEJSU API ODBC .

Aby uzyskać więcej informacji, zobacz artykuły [Recordset: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Przykład

Zobacz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_bool_bulk"></a><a name="rfx_bool_bulk"></a>RFX_Bool_Bulk

Przenosi wiele wierszy danych logicznych z kolumny źródła danych ODBC `CRecordset`do odpowiedniej tablicy w obiekcie pochodnym.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Bool_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BOOL** prgBoolVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Wskaźnik do [obiektu CFieldExchange.](cfieldexchange-class.md) Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [Wymiana pól rekordu: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*Szname*<br/>
Nazwa kolumny danych.

*prgBoolVals (PrgBoolVals)*<br/>
Wskaźnik do tablicy wartości BOOL. Ta tablica będzie przechowywać dane, które mają być przesyłane ze źródła danych do zestawu rekordów.

*PrgLengths (Środki na zm.*<br/>
Wskaźnik do tablicy długich liczby całkowitych. Ta tablica będzie przechowywać długość w bajtach każdej wartości w tablicy wskazywalnej przez *prgBoolVals*. Należy zauważyć, że wartość SQL_NULL_DATA będą przechowywane, jeśli odpowiedni element danych zawiera wartość Null. Aby uzyskać więcej informacji, zobacz `SQLBindCol` funkcję INTERFEJSU API ODBC w *odwołaniu programisty SDK ODBC*.

### <a name="remarks"></a>Uwagi

Kolumna źródła danych musi mieć typ ODBC SQL_BIT. Zestaw rekordów musi definiować element członkowski danych pola wskaźnika typu do BOOL.

Jeśli zainicjować *prgBoolVals* i *prgLengths* do NULL, a następnie tablice, które wskazują na zostaną przydzielone automatycznie, o rozmiarach równych rozmiarze zestawu wierszy.

> [!NOTE]
> Zbiorcza wymiana pól rekordów przenosi tylko dane ze źródła danych do obiektu zestaw rekordów. Aby można było aktualizować swój plik recordset, `SQLSetPos`należy użyć funkcji INTERFEJSU API ODBC .

Aby uzyskać więcej informacji, zobacz artykuły [Recordset: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Przykład

Zobacz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_byte_bulk"></a><a name="rfx_byte_bulk"></a>RFX_Byte_Bulk

Przenosi wiele wierszy pojedynczych bajtów z kolumny źródła danych ODBC do odpowiedniej tablicy w obiekcie pochodnym. `CRecordset`

### <a name="syntax"></a>Składnia

```cpp
void RFX_Byte_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BYTE** prgByteVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Wskaźnik do [obiektu CFieldExchange.](cfieldexchange-class.md) Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [Wymiana pól rekordu: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*Szname*<br/>
Nazwa kolumny danych.

*prgByteVals (Równy zw.*<br/>
Wskaźnik do tablicy wartości BYTE. Ta tablica będzie przechowywać dane, które mają być przesyłane ze źródła danych do zestawu rekordów.

*PrgLengths (Środki na zm.*<br/>
Wskaźnik do tablicy długich liczby całkowitych. Ta tablica będzie przechowywać długość w bajtach każdej wartości w tablicy wskazywalnej przez *prgByteVals*. Należy zauważyć, że wartość SQL_NULL_DATA będą przechowywane, jeśli odpowiedni element danych zawiera wartość Null. Aby uzyskać więcej informacji, zobacz `SQLBindCol` funkcję INTERFEJSU API ODBC w *odwołaniu programisty SDK ODBC*.

### <a name="remarks"></a>Uwagi

Kolumna źródła danych musi mieć typ ODBC SQL_TINYINT. Zestaw rekordów musi definiować element członkowski danych pola wskaźnika typu do BYTE.

Jeśli zainicjować *prgByteVals* i *prgLengths* do NULL, a następnie tablice, które wskazują na zostaną przydzielone automatycznie, o rozmiarach równych rozmiarze zestawu wierszy.

> [!NOTE]
> Zbiorcza wymiana pól rekordów przenosi tylko dane ze źródła danych do obiektu zestaw rekordów. Aby można było aktualizować swój plik recordset, `SQLSetPos`należy użyć funkcji INTERFEJSU API ODBC .

Aby uzyskać więcej informacji, zobacz artykuły [Recordset: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Przykład

Zobacz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_date_bulk"></a><a name="rfx_date_bulk"></a>RFX_Date_Bulk

Przenosi wiele wierszy TIMESTAMP_STRUCT danych z kolumny źródła danych ODBC do odpowiedniej `CRecordset`tablicy w obiekcie pochodnym.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Date_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   TIMESTAMP_STRUCT** prgTSVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Wskaźnik do [obiektu CFieldExchange.](cfieldexchange-class.md) Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [Wymiana pól rekordu: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*Szname*<br/>
Nazwa kolumny danych.

*prgTSVals (syt.*<br/>
Wskaźnik do tablicy wartości TIMESTAMP_STRUCT. Ta tablica będzie przechowywać dane, które mają być przesyłane ze źródła danych do zestawu rekordów. Aby uzyskać więcej informacji na temat TIMESTAMP_STRUCT typu danych, zobacz temat "Typy danych C" w dodatku D *odwołania programisty SDK ODBC*.

*PrgLengths (Środki na zm.*<br/>
Wskaźnik do tablicy długich liczby całkowitych. Ta tablica będzie przechowywać długość w bajtach każdej wartości w tablicy wskazywalnej przez *prgTSVals*. Należy zauważyć, że wartość SQL_NULL_DATA będą przechowywane, jeśli odpowiedni element danych zawiera wartość Null. Aby uzyskać więcej informacji, zobacz `SQLBindCol` funkcję INTERFEJSU API ODBC w *odwołaniu programisty SDK ODBC*.

### <a name="remarks"></a>Uwagi

Kolumna źródła danych może mieć typ ODBC SQL_DATE, SQL_TIME lub SQL_TIMESTAMP. Zestaw rekordów musi definiować element członkowski danych pola wskaźnika typu, aby TIMESTAMP_STRUCT.

Jeśli zainicjować *prgTSVals* i *prgLengths* do NULL, a następnie tablice, które wskazują na zostaną przydzielone automatycznie, o rozmiarach równych rozmiarze zestawu wierszy.

> [!NOTE]
> Zbiorcza wymiana pól rekordów przenosi tylko dane ze źródła danych do obiektu zestaw rekordów. Aby można było aktualizować swój plik recordset, `SQLSetPos`należy użyć funkcji INTERFEJSU API ODBC .

Aby uzyskać więcej informacji, zobacz artykuły [Recordset: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Przykład

Zobacz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_double_bulk"></a><a name="rfx_double_bulk"></a>RFX_Double_Bulk

Przenosi wiele wierszy danych o podwójnej precyzji, zmiennoprzecinkowych z kolumny `CRecordset`źródła danych ODBC do odpowiedniej tablicy w obiekcie pochodnym.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Double_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   double** prgDblVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Wskaźnik do [obiektu CFieldExchange.](cfieldexchange-class.md) Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [Wymiana pól rekordu: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*Szname*<br/>
Nazwa kolumny danych.

*prgDblVals (sydblVals)*<br/>
Wskaźnik do tablicy **podwójnych** wartości. Ta tablica będzie przechowywać dane, które mają być przesyłane ze źródła danych do zestawu rekordów.

*PrgLengths (Środki na zm.*<br/>
Wskaźnik do tablicy długich liczby całkowitych. Ta tablica będzie przechowywać długość w bajtach każdej wartości w tablicy wskazywalnej przez *prgDblVals*. Należy zauważyć, że wartość SQL_NULL_DATA będą przechowywane, jeśli odpowiedni element danych zawiera wartość Null. Aby uzyskać więcej informacji, zobacz `SQLBindCol` funkcję INTERFEJSU API ODBC w *odwołaniu programisty SDK ODBC*.

### <a name="remarks"></a>Uwagi

Kolumna źródła danych musi mieć typ ODBC SQL_DOUBLE. Zestaw rekordów musi definiować element członkowski danych pola wskaźnika typu, aby **podwoić**.

Jeśli zainicjować *prgDblVals* i *prgLengths* do NULL, a następnie tablice, które wskazują na zostaną przydzielone automatycznie, o rozmiarach równych rozmiarze zestawu wierszy.

> [!NOTE]
> Zbiorcza wymiana pól rekordów przenosi tylko dane ze źródła danych do obiektu zestaw rekordów. Aby można było aktualizować swój plik recordset, `SQLSetPos`należy użyć funkcji INTERFEJSU API ODBC .

Aby uzyskać więcej informacji, zobacz artykuły [Recordset: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Przykład

Zobacz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_int_bulk"></a><a name="rfx_int_bulk"></a>RFX_Int_Bulk

Przesyła dane całkowite między elementami elementów członkowskich danych pola `CRecordset` obiektu a kolumnami rekordu w źródle danych typu ODBC SQL_SMALLINT.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji `CFieldExchange` na temat operacji, które obiekt może określić, zobacz artykuł [Wymiana pól rekordu: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*Szname*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana we wskazanym człowianym danych — wartość, która ma zostać przeniesiona. Dla transferu z zestawu rekordów do źródła danych wartość typu **int**jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zbioru rekordów wartość jest przechowywana w określonym elementów członkowskich danych.

### <a name="example"></a>Przykład

Zobacz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_long_bulk"></a><a name="rfx_long_bulk"></a>RFX_Long_Bulk

Przenosi wiele wierszy długich danych całkowitych z kolumny źródła danych ODBC `CRecordset`do odpowiedniej tablicy w obiekcie pochodnym.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Long_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   long** prgLongVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Wskaźnik do [obiektu CFieldExchange.](cfieldexchange-class.md) Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [Wymiana pól rekordu: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*Szname*<br/>
Nazwa kolumny danych.

*prgLongVals (Długie wałki)*<br/>
Wskaźnik do tablicy długich liczby całkowitych. Ta tablica będzie przechowywać dane, które mają być przesyłane ze źródła danych do zestawu rekordów.

*PrgLengths (Środki na zm.*<br/>
Wskaźnik do tablicy długich liczby całkowitych. Ta tablica będzie przechowywać długość w bajtach każdej wartości w tablicy wskazywalnej przez *prgLongVals*. Należy zauważyć, że wartość SQL_NULL_DATA będą przechowywane, jeśli odpowiedni element danych zawiera wartość Null. Aby uzyskać więcej informacji, zobacz `SQLBindCol` funkcję INTERFEJSU API ODBC w *odwołaniu programisty SDK ODBC*.

### <a name="remarks"></a>Uwagi

Kolumna źródła danych musi mieć typ ODBC SQL_INTEGER. Zestaw rekordów musi definiować element członkowski danych pola wskaźnika typu **na długi**.

Jeśli zainicjować *prgLongVals* i *prgLengths* do NULL, a następnie tablice, które wskazują na zostaną przydzielone automatycznie, o rozmiarach równych rozmiarze zestawu wierszy.

> [!NOTE]
> Zbiorcza wymiana pól rekordów przenosi tylko dane ze źródła danych do obiektu zestaw rekordów. Aby można było aktualizować swój plik recordset, `SQLSetPos`należy użyć funkcji INTERFEJSU API ODBC .

Aby uzyskać więcej informacji, zobacz artykuły [Recordset: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Przykład

Zobacz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_single_bulk"></a><a name="rfx_single_bulk"></a>RFX_Single_Bulk

Przenosi wiele wierszy danych zmiennoprzecinkowych z kolumny źródła danych `CRecordset`ODBC do odpowiedniej tablicy w obiekcie pochodnym.

### <a name="syntax"></a>Składnia

```cpp
void RFX_Single_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   float** prgFltVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Wskaźnik do [obiektu CFieldExchange.](cfieldexchange-class.md) Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [Wymiana pól rekordu: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*Szname*<br/>
Nazwa kolumny danych.

*prgFltVals (Równy z o.o.*<br/>
Wskaźnik do tablicy wartości **float.** Ta tablica będzie przechowywać dane, które mają być przesyłane ze źródła danych do zestawu rekordów.

*PrgLengths (Środki na zm.*<br/>
Wskaźnik do tablicy długich liczby całkowitych. Ta tablica będzie przechowywać długość w bajtach każdej wartości w tablicy wskazywalnej przez *prgFltVals*. Należy zauważyć, że wartość SQL_NULL_DATA będą przechowywane, jeśli odpowiedni element danych zawiera wartość Null. Aby uzyskać więcej informacji, zobacz `SQLBindCol` funkcję INTERFEJSU API ODBC w *odwołaniu programisty SDK ODBC*.

### <a name="remarks"></a>Uwagi

Kolumna źródła danych musi mieć typ ODBC SQL_REAL. Zestaw rekordów musi definiować element członkowski danych pola wskaźnika typu, aby **upłynąć .**

Jeśli zainicjować *prgFltVals* i *prgLengths* do NULL, a następnie tablice, które wskazują na zostaną przydzielone automatycznie, o rozmiarach równych rozmiarze zestawu wierszy.

> [!NOTE]
> Zbiorcza wymiana pól rekordów przenosi tylko dane ze źródła danych do obiektu zestaw rekordów. Aby można było aktualizować swój plik recordset, `SQLSetPos`należy użyć funkcji INTERFEJSU API ODBC .

Aby uzyskać więcej informacji, zobacz artykuły [Recordset: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Przykład

Zobacz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_text_bulk"></a><a name="rfx_text_bulk"></a>RFX_Text_Bulk

Przenosi wiele wierszy danych znakowych z kolumny źródła danych ODBC `CRecordset`do odpowiedniej tablicy w obiekcie pochodnym.

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

*Pfx*<br/>
Wskaźnik do [obiektu CFieldExchange.](cfieldexchange-class.md) Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [Wymiana pól rekordu: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*Szname*<br/>
Nazwa kolumny danych.

*prgStrVals (prgStrVals)*<br/>
Wskaźnik do tablicy wartości LPSTR. Ta tablica będzie przechowywać dane, które mają być przesyłane ze źródła danych do zestawu rekordów. Należy zauważyć, że w bieżącej wersji ODBC wartości te nie mogą być Unicode.

*PrgLengths (Środki na zm.*<br/>
Wskaźnik do tablicy długich liczby całkowitych. Ta tablica będzie przechowywać długość w bajtach każdej wartości w tablicy wskazywalnej przez *prgStrVals*. Długość ta nie obejmuje znaku zakończenia zerowego. Należy zauważyć, że wartość SQL_NULL_DATA będą przechowywane, jeśli odpowiedni element danych zawiera wartość Null. Aby uzyskać więcej informacji, zobacz `SQLBindCol` funkcję INTERFEJSU API ODBC w *odwołaniu programisty SDK ODBC*.

*nMaxLength*<br/>
Maksymalna dozwolona długość wartości przechowywanych w tablicy wskazywalnej przez *prgStrVals*, w tym znak zakończenia zerowego. Aby upewnić się, że dane nie zostaną obcięty, przekazać wartość wystarczająco duże, aby pomieścić największy element danych, których oczekujesz.

### <a name="remarks"></a>Uwagi

Kolumna źródła danych może mieć typ ODBC SQL_LONGVARCHAR, SQL_CHAR, SQL_VARCHAR, SQL_DECIMAL lub SQL_NUMERIC. Zestaw rekordów musi definiować element członkowski danych pola typu LPSTR.

Jeśli zainicjować *prgStrVals* i *prgLengths* do NULL, a następnie tablice, które wskazują na zostaną przydzielone automatycznie, o rozmiarach równych rozmiarze zestawu wierszy.

> [!NOTE]
> Zbiorcza wymiana pól rekordów przenosi tylko dane ze źródła danych do obiektu zestaw rekordów. Aby można było aktualizować swój plik recordset, `SQLSetPos`należy użyć funkcji INTERFEJSU API ODBC .

Aby uzyskać więcej informacji, zobacz artykuły [Recordset: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Przykład

Należy ręcznie napisać wywołania `DoBulkFieldExchange` w zastąpień. W tym przykładzie `RFX_Text_Bulk`pokazano wywołanie , `RFX_Long_Bulk`a także wywołanie do transferu danych. Te wywołania są poprzedzone wywołaniem [CFieldExchange::SetFieldType](cfieldexchange-class.md#setfieldtype). Należy zauważyć, że w przypadku parametrów należy wywołać funkcje RFX zamiast funkcji zbiorczego RFX.

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

**Nagłówek:** afxdb.h

## <a name="dfx_binary"></a><a name="dfx_binary"></a>DFX_Binary

Przesyła tablice bajtów między elementami elementów członkowskich danych pola obiektu [CDaoRecordset](cdaorecordset-class.md) a kolumnami rekordu w źródle danych.

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

*Pfx*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji.

*Szname*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana we wskazanym człowianym danych — wartość, która ma zostać przeniesiona. Dla transferu z zestawu rekordów do źródła danych wartość typu [CByteArray](cbytearray-class.md)jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zbioru rekordów wartość jest przechowywana w określonym elementów członkowskich danych.

*nPreAllocSize*<br/>
Struktura preallocates tej ilości pamięci. Jeśli dane są większe, struktura zadlokuje więcej miejsca w razie potrzeby. Aby uzyskać lepszą wydajność, ustaw ten rozmiar na wartość wystarczająco dużą, aby zapobiec ponownemu przydziałowi. Domyślny rozmiar jest zdefiniowany w AFXDAO. H jako AFX_DAO_BINARY_DEFAULT_SIZE.

*dwBindOptions*<br/>
Opcja, która pozwala korzystać z mechanizmu podwójnego buforowania MFC do wykrywania pól zestaw rekordów, które uległy zmianie. Domyślny, AFX_DAO_DISABLE_FIELD_CACHE, nie używa podwójnego buforowania i należy wywołać [SetFieldDirty](cdaorecordset-class.md#setfielddirty) i [SetFieldNull](cdaorecordset-class.md#setfieldnull) siebie. Inna możliwa wartość, AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania i nie trzeba wykonywać dodatkowej pracy, aby oznaczyć pola brudne lub Null. Ze względu na wydajność i pamięć należy unikać tej wartości, chyba że dane binarne są stosunkowo małe.

> [!NOTE]
> Domyślnie można kontrolować, czy dane są domyślnie buforowane dwukrotnie dla wszystkich pól, ustawiając [zestaw CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Dane są mapowane między typem DAO_BYTES w DAO i typu [CByteArray](cbytearray-class.md) w akubacie rekordów.

### <a name="example"></a>Przykład

Zobacz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="dfx_bool"></a><a name="dfx_bool"></a>DFX_Bool

Przesyła dane logiczne między elementami elementów członkowskich danych pola obiektu [CDaoRecordset](cdaorecordset-class.md) a kolumnami rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI DFX_Bool(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BOOL& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji.

*Szname*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana we wskazanym człowianym danych — wartość, która ma zostać przeniesiona. W przypadku transferu z zestawu rekordów do źródła danych wartość typu BOOL jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zbioru rekordów wartość jest przechowywana w określonym elementów członkowskich danych.

*dwBindOptions*<br/>
Opcja, która pozwala korzystać z mechanizmu podwójnego buforowania MFC do wykrywania pól zestaw rekordów, które uległy zmianie. Domyślny, AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania. Inną możliwą wartością jest AFX_DAO_DISABLE_FIELD_CACHE. Jeśli określisz tę wartość, MFC nie sprawdza tego pola. Musisz `SetFieldDirty` zadzwonić `SetFieldNull` i siebie.

> [!NOTE]
> Można kontrolować, czy dane są domyślnie buforowane dwukrotnie, ustawiając [zestaw CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Dane są mapowane między typem DAO_BOOL w DAO i typu BOOL w akusety rekordów.

### <a name="example"></a>Przykład

Zobacz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="dfx_byte"></a><a name="dfx_byte"></a>DFX_Byte

Przesyła pojedyncze bajty między elementami elementów członkowskich danych pola obiektu [CDaoRecordset](cdaorecordset-class.md) a kolumnami rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI DFX_Byte(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BYTE& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji.

*Szname*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana we wskazanym człowianym danych — wartość, która ma zostać przeniesiona. W przypadku transferu z zestawu rekordów do źródła danych wartość typu BYTE jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zbioru rekordów wartość jest przechowywana w określonym elementów członkowskich danych.

*dwBindOptions*<br/>
Opcja, która pozwala korzystać z mechanizmu podwójnego buforowania MFC do wykrywania pól zestaw rekordów, które uległy zmianie. Domyślny, AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania. Inną możliwą wartością jest AFX_DAO_DISABLE_FIELD_CACHE. Jeśli określisz tę wartość, MFC nie sprawdza tego pola. Musisz `SetFieldDirty` zadzwonić `SetFieldNull` i siebie.

> [!NOTE]
> Można kontrolować, czy dane są domyślnie buforowane dwukrotnie, ustawiając [zestaw CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Dane są mapowane między typem DAO_BYTES w DAO i typem BYTE w zbiorze rekordów.

### <a name="example"></a>Przykład

Zobacz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="dfx_currency"></a><a name="dfx_currency"></a>DFX_Currency

Przesyła dane walutowe między elementami elementów członkowskich danych pola obiektu [CDaoRecordset](cdaorecordset-class.md) a kolumnami rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI DFX_Currency(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleCurrency& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji.

*Szname*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana we wskazanym człowianym danych — wartość, która ma zostać przeniesiona. W przypadku transferu z zestawu rekordów do źródła danych wartość ta jest pobierana z określonego elementu członkowskiego danych typu [COleCurrency](colecurrency-class.md). W przypadku transferu ze źródła danych do zbioru rekordów wartość jest przechowywana w określonym elementów członkowskich danych.

*dwBindOptions*<br/>
Opcja, która pozwala korzystać z mechanizmu podwójnego buforowania MFC do wykrywania pól zestaw rekordów, które uległy zmianie. Domyślny, AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania. Inną możliwą wartością jest AFX_DAO_DISABLE_FIELD_CACHE. Jeśli określisz tę wartość, MFC nie sprawdza tego pola. Musisz `SetFieldDirty` zadzwonić `SetFieldNull` i siebie.

> [!NOTE]
> Można kontrolować, czy dane są domyślnie buforowane dwukrotnie, ustawiając [zestaw CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Dane są mapowane między typem DAO_CURRENCY w DAO i typu [COleCurrency](colecurrency-class.md) w zestawrekordy.

### <a name="example"></a>Przykład

Zobacz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="dfx_datetime"></a><a name="dfx_datetime"></a>DFX_DateTime

Przesyła dane o czasie i dacie między elementami elementów członkowskich danych pola obiektu [CDaoRecordset](cdaorecordset-class.md) a kolumnami rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI DFX_DateTime(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleDateTime& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji.

*Szname*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana we wskazanym człowianym danych — wartość, która ma zostać przeniesiona. Funkcja przyjmuje odwołanie do [obiektu COleDateTime.](../../atl-mfc-shared/reference/coledatetime-class.md) W przypadku transferu z zestawu rekordów do źródła danych ta wartość jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zbioru rekordów wartość jest przechowywana w określonym elementów członkowskich danych.

*dwBindOptions*<br/>
Opcja, która pozwala korzystać z mechanizmu podwójnego buforowania MFC do wykrywania pól zestaw rekordów, które uległy zmianie. Domyślny, AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania. Inną możliwą wartością jest AFX_DAO_DISABLE_FIELD_CACHE. Jeśli określisz tę wartość, MFC nie sprawdza tego pola. Musisz `SetFieldDirty` zadzwonić `SetFieldNull` i siebie.

> [!NOTE]
> Można kontrolować, czy dane są domyślnie buforowane dwukrotnie, ustawiając [zestaw CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Dane są mapowane między typem DAO_DATE w DAO i [typem COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) w ach.

> [!NOTE]
> `COleDateTime`zastępuje [CTime](../../atl-mfc-shared/reference/ctime-class.md) i TIMESTAMP_STRUCT w tym celu w klasach DAO. `CTime`i TIMESTAMP_STRUCT są nadal używane dla klas dostępu do danych opartych na ODBC.

### <a name="example"></a>Przykład

Zobacz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="dfx_double"></a><a name="dfx_double"></a>DFX_Double

Przesyła **dane dwuskładników zmiennoprzecjowych** między elementami elementów członkowskich danych pola obiektu [CDaoRecordset](cdaorecordset-class.md) a kolumnami rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI DFX_Double(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   double& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji.

*Szname*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana we wskazanym człowianym danych — wartość, która ma zostać przeniesiona. Dla transferu z zestawu rekordów do źródła danych wartość typu **double**, jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zbioru rekordów wartość jest przechowywana w określonym elementów członkowskich danych.

*dwBindOptions*<br/>
Opcja, która pozwala korzystać z mechanizmu podwójnego buforowania MFC do wykrywania pól zestaw rekordów, które uległy zmianie. Domyślny, AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania. Inną możliwą wartością jest AFX_DAO_DISABLE_FIELD_CACHE. Jeśli określisz tę wartość, MFC nie sprawdza tego pola. Musisz `SetFieldDirty` zadzwonić `SetFieldNull` i siebie.

> [!NOTE]
> Można kontrolować, czy dane są domyślnie buforowane dwukrotnie, ustawiając [zestaw CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Dane są mapowane między typem DAO_R8 w DAO i wpisz **double float** w zestaw rekordów.

### <a name="example"></a>Przykład

Zobacz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="dfx_long"></a><a name="dfx_long"></a>DFX_Long

Przesyła długie dane całkowite między elementami elementów członkowskich danych pola obiektu [CDaoRecordset](cdaorecordset-class.md) a kolumnami rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI DFX_Long(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   long& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji.

*Szname*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana we wskazanym człowianym danych — wartość, która ma zostać przeniesiona. W przypadku transferu z zestawu rekordów do źródła danych wartość typu **long**jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zbioru rekordów wartość jest przechowywana w określonym elementów członkowskich danych.

*dwBindOptions*<br/>
Opcja, która pozwala korzystać z mechanizmu podwójnego buforowania MFC do wykrywania pól zestaw rekordów, które uległy zmianie. Domyślny, AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania. Inną możliwą wartością jest AFX_DAO_DISABLE_FIELD_CACHE. Jeśli określisz tę wartość, MFC nie sprawdza tego pola. Musisz `SetFieldDirty` zadzwonić `SetFieldNull` i siebie.

> [!NOTE]
> Można kontrolować, czy dane są domyślnie buforowane dwukrotnie, ustawiając [zestaw CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Dane są mapowane między typem DAO_I4 w DAO i wpisz **długo** w akublacie rekordów.

### <a name="example"></a>Przykład

Zobacz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="dfx_longbinary"></a><a name="dfx_longbinary"></a>DFX_LongBinary

**Ważne** Zaleca się użycie [DFX_Binary](#dfx_binary) zamiast tej funkcji.

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

*Pfx*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji.

*Szname*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana we wskazanym człowianym danych — wartość, która ma zostać przeniesiona. Dla transferu z zestawu rekordów do źródła danych wartość typu [CLongBinary](clongbinary-class.md), jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zbioru rekordów wartość jest przechowywana w określonym elementów członkowskich danych.

*dwPreAllocSize*<br/>
Struktura preallocates tej ilości pamięci. Jeśli dane są większe, struktura zadlokuje więcej miejsca w razie potrzeby. Aby uzyskać lepszą wydajność, ustaw ten rozmiar na wartość wystarczająco dużą, aby zapobiec ponownemu przydziałowi.

*dwBindOptions*<br/>
Opcja, która pozwala korzystać z mechanizmu podwójnego buforowania MFC do wykrywania pól zestaw rekordów, które uległy zmianie. Domyślny, AFX_DISABLE_FIELD_CACHE, nie używa podwójnego buforowania. Inną możliwą wartością jest AFX_DAO_ENABLE_FIELD_CACHE. Używa podwójnego buforowania i nie trzeba wykonywać dodatkowej pracy, aby oznaczyć pola brudne lub Null. Ze względu na wydajność i pamięć należy unikać tej wartości, chyba że dane binarne są stosunkowo małe.

> [!NOTE]
> Można kontrolować, czy dane są domyślnie buforowane dwukrotnie, ustawiając [zestaw CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

`DFX_LongBinary`zgodność z klasami OdBC MFC. Funkcja `DFX_LongBinary` przenosi binarne dane dużych obiektów `CLongBinary` (BLOB) przy użyciu klasy między elementami elementów członkowskich danych pola obiektu [CDaoRecordset](cdaorecordset-class.md) a kolumnami rekordu w źródle danych. Dane są mapowane między typem DAO_BYTES w DAO i typu [CLongBinary](clongbinary-class.md) w zestaw rekordów.

### <a name="example"></a>Przykład

Zobacz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="dfx_short"></a><a name="dfx_short"></a>DFX_Short

Przesyła krótkie dane całkowite między elementami elementów członkowskich danych pola obiektu [CDaoRecordset](cdaorecordset-class.md) a kolumnami rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI DFX_Short(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   short& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji.

*Szname*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana we wskazanym człowianym danych — wartość, która ma zostać przeniesiona. W przypadku transferu z zestawu rekordów do źródła danych wartość typu **krótkiego**jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zbioru rekordów wartość jest przechowywana w określonym elementów członkowskich danych.

*dwBindOptions*<br/>
Opcja, która pozwala korzystać z mechanizmu podwójnego buforowania MFC do wykrywania pól zestaw rekordów, które uległy zmianie. Domyślny, AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania. Inną możliwą wartością jest AFX_DAO_DISABLE_FIELD_CACHE. Jeśli określisz tę wartość, MFC nie sprawdza tego pola. Musisz `SetFieldDirty` zadzwonić `SetFieldNull` i siebie.

> [!NOTE]
> Można kontrolować, czy dane są domyślnie buforowane dwukrotnie, ustawiając [zestaw CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Dane są mapowane między typem DAO_I2 w DAO i **wpisz krótki** w rekordzie.

> [!NOTE]
> `DFX_Short`odpowiada [RFX_Int](#rfx_int) dla klas opartych na ODBC.

### <a name="example"></a>Przykład

Zobacz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="dfx_single"></a><a name="dfx_single"></a>DFX_Single

Przesyła dane zmiennoprzecinkowe między elementami elementów członkowskich danych pola obiektu [CDaoRecordset](cdaorecordset-class.md) a kolumnami rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI DFX_Single(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   float& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji.

*Szname*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana we wskazanym człowianym danych — wartość, która ma zostać przeniesiona. Dla transferu z zestawu rekordów do źródła danych wartość **typu float**, jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zbioru rekordów wartość jest przechowywana w określonym elementów członkowskich danych.

*dwBindOptions*<br/>
Opcja, która pozwala korzystać z mechanizmu podwójnego buforowania MFC do wykrywania pól zestaw rekordów, które uległy zmianie. Domyślny, AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania. Inną możliwą wartością jest AFX_DAO_DISABLE_FIELD_CACHE. Jeśli określisz tę wartość, MFC nie sprawdza tego pola. Musisz `SetFieldDirty` zadzwonić `SetFieldNull` i siebie.

> [!NOTE]
> Można kontrolować, czy dane są domyślnie buforowane dwukrotnie, ustawiając [zestaw CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Dane są mapowane między typem DAO_R4 w DAO i **typu float** w pliku recordset.

### <a name="example"></a>Przykład

Zobacz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="dfx_text"></a><a name="dfx_text"></a>DFX_Text

Przesyła `CString` dane między elementami elementów członkowskich danych pól obiektu [CDaoRecordset](cdaorecordset-class.md) i kolumnami rekordu w źródle danych.

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

*Pfx*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje definiujące kontekst dla każdego wywołania funkcji.

*Szname*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana we wskazanym człowianym danych — wartość, która ma zostać przeniesiona. Dla transferu z zestawu rekordów do źródła danych wartość typu [CString](../../atl-mfc-shared/reference/cstringt-class.md), jest pobierana z określonego elementu członkowskiego danych. W przypadku transferu ze źródła danych do zbioru rekordów wartość jest przechowywana w określonym elementów członkowskich danych.

*nPreAllocSize*<br/>
Struktura preallocates tej ilości pamięci. Jeśli dane są większe, struktura zadlokuje więcej miejsca w razie potrzeby. Aby uzyskać lepszą wydajność, ustaw ten rozmiar na wartość wystarczająco dużą, aby zapobiec ponownemu przydziałowi.

*dwBindOptions*<br/>
Opcja, która pozwala korzystać z mechanizmu podwójnego buforowania MFC do wykrywania pól zestaw rekordów, które uległy zmianie. Domyślny, AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania. Inną możliwą wartością jest AFX_DAO_DISABLE_FIELD_CACHE. Jeśli określisz tę wartość, MFC nie sprawdza tego pola. Musisz wywołać [SetFieldDirty](cdaorecordset-class.md#setfielddirty) i [SetFieldNull](cdaorecordset-class.md#setfieldnull) siebie.

> [!NOTE]
> Można kontrolować, czy dane są domyślnie buforowane dwukrotnie, ustawiając [zestaw CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Dane są mapowane między typem DAO_CHAR w DAO (lub, jeśli symbol _UNICODE jest zdefiniowany, DAO_WCHAR) i typu [CString](../../atl-mfc-shared/reference/cstringt-class.md) w zbiorze rekordów.  n

### <a name="example"></a>Przykład

W tym przykładzie `DFX_Text`przedstawiono kilka wywołań do . Zwróć również uwagę na dwa wywołania [CDaoFieldExchange::SetFieldType](cdaofieldexchange-class.md#setfieldtype). Należy napisać pierwsze wywołanie `SetFieldType` i jego wywołanie **DFX.** Drugie wywołanie i skojarzone z nim wywołania **DFX** są zwykle zapisywane przez kreatora kodu, który wygenerował klasę.

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

**Nagłówek:** afxdao.h

## <a name="see-also"></a>Zobacz też

[Makra i globals](mfc-macros-and-globals.md)<br/>
[CRecordset::DoFieldExchange](crecordset-class.md#dofieldexchange)<br/>
[CRecordset::DoBulkFieldExchange](crecordset-class.md#dobulkfieldexchange)<br/>
[CDaoRecordset::DoFieldExchange](cdaorecordset-class.md#dofieldexchange)
