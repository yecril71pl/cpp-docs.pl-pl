---
title: Klasa CDaoQueryDef
ms.date: 11/04/2016
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
ms.openlocfilehash: ed298c40daa9485683d0b989e47b97fdce9f6562
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754701"
---
# <a name="cdaoquerydef-class"></a>Klasa CDaoQueryDef

Reprezentuje definicję kwerendy lub "querydef", zwykle jeden zapisany w bazie danych.

## <a name="syntax"></a>Składnia

```
class CDaoQueryDef : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoQueryDef::CDaoQueryDef](#cdaoquerydef)|Konstruuje `CDaoQueryDef` obiekt. Następne `Open` połączenie `Create`lub , w zależności od potrzeb.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoQueryDef::Dołącz](#append)|Dołącza querydef do kolekcji QueryDefs bazy danych jako zapisane zapytanie.|
|[CDaoQueryDef::CanUpdate](#canupdate)|Zwraca wartość niezerową, jeśli kwerenda może zaktualizować bazę danych.|
|[CDaoQueryDef::Zamknij](#close)|Zamyka querydef obiektu. Zniszcz obiekt C++ po jego zakończeniu.|
|[CDaoQueryDef::Utwórz](#create)|Tworzy podstawowy obiekt dao querydef. Użyj querydef jako kwerendy tymczasowej lub wywołania, `Append` aby zapisać go w bazie danych.|
|[CDaoQueryDef::Wykonaj](#execute)|Wykonuje kwerendę zdefiniowaną przez obiekt querydef.|
|[CDaoQueryDef::GetConnect](#getconnect)|Zwraca ciąg połączenia skojarzony z querydef. Parametry połączenia identyfikują źródło danych. (Tylko dla zapytań przekazywania SQL; w przeciwnym razie pusty ciąg).|
|[CDaoQueryDef::GetDateTworzone](#getdatecreated)|Zwraca datę utworzenia zapisanej kwerendy.|
|[CDaoQueryDef::GetDateLastUpdated](#getdatelastupdated)|Zwraca datę ostatniej aktualizacji zapisanej kwerendy.|
|[CDaoQueryDef::GetFieldCount](#getfieldcount)|Zwraca liczbę pól zdefiniowanych przez querydef.|
|[CDaoQueryDef::GetFieldInfo](#getfieldinfo)|Zwraca informacje o określonym polu zdefiniowanym w kwerendzie.|
|[CDaoQueryDef::GetName](#getname)|Zwraca nazwę querydef.|
|[CDaoQueryDef::GetODBCTimeout](#getodbctimeout)|Zwraca wartość limitu czasu używaną przez ODBC (dla kwerendy ODBC) podczas wykonywania querydef. Określa to, jak długo można zezwolić na wykonanie akcji kwerendy.|
|[CDaoQueryDef::GetParameterCount](#getparametercount)|Zwraca liczbę parametrów zdefiniowanych dla kwerendy.|
|[CDaoQueryDef::GetParameterInfo](#getparameterinfo)|Zwraca do kwerendy informacje o określonym parametrze.|
|[CDaoQueryDef::GetParamValue](#getparamvalue)|Zwraca wartość określonego parametru do kwerendy.|
|[CDaoQueryDef::GetRecordsAffected](#getrecordsaffected)|Zwraca liczbę rekordów, których dotyczy kwerenda akcji.|
|[CDaoQueryDef::GetReturnsRecords](#getreturnsrecords)|Zwraca wartość niezerowa, jeśli kwerenda zdefiniowana przez querydef zwraca rekordy.|
|[CDaoQueryDef::GetSQL](#getsql)|Zwraca ciąg SQL, który określa kwerendę zdefiniowaną przez querydef.|
|[CDaoQueryDef::GetType](#gettype)|Zwraca typ kwerendy: usuń, aktualizuj, dołącz, make-table i tak dalej.|
|[CDaoQueryDef::IsOpen](#isopen)|Zwraca wartość niezerowa, jeśli querydef jest otwarty i może być wykonywany.|
|[CDaoQueryDef::Otwórz](#open)|Otwiera istniejącą querydef przechowywane w bazie danych QueryDefs kolekcji.|
|[CDaoQueryDef::SetConnect](#setconnect)|Ustawia ciąg połączenia dla zapytania przekazywania SQL w źródle danych ODBC.|
|[CDaoQueryDef::Nazwa zestawu](#setname)|Ustawia nazwę zapisanej kwerendy, zastępując nazwę używaną podczas tworzenia querydef.|
|[CDaoQueryDef::SetODBCTimeout](#setodbctimeout)|Ustawia wartość limitu czasu używane przez ODBC (dla kwerendy ODBC) podczas wykonywania querydef.|
|[CDaoQueryDef::SetParamValue](#setparamvalue)|Ustawia wartość określonego parametru na kwerendę.|
|[CDaoQueryDef::SetReturnsRecords](#setreturnsrecords)|Określa, czy querydef zwraca rekordy. Ustawienie tego atrybutu na WARTOŚĆ TRUE jest prawidłowe tylko dla zapytań przekazywania SQL.|
|[CDaoQueryDef::SetSQL](#setsql)|Ustawia ciąg SQL, który określa kwerendę zdefiniowaną przez querydef.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDaoQueryDef::m_pDAOQueryDef](#m_pdaoquerydef)|Wskaźnik do interfejsu OLE dla podstawowej dao querydef obiektu.|
|[CDaoQueryDef::m_pDatabase](#m_pdatabase)|Wskaźnik do `CDaoDatabase` obiektu, z którym querydef jest skojarzony. Querydef może być zapisany w bazie danych, czy nie.|

## <a name="remarks"></a>Uwagi

Querydef jest obiektem dostępu do danych, który zawiera instrukcję SQL opisującą kwerendę i jej właściwości, takie jak "Data created" i "TIMEout ODBC". Można również utworzyć tymczasowe querydef obiektów bez zapisywania ich, ale jest to wygodne — i znacznie bardziej wydajne — aby zapisać często ponownie używane kwerendy w bazie danych. Obiekt [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) przechowuje kolekcję o nazwie QueryDefs kolekcji, która zawiera jego zapisane querydefs.

> [!NOTE]
> Klasy bazy danych DAO różnią się od klas bazy danych MFC na podstawie łączności otwartej bazy danych (ODBC). Wszystkie nazwy klas bazy danych DAO mają prefiks "CDao". Nadal można uzyskać dostęp do źródeł danych ODBC z klasami DAO. Ogólnie rzecz biorąc klasy MFC oparte na DAO są bardziej zdolne niż klasy MFC oparte na ODBC; klasy oparte na DAO mogą uzyskiwać dostęp do danych, w tym za pośrednictwem sterowników ODBC, za pośrednictwem własnego aparatu bazy danych. Klasy oparte na DAO obsługują również operacje języka DDL (Data Definition Language), takie jak dodawanie tabel za pośrednictwem klas, bez konieczności bezpośredniego wywoływania DAO.

## <a name="usage"></a>Sposób użycia

Użyj querydef obiektów do pracy z istniejącą kwerendą zapisane lub utworzyć nową zapisaną kwerendę lub kwerendę tymczasową:

1. We wszystkich przypadkach najpierw `CDaoQueryDef` skonstruować obiekt, dostarczając wskaźnik do [obiektu CDaoDatabase,](../../mfc/reference/cdaodatabase-class.md) do którego należy kwerenda.

1. Następnie wykonaj następujące czynności, w zależności od tego, co chcesz:

   - Aby użyć istniejącej zapisanej kwerendy, należy wywołać funkcję elementu członkowskiego Open obiektu [querydef,](#open) podając nazwę zapisanej kwerendy.

   - Aby utworzyć nową zapisaną kwerendę, należy wywołać funkcję [utwórz](#create) element członkowski obiektu querydef, podając nazwę kwerendy. Następnie [wywołaj Dołącz,](#append) aby zapisać kwerendę, dołączając ją do kolekcji QueryDefs bazy danych. `Create`umieszcza querydef w stanie otwartym, `Create` więc po `Open`wywołaniu nie wywołać .

   - Aby utworzyć tymczasową kwerendę, należy wywołać . `Create` Przekaż pusty ciąg dla nazwy kwerendy. Nie dzwonić `Append`.

Po zakończeniu przy użyciu querydef obiektu, wywołać jego [Close](#close) funkcji elementu członkowskiego; następnie zniszczyć querydef obiektu.

> [!TIP]
> Najprostszym sposobem tworzenia zapisanych kwerend jest utworzenie ich i przechowywanie ich w bazie danych przy użyciu programu Microsoft Access. Następnie można otworzyć i używać ich w kodzie MFC.

## <a name="purposes"></a>Celów

Obiektu querydef można użyć dowolne z następujących celów:

- Aby utworzyć `CDaoRecordset` obiekt

- Aby wywołać funkcję `Execute` elementu członkowskiego obiektu, aby bezpośrednio wykonać kwerendę akcji lub kwerendę przekazywania SQL

Można użyć querydef obiektu dla dowolnego typu kwerendy, w tym wybierz, akcja, crosstab, delete, update, append, make-table, definicja danych, SQL pass-through, unii i zbiorczych kwerend. Typ kwerendy jest określana przez zawartość instrukcji SQL, która dostarczasz. Aby uzyskać informacje o `Execute` typach kwerend, zobacz funkcje członkowskie i [GetType.](#gettype) Zestawy rekordów są powszechnie używane dla kwerend zwracających wiersz, zwykle tych, które używają **SELECT ... OD** słów kluczowych. `Execute`jest najczęściej używany do operacji masowych. Aby uzyskać więcej informacji, zobacz [Wykonywanie](#execute) i [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

## <a name="querydefs-and-recordsets"></a>Querydefs i recordsets

Aby użyć querydef obiektu `CDaoRecordset` do utworzenia obiektu, zazwyczaj należy utworzyć lub otworzyć querydef jak opisano powyżej. Następnie skonstruuj obiekt zestawu rekordów, przekazując wskaźnik do obiektu querydef podczas wywoływania [zestawu CDaoRecordset::Open](../../mfc/reference/cdaorecordset-class.md#open). Querydef przekazać musi być w stanie otwartym. Aby uzyskać więcej informacji, zobacz klasę [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Nie można użyć querydef do utworzenia pliku recordset (najbardziej typowe zastosowanie dla querydef), chyba że jest w stanie otwartym. Umieść querydef w stanie otwartym, `Open` wywołując `Create`albo .

## <a name="external-databases"></a>Zewnętrzne bazy danych

Querydef obiekty są preferowanym sposobem korzystania z natywnego dialektu SQL zewnętrznego aparatu bazy danych. Na przykład można utworzyć kwerendę TRANSACT SQL (używaną w programie Microsoft SQL Server) i przechowywać ją w obiekcie querydef. Jeśli trzeba użyć kwerendy SQL nie na podstawie aparatu bazy danych Microsoft Jet, należy podać parametry połączenia, który wskazuje zewnętrzne źródło danych. Kwerendy z prawidłowymi ciągami połączeń pomijają aparat bazy danych i przekazują kwerendę bezpośrednio do zewnętrznego serwera bazy danych w celu przetworzenia.

> [!TIP]
> Preferowanym sposobem pracy z tabelami ODBC jest dołączenie ich do programu Microsoft Jet (. bazy danych MDB).

Aby uzyskać informacje pokrewne, zobacz tematy "QueryDef Object", "QueryDefs Collection" i "CdbDatabase Object" w SDK DAO.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CDaoQueryDef`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="cdaoquerydefappend"></a><a name="append"></a>CDaoQueryDef::Dołącz

