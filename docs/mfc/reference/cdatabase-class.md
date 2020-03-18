---
title: Klasa CDatabase
ms.date: 11/04/2016
f1_keywords:
- CDatabase
- AFXDB/CDatabase
- AFXDB/CDatabase::CDatabase
- AFXDB/CDatabase::BeginTrans
- AFXDB/CDatabase::BindParameters
- AFXDB/CDatabase::Cancel
- AFXDB/CDatabase::CanTransact
- AFXDB/CDatabase::CanUpdate
- AFXDB/CDatabase::Close
- AFXDB/CDatabase::CommitTrans
- AFXDB/CDatabase::ExecuteSQL
- AFXDB/CDatabase::GetBookmarkPersistence
- AFXDB/CDatabase::GetConnect
- AFXDB/CDatabase::GetCursorCommitBehavior
- AFXDB/CDatabase::GetCursorRollbackBehavior
- AFXDB/CDatabase::GetDatabaseName
- AFXDB/CDatabase::IsOpen
- AFXDB/CDatabase::OnSetOptions
- AFXDB/CDatabase::Open
- AFXDB/CDatabase::OpenEx
- AFXDB/CDatabase::Rollback
- AFXDB/CDatabase::SetLoginTimeout
- AFXDB/CDatabase::SetQueryTimeout
- AFXDB/CDatabase::m_hdbc
helpviewer_keywords:
- CDatabase [MFC], CDatabase
- CDatabase [MFC], BeginTrans
- CDatabase [MFC], BindParameters
- CDatabase [MFC], Cancel
- CDatabase [MFC], CanTransact
- CDatabase [MFC], CanUpdate
- CDatabase [MFC], Close
- CDatabase [MFC], CommitTrans
- CDatabase [MFC], ExecuteSQL
- CDatabase [MFC], GetBookmarkPersistence
- CDatabase [MFC], GetConnect
- CDatabase [MFC], GetCursorCommitBehavior
- CDatabase [MFC], GetCursorRollbackBehavior
- CDatabase [MFC], GetDatabaseName
- CDatabase [MFC], IsOpen
- CDatabase [MFC], OnSetOptions
- CDatabase [MFC], Open
- CDatabase [MFC], OpenEx
- CDatabase [MFC], Rollback
- CDatabase [MFC], SetLoginTimeout
- CDatabase [MFC], SetQueryTimeout
- CDatabase [MFC], m_hdbc
ms.assetid: bd0de70a-e3c3-4441-bcaa-bbf434426ca8
ms.openlocfilehash: ebc36d82af9bfe12ab30a86214e58610b5eaab95
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418756"
---
# <a name="cdatabase-class"></a>Klasa CDatabase

Reprezentuje połączenie ze źródłem danych, za pomocą którego można pracować na źródle danych.

## <a name="syntax"></a>Składnia

