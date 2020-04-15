---
title: Klasa CRecordset
ms.date: 11/04/2016
f1_keywords:
- CRecordset
- AFXDB/CRecordset
- AFXDB/CRecordset::CRecordset
- AFXDB/CRecordset::AddNew
- AFXDB/CRecordset::CanAppend
- AFXDB/CRecordset::CanBookmark
- AFXDB/CRecordset::Cancel
- AFXDB/CRecordset::CancelUpdate
- AFXDB/CRecordset::CanRestart
- AFXDB/CRecordset::CanScroll
- AFXDB/CRecordset::CanTransact
- AFXDB/CRecordset::CanUpdate
- AFXDB/CRecordset::CheckRowsetError
- AFXDB/CRecordset::Close
- AFXDB/CRecordset::Delete
- AFXDB/CRecordset::DoBulkFieldExchange
- AFXDB/CRecordset::DoFieldExchange
- AFXDB/CRecordset::Edit
- AFXDB/CRecordset::FlushResultSet
- AFXDB/CRecordset::GetBookmark
- AFXDB/CRecordset::GetDefaultConnect
- AFXDB/CRecordset::GetDefaultSQL
- AFXDB/CRecordset::GetFieldValue
- AFXDB/CRecordset::GetODBCFieldCount
- AFXDB/CRecordset::GetODBCFieldInfo
- AFXDB/CRecordset::GetRecordCount
- AFXDB/CRecordset::GetRowsetSize
- AFXDB/CRecordset::GetRowsFetched
- AFXDB/CRecordset::GetRowStatus
- AFXDB/CRecordset::GetSQL
- AFXDB/CRecordset::GetStatus
- AFXDB/CRecordset::GetTableName
- AFXDB/CRecordset::IsBOF
- AFXDB/CRecordset::IsDeleted
- AFXDB/CRecordset::IsEOF
- AFXDB/CRecordset::IsFieldDirty
- AFXDB/CRecordset::IsFieldNull
- AFXDB/CRecordset::IsFieldNullable
- AFXDB/CRecordset::IsOpen
- AFXDB/CRecordset::Move
- AFXDB/CRecordset::MoveFirst
- AFXDB/CRecordset::MoveLast
- AFXDB/CRecordset::MoveNext
- AFXDB/CRecordset::MovePrev
- AFXDB/CRecordset::OnSetOptions
- AFXDB/CRecordset::OnSetUpdateOptions
- AFXDB/CRecordset::Open
- AFXDB/CRecordset::RefreshRowset
- AFXDB/CRecordset::Requery
- AFXDB/CRecordset::SetAbsolutePosition
- AFXDB/CRecordset::SetBookmark
- AFXDB/CRecordset::SetFieldDirty
- AFXDB/CRecordset::SetFieldNull
- AFXDB/CRecordset::SetLockingMode
- AFXDB/CRecordset::SetParamNull
- AFXDB/CRecordset::SetRowsetCursorPosition
- AFXDB/CRecordset::SetRowsetSize
- AFXDB/CRecordset::Update
- AFXDB/CRecordset::m_hstmt
- AFXDB/CRecordset::m_nFields
- AFXDB/CRecordset::m_nParams
- AFXDB/CRecordset::m_pDatabase
- AFXDB/CRecordset::m_strFilter
- AFXDB/CRecordset::m_strSort
helpviewer_keywords:
- CRecordset [MFC], CRecordset
- CRecordset [MFC], AddNew
- CRecordset [MFC], CanAppend
- CRecordset [MFC], CanBookmark
- CRecordset [MFC], Cancel
- CRecordset [MFC], CancelUpdate
- CRecordset [MFC], CanRestart
- CRecordset [MFC], CanScroll
- CRecordset [MFC], CanTransact
- CRecordset [MFC], CanUpdate
- CRecordset [MFC], CheckRowsetError
- CRecordset [MFC], Close
- CRecordset [MFC], Delete
- CRecordset [MFC], DoBulkFieldExchange
- CRecordset [MFC], DoFieldExchange
- CRecordset [MFC], Edit
- CRecordset [MFC], FlushResultSet
- CRecordset [MFC], GetBookmark
- CRecordset [MFC], GetDefaultConnect
- CRecordset [MFC], GetDefaultSQL
- CRecordset [MFC], GetFieldValue
- CRecordset [MFC], GetODBCFieldCount
- CRecordset [MFC], GetODBCFieldInfo
- CRecordset [MFC], GetRecordCount
- CRecordset [MFC], GetRowsetSize
- CRecordset [MFC], GetRowsFetched
- CRecordset [MFC], GetRowStatus
- CRecordset [MFC], GetSQL
- CRecordset [MFC], GetStatus
- CRecordset [MFC], GetTableName
- CRecordset [MFC], IsBOF
- CRecordset [MFC], IsDeleted
- CRecordset [MFC], IsEOF
- CRecordset [MFC], IsFieldDirty
- CRecordset [MFC], IsFieldNull
- CRecordset [MFC], IsFieldNullable
- CRecordset [MFC], IsOpen
- CRecordset [MFC], Move
- CRecordset [MFC], MoveFirst
- CRecordset [MFC], MoveLast
- CRecordset [MFC], MoveNext
- CRecordset [MFC], MovePrev
- CRecordset [MFC], OnSetOptions
- CRecordset [MFC], OnSetUpdateOptions
- CRecordset [MFC], Open
- CRecordset [MFC], RefreshRowset
- CRecordset [MFC], Requery
- CRecordset [MFC], SetAbsolutePosition
- CRecordset [MFC], SetBookmark
- CRecordset [MFC], SetFieldDirty
- CRecordset [MFC], SetFieldNull
- CRecordset [MFC], SetLockingMode
- CRecordset [MFC], SetParamNull
- CRecordset [MFC], SetRowsetCursorPosition
- CRecordset [MFC], SetRowsetSize
- CRecordset [MFC], Update
- CRecordset [MFC], m_hstmt
- CRecordset [MFC], m_nFields
- CRecordset [MFC], m_nParams
- CRecordset [MFC], m_pDatabase
- CRecordset [MFC], m_strFilter
- CRecordset [MFC], m_strSort
ms.assetid: dd89a21d-ef39-4aab-891b-1e373d67c855
ms.openlocfilehash: 264c9eda4860dfbe41d40c9b454ec40a1a274ba5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368361"
---
# <a name="crecordset-class"></a>Klasa CRecordset

Reprezentuje zestaw rekordów wybranych ze źródła danych.

## <a name="syntax"></a>Składnia

```
class CRecordset : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRecordset::CRecordset](#crecordset)|Konstruuje `CRecordset` obiekt. Klasa pochodna musi dostarczyć konstruktora, który wywołuje ten.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRecordset::AddNew](#addnew)|Przygotowuje się do dodania nowego rekordu. Wywołanie, `Update` aby zakończyć dodawanie.|
|[Zestaw CRecord::CanAppend](#canappend)|Zwraca wartość niezerową, jeśli nowe rekordy mogą `AddNew` być dodawane do pliku recordset za pomocą funkcji elementu członkowskiego.|
|[Zestaw CRecordset::CanBookmark](#canbookmark)|Zwraca wartość niezerową, jeśli zestaw rekordów obsługuje zakładki.|
|[CRecordset::Anuluj](#cancel)|Anuluje operację asynchronizacyjną lub proces z drugiego wątku.|
|[CRecordset::Anulujupdate](#cancelupdate)|Anuluje wszelkie oczekujące `AddNew` `Edit` aktualizacje z powodu operacji lub operacji.|
|[Zestaw CRecordset::CanRestart](#canrestart)|Zwraca wartość niezerowa, jeśli `Requery` można wywołać ponowne uruchomienie kwerendy pliku recordset.|
|[CRecordset::CanScroll](#canscroll)|Zwraca wartość niezerowa, jeśli można przewijać rekordy.|
|[CRecordset::CanTransact](#cantransact)|Zwraca wartość niezerową, jeśli źródło danych obsługuje transakcje.|
|[CRecordset::CanUpdate](#canupdate)|Zwraca wartość niezerową, jeśli można zaktualizować plan records (można dodawać, aktualizować lub usuwać rekordy).|
|[CRecordset::CheckRowsetError](#checkrowseterror)|Wywoływana do obsługi błędów generowanych podczas pobierania rekordów.|
|[CRecordset::Zamknij](#close)|Zamyka rekord i odbc HSTMT skojarzone z nim.|
|[CRecordset::Delete](#delete)|Usuwa bieżący rekord z rekordu. Po usunięciu należy jawnie przewinąć do innego rekordu.|
|[CRecordset::DoBulkFieldExchange](#dobulkfieldexchange)|Wywoływana do wymiany zbiorczych wierszy danych ze źródła danych do zbioru rekordów. Implementuje zbiorczą wymianę pól rekordów (Bulk RFX).|
|[CRecordset::DoFieldExchange](#dofieldexchange)|Wywoływana do wymiany danych (w obu kierunkach) między członkami pola danych zbioru rekordów a odpowiednim rekordem w źródle danych. Implementuje wymianę pól rekordów (RFX).|
|[CRecordset::Edytuj](#edit)|Przygotowuje się do zmian w bieżącym rekordzie. Wywołanie, `Update` aby zakończyć edycję.|
|[Zestaw CRecordset::FlushResultSet](#flushresultset)|Zwraca wartość niezerową, jeśli istnieje inny zestaw wyników do pobrania, podczas korzystania ze wstępnie zdefiniowanej kwerendy.|
|[CRecordset::GetBookmark](#getbookmark)|Przypisuje wartość zakładki rekordu do obiektu parametru.|
|[Zestaw CRecordset::GetDefaultConnect](#getdefaultconnect)|Wywoływany, aby uzyskać domyślny ciąg połączenia.|
|[CRecordset::GetDefaultSQL](#getdefaultsql)|Wywoływany, aby uzyskać domyślny ciąg SQL do wykonania.|
|[Zestaw CRecordset::GetFieldValue](#getfieldvalue)|Zwraca wartość pola w liście rekordów.|
|[Zestaw CRecordset::GetODBCFieldCount](#getodbcfieldcount)|Zwraca liczbę pól w tablicy rekordów.|
|[Zestaw CRecordset::GetODBCFieldInfo](#getodbcfieldinfo)|Zwraca określone rodzaje informacji o polach w ach.|
|[Zestaw CRecordset::GetRecordCount](#getrecordcount)|Zwraca liczbę rekordów w tablicy rekordów.|
|[CRecordset::Rozmiar zestawu GetRowsetSize](#getrowsetsize)|Zwraca liczbę rekordów, które mają być pobierane podczas pojedynczego pobierania.|
|[CRecordset::GetRowsFetched](#getrowsfetched)|Zwraca rzeczywistą liczbę wierszy pobranych podczas pobierania.|
|[CRecordset::GetRowStatus](#getrowstatus)|Zwraca stan wiersza po pobraniu.|
|[Zestaw CRecordset::GetSQL](#getsql)|Pobiera ciąg SQL używany do wybierania rekordów dla pliku recordset.|
|[CRecordset::GetStatus](#getstatus)|Pobiera stan rekordu: indeks bieżącego rekordu i czy uzyskano ostateczną liczbę rekordów.|
|[Zestaw CRecord::GetTableName](#gettablename)|Pobiera nazwę tabeli, na której opiera się rekord.|
|[CRecordset::IsBOF](#isbof)|Zwraca wartość niezerowa, jeśli grupa rekordów została mieszczona przed pierwszym rekordem. Nie ma bieżącego rekordu.|
|[CRecordset::JestDeletowany](#isdeleted)|Zwraca wartość wartość niezerową, jeśli plan rekordów jest umieszczony na usuniętym rekordzie.|
|[CRecordset::IsEOF](#iseof)|Zwraca wartość niezerowa, jeśli po ostatnim rekordzie został umieszczony po ostatnim rekordzie. Nie ma bieżącego rekordu.|
|[CRecordset::IsFieldDirty](#isfielddirty)|Zwraca wartość wartość niezerowa, jeśli określone pole w bieżącym rekordzie zostało zmienione.|
|[CRecordset::IsFieldNull](#isfieldnull)|Zwraca wartość niezerową, jeśli określone pole w bieżącym rekordzie ma wartość null (nie ma wartości).|
|[CRecordset::IsFieldNullable](#isfieldnullable)|Zwraca wartość niezerową, jeśli określone pole w bieżącym rekordzie można ustawić na wartość null (bez wartości).|
|[CRecordset::Isopen](#isopen)|Zwraca wartość niezerowa, jeśli `Open` została wywołana wcześniej.|
|[CRecordset::Przenieś](#move)|Umieszcza zestawu rekordów do określonej liczby rekordów z bieżącego rekordu w obu kierunkach.|
|[CRecordset::MoveFirst](#movefirst)|Umieszcza bieżący rekord w pierwszym rekordzie w rekordzie. Najpierw `IsBOF` przetestuj.|
|[CRecordset::MoveLast](#movelast)|Umieszcza bieżący rekord w ostatnim rekordzie lub w ostatnim zestawie wierszy. Najpierw `IsEOF` przetestuj.|
|[Zestaw CRecordset::MoveNext](#movenext)|Umieszcza bieżący rekord w następnym rekordzie lub w następnym zestawie wierszy. Najpierw `IsEOF` przetestuj.|
|[CRecordset::MovePrev](#moveprev)|Umieszcza bieżący rekord w poprzednim rekordzie lub w poprzednim zestawie wierszy. Najpierw `IsBOF` przetestuj.|
|[CRecordset::OnSetOptions](#onsetoptions)|Wywoływana do ustawiania opcji (używanych przy wyborze) dla określonej instrukcji ODBC.|
|[CRecordset::OnSetUpdateOptions](#onsetupdateoptions)|Wywoływana, aby ustawić opcje (używane w aktualizacji) dla określonej instrukcji ODBC.|
|[Crecordset::open](#open)|Otwiera plik recordset, pobierając tabelę lub wykonując kwerendę, którą reprezentuje aplika.|
|[Zestaw CRecordset::RefreshRowset](#refreshrowset)|Odświeża dane i stan określonych wierszy.|
|[CRecordset::Kwerenda requery](#requery)|Ponownie uruchamia kwerendę wstawki rekordów, aby odświeżyć wybrane rekordy.|
|[CRecordset::SetAbsolutePosition](#setabsoluteposition)|Umieszcza w rekordzie tablicę rekordów odpowiadającą określonej liczbie rekordów.|
|[CRecordset::SetBookmark](#setbookmark)|Umieszcza rekord określony przez zakładkę.|
|[CRecordset::SetFieldDirty](#setfielddirty)|Oznacza określone pole w bieżącym rekordzie jako zmienione.|
|[CRecordset::SetFieldNull](#setfieldnull)|Ustawia wartość określonego pola w bieżącym rekordzie na wartość null (bez wartości).|
|[CRecordset::SetLockingMode](#setlockingmode)|Ustawia tryb blokowania na "optymistyczne" blokowanie (domyślne) lub "pesymistyczne" blokowanie. Określa, jak rekordy są zablokowane dla aktualizacji.|
|[CRecordset::SetParamNull](#setparamnull)|Ustawia określony parametr na wartość null (bez wartości).|
|[CRecordset::SetRowsetCursorPosition](#setrowsetcursorposition)|Umieszcza kursor w określonym wierszu w zestawie wierszy.|
|[CRecordset::SetRowsetSize](#setrowsetsize)|Określa liczbę rekordów, które mają być pobierane podczas pobierania.|
|[CRecordset::Aktualizacja](#update)|Kończy `AddNew` operację, `Edit` zapisując nowe lub edytowane dane w źródle danych.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CRecordset::m_hstmt](#m_hstmt)|Zawiera dojście instrukcji ODBC dla zestawie rekordów. Wpisz polecenie `HSTMT`.|
|[CRecordset::m_nFields](#m_nfields)|Zawiera liczbę elementów członkowskich danych pól w zbiorze rekordów. Wpisz polecenie `UINT`.|
|[CRecordset::m_nParams](#m_nparams)|Zawiera liczbę elementów członkowskich danych parametrów w zbiorze rekordów. Wpisz polecenie `UINT`.|
|[CRecordset::m_pDatabase](#m_pdatabase)|Zawiera wskaźnik do `CDatabase` obiektu, za pomocą którego zestaw rekordów jest połączony ze źródłem danych.|
|[CRecordset::m_strFilter](#m_strfilter)|Zawiera `CString` klauzulę SQL (Structured Query `WHERE` Language). Służy jako filtr do wybierania tylko tych rekordów, które spełniają określone kryteria.|
|[CRecordset::m_strSort](#m_strsort)|Zawiera `CString` klauzulę SQL, `ORDER BY` która określa klauzulę SQL. Służy do kontrolowania sposobu sortowania rekordów.|

## <a name="remarks"></a><a name="remarks"></a>Uwagi

Znane jako "zestawy `CRecordset` rekordów", obiekty są zwykle używane w dwóch formach: dynasets i migawki. Dynaset pozostaje zsynchronizowany z aktualizacjami danych dokonanych przez innych użytkowników. Migawka jest statycznym widokiem danych. Każdy formularz reprezentuje zestaw rekordów ustalonych w momencie otwarcia zestawu rekordów, ale podczas przewijania do rekordu w zestawie dynamiki odzwierciedla on zmiany wprowadzone następnie w rekordzie przez innych użytkowników lub przez inne zestawy rekordów w aplikacji.

> [!NOTE]
> Jeśli pracujesz z klasami obiektów dostępu do danych (DAO), a nie z klasami Open Database Connectivity (ODBC), należy użyć klasy [CDaoRecordset.](../../mfc/reference/cdaorecordset-class.md) Aby uzyskać więcej informacji, zobacz artykuł [Omówienie: Programowanie baz danych](../../data/data-access-programming-mfc-atl.md).

Aby pracować z każdym rodzajem pliku recordset, zazwyczaj należy wyprowadzić `CRecordset`klasę atrybutu specyficznego dla aplikacji z . Zestawy rekordów wybierają rekordy ze źródła danych, a następnie:

- Przewiń rekordy.

- Zaktualizuj rekordy i określ tryb blokowania.

- Filtruj zestaw rekordów, aby ograniczyć rekordy, które wybiera spośród rekordów dostępnych w źródle danych.

- Sortowanie pliku recordset.

- Parametryzacja pliku recordset, aby dostosować jego wybór z informacjami nie znanymi do czasu wykonywania.

Aby użyć klasy, otwórz bazę danych i skonstruuj obiekt `CDatabase` pliku recordset, przekazując konstruktorowi wskaźnik do obiektu. Następnie wywołaj funkcję `Open` elementu członkowskiego zestawu rekordów, gdzie można określić, czy obiekt jest dynaset lub migawki. Wywołanie `Open` wybiera dane ze źródła danych. Po otwarciu obiektu zestaw rekordów użyj jego funkcji członkowskich i elementów członkowskich danych, aby przewijać rekordy i działać na nich. Dostępne operacje zależą od tego, czy obiekt jest dynaset lub migawki, czy jest aktualizowane lub tylko do odczytu (zależy to od możliwości open database connectivity (ODBC) źródło danych) i czy zostały zaimplementowane zbiorcze pobieranie wiersza. Aby odświeżyć rekordy, które mogły `Open` zostać zmienione lub `Requery` dodane od czasu wywołania, wywołaj funkcję elementu członkowskiego obiektu. Wywołaj funkcję `Close` elementu członkowskiego obiektu i zniszcz obiekt po zakończeniu.

W `CRecordset` klasie pochodnej wymiana pól rekordów (RFX) lub zbiorcza wymiana pól rekordów (Bulk RFX) jest używana do obsługi odczytu i aktualizacji pól rekordów.

Aby uzyskać więcej informacji na temat rekordów i wymiany pól rekordów, zobacz artykuły [Omówienie: Programowanie baz danych](../../data/data-access-programming-mfc-atl.md), [Recordset (ODBC)](../../data/odbc/recordset-odbc.md), [Recordset: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)i [Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md). Aby uzyskać fokus na dynasets i migawki, zobacz artykuły [Dynaset](../../data/odbc/dynaset.md) i [Migawka](../../data/odbc/snapshot.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CRecordset`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="crecordsetaddnew"></a><a name="addnew"></a>CRecordset::AddNew