Wywołanie tej funkcji elementu członkowskiego po [wywołaniu Create,](#create) aby utworzyć nowy querydef obiektu.

```
virtual void Append();
```

### <a name="remarks"></a>Uwagi

`Append`zapisuje querydef w bazie danych, dołączając obiekt do kolekcji QueryDefs bazy danych. Można użyć querydef jako obiektu tymczasowego bez dołączania go, ale jeśli chcesz, `Append`aby się upi, należy wywołać .

Jeśli spróbujesz dołączyć obiekt tymczasowego querydef, MFC zgłasza wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

## <a name="cdaoquerydefcanupdate"></a><a name="canupdate"></a>CDaoQueryDef::CanUpdate

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy można zmodyfikować querydef — takie jak zmiana jego nazwy lub ciągu SQL.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli masz prawo do modyfikowania querydef; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Można zmodyfikować querydef, jeśli:

- Nie jest on oparty na bazie danych, która jest otwarta tylko do odczytu.

- Masz uprawnienia do aktualizacji bazy danych.

   Zależy to od tego, czy zaimplementowano funkcje zabezpieczeń. MFC nie zapewnia obsługi zabezpieczeń; należy zaimplementować samodzielnie, wywołując DAO bezpośrednio lub za pomocą programu Microsoft Access. Zobacz temat "Właściwość uprawnień" w Pomocy DAO.

## <a name="cdaoquerydefcdaoquerydef"></a><a name="cdaoquerydef"></a>CDaoQueryDef::CDaoQueryDef

Konstruuje `CDaoQueryDef` obiekt.

```
CDaoQueryDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>Parametry

*pDatabase (baza danych)*<br/>
Wskaźnik do otwartego obiektu [CDaoDatabase.](../../mfc/reference/cdaodatabase-class.md)

### <a name="remarks"></a>Uwagi

Obiekt może reprezentować istniejącą querydef przechowywane w kolekcji QueryDefs bazy danych, nowe zapytanie, które mają być przechowywane w kolekcji lub kwerendy tymczasowej, nie mają być przechowywane. Następny krok zależy od typu querydef:

- Jeśli obiekt reprezentuje istniejącą querydef, wywołaj funkcję [otwórz](#open) element członkowski obiektu, aby ją zainicjować.

- Jeśli obiekt reprezentuje nowy querydef do zapisania, wywołać obiekt [Create](#create) funkcji elementu członkowskiego. Spowoduje to dodanie obiektu do kolekcji QueryDefs bazy danych. Następnie `CDaoQueryDef` wywołaj funkcje członkowskie, aby ustawić atrybuty obiektu. Na koniec zadzwoń [do aplikacji Dołącz](#append).

- Jeśli obiekt reprezentuje tymczasowe querydef (nie do zapisania `Create`w bazie danych), wywołanie , przekazywanie pusty ciąg dla nazwy kwerendy. Po `Create`wywołaniu , zainicjować querydef bezpośrednio ustawienie jego atrybuty. Nie dzwonić `Append`.

Aby ustawić atrybuty querydef, można użyć funkcji członkowskich [SetName](#setname), [SetSQL](#setsql), [SetConnect](#setconnect), [SetODBCTimeout](#setodbctimeout)i [SetReturnsRecords.](#setreturnsrecords)

Po zakończeniu z querydef obiektu, wywołać jego [Close](#close) funkcji elementu członkowskiego. Jeśli masz wskaźnik do querydef, użyj **delete** operator zniszczyć C++ obiektu.

## <a name="cdaoquerydefclose"></a><a name="close"></a>CDaoQueryDef::Zamknij

Wywołanie tej funkcji elementu członkowskiego po zakończeniu przy użyciu querydef obiektu.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Zamknięcie querydef zwalnia podstawowy obiekt DAO, ale nie niszczy zapisanego obiektu `CDaoQueryDef` DAO querydef lub obiektu C++. To nie jest taka sama jak [CDaoDatabase::DeleteQueryDef](../../mfc/reference/cdaodatabase-class.md#deletequerydef), który usuwa querydef z kolekcji QueryDefs bazy danych w DAO (jeśli nie tymczasowe querydef).

## <a name="cdaoquerydefcreate"></a><a name="create"></a>CDaoQueryDef::Utwórz

Wywołanie tej funkcji elementu członkowskiego, aby utworzyć nową zapisaną kwerendę lub nową kwerendę tymczasową.

```
virtual void Create(
    LPCTSTR lpszName = NULL,
    LPCTSTR lpszSQL = NULL);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
Unikatowa nazwa kwerendy zapisanej w bazie danych. Aby uzyskać szczegółowe informacje na temat ciągu, zobacz temat "CreateQueryDef Metoda" w Pomocy DAO. Jeśli zaakceptujesz wartość domyślną, zostanie utworzony pusty ciąg, zostanie utworzona tymczasowa funkcja querydef. Takie zapytanie nie jest zapisywane w kolekcji QueryDefs.

*Lpszsql*<br/>
Ciąg SQL definiujący kwerendę. Jeśli zaakceptujesz domyślną wartość NULL, musisz później wywołać [SetSQL,](#setsql) aby ustawić ciąg. Do tego czasu kwerenda jest niezdefiniowana. Niezdefiniowana kwerenda umożliwia jednak otwarcie kwerendy rekordowej; Zobacz Uwagi, aby uzyskać szczegółowe informacje. Instrukcja SQL musi być zdefiniowana, zanim będzie można dołączyć querydef do QueryDefs kolekcji.

### <a name="remarks"></a>Uwagi

Jeśli przekażesz nazwę w *lpszName*, można następnie wywołać [Dołącz,](#append) aby zapisać querydef w bazie danych QueryDefs kolekcji. W przeciwnym razie obiekt jest tymczasowy querydef i nie jest zapisywany. W obu przypadkach querydef jest w stanie otwartym i można go użyć do utworzenia obiektu [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) lub wywołania funkcji elementu członkowskiego [Execute](#execute) querydef.

Jeśli instrukcja SQL nie zostanie podają w *programie lpszSQL*, nie można uruchomić kwerendy, `Execute` ale można jej użyć do utworzenia zestawie rekordów. W takim przypadku MFC używa domyślnej instrukcji SQL zestawie rekordów.

## <a name="cdaoquerydefexecute"></a><a name="execute"></a>CDaoQueryDef::Wykonaj

Wywołanie tej funkcji elementu członkowskiego, aby uruchomić kwerendę zdefiniowaną przez querydef obiektu.

```
virtual void Execute(int nOptions = dbFailOnError);
```

### <a name="parameters"></a>Parametry

*nOpcje*<br/>
Liczba całkowita, która określa właściwości kwerendy. Aby uzyskać powiązane informacje, zobacz temat "Execute Method" w Pomocy DAO. Operator bitowy OR **(&#124;) **służy do łączenia następujących stałych dla tego argumentu:

- `dbDenyWrite`Odmów uprawnień do zapisu innym użytkownikom.

- `dbInconsistent`Niespójne aktualizacje.

- `dbConsistent`Spójne aktualizacje.

- `dbSQLPassThrough`Przekazywanie SQL. Powoduje, że instrukcja SQL mają być przekazywane do bazy danych ODBC do przetwarzania.

- `dbFailOnError`Wartość domyślna. Wycofywanie aktualizacji, jeśli wystąpi błąd i zgłosić błąd do użytkownika.

- `dbSeeChanges`Wygeneruj błąd czasu wykonywania, jeśli inny użytkownik zmienia edytowane dane.

> [!NOTE]
> Aby uzyskać wyjaśnienie terminów "niespójne" i "spójne", zobacz temat "Execute Method" w Pomocy DAO.

### <a name="remarks"></a>Uwagi

Querydef obiekty używane do wykonywania w ten sposób może reprezentować tylko jeden z następujących typów kwerend:

- Kwerendy akcji

- Zapytania przekazywania sql

`Execute`nie działa w przypadku kwerend zwracających rekordy, takich jak kwerendy wybierające. `Execute`jest powszechnie używany do zbiorczych zapytań operacyjnych, takich jak **UPDATE**, **INSERT**lub **SELECT INTO**, lub dla operacji języka definicji danych (DDL).

> [!TIP]
> Preferowanym sposobem pracy ze źródłami danych ODBC jest dołączenie tabel do programu Microsoft Jet (. bazy danych MDB). Aby uzyskać więcej informacji, zobacz temat "Uzyskiwanie dostępu do zewnętrznych baz danych z DAO" w Pomocy DAO.

Wywołanie funkcji elementu członkowskiego [GetRecordsAffected](#getrecordsaffected) obiektu querydef w celu określenia `Execute` liczby rekordów, których dotyczy ostatnie wywołanie. Na przykład `GetRecordsAffected` zwraca informacje o liczbie rekordów usuniętych, zaktualizowanych lub wstawionych podczas wykonywania kwerendy akcji. Zwrócona liczba nie będzie odzwierciedlać zmian w powiązanych tabelach, gdy aktualizacje kaskadowe lub usuwane są w mocy.

Jeśli dodasz `dbInconsistent` `dbConsistent` oba lub jeśli nie dodasz ani, `dbInconsistent`wynikiem jest domyślny, .

`Execute`nie zwraca pliku recordset. Użycie `Execute` w kwerendzie, która wybiera rekordy powoduje, że MFC zgłasza wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

## <a name="cdaoquerydefgetconnect"></a><a name="getconnect"></a>CDaoQueryDef::GetConnect

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać ciąg połączenia skojarzone ze źródłem danych querydef.Call this member function to get the connection string associated with the querydef's data source.

```
CString GetConnect();
```

### <a name="return-value"></a>Wartość zwracana

[CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierający ciąg połączenia dla querydef.

### <a name="remarks"></a>Uwagi

Ta funkcja jest używana tylko ze źródłami danych ODBC i niektórymi sterownikami ISAM. Nie jest używany z Microsoft Jet (. bazy danych MDB; w takim `GetConnect` przypadku zwraca pusty ciąg. Aby uzyskać więcej informacji, zobacz [SetConnect](#setconnect).

> [!TIP]
> Preferowanym sposobem pracy z tabelami ODBC jest dołączenie ich do pliku . baza danych MDB. Aby uzyskać więcej informacji, zobacz temat "Uzyskiwanie dostępu do zewnętrznych baz danych z DAO" w Pomocy DAO.

Aby uzyskać informacje na temat ciągów połączeń, zobacz temat "Połącz właściwość" w Pomocy DAO.

## <a name="cdaoquerydefgetdatecreated"></a><a name="getdatecreated"></a>CDaoQueryDef::GetDateTworzone

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać datę querydef obiekt został utworzony.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) zawierający datę i godzinę utworzenia querydef.

### <a name="remarks"></a>Uwagi

Aby uzyskać powiązane informacje, zobacz temat "DateCreated, LastUpdated Properties" w Pomocy DAO.

## <a name="cdaoquerydefgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDaoQueryDef::GetDateLastUpdated

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać datę querydef obiekt został ostatnio zaktualizowany — gdy którykolwiek z jego właściwości zostały zmienione, takie jak jego nazwa, jego ciąg SQL lub jego parametry połączenia.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Wartość zwracana

A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiekt zawierający datę i godzinę querydef został ostatnio zaktualizowany.

### <a name="remarks"></a>Uwagi

Aby uzyskać powiązane informacje, zobacz temat "DateCreated, LastUpdated Properties" w Pomocy DAO.

## <a name="cdaoquerydefgetfieldcount"></a><a name="getfieldcount"></a>CDaoQueryDef::GetFieldCount

Wywołanie tej funkcji elementu członkowskiego, aby pobrać liczbę pól w kwerendzie.

```
short GetFieldCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba pól zdefiniowanych w kwerendzie.

### <a name="remarks"></a>Uwagi

`GetFieldCount`jest przydatne do zapętlania wszystkich pól w querydef. W tym celu `GetFieldCount` należy używać w połączeniu z [GetFieldInfo](#getfieldinfo).

## <a name="cdaoquerydefgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoQueryDef::GetFieldInfo

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać różne rodzaje informacji o polu zdefiniowanym w querydef.

```cpp
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

*Nindex*<br/>
Indeks od zera żądanego pola w kolekcji Pola querydef, do wyszukiwania według indeksu.

*Fieldinfo*<br/>
Odwołanie do `CDaoFieldInfo` obiektu, który zwraca żądane informacje.

*dwInfoOptions (NpfoOptions)*<br/>
Opcje określające informacje o polu do pobrania. Dostępne opcje są wymienione tutaj wraz z tym, co powodują, że funkcja do powrotu:

- AFX_DAO_PRIMARY_INFO (domyślna) nazwa, typ, rozmiar, atrybuty

- AFX_DAO_SECONDARY_INFO informacje podstawowe plus: Pozycja porządkowa, Wymagane, Zezwalaj na długość zeru, Pole źródła, Nazwa obca, Tabela źródłowa, Kolejność sortowania

- AFX_DAO_ALL_INFO informacje podstawowe i pomocnicze plus: wartość domyślna, tekst sprawdzania poprawności, reguła sprawdzania poprawności

*Lpszname*<br/>
Ciąg zawierający nazwę żądanego pola, dla wyszukiwania według nazwy. Można użyć [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Uwagi

Aby uzyskać opis informacji zwróconych w *fieldinfo*, zobacz [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) struktury. Ta struktura ma elementy członkowskie, które odpowiadają opisowych informacji w *dwInfoOptions* powyżej. Jeśli poprosisz o jeden poziom informacji, otrzymasz również wcześniejsze poziomy informacji.

## <a name="cdaoquerydefgetname"></a><a name="getname"></a>CDaoQueryDef::GetName

Wywołanie tej funkcji elementu członkowskiego, aby pobrać nazwę kwerendy reprezentowanej przez querydef.

```
CString GetName();
```

### <a name="return-value"></a>Wartość zwracana

Nazwa kwerendy.

### <a name="remarks"></a>Uwagi

Nazwy querydef są unikatowymi nazwami zdefiniowanymi przez użytkownika. Aby uzyskać więcej informacji na temat nazw querydef, zobacz temat "Właściwość nazw" w Pomocy DAO.

## <a name="cdaoquerydefgetodbctimeout"></a><a name="getodbctimeout"></a>CDaoQueryDef::GetODBCTimeout

Wywołanie tej funkcji elementu członkowskiego, aby pobrać bieżący limit czasu przed kwerendą do źródła danych ODBC limit czasu.

```
short GetODBCTimeout();
```

### <a name="return-value"></a>Wartość zwracana

Liczba sekund przed przesuniem czasu kwerendy.

### <a name="remarks"></a>Uwagi

Aby uzyskać informacje na temat tego limitu czasu, zobacz temat "ODBCTimeout Property" w Pomocy DAO.

> [!TIP]
> Preferowanym sposobem pracy z tabelami ODBC jest dołączenie ich do programu Microsoft Jet (. bazy danych MDB). Aby uzyskać więcej informacji, zobacz temat "Uzyskiwanie dostępu do zewnętrznych baz danych z DAO" w Pomocy DAO.

## <a name="cdaoquerydefgetparametercount"></a><a name="getparametercount"></a>CDaoQueryDef::GetParameterCount

Wywołanie tej funkcji elementu członkowskiego, aby pobrać liczbę parametrów w zapisanej kwerendzie.

```
short GetParameterCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba parametrów zdefiniowanych w kwerendzie.

### <a name="remarks"></a>Uwagi

`GetParameterCount`jest przydatne do zapętlania wszystkich parametrów w querydef. W tym celu `GetParameterCount` należy używać w połączeniu z [GetParameterInfo](#getparameterinfo).

Aby uzyskać powiązane informacje, zobacz tematy "Obiekt parametrów", "Zbieranie parametrów" i "Deklaracja PARAMETRÓW (SQL)" w Pomocy DAO.

## <a name="cdaoquerydefgetparameterinfo"></a><a name="getparameterinfo"></a>CDaoQueryDef::GetParameterInfo

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać informacje o parametr zdefiniowany w querydef.

```cpp
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

*Nindex*<br/>
Indeks od zera żądanego parametru w querydef's Parameters kolekcji, dla wyszukiwania według indeksu.

*paraminfo*<br/>
Odwołanie do obiektu [CDaoParameterInfo,](../../mfc/reference/cdaoparameterinfo-structure.md) który zwraca żądane informacje.

*dwInfoOptions (NpfoOptions)*<br/>
Opcje określające informacje o parametrze do pobrania. Dostępna opcja jest wymieniona tutaj wraz z tym, co powoduje, że funkcja do powrotu:

- AFX_DAO_PRIMARY_INFO (domyślna) nazwa, typ

*Lpszname*<br/>
Ciąg zawierający nazwę żądanego parametru dla wyszukiwania według nazwy. Można użyć [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Uwagi

Opis informacji zwróconych w *paraminfo*można znaleźć w strukturze [CDaoParameterInfo.](../../mfc/reference/cdaoparameterinfo-structure.md) Ta struktura ma elementy członkowskie, które odpowiadają opisowych informacji w *dwInfoOptions* powyżej.

Aby uzyskać powiązane informacje, zobacz temat "Deklaracja PARAMETRÓW (SQL)" w Pomocy DAO.

## <a name="cdaoquerydefgetparamvalue"></a><a name="getparamvalue"></a>CDaoQueryDef::GetParamValue

Wywołanie tej funkcji elementu członkowskiego, aby pobrać bieżącą wartość określonego parametru przechowywane w querydef's Parameters kolekcji.

```
virtual COleVariant GetParamValue(LPCTSTR lpszName);
virtual COleVariant GetParamValue(int nIndex);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
Nazwa parametru, którego wartość ma być ciemieniem według nazwy.

*Nindex*<br/>
Indeks oparty na wartości zero parametru w kolekcji parametrów querydef, do wyszukiwania według indeksu. Tę wartość można uzyskać za pomocą wywołań [GetParameterCount](#getparametercount) i [GetParameterInfo](#getparameterinfo).

### <a name="return-value"></a>Wartość zwracana

Obiekt klasy [COleVariant,](../../mfc/reference/colevariant-class.md) który zawiera wartość parametru.

### <a name="remarks"></a>Uwagi

Można uzyskać dostęp do parametru według nazwy lub jego położenia porządkowego w kolekcji.

Aby uzyskać powiązane informacje, zobacz temat "Deklaracja PARAMETRÓW (SQL)" w Pomocy DAO.

## <a name="cdaoquerydefgetrecordsaffected"></a><a name="getrecordsaffected"></a>CDaoQueryDef::GetRecordsAffected

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, ile rekordów zostało dotkniętych przez ostatnie wywołanie [Execute](#execute).

```
long GetRecordsAffected();
```

### <a name="return-value"></a>Wartość zwracana

Liczba rekordów, których to dotyczy.

### <a name="remarks"></a>Uwagi

Zwrócona liczba nie będzie odzwierciedlać zmian w powiązanych tabelach, gdy aktualizacje kaskadowe lub usuwane są w mocy.

Aby uzyskać powiązane informacje, zobacz temat "RecordsAffected Property" w Pomocy DAO.

## <a name="cdaoquerydefgetreturnsrecords"></a><a name="getreturnsrecords"></a>CDaoQueryDef::GetReturnsRecords

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy querydef jest oparty na kwerendzie, która zwraca rekordy.

```
BOOL GetReturnsRecords();
```

### <a name="return-value"></a>Wartość zwracana

Wartość niezerowa, jeśli querydef jest oparta na kwerendzie, która zwraca rekordy; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest używana tylko dla zapytań przekazywania SQL. Aby uzyskać więcej informacji na temat zapytań SQL, zobacz [Funkcję Wykonywania](#execute) elementu członkowskiego. Aby uzyskać więcej informacji na temat pracy z zapytaniami przekazywania SQL, zobacz [SetReturnsRecords funkcji członkowskiej.](#setreturnsrecords)

Aby uzyskać powiązane informacje, zobacz temat "Właściwość ReturnsRecords" w Pomocy DAO.

## <a name="cdaoquerydefgetsql"></a><a name="getsql"></a>CDaoQueryDef::GetSQL

Wywołanie tej funkcji elementu członkowskiego, aby pobrać instrukcję SQL, która definiuje kwerendę, na której jest oparta funkcja querydef.

```
CString GetSQL();
```

### <a name="return-value"></a>Wartość zwracana

Instrukcja SQL, która definiuje kwerendę, na której opiera się querydef.

### <a name="remarks"></a>Uwagi

Następnie prawdopodobnie będziesz analizować ciąg słów kluczowych, nazw tabel i tak dalej.

Aby uzyskać informacje pokrewne, zobacz tematy "Właściwość SQL", "Porównanie sql i SQL ANSI SQL aparatu bazy danych firmy Microsoft Jet" i "Zapytanie bazy danych z sql w kodzie" w Pomocy DAO.

## <a name="cdaoquerydefgettype"></a><a name="gettype"></a>CDaoQueryDef::GetType

Wywołanie tej funkcji elementu członkowskiego, aby określić typ kwerendy querydef.

```
short GetType();
```

### <a name="return-value"></a>Wartość zwracana

Typ kwerendy zdefiniowanej przez querydef. Wartości można znaleźć w polu Uwagi.

### <a name="remarks"></a>Uwagi

Typ kwerendy jest ustawiany przez to, co można określić w querydef's SQL string podczas tworzenia querydef lub wywołać istniejącą [querydef's SetSQL](#setsql) funkcji elementu członkowskiego. Typ kwerendy zwracany przez tę funkcję może być jedną z następujących wartości:

- `dbQSelect`Wybierz

- `dbQAction`Działania

- `dbQCrosstab`Krzyżowej

- `dbQDelete`Usunąć

- `dbQUpdate`Aktualizacji

- `dbQAppend`Dołączyć

- `dbQMakeTable`Stół do wykonania

- `dbQDDL`Definicja danych

- `dbQSQLPassThrough`Przekazujące

- `dbQSetOperation`Unii

- `dbQSPTBulk`Używane `dbQSQLPassThrough` do określania kwerendy, która nie zwraca rekordów.

> [!NOTE]
> Aby utworzyć kwerendę przekazową SQL, nie `dbSQLPassThrough` należy ustawiać stałej. Jest to ustawiane automatycznie przez aparat bazy danych Microsoft Jet podczas tworzenia obiektu querydef i ustawiania ciągu połączenia.

Aby uzyskać informacje o ciągach SQL, zobacz [GetSQL](#getsql). Aby uzyskać informacje o typach kwerend, zobacz [Wykonywanie](#execute).

## <a name="cdaoquerydefisopen"></a><a name="isopen"></a>CDaoQueryDef::IsOpen

Wywołanie tej funkcji elementu `CDaoQueryDef` członkowskiego, aby ustalić, czy obiekt jest aktualnie otwarty.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, `CDaoQueryDef` jeśli obiekt jest aktualnie otwarty; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Querydef musi być w stanie otwartym, zanim użyjesz go do wywołania [Execute](#execute) lub do utworzenia obiektu [CDaoRecordset.](../../mfc/reference/cdaorecordset-class.md) Aby umieścić querydef do wywołania stanu otwartego albo [Create](#create) (dla nowego querydef) lub [Open](#open) (dla istniejącego querydef).

## <a name="cdaoquerydefm_pdatabase"></a><a name="m_pdatabase"></a>CDaoQueryDef::m_pDatabase

Zawiera wskaźnik do obiektu [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) skojarzonego z obiektem querydef.

### <a name="remarks"></a>Uwagi

Ten wskaźnik służy do bezpośredniego dostępu do bazy danych — na przykład, aby uzyskać wskaźniki do innych querydef lub recordset obiektów w kolekcji bazy danych.

## <a name="cdaoquerydefm_pdaoquerydef"></a><a name="m_pdaoquerydef"></a>CDaoQueryDef::m_pDAOQueryDef

Zawiera wskaźnik do interfejsu OLE dla podstawowego obiektu dao querydef.

### <a name="remarks"></a>Uwagi

Ten wskaźnik jest przewidziany dla kompletności i spójności z innymi klasami. Jednak ponieważ MFC raczej w pełni hermetyzuje dao querydefs, jest mało prawdopodobne, aby go potrzebować. Jeśli go używasz, zrób to ostrożnie — w szczególności nie zmieniaj wartości wskaźnika, chyba że wiesz, co robisz.

## <a name="cdaoquerydefopen"></a><a name="open"></a>CDaoQueryDef::Otwórz

Wywołanie tej funkcji elementu członkowskiego, aby otworzyć querydef wcześniej zapisane w bazie danych QueryDefs kolekcji.

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
Ciąg zawierający nazwę zapisanego querydef do otwarcia. Można użyć [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Uwagi

Po otwarciu querydef można wywołać jego [execute](#execute) funkcji elementu członkowskiego lub użyć querydef do [utworzenia obiektu CDaoRecordset.](../../mfc/reference/cdaorecordset-class.md)

## <a name="cdaoquerydefsetconnect"></a><a name="setconnect"></a>CDaoQueryDef::SetConnect

Wywołanie tej funkcji elementu członkowskiego, aby ustawić ciąg połączenia querydef obiektu.

```cpp
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>Parametry

*lpszConnect*<br/>
Ciąg zawierający parametry połączenia dla skojarzonego obiektu [CDaoDatabase.](../../mfc/reference/cdaodatabase-class.md)

### <a name="remarks"></a>Uwagi

Parametry połączenia są używane do przekazywania dodatkowych informacji do odbc i niektórych sterowników ISAM w razie potrzeby. Nie jest używany dla Microsoft Jet (. bazy danych MDB).

> [!TIP]
> Preferowanym sposobem pracy z tabelami ODBC jest dołączenie ich do pliku . baza danych MDB.

Przed wykonaniem querydef, który reprezentuje sql pass-through kwerendy do źródła `SetConnect` danych ODBC, ustawić ciąg połączenia z [SetReturnsRecords,](#setreturnsrecords) aby określić, czy kwerenda zwraca rekordy.

Aby uzyskać więcej informacji na temat struktury ciągu połączenia i przykładów składników ciągu połączenia, zobacz temat "Połącz właściwość" w Pomocy DAO.

## <a name="cdaoquerydefsetname"></a><a name="setname"></a>CDaoQueryDef::Nazwa zestawu

Wywołanie tej funkcji elementu członkowskiego, jeśli chcesz zmienić nazwę querydef, który nie jest tymczasowy.

```cpp
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
Ciąg zawierający nową nazwę kwerendy nietemporarycznej w skojarzonym obiekcie [CDaoDatabase.](../../mfc/reference/cdaodatabase-class.md)

### <a name="remarks"></a>Uwagi

Nazwy querydef są unikatowymi nazwami zdefiniowanymi przez użytkownika. Można wywołać `SetName` przed querydef obiekt jest dołączany do QueryDefs kolekcji.

## <a name="cdaoquerydefsetodbctimeout"></a><a name="setodbctimeout"></a>CDaoQueryDef::SetODBCTimeout

Wywołanie tej funkcji elementu członkowskiego, aby ustawić limit czasu przed kwerendą do źródła danych ODBC limit czasu.

```cpp
void SetODBCTimeout(short nODBCTimeout);
```

### <a name="parameters"></a>Parametry

*NODBCCzasout*<br/>
Liczba sekund przed przesuniem czasu kwerendy.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego umożliwia zastąpienie domyślnej liczby sekund przed kolejnymi operacjami na połączonym źródle danych "limit czasu". Operacja może się przeterminować z powodu problemów z dostępem do sieci, nadmiernego czasu przetwarzania zapytań i tak dalej. Wywołanie `SetODBCTimeout` przed wykonaniem kwerendy z tym querydef, jeśli chcesz zmienić wartość limitu czasu kwerendy. (Gdy ODBC ponownie używa połączeń, wartość limitu czasu jest taka sama dla wszystkich klientów korzystających z tego samego połączenia).

Domyślna wartość limitów czasu kwerendy wynosi 60 sekund.

## <a name="cdaoquerydefsetparamvalue"></a><a name="setparamvalue"></a>CDaoQueryDef::SetParamValue

Wywołanie tej funkcji elementu członkowskiego, aby ustawić wartość parametru w querydef w czasie wykonywania.

```
virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);

virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
Nazwa parametru, którego wartość ma zostać ustawiona.

*wartość varValue*<br/>
Wartość do ustawionego; patrz Uwagi.

*Nindex*<br/>
Położenie porządkowe parametru w querydef's Parameters collection. Tę wartość można uzyskać za pomocą wywołań [GetParameterCount](#getparametercount) i [GetParameterInfo](#getparameterinfo).

### <a name="remarks"></a>Uwagi

Parametr musi już zostały ustanowione jako część querydef's SQL string. Można uzyskać dostęp do parametru według nazwy lub jego położenia porządkowego w kolekcji.

Określ wartość ustawioną `COleVariant` jako obiekt. Aby uzyskać informacje na temat ustawiania żądanej wartości i typu w obiekcie, `COleVariant` zobacz klasa [COleVariant](../../mfc/reference/colevariant-class.md).

## <a name="cdaoquerydefsetreturnsrecords"></a><a name="setreturnsrecords"></a>CDaoQueryDef::SetReturnsRecords

Wywołanie tej funkcji elementu członkowskiego w ramach procesu konfigurowania kwerendy przekazywania SQL do zewnętrznej bazy danych.

```cpp
void SetReturnsRecords(BOOL bReturnsRecords);
```

### <a name="parameters"></a>Parametry

*bReturnsRecords*<br/>
Przekaż wartość TRUE, jeśli kwerenda w zewnętrznej bazie danych zwraca rekordy; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

W takim przypadku należy utworzyć querydef i ustawić jego `CDaoQueryDef` właściwości przy użyciu innych funkcji członkowskich. Aby uzyskać opis zewnętrznych baz danych, zobacz [SetConnect](#setconnect).

## <a name="cdaoquerydefsetsql"></a><a name="setsql"></a>CDaoQueryDef::SetSQL

Wywołanie tej funkcji elementu członkowskiego, aby ustawić instrukcję SQL, która wykonuje querydef.

```cpp
void SetSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>Parametry

*Lpszsql*<br/>
Ciąg zawierający pełną instrukcję SQL, odpowiedni do wykonania. Składnia tego ciągu zależy od dbms, że zapytanie docelowych. Aby zapoznać się ze składnią używaną w silniku bazy danych Microsoft Jet, zobacz temat "Tworzenie instrukcji SQL w kodzie" w Pomocy DAO.

### <a name="remarks"></a>Uwagi

Typowym zastosowaniem `SetSQL` jest konfigurowanie querydef obiektu do użycia w kwerendzie przekazywania SQL. (Aby uzyskać składnię zapytań przekazywania SQL na docelowym dbms, zobacz dokumentację dla dbms.)

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)<br/>
[Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)<br/>
[Klasa CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)<br/>
[Klasa CDaoException](../../mfc/reference/cdaoexception-class.md)