```
class CDatabase : public CObject
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CDatabase:: CDatabase](#cdatabase)|Konstruuje obiekt `CDatabase`. Należy zainicjować obiekt, wywołując `OpenEx` lub `Open`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CDatabase:: BeginTrans](#begintrans)|Uruchamia "transakcję" — szereg wywołań odwracalnych do `AddNew`, `Edit`, `Delete`i `Update` funkcji członkowskich klasy `CRecordset` — w połączonym źródle danych. Źródło danych musi obsługiwać transakcje `BeginTrans`, aby mieć efekt.|
|[CDatabase:: BindParameters](#bindparameters)|Pozwala powiązać parametry przed wywołaniem `CDatabase::ExecuteSQL`.|
|[CDatabase:: Cancel](#cancel)|Anuluje operację asynchroniczną lub proces z drugiego wątku.|
|[CDatabase:: gettransact](#cantransact)|Zwraca wartość różną od zera, jeśli źródło danych obsługuje transakcje.|
|[CDatabase:: Update](#canupdate)|Zwraca wartość różną od zera, jeśli obiekt `CDatabase` jest aktualizowalny (nie tylko do odczytu).|
|[CDatabase:: Close](#close)|Zamyka połączenie ze źródłem danych.|
|[CDatabase:: CommitTrans](#committrans)|Kończy transakcję rozpoczętą przez `BeginTrans`. Polecenia w transakcji, które zmieniają źródło danych, są wykonywane.|
|[CDatabase:: ExecuteSql by](#executesql)|Wykonuje instrukcję języka SQL. Żadne rekordy danych nie są zwracane.|
|[CDatabase:: GetBookmarkPersistence](#getbookmarkpersistence)|Identyfikuje operacje, za pomocą których zakładki są utrwalane na obiektach zestawu rekordów.|
|[CDatabase:: GetConnect](#getconnect)|Zwraca parametry połączenia ODBC używane do łączenia obiektu `CDatabase` ze źródłem danych.|
|[CDatabase:: GetCursorCommitBehavior](#getcursorcommitbehavior)|Określa efekt zatwierdzania transakcji w otwartym obiekcie zestawu rekordów.|
|[CDatabase:: GetCursorRollbackBehavior](#getcursorrollbackbehavior)|Określa efekt wycofania transakcji na otwartym obiekcie zestawu rekordów.|
|[CDatabase:: GetDatabaseName](#getdatabasename)|Zwraca nazwę aktualnie używanej bazy danych.|
|[CDatabase:: IsOpen](#isopen)|Zwraca wartość różną od zera, jeśli obiekt `CDatabase` jest obecnie połączony ze źródłem danych.|
|[CDatabase:: onoptions](#onsetoptions)|Wywoływane przez platformę, by ustawić standardowe opcje połączenia. Domyślna implementacja ustawia wartość limitu czasu zapytania. Możesz później ustalić te opcje, wywołując `SetQueryTimeout`.|
|[CDatabase:: Open](#open)|Nawiązuje połączenie ze źródłem danych (za pośrednictwem sterownika ODBC).|
|[CDatabase:: OpenEx](#openex)|Nawiązuje połączenie ze źródłem danych (za pośrednictwem sterownika ODBC).|
|[CDatabase:: Rollback](#rollback)|Odwraca zmiany wprowadzone w bieżącej transakcji. Źródło danych powraca do poprzedniego stanu, zgodnie z definicją w wywołaniu `BeginTrans`, bez zmian.|
|[CDatabase:: SetLoginTimeout](#setlogintimeout)|Ustawia liczbę sekund, po upływie których zostanie przekroczony limit czasu próby połączenia ze źródłem danych.|
|[CDatabase:: SetQueryTimeout](#setquerytimeout)|Ustawia liczbę sekund, po upływie których limit czasu operacji zapytania bazy danych zostanie przekroczony. Wpływa na wszystkie kolejne `Open`zestawu rekordów, `AddNew`, `Edit`i wywołań `Delete`.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CDatabase:: m_hdbc](#m_hdbc)|Open Database Connectivity (ODBC) dojście połączenia do źródła danych. Wpisz *HDBC*.|

## <a name="remarks"></a>Uwagi

Źródło danych jest określonym wystąpieniem danych hostowanym przez jakiś system zarządzania bazami danych (DBMS). Przykładami mogą być Microsoft SQL Server, Microsoft Access, Borland dBASE i xBASE. W aplikacji możesz jednocześnie korzystać z co najmniej jednego obiektu `CDatabase`.

> [!NOTE]
>  Jeśli pracujesz z klasami obiektów dostępu do danych (DAO), a nie klasami Open Database Connectivity (ODBC), zamiast tego użyj klasy [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) . Aby uzyskać więcej informacji, zobacz [Omówienie artykułu: Programowanie baz danych](../../data/data-access-programming-mfc-atl.md).

Aby użyć `CDatabase`, Utwórz obiekt `CDatabase` i Wywołaj `OpenEx` funkcję członkowską. Spowoduje to otwarcie połączenia. Po utworzeniu `CRecordset` obiektów do działania w połączonym źródle danych, należy przekazać Konstruktor zestawu rekordów wskaźnik do obiektu `CDatabase`. Po zakończeniu korzystania z połączenia wywołaj funkcję członkowską `Close` i zniszcz obiekt `CDatabase`. `Close` zamyka wszystkie zestawy rekordów, które nie zostały wcześniej zamknięte.

Aby uzyskać więcej informacji na temat `CDatabase`, zobacz artykuł [Data Source (ODBC)](../../data/odbc/data-source-odbc.md) i [Omówienie: Programowanie baz danych](../../data/data-access-programming-mfc-atl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CDatabase`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDB. h

##  <a name="begintrans"></a>CDatabase:: BeginTrans

Wywołaj tę funkcję elementu członkowskiego, aby rozpocząć transakcję z połączonym źródłem danych.

