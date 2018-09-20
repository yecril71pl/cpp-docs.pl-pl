---
title: Klasa CDaoQueryDef | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoQueryDef
- AFXDAO/CDaoQueryDef
- AFXDAO/CDaoQueryDef::CDaoQueryDef
- AFXDAO/CDaoQueryDef::Append
- AFXDAO/CDaoQueryDef::CanUpdate
- AFXDAO/CDaoQueryDef::Close
- AFXDAO/CDaoQueryDef::Create
- AFXDAO/CDaoQueryDef::Execute
- AFXDAO/CDaoQueryDef::GetConnect
- AFXDAO/CDaoQueryDef::GetDateCreated
- AFXDAO/CDaoQueryDef::GetDateLastUpdated
- AFXDAO/CDaoQueryDef::GetFieldCount
- AFXDAO/CDaoQueryDef::GetFieldInfo
- AFXDAO/CDaoQueryDef::GetName
- AFXDAO/CDaoQueryDef::GetODBCTimeout
- AFXDAO/CDaoQueryDef::GetParameterCount
- AFXDAO/CDaoQueryDef::GetParameterInfo
- AFXDAO/CDaoQueryDef::GetParamValue
- AFXDAO/CDaoQueryDef::GetRecordsAffected
- AFXDAO/CDaoQueryDef::GetReturnsRecords
- AFXDAO/CDaoQueryDef::GetSQL
- AFXDAO/CDaoQueryDef::GetType
- AFXDAO/CDaoQueryDef::IsOpen
- AFXDAO/CDaoQueryDef::Open
- AFXDAO/CDaoQueryDef::SetConnect
- AFXDAO/CDaoQueryDef::SetName
- AFXDAO/CDaoQueryDef::SetODBCTimeout
- AFXDAO/CDaoQueryDef::SetParamValue
- AFXDAO/CDaoQueryDef::SetReturnsRecords
- AFXDAO/CDaoQueryDef::SetSQL
- AFXDAO/CDaoQueryDef::m_pDAOQueryDef
- AFXDAO/CDaoQueryDef::m_pDatabase
dev_langs:
- C++
helpviewer_keywords:
- CDaoQueryDef [MFC], CDaoQueryDef
- CDaoQueryDef [MFC], Append
- CDaoQueryDef [MFC], CanUpdate
- CDaoQueryDef [MFC], Close
- CDaoQueryDef [MFC], Create
- CDaoQueryDef [MFC], Execute
- CDaoQueryDef [MFC], GetConnect
- CDaoQueryDef [MFC], GetDateCreated
- CDaoQueryDef [MFC], GetDateLastUpdated
- CDaoQueryDef [MFC], GetFieldCount
- CDaoQueryDef [MFC], GetFieldInfo
- CDaoQueryDef [MFC], GetName
- CDaoQueryDef [MFC], GetODBCTimeout
- CDaoQueryDef [MFC], GetParameterCount
- CDaoQueryDef [MFC], GetParameterInfo
- CDaoQueryDef [MFC], GetParamValue
- CDaoQueryDef [MFC], GetRecordsAffected
- CDaoQueryDef [MFC], GetReturnsRecords
- CDaoQueryDef [MFC], GetSQL
- CDaoQueryDef [MFC], GetType
- CDaoQueryDef [MFC], IsOpen
- CDaoQueryDef [MFC], Open
- CDaoQueryDef [MFC], SetConnect
- CDaoQueryDef [MFC], SetName
- CDaoQueryDef [MFC], SetODBCTimeout
- CDaoQueryDef [MFC], SetParamValue
- CDaoQueryDef [MFC], SetReturnsRecords
- CDaoQueryDef [MFC], SetSQL
- CDaoQueryDef [MFC], m_pDAOQueryDef
- CDaoQueryDef [MFC], m_pDatabase
ms.assetid: 9676a4a3-c712-44d4-8c5d-d1cc78288d3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be2676609cae4de6b2f3995be1bc9311f88e0a84
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408717"
---
# <a name="cdaoquerydef-class"></a>Klasa CDaoQueryDef

Przedstawia definicję kwerendy lub "querydef"; zazwyczaj jedna zapisana w bazie danych.

## <a name="syntax"></a>Składnia

