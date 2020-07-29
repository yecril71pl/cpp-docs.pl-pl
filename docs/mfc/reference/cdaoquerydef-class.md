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
ms.openlocfilehash: fabb8e957ffaf8ab8d9d57bca8e7835d366ac390
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231822"
---
# <a name="cdaoquerydef-class"></a>Klasa CDaoQueryDef

Reprezentuje definicję zapytania lub "querydef", zazwyczaj jeden zapisany w bazie danych.

## <a name="syntax"></a>Składnia

```
class CDaoQueryDef : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoQueryDef::CDaoQueryDef](#cdaoquerydef)|Konstruuje `CDaoQueryDef` obiekt. Następne wywołanie `Open` lub `Create` , w zależności od potrzeb.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoQueryDef:: Append](#append)|Dołącza obiekt querydef do kolekcji QueryDefs bazy danych jako zapisane zapytanie.|
|[CDaoQueryDef:: Update](#canupdate)|Zwraca wartość różną od zera, jeśli zapytanie może aktualizować bazę danych.|
|[CDaoQueryDef:: Close](#close)|Zamyka obiekt querydef. Zniszcz obiekt C++ po zakończeniu pracy z nim.|
|[CDaoQueryDef:: Create](#create)|Tworzy źródłowy obiekt DAO querydef. Użyj elementu querydef jako zapytania tymczasowego lub zadzwoń `Append` do zapisania go w bazie danych.|
|[CDaoQueryDef:: Execute](#execute)|Wykonuje zapytanie zdefiniowane przez obiekt querydef.|
|[CDaoQueryDef:: GetConnect](#getconnect)|Zwraca parametry połączenia skojarzone z elementem querydef. Parametry połączenia identyfikują źródło danych. (Dotyczy tylko zapytań przekazujących kod SQL; w przeciwnym razie jest to pusty ciąg).|
|[CDaoQueryDef::GetDateCreated](#getdatecreated)|Zwraca datę utworzenia zapisanego zapytania.|
|[CDaoQueryDef::GetDateLastUpdated](#getdatelastupdated)|Zwraca datę ostatniej aktualizacji zapisanego zapytania.|
|[CDaoQueryDef::GetFieldCount](#getfieldcount)|Zwraca liczbę pól zdefiniowanych przez querydef.|
|[CDaoQueryDef:: GetFieldInfo](#getfieldinfo)|Zwraca informacje dotyczące określonego pola zdefiniowanego w zapytaniu.|
|[CDaoQueryDef:: GetName](#getname)|Zwraca nazwę obiektu querydef.|
|[CDaoQueryDef::GetODBCTimeout](#getodbctimeout)|Zwraca wartość limitu czasu używaną przez ODBC (dla kwerendy ODBC), gdy obiekt querydef jest wykonywany. Pozwala to określić, jak długo ma być możliwe ukończenie akcji zapytania.|
|[CDaoQueryDef::GetParameterCount](#getparametercount)|Zwraca liczbę parametrów zdefiniowanych dla zapytania.|
|[CDaoQueryDef:: GetParameterInfo](#getparameterinfo)|Zwraca informacje o określonym parametrze do zapytania.|
|[CDaoQueryDef::GetParamValue](#getparamvalue)|Zwraca wartość określonego parametru do zapytania.|
|[CDaoQueryDef::GetRecordsAffected](#getrecordsaffected)|Zwraca liczbę rekordów, których dotyczy zapytanie akcji.|
|[CDaoQueryDef::GetReturnsRecords](#getreturnsrecords)|Zwraca wartość różną od zera, jeśli zapytanie zdefiniowane przez program querydef zwraca rekordy.|
|[CDaoQueryDef::GetSQL](#getsql)|Zwraca ciąg SQL, który określa zapytanie zdefiniowane przez querydef.|
|[CDaoQueryDef:: GetType](#gettype)|Zwraca typ zapytania: delete, Update, append, Make-Table i tak dalej.|
|[CDaoQueryDef:: IsOpen](#isopen)|Zwraca wartość różną od zera, jeśli jest otwarta i może zostać wykonana.|
|[CDaoQueryDef:: Open](#open)|Otwiera istniejący obiekt querydef przechowywany w kolekcji QueryDefs bazy danych.|
|[CDaoQueryDef:: SetConnect](#setconnect)|Ustawia parametry połączenia dla zapytania przekazującego SQL na źródle danych ODBC.|
|[CDaoQueryDef:: SetName](#setname)|Ustawia nazwę zapisanego zapytania, zastępując nazwę używaną podczas tworzenia obiektu querydef.|
|[CDaoQueryDef::SetODBCTimeout](#setodbctimeout)|Ustawia wartość limitu czasu używaną przez ODBC (dla kwerendy ODBC), gdy obiekt querydef jest wykonywany.|
|[CDaoQueryDef::SetParamValue](#setparamvalue)|Ustawia wartość określonego parametru do zapytania.|
|[CDaoQueryDef::SetReturnsRecords](#setreturnsrecords)|Określa, czy querydef zwraca rekordy. Ustawienie tego atrybutu na wartość TRUE jest prawidłowe tylko dla zapytań przekazujących SQL.|
|[CDaoQueryDef::SetSQL](#setsql)|Ustawia ciąg SQL, który określa zapytanie zdefiniowane przez querydef.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDaoQueryDef:: m_pDAOQueryDef](#m_pdaoquerydef)|Wskaźnik do interfejsu OLE dla bazowego obiektu DAO querydef.|
|[CDaoQueryDef:: m_pDatabase](#m_pdatabase)|Wskaźnik do obiektu, `CDaoDatabase` z którym jest skojarzona wartość querydef. Querydef może być zapisany w bazie danych programu.|

## <a name="remarks"></a>Uwagi

Querydef to obiekt dostępu do danych, który zawiera instrukcję SQL opisującą zapytanie i jego właściwości, takie jak "Data utworzenia" i "limit czasu ODBC". Można również tworzyć tymczasowe obiekty querydef bez zapisywania, ale jest to wygodne i bardziej wydajne — do zapisywania często ponownie używanych zapytań w bazie danych. Obiekt [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) przechowuje kolekcję o nazwie kolekcja obiektów, która zawiera zapisane w niej obiekty querydef.

> [!NOTE]
> Klasy bazy danych DAO różnią się od klas baz danych MFC opartych na Open Database Connectivity (ODBC). Wszystkie nazwy klas baz danych DAO mają prefiks "CDao". Nadal można uzyskać dostęp do źródeł danych ODBC przy użyciu klas DAO. Ogólnie rzecz biorąc, klasy MFC oparte na obiektach DAO są bardziej możliwością niż klasy MFC oparte na ODBC; klasy oparte na DAO mogą uzyskiwać dostęp do danych, w tym za pośrednictwem sterowników ODBC, za pośrednictwem własnego aparatu bazy danych. Klasy oparte na obiektach DAO obsługują również operacje języka definicji danych (DDL), takie jak Dodawanie tabel za pośrednictwem klas, bez konieczności bezpośredniego wywoływania obiektów DAO.

## <a name="usage"></a>Sposób użycia

Użyj obiektów querydef do pracy z istniejącym zapisanym zapytaniem lub w celu utworzenia nowego zapisanego zapytania lub zapytania tymczasowego:

1. We wszystkich przypadkach najpierw konstruuje `CDaoQueryDef` obiekt, dostarczając wskaźnik do obiektu [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) , do którego należy zapytanie.

1. Następnie wykonaj następujące czynności, w zależności od tego, co chcesz zrobić:

   - Aby użyć istniejącego zapisanego zapytania, wywołaj funkcję [otwierającego](#open) elementu członkowskiego obiektu querydef, podając nazwę zapisanego zapytania.

   - Aby utworzyć nowe zapisane zapytanie, wywołaj funkcję [tworzenia](#create) elementu członkowskiego obiektu querydef, podając nazwę zapytania. Następnie zadzwoń do [dołączenia](#append) , aby zapisać zapytanie przez dołączenie go do kolekcji QueryDefs bazy danych. `Create`umieszcza obiekt querydef w stanie otwartym, dlatego po wywołaniu `Create` nie jest wywoływana `Open` .

   - Aby utworzyć tymczasowy obiekt querydef, wywołaj `Create` . Przekaż pusty ciąg jako nazwę zapytania. Nie wywołuj `Append` .

Po zakończeniu korzystania z obiektu querydef należy wywołać jego funkcję [zamykającą](#close) . następnie Zniszcz obiekt querydef.

> [!TIP]
> Najprostszym sposobem tworzenia zapisanych zapytań jest ich utworzenie i zapisanie ich w bazie danych przy użyciu programu Microsoft Access. Następnie możesz otworzyć i używać ich w kodzie MFC.

## <a name="purposes"></a>Płatnicz

Obiektu querydef można użyć do dowolnego z następujących celów:

- Aby utworzyć `CDaoRecordset` obiekt

- Aby wywołać `Execute` funkcję członkowską obiektu do bezpośredniego wykonania zapytania akcji lub zapytania przekazującego SQL

Można użyć obiektu querydef dla dowolnego typu zapytania, w tym instrukcji SELECT, Action, krzyżowe, DELETE, Update, dołączania, tworzenia tabeli, definicji danych, przekazywania zapytania SQL, Unii i zapytań zbiorczych. Typ zapytania jest określany na podstawie zawartości instrukcji SQL dostarczonej przez użytkownika. Aby uzyskać informacje na temat typów zapytań, zobacz `Execute` i [GetType](#gettype) funkcje składowe. Zestawy rekordów są często używane dla zapytań zwracających wiersze, zazwyczaj przy użyciu **SELECT... Z** słów kluczowych. `Execute`jest najczęściej używany do operacji zbiorczych. Aby uzyskać więcej informacji, zobacz [Execute](#execute) and [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

## <a name="querydefs-and-recordsets"></a>QueryDefs i zestawy rekordów

Aby użyć obiektu querydef do utworzenia `CDaoRecordset` obiektu, zazwyczaj tworzysz lub otwierasz obiekt querydef zgodnie z powyższym opisem. Następnie Utwórz obiekt zestawu rekordów, przekazując wskaźnik do obiektu querydef podczas wywoływania [CDaoRecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open). Przekazany obiekt querydef musi znajdować się w stanie otwartym. Aby uzyskać więcej informacji, zobacz Klasa [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Nie można użyć obiektu querydef do utworzenia zestawu rekordów (najczęściej używany dla querydef), chyba że jest w stanie otwartym. Umieść parametr querydef w stanie otwartym przez wywołanie metody `Open` lub `Create` .

## <a name="external-databases"></a>Zewnętrzne bazy danych

Obiekty querydef są preferowanym sposobem korzystania z natywnego dialektu SQL zewnętrznego aparatu bazy danych. Można na przykład utworzyć zapytanie Transact SQL (używane na Microsoft SQL Server) i zapisać je w obiekcie querydef. Jeśli musisz użyć zapytania SQL, który nie jest oparty na aparacie bazy danych Microsoft Jet, musisz podać parametry połączenia wskazujące zewnętrzne źródło danych. Zapytania z prawidłowymi parametrami połączenia pomijają aparat bazy danych i przekazują zapytanie bezpośrednio do zewnętrznego serwera bazy danych w celu przetworzenia.

> [!TIP]
> Preferowanym sposobem pracy z tabelami ODBC jest dołączenie ich do aparatu Microsoft Jet (. MDB).

Aby uzyskać powiązane informacje, zobacz temat "QueryDef Object", "kolekcja zadań" i "CdbDatabase Object" w zestawie DAO SDK.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CDaoQueryDef`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao. h