```
BOOL BeginTrans();
```

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli wywołanie zakończyło się pomyślnie, a zmiany są zatwierdzane tylko ręcznie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Transakcja składa się z jednego lub większej liczby wywołań funkcji Członkowskich `AddNew`, `Edit`, `Delete`i `Update` obiektu `CRecordset`. Przed rozpoczęciem transakcji, obiekt `CDatabase` musi już być połączony ze źródłem danych, wywołując jego `OpenEx` lub `Open` funkcję członkowską. Aby zakończyć transakcję, wywołaj [CommitTrans](#committrans) , aby zaakceptować wszystkie zmiany w źródle danych (i przenieść je), lub wywołaj funkcję [wycofywania](#rollback) , aby przerwać całą transakcję. Wywołaj `BeginTrans` po otwarciu dowolnego zestawu rekordów związanego z transakcją i jak najbliżej rzeczywistych operacji aktualizowania, jak to możliwe.

> [!CAUTION]
>  W zależności od sterownika ODBC, otwierając zestaw rekordów przed wywołaniem `BeginTrans` może spowodować problemy podczas wywoływania `Rollback`. Należy sprawdzić konkretny używany sterownik. Na przykład w przypadku korzystania z sterownika Microsoft Access Driver zawartego w pakiecie Microsoft ODBC Desktop Driver Pack 3,0 należy uwzględnić wymaganie aparatu bazy danych Jet, że nie należy rozpoczynać transakcji w żadnej bazie danych, która ma otwarty kursor. W klasach baz danych MFC otwarty kursor oznacza otwarty `CRecordset` obiektu. Aby uzyskać więcej informacji, zobacz [Uwagi techniczne 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md).

`BeginTrans` mogą również blokować rekordy danych na serwerze, w zależności od żądanych współbieżności i możliwości źródła danych. Informacje o blokowaniu danych znajdują się w artykule [zestaw rekordów: blokowanie rekordów (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).

Transakcje zdefiniowane przez użytkownika są wyjaśnione w artykule [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).

`BeginTrans` ustala stan, do którego można wycofać sekwencję transakcji (odwrócony). Aby ustanowić nowy stan wycofywania, Zatwierdź każdą bieżącą transakcję, a następnie Wywołaj `BeginTrans` ponownie.

> [!CAUTION]
>  Wywołanie `BeginTrans` ponownie bez wywoływania `CommitTrans` lub `Rollback` jest błędem.

Wywołaj [funkcję DataMember elementu](#cantransact) Członkowskiego, aby określić, czy sterownik obsługuje transakcje dla danej bazy danych. Należy również wywołać [GetCursorCommitBehavior](#getcursorcommitbehavior) i [GetCursorRollbackBehavior](#getcursorrollbackbehavior) , aby określić obsługę zachowywania kursora.

Aby uzyskać więcej informacji na temat transakcji, zobacz artykuł [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Przykład

  Zobacz artykuł [transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="bindparameters"></a>CDatabase:: BindParameters

Przesłoń `BindParameters`, gdy musisz powiązać parametry przed wywołaniem [CDatabase:: ExecuteSql by](#executesql).

```
virtual void BindParameters(HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*hstmt*<br/>
Dojście instrukcji ODBC, dla którego chcesz powiązać parametry.

### <a name="remarks"></a>Uwagi

Takie podejście jest przydatne, gdy nie potrzebujesz zestawu wyników z procedury składowanej.

W zastąpieniu Wywołaj `SQLBindParameters` i powiązane funkcje ODBC, aby powiązać parametry. MFC wywołuje przesłonięcie przed wywołaniem `ExecuteSQL`. Nie ma potrzeby wywoływania `SQLPrepare`; `ExecuteSQL` wywołuje `SQLExecDirect` i niszczy *HSTMT*, który jest używany tylko raz.

##  <a name="cancel"></a>CDatabase:: Cancel

Wywołaj tę funkcję elementu członkowskiego, aby zażądać, aby źródło danych anulował operację asynchroniczną w toku lub proces z drugiego wątku.

```
void Cancel();
```

### <a name="remarks"></a>Uwagi

Należy pamiętać, że klasy MFC ODBC nie są już używane do przetwarzania asynchronicznego; Aby wykonać operację asynchroniczną, należy bezpośrednio wywołać funkcję ODBC API [SQLSetConnectOption](/sql/odbc/reference/syntax/sqlsetconnectoption-function). Aby uzyskać więcej informacji, zobacz [wykonywanie asynchroniczne](/sql/odbc/reference/develop-app/asynchronous-execution).

##  <a name="cantransact"></a>CDatabase:: gettransact

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy baza danych zezwala na transakcje.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli zestawy rekordów używające tego obiektu `CDatabase` zezwalają na transakcje; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać informacje o transakcjach, zobacz artykuł [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="canupdate"></a>CDatabase:: Update

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy obiekt `CDatabase` zezwala na aktualizacje.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli obiekt `CDatabase` zezwala na aktualizacje; w przeciwnym razie, wskazujące, że wartość TRUE w *bReadOnly* została przeniesiona, gdy otwarto obiekt `CDatabase` lub samo źródło danych jest tylko do odczytu. Źródło danych jest tylko do odczytu, jeśli wywołanie funkcji interfejsu API ODBC `SQLGetInfo` dla SQL_DATASOURCE_READ_ONLY zwraca wartość "y".

### <a name="remarks"></a>Uwagi

Nie wszystkie sterowniki obsługują aktualizacje.

##  <a name="cdatabase"></a>CDatabase:: CDatabase

Konstruuje obiekt `CDatabase`.

```
CDatabase();
```

### <a name="remarks"></a>Uwagi

Po utworzeniu obiektu należy wywołać jego `OpenEx` lub `Open` funkcję członkowską, aby nawiązać połączenie z określonym źródłem danych.

Przydatne może być osadzenie obiektu `CDatabase` w klasie dokumentu.

### <a name="example"></a>Przykład

Ten przykład ilustruje użycie `CDatabase` w klasie pochodnej `CDocument`.

[!code-cpp[NVC_MFCDatabase#9](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]

[!code-cpp[NVC_MFCDatabase#10](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]

##  <a name="close"></a>CDatabase:: Close

Wywołaj tę funkcję elementu członkowskiego, jeśli chcesz rozłączyć się ze źródłem danych.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Przed wywołaniem tej funkcji elementu członkowskiego należy zamknąć wszystkie zestawy rekordów skojarzone z obiektem `CDatabase`. Ponieważ `Close` nie niszczy obiektu `CDatabase`, można ponownie użyć tego obiektu, otwierając nowe połączenie z tym samym źródłem danych lub innym źródłem danych.

Wszystkie oczekujące instrukcje `AddNew` lub `Edit` zestawów rekordów używające bazy danych są anulowane i wszystkie oczekujące transakcje zostaną wycofane. Wszystkie zestawy rekordów zależne od obiektu `CDatabase` są pozostawione w niezdefiniowanym stanie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#12](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]

##  <a name="committrans"></a>CDatabase:: CommitTrans

Wywołaj tę funkcję elementu członkowskiego po wykonaniu transakcji.

```
BOOL CommitTrans();
```

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli aktualizacje zostały pomyślnie zatwierdzone; w przeciwnym razie 0. Jeśli `CommitTrans` nie powiedzie się, stan źródła danych jest niezdefiniowany. Należy sprawdzić dane, aby ustalić ich stan.

### <a name="remarks"></a>Uwagi

Transakcja składa się z serii wywołań `AddNew`, `Edit`, `Delete`i `Update` funkcji członkowskich obiektu `CRecordset`, który rozpoczął wywołanie funkcji składowej [BeginTrans](#begintrans) . `CommitTrans` zatwierdza transakcję. Domyślnie aktualizacje są zatwierdzane natychmiast; Wywołanie `BeginTrans` powoduje, że zobowiązania aktualizacji są opóźnione do momentu wywołania `CommitTrans`.

Do momentu wywołania `CommitTrans`, aby zakończyć transakcję, można wywołać funkcję [wycofywania](#rollback) elementu członkowskiego, aby przerwać transakcję i pozostawić źródło danych w pierwotnym stanie. Aby rozpocząć nową transakcję, wywołaj `BeginTrans` ponownie.

Aby uzyskać więcej informacji na temat transakcji, zobacz artykuł [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Przykład

  Zobacz artykuł [transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="executesql"></a>CDatabase:: ExecuteSql by

Wywołaj tę funkcję elementu członkowskiego, gdy musisz bezpośrednio wykonać polecenie SQL.

```
void ExecuteSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>Parametry

*lpszSQL*<br/>
Wskaźnik na ciąg zakończony znakiem null zawierający prawidłowe polecenie SQL do wykonania. Można przekazać [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Uwagi

Utwórz polecenie jako ciąg zakończony znakiem null. `ExecuteSQL` nie zwraca rekordów danych. Jeśli chcesz korzystać z rekordów, zamiast tego użyj obiektu zestawu rekordów.

Większość poleceń dla źródła danych jest emitowanych za pomocą obiektów zestawu rekordów, które obsługują polecenia umożliwiające Zaznaczanie danych, wstawianie nowych rekordów, usuwanie rekordów i edytowanie rekordów. Jednak nie wszystkie funkcje ODBC są bezpośrednio obsługiwane przez klasy baz danych, więc czasami trzeba wykonać bezpośrednie wywołanie SQL z `ExecuteSQL`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#13](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]

##  <a name="getbookmarkpersistence"></a>CDatabase:: GetBookmarkPersistence

Wywołaj tę funkcję elementu członkowskiego, aby określić trwałość zakładek w obiekcie zestawu rekordów po pewnych operacjach.

```
DWORD GetBookmarkPersistence() const;
```

### <a name="return-value"></a>Wartość zwrócona

Maska bitów, która identyfikuje operacje, za pomocą których zakładki są utrwalane na obiekcie zestawu rekordów. Aby uzyskać szczegółowe informacje, zobacz uwagi.

### <a name="remarks"></a>Uwagi

Na przykład jeśli wywołasz `CRecordset::GetBookmark`, a następnie wywołajesz `CRecordset::Requery`, zakładka uzyskana z `GetBookmark` może już być nieprawidłowa. Przed wywołaniem `CRecordset::SetBookmark`należy wywołać `GetBookmarkPersistence`.

W poniższej tabeli wymieniono wartości masek bitowych, które mogą być łączone dla wartości zwracanej `GetBookmarkPersistence`.

|Wartość maski bitowej|Trwałość zakładki|
|-------------------|--------------------------|
|SQL_BP_CLOSE|Zakładki są prawidłowe po operacji `Requery`.|
|SQL_BP_DELETE|Zakładka dla wiersza jest ważna po operacji `Delete` w tym wierszu.|
|SQL_BP_DROP|Zakładki są prawidłowe po operacji `Close`.|
|SQL_BP_SCROLL|Zakładki są prawidłowe po każdej operacji `Move`. Jest to po prostu określenie, czy zakładki są obsługiwane w zestawie rekordów, co zostało zwrócone przez `CRecordset::CanBookmark`.|
|SQL_BP_TRANSACTION|Zakładki są ważne po zatwierdzeniu transakcji lub wycofaniu jej z powrotem.|
|SQL_BP_UPDATE|Zakładka dla wiersza jest ważna po operacji `Update` w tym wierszu.|
|SQL_BP_OTHER_HSTMT|Zakładki skojarzone z jednym obiektem zestawu rekordów są prawidłowe dla drugiego zestawu rekordów.|

Aby uzyskać więcej informacji na temat tej wartości zwracanej, zobacz funkcja interfejsu API ODBC `SQLGetInfo` w Windows SDK. Aby uzyskać więcej informacji na temat zakładek, zobacz [zestaw rekordów artykułów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

##  <a name="getconnect"></a>CDatabase:: GetConnect

Wywołaj tę funkcję elementu członkowskiego, aby pobrać parametry połączenia używane podczas wywołania do `OpenEx` lub `Open`, które połączyły obiekt `CDatabase` ze źródłem danych.

```
const CString GetConnect() const;
```

### <a name="return-value"></a>Wartość zwrócona

**Stała**[CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierająca parametry połączenia w przypadku wywołania `OpenEx` lub `Open`. w przeciwnym razie pusty ciąg.

### <a name="remarks"></a>Uwagi

Zobacz [CDatabase:: Open](#open) , aby uzyskać opis sposobu tworzenia parametrów połączenia.

##  <a name="getcursorcommitbehavior"></a>CDatabase:: GetCursorCommitBehavior

Wywołaj tę funkcję elementu członkowskiego, aby określić, w jaki sposób operacja [CommitTrans](#committrans) ma wpływ na kursory dla otwartych obiektów zestawu rekordów.

```
int GetCursorCommitBehavior() const;
```

### <a name="return-value"></a>Wartość zwrócona

Wartość wskazująca wpływ transakcji na otwarte obiekty zestawu rekordów. Aby uzyskać szczegółowe informacje, zobacz uwagi.

### <a name="remarks"></a>Uwagi

Poniższa tabela zawiera listę możliwych wartości zwracanych dla `GetCursorCommitBehavior` i odpowiadający jej efekt w otwartym zestawie rekordów.

|Wartość zwracana|Wpływ na obiekty CRecordset|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Wywołaj `CRecordset::Requery` natychmiast po zatwierdzeniu transakcji.|
|SQL_CB_DELETE|Wywołaj `CRecordset::Close` natychmiast po zatwierdzeniu transakcji.|
|SQL_CB_PRESERVE|Kontynuuj normalne działanie za pomocą `CRecordset` operacji.|

Aby uzyskać więcej informacji na temat tej wartości zwracanej, zobacz funkcja interfejsu API ODBC `SQLGetInfo` w Windows SDK. Aby uzyskać więcej informacji na temat transakcji, zobacz artykuł [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="getcursorrollbackbehavior"></a>CDatabase:: GetCursorRollbackBehavior

Wywołaj tę funkcję elementu członkowskiego, aby określić, jak operacja [wycofywania](#rollback) wpływa na kursory w otwartych obiektach zestawu rekordów.

```
int GetCursorRollbackBehavior() const;
```

### <a name="return-value"></a>Wartość zwrócona

Wartość wskazująca wpływ transakcji na otwarte obiekty zestawu rekordów. Aby uzyskać szczegółowe informacje, zobacz uwagi.

### <a name="remarks"></a>Uwagi

Poniższa tabela zawiera listę możliwych wartości zwracanych dla `GetCursorRollbackBehavior` i odpowiadający jej efekt w otwartym zestawie rekordów.

|Wartość zwracana|Wpływ na obiekty CRecordset|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Wywołaj `CRecordset::Requery` natychmiast po wycofaniu transakcji.|
|SQL_CB_DELETE|Wywołaj `CRecordset::Close` natychmiast po wycofaniu transakcji.|
|SQL_CB_PRESERVE|Kontynuuj normalne działanie za pomocą `CRecordset` operacji.|

Aby uzyskać więcej informacji na temat tej wartości zwracanej, zobacz funkcja interfejsu API ODBC `SQLGetInfo` w Windows SDK. Aby uzyskać więcej informacji na temat transakcji, zobacz artykuł [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="getdatabasename"></a>CDatabase:: GetDatabaseName

Wywołaj tę funkcję elementu członkowskiego, aby pobrać nazwę aktualnie połączonej bazy danych (pod warunkiem, że źródło danych definiuje nazwany obiekt o nazwie "Database").

```
CString GetDatabaseName() const;
```

### <a name="return-value"></a>Wartość zwrócona

Element [CString](../../atl-mfc-shared/reference/cstringt-class.md) , który zawiera nazwę bazy danych, jeśli się powiedzie; w przeciwnym razie puste `CString`.

### <a name="remarks"></a>Uwagi

Ta wartość nie jest taka sama jak nazwa źródła danych (DSN) określona w wywołaniu `OpenEx` lub `Open`. Jakie `GetDatabaseName` zwraca zależy od ODBC. Ogólnie rzecz biorąc, baza danych jest kolekcją tabel. Jeśli ta jednostka ma nazwę, `GetDatabaseName` zwraca ją.

Możesz na przykład wyświetlić tę nazwę w nagłówku. Jeśli wystąpi błąd podczas pobierania nazwy z ODBC, `GetDatabaseName` zwraca pusty `CString`.

##  <a name="isopen"></a>CDatabase:: IsOpen

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy obiekt `CDatabase` jest obecnie połączony ze źródłem danych.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli obiekt `CDatabase` jest aktualnie połączony; w przeciwnym razie 0.

##  <a name="m_hdbc"></a>CDatabase:: m_hdbc

Zawiera publiczny uchwyt połączenia ze źródłem danych ODBC — "dojście połączenia".

### <a name="remarks"></a>Uwagi

Zwykle nie będzie trzeba bezpośrednio uzyskiwać dostępu do tej zmiennej członkowskiej. Zamiast tego, struktura przydziela dojście podczas wywoływania `OpenEx` lub `Open`. Struktura derezerwuje uchwyt po wywołaniu operatora **delete** w obiekcie `CDatabase`. Należy zauważyć, że funkcja członkowska `Close` nie cofa alokacji dojścia.

Jednak w pewnych okolicznościach może być konieczne bezpośrednie użycie uchwytu. Na przykład, jeśli musisz wywołać funkcje interfejsu API ODBC bezpośrednio, a nie za pośrednictwem klasy `CDatabase`, może być konieczne dojście połączenia do przekazania jako parametr. Zobacz Poniższy przykład kodu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#15](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]

##  <a name="onsetoptions"></a>CDatabase:: onoptions

Struktura wywołuje tę funkcję członkowską podczas bezpośredniego wykonywania instrukcji SQL za pomocą funkcji składowej `ExecuteSQL`.

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*hstmt*<br/>
Dojście instrukcji ODBC, dla którego są ustawiane opcje.

### <a name="remarks"></a>Uwagi

`CRecordset::OnSetOptions` również wywołuje tę funkcję członkowską.

`OnSetOptions` ustawia wartość limitu czasu logowania. Jeśli wcześniej zostały wywołania do `SetQueryTimeout` i funkcji członkowskiej, `OnSetOptions` odzwierciedlają bieżące wartości; w przeciwnym razie ustawia wartości domyślne.

> [!NOTE]
>  Przed MFC 4,2, `OnSetOptions` również ustawić tryb przetwarzania na snychronous lub asynchroniczny. Począwszy od MFC 4,2, wszystkie operacje są synchroniczne. Aby wykonać operację asynchroniczną, należy wykonać bezpośrednie wywołanie funkcji interfejsu API ODBC `SQLSetPos`.

Nie trzeba przesłonić `OnSetOptions`, aby zmienić wartość limitu czasu. Zamiast tego, aby dostosować wartość limitu czasu zapytania, wywołaj `SetQueryTimeout` przed utworzeniem zestawu rekordów; `OnSetOptions` będzie używać nowej wartości. Ustawione wartości stosują się do kolejnych operacji na wszystkich zestawach rekordów lub bezpośrednich wywołaniach SQL.

Przesłoń `OnSetOptions`, jeśli chcesz ustawić dodatkowe opcje. Przesłonięcie powinno wywoływać klasę bazową `OnSetOptions` przed lub po wywołaniu funkcji interfejsu API ODBC `SQLSetStmtOption`. Postępuj zgodnie z metodą zilustrowaną w domyślnej implementacji `OnSetOptions`.

##  <a name="open"></a>CDatabase:: Open

Wywołaj tę funkcję elementu członkowskiego, aby zainicjować nowo skonstruowany obiekt `CDatabase`.

```
virtual BOOL Open(
    LPCTSTR lpszDSN,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T("ODBC;"),
    BOOL bUseCursorLib = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszDSN*<br/>
Określa nazwę źródła danych — nazwę zarejestrowana za pomocą ODBC za pośrednictwem programu administratora ODBC. Jeśli wartość DSN jest określona w *lpszConnect* (w formie "DSN =\<dane >"), nie można jej ponownie określić w *lpszDSN*. W tym przypadku *lpszDSN* powinna mieć wartość null. W przeciwnym razie można przekazać wartość NULL, jeśli użytkownik chce przedstawić użytkownikowi okno dialogowe źródła danych, w którym użytkownik może wybrać źródło danych. Aby uzyskać więcej informacji, zobacz uwagi.

*bExclusive*<br/>
Nieobsługiwane w tej wersji biblioteki klas. Obecnie potwierdzenie kończy się niepowodzeniem, jeśli ten parametr ma wartość TRUE. Źródło danych jest zawsze otwierane jako udostępnione (niewyłączne).

*bReadOnly*<br/>
Ma wartość TRUE, jeśli chcesz, aby połączenie było tylko do odczytu i zabraniać aktualizacji źródła danych. Wszystkie zależne zestawy rekordów dziedziczą ten atrybut. Wartość domyślna to FALSE.

*lpszConnect*<br/>
Określa parametry połączenia. Parametry połączenia łączą informacje, które mogą uwzględniać nazwę źródła danych, identyfikator użytkownika prawidłowy w źródle danych, ciąg uwierzytelniania użytkownika (hasło, jeśli źródło danych wymaga jednego) i inne informacje. Wszystkie parametry połączenia muszą być poprzedzone ciągiem "ODBC;". (wielkie lub małe litery). Ciąg "ODBC;" służy do wskazywania, że połączenie jest źródłem danych ODBC; jest to w celu zapewnienia zgodności z górnymi wersjami, gdy przyszłe wersje biblioteki klas mogą obsługiwać źródła danych inne niż ODBC.

*bUseCursorLib*<br/>
Ma wartość TRUE, jeśli chcesz załadować bibliotekę DLL biblioteki kursora ODBC. Biblioteka kursorów maskuje pewne funkcje podstawowego sterownika ODBC, co skutecznie uniemożliwia korzystanie z zestawów dynamicznych (Jeśli sterownik ich obsługuje). Jedyne kursory obsługiwane, jeśli biblioteka kursorów jest załadowana, są migawkami statycznymi i kursorami progresywnymi. Wartość domyślna to TRUE. Jeśli planujesz utworzyć obiekt zestawu rekordów bezpośrednio z `CRecordset` bez jego wyprowadzania, nie należy ładować biblioteki kursorów.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli połączenie zostało pomyślnie nawiązane; w przeciwnym razie, jeśli użytkownik wybierze przycisk Anuluj, gdy zostanie wyświetlone okno dialogowe z prośbą o dodatkowe informacje o połączeniu. We wszystkich innych przypadkach struktura zgłasza wyjątek.

### <a name="remarks"></a>Uwagi

Obiekt bazy danych musi zostać zainicjowany, aby można było używać go do konstruowania obiektu zestawu rekordów.

> [!NOTE]
>  Wywołanie funkcji składowej [OpenEx](#openex) jest preferowanym sposobem nawiązywania połączenia ze źródłem danych i zainicjowania obiektu bazy danych.

Jeśli parametry w wywołaniu `Open` nie zawierają wystarczającej ilości informacji, aby nawiązać połączenie, sterownik ODBC otwiera okno dialogowe umożliwiające uzyskanie niezbędnych informacji od użytkownika. Podczas wywoływania `Open`parametry połączenia, *lpszConnect*, są przechowywane prywatnie w obiekcie `CDatabase` i są dostępne przez wywołanie funkcji składowej [GetConnect](#getconnect) .

Jeśli chcesz, możesz otworzyć własne okno dialogowe przed wywołaniem `Open`, aby uzyskać informacje od użytkownika, takie jak hasło, a następnie dodać te informacje do parametrów połączenia, które są przekazywane do `Open`. Można też zapisać parametry połączenia, które zostały przekazane, aby można było użyć go ponownie podczas następnego wywołania aplikacji `Open` na obiekcie `CDatabase`.

Możesz również użyć parametrów połączenia dla wielu poziomów autoryzacji logowania (każdy dla innego obiektu `CDatabase`) lub przekazać inne informacje specyficzne dla źródła danych. Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz rozdział 5 w Windows SDK.

W przypadku próby nawiązania połączenia w celu przekroczenia limitu czasu, jeśli na przykład Host systemu DBMS jest niedostępny. Jeśli próba połączenia nie powiedzie się, `Open` zgłosi `CDBException`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#14](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]

##  <a name="openex"></a>CDatabase:: OpenEx

Wywołaj tę funkcję elementu członkowskiego, aby zainicjować nowo skonstruowany obiekt `CDatabase`.

```
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,
    DWORD dwOptions = 0);
```

### <a name="parameters"></a>Parametry

*lpszConnectString*<br/>
Określa parametry połączenia ODBC. Obejmuje to również nazwę źródła danych oraz inne informacje opcjonalne, takie jak identyfikator użytkownika i hasło. Na przykład "DSN = SQLServer_Source; UID = SA; PWD = abc123 "to możliwe parametry połączenia. Należy pamiętać, że w przypadku przekazania wartości NULL dla *lpszConnectString*w oknie dialogowym źródło danych zostanie wyświetlony monit o wybranie źródła danych.

*dwOptions*<br/>
Maska bitów, która określa kombinację następujących wartości. Wartość domyślna to 0, co oznacza, że baza danych zostanie otwarta jako udostępniona z dostępem do zapisu, biblioteka DLL biblioteki kursora ODBC nie zostanie załadowana, a okno dialogowe połączenie ODBC zostanie wyświetlone tylko wtedy, gdy nie ma wystarczającej ilości informacji, aby nawiązać połączenie.

- `CDatabase::openExclusive` nieobsługiwane w tej wersji biblioteki klas. Źródło danych jest zawsze otwierane jako udostępnione (niewyłączne). Obecnie potwierdzenie kończy się niepowodzeniem w przypadku określenia tej opcji.

- `CDatabase::openReadOnly` otworzyć źródła danych jako tylko do odczytu.

- `CDatabase::useCursorLib` załadować biblioteki DLL kursora ODBC. Biblioteka kursorów maskuje pewne funkcje podstawowego sterownika ODBC, co skutecznie uniemożliwia korzystanie z zestawów dynamicznych (Jeśli sterownik ich obsługuje). Jedyne kursory obsługiwane, jeśli biblioteka kursorów jest załadowana, są migawkami statycznymi i kursorami progresywnymi. Jeśli planujesz utworzyć obiekt zestawu rekordów bezpośrednio z `CRecordset` bez jego wyprowadzania, nie należy ładować biblioteki kursorów.

- `CDatabase::noOdbcDialog` nie wyświetlaj okna dialogowego połączenia ODBC, bez względu na to, czy są podane wystarczające informacje o połączeniu.

- `CDatabase::forceOdbcDialog` zawsze wyświetlać okno dialogowe połączenie ODBC.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli połączenie zostało pomyślnie nawiązane; w przeciwnym razie, jeśli użytkownik wybierze przycisk Anuluj, gdy zostanie wyświetlone okno dialogowe z prośbą o dodatkowe informacje o połączeniu. We wszystkich innych przypadkach struktura zgłasza wyjątek.

### <a name="remarks"></a>Uwagi

Obiekt bazy danych musi zostać zainicjowany, aby można było używać go do konstruowania obiektu zestawu rekordów.

Jeśli parametr *lpszConnectString* w wywołaniu `OpenEx` nie zawiera wystarczającej ilości informacji, aby nawiązać połączenie, sterownik ODBC otwiera okno dialogowe umożliwiające uzyskanie niezbędnych informacji od użytkownika, pod warunkiem, że nie ustawiono `CDatabase::noOdbcDialog` lub `CDatabase::forceOdbcDialog` w parametrze *dwOptions* . Podczas wywoływania `OpenEx`parametry połączenia, *lpszConnectString*, są przechowywane prywatnie w obiekcie `CDatabase` i są dostępne przez wywołanie funkcji składowej [GetConnect](#getconnect) .

Jeśli chcesz, możesz otworzyć własne okno dialogowe przed wywołaniem `OpenEx`, aby uzyskać informacje od użytkownika, takie jak hasło, a następnie dodać te informacje do parametrów połączenia, które są przekazywane do `OpenEx`. Można też zapisać parametry połączenia, które zostały przekazane, aby można było użyć go ponownie podczas następnego wywołania aplikacji `OpenEx` na obiekcie `CDatabase`.

Możesz również użyć parametrów połączenia dla wielu poziomów autoryzacji logowania (każdy dla innego obiektu `CDatabase`) lub przekazać inne informacje specyficzne dla źródła danych. Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz rozdział 6 w *Kompendium ODBC Programmer's Reference*.

W przypadku próby nawiązania połączenia w celu przekroczenia limitu czasu, jeśli na przykład Host systemu DBMS jest niedostępny. Jeśli próba połączenia nie powiedzie się, `OpenEx` zgłosi `CDBException`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#11](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]

##  <a name="rollback"></a>CDatabase:: Rollback

Wywołaj tę funkcję elementu członkowskiego, aby odwrócić zmiany wprowadzone w trakcie transakcji.

```
BOOL Rollback();
```

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli transakcja została pomyślnie odwrócona; w przeciwnym razie 0. Jeśli wywołanie `Rollback` nie powiedzie się, źródło danych i Stany transakcji są niezdefiniowane. Jeśli `Rollback` zwraca wartość 0, należy sprawdzić źródło danych w celu określenia jego stanu.

### <a name="remarks"></a>Uwagi

Wszystkie wywołania `CRecordset` `AddNew`, `Edit`, `Delete`i `Update` wykonywane od momentu ostatniego [BeginTrans](#begintrans) są wycofywane do stanu, który istniał w momencie wywołania.

Po wywołaniu `Rollback`transakcja jest w trybie over i należy ponownie wywołać `BeginTrans` dla innej transakcji. Rekord, który był aktualny przed wywołaniem `BeginTrans`, zostaje ponownie bieżącym rekordem po `Rollback`.

Po wycofaniu rekord, który był aktualny przed wycofaniem, pozostaje aktualny. Aby uzyskać szczegółowe informacje o stanie zestawu rekordów i źródła danych po zakończeniu wycofywania, zobacz artykuł [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Przykład

  Zobacz artykuł [transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="setlogintimeout"></a>CDatabase:: SetLoginTimeout

Wywołaj tę funkcję elementu członkowskiego — przed wywołaniem `OpenEx` lub `Open` — aby zastąpić domyślną liczbę sekund dozwoloną przed upływem limitu czasu połączenia ze źródłem danych.

```
void SetLoginTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Parametry

*dwSeconds*<br/>
Liczba sekund, które mają być dozwolone przed upływem limitu czasu połączenia.

### <a name="remarks"></a>Uwagi

Próba połączenia może przekroczyć limit czasu, jeśli na przykład system DBMS nie jest dostępny. Wywołaj `SetLoginTimeout` Po skonstruowaniu niezainicjowanego obiektu `CDatabase`, ale przed wywołaniem `OpenEx` lub `Open`.

Wartość domyślna dla limitów czasu logowania wynosi 15 sekund. Nie wszystkie źródła danych obsługują możliwość określania wartości limitu czasu logowania. Jeśli źródło danych nie obsługuje limitu czasu, uzyskasz wyniki śledzenia, ale nie wyjątek. Wartość 0 oznacza "nieskończone".

##  <a name="setquerytimeout"></a>CDatabase:: SetQueryTimeout

Wywołaj tę funkcję elementu członkowskiego, aby zastąpić domyślną liczbę sekund dozwoloną przed upływem limitu czasu dla kolejnych operacji w połączonym źródle danych.

```
void SetQueryTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Parametry

*dwSeconds*<br/>
Liczba sekund, które mają być dozwolone przed upływem limitu czasu zapytania.

### <a name="remarks"></a>Uwagi

Operacja może przekroczyć limit czasu, ponieważ występują problemy z dostępem do sieci, nadmierny czas przetwarzania zapytania i tak dalej. Wywołaj `SetQueryTimeout` przed otwarciem zestawu rekordów lub przed wywołaniem `AddNew`zestawu rekordów, `Update` lub `Delete` funkcji Członkowskich, jeśli chcesz zmienić wartość limitu czasu zapytania. To ustawienie ma wpływ na wszystkie kolejne `Open`, `AddNew`, `Update`i `Delete` wywołań do dowolnych zestawów rekordów skojarzonych z tym obiektem `CDatabase`. Zmiana wartości limitu czasu zapytania dla zestawu rekordów po otwarciu nie powoduje zmiany wartości zestawu rekordów. Na przykład kolejne operacje `Move` nie używają nowej wartości.

Wartość domyślna dla limitów czasu zapytania wynosi 15 sekund. Nie wszystkie źródła danych obsługują możliwość ustawiania wartości limitu czasu zapytania. Jeśli ustawisz wartość limitu czasu zapytania równy 0, nie zostanie przekroczony limit czasu. Komunikacja ze źródłem danych może przestać odpowiadać. Takie zachowanie może być przydatne podczas opracowywania. Jeśli źródło danych nie obsługuje limitu czasu, uzyskasz wyniki śledzenia, ale nie wyjątek.

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)
