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
ms.openlocfilehash: ee1503f49f0e60b24e0ef3a9c9631f039ad9355e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223112"
---
# <a name="cdatabase-class"></a>Klasa CDatabase

Reprezentuje połączenie ze źródłem danych, za pomocą którego można pracować na źródle danych.

## <a name="syntax"></a>Składnia

```
class CDatabase : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDatabase:: CDatabase](#cdatabase)|Konstruuje `CDatabase` obiekt. Należy zainicjować obiekt, wywołując `OpenEx` lub `Open` .|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDatabase:: BeginTrans](#begintrans)|Uruchamia "transakcję" — szereg wywołań odwracalnych do `AddNew` `Edit` `Delete` funkcji składowych,, i `Update` elementów członkowskich klasy `CRecordset` — w połączonym źródle danych. Aby można było uzyskać efekt, źródło danych musi obsługiwać transakcje `BeginTrans` .|
|[CDatabase:: BindParameters](#bindparameters)|Pozwala powiązać parametry przed wywołaniem `CDatabase::ExecuteSQL` .|
|[CDatabase:: Cancel](#cancel)|Anuluje operację asynchroniczną lub proces z drugiego wątku.|
|[CDatabase:: gettransact](#cantransact)|Zwraca wartość różną od zera, jeśli źródło danych obsługuje transakcje.|
|[CDatabase:: Update](#canupdate)|Zwraca wartość różną od zera, jeśli `CDatabase` obiekt jest aktualizowalny (nie tylko do odczytu).|
|[CDatabase:: Close](#close)|Zamyka połączenie ze źródłem danych.|
|[CDatabase:: CommitTrans](#committrans)|Kończy transakcję rozpoczętą przez `BeginTrans` . Polecenia w transakcji, które zmieniają źródło danych, są wykonywane.|
|[CDatabase:: ExecuteSql by](#executesql)|Wykonuje instrukcję języka SQL. Żadne rekordy danych nie są zwracane.|
|[CDatabase:: GetBookmarkPersistence](#getbookmarkpersistence)|Identyfikuje operacje, za pomocą których zakładki są utrwalane na obiektach zestawu rekordów.|
|[CDatabase:: GetConnect](#getconnect)|Zwraca parametry połączenia ODBC używane do łączenia `CDatabase` obiektu ze źródłem danych.|
|[CDatabase:: GetCursorCommitBehavior](#getcursorcommitbehavior)|Określa efekt zatwierdzania transakcji w otwartym obiekcie zestawu rekordów.|
|[CDatabase:: GetCursorRollbackBehavior](#getcursorrollbackbehavior)|Określa efekt wycofania transakcji na otwartym obiekcie zestawu rekordów.|
|[CDatabase:: GetDatabaseName](#getdatabasename)|Zwraca nazwę aktualnie używanej bazy danych.|
|[CDatabase:: IsOpen](#isopen)|Zwraca wartość różną od zera, jeśli `CDatabase` obiekt jest obecnie połączony ze źródłem danych.|
|[CDatabase:: onoptions](#onsetoptions)|Wywoływane przez platformę, by ustawić standardowe opcje połączenia. Domyślna implementacja ustawia wartość limitu czasu zapytania. Możesz później ustalić te opcje, wywołując `SetQueryTimeout` .|
|[CDatabase:: Open](#open)|Nawiązuje połączenie ze źródłem danych (za pośrednictwem sterownika ODBC).|
|[CDatabase:: OpenEx](#openex)|Nawiązuje połączenie ze źródłem danych (za pośrednictwem sterownika ODBC).|
|[CDatabase:: Rollback](#rollback)|Odwraca zmiany wprowadzone w bieżącej transakcji. Źródło danych powraca do poprzedniego stanu, zgodnie z definicją w `BeginTrans` wywołaniu, bez zmian.|
|[CDatabase:: SetLoginTimeout](#setlogintimeout)|Ustawia liczbę sekund, po upływie których zostanie przekroczony limit czasu próby połączenia ze źródłem danych.|
|[CDatabase:: SetQueryTimeout](#setquerytimeout)|Ustawia liczbę sekund, po upływie których limit czasu operacji zapytania bazy danych zostanie przekroczony. Ma wpływ na wszystkie kolejne zestawy rekordów `Open` , `AddNew` , `Edit` i `Delete` .|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDatabase:: m_hdbc](#m_hdbc)|Open Database Connectivity (ODBC) dojście połączenia do źródła danych. Wpisz *HDBC*.|

## <a name="remarks"></a>Uwagi

Źródło danych jest określonym wystąpieniem danych hostowanym przez jakiś system zarządzania bazami danych (DBMS). Przykładami mogą być Microsoft SQL Server, Microsoft Access, Borland dBASE i xBASE. W aplikacji może być aktywnych jednocześnie jeden lub więcej `CDatabase` obiektów.

> [!NOTE]
> Jeśli pracujesz z klasami obiektów dostępu do danych (DAO), a nie klasami Open Database Connectivity (ODBC), zamiast tego użyj klasy [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) . Aby uzyskać więcej informacji, zobacz [Omówienie artykułu: Programowanie baz danych](../../data/data-access-programming-mfc-atl.md).

Aby użyć `CDatabase` , Skonstruuj `CDatabase` obiekt i Wywołaj jego `OpenEx` funkcję członkowską. Spowoduje to otwarcie połączenia. Gdy następnie utworzysz `CRecordset` obiekty do działania w połączonym źródle danych, Przekaż Konstruktor zestawu rekordów wskaźnik do `CDatabase` obiektu. Po zakończeniu korzystania z połączenia Wywołaj `Close` funkcję członkowską i zniszcz `CDatabase` obiekt. `Close`zamyka wszystkie zestawy rekordów, które nie zostały wcześniej zamknięte.

Aby uzyskać więcej informacji na temat `CDatabase` , zobacz artykuł [Data Source (ODBC)](../../data/odbc/data-source-odbc.md) i [Omówienie: Programowanie baz danych](../../data/data-access-programming-mfc-atl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CDatabase`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDB. h

