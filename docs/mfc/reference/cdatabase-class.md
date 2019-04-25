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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62253717"
---
# <a name="cdatabase-class"></a>Klasa CDatabase

Reprezentuje połączenie ze źródłem danych, dzięki któremu można działać na źródle danych.

## <a name="syntax"></a>Składnia

```
class CDatabase : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDatabase::CDatabase](#cdatabase)|Konstruuje `CDatabase` obiektu. Należy zainicjować obiektu przez wywołanie metody `OpenEx` lub `Open`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDatabase::BeginTrans](#begintrans)|Rozpoczyna się "transakcji" — szereg wywołań odwracalnego `AddNew`, `Edit`, `Delete`, i `Update` funkcji elementów członkowskich klasy `CRecordset` — na połączonego źródła danych. Źródło danych musi obsługiwać następującą liczbę transakcji: `BeginTrans` mieć żadnego efektu.|
|[CDatabase::BindParameters](#bindparameters)|Umożliwia to powiązanie parametrów przed wywołaniem `CDatabase::ExecuteSQL`.|
|[CDatabase::Cancel](#cancel)|Anulowanie operacji asynchronicznej lub proces z drugiego wątku.|
|[CDatabase::CanTransact](#cantransact)|Zwraca wartość różną od zera, jeśli źródło danych obsługuje transakcji.|
|[CDatabase::CanUpdate](#canupdate)|Zwraca wartość różną od zera, jeśli `CDatabase` nadaje obiektu (nie tylko do odczytu).|
|[CDatabase::Close](#close)|Zamyka połączenia ze źródłem danych.|
|[CDatabase::CommitTrans](#committrans)|Kończy transakcji rozpoczyna się od `BeginTrans`. Polecenia w transakcji, zmienić źródła danych są wykonywane.|
|[CDatabase::ExecuteSQL](#executesql)|Wykonuje instrukcję SQL. Nie zwrócono żadnych rekordów danych.|
|[CDatabase::GetBookmarkPersistence](#getbookmarkpersistence)|Identyfikuje operacji za pomocą których zakładki utrwalania obiektów zestawu rekordów.|
|[CDatabase::GetConnect](#getconnect)|Zwraca ciąg połączenia ODBC używane do łączenia z `CDatabase` obiektu ze źródłem danych.|
|[CDatabase::GetCursorCommitBehavior](#getcursorcommitbehavior)|Określa efekt Zatwierdzanie transakcji na obiekcie otwarty zestaw rekordów.|
|[CDatabase::GetCursorRollbackBehavior](#getcursorrollbackbehavior)|Określa efekt wycofywania transakcji na obiekcie otwarty zestaw rekordów.|
|[CDatabase::GetDatabaseName](#getdatabasename)|Zwraca nazwę bazy danych obecnie w użyciu.|
|[CDatabase::IsOpen](#isopen)|Zwraca wartość różną od zera, jeśli `CDatabase` obiektu jest obecnie połączony ze źródłem danych.|
|[CDatabase::OnSetOptions](#onsetoptions)|Metoda wywoływana przez platformę, by ustawić opcje standardowego połączenia. Domyślna implementacja ustawia wartość limitu czasu zapytania. Te opcje wcześniej, można ustanowić przez wywołanie metody `SetQueryTimeout`.|
|[CDatabase::Open](#open)|Nawiązuje połączenie ze źródłem danych (za pośrednictwem sterownika ODBC).|
|[CDatabase::OpenEx](#openex)|Nawiązuje połączenie ze źródłem danych (za pośrednictwem sterownika ODBC).|
|[CDatabase::Rollback](#rollback)|Odwraca zmiany wprowadzone podczas bieżącej transakcji. Źródło danych zwróci do jego poprzedniego stanu, zgodnie z definicją w `BeginTrans` wywołania w niezmienionej formie.|
|[CDatabase::SetLoginTimeout](#setlogintimeout)|Ustawia liczbę sekund, po upływie których próby połączenia źródła danych przekroczy limit czasu.|
|[CDatabase::SetQueryTimeout](#setquerytimeout)|Ustawia liczbę sekund, po której bazy danych zapytania operacje przekroczy limit czasu. Ma wpływ na wszystkie kolejne rekordów `Open`, `AddNew`, `Edit`, i `Delete` wywołania.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDatabase::m_hdbc](#m_hdbc)|Open Database Connectivity (ODBC) dojścia połączenia ze źródłem danych. Typ *HDBC*.|

## <a name="remarks"></a>Uwagi

Źródło danych jest określone wystąpienie danych hostowanych przez niektóre system zarządzania bazami danych (DBMS). Przykłady obejmują programu Microsoft SQL Server, Microsoft Access, Borland dBASE i języka xBASE. Może mieć co najmniej jeden `CDatabase` obiekty aktywne w czasie w aplikacji.

> [!NOTE]
>  Jeśli pracujesz z klas obiektów dostępu do danych (DAO), a nie klasy Open Database Connectivity (ODBC), należy użyć klasy [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) zamiast tego. Aby uzyskać więcej informacji, zobacz artykuł [omówienie: Baza danych programowania](../../data/data-access-programming-mfc-atl.md).

Aby użyć `CDatabase`, konstruowania `CDatabase` obiektu, a następnie wywołać jej `OpenEx` funkcja elementu członkowskiego. Spowoduje to otwarcie połączenia. Gdy następnie konstruowania `CRecordset` obiektów zasilany połączonego źródła danych, Przekaż Konstruktora zestawu rekordów, wskaźnik do Twojej `CDatabase` obiektu. Po zakończeniu wprowadzania zmian przy użyciu połączenia, należy wywołać `Close` element członkowski funkcji i zniszcz `CDatabase` obiektu. `Close` Zamyka wszystkie zestawy rekordów, które wcześniej nie zostało zamknięte.

Aby uzyskać więcej informacji na temat `CDatabase`, zobacz artykuły [źródła danych (ODBC)](../../data/odbc/data-source-odbc.md) i [omówienie: Baza danych programowania](../../data/data-access-programming-mfc-atl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CDatabase`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

