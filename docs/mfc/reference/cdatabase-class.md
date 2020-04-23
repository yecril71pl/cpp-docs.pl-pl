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
ms.openlocfilehash: bc920307e09179dc214710a3b6b19ff27a82749d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754641"
---
# <a name="cdatabase-class"></a>Klasa CDatabase

Reprezentuje połączenie ze źródłem danych, za pośrednictwem którego można działać na źródle danych.

## <a name="syntax"></a>Składnia

```
class CDatabase : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDatabase::CBazy danych](#cdatabase)|Konstruuje `CDatabase` obiekt. Obiekt należy zainicjować, `OpenEx` wywołując `Open`lub .|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDatabase::BeginTrans](#begintrans)|Uruchamia "transakcję" — serię odwracalnych wywołań `Edit` `Delete`do `Update` `AddNew`, , `CRecordset` i funkcji członkowskich klasy — na połączonym źródle danych. Źródło danych musi obsługiwać `BeginTrans` transakcje, aby mieć jakikolwiek wpływ.|
|[CDatabase::BindParameters](#bindparameters)|Umożliwia powiązanie parametrów `CDatabase::ExecuteSQL`przed wywołaniem .|
|[CDatabase::Anuluj](#cancel)|Anuluje operację asynchronizacyjną lub proces z drugiego wątku.|
|[CDatabase::CanTransact](#cantransact)|Zwraca wartość niezerową, jeśli źródło danych obsługuje transakcje.|
|[CDatabase::CanUpdate](#canupdate)|Zwraca wartość niezerową, `CDatabase` jeśli obiekt jest aktualizowany (nie tylko do odczytu).|
|[CDatabase::Zamknij](#close)|Zamyka połączenie ze źródłem danych.|
|[CDatabase::CommitTrans](#committrans)|Kończy transakcję rozpoczętą przez `BeginTrans`. Polecenia w transakcji, które zmieniają źródło danych są wykonywane.|
|[CDatabase::ExecuteSQL](#executesql)|Wykonuje instrukcję SQL. Nie są zwracane żadne rekordy danych.|
|[CDatabase::GetBookmarkPersistence](#getbookmarkpersistence)|Identyfikuje operacje, za pomocą których zakładki utrzymują się na obiektach pliku recordset.|
|[CDatabase::GetConnect](#getconnect)|Zwraca ciąg połączenia ODBC używany `CDatabase` do łączenia obiektu ze źródłem danych.|
|[CDatabase::GetCursorCommitBehavior](#getcursorcommitbehavior)|Identyfikuje wpływ zatwierdzania transakcji na otwarty obiekt aktu rekordów.|
|[CDatabase::GetCursorRollbackBehavior](#getcursorrollbackbehavior)|Identyfikuje wpływ wycofywania transakcji na otwarty obiekt aktu rekordów.|
|[CDatabase::GetDatabaseName](#getdatabasename)|Zwraca nazwę aktualnie używanej bazy danych.|
|[CDatabase::IsOpen](#isopen)|Zwraca wartość niezerową, `CDatabase` jeśli obiekt jest obecnie połączony ze źródłem danych.|
|[CDatabase::OnSetOptions](#onsetoptions)|Wywoływane przez strukturę, aby ustawić standardowe opcje połączenia. Domyślna implementacja ustawia wartość limitu czasu kwerendy. Można ustalić te opcje z `SetQueryTimeout`wyprzedzeniem, dzwoniąc .|
|[Cdatabase::open](#open)|Ustanawia połączenie ze źródłem danych (za pośrednictwem sterownika ODBC).|
|[CDatabase::OpenEx](#openex)|Ustanawia połączenie ze źródłem danych (za pośrednictwem sterownika ODBC).|
|[CDatabase::Wycofywanie](#rollback)|Odwraca zmiany wprowadzone podczas bieżącej transakcji. Źródło danych powraca do poprzedniego stanu, `BeginTrans` zgodnie z definicją w wywołaniu, bez ekstremów.|
|[CDatabase::SetLoginTimeout](#setlogintimeout)|Ustawia liczbę sekund, po których przesunie się czas połączenia źródła danych.|
|[CDatabase::SetQueryTimeout](#setquerytimeout)|Ustawia liczbę sekund, po których operacje kwerendy bazy danych upończe limit czasu. Wpływa na wszystkie `Open`kolejne `AddNew` `Edit`rekordy `Delete` , , i wywołania.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDatabase::m_hdbc](#m_hdbc)|Obsługa połączenia Open Database Connectivity (ODBC) ze źródłem danych. Wpisz *HDBC*.|

## <a name="remarks"></a>Uwagi

Źródło danych jest określonym wystąpieniem danych obsługiwanych przez niektóre systemy zarządzania bazami danych (DBMS). Przykłady obejmują microsoft SQL Server, Microsoft Access, Borland dBASE i xBASE. W aplikacji można `CDatabase` mieć jeden lub więcej obiektów aktywnych w czasie.

> [!NOTE]
> Jeśli pracujesz z klasami obiektów dostępu do danych (DAO), a nie z klasami Open Database Connectivity (ODBC), należy użyć klasy [CDaoDatabase.](../../mfc/reference/cdaodatabase-class.md) Aby uzyskać więcej informacji, zobacz artykuł [Omówienie: Programowanie baz danych](../../data/data-access-programming-mfc-atl.md).

Aby `CDatabase`użyć , `CDatabase` skonstruować `OpenEx` obiekt i wywołać jego funkcję elementu członkowskiego. Spowoduje to otwarcie połączenia. Podczas konstruowania `CRecordset` obiektów do pracy na połączonym źródle danych, przekazać `CDatabase` konstruktora zestaw rekordów wskaźnik do obiektu. Po zakończeniu korzystania z połączenia, wywołać `Close` `CDatabase` funkcję elementu członkowskiego i zniszczyć obiekt. `Close`zamyka wszystkie zestawy rekordów, które nie zostały wcześniej zamknięte.

Aby uzyskać `CDatabase`więcej informacji na temat , zobacz artykuły [Źródło danych (ODBC)](../../data/odbc/data-source-odbc.md) i [Przegląd: Programowanie baz danych](../../data/data-access-programming-mfc-atl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CDatabase`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="cdatabasebegintrans"></a><a name="begintrans"></a>CDatabase::BeginTrans