## <a name="cdaoquerydefappend"></a><a name="append"></a>CDaoQueryDef:: Append

Wywołaj tę funkcję elementu członkowskiego po wywołaniu metody [Create](#create) , aby utworzyć nowy obiekt querydef.

```
virtual void Append();
```

### <a name="remarks"></a>Uwagi

`Append`zapisuje obiekt querydef w bazie danych przez dołączenie go do kolekcji QueryDefs bazy danych. Obiekt querydef można użyć jako obiektu tymczasowego bez dołączania go, ale jeśli chcesz, aby go utrwalał, musisz wywołać metodę `Append` .

Jeśli próbujesz dołączyć tymczasowy obiekt querydef, MFC zgłosi wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

## <a name="cdaoquerydefcanupdate"></a><a name="canupdate"></a>CDaoQueryDef:: Update

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy można modyfikować parametry querydef, takie jak zmiana jego nazwy lub ciągu SQL.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli masz uprawnienia do modyfikowania wartości querydef; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Można zmodyfikować:

- Nie jest on oparty na bazie danych, która jest otwarta tylko do odczytu.

- Masz uprawnienia do aktualizacji bazy danych.

   Jest to zależne od tego, czy zostały zaimplementowane funkcje zabezpieczeń. MFC nie zapewnia obsługi zabezpieczeń; należy zaimplementować go samodzielnie, wywołując obiekt DAO bezpośrednio lub przy użyciu programu Microsoft Access. Zapoznaj się z tematem "Właściwość uprawnienia" w pomocy DAO.

## <a name="cdaoquerydefcdaoquerydef"></a><a name="cdaoquerydef"></a>CDaoQueryDef::CDaoQueryDef

Konstruuje `CDaoQueryDef` obiekt.

```
CDaoQueryDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>Parametry

*pDatabase*<br/>
Wskaźnik do otwartego obiektu [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) .

### <a name="remarks"></a>Uwagi

Obiekt może reprezentować istniejącą wartość querydef przechowywaną w kolekcji QueryDefs bazy danych, nowe zapytanie, które ma być przechowywane w kolekcji lub tymczasowe zapytanie, które nie ma być przechowywane. Następny krok zależy od typu querydef:

- Jeśli obiekt reprezentuje istniejący obiekt querydef, wywołaj funkcję [otwierającego](#open) elementu członkowskiego obiektu, aby ją zainicjować.

- Jeśli obiekt reprezentuje nową querydef do zapisania, wywołaj funkcję [tworzenia](#create) elementu członkowskiego obiektu. Spowoduje to dodanie obiektu do kolekcji QueryDefs bazy danych. Następnie Wywołaj `CDaoQueryDef` funkcje członkowskie, aby ustawić atrybuty obiektu. Na koniec Wywołaj [dołączenie](#append).

- Jeśli obiekt reprezentuje tymczasowy element querydef (nie można zapisać w bazie danych), wywołaj `Create` , przekazując pusty ciąg jako nazwę zapytania. Po wywołaniu `Create` , zainicjuj metodę querydef, bezpośrednio ustawiając jej atrybuty. Nie wywołuj `Append` .

Aby ustawić atrybuty obiektu querydef, można użyć funkcji [SetName](#setname), [SetSQL](#setsql), [SetConnect](#setconnect), [SetODBCTimeout](#setodbctimeout)i [SetReturnsRecords](#setreturnsrecords) .

Po zakończeniu pracy z obiektem querydef należy wywołać jego funkcję [zamykającą](#close) . Jeśli masz wskaźnik do obiektu querydef, użyj **`delete`** operatora, aby zniszczyć obiekt C++.

## <a name="cdaoquerydefclose"></a><a name="close"></a>CDaoQueryDef:: Close

Wywołaj tę funkcję elementu członkowskiego po zakończeniu korzystania z obiektu querydef.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Zamknięcie interfejsu querydef powoduje zwolnienie bazowego obiektu DAO, ale nie niszczy zapisanego obiektu DAO querydef lub `CDaoQueryDef` obiektu C++. Ta wartość nie jest taka sama jak [CDaoDatabase::D eletequerydef](../../mfc/reference/cdaodatabase-class.md#deletequerydef), która usuwa obiekt querydef z kolekcji QueryDefs bazy danych w DAO (jeśli nie jest to tymczasowy obiekt querydef).

## <a name="cdaoquerydefcreate"></a><a name="create"></a>CDaoQueryDef:: Create

Wywołaj tę funkcję elementu członkowskiego, aby utworzyć nową zapisaną kwerendę lub nową tymczasową kwerendę.

```
virtual void Create(
    LPCTSTR lpszName = NULL,
    LPCTSTR lpszSQL = NULL);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Unikatowa nazwa zapytania zapisanego w bazie danych. Aby uzyskać szczegółowe informacje na temat ciągu, zobacz temat "Metoda". "w pomocy DAO. W przypadku zaakceptowania wartości domyślnej, pustego ciągu, zostanie utworzony tymczasowy obiekt querydef. Takie zapytanie nie jest zapisane w kolekcji QueryDefs.

*lpszSQL*<br/>
Ciąg SQL, który definiuje zapytanie. W przypadku zaakceptowania domyślnej wartości NULL należy później wywołać [SetSQL](#setsql) , aby ustawić ciąg. Do tego czasu zapytanie jest niezdefiniowane. Można jednak użyć niezdefiniowanego zapytania, aby otworzyć zestaw rekordów; Aby uzyskać szczegółowe informacje, zobacz uwagi. Instrukcja SQL musi być zdefiniowana, aby można było dołączyć do kolekcji QueryDefs.

### <a name="remarks"></a>Uwagi

W przypadku przekazania nazwy w *lpszName*można następnie wywołać [dołączenie](#append) w celu zapisania obiektu querydef w kolekcji QueryDefs bazy danych. W przeciwnym razie obiekt jest tymczasowy querydef i nie jest zapisywany. W obu przypadkach obiekt querydef jest w stanie otwartym i można go użyć do utworzenia obiektu [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) lub wywołania funkcji elementu członkowskiego [Execute](#execute) .

Jeśli nie podasz instrukcji SQL w *lpszSQL*, nie można uruchomić zapytania z, ale można `Execute` go użyć do utworzenia zestawu rekordów. W takim przypadku MFC używa domyślnej instrukcji SQL zestawu rekordów.

## <a name="cdaoquerydefexecute"></a><a name="execute"></a>CDaoQueryDef:: Execute

Wywołaj tę funkcję elementu członkowskiego, aby uruchomić zapytanie zdefiniowane przez obiekt querydef.

```
virtual void Execute(int nOptions = dbFailOnError);
```

### <a name="parameters"></a>Parametry

*nOptions*<br/>
Liczba całkowita, która określa charakterystykę zapytania. Aby uzyskać powiązane informacje, zobacz temat "Metoda Execute" w pomocy DAO. Można użyć operatora bitowego lub ( **&#124;**), aby połączyć następujące stałe dla tego argumentu:

- `dbDenyWrite`Odmów uprawnienia do zapisu innym użytkownikom.

- `dbInconsistent`Niespójne aktualizacje.

- `dbConsistent`Spójne aktualizacje.

- `dbSQLPassThrough`Przekazywanie SQL. Powoduje przekazanie instrukcji SQL do bazy danych ODBC w celu przetworzenia.

- `dbFailOnError`Wartość domyślna. Wycofaj aktualizacje w przypadku wystąpienia błędu i Zgłoś błąd użytkownikowi.

- `dbSeeChanges`Generuj błąd czasu wykonywania, jeśli inny użytkownik zmienia edytowane dane.

> [!NOTE]
> Aby uzyskać wyjaśnienie warunków "niespójne" i "spójne", zobacz temat "Metoda Execute" w pomocy DAO.

### <a name="remarks"></a>Uwagi

Obiekty querydef używane do wykonywania w ten sposób mogą reprezentować tylko jeden z następujących typów zapytań:

- Zapytania akcji

- Zapytania przekazujące SQL

`Execute`nie działa w przypadku zapytań, które zwracają rekordy, takich jak zapytania select. `Execute`jest często używany do wykonywania zapytań operacji zbiorczych, takich jak **Update**, **INSERT**lub **SELECT INTO**lub dla operacji języka definicji danych (DDL).

> [!TIP]
> Preferowanym sposobem pracy ze źródłami danych ODBC jest dołączenie tabel do programu Microsoft Jet (. MDB). Aby uzyskać więcej informacji, zobacz temat "Uzyskiwanie dostępu do zewnętrznych baz danych za pomocą DAO" w pomocy DAO.

Wywołaj funkcję członkowską [GetRecordsAffected](#getrecordsaffected) obiektu querydef, aby określić liczbę rekordów, których dotyczy ostatnie `Execute` wywołanie. Na przykład `GetRecordsAffected` zwraca informacje o liczbie rekordów usuniętych, zaktualizowanych lub wstawianych podczas wykonywania zapytania akcji. Zwracana liczba nie będzie odzwierciedlać zmian w powiązanych tabelach, gdy są włączone kaskadowe aktualizacje lub usunięcia.

Jeśli dołączysz oba elementy `dbInconsistent` i `dbConsistent` lub jeśli nie dołączysz żadnego z nich, wynik jest wartością domyślną `dbInconsistent` .

`Execute`nie zwraca zestawu rekordów. Użycie `Execute` w zapytaniu, które wybiera rekordy powoduje, że MFC zgłasza wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

## <a name="cdaoquerydefgetconnect"></a><a name="getconnect"></a>CDaoQueryDef:: GetConnect

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać parametry połączenia skojarzone ze źródłem danych querydef.

```
CString GetConnect();
```

### <a name="return-value"></a>Wartość zwracana

[CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierający parametry połączenia dla elementu querydef.

### <a name="remarks"></a>Uwagi

Ta funkcja jest używana tylko ze źródłami danych ODBC i określonymi sterownikami ISAM. Nie jest on używany z programem Microsoft Jet (. MDB) — bazy danych w tym przypadku `GetConnect` zwraca pusty ciąg. Aby uzyskać więcej informacji, zobacz [SetConnect](#setconnect).

> [!TIP]
> Preferowanym sposobem pracy z tabelami ODBC jest dołączenie ich do. Baza danych MDB. Aby uzyskać więcej informacji, zobacz temat "Uzyskiwanie dostępu do zewnętrznych baz danych za pomocą DAO" w pomocy DAO.

Aby uzyskać informacje na temat parametrów połączenia, zobacz temat "Connect Property" w pomocy DAO.

## <a name="cdaoquerydefgetdatecreated"></a><a name="getdatecreated"></a>CDaoQueryDef::GetDateCreated

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać datę utworzenia obiektu querydef.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) zawierający datę i godzinę utworzenia obiektu querydef.

### <a name="remarks"></a>Uwagi

Aby uzyskać powiązane informacje, zobacz temat "DateCreated, LastUpdated Properties" w pomocy DAO.

## <a name="cdaoquerydefgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDaoQueryDef::GetDateLastUpdated

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać datę ostatniej aktualizacji obiektu querydef — w przypadku zmiany jego właściwości, takich jak nazwa, ciąg SQL lub jego parametry połączenia.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) zawierający datę i godzinę ostatniej aktualizacji obiektu querydef.

### <a name="remarks"></a>Uwagi

Aby uzyskać powiązane informacje, zobacz temat "DateCreated, LastUpdated Properties" w pomocy DAO.

## <a name="cdaoquerydefgetfieldcount"></a><a name="getfieldcount"></a>CDaoQueryDef::GetFieldCount

Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę pól w zapytaniu.

```
short GetFieldCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba pól zdefiniowanych w zapytaniu.

### <a name="remarks"></a>Uwagi

`GetFieldCount`jest przydatne do zapętlania przez wszystkie pola w querydef. W tym celu należy użyć `GetFieldCount` w połączeniu z [GetFieldInfo](#getfieldinfo).

## <a name="cdaoquerydefgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoQueryDef:: GetFieldInfo

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać różne rodzaje informacji dotyczących pola zdefiniowanego w wywołaniu obiektu querydef.

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

*nIndex*<br/>
Indeks (liczony od zera) żądanego pola w kolekcji pól querydef dla wyszukiwania według indeksu.

*FieldInfo*<br/>
Odwołanie do `CDaoFieldInfo` obiektu, który zwraca żądane informacje.

*dwInfoOptions*<br/>
Opcje określające, które informacje o polu pobrać. Dostępne opcje są wymienione tutaj wraz z tym, co powodują, że funkcja zwraca:

- AFX_DAO_PRIMARY_INFO (domyślnie) nazwa, typ, rozmiar, atrybuty

- AFX_DAO_SECONDARY_INFO informacje podstawowe plus: pozycja porządkowa, wymagane, Zezwalaj na zerową długość, pole źródłowe, Nazwa obca, tabela źródłowa, porządek sortowania

- AFX_DAO_ALL_INFO informacje podstawowe i pomocnicze oraz: wartość domyślna, walidacja tekstu, reguła walidacji

*lpszName*<br/>
Ciąg zawierający nazwę żądanego pola, dla wyszukiwania według nazwy. Możesz użyć [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Uwagi

Aby uzyskać opis informacji zwracanych w elemencie *FieldInfo*, zobacz strukturę [CDaoFieldInfo —](../../mfc/reference/cdaofieldinfo-structure.md) . Ta struktura zawiera elementy członkowskie, które odpowiadają opisowym informacjom w obszarze *dwInfoOptions* powyżej. Jeśli zażądasz jednego poziomu informacji, uzyskasz również informacje o wcześniejszych poziomach.

## <a name="cdaoquerydefgetname"></a><a name="getname"></a>CDaoQueryDef:: GetName

Wywołaj tę funkcję elementu członkowskiego, aby pobrać nazwę zapytania reprezentowanego przez element querydef.

```
CString GetName();
```

### <a name="return-value"></a>Wartość zwracana

Nazwa zapytania.

### <a name="remarks"></a>Uwagi

Nazwy querydef są unikatowymi nazwami definiowanymi przez użytkownika. Aby uzyskać więcej informacji na temat nazw querydef, zobacz temat "name property" w pomocy DAO.

## <a name="cdaoquerydefgetodbctimeout"></a><a name="getodbctimeout"></a>CDaoQueryDef::GetODBCTimeout

Wywołaj tę funkcję elementu członkowskiego, aby pobrać bieżący limit czasu, zanim zapytanie do źródła danych ODBC przekroczy limit czasu.

```
short GetODBCTimeout();
```

### <a name="return-value"></a>Wartość zwracana

Liczba sekund przed upływem limitu czasu zapytania.

### <a name="remarks"></a>Uwagi

Aby uzyskać informacje o tym limicie czasu, zobacz temat "Właściwość ODBCTimeout" w pomocy DAO.

> [!TIP]
> Preferowanym sposobem pracy z tabelami ODBC jest dołączenie ich do aparatu Microsoft Jet (. MDB). Aby uzyskać więcej informacji, zobacz temat "Uzyskiwanie dostępu do zewnętrznych baz danych za pomocą DAO" w pomocy DAO.

## <a name="cdaoquerydefgetparametercount"></a><a name="getparametercount"></a>CDaoQueryDef::GetParameterCount

Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę parametrów w zapisanej kwerendzie.

```
short GetParameterCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba parametrów zdefiniowanych w zapytaniu.

### <a name="remarks"></a>Uwagi

`GetParameterCount`jest przydatne do zapętlania przez wszystkie parametry w querydef. W tym celu należy użyć `GetParameterCount` w połączeniu z [GetParameterInfo](#getparameterinfo).

Aby uzyskać powiązane informacje, zobacz tematy "obiekt parametrów", "Kolekcja parametrów" i "parametry deklaracji (SQL)" w pomocy DAO.

## <a name="cdaoquerydefgetparameterinfo"></a><a name="getparameterinfo"></a>CDaoQueryDef:: GetParameterInfo

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać informacje o parametrze zdefiniowanym w elemencie querydef.

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

*nIndex*<br/>
Indeks (liczony od zera) odpowiedniego parametru w kolekcji parametrów querydef dla wyszukiwania według indeksu.

*paraminfo*<br/>
Odwołanie do obiektu [CDaoParameterInfo —](../../mfc/reference/cdaoparameterinfo-structure.md) , który zwraca żądane informacje.

*dwInfoOptions*<br/>
Opcje określające informacje o parametrach do pobrania. Dostępna opcja jest wyświetlana w tym miejscu wraz z tym, co powoduje, że funkcja zwraca:

- Nazwa AFX_DAO_PRIMARY_INFO (domyślnie), typ

*lpszName*<br/>
Ciąg zawierający nazwę żądanego parametru dla wyszukiwania według nazwy. Możesz użyć [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Uwagi

Aby uzyskać opis informacji zwracanych w *ParamInfo*, zobacz [CDaoParameterInfo —](../../mfc/reference/cdaoparameterinfo-structure.md) Structure. Ta struktura zawiera elementy członkowskie, które odpowiadają opisowym informacjom w obszarze *dwInfoOptions* powyżej.

Aby uzyskać powiązane informacje, zobacz temat "parametry deklaracji (SQL)" w pomocy DAO.

## <a name="cdaoquerydefgetparamvalue"></a><a name="getparamvalue"></a>CDaoQueryDef::GetParamValue

Wywołaj tę funkcję elementu członkowskiego, aby pobrać bieżącą wartość określonego parametru przechowywanego w kolekcji parametrów obiektu querydef.

```
virtual COleVariant GetParamValue(LPCTSTR lpszName);
virtual COleVariant GetParamValue(int nIndex);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Nazwa parametru, którego wartość ma być wyszukiwana według nazwy.

*nIndex*<br/>
Liczony od zera indeks parametru w kolekcji parametrów querydef dla wyszukiwania według indeksu. Tę wartość można uzyskać za pomocą wywołań [GetParameterCount](#getparametercount) i [GetParameterInfo](#getparameterinfo).

### <a name="return-value"></a>Wartość zwracana

Obiekt klasy [COleVariant](../../mfc/reference/colevariant-class.md) , który zawiera wartość parametru.

### <a name="remarks"></a>Uwagi

Możesz uzyskać dostęp do parametru według nazwy lub według pozycji porządkowej w kolekcji.

Aby uzyskać powiązane informacje, zobacz temat "parametry deklaracji (SQL)" w pomocy DAO.

## <a name="cdaoquerydefgetrecordsaffected"></a><a name="getrecordsaffected"></a>CDaoQueryDef::GetRecordsAffected

Wywołaj tę funkcję elementu członkowskiego, aby określić liczbę rekordów, na które miało wpływ ostatnie wywołanie metody [Execute](#execute).

```
long GetRecordsAffected();
```

### <a name="return-value"></a>Wartość zwracana

Liczba rekordów, których to dotyczy.

### <a name="remarks"></a>Uwagi

Zwracana liczba nie będzie odzwierciedlać zmian w powiązanych tabelach, gdy są włączone kaskadowe aktualizacje lub usunięcia.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość RecordsAffected" w pomocy DAO.

## <a name="cdaoquerydefgetreturnsrecords"></a><a name="getreturnsrecords"></a>CDaoQueryDef::GetReturnsRecords

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy obiekt querydef jest oparty na zapytaniu zwracającym rekordy.

```
BOOL GetReturnsRecords();
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli obiekt querydef jest oparty na zapytaniu zwracającym rekordy; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest używana tylko w przypadku zapytań przekazujących SQL. Aby uzyskać więcej informacji na temat zapytań SQL, zobacz [wykonywanie](#execute) funkcji składowej. Aby uzyskać więcej informacji na temat pracy z kwerendami przekazującymi dane SQL, zobacz funkcja członkowska [SetReturnsRecords](#setreturnsrecords) .

Aby uzyskać powiązane informacje, zobacz temat "Właściwość ReturnsRecords" w pomocy DAO.

## <a name="cdaoquerydefgetsql"></a><a name="getsql"></a>CDaoQueryDef::GetSQL

Wywołaj tę funkcję elementu członkowskiego, aby pobrać instrukcję SQL, która definiuje zapytanie, na którym bazuje.

```
CString GetSQL();
```

### <a name="return-value"></a>Wartość zwracana

Instrukcja SQL definiująca zapytanie, na którym bazuje querydef.

### <a name="remarks"></a>Uwagi

Następnie prawdopodobnie przeanalizuje ciąg słów kluczowych, nazw tabel i tak dalej.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość SQL", "porównanie aparatu bazy danych Microsoft Jet SQL i ANSI SQL" oraz "wykonywanie zapytania względem bazy danych SQL w kodzie" w pomocy DAO.

## <a name="cdaoquerydefgettype"></a><a name="gettype"></a>CDaoQueryDef:: GetType

Wywołaj tę funkcję elementu członkowskiego, aby określić typ zapytania dla obiektu querydef.

```
short GetType();
```

### <a name="return-value"></a>Wartość zwracana

Typ zapytania zdefiniowany przez querydef. Aby uzyskać wartości, zobacz uwagi.

### <a name="remarks"></a>Uwagi

Typ zapytania jest ustawiany przez wartość określoną w ciągu SQL obiektu querydef podczas tworzenia obiektu querydef lub wywołaj funkcję członkowską [SetSQL](#setsql) istniejącej obiektu querydef. Typ zapytania zwracany przez tę funkcję może być jedną z następujących wartości:

- `dbQSelect`Zaznaczenia

- `dbQAction`Transakcji

- `dbQCrosstab`Krzyż

- `dbQDelete`Usunięty

- `dbQUpdate`Aktualizacji

- `dbQAppend`Łączono

- `dbQMakeTable`Utwórz tabelę

- `dbQDDL`Definicja danych

- `dbQSQLPassThrough`Przekazywanie

- `dbQSetOperation`Unii

- `dbQSPTBulk`Używany z programem w `dbQSQLPassThrough` celu określenia zapytania, które nie zwraca rekordów.

> [!NOTE]
> Aby utworzyć kwerendę przekazującą SQL, nie ustawiaj `dbSQLPassThrough` stałej. Ta wartość jest ustawiana automatycznie przez aparat bazy danych Microsoft Jet podczas tworzenia obiektu querydef i ustawiania parametrów połączenia.

Aby uzyskać informacje o ciągach SQL, zobacz [GetSQL](#getsql). Aby uzyskać informacje na temat typów zapytań, zobacz [Execute](#execute).

## <a name="cdaoquerydefisopen"></a><a name="isopen"></a>CDaoQueryDef:: IsOpen

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy `CDaoQueryDef` obiekt jest aktualnie otwarty.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli `CDaoQueryDef` obiekt jest aktualnie otwarty; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Obiekt querydef musi znajdować się w stanie otwartym przed użyciem go do wywołania [Execute](#execute) lub do utworzenia obiektu [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) . Aby umieścić obiekt querydef w wywołaniu w stanie otwartym, [Utwórz](#create) (dla nowego obiektu querydef) lub [Otwórz](#open) (dla istniejącego obiektu querydef).

## <a name="cdaoquerydefm_pdatabase"></a><a name="m_pdatabase"></a>CDaoQueryDef:: m_pDatabase

Zawiera wskaźnik do obiektu [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) skojarzonego z obiektem querydef.

### <a name="remarks"></a>Uwagi

Użyj tego wskaźnika, jeśli chcesz uzyskać bezpośredni dostęp do bazy danych — na przykład, aby uzyskać wskaźniki do innych obiektów querydef lub Recordset w kolekcjach baz danych.

## <a name="cdaoquerydefm_pdaoquerydef"></a><a name="m_pdaoquerydef"></a>CDaoQueryDef:: m_pDAOQueryDef

Zawiera wskaźnik do interfejsu OLE dla bazowego obiektu DAO querydef.

### <a name="remarks"></a>Uwagi

Ten wskaźnik zapewnia kompletność i spójność z innymi klasami. Jednak, ponieważ MFC nie pełni hermetyzowa obiektów DAO, prawdopodobnie nie będą potrzebne. W razie potrzeby należy zachować ostrożność — w szczególności nie należy zmieniać wartości wskaźnika, chyba że wiesz, co robisz.

## <a name="cdaoquerydefopen"></a><a name="open"></a>CDaoQueryDef:: Open

Wywołaj tę funkcję elementu członkowskiego, aby otworzyć obiekt querydef wcześniej zapisany w kolekcji QueryDefs bazy danych.

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Ciąg, który zawiera nazwę zapisanego obiektu querydef do otwarcia. Możesz użyć [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Uwagi

Gdy obiekt querydef jest otwarty, można [wywołać jego funkcję](#execute) elementu członkowskiego lub użyć obiektu querydef do tworzenia obiektów [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) .

## <a name="cdaoquerydefsetconnect"></a><a name="setconnect"></a>CDaoQueryDef:: SetConnect

Wywołaj tę funkcję elementu członkowskiego, aby ustawić parametry połączenia obiektu querydef.

```cpp
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>Parametry

*lpszConnect*<br/>
Ciąg zawierający parametry połączenia dla skojarzonego obiektu [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) .

### <a name="remarks"></a>Uwagi

Parametry połączenia służą do przekazywania dodatkowych informacji do ODBC i niektórych sterowników ISAM zgodnie z wymaganiami. Nie jest on używany w programie Microsoft Jet (. MDB).

> [!TIP]
> Preferowanym sposobem pracy z tabelami ODBC jest dołączenie ich do. Baza danych MDB.

Przed wykonaniem obiektu querydef reprezentującego kwerendę przekazujące SQL do źródła danych ODBC, należy ustawić parametry połączenia z `SetConnect` i wywołać [SetReturnsRecords](#setreturnsrecords) , aby określić, czy zapytanie zwraca rekordy.

Aby uzyskać więcej informacji o strukturze i przykładach parametrów połączenia, zobacz temat "Connect Property" w pomocy DAO.

## <a name="cdaoquerydefsetname"></a><a name="setname"></a>CDaoQueryDef:: SetName

Wywołaj tę funkcję elementu członkowskiego, jeśli chcesz zmienić nazwę obiektu querydef, która nie jest tymczasowa.

```cpp
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Ciąg, który zawiera nową nazwę dla nietymczasowego zapytania w skojarzonym obiekcie [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) .

### <a name="remarks"></a>Uwagi

Nazwy querydef są unikatowe, zdefiniowane przez użytkownika nazwy. Możesz wywołać `SetName` przed dołączeniem obiektu querydef do kolekcji QueryDefs.

## <a name="cdaoquerydefsetodbctimeout"></a><a name="setodbctimeout"></a>CDaoQueryDef::SetODBCTimeout

Wywołaj tę funkcję elementu członkowskiego, aby ustawić limit czasu, zanim zapytanie ze źródłem danych ODBC przekroczyło limit czasu.

```cpp
void SetODBCTimeout(short nODBCTimeout);
```

### <a name="parameters"></a>Parametry

*nODBCTimeout*<br/>
Liczba sekund przed upływem limitu czasu zapytania.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska pozwala zastąpić domyślną liczbę sekund przed upływem limitu czasu dla kolejnych operacji w połączonym źródle danych. Operacja może przekroczyć limit czasu, ponieważ występują problemy z dostępem do sieci, nadmierny czas przetwarzania zapytania i tak dalej. Wywołaj `SetODBCTimeout` przed wykonaniem zapytania przy użyciu tego elementu querydef, jeśli chcesz zmienić wartość limitu czasu zapytania. (Jako że ODBC ponownie używa połączeń, wartość limitu czasu jest taka sama dla wszystkich klientów w ramach tego samego połączenia).

Wartość domyślna dla limitów czasu zapytania to 60 sekund.

## <a name="cdaoquerydefsetparamvalue"></a><a name="setparamvalue"></a>CDaoQueryDef::SetParamValue

Wywołaj tę funkcję elementu członkowskiego, aby ustawić wartość parametru w wywołaniu obiektu querydef w czasie wykonywania.

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
Nazwa parametru, którego wartość ma zostać ustawiona.

*varValue*<br/>
Wartość do ustawienia; Zobacz uwagi.

*nIndex*<br/>
Pozycja porządkowa parametru w kolekcji parametrów querydef. Tę wartość można uzyskać za pomocą wywołań [GetParameterCount](#getparametercount) i [GetParameterInfo](#getparameterinfo).

### <a name="remarks"></a>Uwagi

Parametr musi już zostać ustanowiony jako część ciągu SQL obiektu querydef. Możesz uzyskać dostęp do parametru według nazwy lub według pozycji porządkowej w kolekcji.

Określ wartość, która ma zostać ustawiona jako `COleVariant` obiekt. Aby uzyskać informacje na temat ustawiania żądanej wartości i typu w `COleVariant` obiekcie, zobacz Klasa [COleVariant](../../mfc/reference/colevariant-class.md).

## <a name="cdaoquerydefsetreturnsrecords"></a><a name="setreturnsrecords"></a>CDaoQueryDef::SetReturnsRecords

Wywołaj tę funkcję elementu członkowskiego w ramach procesu konfigurowania zapytania przekazującego SQL do zewnętrznej bazy danych.

```cpp
void SetReturnsRecords(BOOL bReturnsRecords);
```

### <a name="parameters"></a>Parametry

*bReturnsRecords*<br/>
Należy przekazać wartość TRUE, jeśli zapytanie dotyczące zewnętrznej bazy danych zwraca rekordy; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

W takim przypadku należy utworzyć obiekt querydef i ustawić jego właściwości przy użyciu innych `CDaoQueryDef` funkcji Członkowskich. Aby uzyskać opis zewnętrznych baz danych, zobacz [SetConnect](#setconnect).

## <a name="cdaoquerydefsetsql"></a><a name="setsql"></a>CDaoQueryDef::SetSQL

Wywołaj tę funkcję elementu członkowskiego, aby ustawić instrukcję SQL, która jest wykonywana przez querydef.

```cpp
void SetSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>Parametry

*lpszSQL*<br/>
Ciąg zawierający kompletną instrukcję SQL, odpowiednią do wykonania. Składnia tego ciągu zależy od systemu DBMS, do którego odwołuje się zapytanie. Omówienie składni używanej w aparacie bazy danych Microsoft Jet można znaleźć w temacie "Kompilowanie instrukcji SQL w kodzie" w pomocy DAO.

### <a name="remarks"></a>Uwagi

Typowym zastosowaniem `SetSQL` jest skonfigurowanie obiektu querydef do użycia w zapytaniu przekazującym SQL. (Składnia zapytań przekazujących SQL w docelowym systemie DBMS znajduje się w dokumentacji systemu DBMS).

## <a name="see-also"></a>Zobacz także

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)<br/>
[Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)<br/>
[Klasa CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)<br/>
[Klasa CDaoException](../../mfc/reference/cdaoexception-class.md)