##  <a name="begintrans"></a>  CDatabase::BeginTrans

Wywołaj tę funkcję elementu członkowskiego, aby rozpocząć transakcji z połączonego źródła danych.

```
BOOL BeginTrans();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli wywołanie zakończyło się pomyślnie, a zmiany zostaną zatwierdzone tylko ręcznie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Transakcja składa się z jednego lub wielu wywołań do `AddNew`, `Edit`, `Delete`, i `Update` funkcje elementów członkowskich `CRecordset` obiektu. Przed rozpoczęciem transakcji, `CDatabase` obiektu powinny już być podłączone do źródła danych przez wywołanie jego `OpenEx` lub `Open` funkcja elementu członkowskiego. Aby zakończyć transakcji, należy wywołać [CommitTrans](#committrans) Zaakceptuj wszystkie zmiany do źródła danych (i ich wykonania) lub zadzwoń [wycofywania](#rollback) przerwania cała transakcja. Wywołaj `BeginTrans` po Otwórz żadnych zestawów rekordów biorących udział w transakcji, a w pobliżu rzeczywiste aktualizacji operacji jak to możliwe.

> [!CAUTION]
>  W zależności od sterownika ODBC, otwierając zestaw rekordów przed wywołaniem `BeginTrans` mogą powodować problemy podczas wywoływania `Rollback`. Należy sprawdzić określonego sterownika, którego używasz. Na przykład gdy za pomocą sterownika Microsoft Access, należącym do firmy Microsoft 3.0 pakiet sterownika pulpitu ODBC, należy uwzględnić wymagania aparatu bazy danych Jet nie powinna rozpoczynać transakcji na dowolnej bazy danych, który ma otwartego kursora. W klas baz danych MFC, otwartego kursora oznacza, że otwartą `CRecordset` obiektu. Aby uzyskać więcej informacji, zobacz [techniczne 68 Uwaga](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md).

`BeginTrans` również może zablokować rekordów danych na serwerze, w zależności od żądanej współbieżność i możliwości źródła danych. Dla informacji na temat blokowania danych, zobacz artykuł [zestaw rekordów: Blokowanie rekordów (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).

Zdefiniowane przez użytkownika transakcje są wyjaśnione w artykule [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).

`BeginTrans` ustanawia stanu, w którym sekwencja transakcji można wycofać (odwrotne). Aby ustanowić nowy stan wycofywanie zmian, zatwierdzenia dowolnej bieżącej transakcji następnie wywołać `BeginTrans` ponownie.

> [!CAUTION]
>  Wywoływanie `BeginTrans` ponownie bez wywoływania `CommitTrans` lub `Rollback` , występuje błąd.

Wywołaj [CanTransact](#cantransact) funkcja elementu członkowskiego, aby ustalić, czy sterownik obsługuje transakcji określonej bazy danych. Należy także wywołać [GetCursorCommitBehavior](#getcursorcommitbehavior) i [GetCursorRollbackBehavior](#getcursorrollbackbehavior) ustalenie, pomoc techniczna dotycząca zachowania kursora.

Aby uzyskać więcej informacji na temat transakcji, zobacz artykuł [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Przykład

  Zapoznaj się z artykułem [transakcji: Wykonywanie transakcji w zestawie rekordów (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="bindparameters"></a>  CDatabase::BindParameters

Zastąp `BindParameters` niezbędne, aby powiązać parametry przed wywołaniem [CDatabase::ExecuteSQL](#executesql).

```
virtual void BindParameters(HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*hstmt*<br/>
Dojście instrukcji ODBC, dla którego chcesz powiązać parametry.

### <a name="remarks"></a>Uwagi

To podejście jest przydatne w przypadku, gdy nie ma potrzeby wynik z procedury składowanej.

W przypadku przesłonięcia, wywołaj `SQLBindParameters` i pokrewne funkcje ODBC do powiązania parametrów. MFC wywołuje przesłonięcia przed wywołania do `ExecuteSQL`. Nie trzeba wywoływać `SQLPrepare`; `ExecuteSQL` wywołania `SQLExecDirect` i niszczy *hstmt*, która jest używana tylko raz.

##  <a name="cancel"></a>  CDatabase::Cancel

Wywołaj tę funkcję elementu członkowskiego, aby zażądać, że źródło danych anulować operację asynchroniczną w toku lub proces z drugiego wątku.

```
void Cancel();
```

### <a name="remarks"></a>Uwagi

Pamiętaj, że klasach MFC ODBC nie jest już używać asynchronicznego przetwarzania; Aby wykonać operację asynchroniczną, musi bezpośrednio wywoływać funkcję interfejsu API ODBC [SQLSetConnectOption](/sql/odbc/reference/syntax/sqlsetconnectoption-function). Aby uzyskać więcej informacji, zobacz [wykonanie asynchroniczne](/sql/odbc/reference/develop-app/asynchronous-execution).

##  <a name="cantransact"></a>  CDatabase::CanTransact

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy baza danych umożliwia transakcji.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość różną od zera zestawów rekordów za pomocą tego `CDatabase` obiektu zezwala na transakcje; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać informacje dotyczące transakcji, zobacz artykuł [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="canupdate"></a>  CDatabase::CanUpdate

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy `CDatabase` obiektu zezwala na aktualizacje.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość różną od zera `CDatabase` obiektu zezwala na aktualizacje; w przeciwnym razie 0, wskazujący, że administrator przekazać wartość TRUE w *bReadOnly* po otwarciu `CDatabase` obiektu lub że źródła danych, sama jest tylko do odczytu. Źródło danych jest tylko do odczytu wywołanie funkcji interfejsu API ODBC `SQLGetInfo` dla SQL_DATASOURCE_READ_ONLY zwraca "y".

### <a name="remarks"></a>Uwagi

Nie wszystkie sterowniki obsługują aktualizacje.

##  <a name="cdatabase"></a>  CDatabase::CDatabase

Konstruuje `CDatabase` obiektu.

```
CDatabase();
```

### <a name="remarks"></a>Uwagi

Po konstruowanie obiektu, należy wywołać jej `OpenEx` lub `Open` funkcja elementu członkowskiego do ustanowienia połączenia z określonym źródłem danych.

Może okazać się wygodne do osadzenia `CDatabase` obiektów w klasie dokumentów.

### <a name="example"></a>Przykład

Ten przykład ilustruje użycie `CDatabase` w `CDocument`-klasy pochodnej.

[!code-cpp[NVC_MFCDatabase#9](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]

[!code-cpp[NVC_MFCDatabase#10](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]

##  <a name="close"></a>  CDatabase::Close

Wywołaj tę funkcję elementu członkowskiego, jeśli chcesz odłączyć od źródła danych.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Należy zamknąć wszystkie zestawie rekordów skojarzonych z `CDatabase` obiekt przed wywołaniem tej funkcji elementu członkowskiego. Ponieważ `Close` nie niszczy `CDatabase` obiektu, można ponownie użyć obiektu przez otwarcie nowego połączenia do tego samego źródła danych lub innego źródła danych.

Wszystkie oczekujące `AddNew` lub `Edit` instrukcji zestawów rekordów przy użyciu bazy danych, zostaną anulowane, a wszystkie oczekujące transakcje są wycofywane. Wszystkie zestawy rekordów zależne od `CDatabase` obiektu pozostają w stanie niezdefiniowane.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#12](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]

##  <a name="committrans"></a>  CDatabase::CommitTrans

Wywołaj tę funkcję elementu członkowskiego, po zakończeniu transakcji.

```
BOOL CommitTrans();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli aktualizacje zostały pomyślnie przekazane; w przeciwnym razie 0. Jeśli `CommitTrans` zakończy się niepowodzeniem, stan źródła danych jest niezdefiniowana. Należy sprawdzić dane, aby określić jego stanu.

### <a name="remarks"></a>Uwagi

Transakcja składa się z szeregu wywołania `AddNew`, `Edit`, `Delete`, i `Update` funkcje elementów członkowskich `CRecordset` obiekt, który rozpoczął się wywołanie [BeginTrans](#begintrans) funkcja elementu członkowskiego. `CommitTrans` zatwierdzeń transakcji. Domyślnie aktualizacje zostają zatwierdzone natychmiast; wywoływanie `BeginTrans` powoduje, że zaangażowanie aktualizacje opóźnione aż do `CommitTrans` jest wywoływana.

Dopóki nie zostanie wywołana `CommitTrans` do zakończenia transakcji, można wywołać [wycofywania](#rollback) funkcja elementu członkowskiego, aby przerwać transakcji i pozostawić źródła danych na stanu pierwotnego. Aby rozpocząć nowej transakcji, należy wywołać `BeginTrans` ponownie.

Aby uzyskać więcej informacji na temat transakcji, zobacz artykuł [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Przykład

  Zapoznaj się z artykułem [transakcji: Wykonywanie transakcji w zestawie rekordów (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="executesql"></a>  CDatabase::ExecuteSQL

Wywołaj tę funkcję elementu członkowskiego, gdy trzeba wykonać bezpośrednio za pomocą polecenia SQL.

```
void ExecuteSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>Parametry

*lpszSQL*<br/>
Wskaźnik na ciąg zakończony wartością null zawierający prawidłowe polecenie SQL do wykonania. Możesz przekazać [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Uwagi

Utwórz polecenie jako ciąg znaków zakończony znakiem null. `ExecuteSQL` nie zwraca rekordów danych. Jeśli użytkownik chce działać na rekordy, należy użyć obiektu zestawu rekordów.

Większość poleceń dla źródła danych są wydawane za pośrednictwem obiektów zestawu rekordów, które obsługują polecenia wybierania danych, wstawianie nowych rekordów, usuwanie rekordów i edytowanie rekordów. Jednak nie wszystkie funkcje ODBC bezpośrednio jest obsługiwana przez klasy bazy danych, dlatego czasami może zajść potrzeba wprowadzenia bezpośrednie wywołania SQL z `ExecuteSQL`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#13](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]

##  <a name="getbookmarkpersistence"></a>  CDatabase::GetBookmarkPersistence

Wywołaj tę funkcję elementu członkowskiego, aby określić stan trwały zakładki na obiekty zestawów rekordów, które po niektórych operacjach.

```
DWORD GetBookmarkPersistence() const;
```

### <a name="return-value"></a>Wartość zwracana

Maska bitów identyfikujący operacji za pomocą których zakładki utrwalić obiektu zestawu rekordów. Aby uzyskać więcej informacji zobacz uwagi.

### <a name="remarks"></a>Uwagi

Na przykład, jeśli wywołasz `CRecordset::GetBookmark` , a następnie wywołać `CRecordset::Requery`, zakładka uzyskany z `GetBookmark` może nie być już prawidłowa. Należy wywołać `GetBookmarkPersistence` przed wywołaniem `CRecordset::SetBookmark`.

Poniższa lista zawiera wartości masek bitowych, które można łączyć, aby uzyskać wartość zwracaną przez `GetBookmarkPersistence`.

|Wartość maski bitowej|Trwałość zakładki|
|-------------------|--------------------------|
|SQL_BP_CLOSE|Zakładki są prawidłowe po `Requery` operacji.|
|SQL_BP_DELETE|Zakładki dla wiersza jest prawidłowe po `Delete` operacji w tym wierszu.|
|SQL_BP_DROP|Zakładki są prawidłowe po `Close` operacji.|
|SQL_BP_SCROLL|Zakładki są prawidłowe po każdym `Move` operacji. To po prostu Określa, czy zakładki są obsługiwane w zestawie rekordów zwrócone przez `CRecordset::CanBookmark`.|
|SQL_BP_TRANSACTION|Zakładki są prawidłowe, po transakcji nie zostanie przekazana lub wycofana.|
|SQL_BP_UPDATE|Zakładki dla wiersza jest prawidłowe po `Update` operacji w tym wierszu.|
|SQL_BP_OTHER_HSTMT|Zakładki skojarzone z jednego obiektu zestawu rekordów są prawidłowe dla drugiego zestawu rekordów.|

Aby uzyskać więcej informacji na temat tej wartości zwracanej, zobacz opis funkcji interfejsu API ODBC `SQLGetInfo` w zestawie Windows SDK. Aby uzyskać więcej informacji na temat zakładek, zobacz artykuł [zestaw rekordów: Zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

##  <a name="getconnect"></a>  CDatabase::GetConnect

Wywołaj tę funkcję elementu członkowskiego, aby pobrać parametry połączenia używane podczas wywołania `OpenEx` lub `Open` który połączony `CDatabase` obiektu ze źródłem danych.

```
const CString GetConnect() const;
```

### <a name="return-value"></a>Wartość zwracana

A **const**[CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierającego parametry połączenia, jeśli `OpenEx` lub `Open` została wywołana; w przeciwnym razie, pusty ciąg.

### <a name="remarks"></a>Uwagi

Zobacz [CDatabase::Open](#open) opis sposobu tworzenia parametrów połączenia.

##  <a name="getcursorcommitbehavior"></a>  CDatabase::GetCursorCommitBehavior

Wywołanie tej funkcji elementu członkowskiego, aby określić, jak [CommitTrans](#committrans) operacja ma wpływ na kursory na obiektach otwarty zestaw rekordów.

```
int GetCursorCommitBehavior() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość wskazująca, efekt transakcji na obiektach otwarty zestaw rekordów. Aby uzyskać więcej informacji zobacz uwagi.

### <a name="remarks"></a>Uwagi

Poniższa tabela zawiera listę możliwych wartości zwracanych dla `GetCursorCommitBehavior` i odpowiedni wpływ na otwarty zestaw rekordów.

|Wartość zwracana|Wpływ na crecordset — obiekty|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Wywołaj `CRecordset::Requery` natychmiast po zatwierdzanie transakcji.|
|SQL_CB_DELETE|Wywołaj `CRecordset::Close` natychmiast po zatwierdzanie transakcji.|
|SQL_CB_PRESERVE|Należy kontynuować `CRecordset` operacji.|

Aby uzyskać więcej informacji na temat tej wartości zwracanej, zobacz opis funkcji interfejsu API ODBC `SQLGetInfo` w zestawie Windows SDK. Aby uzyskać więcej informacji na temat transakcji, zobacz artykuł [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="getcursorrollbackbehavior"></a>  CDatabase::GetCursorRollbackBehavior

Wywołanie tej funkcji elementu członkowskiego, aby określić, jak [wycofywania](#rollback) operacja ma wpływ na kursory na obiektach otwarty zestaw rekordów.

```
int GetCursorRollbackBehavior() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość wskazująca, efekt transakcji na obiektach otwarty zestaw rekordów. Aby uzyskać więcej informacji zobacz uwagi.

### <a name="remarks"></a>Uwagi

Poniższa tabela zawiera listę możliwych wartości zwracanych dla `GetCursorRollbackBehavior` i odpowiedni wpływ na otwarty zestaw rekordów.

|Wartość zwracana|Wpływ na crecordset — obiekty|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Wywołaj `CRecordset::Requery` natychmiast po wycofanie transakcji.|
|SQL_CB_DELETE|Wywołaj `CRecordset::Close` natychmiast po wycofanie transakcji.|
|SQL_CB_PRESERVE|Należy kontynuować `CRecordset` operacji.|

Aby uzyskać więcej informacji na temat tej wartości zwracanej, zobacz opis funkcji interfejsu API ODBC `SQLGetInfo` w zestawie Windows SDK. Aby uzyskać więcej informacji na temat transakcji, zobacz artykuł [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="getdatabasename"></a>  CDatabase::GetDatabaseName

Wywołaj tę funkcję elementu członkowskiego, aby pobrać nazwę aktualnie połączonych bazy danych (pod warunkiem, że źródła danych definiuje nazwany obiekt o nazwie "baza danych").

```
CString GetDatabaseName() const;
```

### <a name="return-value"></a>Wartość zwracana

A [CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierający nazwę bazy danych w przypadku powodzenia; w przeciwnym razie, pusta `CString`.

### <a name="remarks"></a>Uwagi

To nie jest taka sama jak nazwa źródła danych (DSN) określona w `OpenEx` lub `Open` wywołania. Co `GetDatabaseName` zwraca zależy od ODBC. Ogólnie rzecz biorąc bazy danych to zbiór tabel. Jeśli ta jednostka ma nazwę, `GetDatabaseName` zwraca go.

Na przykład, można wyświetlać tę nazwę w pozycji. Jeśli wystąpi błąd podczas pobierania nazwy z ODBC i `GetDatabaseName` zwraca pustą `CString`.

##  <a name="isopen"></a>  CDatabase::IsOpen

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy `CDatabase` obiektu jest obecnie połączony ze źródłem danych.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość różną od zera `CDatabase` aktualnie połączony jest obiekt; w przeciwnym razie 0.

##  <a name="m_hdbc"></a>  CDatabase::m_hdbc

Zawiera publiczne dojścia do połączenia ze źródłem danych ODBC — "dojścia połączenia".

### <a name="remarks"></a>Uwagi

Normalnie będziesz mieć bezpośredni dostęp do tej zmiennej elementu członkowskiego nie ma potrzeby. Zamiast tego ramach przydziela dojście, po wywołaniu `OpenEx` lub `Open`. Struktura powoduje cofnięcie przydziału uchwytu po wywołaniu **Usuń** operatora na `CDatabase` obiektu. Należy pamiętać, że `Close` funkcji składowej nie deallocate uchwytu.

Jednak w pewnych okolicznościach może być konieczne bezpośrednio za pomocą uchwytu. Na przykład, jeśli potrzebne do wywoływania funkcji ODBC API bezpośrednio, a nie za pośrednictwem klasy `CDatabase`, może być konieczne dojścia połączenia, aby przekazać jako parametru. Zobacz poniższy przykładowy kod.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#15](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]

##  <a name="onsetoptions"></a>  CDatabase::OnSetOptions

Struktura wywołuje tej funkcji elementu członkowskiego, wykonywaniem bezpośrednio za pomocą instrukcji języka SQL `ExecuteSQL` funkcja elementu członkowskiego.

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*hstmt*<br/>
Dojście instrukcji ODBC, dla których zostały ustawione opcje.

### <a name="remarks"></a>Uwagi

`CRecordset::OnSetOptions` Ponadto wywołuje tej funkcji elementu członkowskiego.

`OnSetOptions` Ustawia wartość limitu czasu logowania. Jeśli zostały poprzedniego wywołania `SetQueryTimeout` i funkcja elementu członkowskiego `OnSetOptions` odzwierciedla bieżące wartości; w przeciwnym wypadku ustawia wartości domyślne.

> [!NOTE]
>  Przed MFC 4.2 `OnSetOptions` również ustawić tryb przetwarzania albo snychronous lub asynchronicznego. Począwszy od MFC 4.2, wszystkie operacje są synchroniczne. Aby wykonać operację asynchroniczną, należy wprowadzić bezpośrednie wywołanie do funkcji interfejsu API ODBC `SQLSetPos`.

Nie trzeba zastąpić `OnSetOptions` można zmienić wartość limitu czasu. Zamiast tego, aby dostosować wartość limitu czasu zapytania, należy wywołać `SetQueryTimeout` przed utworzeniem zestawu rekordów; `OnSetOptions` będą używać nowej wartości. Ustaw wartości mają zastosowanie do kolejnych operacji na wszystkich zestawów rekordów lub bezpośrednich wywołań SQL.

Zastąp `OnSetOptions` Jeśli chcesz ustawić opcje dodatkowe. Przesłonięcia powinna wywołać klasy bazowej `OnSetOptions` przed lub po wywołaniu funkcji interfejsu API ODBC `SQLSetStmtOption`. Należy wykonać w sposób określony w implementacji domyślnej struktury `OnSetOptions`.

##  <a name="open"></a>  CDatabase::Open

Wywołaj tę funkcję elementu członkowskiego, aby zainicjować nowo skonstruowany `CDatabase` obiektu.

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
Określa nazwę źródła danych — nazwa zarejestrowana ODBC za pośrednictwem programu Administratora ODBC. Jeśli określono wartość DSN w *lpszConnect* (w formie "DSN =\<źródło danych >"), nie może być określony w ponownie w *lpszDSN*. W tym przypadku *lpszDSN* powinna być równa NULL. W przeciwnym razie można przekazać wartości NULL, jeśli chcesz przedstawić użytkownikowi okno dialogowe źródła danych, w którym użytkownik może wybrać źródło danych. Aby uzyskać więcej informacji zobacz uwagi.

*bExclusive*<br/>
Nie są obsługiwane w tej wersji biblioteki klas. Obecnie potwierdzenie kończy się niepowodzeniem, jeśli ten parametr ma wartość TRUE. Źródło danych jest zawsze otwierany jako udostępniony (nie wyłącznie).

*bReadOnly*<br/>
Wartość TRUE, jeśli jest planowane połączenie tylko do odczytu i Stanów Zjednoczonych zabraniają aktualizacji do źródła danych. Wszystkie zależne zestawy rekordów dziedziczenia tego atrybutu. Wartość domyślna to FALSE.

*lpszConnect*<br/>
Określa parametry połączenia. Parametry połączenia łączy informacje o prawdopodobnie nazwa źródła danych, prawidłowy identyfikator użytkownika w źródle danych, ciąg uwierzytelniający użytkownika (hasło, jeśli źródło danych wymaga takiego) i inne informacje. Parametry połączenia całego musi być poprzedzona przez ciąg "ODBC;" (wielkie lub małe). "ODBC;" ciąg jest używany do wskazania, że połączenie jest do źródła danych ODBC; dotyczy to zgodności w górę przy przyszłych wersji biblioteki klas może obsługiwać inne niż ODBC — źródła danych.

*bUseCursorLib*<br/>
Wartość TRUE, jeśli chcesz, aby DLL biblioteki kursorów ODBC, który ma być załadowany. Biblioteka kursorów maskuje niektóre funkcje odpowiedni sterownik ODBC, efektywnie pozwalają na korzystanie z zestawów dynamicznych (Jeśli sterownik obsługuje je). Kursorami progresywnymi obsługiwane, gdy jest ładowany z biblioteki kursorów są statyczne migawki i kursory tylko do przodu. Wartość domyślna to TRUE. Jeśli zamierzasz utworzyć obiekt zestawu rekordów bezpośrednio z `CRecordset` bez pochodząca z niego, nie powinien ładować z biblioteki kursorów.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli połączenie zostało pomyślnie nawiązane; w przeciwnym razie 0, jeśli użytkownik zdecyduje się na anulowanie umieszczeniem okno dialogowe z pytaniem, aby uzyskać więcej informacji o połączeniu. We wszystkich innych przypadkach w ramach zgłasza wyjątek.

### <a name="remarks"></a>Uwagi

Obiekt bazy danych muszą zostać zainicjowane, przed służy do konstruowania obiektu zestawu rekordów.

> [!NOTE]
>  Wywoływanie [OpenEx](#openex) funkcja członkowska jest preferowany sposób, aby nawiązać połączenie ze źródłem danych i zainicjowania obiektu bazy danych.

Jeśli parametry w swojej `Open` wywołania nie zawiera wystarczających informacji, aby nawiązać połączenie, sterownik ODBC powoduje otwarcie okna dialogowego, aby uzyskać niezbędne informacje od użytkownika. Gdy wywołujesz `Open`, parametry połączenia, *lpszConnect*, są przechowywane przez użytkowników w `CDatabase` obiektu i jest dostępny, wywołując [GetConnect](#getconnect) funkcja elementu członkowskiego.

Jeśli chcesz, możesz otworzyć własne okno dialogowe przed wywołaniem `Open` Aby uzyskać informacje od użytkownika, takie jak hasła, następnie dodać tych informacji do przekazania do ciągu połączenia `Open`. Można też zapisać parametry połączenia, należy przekazać, więc można używać następnego czasu wywołania aplikacji `Open` na `CDatabase` obiektu.

Umożliwia również parametry połączenia dla autoryzacji logowanie na wielu poziomach (każdy inny `CDatabase` obiekt) lub przekazywać innych informacji specyficznych dla źródła danych. Aby uzyskać więcej informacji dotyczących parametrów połączenia zobacz rozdział 5 w zestawie Windows SDK.

Istnieje możliwość, przekroczy limit czasu próby połączenia, jeśli na przykład host systemu DBMS jest niedostępny. Jeśli próba połączenia zakończy się niepowodzeniem, `Open` zgłasza `CDBException`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#14](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]

##  <a name="openex"></a>  CDatabase::OpenEx

Wywołaj tę funkcję elementu członkowskiego, aby zainicjować nowo skonstruowany `CDatabase` obiektu.

```
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,
    DWORD dwOptions = 0);
```

### <a name="parameters"></a>Parametry

*lpszConnectString*<br/>
Określa parametry połączenia ODBC. W tym nazwa źródła danych, a także inne informacje opcjonalne, takie jak nazwa użytkownika i hasło. Na przykład "DSN = SQLServer_Source; IDENTYFIKATOR UID = SA; PWD = abc123 "ciąg połączenia możliwe. Należy pamiętać, że w przypadku przekazania wartości NULL *lpszConnectString*, okno dialogowe źródło danych zostanie wyświetlony monit o wybranie źródła danych.

*dwOptions*<br/>
Maska bitów, który określa kombinację następujących wartości. Wartość domyślna to 0, co oznacza, że baza danych zostanie otwarty jako udostępniony z dostępem do zapisu, DLL biblioteki kursorów ODBC nie zostanie załadowany i wyświetli okno dialogowe połączenia ODBC, tylko wtedy, gdy nie ma wystarczających informacji do nawiązania połączenia.

- `CDatabase::openExclusive` Nie są obsługiwane w tej wersji biblioteki klas. Źródło danych jest zawsze otwierany jako udostępniony (nie wyłącznie). Obecnie potwierdzenie kończy się niepowodzeniem, jeśli ta opcja jest określona.

- `CDatabase::openReadOnly` Otwórz źródło danych jako tylko do odczytu.

- `CDatabase::useCursorLib` Ładowanie z biblioteki kursorów ODBC biblioteki DLL. Biblioteka kursorów maskuje niektóre funkcje odpowiedni sterownik ODBC, efektywnie pozwalają na korzystanie z zestawów dynamicznych (Jeśli sterownik obsługuje je). Kursorami progresywnymi obsługiwane, gdy jest ładowany z biblioteki kursorów są statyczne migawki i kursory tylko do przodu. Jeśli zamierzasz utworzyć obiekt zestawu rekordów bezpośrednio z `CRecordset` bez pochodząca z niego, nie powinien ładować z biblioteki kursorów.

- `CDatabase::noOdbcDialog` Wyświetla okno dialogowe połączenia ODBC, niezależnie od tego, czy podano wystarczających informacji o połączeniu.

- `CDatabase::forceOdbcDialog` Zawsze wyświetlane okno dialogowe połączenia ODBC.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli połączenie zostało pomyślnie nawiązane; w przeciwnym razie 0, jeśli użytkownik zdecyduje się na anulowanie umieszczeniem okno dialogowe z pytaniem, aby uzyskać więcej informacji o połączeniu. We wszystkich innych przypadkach w ramach zgłasza wyjątek.

### <a name="remarks"></a>Uwagi

Obiekt bazy danych muszą zostać zainicjowane, przed służy do konstruowania obiektu zestawu rekordów.

Jeśli *lpszConnectString* parametru w swojej `OpenEx` wywołania nie zawiera wystarczających informacji do nawiązania połączenia, sterownik ODBC powoduje otwarcie okna dialogowego, aby uzyskać niezbędne informacje od użytkownika, pod warunkiem, że nie Ustaw `CDatabase::noOdbcDialog` lub `CDatabase::forceOdbcDialog` w *dwOptions* parametru. Gdy wywołujesz `OpenEx`, parametry połączenia, *lpszConnectString*, są przechowywane przez użytkowników w `CDatabase` obiektu i jest dostępny, wywołując [GetConnect](#getconnect) funkcja elementu członkowskiego.

Jeśli chcesz, możesz otworzyć własne okno dialogowe przed wywołaniem `OpenEx` Uzyskaj informacje od użytkownika, takie jak hasła, a następnie dodaj te informacje do przekazania do ciągu połączenia `OpenEx`. Można też zapisać parametry połączenia, należy przekazać, więc można używać następnego czasu wywołania aplikacji `OpenEx` na `CDatabase` obiektu.

Umożliwia również parametry połączenia dla autoryzacji logowanie na wielu poziomach (każdy inny `CDatabase` obiekt) lub przekazywać innych informacji specyficznych dla źródła danych. Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz rozdział 6 w *odwołania programisty ODBC*.

Istnieje możliwość, przekroczy limit czasu próby połączenia, jeśli na przykład host systemu DBMS jest niedostępny. Jeśli próba połączenia zakończy się niepowodzeniem, `OpenEx` zgłasza `CDBException`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#11](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]

##  <a name="rollback"></a>  CDatabase::Rollback

Wywołaj tę funkcję elementu członkowskiego, aby wycofać zmiany wprowadzone podczas transakcji.

```
BOOL Rollback();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli pomyślnie można wycofać transakcji; w przeciwnym razie 0. Jeśli `Rollback` wywołanie zakończy się niepowodzeniem, źródła danych i transakcji stany są niezdefiniowane. Jeśli `Rollback` zwraca wartość 0, należy sprawdzić źródło danych, aby określić jego stan.

### <a name="remarks"></a>Uwagi

Wszystkie `CRecordset` `AddNew`, `Edit`, `Delete`, i `Update` wywołania wykonywane od momentu ostatniego [BeginTrans](#begintrans) zostaną przywrócone do stanu który istniał w momencie wywołania.

Po wywołaniu `Rollback`, dobiegł końca transakcji i musi wywołać `BeginTrans` ponownie przez inną transakcję. Rekord, który były aktualne, zanim wywołana `BeginTrans` staje się bieżącym rekordem ponownie po `Rollback`.

Po wycofanie rekord, który były aktualne przed wycofaniem pozostaje bieżącego. Aby uzyskać szczegółowe informacje o stanie zestawu rekordów i źródła danych po wycofywania, zobacz artykuł [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Przykład

  Zapoznaj się z artykułem [transakcji: Wykonywanie transakcji w zestawie rekordów (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="setlogintimeout"></a>  CDatabase::SetLoginTimeout

Wywołaj tę funkcję elementu członkowskiego — przed wywołaniem `OpenEx` lub `Open` — do zastąpienia domyślna liczba sekund przed danych próba połączenia ze źródłem upłynie limit czasu.

```
void SetLoginTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Parametry

*dwSeconds*<br/>
Liczba sekund, zanim próba połączenia upłynie limit czasu.

### <a name="remarks"></a>Uwagi

Próba połączenia może upłynąć limit czasu, jeśli na przykład systemu DBMS nie jest dostępna. Wywołaj `SetLoginTimeout` po konstruowania niezainicjowanej `CDatabase` obiektu, ale zanim wywołasz `OpenEx` lub `Open`.

Wartością domyślną dla nazwy logowania przekroczeń limitu czasu wynosi 15 sekund. Nie wszystkie źródła danych obsługują możliwość określenia wartość limitu czasu logowania. Jeśli źródło danych nie obsługuje limitu czasu, otrzymasz dane wyjściowe śledzenia, ale nie wyjątek. Wartość 0 oznacza, że "nieskończone."

##  <a name="setquerytimeout"></a>  CDatabase::SetQueryTimeout

Wywołaj tę funkcję elementu członkowskiego, aby zastąpić domyślną liczbę sekund określającą kolejne operacje na limit czasu połączonych danych źródłowych.

```
void SetQueryTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Parametry

*dwSeconds*<br/>
Liczba sekund, aby przed próby kwerendy upłynie limit czasu.

### <a name="remarks"></a>Uwagi

Przekroczono limit czasu może być operacją, ze względu na problemy z dostępem do sieci, czasu przetwarzania zapytania nadmiernego i tak dalej. Wywołaj `SetQueryTimeout` przed otwarciem rekordów lub przed wywołaniem zestawu rekordów `AddNew`, `Update` lub `Delete` funkcje Członkowskie, jeśli chcesz zmienić wartość limitu czasu zapytania. To ustawienie ma wpływ na wszystkie kolejne `Open`, `AddNew`, `Update`, i `Delete` wywołania do żadnych zestawów rekordów skojarzonych z tym `CDatabase` obiektu. Zmiana wartości limitu czasu zapytania dla zestawu rekordów po otwarciu nie zmienia wartość dla zestawu rekordów. Na przykład, kolejne `Move` operacji należy używać nowej wartości.

Wartością domyślną dla zapytania przekroczeń limitu czasu wynosi 15 sekund. Nie wszystkie źródła danych obsługują możliwość ustawiania wartości limitu czasu zapytania. Jeśli ustawisz wartość limitu czasu zapytania, 0, następuje limitu czasu; komunikacja ze źródłem danych może przestać odpowiadać. To zachowanie może być przydatne podczas programowania. Jeśli źródło danych nie obsługuje limitu czasu, otrzymasz dane wyjściowe śledzenia, ale nie wyjątek.

## <a name="see-also"></a>Zobacz także

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)
