---
title: Funkcje wymiany pól rejestrowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 430d9d297161a05f9158893454f00be2afbe7a47
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408573"
---
# <a name="record-field-exchange-functions"></a>Funkcje wymiany pól rekordów

W tym temacie wymieniono wymiana pól rekordów (RFX zbiorcze RFX i DFX) funkcji, które służą do automatyzowania transfer danych między obiektem zestawu rekordów a źródłem danych i wykonywać inne operacje na danych.

Jeśli używasz klasy oparte na ODBC i udało Ci się wdrożyć zbiorcze pobieranie z wiersza, należy ręcznie zmienić `DoBulkFieldExchange` funkcji składowej typu `CRecordset` przez wywołanie funkcji zbiorcze RFX dla każdego elementu członkowskiego danych, odpowiadający kolumny źródła danych.

Jeśli nie zaimplementowano zbiorcze pobieranie z wiersza do klas na podstawie ODBC lub jeśli używasz klasy oparte na DAO ClassWizard spowoduje przesłonięcie `DoFieldExchange` funkcji składowej typu `CRecordset` lub `CDaoRecordset` przez wywołanie funkcji RFX (dla ODBC — klasy ) lub funkcje DFX (dla klas DAO) dla każdego elementu członkowskiego danych pola w twoim zestawie rekordów.

Funkcje wymiany pól rekordów transferu danych w każdym struktura wywołuje `DoFieldExchange` lub `DoBulkFieldExchange`. Każda funkcja przesyła dane określonego typu.

Aby uzyskać więcej informacji na temat używania tych funkcji, zobacz artykuły [wymiana pól rekordów: jak działa RFX (ODBC)](../../data/odbc/record-field-exchange-how-rfx-works.md). Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

