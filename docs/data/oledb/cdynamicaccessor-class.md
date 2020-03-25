---
title: CDynamicAccessor — Klasa
ms.date: 11/04/2016
f1_keywords:
- ATL.CDynamicAccessor
- ATL::CDynamicAccessor
- CDynamicAccessor
- ATL::CDynamicAccessor::AddBindEntry
- CDynamicAccessor.AddBindEntry
- CDynamicAccessor::AddBindEntry
- ATL.CDynamicAccessor.AddBindEntry
- CDynamicAccessor::CDynamicAccessor
- ATL::CDynamicAccessor::CDynamicAccessor
- ATL.CDynamicAccessor.CDynamicAccessor
- CDynamicAccessor.CDynamicAccessor
- ATL::CDynamicAccessor::Close
- ATL.CDynamicAccessor.Close
- CDynamicAccessor.Close
- CDynamicAccessor::Close
- ATL.CDynamicAccessor.GetBlobHandling
- CDynamicAccessor::GetBlobHandling
- ATL::CDynamicAccessor::GetBlobHandling
- GetBlobHandling
- CDynamicAccessor.GetBlobHandling
- ATL::CDynamicAccessor::GetBlobSizeLimit
- CDynamicAccessor.GetBlobSizeLimit
- CDynamicAccessor::GetBlobSizeLimit
- GetBlobSizeLimit
- ATL.CDynamicAccessor.GetBlobSizeLimit
- CDynamicAccessor.GetBookmark
- GetBookmark
- CDynamicAccessor::GetBookmark
- ATL.CDynamicAccessor.GetBookmark
- ATL::CDynamicAccessor::GetBookmark
- ATL.CDynamicAccessor.GetColumnCount
- ATL::CDynamicAccessor::GetColumnCount
- CDynamicAccessor::GetColumnCount
- CDynamicAccessor.GetColumnCount
- GetColumnCount
- CDynamicAccessor.GetColumnFlags
- ATL::CDynamicAccessor::GetColumnFlags
- ATL.CDynamicAccessor.GetColumnFlags
- CDynamicAccessor::GetColumnFlags
- ATL.CDynamicAccessor.GetColumnInfo
- ATL::CDynamicAccessor::GetColumnInfo
- CDynamicAccessor.GetColumnInfo
- CDynamicAccessor::GetColumnInfo
- ATL::CDynamicAccessor::GetColumnName
- GetColumnName
- ATL.CDynamicAccessor.GetColumnName
- CDynamicAccessor::GetColumnName
- CDynamicAccessor.GetColumnName
- ATL.CDynamicAccessor.GetColumnType
- CDynamicAccessor::GetColumnType
- GetColumnType
- CDynamicAccessor.GetColumnType
- ATL::CDynamicAccessor::GetColumnType
- CDynamicAccessor.GetLength
- ATL.CDynamicAccessor.GetLength
- CDynamicAccessor::GetLength
- ATL::CDynamicAccessor::GetLength
- CDynamicAccessor.GetOrdinal
- ATL::CDynamicAccessor::GetOrdinal
- CDynamicAccessor::GetOrdinal
- ATL.CDynamicAccessor.GetOrdinal
- GetOrdinal
- ATL::CDynamicAccessor::GetStatus
- CDynamicAccessor.GetStatus
- ATL.CDynamicAccessor.GetStatus
- CDynamicAccessor::GetStatus
- GetValue
- CDynamicAccessor::GetValue<ctype>
- ATL.CDynamicAccessor.GetValue<ctype>
- CDynamicAccessor.GetValue
- CDynamicAccessor::GetValue
- ATL.CDynamicAccessor.GetValue
- ATL::CDynamicAccessor::GetValue
- ATL::CDynamicAccessor::GetValue<ctype>
- CDynamicAccessor::SetBlobHandling
- CDynamicAccessor.SetBlobHandling
- ATL::CDynamicAccessor::SetBlobHandling
- SetBlobHandling
- ATL.CDynamicAccessor.SetBlobHandling
- CDynamicAccessor::SetBlobSizeLimit
- SetBlobSizeLimit
- CDynamicAccessor.SetBlobSizeLimit
- ATL.CDynamicAccessor.SetBlobSizeLimit
- ATL::CDynamicAccessor::SetBlobSizeLimit
- ATL::CDynamicAccessor::SetLength
- CDynamicAccessor.SetLength
- CDynamicAccessor::SetLength
- ATL.CDynamicAccessor.SetLength
- CDynamicAccessor::SetStatus
- ATL::CDynamicAccessor::SetStatus
- CDynamicAccessor.SetStatus
- ATL.CDynamicAccessor.SetStatus
- ATL.CDynamicAccessor.SetValue
- ATL::CDynamicAccessor::SetValue
- ATL::CDynamicAccessor::SetValue<ctype>
- CDynamicAccessor.SetValue
- ATL.CDynamicAccessor.SetValue<ctype>
- CDynamicAccessor::SetValue
- CDynamicAccessor::SetValue<ctype>
helpviewer_keywords:
- CDynamicAccessor class
- AddBindEntry method
- CDynamicAccessor class, constructor
- Close method
- GetBlobHandling method
- GetBlobSizeLimit method
- GetBookmark method
- GetColumnCount method
- GetColumnFlags method
- GetColumnInfo method
- GetColumnName method
- GetColumnType method
- GetLength method
- GetOrdinal method
- GetStatus method
- GetValue method
- SetBlobHandling method
- SetBlobSizeLimit method
- SetLength method
- SetStatus method
- SetValue method
ms.assetid: 374b13b7-1f09-457d-9e6b-df260ff4d178
ms.openlocfilehash: 160e5b6d8eb4b45850dc071299413d9ad2cfcee9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212068"
---
# <a name="cdynamicaccessor-class"></a>CDynamicAccessor — Klasa

