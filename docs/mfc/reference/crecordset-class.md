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
ms.openlocfilehash: d00764205b3b81e9f01dbe53d0c67372ebb2532e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219628"
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
|[CRecordset::CRecordset](#crecordset)|Konstruuje `CRecordset` obiekt. Klasa pochodna musi udostępniać Konstruktor, który wywołuje ten obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRecordset:: AddNew](#addnew)|Przygotowuje się do dodania nowego rekordu. Wywołaj `Update` , aby ukończyć Dodawanie.|
|[CRecordset:: dołączanie](#canappend)|Zwraca wartość różną od zera, jeśli nowe rekordy można dodać do zestawu rekordów za pośrednictwem `AddNew` funkcji składowej.|
|[CRecordset:: wypisano](#canbookmark)|Zwraca wartość różną od zera, jeśli zestaw rekordów obsługuje zakładki.|
|[CRecordset:: Cancel](#cancel)|Anuluje operację asynchroniczną lub proces z drugiego wątku.|
|[CRecordset::CancelUpdate](#cancelupdate)|Anuluje wszystkie oczekujące aktualizacje spowodowane `AddNew` `Edit` operacją lub.|
|[CRecordset:: restart](#canrestart)|Zwraca wartość różną od zera `Requery` , jeśli można ją wywołać, aby ponownie uruchomić zapytanie zestawu rekordów.|
|[CRecordset:: Scroll](#canscroll)|Zwraca wartość różną od zera, jeśli można przewijać rekordy.|
|[CRecordset:: gettransact](#cantransact)|Zwraca wartość różną od zera, jeśli źródło danych obsługuje transakcje.|
|[CRecordset:: Update](#canupdate)|Zwraca wartość różną od zera, jeśli zestaw rekordów można zaktualizować (można dodawać, aktualizować lub usuwać rekordy).|
|[CRecordset::CheckRowsetError](#checkrowseterror)|Wywołuje się, by obsługiwać błędy generowane podczas pobierania rekordów.|
|[CRecordset:: Close](#close)|Zamyka zestaw rekordów i skojarzone z nim ODBC HSTMT.|
|[CRecordset::D Usuń](#delete)|Usuwa bieżący rekord z zestawu rekordów. Po usunięciu należy jawnie przewinąć do innego rekordu.|
|[CRecordset::D oBulkFieldExchange](#dobulkfieldexchange)|Wywołuje się, by przeprowadzić wymianę zbiorczych wierszy danych ze źródła danych do zestawu rekordów. Implementuje wymianę zbiorczą pól rekordów (bulk RFX).|
|[CRecordset::D oFieldExchange](#dofieldexchange)|Wywołuje się, by wymienić dane (w obu kierunkach) między elementami członkowskimi danych pola zestawu rekordów i odpowiednim rekordem w źródle danych. Implementuje wymianę pól rekordów (RFX).|
|[CRecordset:: Edit](#edit)|Przygotowuje się do zmian w bieżącym rekordzie. Wywołaj `Update` , aby ukończyć edycję.|
|[CRecordset::FlushResultSet](#flushresultset)|Zwraca wartość różną od zera, jeśli istnieje inny zestaw wyników do pobrania przy użyciu wstępnie zdefiniowanego zapytania.|
|[CRecordset:: GetBookmark](#getbookmark)|Przypisuje wartość zakładki rekordu do obiektu Parameter.|
|[CRecordset::GetDefaultConnect](#getdefaultconnect)|Wywołuje się, by uzyskać domyślne parametry połączenia.|
|[CRecordset::GetDefaultSQL](#getdefaultsql)|Wywołuje się, by uzyskać domyślny ciąg SQL do wykonania.|
|[CRecordset:: GetFieldValue —](#getfieldvalue)|Zwraca wartość pola w zestawie rekordów.|
|[CRecordset::GetODBCFieldCount](#getodbcfieldcount)|Zwraca liczbę pól w zestawie rekordów.|
|[CRecordset::GetODBCFieldInfo](#getodbcfieldinfo)|Zwraca określone rodzaje informacji o polach w zestawie rekordów.|
|[CRecordset::GetRecordCount](#getrecordcount)|Zwraca liczbę rekordów w zestawie rekordów.|
|[CRecordset::GetRowsetSize](#getrowsetsize)|Zwraca liczbę rekordów, które mają zostać pobrane podczas pojedynczego pobierania.|
|[CRecordset::GetRowsFetched](#getrowsfetched)|Zwraca rzeczywistą liczbę wierszy pobranych podczas pobierania.|
|[CRecordset:: GetRowStatus](#getrowstatus)|Zwraca stan wiersza po pobraniu.|
|[CRecordset::GetSQL](#getsql)|Pobiera ciąg SQL używany do wybierania rekordów dla zestawu rekordów.|
|[CRecordset:: GetStatus](#getstatus)|Pobiera stan zestawu rekordów: indeks bieżącego rekordu oraz czy uzyskano ostateczną liczbę rekordów.|
|[CRecordset:: gettablename](#gettablename)|Pobiera nazwę tabeli, na której bazuje zestaw rekordów.|
|[CRecordset::IsBOF](#isbof)|Zwraca wartość różną od zera, jeśli zestaw rekordów został umieszczony przed pierwszym rekordem. Brak bieżącego rekordu.|
|[CRecordset:: IsDeleted](#isdeleted)|Zwraca wartość różną od zera, jeśli zestaw rekordów został umieszczony w usuniętym rekordzie.|
|[CRecordset::IsEOF](#iseof)|Zwraca wartość różną od zera, jeśli zestaw rekordów został umieszczony po ostatnim rekordzie. Brak bieżącego rekordu.|
|[CRecordset::IsFieldDirty](#isfielddirty)|Zwraca wartość różną od zera, jeśli określone pole w bieżącym rekordzie zostało zmienione.|
|[CRecordset::IsFieldNull](#isfieldnull)|Zwraca wartość różną od zera, jeśli określone pole w bieżącym rekordzie ma wartość null (nie ma wartości).|
|[CRecordset::IsFieldNullable](#isfieldnullable)|Zwraca wartość różną od zera, jeśli określone pole w bieżącym rekordzie można ustawić na wartość null (bez wartości).|
|[CRecordset:: IsOpen](#isopen)|Zwraca wartość różną od zera, jeśli `Open` została wcześniej wywołana.|
|[CRecordset:: Move](#move)|Ustawia zestaw rekordów na określoną liczbę rekordów z bieżącego rekordu w dowolnym kierunku.|
|[CRecordset:: MoveFirst](#movefirst)|Ustawia bieżący rekord pierwszego rekordu w zestawie rekordów. Najpierw Przetestuj test `IsBOF` .|
|[CRecordset:: MoveLast](#movelast)|Określa położenie bieżącego rekordu w ostatnim rekordzie lub w ostatnim zestawie wierszy. Najpierw Przetestuj test `IsEOF` .|
|[CRecordset:: MoveNext](#movenext)|Określa położenie bieżącego rekordu w następnym rekordzie lub w następnym zestawie wierszy. Najpierw Przetestuj test `IsEOF` .|
|[CRecordset:: MovePrev](#moveprev)|Określa położenie bieżącego rekordu w poprzednim rekordzie lub w poprzednim zestawie wierszy. Najpierw Przetestuj test `IsBOF` .|
|[CRecordset:: onoptions](#onsetoptions)|Wywołuje się, by ustawić opcje (używane przy wyborze) dla określonej instrukcji ODBC.|
|[CRecordset::OnSetUpdateOptions](#onsetupdateoptions)|Wywołuje się, by ustawić opcje (używane podczas aktualizacji) dla określonej instrukcji ODBC.|
|[CRecordset:: Open](#open)|Otwiera zestaw rekordów przez pobranie tabeli lub wykonanie zapytania, które reprezentuje zestaw rekordów.|
|[CRecordset::RefreshRowset](#refreshrowset)|Odświeża dane i stan wskazanych wierszy.|
|[CRecordset:: Requery](#requery)|Uruchamia ponownie zapytanie zestawu rekordów w celu odświeżenia wybranych rekordów.|
|[CRecordset::SetAbsolutePosition](#setabsoluteposition)|Ustawia zestaw rekordów dla rekordu odpowiadającego określonemu numerowi rekordu.|
|[CRecordset:: SetBookmark](#setbookmark)|Ustawia zestaw rekordów dla rekordu określonego przez zakładkę.|
|[CRecordset::SetFieldDirty](#setfielddirty)|Oznacza określone pole w bieżącym rekordzie jako zmienione.|
|[CRecordset::SetFieldNull](#setfieldnull)|Ustawia wartość określonego pola w bieżącym rekordzie na null (bez wartości).|
|[CRecordset:: setlockmode](#setlockingmode)|Ustawia tryb blokowania na "optymistyczne" blokowania (ustawienie domyślne) lub "pesymistyczne". Określa sposób blokowania rekordów na potrzeby aktualizacji.|
|[CRecordset::SetParamNull](#setparamnull)|Ustawia określony parametr na wartość null (bez wartości).|
|[CRecordset::SetRowsetCursorPosition](#setrowsetcursorposition)|Umieszcza kursor w określonym wierszu w zestawie wierszy.|
|[CRecordset::SetRowsetSize](#setrowsetsize)|Określa liczbę rekordów, które mają zostać pobrane podczas pobierania.|
|[CRecordset:: Update](#update)|Wykonuje `AddNew` operację lub `Edit` , zapisując nowe lub edytowane dane w źródle danych.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CRecordset:: m_hstmt](#m_hstmt)|Zawiera dojście instrukcji ODBC dla zestawu rekordów. Wpisz `HSTMT`.|
|[CRecordset:: m_nFields](#m_nfields)|Zawiera liczbę elementów członkowskich danych pola w zestawie rekordów. Wpisz `UINT`.|
|[CRecordset:: m_nParams](#m_nparams)|Zawiera liczbę elementów członkowskich danych parametrów w zestawie rekordów. Wpisz `UINT`.|
|[CRecordset:: m_pDatabase](#m_pdatabase)|Zawiera wskaźnik do obiektu, `CDatabase` za pomocą którego zestaw rekordów jest połączony ze źródłem danych.|
|[CRecordset:: m_strFilter](#m_strfilter)|Zawiera element `CString` określający klauzulę Structured Query Language (SQL) `WHERE` . Służy jako filtr do wybierania tylko tych rekordów, które spełniają określone kryteria.|
|[CRecordset:: m_strSort](#m_strsort)|Zawiera element `CString` określający `ORDER BY` klauzulę SQL. Służy do kontrolowania sposobu sortowania rekordów.|

## <a name="remarks"></a><a name="remarks"></a>Uwagi

Obiekty "zestawy rekordów" `CRecordset` są zwykle używane w dwóch formach: dynamicznych i migawek. Zestaw dynamiczny pozostaje zsynchronizowany z aktualizacjami danych wykonywanymi przez innych użytkowników. Migawka jest statycznym widokiem danych. Każdy formularz reprezentuje zestaw rekordów naprawionych w momencie otwarcia zestawu rekordów, ale podczas przewijania do rekordu w zestawie dynamicznym odzwierciedla zmiany wprowadzone w tym rekordzie przez innych użytkowników lub inne zestawy rekordów w aplikacji.

> [!NOTE]
> Jeśli pracujesz z klasami obiektów dostępu do danych (DAO), a nie klasami Open Database Connectivity (ODBC), zamiast tego użyj klasy [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) . Aby uzyskać więcej informacji, zobacz [Omówienie artykułu: Programowanie baz danych](../../data/data-access-programming-mfc-atl.md).

Aby można było korzystać z dowolnego rodzaju zestawu rekordów, zazwyczaj uzyskuje się klasy zestawu rekordów specyficzne dla aplikacji z `CRecordset` . Zestawy rekordów wybierają rekordy ze źródła danych, a następnie można:

- Przewijaj rekordy.

- Aktualizowanie rekordów i Określanie trybu blokowania.

- Filtruj zestaw rekordów, aby ograniczyć, które rekordy wybierają z tych, które są dostępne w źródle danych.

- Posortuj zestaw rekordów.

- Sparametryzuj zestaw rekordów, aby dostosować jego wybór o informacje nieznane do czasu wykonywania.

Aby użyć klasy, Otwórz bazę danych i Skonstruuj obiekt zestawu rekordów, przekazując konstruktora wskaźnik do `CDatabase` obiektu. Następnie Wywołaj `Open` funkcję członkowską zestawu rekordów, w której można określić, czy obiekt jest zestawem dynamicznym, czy migawką. Wywołanie `Open` wybiera dane ze źródła danych. Po otwarciu obiektu zestawu rekordów Użyj jego funkcji składowych i składowych danych, aby przewijać rekordy i korzystać z nich. Dostępne operacje zależą od tego, czy obiekt jest zestawem dynamicznym, czy migawką, czy jest on aktualizowalny, czy tylko do odczytu (jest to zależne od możliwości źródła danych Open Database Connectivity (ODBC), a także od tego, czy wdrożono pobieranie wierszy zbiorczych. Aby odświeżyć rekordy, które mogły zostać zmienione lub dodane od czasu `Open` wywołania, wywołaj `Requery` funkcję członkowską obiektu. Wywołaj `Close` funkcję członkowską obiektu i zniszcz obiekt po zakończeniu pracy z nim.

W klasie pochodnej `CRecordset` do obsługi odczytywania i aktualizowania pól rekordów jest używana wymiana pól rekordów (RFX) lub wymiana pól rekordów zbiorczych (bulk RFX).

Aby uzyskać więcej informacji na temat zestawów rekordów i wymiany pól rekordów, zobacz artykuł [Omówienie: Programowanie baz danych](../../data/data-access-programming-mfc-atl.md), [zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md), [zestaw rekordów: pobieranie rekordów w zbiorczej (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)i [wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md). Aby skoncentrować się na zestawach dynamicznych i migawek, zobacz artykuły [zestaw dynamiczny](../../data/odbc/dynaset.md) i [migawkę](../../data/odbc/snapshot.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CRecordset`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDB. h

## <a name="crecordsetaddnew"></a><a name="addnew"></a>CRecordset:: AddNew

Przygotowuje się do dodania nowego rekordu do tabeli.

```
virtual void AddNew();
```

### <a name="remarks"></a>Uwagi

Aby zobaczyć nowo dodany rekord, należy wywołać funkcję elementu członkowskiego [PonówKwerendę](#requery) . Pola rekordu są początkowo puste. (W terminologii bazy danych wartość null oznacza brak wartości i nie jest taka sama jak wartość NULL w języku C++). Aby ukończyć operację, należy wywołać funkcję elementu członkowskiego [aktualizacji](#update) . `Update`zapisuje zmiany w źródle danych.

> [!NOTE]
> Jeśli zaimplementowano pobieranie wierszy zbiorczych, nie można wywołać `AddNew` . Spowoduje to nieudane potwierdzenie. Chociaż Klasa nie `CRecordset` udostępnia mechanizmu do aktualizowania wierszy danych zbiorczych, można napisać własne funkcje przy użyciu funkcji ODBC API `SQLSetPos` . Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`AddNew`przygotowuje nowy, pusty rekord za pomocą elementów członkowskich danych pola zestawu rekordów. Po wywołaniu `AddNew` Ustaw odpowiednie wartości w elementach członkowskich danych pola zestawu rekordów. (W tym celu nie ma potrzeby wywoływania funkcji [Edytuj](#edit) element członkowski; Użyj `Edit` tylko dla istniejących rekordów). Po późniejszej wywołaniu `Update` wartości zmieniony w elementach członkowskich danych pola są zapisywane w źródle danych.

> [!CAUTION]
> Jeśli przewiniesz do nowego rekordu przed wywołaniem `Update` , nowy rekord zostanie utracony i nie zostanie określone żadne ostrzeżenie.

Jeśli źródło danych obsługuje transakcje, możesz `AddNew` wywołać część transakcji. Aby uzyskać więcej informacji na temat transakcji, zobacz Klasa [CDatabase](../../mfc/reference/cdatabase-class.md). Należy pamiętać, że należy wywołać [CDatabase:: BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) przed wywołaniem metody `AddNew` .

> [!NOTE]
> W przypadku zestawów dynamicznych nowe rekordy są dodawane do zestawu rekordów jako ostatni rekord. Dodane rekordy nie są dodawane do migawek; musisz wywołać `Requery` , aby odświeżyć zestaw rekordów.

Wywołanie `AddNew` zestawu rekordów, którego `Open` funkcja członkowska nie została wywołana, jest niedozwolone. `CDBException`Jest zgłaszany w przypadku wywołania `AddNew` zestawu rekordów, którego nie można dołączyć do. Można określić, czy zestaw rekordów jest aktualizowalny przez wywołanie funkcji [dołączania](#canappend).

Aby uzyskać więcej informacji, zobacz następujące artykuły: [zestaw rekordów: jak zestawy rekordów aktualizują rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md), [zestaw rekordów: Dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)i [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Przykład

Zobacz artykuł [transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="crecordsetcanappend"></a><a name="canappend"></a>CRecordset:: dołączanie

Określa, czy poprzednio otwarty zestaw rekordów pozwala dodawać nowe rekordy.

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli zestaw rekordów zezwala na dodawanie nowych rekordów; w przeciwnym razie 0. `CanAppend`Program zwróci wartość 0, jeśli zestaw rekordów został otwarty jako tylko do odczytu.

## <a name="crecordsetcanbookmark"></a><a name="canbookmark"></a>CRecordset:: wypisano

Określa, czy zestaw rekordów umożliwia oznaczanie rekordów przy użyciu zakładek.

```
BOOL CanBookmark() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli zestaw rekordów obsługuje zakładki; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest niezależna od `CRecordset::useBookmarks` opcji w parametrze *DwOptions* funkcji [Open](#open) member. `CanBookmark`wskazuje, czy dany sterownik ODBC i typ kursora obsługują zakładki. `CRecordset::useBookmarks`wskazuje, czy zakładki będą dostępne, pod warunkiem, że są one obsługiwane.

> [!NOTE]
> Zakładki nie są obsługiwane w zestawach rekordów tylko do przodu.

Aby uzyskać więcej informacji o zakładkach i nawigowaniu po zestawach rekordów, zobacz [zestawy rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) i [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="crecordsetcancel"></a><a name="cancel"></a>CRecordset:: Cancel

Żąda, aby źródło danych anulował operację asynchroniczną w toku lub proces z drugiego wątku.

```cpp
void Cancel();
```

### <a name="remarks"></a>Uwagi

Należy pamiętać, że klasy MFC ODBC nie są już używane do przetwarzania asynchronicznego; Aby wykonać operację asychronous, należy bezpośrednio wywołać funkcję interfejsu API ODBC `SQLSetConnectOption` . Aby uzyskać więcej informacji, zobacz temat "wykonywanie funkcji asynchronicznie" w *przewodniku programisty zestawu ODBC SDK*.

## <a name="crecordsetcancelupdate"></a><a name="cancelupdate"></a>CRecordset::CancelUpdate

Anuluje oczekujące aktualizacje, spowodowane przez operację [edycji](#edit) lub [AddNew](#addnew) przed wywołaniem [aktualizacji](#update) .

```cpp
void CancelUpdate();
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Ta funkcja członkowska nie ma zastosowania w zestawach rekordów używających pobierania wierszy zbiorczych, ponieważ takie zestawy rekordów nie mogą wywoływać `Edit` , `AddNew` , ani `Update` . Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Jeśli włączono automatyczne sprawdzanie pola, `CancelUpdate` program przywróci Zmienne Członkowskie do wartości, które wcześniej znajdowały się `Edit` lub `AddNew` zostały wywołane. w przeciwnym razie wszelkie zmiany wartości pozostaną. Domyślnie Automatyczne sprawdzanie pól jest włączane podczas otwierania zestawu rekordów. Aby go wyłączyć, należy określić wartość `CRecordset::noDirtyFieldCheck` w parametrze *DwOptions* funkcji [Open](#open) member.

Aby uzyskać więcej informacji na temat aktualizowania danych, zobacz [zestaw rekordów artykułów: Dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md).

## <a name="crecordsetcanrestart"></a><a name="canrestart"></a>CRecordset:: restart

Określa, czy zestaw rekordów umożliwia ponowne uruchomienie zapytania (w celu odświeżenia jego rekordów) przez wywołanie `Requery` funkcji elementu członkowskiego.

```
BOOL CanRestart() const;
```

### <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli jest dozwolona ponowna kwerenda; w przeciwnym razie 0.

## <a name="crecordsetcanscroll"></a><a name="canscroll"></a>CRecordset:: Scroll

Określa, czy zestaw rekordów umożliwia przewijanie.

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli zestaw rekordów umożliwia przewijanie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat przewijania, zobacz [zestaw rekordów artykułów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="crecordsetcantransact"></a><a name="cantransact"></a>CRecordset:: gettransact

Określa, czy zestaw rekordów zezwala na transakcje.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli zestaw rekordów zezwala na transakcje; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz artykuł [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="crecordsetcanupdate"></a><a name="canupdate"></a>CRecordset:: Update

Określa, czy można aktualizować zestaw rekordów.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli zestaw rekordów można zaktualizować; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zestaw rekordów może być tylko do odczytu, jeśli bazowe źródło danych jest tylko do odczytu lub jeśli określono `CRecordset::readOnly` w parametrze *dwOptions* podczas otwierania zestawu rekordów.

## <a name="crecordsetcheckrowseterror"></a><a name="checkrowseterror"></a>CRecordset::CheckRowsetError

Wywołuje się, by obsługiwać błędy generowane podczas pobierania rekordów.

```
virtual void CheckRowsetError(RETCODE nRetCode);
```

### <a name="parameters"></a>Parametry

*nRetCode*<br/>
Kod zwracany przez funkcję interfejsu API ODBC. Aby uzyskać szczegółowe informacje, zobacz uwagi.

### <a name="remarks"></a>Uwagi

Ta wirtualna funkcja członkowska obsługuje błędy występujące podczas pobierania rekordów i jest przydatna podczas pobierania wierszy zbiorczych. Warto rozważyć zastępowanie, `CheckRowsetError` Aby zaimplementować swoją własną obsługę błędów.

`CheckRowsetError`jest wywoływana automatycznie w operacji nawigacji kursora, takiej jak `Open` , `Requery` lub dowolnej `Move` operacji. Przeszedł wartość zwracaną przez funkcję interfejsu API ODBC `SQLExtendedFetch` . Poniższa tabela zawiera listę możliwych wartości parametru *nRetCode* .

|nRetCode|Opis|
|--------------|-----------------|
|SQL_SUCCESS|Funkcja została ukończona pomyślnie; Brak dostępnych dodatkowych informacji.|
|SQL_SUCCESS_WITH_INFO|Funkcja została zakończona pomyślnie, prawdopodobnie z błędem niekrytycznym. Dodatkowe informacje można uzyskać, wywołując metodę `SQLError` .|
|SQL_NO_DATA_FOUND|Wszystkie wiersze z zestawu wyników zostały pobrane.|
|SQL_ERROR|Nie można wykonać funkcji. Dodatkowe informacje można uzyskać, wywołując metodę `SQLError` .|
|SQL_INVALID_HANDLE|Działanie nie powiodło się z powodu nieprawidłowego dojścia do środowiska, dojścia do połączenia lub dojście do instrukcji. Wskazuje to na błąd programowania. Żadne dodatkowe informacje nie są dostępne w programie `SQLError` .|
|SQL_STILL_EXECUTING|Funkcja, która została uruchomiona asynchronicznie, nadal jest wykonywana. Należy pamiętać, że domyślnie MFC nigdy nie przekaże tej wartości do `CheckRowsetError` ; MFC będzie kontynuować wywoływanie `SQLExtendedFetch` , dopóki nie zwróci już SQL_STILL_EXECUTING.|

Aby uzyskać więcej informacji na temat `SQLError` , zobacz Windows SDK. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetclose"></a><a name="close"></a>CRecordset:: Close

Zamyka zestaw rekordów.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

HSTMT ODBC i wszystkie pamięci dla struktury przydzieloną dla zestawu rekordów są cofane. Zwykle po wywołaniu `Close` należy usunąć obiekt zestawu rekordów języka C++, jeśli został on przydzielony przy użyciu **`new`** .

Możesz wywołać `Open` ponownie po wywołaniu `Close` . Pozwala to ponownie wykorzystać obiekt zestawu rekordów. Alternatywą jest wywołanie metody `Requery` .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#17](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]

## <a name="crecordsetcrecordset"></a><a name="crecordset"></a>CRecordset::CRecordset

Konstruuje `CRecordset` obiekt.

```
CRecordset(CDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>Parametry

*pDatabase*<br/>
Zawiera wskaźnik do `CDatabase` obiektu lub wartość null. Jeśli wartość nie jest równa NULL, a `CDatabase` `Open` funkcja członkowska obiektu nie została wywołana, aby połączyć ją ze źródłem danych, zestaw rekordów próbuje otworzyć go dla Ciebie podczas jego `Open` wywołania. W przypadku przekazania wartości NULL `CDatabase` obiekt jest konstruowany i połączony z użyciem informacji o źródle danych, które zostały określone podczas wyprowadzania klasy zestawu rekordów przy użyciu ClassWizard.

### <a name="remarks"></a>Uwagi

Można użyć `CRecordset` bezpośrednio lub utworzyć klasę specyficzną dla aplikacji z `CRecordset` . Możesz użyć ClassWizard, aby utworzyć klasy zestawu rekordów.

> [!NOTE]
> Klasa pochodna *musi* dostarczyć własnego konstruktora. W konstruktorze klasy pochodnej Wywołaj konstruktora `CRecordset::CRecordset` , przekazując odpowiednie parametry do niego.

Przekaż wartość NULL do konstruktora zestawu rekordów, aby `CDatabase` obiekt został skonstruowany i połączony automatycznie. Jest to przydatne skróty, które nie wymagają tworzenia i łączenia `CDatabase` obiektu przed konstruowaniem zestawu rekordów.

### <a name="example"></a>Przykład

Aby uzyskać więcej informacji, zobacz [zestaw rekordów artykułów: deklarowanie klasy dla tabeli (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).

## <a name="crecordsetdelete"></a><a name="delete"></a>CRecordset::D Usuń

Usuwa bieżący rekord.

```
virtual void Delete();
```

### <a name="remarks"></a>Uwagi

Po pomyślnym usunięciu elementy członkowskie danych pola zestawu rekordów są ustawiane na wartość null i należy jawnie wywołać jedną z `Move` funkcji w celu przeniesienia usuniętego rekordu. Po przejściu z usuniętego rekordu nie można do niego powrócić. Jeśli źródło danych obsługuje transakcje, można utworzyć `Delete` część wywołania transakcji. Aby uzyskać więcej informacji, zobacz artykuł [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

> [!NOTE]
> Jeśli zaimplementowano pobieranie wierszy zbiorczych, nie można wywołać `Delete` . Spowoduje to nieudane potwierdzenie. Chociaż Klasa nie `CRecordset` udostępnia mechanizmu do aktualizowania wierszy danych zbiorczych, można napisać własne funkcje przy użyciu funkcji ODBC API `SQLSetPos` . Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!CAUTION]
> Zestaw rekordów musi być aktualizowalny, a w zestawie rekordów musi istnieć prawidłowy rekord `Delete` . w przeciwnym razie wystąpi błąd. Na przykład, jeśli usuniesz rekord, ale nie przewiniesz do nowego rekordu przed ponownym wywołaniem `Delete` , `Delete` zgłosi [CDBException](../../mfc/reference/cdbexception-class.md).

W przeciwieństwie do [parametru AddNew](#addnew) i [Edit](#edit), wywołanie `Delete` nie następuje po wywołaniu metody [Update](#update). Jeśli `Delete` wywołanie zakończy się niepowodzeniem, elementy członkowskie danych pola są pozostawione bez zmian.

### <a name="example"></a>Przykład

Ten przykład pokazuje zestaw rekordów utworzony w ramce funkcji. W przykładzie przyjęto, że `m_dbCust` zmienna członkowska typu jest `CDatabase` już połączona ze źródłem danych.

[!code-cpp[NVC_MFCDatabase#18](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]

## <a name="crecordsetdobulkfieldexchange"></a><a name="dobulkfieldexchange"></a>CRecordset::D oBulkFieldExchange

Wywołuje się, by przeprowadzić wymianę zbiorczych wierszy danych ze źródła danych do zestawu rekordów. Implementuje wymianę zbiorczą pól rekordów (bulk RFX).

```
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) . Platforma ma już skonfigurowany ten obiekt, aby określić kontekst dla operacji wymiany pól.

### <a name="remarks"></a>Uwagi

Po zaimplementowaniu pobierania wierszy zbiorczych, struktura wywołuje tę funkcję elementu członkowskiego, aby automatycznie przesyłać dane ze źródła danych do obiektu zestawu rekordów. `DoBulkFieldExchange`wiąże także elementy członkowskie danych parametrów, jeśli istnieją, do zastępczych parametrów w ciągu instrukcji SQL dla wyboru zestawu rekordów.

Jeśli pobieranie wierszy zbiorczych nie jest zaimplementowane, struktura wywołuje [DoFieldExchange](#dofieldexchange). Aby zaimplementować pobieranie wierszy zbiorczych, należy określić `CRecordset::useMultiRowFetch` opcję parametru *dwOptions* w funkcji [Open](#open) member.

> [!NOTE]
> `DoBulkFieldExchange`jest dostępny tylko wtedy, gdy używana jest Klasa pochodna z `CRecordset` . Jeśli obiekt zestawu rekordów został utworzony bezpośrednio z `CRecordset` , należy wywołać funkcję elementu członkowskiego [GetFieldValue —](#getfieldvalue) , aby pobrać dane.

Wymiana pól rekordów zbiorczych (bulk RFX) jest podobna do wymiany pól rekordów (RFX). Dane są automatycznie przenoszone ze źródła danych do obiektu zestawu rekordów. Nie można jednak wywołać `AddNew` , `Edit` , `Delete` , ani `Update` przesłać zmian z powrotem do źródła danych. Klasa `CRecordset` obecnie nie udostępnia mechanizmu do aktualizowania wierszy danych zbiorczych. można jednak napisać własne funkcje przy użyciu funkcji ODBC API `SQLSetPos` .

Należy pamiętać, że ClassWizard nie obsługuje wymiany pól rekordów zbiorczych; w związku z tym należy przesłonić `DoBulkFieldExchange` ręcznie, pisząc wywołania funkcji RFX zbiorczych. Aby uzyskać więcej informacji o tych funkcjach, zobacz temat [Funkcje wymiany pola rekordu](../../mfc/reference/record-field-exchange-functions.md)tematu.

Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Aby uzyskać powiązane informacje, zobacz artykuł [rekord pola rekordu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

## <a name="crecordsetdofieldexchange"></a><a name="dofieldexchange"></a>CRecordset::D oFieldExchange

Wywołuje się, by wymienić dane (w obu kierunkach) między elementami członkowskimi danych pola zestawu rekordów i odpowiednim rekordem w źródle danych. Implementuje wymianę pól rekordów (RFX).

```
virtual void DoFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Wskaźnik do obiektu [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) . Platforma ma już skonfigurowany ten obiekt, aby określić kontekst dla operacji wymiany pól.

### <a name="remarks"></a>Uwagi

Gdy pobieranie wierszy zbiorczych nie jest zaimplementowane, struktura wywołuje tę funkcję elementu członkowskiego, aby automatycznie wymieniać dane między elementami członkowskimi obiektu zestawu rekordów i odpowiednimi kolumnami bieżącego rekordu w źródle danych. `DoFieldExchange`wiąże także elementy członkowskie danych parametrów, jeśli istnieją, do zastępczych parametrów w ciągu instrukcji SQL dla wyboru zestawu rekordów.

Jeśli zaimplementowano pobieranie wierszy zbiorczych, struktura wywołuje [DoBulkFieldExchange](#dobulkfieldexchange). Aby zaimplementować pobieranie wierszy zbiorczych, należy określić `CRecordset::useMultiRowFetch` opcję parametru *dwOptions* w funkcji [Open](#open) member.

> [!NOTE]
> `DoFieldExchange`jest dostępny tylko wtedy, gdy używana jest Klasa pochodna z `CRecordset` . Jeśli obiekt zestawu rekordów został utworzony bezpośrednio z `CRecordset` , należy wywołać funkcję elementu członkowskiego [GetFieldValue —](#getfieldvalue) , aby pobrać dane.

Wymiana danych pól, nazywana wymianą pól rekordów (RFX), działa w obu kierunkach: od elementów członkowskich danych pola obiektu recordset do pól rekordu w źródle danych i z rekordu źródła danych do obiektu zestawu rekordów.

Jedyną akcją, którą należy zwykle wykonać w celu wdrożenia `DoFieldExchange` dla pochodnej klasy zestawu rekordów, jest utworzenie klasy z ClassWizard i określenie nazw i typów danych elementów członkowskich danych pola. Możesz również dodać kod do ClassWizard zapisów, aby określić składowe danych parametrów lub aby zająć się wszystkimi kolumnami, które są powiązane dynamicznie. Aby uzyskać więcej informacji, zobacz [zestaw rekordów artykułów: dynamiczne wiązanie kolumn danych (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Po zadeklarowaniu pochodnej klasy zestawu rekordów przy użyciu ClassWizard kreator zapisuje przesłonięcie `DoFieldExchange` dla Ciebie, co przypomina następujący przykład:

[!code-cpp[NVC_MFCDatabase#19](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]

Aby uzyskać więcej informacji o funkcjach RFX, zobacz temat [Funkcje wymiany pola rekordu](../../mfc/reference/record-field-exchange-functions.md)tematu.

Aby uzyskać więcej przykładów i szczegółowych informacji o `DoFieldExchange` programie, zobacz temat [wymiana pól rekordów artykułu: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Aby uzyskać ogólne informacje na temat RFX, zobacz artykuł [rekord pola rekordu](../../data/odbc/record-field-exchange-rfx.md).

## <a name="crecordsetedit"></a><a name="edit"></a>CRecordset:: Edit

Zezwala na zmiany w bieżącym rekordzie.

```
virtual void Edit();
```

### <a name="remarks"></a>Uwagi

Po wywołaniu `Edit` , można zmienić elementy członkowskie danych pola przez bezpośrednie Resetowanie ich wartości. Operacja jest wykonywana po ponownym wywołaniu funkcji [Update](#update) member w celu zapisania zmian w źródle danych.

> [!NOTE]
> Jeśli zaimplementowano pobieranie wierszy zbiorczych, nie można wywołać `Edit` . Spowoduje to nieudane potwierdzenie. Chociaż Klasa nie `CRecordset` udostępnia mechanizmu do aktualizowania wierszy danych zbiorczych, można napisać własne funkcje przy użyciu funkcji ODBC API `SQLSetPos` . Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`Edit`zapisuje wartości elementów członkowskich danych zestawu rekordów. Jeśli wywołasz `Edit` , wprowadzisz zmiany, a następnie wywołajesz `Edit` ponownie, wartości rekordu są przywracane do tych, które były przed pierwszym `Edit` wywołaniem.

W niektórych przypadkach możesz chcieć zaktualizować kolumnę, wprowadzając wartość null (bez danych). Aby to zrobić, należy wywołać [SetFieldNull](#setfieldnull) z parametrem true, aby oznaczyć pole null. powoduje to również zaktualizowanie kolumny. Jeśli chcesz, aby pole było zapisywane w źródle danych, mimo że jego wartość nie uległa zmianie, wywołaj [SetFieldDirty](#setfielddirty) z parametrem true. Działa to nawet wtedy, gdy pole ma wartość null.

Jeśli źródło danych obsługuje transakcje, można utworzyć `Edit` część wywołania transakcji. Należy pamiętać, że należy wywołać [CDatabase:: BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) przed wywołaniem `Edit` i po otwarciu zestawu rekordów. Należy również zauważyć, że wywołanie [CDatabase:: CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) nie zastępuje wywołania, `Update` Aby ukończyć `Edit` operację. Aby uzyskać więcej informacji na temat transakcji, zobacz Klasa [CDatabase](../../mfc/reference/cdatabase-class.md).

W zależności od bieżącego trybu blokowania, aktualizowany rekord może być zablokowany `Edit` do momentu wywołania `Update` lub przewinięcia do innego rekordu lub może być zablokowany tylko podczas `Edit` wywołania. Tryb blokowania można zmienić za pomocą [Setlockmode](#setlockingmode).

Poprzednia wartość w bieżącym rekordzie zostanie przywrócona, jeśli przewiniesz do nowego rekordu `Update` . `CDBException`Jest zgłaszany w przypadku wywołania `Edit` zestawu rekordów, którego nie można zaktualizować lub jeśli nie ma bieżącego rekordu.

Aby uzyskać więcej informacji, zobacz artykuł [transakcje (ODBC)](../../data/odbc/transaction-odbc.md) i [zestaw rekordów: blokowanie rekordów (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#20](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]

## <a name="crecordsetflushresultset"></a><a name="flushresultset"></a>CRecordset::FlushResultSet

Pobiera następny zestaw wyników wstępnie zdefiniowanego zapytania (procedura składowana), jeśli istnieje wiele zestawów wyników.

```
BOOL FlushResultSet();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli istnieje więcej zestawów wyników do pobrania; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Należy wywołać `FlushResultSet` tylko wtedy, gdy wszystko jest gotowe do końca z kursorem w bieżącym zestawie wyników. Należy pamiętać, że po pobraniu następnego zestawu wyników przez wywołanie `FlushResultSet` , kursor nie jest prawidłowy w tym zestawie wyników; należy wywołać funkcję elementu członkowskiego [MoveNext](#movenext) po wywołaniu `FlushResultSet` .

Jeśli wstępnie zdefiniowane zapytanie używa parametru wyjściowego lub parametrów wejściowych/wyjściowych, należy wywołać `FlushResultSet` do momentu, aż zwróci `FALSE` (wartość 0), aby uzyskać te wartości parametrów.

`FlushResultSet`wywołuje funkcję interfejsu API ODBC `SQLMoreResults` . Jeśli `SQLMoreResults` zwraca SQL_ERROR lub SQL_INVALID_HANDLE, `FlushResultSet` zostanie zgłoszony wyjątek. Aby uzyskać więcej informacji na temat `SQLMoreResults` , zobacz Windows SDK.

Procedura składowana musi mieć powiązane pola, jeśli chcesz wywołać `FlushResultSet` .

### <a name="example"></a>Przykład

Poniższy kod założono, że `COutParamRecordset` jest `CRecordset` obiektem pochodnym na podstawie wstępnie zdefiniowanego zapytania z parametrem wejściowym i parametrem Output i ma wiele zestawów wyników. Zanotuj strukturę przesłonięcia [DoFieldExchange](#dofieldexchange) .

[!code-cpp[NVC_MFCDatabase#21](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]

[!code-cpp[NVC_MFCDatabase#22](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]

## <a name="crecordsetgetbookmark"></a><a name="getbookmark"></a>CRecordset:: GetBookmark

Uzyskuje wartość zakładki dla bieżącego rekordu.

```cpp
void GetBookmark(CDBVariant& varBookmark);
```

### <a name="parameters"></a>Parametry

*varBookmark*<br/>
Odwołanie do obiektu [CDBVariant](../../mfc/reference/cdbvariant-class.md) reprezentującego zakładkę dla bieżącego rekordu.

### <a name="remarks"></a>Uwagi

Aby określić, czy zakładki są obsługiwane w zestawie rekordów, [Wywołaj polecenie](#canbookmark). Aby zakładki były dostępne, jeśli są obsługiwane, należy ustawić `CRecordset::useBookmarks` opcję w parametrze *DwOptions* funkcji [Open](#open) member.

> [!NOTE]
> Jeśli zakładki są nieobsługiwane lub niedostępne, wywołanie `GetBookmark` spowoduje zgłoszenie wyjątku. Zakładki nie są obsługiwane w zestawach rekordów tylko do przodu.

`GetBookmark`przypisuje wartość zakładki dla bieżącego rekordu do `CDBVariant` obiektu. Aby powrócić do tego rekordu w dowolnym momencie po przejściu do innego rekordu, wywołaj metodę [SetBookmark](#setbookmark) z odpowiednim `CDBVariant` obiektem.

> [!NOTE]
> Po pewnych operacjach zestawu rekordów zakładki mogą nie być już prawidłowe. Na przykład, jeśli wywołujesz `GetBookmark` `Requery` polecenie, możesz nie być w stanie wrócić do rekordu przy użyciu `SetBookmark` . Wywołaj [CDatabase:: GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) , aby sprawdzić, czy można bezpiecznie wywołać `SetBookmark` .

Aby uzyskać więcej informacji o zakładkach i nawigowaniu po zestawach rekordów, zobacz [zestawy rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) i [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="crecordsetgetdefaultconnect"></a><a name="getdefaultconnect"></a>CRecordset::GetDefaultConnect

Wywołuje się, by uzyskać domyślne parametry połączenia.

```
virtual CString GetDefaultConnect();
```

### <a name="return-value"></a>Wartość zwracana

A `CString` , który zawiera domyślne parametry połączenia.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę funkcję elementu członkowskiego, aby uzyskać domyślne parametry połączenia dla źródła danych, na którym bazuje zestaw rekordów. ClassWizard implementuje tę funkcję przez zidentyfikowanie tego samego źródła danych, którego używasz w ClassWizard, aby uzyskać informacje o tabelach i kolumnach. Prawdopodobnie warto zależeć od domyślnego połączenia podczas tworzenia aplikacji. Ale domyślne połączenie może nie być odpowiednie dla użytkowników aplikacji. W takim przypadku należy wdrożyć tę funkcję, odrzucając wersję ClassWizard. Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz artykuł [Data Source (ODBC)](../../data/odbc/data-source-odbc.md).

## <a name="crecordsetgetdefaultsql"></a><a name="getdefaultsql"></a>CRecordset::GetDefaultSQL

Wywołuje się, by uzyskać domyślny ciąg SQL do wykonania.

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>Wartość zwracana

A `CString` , który zawiera domyślną instrukcję języka SQL.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę funkcję elementu członkowskiego, aby uzyskać domyślną instrukcję SQL, na której bazuje zestaw rekordów. Może to być nazwa tabeli lub instrukcja **SELECT** języka SQL.

Można pośrednio zdefiniować domyślną instrukcję SQL, deklarując klasę zestawu rekordów z ClassWizard i ClassWizard wykonuje to zadanie.

Jeśli potrzebujesz ciągu instrukcji SQL do własnego użytku, należy wywołać metodę `GetSQL` , która zwraca instrukcję SQL używaną do wybierania rekordów zestawu rekordów, gdy została otwarta. Można edytować domyślny ciąg SQL w przesłonięciu klasy `GetDefaultSQL` . Można na przykład określić wywołanie wstępnie zdefiniowanego zapytania przy użyciu instrukcji **call** . (Pamiętaj jednak, że Jeśli edytujesz `GetDefaultSQL` , musisz także zmodyfikować, `m_nFields` Aby dopasować liczbę kolumn w źródle danych).

Aby uzyskać więcej informacji, zobacz [zestaw rekordów artykułów: deklarowanie klasy dla tabeli (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).

> [!CAUTION]
> Nazwa tabeli będzie pusta, jeśli struktura nie może zidentyfikować nazwy tabeli, jeśli podano wiele nazw tabel lub nie można zinterpretować instrukcji **call** . Należy pamiętać, że w przypadku używania instrukcji **call** nie należy wstawiać odstępów między nawiasem klamrowym i słowem kluczowym **wywołania** , ani wstawiać odstępów przed nawiasem klamrowym lub przed słowem kluczowym **SELECT** w instrukcji **SELECT** .

## <a name="crecordsetgetfieldvalue"></a><a name="getfieldvalue"></a>CRecordset:: GetFieldValue —

Pobiera dane pól w bieżącym rekordzie.

```cpp
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

*lpszName*<br/>
Nazwa pola.

*varValu*e odwołanie do obiektu [CDBVariant](../../mfc/reference/cdbvariant-class.md) , który będzie przechowywać wartość pola.

*nFieldType*<br/>
Typ danych ODBC C pola. Korzystając z wartości domyślnej, DEFAULT_FIELD_TYPE, wymuszają `GetFieldValue` Określanie typu danych C z typu danych SQL w oparciu o poniższą tabelę. W przeciwnym razie można określić typ danych bezpośrednio lub wybrać zgodny typ danych. na przykład można przechowywać dowolny typ danych w SQL_C_CHAR.

|Typ danych języka C|Typ danych SQL|
|-----------------|-------------------|
|SQL_C_BIT|SQL_BIT|
|SQL_C_UTINYINT|SQL_TINYINT|
|SQL_C_SSHORT|SQL_SMALLINT|
|SQL_C_SLONG|SQL_INTEGER|
|SQL_C_FLOAT|SQL_REAL|
|SQL_C_DOUBLE|SQL_FLOATSQL_DOUBLE|
|SQL_C_TIMESTAMP|SQL_DATESQL_TIMESQL_TIMESTAMP|
|SQL_C_CHAR|SQL_NUMERICSQL_DECIMALSQL_BIGINTSQL_CHARSQL_VARCHARSQL_LONGVARCHAR|
|SQL_C_BINARY|SQL_BINARYSQL_VARBINARYSQL_LONGVARBINARY|

Aby uzyskać więcej informacji na temat typów danych ODBC, zobacz tematy "typy danych SQL" i "typy danych C" w dodatku D Windows SDK.

*nIndex*<br/>
Indeks pola (liczony od zera).

*strValue*<br/>
Odwołanie do obiektu [CString](../../atl-mfc-shared/reference/cstringt-class.md) , w którym będzie przechowywana wartość pola konwertowana na tekst, niezależnie od typu danych pola.

### <a name="remarks"></a>Uwagi

Można wyszukać pole według nazwy lub indeksu. Wartość pola można przechowywać w `CDBVariant` obiekcie lub `CString` obiekcie.

Jeśli zaimplementowano pobieranie wierszy zbiorczych, bieżący rekord jest zawsze umieszczany na pierwszym rekordzie zestawu wierszy. Aby można było użyć `GetFieldValue` rekordu w ramach danego zestawu wierszy, należy najpierw wywołać funkcję elementu członkowskiego [SetRowsetCursorPosition](#setrowsetcursorposition) , aby przenieść kursor do żądanego wiersza w tym zestawie wierszy. Następnie Wywołaj `GetFieldValue` dla tego wiersza. Aby zaimplementować pobieranie wierszy zbiorczych, należy określić `CRecordset::useMultiRowFetch` opcję parametru *dwOptions* w funkcji [Open](#open) member.

Można użyć `GetFieldValue` do dynamicznego pobierania pól w czasie wykonywania zamiast statycznego powiązania ich w czasie projektowania. Na przykład, Jeśli zadeklarowano obiekt zestawu rekordów bezpośrednio z `CRecordset` , należy użyć, `GetFieldValue` Aby pobrać dane pola; nie zaimplementowano wymiany pól rekordów (RFX) lub wymiany pól rekordów zbiorczych (bulk RFX).

> [!NOTE]
> Jeśli zadeklarujesz obiekt zestawu rekordów bez wyprowadzania z `CRecordset` , nie masz załadowanej biblioteki kursora ODBC. Biblioteka kursorów wymaga, aby zestaw rekordów zawierał co najmniej jedną kolumnę powiązaną; Jeśli jednak używasz `CRecordset` bezpośrednio, żadna z kolumn nie jest powiązana. Funkcje członkowskie [CDatabase:: OpenEx](../../mfc/reference/cdatabase-class.md#openex) i [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open) kontrolują, czy biblioteka kursorów zostanie załadowana.

`GetFieldValue`wywołuje funkcję interfejsu API ODBC `SQLGetData` . Jeśli sterownik wyprowadza wartość SQL_NO_TOTAL dla rzeczywistej długości wartości pola, `GetFieldValue` zgłasza wyjątek. Aby uzyskać więcej informacji na temat `SQLGetData` , zobacz Windows SDK.

### <a name="example"></a>Przykład

Następujący przykładowy kod ilustruje wywołania `GetFieldValue` dla obiektu zestawu rekordów zadeklarowanego bezpośrednio z `CRecordset` .

[!code-cpp[NVC_MFCDatabase#23](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]

> [!NOTE]
> W przeciwieństwie do klasy `CDaoRecordset` DAO `CRecordset` nie ma `SetFieldValue` funkcji członkowskiej. Jeśli utworzysz obiekt bezpośrednio z `CRecordset` , jest on efektywnie tylko do odczytu.

Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetgetodbcfieldcount"></a><a name="getodbcfieldcount"></a>CRecordset::GetODBCFieldCount

Pobiera łączną liczbę pól w obiekcie zestawu rekordów.

```
short GetODBCFieldCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba pól w zestawie rekordów.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat tworzenia zestawów rekordów, zobacz [zestaw rekordów artykułów: Tworzenie i zamykanie zestawów rekordów (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

## <a name="crecordsetgetodbcfieldinfo"></a><a name="getodbcfieldinfo"></a>CRecordset::GetODBCFieldInfo

Uzyskuje informacje o polach w zestawie rekordów.

```cpp
void GetODBCFieldInfo(
    LPCTSTR lpszName,
    CODBCFieldInfo& fieldinfo);

void GetODBCFieldInfo(
    short nIndex,
    CODBCFieldInfo& fieldinfo);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Nazwa pola.

*FieldInfo*<br/>
Odwołanie do `CODBCFieldInfo` struktury.

*nIndex*<br/>
Indeks pola (liczony od zera).

### <a name="remarks"></a>Uwagi

Jedna wersja funkcji pozwala wyszukiwać pola według nazwy. Inna wersja pozwala wyszukiwać pola według indeksu.

Aby uzyskać opis zwracanych informacji, zobacz strukturę [CODBCFieldInfo —](../../mfc/reference/codbcfieldinfo-structure.md) .

Aby uzyskać więcej informacji na temat tworzenia zestawów rekordów, zobacz [zestaw rekordów artykułów: Tworzenie i zamykanie zestawów rekordów (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

## <a name="crecordsetgetrecordcount"></a><a name="getrecordcount"></a>CRecordset::GetRecordCount

Określa rozmiar zestawu rekordów.

```
long GetRecordCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba rekordów w zestawie rekordów; 0, jeśli zestaw rekordów nie zawiera żadnych rekordów; lub-1, jeśli nie można określić liczby rekordów.

### <a name="remarks"></a>Uwagi

> [!CAUTION]
> Liczba rekordów jest utrzymywana jako "górny znacznik", czyli rekord najwyższego numeruka, który jest jeszcze widoczny, gdy użytkownik przechodzi przez rekordy. Łączna liczba rekordów jest znana tylko po przeniesieniu użytkownika poza ostatni rekord. Ze względu na wydajność liczba nie jest aktualizowana podczas wywoływania `MoveLast` . Aby samodzielnie policzyć rekordy, Połącz się `MoveNext` wielokrotnie do momentu, gdy `IsEOF` zwróci wartość różną od zera. Dodawanie rekordu przy użyciu `CRecordset:AddNew` i `Update` zwiększanie liczby; Usuwanie rekordu przez `CRecordset::Delete` zmniejszenie liczby.

## <a name="crecordsetgetrowsetsize"></a><a name="getrowsetsize"></a>CRecordset::GetRowsetSize

Uzyskuje bieżące ustawienie liczby wierszy, które mają zostać pobrane podczas danego pobierania.

```
DWORD GetRowsetSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba wierszy do pobrania podczas danego pobierania.

### <a name="remarks"></a>Uwagi

Jeśli używasz pobierania wierszy zbiorczych, domyślnym rozmiarem zestawu wierszy podczas otwierania zestawu rekordów jest 25; w przeciwnym razie jest to 1.

Aby zaimplementować pobieranie wierszy zbiorczych, należy określić `CRecordset::useMultiRowFetch` opcję w parametrze *DwOptions* funkcji [Open](#open) member. Aby zmienić ustawienie dla rozmiaru zestawu wierszy, wywołaj [SetRowsetSize](#setrowsetsize).

Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetgetrowsfetched"></a><a name="getrowsfetched"></a>CRecordset::GetRowsFetched

Określa liczbę rekordów, które zostały faktycznie pobrane po zakończeniu pobierania.

```
DWORD GetRowsFetched() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba wierszy pobranych ze źródła danych po danym pobieraniu.

### <a name="remarks"></a>Uwagi

Jest to przydatne, gdy wdrożono pobieranie wierszy zbiorczych. Rozmiar zestawu wierszy zwykle wskazuje, ile wierszy zostanie pobranych z pobrania; jednak całkowita liczba wierszy w zestawie rekordów wpływa również na liczbę wierszy, które będą pobierane w zestawie wierszy. Na przykład jeśli zestaw rekordów zawiera 10 rekordów z ustawieniem rozmiaru zestawu wierszy wynoszącym 4, zapętlenie przez wywołanie zestawu rekordów `MoveNext` spowoduje, że końcowy zestaw wierszy ma tylko 2 rekordy.

Aby zaimplementować pobieranie wierszy zbiorczych, należy określić `CRecordset::useMultiRowFetch` opcję w parametrze *DwOptions* funkcji [Open](#open) member. Aby określić rozmiar zestawu wierszy, wywołaj [SetRowsetSize](#setrowsetsize).

Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#24](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]

## <a name="crecordsetgetrowstatus"></a><a name="getrowstatus"></a>CRecordset:: GetRowStatus

Uzyskuje stan wiersza w bieżącym zestawie wierszy.

```
WORD GetRowStatus(WORD wRow) const;
```

### <a name="parameters"></a>Parametry

*wRow*<br/>
Pozycja jednego wiersza w bieżącym zestawie wierszy. Ta wartość może być z zakresu od 1 do rozmiaru zestawu wierszy.

### <a name="return-value"></a>Wartość zwracana

Wartość stanu wiersza. Aby uzyskać szczegółowe informacje, zobacz uwagi.

### <a name="remarks"></a>Uwagi

`GetRowStatus`Zwraca wartość, która wskazuje każdą zmianę stanu do wiersza od momentu ostatniego pobrania ze źródła danych lub że nie został pobrany żaden wiersz odpowiadający *wRow* . Poniższa tabela zawiera listę możliwych zwracanych wartości.

|Wartość stanu|Opis|
|------------------|-----------------|
|SQL_ROW_SUCCESS|Wiersz nie jest zmieniany.|
|SQL_ROW_UPDATED|Wiersz został zaktualizowany.|
|SQL_ROW_DELETED|Wiersz został usunięty.|
|SQL_ROW_ADDED|Wiersz został dodany.|
|SQL_ROW_ERROR|Nie można pobrać wiersza z powodu błędu.|
|SQL_ROW_NOROW|Brak wiersza, który odnosi się do *wRow*.|

Aby uzyskać więcej informacji, zobacz Funkcja ODBC API `SQLExtendedFetch` w Windows SDK.

## <a name="crecordsetgetstatus"></a><a name="getstatus"></a>CRecordset:: GetStatus

Określa indeks bieżącego rekordu w zestawie rekordów i wskazuje, czy został wyświetlony ostatni rekord.

```cpp
void GetStatus(CRecordsetStatus& rStatus) const;
```

### <a name="parameters"></a>Parametry

*rStatus*<br/>
Odwołanie do `CRecordsetStatus` obiektu. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.

### <a name="remarks"></a>Uwagi

`CRecordset`próbuje śledzić indeks, ale w pewnych okolicznościach może to nie być możliwe. Zobacz [GetRecordCount](#getrecordcount) , aby uzyskać wyjaśnienie.

`CRecordsetStatus`Struktura ma następującą postać:

```cpp
struct CRecordsetStatus
{
    long m_lCurrentRecord;
    BOOL m_bRecordCountFinal;
};
```

Dwa elementy członkowskie `CRecordsetStatus` mają następujące znaczenie:

- `m_lCurrentRecord`Zawiera indeks (liczony od zera) bieżącego rekordu w zestawie rekordów, jeśli jest znany. Jeśli nie można ustalić indeksu, ten element członkowski zawiera AFX_CURRENT_RECORD_UNDEFINED (-2). Jeśli `IsBOF` wartość jest równa true (pusty zestaw rekordów lub próba przewinięcia przed pierwszym rekordem), `m_lCurrentRecord` zostanie ustawiona wartość AFX_CURRENT_RECORD_BOF (-1). Jeśli pierwszy rekord jest ustawiony na 0, drugi rekord 1 i tak dalej.

- `m_bRecordCountFinal`Wartość różna od zera, jeśli określono łączną liczbę rekordów w zestawie rekordów. Ogólnie rzecz biorąc należy to zrobić, zaczynając od początku zestawu rekordów i wywołując `MoveNext` do momentu, gdy `IsEOF` zwróci wartość różną od zera. Jeśli ten element członkowski ma wartość zero, liczba rekordów w postaci zwróconej przez `GetRecordCount` , jeśli nie-1, jest liczbą rekordów równą "górny znacznik wodny".

## <a name="crecordsetgetsql"></a><a name="getsql"></a>CRecordset::GetSQL

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać instrukcję SQL, która została użyta do wybrania rekordów zestawu rekordów, gdy została otwarta.

```
const CString& GetSQL() const;
```

### <a name="return-value"></a>Wartość zwracana

**`const`** Odwołanie do elementu `CString` , który zawiera instrukcję języka SQL.

### <a name="remarks"></a>Uwagi

Zwykle będzie to instrukcja **SELECT** języka SQL. Ciąg zwracany przez `GetSQL` jest tylko do odczytu.

Ciąg zwracany przez `GetSQL` jest zwykle różny od dowolnego ciągu, który mógł zostać przekazana do zestawu rekordów w parametrze *lpszSQL* do `Open` funkcji członkowskiej. Wynika to z faktu, że zestaw rekordów tworzy pełną instrukcję SQL na podstawie tego, co zostało przesłane do `Open` , co zostało określone za pomocą ClassWizard, co można określić w `m_strFilter` `m_strSort` elementach członkowskich danych i w określonych parametrach. Aby uzyskać szczegółowe informacje o tym, jak zestaw rekordów tworzy instrukcję SQL, zobacz [zestaw rekordów artykułów: jak zestawy rekordów wybierają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

> [!NOTE]
> Wywołaj tę funkcję elementu członkowskiego tylko po wywołaniu metody [Open](#open).

## <a name="crecordsetgettablename"></a><a name="gettablename"></a>CRecordset:: gettablename

Pobiera nazwę tabeli SQL, na której bazuje zapytanie zestawu rekordów.

```
const CString& GetTableName() const;
```

### <a name="return-value"></a>Wartość zwracana

**`const`** Odwołanie do obiektu, `CString` który zawiera nazwę tabeli, jeśli zestaw rekordów jest oparty na tabeli; w przeciwnym razie pusty ciąg.

### <a name="remarks"></a>Uwagi

`GetTableName`jest prawidłowy tylko wtedy, gdy zestaw rekordów jest oparty na tabeli, a nie w sprzężeniu wielu tabel lub wstępnie zdefiniowanego zapytania (procedura składowana). Nazwa jest tylko do odczytu.

> [!NOTE]
> Wywołaj tę funkcję elementu członkowskiego tylko po wywołaniu metody [Open](#open).

## <a name="crecordsetisbof"></a><a name="isbof"></a>CRecordset::IsBOF

Zwraca wartość różną od zera, jeśli zestaw rekordów został umieszczony przed pierwszym rekordem. Brak bieżącego rekordu.

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli zestaw rekordów nie zawiera żadnych rekordów lub przewinie wstecz przed pierwszym rekordem; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję elementu członkowskiego przed przewinięciem rekordu do rekordu, aby dowiedzieć się, czy przed pierwszym rekordem zestawu rekordów został usunięty. Można również użyć programu `IsBOF` oraz, `IsEOF` Aby określić, czy zestaw rekordów zawiera wszystkie rekordy, czy jest pusty. Natychmiast po wywołaniu `Open` , jeśli zestaw rekordów nie zawiera żadnych rekordów, `IsBOF` zwraca wartość różną od zera. Po otwarciu zestawu rekordów, który ma co najmniej jeden rekord, pierwszy rekord jest bieżącym rekordem i `IsBOF` zwraca 0.

Jeśli pierwszy rekord jest bieżącym rekordem i wywołaniem `MovePrev` , `IsBOF` następnie zwróci wartość różną od zera. Jeśli `IsBOF` zwraca wartość różną od zera i wywołuje `MovePrev` , wystąpi błąd. Jeśli `IsBOF` zwraca wartość różną od zera, bieżący rekord jest niezdefiniowany i wszystkie akcje, które wymagają bieżącego rekordu, spowodują wystąpienie błędu.

### <a name="example"></a>Przykład

Ten przykład używa `IsBOF` i `IsEOF` do wykrywania limitów zestawu rekordów w miarę przewijania kodu przez zestaw rekordów w obu kierunkach.

[!code-cpp[NVC_MFCDatabase#25](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]

## <a name="crecordsetisdeleted"></a><a name="isdeleted"></a>CRecordset:: IsDeleted

Określa, czy bieżący rekord został usunięty.

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli zestaw rekordów jest umieszczony na usuniętym rekordzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli przewiniesz do rekordu i `IsDeleted` zwrócisz wartość true (niezerowa), należy przewinąć do innego rekordu przed wykonaniem innych operacji zestawu rekordów.

Wynik zależy od `IsDeleted` wielu czynników, takich jak typ zestawu rekordów, czy zestaw rekordów jest aktualizowalny, niezależnie od tego, czy określono `CRecordset::skipDeletedRecords` opcję podczas otwierania zestawu rekordów, czy pakiety sterowników zostały usunięte, oraz czy istnieje wielu użytkowników.

Aby uzyskać więcej informacji na temat `CRecordset::skipDeletedRecords` i pakowanie sterowników, zobacz [Open](#open) member Function.

> [!NOTE]
> Jeśli zaimplementowano pobieranie wierszy zbiorczych, nie należy wywoływać `IsDeleted` . Zamiast tego wywołaj funkcję członkowską [GetRowStatus](#getrowstatus) . Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetiseof"></a><a name="iseof"></a>CRecordset::IsEOF

Zwraca wartość różną od zera, jeśli zestaw rekordów został umieszczony po ostatnim rekordzie. Brak bieżącego rekordu.

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli zestaw rekordów nie zawiera żadnych rekordów lub przewinie się poza ostatnim rekordem; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję elementu członkowskiego podczas przewijania z rekordu do rekordu, aby dowiedzieć się, czy zostały utracone poza ostatnim rekordem zestawu rekordów. Można również użyć, `IsEOF` Aby określić, czy zestaw rekordów zawiera wszystkie rekordy, czy jest pusty. Natychmiast po wywołaniu `Open` , jeśli zestaw rekordów nie zawiera żadnych rekordów, `IsEOF` zwraca wartość różną od zera. Po otwarciu zestawu rekordów, który ma co najmniej jeden rekord, pierwszy rekord jest bieżącym rekordem i `IsEOF` zwraca 0.

Jeśli ostatni rekord jest bieżącym rekordem podczas wywołania, zwróci `MoveNext` `IsEOF` wynik różny od zera. Jeśli `IsEOF` zwraca wartość różną od zera i wywołuje `MoveNext` , wystąpi błąd. Jeśli `IsEOF` zwraca wartość różną od zera, bieżący rekord jest niezdefiniowany i wszystkie akcje, które wymagają bieżącego rekordu, spowodują wystąpienie błędu.

### <a name="example"></a>Przykład

Zobacz przykład dla [IsBOF](#isbof).

## <a name="crecordsetisfielddirty"></a><a name="isfielddirty"></a>CRecordset::IsFieldDirty

Określa, czy określony element członkowski danych pola został zmieniony od momentu wywołania metody [Edit](#edit) lub [AddNew](#addnew) .

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>Parametry

*wa*<br/>
Wskaźnik do elementu członkowskiego danych pola, którego stan chcesz sprawdzić, lub wartość NULL, aby określić, czy dowolne z pól są zanieczyszczone.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli określony element członkowski danych pola został zmieniony od czasu wywołania `AddNew` lub `Edit` ; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Dane we wszystkich elementach członkowskich danych zanieczyszczonych pól zostaną przesłane do rekordu w źródle danych, gdy bieżący rekord zostanie zaktualizowany przez wywołanie funkcji elementu członkowskiego [aktualizacji](#update) `CRecordset` (po wywołaniu `Edit` lub `AddNew` ).

> [!NOTE]
> Ta funkcja członkowska nie ma zastosowania w zestawach rekordów używających pobierania wierszy zbiorczych. Jeśli zaimplementowano pobieranie wierszy zbiorczych, program `IsFieldDirty` zawsze zwróci wartość false i spowoduje, że zakończyło się niepowodzeniem. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Wywołanie `IsFieldDirty` spowoduje zresetowanie efektów poprzednich wywołań do [SetFieldDirty](#setfielddirty) , ponieważ zmieniony stan pola jest ponownie oceniony. W `AddNew` przypadku, gdy bieżąca wartość pola różni się od wartości pseudo null, stan pola jest ustawiony na wartość Dirty. W `Edit` przypadku gdy wartość pola różni się od wartości w pamięci podręcznej, stan pola jest ustawiony na wartość Dirty.

`IsFieldDirty`jest implementowana za poorednictwem [DoFieldExchange](#dofieldexchange).

Aby uzyskać więcej informacji na temat flagi Dirty, zobacz [zestaw rekordów artykułów: jak zestawy rekordów wybierają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

## <a name="crecordsetisfieldnull"></a><a name="isfieldnull"></a>CRecordset::IsFieldNull

Zwraca wartość różną od zera, jeśli określone pole w bieżącym rekordzie ma wartość null (nie ma wartości).

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>Parametry

*wa*<br/>
Wskaźnik do elementu członkowskiego danych pola, którego stan chcesz sprawdzić, lub wartość NULL, aby określić, czy którekolwiek z pól mają wartość null.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli określony element członkowski danych pola jest oflagowany jako null; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy określony element członkowski danych pola zestawu rekordów został oflagowany jako wartość null. (W terminologii bazy danych wartość null oznacza brak wartości i nie jest taka sama jak wartość NULL w języku C++). Jeśli element członkowski danych pola jest oflagowany jako null, jest interpretowany jako kolumna bieżącego rekordu, dla którego nie ma wartości.

> [!NOTE]
> Ta funkcja członkowska nie ma zastosowania w zestawach rekordów używających pobierania wierszy zbiorczych. Jeśli zaimplementowano pobieranie wierszy zbiorczych, program `IsFieldNull` zawsze zwróci wartość false i spowoduje, że zakończyło się niepowodzeniem. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`IsFieldNull`jest implementowana za poorednictwem [DoFieldExchange](#dofieldexchange).

## <a name="crecordsetisfieldnullable"></a><a name="isfieldnullable"></a>CRecordset::IsFieldNullable

Zwraca wartość różną od zera, jeśli określone pole w bieżącym rekordzie można ustawić na wartość null (bez wartości).

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>Parametry

*wa*<br/>
Wskaźnik do elementu członkowskiego danych pola, którego stan chcesz sprawdzić, lub wartość NULL, aby określić, czy dowolne z pól można ustawić na wartość null.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy określony element członkowski danych pola jest typu "nullable" (można ustawić wartość null; Język C++ o wartości NULL nie jest taki sam jak wartość null, co w terminologii bazy danych oznacza, że nie ma żadnej wartości.

> [!NOTE]
> Jeśli zaimplementowano pobieranie wierszy zbiorczych, nie można wywołać `IsFieldNullable` . Zamiast tego wywołaj funkcję elementu członkowskiego [GetODBCFieldInfo](#getodbcfieldinfo) , aby określić, czy pole może mieć ustawioną wartość null. Należy pamiętać, że zawsze można wywołać `GetODBCFieldInfo` , niezależnie od tego, czy wdrożono pobieranie wierszy zbiorczych. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Pole, które nie może mieć wartości null, musi mieć wartość. Jeśli podczas dodawania lub aktualizowania rekordu zostanie podjęta próba ustawienia takiego pola na wartość null, źródło danych odrzuci dodanie lub aktualizację, a [Aktualizacja](#update) zgłosi wyjątek. Wyjątek występuje w przypadku wywołania `Update` , nie w przypadku wywołania [SetFieldNull](#setfieldnull).

Użycie wartości NULL dla pierwszego argumentu funkcji spowoduje zastosowanie funkcji tylko do `outputColumn` pól, a nie `param` pól. Na przykład wywołanie

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

spowoduje ustawienie tylko `outputColumn` pól na null; nie `param` wpłynie to na pola.

Aby można było korzystać z `param` pól, należy podać rzeczywisty adres osoby `param` , na której ma być wykonywane działanie, na przykład:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

Oznacza to, że nie można ustawić `param` wartości null dla wszystkich pól, jak można z `outputColumn` polami.

`IsFieldNullable`jest implementowana za poorednictwem [DoFieldExchange](#dofieldexchange).

## <a name="crecordsetisopen"></a><a name="isopen"></a>CRecordset:: IsOpen

Określa, czy zestaw rekordów jest już otwarty.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja członkowska [Open](#open) lub [Requery](#requery) obiektu zestawu rekordów została wcześniej wywołana i zestaw rekordów nie został zamknięty. w przeciwnym razie 0.

## <a name="crecordsetm_hstmt"></a><a name="m_hstmt"></a>CRecordset:: m_hstmt

Zawiera dojście do struktury danych instrukcji ODBC, typu HSTMT, skojarzone z zestawem rekordów.

### <a name="remarks"></a>Uwagi

Każde zapytanie do źródła danych ODBC jest skojarzone z HSTMT.

> [!CAUTION]
> Nie należy używać `m_hstmt` przed wywołaniem metody [Open](#open) .

Zwykle nie ma potrzeby bezpośredniego dostępu do HSTMT, ale może być konieczne do bezpośredniego wykonania instrukcji SQL. `ExecuteSQL`Funkcja członkowska klasy `CDatabase` zawiera przykład użycia `m_hstmt` .

## <a name="crecordsetm_nfields"></a><a name="m_nfields"></a>CRecordset:: m_nFields

Zawiera liczbę elementów członkowskich danych pola w klasie zestawu rekordów; oznacza to, że liczba kolumn wybranych przez zestaw rekordów ze źródła danych.

### <a name="remarks"></a>Uwagi

Konstruktor dla klasy zestawu rekordów musi być zainicjowany `m_nFields` z poprawnym numerem. Jeśli nie zaimplementowano pobierania wierszy zbiorczych, ClassWizard zapisuje tę inicjalizację w przypadku użycia jej do deklarowania klasy zestawu rekordów. Możesz również napisać je ręcznie.

Struktura używa tej liczby do zarządzania interakcją między elementami członkowskimi danych pola i odpowiednimi kolumnami bieżącego rekordu w źródle danych.

> [!CAUTION]
> Ta liczba musi odpowiadać liczbie "kolumn wyjściowych" zarejestrowanych w `DoFieldExchange` lub `DoBulkFieldExchange` po wywołaniu metody [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) z parametrem `CFieldExchange::outputColumn` .

Można powiązać kolumny dynamicznie, jak wyjaśniono w artykule "zestaw rekordów: dynamiczne powiązanie kolumn danych". W takim przypadku należy zwiększyć liczbę w, `m_nFields` aby odzwierciedlić liczbę wywołań funkcji RFX lub bulk RFX w `DoFieldExchange` `DoBulkFieldExchange` funkcji składowej dla kolumn z wartościami dynamicznymi.

Aby uzyskać więcej informacji, zobacz [zestawy rekordów: dynamiczne wiązanie kolumn danych (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) i [zestaw rekordów: pobieranie rekordów w zbiorczej (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Przykład

Zapoznaj się z artykułem [wymiana pól rekordów: używanie RFX](../../data/odbc/record-field-exchange-using-rfx.md).

## <a name="crecordsetm_nparams"></a><a name="m_nparams"></a>CRecordset:: m_nParams

Zawiera liczbę elementów członkowskich danych parametrów w klasie zestawu rekordów; oznacza to, że liczba parametrów przesłanych z zapytaniem zestawu rekordów.

### <a name="remarks"></a>Uwagi

Jeśli Klasa zestawu rekordów ma wszystkie elementy członkowskie danych parametrów, Konstruktor dla klasy musi być zainicjowany `m_nParams` z poprawnym numerem. Wartość `m_nParams` domyślna to 0. W przypadku dodawania elementów członkowskich danych parametru (które należy wykonać ręcznie) należy również ręcznie dodać inicjalizację w konstruktorze klasy w celu odzwierciedlenia liczby parametrów (co musi być co najmniej tak duże jak liczba symboli zastępczych "" w `m_strFilter` ciągu lub " `m_strSort` ).

Struktura używa tej liczby podczas parameterizes zapytania zestawu rekordów.

> [!CAUTION]
> Ta liczba musi odpowiadać liczbie parametrów "params" zarejestrowanej w `DoFieldExchange` lub `DoBulkFieldExchange` po wywołaniu metody [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) z wartością parametru `CFieldExchange::inputParam` , `CFieldExchange::param` , `CFieldExchange::outputParam` , lub `CFieldExchange::inoutParam` .

### <a name="example"></a>Przykład

  Zobacz [zestawy rekordów: parametryzacja a zestaw rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) i [wymiana pól rekordów: przy użyciu RFX](../../data/odbc/record-field-exchange-using-rfx.md).

## <a name="crecordsetm_pdatabase"></a><a name="m_pdatabase"></a>CRecordset:: m_pDatabase

Zawiera wskaźnik do obiektu, `CDatabase` za pomocą którego zestaw rekordów jest połączony ze źródłem danych.

### <a name="remarks"></a>Uwagi

Ta zmienna jest ustawiana na dwa sposoby. Zwykle przekazuje się wskaźnik do już połączonego `CDatabase` obiektu podczas konstruowania obiektu zestawu rekordów. Jeśli zamiast tego przejdziesz wartość NULL, program `CRecordset` utworzy `CDatabase` obiekt dla Ciebie i nawiąże połączenie. W obu przypadkach, `CRecordset` zapisuje wskaźnik w tej zmiennej.

Zwykle nie trzeba bezpośrednio używać wskaźnika przechowywanego w `m_pDatabase` . W przypadku pisania własnych rozszerzeń do programu `CRecordset` może być konieczne użycie wskaźnika. Na przykład może być potrzebny wskaźnik, jeśli wygenerujesz własne `CDBException` . Lub może być konieczne, jeśli trzeba wykonać coś przy użyciu tego samego `CDatabase` obiektu, takiego jak uruchamianie transakcji, ustawienie limitów czasu lub wywołanie `ExecuteSQL` funkcji elementu członkowskiego klasy `CDatabase` do bezpośredniego wykonywania instrukcji SQL.

## <a name="crecordsetm_strfilter"></a><a name="m_strfilter"></a>CRecordset:: m_strFilter

Po utworzeniu obiektu zestawu rekordów, ale przed wywołaniem jego `Open` funkcji składowej, należy użyć tego elementu członkowskiego danych do przechowywania `CString` zawierającej klauzulę SQL **WHERE** .

### <a name="remarks"></a>Uwagi

Zestaw rekordów używa tego ciągu do ograniczania (lub filtrowania) rekordów wybieranych podczas `Open` wywołania lub `Requery` . Jest to przydatne w przypadku wybierania podzestawu rekordów, takich jak "Wszyscy sprzedawcy z uwzględnieniem Kalifornii" ("State = CA"). Składnia ODBC SQL dla klauzuli **WHERE** to

`WHERE search-condition`

Należy zauważyć, że w ciągu nie są uwzględniane słowa kluczowego **WHERE** . Środowisko to zapewnia.

Możesz również Sparametryzuj swój ciąg filtru, umieszczając w nim symbole zastępcze "", deklarując element członkowski danych parametru w klasie dla każdego symbolu zastępczego i przekazując parametry do zestawu rekordów w czasie wykonywania. Pozwala to utworzyć filtr w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [zestaw rekordów artykułów: parametryzacja a zestaw rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

Aby uzyskać więcej informacji na temat klauzul SQL **WHERE** , zapoznaj się z artykułem [SQL](../../data/odbc/sql.md). Aby uzyskać więcej informacji o wybieraniu i filtrowaniu rekordów, zobacz [zestaw rekordów artykułów: filtrowanie rekordów (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#30](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]

## <a name="crecordsetm_strsort"></a><a name="m_strsort"></a>CRecordset:: m_strSort

Po utworzeniu obiektu zestawu rekordów, ale przed wywołaniem jego `Open` funkcji składowej, należy użyć tego elementu członkowskiego danych do przechowywania `CString` zawierającej klauzulę **order by** języka SQL.

### <a name="remarks"></a>Uwagi

Zestaw rekordów używa tego ciągu do sortowania rekordów wybieranych podczas `Open` `Requery` wywołania lub. Za pomocą tej funkcji można sortować zestaw rekordów dla jednej lub wielu kolumn. Składnia ODBC SQL dla klauzuli **order by** jest

`ORDER BY sort-specification [, sort-specification]...`

gdzie sortowanie — specyfikacja jest liczbą całkowitą lub kolumną. Można również określić kolejność rosnącą lub malejącą (kolejność jest rosnąca domyślnie) przez dołączenie "ASC" lub "DESC" do listy kolumn w ciągu sortowania. Wybrane rekordy są sortowane najpierw według pierwszej kolumny na liście, a następnie według drugiej itd. Na przykład można zamówić zestaw rekordów "Customers" według nazwiska, a następnie imię. Liczba kolumn, które można wyświetlić, zależy od źródła danych. Aby uzyskać więcej informacji, zobacz Windows SDK.

Należy pamiętać, że w ciągu nie są uwzględniane słowa kluczowe **order by** . Środowisko to zapewnia.

Aby uzyskać więcej informacji na temat klauzul SQL, zobacz artykuł [SQL](../../data/odbc/sql.md). Aby uzyskać więcej informacji na temat sortowania rekordów, zobacz [zestaw rekordów artykułów: sortowanie rekordów (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#31](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]

## <a name="crecordsetmove"></a><a name="move"></a>CRecordset:: Move

Przenosi wskaźnik bieżącego rekordu w zestawie rekordów, do przodu lub do tyłu.

```
virtual void Move(
    long nRows,
    WORD wFetchType = SQL_FETCH_RELATIVE);
```

### <a name="parameters"></a>Parametry

*nRows*<br/>
Liczba wierszy do przeniesienia do przodu lub do tyłu. Wartości dodatnie przesuwają się w przód, w kierunku końca zestawu rekordów. Wartości ujemne przesuwają się do tyłu, w kierunku początku.

*wFetchType*<br/>
Określa zestaw wierszy, który `Move` będzie pobierany. Aby uzyskać szczegółowe informacje, zobacz uwagi.

### <a name="remarks"></a>Uwagi

W przypadku przekazania wartości 0 dla *nrows*program `Move` odświeża bieżący rekord; zakończy `Move` wszystkie bieżące `AddNew` lub `Edit` w trybie i przywróci wartość bieżącego rekordu przed `AddNew` lub `Edit` .

> [!NOTE]
> Podczas przechodzenia przez zestaw rekordów nie można pominąć usuniętych rekordów. Aby uzyskać więcej informacji, zobacz [CRecordset:: IsDeleted](#isdeleted) . Po otwarciu `CRecordset` z `skipDeletedRecords` zestawem opcji `Move` Asserts, jeśli parametr *nrows* ma wartość 0. Takie zachowanie zapobiega odświeżeniu wierszy, które są usuwane przez inne aplikacje klienckie przy użyciu tych samych danych. Zobacz *dwOption* parametr in [Open](#open) , aby uzyskać opis `skipDeletedRecords` .

`Move`Zmienia położenie zestawu rekordów według zestawów wierszy. Na podstawie wartości parametrów *nrows* i *wFetchType* `Move` Pobiera odpowiedni zestaw wierszy, a następnie tworzy pierwszy rekord w tym zestawie wierszy jako bieżący rekord. Jeśli nie zaimplementowano pobierania wierszy zbiorczych, rozmiar zestawu wierszy będzie zawsze 1. Podczas pobierania zestawu wierszy `Move` bezpośrednio wywołuje funkcję elementu członkowskiego [CheckRowsetError](#checkrowseterror) w celu obsługi wszystkich błędów wynikających z pobierania.

W zależności od przekazanych wartości `Move` jest równoważne z innymi `CRecordset` funkcjami składowymi. W szczególności wartość *wFetchType* może wskazywać funkcję członkowską, która jest bardziej intuicyjna i często preferowaną metodą przeniesienia bieżącego rekordu.

Poniższa tabela zawiera listę możliwych wartości dla *wFetchType*, zestaw wierszy `Move` pobieranych na podstawie *wFetchType* i *nrows*, a także dowolną równoważną funkcję członkowską odpowiadającą *wFetchType*.

|wFetchType|Zestaw wierszy pobranych|Równoważna funkcja członkowska|
|----------------|--------------------|--------------------------------|
|SQL_FETCH_RELATIVE (wartość domyślna)|Zestaw wierszy rozpoczyna *nrows* wierszy z pierwszego wiersza w bieżącym zestawie wierszy.||
|SQL_FETCH_NEXT|Następny zestaw wierszy; *nrows* jest ignorowana.|[Element](#movenext)|
|SQL_FETCH_PRIOR|Poprzedni zestaw wierszy; *nrows* jest ignorowana.|[MovePrev](#moveprev)|
|SQL_FETCH_FIRST|Pierwszy zestaw wierszy w zestawie rekordów; *nrows* jest ignorowana.|[MoveFirst](#movefirst)|
|SQL_FETCH_LAST|Ostatni kompletny zestaw wierszy w zestawie rekordów; *nrows* jest ignorowana.|[MoveLast](#movelast)|
|SQL_FETCH_ABSOLUTE|Jeśli *nRows* > 0, zestaw wierszy rozpoczyna *nrows* wierszy od początku zestawu rekordów. Jeśli *nRows* < 0, zestaw wierszy rozpoczyna *nrows* wierszy od końca zestawu rekordów. Jeśli *nrows* = 0, zwracany jest warunek początku pliku (BOF).|[SetAbsolutePosition](#setabsoluteposition)|
|SQL_FETCH_BOOKMARK|Zestaw wierszy zaczynający się od wiersza, którego wartość zakładki odpowiada *nrows*.|[SetBookmark](#setbookmark)|

> [!NOTE]
> Dla zestawów rekordów tylko do przodu `Move` jest prawidłowy tylko z wartością SQL_FETCH_NEXT dla *wFetchType*.

> [!CAUTION]
> Wywołanie `Move` zgłasza wyjątek, jeśli zestaw rekordów nie zawiera żadnych rekordów. Aby określić, czy zestaw rekordów zawiera jakiekolwiek rekordy, wywołaj [IsBOF](#isbof) i [IsEOF](#iseof).

> [!NOTE]
> Jeśli przewiniesz poza początkową lub końcem zestawu rekordów ( `IsBOF` lub `IsEOF` zwraca wartość różną od zera), wywołanie `Move` funkcji będzie prawdopodobnie zgłosić `CDBException` . Na przykład, jeśli `IsEOF` zwraca wartość różną od zera i nie `IsBOF` , `MoveNext` zgłosi wyjątek, ale `MovePrev` nie będzie.

> [!NOTE]
> Jeśli wywołasz `Move` , gdy bieżący rekord zostanie zaktualizowany lub dodany, aktualizacje zostaną utracone bez ostrzeżenia.

Aby uzyskać więcej informacji na temat nawigowania po zestawach rekordów, zobacz [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) i [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Aby uzyskać powiązane informacje, zobacz Funkcja ODBC API `SQLExtendedFetch` w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#28](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]

## <a name="crecordsetmovefirst"></a><a name="movefirst"></a>CRecordset:: MoveFirst

Tworzy pierwszy rekord w pierwszym zestawie wierszy w bieżącym rekordzie.

```cpp
void MoveFirst();
```

### <a name="remarks"></a>Uwagi

Bez względu na to, czy zaimplementowano pobieranie wierszy zbiorczych, zawsze będzie to pierwszy rekord w zestawie rekordów.

Nie ma potrzeby wywoływania `MoveFirst` natychmiast po otwarciu zestawu rekordów. W tym momencie pierwszy rekord (jeśli istnieje) jest automatycznie bieżącym rekordem.

> [!NOTE]
> Ta funkcja członkowska nie jest prawidłowa dla zestawów rekordów tylko do przodu.

> [!NOTE]
> Podczas przechodzenia przez zestaw rekordów nie można pominąć usuniętych rekordów. Aby uzyskać szczegółowe informacje, zobacz funkcję elementu członkowskiego [isdelete](#isdeleted) .

> [!CAUTION]
> Wywołanie którejkolwiek z `Move` funkcji zgłasza wyjątek, jeśli zestaw rekordów nie zawiera żadnych rekordów. Aby określić, czy zestaw rekordów zawiera jakiekolwiek rekordy, wywołaj `IsBOF` i `IsEOF` .

> [!NOTE]
> Jeśli `Move` podczas aktualizowania lub dodawania bieżącego rekordu zostanie wywołana jakakolwiek funkcja, aktualizacje zostaną utracone bez ostrzeżenia.

Aby uzyskać więcej informacji na temat nawigowania po zestawach rekordów, zobacz [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) i [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Przykład

  Zobacz przykład dla [IsBOF](#isbof).

## <a name="crecordsetmovelast"></a><a name="movelast"></a>CRecordset:: MoveLast

Tworzy pierwszy rekord w ostatnim kompletnym zestawie wierszy w bieżącym rekordzie.

```cpp
void MoveLast();
```

### <a name="remarks"></a>Uwagi

Jeśli nie zaimplementowano pobierania wierszy zbiorczych, zestaw rekordów ma rozmiar zestawu wierszy 1, więc `MoveLast` po prostu przenosi do ostatniego rekordu w zestawie rekordów.

> [!NOTE]
> Ta funkcja członkowska nie jest prawidłowa dla zestawów rekordów tylko do przodu.

> [!NOTE]
> Podczas przechodzenia przez zestaw rekordów nie można pominąć usuniętych rekordów. Aby uzyskać szczegółowe informacje, zobacz funkcję elementu członkowskiego [isdelete](#isdeleted) .

> [!CAUTION]
> Wywołanie którejkolwiek z `Move` funkcji zgłasza wyjątek, jeśli zestaw rekordów nie zawiera żadnych rekordów. Aby określić, czy zestaw rekordów zawiera jakiekolwiek rekordy, wywołaj `IsBOF` i `IsEOF` .

> [!NOTE]
> Jeśli `Move` podczas aktualizowania lub dodawania bieżącego rekordu zostanie wywołana jakakolwiek funkcja, aktualizacje zostaną utracone bez ostrzeżenia.

Aby uzyskać więcej informacji na temat nawigowania po zestawach rekordów, zobacz [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) i [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Przykład

  Zobacz przykład dla [IsBOF](#isbof).

## <a name="crecordsetmovenext"></a><a name="movenext"></a>CRecordset:: MoveNext

Tworzy pierwszy rekord w następnym zestawie wierszy w bieżącym rekordzie.

```cpp
void MoveNext();
```

### <a name="remarks"></a>Uwagi

Jeśli nie zaimplementowano pobierania wierszy zbiorczych, zestaw rekordów ma rozmiar zestawu wierszy 1, więc `MoveNext` po prostu przenosi się do następnego rekordu.

> [!NOTE]
> Podczas przechodzenia przez zestaw rekordów nie można pominąć usuniętych rekordów. Aby uzyskać szczegółowe informacje, zobacz funkcję elementu członkowskiego [isdelete](#isdeleted) .

> [!CAUTION]
> Wywołanie którejkolwiek z `Move` funkcji zgłasza wyjątek, jeśli zestaw rekordów nie zawiera żadnych rekordów. Aby określić, czy zestaw rekordów zawiera jakiekolwiek rekordy, wywołaj `IsBOF` i `IsEOF` .

> [!NOTE]
> Zaleca się również wywołanie `IsEOF` przed wywołaniem metody `MoveNext` . Na przykład, jeśli przewiniesz poza końcem zestawu rekordów, `IsEOF` zwróci wartość różną od zera; następne wywołanie `MoveNext` spowodowałaby zgłoszenie wyjątku.

> [!NOTE]
> Jeśli `Move` podczas aktualizowania lub dodawania bieżącego rekordu zostanie wywołana jakakolwiek funkcja, aktualizacje zostaną utracone bez ostrzeżenia.

Aby uzyskać więcej informacji na temat nawigowania po zestawach rekordów, zobacz [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) i [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Przykład

  Zobacz przykład dla [IsBOF](#isbof).

## <a name="crecordsetmoveprev"></a><a name="moveprev"></a>CRecordset:: MovePrev

Tworzy pierwszy rekord w poprzednim zestawie wierszy w bieżącym rekordzie.

```cpp
void MovePrev();
```

### <a name="remarks"></a>Uwagi

Jeśli nie zaimplementowano pobierania wierszy zbiorczych, zestaw rekordów ma rozmiar zestawu wierszy 1, więc `MovePrev` po prostu przenosi się do poprzedniego rekordu.

> [!NOTE]
> Ta funkcja członkowska nie jest prawidłowa dla zestawów rekordów tylko do przodu.

> [!NOTE]
> Podczas przechodzenia przez zestaw rekordów nie można pominąć usuniętych rekordów. Aby uzyskać szczegółowe informacje, zobacz funkcję elementu członkowskiego [isdelete](#isdeleted) .

> [!CAUTION]
> Wywołanie którejkolwiek z `Move` funkcji zgłasza wyjątek, jeśli zestaw rekordów nie zawiera żadnych rekordów. Aby określić, czy zestaw rekordów zawiera jakiekolwiek rekordy, wywołaj `IsBOF` i `IsEOF` .

> [!NOTE]
> Zaleca się również wywołanie `IsBOF` przed wywołaniem metody `MovePrev` . Na przykład, jeśli przewiniesz przed początkiem zestawu rekordów, `IsBOF` zwróci wartość różną od zera; następne wywołanie `MovePrev` spowodowałaby zgłoszenie wyjątku.

> [!NOTE]
> Jeśli `Move` podczas aktualizowania lub dodawania bieżącego rekordu zostanie wywołana jakakolwiek funkcja, aktualizacje zostaną utracone bez ostrzeżenia.

Aby uzyskać więcej informacji na temat nawigowania po zestawach rekordów, zobacz [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) i [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Przykład

  Zobacz przykład dla [IsBOF](#isbof).

## <a name="crecordsetonsetoptions"></a><a name="onsetoptions"></a>CRecordset:: onoptions

Wywołuje się, by ustawić opcje (używane przy wyborze) dla określonej instrukcji ODBC.

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*hstmt*<br/>
HSTMT instrukcji ODBC, której opcje mają być ustawione.

### <a name="remarks"></a>Uwagi

Wywołanie `OnSetOptions` opcji Set (używane przy wyborze) dla określonej instrukcji ODBC. Struktura wywołuje tę funkcję elementu członkowskiego, aby ustawić opcje początkowe zestawu rekordów. `OnSetOptions`Określa wsparcie dla źródła danych dla kursorów przewijalnych oraz dla współbieżności kursora i ustawia odpowiednie opcje zestawu rekordów. ( `OnSetOptions` Używany do operacji wyboru `OnSetUpdateOptions` jest używany na potrzeby operacji aktualizacji).

Przesłoń `OnSetOptions` , aby ustawić opcje specyficzne dla sterownika lub źródła danych. Na przykład, jeśli źródło danych obsługuje otwieranie do wyłącznego dostępu, można przesłonić, `OnSetOptions` Aby skorzystać z tej możliwości.

Aby uzyskać więcej informacji na temat kursorów, zobacz artykuł [ODBC](../../data/odbc/odbc-basics.md).

## <a name="crecordsetonsetupdateoptions"></a><a name="onsetupdateoptions"></a>CRecordset::OnSetUpdateOptions

Wywołuje się, by ustawić opcje (używane podczas aktualizacji) dla określonej instrukcji ODBC.

```
virtual void OnSetUpdateOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*hstmt*<br/>
HSTMT instrukcji ODBC, której opcje mają być ustawione.

### <a name="remarks"></a>Uwagi

Wywołanie `OnSetUpdateOptions` opcji Set (używane podczas aktualizacji) dla określonej instrukcji ODBC. Struktura wywołuje tę funkcję członkowską po utworzeniu HSTMT do aktualizowania rekordów w zestawie rekordów. ( `OnSetOptions` Używany do operacji wyboru `OnSetUpdateOptions` jest używany do operacji aktualizacji). `OnSetUpdateOptions` określa obsługę źródła danych dla przewijanych kursorów i współbieżność kursora i ustawia odpowiednie opcje zestawu rekordów.

Przesłoń, `OnSetUpdateOptions` Aby ustawić opcje instrukcji ODBC, zanim ta instrukcja zostanie użyta w celu uzyskania dostępu do bazy danych.

Aby uzyskać więcej informacji na temat kursorów, zobacz artykuł [ODBC](../../data/odbc/odbc-basics.md).

## <a name="crecordsetopen"></a><a name="open"></a>CRecordset:: Open

Otwiera zestaw rekordów przez pobranie tabeli lub wykonanie zapytania, które reprezentuje zestaw rekordów.

```
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,
    LPCTSTR lpszSQL = NULL,
    DWORD dwOptions = none);
```

### <a name="parameters"></a>Parametry

*nOpenType*<br/>
Zaakceptuj wartość domyślną, AFX_DB_USE_DEFAULT_TYPE lub użyj jednej z następujących wartości z `enum OpenType` :

- `CRecordset::dynaset`Zestaw rekordów z przewijaniem dwukierunkowym. Członkostwo i porządkowanie rekordów są określane podczas otwierania zestawu rekordów, ale zmiany wprowadzone przez innych użytkowników do wartości danych są widoczne po operacji pobierania. Zestawy dynamiczne są również znane jako zestawy rekordów oparte na zestawach kluczy.

- `CRecordset::snapshot`Statyczny zestaw rekordów z przewijaniem dwukierunkowym. Członkostwo i porządkowanie rekordów są określane podczas otwierania zestawu rekordów; wartości danych są określane podczas pobierania rekordów. Zmiany wprowadzone przez innych użytkowników nie są widoczne, dopóki zestaw rekordów nie zostanie zamknięty i ponownie otwarty.

- `CRecordset::dynamic`Zestaw rekordów z przewijaniem dwukierunkowym. Zmiany wprowadzone przez innych użytkowników do członkostwa, sortowania i wartości danych są widoczne po operacji pobierania. Należy zauważyć, że wiele sterowników ODBC nie obsługuje tego typu zestawu rekordów.

- `CRecordset::forwardOnly`Zestaw rekordów tylko do odczytu z przewijaniem do przodu.

   W przypadku `CRecordset` , wartość domyślna to `CRecordset::snapshot` . Domyślny mechanizm wartości umożliwia kreatorom Visual C++ współpracującie z ODBC `CRecordset` i DAO `CDaoRecordset` , które mają różne ustawienia domyślne.

Aby uzyskać więcej informacji na temat tych typów zestawów rekordów, zobacz [zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)artykułu. Aby uzyskać powiązane informacje, zobacz artykuł "Używanie kursorów bloku i przewijania" w Windows SDK.

> [!CAUTION]
> Jeśli żądany typ nie jest obsługiwany, platforma zgłasza wyjątek.

*lpszSQL*<br/>
Wskaźnik ciągu zawierający jedną z następujących wartości:

- Wskaźnik o wartości NULL.

- Nazwa tabeli.

- Instrukcja **SELECT** języka SQL (opcjonalnie z klauzulą **WHERE** lub Order **by** ).

- Instrukcja **call** określająca nazwę wstępnie zdefiniowanego zapytania (procedura składowana). Należy zachować ostrożność, aby nie wstawiać odstępów między nawiasami klamrowymi i słowem kluczowym **call** .

Aby uzyskać więcej informacji na temat tego ciągu, zobacz tabelę i Omówienie roli ClassWizard w sekcji [uwagi](#remarks) .

> [!NOTE]
> Kolejność kolumn w zestawie wyników musi być zgodna z kolejnością wywołań funkcji RFX lub bulk RFX w przesłonięciu funkcji [DoFieldExchange](#dofieldexchange) lub [DoBulkFieldExchange](#dobulkfieldexchange) .

*dwOptions*<br/>
Maska bitów, która może określać kombinację wartości wymienionych poniżej. Niektóre z nich wykluczają się wzajemnie. Wartość domyślna to **none**.

- `CRecordset::none`Brak ustawionych opcji. Ta wartość parametru wzajemnie się wykluczają z innymi wartościami. Domyślnie zestaw rekordów można aktualizować za pomocą operacji [Edytuj](#edit) lub [Usuń](#delete) i umożliwia dołączanie nowych rekordów przy użyciu [parametru AddNew](#addnew). Możliwość aktualizacji zależy od źródła danych, a także od wybranej opcji *nOpenType* . Optymalizacja dodatków zbiorczych jest niedostępna. Pobieranie wierszy zbiorczych nie zostanie zaimplementowane. Usunięte rekordy nie zostaną pominięte podczas nawigowania po zestawie rekordów. Zakładki nie są dostępne. Zaimplementowano automatyczne sprawdzanie pól zanieczyszczone.

- `CRecordset::appendOnly`Nie dopuszczaj `Edit` ani nie `Delete` w zestawie rekordów. `AddNew`Tylko Zezwalaj. Ta opcja jest wzajemnie wykluczana z `CRecordset::readOnly` .

- `CRecordset::readOnly`Otwórz zestaw rekordów jako tylko do odczytu. Ta opcja jest wzajemnie wykluczana z `CRecordset::appendOnly` .

- `CRecordset::optimizeBulkAdd`Aby zoptymalizować Dodawanie wielu rekordów jednocześnie, użyj przygotowanej instrukcji SQL. Ma zastosowanie tylko wtedy, gdy nie jest używana funkcja interfejsu API ODBC `SQLSetPos` do aktualizowania zestawu rekordów. Pierwsza Aktualizacja określa, które pola są oznaczone jako zanieczyszczone. Ta opcja jest wzajemnie wykluczana z `CRecordset::useMultiRowFetch` .

- `CRecordset::useMultiRowFetch`Zaimplementuj pobieranie wierszy zbiorczych, aby umożliwić pobieranie wielu wierszy w jednej operacji pobierania. Jest to zaawansowana funkcja zaprojektowana w celu zwiększenia wydajności. jednak wymiana pól rekordów zbiorczych nie jest obsługiwana przez ClassWizard. Ta opcja jest wzajemnie wykluczana z `CRecordset::optimizeBulkAdd` . Należy pamiętać, że jeśli określisz `CRecordset::useMultiRowFetch` , opcja `CRecordset::noDirtyFieldCheck` zostanie włączona automatycznie (podwójne buforowanie nie będzie dostępne); w zestawach rekordów tylko do przodu opcja `CRecordset::useExtendedFetch` zostanie włączona automatycznie. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

- `CRecordset::skipDeletedRecords`Pomiń wszystkie usunięte rekordy podczas nawigowania po zestawie rekordów. Spowoduje to spowolnienie działania niektórych względnych pobrań. Ta opcja nie jest prawidłowa w zestawach rekordów tylko do przodu. Jeśli wywołasz polecenie [Move](#move) z parametrem *nrows* ustawionym na 0, a `CRecordset::skipDeletedRecords` zestaw opcji, `Move` zostanie zatwierdzona. Należy pamiętać, że `CRecordset::skipDeletedRecords` jest podobny do *opakowania sterownika*, co oznacza, że usunięte wiersze są usuwane z zestawu rekordów. Jednak jeśli pakiety sterowników są rejestrowane, spowoduje to pominięcie tylko tych rekordów, które zostały usunięte. nie spowoduje to pominięcia rekordów usuniętych przez innych użytkowników, gdy zestaw rekordów jest otwarty. `CRecordset::skipDeletedRecords`spowoduje pominięcie wierszy usuniętych przez innych użytkowników.

- `CRecordset::useBookmarks`Może używać zakładek w zestawie rekordów, jeśli jest obsługiwany. Zakładki spowalniają pobieranie danych, ale poprawiają wydajność nawigacji po danych. Nieprawidłowe w zestawach rekordów tylko do przodu. Aby uzyskać więcej informacji, zobacz [zestaw rekordów artykułów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

- `CRecordset::noDirtyFieldCheck`Wyłącz automatyczne sprawdzanie zanieczyszczonych pól (podwójne buforowanie). Poprawi to wydajność; należy jednak ręcznie oznaczyć pola jako zanieczyszczone przez wywołanie `SetFieldDirty` `SetFieldNull` funkcji i. Należy zauważyć, że podwójne buforowanie w klasie `CRecordset` jest podobne do podwójnego buforowania w klasie `CDaoRecordset` . Jednak w `CRecordset` systemie nie można włączyć podwójnego buforowania dla pojedynczych pól. można je włączyć dla wszystkich pól lub wyłączyć dla wszystkich pól. Należy pamiętać, że jeśli określisz opcję `CRecordset::useMultiRowFetch` , `CRecordset::noDirtyFieldCheck` zostanie ona włączona automatycznie, ale nie będzie `SetFieldDirty` `SetFieldNull` można jej używać w zestawach rekordów, które implementują pobieranie wierszy zbiorczych.

- `CRecordset::executeDirect`Nie należy używać przygotowanej instrukcji języka SQL. Aby zwiększyć wydajność, należy określić tę opcję, jeśli `Requery` funkcja członkowska nigdy nie zostanie wywołana.

- `CRecordset::useExtendedFetch`Implementuj `SQLExtendedFetch` zamiast `SQLFetch` . Jest to przeznaczone do implementowania pobierania wierszy zbiorczych w zestawach rekordów tylko do przodu. Jeśli określisz opcję `CRecordset::useMultiRowFetch` dla zestawu rekordów tylko do przodu, zostanie on `CRecordset::useExtendedFetch` włączony automatycznie.

- `CRecordset::userAllocMultiRowBuffers`Użytkownik przydzieli bufory magazynu dla danych. Tej opcji należy używać w połączeniu z usługą `CRecordset::useMultiRowFetch` , jeśli chcesz przydzielić własny magazyn; w przeciwnym razie platforma automatycznie przydzieli konieczny magazyn. Aby uzyskać więcej informacji, zobacz [zestaw rekordów artykułów: zbiorcze pobieranie rekordów (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Należy zauważyć, że określenie `CRecordset::userAllocMultiRowBuffers` bez określenia `CRecordset::useMultiRowFetch` spowoduje niepomyślne potwierdzenie.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli `CRecordset` obiekt został pomyślnie otwarty; w przeciwnym razie 0, jeśli [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open) (jeśli wywoływana) zwróci wartość 0.

### <a name="remarks"></a>Uwagi

Należy wywołać tę funkcję elementu członkowskiego, aby uruchomić zapytanie zdefiniowane przez zestaw rekordów. Przed wywołaniem `Open` należy skonstruować obiekt zestawu rekordów.

Połączenie tego zestawu rekordów ze źródłem danych zależy od sposobu konstruowania zestawu rekordów przed wywołaniem `Open` . Jeśli przekażesz obiekt [CDatabase](../../mfc/reference/cdatabase-class.md) do konstruktora zestawu rekordów, który nie został połączony ze źródłem danych, ta funkcja elementu członkowskiego używa [GetDefaultConnect](#getdefaultconnect) do próby otwarcia obiektu bazy danych. Jeśli przekażesz wartość NULL do konstruktora zestawu rekordów, Konstruktor konstruuje `CDatabase` obiekt dla Ciebie i `Open` spróbuje połączyć obiekt bazy danych. Aby uzyskać szczegółowe informacje na temat zamykania zestawu rekordów i połączenia w różnych warunkach, zobacz [Zamknij](#close).

> [!NOTE]
> Dostęp do źródła danych za pomocą `CRecordset` obiektu jest zawsze udostępniany. W przeciwieństwie do `CDaoRecordset` klasy, nie można użyć `CRecordset` obiektu, aby otworzyć źródło danych z wyłącznym dostępem.

W przypadku wywołania `Open` , zapytania, zazwyczaj instrukcji **SELECT** języka SQL, program wybiera rekordy na podstawie kryteriów przedstawionych w poniższej tabeli.

|Wartość parametru lpszSQL|Wybrane rekordy są określane przez|Przykład|
|------------------------------------|----------------------------------------|-------------|
|NULL|Ciąg zwracany przez `GetDefaultSQL` .||
|Nazwa tabeli SQL|Wszystkie kolumny listy tabeli w `DoFieldExchange` lub `DoBulkFieldExchange` .|`"Customer"`|
|Nazwa wstępnie zdefiniowanego zapytania (procedura składowana)|Kolumny, które mają zostać zwrócone przez zapytanie.|`"{call OverDueAccts}"`|
|**Wybierz** kolumnę-list **z** listy tabel|Określone kolumny z określonych tabel.|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|

> [!CAUTION]
> Należy pamiętać, że w ciągu SQL nie są wstawiane dodatkowe odstępy. Na przykład po wstawieniu odstępu między nawiasem klamrowym i słowem kluczowym **wywołania** MFC będzie błędnie interpretować ciąg SQL jako nazwę tabeli i dołączyć go do instrukcji **SELECT** , co spowoduje wystąpienie wyjątku. Podobnie, jeśli wstępnie zdefiniowane zapytanie używa parametru wyjściowego, nie należy wstawiać odstępów między nawiasem klamrowym i symbolem "". Na koniec nie należy wstawiać odstępów przed nawiasem klamrowym w instrukcji **call** lub przed słowem kluczowym **SELECT** w instrukcji **SELECT** .

Typową procedurą jest przekazanie wartości NULL do `Open` ; w tym przypadku `Open` wywołania [GetDefaultSQL](#getdefaultsql). Jeśli używasz `CRecordset` klasy pochodnej, `GetDefaultSQL` nadaje nazwę tabeli, która została określona w ClassWizard. Zamiast tego można określić inne informacje w `lpszSQL` parametrze.

Niezależnie od tego, co zostało przekazane, `Open` konstruuje końcowy ciąg SQL dla zapytania (ciąg może zawierać klauzule **WHERE** i **order by** , które są dołączone do `lpszSQL` przekazanego ciągu), a następnie wykonuje zapytanie. Można przeanalizować skonstruowany ciąg przez wywołanie [GetSQL](#getsql) po wywołaniu `Open` . Aby uzyskać dodatkowe informacje na temat sposobu tworzenia przez zestaw rekordów instrukcji SQL i wybierania rekordów, zobacz [zestaw rekordów artykułów: jak zestawy rekordów wybierają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

Elementy członkowskie danych pól klasy zestaw rekordów są powiązane z kolumnami wybranych danych. Jeśli wszystkie rekordy są zwracane, pierwszy rekord zostanie bieżącym rekordem.

Jeśli chcesz ustawić opcje dla zestawu rekordów, takie jak filtr lub sortowanie, określ je po utworzeniu obiektu zestawu rekordów, ale przed wywołaniem `Open` . Jeśli chcesz odświeżyć rekordy w zestawie rekordów po tym, jak zestaw rekordów jest już otwarty, należy wywołać polecenie [PonówKwerendę](#requery).

Aby uzyskać więcej informacji, w tym o dodatkowych przykładach, zobacz [zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md), [zestaw rekordów: jak zestawy rekordów wybierają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)i [zestaw rekordów: Tworzenie i zamykanie zestawów rekordów (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

### <a name="example"></a>Przykład

Poniższe przykłady kodu przedstawiają różne formy `Open` wywołania.

[!code-cpp[NVC_MFCDatabase#16](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]

## <a name="crecordsetrefreshrowset"></a><a name="refreshrowset"></a>CRecordset::RefreshRowset

Aktualizuje dane i stan dla wiersza w bieżącym zestawie wierszy.

```cpp
void RefreshRowset(
    WORD wRow,
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>Parametry

*wRow*<br/>
Pozycja jednego wiersza w bieżącym zestawie wierszy. Ta wartość może się wahać od zera do rozmiaru zestawu wierszy.

*wLockType*<br/>
Wartość wskazująca, jak zablokować wiersz po jego odświeżeniu. Aby uzyskać szczegółowe informacje, zobacz uwagi.

### <a name="remarks"></a>Uwagi

W przypadku przekazania wartości zero dla *wRow*, każdy wiersz w zestawie wierszy zostanie odświeżony.

Aby użyć `RefreshRowset` , musisz mieć zaimplementowane pobieranie wierszy zbiorczych przez określenie `CRecordset::useMulitRowFetch` opcji w funkcji [Open](#open) member.

`RefreshRowset`wywołuje funkcję interfejsu API ODBC `SQLSetPos` . Parametr *wLockType* określa stan blokady wiersza po `SQLSetPos` wykonaniu. W poniższej tabeli opisano możliwe wartości dla *wLockType*.

|wLockType|Opis|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE (wartość domyślna)|Sterownik lub źródło danych gwarantuje, że wiersz znajduje się w tym samym stanie zablokowanym lub odblokowanym, ponieważ wcześniej `RefreshRowset` został wywołany.|
|SQL_LOCK_EXCLUSIVE|Sterownik lub źródło danych blokuje wiersz w trybie wyłączności. Nie wszystkie źródła danych obsługują ten typ blokady.|
|SQL_LOCK_UNLOCK|Sterownik lub źródło danych odblokowuje wiersz. Nie wszystkie źródła danych obsługują ten typ blokady.|

Aby uzyskać więcej informacji na temat `SQLSetPos` , zobacz Windows SDK. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetrequery"></a><a name="requery"></a>CRecordset:: Requery

Ponownie kompiluje (odświeża) zestaw rekordów.

```
virtual BOOL Requery();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli zestaw rekordów został pomyślnie odbudowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli wszystkie rekordy są zwracane, pierwszy rekord zostanie bieżącym rekordem.

Aby zestaw rekordów odzwierciedlał operacje dodawania i usuwania, które są używane przez użytkownika lub innych użytkowników do źródła danych, należy ponownie skompilować zestaw rekordów, wywołując metodę `Requery` . Jeśli zestaw rekordów jest dynamiczny, automatycznie odzwierciedla aktualizacje, które zostały wprowadzone przez użytkownika lub innych użytkowników do istniejących rekordów (ale nie do dodania). Jeśli zestaw rekordów jest migawką, należy wywołać, `Requery` aby odzwierciedlić zmiany wprowadzone przez innych użytkowników, a także Dodatki i usunięcia.

W przypadku zestawu dynamicznego lub migawki Wywołaj `Requery` dowolną godzinę, w której chcesz skompilować zestaw rekordów przy użyciu nowego filtru lub sortowania lub nowych wartości parametrów. Ustaw nowy filtr lub Właściwość sortowania, przypisując nowe wartości do `m_strFilter` i `m_strSort` przed wywołaniem `Requery` . Ustaw nowe parametry, przypisując nowe wartości do elementów członkowskich danych przed wywołaniem `Requery` . Jeśli filtry i ciągi sortowania nie są zmieniane, można ponownie użyć zapytania, co zwiększa wydajność.

Jeśli próba odbudowy zestawu rekordów nie powiedzie się, zestaw rekordów zostanie zamknięty. Przed wywołaniem można `Requery` określić, czy zestaw rekordów może być badany przez wywołanie `CanRestart` funkcji elementu członkowskiego. `CanRestart`nie gwarantuje, że powiedzie `Requery` się.

> [!CAUTION]
> Wywołanie `Requery` tylko po wywołaniu metody [Open](#open).

### <a name="example"></a>Przykład

Ten przykład odbudowuje zestaw rekordów, aby zastosować inny porządek sortowania.

[!code-cpp[NVC_MFCDatabase#29](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]

## <a name="crecordsetsetabsoluteposition"></a><a name="setabsoluteposition"></a>CRecordset::SetAbsolutePosition

Ustawia zestaw rekordów dla rekordu odpowiadającego określonemu numerowi rekordu.

```cpp
void SetAbsolutePosition(long nRows);
```

### <a name="parameters"></a>Parametry

*nRows*<br/>
Jednowymiarowa pozycja porządkowa bieżącego rekordu w zestawie rekordów.

### <a name="remarks"></a>Uwagi

`SetAbsolutePosition`przenosi wskaźnik bieżącego rekordu w oparciu o tę pozycję porządkową.

> [!NOTE]
> Ta funkcja członkowska nie jest prawidłowa w zestawach rekordów tylko do przodu.

W przypadku zestawów rekordów ODBC ustawienie pozycjonowania bezwzględnego (1) odnosi się do pierwszego rekordu w zestawie rekordów; ustawienie wartości 0 oznacza pozycję początku pliku (BOF).

Wartości ujemne można także przekazać do `SetAbsolutePosition` . W takim przypadku pozycja zestawu rekordów jest oceniana na podstawie końca zestawu rekordów. Na przykład `SetAbsolutePosition( -1 )` przenosi bieżący wskaźnik rekordu do ostatniego rekordu w zestawie rekordów.

> [!NOTE]
> Pozycja absolutna nie jest przeznaczona do użycia jako numer rekordu zastępczego. Zakładki są nadal zalecanym sposobem zachowywania i powrotu do danego położenia, ponieważ pozycja rekordu zmienia się po usunięciu poprzedzających rekordów. Ponadto nie można zagwarantować, że dany rekord będzie miał tę samą absolutną pozycję, jeśli zestaw rekordów zostanie ponownie utworzony, ponieważ kolejność poszczególnych rekordów w zestawie rekordów nie jest gwarantowana, chyba że zostanie utworzona za pomocą instrukcji SQL przy użyciu klauzuli **order by** .

Więcej informacji o nawigacji i zakładkach zestawu rekordów znajduje się w artykule [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) i [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

## <a name="crecordsetsetbookmark"></a><a name="setbookmark"></a>CRecordset:: SetBookmark

Umieszcza zestaw rekordów w rekordzie zawierającym określoną zakładkę.

```cpp
void SetBookmark(const CDBVariant& varBookmark);
```

### <a name="parameters"></a>Parametry

*varBookmark*<br/>
Odwołanie do obiektu [CDBVariant](../../mfc/reference/cdbvariant-class.md) zawierającego wartość zakładki dla określonego rekordu.

### <a name="remarks"></a>Uwagi

Aby określić, czy zakładki są obsługiwane w zestawie rekordów, [Wywołaj polecenie](#canbookmark). Aby zakładki były dostępne, jeśli są obsługiwane, należy ustawić `CRecordset::useBookmarks` opcję w parametrze *DwOptions* funkcji [Open](#open) member.

> [!NOTE]
> Jeśli zakładki są nieobsługiwane lub niedostępne, wywołanie `SetBookmark` spowoduje zgłoszenie wyjątku. Zakładki nie są obsługiwane w zestawach rekordów tylko do przodu.

Aby najpierw pobrać zakładkę dla bieżącego rekordu, wywołaj metodę [GetBookmark](#getbookmark), która zapisuje wartość zakładki w `CDBVariant` obiekcie. Później możesz powrócić do tego rekordu, wywołując `SetBookmark` przy użyciu wartości zapisanej zakładki.

> [!NOTE]
> Po pewnych operacjach zestawu rekordów należy sprawdzić trwałość zakładki przed wywołaniem `SetBookmark` . Na przykład jeśli pobrano zakładkę z `GetBookmark` , a następnie Wywołaj `Requery` , zakładka może nie być już prawidłowa. Wywołaj [CDatabase:: GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) , aby sprawdzić, czy można bezpiecznie wywołać `SetBookmark` .

Aby uzyskać więcej informacji o zakładkach i nawigowaniu po zestawach rekordów, zobacz [zestawy rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) i [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="crecordsetsetfielddirty"></a><a name="setfielddirty"></a>CRecordset::SetFieldDirty

Flaguje element członkowski danych pola zestawu rekordów jako zmieniony lub niezmieniony.

```cpp
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```

### <a name="parameters"></a>Parametry

*wa*<br/>
Zawiera adres elementu członkowskiego danych pola w zestawie rekordów lub wartości NULL. Jeśli wartość jest równa NULL, wszystkie elementy członkowskie danych pól w zestawie rekordów są oflagowane. (Wartość NULL C++ nie jest taka sama jak wartość null w terminologii bazy danych, co oznacza, że nie ma wartości ")".

*bDirty*<br/>
Ma wartość TRUE, jeśli element członkowski danych Field ma być oflagowany jako "zanieczyszczony" (zmieniony). W przeciwnym razie zwraca wartość FALSE, jeśli element członkowski danych pola ma być oflagowany jako "czysty" (niezmieniony).

### <a name="remarks"></a>Uwagi

Oznaczanie pól jako niezmienionych gwarantuje, że pole nie zostanie zaktualizowane i spowoduje zmniejszenie ruchu SQL.

> [!NOTE]
> Ta funkcja członkowska nie ma zastosowania w zestawach rekordów używających pobierania wierszy zbiorczych. Jeśli zaimplementowano pobieranie wierszy zbiorczych, `SetFieldDirty` spowoduje to nieudane potwierdzenie. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Struktura oznacza zmienione elementy członkowskie danych pola, aby upewnić się, że zostaną one zamienione na rekord w źródle danych przez mechanizm wymiany pól rekordów (RFX). Zmiana wartości pola na ogół ustawia pole jako zanieczyszczone automatycznie, więc rzadko trzeba będzie wywołać `SetFieldDirty` siebie, ale czasami warto upewnić się, że kolumny będą jawnie aktualizowane lub wstawiane niezależnie od tego, jaka wartość znajduje się w polu elementu członkowskiego danych.

> [!CAUTION]
> Wywołaj tę funkcję elementu członkowskiego tylko po wywołaniu metody [Edit](#edit) lub [AddNew](#addnew).

Użycie wartości NULL dla pierwszego argumentu funkcji spowoduje zastosowanie funkcji tylko do `outputColumn` pól, a nie `param` pól. Na przykład wywołanie

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

spowoduje ustawienie tylko `outputColumn` pól na null; nie `param` wpłynie to na pola.

Aby można było korzystać z `param` pól, należy podać rzeczywisty adres osoby `param` , na której ma być wykonywane działanie, na przykład:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

Oznacza to, że nie można ustawić `param` wartości null dla wszystkich pól, jak można z `outputColumn` polami.

## <a name="crecordsetsetfieldnull"></a><a name="setfieldnull"></a>CRecordset::SetFieldNull

Flaguje element członkowski danych pola zestawu rekordów jako null (w przypadku braku wartości) lub jako niebędący wartością null.

```cpp
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parametry

*wa*<br/>
Zawiera adres elementu członkowskiego danych pola w zestawie rekordów lub wartości NULL. Jeśli wartość jest równa NULL, wszystkie elementy członkowskie danych pól w zestawie rekordów są oflagowane. (Wartość NULL C++ nie jest taka sama jak wartość null w terminologii bazy danych, co oznacza, że nie ma wartości ")".

*bNull*<br/>
Różne od zera, jeśli element członkowski danych Field ma być oflagowany jako nieposiadający wartości (null). W przeciwnym razie wartość 0, jeśli element członkowski danych pola ma być oflagowany jako inny niż null.

### <a name="remarks"></a>Uwagi

Po dodaniu nowego rekordu do zestawu rekordów wszystkie elementy członkowskie danych pola są początkowo ustawiane na wartość null i oflagowane jako "zanieczyszczone" (zmienione). Gdy pobierasz rekord ze źródła danych, jego kolumny mają już wartości lub mają wartość null.

> [!NOTE]
> Nie wywołuj tej funkcji elementu członkowskiego w zestawach rekordów używających pobierania wierszy zbiorczych. Jeśli zaimplementowano pobieranie wierszy zbiorczych, wywoływanie `SetFieldNull` wyników nie powiodło się. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Jeśli celowo chcesz wyznaczyć pole bieżącego rekordu jako niemające wartości, wywołaj `SetFieldNull` z *bNull* USTAWIONĄ na wartość true, aby oflagować ją jako wartość null. Jeśli pole zostało wcześniej oznaczone jako puste i teraz chcesz nadać mu wartość, po prostu ustaw jej nową wartość. Nie trzeba usuwać flagi o wartości null przy użyciu `SetFieldNull` . Aby określić, czy pole może mieć wartość null, wywołaj `IsFieldNullable` .

> [!CAUTION]
> Wywołaj tę funkcję elementu członkowskiego tylko po wywołaniu metody [Edit](#edit) lub [AddNew](#addnew).

Użycie wartości NULL dla pierwszego argumentu funkcji spowoduje zastosowanie funkcji tylko do `outputColumn` pól, a nie `param` pól. Na przykład wywołanie

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

spowoduje ustawienie tylko `outputColumn` pól na null; nie `param` wpłynie to na pola.

Aby można było korzystać z `param` pól, należy podać rzeczywisty adres osoby `param` , na której ma być wykonywane działanie, na przykład:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

Oznacza to, że nie można ustawić `param` wartości null dla wszystkich pól, jak można z `outputColumn` polami.

> [!NOTE]
> Podczas ustawiania parametrów do wartości null wywołanie `SetFieldNull` przed otwartym zestawem rekordów skutkuje potwierdzeniem. W tym przypadku Wywołaj [SetParamNull](#setparamnull).

`SetFieldNull`jest implementowana za poorednictwem [DoFieldExchange](#dofieldexchange).

## <a name="crecordsetsetlockingmode"></a><a name="setlockingmode"></a>CRecordset:: setlockmode

Ustawia tryb blokowania na "optymistyczne" blokowania (ustawienie domyślne) lub "pesymistyczne". Określa sposób blokowania rekordów na potrzeby aktualizacji.

```cpp
void SetLockingMode(UINT nMode);
```

### <a name="parameters"></a>Parametry

*nMode*<br/>
Zawiera jedną z następujących wartości z `enum LockMode` :

- `optimistic`Optymistyczne blokowanie blokuje rekord, który jest aktualizowany tylko w trakcie wywołania do `Update` .

- `pessimistic`Zablokowanie pesymistyczne blokuje rekord natychmiast po `Edit` wywołaniu i zachowuje jego zablokowany do momentu `Update` zakończenia wywołania lub przejścia do nowego rekordu.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję elementu członkowskiego, jeśli chcesz określić, która z dwóch strategii blokowania rekordów jest używana przez zestaw rekordów dla aktualizacji. Domyślnie tryb blokowania zestawu rekordów to `optimistic` . Można to zmienić, aby zachować bardziej ostrożną `pessimistic` strategię blokowania. Wywołaj `SetLockingMode` po utworzeniu i otwarciu obiektu zestawu rekordów, ale przed wywołaniem `Edit` .

## <a name="crecordsetsetparamnull"></a><a name="setparamnull"></a>CRecordset::SetParamNull

Flaguje parametr jako null (w przypadku braku wartości) lub jako inny niż null.

```cpp
void SetParamNull(
    int nIndex,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks (liczony od zera) parametru.

*bNull*<br/>
W przypadku wartości TRUE (wartość domyślna) parametr jest oflagowany jako wartość null. W przeciwnym razie parametr jest oflagowany jako inny niż null.

### <a name="remarks"></a>Uwagi

W przeciwieństwie do [SetFieldNull](#setfieldnull), można wywołać `SetParamNull` przed otwarciem zestawu rekordów.

`SetParamNull`jest zazwyczaj używany z wstępnie zdefiniowanymi zapytaniami (procedury składowane).

## <a name="crecordsetsetrowsetcursorposition"></a><a name="setrowsetcursorposition"></a>CRecordset::SetRowsetCursorPosition

Przenosi kursor do wiersza w bieżącym zestawie wierszy.

```cpp
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>Parametry

*wRow*<br/>
Pozycja jednego wiersza w bieżącym zestawie wierszy. Ta wartość może być z zakresu od 1 do rozmiaru zestawu wierszy.

*wLockType*<br/>
Wartość wskazująca, jak zablokować wiersz po jego odświeżeniu. Aby uzyskać szczegółowe informacje, zobacz uwagi.

### <a name="remarks"></a>Uwagi

Podczas wdrażania pobierania wierszy zbiorczych rekordy są pobierane przez zestawy wierszy, gdzie pierwszy rekord w pobranym zestawie wierszy jest bieżącym rekordem. W celu wprowadzenia innego rekordu w zestawie wierszy jako bieżącego rekordu, wywołaj `SetRowsetCursorPosition` . Na przykład można połączyć `SetRowsetCursorPosition` z funkcją składową [GetFieldValue —](#getfieldvalue) , aby dynamicznie pobrać dane z dowolnego rekordu zestawu rekordów.

Aby użyć `SetRowsetCursorPosition` , musisz mieć zaimplementowane pobieranie wierszy zbiorczych przez określenie `CRecordset::useMultiRowFetch` opcji parametru *DwOptions* w funkcji [Open](#open) member.

`SetRowsetCursorPosition`wywołuje funkcję interfejsu API ODBC `SQLSetPos` . Parametr *wLockType* określa stan blokady wiersza po `SQLSetPos` wykonaniu. W poniższej tabeli opisano możliwe wartości dla *wLockType*.

|wLockType|Opis|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE (wartość domyślna)|Sterownik lub źródło danych gwarantuje, że wiersz znajduje się w tym samym stanie zablokowanym lub odblokowanym, ponieważ wcześniej `SetRowsetCursorPosition` został wywołany.|
|SQL_LOCK_EXCLUSIVE|Sterownik lub źródło danych blokuje wiersz w trybie wyłączności. Nie wszystkie źródła danych obsługują ten typ blokady.|
|SQL_LOCK_UNLOCK|Sterownik lub źródło danych odblokowuje wiersz. Nie wszystkie źródła danych obsługują ten typ blokady.|

Aby uzyskać więcej informacji na temat `SQLSetPos` , zobacz Windows SDK. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetsetrowsetsize"></a><a name="setrowsetsize"></a>CRecordset::SetRowsetSize

Określa liczbę rekordów, które mają zostać pobrane podczas pobierania.

```
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```

### <a name="parameters"></a>Parametry

*dwNewRowsetSize*<br/>
Liczba wierszy do pobrania podczas danego pobierania.

### <a name="remarks"></a>Uwagi

Ta wirtualna funkcja członkowska określa liczbę wierszy, które mają zostać pobrane podczas pojedynczego pobierania podczas korzystania z pobierania wierszy zbiorczych. Aby zaimplementować pobieranie wierszy zbiorczych, należy ustawić `CRecordset::useMultiRowFetch` opcję w parametrze *DwOptions* funkcji [Open](#open) member.

> [!NOTE]
> Wywołanie `SetRowsetSize` bez wdrożenia wierszy zbiorczych spowoduje niepomyślne potwierdzenie.

`SetRowsetSize`Przed wywołaniem `Open` wstępnego Ustaw rozmiar zestawu wierszy dla zestawu rekordów. Domyślny rozmiar zestawu wierszy podczas implementowania pobierania wierszy zbiorczych to 25.

> [!NOTE]
> Podczas wywoływania należy zachować ostrożność `SetRowsetSize` . Jeśli ręcznie alokujesz magazyn dla danych (określony przez `CRecordset::userAllocMultiRowBuffers` opcję parametru dwOptions w programie `Open` ), należy sprawdzić, czy należy ponownie przydzielić te bufory magazynu po wywołaniu `SetRowsetSize` , ale przed wykonaniem jakiejkolwiek operacji nawigacji kursora.

Aby uzyskać bieżące ustawienie rozmiaru zestawu wierszy, wywołaj [GetRowsetSize](#getrowsetsize).

Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetupdate"></a><a name="update"></a>CRecordset:: Update

Wykonuje `AddNew` operację lub `Edit` , zapisując nowe lub edytowane dane w źródle danych.

```
virtual BOOL Update();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli jeden rekord został pomyślnie zaktualizowany; w przeciwnym razie, jeśli żadna kolumna nie została zmieniona. Jeśli żadne rekordy nie zostały zaktualizowane lub Zaktualizowano więcej niż jeden rekord, zgłaszany jest wyjątek. Wyjątek jest również zgłaszany dla każdego innego błędu w źródle danych.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję elementu członkowskiego po wywołaniu funkcji [AddNew](#addnew) lub [Edit](#edit) member. To wywołanie jest wymagane do ukończenia `AddNew` operacji lub `Edit` .

> [!NOTE]
> Jeśli zaimplementowano pobieranie wierszy zbiorczych, nie można wywołać `Update` . Spowoduje to nieudane potwierdzenie. Chociaż Klasa nie `CRecordset` udostępnia mechanizmu do aktualizowania wierszy danych zbiorczych, można napisać własne funkcje przy użyciu funkcji ODBC API `SQLSetPos` . Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Zarówno `AddNew` , jak i `Edit` przygotowując bufor edycji, w którym dodane lub edytowane dane są umieszczane w celu zapisywania do źródła danych. `Update`zapisuje dane. Aktualizowane są tylko pola oznaczone lub wykryte jako zmienione.

Jeśli źródło danych obsługuje transakcje, można wykonać `Update` wywołanie (oraz jego odpowiadające `AddNew` lub `Edit` wywołania) część transakcji. Aby uzyskać więcej informacji na temat transakcji, zobacz artykuł [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

> [!CAUTION]
> W przypadku wywołania `Update` bez uprzedniego wywołania metody `AddNew` lub `Edit` , `Update` zgłasza `CDBException` . Jeśli wywołasz `AddNew` lub `Edit` , musisz wywołać `Update` przed wywołaniem `Move` operacji lub przed zamknięciem zestawu rekordów lub połączenia ze źródłem danych. W przeciwnym razie zmiany zostaną utracone bez powiadomienia.

Aby uzyskać szczegółowe informacje o `Update` błędach obsługi, zobacz [zestaw rekordów artykułów: jak zestawy rekordów aktualizują rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

### <a name="example"></a>Przykład

Zobacz artykuł [transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="see-also"></a>Zobacz także

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDatabase](../../mfc/reference/cdatabase-class.md)<br/>
[Klasa formularzy CRecordView](../../mfc/reference/crecordview-class.md)