Przygotowuje się do dodania nowego rekordu do tabeli.

```
virtual void AddNew();
```

### <a name="remarks"></a>Uwagi

Aby wyświetlić nowo dodany rekord, należy wywołać funkcję członka [kwerendy.](#requery) Pola rekordu są początkowo null. (W terminologii bazy danych Null oznacza "bez wartości" i nie jest taka sama jak NULL w języku C++.) Aby wykonać operację, należy [wywołać](#update) update funkcji elementu członkowskiego. `Update`zapisuje zmiany w źródle danych.

> [!NOTE]
> Jeśli zaimplementowano pobieranie wiersza `AddNew`zbiorczego, nie można wywołać . Spowoduje to nie powiodło się twierdzenie. Chociaż `CRecordset` klasa nie zapewnia mechanizmu aktualizowania zbiorczych wierszy danych, można napisać własne `SQLSetPos`funkcje przy użyciu funkcji INTERFEJSU API ODBC. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`AddNew`przygotowuje nowy, pusty rekord przy użyciu elementów członkowskich danych pól zbioru rekordów. Po wywołaniu `AddNew`ustaw wartości, które mają być w elementach członkowskich danych pól zestawu rekordów. (Nie trzeba wywoływać funkcji [Edytuj](#edit) element członkowski `Edit` w tym celu; używać tylko dla istniejących rekordów). Podczas późniejszego `Update`wywoływania zmienione wartości w elementach członkowskich danych pola są zapisywane w źródle danych.

> [!CAUTION]
> Jeśli przewiniesz do nowego `Update`rekordu przed wywołaniem, nowy rekord zostanie utracony i nie zostanie podane żadne ostrzeżenie.

Jeśli źródło danych obsługuje transakcje, można `AddNew` dokonać połączenia część transakcji. Aby uzyskać więcej informacji o transakcjach, zobacz klasę [CDatabase](../../mfc/reference/cdatabase-class.md). Należy zauważyć, że należy wywołać [CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) przed wywołaniem `AddNew`.

> [!NOTE]
> W przypadku zestawów dynamicznych nowe rekordy są dodawane do zestawu rekordów jako ostatni rekord. Dodane rekordy nie są dodawane do migawek; należy wywołać, `Requery` aby odświeżyć rekord.

Niezgodne z prawem `AddNew` jest wywołanie `Open` pliku recordset, którego funkcja elementu członkowskiego nie została wywołana. A `CDBException` jest generowany, `AddNew` jeśli wywołasz dla pliku recordset, do którego nie można dołączyć. Można określić, czy plik rekordów można aktualizować, wywołując program [CanAppend](#canappend).

Aby uzyskać więcej informacji, zobacz następujące artykuły: [Zestawy rekordów: Jak recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md), [Recordset: Dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)i [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Przykład

Zobacz artykuł [Transakcja: Wykonywanie transakcji w zajrzy (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="crecordsetcanappend"></a><a name="canappend"></a>Zestaw CRecord::CanAppend

Określa, czy wcześniej otwarty rekord umożliwia dodawanie nowych rekordów.

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli recordset umożliwia dodawanie nowych rekordów; w przeciwnym razie 0. `CanAppend`powróci 0, jeśli otworzysz plik recordset jako tylko do odczytu.

## <a name="crecordsetcanbookmark"></a><a name="canbookmark"></a>Zestaw CRecordset::CanBookmark

Określa, czy nastawie rekordów można oznaczać za pomocą zakładek.

```
BOOL CanBookmark() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli zestaw rekordów obsługuje zakładki; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest `CRecordset::useBookmarks` niezależna od opcji w parametrze *dwOptions* funkcji [otwórz](#open) element członkowski. `CanBookmark`wskazuje, czy danego sterownika ODBC i typu kursora obsługują zakładki. `CRecordset::useBookmarks`wskazuje, czy zakładki będą dostępne, pod warunkiem, że są obsługiwane.

> [!NOTE]
> Zakładki nie są obsługiwane w rekordach tylko do przodu.

Aby uzyskać więcej informacji na temat zakładek i nawigacji na tabliczce rekordów, zobacz artykuły [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) oraz [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="crecordsetcancel"></a><a name="cancel"></a>CRecordset::Anuluj

Żąda, aby źródło danych anulowało operację asynchroniza w toku lub proces z drugiego wątku.

```
void Cancel();
```

### <a name="remarks"></a>Uwagi

Należy zauważyć, że klasy ODBC MFC nie używają już przetwarzania asynchroniczne; aby wykonać operację asychronikę, należy bezpośrednio wywołać `SQLSetConnectOption`funkcję INTERFEJSU API ODBC . Aby uzyskać więcej informacji, zobacz temat "Wykonywanie funkcji asynchronicznie" w *przewodniku programisty SDK ODBC*.

## <a name="crecordsetcancelupdate"></a><a name="cancelupdate"></a>CRecordset::Anulujupdate

Anuluje wszelkie oczekujące aktualizacje, spowodowane przez operację [Edytuj](#edit) lub [DodajNe,](#addnew) zanim [zostanie wywołana aktualizacja.](#update)

```
void CancelUpdate();
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Ta funkcja elementu członkowskiego nie ma zastosowania w grupach rekordów, które `Edit` `AddNew`używają `Update`pobierania wierszy zbiorczych, ponieważ takie zestawy rekordów nie mogą wywoływać , lub . Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Jeśli automatyczne sprawdzanie brudnego pola `CancelUpdate` jest włączone, przywróci zmienne członkowskie `Edit` `AddNew` do wartości, które miały przed lub został wywołany; w przeciwnym razie wszelkie zmiany wartości pozostaną. Domyślnie automatyczne sprawdzanie pola jest włączone po otwarciu listy rekordów. Aby go wyłączyć, należy `CRecordset::noDirtyFieldCheck` określić w *dwOptions* parametr Funkcji elementu członkowskiego [Otwórz.](#open)

Aby uzyskać więcej informacji na temat aktualizowania danych, zobacz artykuł [Zestaw rekordów: Dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md).

## <a name="crecordsetcanrestart"></a><a name="canrestart"></a>Zestaw CRecordset::CanRestart

Określa, czy plik recordset umożliwia ponowne uruchomienie kwerendy (aby odświeżyć jego rekordy) przez wywołanie `Requery` funkcji elementu członkowskiego.

```
BOOL CanRestart() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli ponowne zapytanie jest dozwolone; w przeciwnym razie 0.

## <a name="crecordsetcanscroll"></a><a name="canscroll"></a>CRecordset::CanScroll

Określa, czy plik recordset umożliwia przewijanie.

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli recordset umożliwia przewijanie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat przewijania, zobacz artykuł [Rekord: Przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="crecordsetcantransact"></a><a name="cantransact"></a>CRecordset::CanTransact

Określa, czy rekordwzór zezwala na transakcje.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli rekordet umożliwia transakcje; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz artykuł [Transakcja (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="crecordsetcanupdate"></a><a name="canupdate"></a>CRecordset::CanUpdate

Określa, czy można zaktualizować go.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli można zaktualizować rekord; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zestaw rekordów może być tylko do odczytu, jeśli źródłowe `CRecordset::readOnly` źródło danych jest tylko do odczytu lub jeśli określono w *dwOptions* parametr podczas otwarcia zestaw rekordów.

## <a name="crecordsetcheckrowseterror"></a><a name="checkrowseterror"></a>CRecordset::CheckRowsetError

Wywoływana do obsługi błędów generowanych podczas pobierania rekordów.

```
virtual void CheckRowsetError(RETCODE nRetCode);
```

### <a name="parameters"></a>Parametry

*kod nRetCode*<br/>
Kod zwrotny funkcji INTERFEJSU API ODBC. Aby uzyskać szczegółowe informacje, zobacz Uwagi.

### <a name="remarks"></a>Uwagi

Ta funkcja wirtualnego elementu członkowskiego obsługuje błędy, które występują podczas pobierania rekordów i jest przydatna podczas pobierania wiersza zbiorczego. Można rozważyć zastąpienie `CheckRowsetError` do zaimplementowania obsługi błędów własnych.

`CheckRowsetError`jest wywoływana automatycznie w operacji nawigacji kursora, takiej jak `Open`, `Requery`lub dowolnej `Move` operacji. Jest przekazywana wartość zwracana funkcji `SQLExtendedFetch`INTERFEJSU API ODBC . W poniższej tabeli wymieniono możliwe wartości parametru *nRetCode.*

|kod nRetCode|Opis|
|--------------|-----------------|
|Sql_success|Funkcja została ukończona pomyślnie; nie są dostępne żadne dodatkowe informacje.|
|Sql_success_with_info|Funkcja została ukończona pomyślnie, prawdopodobnie z błędem nieśmiearnym. Dodatkowe informacje można uzyskać `SQLError`dzwoniąc pod numer .|
|SQL_NO_DATA_FOUND|Wszystkie wiersze z zestawu wyników zostały pobrane.|
|Sql_error|Funkcja nie powiodła się. Dodatkowe informacje można uzyskać `SQLError`dzwoniąc pod numer .|
|SQL_INVALID_HANDLE|Funkcja nie powiodła się z powodu nieprawidłowego dojścia do środowiska, dojścia połączenia lub dojścia instrukcji. Oznacza to błąd programowania. Żadne dodatkowe informacje `SQLError`nie są dostępne w pliku .|
|Sql_still_executing|Funkcja, która została uruchomiona asynchronicznie jest nadal wykonywana. Należy zauważyć, że domyślnie MFC `CheckRowsetError`nigdy nie przekaże tej wartości do ; MFC będzie `SQLExtendedFetch` nadal wywoływać, dopóki nie zwróci SQL_STILL_EXECUTING.|

Aby uzyskać `SQLError`więcej informacji na temat programu , zobacz SDK systemu Windows. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetclose"></a><a name="close"></a>CRecordset::Zamknij

Zamyka rekord.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Odbc HSTMT i wszystkie pamięci ramy przydzielone dla pliku recordset są cofnięte. Zwykle po `Close`wywołaniu obiektu C++ recordset można usunąć, jeśli został przydzielony **z nowym**.

Możesz zadzwonić `Open` ponownie `Close`po wywołaniu . Dzięki temu można ponownie użyć obiektu akcesetu. Alternatywą jest `Requery`wywołanie .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#17](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]

## <a name="crecordsetcrecordset"></a><a name="crecordset"></a>CRecordset::CRecordset

Konstruuje `CRecordset` obiekt.

```
CRecordset(CDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>Parametry

*pDatabase (baza danych)*<br/>
Zawiera wskaźnik do `CDatabase` obiektu lub wartość NULL. Jeśli nie NULL `CDatabase` i `Open` funkcja elementu członkowskiego obiektu nie został wywołany, aby połączyć go ze źródłem danych, zestaw rekordów próbuje otworzyć go dla Ciebie podczas własnego `Open` wywołania. Jeśli przekażesz `CDatabase` null, obiekt jest konstruowany i połączony dla Ciebie przy użyciu informacji o źródle danych określonych podczas uzyskiwania klasy zestaw rekordów z ClassWizard.

### <a name="remarks"></a>Uwagi

Można użyć `CRecordset` bezpośrednio lub wyprowadzić klasę specyficzną dla aplikacji z programu `CRecordset`. ClassWizard służy do uzyskiwania klas recordset.

> [!NOTE]
> Klasa pochodna *musi* dostarczyć własny konstruktor. W konstruktorze klasy pochodnej wywołać `CRecordset::CRecordset`konstruktora , przekazując odpowiednie parametry wraz z nim.

Przekaż wartość NULL do konstruktora pliku recordset, `CDatabase` aby obiekt został automatycznie skonstruowany i połączony. Jest to przydatne skrót, który nie wymaga konstruowania i łączenia `CDatabase` obiektu przed konstruowania pliku recordset.

### <a name="example"></a>Przykład

Aby uzyskać więcej informacji, zobacz artykuł [Rekord: Deklarowanie klasy dla tabeli (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).

## <a name="crecordsetdelete"></a><a name="delete"></a>CRecordset::Delete

Usuwa bieżący rekord.

```
virtual void Delete();
```

### <a name="remarks"></a>Uwagi

Po pomyślnym usunięciu elementy członkowskie danych pola zestawu rekordów są ustawione na wartość Null i `Move` należy jawnie wywołać jedną z funkcji, aby przenieść usunięty rekord. Po przeniesieniu usuniętego rekordu nie można do niego powrócić. Jeśli źródło danych obsługuje transakcje, można `Delete` dokonać wywołania część transakcji. Aby uzyskać więcej informacji, zobacz artykuł [Transakcja (ODBC)](../../data/odbc/transaction-odbc.md).

> [!NOTE]
> Jeśli zaimplementowano pobieranie wiersza `Delete`zbiorczego, nie można wywołać . Spowoduje to nie powiodło się twierdzenie. Chociaż `CRecordset` klasa nie zapewnia mechanizmu aktualizowania zbiorczych wierszy danych, można napisać własne `SQLSetPos`funkcje przy użyciu funkcji INTERFEJSU API ODBC. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!CAUTION]
> Więdną czasowy rekordu, a w ujmijuj `Delete`rekord musi być rozpowszechniony rekord; w przeciwnym razie wystąpi błąd. Na przykład, jeśli usuniesz rekord, ale nie `Delete` przewiń do nowego rekordu przed ponownym wywołaniem, `Delete` zrzuci [cdbexception](../../mfc/reference/cdbexception-class.md).

W przeciwieństwie do [AddNew](#addnew) `Delete` i [Edit,](#edit)wywołanie nie następuje wywołanie [aktualizacji](#update). Jeśli `Delete` wywołanie nie powiedzie się, elementy członkowskie danych pola pozostają niezmienione.

### <a name="example"></a>Przykład

W tym przykładzie pokazano rekord utworzony w ramce funkcji. W przykładzie przyjęto `m_dbCust`założenie istnienia , `CDatabase` zmiennej członkowskiej typu już połączone ze źródłem danych.

[!code-cpp[NVC_MFCDatabase#18](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]

## <a name="crecordsetdobulkfieldexchange"></a><a name="dobulkfieldexchange"></a>CRecordset::DoBulkFieldExchange

Wywoływana do wymiany zbiorczych wierszy danych ze źródła danych do zbioru rekordów. Implementuje zbiorczą wymianę pól rekordów (Bulk RFX).

```
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Wskaźnik do [obiektu CFieldExchange.](../../mfc/reference/cfieldexchange-class.md) Struktura będzie już skonfigurować ten obiekt, aby określić kontekst dla operacji wymiany pola.

### <a name="remarks"></a>Uwagi

Po zaimplementowaniu pobierania wiersza zbiorczego, framework wywołuje tę funkcję elementu członkowskiego, aby automatycznie przesyłać dane ze źródła danych do obiektu zestaw rekordów. `DoBulkFieldExchange`również wiąże elementy członkowskie danych parametru, jeśli istnieją, do symboli zastępczych parametrów w ciągu instrukcji SQL dla wyboru zestawie rekordów.

Jeśli pobieranie wiersza zbiorczego nie jest implementowane, struktura wywołuje [DoFieldExchange](#dofieldexchange). Aby zaimplementować pobieranie wiersza `CRecordset::useMultiRowFetch` zbiorczego, należy określić opcję parametru *dwOptions* w funkcji Elementu członkowskiego [Otwórz.](#open)

> [!NOTE]
> `DoBulkFieldExchange`jest dostępna tylko w przypadku korzystania `CRecordset`z klasy pochodzącej od . Jeśli obiekt zestaw rekordów został `CRecordset`utworzony bezpośrednio z obiektu , należy wywołać funkcję elementu członkowskiego [GetFieldValue](#getfieldvalue) w celu pobrania danych.

Zbiorcza wymiana pól rekordów (Bulk RFX) jest podobna do wymiany pól rekordów (RFX). Dane są automatycznie przesyłane ze źródła danych do obiektu zestaw rekordów. Nie można jednak `AddNew` `Edit`wywołać , , `Delete`lub `Update` przenieść zmiany z powrotem do źródła danych. Klasa `CRecordset` obecnie nie zapewnia mechanizm aktualizacji wierszy zbiorczych danych; można jednak zapisywać własne funkcje za pomocą `SQLSetPos`funkcji API ODBC .

Należy zauważyć, że ClassWizard nie obsługuje zbiorczej wymiany pól rekordów; w związku z tym `DoBulkFieldExchange` należy zastąpić ręcznie, zapisując wywołania do funkcji RFX luzem. Aby uzyskać więcej informacji na temat tych funkcji, zobacz temat [Rejestrowanie funkcji wymiany pól](../../mfc/reference/record-field-exchange-functions.md).

Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Aby uzyskać powiązane informacje, zobacz artykuł [Wymiana pól rekordu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

## <a name="crecordsetdofieldexchange"></a><a name="dofieldexchange"></a>CRecordset::DoFieldExchange

Wywoływana do wymiany danych (w obu kierunkach) między członkami pola danych zbioru rekordów a odpowiednim rekordem w źródle danych. Implementuje wymianę pól rekordów (RFX).

```
virtual void DoFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Wskaźnik do [obiektu CFieldExchange.](../../mfc/reference/cfieldexchange-class.md) Struktura będzie już skonfigurować ten obiekt, aby określić kontekst dla operacji wymiany pola.

### <a name="remarks"></a>Uwagi

Gdy pobieranie wiersza zbiorczego nie jest implementowane, struktura wywołuje tę funkcję elementu członkowskiego, aby automatycznie wymieniać dane między elementami członkowskimi danych pola obiektu zestaw rekordów i odpowiednimi kolumnami bieżącego rekordu w źródle danych. `DoFieldExchange`również wiąże elementy członkowskie danych parametru, jeśli istnieją, do symboli zastępczych parametrów w ciągu instrukcji SQL dla wyboru zestawie rekordów.

Jeśli zaimplementowano pobieranie wierszy zbiorczych, struktura wywołuje [doBulkFieldExchange](#dobulkfieldexchange). Aby zaimplementować pobieranie wiersza `CRecordset::useMultiRowFetch` zbiorczego, należy określić opcję parametru *dwOptions* w funkcji Elementu członkowskiego [Otwórz.](#open)

> [!NOTE]
> `DoFieldExchange`jest dostępna tylko w przypadku korzystania `CRecordset`z klasy pochodzącej od . Jeśli obiekt zestaw rekordów został `CRecordset`utworzony bezpośrednio z obiektu , należy wywołać funkcję elementu członkowskiego [GetFieldValue](#getfieldvalue) w celu pobrania danych.

Wymiana danych pól, zwana wymianą pól rekordów (RFX), działa w obu kierunkach: od elementów członkowskich danych pola obiektu recordset do pól rekordu w źródle danych oraz z rekordu w źródle danych do obiektu zestaw rekordów.

Jedyną czynnością, którą zwykle `DoFieldExchange` należy podjąć w celu zaimplementowania dla pochodnej klasy zestaw rekordów jest utworzenie klasy z ClassWizard i określić nazwy i typy danych elementów członkowskich danych pola. Można również dodać kod do tego, co pisze ClassWizard, aby określić elementy członkowskie danych parametrów lub do czynienia z kolumnami, które wiążą dynamicznie. Aby uzyskać więcej informacji, zobacz artykuł [Zestaw rekordów: Dynamicznie wiążące kolumny danych (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Podczas deklarowania pochodnej klasy tablicy rekordów za pomocą ClassWizard `DoFieldExchange` kreator zapisuje dla Ciebie zastąpienie, które przypomina poniższy przykład:

[!code-cpp[NVC_MFCDatabase#19](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]

Aby uzyskać więcej informacji na temat funkcji RFX, zobacz temat [Rejestrowanie funkcji wymiany pól](../../mfc/reference/record-field-exchange-functions.md).

Aby uzyskać więcej przykładów i szczegółów na temat `DoFieldExchange`, zobacz artykuł Wymiana pól [rekordu: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Aby uzyskać ogólne informacje na temat rfx, zobacz artykuł [Wymiana pól rekordu](../../data/odbc/record-field-exchange-rfx.md).

## <a name="crecordsetedit"></a><a name="edit"></a>CRecordset::Edytuj

Zezwala na zmiany w bieżącym rekordzie.

```
virtual void Edit();
```

### <a name="remarks"></a>Uwagi

Po wywołaniu `Edit`program można zmienić elementy członkowskie danych pola, bezpośrednio resetując ich wartości. Operacja jest zakończona po wywołaniu update funkcji [elementu](#update) członkowskiego, aby zapisać zmiany w źródle danych.

> [!NOTE]
> Jeśli zaimplementowano pobieranie wiersza `Edit`zbiorczego, nie można wywołać . Spowoduje to nie powiodło się twierdzenie. Chociaż `CRecordset` klasa nie zapewnia mechanizmu aktualizowania zbiorczych wierszy danych, można napisać własne `SQLSetPos`funkcje przy użyciu funkcji INTERFEJSU API ODBC. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`Edit`zapisuje wartości elementów członkowskich danych zbioru rekordów. Jeśli wywołasz `Edit`, wprowadzać `Edit` zmiany, a następnie wywołać ponownie, wartości `Edit` rekordu są przywracane do tego, co było przed pierwszym wywołaniem.

W niektórych przypadkach można zaktualizować kolumnę, czyniąc ją Null (zawierającą żadnych danych). Aby to zrobić, należy wywołać [SetFieldNull](#setfieldnull) z parametrem TRUE, aby oznaczyć pole Null; powoduje to również, że kolumna ma zostać zaktualizowana. Jeśli chcesz, aby pole zostało zapisane w źródle danych, nawet jeśli jego wartość nie uległa zmianie, należy wywołać [SetFieldDirty](#setfielddirty) z parametrem TRUE. Działa to nawet wtedy, gdy pole miało wartość Null.

Jeśli źródło danych obsługuje transakcje, można `Edit` dokonać wywołania część transakcji. Należy zauważyć, że należy wywołać [CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) przed wywołaniem `Edit` i po otwarciu pliku recordset. Należy również zauważyć, że wywołanie [CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) nie jest substytutem wywołania, `Update` aby zakończyć `Edit` operację. Aby uzyskać więcej informacji o transakcjach, zobacz klasę [CDatabase](../../mfc/reference/cdatabase-class.md).

W zależności od bieżącego trybu blokowania aktualizowany rekord `Edit` może `Update` być zablokowany do momentu wywołania lub przewinięcia do innego rekordu lub może zostać zablokowany tylko podczas `Edit` połączenia. Tryb blokowania można zmienić za pomocą [funkcji SetLockingMode](#setlockingmode).

Poprzednia wartość bieżącego rekordu zostanie przywrócona po `Update`przewinięciu do nowego rekordu przed wywołaniem . A `CDBException` jest generowany, `Edit` jeśli wywołasz dla pliku recordset, który nie może być zaktualizowany lub jeśli nie ma bieżącego rekordu.

Aby uzyskać więcej informacji, zobacz artykuły [Transaction (ODBC)](../../data/odbc/transaction-odbc.md) i [Recordset: Locking Records (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#20](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]

## <a name="crecordsetflushresultset"></a><a name="flushresultset"></a>Zestaw CRecordset::FlushResultSet

Pobiera następny zestaw wyników wstępnie zdefiniowanej kwerendy (procedura składowana), jeśli istnieje wiele zestawów wyników.

```
BOOL FlushResultSet();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli istnieje więcej zestawów wyników do pobrania; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołać `FlushResultSet` tylko wtedy, gdy są całkowicie zakończone z kursorem na bieżącym zestawie wyników. Należy zauważyć, że podczas pobierania następnego zestawu wyników przez wywołanie `FlushResultSet`kursor nie jest prawidłowy w tym zestawie wyników; należy wywołać funkcję [movenext](#movenext) `FlushResultSet`elementu członkowskiego po wywołaniu .

Jeśli wstępnie zdefiniowana kwerenda używa parametru wyjściowego lub parametrów wejścia/wyjścia, należy wywołać, `FlushResultSet` dopóki nie zwróci `FALSE` (wartość 0), w celu uzyskania tych wartości parametrów.

`FlushResultSet`wywołuje funkcję `SQLMoreResults`API ODBC . Jeśli `SQLMoreResults` zwraca SQL_ERROR lub SQL_INVALID_HANDLE, następnie `FlushResultSet` zda wyjątek. Aby uzyskać `SQLMoreResults`więcej informacji na temat programu , zobacz SDK systemu Windows.

Procedura składowana musi mieć powiązane pola, `FlushResultSet`jeśli chcesz wywołać .

### <a name="example"></a>Przykład

Poniższy kod zakłada, `COutParamRecordset` `CRecordset`że jest obiektem pochodnym opartym na wstępnie zdefiniowanej kwerendzie z parametrem wejściowym i parametrem wyjściowym i posiadającym wiele zestawów wyników. Zwróć uwagę na strukturę zastąpienia [DoFieldExchange.](#dofieldexchange)

[!code-cpp[NVC_MFCDatabase#21](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]

[!code-cpp[NVC_MFCDatabase#22](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]

## <a name="crecordsetgetbookmark"></a><a name="getbookmark"></a>CRecordset::GetBookmark

Uzyskuje wartość zakładki dla bieżącego rekordu.

```
void GetBookmark(CDBVariant& varBookmark);
```

### <a name="parameters"></a>Parametry

*varBookmark (znak zdj.*<br/>
Odwołanie do [obiektu CDBVariant](../../mfc/reference/cdbvariant-class.md) reprezentującego zakładkę w bieżącym rekordzie.

### <a name="remarks"></a>Uwagi

Aby ustalić, czy zakładki są obsługiwane w ach, zadzwoń do [canbookmark](#canbookmark). Aby udostępnić zakładki, jeśli są obsługiwane, `CRecordset::useBookmarks` należy ustawić opcję w parametrze *dwOptions* funkcji elementu członkowskiego [Otwórz.](#open)

> [!NOTE]
> Jeśli zakładki nie są obsługiwane lub niedostępne, wywołanie `GetBookmark` spowoduje wyjątek. Zakładki nie są obsługiwane w rekordach tylko do przodu.

`GetBookmark`przypisuje do `CDBVariant` obiektu wartość zakładki bieżącego rekordu. Aby powrócić do tego rekordu w dowolnym momencie po przejściu `CDBVariant` do innego rekordu, [wywołanie SetBookmark](#setbookmark) z odpowiednim obiektem.

> [!NOTE]
> Po niektórych operacjach nastawy rekordów zakładki mogą nie być już prawidłowe. Na przykład, jeśli `GetBookmark` następuje połączenie `Requery`, możesz nie być `SetBookmark`w stanie powrócić do rekordu za pomocą . Wywołanie [CDatabase::GetBookmarkPersistence,](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) aby sprawdzić, czy można bezpiecznie wywołać `SetBookmark`.

Aby uzyskać więcej informacji na temat zakładek i nawigacji na tabliczce rekordów, zobacz artykuły [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) oraz [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="crecordsetgetdefaultconnect"></a><a name="getdefaultconnect"></a>Zestaw CRecordset::GetDefaultConnect

Wywoływany, aby uzyskać domyślny ciąg połączenia.

```
virtual CString GetDefaultConnect();
```

### <a name="return-value"></a>Wartość zwracana

A, `CString` który zawiera domyślny ciąg połączenia.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę funkcję elementu członkowskiego, aby uzyskać domyślny ciąg połączenia dla źródła danych, na którym jest oparty zestaw rekordów. ClassWizard implementuje tę funkcję za pomocą tego samego źródła danych, którego używasz w ClassWizard, aby uzyskać informacje o tabelach i kolumnach. Prawdopodobnie będzie można polegać na tym domyślnym połączeniu podczas tworzenia aplikacji. Ale domyślne połączenie może nie być odpowiednie dla użytkowników aplikacji. W takim przypadku należy ponownie zaimplementować tę funkcję, odrzucając wersję ClassWizard. Aby uzyskać więcej informacji na temat ciągów połączeń, zobacz artykuł [Źródło danych (ODBC)](../../data/odbc/data-source-odbc.md).

## <a name="crecordsetgetdefaultsql"></a><a name="getdefaultsql"></a>CRecordset::GetDefaultSQL

Wywoływany, aby uzyskać domyślny ciąg SQL do wykonania.

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>Wartość zwracana

A, `CString` który zawiera domyślną instrukcję SQL.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę funkcję elementu członkowskiego, aby uzyskać domyślną instrukcję SQL, na której opiera się zestawie rekordów. Może to być nazwa tabeli lub instrukcja SQL **SELECT.**

Pośrednio zdefiniować domyślną instrukcję SQL, deklarując klasę zestawie rekordów z ClassWizard i ClassWizard wykonuje to zadanie dla Ciebie.

Jeśli potrzebujesz ciągu instrukcji SQL do własnego `GetSQL`użytku, wywołaj , który zwraca instrukcję SQL używaną do wybierania rekordów zestawie rekordów rekordów podczas jego otwarcia. Domyślny ciąg SQL można edytować w zastąpiona `GetDefaultSQL`przez klasę . Na przykład można określić wywołanie wstępnie zdefiniowanej kwerendy przy użyciu instrukcji **CALL.** (Należy jednak pamiętać, że `GetDefaultSQL`w przypadku edycji należy również zmodyfikować, `m_nFields` aby dopasować je do liczby kolumn w źródle danych).

Aby uzyskać więcej informacji, zobacz artykuł [Rekord: Deklarowanie klasy dla tabeli (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).

> [!CAUTION]
> Nazwa tabeli będzie pusta, jeśli struktura nie może zidentyfikować nazwy tabeli, jeśli podano wiele nazw tabel lub jeśli nie można zinterpretować instrukcji **CALL.** Należy zauważyć, że w przypadku korzystania z instrukcji **CALL** nie wolno wstawiać odstępów między nawiasem klamrowym a słowem kluczowym **CALL,** ani nie należy wstawiać odstępów przed nawiasem klamrowym lub przed słowem kluczowym **SELECT** w instrukcji **SELECT.**

## <a name="crecordsetgetfieldvalue"></a><a name="getfieldvalue"></a>Zestaw CRecordset::GetFieldValue

Pobiera dane pól w bieżącym rekordzie.

```
void GetFieldValue(
    LPCTSTR lpszName,
    CDBVariant& varValue,
    short nFieldType = DEFAULT_FIELD_TYPE);

void GetFieldValue(
    short nIndex,
    CDBVariant& varValue,
    short nFieldType = DEFAULT_FIELD_TYPE);

void GetFieldValue(
    short nIndex,
    CStringA& strValue);

void GetFieldValue(
    short nIndex,
    CStringW& strValue);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
Nazwa pola.

*varValu*e Odwołanie do obiektu [CDBVariant,](../../mfc/reference/cdbvariant-class.md) który będzie przechowywać wartość pola.

*nPusty typ pola*<br/>
Typ danych ODBC C pola. Przy użyciu wartości domyślnej, DEFAULT_FIELD_TYPE, siły `GetFieldValue` do określenia typu danych C z typu danych SQL, na podstawie poniższej tabeli. W przeciwnym razie można określić typ danych bezpośrednio lub wybrać zgodny typ danych; można na przykład zapisać dowolny typ danych w SQL_C_CHAR.

|Typ danych C|Typ danych SQL|
|-----------------|-------------------|
|SQL_C_BIT|SQL_BIT|
|SQL_C_UTINYINT|SQL_TINYINT|
|SQL_C_SSHORT|SQL_SMALLINT|
|SQL_C_SLONG|SQL_INTEGER|
|SQL_C_FLOAT|SQL_REAL|
|SQL_C_DOUBLE|SQL_FLOATSQL_DOUBLE|
|SQL_C_TIMESTAMP|SQL_DATESQL_TIMESQL_TIMESTAMP|
|Sql_c_char|SQL_NUMERICSQL_DECIMALSQL_BIGINTSQL_CHARSQL_VARCHARSQL_LONGVARCHAR|
|Sql_c_binary|SQL_BINARYSQL_VARBINARYSQL_LONGVARBINARY|

Aby uzyskać więcej informacji na temat typów danych ODBC, zobacz tematy "Typy danych SQL" i "Typy danych C" w dodatku D zestawu SDK systemu Windows.

*Nindex*<br/>
Indeks pola od zera.

*strValue (wartość)*<br/>
Odwołanie do obiektu [CString,](../../atl-mfc-shared/reference/cstringt-class.md) który będzie przechowywać wartość pola przekonwertowane na tekst, niezależnie od typu danych pola.

### <a name="remarks"></a>Uwagi

Można wyszukać pole według nazwy lub indeksu. Wartość pola można przechowywać w `CDBVariant` obiekcie `CString` lub obiekcie.

Jeśli zaimplementowano pobieranie wiersza zbiorczego, bieżący rekord jest zawsze umieszczany na pierwszym rekordzie w zestawie wierszy. Aby `GetFieldValue` użyć w rekordzie w danym zestawie wierszy, należy najpierw wywołać [setRowsetCursorPosition](#setrowsetcursorposition) funkcji elementu członkowskiego, aby przenieść kursor do żądanego wiersza w tym zestawie wierszy. Następnie `GetFieldValue` zadzwoń do tego wiersza. Aby zaimplementować pobieranie wiersza `CRecordset::useMultiRowFetch` zbiorczego, należy określić opcję parametru *dwOptions* w funkcji Elementu członkowskiego [Otwórz.](#open)

Można użyć `GetFieldValue` do dynamicznego pobierania pól w czasie wykonywania, a nie statycznie wiążąc je w czasie projektowania. Na przykład, jeśli zadeklarowano obiekt zestaw `CRecordset`rekordów bezpośrednio `GetFieldValue` z programu , należy użyć do pobrania danych pola; wymiana pól rekordów (RFX) lub zbiorcza wymiana pól rekordów (Bulk RFX) nie jest zaimplementowana.

> [!NOTE]
> Jeśli deklarujesz obiekt pliku recordset `CRecordset`bez wyprowadzania z , nie mają biblioteki kursora ODBC załadowany. Biblioteka kursorów wymaga, aby wstawce rekordów była co najmniej jedna kolumna powiązana; jednak podczas korzystania `CRecordset` bezpośrednio, żadna z kolumn są powiązane. Funkcje członkowskie [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) i [CDatabase::Otwórz](../../mfc/reference/cdatabase-class.md#open) kontrolę, czy biblioteka kursora zostanie załadowana.

`GetFieldValue`wywołuje funkcję `SQLGetData`API ODBC . Jeśli sterownik wyprowadza wartość SQL_NO_TOTAL dla rzeczywistej długości wartości pola, `GetFieldValue` zgłasza wyjątek. Aby uzyskać `SQLGetData`więcej informacji na temat programu , zobacz SDK systemu Windows.

### <a name="example"></a>Przykład

Poniższy przykładowy kod `GetFieldValue` ilustruje wywołania obiektu `CRecordset`zestawu rekordów zadeklarowanego bezpośrednio z pliku .

[!code-cpp[NVC_MFCDatabase#23](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]

> [!NOTE]
> W przeciwieństwie do `CDaoRecordset` `CRecordset` klasy DAO `SetFieldValue` , nie ma funkcji elementu członkowskiego. Jeśli obiekt zostanie utworzony `CRecordset`bezpośrednio z obiektu , jest on skutecznie tylko do odczytu.

Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetgetodbcfieldcount"></a><a name="getodbcfieldcount"></a>Zestaw CRecordset::GetODBCFieldCount

Pobiera całkowitą liczbę pól w obiekcie zestawu rekordów.

```
short GetODBCFieldCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba pól w tablicy rekordów.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat tworzenia rekordów, zobacz artykuł [Tablica rekordów: Tworzenie i zamykanie rekordów (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

## <a name="crecordsetgetodbcfieldinfo"></a><a name="getodbcfieldinfo"></a>Zestaw CRecordset::GetODBCFieldInfo

Uzyskuje informacje o polach w zakuła rekord.

```
void GetODBCFieldInfo(
    LPCTSTR lpszName,
    CODBCFieldInfo& fieldinfo);

void GetODBCFieldInfo(
    short nIndex,
    CODBCFieldInfo& fieldinfo);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
Nazwa pola.

*Fieldinfo*<br/>
Odwołanie do `CODBCFieldInfo` struktury.

*Nindex*<br/>
Indeks pola od zera.

### <a name="remarks"></a>Uwagi

Jedna wersja funkcji umożliwia wyszukywanie pola według nazwy. Druga wersja umożliwia wyszukywę pola według indeksu.

Aby uzyskać opis zwracanych informacji, zobacz [strukturę CODBCFieldInfo.](../../mfc/reference/codbcfieldinfo-structure.md)

Aby uzyskać więcej informacji na temat tworzenia rekordów, zobacz artykuł [Tablica rekordów: Tworzenie i zamykanie rekordów (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

## <a name="crecordsetgetrecordcount"></a><a name="getrecordcount"></a>Zestaw CRecordset::GetRecordCount

Określa rozmiar pliku recordset.

```
long GetRecordCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba rekordów w tablicy rekordów; 0, jeśli w akucie nie ma rekordów; lub -1, jeśli nie można określić liczby rekordów.

### <a name="remarks"></a>Uwagi

> [!CAUTION]
> Liczba rekordów jest utrzymywana jako "wysoki znak wody", rekord o najwyższym numerze, który jest jeszcze widoczny, gdy użytkownik przechodzi przez rekordy. Całkowita liczba rekordów jest znana tylko po przeniesieniu przez użytkownika poza ostatni rekord. Ze względu na wydajność liczba nie `MoveLast`jest aktualizowana podczas wywoływania . Aby zliczyć rekordy `MoveNext` samodzielnie, `IsEOF` wywołaj wielokrotnie, aż powróci nonzero. Dodawanie rekordu `CRecordset:AddNew` za `Update` pośrednictwem i zwiększa liczbę; usunięcie rekordu poprzez `CRecordset::Delete` zmniejszenie liczby.

## <a name="crecordsetgetrowsetsize"></a><a name="getrowsetsize"></a>CRecordset::Rozmiar zestawu GetRowsetSize

Uzyskuje bieżące ustawienie liczby wierszy, które mają być pobierane podczas danego pobierania.

```
DWORD GetRowsetSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba wierszy do pobrania podczas danego pobierania.

### <a name="remarks"></a>Uwagi

Jeśli używasz pobierania wiersza zbiorczego, domyślny rozmiar zestawu wierszy po otwarciu zestawu rekordów wynosi 25; w przeciwnym razie jest to 1.

Aby zaimplementować pobieranie wiersza `CRecordset::useMultiRowFetch` zbiorczego, należy określić opcję w parametrze *dwOptions* funkcji elementu członkowskiego [Otwórz.](#open) Aby zmienić ustawienie rozmiaru zestawu wierszy, zadzwoń do [SetRowsetSize](#setrowsetsize).

Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetgetrowsfetched"></a><a name="getrowsfetched"></a>CRecordset::GetRowsFetched

Określa, ile rekordów zostało faktycznie pobranych po pobraniu.

```
DWORD GetRowsFetched() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba wierszy pobranych ze źródła danych po danym pobraniu.

### <a name="remarks"></a>Uwagi

Jest to przydatne, gdy zaimplementowano pobieranie wiersza zbiorczego. Rozmiar zestawu wierszy zwykle wskazuje, ile wierszy zostanie pobranych z pobierania; jednak całkowita liczba wierszy w zestawie rekordów wpływa również na liczbę wierszy pobranych w zestawie wierszy. Na przykład jeśli zestaw rekordów ma 10 rekordów z ustawieniem rozmiaru zestawu wierszy `MoveNext` 4, a następnie zapętlanie przez zestaw rekordów przez wywołanie spowoduje, że końcowy zestaw wierszy ma tylko 2 rekordy.

Aby zaimplementować pobieranie wiersza `CRecordset::useMultiRowFetch` zbiorczego, należy określić opcję w parametrze *dwOptions* funkcji elementu członkowskiego [Otwórz.](#open) Aby określić rozmiar zestawu wierszy, zadzwoń do [SetRowsetSize](#setrowsetsize).

Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#24](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]

## <a name="crecordsetgetrowstatus"></a><a name="getrowstatus"></a>CRecordset::GetRowStatus

Uzyskuje stan wiersza w bieżącym zestawie wierszy.

```
WORD GetRowStatus(WORD wRow) const;
```

### <a name="parameters"></a>Parametry

*wrow (wrow)*<br/>
Jednopozycjowe położenie wiersza w bieżącym zestawie wierszy. Ta wartość może wynosić od 1 do rozmiaru zestawu wierszy.

### <a name="return-value"></a>Wartość zwracana

Wartość stanu dla wiersza. Aby uzyskać szczegółowe informacje, zobacz Uwagi.

### <a name="remarks"></a>Uwagi

`GetRowStatus`zwraca wartość, która wskazuje, że wszelkie zmiany stanu wiersza, ponieważ został ostatnio pobrany ze źródła danych lub że nie wiersz *odpowiadający wRow* został pobrany. W poniższej tabeli wymieniono możliwe wartości zwracane.

|Wartość stanu|Opis|
|------------------|-----------------|
|SQL_ROW_SUCCESS|Wiersz pozostaje niezmieniony.|
|SQL_ROW_UPDATED|Wiersz został zaktualizowany.|
|Sql_row_deleted|Wiersz został usunięty.|
|SQL_ROW_ADDED|Wiersz został dodany.|
|SQL_ROW_ERROR|Wiersz jest niedoścignielny z powodu błędu.|
|SQL_ROW_NOROW|Nie ma wiersza, który odpowiada *wRow*.|

Aby uzyskać więcej informacji, zobacz `SQLExtendedFetch` funkcję interfejsu API ODBC w programie Windows SDK.

## <a name="crecordsetgetstatus"></a><a name="getstatus"></a>CRecordset::GetStatus

Określa indeks bieżącego rekordu w ach i to, czy ostatni rekord został zaobserwowany.

```
void GetStatus(CRecordsetStatus& rStatus) const;
```

### <a name="parameters"></a>Parametry

*rStatus*<br/>
Odwołanie do `CRecordsetStatus` obiektu. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.

### <a name="remarks"></a>Uwagi

`CRecordset`próby śledzenia indeksu, ale w pewnych okolicznościach może to nie być możliwe. Zobacz [GetRecordCount,](#getrecordcount) aby uzyskać wyjaśnienie.

Struktura `CRecordsetStatus` ma następującą formę:

```cpp
struct CRecordsetStatus
{
    long m_lCurrentRecord;
    BOOL m_bRecordCountFinal;
};
```

Dwaj członkowie `CRecordsetStatus` mają następujące znaczenie:

- `m_lCurrentRecord`Zawiera indeks od zera bieżącego rekordu w rekordzie, jeśli jest znany. Jeśli nie można określić indeksu, ten element członkowski zawiera AFX_CURRENT_RECORD_UNDEFINED (-2). Jeśli `IsBOF` ma wartość TRUE (pusty zestaw rekordów `m_lCurrentRecord` lub próba przewijania przed pierwszym rekordem), jest ustawiona na AFX_CURRENT_RECORD_BOF (-1). Jeśli na pierwszym rekordzie, a następnie jest ustawiona na 0, drugi rekord 1 i tak dalej.

- `m_bRecordCountFinal`Wartość niezerowa, jeśli ustalono całkowitą liczbę rekordów w tablicy rekordów. Ogólnie rzecz biorąc, należy to osiągnąć, zaczynając od `MoveNext` `IsEOF` początku pliku recordset i wywołując do momentu powrotu nonzero. Jeśli ten element członkowski wynosi zero, liczba rekordów zwracana przez `GetRecordCount`, jeśli nie -1, jest tylko "znakiem wysokiej wody" liczby rekordów.

## <a name="crecordsetgetsql"></a><a name="getsql"></a>Zestaw CRecordset::GetSQL

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać instrukcję SQL, która została użyta do wybrania rekordów zestawie rekordów rekordów podczas jego otwarcia.

```
const CString& GetSQL() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie **const** do `CString` instrukcji SQL, która zawiera instrukcję SQL.

### <a name="remarks"></a>Uwagi

Zazwyczaj będzie to instrukcja SQL **SELECT.** Ciąg zwracany `GetSQL` przez jest tylko do odczytu.

Ciąg zwracany `GetSQL` przez zazwyczaj różni się od dowolnego ciągu, który mógł zostać przekazany do `Open` pliku recordset w parametrze *lpszSQL* do funkcji elementu członkowskiego. Dzieje się tak, ponieważ zestaw rekordów konstruuje `Open`pełną instrukcję SQL na podstawie tego, do `m_strFilter` czego `m_strSort` został przekazany , co zostało określone za pomocą ClassWizard, co można określić w i elementy członkowskie danych i wszelkie parametry, które mogą być określone. Aby uzyskać szczegółowe informacje o tym, jak zestawie rekordów konstruuje tę instrukcję SQL, zobacz artykuł [Zestawienie rekordów: Jak zestawy rekordów wybierz rekordy (ODBC).](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)

> [!NOTE]
> Wywołanie tej funkcji elementu członkowskiego dopiero po wywołaniu [otwórz](#open).

## <a name="crecordsetgettablename"></a><a name="gettablename"></a>Zestaw CRecord::GetTableName

Pobiera nazwę tabeli SQL, na której opiera się kwerenda omioń.

```
const CString& GetTableName() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie **const** do `CString` a, który zawiera nazwę tabeli, jeśli rekord jest oparty na tabeli; w przeciwnym razie pusty ciąg.

### <a name="remarks"></a>Uwagi

`GetTableName`jest prawidłowy tylko wtedy, gdy zestaw rekordów jest oparty na tabeli, a nie sprzężeniu wielu tabel lub wstępnie zdefiniowanej kwerendy (procedura składowana). Nazwa jest tylko do odczytu.

> [!NOTE]
> Wywołanie tej funkcji elementu członkowskiego dopiero po wywołaniu [otwórz](#open).

## <a name="crecordsetisbof"></a><a name="isbof"></a>CRecordset::IsBOF

Zwraca wartość niezerowa, jeśli grupa rekordów została mieszczona przed pierwszym rekordem. Nie ma bieżącego rekordu.

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość niezerowa, jeśli grupa rekordów nie zawiera żadnych rekordów lub jeśli przewinąłeś do tyłu przed pierwszym rekordem; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji elementu członkowskiego przed przewinięciem z rekordu do rekordu, aby dowiedzieć się, czy zostały one przed pierwszym rekordem rekordu rekordu. Można również `IsBOF` użyć `IsEOF` wraz z określić, czy plik recordset zawiera żadnych rekordów lub jest pusty. Natychmiast po `Open`wywołaniu , jeśli plik `IsBOF` recordset nie zawiera żadnych rekordów, zwraca wartość niezerowa. Po otwarciu pliku recordset, który ma co najmniej jeden `IsBOF` rekord, pierwszym rekordem jest bieżący rekord i zwraca wartość 0.

Jeśli pierwszy rekord jest bieżący `MovePrev`rekord `IsBOF` i wywołanie , następnie zwróci nonzero. Jeśli `IsBOF` zwraca nonzero `MovePrev`i wywołać , występuje błąd. Jeśli `IsBOF` zwraca wartość niezerową, bieżący rekord jest niezdefiniowany, a każda akcja wymagająca bieżącego rekordu spowoduje błąd.

### <a name="example"></a>Przykład

W tym `IsBOF` przykładzie użyto i `IsEOF` wykryć limity a recordset jak kod przewija się przez recordset w obu kierunkach.

[!code-cpp[NVC_MFCDatabase#25](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]

## <a name="crecordsetisdeleted"></a><a name="isdeleted"></a>CRecordset::JestDeletowany

Określa, czy bieżący rekord został usunięty.

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>Wartość zwracana

Pozycja niezerowa, jeśli znak rekordów jest umieszczony na usuniętym rekordzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli przewiniesz `IsDeleted` do rekordu i zwróci wartość TRUE (niezerowa), należy przewinąć do innego rekordu, zanim będzie można wykonać inne operacje na macie rekord.

Wynik `IsDeleted` zależy od wielu czynników, takich jak typ zestawu rekordów, czy zestaw rekordów jest aktualizowany, czy `CRecordset::skipDeletedRecords` określono opcję podczas otwarcia zestawu rekordów, czy sterownikuje usunięte rekordy i czy istnieje wielu użytkowników.

Aby uzyskać `CRecordset::skipDeletedRecords` więcej informacji na temat pakowania sterowników i ich pakowania, zobacz funkcję [Otwórz](#open) element członkowski.

> [!NOTE]
> Jeśli zaimplementowano pobieranie wiersza zbiorczego, nie należy wywoływać `IsDeleted`. Zamiast tego wywołać funkcję elementu członkowskiego [GetRowStatus.](#getrowstatus) Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetiseof"></a><a name="iseof"></a>CRecordset::IsEOF

Zwraca wartość niezerowa, jeśli po ostatnim rekordzie został umieszczony po ostatnim rekordzie. Nie ma bieżącego rekordu.

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli rekord nie zawiera żadnych rekordów lub jeśli przewinął poza ostatni rekord; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji elementu członkowskiego podczas przewijania z rekordu do rekordu, aby dowiedzieć się, czy wyszedłeś poza ostatni rekord rekordu rekordu rekordu. Można również `IsEOF` użyć do określenia, czy plik recordset zawiera jakieś rekordy lub jest pusty. Natychmiast po `Open`wywołaniu , jeśli plik `IsEOF` recordset nie zawiera żadnych rekordów, zwraca wartość niezerowa. Po otwarciu pliku recordset, który ma co najmniej jeden `IsEOF` rekord, pierwszym rekordem jest bieżący rekord i zwraca wartość 0.

Jeśli ostatni rekord jest bieżącym rekordem `IsEOF` podczas wywoływania, `MoveNext`następnie zwróci nonzero. Jeśli `IsEOF` zwraca nonzero `MoveNext`i wywołać , występuje błąd. Jeśli `IsEOF` zwraca wartość niezerową, bieżący rekord jest niezdefiniowany, a każda akcja wymagająca bieżącego rekordu spowoduje błąd.

### <a name="example"></a>Przykład

Zobacz przykład [dla IsBOF](#isbof).

## <a name="crecordsetisfielddirty"></a><a name="isfielddirty"></a>CRecordset::IsFieldDirty

Określa, czy określony element członkowski danych pola został zmieniony od czasu [wywołania edycji](#edit) lub [addnew.](#addnew)

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
Wskaźnik do elementu członkowskiego danych pola, którego stan chcesz sprawdzić, lub NULL, aby ustalić, czy którekolwiek z pól są zabrudzone.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli określony element członkowski `AddNew` `Edit`danych pola zmienił się od momentu wywołania lub ; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Dane we wszystkich elementach członkowskich danych brudnego pola zostaną przesłane do rekordu w źródle danych, gdy bieżący `Edit` rekord `AddNew`zostanie zaktualizowany przez wywołanie funkcji Aktualizuj element [członkowski](#update) `CRecordset` (po wywołaniu lub ).

> [!NOTE]
> Ta funkcja elementu członkowskiego nie ma zastosowania w grupach rekordów, które używają zbiorczego pobierania wierszy. Jeśli zaimplementowano pobieranie wiersza zbiorczego, zawsze `IsFieldDirty` zwróci wartość FAŁSZ i spowoduje niepowodzenie potwierdzenia. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Wywołanie `IsFieldDirty` spowoduje zresetowanie efektów poprzednich wywołań [do SetFieldDirty,](#setfielddirty) ponieważ stan brudny pola jest ponownie oceniany. W `AddNew` przypadku, gdy bieżąca wartość pola różni się od pseudo null wartość, stan pola jest ustawiony zabrudzony. W `Edit` przypadku, gdy wartość pola różni się od wartości buforowanej, stan pola jest ustawiony zabrudzony.

`IsFieldDirty`jest realizowany za pośrednictwem [DoFieldExchange](#dofieldexchange).

Aby uzyskać więcej informacji na temat brudnej flagi, zobacz artykuł [Recordset: How Recordsets Select Records (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

## <a name="crecordsetisfieldnull"></a><a name="isfieldnull"></a>CRecordset::IsFieldNull

Zwraca wartość niezerową, jeśli określone pole w bieżącym rekordzie to Null (nie ma wartości).

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
Wskaźnik do elementu członkowskiego danych pola, którego stan chcesz sprawdzić, lub NULL, aby ustalić, czy którekolwiek z pól ma wartość Null.

### <a name="return-value"></a>Wartość zwracana

Wartość niezerowa, jeśli określony element członkowski danych pola jest oznaczony jako Null; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy określony element członkowski danych pola zestaw rekordów został oznaczony jako Null. (W terminologii bazy danych Null oznacza "bez wartości" i nie jest taka sama jak NULL w języku C++.) Jeśli element członkowski danych pola jest oflagowany jako Null, jest interpretowany jako kolumna bieżącego rekordu, dla której nie ma wartości.

> [!NOTE]
> Ta funkcja elementu członkowskiego nie ma zastosowania w grupach rekordów, które używają zbiorczego pobierania wierszy. Jeśli zaimplementowano pobieranie wiersza zbiorczego, zawsze `IsFieldNull` zwróci wartość FAŁSZ i spowoduje niepowodzenie potwierdzenia. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`IsFieldNull`jest realizowany za pośrednictwem [DoFieldExchange](#dofieldexchange).

## <a name="crecordsetisfieldnullable"></a><a name="isfieldnullable"></a>CRecordset::IsFieldNullable

Zwraca wartość wartość niezerową, jeśli określone pole w bieżącym rekordzie można ustawić na Null (bez wartości).

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
Wskaźnik do elementu członkowskiego danych pola, którego stan chcesz sprawdzić, lub NULL, aby ustalić, czy którekolwiek z pól można ustawić na wartość Null.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy określony element członkowski danych pola jest "nullable" (można ustawić na wartość Null; C++ NULL nie jest taki sam jak Null, co w terminologii bazy danych oznacza "nie mając żadnej wartości").

> [!NOTE]
> Jeśli zaimplementowano pobieranie wiersza `IsFieldNullable`zbiorczego, nie można wywołać . Zamiast tego należy wywołać funkcję elementu członkowskiego [GetODBCFieldInfo,](#getodbcfieldinfo) aby ustalić, czy pole można ustawić na wartość Null. Należy zauważyć, że `GetODBCFieldInfo`zawsze można wywołać , niezależnie od tego, czy zostały zaimplementowane pobieranie wiersza zbiorczego. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Pole, które nie może być null musi mieć wartość. Jeśli spróbujesz ustawić takie pole na Null podczas dodawania lub aktualizowania rekordu, źródło danych odrzuca dodawanie lub aktualizację, a [update](#update) zda wyjątek. Wyjątek występuje podczas `Update`wywoływania , a nie podczas wywoływania [SetFieldNull](#setfieldnull).

Użycie wartości NULL dla pierwszego argumentu funkcji `outputColumn` spowoduje zastosowanie `param` funkcji tylko do pól, a nie pól. Na przykład wezwanie do

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

ustawi `outputColumn` tylko pola na NULL; `param` nie ulegnie to poprawie.

Aby pracować `param` nad polami, należy podać `param` rzeczywisty adres osoby, nad którą chcesz pracować, na przykład:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

Oznacza to, że `param` nie można ustawić wszystkich `outputColumn` pól na NULL, tak jak w polach.

`IsFieldNullable`jest realizowany za pośrednictwem [DoFieldExchange](#dofieldexchange).

## <a name="crecordsetisopen"></a><a name="isopen"></a>CRecordset::Isopen

Określa, czy plan rekordów jest już otwarty.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Wartość zwracana

Opcja niezerowa, jeśli funkcja elementu członkowskiego [Otwórz](#open) lub [Ponowniequerować](#requery) obiektu jest wcześniej wywoływana, a grupa rekordów nie została zamknięta; w przeciwnym razie 0.

## <a name="crecordsetm_hstmt"></a><a name="m_hstmt"></a>CRecordset::m_hstmt

Zawiera dojście do struktury danych instrukcji ODBC typu HSTMT skojarzonego z zestawem rekordów.

### <a name="remarks"></a>Uwagi

Każde zapytanie do źródła danych ODBC jest skojarzone z HSTMT.

> [!CAUTION]
> Nie używaj `m_hstmt` przed wywołaniem [Open.](#open)

Zwykle nie trzeba uzyskać dostęp do HSTMT bezpośrednio, ale może być potrzebny do bezpośredniego wykonywania instrukcji SQL. Funkcja `ExecuteSQL` elementu członkowskiego `CDatabase` klasy zawiera `m_hstmt`przykład użycia .

## <a name="crecordsetm_nfields"></a><a name="m_nfields"></a>CRecordset::m_nFields

Zawiera liczbę elementów członkowskich danych pól w klasie zestawu rekordów; oznacza to, że liczba kolumn wybranych przez zestaw rekordów ze źródła danych.

### <a name="remarks"></a>Uwagi

Konstruktor dla klasy zestawu rekordów musi zainicjować `m_nFields` z poprawną liczbą. Jeśli pobieranie wiersza zbiorczego nie zostało zaimplementowane, ClassWizard zapisuje tę inicjację, gdy używasz jej do deklarowania klasy pliku recordset. Można również napisać go ręcznie.

Struktura używa tego numeru do zarządzania interakcją między elementami członkowskich danych pola i odpowiednimi kolumnami bieżącego rekordu w źródle danych.

> [!CAUTION]
> Liczba ta musi odpowiadać liczbie "kolumn wyjściowych" zarejestrowanych `DoFieldExchange` w lub `DoBulkFieldExchange` po wywołaniu [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) z parametrem `CFieldExchange::outputColumn`.

Kolumny można wiązać dynamicznie, jak wyjaśniono w artykule "Zestaw rekordów: dynamicznie wiążące kolumny danych". W tym przypadku należy zwiększyć liczbę, `m_nFields` aby odzwierciedlić liczbę wywołań `DoFieldExchange` funkcji `DoBulkFieldExchange` RFX lub bulk RFX w funkcji lub elementu członkowskiego dla kolumn powiązanych dynamicznie.

Aby uzyskać więcej informacji, zobacz artykuły [Zestaw rekordów: Dynamicznie wiążące kolumny danych (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) i [Recordset: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Przykład

Zobacz artykuł [Wymiana pól rekordu: korzystanie z RFX](../../data/odbc/record-field-exchange-using-rfx.md).

## <a name="crecordsetm_nparams"></a><a name="m_nparams"></a>CRecordset::m_nParams

Zawiera liczbę elementów członkowskich danych parametrów w klasie zestawu rekordów; oznacza to, że liczba parametrów przekazanych wraz z zapytaniem zestawu rekordów.

### <a name="remarks"></a>Uwagi

Jeśli klasa zestawu rekordów ma żadnych elementów członkowskich danych `m_nParams` parametrów, konstruktor dla klasy musi zainicjować z poprawną liczbą. Wartość domyślna `m_nParams` wynosi 0. W przypadku dodawania elementów członkowskich danych parametrów (które należy wykonać ręcznie) należy również ręcznie dodać inicjalizację w konstruktorze klasy, aby `m_strFilter` odzwierciedlić liczbę parametrów (które muszą być co najmniej tak duże, jak liczba symboli zastępczych '' w lub `m_strSort` ciągu).

Struktura używa tej liczby, gdy parametryzuje kwerendę zestawu rekordów.

> [!CAUTION]
> Numer ten musi odpowiadać liczbie "params" `DoFieldExchange` zarejestrowanej w lub `DoBulkFieldExchange` po wywołaniu `CFieldExchange::param` [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) z wartością parametru `CFieldExchange::inputParam`, `CFieldExchange::outputParam`, lub `CFieldExchange::inoutParam`.

### <a name="example"></a>Przykład

  Zobacz artykuły [Recordset: Parametrizing a Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) and [Record Field Exchange: Using RFX](../../data/odbc/record-field-exchange-using-rfx.md).

## <a name="crecordsetm_pdatabase"></a><a name="m_pdatabase"></a>CRecordset::m_pDatabase

Zawiera wskaźnik do `CDatabase` obiektu, za pomocą którego zestaw rekordów jest połączony ze źródłem danych.

### <a name="remarks"></a>Uwagi

Ta zmienna jest ustawiona na dwa sposoby. Zazwyczaj wskaźnik jest przekazywać do `CDatabase` już połączonego obiektu podczas konstruowania obiektu pliku recordset. Jeśli zamiast tego przekażesz wartość NULL, `CRecordset` utworzy `CDatabase` obiekt dla Ciebie i połączy go. W obu przypadkach `CRecordset` przechowuje wskaźnik w tej zmiennej.

Zwykle nie trzeba bezpośrednio używać wskaźnika przechowywanego w `m_pDatabase`pliku . Jeśli jednak piszesz własne `CRecordset`rozszerzenia, może być konieczne użycie wskaźnika. Na przykład może być potrzebny wskaźnik, `CDBException`jeśli rzucisz własne s. Lub może być konieczne, jeśli trzeba zrobić `CDatabase` coś przy użyciu tego samego obiektu, takich `ExecuteSQL` jak uruchamianie `CDatabase` transakcji, ustawianie limitów czasu lub wywoływania funkcji elementu członkowskiego klasy do wykonywania instrukcji SQL bezpośrednio.

## <a name="crecordsetm_strfilter"></a><a name="m_strfilter"></a>CRecordset::m_strFilter

Po skonstruowaniu obiektu zestaw rekordów, `Open` ale przed wywołaniem jego funkcji `CString` elementu członkowskiego, należy użyć tego elementu członkowskiego danych do przechowywania zawierający klauzulę SQL **WHERE.**

### <a name="remarks"></a>Uwagi

The recordset używa tego ciągu do ograniczenia (lub filtrowania) rekordów, które wybiera podczas `Open` lub `Requery` wywołania. Jest to przydatne w przypadku wybierania podzbioru rekordów, takich jak "wszyscy sprzedawcy z siedzibą w Kalifornii" ("stan = urząd certyfikacji"). Składnia SQL ODBC dla klauzuli **WHERE** jest

`WHERE search-condition`

Należy pamiętać, że nie zawierają **where** słowa kluczowego w ciągu. Ramy dostarcza go.

Można również sparametryzować ciąg filtru, umieszczając w nim symbole zastępcze '', deklarując element członkowski danych parametrów w klasie dla każdego symbolu zastępczego i przekazując parametry do zestawu rekordów w czasie wykonywania. Dzięki temu można skonstruować filtr w czasie wykonywania. Aby uzyskać więcej informacji, zobacz artykuł [Recordset: Parametrizing a Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

Aby uzyskać więcej informacji na temat klauzul SQL **WHERE,** zobacz artykuł [SQL](../../data/odbc/sql.md). Aby uzyskać więcej informacji na temat wybierania i filtrowania rekordów, zobacz artykuł [Tablica rekordów: Filtrowanie rekordów (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#30](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]

## <a name="crecordsetm_strsort"></a><a name="m_strsort"></a>CRecordset::m_strSort

Po skonstruowaniu obiektu zestaw rekordów, `Open` ale przed wywołaniem jego funkcji `CString` elementu członkowskiego, należy użyć tego elementu członkowskiego danych do przechowywania zawierającego klauzulę **SQL ORDER BY.**

### <a name="remarks"></a>Uwagi

The recordset używa tego ciągu do sortowania `Open` rekordów, które wybiera podczas lub `Requery` wywołania. Za pomocą tej funkcji można sortować grupę rekordów w jednej lub kilku kolumnach. Składnia SQL ODBC dla klauzuli **ORDER BY** jest

`ORDER BY sort-specification [, sort-specification]...`

gdzie specyfikacja sortowania jest całkowitej liczby lub nazwy kolumny. Można również określić kolejność rosnącą lub malejącą (kolejność jest domyślnie rosnąca), dołączając "ASC" lub "DESC" do listy kolumn w ciągu sortowania. Wybrane rekordy są sortowane najpierw według pierwszej kolumny na liście, następnie według drugiej i tak dalej. Na przykład można zamówić "Klienci" recordset według nazwiska, a następnie imię. Liczba kolumn, które można wyświetlić, zależy od źródła danych. Aby uzyskać więcej informacji, zobacz SDK systemu Windows.

Należy pamiętać, że nie zawierają **kolejność według** słowa kluczowego w ciągu. Ramy dostarcza go.

Aby uzyskać więcej informacji na temat klauzul SQL, zobacz artykuł [SQL](../../data/odbc/sql.md). Aby uzyskać więcej informacji na temat sortowania rekordów, zobacz artykuł [Tablica rekordów: Sortowanie rekordów (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#31](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]

## <a name="crecordsetmove"></a><a name="move"></a>CRecordset::Przenieś

Przesuwa bieżący wskaźnik rekordu w komecie rekordów do przodu lub do tyłu.

```
virtual void Move(
    long nRows,
    WORD wFetchType = SQL_FETCH_RELATIVE);
```

### <a name="parameters"></a>Parametry

*Nrows*<br/>
Liczba wierszy do przesuń do przodu lub do tyłu. Wartości dodatnie poruszają się do przodu, pod koniec pliku recordset. Wartości ujemne przesuwają się do tyłu, w kierunku początku.

*wFetchType (Typ)*<br/>
Określa zestaw wierszy, który `Move` zostanie pobrany. Aby uzyskać szczegółowe informacje, zobacz Uwagi.

### <a name="remarks"></a>Uwagi

Jeśli przekażesz wartość 0 dla `Move` *nRows,* odświeży bieżący rekord; `Move` zakończy wszelkie `AddNew` bieżące lub `Edit` tryby i przywróci wartość `AddNew` `Edit` bieżącego rekordu przed lub został wywołany.

> [!NOTE]
> Podczas przechodzenia przez plan rekordów nie można pominąć usuniętych rekordów. Zobacz [CRecordset::IsDeleted aby](#isdeleted) uzyskać więcej informacji. Po otwarciu `CRecordset` `skipDeletedRecords` z zestawem `Move` opcji, potwierdza, jeśli *nRows* parametr jest 0. To zachowanie zapobiega odświeżaniu wierszy, które są usuwane przez inne aplikacje klienckie przy użyciu tych samych danych. Zobacz parametr *dwOption* w [Otwórz,](#open) aby uzyskać opis `skipDeletedRecords`.

`Move`zmienia położenie zestawu rekordów według zestawów wierszy. Na podstawie wartości *dla nRows* i *wFetchType*, pobiera odpowiedni zestaw wierszy, `Move` a następnie sprawia, że pierwszy rekord w tym wierszuzastaw bieżący rekord. Jeśli pobieranie wiersza zbiorczego nie zostało zaimplementowane, rozmiar zestawu wierszy jest zawsze 1. Podczas pobierania zestawu wierszy, `Move` bezpośrednio wywołuje [CheckRowsetError](#checkrowseterror) funkcji elementu członkowskiego do obsługi wszelkich błędów wynikających z pobierania.

W zależności od wartości, które `Move` `CRecordset` przekazujesz, jest odpowiednikiem innych funkcji członkowskich. W szczególności wartość *wFetchType* może wskazywać funkcję elementu członkowskiego, która jest bardziej intuicyjna i często preferowaną metodą przenoszenia bieżącego rekordu.

W poniższej tabeli wymieniono możliwe wartości dla *wFetchType*, zestawu wierszy, `Move` który zostanie pobrany na podstawie *wFetchType* i *nRows*oraz dowolnej równoważnej funkcji elementu członkowskiego odpowiadającej *wFetchType*.

|wFetchType (Typ)|Pobrany zestaw wierszy|Równoważna funkcja elementu członkowskiego|
|----------------|--------------------|--------------------------------|
|SQL_FETCH_RELATIVE (wartość domyślna)|Zestaw wierszy *rozpoczynający wiersze nRows* od pierwszego wiersza w bieżącym zestawie wierszy.||
|SQL_FETCH_NEXT|Następny zestaw wierszy; *nRows* jest ignorowany.|[Movenext](#movenext)|
|SQL_FETCH_PRIOR|Poprzedni zestaw wierszy; *nRows* jest ignorowany.|[Moveprev](#moveprev)|
|SQL_FETCH_FIRST|Pierwszy zestaw wierszy w zestawie rekordów; *nRows* jest ignorowany.|[Movefirst](#movefirst)|
|SQL_FETCH_LAST|Ostatni kompletny zestaw wierszy w zestawie rekordów; *nRows* jest ignorowany.|[Movelast](#movelast)|
|SQL_FETCH_ABSOLUTE|Jeśli *nRows* > 0, zestaw *wierszy rozpoczynających nRows* wierszy od początku zestawu rekordów. Jeśli *nRows* < 0, zestaw *wierszy rozpoczynających nRows* wierszy od końca zestawu rekordów. Jeśli *nRows* = 0, zwracany jest warunek początku pliku (BOF).|[SetAbsolutePosition (Pozycja zestawu)](#setabsoluteposition)|
|SQL_FETCH_BOOKMARK|Zestaw wierszy rozpoczynający się od wiersza, którego wartość zakładki odpowiada *nRows*.|[SetBookmark (Znak zestawu)](#setbookmark)|

> [!NOTE]
> W przypadku rekordów `Move` tylko do przodu jest prawidłowy tylko z wartością SQL_FETCH_NEXT dla *wFetchType*.

> [!CAUTION]
> Wywołanie `Move` zgłasza wyjątek, jeśli plik recordset nie ma rekordów. Aby ustalić, czy na maciewce rekordów są jakieś rekordy, należy wywołać [isbof](#isbof) i [iseof](#iseof).

> [!NOTE]
> Jeśli przewinąłeś poza początek lub koniec`IsBOF` pliku `IsEOF` recordset ( lub `Move` zwracasz wartość `CDBException`niezerową), wywołanie funkcji prawdopodobnie spowoduje wrzucenie pliku . Na przykład `IsEOF` jeśli zwraca nonzero `IsBOF` i `MoveNext` nie, a `MovePrev` następnie zda wyjątek, ale nie będzie.

> [!NOTE]
> Jeśli wywołasz, `Move` gdy bieżący rekord jest aktualizowany lub dodawany, aktualizacje zostaną utracone bez ostrzeżenia.

Aby uzyskać więcej informacji na temat nawigacji w forsach rekordów, zobacz artykuły [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) i [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Aby uzyskać powiązane informacje, zobacz `SQLExtendedFetch` funkcję interfejsu API ODBC w programie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#28](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]

## <a name="crecordsetmovefirst"></a><a name="movefirst"></a>CRecordset::MoveFirst

Sprawia, że pierwszy rekord w pierwszym wierszuzmieja bieżący rekord.

```
void MoveFirst();
```

### <a name="remarks"></a>Uwagi

Niezależnie od tego, czy pobieranie wiersza zbiorczego zostało zaimplementowane, zawsze będzie to pierwszy rekord w rekordzie.

Nie trzeba dzwonić `MoveFirst` natychmiast po otwarciu pliku recordset. W tym czasie pierwszy rekord (jeśli istnieje) jest automatycznie bieżącym rekordem.

> [!NOTE]
> Ta funkcja elementu członkowskiego jest nieprawidłowa dla rekordów tylko do przodu.

> [!NOTE]
> Podczas przechodzenia przez plan rekordów nie można pominąć usuniętych rekordów. Szczegółowe informacje można znaleźć w funkcji elementu członkowskiego [IsDeleted.](#isdeleted)

> [!CAUTION]
> Wywołanie `Move` dowolnej z funkcji zgłasza wyjątek, jeśli plik recordset nie ma rekordów. Aby ustalić, czy na macie `IsBOF` `IsEOF`rekordach są jakieś rekordy, należy wywołać i określić program .

> [!NOTE]
> Jeśli wywołasz dowolną `Move` z funkcji, gdy bieżący rekord jest aktualizowany lub dodawany, aktualizacje zostaną utracone bez ostrzeżenia.

Aby uzyskać więcej informacji na temat nawigacji w forsach rekordów, zobacz artykuły [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) i [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Przykład

  Zobacz przykład [dla IsBOF](#isbof).

## <a name="crecordsetmovelast"></a><a name="movelast"></a>CRecordset::MoveLast

Sprawia, że pierwszy rekord w ostatnim pełnym wierszuzmieć bieżący rekord.

```
void MoveLast();
```

### <a name="remarks"></a>Uwagi

Jeśli pobieranie wiersza zbiorczego nie zostało zaimplementowane, zestaw rekordów `MoveLast` ma rozmiar zestawu wierszy 1, więc po prostu przenosi się do ostatniego rekordu w zestawie rekordów.

> [!NOTE]
> Ta funkcja elementu członkowskiego jest nieprawidłowa dla rekordów tylko do przodu.

> [!NOTE]
> Podczas przechodzenia przez plan rekordów nie można pominąć usuniętych rekordów. Szczegółowe informacje można znaleźć w funkcji elementu członkowskiego [IsDeleted.](#isdeleted)

> [!CAUTION]
> Wywołanie `Move` dowolnej z funkcji zgłasza wyjątek, jeśli plik recordset nie ma rekordów. Aby ustalić, czy na macie `IsBOF` `IsEOF`rekordach są jakieś rekordy, należy wywołać i określić program .

> [!NOTE]
> Jeśli wywołasz dowolną `Move` z funkcji, gdy bieżący rekord jest aktualizowany lub dodawany, aktualizacje zostaną utracone bez ostrzeżenia.

Aby uzyskać więcej informacji na temat nawigacji w forsach rekordów, zobacz artykuły [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) i [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Przykład

  Zobacz przykład [dla IsBOF](#isbof).

## <a name="crecordsetmovenext"></a><a name="movenext"></a>Zestaw CRecordset::MoveNext

Sprawia, że pierwszy rekord w następnym wierszustawy bieżącego rekordu.

```
void MoveNext();
```

### <a name="remarks"></a>Uwagi

Jeśli pobieranie wiersza zbiorczego nie zostało zaimplementowane, zestaw rekordów `MoveNext` ma rozmiar zestawu wierszy 1, więc po prostu przechodzi do następnego rekordu.

> [!NOTE]
> Podczas przechodzenia przez plan rekordów nie można pominąć usuniętych rekordów. Szczegółowe informacje można znaleźć w funkcji elementu członkowskiego [IsDeleted.](#isdeleted)

> [!CAUTION]
> Wywołanie `Move` dowolnej z funkcji zgłasza wyjątek, jeśli plik recordset nie ma rekordów. Aby ustalić, czy na macie `IsBOF` `IsEOF`rekordach są jakieś rekordy, należy wywołać i określić program .

> [!NOTE]
> Zaleca się również połączenie `IsEOF` przed `MoveNext`wywołaniem . Na przykład, jeśli przewinąłeś poza koniec `IsEOF` akusety, zwróci nonzero; kolejne wywołanie `MoveNext` zgłosić wyjątek.

> [!NOTE]
> Jeśli wywołasz dowolną `Move` z funkcji, gdy bieżący rekord jest aktualizowany lub dodawany, aktualizacje zostaną utracone bez ostrzeżenia.

Aby uzyskać więcej informacji na temat nawigacji w forsach rekordów, zobacz artykuły [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) i [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Przykład

  Zobacz przykład [dla IsBOF](#isbof).

## <a name="crecordsetmoveprev"></a><a name="moveprev"></a>CRecordset::MovePrev

Sprawia, że pierwszy rekord w poprzednim wierszuzmieja bieżący rekord.

```
void MovePrev();
```

### <a name="remarks"></a>Uwagi

Jeśli pobieranie wiersza zbiorczego nie zostało zaimplementowane, zestaw rekordów `MovePrev` ma rozmiar zestawu wierszy 1, więc po prostu przechodzi do poprzedniego rekordu.

> [!NOTE]
> Ta funkcja elementu członkowskiego jest nieprawidłowa dla rekordów tylko do przodu.

> [!NOTE]
> Podczas przechodzenia przez plan rekordów nie można pominąć usuniętych rekordów. Szczegółowe informacje można znaleźć w funkcji elementu członkowskiego [IsDeleted.](#isdeleted)

> [!CAUTION]
> Wywołanie `Move` dowolnej z funkcji zgłasza wyjątek, jeśli plik recordset nie ma rekordów. Aby ustalić, czy na macie `IsBOF` `IsEOF`rekordach są jakieś rekordy, należy wywołać i określić program .

> [!NOTE]
> Zaleca się również połączenie `IsBOF` przed `MovePrev`wywołaniem . Na przykład, jeśli przewinąłeś przed rozpoczęciem forsowania, `IsBOF` powróci nonzero; kolejne wywołanie `MovePrev` zgłosić wyjątek.

> [!NOTE]
> Jeśli wywołasz dowolną `Move` z funkcji, gdy bieżący rekord jest aktualizowany lub dodawany, aktualizacje zostaną utracone bez ostrzeżenia.

Aby uzyskać więcej informacji na temat nawigacji w forsach rekordów, zobacz artykuły [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) i [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Przykład

  Zobacz przykład [dla IsBOF](#isbof).

## <a name="crecordsetonsetoptions"></a><a name="onsetoptions"></a>CRecordset::OnSetOptions

Wywoływana do ustawiania opcji (używanych przy wyborze) dla określonej instrukcji ODBC.

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*Hstmt*<br/>
HSTMT instrukcji ODBC, których opcje mają być ustawione.

### <a name="remarks"></a>Uwagi

Wywołanie, `OnSetOptions` aby ustawić opcje (używane przy wyborze) dla określonej instrukcji ODBC. Struktura wywołuje tę funkcję elementu członkowskiego, aby ustawić opcje początkowe dla zestawu rekordów. `OnSetOptions`określa obsługę źródła danych dla przewijanych kursorów i współbieżności kursora i odpowiednio ustawia opcje zestawu rekordów. (Podczas `OnSetOptions` gdy jest używany `OnSetUpdateOptions` do operacji selekcji, jest używany do operacji aktualizacji.)

Zastądania, `OnSetOptions` aby ustawić opcje specyficzne dla sterownika lub źródła danych. Na przykład jeśli źródło danych obsługuje otwieranie `OnSetOptions` dla wyłącznego dostępu, można zastąpić, aby skorzystać z tej możliwości.

Aby uzyskać więcej informacji na temat kursorów, zobacz artykuł [ODBC](../../data/odbc/odbc-basics.md).

## <a name="crecordsetonsetupdateoptions"></a><a name="onsetupdateoptions"></a>CRecordset::OnSetUpdateOptions

Wywoływana, aby ustawić opcje (używane w aktualizacji) dla określonej instrukcji ODBC.

```
virtual void OnSetUpdateOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*Hstmt*<br/>
HSTMT instrukcji ODBC, których opcje mają być ustawione.

### <a name="remarks"></a>Uwagi

Wywołanie, `OnSetUpdateOptions` aby ustawić opcje (używane w aktualizacji) dla określonej instrukcji ODBC. Struktura wywołuje tę funkcję elementu członkowskiego po tym, jak tworzy HSTMT do aktualizowania rekordów w ach. (Podczas `OnSetOptions` gdy jest używany `OnSetUpdateOptions` do operacji selekcji, jest używany do operacji aktualizacji.) `OnSetUpdateOptions` określa obsługę źródła danych dla przewijanych kursorów i współbieżności kursora i odpowiednio ustawia opcje zestawu rekordów.

`OnSetUpdateOptions` Zastąp, aby ustawić opcje instrukcji ODBC, zanim ta instrukcja jest używana do uzyskiwania dostępu do bazy danych.

Aby uzyskać więcej informacji na temat kursorów, zobacz artykuł [ODBC](../../data/odbc/odbc-basics.md).

## <a name="crecordsetopen"></a><a name="open"></a>Crecordset::open

Otwiera plik recordset, pobierając tabelę lub wykonując kwerendę, którą reprezentuje aplika.

```
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,
    LPCTSTR lpszSQL = NULL,
    DWORD dwOptions = none);
```

### <a name="parameters"></a>Parametry

*nOtwartyty*<br/>
Zaakceptuj wartość domyślną, AFX_DB_USE_DEFAULT_TYPE lub użyj jednej z następujących `enum OpenType`wartości z :

- `CRecordset::dynaset`Wielokierunkowy pasek z przewijaniem dwukierunkowym. Członkostwo i kolejność rekordów są określane po otwarciu zbioru rekordów, ale zmiany wprowadzone przez innych użytkowników do wartości danych są widoczne po operacji pobierania. Zestawy dynasetów są również nazywane zestawami rekordów opartymi na zestawach kluczy.

- `CRecordset::snapshot`Statyczny rekord z dwukierunkowym przewijaniem. Członkostwo i kolejność rekordów są określane po otwarciu listy rekordów; wartości danych są określane podczas pobierania rekordów. Zmiany wprowadzone przez innych użytkowników nie są widoczne, dopóki plik rekordów nie zostanie zamknięty, a następnie ponownie otwarty.

- `CRecordset::dynamic`Wielokierunkowy pasek z przewijaniem dwukierunkowym. Zmiany wprowadzone przez innych użytkowników do członkostwa, zamawiania i wartości danych są widoczne po operacji pobierania. Należy zauważyć, że wiele sterowników ODBC nie obsługuje tego typu pliku recordset.

- `CRecordset::forwardOnly`A tylko do odczytu rekordet z tylko do przodu przewijania.

   Dla `CRecordset`, wartość `CRecordset::snapshot`domyślna to . Mechanizm wartości domyślnej umożliwia kreatorom języka Visual C++ `CRecordset` interakcję `CDaoRecordset`z odbc i DAO, które mają różne wartości domyślne.

Aby uzyskać więcej informacji na temat tych typów rekordów, zobacz artykuł [Recordset (ODBC)](../../data/odbc/recordset-odbc.md). Aby uzyskać powiązane informacje, zobacz artykuł "Używanie kursorów blokowych i przewijalnych" w programie Windows SDK.

> [!CAUTION]
> Jeśli żądany typ nie jest obsługiwany, struktura zgłasza wyjątek.

*Lpszsql*<br/>
Wskaźnik ciągu zawierający jedną z następujących czynności:

- Wskaźnik NULL.

- Nazwa tabeli.

- Instrukcja SQL **SELECT** (opcjonalnie z klauzulą SQL **WHERE** lub **ORDER BY).**

- Instrukcja **CALL** określająca nazwę wstępnie zdefiniowanej kwerendy (procedura składowana). Należy uważać, aby nie wstawiać odstępów między nawiasem klamry kręcone i **CALL** słowa kluczowego.

Aby uzyskać więcej informacji na temat tego ciągu, zobacz tabeli i dyskusji roli ClassWizard w sekcji [Uwagi.](#remarks)

> [!NOTE]
> Kolejność kolumn w zestawie wyników musi być zgodna z kolejnością wywołań funkcji RFX lub Bulk RFX w zastąpieniu funkcji [DoFieldExchange](#dofieldexchange) lub [DoBulkFieldExchange.](#dobulkfieldexchange)

*Dwoptions*<br/>
Maska bitowa, która może określić kombinację wartości wymienionych poniżej. Niektóre z nich wzajemnie się wykluczają. Wartością domyślną jest **brak**.

- `CRecordset::none`Nie ustawiono opcji. Ta wartość parametru wzajemnie się wyklucza ze wszystkimi innymi wartościami. Domyślnie, plik recordset można zaktualizować za pomocą [funkcji Edytuj](#edit) lub [Usuń](#delete) i umożliwia dołączanie nowych rekordów do [AddNew](#addnew). Możliwość aktualizacji zależy od źródła danych, a także od określonej opcji *nOpenType.* Optymalizacja dla dodatków zbiorczych nie jest dostępna. Pobieranie wiersza zbiorczego nie zostanie zaimplementowane. Usunięte rekordy nie zostaną pominięte podczas nawigacji po nastawie rekordów. Zakładki nie są dostępne. Zaimplementowano automatyczne sprawdzanie brudnego pola.

- `CRecordset::appendOnly`Nie zezwalaj `Delete` ani nie ma `Edit` na nim pliku recordset. Zezwalaj `AddNew` tylko. Ta opcja wzajemnie `CRecordset::readOnly`się wyklucza z .

- `CRecordset::readOnly`Otwórz go jako tylko do odczytu. Ta opcja wzajemnie `CRecordset::appendOnly`się wyklucza z .

- `CRecordset::optimizeBulkAdd`Użyj przygotowanej instrukcji SQL, aby zoptymalizować dodawanie wielu rekordów jednocześnie. Ma zastosowanie tylko wtedy, gdy nie `SQLSetPos` używasz funkcji INTERFEJSU API ODBC do aktualizacji pliku recordset. Pierwsza aktualizacja określa, które pola są oznaczone jako zabrudzone. Ta opcja wzajemnie `CRecordset::useMultiRowFetch`się wyklucza z .

- `CRecordset::useMultiRowFetch`Zaimplementuj pobieranie wiersza zbiorczego, aby umożliwić pobieranie wielu wierszy w ramach jednej operacji pobierania. Jest to zaawansowana funkcja mająca na celu poprawę wydajności; Jednak zbiorcza wymiana pól rekordów nie jest obsługiwana przez ClassWizard. Ta opcja wzajemnie `CRecordset::optimizeBulkAdd`się wyklucza z . Należy zauważyć, `CRecordset::useMultiRowFetch`że jeśli `CRecordset::noDirtyFieldCheck` określisz , opcja zostanie włączona automatycznie (podwójne buforowanie nie będzie dostępne); w zestawach rekordów tylko `CRecordset::useExtendedFetch` do przodu opcja zostanie włączona automatycznie. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

- `CRecordset::skipDeletedRecords`Pomiń wszystkie usunięte rekordy podczas nawigowania po zajmijki po ziejącym rekordy. Spowoduje to spowolnienie wydajności w niektórych względnych pobiera. Ta opcja jest nieprawidłowa w przypadku zestawów rekordów tylko do przodu. Jeśli wywołasz [Move](#move) z *nRows* parametr ustawiony `CRecordset::skipDeletedRecords` na 0, a zestaw opcji, `Move` będzie potwierdzać. Należy `CRecordset::skipDeletedRecords` zauważyć, że jest podobny do *pakowania sterowników*, co oznacza, że usunięte wiersze są usuwane z zestawu rekordów. Jeśli jednak kierowca pakuje rekordy, pominie tylko te rekordy, które usuniesz; nie pominie rekordów usuniętych przez innych użytkowników, gdy jest otwarty. `CRecordset::skipDeletedRecords`pominie wiersze usunięte przez innych użytkowników.

- `CRecordset::useBookmarks`Może używać zakładek na gromadzie rekordów, jeśli jest obsługiwana. Zakładki spowalniają pobieranie danych, ale zwiększają wydajność nawigacji po danych. Nieprawidłowe w przypadku rekordów tylko do przodu. Aby uzyskać więcej informacji, zobacz artykuł [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

- `CRecordset::noDirtyFieldCheck`Wyłącz automatyczne sprawdzanie brudnego pola (podwójne buforowanie). Poprawi to wydajność; jednak należy ręcznie oznaczyć pola jako `SetFieldDirty` `SetFieldNull` zabrudzone, wywołując funkcje i element członkowski. Należy zauważyć, że `CRecordset` podwójne buforowanie w klasie `CDaoRecordset`jest podobne do podwójnego buforowania w klasie . Jednak w `CRecordset`programie nie można włączyć podwójnego buforowania w poszczególnych polach; można włączyć go dla wszystkich pól lub wyłączyć go dla wszystkich pól. Należy zauważyć, że `CRecordset::useMultiRowFetch`jeśli `CRecordset::noDirtyFieldCheck` określisz tę opcję, zostanie ona automatycznie włączona; jednak `SetFieldDirty` i `SetFieldNull` nie można używać w zestawy rekordów, które implementują pobieranie wiersza zbiorczego.

- `CRecordset::executeDirect`Nie należy używać przygotowanej instrukcji SQL. Aby zwiększyć wydajność, należy `Requery` określić tę opcję, jeśli funkcja elementu członkowskiego nigdy nie zostanie wywołana.

- `CRecordset::useExtendedFetch`Zaimplementuj `SQLExtendedFetch` `SQLFetch`zamiast . Jest to przeznaczone do implementowania pobierania wiersza zbiorczego na rekordach tylko do przodu. Jeśli określisz `CRecordset::useMultiRowFetch` opcję na liście rekordów `CRecordset::useExtendedFetch` tylko do przodu, zostanie ona włączona automatycznie.

- `CRecordset::userAllocMultiRowBuffers`Użytkownik przydzieli bufory magazynu dla danych. Użyj tej opcji `CRecordset::useMultiRowFetch` w połączeniu z, jeśli chcesz przydzielić własny magazyn; w przeciwnym razie struktura automatycznie przydzieli niezbędne przechowywanie. Aby uzyskać więcej informacji, zobacz artykuł [Recordset: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Należy zauważyć, `CRecordset::userAllocMultiRowBuffers` że `CRecordset::useMultiRowFetch` określenie bez określania spowoduje potwierdzenia nie powiodło się.

### <a name="return-value"></a>Wartość zwracana

Nonzero, `CRecordset` jeśli obiekt został pomyślnie otwarty; w przeciwnym razie 0, jeśli [CDatabase::Otwórz](../../mfc/reference/cdatabase-class.md#open) (jeśli jest wywoływana) zwraca 0.

### <a name="remarks"></a>Uwagi

Aby uruchomić kwerendę zdefiniowaną przez zapytanie rekordów, należy wywołać tę funkcję elementu członkowskiego. Przed `Open`wywołaniem należy skonstruować obiekt pliku recordset.

Połączenie tego zbioru rekordów ze źródłem danych zależy od `Open`sposobu konstruowania zbioru rekordów przed wywołaniem . Jeśli przekażesz [obiekt CDatabase](../../mfc/reference/cdatabase-class.md) do konstruktora zestawów rekordów, który nie został połączony ze źródłem danych, ta funkcja elementu członkowskiego używa [usługi GetDefaultConnect](#getdefaultconnect) do próby otwarcia obiektu bazy danych. Jeśli przekażesz NULL do konstruktora pliku `CDatabase` recordset, konstruktor konstruuje obiekt dla Ciebie i `Open` próbuje połączyć obiekt bazy danych. Aby uzyskać szczegółowe informacje na temat zamykania pliku recordset i połączenia w tych różnych okolicznościach, zobacz [Zamknij](#close).

> [!NOTE]
> Dostęp do źródła danych `CRecordset` za pośrednictwem obiektu jest zawsze współużytkowane. W `CDaoRecordset` przeciwieństwie do klasy `CRecordset` nie można użyć obiektu do otwarcia źródła danych z wyłącznym dostępem.

Podczas wywoływania `Open`kwerendy, zwykle instrukcji SQL **SELECT,** wybiera rekordy na podstawie kryteriów pokazanych w poniższej tabeli.

|Wartość parametru lpszSQL|Wybrane rekordy są określane przez|Przykład|
|------------------------------------|----------------------------------------|-------------|
|NULL|Ciąg zwrócony `GetDefaultSQL`przez .||
|Nazwa tabeli SQL|Wszystkie kolumny listy tabel w `DoFieldExchange` `DoBulkFieldExchange`pliku .|`"Customer"`|
|Nazwa wstępnie zdefiniowanej kwerendy (procedura składowana)|Kolumny, które kwerenda jest zdefiniowana do zwrócenia.|`"{call OverDueAccts}"`|
|**WYBIERZ** listę kolumn **FROM z** listy tabeli|Określone kolumny z określonych tabel.|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|

> [!CAUTION]
> Należy uważać, aby nie wstawiać dodatkowe odstępy w ciągu SQL. Na przykład jeśli wstawisz odstępy między nawiasem klamrowym i **call** słowa kluczowego, MFC błędnie zinterpretować ciąg SQL jako nazwę tabeli i włączyć go do **SELECT** instrukcji, co spowoduje wyjątek. Podobnie, jeśli wstępnie zdefiniowana kwerenda używa parametru wyjściowego, nie należy wstawiać odstępów między nawiasem klamrowym a symbolem ''. Na koniec nie należy wstawiać odstępów przed nawiasem klamrowym w instrukcji **CALL** lub przed **select** słowa kluczowego w **SELECT** instrukcji.

Zwykle procedura jest przekazać `Open`NULL do ; w takim `Open` przypadku wywołuje [GetDefaultSQL](#getdefaultsql). Jeśli używasz `CRecordset` klasy pochodnej, `GetDefaultSQL` podaje nazwy tabeli określone w ClassWizard. Zamiast tego można określić `lpszSQL` inne informacje w parametrze.

Niezależnie od `Open` przekazania, tworzy końcowy ciąg SQL dla kwerendy (ciąg może mieć klauzule `lpszSQL` SQL **WHERE** i ORDER **BY** dołączone do ciągu, który przeszedł), a następnie wykonuje kwerendę. Można sprawdzić skonstruowany ciąg, wywołując [GetSQL](#getsql) po wywołaniu `Open`. Aby uzyskać dodatkowe informacje na temat sposobu konstruowania instrukcji SQL i wybierania rekordów, zobacz artykuł [Zestawienie rekordów: Jak rekordy wybierz rekordy (ODBC).](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)

Elementy członkowskie danych pól klasy zestaw rekordów są powiązane z kolumnami wybranych danych. Jeśli wszystkie rekordy są zwracane, pierwszy rekord staje się bieżącym rekordem.

Jeśli chcesz ustawić opcje dla zestawu rekordów, takie jak filtr lub sortowanie, określ `Open`je po skonstruowaniu obiektu zestawu rekordów, ale przed wywołaniem . Jeśli chcesz odświeżyć rekordy w forcie rekordów po jego otwarciu, zadzwoń do [funkcji Requery](#requery).

Aby uzyskać więcej informacji, w tym dodatkowe przykłady, zobacz artykuły [Recordset (ODBC)](../../data/odbc/recordset-odbc.md), [Recordset: How Recordsets Select Records (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)i [Recordset: Creating and Closing Recordsets (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

### <a name="example"></a>Przykład

Poniższe przykłady kodu pokazują `Open` różne formy wywołania.

[!code-cpp[NVC_MFCDatabase#16](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]

## <a name="crecordsetrefreshrowset"></a><a name="refreshrowset"></a>Zestaw CRecordset::RefreshRowset

Aktualizuje dane i stan wiersza w bieżącym zestawie wierszy.

```
void RefreshRowset(
    WORD wRow,
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>Parametry

*wrow (wrow)*<br/>
Jednopozycjowe położenie wiersza w bieżącym zestawie wierszy. Ta wartość może wynosić od zera do rozmiaru zestawu wierszy.

*wLockType (Typ zamka)*<br/>
Wartość wskazująca sposób blokowania wiersza po odświeżeniu. Aby uzyskać szczegółowe informacje, zobacz Uwagi.

### <a name="remarks"></a>Uwagi

Jeśli przekażesz wartość zero dla *wRow,* każdy wiersz w zestawie wierszy zostanie odświeżony.

Aby `RefreshRowset`użyć programu , należy zaimplementować pobieranie `CRecordset::useMulitRowFetch` wiersza zbiorczego, określając opcję w funkcji [Otwórz](#open) element członkowski.

`RefreshRowset`wywołuje funkcję `SQLSetPos`API ODBC . Parametr *wLockType* określa stan blokady wiersza po `SQLSetPos` wykonaniu. W poniższej tabeli opisano możliwe wartości dla *wLockType*.

|wLockType (Typ zamka)|Opis|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE (wartość domyślna)|Sterownik lub źródło danych zapewnia, że wiersz jest w tym samym stanie `RefreshRowset` zablokowanym lub odblokowanym, jak przed wywołaniem.|
|SQL_LOCK_EXCLUSIVE|Sterownik lub źródło danych blokuje wiersz wyłącznie. Nie wszystkie źródła danych obsługują ten typ blokady.|
|SQL_LOCK_UNLOCK|Sterownik lub źródło danych odblokowuje wiersz. Nie wszystkie źródła danych obsługują ten typ blokady.|

Aby uzyskać `SQLSetPos`więcej informacji na temat programu , zobacz SDK systemu Windows. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetrequery"></a><a name="requery"></a>CRecordset::Kwerenda requery

Przebudowuje (odświeża) rekord.

```
virtual BOOL Requery();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli recordset został pomyślnie przebudowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli wszystkie rekordy są zwracane, pierwszy rekord staje się bieżącym rekordem.

Aby zestaw rekordów odzwierciedlał dodatki i usunięcia dokonane przez użytkownika lub innych użytkowników w źródle danych, `Requery`należy odbudować zestaw rekordów, wywołując program . Jeśli zestaw rekordów jest zestawem dynaset, automatycznie odzwierciedla aktualizacje, które użytkownik lub inni użytkownicy dokonują do istniejących rekordów (ale nie dodatków). Jeśli plik recordset jest migawką, należy wywołać, `Requery` aby odzwierciedlić zmiany wprowadzone przez innych użytkowników, a także uzupełnienia i usunięcia.

W przypadku zestawu dynamicznego lub migawki wywołaj w `Requery` dowolnym momencie, gdy chcesz odbudować zestaw rekordów przy użyciu nowego filtru lub sortowania lub nowych wartości parametrów. Ustaw nowy filtr lub sortuj właściwość, przypisując nowe wartości do `m_strFilter` i `m_strSort` przed wywołaniem `Requery`. Ustaw nowe parametry, przypisując nowe wartości `Requery`członkom danych parametrów przed wywołaniem . Jeśli ciągi filtru i sortowania pozostają niezmienione, można ponownie użyć kwerendy, co zwiększa wydajność.

Jeśli próba odbudowania pliku recordset zakończy się niepowodzeniem, jest on zamykany. Przed wywołaniem `Requery`można określić, czy rekord może zostać ponowniequerowany przez wywołanie `CanRestart` funkcji elementu członkowskiego. `CanRestart`nie gwarantuje, `Requery` że się uda.

> [!CAUTION]
> Zadzwoń `Requery` tylko po wywołaniu [Otwórz](#open).

### <a name="example"></a>Przykład

W tym przykładzie odbudowuje rekord, aby zastosować inną kolejność sortowania.

[!code-cpp[NVC_MFCDatabase#29](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]

## <a name="crecordsetsetabsoluteposition"></a><a name="setabsoluteposition"></a>CRecordset::SetAbsolutePosition

Umieszcza w rekordzie tablicę rekordów odpowiadającą określonej liczbie rekordów.

```
void SetAbsolutePosition(long nRows);
```

### <a name="parameters"></a>Parametry

*Nrows*<br/>
Jednonaszowa pozycja porządkowa dla bieżącego rekordu w zakułu rekordów.

### <a name="remarks"></a>Uwagi

`SetAbsolutePosition`przesuwa bieżący wskaźnik rekordu na podstawie tej pozycji porządkowej.

> [!NOTE]
> Ta funkcja elementu członkowskiego jest nieprawidłowa w przypadku rekordów tylko do przodu.

W przypadku rekordów ODBC bezwzględne ustawienie pozycji 1 odnosi się do pierwszego rekordu w rekordzie; ustawienie 0 odnosi się do pozycji początku pliku (BOF).

Można również przekazać wartości `SetAbsolutePosition`ujemne do . W tym przypadku pozycja pliku recordset jest obliczana od końca pliku recordset. Na przykład `SetAbsolutePosition( -1 )` przenosi bieżący wskaźnik rekordu do ostatniego rekordu w forsecie rekordów.

> [!NOTE]
> Pozycja bezwzględna nie jest przeznaczona do użycia jako liczba rekordów zastępczych. Zakładki są nadal zalecanym sposobem zachowania i powrotu do danej pozycji, ponieważ pozycja rekordu zmienia się po usunięciu poprzednich rekordów. Ponadto nie można mieć pewności, że dany rekord będzie miał taką samą pozycję bezwzględną, jeśli znak rekordów zostanie ponownie utworzony, ponieważ kolejność poszczególnych rekordów w zestawie rekordów nie jest gwarantowana, chyba że zostanie utworzona za pomocą instrukcji SQL przy użyciu klauzuli **ORDER BY.**

Aby uzyskać więcej informacji na temat nawigacji i zakładek na tabliczce rekordów, zobacz artykuły [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) i [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

## <a name="crecordsetsetbookmark"></a><a name="setbookmark"></a>CRecordset::SetBookmark

Umieszcza w rekordzie rekord zawierający określoną zakładkę.

```
void SetBookmark(const CDBVariant& varBookmark);
```

### <a name="parameters"></a>Parametry

*varBookmark (znak zdj.*<br/>
Odwołanie do [obiektu CDBVariant](../../mfc/reference/cdbvariant-class.md) zawierającego wartość zakładki dla określonego rekordu.

### <a name="remarks"></a>Uwagi

Aby ustalić, czy zakładki są obsługiwane w ach, zadzwoń do [canbookmark](#canbookmark). Aby udostępnić zakładki, jeśli są obsługiwane, `CRecordset::useBookmarks` należy ustawić opcję w parametrze *dwOptions* funkcji elementu członkowskiego [Otwórz.](#open)

> [!NOTE]
> Jeśli zakładki nie są obsługiwane lub niedostępne, wywołanie `SetBookmark` spowoduje wyjątek. Zakładki nie są obsługiwane w rekordach tylko do przodu.

Aby najpierw pobrać zakładkę dla bieżącego rekordu, zadzwoń do [GetBookmark](#getbookmark), `CDBVariant` który zapisuje wartość zakładki w obiekcie. Później można powrócić do tego `SetBookmark` rekordu, wywołując przy użyciu zapisanej wartości zakładki.

> [!NOTE]
> Po niektórych operacjach nastawy rekordów należy `SetBookmark`sprawdzić trwałość zakładki przed wywołaniem . Na przykład, jeśli pobierzesz `GetBookmark` zakładkę `Requery`z, a następnie wywołanie, zakładka może przestać być prawidłowa. Wywołanie [CDatabase::GetBookmarkPersistence,](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) aby sprawdzić, czy można bezpiecznie wywołać `SetBookmark`.

Aby uzyskać więcej informacji na temat zakładek i nawigacji na tabliczce rekordów, zobacz artykuły [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) oraz [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="crecordsetsetfielddirty"></a><a name="setfielddirty"></a>CRecordset::SetFieldDirty

Oznacza element członkowski danych pola w zbiorze rekordów jako zmieniony lub niezmieniony.

```
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
Zawiera adres elementu członkowskiego danych pola w liście rekordów lub wartości NULL. Jeśli null, wszystkie elementy członkowskie danych pola w liście rekordów są oflagowane. (C++ NULL nie jest taki sam jak Null w terminologii bazy danych, co oznacza "bez wartości.")

*bDirty*<br/>
PRAWDA, jeśli element członkowski danych pola ma być oznaczony jako "brudny" (zmieniony). W przeciwnym razie FALSE, jeśli element członkowski danych pola ma być oflagowany jako "czysty" (bez zmian).

### <a name="remarks"></a>Uwagi

Oznaczanie pól jako niezmienionych gwarantuje, że pole nie jest aktualizowane i powoduje mniejszy ruch SQL.

> [!NOTE]
> Ta funkcja elementu członkowskiego nie ma zastosowania w grupach rekordów, które używają zbiorczego pobierania wierszy. Jeśli zaimplementowano pobieranie wiersza zbiorczego, `SetFieldDirty` spowoduje to nie powiodło się twierdzenie. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Znaki ramowe zmieniły elementy członkowskie danych pól, aby upewnić się, że zostaną one zapisane w rekordzie w źródle danych przez mechanizm wymiany pól rekordów (RFX). Zmiana wartości pola zazwyczaj ustawia pole zabrudzone automatycznie, więc rzadko `SetFieldDirty` trzeba wywołać siebie, ale czasami warto upewnić się, że kolumny będą jawnie aktualizowane lub wstawiane niezależnie od wartości, która znajduje się w polu elementu członkowskiego danych.

> [!CAUTION]
> Wywołanie tej funkcji członkowskiej dopiero po [wywołaniu Edytuj](#edit) lub [DodajNew](#addnew).

Użycie wartości NULL dla pierwszego argumentu funkcji `outputColumn` spowoduje zastosowanie `param` funkcji tylko do pól, a nie pól. Na przykład wezwanie do

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

ustawi `outputColumn` tylko pola na NULL; `param` nie ulegnie to poprawie.

Aby pracować `param` nad polami, należy podać `param` rzeczywisty adres osoby, nad którą chcesz pracować, na przykład:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

Oznacza to, że `param` nie można ustawić wszystkich `outputColumn` pól na NULL, tak jak w polach.

## <a name="crecordsetsetfieldnull"></a><a name="setfieldnull"></a>CRecordset::SetFieldNull

Oznacza element członkowski danych pól w zbiorze rekordów jako null (w szczególności nie ma wartości) lub jako nie-Null.

```
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
Zawiera adres elementu członkowskiego danych pola w liście rekordów lub wartości NULL. Jeśli null, wszystkie elementy członkowskie danych pola w liście rekordów są oflagowane. (C++ NULL nie jest taki sam jak Null w terminologii bazy danych, co oznacza "bez wartości.")

*bBull (Angielski)*<br/>
Wartość niezerowa, jeśli element członkowski danych pola ma być oflagowany jako nie posiadający żadnej wartości (Null). W przeciwnym razie 0, jeśli element członkowski danych pola ma być oflagowany jako inny niż Null.

### <a name="remarks"></a>Uwagi

Po dodaniu nowego rekordu do zestawu rekordów wszystkie elementy członkowskie danych pola są początkowo ustawione na wartość Null i oznaczone jako "brudne" (zmienione). Podczas pobierania rekordu ze źródła danych jego kolumny mają już wartości lub są null.

> [!NOTE]
> Nie należy wywoływać tej funkcji elementu członkowskiego w zestawy rekordów, które są przy użyciu pobierania wiersza zbiorczego. Jeśli zaimplementowano pobieranie wiersza zbiorczego, wywołanie `SetFieldNull` powoduje niepowodzeniem potwierdzenia. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Jeśli w szczególności chcesz wyznaczyć pole bieżącego rekordu jako nieposięcie wartości, wywołanie `SetFieldNull` z *bNull* ustawioną na WARTOŚĆ TRUE oznaczanie jest null. Jeśli pole zostało wcześniej oznaczone jako Null i teraz chcesz nadać mu wartość, po prostu ustaw jego nową wartość. Nie trzeba usuwać flagi Null `SetFieldNull`za pomocą pliku . Aby ustalić, czy pole może być `IsFieldNullable`null, wywołać .

> [!CAUTION]
> Wywołanie tej funkcji członkowskiej dopiero po [wywołaniu Edytuj](#edit) lub [DodajNew](#addnew).

Użycie wartości NULL dla pierwszego argumentu funkcji `outputColumn` spowoduje zastosowanie `param` funkcji tylko do pól, a nie pól. Na przykład wezwanie do

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

ustawi `outputColumn` tylko pola na NULL; `param` nie ulegnie to poprawie.

Aby pracować `param` nad polami, należy podać `param` rzeczywisty adres osoby, nad którą chcesz pracować, na przykład:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

Oznacza to, że `param` nie można ustawić wszystkich `outputColumn` pól na NULL, tak jak w polach.

> [!NOTE]
> Podczas ustawiania parametrów null, wywołanie `SetFieldNull` przed otwarciem zestawu rekordów powoduje potwierdzenia. W takim przypadku zadzwoń [SetParamNull](#setparamnull).

`SetFieldNull`jest realizowany za pośrednictwem [DoFieldExchange](#dofieldexchange).

## <a name="crecordsetsetlockingmode"></a><a name="setlockingmode"></a>CRecordset::SetLockingMode

Ustawia tryb blokowania na "optymistyczne" blokowanie (domyślne) lub "pesymistyczne" blokowanie. Określa, jak rekordy są zablokowane dla aktualizacji.

```
void SetLockingMode(UINT nMode);
```

### <a name="parameters"></a>Parametry

*nMode*<br/>
Zawiera jedną z następujących `enum LockMode`wartości z :

- `optimistic`Optymistyczne blokowanie blokuje rekord aktualizowany tylko `Update`podczas wywołania do .

- `pessimistic`Pesymistyczne blokowanie blokuje rekord tak `Edit` szybko, jak jest wywoływana i utrzymuje go zablokowany, aż `Update` połączenie zostanie zakończone lub przenieść do nowego rekordu.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji elementu członkowskiego, jeśli trzeba określić, które z dwóch strategii blokowania rekordów jest używany do aktualizacji. Domyślnie tryb blokowania zestawu rekordów `optimistic`to . Można to zmienić na `pessimistic` bardziej ostrożną strategię blokowania. Wywołanie `SetLockingMode` po skonstruowaniu i otwarciu obiektu `Edit`pliku recordset, ale przed wywołaniem .

## <a name="crecordsetsetparamnull"></a><a name="setparamnull"></a>CRecordset::SetParamNull

Oznacza parametr jako Null (w szczególności nie ma wartości) lub jako nie-Null.

```
void SetParamNull(
    int nIndex,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks od zera parametru.

*bBull (Angielski)*<br/>
Jeśli wartość TRUE (wartość domyślna), parametr jest oflagowany jako Null. W przeciwnym razie parametr jest oflagowany jako inny niż Null.

### <a name="remarks"></a>Uwagi

W przeciwieństwie do [SetFieldNull](#setfieldnull)można wywołać przed `SetParamNull` otwarciem zestawu rekordów.

`SetParamNull`jest zwykle używany ze wstępnie zdefiniowanymi zapytaniami (procedurami przechowywanymi).

## <a name="crecordsetsetrowsetcursorposition"></a><a name="setrowsetcursorposition"></a>CRecordset::SetRowsetCursorPosition

Przenosi kursor do wiersza w bieżącym zestawie wierszy.

```
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>Parametry

*wrow (wrow)*<br/>
Jednopozycjowe położenie wiersza w bieżącym zestawie wierszy. Ta wartość może wynosić od 1 do rozmiaru zestawu wierszy.

*wLockType (Typ zamka)*<br/>
Wartość wskazująca sposób blokowania wiersza po odświeżeniu. Aby uzyskać szczegółowe informacje, zobacz Uwagi.

### <a name="remarks"></a>Uwagi

Podczas implementowania zbiorczego pobierania wierszy rekordy są pobierane przez zestawy wierszy, gdzie pierwszym rekordem w pobranym zestawie wierszy jest bieżący rekord. Aby nawiązać kolejny rekord w wierszu ustawiony `SetRowsetCursorPosition`bieżący rekord, zadzwoń do obiektu . Na przykład można `SetRowsetCursorPosition` połączyć z funkcją elementu członkowskiego [GetFieldValue](#getfieldvalue) dynamicznie pobierać dane z dowolnego rekordu zestawu rekordów.

Aby `SetRowsetCursorPosition`użyć programu , należy zaimplementować pobieranie `CRecordset::useMultiRowFetch` wiersza zbiorczego, określając opcję parametru *dwOptions* w funkcji [Otwórz](#open) element członkowski.

`SetRowsetCursorPosition`wywołuje funkcję `SQLSetPos`API ODBC . Parametr *wLockType* określa stan blokady wiersza po `SQLSetPos` wykonaniu. W poniższej tabeli opisano możliwe wartości dla *wLockType*.

|wLockType (Typ zamka)|Opis|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE (wartość domyślna)|Sterownik lub źródło danych zapewnia, że wiersz jest w tym samym stanie `SetRowsetCursorPosition` zablokowanym lub odblokowanym, jak przed wywołaniem.|
|SQL_LOCK_EXCLUSIVE|Sterownik lub źródło danych blokuje wiersz wyłącznie. Nie wszystkie źródła danych obsługują ten typ blokady.|
|SQL_LOCK_UNLOCK|Sterownik lub źródło danych odblokowuje wiersz. Nie wszystkie źródła danych obsługują ten typ blokady.|

Aby uzyskać `SQLSetPos`więcej informacji na temat programu , zobacz SDK systemu Windows. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetsetrowsetsize"></a><a name="setrowsetsize"></a>CRecordset::SetRowsetSize

Określa liczbę rekordów, które mają być pobierane podczas pobierania.

```
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```

### <a name="parameters"></a>Parametry

*dwNewRowsetSize*<br/>
Liczba wierszy do pobrania podczas danego pobierania.

### <a name="remarks"></a>Uwagi

Ta funkcja wirtualnego elementu członkowskiego określa, ile wierszy chcesz pobrać podczas pojedynczego pobierania podczas pobierania zbiorczego. Aby zaimplementować pobieranie wiersza `CRecordset::useMultiRowFetch` zbiorczego, należy ustawić opcję w parametrze *dwOptions* funkcji elementu członkowskiego [Otwórz.](#open)

> [!NOTE]
> Wywołanie `SetRowsetSize` bez implementowania pobierania wiersza zbiorczego spowoduje niepowodzenie potwierdzenia.

Wywołanie `SetRowsetSize` `Open` przed wywołaniem, aby początkowo ustawić rozmiar zestawu wierszy dla zestawu rekordów. Domyślny rozmiar zestawu wierszy podczas implementowania pobierania wiersza zbiorczego wynosi 25.

> [!NOTE]
> Należy zachować `SetRowsetSize`ostrożność podczas dzwonienia . W przypadku ręcznego przydzielania magazynu dla danych `CRecordset::userAllocMultiRowBuffers` (zgodnie z opcją parametru `Open`dwOptions w ), należy sprawdzić, czy po `SetRowsetSize`wywołaniu należy ponownie przydzielić te bufory magazynu, ale przed wykonaniem jakiejkolwiek operacji nawigacji kursora.

Aby uzyskać bieżące ustawienie rozmiaru zestawu wierszy, należy wywołać [getrowsetsize](#getrowsetsize).

Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetupdate"></a><a name="update"></a>CRecordset::Aktualizacja

Kończy `AddNew` operację, `Edit` zapisując nowe lub edytowane dane w źródle danych.

```
virtual BOOL Update();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli jeden rekord został pomyślnie zaktualizowany; w przeciwnym razie 0, jeśli żadne kolumny nie uległy zmianie. Jeśli żadne rekordy nie zostały zaktualizowane lub jeśli zaktualizowano więcej niż jeden rekord, zostanie zgłoszony wyjątek. Wyjątek jest również zgłaszany dla innych awarii w źródle danych.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji elementu członkowskiego po wywołaniu funkcji [AddNew](#addnew) lub [Edit](#edit) member. To wywołanie jest wymagane `AddNew` `Edit` do ukończenia operacji lub.

> [!NOTE]
> Jeśli zaimplementowano pobieranie wiersza `Update`zbiorczego, nie można wywołać . Spowoduje to nie powiodło się twierdzenie. Chociaż `CRecordset` klasa nie zapewnia mechanizmu aktualizowania zbiorczych wierszy danych, można napisać własne `SQLSetPos`funkcje przy użyciu funkcji INTERFEJSU API ODBC. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Zarówno `AddNew` `Edit` i przygotować bufor edycji, w którym dodane lub edytowane dane są umieszczane do zapisywania w źródle danych. `Update`zapisuje dane. Aktualizowane są tylko te pola oznaczone lub wykryte jako zmienione.

Jeśli źródło danych obsługuje transakcje, można `Update` nawiązać połączenie `AddNew` `Edit` (i jego odpowiednie lub wywołanie) część transakcji. Aby uzyskać więcej informacji o transakcjach, zobacz artykuł [Transakcja (ODBC)](../../data/odbc/transaction-odbc.md).

> [!CAUTION]
> Jeśli `Update` dzwonisz bez pierwszego `AddNew` `Edit`połączenia `Update` albo `CDBException`lub , rzuca . Jeśli `AddNew` dzwonisz `Edit`lub musisz `Update` zadzwonić `Move` przed wywołaniem operacji lub przed zamknięciem zestawu rekordów lub połączenia ze źródłem danych. W przeciwnym razie zmiany zostaną utracone bez powiadomienia.

Aby uzyskać `Update` szczegółowe informacje na temat obsługi błędów, zobacz artykuł [Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

### <a name="example"></a>Przykład

Zobacz artykuł [Transakcja: Wykonywanie transakcji w zajrzy (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDatabase](../../mfc/reference/cdatabase-class.md)<br/>
[Klasa CRecordView](../../mfc/reference/crecordview-class.md)