Pozwala uzyskać dostęp do źródła danych, gdy nie ma informacji o schemacie bazy danych (źródłowa struktura bazy danych).

## <a name="syntax"></a>Składnia

```cpp
class CDynamicAccessor : public CAccessorBase
```

## <a name="requirements"></a>Wymagania

**Nagłówek**: atldbcli. h

## <a name="members"></a>Members

### <a name="methods"></a>Metody

|||
|-|-|
|[AddBindEntry](#addbindentry)|Dodaje wpis powiązania do kolumn wyjściowych podczas zastępowania domyślnego akcesora.|
|[CDynamicAccessor](#cdynamicaccessor)|Tworzy wystąpienia i inicjuje obiekt `CDynamicAccessor`.|
|[Ściśle](#close)|Cofa powiązania wszystkich kolumn, zwalnia przydzieloną pamięć i zwalnia wskaźnik interfejsu [IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85)) w klasie.|
|[GetBlobHandling](#getblobhandling)|Pobiera wartość obsługi obiektu BLOB dla bieżącego wiersza.|
|[GetBlobSizeLimit](#getblobsizelimit)|Pobiera maksymalny rozmiar obiektu BLOB w bajtach.|
|[GetBookmark](#getbookmark)|Pobiera zakładkę dla bieżącego wiersza.|
|[GetColumnCount](#getcolumncount)|Pobiera liczbę kolumn w zestawie wierszy.|
|[GetColumnFlags](#getcolumnflags)|Pobiera charakterystyki kolumny.|
|[GetColumnInfo](#getcolumninfo)|Pobiera metadane kolumny.|
|[Getcolumnname](#getcolumnname)|Pobiera nazwę określonej kolumny.|
|[GetColumnType](#getcolumntype)|Pobiera typ danych określonej kolumny.|
|[GetLength —](#getlength)|Pobiera maksymalną możliwą długość kolumny w bajtach.|
|[GetOrdinal](#getordinal)|Pobiera indeks kolumny przy użyciu nazwy kolumny.|
|[GetStatus](#getstatus)|Pobiera stan określonej kolumny.|
|[GetValue](#getvalue)|Pobiera dane z buforu.|
|[SetBlobHandling](#setblobhandling)|Ustawia wartość obsługi obiektów BLOB dla bieżącego wiersza.|
|[SetBlobSizeLimit](#setblobsizelimit)|Ustawia maksymalny rozmiar obiektu BLOB w bajtach.|
|[SetLength](#setlength)|Ustawia długość kolumny w bajtach.|
|[SetStatus](#setstatus)|Ustawia stan określonej kolumny.|
|[SetValue](#setvalue)|Przechowuje dane w buforze.|

## <a name="remarks"></a>Uwagi

Użyj metod `CDynamicAccessor`, aby uzyskać informacje o kolumnach, takie jak nazwy kolumn, liczba kolumn, typ danych i tak dalej. Następnie za pomocą tych informacji można utworzyć metodę dostępu dynamicznie w czasie wykonywania.

Informacje o kolumnie są przechowywane w buforze, który jest tworzony i zarządzany przez tę klasę. Pobierz dane z buforu przy użyciu [GetValue](../../data/oledb/cdynamicaccessor-getvalue.md).

Aby zapoznać się z omówieniem i przykładami dotyczącymi korzystania z klas akcesorów dynamicznych, zobacz [Używanie dynamicznych metod dostępu](../../data/oledb/using-dynamic-accessors.md).

## <a name="cdynamicaccessoraddbindentry"></a><a name="addbindentry"></a>CDynamicAccessor:: AddBindEntry

Dodaje wpis powiązania do kolumn danych wyjściowych.

### <a name="syntax"></a>Składnia

```cpp
HRESULT AddBindEntry(const DBCOLUMNINFO& info) throw();
```

#### <a name="parameters"></a>Parametry

*informacje*<br/>
podczas Struktura `DBCOLUMNINFO` zawierająca informacje o kolumnie. Zobacz "struktury DBCOLUMNINFO" w [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) w *dokumentacji programisty OLE DB*.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Użyj tej metody podczas zastępowania domyślnego akcesora utworzonego za pomocą `CDynamicAccessor` (zobacz [jak pobrać dane?](../../data/oledb/fetching-data.md)).

## <a name="cdynamicaccessorcdynamicaccessor"></a><a name="cdynamicaccessor"></a>CDynamicAccessor:: CDynamicAccessor

Tworzy wystąpienia i inicjuje obiekt `CDynamicAccessor`.

### <a name="syntax"></a>Składnia

```cpp
CDynamicAccessor(DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,
   DBLENGTH nBlobSize = 8000);
```

#### <a name="parameters"></a>Parametry

*eBlobHandling*<br/>
Określa, jak mają być obsługiwane dane binarne obiektów binarnych (BLOB). Wartość domyślna to DBBLOBHANDLING_DEFAULT. Zobacz [SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) , aby uzyskać opis wartości DBBLOBHANDLINGENUM.

*nBlobSize*<br/>
Maksymalny rozmiar obiektu BLOB w bajtach; dane kolumny za tą wartością są traktowane jako obiekty BLOB. Wartość domyślna to 8 000. Aby uzyskać szczegółowe informacje, zobacz [SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) .

### <a name="remarks"></a>Uwagi

Jeśli używasz konstruktora do zainicjowania obiektu `CDynamicAccessor`, możesz określić sposób powiązania obiektów BLOB. Obiekty blob mogą zawierać dane binarne, takie jak grafika, dźwięk lub skompilowany kod. Domyślnym zachowaniem jest traktowanie kolumn o więcej niż 8 000 bajtów jako obiektów blob i próba powiązania ich z obiektem `ISequentialStream`. Można jednak określić inną wartość jako rozmiar obiektu BLOB.

Możesz również określić sposób, w jaki `CDynamicAccessor` obsługuje dane kolumn, które są zgodne z danymi obiektów BLOB: może obsługiwać dane obiektów BLOB w sposób domyślny; może pomijać (nie tworzy powiązań) dane obiektów BLOB; może również powiązać dane obiektów BLOB w pamięci przydzieloną przez dostawcę.

## <a name="cdynamicaccessorclose"></a><a name="close"></a>CDynamicAccessor:: Close

Cofa powiązania wszystkich kolumn, zwalnia przydzieloną pamięć i zwalnia wskaźnik interfejsu [IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85)) w klasie.

### <a name="syntax"></a>Składnia

```cpp
void Close() throw();
```

## <a name="cdynamicaccessorgetblobhandling"></a><a name="getblobhandling"></a>CDynamicAccessor:: GetBlobHandling

Pobiera wartość obsługi obiektu BLOB dla bieżącego wiersza.

### <a name="syntax"></a>Składnia

```cpp
const DBBLOBHANDLINGENUM GetBlobHandling() const;
```

### <a name="remarks"></a>Uwagi

Zwraca wartość obsługi obiektu BLOB *eBlobHandling* jako ustawioną przez [SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md).

## <a name="cdynamicaccessorgetblobsizelimit"></a><a name="getblobsizelimit"></a>CDynamicAccessor:: GetBlobSizeLimit

Pobiera maksymalny rozmiar obiektu BLOB w bajtach.

### <a name="syntax"></a>Składnia

```cpp
const DBLENGTH GetBlobSizeLimit() const;
```

### <a name="remarks"></a>Uwagi

Zwraca wartość obsługi obiektu BLOB *nBlobSize* jako ustawioną przez [SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md).

## <a name="cdynamicaccessorgetbookmark"></a><a name="getbookmark"></a>CDynamicAccessor:: GetBookmark

Pobiera zakładkę dla bieżącego wiersza.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetBookmark(CBookmark< >* pBookmark) const throw();
```

#### <a name="parameters"></a>Parametry

*pBookmark*<br/>
określoną Wskaźnik do obiektu [CBookmark](../../data/oledb/cbookmark-class.md) .

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Aby można było pobrać zakładkę, należy ustawić `DBPROP_IRowsetLocate` VARIANT_TRUE.

## <a name="cdynamicaccessorgetcolumncount"></a><a name="getcolumncount"></a>CDynamicAccessor:: GetColumnCount

Pobiera liczbę kolumn.

### <a name="syntax"></a>Składnia

```cpp
DBORDINAL GetColumnCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Liczba pobranych kolumn.

## <a name="cdynamicaccessorgetcolumnflags"></a><a name="getcolumnflags"></a>CDynamicAccessor:: GetColumnFlags

Pobiera charakterystyki kolumny.

### <a name="syntax"></a>Składnia

```cpp
bool GetColumnFlags(DBORDINAL nColumn,
   DBCOLUMNFLAGS* pFlags) const throw();
```

#### <a name="parameters"></a>Parametry

*nColumn*<br/>
podczas Numer kolumny. Numery kolumn zaczynają się od 1. Wartość 0 oznacza kolumnę zakładki (jeśli istnieje).

*pFlags*<br/>
określoną Wskaźnik do maski bitowej, który opisuje charakterystykę kolumny. Zobacz "DBCOLUMNFLAGS typ wyliczeniowy" w [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) w *odwołaniu programisty OLE DB*.

### <a name="return-value"></a>Wartość zwracana

Zwraca **wartość true** , jeśli Charakterystyka kolumny została pobrana pomyślnie. W przeciwnym razie zwraca **wartość false**.

### <a name="remarks"></a>Uwagi

Numer kolumny jest przesunięty od jednego. Kolumna zero jest szczególnym przypadkiem; jest to zakładka, jeśli jest dostępna.

## <a name="cdynamicaccessorgetcolumninfo"></a><a name="getcolumninfo"></a>CDynamicAccessor:: GetColumnInfo

Zwraca metadane kolumny, które są zbędne przez większość użytkowników.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetColumnInfo(IRowset* pRowset,
   DBORDINAL* pColumns,
   DBCOLUMNINFO** ppColumnInfo,
   OLECHAR** ppStringsBuffer) throw();
```

#### <a name="parameters"></a>Parametry

*pRowset*<br/>
podczas Wskaźnik do interfejsu [IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85)) .

*pColumns*<br/>
określoną Wskaźnik do pamięci, w której ma zostać zwrócona liczba kolumn w zestawie wierszy; Ta liczba zawiera kolumnę zakładka (jeśli istnieje).

*ppColumnInfo*<br/>
określoną Wskaźnik do pamięci, w której ma zostać zwrócona tablica struktur `DBCOLUMNINFO`. Zobacz "struktury DBCOLUMNINFO" w [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) w *dokumentacji programisty OLE DB*.

*ppStringsBuffer*<br/>
określoną Wskaźnik do pamięci, w której ma zostać zwrócony wskaźnik do magazynu dla wszystkich wartości ciągu (nazw używanych w ramach *ColumnID* lub dla *pwszName*) w ramach pojedynczego bloku alokacji.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Aby uzyskać informacje na temat typów danych `DBORDINAL`, `DBCOLUMNINFO`i `OLECHAR`, zobacz [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) w *dokumentacji programisty OLE DB* .

## <a name="cdynamicaccessorgetcolumnname"></a><a name="getcolumnname"></a>CDynamicAccessor:: getcolumnname

Pobiera nazwę podanej kolumny.

### <a name="syntax"></a>Składnia

```cpp
LPOLESTR GetColumnName(DBORDINAL nColumn) const throw();
```

#### <a name="parameters"></a>Parametry

*nColumn*<br/>
podczas Numer kolumny. Numery kolumn zaczynają się od 1. Wartość 0 oznacza kolumnę zakładki (jeśli istnieje).

### <a name="return-value"></a>Wartość zwracana

Nazwa określonej kolumny.

## <a name="cdynamicaccessorgetcolumntype"></a><a name="getcolumntype"></a>CDynamicAccessor:: GetColumnType

Pobiera typ danych określonej kolumny.

### <a name="syntax"></a>Składnia

```cpp
bool GetColumnType(DBORDINAL nColumn,
   DBTYPE* pType) const throw();
```

#### <a name="parameters"></a>Parametry

*nColumn*<br/>
podczas Numer kolumny. Numery kolumn zaczynają się od 1. Wartość 0 oznacza kolumnę zakładki (jeśli istnieje).

*pType*<br/>
określoną Wskaźnik do typu danych w określonej kolumnie.

### <a name="return-value"></a>Wartość zwracana

Zwraca **wartość true** dla sukcesu lub **false** w przypadku niepowodzenia.

## <a name="cdynamicaccessorgetlength"></a><a name="getlength"></a>CDynamicAccessor:: GetLength

Pobiera długość określonej kolumny.

### <a name="syntax"></a>Składnia

```cpp
bool GetLength(DBORDINAL nColumn,
   DBLENGTH* pLength) const throw();

bool GetLength(const CHAR* pColumnName,
   DBLENGTH* pLength) const throw();

bool GetLength(const WCHAR* pColumnName,
   DBLENGTH* pLength) const throw();
```

#### <a name="parameters"></a>Parametry

*nColumn*<br/>
podczas Numer kolumny. Numery kolumn zaczynają się od 1. Wartość 0 oznacza kolumnę zakładki (jeśli istnieje).

*pColumnName*<br/>
podczas Wskaźnik do ciągu znaków zawierającego nazwę kolumny.

*pLength*<br/>
określoną Wskaźnik do liczby całkowitej zawierającej długość kolumny w bajtach.

### <a name="return-value"></a>Wartość zwracana

Zwraca **wartość PRAWDA** , jeśli określona kolumna zostanie znaleziona. W przeciwnym razie ta funkcja zwraca **wartość false**.

### <a name="remarks"></a>Uwagi

Pierwsze zastąpienie przyjmuje numer kolumny, a drugi i trzeci przesłonięcia przyjmują odpowiednio nazwę kolumny w formacie ANSI lub Unicode.

## <a name="cdynamicaccessorgetordinal"></a><a name="getordinal"></a>CDynamicAccessor:: GetOrdinal

Pobiera numer kolumny z podaną nazwą kolumny.

### <a name="syntax"></a>Składnia

```cpp
bool GetOrdinal(const CHAR* pColumnName,
   DBORDINAL* pOrdinal) const throw();

bool GetOrdinal(const WCHAR* pColumnName,
   DBORDINAL* pOrdinal) const throw();
```

#### <a name="parameters"></a>Parametry

*pColumnName*<br/>
podczas Wskaźnik do ciągu znaków zawierającego nazwę kolumny.

*pOrdinal*<br/>
określoną Wskaźnik do numeru kolumny.

### <a name="return-value"></a>Wartość zwracana

Zwraca **wartość true** , jeśli zostanie znaleziona kolumna o określonej nazwie. W przeciwnym razie ta funkcja zwraca **wartość false**.

## <a name="cdynamicaccessorgetstatus"></a><a name="getstatus"></a>CDynamicAccessor:: GetStatus

Pobiera stan określonej kolumny.

### <a name="syntax"></a>Składnia

```cpp
bool GetStatus(DBORDINAL nColumn,
   DBSTATUS* pStatus) const throw();

bool GetStatus(const CHAR* pColumnName,
   DBSTATUS* pStatus) const throw();

bool GetStatus(const WCHAR* pColumnName,
   DBSTATUS* pStatus) const throw();
```

#### <a name="parameters"></a>Parametry

*nColumn*<br/>
podczas Numer kolumny. Numery kolumn zaczynają się od 1. Wartość 0 oznacza kolumnę zakładki (jeśli istnieje).

*pColumnName*<br/>
podczas Wskaźnik do ciągu znaków zawierającego nazwę kolumny.

*pStatus*<br/>
określoną Wskaźnik do zmiennej zawierającej stan kolumny. Aby uzyskać więcej informacji, zobacz [DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) w *dokumentacji programisty OLE DB* .

### <a name="return-value"></a>Wartość zwracana

Zwraca **wartość PRAWDA** , jeśli określona kolumna zostanie znaleziona. W przeciwnym razie ta funkcja zwraca **wartość false**.

## <a name="cdynamicaccessorgetvalue"></a><a name="getvalue"></a>CDynamicAccessor:: GetValue

Pobiera dane dla określonej kolumny.

### <a name="syntax"></a>Składnia

```cpp
void* GetValue(DBORDINAL nColumn) const throw();

void* GetValue(const CHAR* pColumnName) const throw();

void* GetValue(const WCHAR* pColumnName) const throw();

template < class ctype >
bool GetValue(DBORDINAL nColumn, ctype* pData) const throw();

template < class ctype >
bool GetValue(const CHAR* pColumnName, ctype* pData) const throw();

template < class ctype >
bool GetValue(const WCHAR* pColumnName, ctype* pData) const throw();
```

#### <a name="parameters"></a>Parametry

*CType*<br/>
podczas Parametr z szablonami obsługujący dowolny typ danych z wyjątkiem typów ciągów (`CHAR*`, `WCHAR*`), które wymagają specjalnej obsługi. `GetValue` używa odpowiedniego typu danych na podstawie tego, co jest określone w tym miejscu.

*nColumn*<br/>
podczas Numer kolumny. Numery kolumn zaczynają się od 1. Wartość 0 oznacza kolumnę zakładki (jeśli istnieje).

*pColumnName*<br/>
podczas Nazwa kolumny.

*pData*<br/>
określoną Wskaźnik do zawartości określonej kolumny.

### <a name="return-value"></a>Wartość zwracana

Jeśli chcesz przekazać dane ciągu, użyj nieszablonowych wersji `GetValue`. Nieszablonowe wersje tej metody zwracają `void*`, które wskazują część buforu, która zawiera dane określonego kolumny. Zwraca wartość NULL, jeśli nie można odnaleźć kolumny.

W przypadku wszystkich innych typów danych łatwiej jest używać szablonów `GetValue`. Wersje z szablonami zwracają **wartość true** dla sukcesu lub **false** w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Użyj wersji nienależących do szablonu, aby zwrócić kolumny zawierające ciągi i wersje z szablonami dla kolumn, które zawierają inne typy danych.

W trybie debugowania otrzymasz potwierdzenie, jeśli rozmiar *pData* jest nierówny rozmiarowi kolumny, do której wskazuje.

## <a name="cdynamicaccessorsetblobhandling"></a><a name="setblobhandling"></a>CDynamicAccessor:: SetBlobHandling

Ustawia wartość obsługi obiektów BLOB dla bieżącego wiersza.

### <a name="syntax"></a>Składnia

```cpp
bool SetBlobHandling(DBBLOBHANDLINGENUM eBlobHandling);
```

#### <a name="parameters"></a>Parametry

*eBlobHandling*<br/>
Określa, w jaki sposób dane obiektów BLOB mają być obsługiwane. Może przyjmować następujące wartości:

- DBBLOBHANDLING_DEFAULT: Obsługuj dane kolumn, które są większe niż *nBlobSize* (zgodnie z zestawem `SetBlobSizeLimit`) jako dane obiektów blob i pobierając je za pomocą `ISequentialStream` lub `IStream` obiektu. Ta opcja spowoduje podjęcie próby powiązania każdej kolumny zawierającej dane większe niż *nBlobSize* lub wymienione jako DBTYPE_IUNKNOWN jako dane obiektów BLOB.

- DBBLOBHANDLING_NOSTREAMS: Obsługuj dane kolumn, które są większe niż *nBlobSize* (zgodnie z zestawem `SetBlobSizeLimit`) jako dane obiektów blob i pobieraj je za pomocą odwołania w przydzielonej przez dostawcę pamięci należącej do konsumenta. Ta opcja jest przydatna w przypadku tabel, które mają więcej niż jedną kolumnę obiektu BLOB, a dostawca obsługuje tylko jeden `ISequentialStream` obiektu na metodę dostępu.

- DBBLOBHANDLING_SKIP: kolumny Skip (nie Powiąż) kwalifikujące się jako zawierające obiekty blob (metoda dostępu nie będzie powiązać ani nie pobiera wartości kolumny, ale nadal będzie pobierać stan i długość kolumny).

### <a name="remarks"></a>Uwagi

Przed wywołaniem `Open`należy wywołać `SetBlobHandling`.

Metoda konstruktora [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) ustawia wartość obsługi obiektów BLOB na DBBLOBHANDLING_DEFAULT.

## <a name="cdynamicaccessorsetblobsizelimit"></a><a name="setblobsizelimit"></a>CDynamicAccessor:: SetBlobSizeLimit

Ustawia maksymalny rozmiar obiektu BLOB w bajtach.

### <a name="syntax"></a>Składnia

```cpp
void SetBlobSizeLimit(DBLENGTH nBlobSize);
```

#### <a name="parameters"></a>Parametry

*nBlobSize*<br/>
Określa limit rozmiaru obiektu BLOB.

### <a name="remarks"></a>Uwagi

Ustawia maksymalny rozmiar obiektu BLOB w bajtach; dane kolumny większe niż ta wartość są traktowane jako obiekty BLOB. Niektórzy dostawcy zapewniają bardzo duże rozmiary kolumn (takich jak 2 GB). Zamiast podejmować próby przydzielenia pamięci dla kolumny o tym rozmiarze, zazwyczaj spróbuj powiązać te kolumny jako obiekty blob. W ten sposób nie musisz przydzielić całej pamięci, ale nadal możesz odczytywać wszystkie dane bez obaw o obcinanie. Istnieją jednak sytuacje, w których warto wymusić, aby `CDynamicAccessor` powiązać duże kolumny w ich natywnych typach danych. Aby to zrobić, wywołaj `SetBlobSizeLimit` przed wywołaniem `Open`.

Metoda konstruktora [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) ustawia maksymalny rozmiar obiektu BLOB na wartość domyślną 8 000 bajtów.

## <a name="cdynamicaccessorsetlength"></a><a name="setlength"></a>CDynamicAccessor:: SetLength

Ustawia długość określonej kolumny.

### <a name="syntax"></a>Składnia

```cpp
bool SetLength(DBORDINAL nColumn,
   DBLENGTH nLength)throw();

bool SetLength(const CHAR* pColumnName,
   DBLENGTH nLength) throw();

bool SetLength(const WCHAR* pColumnName,
   DBLENGTH nLength) throw();
```

#### <a name="parameters"></a>Parametry

*nColumn*<br/>
podczas Numer kolumny. Numery kolumn zaczynają się od 1. Wartość 0 oznacza kolumnę zakładki (jeśli istnieje).

*nLength*<br/>
podczas Długość kolumny w bajtach.

*pColumnName*<br/>
podczas Wskaźnik do ciągu znaków zawierającego nazwę kolumny.

### <a name="return-value"></a>Wartość zwracana

Zwraca **wartość true** , jeśli określona długość kolumny została ustawiona pomyślnie. W przeciwnym razie ta funkcja zwraca **wartość false**.

## <a name="cdynamicaccessorsetstatus"></a><a name="setstatus"></a>CDynamicAccessor:: SetStatus

Ustawia stan określonej kolumny.

### <a name="syntax"></a>Składnia

```cpp
bool SetStatus(DBORDINAL nColumn,
   DBSTATUS status)throw();

bool SetStatus(const CHAR* pColumnName,
   DBSTATUS status) throw();

bool SetStatus(const WCHAR* pColumnName,
   DBSTATUS status) throw();
```

#### <a name="parameters"></a>Parametry

*nColumn*<br/>
podczas Numer kolumny. Numery kolumn zaczynają się od 1. Wartość 0 oznacza kolumnę zakładki (jeśli istnieje).

*Stany*<br/>
podczas Stan kolumny. Aby uzyskać więcej informacji, zobacz [DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) w *dokumentacji programisty OLE DB* .

*pColumnName*<br/>
podczas Wskaźnik do ciągu znaków zawierającego nazwę kolumny.

### <a name="return-value"></a>Wartość zwracana

Zwraca **wartość PRAWDA** , jeśli określona kolumna stanu jest ustawiona pomyślnie. W przeciwnym razie ta funkcja zwraca **wartość false**.

## <a name="cdynamicaccessorsetvalue"></a><a name="setvalue"></a>CDynamicAccessor:: SetValue

Przechowuje dane w określonej kolumnie.

### <a name="syntax"></a>Składnia

```cpp
template <class ctype>
bool SetValue(
   DBORDINAL nColumn,
   constctype& data) throw( );

template <class ctype>
bool SetValue(
   const CHAR * pColumnName,
   const ctype& data) throw( );

template <class ctype>
bool SetValue(
   const WCHAR *pColumnName,
   const ctype& data) throw( );
```

#### <a name="parameters"></a>Parametry

*CType*<br/>
podczas Parametr z szablonami obsługujący dowolny typ danych z wyjątkiem typów ciągów (`CHAR*`, `WCHAR*`), które wymagają specjalnej obsługi. `GetValue` używa odpowiedniego typu danych na podstawie tego, co jest określone w tym miejscu.

*pColumnName*<br/>
podczas Wskaźnik do ciągu znaków zawierającego nazwę kolumny.

*Data*<br/>
podczas Wskaźnik do pamięci zawierającej dane.

*nColumn*<br/>
podczas Numer kolumny. Numery kolumn zaczynają się od 1. Wartość 0 oznacza kolumnę zakładki (jeśli istnieje).

### <a name="return-value"></a>Wartość zwracana

Jeśli chcesz ustawić dane ciągu, użyj nieszablonowych wersji `GetValue`. Nieszablonowe wersje tej metody zwracają `void*`, które wskazują część buforu, która zawiera dane określonego kolumny. Zwraca wartość NULL, jeśli nie można odnaleźć kolumny.

W przypadku wszystkich innych typów danych łatwiej jest używać szablonów `GetValue`. Wersje z szablonami zwracają **wartość true** dla sukcesu lub **false** w przypadku niepowodzenia.

## <a name="see-also"></a>Zobacz też

[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor, klasa](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor, klasa](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor, klasa](../../data/oledb/cmanualaccessor-class.md)
