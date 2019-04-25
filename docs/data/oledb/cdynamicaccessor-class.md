---
title: CDynamicAccessor — Klasa
ms.date: 11/04/2016
f1_keywords:
- ATL.CDynamicAccessor
- ATL::CDynamicAccessor
- CDynamicAccessor
- ATL::CDynamicAccessor::AddBindEntry
- AddBindEntry
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
- GetColumnFlags
- GetColumnInfo
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
ms.openlocfilehash: 19b8d0c86044e04cc60fd7aab89ec828c46f5fb9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209302"
---
# <a name="cdynamicaccessor-class"></a>CDynamicAccessor — Klasa

Umożliwia dostęp do źródła danych, gdy masz nie znajomości schematu bazy danych (wewnętrzna struktura bazy danych).

## <a name="syntax"></a>Składnia

```cpp
class CDynamicAccessor : public CAccessorBase
```

## <a name="requirements"></a>Wymagania

**Nagłówek**: atldbcli.h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[AddBindEntry](#addbindentry)|Dodaje wpis powiązanie kolumn danych wyjściowych, podczas zastępowania domyślną metodę dostępu.|
|[CDynamicAccessor](#cdynamicaccessor)|Tworzy i inicjuje `CDynamicAccessor` obiektu.|
|[Zamknij](#close)|Rozpina wszystkie kolumny, zwalnia ilość przydzielonej pamięci i zwalnia [IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85)) wskaźnik interfejsu w klasie.|
|[GetBlobHandling](#getblobhandling)|Pobiera obiekt BLOB, Obsługa wartości bieżącego wiersza.|
|[GetBlobSizeLimit](#getblobsizelimit)|Pobiera maksymalny rozmiar obiektu BLOB w bajtach.|
|[GetBookmark](#getbookmark)|Pobiera zakładki dla bieżącego wiersza.|
|[GetColumnCount](#getcolumncount)|Pobiera liczbę kolumn w zestawie wierszy.|
|[GetColumnFlags](#getcolumnflags)|Pobiera właściwości kolumny.|
|[GetColumnInfo](#getcolumninfo)|Pobiera metadane kolumn.|
|[GetColumnName](#getcolumnname)|Pobiera nazwę określonej kolumny.|
|[GetColumnType](#getcolumntype)|Pobiera typ danych w określonej kolumnie.|
|[GetLength](#getlength)|Pobiera maksymalna możliwa długość kolumny w bajtach.|
|[GetOrdinal](#getordinal)|Pobiera indeks kolumny otrzymuje nazwę kolumny.|
|[GetStatus](#getstatus)|Pobiera stan określonej kolumny.|
|[GetValue](#getvalue)|Pobiera dane z buforu.|
|[SetBlobHandling](#setblobhandling)|Ustawia obiekt BLOB, Obsługa wartości bieżącego wiersza.|
|[SetBlobSizeLimit](#setblobsizelimit)|Ustawia maksymalny rozmiar obiektu BLOB w bajtach.|
|[SetLength](#setlength)|Ustawia długość kolumny, w bajtach.|
|[SetStatus —](#setstatus)|Ustawia stan określonej kolumny.|
|[SetValue](#setvalue)|Przechowuje dane w buforze.|

## <a name="remarks"></a>Uwagi

Użyj `CDynamicAccessor` metody, aby uzyskać informacje o kolumnach, takich jak nazwy kolumn, liczba kolumn, typ danych i tak dalej. Informacje o kolumnie jest następnie użyć do tworzenia metody dostępu dynamicznie w czasie wykonywania.

Informacje o kolumnach są przechowywane w buforu, który jest tworzony i zarządzany przez tę klasę. Uzyskiwanie danych z bufora przy użyciu [GetValue](../../data/oledb/cdynamicaccessor-getvalue.md).

Dyskusję na temat i przykłady użycia klas dynamicznej metody dostępu, zobacz [przy użyciu dynamicznych metod dostępu](../../data/oledb/using-dynamic-accessors.md).

## <a name="addbindentry"></a> CDynamicAccessor::AddBindEntry

Dodaje wpis powiązanie kolumn danych wyjściowych.

### <a name="syntax"></a>Składnia

```cpp
HRESULT AddBindEntry(const DBCOLUMNINFO& info) throw();
```

#### <a name="parameters"></a>Parametry

*info*<br/>
[in] A `DBCOLUMNINFO` struktury zawierającej informacje o kolumnach. Zobacz sekcję "DBCOLUMNINFO struktury" w [IColumnsInfo::GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) w *OLE DB Podręcznik programisty*.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

Użyj tej metody, podczas zastępowania domyślną metodę dostępu, utworzony za pomocą `CDynamicAccessor` (zobacz [jak mogę pobrać dane?](../../data/oledb/fetching-data.md)).

## <a name="cdynamicaccessor"></a> CDynamicAccessor::CDynamicAccessor

Tworzy i inicjuje `CDynamicAccessor` obiektu.

### <a name="syntax"></a>Składnia

```cpp
CDynamicAccessor(DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,
   DBLENGTH nBlobSize = 8000);
```

#### <a name="parameters"></a>Parametry

*eBlobHandling*<br/>
Określa, jak dane dużych obiektów binarnych (BLOB) ma być obsługiwane. Wartość domyślna to DBBLOBHANDLING_DEFAULT. Zobacz [setblobhandling —](../../data/oledb/cdynamicaccessor-setblobhandling.md) opis wartości DBBLOBHANDLINGENUM.

*nBlobSize*<br/>
Maksymalny rozmiar obiektu BLOB w bajtach; kolumny danych za pośrednictwem ta wartość jest traktowana jako obiekt BLOB. Wartość domyślna to 8000. Zobacz [setblobsizelimit —](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) Aby uzyskać szczegółowe informacje.

### <a name="remarks"></a>Uwagi

Jeśli używasz konstruktora do zainicjowania `CDynamicAccessor` obiektu, można określić, jak powiązać obiekty BLOB. Obiekty BLOB może zawierać danych binarnych, takich jak grafiki, dźwięku lub skompilowanego kodu. Domyślnym zachowaniem jest traktowanie kolumn ponad 8000 bajtów jako obiekty BLOB, a następnie próbujesz powiązać je z `ISequentialStream` obiektu. Można jednak określić inną wartość na rozmiar obiektu BLOB.

Można również określić, jak `CDynamicAccessor` służy do obsługi danych kolumny, która zaliczamy do danych obiektów BLOB: danych obiektów BLOB w sposób domyślne może obsługiwać; można pominąć (nie jest powiązana) danych obiektów BLOB; lub jest on można powiązać danych obiektów BLOB w pamięci przydzielonej przez dostawcę.

## <a name="close"></a> CDynamicAccessor::Close

Rozpina wszystkie kolumny, zwalnia ilość przydzielonej pamięci i zwalnia [IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85)) wskaźnik interfejsu w klasie.

### <a name="syntax"></a>Składnia

```cpp
void Close() throw();
```

## <a name="getblobhandling"></a> CDynamicAccessor::GetBlobHandling

Pobiera obiekt BLOB, Obsługa wartości bieżącego wiersza.

### <a name="syntax"></a>Składnia

```cpp
const DBBLOBHANDLINGENUM GetBlobHandling() const;
```

### <a name="remarks"></a>Uwagi

Zwraca obiekt BLOB, obsługa wartość *eBlobHandling* jako ustawione przez [setblobhandling —](../../data/oledb/cdynamicaccessor-setblobhandling.md).

## <a name="getblobsizelimit"></a> CDynamicAccessor::GetBlobSizeLimit

Pobiera maksymalny rozmiar obiektu BLOB w bajtach.

### <a name="syntax"></a>Składnia

```cpp
const DBLENGTH GetBlobSizeLimit() const;
```

### <a name="remarks"></a>Uwagi

Zwraca obiekt BLOB, obsługa wartość *nBlobSize* jako ustawione przez [setblobsizelimit —](../../data/oledb/cdynamicaccessor-setblobsizelimit.md).

## <a name="getbookmark"></a> CDynamicAccessor::GetBookmark

Pobiera zakładki dla bieżącego wiersza.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetBookmark(CBookmark< >* pBookmark) const throw();
```

#### <a name="parameters"></a>Parametry

*pBookmark*<br/>
[out] Wskaźnik do [CBookmark](../../data/oledb/cbookmark-class.md) obiektu.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

Należy ustawić `DBPROP_IRowsetLocate` VARIANT_TRUE można pobrać zakładki.

## <a name="getcolumncount"></a> CDynamicAccessor::GetColumnCount

Pobiera liczbę kolumn.

### <a name="syntax"></a>Składnia

```cpp
DBORDINAL GetColumnCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Pobrać liczbę kolumn.

## <a name="getcolumnflags"></a> CDynamicAccessor::GetColumnFlags

Pobiera właściwości kolumny.

### <a name="syntax"></a>Składnia

```cpp
bool GetColumnFlags(DBORDINAL nColumn,
   DBCOLUMNFLAGS* pFlags) const throw();
```

#### <a name="parameters"></a>Parametry

*nColumn*<br/>
[in] Numer kolumny. Numery kolumn zaczynać od 1. Wartość 0 odwołuje się do kolumny zakładki, jeśli istnieje.

*pFlags*<br/>
[out] Wskaźnik do maski bitów, który opisuje charakterystykę kolumny. Zobacz sekcję "Typ wyliczany DBCOLUMNFLAGS" w [IColumnsInfo::GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) w *OLE DB Podręcznik programisty*.

### <a name="return-value"></a>Wartość zwracana

Zwraca **true** Jeśli charakterystyki kolumny są pomyślnie pobrane. W przeciwnym razie zwraca **false**.

### <a name="remarks"></a>Uwagi

Numer kolumny jest przesuwane z jednego. Kolumna zero jest przypadkiem szczególnym; Jeśli jest dostępna, jest zakładki.

## <a name="getcolumninfo"></a> CDynamicAccessor::GetColumnInfo

Zwraca metadane kolumny wymagane przez większość klientów.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetColumnInfo(IRowset* pRowset,
   DBORDINAL* pColumns,
   DBCOLUMNINFO** ppColumnInfo,
   OLECHAR** ppStringsBuffer) throw();
```

#### <a name="parameters"></a>Parametry

*pRowset*<br/>
[in] Wskaźnik do [IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85)) interfejsu.

*pColumns*<br/>
[out] Wskaźnik do pamięci, w której ma zostać zwrócone z liczbą kolumn w zestawie wierszy; Liczba ta obejmuje kolumny zakładki, jeśli taka istnieje.

*ppColumnInfo*<br/>
[out] Wskaźnik do pamięci, w której ma zostać zwrócone tablicę `DBCOLUMNINFO` struktury. Zobacz sekcję "DBCOLUMNINFO struktury" w [IColumnsInfo::GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) w *OLE DB Podręcznik programisty*.

*ppStringsBuffer*<br/>
[out] Wskaźnik do pamięci, w której ma zostać zwracają wskaźnik do magazynu dla wszystkich wartości parametrów (nazwy używane znajdującego się w obrębie *columnid* lub *pwszName*) w ramach bloku pojedynczą alokację.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

Zobacz [IColumnsInfo::GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) w *OLE DB Podręcznik programisty* informacji na temat typów danych `DBORDINAL`, `DBCOLUMNINFO`, i `OLECHAR`.

## <a name="getcolumnname"></a> CDynamicAccessor::GetColumnName

Pobiera nazwę określonej kolumny.

### <a name="syntax"></a>Składnia

```cpp
LPOLESTR GetColumnName(DBORDINAL nColumn) const throw();
```

#### <a name="parameters"></a>Parametry

*nColumn*<br/>
[in] Numer kolumny. Numery kolumn zaczynać od 1. Wartość 0 odwołuje się do kolumny zakładki, jeśli istnieje.

### <a name="return-value"></a>Wartość zwracana

Nazwa określonej kolumny.

## <a name="getcolumntype"></a> CDynamicAccessor::GetColumnType

Pobiera typ danych w określonej kolumnie.

### <a name="syntax"></a>Składnia

```cpp
bool GetColumnType(DBORDINAL nColumn,
   DBTYPE* pType) const throw();
```

#### <a name="parameters"></a>Parametry

*nColumn*<br/>
[in] Numer kolumny. Numery kolumn zaczynać od 1. Wartość 0 odwołuje się do kolumny zakładki, jeśli istnieje.

*pType*<br/>
[out] Wskaźnik do typu danych dla określonej kolumny.

### <a name="return-value"></a>Wartość zwracana

Zwraca **true** w przypadku powodzenia lub **false** w przypadku niepowodzenia.

## <a name="getlength"></a> CDynamicAccessor::GetLength

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
[in] Numer kolumny. Numery kolumn zaczynać od 1. Wartość 0 odwołuje się do kolumny zakładki, jeśli istnieje.

*pColumnName*<br/>
[in] Wskaźnik na ciąg znaków zawierający nazwę kolumny.

*pLength*<br/>
[out] Wskaźnik do liczby całkowitej, zawierająca długość kolumny w bajtach.

### <a name="return-value"></a>Wartość zwracana

Zwraca **true** Jeśli zostanie znaleziony w określonej kolumnie. W przeciwnym razie funkcja zwraca **false**.

### <a name="remarks"></a>Uwagi

Pierwszy zastąpienie przyjmuje numer kolumny, natomiast drugi i trzeci zastąpienia nazwa kolumny w formacie ANSI lub Unicode, odpowiednio.

## <a name="getordinal"></a> CDynamicAccessor::GetOrdinal

Pobiera numer kolumny, otrzymuje nazwę kolumny.

### <a name="syntax"></a>Składnia

```cpp
bool GetOrdinal(const CHAR* pColumnName,
   DBORDINAL* pOrdinal) const throw();

bool GetOrdinal(const WCHAR* pColumnName,
   DBORDINAL* pOrdinal) const throw();
```

#### <a name="parameters"></a>Parametry

*pColumnName*<br/>
[in] Wskaźnik na ciąg znaków zawierający nazwę kolumny.

*pOrdinal*<br/>
[out] Wskaźnik do liczby kolumn.

### <a name="return-value"></a>Wartość zwracana

Zwraca **true** jeśli znajduje się kolumna o określonej nazwie. W przeciwnym razie funkcja zwraca **false**.

## <a name="getstatus"></a> CDynamicAccessor::GetStatus

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
[in] Numer kolumny. Numery kolumn zaczynać od 1. Wartość 0 odwołuje się do kolumny zakładki, jeśli istnieje.

*pColumnName*<br/>
[in] Wskaźnik na ciąg znaków zawierający nazwę kolumny.

*pStatus*<br/>
[out] Wskaźnik do zmiennej, zawierający stan kolumny. Zobacz [DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) w *OLE DB Podręcznik programisty* Aby uzyskać więcej informacji.

### <a name="return-value"></a>Wartość zwracana

Zwraca **true** Jeśli zostanie znaleziony w określonej kolumnie. W przeciwnym razie funkcja zwraca **false**.

## <a name="getvalue"></a> CDynamicAccessor::GetValue

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

*ctype*<br/>
[in] Oparte na szablonach parametr, który obsługuje żadnego typu danych, z wyjątkiem typów ciągów (`CHAR*`, `WCHAR*`), które wymagają specjalnej obsługi. `GetValue` używa odpowiedni typ danych oparte na w tym miejscu Określ.

*nColumn*<br/>
[in] Numer kolumny. Numery kolumn zaczynać od 1. Wartość 0 odwołuje się do kolumny zakładki, jeśli istnieje.

*pColumnName*<br/>
[in] Nazwa kolumny.

*pData*<br/>
[out] Wskaźnik do zawartości dla określonej kolumny.

### <a name="return-value"></a>Wartość zwracana

Jeśli chcesz przekazać dane ciągu, użyj wersji nieszablonową `GetValue`. Wersje nieszablonową tej metody zwrócić `void*`, który wskazuje na część buforu, który zawiera dane określonej kolumny. Zwraca wartość NULL, jeśli kolumna nie zostanie znaleziony.

W przypadku wszystkich innych typów danych jest łatwiejszy w obsłudze oparte na szablonach wersje `GetValue`. Zwróć oparte na szablonach wersje **true** w przypadku powodzenia lub **false** w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Użyj wersji nieszablonową, aby zwrócić kolumn zawierających ciągi i oparte na szablonach wersje dla kolumny, które zawierają inne typy danych.

W trybie debugowania, otrzymasz potwierdzenie Jeśli rozmiar *pData* jest nierówne rozmiar kolumny, na którą wskazuje.

## <a name="setblobhandling"></a> CDynamicAccessor::SetBlobHandling

Ustawia obiekt BLOB, Obsługa wartości bieżącego wiersza.

### <a name="syntax"></a>Składnia

```cpp
bool SetBlobHandling(DBBLOBHANDLINGENUM eBlobHandling);
```

#### <a name="parameters"></a>Parametry

*eBlobHandling*<br/>
Określa sposób obsługi danych obiektów BLOB. Może upłynąć następujące wartości:

- DBBLOBHANDLING_DEFAULT: Obsługa danych kolumny jest większa niż *nBlobSize* (jak ustawione przez `SetBlobSizeLimit`) jako dane obiektu BLOB i pobrać ją przy użyciu `ISequentialStream` lub `IStream` obiektu. Ta opcja spowoduje podjęcie próby powiązać każdy kolumny zawierającej dane, które są większe niż *nBlobSize* lub wymieniony jako DBTYPE_IUNKNOWN jako danych obiektów BLOB.

- DBBLOBHANDLING_NOSTREAMS: Obsługa danych kolumny jest większa niż *nBlobSize* (jak ustawione przez `SetBlobSizeLimit`) jako dane obiektu BLOB i pobierania jej poprzez odwołanie do pamięci przydzielonej przez dostawcę, należące do klientów. Ta opcja jest przydatna w przypadku tabel, które mają więcej niż jednej kolumny obiektów BLOB, a dostawca obsługuje tylko jeden `ISequentialStream` obiektem w osobnym metody dostępu.

- DBBLOBHANDLING_SKIP: Pomiń (nie tworzy wiązania) kolumny kwalifikujących się jako zawierające obiekty BLOB (akcesor powiązania nie lub pobrać wartości kolumny, ale nadal będzie pobierać, stan kolumny i długości).

### <a name="remarks"></a>Uwagi

Należy wywołać `SetBlobHandling` przed wywołaniem `Open`.

Metoda konstruktora [cdynamicaccessor —](../../data/oledb/cdynamicaccessor-class.md) ustawia obsługi wartość DBBLOBHANDLING_DEFAULT obiektu BLOB.

## <a name="setblobsizelimit"></a> CDynamicAccessor::SetBlobSizeLimit

Ustawia maksymalny rozmiar obiektu BLOB w bajtach.

### <a name="syntax"></a>Składnia

```cpp
void SetBlobSizeLimit(DBLENGTH nBlobSize);
```

#### <a name="parameters"></a>Parametry

*nBlobSize*<br/>
Określa limit rozmiaru obiektów BLOB.

### <a name="remarks"></a>Uwagi

Ustawia maksymalny rozmiar obiektu BLOB w bajtach; kolumny danych większe niż ta wartość jest traktowana jako obiekt BLOB. Niektórzy dostawcy zapewniają bardzo duże rozmiary kolumn (na przykład 2 GB). Zamiast próbuje przydzielić pamięci dla kolumny ten rozmiar, będzie zazwyczaj spróbuj powiązać te kolumny jako obiekty BLOB. Dzięki temu nie trzeba przydzielić jej całą pamięć, ale nadal można odczytywać wszystkie dane bez obawy obcięcie. Jednakże istnieją przypadki, w których możesz chcieć wymusić `CDynamicAccessor` powiązać duże kolumny w ich typach danych natywnych. Aby to zrobić, należy wywołać `SetBlobSizeLimit` przed wywołaniem `Open`.

Metoda konstruktora [cdynamicaccessor —](../../data/oledb/cdynamicaccessor-class.md) Ustawia maksymalny rozmiar obiektu BLOB na wartość domyślną 8000 bajtów.

## <a name="setlength"></a> CDynamicAccessor::SetLength

Ustawia długość dla określonej kolumny.

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
[in] Numer kolumny. Numery kolumn zaczynać od 1. Wartość 0 odwołuje się do kolumny zakładki, jeśli istnieje.

*nLength*<br/>
[in] Długość kolumny w bajtach.

*pColumnName*<br/>
[in] Wskaźnik na ciąg znaków zawierający nazwę kolumny.

### <a name="return-value"></a>Wartość zwracana

Zwraca **true** Jeśli długość określona kolumna jest ustawiona pomyślnie. W przeciwnym razie funkcja zwraca **false**.

## <a name="setstatus"></a> CDynamicAccessor::SetStatus

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
[in] Numer kolumny. Numery kolumn zaczynać od 1. Wartość 0 odwołuje się do kolumny zakładki, jeśli istnieje.

*status*<br/>
[in] Stan kolumny. Zobacz [DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) w *OLE DB Podręcznik programisty* Aby uzyskać więcej informacji.

*pColumnName*<br/>
[in] Wskaźnik na ciąg znaków zawierający nazwę kolumny.

### <a name="return-value"></a>Wartość zwracana

Zwraca **true** Jeśli pomyślnie ustawiono stan określonej kolumny. W przeciwnym razie funkcja zwraca **false**.

## <a name="setvalue"></a> CDynamicAccessor::SetValue

Przechowuje dane do określonej kolumny.

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

*ctype*<br/>
[in] Oparte na szablonach parametr, który obsługuje żadnego typu danych, z wyjątkiem typów ciągów (`CHAR*`, `WCHAR*`), które wymagają specjalnej obsługi. `GetValue` używa odpowiedni typ danych oparte na w tym miejscu Określ.

*pColumnName*<br/>
[in] Wskaźnik na ciąg znaków zawierający nazwę kolumny.

*data*<br/>
[in] Wskaźnik do pamięci zawierający dane.

*nColumn*<br/>
[in] Numer kolumny. Numery kolumn zaczynać od 1. Wartość 0 odwołuje się do kolumny zakładki, jeśli istnieje.

### <a name="return-value"></a>Wartość zwracana

Jeśli chcesz ustawić ciąg danych, użyj wersji nieszablonową `GetValue`. Wersje nieszablonową tej metody zwrócić `void*`, który wskazuje na część buforu, który zawiera dane określonej kolumny. Zwraca wartość NULL, jeśli kolumna nie zostanie znaleziony.

W przypadku wszystkich innych typów danych jest łatwiejszy w obsłudze oparte na szablonach wersje `GetValue`. Zwróć oparte na szablonach wersje **true** w przypadku powodzenia lub **false** w przypadku niepowodzenia.

## <a name="see-also"></a>Zobacz także

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor, klasa](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor, klasa](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor, klasa](../../data/oledb/cmanualaccessor-class.md)