## <a name="cdatabasebegintrans"></a><a name="begintrans"></a>CDatabase:: BeginTrans

Wywołaj tę funkcję elementu członkowskiego, aby rozpocząć transakcję z połączonym źródłem danych.

```
BOOL BeginTrans();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wywołanie zakończyło się pomyślnie, a zmiany są zatwierdzane tylko ręcznie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Transakcja składa się z jednego lub większej liczby wywołań `AddNew` do `Edit` `Delete` `Update` funkcji składowych obiektu,,, i `CRecordset` . Przed rozpoczęciem transakcji, `CDatabase` obiekt musi być już połączony ze źródłem danych, wywołując jego `OpenEx` `Open` funkcję or. Aby zakończyć transakcję, wywołaj [CommitTrans](#committrans) , aby zaakceptować wszystkie zmiany w źródle danych (i przenieść je), lub wywołaj funkcję [wycofywania](#rollback) , aby przerwać całą transakcję. Wywołaj `BeginTrans` po otwarciu dowolnego zestawu rekordów związanego z transakcją i jak najbliżej rzeczywistych operacji aktualizowania, jak to możliwe.

> [!CAUTION]
> W zależności od sterownika ODBC otwarcie zestawu rekordów przed wywołaniem `BeginTrans` może spowodować problemy podczas wywoływania `Rollback` . Należy sprawdzić konkretny używany sterownik. Na przykład w przypadku korzystania z sterownika Microsoft Access Driver zawartego w pakiecie Microsoft ODBC Desktop Driver Pack 3,0 należy uwzględnić wymaganie aparatu bazy danych Jet, że nie należy rozpoczynać transakcji w żadnej bazie danych, która ma otwarty kursor. W klasach baz danych MFC kursor oznacza otwarty `CRecordset` obiekt. Aby uzyskać więcej informacji, zobacz [Uwagi techniczne 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md).

`BeginTrans`program może również blokować rekordy danych na serwerze w zależności od żądanych współbieżności i możliwości źródła danych. Informacje o blokowaniu danych znajdują się w artykule [zestaw rekordów: blokowanie rekordów (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).

Transakcje zdefiniowane przez użytkownika są wyjaśnione w artykule [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).

`BeginTrans`Określa stan, do którego można wycofać sekwencję transakcji (odwróconą). Aby ustanowić nowy stan wycofywania, Zatwierdź każdą bieżącą transakcję, a następnie `BeginTrans` ponownie wywołaj.

> [!CAUTION]
> Wywoływanie `BeginTrans` ponownie bez wywoływania `CommitTrans` lub `Rollback` jest błędem.

Wywołaj [funkcję DataMember elementu](#cantransact) Członkowskiego, aby określić, czy sterownik obsługuje transakcje dla danej bazy danych. Należy również wywołać [GetCursorCommitBehavior](#getcursorcommitbehavior) i [GetCursorRollbackBehavior](#getcursorrollbackbehavior) , aby określić obsługę zachowywania kursora.

Aby uzyskać więcej informacji na temat transakcji, zobacz artykuł [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Przykład

  Zobacz artykuł [transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="cdatabasebindparameters"></a><a name="bindparameters"></a>CDatabase:: BindParameters

Przesłoń `BindParameters` , gdy musisz powiązać parametry przed wywołaniem [CDatabase:: ExecuteSql by](#executesql).

```
virtual void BindParameters(HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*hstmt*<br/>
Dojście instrukcji ODBC, dla którego chcesz powiązać parametry.

### <a name="remarks"></a>Uwagi

Takie podejście jest przydatne, gdy nie potrzebujesz zestawu wyników z procedury składowanej.

W przypadku zastąpienia, wywołania `SQLBindParameters` i powiązane funkcje ODBC do powiązania parametrów. MFC wywołuje przesłonięcie przed wywołaniem do `ExecuteSQL` . Nie ma potrzeby wywoływania `SQLPrepare` ; `ExecuteSQL` wywołuje `SQLExecDirect` i niszczy *HSTMT*, który jest używany tylko raz.

## <a name="cdatabasecancel"></a><a name="cancel"></a>CDatabase:: Cancel

Wywołaj tę funkcję elementu członkowskiego, aby zażądać, aby źródło danych anulował operację asynchroniczną w toku lub proces z drugiego wątku.

```cpp
void Cancel();
```

### <a name="remarks"></a>Uwagi

Należy pamiętać, że klasy MFC ODBC nie są już używane do przetwarzania asynchronicznego; Aby wykonać operację asynchroniczną, należy bezpośrednio wywołać funkcję ODBC API [SQLSetConnectOption](/sql/odbc/reference/syntax/sqlsetconnectoption-function). Aby uzyskać więcej informacji, zobacz [wykonywanie asynchroniczne](/sql/odbc/reference/develop-app/asynchronous-execution).

## <a name="cdatabasecantransact"></a><a name="cantransact"></a>CDatabase:: gettransact

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy baza danych zezwala na transakcje.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli zestawy rekordów używające tego `CDatabase` obiektu zezwalają na transakcje; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać informacje o transakcjach, zobacz artykuł [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="cdatabasecanupdate"></a><a name="canupdate"></a>CDatabase:: Update

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy `CDatabase` obiekt zezwala na aktualizacje.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różna od zera `CDatabase` , jeśli obiekt zezwala na aktualizacje; w przeciwnym razie wartość 0 wskazuje, że wartość true w *bReadOnly* została przeniesiona podczas otwierania `CDatabase` obiektu lub że samo źródło danych jest tylko do odczytu. Źródło danych jest tylko do odczytu, jeśli wywołanie funkcji interfejsu API ODBC `SQLGetInfo` dla SQL_DATASOURCE_READ_ONLY zwraca wartość "y".

### <a name="remarks"></a>Uwagi

Nie wszystkie sterowniki obsługują aktualizacje.

## <a name="cdatabasecdatabase"></a><a name="cdatabase"></a>CDatabase:: CDatabase

Konstruuje `CDatabase` obiekt.

```
CDatabase();
```

### <a name="remarks"></a>Uwagi

Po skonstruowaniu obiektu, należy wywołać jego `OpenEx` `Open` funkcję elementu członkowskiego, aby nawiązać połączenie z określonym źródłem danych.

Przydatne może być osadzenie `CDatabase` obiektu w klasie dokumentu.

### <a name="example"></a>Przykład

Ten przykład ilustruje użycie `CDatabase` w `CDocument` klasie pochodnej.

[!code-cpp[NVC_MFCDatabase#9](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]

[!code-cpp[NVC_MFCDatabase#10](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]

## <a name="cdatabaseclose"></a><a name="close"></a>CDatabase:: Close

Wywołaj tę funkcję elementu członkowskiego, jeśli chcesz rozłączyć się ze źródłem danych.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

`CDatabase`Przed wywołaniem tej funkcji elementu członkowskiego należy zamknąć wszystkie zestawy rekordów skojarzone z obiektem. Ponieważ nie `Close` niszczy tego `CDatabase` obiektu, można ponownie użyć tego obiektu, otwierając nowe połączenie z tym samym źródłem danych lub innym źródłem danych.

Wszystkie oczekujące `AddNew` lub `Edit` instrukcje zestawów rekordów korzystających z bazy danych są anulowane, a wszystkie oczekujące transakcje są wycofywane. Wszystkie zestawy rekordów zależne od `CDatabase` obiektu są pozostawione w niezdefiniowanym stanie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#12](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]

## <a name="cdatabasecommittrans"></a><a name="committrans"></a>CDatabase:: CommitTrans

Wywołaj tę funkcję elementu członkowskiego po wykonaniu transakcji.

```
BOOL CommitTrans();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli aktualizacje zostały pomyślnie zatwierdzone; w przeciwnym razie 0. Jeśli to `CommitTrans` się nie powiedzie, stan źródła danych jest niezdefiniowany. Należy sprawdzić dane, aby ustalić ich stan.

### <a name="remarks"></a>Uwagi

Transakcja składa się z serii wywołań do `AddNew` `Edit` `Delete` funkcji składowych,, i `Update` elementów członkowskich obiektu, `CRecordset` które rozpoczęły wywołanie funkcji składowej [BeginTrans](#begintrans) . `CommitTrans`Zatwierdza transakcję. Domyślnie aktualizacje są zatwierdzane natychmiast; wywołanie `BeginTrans` powoduje, że zobowiązania dotyczące aktualizacji są opóźnione do momentu `CommitTrans` wywołania.

Do momentu wywołania `CommitTrans` do końca transakcji można wywołać funkcję [wycofywania](#rollback) elementu członkowskiego, aby przerwać transakcję i pozostawić źródło danych w jego pierwotnym stanie. Aby rozpocząć nową transakcję, zadzwoń `BeginTrans` ponownie.

Aby uzyskać więcej informacji na temat transakcji, zobacz artykuł [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Przykład

  Zobacz artykuł [transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="cdatabaseexecutesql"></a><a name="executesql"></a>CDatabase:: ExecuteSql by

Wywołaj tę funkcję elementu członkowskiego, gdy musisz bezpośrednio wykonać polecenie SQL.

```cpp
void ExecuteSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>Parametry

*lpszSQL*<br/>
Wskaźnik na ciąg zakończony znakiem null zawierający prawidłowe polecenie SQL do wykonania. Można przekazać [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Uwagi

Utwórz polecenie jako ciąg zakończony znakiem null. `ExecuteSQL`nie zwraca rekordów danych. Jeśli chcesz korzystać z rekordów, zamiast tego użyj obiektu zestawu rekordów.

Większość poleceń dla źródła danych jest emitowanych za pomocą obiektów zestawu rekordów, które obsługują polecenia umożliwiające Zaznaczanie danych, wstawianie nowych rekordów, usuwanie rekordów i edytowanie rekordów. Jednak nie wszystkie funkcje ODBC są bezpośrednio obsługiwane przez klasy baz danych, więc czasami trzeba wykonać bezpośrednie wywołanie SQL z `ExecuteSQL` .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#13](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]

## <a name="cdatabasegetbookmarkpersistence"></a><a name="getbookmarkpersistence"></a>CDatabase:: GetBookmarkPersistence

Wywołaj tę funkcję elementu członkowskiego, aby określić trwałość zakładek w obiekcie zestawu rekordów po pewnych operacjach.

```
DWORD GetBookmarkPersistence() const;
```

### <a name="return-value"></a>Wartość zwracana

Maska bitów, która identyfikuje operacje, za pomocą których zakładki są utrwalane na obiekcie zestawu rekordów. Aby uzyskać szczegółowe informacje, zobacz uwagi.

### <a name="remarks"></a>Uwagi

Na przykład jeśli wywołasz metodę `CRecordset::GetBookmark` , a następnie wywołajesz `CRecordset::Requery` , zakładka uzyskana od `GetBookmark` może nie być już prawidłowa. Należy wywołać `GetBookmarkPersistence` przed wywołaniem metody `CRecordset::SetBookmark` .

W poniższej tabeli wymieniono wartości masek bitowych, które mogą być łączone dla zwracanej wartości `GetBookmarkPersistence` .

|Wartość maski bitowej|Trwałość zakładki|
|-------------------|--------------------------|
|SQL_BP_CLOSE|Zakładki są prawidłowe po `Requery` operacji.|
|SQL_BP_DELETE|Zakładka dla wiersza jest ważna po `Delete` operacji w tym wierszu.|
|SQL_BP_DROP|Zakładki są prawidłowe po `Close` operacji.|
|SQL_BP_SCROLL|Zakładki są prawidłowe po każdej `Move` operacji. Jest to po prostu określenie, czy zakładki są obsługiwane w zestawie rekordów, jak zostało to zwrócone przez `CRecordset::CanBookmark` .|
|SQL_BP_TRANSACTION|Zakładki są ważne po zatwierdzeniu transakcji lub wycofaniu jej z powrotem.|
|SQL_BP_UPDATE|Zakładka dla wiersza jest ważna po `Update` operacji w tym wierszu.|
|SQL_BP_OTHER_HSTMT|Zakładki skojarzone z jednym obiektem zestawu rekordów są prawidłowe dla drugiego zestawu rekordów.|

Aby uzyskać więcej informacji na temat tej wartości zwracanej, zobacz Funkcja ODBC API `SQLGetInfo` w Windows SDK. Aby uzyskać więcej informacji na temat zakładek, zobacz [zestaw rekordów artykułów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

## <a name="cdatabasegetconnect"></a><a name="getconnect"></a>CDatabase:: GetConnect

Wywołaj tę funkcję elementu członkowskiego, aby pobrać parametry połączenia używane podczas wywołania `OpenEx` lub `Open` , które połączyły `CDatabase` obiekt ze źródłem danych.

```
const CString GetConnect() const;
```

### <a name="return-value"></a>Wartość zwracana

**`const`** [CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierający parametry połączenia, jeśli `OpenEx` lub `Open` został wywołany; w przeciwnym razie, pusty ciąg.

### <a name="remarks"></a>Uwagi

Zobacz [CDatabase:: Open](#open) , aby uzyskać opis sposobu tworzenia parametrów połączenia.

## <a name="cdatabasegetcursorcommitbehavior"></a><a name="getcursorcommitbehavior"></a>CDatabase:: GetCursorCommitBehavior

Wywołaj tę funkcję elementu członkowskiego, aby określić, w jaki sposób operacja [CommitTrans](#committrans) ma wpływ na kursory dla otwartych obiektów zestawu rekordów.

```
int GetCursorCommitBehavior() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość wskazująca wpływ transakcji na otwarte obiekty zestawu rekordów. Aby uzyskać szczegółowe informacje, zobacz uwagi.

### <a name="remarks"></a>Uwagi

Poniższa tabela zawiera listę możliwych zwracanych wartości dla `GetCursorCommitBehavior` i odpowiadający efekt w otwartym zestawie rekordów.

|Wartość zwracana|Wpływ na obiekty CRecordset|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Wywołaj `CRecordset::Requery` bezpośrednio po zatwierdzeniu transakcji.|
|SQL_CB_DELETE|Wywołaj `CRecordset::Close` bezpośrednio po zatwierdzeniu transakcji.|
|SQL_CB_PRESERVE|Kontynuuj normalne `CRecordset` działanie.|

Aby uzyskać więcej informacji na temat tej wartości zwracanej, zobacz Funkcja ODBC API `SQLGetInfo` w Windows SDK. Aby uzyskać więcej informacji na temat transakcji, zobacz artykuł [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="cdatabasegetcursorrollbackbehavior"></a><a name="getcursorrollbackbehavior"></a>CDatabase:: GetCursorRollbackBehavior

Wywołaj tę funkcję elementu członkowskiego, aby określić, jak operacja [wycofywania](#rollback) wpływa na kursory w otwartych obiektach zestawu rekordów.

```
int GetCursorRollbackBehavior() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość wskazująca wpływ transakcji na otwarte obiekty zestawu rekordów. Aby uzyskać szczegółowe informacje, zobacz uwagi.

### <a name="remarks"></a>Uwagi

Poniższa tabela zawiera listę możliwych zwracanych wartości dla `GetCursorRollbackBehavior` i odpowiadający efekt w otwartym zestawie rekordów.

|Wartość zwracana|Wpływ na obiekty CRecordset|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Wywołaj `CRecordset::Requery` bezpośrednio po wycofaniu transakcji.|
|SQL_CB_DELETE|Wywołaj `CRecordset::Close` bezpośrednio po wycofaniu transakcji.|
|SQL_CB_PRESERVE|Kontynuuj normalne `CRecordset` działanie.|

Aby uzyskać więcej informacji na temat tej wartości zwracanej, zobacz Funkcja ODBC API `SQLGetInfo` w Windows SDK. Aby uzyskać więcej informacji na temat transakcji, zobacz artykuł [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="cdatabasegetdatabasename"></a><a name="getdatabasename"></a>CDatabase:: GetDatabaseName

Wywołaj tę funkcję elementu członkowskiego, aby pobrać nazwę aktualnie połączonej bazy danych (pod warunkiem, że źródło danych definiuje nazwany obiekt o nazwie "Database").

```
CString GetDatabaseName() const;
```

### <a name="return-value"></a>Wartość zwracana

Element [CString](../../atl-mfc-shared/reference/cstringt-class.md) , który zawiera nazwę bazy danych, jeśli się powiedzie; w przeciwnym razie jest pusta `CString` .

### <a name="remarks"></a>Uwagi

Ta wartość nie jest taka sama jak nazwa źródła danych (DSN) określona w `OpenEx` wywołaniu lub `Open` . Jakie dane `GetDatabaseName` zwrotne są zależne od ODBC. Ogólnie rzecz biorąc, baza danych jest kolekcją tabel. Jeśli ta jednostka ma nazwę, `GetDatabaseName` zwraca ją.

Możesz na przykład wyświetlić tę nazwę w nagłówku. Jeśli wystąpi błąd podczas pobierania nazwy z ODBC, `GetDatabaseName` Funkcja zwraca wartość pustą `CString` .

## <a name="cdatabaseisopen"></a><a name="isopen"></a>CDatabase:: IsOpen

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy `CDatabase` obiekt jest obecnie połączony ze źródłem danych.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli `CDatabase` obiekt jest aktualnie połączony; w przeciwnym razie 0.

## <a name="cdatabasem_hdbc"></a><a name="m_hdbc"></a>CDatabase:: m_hdbc

Zawiera publiczny uchwyt połączenia ze źródłem danych ODBC — "dojście połączenia".

### <a name="remarks"></a>Uwagi

Zwykle nie będzie trzeba bezpośrednio uzyskiwać dostępu do tej zmiennej członkowskiej. Zamiast tego, struktura przydziela dojście podczas wywoływania `OpenEx` lub `Open` . Struktura cofa alokację dojścia po wywołaniu **`delete`** operatora dla `CDatabase` obiektu. Należy zauważyć, że `Close` funkcja członkowska nie cofa alokacji dojścia.

Jednak w pewnych okolicznościach może być konieczne bezpośrednie użycie uchwytu. Na przykład, jeśli musisz wywołać funkcje interfejsu API ODBC bezpośrednio, a nie za pośrednictwem klasy `CDatabase` , może być konieczne dojście połączenia do przekazania jako parametr. Zobacz Poniższy przykład kodu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#15](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]

## <a name="cdatabaseonsetoptions"></a><a name="onsetoptions"></a>CDatabase:: onoptions

Struktura wywołuje tę funkcję członkowską podczas bezpośredniego wykonywania instrukcji SQL z `ExecuteSQL` funkcją członkowską.

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*hstmt*<br/>
Dojście instrukcji ODBC, dla którego są ustawiane opcje.

### <a name="remarks"></a>Uwagi

`CRecordset::OnSetOptions`wywołuje również tę funkcję elementu członkowskiego.

`OnSetOptions`ustawia wartość limitu czasu logowania. Jeśli istnieją poprzednie wywołania `SetQueryTimeout` funkcji i elementu członkowskiego, `OnSetOptions` odzwierciedlają bieżące wartości; w przeciwnym razie ustawia wartości domyślne.

> [!NOTE]
> Przed MFC 4,2, należy `OnSetOptions` również ustawić tryb przetwarzania na snychronous lub asynchroniczny. Począwszy od MFC 4,2, wszystkie operacje są synchroniczne. Aby wykonać operację asynchroniczną, należy wykonać bezpośrednie wywołanie funkcji interfejsu API ODBC `SQLSetPos` .

Nie trzeba przesłonić, `OnSetOptions` Aby zmienić wartość limitu czasu. Zamiast tego, aby dostosować wartość limitu czasu zapytania, należy wywołać `SetQueryTimeout` przed utworzeniem zestawu rekordów; `OnSetOptions` zostanie użyta nowa wartość. Ustawione wartości stosują się do kolejnych operacji na wszystkich zestawach rekordów lub bezpośrednich wywołaniach SQL.

Przesłoń `OnSetOptions` , jeśli chcesz ustawić dodatkowe opcje. Przesłonięcie powinno wywołać klasę bazową `OnSetOptions` przed lub po wywołaniu funkcji interfejsu API ODBC `SQLSetStmtOption` . Wykonaj metodę zilustrowaną w domyślnej implementacji platformy `OnSetOptions` .

## <a name="cdatabaseopen"></a><a name="open"></a>CDatabase:: Open

Wywołaj tę funkcję elementu członkowskiego, aby zainicjować nowo skonstruowany `CDatabase` obiekt.

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
Określa nazwę źródła danych — nazwę zarejestrowana za pomocą ODBC za pośrednictwem programu administratora ODBC. Jeśli wartość DSN jest określona w *lpszConnect* (w postaci "DSN = \<data-source> "), nie może być określona ponownie w *lpszDSN*. W tym przypadku *lpszDSN* powinna mieć wartość null. W przeciwnym razie można przekazać wartość NULL, jeśli użytkownik chce przedstawić użytkownikowi okno dialogowe źródła danych, w którym użytkownik może wybrać źródło danych. Aby uzyskać więcej informacji, zobacz uwagi.

*bExclusive*<br/>
Nieobsługiwane w tej wersji biblioteki klas. Obecnie potwierdzenie kończy się niepowodzeniem, jeśli ten parametr ma wartość TRUE. Źródło danych jest zawsze otwierane jako udostępnione (niewyłączne).

*bReadOnly*<br/>
Ma wartość TRUE, jeśli chcesz, aby połączenie było tylko do odczytu i zabraniać aktualizacji źródła danych. Wszystkie zależne zestawy rekordów dziedziczą ten atrybut. Wartość domyślna to FALSE.

*lpszConnect*<br/>
Określa parametry połączenia. Parametry połączenia łączą informacje, które mogą uwzględniać nazwę źródła danych, identyfikator użytkownika prawidłowy w źródle danych, ciąg uwierzytelniania użytkownika (hasło, jeśli źródło danych wymaga jednego) i inne informacje. Wszystkie parametry połączenia muszą być poprzedzone ciągiem "ODBC;". (wielkie lub małe litery). Ciąg "ODBC;" służy do wskazywania, że połączenie jest źródłem danych ODBC; jest to w celu zapewnienia zgodności z górnymi wersjami, gdy przyszłe wersje biblioteki klas mogą obsługiwać źródła danych inne niż ODBC.

*bUseCursorLib*<br/>
Ma wartość TRUE, jeśli chcesz załadować bibliotekę DLL biblioteki kursora ODBC. Biblioteka kursorów maskuje pewne funkcje podstawowego sterownika ODBC, co skutecznie uniemożliwia korzystanie z zestawów dynamicznych (Jeśli sterownik ich obsługuje). Jedyne kursory obsługiwane, jeśli biblioteka kursorów jest załadowana, są migawkami statycznymi i kursorami progresywnymi. Wartość domyślna to TRUE. Jeśli planujesz utworzyć obiekt zestawu rekordów bezpośrednio z poziomu `CRecordset` tego programu, nie należy ładować biblioteki kursorów.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli połączenie zostało pomyślnie nawiązane; w przeciwnym razie, jeśli użytkownik wybierze przycisk Anuluj, gdy zostanie wyświetlone okno dialogowe z prośbą o dodatkowe informacje o połączeniu. We wszystkich innych przypadkach struktura zgłasza wyjątek.

### <a name="remarks"></a>Uwagi

Obiekt bazy danych musi zostać zainicjowany, aby można było używać go do konstruowania obiektu zestawu rekordów.

> [!NOTE]
> Wywołanie funkcji składowej [OpenEx](#openex) jest preferowanym sposobem nawiązywania połączenia ze źródłem danych i zainicjowania obiektu bazy danych.

Jeśli parametry w `Open` wywołaniu nie zawierają wystarczającej ilości informacji do nawiązania połączenia, sterownik ODBC otwiera okno dialogowe umożliwiające uzyskanie niezbędnych informacji od użytkownika. Po wywołaniu `Open` Parametry połączenia, *lpszConnect*, są przechowywane prywatnie w `CDatabase` obiekcie i są dostępne przez wywołanie funkcji składowej [GetConnect](#getconnect) .

Jeśli chcesz, możesz otworzyć własne okno dialogowe przed wywołaniem, `Open` Aby uzyskać informacje od użytkownika, takie jak hasło, a następnie dodać te informacje do parametrów połączenia, które są przekazywane `Open` . Można też zapisać parametry połączenia, które zostały przekazane, aby można było użyć go ponownie podczas następnego wywołania aplikacji `Open` na `CDatabase` obiekcie.

Można również użyć parametrów połączenia dla wielu poziomów autoryzacji logowania (dla różnych `CDatabase` obiektów) lub przekazać inne informacje specyficzne dla źródła danych. Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz rozdział 5 w Windows SDK.

W przypadku próby nawiązania połączenia w celu przekroczenia limitu czasu, jeśli na przykład Host systemu DBMS jest niedostępny. Jeśli próba połączenia nie powiedzie się, program `Open` zgłosi wartość `CDBException` .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#14](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]

## <a name="cdatabaseopenex"></a><a name="openex"></a>CDatabase:: OpenEx

Wywołaj tę funkcję elementu członkowskiego, aby zainicjować nowo skonstruowany `CDatabase` obiekt.

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

- `CDatabase::openExclusive`Nieobsługiwane w tej wersji biblioteki klas. Źródło danych jest zawsze otwierane jako udostępnione (niewyłączne). Obecnie potwierdzenie kończy się niepowodzeniem w przypadku określenia tej opcji.

- `CDatabase::openReadOnly`Otwórz źródło danych jako tylko do odczytu.

- `CDatabase::useCursorLib`Załaduj bibliotekę DLL biblioteki kursora ODBC. Biblioteka kursorów maskuje pewne funkcje podstawowego sterownika ODBC, co skutecznie uniemożliwia korzystanie z zestawów dynamicznych (Jeśli sterownik ich obsługuje). Jedyne kursory obsługiwane, jeśli biblioteka kursorów jest załadowana, są migawkami statycznymi i kursorami progresywnymi. Jeśli planujesz utworzyć obiekt zestawu rekordów bezpośrednio z poziomu `CRecordset` tego programu, nie należy ładować biblioteki kursorów.

- `CDatabase::noOdbcDialog`Nie wyświetlaj okna dialogowego połączenie ODBC, niezależnie od tego, czy są podane wystarczające informacje o połączeniu.

- `CDatabase::forceOdbcDialog`Zawsze wyświetlaj okno dialogowe połączenie ODBC.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli połączenie zostało pomyślnie nawiązane; w przeciwnym razie, jeśli użytkownik wybierze przycisk Anuluj, gdy zostanie wyświetlone okno dialogowe z prośbą o dodatkowe informacje o połączeniu. We wszystkich innych przypadkach struktura zgłasza wyjątek.

### <a name="remarks"></a>Uwagi

Obiekt bazy danych musi zostać zainicjowany, aby można było używać go do konstruowania obiektu zestawu rekordów.

Jeśli parametr *lpszConnectString* w `OpenEx` wywołaniu nie zawiera wystarczającej ilości informacji do nawiązania połączenia, sterownik ODBC otwiera okno dialogowe umożliwiające uzyskanie niezbędnych informacji od użytkownika, pod warunkiem, że nie ustawiono lub nie określono `CDatabase::noOdbcDialog` `CDatabase::forceOdbcDialog` parametru *dwOptions* . Po wywołaniu `OpenEx` Parametry połączenia, *lpszConnectString*, są przechowywane prywatnie w `CDatabase` obiekcie i są dostępne przez wywołanie funkcji składowej [GetConnect](#getconnect) .

Jeśli chcesz, możesz otworzyć własne okno dialogowe przed wywołaniem, `OpenEx` Aby uzyskać informacje od użytkownika, takie jak hasło, a następnie dodać te informacje do parametrów połączenia, które są przekazywane `OpenEx` . Można też zapisać parametry połączenia, które zostały przekazane, aby można było użyć go ponownie podczas następnego wywołania aplikacji `OpenEx` na `CDatabase` obiekcie.

Można również użyć parametrów połączenia dla wielu poziomów autoryzacji logowania (dla różnych `CDatabase` obiektów) lub przekazać inne informacje specyficzne dla źródła danych. Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz rozdział 6 w *Kompendium ODBC Programmer's Reference*.

W przypadku próby nawiązania połączenia w celu przekroczenia limitu czasu, jeśli na przykład Host systemu DBMS jest niedostępny. Jeśli próba połączenia nie powiedzie się, program `OpenEx` zgłosi wartość `CDBException` .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#11](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]

## <a name="cdatabaserollback"></a><a name="rollback"></a>CDatabase:: Rollback

Wywołaj tę funkcję elementu członkowskiego, aby odwrócić zmiany wprowadzone w trakcie transakcji.

```
BOOL Rollback();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli transakcja została pomyślnie odwrócona; w przeciwnym razie 0. Jeśli `Rollback` wywołanie nie powiedzie się, źródło danych i Stany transakcji są niezdefiniowane. Jeśli `Rollback` zwraca wartość 0, należy sprawdzić źródło danych w celu określenia jego stanu.

### <a name="remarks"></a>Uwagi

Wszystkie `CRecordset` `AddNew` , `Edit` , `Delete` i `Update` wywołania wykonywane od momentu ostatniej [BeginTrans](#begintrans) są przywracane do stanu, który istniał w momencie tego wywołania.

Po wywołaniu transakcji jest on w trybie `Rollback` failover, a użytkownik musi ponownie wywołać `BeginTrans` inną transakcję. Rekord, który był aktualny przed wywołaniem `BeginTrans` , będzie ponownie bieżącym rekordem po `Rollback` .

Po wycofaniu rekord, który był aktualny przed wycofaniem, pozostaje aktualny. Aby uzyskać szczegółowe informacje o stanie zestawu rekordów i źródła danych po zakończeniu wycofywania, zobacz artykuł [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Przykład

  Zobacz artykuł [transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="cdatabasesetlogintimeout"></a><a name="setlogintimeout"></a>CDatabase:: SetLoginTimeout

Wywołaj tę funkcję elementu członkowskiego — przed wywołaniem `OpenEx` lub `Open` — Aby zastąpić domyślną liczbę sekund dozwoloną przed upływem limitu czasu połączenia ze źródłem danych.

```cpp
void SetLoginTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Parametry

*dwSeconds*<br/>
Liczba sekund, które mają być dozwolone przed upływem limitu czasu połączenia.

### <a name="remarks"></a>Uwagi

Próba połączenia może przekroczyć limit czasu, jeśli na przykład system DBMS nie jest dostępny. Wywołaj `SetLoginTimeout` po utworzeniu niezainicjowanego `CDatabase` obiektu, ale przed wywołaniem `OpenEx` lub `Open` .

Wartość domyślna dla limitów czasu logowania wynosi 15 sekund. Nie wszystkie źródła danych obsługują możliwość określania wartości limitu czasu logowania. Jeśli źródło danych nie obsługuje limitu czasu, uzyskasz wyniki śledzenia, ale nie wyjątek. Wartość 0 oznacza "nieskończone".

## <a name="cdatabasesetquerytimeout"></a><a name="setquerytimeout"></a>CDatabase:: SetQueryTimeout

Wywołaj tę funkcję elementu członkowskiego, aby zastąpić domyślną liczbę sekund dozwoloną przed upływem limitu czasu dla kolejnych operacji w połączonym źródle danych.

```cpp
void SetQueryTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Parametry

*dwSeconds*<br/>
Liczba sekund, które mają być dozwolone przed upływem limitu czasu zapytania.

### <a name="remarks"></a>Uwagi

Operacja może przekroczyć limit czasu, ponieważ występują problemy z dostępem do sieci, nadmierny czas przetwarzania zapytania i tak dalej. Wywołaj `SetQueryTimeout` przed otwarciem zestawu rekordów lub przed wywołaniem zestawu rekordów `AddNew` `Update` lub `Delete` funkcji Członkowskich, jeśli chcesz zmienić wartość limitu czasu zapytania. Ustawienie ma wpływ na wszystkie kolejne `Open` , `AddNew` , `Update` , i `Delete` wywołania do dowolnych zestawów rekordów skojarzonych z tym `CDatabase` obiektem. Zmiana wartości limitu czasu zapytania dla zestawu rekordów po otwarciu nie powoduje zmiany wartości zestawu rekordów. Na przykład kolejne `Move` operacje nie używają nowej wartości.

Wartość domyślna dla limitów czasu zapytania wynosi 15 sekund. Nie wszystkie źródła danych obsługują możliwość ustawiania wartości limitu czasu zapytania. Jeśli ustawisz wartość limitu czasu zapytania równy 0, nie zostanie przekroczony limit czasu. Komunikacja ze źródłem danych może przestać odpowiadać. Takie zachowanie może być przydatne podczas opracowywania. Jeśli źródło danych nie obsługuje limitu czasu, uzyskasz wyniki śledzenia, ale nie wyjątek.

## <a name="see-also"></a>Zobacz także

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)
