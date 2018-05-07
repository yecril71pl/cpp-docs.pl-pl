---
title: Funkcje wymiany pól rekordów | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 564d797a30e4b2d8518c73c5f7589aae205b6907
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="record-field-exchange-functions"></a>Funkcje wymiany pól rekordów
W tym temacie wymieniono wymiana pól rekordów (RFX RFX zbiorcze i DFX) funkcje używane do automatyzowania transferu danych między obiektem zestawu rekordów a źródłem danych i wykonywać inne operacje na danych.  
  
 Jeśli używasz klasy oparte na ODBC i zostały zaimplementowane zbiorcze pobieranie z wiersza, należy ręcznie zmienić `DoBulkFieldExchange` funkcji członkowskiej klasy `CRecordset` przez wywołanie funkcji RFX zbiorczego dla każdego elementu członkowskiego danych odpowiadające kolumnie źródła danych.  
  
 Jeśli nie zaimplementowano zbiorcze pobieranie z wiersza na podstawie ODBC klas, lub jeśli używasz klasy oparte na DAO ClassWizard spowoduje zastąpienie `DoFieldExchange` funkcji członkowskiej klasy `CRecordset` lub `CDaoRecordset` przez wywołanie funkcji RFX (dla ODBC — klasy ) lub funkcje DFX (dla klasy DAO) dla każdego elementu członkowskiego danych pola w twoim zestawie rekordów.  
  
 Funkcje wymiany pól rekordów transferu danych zawsze struktura wywołuje `DoFieldExchange` lub `DoBulkFieldExchange`. Każda funkcja przesyła dane określonego typu.  
  
 Aby uzyskać więcej informacji na temat korzystania z tych funkcji, zobacz artykuły [wymiana pól rekordów: jak działa RFX (ODBC)](../../data/odbc/record-field-exchange-how-rfx-works.md). Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Dla kolumny danych, które można powiązać dynamicznie, możesz także wywołać funkcji RFX lub DFX samodzielnie, zgodnie z objaśnieniem w artykułach [zestaw rekordów: dynamiczne wiązanie danych kolumn (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md). Ponadto można napisać własne niestandardowe procedury RFX lub DFX, zgodnie z objaśnieniem w technicznej Uwaga [43](../../mfc/tn043-rfx-routines.md) (dla ODBC) i Uwagi techniczne [53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) (dla DAO).  
  
 Na przykład RFX i RFX zbiorczego funkcje znajdujące się w `DoFieldExchange` i `DoBulkFieldExchange` funkcji, zobacz [rfx_text —](#rfx_text) i rfx_text_bulk — # [rfx_text_bulk —]). Funkcje DFX są bardzo podobne do funkcji RFX.  
  
### <a name="rfx-functions-odbc"></a>Funkcje RFX (ODBC)  
  
|||  
|-|-|  
|[Rfx_binary —](#rfx_binary)|Transfery tablice bajtów typu [CByteArray](cbytearray-class.md).|  
|[Rfx_bool —](#rfx_bool)|Transfery danych logicznych.|  
|[Rfx_byte —](#rfx_byte)|Przenosi pojedynczy bajt danych.|  
|[Rfx_date —](#rfx_date)|Transfery godzinę i datę danych przy użyciu [ctime —](../../atl-mfc-shared/reference/ctime-class.md) lub **TIMESTAMP_STRUCT**.|  
|[Rfx_double —](#rfx_double)|Przesyła dane zmiennoprzecinkowe podwójnej precyzji.|  
|[Rfx_int —](#rfx_int)|Transfery danych liczb całkowitych.|  
|[Rfx_long —](#rfx_long)|Transfery długości danych liczb całkowitych.|  
|[Rfx_longbinary —](#rfx_longbinary)|Transfery danych dużego obiektu binarnego (BLOB) za pomocą obiektu [clongbinary —](clongbinary-class.md) klasy.|  
|[Rfx_single —](#rfx_single)|Transfery float danych.|  
|[Rfx_text —](#rfx_text)|Dane ciągu transferów.|  
  
### <a name="bulk-rfx-functions-odbc"></a>Funkcje zbiorczej wymiany RFX (ODBC)  
  
|||  
|-|-|  
|[Rfx_binary_bulk —](#rfx_binary_bulk)|Transfery tablic bajtów danych.|  
|[Rfx_bool_bulk —](#rfx_bool_bulk)|Transfery tablic logiczną danych.|  
|[Rfx_byte_bulk —](#rfx_byte_bulk)|Transfery tablice bajtów pojedynczego.|  
|[Rfx_date_bulk —](#rfx_date_bulk)|Transfery tablic danych typu **TIMESTAMP_STRUCT**.|  
|[Rfx_double_bulk —](#rfx_double_bulk)|Transfery tablic danych podwójnej precyzji, zmiennoprzecinkowych.|  
|[Rfx_int_bulk —](#rfx_int_bulk)|Transfery tablic danych liczb całkowitych.|  
|[Rfx_long_bulk —](#rfx_long_bulk)|Transfery tablic danych długich liczb całkowitych.|  
|[Rfx_single_bulk —](#rfx_single_bulk)|Transfery tablic danych zmiennoprzecinkowych.|  
|[Rfx_text_bulk —](#rfx_text_bulk)|Transfery tablic danych typu **LPSTR**.|  
  
### <a name="dfx-functions-dao"></a>Funkcje DFX (DAO)  
  
|||
|-|-|  
|[Dfx_binary —](#dfx_binary)|Transfery tablice bajtów typu [CByteArray](cbytearray-class.md).|  
|[Dfx_bool —](#dfx_bool)|Transfery danych logicznych.|  
|[Dfx_byte —](#dfx_byte)|Przenosi pojedynczy bajt danych.|  
|[Dfx_currency —](#dfx_currency)|Transfery danych walutowych typu [COleCurrency](colecurrency-class.md).|  
|[Dfx_datetime —](#dfx_datetime)|Transfery danych Data i godzina, typu [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md).|  
|[Dfx_double —](#dfx_double)|Przesyła dane zmiennoprzecinkowe podwójnej precyzji.|  
|[Dfx_long —](#dfx_long)|Transfery długości danych liczb całkowitych.|  
|[Dfx_longbinary —](#dfx_longbinary)|Transfery danych dużego obiektu binarnego (BLOB) za pomocą obiektu `CLongBinary` klasy. Dla obiektów DAO, zaleca się używanie [dfx_binary —](#dfx_binary) zamiast tego.|  
|[Dfx_short —](#dfx_short)|Transfery krótka danych liczb całkowitych.|  
|[Dfx_single —](#dfx_single)|Transfery float danych.|  
|[Dfx_text —](#dfx_text)|Dane ciągu transferów.|  

 =============================================

## <a name="rfx_binary"></a>  Rfx_binary —
Transfery między elementy członkowskie danych pola z tablice bajtów `CRecordset` obiektu i kolumn w źródle danych ODBC typu rekordu **SQL_BINARY**, **SQL_VARBINARY**, lub **SQL_ LONGVARBINARY**.  
  
### <a name="syntax"></a>Składnia  
  
```
void RFX_Binary(  
   CFieldExchange* pFX,  
   const char* szName,  
   CByteArray& value,  
   int nMaxLength = 255);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` obiektu można określić, zapoznaj się z artykułem [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Nazwa kolumny danych.  
  
 *value*  
 Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu [CByteArray](cbytearray-class.md), pochodzi z elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.  
  
 `nMaxLength`  
 Maksymalna dozwolona długość ciąg lub tablica przesyłane. Wartość domyślna `nMaxLength` wynosi 255. Wartości to 1- `INT_MAX`. Platformę przydziela ilość miejsca dla danych. Aby uzyskać najlepszą wydajność należy przekazać wartość wystarczająco duże, aby pomieścić największy element danych oczekiwane.  
  
### <a name="remarks"></a>Uwagi  
 Dane w źródle danych tych typów jest zamapowana do i z typu `CByteArray` w zestawie rekordów.  
  
### <a name="example"></a>Przykład  
 Zobacz [rfx_text —](#rfx_text).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdb.h  

## <a name="rfx_bool"></a>  Rfx_bool —
Transfer danych logicznych między elementy członkowskie danych pola z `CRecordset` obiektu i kolumn w źródle danych ODBC typu rekordu **SQL_BIT**.  
  
### <a name="syntax"></a>Składnia  
  
```
void RFX_Bool(  
   CFieldExchange* pFX,  
   const char* szName,  
   BOOL& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` obiektu można określić, zapoznaj się z artykułem [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Nazwa kolumny danych.  
  
 *value*  
 Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu **BOOL**, pochodzi z elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.  
  
### <a name="example"></a>Przykład  
 Zobacz [rfx_text —](#rfx_text).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdb.h  

## <a name="rfx_byte"></a>  Rfx_byte —
Transfery pojedynczy bajtów między elementy członkowskie danych pola z `CRecordset` obiektu i kolumn w źródle danych ODBC typu rekordu **SQL_TINYINT**.  
  
### <a name="syntax"></a>Składnia  
  
```
void RFX_Byte(  
   CFieldExchange* pFX,  
   const char* szName,  
   BYTE& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` obiektu można określić, zapoznaj się z artykułem [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Nazwa kolumny danych.  
  
 *value*  
 Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu **BAJTÓW**, pochodzi z elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.  
  
### <a name="example"></a>Przykład  
 Zobacz [rfx_text —](#rfx_text).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdb.h  

## <a name="rfx_date"></a>  Rfx_date —
Transfery `CTime` lub **TIMESTAMP_STRUCT** danych między elementy członkowskie danych pola z `CRecordset` obiektu i kolumn w źródle danych ODBC typu rekordu **SQL_DATE**, **SQL_TIME**, lub **SQL_TIMESTAMP**.  
  
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
 `pFX`  
 Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` obiektu można określić, zapoznaj się z artykułem [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Nazwa kolumny danych.  
  
 *value*  
 Wartość przechowywana w element członkowski danych wskazany; wartość do przeniesienia. Różne wersje funkcji wykonać różne typy danych dla wartości:  
  
 Pierwszą wersję funkcja przyjmuje odwołanie do [ctime —](../../atl-mfc-shared/reference/ctime-class.md) obiektu. Transferu z zestawu rekordów do źródła danych ta wartość jest pobierana z elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.  
  
 Druga wersja funkcja przyjmuje odwołanie do **TIMESTAMP_STRUCT** struktury. Należy skonfigurować to struktura samodzielnie przed wywołaniem. Obsługuje ani wymiana danych okna dialogowego (DDX) ani obsługi kodu kreatora jest dostępna dla tej wersji. Trzecia wersja funkcja działa podobnie do pierwszej wersji z tą różnicą, że trwa odwołanie do [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 `CTime` Wersji funkcji nakłada koszty pośrednie przetwarza i ma nieco ograniczony zakres. Jeśli możesz znaleźć żadnego z tych czynników zbyt ograniczenie, użyj druga wersja funkcji. Jednak należy pamiętać, Brak kodu kreatora i pomocy technicznej DDX i wymaganie, skonfigurowanej w strukturze samodzielnie.  
  
### <a name="example"></a>Przykład  
 Zobacz [rfx_text —](#rfx_text).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdb.h  

## <a name="rfx_double"></a>  Rfx_double —
Transfery **podwójne float** danych między elementy członkowskie danych pola z `CRecordset` obiektu i kolumn w źródle danych ODBC typu rekordu **SQL_DOUBLE**.  
  
### <a name="syntax"></a>Składnia  
  
```
void RFX_Double(  
   CFieldExchange* pFX,  
   const char* szName,  
   double& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` obiektu można określić, zapoznaj się z artykułem [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Nazwa kolumny danych.  
  
 *value*  
 Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu **podwójne**, pochodzi z elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.  
  
### <a name="example"></a>Przykład  
 Zobacz [rfx_text —](#rfx_text).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdb.h  

## <a name="rfx_int"></a>  Rfx_int —
Transfer danych liczb całkowitych między elementy członkowskie danych pola z `CRecordset` obiektu i kolumn w źródle danych ODBC typu rekordu **SQL_SMALLINT**.  
  
### <a name="syntax"></a>Składnia  
  
```
void RFX_Int(  
   CFieldExchange* pFX,  
   const char* szName,  
   int& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` obiektu można określić, zapoznaj się z artykułem [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Nazwa kolumny danych.  
  
 *value*  
 Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu `int`, pochodzi z elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.  
  
### <a name="example"></a>Przykład  
 Zobacz [rfx_text —](#rfx_text).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdb.h  

## <a name="rfx_long"></a>  Rfx_long —
Transfer danych długich liczb całkowitych między elementy członkowskie danych pola z `CRecordset` obiektu i kolumn w źródle danych ODBC typu rekordu **SQL_INTEGER**.  
  
### <a name="syntax"></a>Składnia  
  
```
void RFX_Long(  
   CFieldExchange* pFX,  
   const char* szName,  
   LONG&   
value );  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` obiektu można określić, zapoznaj się z artykułem [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Nazwa kolumny danych.  
  
 *value*  
 Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu **długi**, pochodzi z elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.  
  
### <a name="example"></a>Przykład  
 Zobacz [rfx_text —](#rfx_text).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdb.h  
  
## <a name="rfx_longbinary"></a>  Rfx_longbinary —
Transfery danych dużego obiektu binarnego (BLOB) przy użyciu klasy [clongbinary —](clongbinary-class.md) między elementy członkowskie danych pola z `CRecordset` obiektu i kolumn w źródle danych ODBC typu rekordu **SQL_LONGVARBINARY**lub **SQL_LONGVARCHAR**.  
  
### <a name="syntax"></a>Składnia  
  
```
void RFX_LongBinary(  
   CFieldExchange* pFX,  
   const char* szName,  
   CLongBinary& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` obiektu można określić, zapoznaj się z artykułem [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Nazwa kolumny danych.  
  
 *value*  
 Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu `CLongBinary`, pochodzi z elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.  
  
### <a name="example"></a>Przykład  
 Zobacz [rfx_text —](#rfx_text).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdb.h  

## <a name="rfx_single"></a>  Rfx_single —
Transfer danych zmiennoprzecinkowych między elementy członkowskie danych pola z `CRecordset` obiektu i kolumn w źródle danych ODBC typu rekordu **SQL_REAL**.  
  
### <a name="syntax"></a>Składnia  
  
```
void RFX_Single(  
   CFieldExchange* pFX,  
   const char* szName,  
   float& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` obiektu można określić, zapoznaj się z artykułem [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Nazwa kolumny danych.  
  
 *value*  
 Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu **float**, pochodzi z elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.  
  
### <a name="example"></a>Przykład  
 Zobacz [rfx_text —](#rfx_text).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdb.h  
  

## <a name="rfx_text"></a>  Rfx_text —
Transfery `CString` danych między elementy członkowskie danych pola z `CRecordset` obiektu i kolumn w źródle danych ODBC typu rekordu **SQL_LONGVARCHAR**, **SQL_CHAR**, **SQL_ VARCHAR**, **SQL_DECIMAL**, lub **SQL_NUMERIC**.  
  
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
 `pFX`  
 Wskaźnik do obiektu klasy `CFieldExchange`. Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` obiektu można określić, zapoznaj się z artykułem [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Nazwa kolumny danych.  
  
 *value*  
 Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu `CString`, pochodzi z elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.  
  
 `nMaxLength`  
 Maksymalna dozwolona długość ciąg lub tablica przesyłane. Wartość domyślna `nMaxLength` wynosi 255. Wartości to 1- `INT_MAX`). Platformę przydziela ilość miejsca dla danych. Aby uzyskać najlepszą wydajność należy przekazać wartość wystarczająco duże, aby pomieścić największy element danych oczekiwane.  
  
 *nColumnType*  
 Używany głównie dla parametrów. Liczba całkowita wskazująca typ danych parametru. Typ jest typem danych ODBC formularza **SQL_XXX**.  
  
 `nScale`  
 Określa skalę dla wartości typu ODBC **SQL_DECIMAL** lub **SQL_NUMERIC**. `nScale` jest przydatna podczas ustawiania wartości parametrów. Aby uzyskać więcej informacji, zobacz temat "Precyzja, skala długość i rozmiar wyświetlania" w dodatku D *ODBC SDK Podręcznik programisty*.  
  
### <a name="remarks"></a>Uwagi  
 Dane w źródle danych typu jest zamapowana do i z `CString` w zestawie rekordów.  
  
### <a name="example"></a>Przykład  
 W tym przykładzie pokazano kilka wywołań `RFX_Text`. Zauważ również dwa wywołań `CFieldExchange::SetFieldType`. Dla parametrów musi być zapisana wywołanie `SetFieldType` i jego RFX wywołania. Wywołanie kolumny danych wyjściowych i jego skojarzony wywołania RFX zwykle są zapisywane przez kreatora kodu.  
  
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
Przesyła wiele wierszy danych bajtowych z kolumną źródła danych ODBC do odpowiedniego tablicy w `CRecordset`-pochodzi z obiektu.  
  
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
 `pFX`  
 Wskaźnik do [CFieldExchange](cfieldexchange-class.md) obiektu. Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Nazwa kolumny danych.  
  
 `prgByteVals`  
 Wskaźnik do tablicy **BAJTÓW** wartości. Ta tablica będzie przechowywać danych przekazywanych ze źródła danych do zestawu rekordów.  
  
 `prgLengths`  
 Wskaźnik do tablicy długich liczb całkowitych. Ta tablica zapisze długość w bajtach każdej wartości w tablicy wskazywana przez `prgByteVals`. Należy pamiętać, że wartość **SQL_NULL_DATA** będą przechowywane, jeśli odpowiadający mu element danych zawiera wartość Null. Aby uzyskać więcej informacji, zobacz opis funkcji interfejsu API ODBC **Procedura SQLBindCol** w *ODBC SDK Podręcznik programisty*.  
  
 `nMaxLength`  
 Maksymalna dozwolona długość wartości przechowywane w tablicy wskazywana przez `prgByteVals`. Aby upewnić się, że dane nie zostaną obcięte, należy przekazać wartość wystarczająco duże, aby pomieścić największy element danych oczekiwane.  
  
### <a name="remarks"></a>Uwagi  
 Kolumna źródła danych może mieć typu ODBC **SQL_BINARY**, **SQL_VARBINARY**, lub **SQL_LONGVARBINARY**. Zestaw rekordów należy zdefiniować element członkowski danych pola typu wskaźnika do **BAJTÓW**.  
  
 Jeśli musisz zainicjować `prgByteVals` i `prgLengths` do **NULL**, następnie tablice nie zostaną przydzielone automatycznie, o rozmiarze równe rozmiarowi zestawu wierszy.  
  
> [!NOTE]
>  Zbiorcza wymiana pól rekordów tylko przesyła dane ze źródła danych do obiektu zestawu rekordów. Aby ustawić można aktualizować zestawu rekordów, należy użyć funkcji interfejsu API ODBC **SQLSetPos**.  
  
 Aby uzyskać więcej informacji, zobacz artykuły [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [wymiany pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
### <a name="example"></a>Przykład  
 Zobacz [rfx_text_bulk —](#rfx_text_bulk).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdb.h  

## <a name="rfx_bool_bulk"></a>  Rfx_bool_bulk —
Przesyła wiele wierszy danych logicznych z kolumną źródła danych ODBC do odpowiedniego tablicy w `CRecordset`-pochodzi z obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```
void RFX_Bool_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   BOOL** prgBoolVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Wskaźnik do [CFieldExchange](cfieldexchange-class.md) obiektu. Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Nazwa kolumny danych.  
  
 `prgBoolVals`  
 Wskaźnik do tablicy **BOOL** wartości. Ta tablica będzie przechowywać danych przekazywanych ze źródła danych do zestawu rekordów.  
  
 `prgLengths`  
 Wskaźnik do tablicy długich liczb całkowitych. Ta tablica zapisze długość w bajtach każdej wartości w tablicy wskazywana przez `prgBoolVals`. Należy pamiętać, że wartość **SQL_NULL_DATA** będą przechowywane, jeśli odpowiadający mu element danych zawiera wartość Null. Aby uzyskać więcej informacji, zobacz opis funkcji interfejsu API ODBC **Procedura SQLBindCol** w *ODBC SDK Podręcznik programisty*.  
  
### <a name="remarks"></a>Uwagi  
 Kolumny źródła danych muszą mieć typ ODBC **SQL_BIT**. Zestaw rekordów należy zdefiniować element członkowski danych pola typu wskaźnika do **BOOL**.  
  
 Jeśli musisz zainicjować `prgBoolVals` i `prgLengths` do **NULL**, następnie tablice nie zostaną przydzielone automatycznie, o rozmiarze równe rozmiarowi zestawu wierszy.  
  
> [!NOTE]
>  Zbiorcza wymiana pól rekordów tylko przesyła dane ze źródła danych do obiektu zestawu rekordów. Aby wprowadzić można aktualizować zestawu rekordów, należy użyć funkcji interfejsu API ODBC **SQLSetPos**.  
  
 Aby uzyskać więcej informacji, zobacz artykuły [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [wymiany pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
### <a name="example"></a>Przykład  
 Zobacz [rfx_text_bulk —](#rfx_text_bulk).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdb.h  

## <a name="rfx_byte_bulk"></a>  Rfx_byte_bulk —
Przesyła wiele wierszy bajtów jednego z kolumną źródła danych ODBC do odpowiedniego tablicy w `CRecordset`-pochodzi z obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```
void RFX_Byte_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   BYTE** prgByteVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Wskaźnik do [CFieldExchange](cfieldexchange-class.md) obiektu. Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Nazwa kolumny danych.  
  
 `prgByteVals`  
 Wskaźnik do tablicy **BAJTÓW** wartości. Ta tablica będzie przechowywać danych przekazywanych ze źródła danych do zestawu rekordów.  
  
 `prgLengths`  
 Wskaźnik do tablicy długich liczb całkowitych. Ta tablica zapisze długość w bajtach każdej wartości w tablicy wskazywana przez `prgByteVals`. Należy pamiętać, że wartość **SQL_NULL_DATA** będą przechowywane, jeśli odpowiadający mu element danych zawiera wartość Null. Aby uzyskać więcej informacji, zobacz opis funkcji interfejsu API ODBC **Procedura SQLBindCol** w *ODBC SDK Podręcznik programisty*.  
  
### <a name="remarks"></a>Uwagi  
 Kolumny źródła danych muszą mieć typ ODBC **SQL_TINYINT**. Zestaw rekordów należy zdefiniować element członkowski danych pola typu wskaźnika do **BAJTÓW**.  
  
 Jeśli musisz zainicjować `prgByteVals` i `prgLengths` do **NULL**, następnie tablice nie zostaną przydzielone automatycznie, o rozmiarze równe rozmiarowi zestawu wierszy.  
  
> [!NOTE]
>  Zbiorcza wymiana pól rekordów tylko przesyła dane ze źródła danych do obiektu zestawu rekordów. Aby wprowadzić można aktualizować zestawu rekordów, należy użyć funkcji interfejsu API ODBC **SQLSetPos**.  
  
 Aby uzyskać więcej informacji, zobacz artykuły [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [wymiany pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
### <a name="example"></a>Przykład  
 Zobacz [rfx_text_bulk —](#rfx_text_bulk).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdb.h  
  
## <a name="rfx_date_bulk"></a>  Rfx_date_bulk —
Przesyła wiele wierszy **TIMESTAMP_STRUCT** danych z kolumny źródła danych ODBC do odpowiedniego tablicy w `CRecordset`-pochodzi z obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```
void RFX_Date_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   TIMESTAMP_STRUCT** prgTSVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Wskaźnik do [CFieldExchange](cfieldexchange-class.md) obiektu. Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Nazwa kolumny danych.  
  
 `prgTSVals`  
 Wskaźnik do tablicy **TIMESTAMP_STRUCT** wartości. Ta tablica będzie przechowywać danych przekazywanych ze źródła danych do zestawu rekordów. Aby uzyskać więcej informacji na temat **TIMESTAMP_STRUCT** typ danych, zobacz temat "Typy danych C" z dodatkiem D *ODBC SDK Podręcznik programisty*.  
  
 `prgLengths`  
 Wskaźnik do tablicy długich liczb całkowitych. Ta tablica zapisze długość w bajtach każdej wartości w tablicy wskazywana przez `prgTSVals`. Należy pamiętać, że wartość **SQL_NULL_DATA** będą przechowywane, jeśli odpowiadający mu element danych zawiera wartość Null. Aby uzyskać więcej informacji, zobacz opis funkcji interfejsu API ODBC **Procedura SQLBindCol** w *ODBC SDK Podręcznik programisty*.  
  
### <a name="remarks"></a>Uwagi  
 Kolumna źródła danych może mieć typu ODBC **SQL_DATE**, **SQL_TIME**, lub **SQL_TIMESTAMP**. Zestaw rekordów należy zdefiniować element członkowski danych pola typu wskaźnika do **TIMESTAMP_STRUCT**.  
  
 Jeśli musisz zainicjować `prgTSVals` i `prgLengths` do **NULL**, następnie tablice nie zostaną przydzielone automatycznie, o rozmiarze równe rozmiarowi zestawu wierszy.  
  
> [!NOTE]
>  Zbiorcza wymiana pól rekordów tylko przesyła dane ze źródła danych do obiektu zestawu rekordów. Aby wprowadzić można aktualizować zestawu rekordów, należy użyć funkcji interfejsu API ODBC **SQLSetPos**.  
  
 Aby uzyskać więcej informacji, zobacz artykuły [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [wymiany pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
### <a name="example"></a>Przykład  
 Zobacz [rfx_text_bulk —](#rfx_text_bulk).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdb.h  

## <a name="rfx_double_bulk"></a>  Rfx_double_bulk —
Przesyła wiele wierszy danych podwójnej precyzji, zmiennoprzecinkowych z kolumną źródła danych ODBC do odpowiedniego tablicy w `CRecordset`-pochodzi z obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```
void RFX_Double_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   double** prgDblVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Wskaźnik do [CFieldExchange](cfieldexchange-class.md) obiektu. Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Nazwa kolumny danych.  
  
 `prgDblVals`  
 Wskaźnik do tablicy **podwójne** wartości. Ta tablica będzie przechowywać danych przekazywanych ze źródła danych do zestawu rekordów.  
  
 `prgLengths`  
 Wskaźnik do tablicy długich liczb całkowitych. Ta tablica zapisze długość w bajtach każdej wartości w tablicy wskazywana przez `prgDblVals`. Należy pamiętać, że wartość **SQL_NULL_DATA** będą przechowywane, jeśli odpowiadający mu element danych zawiera wartość Null. Aby uzyskać więcej informacji, zobacz opis funkcji interfejsu API ODBC **Procedura SQLBindCol** w *ODBC SDK Podręcznik programisty*.  
  
### <a name="remarks"></a>Uwagi  
 Kolumny źródła danych muszą mieć typ ODBC **SQL_DOUBLE**. Zestaw rekordów należy zdefiniować element członkowski danych pola typu wskaźnika do **podwójne**.  
  
 Jeśli musisz zainicjować `prgDblVals` i `prgLengths` do **NULL**, następnie tablice nie zostaną przydzielone automatycznie, o rozmiarze równe rozmiarowi zestawu wierszy.  
  
> [!NOTE]
>  Zbiorcza wymiana pól rekordów tylko przesyła dane ze źródła danych do obiektu zestawu rekordów. Aby wprowadzić można aktualizować zestawu rekordów, należy użyć funkcji interfejsu API ODBC **SQLSetPos**.  
  
 Aby uzyskać więcej informacji, zobacz artykuły [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [wymiany pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
### <a name="example"></a>Przykład  
 Zobacz [rfx_text_bulk —](#rfx_text_bulk).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdb.h  

## <a name="rfx_int_bulk"></a>  Rfx_int_bulk —
Transfer danych liczb całkowitych między elementy członkowskie danych pola z `CRecordset` obiektu i kolumn w źródle danych ODBC typu rekordu **SQL_SMALLINT**.  
  
### <a name="syntax"></a>Składnia  
  
```
void RFX_Int(  
   CFieldExchange* pFX,  
   const char* szName,  
   int& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Wskaźnik do obiektu klasy [CFieldExchange](cfieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji o operacjach `CFieldExchange` obiektu można określić, zapoznaj się z artykułem [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Nazwa kolumny danych.  
  
 *value*  
 Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu `int`, pochodzi z elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.  
  
### <a name="example"></a>Przykład  
 Zobacz [rfx_text —](#rfx_text).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdb.h  

## <a name="rfx_long_bulk"></a>  Rfx_long_bulk —
Przesyła wiele wierszy danych długich liczb całkowitych z kolumną źródła danych ODBC do odpowiedniego tablicy w `CRecordset`-pochodzi z obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```
void RFX_Long_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   long** prgLongVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Wskaźnik do [CFieldExchange](cfieldexchange-class.md) obiektu. Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Nazwa kolumny danych.  
  
 `prgLongVals`  
 Wskaźnik do tablicy długich liczb całkowitych. Ta tablica będzie przechowywać danych przekazywanych ze źródła danych do zestawu rekordów.  
  
 `prgLengths`  
 Wskaźnik do tablicy długich liczb całkowitych. Ta tablica zapisze długość w bajtach każdej wartości w tablicy wskazywana przez `prgLongVals`. Należy pamiętać, że wartość **SQL_NULL_DATA** będą przechowywane, jeśli odpowiadający mu element danych zawiera wartość Null. Aby uzyskać więcej informacji, zobacz opis funkcji interfejsu API ODBC **Procedura SQLBindCol** w *ODBC SDK Podręcznik programisty*.  
  
### <a name="remarks"></a>Uwagi  
 Kolumny źródła danych muszą mieć typ ODBC **SQL_INTEGER**. Zestaw rekordów należy zdefiniować element członkowski danych pola typu wskaźnika do **długi**.  
  
 Jeśli musisz zainicjować `prgLongVals` i `prgLengths` do **NULL**, następnie tablice nie zostaną przydzielone automatycznie, o rozmiarze równe rozmiarowi zestawu wierszy.  
  
> [!NOTE]
>  Zbiorcza wymiana pól rekordów tylko przesyła dane ze źródła danych do obiektu zestawu rekordów. Aby wprowadzić można aktualizować zestawu rekordów, należy użyć funkcji interfejsu API ODBC **SQLSetPos**.  
  
 Aby uzyskać więcej informacji, zobacz artykuły [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [wymiany pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
### <a name="example"></a>Przykład  
 Zobacz [rfx_text_bulk —](#rfx_text_bulk).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdb.h  

## <a name="rfx_single_bulk"></a>  Rfx_single_bulk —
Przesyła wiele wierszy danych zmiennoprzecinkowych z kolumną źródła danych ODBC do odpowiedniego tablicy w `CRecordset`-pochodzi z obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```
void RFX_Single_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   float** prgFltVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Wskaźnik do [CFieldExchange](cfieldexchange-class.md) obiektu. Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Nazwa kolumny danych.  
  
 `prgFltVals`  
 Wskaźnik do tablicy **float** wartości. Ta tablica będzie przechowywać danych przekazywanych ze źródła danych do zestawu rekordów.  
  
 `prgLengths`  
 Wskaźnik do tablicy długich liczb całkowitych. Ta tablica zapisze długość w bajtach każdej wartości w tablicy wskazywana przez `prgFltVals`. Należy pamiętać, że wartość **SQL_NULL_DATA** będą przechowywane, jeśli odpowiadający mu element danych zawiera wartość Null. Aby uzyskać więcej informacji, zobacz opis funkcji interfejsu API ODBC **Procedura SQLBindCol** w *ODBC SDK Podręcznik programisty*.  
  
### <a name="remarks"></a>Uwagi  
 Kolumny źródła danych muszą mieć typ ODBC **SQL_REAL**. Zestaw rekordów należy zdefiniować element członkowski danych pola typu wskaźnika do **float**.  
  
 Jeśli musisz zainicjować `prgFltVals` i `prgLengths` do **NULL**, następnie tablice nie zostaną przydzielone automatycznie, o rozmiarze równe rozmiarowi zestawu wierszy.  
  
> [!NOTE]
>  Zbiorcza wymiana pól rekordów tylko przesyła dane ze źródła danych do obiektu zestawu rekordów. Aby wprowadzić można aktualizować zestawu rekordów, należy użyć funkcji interfejsu API ODBC **SQLSetPos**.  
  
 Aby uzyskać więcej informacji, zobacz artykuły [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [wymiany pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
### <a name="example"></a>Przykład  
 Zobacz [rfx_text_bulk —](#rfx_text_bulk).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdb.h  
  

## <a name="rfx_text_bulk"></a>  Rfx_text_bulk —
Przesyła wiele wierszy danych znakowych z kolumną źródła danych ODBC do odpowiedniego tablicy w `CRecordset`-pochodzi z obiektu.  
  
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
 `pFX`  
 Wskaźnik do [CFieldExchange](cfieldexchange-class.md) obiektu. Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Nazwa kolumny danych.  
  
 `prgStrVals`  
 Wskaźnik do tablicy **LPSTR** wartości. Ta tablica będzie przechowywać danych przekazywanych ze źródła danych do zestawu rekordów. Należy pamiętać, że w bieżącej wersji ODBC, te wartości nie może być w formacie Unicode.  
  
 `prgLengths`  
 Wskaźnik do tablicy długich liczb całkowitych. Ta tablica zapisze długość w bajtach każdej wartości w tablicy wskazywana przez `prgStrVals`. To długość wyklucza znak zakończenia o wartości null. Należy pamiętać, że wartość **SQL_NULL_DATA** będą przechowywane, jeśli odpowiadający mu element danych zawiera wartość Null. Aby uzyskać więcej informacji, zobacz opis funkcji interfejsu API ODBC **Procedura SQLBindCol** w *ODBC SDK Podręcznik programisty*.  
  
 `nMaxLength`  
 Maksymalna dozwolona długość wartości przechowywane w tablicy wskazywana przez `prgStrVals`, tym znak zakończenia o wartości null. Aby upewnić się, że dane nie zostaną obcięte, należy przekazać wartość wystarczająco duże, aby pomieścić największy element danych oczekiwane.  
  
### <a name="remarks"></a>Uwagi  
 Kolumna źródła danych może mieć typu ODBC **SQL_LONGVARCHAR**, **SQL_CHAR**, **SQL_VARCHAR**, **SQL_DECIMAL**, lub **SQL_NUMERIC**. Zestaw rekordów należy zdefiniować element członkowski danych pola typu **LPSTR**.  
  
 Jeśli musisz zainicjować `prgStrVals` i `prgLengths` do **NULL**, następnie tablice nie zostaną przydzielone automatycznie, o rozmiarze równe rozmiarowi zestawu wierszy.  
  
> [!NOTE]
>  Zbiorcza wymiana pól rekordów tylko przesyła dane ze źródła danych do obiektu zestawu rekordów. Aby wprowadzić można aktualizować zestawu rekordów, należy użyć funkcji interfejsu API ODBC **SQLSetPos**.  
  
 Aby uzyskać więcej informacji, zobacz artykuły [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) i [wymiany pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
### <a name="example"></a>Przykład  
 Należy ręcznie napisać wywołań w Twojej `DoBulkFieldExchange` zastąpienia. W tym przykładzie przedstawiono sposób wywołania `RFX_Text_Bulk`, a także wywołania `RFX_Long_Bulk`, do transferu danych. Te wywołania są poprzedzone wywołanie [CFieldExchange::SetFieldType](CFieldExchange::SetFieldType.md). Należy pamiętać, że dla parametrów, należy wywołać funkcji RFX zamiast funkcji RFX zbiorczego.  
  
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
Transfery między elementy członkowskie danych pola z tablice bajtów [cdaorecordset —](cdaorecordset-class.md) obiektu i kolumny rekordu w źródle danych.  
  
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
 `pFX`  
 Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji.  
  
 `szName`  
 Nazwa kolumny danych.  
  
 *value*  
 Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu [CByteArray](cbytearray-class.md), pochodzi z elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.  
  
 `nPreAllocSize`  
 Platformę preallocates to ilość pamięci. Jeśli dane są większe, platformę zostaną przydzielone więcej miejsca, w razie potrzeby. Lepszą wydajność Ustaw ten rozmiar wystarczająco duży, aby zapobiec przeniesień wartość. Domyślny rozmiar jest zdefiniowany w AFXDAO. H pliku jako **AFX_DAO_BINARY_DEFAULT_SIZE**.  
  
 `dwBindOptions`  
 Opcja, która umożliwia wykorzystanie mechanizmu MFC podwójnego buforowania wykrywania pól rekordów, które zostały zmienione. Wartość domyślna `AFX_DAO_DISABLE_FIELD_CACHE`nie Użyj podwójnego buforowania i należy wywołać [SetFieldDirty](cdaorecordset-class.md#setfielddirty) i [SetFieldNull](cdaorecordset-class.md#setfieldnull) samodzielnie. Możliwa wartość, `AFX_DAO_ENABLE_FIELD_CACHE`, używa podwójnego buforowania, na które ma wykonywać dodatkowe zadania do oznaczenia zmieniony, lub wartość Null. Względu na wydajność i pamięci należy unikać tej wartości, chyba, że dane binarne jest stosunkowo mały.  
  
> [!NOTE]
>  Można kontrolować, czy dane są dwa razy buforowana we wszystkich polach, domyślnie przez ustawienie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Uwagi  
 Dane są zmapowane między typem **DAO_BYTES** w DAO i wpisz [CByteArray](cbytearray-class.md) w zestawie rekordów.  
  
### <a name="example"></a>Przykład  
 Zobacz [dfx_text —](#dfx_text).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  
  

## <a name="dfx_bool"></a>  Dfx_bool —
Transfer danych logicznych między elementy członkowskie danych pola z [cdaorecordset —](cdaorecordset-class.md) obiektu i kolumny rekordu w źródle danych.  
  
### <a name="syntax"></a>Składnia  
  
```
void AFXAPI DFX_Bool(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   BOOL& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji.  
  
 `szName`  
 Nazwa kolumny danych.  
  
 *value*  
 Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu **BOOL**, pochodzi z elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.  
  
 `dwBindOptions`  
 Opcja, która umożliwia wykorzystanie mechanizmu MFC podwójnego buforowania wykrywania pól rekordów, które zostały zmienione. Wartość domyślna `AFX_DAO_ENABLE_FIELD_CACHE`, używa podwójnego buforowania. Możliwa wartość to `AFX_DAO_DISABLE_FIELD_CACHE`. Jeśli ta wartość jest określona, MFC nie bez sprawdzania dla tego pola. Należy wywołać `SetFieldDirty` i `SetFieldNull` samodzielnie.  
  
> [!NOTE]
>  Można kontrolować, czy dane są dwa razy buforowana domyślnie przez ustawienie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Uwagi  
 Dane są zmapowane między typem **DAO_BOOL** w DAO i wpisz **BOOL** w zestawie rekordów.  
  
### <a name="example"></a>Przykład  
 Zobacz [dfx_text —](#dfx_text).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  

## <a name="dfx_byte"></a>  Dfx_byte —
Transfery pojedynczy bajtów między elementy członkowskie danych pola z [cdaorecordset —](cdaorecordset-class.md) obiektu i kolumny rekordu w źródle danych.  
  
### <a name="syntax"></a>Składnia  
  
```
void AFXAPI DFX_Byte(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   BYTE& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji.  
  
 `szName`  
 Nazwa kolumny danych.  
  
 *value*  
 Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu **BAJTÓW**, pochodzi z elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.  
  
 `dwBindOptions`  
 Opcja, która umożliwia wykorzystanie mechanizmu MFC podwójnego buforowania wykrywania pól rekordów, które zostały zmienione. Wartość domyślna `AFX_DAO_ENABLE_FIELD_CACHE`, używa podwójnego buforowania. Możliwa wartość to `AFX_DAO_DISABLE_FIELD_CACHE`. Jeśli ta wartość jest określona, MFC nie bez sprawdzania dla tego pola. Należy wywołać `SetFieldDirty` i `SetFieldNull` samodzielnie.  
  
> [!NOTE]
>  Można kontrolować, czy dane są dwa razy buforowana domyślnie przez ustawienie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Uwagi  
 Dane są zmapowane między typem **DAO_BYTES** w DAO i wpisz **BAJTÓW** w zestawie rekordów.  
  
### <a name="example"></a>Przykład  
 Zobacz [dfx_text —](#dfx_text).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  

## <a name="dfx_currency"></a>  Dfx_currency —
Transfer danych walutowych między elementy członkowskie danych pola z [cdaorecordset —](cdaorecordset-class.md) obiektu i kolumny rekordu w źródle danych.  
  
### <a name="syntax"></a>Składnia  
  
```
void AFXAPI DFX_Currency(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   COleCurrency& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji.  
  
 `szName`  
 Nazwa kolumny danych.  
  
 *value*  
 Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, ta wartość jest pobierana z elementu członkowskiego danych określonego typu [COleCurrency](colecurrency-class.md). W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.  
  
 `dwBindOptions`  
 Opcja, która umożliwia wykorzystanie mechanizmu MFC podwójnego buforowania wykrywania pól rekordów, które zostały zmienione. Wartość domyślna `AFX_DAO_ENABLE_FIELD_CACHE`, używa podwójnego buforowania. Możliwa wartość to `AFX_DAO_DISABLE_FIELD_CACHE`. Jeśli ta wartość jest określona, MFC nie bez sprawdzania dla tego pola. Należy wywołać `SetFieldDirty` i `SetFieldNull` samodzielnie.  
  
> [!NOTE]
>  Można kontrolować, czy dane są dwa razy buforowana domyślnie przez ustawienie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Uwagi  
 Dane są zmapowane między typem **DAO_CURRENCY** w DAO i wpisz [COleCurrency](colecurrency-class.md) w zestawie rekordów.  
  
### <a name="example"></a>Przykład  
 Zobacz [dfx_text —](#dfx_text).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  

## <a name="dfx_datetime"></a>  Dfx_datetime —
Transfer danych Data i godzina między elementy członkowskie danych pola z [cdaorecordset —](cdaorecordset-class.md) obiektu i kolumny rekordu w źródle danych.  
  
### <a name="syntax"></a>Składnia  
  
```
void AFXAPI DFX_DateTime(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   COleDateTime& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji.  
  
 `szName`  
 Nazwa kolumny danych.  
  
 *value*  
 Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. Funkcja przyjmuje odwołanie do [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiektu. Transferu z zestawu rekordów do źródła danych ta wartość jest pobierana z elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.  
  
 `dwBindOptions`  
 Opcja, która umożliwia wykorzystanie mechanizmu MFC podwójnego buforowania wykrywania pól rekordów, które zostały zmienione. Wartość domyślna `AFX_DAO_ENABLE_FIELD_CACHE`, używa podwójnego buforowania. Możliwa wartość to `AFX_DAO_DISABLE_FIELD_CACHE`. Jeśli ta wartość jest określona, MFC nie bez sprawdzania dla tego pola. Należy wywołać `SetFieldDirty` i `SetFieldNull` samodzielnie.  
  
> [!NOTE]
>  Można kontrolować, czy dane są dwa razy buforowana domyślnie przez ustawienie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Uwagi  
 Dane są zmapowane między typem **DAO_DATE** w DAO i wpisz [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) w zestawie rekordów.  
  
> [!NOTE]
>  `COleDateTime` zastępuje [ctime —](../../atl-mfc-shared/reference/ctime-class.md) i **TIMESTAMP_STRUCT** w tym celu w klasach DAO. `CTime` i **TIMESTAMP_STRUCT** nadal są używane dla klas dostępu do danych ODBC.  
  
### <a name="example"></a>Przykład  
 Zobacz [dfx_text —](#dfx_text).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  

## <a name="dfx_double"></a>  Dfx_double —
Transfery **podwójne float** danych między elementy członkowskie danych pola z [cdaorecordset —](cdaorecordset-class.md) obiektu i kolumny rekordu w źródle danych.  
  
### <a name="syntax"></a>Składnia  
  
```
void AFXAPI DFX_Double(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   double& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji.  
  
 `szName`  
 Nazwa kolumny danych.  
  
 *value*  
 Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu **podwójne**, pochodzi z elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.  
  
 `dwBindOptions`  
 Opcja, która umożliwia wykorzystanie mechanizmu MFC podwójnego buforowania wykrywania pól rekordów, które zostały zmienione. Wartość domyślna `AFX_DAO_ENABLE_FIELD_CACHE`, używa podwójnego buforowania. Możliwa wartość to `AFX_DAO_DISABLE_FIELD_CACHE`. Jeśli ta wartość jest określona, MFC nie bez sprawdzania dla tego pola. Należy wywołać `SetFieldDirty` i `SetFieldNull` samodzielnie.  
  
> [!NOTE]
>  Można kontrolować, czy dane są dwa razy buforowana domyślnie przez ustawienie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Uwagi  
 Danych jest mapowany między typem **DAO_R8** w DAO i wpisz **podwójne float** w zestawie rekordów.  
  
### <a name="example"></a>Przykład  
 Zobacz [dfx_text —](#dfx_text).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  

## <a name="dfx_long"></a>  Dfx_long —
Transfer danych długich liczb całkowitych między elementy członkowskie danych pola z [cdaorecordset —](cdaorecordset-class.md) obiektu i kolumny rekordu w źródle danych.  
  
### <a name="syntax"></a>Składnia  
  
```
void AFXAPI DFX_Long(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   long& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji.  
  
 `szName`  
 Nazwa kolumny danych.  
  
 *value*  
 Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu **długi**, pochodzi z elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.  
  
 `dwBindOptions`  
 Opcja, która umożliwia wykorzystanie mechanizmu MFC podwójnego buforowania wykrywania pól rekordów, które zostały zmienione. Wartość domyślna `AFX_DAO_ENABLE_FIELD_CACHE`, używa podwójnego buforowania. Możliwa wartość to `AFX_DAO_DISABLE_FIELD_CACHE`. Jeśli ta wartość jest określona, MFC nie bez sprawdzania dla tego pola. Należy wywołać `SetFieldDirty` i `SetFieldNull` samodzielnie.  
  
> [!NOTE]
>  Można kontrolować, czy dane są dwa razy buforowana domyślnie przez ustawienie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Uwagi  
 Danych jest mapowany między typem **DAO_I4** w DAO i wpisz **długi** w zestawie rekordów.  
  
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
 `pFX`  
 Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji.  
  
 `szName`  
 Nazwa kolumny danych.  
  
 *value*  
 Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu [clongbinary —](clongbinary-class.md), pochodzi z elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.  
  
 *dwPreAllocSize*  
 Platformę preallocates to ilość pamięci. Jeśli dane są większe, platformę zostaną przydzielone więcej miejsca, w razie potrzeby. Lepszą wydajność Ustaw ten rozmiar wystarczająco duży, aby zapobiec przeniesień wartość.  
  
 `dwBindOptions`  
 Opcja, która umożliwia wykorzystanie mechanizmu MFC podwójnego buforowania wykrywania pól rekordów, które zostały zmienione. Wartość domyślna **AFX_DISABLE_FIELD_CACHE**, nie używa podwójnego buforowania. Możliwa wartość to `AFX_DAO_ENABLE_FIELD_CACHE`. Używa podwójnego buforowania, na które ma wykonywać dodatkowe zadania do oznaczenia zmieniony, lub wartość Null. Względu na wydajność i pamięci należy unikać tej wartości, chyba, że dane binarne jest stosunkowo mały.  
  
> [!NOTE]
>  Można kontrolować, czy dane są dwa razy buforowana domyślnie przez ustawienie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Uwagi  
 `DFX_LongBinary` to zapewnia zgodność z klas MFC ODBC. `DFX_LongBinary` Funkcja przesyła dane binarne dużych obiektów (BLOB) za pomocą klasy `CLongBinary` między elementy członkowskie danych pola z [cdaorecordset —](cdaorecordset-class.md) obiektu i kolumny rekordu w źródle danych. Dane są zmapowane między typem **DAO_BYTES** w DAO i wpisz [clongbinary —](clongbinary-class.md) w zestawie rekordów.  
  
### <a name="example"></a>Przykład  
 Zobacz [dfx_text —](#dfx_text).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  

## <a name="dfx_short"></a>  Dfx_short —
Transfery krótka danych liczb całkowitych między elementy członkowskie danych pola z [cdaorecordset —](cdaorecordset-class.md) obiektu i kolumny rekordu w źródle danych.  
  
### <a name="syntax"></a>Składnia  
  
```
void AFXAPI DFX_Short(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   short& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji.  
  
 `szName`  
 Nazwa kolumny danych.  
  
 *value*  
 Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu **krótki**, pochodzi z elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.  
  
 `dwBindOptions`  
 Opcja, która umożliwia wykorzystanie mechanizmu MFC podwójnego buforowania wykrywania pól rekordów, które zostały zmienione. Wartość domyślna `AFX_DAO_ENABLE_FIELD_CACHE`, używa podwójnego buforowania. Możliwa wartość to `AFX_DAO_DISABLE_FIELD_CACHE`. Jeśli ta wartość jest określona, MFC nie bez sprawdzania dla tego pola. Należy wywołać `SetFieldDirty` i `SetFieldNull` samodzielnie.  
  
> [!NOTE]
>  Można kontrolować, czy dane są dwa razy buforowana domyślnie przez ustawienie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Uwagi  
 Danych jest mapowany między typem **DAO_I2** w DAO i wpisz **krótki** w zestawie rekordów.  
  
> [!NOTE]
>  `DFX_Short` jest odpowiednikiem [rfx_int —](#rfx_int) dla klasy oparte na ODBC.  
  
### <a name="example"></a>Przykład  
 Zobacz [dfx_text —](#dfx_text).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  
  

## <a name="dfx_single"></a>  Dfx_single —
Transfer danych zmiennoprzecinkowych między elementy członkowskie danych pola z [cdaorecordset —](cdaorecordset-class.md) obiektu i kolumny rekordu w źródle danych.  
  
### <a name="syntax"></a>Składnia  
  
```
void AFXAPI DFX_Single(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   float& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji.  
  
 `szName`  
 Nazwa kolumny danych.  
  
 *value*  
 Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu **float**, pochodzi z elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.  
  
 `dwBindOptions`  
 Opcja, która umożliwia wykorzystanie mechanizmu MFC podwójnego buforowania wykrywania pól rekordów, które zostały zmienione. Wartość domyślna `AFX_DAO_ENABLE_FIELD_CACHE`, używa podwójnego buforowania. Możliwa wartość to `AFX_DAO_DISABLE_FIELD_CACHE`. Jeśli ta wartość jest określona, MFC nie bez sprawdzania dla tego pola. Należy wywołać `SetFieldDirty` i `SetFieldNull` samodzielnie.  
  
> [!NOTE]
>  Można kontrolować, czy dane są dwa razy buforowana domyślnie przez ustawienie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Uwagi  
 Dane są zmapowane między typem **DAO_R4** w DAO i wpisz **float** w zestawie rekordów.  
  
### <a name="example"></a>Przykład  
 Zobacz [dfx_text —](#dfx_text).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  

## <a name="dfx_text"></a>  Dfx_text —
Transfery `CString` danych między elementy członkowskie danych pola z [cdaorecordset —](cdaorecordset-class.md) obiektu i kolumny rekordu w źródle danych.  
  
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
 `pFX`  
 Wskaźnik do obiektu klasy [CDaoFieldExchange](cdaofieldexchange-class.md). Ten obiekt zawiera informacje, aby zdefiniować kontekst dla każdego wywołania funkcji.  
  
 `szName`  
 Nazwa kolumny danych.  
  
 *value*  
 Wartość przechowywana w elemencie członkowskim danych wskazany — wartość do przeniesienia. W przypadku przeniesienia z zestawu rekordów do źródła danych, wartości typu [cstring —](../../atl-mfc-shared/reference/cstringt-class.md), pochodzi z elementu członkowskiego określone dane. W przypadku przeniesienia ze źródła danych do zestawu rekordów wartość jest przechowywana w elemencie członkowskim określone dane.  
  
 `nPreAllocSize`  
 Platformę preallocates to ilość pamięci. Jeśli dane są większe, platformę zostaną przydzielone więcej miejsca, w razie potrzeby. Lepszą wydajność Ustaw ten rozmiar wystarczająco duży, aby zapobiec przeniesień wartość.  
  
 `dwBindOptions`  
 Opcja, która umożliwia wykorzystanie mechanizmu MFC podwójnego buforowania wykrywania pól rekordów, które zostały zmienione. Wartość domyślna `AFX_DAO_ENABLE_FIELD_CACHE`, używa podwójnego buforowania. Możliwa wartość to `AFX_DAO_DISABLE_FIELD_CACHE`. Jeśli ta wartość jest określona, MFC nie bez sprawdzania dla tego pola. Należy wywołać [SetFieldDirty](cdaorecordset-class.md#setfielddirty) i [SetFieldNull](cdaorecordset-class.md#setfieldnull) samodzielnie.  
  
> [!NOTE]
>  Można kontrolować, czy dane są dwa razy buforowana domyślnie przez ustawienie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Uwagi  
 Danych jest mapowany między typem **DAO_CHAR** w DAO (lub, jeśli symbol **_unicode —** jest zdefiniowany, **DAO_WCHAR**) i typ [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) w zestaw rekordów.  n
  
### <a name="example"></a>Przykład  
 W tym przykładzie pokazano kilka wywołań `DFX_Text`. Zauważ również dwa wywołań [CDaoFieldExchange::SetFieldType](cdaofieldexchange-class.md#setfieldtype). Musi być zapisana w pierwszym wywołaniu `SetFieldType` i jego **DFX** wywołania. Drugie wywołanie i jego skojarzony **DFX** wywołania są zwykle zapisywane przez kreatora kodu, który wygenerował klasy.  
  
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
 [Makra i funkcje globalne](mfc-macros-and-globals.md)   
 [CRecordset::DoFieldExchange](crecordset-class.md#dofieldexchange)   
 [CRecordset::DoBulkFieldExchange](crecordset-class.md#dobulkfieldexchange)   
 [CDaoRecordset::DoFieldExchange](cdaorecordset-class.md#dofieldexchange)