```
class CDaoQueryDef : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoQueryDef::CDaoQueryDef](#cdaoquerydef)|Konstruuje `CDaoQueryDef` obiektu. Następnie wywołaj `Open` lub `Create`, w zależności od potrzeb.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoQueryDef::Append](#append)|Dołącza querydef do bazy danych querydefs — kolekcja jako zapisaną kwerendę.|
|[CDaoQueryDef::CanUpdate](#canupdate)|Zwraca wartość różną od zera, jeśli zapytanie można zaktualizować bazy danych.|
|[CDaoQueryDef::Close](#close)|Zamyka obiektu querydef. Zniszczenie obiektu języka C++, po zapoznaniu się z nim.|
|[CDaoQueryDef::Create](#create)|Tworzy obiekt źródłowy querydef DAO. Użyj querydef jako tymczasowy kwerendy lub wywołanie `Append` go zapisać w bazie danych.|
|[CDaoQueryDef::Execute](#execute)|Wykonuje zapytanie zdefiniowane przez obiekt querydef.|
|[CDaoQueryDef::GetConnect](#getconnect)|Zwraca ciąg połączenia skojarzone z querydef. Parametry połączenia identyfikuje źródła danych. (Dla programu SQL zapytań przekazujących tylko; w przeciwnym razie pusty ciąg.)|
|[CDaoQueryDef::GetDateCreated](#getdatecreated)|Zwraca daty utworzenia zapisanego zapytania.|
|[CDaoQueryDef::GetDateLastUpdated](#getdatelastupdated)|Zwraca datę ostatniej aktualizacji zapisanego zapytania.|
|[CDaoQueryDef::GetFieldCount](#getfieldcount)|Zwraca liczbę pól zdefiniowanych przez querydef.|
|[CDaoQueryDef::GetFieldInfo](#getfieldinfo)|Zwraca informacje dotyczące określonego pola zdefiniowane w zapytaniu.|
|[CDaoQueryDef::GetName](#getname)|Zwraca nazwę obiektu querydef.|
|[CDaoQueryDef::GetODBCTimeout](#getodbctimeout)|Zwraca wartość limitu czasu, używany przez ODBC (dla kwerendy ODBC) po wykonaniu querydef. Jak długo określa umożliwić ukończenie akcji zapytania.|
|[CDaoQueryDef::GetParameterCount](#getparametercount)|Zwraca liczbę parametrów zdefiniowanych w zapytaniu.|
|[CDaoQueryDef::GetParameterInfo](#getparameterinfo)|Zwraca informacje dotyczące określonego parametru zapytania.|
|[CDaoQueryDef::GetParamValue](#getparamvalue)|Zwraca wartość określonego parametru zapytania.|
|[CDaoQueryDef::GetRecordsAffected](#getrecordsaffected)|Zwraca liczbę rekordów dotyczy kwerenda.|
|[CDaoQueryDef::GetReturnsRecords](#getreturnsrecords)|Zwraca wartość różną od zera, jeśli zapytanie zdefiniowane przez querydef zwraca rekordy.|
|[CDaoQueryDef::GetSQL](#getsql)|Zwraca ciąg SQL, który określa zapytanie zdefiniowane przez querydef.|
|[CDaoQueryDef::GetType](#gettype)|Zwraca typ zapytania: usuwanie, aktualizowanie, Dołącz tworzącej tabelę i tak dalej.|
|[CDaoQueryDef::IsOpen](#isopen)|Zwraca wartość różną od zera, jeśli querydef jest otwarta i może być wykonywane.|
|[CDaoQueryDef::Open](#open)|Otwiera istniejący querydef przechowywane w bazie danych querydefs — kolekcja.|
|[CDaoQueryDef::SetConnect](#setconnect)|Ustawia parametry połączenia dla zapytania przekazującego SQL źródła danych ODBC.|
|[CDaoQueryDef::SetName](#setname)|Określa nazwę zapisanego zapytania, zastępując nazwa używana podczas tworzenia obiektu querydef.|
|[CDaoQueryDef::SetODBCTimeout](#setodbctimeout)|Ustawia wartość limitu czasu, używany przez ODBC (dla kwerendy ODBC) po wykonaniu querydef.|
|[CDaoQueryDef::SetParamValue](#setparamvalue)|Ustawia wartość określonego parametru zapytania.|
|[CDaoQueryDef::SetReturnsRecords](#setreturnsrecords)|Określa, czy querydef zwraca rekordy. Ustawienie tego atrybutu na wartość TRUE jest prawidłowy tylko dla przekazywania kwerend SQL.|
|[CDaoQueryDef::SetSQL](#setsql)|Ustawia ciąg SQL, który określa zapytanie zdefiniowane przez querydef.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDaoQueryDef::m_pDAOQueryDef](#m_pdaoquerydef)|Wskaźnik do interfejsu OLE dla obiektu źródłowego querydef DAO.|
|[CDaoQueryDef::m_pDatabase](#m_pdatabase)|Wskaźnik do `CDaoDatabase` obiektu, z którym jest skojarzona querydef. Querydef może być zapisany w bazie danych, czy nie.|

## <a name="remarks"></a>Uwagi

Querydef jest obiekt dostępu do danych, który zawiera instrukcję SQL, która opisuje kwerendy i jego właściwości, takie jak "Data utworzenia" i "Limit czasu ODBC." Możesz również utworzyć obiekty tymczasowe querydef bez ich zapisywania, ale jest to wygodne — i znacznie bardziej efektywne — zapisać często używane ponownie zapytań w bazie danych. A [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) obiekt przechowuje kolekcję o nazwie querydefs — kolekcja zawierającego jego zapisane querydefs —.

> [!NOTE]
>  Klasy bazy danych DAO różnią się od klas baz danych MFC, które są oparte na Open Database Connectivity (ODBC). Wszystkie nazwy klasy bazy danych DAO mają prefiks "CDao". Możesz nadal dostęp do źródła danych ODBC przy użyciu klas DAO. Ogólnie rzecz biorąc klasy MFC, w oparciu o DAO sprzętowi więcej niż klas MFC, w oparciu o ODBC; klasy oparte na DAO można uzyskać dostęp do danych, w tym za pomocą sterowników ODBC, za pomocą ich własnych aparatu bazy danych. Klasy oparte na DAO obsługują także operacji języka definicji danych (DDL), takich jak dodawanie tablic przy użyciu klas, bez konieczności wywoływanie obiektów DAO bezpośrednio.

## <a name="usage"></a>Użycie

Za pomocą querydef obiektów albo do pracy z istniejącego zapisanego zapytania, lub utworzyć nową zapisać kwerendę lub tymczasowego:

1. We wszystkich przypadkach najpierw skonstruuj `CDaoQueryDef` obiektu, podając wskaźnik do [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) obiekt, do którego należy zapytania.

1. Następnie wykonaj następujące czynności, w zależności od tego, co chcesz zrobić:

   - Aby użyć istniejącego zapisanego zapytania, należy wywołać obiekt querydef [Otwórz](#open) funkcji członkowskiej, podając nazwę zapisanego zapytania.

   - Aby utworzyć nową zapisaną kwerendę, wywołaj obiektu querydef [Utwórz](#create) funkcji członkowskiej, podając nazwę kwerendy. Następnie wywołaj [Append](#append) można zapisać zapytania przez dodanie go do bazy danych querydefs — kolekcja. `Create` umieszcza querydef do stanu rozwartego, więc po wywołaniu `Create` Nie wywołuj `Open`.

   - Aby utworzyć tymczasowy querydef, wywołaj `Create`. Przekazać pusty ciąg jako nazwę zapytania. Nie wywołuj `Append`.

Po zakończeniu za pomocą obiektu querydef wywołać jej [Zamknij](#close) element członkowski funkcji; następnie zniszczenie obiektu querydef.

> [!TIP]
>  Najprostszym sposobem utworzenia zapisane zapytania jest je tworzyć i przechowywać je w bazie danych przy użyciu programu Microsoft Access. Następnie można otworzyć i używać ich w kodzie MFC.

## <a name="purposes"></a>Do celów

Można użyć obiektu querydef dla żadnego z następujących celów:

- Aby utworzyć `CDaoRecordset` obiektu

- Aby wywołać obiekt `Execute` funkcja elementu członkowskiego na bezpośrednie wykonywanie akcji lub kwerendy SQL przekazywania

Można użyć obiektu querydef dla dowolnego typu zapytania, w tym wybierz akcję, krzyżowej, usuwania, aktualizacji, Dołącz tworzącej, definicja danych, przekazywanego SQL, Unii i zbiorczo zapytania. Typ kwerendy jest ustalany przez zawartość instrukcji SQL, który podasz. Aby uzyskać informacji na temat typów zapytań, zobacz `Execute` i [GetType](#gettype) funkcji elementów członkowskich. Zestawy rekordów są często używane do zwracania wiersza zapytania, zwykle za pomocą **wybierz... Z** słów kluczowych. `Execute` najczęściej używane dla operacji zbiorczych. Aby uzyskać więcej informacji, zobacz [Execute](#execute) i [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

## <a name="querydefs-and-recordsets"></a>Querydefs — i zestawy rekordów

Na potrzeby tworzenia obiektu querydef `CDaoRecordset` obiektu zwykle tworzenia lub otwierania querydef zgodnie z powyższym opisem. Następnie skonstruować obiekt zestawu rekordów przekazywania wskaźnika do obiektu querydef po wywołaniu [CDaoRecordset::Open](../../mfc/reference/cdaorecordset-class.md#open). Querydef, które można przekazać musi być w stanie otwartym. Aby uzyskać więcej informacji, zobacz klasy [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Za pomocą querydef nie można utworzyć zestaw rekordów (najczęściej używane dla querydef), chyba że jest w stanie otwartym. Umieść querydef otwarte przez wywołanie metody albo `Open` lub `Create`.

## <a name="external-databases"></a>Zewnętrznych baz danych

Obiekty QueryDef są preferowanym sposobem użycia natywnych dialekt SQL z zewnętrznej bazy danych aparatu. Na przykład można utworzyć zapytanie Transact SQL (tak jak program Microsoft SQL Server) i zapisz go w obiekcie querydef. Jeśli muszą korzystać z zapytania SQL nie jest oparta na aparacie bazy danych Microsoft Jet, musisz podać parametry połączenia, który wskazuje na zewnętrzne źródło danych. Zapytania z ciągami prawidłowe połączenie obejścia aparatu bazy danych i przekazać zapytanie bezpośrednio do serwera zewnętrznej bazy danych w celu przetwarzania.

> [!TIP]
>  Dołącz je do programu Microsoft Jet jest preferowany sposób pracy z tabel ODBC (. Baza danych MDB).

Aby uzyskać powiązane informacje zobacz tematy "QueryDef Object", "Querydefs — Kolekcja" i "Obiekt CdbDatabase" w zestawie SDK DAO.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CDaoQueryDef`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