Wywołanie tej funkcji elementu członkowskiego, aby rozpocząć transakcję z połączonym źródłem danych.

```
BOOL BeginTrans();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wywołanie zakończyło się pomyślnie, a zmiany są zatwierdzane tylko ręcznie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Transakcja składa się z jednego `AddNew`lub `Edit` `Delete`więcej `Update` wywołań funkcji `CRecordset` , , i elementu członkowskiego obiektu. Przed rozpoczęciem transakcji `CDatabase` obiekt musi już być połączony ze źródłem danych, wywołując jego `OpenEx` lub `Open` funkcję elementu członkowskiego. Aby zakończyć transakcję, [wywołaj CommitTrans,](#committrans) aby zaakceptować wszystkie zmiany w źródle danych (i przeprowadzić je) lub wywołać [wycofywanie,](#rollback) aby przerwać całą transakcję. Wywołanie `BeginTrans` po otwarciu wszystkich rekordów zaangażowanych w transakcję i jak najbliżej rzeczywistych operacji aktualizacji, jak to możliwe.

> [!CAUTION]
> W zależności od sterownika ODBC otwarcie `BeginTrans` a recordset `Rollback`przed wywołaniem może powodować problemy podczas dzwonienia . Należy sprawdzić konkretny sterownik, którego używasz. Na przykład podczas korzystania ze sterownika programu Microsoft Access zawartego w pakiecie sterowników pulpitu Microsoft ODBC 3.0 należy uwzględnić wymagania aparatu bazy danych Jet, aby nie rozpoczynać transakcji w żadnej bazie danych z otwartym kursorem. W klasach bazy danych MFC otwarty kursor oznacza otwarty `CRecordset` obiekt. Aby uzyskać więcej informacji, zobacz [Uwaga techniczna 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md).

`BeginTrans`może również zablokować rekordy danych na serwerze, w zależności od żądanej współbieżności i możliwości źródła danych. Aby uzyskać informacje na temat blokowania danych, zobacz artykuł [Zestaw rekordów: Blokowanie rekordów (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).

Transakcje zdefiniowane przez użytkownika są wyjaśnione w artykule [Transakcja (ODBC)](../../data/odbc/transaction-odbc.md).

`BeginTrans`ustanawia stan, do którego sekwencja transakcji może zostać wycofana (odwrócona). Aby ustanowić nowy stan wycofywania, zatwierdz każdą `BeginTrans` bieżącą transakcję, a następnie wywołaj ponownie.

> [!CAUTION]
> Wywołanie `BeginTrans` ponownie `CommitTrans` `Rollback` bez wywoływania lub jest błędem.

Wywołanie [CanTransact](#cantransact) funkcji elementu członkowskiego, aby ustalić, czy sterownik obsługuje transakcje dla danej bazy danych. Należy również wywołać [GetCursorCommitBehavior](#getcursorcommitbehavior) i [GetCursorRollbackBehavior,](#getcursorrollbackbehavior) aby określić obsługę zachowania kursora.

Aby uzyskać więcej informacji o transakcjach, zobacz artykuł [Transakcja (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Przykład

  Zobacz artykuł [Transakcja: Wykonywanie transakcji w zajrzy (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="cdatabasebindparameters"></a><a name="bindparameters"></a>CDatabase::BindParameters

`BindParameters` Zastąp, gdy trzeba powiązać parametry przed wywołaniem [CDatabase::ExecuteSQL](#executesql).

```
virtual void BindParameters(HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*Hstmt*<br/>
Dojście instrukcji ODBC, dla których mają zostać powiązane parametry.

### <a name="remarks"></a>Uwagi

Takie podejście jest przydatne, gdy nie potrzebujesz zestawu wyników z procedury składowanej.

W zastąpienie wywołanie `SQLBindParameters` i powiązanych funkcji ODBC do powiązania parametrów. MFC wywołuje zastąpienie przed wywołaniem `ExecuteSQL`. Nie musisz dzwonić `SQLPrepare`; `ExecuteSQL` i `SQLExecDirect` niszczy *hstmt*, który jest używany tylko raz.

## <a name="cdatabasecancel"></a><a name="cancel"></a>CDatabase::Anuluj

Wywołanie tej funkcji elementu członkowskiego, aby zażądać, aby źródło danych anulowało operację asynchroniza w toku lub proces z drugiego wątku.

```cpp
void Cancel();
```

### <a name="remarks"></a>Uwagi

Należy zauważyć, że klasy ODBC MFC nie używają już przetwarzania asynchroniczne; aby wykonać operację asynchronizacyjną, należy bezpośrednio wywołać funkcję INTERFEJSU API ODBC [SQLSetConnectOption](/sql/odbc/reference/syntax/sqlsetconnectoption-function). Aby uzyskać więcej informacji, zobacz [Wykonanie asynchroniczne](/sql/odbc/reference/develop-app/asynchronous-execution).

## <a name="cdatabasecantransact"></a><a name="cantransact"></a>CDatabase::CanTransact

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy baza danych zezwala na transakcje.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli zestawy `CDatabase` rekordów przy użyciu tego obiektu zezwalają na transakcje; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać informacje o transakcjach, zobacz artykuł [Transakcja (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="cdatabasecanupdate"></a><a name="canupdate"></a>CDatabase::CanUpdate

Wywołanie tej funkcji elementu `CDatabase` członkowskiego, aby ustalić, czy obiekt zezwala na aktualizacje.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, `CDatabase` jeśli obiekt zezwala na aktualizacje; w przeciwnym razie 0, wskazując, że przeszedłeś true w `CDatabase` *bCzytylko* podczas otwarcia obiektu lub że samo źródło danych jest tylko do odczytu. Źródło danych jest tylko do odczytu, jeśli `SQLGetInfo` wywołanie funkcji INTERFEJSU API ODBC dla SQL_DATASOURCE_READ_ONLY zwraca "y".

### <a name="remarks"></a>Uwagi

Nie wszystkie sterowniki obsługują aktualizacje.

## <a name="cdatabasecdatabase"></a><a name="cdatabase"></a>CDatabase::CBazy danych

Konstruuje `CDatabase` obiekt.

```
CDatabase();
```

### <a name="remarks"></a>Uwagi

Po skonstruowaniu obiektu należy wywołać jego `OpenEx` lub `Open` element członkowski funkcji, aby ustanowić połączenie z określonym źródłem danych.

Zagoscjenie obiektu w `CDatabase` klasie dokumentu może okazać się wygodne.

### <a name="example"></a>Przykład

W tym przykładzie ilustruje przy użyciu `CDatabase` w klasie pochodnej. `CDocument`

[!code-cpp[NVC_MFCDatabase#9](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]

[!code-cpp[NVC_MFCDatabase#10](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]

## <a name="cdatabaseclose"></a><a name="close"></a>CDatabase::Zamknij

Wywołanie tej funkcji elementu członkowskiego, jeśli chcesz odłączyć się od źródła danych.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Przed wywołaniem `CDatabase` tej funkcji elementu członkowskiego należy zamknąć wszystkie zestawy rekordów skojarzone z obiektem. Ponieważ `Close` obiekt nie `CDatabase` niszczy obiektu, można ponownie użyć obiektu, otwierając nowe połączenie z tym samym źródłem danych lub innym źródłem danych.

Wszystkie `AddNew` oczekujące lub `Edit` instrukcje zestawień rekordów przy użyciu bazy danych są anulowane, a wszystkie oczekujące transakcje są przywracane. Wszystkie zestawy rekordów `CDatabase` zależne od obiektu pozostają w stanie niezdefiniowanym.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#12](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]

## <a name="cdatabasecommittrans"></a><a name="committrans"></a>CDatabase::CommitTrans

Wywołanie tej funkcji członka po zakończeniu transakcji.

```
BOOL CommitTrans();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli aktualizacje zostały pomyślnie zatwierdzone; w przeciwnym razie 0. Jeśli `CommitTrans` nie powiedzie się, stan źródła danych jest niezdefiniowany. Należy sprawdzić dane, aby określić jego stan.

### <a name="remarks"></a>Uwagi

Transakcja składa się z serii `AddNew`wywołań `Delete`, `Update` `Edit`, i `CRecordset` funkcji członkowskich obiektu, który rozpoczął się od wywołania funkcji elementu członkowskiego [BeginTrans.](#begintrans) `CommitTrans`zatwierdza transakcję. Domyślnie aktualizacje są zatwierdzane natychmiast; wywołanie `BeginTrans` powoduje, że zobowiązanie `CommitTrans` aktualizacji jest opóźnione, dopóki nie zostanie wywołana.

Dopóki nie `CommitTrans` wywołasz, aby zakończyć transakcję, można wywołać [rollback](#rollback) funkcji elementu członkowskiego, aby przerwać transakcję i pozostawić źródło danych w stanie pierwotnym. Aby rozpocząć nową transakcję, zadzwoń ponownie. `BeginTrans`

Aby uzyskać więcej informacji o transakcjach, zobacz artykuł [Transakcja (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Przykład

  Zobacz artykuł [Transakcja: Wykonywanie transakcji w zajrzy (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="cdatabaseexecutesql"></a><a name="executesql"></a>CDatabase::ExecuteSQL

Wywołanie tej funkcji elementu członkowskiego, gdy trzeba wykonać polecenie SQL bezpośrednio.

```cpp
void ExecuteSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>Parametry

*Lpszsql*<br/>
Wskaźnik do ciągu zakończonego zerem zawierającego prawidłowe polecenie SQL do wykonania. Można przekazać [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Uwagi

Utwórz polecenie jako ciąg zakończony z wartością null. `ExecuteSQL`nie zwraca rekordów danych. Jeśli chcesz działać na rekordach, użyj obiektu akcesji.

Większość poleceń dla źródła danych jest wydawana za pośrednictwem obiektów zestawów rekordów, które obsługują polecenia służące do wybierania danych, wstawiania nowych rekordów, usuwania rekordów i edytowania rekordów. Jednak nie wszystkie funkcje ODBC są bezpośrednio obsługiwane przez klasy bazy danych, więc czasami `ExecuteSQL`może być konieczne nawiązywać bezpośrednie połączenie SQL za pomocą programu .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#13](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]

## <a name="cdatabasegetbookmarkpersistence"></a><a name="getbookmarkpersistence"></a>CDatabase::GetBookmarkPersistence

Wywołanie tej funkcji elementu członkowskiego, aby określić trwałość zakładek na obiektu pliku recordset po niektórych operacjach.

```
DWORD GetBookmarkPersistence() const;
```

### <a name="return-value"></a>Wartość zwracana

Maska bitowa identyfikujący operacje, za pomocą których zakładki utrzymują się na obiektu pliku recordset. Aby uzyskać szczegółowe informacje, zobacz Uwagi.

### <a name="remarks"></a>Uwagi

Na przykład, jeśli `CRecordset::GetBookmark` zadzwonisz, a następnie `CRecordset::Requery` `GetBookmark` zadzwoń, zakładka uzyskana z może nie być już prawidłowa. Należy zadzwonić `GetBookmarkPersistence` `CRecordset::SetBookmark`przed wywołaniem .

W poniższej tabeli wymieniono wartości maski bitowej, które można połączyć dla wartości zwracanej `GetBookmarkPersistence`.

|Wartość maski bitów|Trwałość zakładki|
|-------------------|--------------------------|
|SQL_BP_CLOSE|Zakładki są prawidłowe `Requery` po operacji.|
|SQL_BP_DELETE|Zakładka dla wiersza jest `Delete` prawidłowa po operacji w tym wierszu.|
|SQL_BP_DROP|Zakładki są prawidłowe `Close` po operacji.|
|SQL_BP_SCROLL|Zakładki są prawidłowe `Move` po każdej operacji. To po prostu określa, czy zakładki są obsługiwane na `CRecordset::CanBookmark`rekordze, jak zwrócono przez .|
|SQL_BP_TRANSACTION|Zakładki są prawidłowe po zawiązanym lub wycofanym powrocie transakcji.|
|SQL_BP_UPDATE|Zakładka dla wiersza jest `Update` prawidłowa po operacji w tym wierszu.|
|SQL_BP_OTHER_HSTMT|Zakładki skojarzone z jednym obiektem aktu rekordów są prawidłowe w drugim zazestawie.|

Aby uzyskać więcej informacji na temat tej `SQLGetInfo` wartości zwracanej, zobacz funkcję interfejsu API ODBC w sdk systemu Windows. Aby uzyskać więcej informacji na temat zakładek, zobacz artykuł [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

## <a name="cdatabasegetconnect"></a><a name="getconnect"></a>CDatabase::GetConnect

Wywołanie tej funkcji elementu członkowskiego, aby pobrać `OpenEx` `Open` ciąg połączenia `CDatabase` używane podczas wywołania lub który połączył obiekt ze źródłem danych.

```
const CString GetConnect() const;
```

### <a name="return-value"></a>Wartość zwracana

**Const**[CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierający ciąg `OpenEx` połączenia, jeśli lub `Open` został wywołany; w przeciwnym razie pusty ciąg.

### <a name="remarks"></a>Uwagi

Zobacz [CDatabase::Otwórz](#open) opis sposobu tworzenia ciągu połączenia.

## <a name="cdatabasegetcursorcommitbehavior"></a><a name="getcursorcommitbehavior"></a>CDatabase::GetCursorCommitBehavior

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, jak [CommitTrans](#committrans) operacja wpływa na kursory na otwartych obiektów aktujów.

```
int GetCursorCommitBehavior() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość wskazująca wpływ transakcji na otwarte obiekty aktu rekordów. Aby uzyskać szczegółowe informacje, zobacz Uwagi.

### <a name="remarks"></a>Uwagi

W poniższej tabeli wymieniono możliwe wartości zwracane `GetCursorCommitBehavior` i odpowiadający im wpływ na otwarty zestawie rekordów.

|Wartość zwracana|Wpływ na obiekty CRecordset|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Wywołanie `CRecordset::Requery` bezpośrednio po zatwierdzeniu transakcji.|
|SQL_CB_DELETE|Wywołanie `CRecordset::Close` bezpośrednio po zatwierdzeniu transakcji.|
|SQL_CB_PRESERVE|Normalnie postępować `CRecordset` z operacjami.|

Aby uzyskać więcej informacji na temat tej `SQLGetInfo` wartości zwracanej, zobacz funkcję interfejsu API ODBC w sdk systemu Windows. Aby uzyskać więcej informacji o transakcjach, zobacz artykuł [Transakcja (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="cdatabasegetcursorrollbackbehavior"></a><a name="getcursorrollbackbehavior"></a>CDatabase::GetCursorRollbackBehavior

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, jak operacja [wycofywania](#rollback) wpływa na kursory na otwartych obiektach zestawie rekordów.

```
int GetCursorRollbackBehavior() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość wskazująca wpływ transakcji na otwarte obiekty aktu rekordów. Aby uzyskać szczegółowe informacje, zobacz Uwagi.

### <a name="remarks"></a>Uwagi

W poniższej tabeli wymieniono możliwe wartości zwracane `GetCursorRollbackBehavior` i odpowiadający im wpływ na otwarty zestawie rekordów.

|Wartość zwracana|Wpływ na obiekty CRecordset|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Wywołanie `CRecordset::Requery` bezpośrednio po wycofywaniu transakcji.|
|SQL_CB_DELETE|Wywołanie `CRecordset::Close` bezpośrednio po wycofywaniu transakcji.|
|SQL_CB_PRESERVE|Normalnie postępować `CRecordset` z operacjami.|

Aby uzyskać więcej informacji na temat tej `SQLGetInfo` wartości zwracanej, zobacz funkcję interfejsu API ODBC w sdk systemu Windows. Aby uzyskać więcej informacji o transakcjach, zobacz artykuł [Transakcja (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="cdatabasegetdatabasename"></a><a name="getdatabasename"></a>CDatabase::GetDatabaseName

Wywołanie tej funkcji elementu członkowskiego, aby pobrać nazwę aktualnie połączonej bazy danych (pod warunkiem, że źródło danych definiuje nazwany obiekt o nazwie "baza danych").

```
CString GetDatabaseName() const;
```

### <a name="return-value"></a>Wartość zwracana

[CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierający nazwę bazy danych, jeśli zakończy się pomyślnie; w przeciwnym `CString`razie pusty plik .

### <a name="remarks"></a>Uwagi

To nie jest taka sama jak nazwa źródła danych `OpenEx` `Open` (DSN) określona w lub wywołania. Co `GetDatabaseName` zwraca zależy od ODBC. Ogólnie rzecz biorąc baza danych jest zbiorem tabel. Jeśli ta jednostka ma `GetDatabaseName` nazwę, zwraca ją.

Można na przykład wyświetlić tę nazwę w nagłówku. Jeśli podczas pobierania nazwy z odbc `GetDatabaseName` wystąpi błąd, zwraca pusty `CString`plik .

## <a name="cdatabaseisopen"></a><a name="isopen"></a>CDatabase::IsOpen

Wywołanie tej funkcji elementu `CDatabase` członkowskiego, aby ustalić, czy obiekt jest obecnie połączony ze źródłem danych.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, `CDatabase` jeśli obiekt jest aktualnie podłączony; w przeciwnym razie 0.

## <a name="cdatabasem_hdbc"></a><a name="m_hdbc"></a>CDatabase::m_hdbc

Zawiera publiczny dojście do połączenia ze źródłem danych ODBC — "dojście połączenia".

### <a name="remarks"></a>Uwagi

Zwykle nie trzeba będzie bezpośrednio uzyskiwać dostępu do tej zmiennej członkowskiej. Zamiast tego struktura przydziela dojście `OpenEx` podczas `Open`wywoływania lub . Struktura deallokuje dojście podczas **delete** wywoływania `CDatabase` delete operator na obiekcie. Należy zauważyć, że funkcja `Close` elementu członkowskiego nie przydzieli alokacji dojścia.

W pewnych okolicznościach może być jednak konieczne użycie uchwytu bezpośrednio. Na przykład, jeśli trzeba wywołać funkcje INTERFEJSU API `CDatabase`ODBC bezpośrednio, a nie za pośrednictwem klasy, może być konieczne dojście połączenia do przekazania jako parametr. Zobacz przykład kodu poniżej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#15](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]

## <a name="cdatabaseonsetoptions"></a><a name="onsetoptions"></a>CDatabase::OnSetOptions

Struktura wywołuje tę funkcję elementu członkowskiego podczas bezpośredniego `ExecuteSQL` wykonywania instrukcji SQL z funkcją elementu członkowskiego.

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*Hstmt*<br/>
Dojście instrukcji ODBC, dla których są ustawiane opcje.

### <a name="remarks"></a>Uwagi

`CRecordset::OnSetOptions`wywołuje również tę funkcję członkową.

`OnSetOptions`ustawia wartość limitu czasu logowania. Jeśli były poprzednie wywołania `SetQueryTimeout` funkcji i `OnSetOptions` elementu członkowskiego, odzwierciedla bieżące wartości; w przeciwnym razie ustawia wartości domyślne.

> [!NOTE]
> Przed MFC 4.2, `OnSetOptions` również ustawić tryb przetwarzania na snychronous lub asynchronous. Począwszy od MFC 4.2, wszystkie operacje są synchroniczne. Aby wykonać operację asynchronizacyjną, należy wykonać bezpośrednie wywołanie funkcji `SQLSetPos`interfejsu API ODBC.

Nie trzeba `OnSetOptions` zastępować, aby zmienić wartość limitu czasu. Zamiast tego, aby dostosować wartość limitu `SetQueryTimeout` czasu kwerendy, wywołanie przed utworzeniem a recordset; `OnSetOptions` użyje nowej wartości. Ustawione wartości dotyczą kolejnych operacji we wszystkich zestawach rekordów lub bezpośrednich wywołaniach SQL.

Zastąd, `OnSetOptions` jeśli chcesz ustawić dodatkowe opcje. Zastąpienie należy wywołać klasę `OnSetOptions` podstawową przed lub po wywołaniu `SQLSetStmtOption`funkcji interfejsu API ODBC . Postępuj zgodnie z metodą zilustrowane `OnSetOptions`w domyślnej implementacji struktury .

## <a name="cdatabaseopen"></a><a name="open"></a>Cdatabase::open

Wywołanie tej funkcji elementu członkowskiego, `CDatabase` aby zainicjować nowo skonstruowany obiekt.

```
virtual BOOL Open(
    LPCTSTR lpszDSN,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T("ODBC;"),
    BOOL bUseCursorLib = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszdsn*<br/>
Określa nazwę źródła danych — nazwę zarejestrowaną w odbc za pośrednictwem programu Administrator ODBC. Jeśli wartość DSN jest określona w *lpszConnect* (w postaci "DSN=\<data-source>"), nie może być określona ponownie w *lpszDSN*. W takim przypadku *lpszDSN* powinna mieć wartość NULL. W przeciwnym razie można przekazać null, jeśli chcesz przedstawić użytkownikowi okno dialogowe Źródło danych, w którym użytkownik może wybrać źródło danych. Aby uzyskać więcej informacji, zobacz Uwagi.

*bWyłącze*<br/>
Nie jest obsługiwana w tej wersji biblioteki klas. Obecnie asercja kończy się niepowodzeniem, jeśli ten parametr ma wartość TRUE. Źródło danych jest zawsze otwierane jako udostępnione (nie wyłączne).

*bCzytyNie*<br/>
PRAWDA, jeśli chcesz, aby połączenie było tylko do odczytu i zabronić aktualizacji źródła danych. Wszystkie zależne zestawy rekordów dziedziczą ten atrybut. Wartością domyślną jest FAŁSZ.

*lpszConnect*<br/>
Określa parametry połączenia. Ciąg połączenia łączy informacje, ewentualnie w tym nazwę źródła danych, identyfikator użytkownika prawidłowy w źródle danych, ciąg uwierzytelniania użytkownika (hasło, jeśli źródło danych wymaga jednego) i inne informacje. Cały ciąg połączenia musi być poprzedzony ciągiem "ODBC;" (wielkie lub małe litery). Ciąg "ODBC;" jest używany do wskazania, że połączenie jest ze źródłem danych ODBC; jest to dla zgodności w górę, gdy przyszłe wersje biblioteki klas może obsługiwać źródła danych innych niż ODBC.

*bUchujCursorLib*<br/>
PRAWDA, jeśli chcesz załadować bibliotekę DLL biblioteki kursora ODBC. Biblioteka kursorów maskuje niektóre funkcje podstawowego sterownika ODBC, skutecznie zapobiegając używaniu zestawów dynamiki (jeśli sterownik je obsługuje). Tylko kursory obsługiwane, jeśli biblioteka kursor jest ładowany są migawki statyczne i tylko do przodu kursory. Wartością domyślną jest PRAWDA. Jeśli zamierzasz utworzyć obiekt pliku recordset bezpośrednio z `CRecordset` niego bez wyprowadzania z niego, nie należy ładować biblioteki kursorów.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli połączenie zostanie pomyślnie wykonane; w przeciwnym razie 0, jeśli użytkownik wybierze Anuluj po wyświetleniu okna dialogowego z prośbą o więcej informacji o połączeniu. We wszystkich innych przypadkach struktura zgłasza wyjątek.

### <a name="remarks"></a>Uwagi

Obiekt bazy danych musi zostać zainicjowany, zanim będzie można go użyć do skonstruowania obiektu pliku recordset.

> [!NOTE]
> Wywołanie funkcji elementu członkowskiego [OpenEx](#openex) jest preferowanym sposobem łączenia się ze źródłem danych i inicjowania obiektu bazy danych.

Jeśli parametry w `Open` wywołaniu nie zawierają wystarczającej ilości informacji, aby nawiązać połączenie, sterownik ODBC otwiera okno dialogowe w celu uzyskania niezbędnych informacji od użytkownika. Połączenie `Open`, parametry *połączenia, lpszConnect*, jest przechowywane `CDatabase` prywatnie w obiekcie i jest dostępne przez wywołanie funkcji elementu członkowskiego [GetConnect.](#getconnect)

Jeśli chcesz, możesz otworzyć własne okno dialogowe przed wywołaniem, `Open` aby uzyskać informacje od użytkownika, takie jak `Open`hasło, a następnie dodać te informacje do ciągu połączenia, który przekazujesz do programu . Lub można zapisać parametry połączenia, które przekazujesz, dzięki czemu można `Open` go `CDatabase` ponownie użyć następnym razem, gdy aplikacja wywołuje obiekt.

Można również użyć ciągu połączenia dla wielu poziomów autoryzacji `CDatabase` logowania (każdy dla innego obiektu) lub do przekazywania innych informacji specyficznych dla źródła danych. Aby uzyskać więcej informacji na temat ciągów połączeń, zobacz rozdział 5 w sdk systemu Windows.

Jest możliwe dla próby połączenia limit czasu, jeśli, na przykład, host DBMS jest niedostępny. Jeśli próba połączenia `Open` nie powiedzie się, zgłasza plik `CDBException`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#14](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]

## <a name="cdatabaseopenex"></a><a name="openex"></a>CDatabase::OpenEx

Wywołanie tej funkcji elementu członkowskiego, `CDatabase` aby zainicjować nowo skonstruowany obiekt.

```
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,
    DWORD dwOptions = 0);
```

### <a name="parameters"></a>Parametry

*lpszConnectString*<br/>
Określa parametry połączenia ODBC. Obejmuje to nazwę źródła danych, a także inne opcjonalne informacje, takie jak identyfikator użytkownika i hasło. Na przykład "DSN=SQLServer_Source; UID=SA; PWD=abc123" jest możliwym ciągiem połączenia. Należy zauważyć, że jeśli zostanie przegłosowane NULL dla *lpszConnectString*, okno dialogowe Źródło danych wyświetli monit o wybranie źródła danych.

*Dwoptions*<br/>
Maska bitowa określająca kombinację następujących wartości. Wartość domyślna to 0, co oznacza, że baza danych zostanie otwarta jako udostępniona z dostępem do zapisu, biblioteka DLL biblioteki kursora ODBC nie zostanie załadowana, a okno dialogowe połączenia ODBC będzie wyświetlane tylko wtedy, gdy nie ma wystarczającej ilości informacji do nawiązania połączenia.

- `CDatabase::openExclusive`Nie jest obsługiwana w tej wersji biblioteki klas. Źródło danych jest zawsze otwierane jako udostępnione (nie wyłączne). Obecnie asercja kończy się niepowodzeniem, jeśli określisz tę opcję.

- `CDatabase::openReadOnly`Otwórz źródło danych jako tylko do odczytu.

- `CDatabase::useCursorLib`Załaduj bibliotekę DLL biblioteki kursora ODBC. Biblioteka kursorów maskuje niektóre funkcje podstawowego sterownika ODBC, skutecznie zapobiegając używaniu zestawów dynamiki (jeśli sterownik je obsługuje). Tylko kursory obsługiwane, jeśli biblioteka kursor jest ładowany są migawki statyczne i tylko do przodu kursory. Jeśli zamierzasz utworzyć obiekt pliku recordset bezpośrednio z `CRecordset` niego bez wyprowadzania z niego, nie należy ładować biblioteki kursorów.

- `CDatabase::noOdbcDialog`Nie wyświetlaj okna dialogowego połączenia ODBC, niezależnie od tego, czy podano wystarczającą ilość informacji o połączeniu.

- `CDatabase::forceOdbcDialog`Zawsze wyświetlaj okno dialogowe połączenia ODBC.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli połączenie zostanie pomyślnie wykonane; w przeciwnym razie 0, jeśli użytkownik wybierze Anuluj po wyświetleniu okna dialogowego z prośbą o więcej informacji o połączeniu. We wszystkich innych przypadkach struktura zgłasza wyjątek.

### <a name="remarks"></a>Uwagi

Obiekt bazy danych musi zostać zainicjowany, zanim będzie można go użyć do skonstruowania obiektu pliku recordset.

Jeśli parametr *lpszConnectString* `OpenEx` w wywołaniu nie zawiera wystarczających informacji do nawiązania połączenia, sterownik ODBC otwiera okno dialogowe `CDatabase::noOdbcDialog` `CDatabase::forceOdbcDialog` w celu uzyskania niezbędnych informacji od użytkownika, pod warunkiem, że nie zostały ustawione lub w parametrze *dwOptions.* Połączenie `OpenEx`, parametry połączenia, *lpszConnectString*, jest przechowywane `CDatabase` prywatnie w obiekcie i jest dostępne przez wywołanie funkcji elementu członkowskiego [GetConnect.](#getconnect)

Jeśli chcesz, możesz otworzyć własne okno dialogowe przed wywołaniem, `OpenEx` aby uzyskać informacje od użytkownika, takie jak hasło, a następnie dodać te informacje do ciągu połączenia, który przechodzisz do `OpenEx`programu . Lub można zapisać parametry połączenia, które przekazujesz, dzięki czemu można `OpenEx` go `CDatabase` ponownie użyć następnym razem, gdy aplikacja wywołuje obiekt.

Można również użyć ciągu połączenia dla wielu poziomów autoryzacji `CDatabase` logowania (każdy dla innego obiektu) lub do przekazywania innych informacji specyficznych dla źródła danych. Aby uzyskać więcej informacji na temat ciągów połączeń, zobacz rozdział 6 w *odwołaniu programisty ODBC*.

Jest możliwe dla próby połączenia limit czasu, jeśli, na przykład, host DBMS jest niedostępny. Jeśli próba połączenia `OpenEx` nie powiedzie się, zgłasza plik `CDBException`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#11](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]

## <a name="cdatabaserollback"></a><a name="rollback"></a>CDatabase::Wycofywanie

Wywołanie tej funkcji elementu członkowskiego, aby odwrócić zmiany wprowadzone podczas transakcji.

```
BOOL Rollback();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli transakcja została pomyślnie wycofana; w przeciwnym razie 0. Jeśli `Rollback` wywołanie nie powiedzie się, źródło danych i stany transakcji są niezdefiniowane. Jeśli `Rollback` zwraca 0, należy sprawdzić źródło danych, aby określić jego stan.

### <a name="remarks"></a>Uwagi

Wszystkie `CRecordset` `AddNew` `Edit`, `Delete`, `Update` i wywołania wykonywane od ostatniego [BeginTrans](#begintrans) są przywracane do stanu, który istniał w czasie tego wywołania.

Po wywołaniu `Rollback`transakcji transakcja jest skończonią `BeginTrans` i należy ponownie zadzwonić do innej transakcji. Rekord, który był aktualny `BeginTrans` przed wywołaniem `Rollback`staje się bieżącym rekordem ponownie po .

Po wycofywaniu rekord, który był aktualny przed wycofaniem pozostaje aktualny. Aby uzyskać szczegółowe informacje na temat stanu zestawie rekordów i źródła danych po wycofywaniu, zobacz artykuł [Transakcja (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Przykład

  Zobacz artykuł [Transakcja: Wykonywanie transakcji w zajrzy (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="cdatabasesetlogintimeout"></a><a name="setlogintimeout"></a>CDatabase::SetLoginTimeout

Wywołanie tej funkcji elementu `OpenEx` `Open` członkowskiego — przed wywołaniem lub — aby zastąpić domyślną liczbę sekund dozwoloną przed przesuniem czasu połączenia ze źródłem danych.

```cpp
void SetLoginTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Parametry

*dwSekundy*<br/>
Liczba sekund, aby zezwolić przed zakończeniem próby połączenia.

### <a name="remarks"></a>Uwagi

Próba połączenia może się przekreślić, jeśli na przykład system dbms nie jest dostępny. Wywołaj `SetLoginTimeout` po skonstruowaniu niezainicjowanego obiektu, `CDatabase` ale przed wywołaniem `OpenEx` lub `Open`.

Domyślna wartość limitów czasu logowania wynosi 15 sekund. Nie wszystkie źródła danych obsługują możliwość określenia wartości limitu czasu logowania. Jeśli źródło danych nie obsługuje limitu czasu, otrzymasz dane wyjściowe śledzenia, ale nie wyjątek. Wartość 0 oznacza "nieskończoną".

## <a name="cdatabasesetquerytimeout"></a><a name="setquerytimeout"></a>CDatabase::SetQueryTimeout

Wywołanie tej funkcji elementu członkowskiego, aby zastąpić domyślną liczbę sekund, aby zezwolić przed kolejnymi operacjami na połączonym źródle danych limit czasu.

```cpp
void SetQueryTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Parametry

*dwSekundy*<br/>
Liczba sekund, aby zezwolić przed kwerendy próby przesunięcia.

### <a name="remarks"></a>Uwagi

Operacja może się przeterminować z powodu problemów z dostępem do sieci, nadmiernego czasu przetwarzania zapytań i tak dalej. `SetQueryTimeout` Wywołanie przed otwarciem pliku recordset lub przed `AddNew` `Update` wywołaniem funkcji , lub `Delete` elementu członkowskiego w programie Recordset, jeśli chcesz zmienić wartość limitu czasu kwerendy. Ustawienie ma wpływ `Open`na `AddNew` `Update`wszystkie `Delete` kolejne , , i wywołuje `CDatabase` wszystkie zestawy rekordów skojarzone z tym obiektem. Zmiana wartości limitu czasu kwerendy dla pliku recordset po otwarciu nie powoduje zmiany wartości dla pliku recordset. Na przykład `Move` kolejne operacje nie używają nowej wartości.

Domyślna wartość limitów czasu kwerendy wynosi 15 sekund. Nie wszystkie źródła danych obsługują możliwość ustawienia wartości limitu czasu kwerendy. Jeśli ustawisz wartość limitu czasu kwerendy 0, nie występuje limit czasu; komunikacja ze źródłem danych może przestać odpowiadać. To zachowanie może być przydatne podczas tworzenia. Jeśli źródło danych nie obsługuje limitu czasu, otrzymasz dane wyjściowe śledzenia, ale nie wyjątek.

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)