W przypadku kolumn danych, które można powiązać dynamicznie, można również wywołać funkcje RFX lub DFX samodzielnie, jak wyjaśniono w artykułach [zestaw rekordów: dynamiczne powiązanie danych kolumn (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md). Ponadto można napisać własne niestandardowe procedury RFX lub DFX, jak wyjaśniono w Uwaga techniczna [43](../../mfc/tn043-rfx-routines.md) (dla ODBC) i Uwaga techniczna [53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) (w przypadku DAO).

Na przykład RFX i zbiorcze RFX funkcje, w jakiej występują w `DoFieldExchange` i `DoBulkFieldExchange` funkcji, zobacz [rfx_text —](#rfx_text) i rfx_text_bulk — # [rfx_text_bulk —]). Funkcje DFX są bardzo podobne do funkcji RFX.

### <a name="rfx-functions-odbc"></a>Funkcje RFX (ODBC)

|||
|-|-|
|[Rfx_binary —](#rfx_binary)|Przesyła tablice bajtów typu [CByteArray](cbytearray-class.md).|
|[Rfx_bool —](#rfx_bool)|Przesyłanie danych logicznych.|
|[Rfx_byte —](#rfx_byte)|Przesyła jednego bajtu danych.|
|[Rfx_date —](#rfx_date)|Przesyła czasu i daty, używając [CTime](../../atl-mfc-shared/reference/ctime-class.md) lub TIMESTAMP_STRUCT.|
|[Rfx_double —](#rfx_double)|Przesyła dane zmiennoprzecinkowe podwójnej precyzji.|
|[Rfx_int —](#rfx_int)|Przesyłanie danych liczb całkowitych.|
|[Rfx_long —](#rfx_long)|Transfery długie danych liczb całkowitych.|
|[Rfx_longbinary —](#rfx_longbinary)|Przesyła dane dużych obiektów binarnych (BLOB) dla obiektu [CLongBinary](clongbinary-class.md) klasy.|
|[Rfx_single —](#rfx_single)|Transfery float danych.|
|[Rfx_text —](#rfx_text)|Dane ciągowe transferu.|

### <a name="bulk-rfx-functions-odbc"></a>Funkcje zbiorczej wymiany RFX (ODBC)

|||
|-|-|
|[Rfx_binary_bulk —](#rfx_binary_bulk)|Przesyła tablic bajtów danych.|
|[Rfx_bool_bulk —](#rfx_bool_bulk)|Przesyła tablic danych logicznych.|
|[Rfx_byte_bulk —](#rfx_byte_bulk)|Przesyła tablice bajtów jednego.|
|[Rfx_date_bulk —](#rfx_date_bulk)|Przesyła tablic danych typu TIMESTAMP_STRUCT.|
|[Rfx_double_bulk —](#rfx_double_bulk)|Przesyła tablic danych podwójnej precyzji, zmiennoprzecinkowych.|
|[Rfx_int_bulk —](#rfx_int_bulk)|Przesyła tablic danych liczb całkowitych.|
|[Rfx_long_bulk —](#rfx_long_bulk)|Przesyła tablic danych Liczba całkowita typu long.|
|[Rfx_single_bulk —](#rfx_single_bulk)|Przesyła tablic danych zmiennoprzecinkowych.|
|[Rfx_text_bulk —](#rfx_text_bulk)|Przesyła tablic danych typu LPSTR.|

### <a name="dfx-functions-dao"></a>Funkcje DFX (DAO)

|||
|-|-|
|[Dfx_binary —](#dfx_binary)|Przesyła tablice bajtów typu [CByteArray](cbytearray-class.md).|
|[Dfx_bool —](#dfx_bool)|Przesyłanie danych logicznych.|
|[Dfx_byte —](#dfx_byte)|Przesyła jednego bajtu danych.|
|[Dfx_currency —](#dfx_currency)|Transfery danych walutowych, typu [COleCurrency](colecurrency-class.md).|
|[Dfx_datetime —](#dfx_datetime)|Transfery danych Data i godzina, o typie [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md).|
|[Dfx_double —](#dfx_double)|Przesyła dane zmiennoprzecinkowe podwójnej precyzji.|
|[Dfx_long —](#dfx_long)|Transfery długie danych liczb całkowitych.|
|[Dfx_longbinary —](#dfx_longbinary)|Przesyła dane dużych obiektów binarnych (BLOB) dla obiektu `CLongBinary` klasy. DAO, zalecane jest użycie [dfx_binary —](#dfx_binary) zamiast tego.|
|[Dfx_short —](#dfx_short)|Transfery krótkie danych liczb całkowitych.|
|[Dfx_single —](#dfx_single)|Transfery float danych.|
|[Dfx_text —](#dfx_text)|Dane ciągowe transferu.|

=============================================

## <a name="rfx_binary"></a>  Rfx_binary —

Tablice bajtów do transferu między elementy członkowskie danych pola z `CRecordset` obiektu i kolumn rekordu w źródle danych ODBC wpisz SQL_BINARY, SQL_VARBINARY lub SQL_LONGVARBINARY.

### <a name="syntax"></a>Składnia

```
void RFX_Binary(
   CFieldExchange* pFX,
   const char* szName,
   CByteArray& value,
   int nMaxLength = 255);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` można określić obiektu, zapoznaj się z artykułem [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu [CByteArray](cbytearray-class.md), pochodzi od elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.

*nMaxLength*<br/>
Maksymalna dozwolona liczba znaków, string lub tablicy przesyłane. Wartość domyślna *nMaxLength* wynosi 255. Wartości prawne są 1, aby INT_MAX. Struktura przydziela taka ilość miejsca na dane. Aby uzyskać najlepszą wydajność należy przekazać wartość wystarczająco dużą do obsługi największych element danych, których oczekujesz.

### <a name="remarks"></a>Uwagi

Dane w źródle danych tego typu jest mapowany do i z typu `CByteArray` w zestawie rekordów.

### <a name="example"></a>Przykład

Zobacz [rfx_text —](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_bool"></a>  Rfx_bool —

Transfer danych logicznych między elementy członkowskie danych pola z `CRecordset` SQL_BIT typu obiektu i kolumn rekordu w źródle danych ODBC.

### <a name="syntax"></a>Składnia

```
void RFX_Bool(
   CFieldExchange* pFX,
   const char* szName,
   BOOL& value);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` można określić obiektu, zapoznaj się z artykułem [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych wartości typu BOOL, jest pobierana z elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.

### <a name="example"></a>Przykład

Zobacz [rfx_text —](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_byte"></a>  Rfx_byte —

Transfery pojedynczy bajtów między elementy członkowskie danych pola z `CRecordset` SQL_TINYINT typu obiektu i kolumn rekordu w źródle danych ODBC.

### <a name="syntax"></a>Składnia

```
void RFX_Byte(
   CFieldExchange* pFX,
   const char* szName,
   BYTE& value);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` można określić obiektu, zapoznaj się z artykułem [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych wartość typu BYTE, jest pobierana z elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.

### <a name="example"></a>Przykład

Zobacz [rfx_text —](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_date"></a>  Rfx_date —

Transfery `CTime` lub TIMESTAMP_STRUCT danych między elementy członkowskie danych pola z `CRecordset` obiektu i kolumn rekordu w źródle danych ODBC wpisz SQL_DATE, SQL_TIME lub SQL_TIMESTAMP.

### <a name="syntax"></a>Składnia

```
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

*Plik pFX*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` można określić obiektu, zapoznaj się z artykułem [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana w składowej danych wskazany; wartość do przeniesienia. Różne wersje funkcji przyjmują różne typy danych dla wartości:

Pierwsza wersja funkcja przyjmuje odwołanie do [CTime](../../atl-mfc-shared/reference/ctime-class.md) obiektu. Transfer z zestawu rekordów do źródła danych ta wartość jest pobierana z elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.

Druga wersja funkcja przyjmuje odwołanie do `TIMESTAMP_STRUCT` struktury. Należy ustawić tę strukturę samodzielnie przed wywołaniem. Obsługa ani wymiana danych okna dialogowego (DDX) ani kodu kreatora obsługa jest dostępna dla tej wersji. Trzecia wersja funkcja działa podobnie do pierwszej wersji z tą różnicą, że wykorzystuje odwołanie do [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiektu.

### <a name="remarks"></a>Uwagi

`CTime` Wersję funkcji nakłada obciążenie przetworzenie pośrednich i ma nieco ograniczone zakres. Jeśli okaże się jedną z tych czynników zbyt ograniczanie, należy użyć drugą wersję funkcji. Jednak należy pamiętać, brak kreatora kodu i obsługa DDX wymóg, że możesz skonfigurować strukturę samodzielnie.

### <a name="example"></a>Przykład

Zobacz [rfx_text —](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_double"></a>  Rfx_double —

Transfery **double float** danych między elementy członkowskie danych pola z `CRecordset` SQL_DOUBLE typu obiektu i kolumn rekordu w źródle danych ODBC.

### <a name="syntax"></a>Składnia

```
void RFX_Double(
   CFieldExchange* pFX,
   const char* szName,
   double& value);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` można określić obiektu, zapoznaj się z artykułem [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu **double**, pochodzi od elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.

### <a name="example"></a>Przykład

Zobacz [rfx_text —](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_int"></a>  Rfx_int —

Transfer danych liczb całkowitych między elementy członkowskie danych pola z `CRecordset` SQL_SMALLINT typu obiektu i kolumn rekordu w źródle danych ODBC.

### <a name="syntax"></a>Składnia

```
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` można określić obiektu, zapoznaj się z artykułem [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu **int**, pochodzi od elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.

### <a name="example"></a>Przykład

Zobacz [rfx_text —](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_long"></a>  Rfx_long —

Transfer danych długich liczb całkowitych między elementy członkowskie danych pola z `CRecordset` SQL_INTEGER typu obiektu i kolumn rekordu w źródle danych ODBC.

### <a name="syntax"></a>Składnia

```
void RFX_Long(
   CFieldExchange* pFX,
   const char* szName,
   LONG&
value );
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` można określić obiektu, zapoznaj się z artykułem [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu **długie**, pochodzi od elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.

### <a name="example"></a>Przykład

Zobacz [rfx_text —](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_longbinary"></a>  Rfx_longbinary —

Transfery danych binarnych, dużych obiektów (BLOB) przy użyciu klasy [CLongBinary](clongbinary-class.md) między elementy członkowskie danych pola z `CRecordset` obiektu i kolumn rekordu w źródle danych ODBC wpisz SQL_LONGVARBINARY lub SQL_LONGVARCHAR.

### <a name="syntax"></a>Składnia

```
void RFX_LongBinary(
   CFieldExchange* pFX,
   const char* szName,
   CLongBinary& value);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` można określić obiektu, zapoznaj się z artykułem [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu `CLongBinary`, pochodzi od elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.

### <a name="example"></a>Przykład

Zobacz [rfx_text —](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_single"></a>  Rfx_single —

Transfer danych zmiennopozycyjnych między elementy członkowskie danych pola z `CRecordset` SQL_REAL typu obiektu i kolumn rekordu w źródle danych ODBC.

### <a name="syntax"></a>Składnia

```
void RFX_Single(
   CFieldExchange* pFX,
   const char* szName,
   float& value);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` można określić obiektu, zapoznaj się z artykułem [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu **float**, pochodzi od elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.

### <a name="example"></a>Przykład

Zobacz [rfx_text —](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h


## <a name="rfx_text"></a>  Rfx_text —

Transfery `CString` danych między elementy członkowskie danych pola z `CRecordset` obiektu i kolumn rekordu w źródle danych ODBC typu SQL_LONGVARCHAR, SQL_CHAR, SQL_VARCHAR, SQL_DECIMAL lub SQL_NUMERIC.

### <a name="syntax"></a>Składnia

```
void RFX_Text(
   CFieldExchange* pFX,
   const char* szName,
   CString& value,
   int nMaxLength = 255,
   int nColumnType = SQL_VARCHAR,
   short nScale = 0);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do obiektu klasy `CFieldExchange`. Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` można określić obiektu, zapoznaj się z artykułem [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu `CString`, pochodzi od elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.

*nMaxLength*<br/>
Maksymalna dozwolona liczba znaków, string lub tablicy przesyłane. Wartość domyślna *nMaxLength* wynosi 255. Wartości prawne są 1, aby INT_MAX). Struktura przydziela taka ilość miejsca na dane. Aby uzyskać najlepszą wydajność należy przekazać wartość wystarczająco dużą do obsługi największych element danych, których oczekujesz.

*nColumnType*<br/>
Używane głównie dla parametrów. Liczba całkowita wskazująca typ danych parametru. Typ jest typem danych ODBC formularza **SQL_XXX**.

*nScale*<br/>
Określa dla wartości typu ODBC SQL_DECIMAL lub SQL_NUMERIC skali. *nScale* przydaje się tylko podczas ustawiania wartości parametrów. Aby uzyskać więcej informacji, zobacz temat "Dokładność, skala, długość i rozmiar wyświetlania", w dodatku D *ODBC SDK Podręcznik programisty*.

### <a name="remarks"></a>Uwagi

Dane w źródle danych wszystkich tych typów jest mapowany do i z `CString` w zestawie rekordów.

### <a name="example"></a>Przykład

W tym przykładzie pokazano kilka wywołań `RFX_Text`. Zwróć uwagę, również dwa wywołania `CFieldExchange::SetFieldType`. Dla parametrów musi zapisać wywołania `SetFieldType` , a następnie wywołać jej RFX. Wywołanie kolumny danych wyjściowych i jego skojarzone wywołania RFX zwykle są zapisywane przez kreatora kodu.

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


## <a name="rfx_binary_bulk"></a>  Rfx_binary_bulk —

Przesyła wiele wierszy danych bajtowych wartości z kolumny źródła danych ODBC do odpowiedniej tablicy w `CRecordset`-pochodnych obiektu.

### <a name="syntax"></a>Składnia

```
void RFX_Binary_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BYTE** prgByteVals,
   long** prgLengths,
   int nMaxLength);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do [CFieldExchange](cfieldexchange-class.md) obiektu. Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*prgByteVals*<br/>
Wskaźnik do tablicy wartości BAJTÓW. Ta tablica będą przechowywane dane przesłane ze źródła danych do zestawu rekordów.

*prgLengths*<br/>
Wskaźnik do tablicy liczb całkowitych długie. Ta tablica zapisze długość w bajtach każdej wartości w tablicy, do których prowadzą *prgByteVals*. Należy zauważyć, że wartość SQL_NULL_DATA będą przechowywane, jeśli odpowiadającego mu elementu danych zawiera wartość Null. Aby uzyskać więcej informacji, zobacz opis funkcji interfejsu API ODBC `SQLBindCol` w *ODBC SDK Podręcznik programisty*.

*nMaxLength*<br/>
Maksymalna dozwolona liczba znaków wartości przechowywane w tablicy, do których prowadzą *prgByteVals*. Aby upewnić się, że dane nie zostaną obcięte, należy przekazać wartość wystarczająco dużą do obsługi największych element danych, których oczekujesz.

### <a name="remarks"></a>Uwagi

Kolumny źródła danych może mieć typu ODBC SQL_BINARY, SQL_VARBINARY lub SQL_LONGVARBINARY. Zestaw rekordów musi definiować element członkowski danych pola typu wskaźnika na BAJT.

Jeśli inicjowania *prgByteVals* i *prgLengths* na wartość NULL, a następnie tablic, które one wskazują zostaną przydzielone automatycznie, o rozmiarach równy rozmiarowi zestawu wierszy.

> [!NOTE]
>  Zbiorcza wymiana pól rekordów tylko przesyła dane ze źródła danych do obiektu zestawu rekordów. Aby można było wprowadzić rekordów można aktualizować, należy użyć funkcji interfejsu API ODBC `SQLSetPos`.

Aby uzyskać więcej informacji, zobacz artykuły [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [wymiany pól rekordu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Przykład

Zobacz [rfx_text_bulk —](#rfx_text_bulk).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_bool_bulk"></a>  Rfx_bool_bulk —

Przesyła wiele wierszy danych logicznych z kolumną źródła danych ODBC do odpowiedniej tablicy w `CRecordset`-pochodnych obiektu.

### <a name="syntax"></a>Składnia

```
void RFX_Bool_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BOOL** prgBoolVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do [CFieldExchange](cfieldexchange-class.md) obiektu. Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*prgBoolVals*<br/>
Wskaźnik do tablicy wartości. Ta tablica będą przechowywane dane przesłane ze źródła danych do zestawu rekordów.

*prgLengths*<br/>
Wskaźnik do tablicy liczb całkowitych długie. Ta tablica zapisze długość w bajtach każdej wartości w tablicy, do których prowadzą *prgBoolVals*. Należy zauważyć, że wartość SQL_NULL_DATA będą przechowywane, jeśli odpowiadającego mu elementu danych zawiera wartość Null. Aby uzyskać więcej informacji, zobacz opis funkcji interfejsu API ODBC `SQLBindCol` w *ODBC SDK Podręcznik programisty*.

### <a name="remarks"></a>Uwagi

Kolumny źródła danych musi mieć typ SQL_BIT ODBC. Zestaw rekordów musi definiować element członkowski danych pola typu wskaźnika na BOOL.

Jeśli inicjowania *prgBoolVals* i *prgLengths* na wartość NULL, a następnie tablic, które one wskazują zostaną przydzielone automatycznie, o rozmiarach równy rozmiarowi zestawu wierszy.

> [!NOTE]
>  Zbiorcza wymiana pól rekordów tylko przesyła dane ze źródła danych do obiektu zestawu rekordów. Aby rekordów można aktualizować, należy użyć funkcji interfejsu API ODBC `SQLSetPos`.

Aby uzyskać więcej informacji, zobacz artykuły [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [wymiany pól rekordu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Przykład

Zobacz [rfx_text_bulk —](#rfx_text_bulk).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_byte_bulk"></a>  Rfx_byte_bulk —

Przesyła wiele wierszy bajtów jednego z kolumną źródła danych ODBC do odpowiedniej tablicy w `CRecordset`-pochodnych obiektu.

### <a name="syntax"></a>Składnia

```
void RFX_Byte_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BYTE** prgByteVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do [CFieldExchange](cfieldexchange-class.md) obiektu. Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*prgByteVals*<br/>
Wskaźnik do tablicy wartości BAJTÓW. Ta tablica będą przechowywane dane przesłane ze źródła danych do zestawu rekordów.

*prgLengths*<br/>
Wskaźnik do tablicy liczb całkowitych długie. Ta tablica zapisze długość w bajtach każdej wartości w tablicy, do których prowadzą *prgByteVals*. Należy zauważyć, że wartość SQL_NULL_DATA będą przechowywane, jeśli odpowiadającego mu elementu danych zawiera wartość Null. Aby uzyskać więcej informacji, zobacz opis funkcji interfejsu API ODBC `SQLBindCol` w *ODBC SDK Podręcznik programisty*.

### <a name="remarks"></a>Uwagi

Kolumny źródła danych musi mieć typ SQL_TINYINT ODBC. Zestaw rekordów musi definiować element członkowski danych pola typu wskaźnika na BAJT.

Jeśli inicjowania *prgByteVals* i *prgLengths* na wartość NULL, a następnie tablic, które one wskazują zostaną przydzielone automatycznie, o rozmiarach równy rozmiarowi zestawu wierszy.

> [!NOTE]
>  Zbiorcza wymiana pól rekordów tylko przesyła dane ze źródła danych do obiektu zestawu rekordów. Aby rekordów można aktualizować, należy użyć funkcji interfejsu API ODBC `SQLSetPos`.

Aby uzyskać więcej informacji, zobacz artykuły [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [wymiany pól rekordu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Przykład

Zobacz [rfx_text_bulk —](#rfx_text_bulk).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_date_bulk"></a>  Rfx_date_bulk —

Przesyła wiele wierszy danych TIMESTAMP_STRUCT z kolumną źródła danych ODBC do odpowiedniej tablicy w `CRecordset`-pochodnych obiektu.

### <a name="syntax"></a>Składnia

```
void RFX_Date_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   TIMESTAMP_STRUCT** prgTSVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do [CFieldExchange](cfieldexchange-class.md) obiektu. Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*prgTSVals*<br/>
Wskaźnik do tablicy wartości TIMESTAMP_STRUCT. Ta tablica będą przechowywane dane przesłane ze źródła danych do zestawu rekordów. Aby uzyskać więcej informacji o typie danych TIMESTAMP_STRUCT, zobacz temat "Typy danych C" w dodatku D *ODBC SDK Podręcznik programisty*.

*prgLengths*<br/>
Wskaźnik do tablicy liczb całkowitych długie. Ta tablica zapisze długość w bajtach każdej wartości w tablicy, do których prowadzą *prgTSVals*. Należy zauważyć, że wartość SQL_NULL_DATA będą przechowywane, jeśli odpowiadającego mu elementu danych zawiera wartość Null. Aby uzyskać więcej informacji, zobacz opis funkcji interfejsu API ODBC `SQLBindCol` w *ODBC SDK Podręcznik programisty*.

### <a name="remarks"></a>Uwagi

Kolumny źródła danych może mieć typu ODBC SQL_DATE, SQL_TIME lub SQL_TIMESTAMP. Zestaw rekordów musi definiować element członkowski danych pola typu wskaźnika TIMESTAMP_STRUCT.

Jeśli inicjowania *prgTSVals* i *prgLengths* na wartość NULL, a następnie tablic, które one wskazują zostaną przydzielone automatycznie, o rozmiarach równy rozmiarowi zestawu wierszy.

> [!NOTE]
>  Zbiorcza wymiana pól rekordów tylko przesyła dane ze źródła danych do obiektu zestawu rekordów. Aby rekordów można aktualizować, należy użyć funkcji interfejsu API ODBC `SQLSetPos`.

Aby uzyskać więcej informacji, zobacz artykuły [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [wymiany pól rekordu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Przykład

Zobacz [rfx_text_bulk —](#rfx_text_bulk).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_double_bulk"></a>  Rfx_double_bulk —

Przesyła wiele wierszy podwójnej precyzji, zmiennoprzecinkowych dane z kolumny źródła danych ODBC do odpowiedniej tablicy w `CRecordset`-pochodnych obiektu.

### <a name="syntax"></a>Składnia

```
void RFX_Double_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   double** prgDblVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do [CFieldExchange](cfieldexchange-class.md) obiektu. Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*prgDblVals*<br/>
Wskaźnik do tablicy **double** wartości. Ta tablica będą przechowywane dane przesłane ze źródła danych do zestawu rekordów.

*prgLengths*<br/>
Wskaźnik do tablicy liczb całkowitych długie. Ta tablica zapisze długość w bajtach każdej wartości w tablicy, do których prowadzą *prgDblVals*. Należy zauważyć, że wartość SQL_NULL_DATA będą przechowywane, jeśli odpowiadającego mu elementu danych zawiera wartość Null. Aby uzyskać więcej informacji, zobacz opis funkcji interfejsu API ODBC `SQLBindCol` w *ODBC SDK Podręcznik programisty*.

### <a name="remarks"></a>Uwagi

Kolumny źródła danych musi mieć typ SQL_DOUBLE ODBC. Zestaw rekordów musi definiować element członkowski danych pola typu wskaźnika do **double**.

Jeśli inicjowania *prgDblVals* i *prgLengths* na wartość NULL, a następnie tablic, które one wskazują zostaną przydzielone automatycznie, o rozmiarach równy rozmiarowi zestawu wierszy.

> [!NOTE]
>  Zbiorcza wymiana pól rekordów tylko przesyła dane ze źródła danych do obiektu zestawu rekordów. Aby rekordów można aktualizować, należy użyć funkcji interfejsu API ODBC `SQLSetPos`.

Aby uzyskać więcej informacji, zobacz artykuły [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [wymiany pól rekordu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Przykład

Zobacz [rfx_text_bulk —](#rfx_text_bulk).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_int_bulk"></a>  Rfx_int_bulk —

Transfer danych liczb całkowitych między elementy członkowskie danych pola z `CRecordset` SQL_SMALLINT typu obiektu i kolumn rekordu w źródle danych ODBC.

### <a name="syntax"></a>Składnia

```
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` można określić obiektu, zapoznaj się z artykułem [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu **int**, pochodzi od elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.

### <a name="example"></a>Przykład

Zobacz [rfx_text —](#rfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_long_bulk"></a>  Rfx_long_bulk —

Przesyła wiele wierszy danych długich liczb całkowitych z kolumną źródła danych ODBC do odpowiedniej tablicy w `CRecordset`-pochodnych obiektu.

### <a name="syntax"></a>Składnia

```
void RFX_Long_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   long** prgLongVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do [CFieldExchange](cfieldexchange-class.md) obiektu. Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*prgLongVals*<br/>
Wskaźnik do tablicy liczb całkowitych długie. Ta tablica będą przechowywane dane przesłane ze źródła danych do zestawu rekordów.

*prgLengths*<br/>
Wskaźnik do tablicy liczb całkowitych długie. Ta tablica zapisze długość w bajtach każdej wartości w tablicy, do których prowadzą *prgLongVals*. Należy zauważyć, że wartość SQL_NULL_DATA będą przechowywane, jeśli odpowiadającego mu elementu danych zawiera wartość Null. Aby uzyskać więcej informacji, zobacz opis funkcji interfejsu API ODBC `SQLBindCol` w *ODBC SDK Podręcznik programisty*.

### <a name="remarks"></a>Uwagi

Kolumny źródła danych musi mieć typ SQL_INTEGER ODBC. Zestaw rekordów musi definiować element członkowski danych pola typu wskaźnika do **długie**.

Jeśli inicjowania *prgLongVals* i *prgLengths* na wartość NULL, a następnie tablic, które one wskazują zostaną przydzielone automatycznie, o rozmiarach równy rozmiarowi zestawu wierszy.

> [!NOTE]
>  Zbiorcza wymiana pól rekordów tylko przesyła dane ze źródła danych do obiektu zestawu rekordów. Aby rekordów można aktualizować, należy użyć funkcji interfejsu API ODBC `SQLSetPos`.

Aby uzyskać więcej informacji, zobacz artykuły [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [wymiany pól rekordu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Przykład

Zobacz [rfx_text_bulk —](#rfx_text_bulk).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="rfx_single_bulk"></a>  Rfx_single_bulk —

Przesyła wiele wierszy danych zmiennopozycyjnych z kolumną źródła danych ODBC do odpowiedniej tablicy w `CRecordset`-pochodnych obiektu.

### <a name="syntax"></a>Składnia

```
void RFX_Single_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   float** prgFltVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do [CFieldExchange](cfieldexchange-class.md) obiektu. Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*prgFltVals*<br/>
Wskaźnik do tablicy **float** wartości. Ta tablica będą przechowywane dane przesłane ze źródła danych do zestawu rekordów.

*prgLengths*<br/>
Wskaźnik do tablicy liczb całkowitych długie. Ta tablica zapisze długość w bajtach każdej wartości w tablicy, do których prowadzą *prgFltVals*. Należy zauważyć, że wartość SQL_NULL_DATA będą przechowywane, jeśli odpowiadającego mu elementu danych zawiera wartość Null. Aby uzyskać więcej informacji, zobacz opis funkcji interfejsu API ODBC `SQLBindCol` w *ODBC SDK Podręcznik programisty*.

### <a name="remarks"></a>Uwagi

Kolumny źródła danych musi mieć typ SQL_REAL ODBC. Zestaw rekordów musi definiować element członkowski danych pola typu wskaźnika do **float**.

Jeśli inicjowania *prgFltVals* i *prgLengths* na wartość NULL, a następnie tablic, które one wskazują zostaną przydzielone automatycznie, o rozmiarach równy rozmiarowi zestawu wierszy.

> [!NOTE]
>  Zbiorcza wymiana pól rekordów tylko przesyła dane ze źródła danych do obiektu zestawu rekordów. Aby rekordów można aktualizować, należy użyć funkcji interfejsu API ODBC `SQLSetPos`.

Aby uzyskać więcej informacji, zobacz artykuły [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [wymiany pól rekordu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Przykład

Zobacz [rfx_text_bulk —](#rfx_text_bulk).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h


## <a name="rfx_text_bulk"></a>  Rfx_text_bulk —

Przesyła wiele wierszy danych znakowych z kolumną źródła danych ODBC do odpowiedniej tablicy w `CRecordset`-pochodnych obiektu.

### <a name="syntax"></a>Składnia

```
void RFX_Text_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   LPSTR* prgStrVals,
   long** prgLengths,
   int nMaxLength);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do [CFieldExchange](cfieldexchange-class.md) obiektu. Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nazwa kolumny danych.

*prgStrVals*<br/>
Wskaźnik do tablicy wartości LPSTR. Ta tablica będą przechowywane dane przesłane ze źródła danych do zestawu rekordów. Należy pamiętać, że w bieżącej wersji ODBC, te wartości nie może być Unicode.

*prgLengths*<br/>
Wskaźnik do tablicy liczb całkowitych długie. Ta tablica zapisze długość w bajtach każdej wartości w tablicy, do których prowadzą *prgStrVals*. Tej długości wyklucza znak zakończenia o wartości null. Należy zauważyć, że wartość SQL_NULL_DATA będą przechowywane, jeśli odpowiadającego mu elementu danych zawiera wartość Null. Aby uzyskać więcej informacji, zobacz opis funkcji interfejsu API ODBC `SQLBindCol` w *ODBC SDK Podręcznik programisty*.

*nMaxLength*<br/>
Maksymalna dozwolona liczba znaków wartości przechowywane w tablicy, do których prowadzą *prgStrVals*, w tym znak zakończenia o wartości null. Aby upewnić się, że dane nie zostaną obcięte, należy przekazać wartość wystarczająco dużą do obsługi największych element danych, których oczekujesz.

### <a name="remarks"></a>Uwagi

Kolumny źródła danych może mieć typu ODBC SQL_LONGVARCHAR, SQL_CHAR, SQL_VARCHAR, SQL_DECIMAL lub SQL_NUMERIC. Zestaw rekordów, należy zdefiniować pole składowej danych typu LPSTR.

Jeśli inicjowania *prgStrVals* i *prgLengths* na wartość NULL, a następnie tablic, które one wskazują zostaną przydzielone automatycznie, o rozmiarach równy rozmiarowi zestawu wierszy.

> [!NOTE]
>  Zbiorcza wymiana pól rekordów tylko przesyła dane ze źródła danych do obiektu zestawu rekordów. Aby rekordów można aktualizować, należy użyć funkcji interfejsu API ODBC `SQLSetPos`.

Aby uzyskać więcej informacji, zobacz artykuły [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [wymiany pól rekordu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Przykład

Należy ręcznie napisać wywołań w swojej `DoBulkFieldExchange` zastąpienia. W tym przykładzie przedstawiono sposób wywołania `RFX_Text_Bulk`, a także wywołanie `RFX_Long_Bulk`, opłata za transfer danych. Te wywołania są poprzedzone wywołanie [CFieldExchange::SetFieldType](CFieldExchange::SetFieldType.md). Należy pamiętać, że dla parametrów, należy wywołać funkcje RFX zamiast funkcji zbiorcze RFX.

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

## <a name="dfx_binary"></a>  Dfx_binary —

Tablice bajtów do transferu między elementy członkowskie danych pola z [CDaoRecordset](cdaorecordset-class.md) obiektu i kolumn rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```
void AFXAPI DFX_Binary(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CByteArray& value,
   int nPreAllocSize = AFX_DAO_BINARY_DEFAULT_SIZE,
   DWORD dwBindOptions = 0);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji.

*szName*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu [CByteArray](cbytearray-class.md), pochodzi od elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.

*nPreAllocSize*<br/>
Struktura preallocates taka ilość pamięci. Jeśli danych jest większy, struktura zostanie przydzielone więcej miejsca, zgodnie z potrzebami. Lepszą wydajność Ustaw ten rozmiar na wartość wystarczająco duży, aby uniemożliwić ponowne alokacje. Domyślny rozmiar jest zdefiniowany w AFXDAO. Plik H jako AFX_DAO_BINARY_DEFAULT_SIZE.

*dwBindOptions*<br/>
Opcja, która umożliwia wykorzystanie biblioteki MFC podwójnego buforowania mechanizm wykrywania pól rekordów, które uległy zmianie. Domyślnie, AFX_DAO_DISABLE_FIELD_CACHE, nie mogą używać podwójnego buforowania, a następnie należy wywołać [SetFieldDirty](cdaorecordset-class.md#setfielddirty) i [SetFieldNull](cdaorecordset-class.md#setfieldnull) samodzielnie. Inne możliwe wartości AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania, a nie trzeba wykonać dodatkową pracę, aby oznaczyć pola zakłóconych lub wartość Null. Względu na wydajność i pamięci należy unikać tej wartości, chyba, że Twoje dane binarne jest stosunkowo niewielka.

> [!NOTE]
>  Można kontrolować, czy dane są double buforowana dla wszystkich pól domyślnie przez ustawienie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Data jest mapowany między typem DAO_BYTES w DAO i typem [CByteArray](cbytearray-class.md) w zestawie rekordów.

### <a name="example"></a>Przykład

Zobacz [dfx_text —](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h


## <a name="dfx_bool"></a>  Dfx_bool —

Transfer danych logicznych między elementy członkowskie danych pola z [CDaoRecordset](cdaorecordset-class.md) obiektu i kolumn rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```
void AFXAPI DFX_Bool(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BOOL& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji.

*szName*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych wartości typu BOOL, jest pobierana z elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.

*dwBindOptions*<br/>
Opcja, która umożliwia wykorzystanie biblioteki MFC podwójnego buforowania mechanizm wykrywania pól rekordów, które uległy zmianie. Domyślnie AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania. Możliwa wartość to AFX_DAO_DISABLE_FIELD_CACHE. Jeśli określono tę wartość MFC nie, żadne sprawdzanie dla tego pola. Należy wywołać `SetFieldDirty` i `SetFieldNull` samodzielnie.

> [!NOTE]
>  Można kontrolować, czy dane są double buforowana domyślnie przez ustawienie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Data jest mapowany między typem DAO_BOOL w DAO i typu BOOL w zestawie rekordów.

### <a name="example"></a>Przykład

Zobacz [dfx_text —](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="dfx_byte"></a>  Dfx_byte —

Transfery pojedynczy bajtów między elementy członkowskie danych pola z [CDaoRecordset](cdaorecordset-class.md) obiektu i kolumn rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```
void AFXAPI DFX_Byte(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BYTE& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji.

*szName*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych wartość typu BYTE, jest pobierana z elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.

*dwBindOptions*<br/>
Opcja, która umożliwia wykorzystanie biblioteki MFC podwójnego buforowania mechanizm wykrywania pól rekordów, które uległy zmianie. Domyślnie AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania. Możliwa wartość to AFX_DAO_DISABLE_FIELD_CACHE. Jeśli określono tę wartość MFC nie, żadne sprawdzanie dla tego pola. Należy wywołać `SetFieldDirty` i `SetFieldNull` samodzielnie.

> [!NOTE]
>  Można kontrolować, czy dane są double buforowana domyślnie przez ustawienie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Data jest mapowany między typem DAO_BYTES w DAO i typem BAJTÓW w zestawie rekordów.

### <a name="example"></a>Przykład

Zobacz [dfx_text —](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="dfx_currency"></a>  Dfx_currency —

Transfer danych walutowych między elementy członkowskie danych pola z [CDaoRecordset](cdaorecordset-class.md) obiektu i kolumn rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```
void AFXAPI DFX_Currency(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleCurrency& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji.

*szName*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, ta wartość jest pobierana z składowej danych określonego typu [COleCurrency](colecurrency-class.md). W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.

*dwBindOptions*<br/>
Opcja, która umożliwia wykorzystanie biblioteki MFC podwójnego buforowania mechanizm wykrywania pól rekordów, które uległy zmianie. Domyślnie AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania. Możliwa wartość to AFX_DAO_DISABLE_FIELD_CACHE. Jeśli określono tę wartość MFC nie, żadne sprawdzanie dla tego pola. Należy wywołać `SetFieldDirty` i `SetFieldNull` samodzielnie.

> [!NOTE]
>  Można kontrolować, czy dane są double buforowana domyślnie przez ustawienie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Data jest mapowany między typem DAO_CURRENCY w DAO i typem [COleCurrency](colecurrency-class.md) w zestawie rekordów.

### <a name="example"></a>Przykład

Zobacz [dfx_text —](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="dfx_datetime"></a>  Dfx_datetime —

Transfer danych Data i godzina między elementy członkowskie danych pola z [CDaoRecordset](cdaorecordset-class.md) obiektu i kolumn rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```
void AFXAPI DFX_DateTime(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleDateTime& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji.

*szName*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. Funkcja przyjmuje odwołanie do [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiektu. Transfer z zestawu rekordów do źródła danych ta wartość jest pobierana z elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.

*dwBindOptions*<br/>
Opcja, która umożliwia wykorzystanie biblioteki MFC podwójnego buforowania mechanizm wykrywania pól rekordów, które uległy zmianie. Domyślnie AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania. Możliwa wartość to AFX_DAO_DISABLE_FIELD_CACHE. Jeśli określono tę wartość MFC nie, żadne sprawdzanie dla tego pola. Należy wywołać `SetFieldDirty` i `SetFieldNull` samodzielnie.

> [!NOTE]
>  Można kontrolować, czy dane są double buforowana domyślnie przez ustawienie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Data jest mapowany między typem DAO_DATE w DAO i typem [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) w zestawie rekordów.

> [!NOTE]
>  `COleDateTime` zastępuje [CTime](../../atl-mfc-shared/reference/ctime-class.md) i TIMESTAMP_STRUCT w tym celu w klasach DAO. `CTime` i TIMESTAMP_STRUCT są nadal używane dla klas dostępu do danych ODBC.

### <a name="example"></a>Przykład

Zobacz [dfx_text —](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="dfx_double"></a>  Dfx_double —

Transfery **double float** danych między elementy członkowskie danych pola z [CDaoRecordset](cdaorecordset-class.md) obiektu i kolumn rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```
void AFXAPI DFX_Double(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   double& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji.

*szName*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu **double**, pochodzi od elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.

*dwBindOptions*<br/>
Opcja, która umożliwia wykorzystanie biblioteki MFC podwójnego buforowania mechanizm wykrywania pól rekordów, które uległy zmianie. Domyślnie AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania. Możliwa wartość to AFX_DAO_DISABLE_FIELD_CACHE. Jeśli określono tę wartość MFC nie, żadne sprawdzanie dla tego pola. Należy wywołać `SetFieldDirty` i `SetFieldNull` samodzielnie.

> [!NOTE]
>  Można kontrolować, czy dane są double buforowana domyślnie przez ustawienie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Data jest mapowany między typem DAO_R8 w DAO i typem **double float** w zestawie rekordów.

### <a name="example"></a>Przykład

Zobacz [dfx_text —](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="dfx_long"></a>  Dfx_long —

Transfer danych długich liczb całkowitych między elementy członkowskie danych pola z [CDaoRecordset](cdaorecordset-class.md) obiektu i kolumn rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```
void AFXAPI DFX_Long(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   long& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji.

*szName*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu **długie**, pochodzi od elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.

*dwBindOptions*<br/>
Opcja, która umożliwia wykorzystanie biblioteki MFC podwójnego buforowania mechanizm wykrywania pól rekordów, które uległy zmianie. Domyślnie AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania. Możliwa wartość to AFX_DAO_DISABLE_FIELD_CACHE. Jeśli określono tę wartość MFC nie, żadne sprawdzanie dla tego pola. Należy wywołać `SetFieldDirty` i `SetFieldNull` samodzielnie.

> [!NOTE]
>  Można kontrolować, czy dane są double buforowana domyślnie przez ustawienie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Data jest mapowany między typem DAO_I4 w DAO i typem **długie** w zestawie rekordów.

### <a name="example"></a>Przykład

Zobacz [dfx_text —](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h


## <a name="dfx_longbinary"></a>  Dfx_longbinary —

**Ważne** zaleca się, że używasz [dfx_binary —](#dfx_binary) zamiast tej funkcji.

### <a name="syntax"></a>Składnia

```
void AFXAPI DFX_LongBinary(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CLongBinary& value,
   DWORD dwPreAllocSize = AFX_DAO_LONGBINARY_DEFAULT_SIZE,
   DWORD dwBindOptions = 0);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji.

*szName*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu [CLongBinary](clongbinary-class.md), pochodzi od elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.

*dwPreAllocSize*<br/>
Struktura preallocates taka ilość pamięci. Jeśli danych jest większy, struktura zostanie przydzielone więcej miejsca, zgodnie z potrzebami. Lepszą wydajność Ustaw ten rozmiar na wartość wystarczająco duży, aby uniemożliwić ponowne alokacje.

*dwBindOptions*<br/>
Opcja, która umożliwia wykorzystanie biblioteki MFC podwójnego buforowania mechanizm wykrywania pól rekordów, które uległy zmianie. Domyślnie, AFX_DISABLE_FIELD_CACHE, nie mogą używać podwójnego buforowania. Możliwa wartość to AFX_DAO_ENABLE_FIELD_CACHE. Używa podwójnego buforowania, a nie trzeba wykonać dodatkową pracę, aby oznaczyć pola zakłóconych lub wartość Null. Względu na wydajność i pamięci należy unikać tej wartości, chyba, że Twoje dane binarne jest stosunkowo niewielka.

> [!NOTE]
>  Można kontrolować, czy dane są double buforowana domyślnie przez ustawienie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

`DFX_LongBinary` zapewnia zgodność z klas MFC ODBC. `DFX_LongBinary` Funkcja przesyła dane binarne dużych obiektów (BLOB), za pomocą klasy `CLongBinary` między elementy członkowskie danych pola z [CDaoRecordset](cdaorecordset-class.md) obiektu i kolumn rekordu w źródle danych. Data jest mapowany między typem DAO_BYTES w DAO i typem [CLongBinary](clongbinary-class.md) w zestawie rekordów.

### <a name="example"></a>Przykład

Zobacz [dfx_text —](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="dfx_short"></a>  Dfx_short —

Transfery krótkiej liczby całkowitej danych między elementy członkowskie danych pola z [CDaoRecordset](cdaorecordset-class.md) obiektu i kolumn rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```
void AFXAPI DFX_Short(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   short& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji.

*szName*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu **krótki**, pochodzi od elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.

*dwBindOptions*<br/>
Opcja, która umożliwia wykorzystanie biblioteki MFC podwójnego buforowania mechanizm wykrywania pól rekordów, które uległy zmianie. Domyślnie AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania. Możliwa wartość to AFX_DAO_DISABLE_FIELD_CACHE. Jeśli określono tę wartość MFC nie, żadne sprawdzanie dla tego pola. Należy wywołać `SetFieldDirty` i `SetFieldNull` samodzielnie.

> [!NOTE]
>  Można kontrolować, czy dane są double buforowana domyślnie przez ustawienie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Data jest mapowany między typem DAO_I2 w DAO i typem **krótki** w zestawie rekordów.

> [!NOTE]
>  `DFX_Short` jest odpowiednikiem [rfx_int —](#rfx_int) dla klas na podstawie ODBC.

### <a name="example"></a>Przykład

Zobacz [dfx_text —](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h


## <a name="dfx_single"></a>  Dfx_single —

Transfer danych zmiennopozycyjnych między elementy członkowskie danych pola z [CDaoRecordset](cdaorecordset-class.md) obiektu i kolumn rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```
void AFXAPI DFX_Single(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   float& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji.

*szName*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu **float**, pochodzi od elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.

*dwBindOptions*<br/>
Opcja, która umożliwia wykorzystanie biblioteki MFC podwójnego buforowania mechanizm wykrywania pól rekordów, które uległy zmianie. Domyślnie AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania. Możliwa wartość to AFX_DAO_DISABLE_FIELD_CACHE. Jeśli określono tę wartość MFC nie, żadne sprawdzanie dla tego pola. Należy wywołać `SetFieldDirty` i `SetFieldNull` samodzielnie.

> [!NOTE]
>  Można kontrolować, czy dane są double buforowana domyślnie przez ustawienie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Data jest mapowany między typem DAO_R4 w DAO i typem **float** w zestawie rekordów.

### <a name="example"></a>Przykład

Zobacz [dfx_text —](#dfx_text).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="dfx_text"></a>  Dfx_text —

Transfery `CString` danych między elementy członkowskie danych pola z [CDaoRecordset](cdaorecordset-class.md) obiektu i kolumn rekordu w źródle danych.

### <a name="syntax"></a>Składnia

```
void AFXAPI DFX_Text(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CString& value,
   int nPreAllocSize = AFX_DAO_TEXT_DEFAULT_SIZE,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji.

*szName*<br/>
Nazwa kolumny danych.

*value*<br/>
Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu [CString](../../atl-mfc-shared/reference/cstringt-class.md), pochodzi od elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.

*nPreAllocSize*<br/>
Struktura preallocates taka ilość pamięci. Jeśli danych jest większy, struktura zostanie przydzielone więcej miejsca, zgodnie z potrzebami. Lepszą wydajność Ustaw ten rozmiar na wartość wystarczająco duży, aby uniemożliwić ponowne alokacje.

*dwBindOptions*<br/>
Opcja, która umożliwia wykorzystanie biblioteki MFC podwójnego buforowania mechanizm wykrywania pól rekordów, które uległy zmianie. Domyślnie AFX_DAO_ENABLE_FIELD_CACHE, używa podwójnego buforowania. Możliwa wartość to AFX_DAO_DISABLE_FIELD_CACHE. Jeśli określono tę wartość MFC nie, żadne sprawdzanie dla tego pola. Należy wywołać [SetFieldDirty](cdaorecordset-class.md#setfielddirty) i [SetFieldNull](cdaorecordset-class.md#setfieldnull) samodzielnie.

> [!NOTE]
>  Można kontrolować, czy dane są double buforowana domyślnie przez ustawienie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Uwagi

Data jest mapowany między typem DAO_CHAR w DAO (lub, jeśli nie zdefiniowano _UNICODE symboli, DAO_WCHAR) i typ [CString](../../atl-mfc-shared/reference/cstringt-class.md) w zestawie rekordów.  n

### <a name="example"></a>Przykład

W tym przykładzie pokazano kilka wywołań `DFX_Text`. Zwróć uwagę, również dwa wywołania [CDaoFieldExchange::SetFieldType](cdaofieldexchange-class.md#setfieldtype). Trzeba napisać, pierwsze wywołanie `SetFieldType` i jego **DFX** wywołania. Drugie wywołanie i związanych z nią **DFX** wywołania są zwykle zapisywane przez kreatora kod, który wygenerował klasy.

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

[Makra i funkcje globalne](mfc-macros-and-globals.md)<br/>
[CRecordset::DoFieldExchange](crecordset-class.md#dofieldexchange)<br/>
[CRecordset::DoBulkFieldExchange](crecordset-class.md#dobulkfieldexchange)<br/>
[CDaoRecordset::DoFieldExchange](cdaorecordset-class.md#dofieldexchange)