##  <a name="append"></a>  CDaoQueryDef::Append

Wywołaj tę funkcję elementu członkowskiego, po wywołaniu metody [Utwórz](#create) można utworzyć nowego obiektu querydef.

```
virtual void Append();
```

### <a name="remarks"></a>Uwagi

`Append` zapisuje querydef w bazie danych, dodając obiekt do bazy danych querydefs — kolekcja. Querydef można używać jako obiekt tymczasowy, bez dołączenie jej, ale jeśli chcesz, aby utrwalić, należy wywołać `Append`.

Jeśli spróbujesz dołączyć obiektu tymczasowego querydef MFC zgłasza wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

##  <a name="canupdate"></a>  CDaoQueryDef::CanUpdate

Wywołaj tę funkcję elementu członkowskiego, aby ustalić, czy można zmodyfikować obiektu querydef — takie jak zmiana jego nazwy lub parametrów SQL.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli masz uprawnień do modyfikowania querydef; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Można zmodyfikować obiektu querydef, jeśli:

- Nie jest oparty na bazie danych, która jest otwarta w trybie tylko do odczytu.

- Masz uprawnienia do aktualizacji bazy danych.

     Zależy to od tego, czy udało Ci się wdrożyć funkcje zabezpieczeń. MFC nie zapewnia obsługi zabezpieczeń; należy zaimplementować go samodzielnie za wywoływanie obiektów DAO bezpośrednio lub za pomocą programu Microsoft Access. Zobacz temat "Property uprawnień" w Pomocy programu DAO.

##  <a name="cdaoquerydef"></a>  CDaoQueryDef::CDaoQueryDef

Konstruuje `CDaoQueryDef` obiektu.

```
CDaoQueryDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>Parametry

*pDatabase*<br/>
Wskaźnik otwartych [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) obiektu.

### <a name="remarks"></a>Uwagi

Obiekt może reprezentować querydef istniejących w bazy danych querydefs — kolekcja, nowe zapytanie ma być przechowywany w kolekcji lub tymczasowego zapytania, aby nie były przechowywane. Następnym krokiem jest zależna od typu querydef:

- Jeśli obiekt reprezentuje istniejących querydef, należy wywołać obiekt [Otwórz](#open) funkcja elementu członkowskiego, aby go zainicjować.

- Jeśli obiekt reprezentuje nowe querydef do zapisania, należy wywołać obiekt [Utwórz](#create) funkcja elementu członkowskiego. Spowoduje to dodanie obiektu do bazy danych querydefs — kolekcja. Następnie wywołaj `CDaoQueryDef` funkcji elementów członkowskich, które można ustawić atrybutów obiektu. Na koniec Wywołaj [Append](#append).

- Jeśli obiekt reprezentuje tymczasowe querydef (nie można zapisać w bazie danych), należy wywołać `Create`, przekazując pusty ciąg nazwy zapytania. Po wywołaniu `Create`, zainicjować querydef bezpośrednio, ustawiając jego atrybuty. Nie wywołuj `Append`.

Aby ustawić atrybuty obiektu QueryDef, można użyć [SetName](#setname), [SetSQL](#setsql), [SetConnect](#setconnect), [SetODBCTimeout](#setodbctimeout)i [SetReturnsRecords](#setreturnsrecords) funkcji elementów członkowskich.

Po zakończeniu z obiektem querydef wywołać jej [Zamknij](#close) funkcja elementu członkowskiego. Jeśli masz wskaźnik do obiektu querydef, użyj **Usuń** operatora do zniszczenia obiektu języka C++.

##  <a name="close"></a>  CDaoQueryDef::Close

Wywołaj tę funkcję elementu członkowskiego, po zakończeniu używania obiektu querydef.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Zamykanie querydef zwalnia obiekt DAO, ale nie niszczy zapisany obiekt querydef DAO lub C++ `CDaoQueryDef` obiektu. To nie jest taka sama jak [CDaoDatabase::DeleteQueryDef](../../mfc/reference/cdaodatabase-class.md#deletequerydef), które powoduje usunięcie querydef z bazy danych querydefs — kolekcja w DAO (Jeśli nie querydef tymczasowe).

##  <a name="create"></a>  CDaoQueryDef::Create

Wywołaj tę funkcję elementu członkowskiego, aby utworzyć nowe zapytanie zapisanego lub nowe zapytanie tymczasowych.

```
virtual void Create(
    LPCTSTR lpszName = NULL,
    LPCTSTR lpszSQL = NULL);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Unikatowa nazwa zapytania zapisane w bazie danych. Szczegółowe informacje na temat parametrów zobacz temat "CreateQueryDef metody" w Pomocy programu DAO. Jeśli zaakceptuj wartość domyślną, ciągiem pustym querydef tymczasowy zostanie utworzony. W przypadku takiego zapytania nie są zapisywane w querydefs — kolekcja.

*lpszSQL*<br/>
Ciąg SQL, który definiuje zapytanie. Jeśli użytkownik zaakceptuje domyślna wartość NULL, później należy wywołać [SetSQL](#setsql) można ustawić parametrów. W międzyczasie zapytanie jest niezdefiniowany. Można jednak, używając niezdefiniowane kwerendy, można otworzyć zestawu rekordów; Aby uzyskać szczegółowe informacje, zobacz uwagi. Instrukcja SQL musi być zdefiniowana, zanim będzie możliwe dołączenie querydef do querydefs — kolekcja.

### <a name="remarks"></a>Uwagi

W przypadku przekazania nazwy w *lpszName*, następnie możesz wywołać [Append](#append) można zapisać obiektu querydef w bazie danych querydefs — kolekcja. W przeciwnym razie obiekt jest tymczasowy querydef i nie został zapisany. W obu przypadkach querydef znajduje się w stanie otwartym. Ponadto możesz użyć go do utworzenia [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obiektu lub wywołać querydef [Execute](#execute) funkcja elementu członkowskiego.

Jeśli nie podasz instrukcję SQL w *lpszSQL*, nie można uruchomić zapytania przez łączenie `Execute` , ale można go utworzyć zestaw rekordów. W takim przypadku MFC używa domyślnego instrukcji SQL zestawu rekordów.

##  <a name="execute"></a>  CDaoQueryDef::Execute

Wywołaj tę funkcję elementu członkowskiego, aby uruchomić zapytanie zdefiniowane przez obiekt querydef.

```
virtual void Execute(int nOptions = dbFailOnError);
```

### <a name="parameters"></a>Parametry

*nOptions*<br/>
Liczba całkowita, która określa właściwości zapytania. Aby uzyskać powiązane informacje zobacz temat "Wykonania metody" w Pomocy programu DAO. Możesz użyć operatora bitowego OR ( **&#124;**) do łączenia się z następujących stałych dla tego argumentu:

- `dbDenyWrite` Odmowa uprawnień do zapisu dla innych użytkowników.

- `dbInconsistent` Niespójne aktualizacje.

- `dbConsistent` Zgodne aktualizacje.

- `dbSQLPassThrough` Przekazywane SQL. Powoduje, że instrukcji SQL, które zostaną przekazane do bazy danych ODBC do przetworzenia.

- `dbFailOnError` Wartość domyślna. Wycofywanie aktualizacji, jeśli wystąpi błąd i Raport ten błąd użytkownikowi.

- `dbSeeChanges` Generowanie błędów czasu wykonywania, jeśli inny użytkownik ulegają zmianie danych, który jest edytowany.

> [!NOTE]
>  Wyjaśnienie warunki "niezgodne" i "zgodne" w temacie "Wykonania metody" w Pomocy programu DAO.

### <a name="remarks"></a>Uwagi

Obiekty QueryDef używany do wykonania w ten sposób może być reprezentowana przez jedną z następujących typów zapytań:

- Akcja zapytania

- Zapytania przekazujące SQL

`Execute` nie działa dla zapytań zwracających rekordów, takich jak zapytań select. `Execute` jest powszechnie używany do zbiorczego operacji zapytań, takich jak **aktualizacji**, **Wstaw**, lub **SELECT INTO**, lub operacje na danych definicji języka (DDL).

> [!TIP]
>  Preferowanym sposobem pracują ze źródłami danych ODBC jest Dołącz tabele do Microsoft Jet (. Baza danych MDB). Aby uzyskać więcej informacji zobacz temat "Dostęp do zewnętrznych baz danych za pomocą DAO" w Pomocy programu DAO.

Wywołaj [GetRecordsAffected](#getrecordsaffected) funkcja elementu członkowskiego obiektu querydef, aby określić liczbę rekordów na najnowszych, ostatnio `Execute` wywołania. Na przykład `GetRecordsAffected` zwraca informacje o liczbie rekordów usunięty, zaktualizowane lub wstawić podczas wykonywania kwerendy funkcjonalnej. Liczba zwracane nie będzie odzwierciedlał zmian w tabelach pokrewnych, gdy cascade aktualizuje lub usuwa są stosowane.

Jeśli dołączysz zarówno `dbInconsistent` i `dbConsistent` lub jeśli nie dodasz, wynik jest zachowaniem domyślnym, `dbInconsistent`.

`Execute` Zwraca zestaw rekordów. Za pomocą `Execute` na kwerendzie, która wybiera rekordy powoduje, że MFC, aby zgłosić wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

##  <a name="getconnect"></a>  CDaoQueryDef::GetConnect

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać parametry połączenia, skojarzone ze źródłem danych querydef.

```
CString GetConnect();
```

### <a name="return-value"></a>Wartość zwracana

A [CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierającego parametry połączenia dla querydef.

### <a name="remarks"></a>Uwagi

Ta funkcja jest używana tylko w przypadku źródeł danych ODBC i sterowników niektórych ISAM. Nie jest używany przy użyciu programu Microsoft Jet (. Baz danych MDB); w tym przypadku `GetConnect` zwraca pusty ciąg. Aby uzyskać więcej informacji, zobacz [SetConnect](#setconnect).

> [!TIP]
>  Dołącz je do jest preferowany sposób pracy z tabel ODBC. MDB bazy danych. Aby uzyskać więcej informacji zobacz temat "Dostęp do zewnętrznych baz danych za pomocą DAO" w Pomocy programu DAO.

Aby uzyskać informacji dotyczących parametrów połączenia Zobacz temat "Connect Property" w Pomocy programu DAO.

##  <a name="getdatecreated"></a>  CDaoQueryDef::GetDateCreated

Wywołaj tę funkcję elementu członkowskiego, aby pobrać daty utworzenia obiektu querydef.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Wartość zwracana

A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiekt zawierający datę i godzinę querydef został utworzony.

### <a name="remarks"></a>Uwagi

Aby uzyskać powiązane informacje zobacz temat "DateCreated LastUpdated właściwości", w Pomocy programu DAO.

##  <a name="getdatelastupdated"></a>  CDaoQueryDef::GetDateLastUpdated

Wywołanie tej funkcji elementu członkowskiego, można pobrać obiektu querydef datę ostatniej aktualizacji — gdy żadnej z jej właściwości zostały zmienione, takie jak jego nazwa, jego parametry SQL lub jego parametry połączenia.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Wartość zwracana

A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiekt zawierający datę i godzinę ostatniej aktualizacji querydef.

### <a name="remarks"></a>Uwagi

Aby uzyskać powiązane informacje zobacz temat "DateCreated LastUpdated właściwości", w Pomocy programu DAO.

##  <a name="getfieldcount"></a>  CDaoQueryDef::GetFieldCount

Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę pól w zapytaniu.

```
short GetFieldCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba pól zdefiniowanych w zapytaniu.

### <a name="remarks"></a>Uwagi

`GetFieldCount` jest przydatne w przypadku wszystkich pól w querydef w pętli. W tym celu należy użyć `GetFieldCount` w połączeniu z [GetFieldInfo](#getfieldinfo).

##  <a name="getfieldinfo"></a>  CDaoQueryDef::GetFieldInfo

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać różne rodzaje informacji na temat pola zdefiniowane w querydef.

```
void GetFieldInfo(
    int nIndex,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);


void GetFieldInfo(
    LPCTSTR lpszName,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Liczony od zera indeks żądanego pola w kolekcji pól querydef, wyszukiwania według indeksu.

*FieldInfo*<br/>
Odwołanie do `CDaoFieldInfo` obiektów, które zwraca żądane informacje.

*dwInfoOptions*<br/>
Opcje, które określają, które informacje o polu do pobrania. Dostępne opcje są wymienione w tym miejscu oraz co mogą spowodować, że funkcja zwróci:

- Nazwa, typ, AFX_DAO_PRIMARY_INFO (ustawienie domyślne), rozmiar, atrybuty

- AFX_DAO_SECONDARY_INFO głównej informacje oraz: numer pozycji, wymagane, Zezwalaj na zera długość, pole źródła, nazwa obcego, tabeli źródłowej, kolejność sortowania

- AFX_DAO_ALL_INFO głównych i dodatkowych informacji plus: domyślna wartość tekst sprawdzania poprawności reguły walidacji

*lpszName*<br/>
Ciąg zawierający nazwę żądanego pola wyszukiwania według nazwy. Możesz użyć [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Uwagi

Aby uzyskać opis informacje zwracane w *fieldinfo*, zobacz [cdaofieldinfo —](../../mfc/reference/cdaofieldinfo-structure.md) struktury. Ta struktura zawiera elementy członkowskie, które odpowiadają opisowe informacje w obszarze *dwInfoOptions* powyżej. W przypadku żądania informacji o jeden poziom, otrzymują wszelkie wcześniejsze poziomy również informacje o.

##  <a name="getname"></a>  CDaoQueryDef::GetName

Wywołaj tę funkcję elementu członkowskiego, aby pobrać nazwę zapytanie, reprezentowane przez querydef.

```
CString GetName();
```

### <a name="return-value"></a>Wartość zwracana

Nazwa zapytania.

### <a name="remarks"></a>Uwagi

QueryDef nazwy są unikatowe nazwy użytkownika. Aby uzyskać więcej informacji na temat nazw querydef zobacz temat "Nazwa właściwości" w Pomocy programu DAO.

##  <a name="getodbctimeout"></a>  CDaoQueryDef::GetODBCTimeout

Wywołaj tę funkcję elementu członkowskiego, aby pobrać bieżący limit czasu, zanim upłynie limit czasu zapytania do źródła danych ODBC.

```
short GetODBCTimeout();
```

### <a name="return-value"></a>Wartość zwracana

Liczba sekund przed zapytania upłynie limit czasu.

### <a name="remarks"></a>Uwagi

Dla informacji na temat tego limitu czasu zobacz temat "ODBCTimeout Property" w Pomocy programu DAO.

> [!TIP]
>  Dołącz je do programu Microsoft Jet jest preferowany sposób pracy z tabel ODBC (. Baza danych MDB). Aby uzyskać więcej informacji zobacz temat "Dostęp do zewnętrznych baz danych za pomocą DAO" w Pomocy programu DAO.

##  <a name="getparametercount"></a>  CDaoQueryDef::GetParameterCount

Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę parametrów w zapisanego zapytania.

```
short GetParameterCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba parametrów zdefiniowanych w zapytaniu.

### <a name="remarks"></a>Uwagi

`GetParameterCount` jest przydatne w przypadku wszystkich parametrów w querydef w pętli. W tym celu należy użyć `GetParameterCount` w połączeniu z [getparameterinfo —](#getparameterinfo).

Aby uzyskać powiązane informacje zobacz tematy "Parametr obiektu", "Kolekcję parametrów" i "parametry deklaracji (SQL)" w Pomocy programu DAO.

##  <a name="getparameterinfo"></a>  CDaoQueryDef::GetParameterInfo

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać informacje dotyczące parametru zdefiniowane w querydef.

```
void GetParameterInfo(
    int nIndex,
    CDaoParameterInfo& paraminfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);


void GetParameterInfo(
    LPCTSTR lpszName,
    CDaoParameterInfo& paraminfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Liczony od zera indeks żądanego parametru w kolekcji parametrów querydef, wyszukiwania według indeksu.

*paraminfo*<br/>
Odwołanie do [cdaoparameterinfo —](../../mfc/reference/cdaoparameterinfo-structure.md) obiektów, które zwraca żądane informacje.

*dwInfoOptions*<br/>
Opcje, które określają, które informacje dotyczące parametru do pobrania. Opcja dostępna w tym miejscu znajduje wraz z co go powoduje, że funkcja zwróci:

- Nazwa AFX_DAO_PRIMARY_INFO (ustawienie domyślne), typ

*lpszName*<br/>
Ciąg zawierający nazwę żądanego parametru wyszukiwania według nazwy. Możesz użyć [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Uwagi

Aby uzyskać opis informacje zwracane w *paraminfo*, zobacz [cdaoparameterinfo —](../../mfc/reference/cdaoparameterinfo-structure.md) struktury. Ta struktura zawiera elementy członkowskie, które odpowiadają opisowe informacje w obszarze *dwInfoOptions* powyżej.

Aby uzyskać powiązane informacje zobacz temat "parametry deklaracji (SQL)" w Pomocy programu DAO.

##  <a name="getparamvalue"></a>  CDaoQueryDef::GetParamValue

Wywołaj tę funkcję elementu członkowskiego, aby pobrać bieżącą wartość określonego parametru przechowywanych w kolekcji parametrów querydef.

```
virtual COleVariant GetParamValue(LPCTSTR lpszName);
virtual COleVariant GetParamValue(int nIndex);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Nazwa parametru, którego wartość należy do wyszukiwania według nazwy.

*nIndex*<br/>
Liczony od zera indeks parametru w kolekcji parametrów querydef, wyszukiwania według indeksu. Możesz uzyskać tę wartość przy użyciu wywołań [GetParameterCount](#getparametercount) i [getparameterinfo —](#getparameterinfo).

### <a name="return-value"></a>Wartość zwracana

Obiekt klasy [COleVariant](../../mfc/reference/colevariant-class.md) zawierającą wartość parametru.

### <a name="remarks"></a>Uwagi

Według nazwy lub jego porządkowym w kolekcji, można uzyskać dostęp do parametru.

Aby uzyskać powiązane informacje zobacz temat "parametry deklaracji (SQL)" w Pomocy programu DAO.

##  <a name="getrecordsaffected"></a>  CDaoQueryDef::GetRecordsAffected

Wywołanie tej funkcji elementu członkowskiego, aby określić liczbę rekordów wpłynęła na ostatnie wywołanie elementu [Execute](#execute).

```
long GetRecordsAffected();
```

### <a name="return-value"></a>Wartość zwracana

Liczba zmodyfikowanych rekordów.

### <a name="remarks"></a>Uwagi

Liczba zwracane nie będzie odzwierciedlał zmian w tabelach pokrewnych, gdy cascade aktualizuje lub usuwa są stosowane.

Powiązane informacje na ten temat można znaleźć w temacie "RecordsAffected Property" w Pomocy programu DAO.

##  <a name="getreturnsrecords"></a>  CDaoQueryDef::GetReturnsRecords

Wywołaj tę funkcję elementu członkowskiego, aby ustalić, czy querydef opiera się na zapytanie, które zwraca rekordy.

```
BOOL GetReturnsRecords();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli querydef jest oparty na zapytaniu, które zwraca rekordy; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego tylko jest używany do przekazywania kwerend SQL. Aby uzyskać więcej informacji na temat zapytań SQL zobacz [Execute](#execute) funkcja elementu członkowskiego. Aby uzyskać więcej informacji dotyczących pracy za pomocą przekazywanego zapytań SQL zobacz [SetReturnsRecords](#setreturnsrecords) funkcja elementu członkowskiego.

Aby uzyskać powiązane informacje zobacz temat "ReturnsRecords Property" w Pomocy programu DAO.

##  <a name="getsql"></a>  CDaoQueryDef::GetSQL

Wywołaj tę funkcję elementu członkowskiego, aby pobrać instrukcję SQL, która definiuje zapytanie, na którym bazuje querydef.

```
CString GetSQL();
```

### <a name="return-value"></a>Wartość zwracana

Instrukcja SQL, który definiuje zapytanie, na którym bazuje querydef.

### <a name="remarks"></a>Uwagi

Następnie będzie prawdopodobnie przeanalizować parametrów dla słów kluczowych, nazwy tabel i tak dalej.

Aby uzyskać powiązane informacje zobacz tematy "Właściwości SQL", "Porównanie programu Microsoft Jet bazy danych aparatu SQL i ANSI SQL" i "Zapytań bazy danych za pomocą programu SQL w kod" w Pomocy programu DAO.

##  <a name="gettype"></a>  CDaoQueryDef::GetType

Wywołaj tę funkcję elementu członkowskiego, aby określić typ zapytania querydef.

```
short GetType();
```

### <a name="return-value"></a>Wartość zwracana

Typ kwerendy zdefiniowane przez querydef. W przypadku wartości zobacz uwagi.

### <a name="remarks"></a>Uwagi

Typ kwerendy jest ustawiana przez, jaki określono w parametrach SQL querydef podczas tworzenia obiektu querydef lub wywołać istniejących querydef [SetSQL](#setsql) funkcja elementu członkowskiego. Typ zapytania, zwrócona przez tę funkcję, może być jedną z następujących wartości:

- `dbQSelect` Wybierz pozycję

- `dbQAction` Akcja

- `dbQCrosstab` Krzyżowe

- `dbQDelete` Usuń

- `dbQUpdate` Aktualizacja

- `dbQAppend` Dołącz

- `dbQMakeTable` Tworzące tabelę

- `dbQDDL` Definicja danych

- `dbQSQLPassThrough` przekazywane

- `dbQSetOperation` Unia

- `dbQSPTBulk` Używane z `dbQSQLPassThrough` do określenia kwerendę, która nie zwraca rekordy.

> [!NOTE]
>  Aby utworzyć zapytania przekazującego SQL, nie należy ustawiać `dbSQLPassThrough` stałej. To jest ustawiana automatycznie przez aparat bazy danych Microsoft Jet podczas tworzenia obiektu querydef i ustawić parametrów połączenia.

Aby uzyskać informacji na temat ciągów SQL, zobacz [GetSQL](#getsql). Aby uzyskać informacji na temat typów zapytań, zobacz [Execute](#execute).

##  <a name="isopen"></a>  CDaoQueryDef::IsOpen

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy `CDaoQueryDef` obiektu jest obecnie otwarty.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość różną od zera `CDaoQueryDef` obiekt jest obecnie otwarty; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Querydef musi być w stanie otwarcia, zanim użyjesz go do wywoływania [Execute](#execute) lub utworzyć [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obiektu. Albo umieścić querydef do stanu rozwartego wywołania [Utwórz](#create) (w przypadku nowych querydef) lub [Otwórz](#open) (w przypadku istniejących querydef).

##  <a name="m_pdatabase"></a>  CDaoQueryDef::m_pDatabase

Zawiera wskaźnik do [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) obiekt skojarzony z obiektem querydef.

### <a name="remarks"></a>Uwagi

Jeśli potrzebujesz dostępu do bazy danych bezpośrednio za pomocą tego wskaźnika — na przykład, można uzyskać wskaźniki do innych querydef i zestawie rekordów obiekty w kolekcjach w bazie danych.

##  <a name="m_pdaoquerydef"></a>  CDaoQueryDef::m_pDAOQueryDef

Zawiera wskaźnik do interfejsu OLE dla obiektu źródłowego querydef DAO.

### <a name="remarks"></a>Uwagi

This, wskaźnik zapewnia kompletność oraz spójność z innych klas. Ponieważ zamiast pełni hermetyzuje querydefs — DAO MFC jest jednak prawdopodobnie nie będzie on potrzebny. Jeśli używasz, tym ostrożnie — w szczególności nie należy zmieniać wartość wskaźnika, jeśli nie masz pewności, co robią.

##  <a name="open"></a>  CDaoQueryDef::Open

Wywołaj tę funkcję elementu członkowskiego, aby otworzyć querydef wcześniej zapisanych w bazie danych querydefs — kolekcja.

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Ciąg, który zawiera nazwę zapisanego querydef, aby otworzyć. Możesz użyć [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Uwagi

Po otwarciu querydef może wywołać jej [Execute](#execute) funkcja elementu członkowskiego lub użyj querydef, aby utworzyć [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obiektu.

##  <a name="setconnect"></a>  CDaoQueryDef::SetConnect

Wywołaj tę funkcję elementu członkowskiego, aby ustawić parametry połączenia obiektu querydef.

```
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>Parametry

*lpszConnect*<br/>
Ciąg, który zawiera ciąg połączenia dla skojarzonego [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) obiektu.

### <a name="remarks"></a>Uwagi

Ciąg połączenia jest używany do przekazywania dodatkowych informacji do ODBC i sterownikami niektórych ISAM, zgodnie z potrzebami. Nie jest używany dla programu Microsoft Jet (. Bazy danych MDB).

> [!TIP]
>  Dołącz je do jest preferowany sposób pracy z tabel ODBC. MDB bazy danych.

Przed wykonaniem querydef, reprezentujący zapytania przekazującego SQL źródła danych ODBC, ustawimy parametry połączenia za pomocą `SetConnect` i wywołać [SetReturnsRecords](#setreturnsrecords) do określenia, czy kwerenda zwraca rekordy.

Aby uzyskać więcej informacji na temat struktury parametry połączenia i przykłady składników ciągów połączenia Zobacz temat "Connect Property" w Pomocy programu DAO.

##  <a name="setname"></a>  CDaoQueryDef::SetName

Wywołaj tę funkcję elementu członkowskiego, jeśli chcesz zmienić nazwę querydef, który nie jest tymczasowe.

```
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Ciąg, który zawiera nową nazwę dla nontemporary zapytania w skojarzonej [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) obiektu.

### <a name="remarks"></a>Uwagi

QueryDef nazwy są unikatowe, zdefiniowane przez użytkownika nazwy. Możesz wywołać `SetName` przed querydef obiektu jest dołączany do querydefs — kolekcja.

##  <a name="setodbctimeout"></a>  CDaoQueryDef::SetODBCTimeout

Wywołaj tę funkcję elementu członkowskiego, aby ustawić limit czasu, zanim upłynie limit czasu zapytania do źródła danych ODBC.

```
void SetODBCTimeout(short nODBCTimeout);
```

### <a name="parameters"></a>Parametry

*nODBCTimeout*<br/>
Liczba sekund przed zapytania upłynie limit czasu.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego umożliwia zastąpienie domyślnej liczby sekund przed kolejne operacje na połączonego źródła danych "mają limit czasu". Przekroczono limit czasu może być operacją, ze względu na problemy z dostępem do sieci, czasu przetwarzania zapytania nadmiernego i tak dalej. Wywołaj `SetODBCTimeout` przed wykonaniem kwerendy z tym querydef, jeśli chcesz zmienić wartość limitu czasu zapytania. (Zgodnie z ODBC ponownie używa połączenia, wartość limitu czasu jest taka sama dla wszystkich klientów w ramach tego samego połączenia).

Wartością domyślną dla zapytania przekroczeń limitu czasu wynosi 60 sekund.

##  <a name="setparamvalue"></a>  CDaoQueryDef::SetParamValue

Wywołaj tę funkcję elementu członkowskiego, aby ustawić wartości parametru w querydef w czasie wykonywania.

```
virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);


virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Nazwa parametru, której wartość chcesz ustawić.

*varValue*<br/>
Wartość do ustawienia; Zobacz uwagi.

*nIndex*<br/>
Numer porządkowy pozycja parametru w kolekcji parametrów querydef. Możesz uzyskać tę wartość przy użyciu wywołań [GetParameterCount](#getparametercount) i [getparameterinfo —](#getparameterinfo).

### <a name="remarks"></a>Uwagi

Parametr musi już zostały określone jako część ciągu SQL querydef. Według nazwy lub jego porządkowym w kolekcji, można uzyskać dostęp do parametru.

Określ wartość do ustawienia jako `COleVariant` obiektu. Informacje o ustawianiu na żądaną wartość i wpisz swoje `COleVariant` obiektów, zobacz klasę [COleVariant](../../mfc/reference/colevariant-class.md).

##  <a name="setreturnsrecords"></a>  CDaoQueryDef::SetReturnsRecords

Wywołaj tę funkcję elementu członkowskiego, w ramach procesu konfigurowania przekazywania zapytanie SQL do zewnętrznej bazy danych.

```
void SetReturnsRecords(BOOL bReturnsRecords);
```

### <a name="parameters"></a>Parametry

*bReturnsRecords*<br/>
Przekazać wartość TRUE, jeśli zapytanie w zewnętrznej bazy danych zwraca rekordy; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

W takim przypadku należy utworzyć querydef i ustaw jego właściwości, za pomocą innych `CDaoQueryDef` funkcji elementów członkowskich. Aby uzyskać opis zewnętrznych baz danych, zobacz [SetConnect](#setconnect).

##  <a name="setsql"></a>  CDaoQueryDef::SetSQL

Wywołaj tę funkcję elementu członkowskiego, aby ustawić instrukcji SQL, który jest wykonywany querydef.

```
void SetSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>Parametry

*lpszSQL*<br/>
Ciąg zawierający pełną instrukcję SQL, odpowiednie do wykonania. Składnia tego ciągu zależy od systemu DBMS, elementy docelowe zapytania. Omówienie składnią używaną w aparacie bazy danych Microsoft Jet zobacz temat "Tworzenie SQL instrukcji w Code" w Pomocy programu DAO.

### <a name="remarks"></a>Uwagi

Typowym zastosowaniem `SetSQL` jest skonfigurowanie obiektu querydef do użycia w zapytaniu SQL przekazywania. (Składnię przekazywanego zapytania SQL, na docelowy system DBMS, zobacz dokumentację dla systemu DBMS).

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)<br/>
[Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)<br/>
[Klasa CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)<br/>
[Klasa CDaoException](../../mfc/reference/cdaoexception-class.md)
