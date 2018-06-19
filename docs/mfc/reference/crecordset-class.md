---
title: Crecordset — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 683f1d612a57e4f6e2d8661af17faa73f725d3d6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33378738"
---
# <a name="crecordset-class"></a>Crecordset — klasa
Reprezentuje zestaw rekordów wybrane źródła danych.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CRecordset : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRecordset::CRecordset](#crecordset)|Konstruuje `CRecordset` obiektu. Klasy pochodne podać konstruktora, który wywołuje ten zestaw.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRecordset::AddNew](#addnew)|Przygotowuje do dodawania nowego rekordu. Wywołanie `Update` przeprowadzenie operacji dodawania.|  
|[CRecordset::CanAppend](#canappend)|Zwraca wartość niezerową, jeśli można dodać nowych rekordów do zestawu rekordów za pośrednictwem `AddNew` funkcję elementu członkowskiego.|  
|[CRecordset::CanBookmark](#canbookmark)|Zwraca wartość niezerową, jeśli zestaw rekordów obsługuje zakładki.|  
|[CRecordset::Cancel](#cancel)|Anuluje operację asynchroniczną lub procesu z drugiego wątku.|  
|[CRecordset::CancelUpdate](#cancelupdate)|Anuluje wszystkie oczekujące aktualizacje z powodu `AddNew` lub `Edit` operacji.|  
|[CRecordset::CanRestart](#canrestart)|Zwraca różną od zera, jeśli `Requery` można wywołać ponowne uruchomienie zapytania w zestawie rekordów.|  
|[CRecordset::CanScroll](#canscroll)|Zwraca wartość niezerową, jeśli można przewijać rekordy.|  
|[CRecordset::CanTransact](#cantransact)|Zwraca wartość niezerową, jeśli źródło danych obsługuje transakcji.|  
|[CRecordset::CanUpdate](#canupdate)|Zwraca wartość niezerową, jeśli można zaktualizować zestawu rekordów (możesz dodać, zaktualizować lub usunąć rekordy).|  
|[CRecordset::CheckRowsetError](#checkrowseterror)|Wywołuje się, by obsłużyć wygenerowane błędy podczas pobierania rekordu.|  
|[CRecordset::Close](#close)|Zamyka zestawu rekordów i ODBC **HSTMT** skojarzonych z nim.|  
|[CRecordset::Delete](#delete)|Usuwa rekord bieżący w zestawie. Należy jawnie przewiń do innego rekordu, po usunięciu.|  
|[CRecordset::DoBulkFieldExchange](#dobulkfieldexchange)|Wywołuje się, by wymienić zbiorczego wiersze danych ze źródła danych do zestawu rekordów. Implementuje zbiorcze wymiana pól rekordów (RFX zbiorczego).|  
|[CRecordset::DoFieldExchange](#dofieldexchange)|Wywoływane w celu wymiany danych (w obu kierunkach) między elementy członkowskie danych pola zestawu rekordów i odpowiedniego rekordu w źródle danych. Implementuje rekord wymiana pól (RFX).|  
|[CRecordset::Edit](#edit)|Przygotowuje się do zmian dla bieżącego rekordu. Wywołanie `Update` przeprowadzenie edycji.|  
|[CRecordset::FlushResultSet](#flushresultset)|Zwraca wartość niezerową, jeśli istnieje inny wynik ustawioną można pobrać przy użyciu wstępnie zdefiniowanego zapytania.|  
|[CRecordset::GetBookmark](#getbookmark)|Przypisuje wartość zakładki rekordu do obiektu parameter.|  
|[CRecordset::GetDefaultConnect](#getdefaultconnect)|Wywołuje się, by pobrać domyślny ciąg połączenia.|  
|[CRecordset::GetDefaultSQL](#getdefaultsql)|Wywołuje się, by pobrać domyślny ciąg SQL do wykonania.|  
|[CRecordset::GetFieldValue](#getfieldvalue)|Zwraca wartość pola w zestawie rekordów.|  
|[CRecordset::GetODBCFieldCount](#getodbcfieldcount)|Zwraca liczbę pól w zestawie rekordów.|  
|[CRecordset::GetODBCFieldInfo](#getodbcfieldinfo)|Zwraca określonych rodzajów informacji o polach w zestawie rekordów.|  
|[CRecordset::GetRecordCount](#getrecordcount)|Zwraca liczbę rekordów w zestawie rekordów.|  
|[CRecordset::GetRowsetSize](#getrowsetsize)|Zwraca liczbę rekordów, które chcesz pobrać podczas jednego pobierania.|  
|[CRecordset::GetRowsFetched](#getrowsfetched)|Zwraca wartość rzeczywistą liczbę pobieranych podczas pobierania wierszy.|  
|[CRecordset::GetRowStatus](#getrowstatus)|Zwraca informacje o stanie wiersza po pobraniu.|  
|[CRecordset::GetSQL](#getsql)|Pobiera ciąg SQL używana do wybierania rekordów dla zestawu rekordów.|  
|[CRecordset::GetStatus](#getstatus)|Pobiera stan zestaw rekordów: indeks bieżącego rekordu i czy został uzyskany końcowego liczbę rekordów.|  
|[CRecordset::GetTableName](#gettablename)|Pobiera nazwę tabeli, na której oparto zestawu rekordów.|  
|[CRecordset::IsBOF](#isbof)|Zwraca wartość niezerową, jeśli zestaw rekordów ma zostać umieszczony przed pierwszy rekord. Brak bieżącego rekordu.|  
|[CRecordset::IsDeleted](#isdeleted)|Zwraca wartość niezerową, jeśli zestaw rekordów jest ustawiony na usunięty rekord.|  
|[CRecordset::IsEOF](#iseof)|Zwraca wartość niezerową, jeśli zestaw rekordów zawiera została ustawiona za ostatni rekord. Brak bieżącego rekordu.|  
|[CRecordset::IsFieldDirty](#isfielddirty)|Zwraca wartość niezerową, jeśli określone pole bieżącego rekordu została zmieniona.|  
|[CRecordset::IsFieldNull](#isfieldnull)|Zwraca wartość niezerową, jeśli określone pole bieżącego rekordu ma wartość null (nie ma wartości).|  
|[CRecordset::IsFieldNullable](#isfieldnullable)|Zwraca wartość niezerową, jeśli określone pole bieżącego rekordu można ustawić wartości null (o wartości).|  
|[CRecordset::IsOpen](#isopen)|Zwraca różną od zera, jeśli `Open` wcześniej została wywołana.|  
|[CRecordset::Move](#move)|Umieszcza zestaw rekordów do określonej liczby rekordów z bieżącego rekordu w żadnym kierunku.|  
|[CRecordset::MoveFirst](#movefirst)|Określa położenie bieżącego rekordu na pierwszy rekord w zestawie rekordów. Badanie `IsBOF` pierwszy.|  
|[CRecordset::MoveLast](#movelast)|Umieszcza bieżącego rekordu ostatniego rekordu lub ostatnich wierszy. Badanie `IsEOF` pierwszy.|  
|[CRecordset::MoveNext](#movenext)|Umieszcza bieżącego rekordu następnego rekordu lub dalej zestawu wierszy. Badanie `IsEOF` pierwszy.|  
|[CRecordset::MovePrev](#moveprev)|Umieszcza bieżącego rekordu poprzedniego rekordu lub poprzedniego zestawu wierszy. Badanie `IsBOF` pierwszy.|  
|[CRecordset::OnSetOptions](#onsetoptions)|Wywołuje się, by ustawić opcje (używane na wybór) określona w instrukcji ODBC.|  
|[CRecordset::OnSetUpdateOptions](#onsetupdateoptions)|Wywołuje się, by ustawić opcje (używane na aktualizację) określona w instrukcji ODBC.|  
|[CRecordset::Open](#open)|Zostanie otwarty zestaw rekordów przez pobieranie tabeli lub wykonywania zapytania, który reprezentuje zestaw rekordów.|  
|[CRecordset::RefreshRowset](#refreshrowset)|Odświeża dane i stan określonego wiersze.|  
|[CRecordset::Requery](#requery)|Uruchamia kwerendy w zestawie rekordów ponownie, aby odświeżyć wybranych rekordów.|  
|[CRecordset::SetAbsolutePosition](#setabsoluteposition)|Umieszcza zestawu rekordów w rekordzie odpowiadającą liczbie określonego rekordu.|  
|[CRecordset::SetBookmark](#setbookmark)|Umieszcza zestawu rekordów na określony zakładką rekord.|  
|[CRecordset::SetFieldDirty](#setfielddirty)|Oznacza określonego pola w bieżącym rekordem, ponieważ zmianie.|  
|[CRecordset::SetFieldNull](#setfieldnull)|Ustawia wartość określonego pola w bieżącym rekordzie null (o wartości).|  
|[CRecordset::SetLockingMode](#setlockingmode)|Ustawia tryb blokowania "optymistycznej" blokowania (ustawienie domyślne) lub blokowania "pesymistyczne". Określa sposób blokowania rekordów aktualizacji.|  
|[CRecordset::SetParamNull](#setparamnull)|Ustawia określony parametr null (o wartości).|  
|[CRecordset::SetRowsetCursorPosition](#setrowsetcursorposition)|Umieszcza kursor na określony wiersz w zestawie wierszy.|  
|[CRecordset::SetRowsetSize](#setrowsetsize)|Określa liczbę rekordów, które chcesz pobrać podczas pobierania.|  
|[CRecordset::Update](#update)|Kończy `AddNew` lub `Edit` operacji zapisując nowe lub zmodyfikowane dane w źródle danych.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRecordset::m_hstmt](#m_hstmt)|Zawiera dojście do instrukcji ODBC dla zestawu rekordów. Typ `HSTMT`.|  
|[CRecordset::m_nFields](#m_nfields)|Zawiera liczbę elementy członkowskie danych pola w zestawie rekordów. Typ `UINT`.|  
|[CRecordset::m_nParams](#m_nparams)|Zawiera liczbę elementy członkowskie danych parametru w zestawie rekordów. Typ `UINT`.|  
|[CRecordset::m_pDatabase](#m_pdatabase)|Zawiera wskaźnik do `CDatabase` obiektu za pomocą których zestaw rekordów jest połączony ze źródłem danych.|  
|[CRecordset::m_strFilter](#m_strfilter)|Zawiera `CString` języka SQL (Structured Query), który określa `WHERE` klauzuli. Używane jako filtr, aby wybrać tylko te rekordy, które spełniają określone kryteria.|  
|[CRecordset::m_strSort](#m_strsort)|Zawiera `CString` SQL, który określa `ORDER BY` klauzuli. Służy do kontrolowania sposobu sortowania.|  
  
## <a name="remarks"></a>Uwagi  
 Znany jako "zestawy rekordów," `CRecordset` obiekty są zazwyczaj używane w dwóch formach: zestawów dynamicznych i migawek. Zestaw dynamiczny jest synchronizowany z aktualizacjami danych wprowadzonych przez innych użytkowników. Migawka jest widok statyczny danych. Każdy formularz reprezentuje zestaw rekordów ustalone w momencie otwarcia zestawu rekordów, ale podczas przewijania do rekordu w dynamiczny odzwierciedlały zmiany przeprowadzeniu dla rekordu przez innych użytkowników lub innych zestawów rekordów w aplikacji.  
  
> [!NOTE]
>  Jeśli pracujesz z klas obiektów DAO (Data Access), a nie klasy otwarte połączenie bazy danych (ODBC), należy użyć klasy [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) zamiast tego. Aby uzyskać więcej informacji, zobacz artykuł [omówienie: programowania bazy danych](../../data/data-access-programming-mfc-atl.md).  
  
 Aby pracować z dowolnego typu zestawu rekordów, zwykle pochodzi klasy specyficzne dla aplikacji zestawu rekordów z `CRecordset`. Zestawy rekordów wybierz rekordy ze źródła danych, a następnie możesz:  
  
-   Przewijanie rekordów.  
  
-   Zaktualizuj rekordów i określ tryb blokowania.  
  
-   Filtrowanie rekordów, aby ograniczyć rekordy, które powoduje wybranie od tych, które są dostępne w źródle danych.  
  
-   Aby posortować zestawu rekordów.  
  
-   Parametryzacja zestawu rekordów, aby dostosować jego zaznaczenie informacje nie są znane do czasu wykonywania.  
  
 Aby używać klasy, Otwieranie bazy danych i utworzyć obiekt zestawu rekordów, przekazywanie konstruktora wskaźnik do Twojej `CDatabase` obiektu. Następnie wywołaj zestawu rekordów **Otwórz** funkcji członkowskiej, w którym można określić, czy obiekt jest dynamiczny lub migawki. Wywoływanie **Otwórz** wybiera danych ze źródła danych. Po otwarciu obiektu zestawu rekordów, użyj jego element członkowski funkcji i danych elementów członkowskich do przewijania rekordów i działają na nich. Operacje dostępne są zależne od tego, czy obiekt jest dynamiczny lub migawki, można aktualizować lub tylko do odczytu (to zależy od możliwości źródła danych, Otwórz połączenie bazy danych (ODBC)), i czy zostały zaimplementowane zbiorcze pobieranie z wiersza. Aby odświeżyć rekordy, które mogą zostały zmienione lub dodane po **Otwórz** wywołania, należy wywołać obiektu **Requery** funkcji członkowskiej. Wywołanie obiektu **Zamknij** elementu członkowskiego działać, a obiekt zniszczyć, po zakończeniu pracy z nim.  
  
 W pochodnym `CRecordset` klasy, zarejestrować wymiana pól (RFX) lub zbiorcza wymiana pól rekordów (RFX zbiorczego) jest używana do obsługi odczytywanie i aktualizowanie pola rekordu.  
  
 Aby uzyskać więcej informacji na temat zestawów rekordów i rekordu wymiana pól, zobacz artykuły [omówienie: programowania bazy danych](../../data/data-access-programming-mfc-atl.md), [zestawu rekordów (ODBC)](../../data/odbc/recordset-odbc.md), [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC) ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md), i [(RFX). wymiana pól rekordów](../../data/odbc/record-field-exchange-rfx.md). Aby fokus na zestawów dynamicznych i migawek, zobacz artykuły [dynamiczny](../../data/odbc/dynaset.md) i [migawki](../../data/odbc/snapshot.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CRecordset`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdb.h  
  
##  <a name="addnew"></a>  CRecordset::AddNew  
 Przygotowuje do dodawania nowego rekordu do tabeli.  
  
```  
virtual void AddNew();
```  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać [Requery](#requery) funkcji członkowskiej w celu wyświetlenia nowo dodanego rekordu. Pola rekordu są początkowo wartości Null. (W terminologii bazy danych o wartości Null oznacza, że "o wartości" i nie jest taka sama jak **NULL** w języku C++.) Aby ukończyć operację, należy wywołać [aktualizacji](#update) funkcję elementu członkowskiego. **Aktualizacja** zapisuje zmiany w źródle danych.  
  
> [!NOTE]
>  Jeśli zaimplementowano zbiorcze pobieranie z wiersza, nie można wywołać `AddNew`. Spowoduje to potwierdzenie nie powiodło się. Chociaż klasa `CRecordset` nie udostępniają mechanizm aktualizacji zbiorczej wiersze danych, można zapisać własnych funkcji przy użyciu funkcji interfejsu API ODBC **SQLSetPos**. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 `AddNew` przygotowuje nowy, pusty rekord przy użyciu elementy członkowskie danych pola w zestawie rekordów. Po wywołaniu metody `AddNew`, ustawić wartości ma elementy członkowskie danych pola w zestawie rekordów. (Nie trzeba wywołać [Edytuj](#edit) funkcji członkowskiej, w tym celu; użyj **Edytuj** tylko w przypadku istniejących rekordów.) Jeśli następnie wywołaj **aktualizacji**, zmienione wartości w elementy członkowskie danych pola są zapisywane w źródle danych.  
  
> [!CAUTION]
>  Jeśli przewijania do nowego rekordu przed wywołaniem **aktualizacji**nowego rekordu zostaną utracone i podano bez ostrzeżenia.  
  
 Jeśli źródło danych obsługuje transakcje, możesz wprowadzić Twojej `AddNew` wywołać w ramach transakcji. Aby uzyskać więcej informacji na temat transakcji, zobacz klasy [cdatabase —](../../mfc/reference/cdatabase-class.md). Należy pamiętać, że należy wywołać [CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) przed wywołaniem `AddNew`.  
  
> [!NOTE]
>  Dla zestawów dynamicznych nowe rekordy są dodawane do zestawu rekordów jako ostatni rekord. Dodano rekordy nie zostaną dodane do migawki; należy wywołać **Requery** do odświeżenia zestawu rekordów.  
  
 Nie jest dozwolone wywoływanie `AddNew` dla zestawu rekordów których **Otwórz** funkcja członkowska nie została wywołana. A `CDBException` jest generowany, jeśli wywołujesz `AddNew` dla zestawu rekordów, która nie może być dołączona. Można określić, czy zestaw rekordów jest nadaje się do aktualizacji, wywołując [CanAppend](#canappend).  
  
 Aby uzyskać więcej informacji, zobacz następujące artykuły: [zestaw rekordów: jak zestawy rekordów aktualizacji rekordów (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md), [zestaw rekordów: Dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), i [(transakcji ODBC)](../../data/odbc/transaction-odbc.md).  
  
### <a name="example"></a>Przykład  
 Zapoznaj się z artykułem [transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
##  <a name="canappend"></a>  CRecordset::CanAppend  
 Określa, czy wcześniej otwartych rekordów pozwala na dodawanie nowych rekordów.  
  
```  
BOOL CanAppend() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli zestaw rekordów zezwala na dodawanie nowych rekordów; w przeciwnym razie 0. `CanAppend` Zwraca wartość 0, gdy otwarty zestaw rekordów jako tylko do odczytu.  
  
##  <a name="canbookmark"></a>  CRecordset::CanBookmark  
 Określa, czy zestaw rekordów umożliwia oznaczanie rekordów korzystanie z zakładek.  
  
```  
BOOL CanBookmark() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli zestaw rekordów obsługuje zakładki; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest niezależna od **CRecordset::useBookmarks** opcji `dwOptions` parametr [Otwórz](#open) funkcji członkowskiej. `CanBookmark` Wskazuje, czy danego sterownika ODBC i kursora typu zakładki pomocy technicznej. **CRecordset::useBookmarks** wskazuje, czy zakładki będzie dostępny, pod warunkiem są obsługiwane.  
  
> [!NOTE]
>  Zakładki nie są obsługiwane na zestawy rekordów tylko do przodu.  
  
 Aby uzyskać więcej informacji na temat zakładek i nawigacji zestawu rekordów, zobacz artykuły [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) i [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="cancel"></a>  CRecordset::Cancel  
 Żądania, że źródło danych anulować operacji asynchronicznej w toku lub procesu z drugiego wątku.  
  
```  
void Cancel();
```  
  
### <a name="remarks"></a>Uwagi  
 Należy pamiętać, że klasach MFC ODBC nie jest już przetwarzania asynchronicznego; Próba wykonania operacji asychronous, możesz bezpośrednio wywołanie funkcji interfejsu API ODBC **SQLSetConnectOption**. Aby uzyskać więcej informacji, zobacz temat "Wykonywane asynchronicznie funkcje" w *ODBC SDK przewodnik*.  
  
##  <a name="cancelupdate"></a>  CRecordset::CancelUpdate  
 Anuluje wszystkie oczekujące aktualizacje, spowodowane [Edytuj](#edit) lub [AddNew](#addnew) operacji przed [aktualizacji](#update) jest wywoływana.  
  
```  
void CancelUpdate();
```  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ta funkcja członkowska nie ma zastosowania na zestawy rekordów, które korzystają z zbiorcze pobieranie z wiersza, ponieważ nie można wywołać takie zestawy rekordów **Edytuj**, `AddNew`, lub **aktualizacji**. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Jeśli włączono automatyczne pola zanieczyszczone sprawdzanie `CancelUpdate` spowoduje przywrócenie zmienne Członkowskie wartości miało przed **Edytuj** lub `AddNew` została wywołana; w przeciwnym, pozostanie zmiany wartości. Domyślnie pole Automatyczne sprawdzanie jest włączone po otwarciu zestawu rekordów. Aby ją wyłączyć, należy określić **CRecordset::noDirtyFieldCheck** w `dwOptions` parametr [Otwórz](#open) funkcję elementu członkowskiego.  
  
 Aby uzyskać więcej informacji na temat aktualizowania danych, zobacz artykuł [zestaw rekordów: Dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md).  
  
##  <a name="canrestart"></a>  CRecordset::CanRestart  
 Określa, czy zestaw rekordów zezwala na ponowne uruchomienie jej zapytania (na przykład aby odświeżyć swoje rekordy) przez wywołanie metody **Requery** funkcję elementu członkowskiego.  
  
```  
BOOL CanRestart() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli jest dozwolone ponowne wykonanie kwerendy; w przeciwnym razie 0.  
  
##  <a name="canscroll"></a>  CRecordset::CanScroll  
 Określa, czy zestaw rekordów umożliwia przewijania.  
  
```  
BOOL CanScroll() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli zestaw rekordów umożliwia przewijanie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat przewijania, zobacz artykuł [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="cantransact"></a>  CRecordset::CanTransact  
 Określa, czy zestaw rekordów zezwala transakcji.  
  
```  
BOOL CanTransact() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli zestaw rekordów umożliwia transakcji; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz artykuł [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="canupdate"></a>  CRecordset::CanUpdate  
 Określa, czy zestaw rekordów może być aktualizowana.  
  
```  
BOOL CanUpdate() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli można zaktualizować zestawu rekordów; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Zestaw rekordów może być tylko do odczytu, jeśli źródła danych jest tylko do odczytu lub nie określono **CRecordset::readOnly** w `dwOptions` parametru po otwarciu zestawu rekordów.  
  
##  <a name="checkrowseterror"></a>  CRecordset::CheckRowsetError  
 Wywołuje się, by obsłużyć wygenerowane błędy podczas pobierania rekordu.  
  
```  
virtual void CheckRowsetError(RETCODE nRetCode);
```  
  
### <a name="parameters"></a>Parametry  
 `nRetCode`  
 Kod powrotu funkcji interfejsu API ODBC. Aby uzyskać więcej informacji zobacz uwagi.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja wirtualny element członkowski obsługuje błędów występujących podczas rekordy są pobierane, co jest przydatne podczas zbiorcze pobieranie z wiersza. Warto rozważyć zastąpienie `CheckRowsetError` do zaimplementowania własne obsługi błędów.  
  
 `CheckRowsetError` jest wywoływana automatycznie w ramach operacji nawigacji kursora, takich jak **Otwórz**, **Requery**, lub **Przenieś** operacji. Została przekazana wartość zwracana funkcji interfejsu API ODBC **procedury SQLExtendedFetch**. W poniższej tabeli przedstawiono możliwe wartości `nRetCode` parametru.  
  
|nRetCode|Opis|  
|--------------|-----------------|  
|**SQL_SUCCESS**|Funkcja zakończyła się pomyślnie; dodatkowe informacje są niedostępne.|  
|**WARTOŚĆ SQL_SUCCESS_WITH_INFO**|Funkcja została ukończona pomyślnie, prawdopodobnie z błąd niekrytyczny. Dodatkowe informacje można uzyskać przez wywołanie metody **SQLError**.|  
|**SQL_NO_DATA_FOUND**|Pobrano wszystkie wiersze z zestawu wyników.|  
|**WARTOŚĆ SQL_ERROR**|Funkcja nie powiodło się. Dodatkowe informacje można uzyskać przez wywołanie metody **SQLError**.|  
|**SQL_INVALID_HANDLE**|Funkcja nie powiodło się z powodu środowiska nieprawidłowy uchwyt, dojścia połączenia lub instrukcji. Oznacza to błąd programistyczny. Dodatkowe informacje są niedostępne z **SQLError**.|  
|`SQL_STILL_EXECUTING`|Funkcja, która została uruchomiona asynchronicznie jest nadal wykonywane. Należy pamiętać, że domyślnie MFC nigdy nie zostanie przekazany tę wartość na `CheckRowsetError`; MFC będzie wywoływania **procedury SQLExtendedFetch** dopóki nie będzie już zwracać `SQL_STILL_EXECUTING`.|  
  
 Aby uzyskać więcej informacji na temat **SQLError**, zobacz zestaw Windows SDK. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="close"></a>  CRecordset::Close  
 Zamyka zestawu rekordów.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Uwagi  
 ODBC **HSTMT** i całej pamięci są alokację framework przydzielony do zestaw rekordów. Zwykle po wywołaniu **Zamknij**, Usuń obiekty zestawów rekordów C++, jeśli został przydzielony z **nowe**.  
  
 Możesz wywołać **Otwórz** ponownie po wywołaniu **Zamknij**. Dzięki temu można użyć ponownie obiektu zestawu rekordów. Alternatywą jest wywołać **Requery**.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDatabase#17](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]  
  
##  <a name="crecordset"></a>  CRecordset::CRecordset  
 Konstruuje `CRecordset` obiektu.  
  
```  
CRecordset(CDatabase* pDatabase = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pDatabase`  
 Zawiera wskaźnik do `CDatabase` obiektu lub wartość **NULL**. Jeśli nie **NULL** i `CDatabase` obiektu **Otwórz** nie została wywołana funkcja członkowska nawiązać źródła danych, próbuje on otwarty przez podczas własny zestaw rekordów **Otwórz**  wywołania. W przypadku przekazania **NULL**, `CDatabase` obiektu jest konstruowane i połączone przy użyciu określonego podczas pochodnej klasy rekordów z ClassWizard informacje o źródle danych.  
  
### <a name="remarks"></a>Uwagi  
 Można użyć `CRecordset` bezpośrednio lub pochodzi z klasy specyficzne dla aplikacji z `CRecordset`. ClassWizard umożliwia pochodzi z klasy zestawu rekordów.  
  
> [!NOTE]
>  Klasa pochodna *musi* podać własne konstruktora. W konstruktorze klasy pochodnej, wywołanie konstruktora `CRecordset::CRecordset`, przekazywanie do niego odpowiednie parametry wzdłuż.  
  
 Przekaż **wartości NULL** Twojego Konstruktora zestawu rekordów mają `CDatabase` obiekt utworzone i połączone można automatycznie. Jest to przydatne skrótowa, która nie wymaga do utworzenia i połączenia `CDatabase` obiektu przed konstruowania zestawu rekordów.  
  
### <a name="example"></a>Przykład  
 Aby uzyskać więcej informacji, zobacz artykuł [zestaw rekordów: deklarowanie klasy dla tabeli (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).  
  
##  <a name="delete"></a>  CRecordset::Delete  
 Umożliwia usunięcie bieżącego rekordu.  
  
```  
virtual void Delete();
```  
  
### <a name="remarks"></a>Uwagi  
 Po pomyślnym usunięciu, elementy członkowskie danych pola w zestawie rekordów są ustawione na wartość Null i musi jawnie wywołać jeden z **Przenieś** funkcji, aby opuścić usunięty rekord. Po przeniesieniu poza usunięty rekord nie jest możliwe do niego wrócić. Jeśli źródło danych obsługuje transakcje, możesz wprowadzić **usunąć** wywołać w ramach transakcji. Aby uzyskać więcej informacji, zobacz artykuł [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).  
  
> [!NOTE]
>  Jeśli zaimplementowano zbiorcze pobieranie z wiersza, nie można wywołać **usunąć**. Spowoduje to potwierdzenie nie powiodło się. Chociaż klasa `CRecordset` nie udostępniają mechanizm aktualizacji zbiorczej wiersze danych, można zapisać własnych funkcji przy użyciu funkcji interfejsu API ODBC **SQLSetPos**. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
> [!CAUTION]
>  Zestaw rekordów musi zezwalać na aktualizacje, a musi być prawidłowy rekord bieżący w zestawie rekordów podczas wywoływania **usunąć**; w przeciwnym razie wystąpi błąd. Na przykład usunąć rekord, ale nie przewiń do nowego rekordu przed wywołaniem **usunąć** ponownie, **usunąć** zgłasza [CDBException](../../mfc/reference/cdbexception-class.md).  
  
 W odróżnieniu od [AddNew](#addnew) i [Edytuj](#edit), wywołanie **usunąć** nie następuje wywołanie [aktualizacji](#update). Jeśli **usunąć** wywołania nie powiedzie się, dane pola członków pozostaną bez zmian.  
  
### <a name="example"></a>Przykład  
 Ten przykład przedstawia utworzone na ramce funkcji zestawu rekordów. W przykładzie założono istnienie `m_dbCust`, zmiennej elementu członkowskiego typu `CDatabase` już połączono ze źródłem danych.  
  
 [!code-cpp[NVC_MFCDatabase#18](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]  
  
##  <a name="dobulkfieldexchange"></a>  CRecordset::DoBulkFieldExchange  
 Wywołuje się, by wymienić zbiorczego wiersze danych ze źródła danych do zestawu rekordów. Implementuje zbiorcze wymiana pól rekordów (RFX zbiorczego).  
  
```  
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Wskaźnik do [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) obiektu. Platformę będzie już skonfigurowano tego obiektu do określenia kontekstu dla operacji wymiana pola.  
  
### <a name="remarks"></a>Uwagi  
 Po zaimplementowaniu zbiorcze pobieranie z wiersza struktura wywołuje funkcji członkowskiej automatycznie przesyłać dane ze źródła danych do obiektu zestawu rekordów. `DoBulkFieldExchange` także wiąże użytkownika elementy członkowskie danych parametru do parametru zastępcze w ciągu instrukcji SQL dla zaznaczenia w zestawie rekordów.  
  
 Jeśli zbiorcze pobieranie z wiersza nie jest zaimplementowana, struktura wywołuje [DoFieldExchange](#dofieldexchange). Aby zaimplementować zbiorcze pobieranie z wiersza, należy określić `CRecordset::useMultiRowFetch` opcji `dwOptions` parametru w [Otwórz](#open) funkcję elementu członkowskiego.  
  
> [!NOTE]
> `DoBulkFieldExchange` jest dostępna tylko wtedy, gdy używasz klasę pochodzącą od `CRecordset`. Jeśli utworzono obiekt zestawu rekordów bezpośrednio z `CRecordset`, należy wywołać [GetFieldValue](#getfieldvalue) funkcji członkowskiej do pobierania danych.  
  
 Zbiorcza wymiana pól rekordów (RFX zbiorczego) jest podobny do wymiana pól rekordów (RFX). Danych jest automatycznie przenoszona ze źródła danych do obiektu zestawu rekordów. Jednak nie można wywołać `AddNew`, **Edytuj**, **usunąć**, lub **aktualizacji** Aby przetransferować zmiany wprowadzone do źródła danych. Klasa `CRecordset` aktualnie nie zapewnia mechanizm aktualizacji zbiorczej wiersze danych; jednak napisania własnych funkcji za pomocą funkcji interfejsu API ODBC **SQLSetPos**.  
  
 Należy pamiętać, że ClassWizard nie obsługuje zbiorcza wymiana pól rekordów; w związku z tym konieczne jest przesłonięcie `DoBulkFieldExchange` ręcznie pisząc wywołania funkcji RFX zbiorczego. Aby uzyskać więcej informacji o tych funkcjach, zobacz temat [funkcje wymiany pól rekordów](../../mfc/reference/record-field-exchange-functions.md).  
  
 Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Aby uzyskać odpowiednie informacje, zobacz artykuł [wymiany pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
##  <a name="dofieldexchange"></a>  CRecordset::DoFieldExchange  
 Wywoływane w celu wymiany danych (w obu kierunkach) między elementy członkowskie danych pola zestawu rekordów i odpowiedniego rekordu w źródle danych. Implementuje rekord wymiana pól (RFX).  
  
```  
virtual void DoFieldExchange(CFieldExchange* pFX);
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Wskaźnik do [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) obiektu. Platformę będzie już skonfigurowano tego obiektu do określenia kontekstu dla operacji wymiana pola.  
  
### <a name="remarks"></a>Uwagi  
 Gdy zbiorcze pobieranie z wiersza nie jest zaimplementowana, struktura wywołuje funkcji członkowskiej do automatycznie wymiany danych między elementy członkowskie danych pola obiektu zestawu rekordów i odpowiednie kolumny bieżącego rekordu w źródle danych. `DoFieldExchange` także wiąże użytkownika elementy członkowskie danych parametru do parametru zastępcze w ciągu instrukcji SQL dla zaznaczenia w zestawie rekordów.  
  
 Jeśli zaimplementowano zbiorcze pobieranie z wiersza struktura wywołuje [DoBulkFieldExchange](#dobulkfieldexchange). Aby zaimplementować zbiorcze pobieranie z wiersza, należy określić `CRecordset::useMultiRowFetch` opcji `dwOptions` parametru w [Otwórz](#open) funkcję elementu członkowskiego.  
  
> [!NOTE]
> `DoFieldExchange` jest dostępna tylko wtedy, gdy używasz klasę pochodzącą od `CRecordset`. Jeśli utworzono obiekt zestawu rekordów bezpośrednio z `CRecordset`, należy wywołać [GetFieldValue](#getfieldvalue) funkcji członkowskiej do pobierania danych.  
  
 Pola danych, nazywane wymiana pól rekordów (RFX) programu exchange działa w obu kierunkach: elementy członkowskie danych pola obiektu zestawu rekordów w polach rekordu w źródle danych oraz rekordu w źródle danych do obiektu zestawu rekordów.  
  
 Jedyną akcją, zazwyczaj należy wykonać, aby zaimplementować `DoFieldExchange` dla pochodnego zestawu rekordów klasy ma utworzyć klasę z ClassWizard i określić nazwy i typy danych elementy członkowskie danych pola. Mogą również dodać kod, w jaki ClassWizard zapisuje, aby określić elementy członkowskie danych parametru lub radzenia sobie z dowolnej kolumny, które można powiązać dynamicznie. Aby uzyskać więcej informacji, zobacz artykuł [zestaw rekordów: dynamiczne wiązanie danych kolumn (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
 Deklaracja klasy pochodnej rekordów z ClassWizard kreator zapisuje zastępująca `DoFieldExchange` , który podobnego do następującego:  
  
 [!code-cpp[NVC_MFCDatabase#19](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]  
  
 Aby uzyskać więcej informacji na temat funkcji RFX, zobacz temat [funkcje wymiany pól rekordów](../../mfc/reference/record-field-exchange-functions.md).  
  
 Dalsze przykłady i szczegółowe informacje o `DoFieldExchange`, zapoznaj się z artykułem [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Aby uzyskać ogólne informacje o RFX, zobacz artykuł [wymiana pól rekordów](../../data/odbc/record-field-exchange-rfx.md).  
  
##  <a name="edit"></a>  CRecordset::Edit  
 Zezwala na zmiany bieżącego rekordu.  
  
```  
virtual void Edit();
```  
  
### <a name="remarks"></a>Uwagi  
 Po wywołaniu metody **Edytuj**, można zmienić elementy członkowskie danych pola bezpośrednio resetując ich wartości. Ukończenie tej operacji po wywołaniu następnie [aktualizacji](#update) funkcji członkowskiej, aby zapisać zmiany w źródle danych.  
  
> [!NOTE]
>  Jeśli zaimplementowano zbiorcze pobieranie z wiersza, nie można wywołać **Edytuj**. Spowoduje to potwierdzenie nie powiodło się. Chociaż klasa `CRecordset` nie udostępniają mechanizm aktualizacji zbiorczej wiersze danych, można zapisać własnych funkcji przy użyciu funkcji interfejsu API ODBC **SQLSetPos**. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 **Edytuj** zapisuje wartości elementów członkowskich danych w zestawie rekordów. Wywołanie **Edytuj**, wprowadzić zmiany, następnie wywołaj **Edytuj** ponownie, wartości rekordu zostaną przywrócone były przed pierwszym **Edytuj** wywołania.  
  
 W niektórych przypadkach można zaktualizować kolumny czyniąc ją (bez danych zawierający) o wartości Null. Aby to zrobić, należy wywołać [SetFieldNull](#setfieldnull) z parametrem **TRUE** do oznaczania pola wartość Null; powoduje również kolumny, która ma zostać zaktualizowany. Jeśli pole ma zapisywane do źródła danych, mimo że nie zmieniono jego wartość, należy wywołać [SetFieldDirty](#setfielddirty) z parametrem **TRUE**. To działanie, nawet jeśli pole ma wartość Null.  
  
 Jeśli źródło danych obsługuje transakcje, możesz wprowadzić **Edytuj** wywołać w ramach transakcji. Należy pamiętać, że należy wywołać [CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) przed wywołaniem **Edytuj** i po otwarciu zestawu rekordów. Należy również zauważyć, że wywołania [CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) nie jest zamiast wywoływania **aktualizacji** do ukończenia **Edytuj** operacji. Aby uzyskać więcej informacji na temat transakcji, zobacz klasy [cdatabase —](../../mfc/reference/cdatabase-class.md).  
  
 W zależności od bieżącej tryb blokowania rekordu aktualizacji może być zablokowana przez **Edytuj** czasu wywołania **aktualizacji** lub przewiń do innego rekordu lub może być zablokowana tylko podczas **Edytuj** wywołania. Można zmienić tryb blokowania z [SetLockingMode](#setlockingmode).  
  
 Poprzednia wartość bieżącego rekordu jest przywracane przewiń do nowego rekordu przed wywołaniem **aktualizacji**. A `CDBException` jest generowany, jeśli wywołujesz **Edytuj** dla zestawu rekordów, które nie można zaktualizować lub jeśli nie ma bieżącej rekordów.  
  
 Aby uzyskać więcej informacji, zobacz artykuły [transakcja (ODBC)](../../data/odbc/transaction-odbc.md) i [zestaw rekordów: blokowanie rekordów (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDatabase#20](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]  
  
##  <a name="flushresultset"></a>  CRecordset::FlushResultSet  
 Pobiera zestaw wyników dalej wstępnie zdefiniowanego zapytania (procedury składowanej), jeśli istnieje wiele zestawów wyników.  
  
```  
BOOL FlushResultSet();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli istnieje więcej zestawów wyników, które mają zostać pobrane; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać `FlushResultSet` tylko po zakończeniu całkowicie umieść kursor w bieżącym zestawie wyników. Należy pamiętać, że podczas pobierania następnego wyniku ustawiony przez wywołanie `FlushResultSet`, kursor nie jest prawidłowy w tym zestawie wyników; należy wywołać [MoveNext](#movenext) funkcji członkowskiej po wywołaniu `FlushResultSet`.  
  
 Jeśli wstępnie zdefiniowanego zapytania używa parametru wyjściowego lub parametry wejścia/wyjścia, należy wywołać `FlushResultSet` dopóki zwraca `FALSE` (wartość 0), w celu uzyskania tych wartości parametru.  
  
 `FlushResultSet` wywołuje funkcję interfejsu API ODBC `SQLMoreResults`. Jeśli `SQLMoreResults` zwraca `SQL_ERROR` lub `SQL_INVALID_HANDLE`, następnie `FlushResultSet` spowoduje zgłoszenie wyjątku. Aby uzyskać więcej informacji na temat `SQLMoreResults`, zobacz zestaw Windows SDK.  
  
 Twoja procedura składowana musi mieć powiązany pola, jeśli chcesz wywołać `FlushResultSet`.  
  
### <a name="example"></a>Przykład  
 Następujący kod, przy założeniu, że `COutParamRecordset` jest `CRecordset`-pochodnej obiekt na podstawie wstępnie zdefiniowanego zapytania z parametrem wejściowym i parametru wyjściowego i mających wiele zestawów wyników. Należy pamiętać, struktura [DoFieldExchange](#dofieldexchange) zastąpienia.  
  
 [!code-cpp[NVC_MFCDatabase#21](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDatabase#22](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]  
  
##  <a name="getbookmark"></a>  CRecordset::GetBookmark  
 Pobiera wartość zakładki dla bieżącego rekordu.  
  
```  
void GetBookmark(CDBVariant& varBookmark);
```  
  
### <a name="parameters"></a>Parametry  
 `varBookmark`  
 Odwołanie do [cdbvariant —](../../mfc/reference/cdbvariant-class.md) obiekt reprezentujący zakładki bieżącego rekordu.  
  
### <a name="remarks"></a>Uwagi  
 Aby ustalić, czy zakładki są obsługiwane w zestawie rekordów, należy wywołać [CanBookmark](#canbookmark). Aby udostępnić zakładki, jeśli są obsługiwane, należy ustawić **CRecordset::useBookmarks** opcji `dwOptions` parametr [Otwórz](#open) funkcję elementu członkowskiego.  
  
> [!NOTE]
>  Jeśli zakładki są nieobsługiwane lub jest niedostępny, wywoływania `GetBookmark` spowodują wyjątek. Zakładki nie są obsługiwane na zestawy rekordów tylko do przodu.  
  
 `GetBookmark` przypisuje wartość zakładki dla bieżącego rekordu `CDBVariant` obiektu. Aby powrócić do tego rekordu w dowolnym momencie po przeniesieniu do innego rekordu, należy wywołać [SetBookmark](#setbookmark) z odpowiednimi `CDBVariant` obiektu.  
  
> [!NOTE]
>  Po pewnych operacji rekordów zakładki może nie być już prawidłowe. Na przykład, jeśli wywołujesz `GetBookmark` następuje **Requery**, nie może być może zwrócić do rekordu o `SetBookmark`. Wywołanie [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) do sprawdzenia, czy można bezpiecznie wywołać `SetBookmark`.  
  
 Aby uzyskać więcej informacji na temat zakładek i nawigacji zestawu rekordów, zobacz artykuły [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) i [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="getdefaultconnect"></a>  CRecordset::GetDefaultConnect  
 Wywołuje się, by pobrać domyślny ciąg połączenia.  
  
```  
virtual CString GetDefaultConnect();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CString` zawierający domyślne parametry połączenia.  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje tę funkcję elementu członkowskiego, aby pobrać domyślny ciąg połączenia dla źródła danych, na której oparto zestaw rekordów. ClassWizard implementuje tę funkcję dla Ciebie, określając to samo źródło danych używanych w ClassWizard, aby uzyskać informacje dotyczące tabel i kolumn. Prawdopodobnie znajduje się ona wygodne polegać na tym domyślne połączenie podczas tworzenia aplikacji. Jednak domyślne połączenie nie może być odpowiednie dla użytkowników aplikacji. Jeśli tak jest, należy reimplement tej funkcji, odrzucając ClassWizard w wersji. Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz artykuł [źródła danych (ODBC)](../../data/odbc/data-source-odbc.md).  
  
##  <a name="getdefaultsql"></a>  CRecordset::GetDefaultSQL  
 Wywołuje się, by pobrać domyślny ciąg SQL do wykonania.  
  
```  
virtual CString GetDefaultSQL();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CString` zawiera domyślną instrukcję SQL.  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje tę funkcję elementu członkowskiego, aby pobrać domyślną instrukcję SQL, na której oparto zestawu rekordów. Może to być nazwa tabeli lub SQL **wybierz** instrukcji.  
  
 Pośrednio zdefiniować domyślną instrukcję SQL od zadeklarowania klasy rekordów z ClassWizard i ClassWizard wykonuje to zadanie.  
  
 Jeśli potrzebujesz ciąg instrukcji SQL na własny użytek wywołania `GetSQL`, która zwraca instrukcję SQL używana do wybierania rekordów w zestawie rekordów, jeśli został on otwarty. Można edytować domyślnego ciągu SQL w swojej klasy zastępowania `GetDefaultSQL`. Na przykład można określić wywołanie wstępnie zdefiniowanego zapytania przy użyciu **WYWOŁAĆ** instrukcji. (Uwaga, jednak, że jeśli zmodyfikować `GetDefaultSQL`, należy również zmodyfikować `m_nFields` do dopasowania liczby kolumn w źródle danych.)  
  
 Aby uzyskać więcej informacji, zobacz artykuł [zestaw rekordów: deklarowanie klasy dla tabeli (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).  
  
> [!CAUTION]
>  Nazwa tabeli będzie pusty, jeśli w ramach nie można zidentyfikować nazwę tabeli, jeśli podano wiele nazw tabel lub **WYWOŁANIA** nie można zinterpretować instrukcji. Należy pamiętać, że podczas korzystania **WYWOŁAĆ** instrukcji, nie należy umieszczać odstępów między nawias klamrowy i **WYWOŁAĆ** — słowo kluczowe, ani powinien Wstaw odstęp przed nawias klamrowy lub przed  **Wybierz** — słowo kluczowe w **wybierz** instrukcji.  
  
##  <a name="getfieldvalue"></a>  CRecordset::GetFieldValue  
 Pobiera dane pola z bieżącego rekordu.  
  
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
 `lpszName`  
 Nazwa pola.  
  
 *varValu*e  
 Odwołanie do [cdbvariant —](../../mfc/reference/cdbvariant-class.md) obiekt, który będzie przechowywać wartość pola.  
  
 `nFieldType`  
 Typ danych ODBC C pola. Przy użyciu wartości domyślnej **DEFAULT_FIELD_TYPE**, wymusza `GetFieldValue` można ustalić typu danych C z typem danych SQL na podstawie poniższej tabeli. W przeciwnym razie można określić typu bezpośrednio danych lub wybierz zgodny typ danych; na przykład można przechowywać dane dowolnego typu do **SQL_C_CHAR**.  
  
|C — typ danych|Typ danych SQL|  
|-----------------|-------------------|  
|**SQL_C_BIT**|**SQL_BIT**|  
|**SQL_C_UTINYINT**|**SQL_TINYINT**|  
|**SQL_C_SSHORT**|**SQL_SMALLINT**|  
|**SQL_C_SLONG**|**SQL_INTEGER**|  
|**SQL_C_FLOAT**|**SQL_REAL**|  
|**SQL_C_DOUBLE**|**SQL_FLOATSQL_DOUBLE**|  
|**SQL_C_TIMESTAMP**|**SQL_DATESQL_TIMESQL_TIMESTAMP**|  
|**SQL_C_CHAR**|**SQL_NUMERICSQL_DECIMALSQL_BIGINTSQL_CHARSQL_VARCHARSQL_LONGVARCHAR**|  
|**SQL_C_BINARY**|**SQL_BINARYSQL_VARBINARYSQL_LONGVARBINARY**|  
  
 Aby uzyskać więcej informacji o typach danych ODBC zobacz tematy "Typy danych SQL" i "C typów danych" w dodatku D zestawu Windows SDK.  
  
 `nIndex`  
 Liczony od zera indeks pola.  
  
 `strValue`  
 Odwołanie do [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) obiekt, który będzie przechowywać wartość pola przekonwertowane na tekst, niezależnie od typu danych pola.  
  
### <a name="remarks"></a>Uwagi  
 Pola można wyszukiwać według nazwy lub indeksu. Wartość pola można przechowywać w jednym `CDBVariant` obiektu lub `CString` obiektu.  
  
 Jeśli zaimplementowano zbiorcze pobieranie z wiersza, bieżący rekord jest zawsze ustawiony na pierwszy rekord w zestawie wierszy. Aby użyć `GetFieldValue` rekord w ramach danego zestawu wierszy, najpierw musisz wywołać [SetRowsetCursorPosition](#setrowsetcursorposition) funkcji członkowskiej, aby przesunąć kursor do żądanego wiersza w tym zestawie wierszy. Następnie wywołaj `GetFieldValue` dla tego wiersza. Aby zaimplementować zbiorcze pobieranie z wiersza, należy określić `CRecordset::useMultiRowFetch` opcji `dwOptions` parametru w [Otwórz](#open) funkcję elementu członkowskiego.  
  
 Można użyć `GetFieldValue` można dynamicznie pobrać pola w czasie wykonywania, a nie statycznie obowiązujące w czasie projektowania. Na przykład, jeśli ma zadeklarowany jako obiekt zestawu rekordów bezpośrednio z `CRecordset`, należy użyć `GetFieldValue` można pobrać danych pola; wymiana pól rekordów (RFX) lub zbiorcza wymiana pól rekordów (RFX zbiorczego), nie jest zaimplementowana.  
  
> [!NOTE]
>  W przypadku obiektu zestawu rekordów bez wynikających z `CRecordset`, nie ma załadowana Biblioteka kursorów ODBC. Biblioteka kursorów musi mieć zestawu rekordów co najmniej jedną kolumnę powiązane; Jednak jeśli używasz `CRecordset` bezpośrednio, Brak kolumn są powiązane. Funkcje Członkowskie [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) i [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) kontrolowanie, czy Biblioteka kursorów zostanie załadowany.  
  
 `GetFieldValue` wywołuje funkcję interfejsu API ODBC **Procedura SQLGetData**. Jeśli sterownik Wyświetla wartość **SQL_NO_TOTAL** rzeczywista długość wartości pola `GetFieldValue` zgłasza wyjątek. Aby uzyskać więcej informacji na temat **Procedura SQLGetData**, zobacz zestaw Windows SDK.  
  
### <a name="example"></a>Przykład  
 Następujący przykładowy kod przedstawia wywołań `GetFieldValue` dla obiekt zestawu rekordów zadeklarowany bezpośrednio z `CRecordset`.  
  
 [!code-cpp[NVC_MFCDatabase#23](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]  
  
> [!NOTE]
>  W odróżnieniu od klasy DAO `CDaoRecordset`, `CRecordset` nie ma `SetFieldValue` funkcję elementu członkowskiego. W przypadku utworzenia obiektu bezpośrednio z `CRecordset`, jest efektywne tylko do odczytu.  
  
 Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="getodbcfieldcount"></a>  CRecordset::GetODBCFieldCount  
 Pobiera całkowitą liczbę pól w obiekt zestawu rekordów.  
  
```  
short GetODBCFieldCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba pól w zestawie rekordów.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji o tworzeniu zestawów rekordów, zobacz artykuł [zestaw rekordów: tworzenie i zamykanie zestawów rekordów (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).  
  
##  <a name="getodbcfieldinfo"></a>  CRecordset::GetODBCFieldInfo  
 Pobiera informacje o polach w zestawie rekordów.  
  
```  
void GetODBCFieldInfo(
    LPCTSTR lpszName,  
    CODBCFieldInfo& fieldinfo);

 
void GetODBCFieldInfo(
    short nIndex,  
    CODBCFieldInfo& fieldinfo);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Nazwa pola.  
  
 `fieldinfo`  
 Odwołanie do `CODBCFieldInfo` struktury.  
  
 `nIndex`  
 Liczony od zera indeks pola.  
  
### <a name="remarks"></a>Uwagi  
 Jedna wersja funkcji umożliwia wyszukiwania według nazwy pola. Druga wersja pozwala pole wyszukiwania według indeksu.  
  
 Opis o zwracanych informacji, zobacz [codbcfieldinfo —](../../mfc/reference/codbcfieldinfo-structure.md) struktury.  
  
 Aby uzyskać więcej informacji o tworzeniu zestawów rekordów, zobacz artykuł [zestaw rekordów: tworzenie i zamykanie zestawów rekordów (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).  
  
##  <a name="getrecordcount"></a>  CRecordset::GetRecordCount  
 Określa rozmiar zestawu rekordów.  
  
```  
long GetRecordCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba rekordów w zestawie rekordów; 0, jeśli zestaw nie zawiera żadnych rekordów; lub -1, jeśli nie można określić liczbę rekordów.  
  
### <a name="remarks"></a>Uwagi  
  
> [!CAUTION]
>  Liczba rekordów jest przechowywany jako "znacznik limitu górnego," rekordu najwyższym numerze jeszcze występuje, gdy użytkownik przechodzi do rekordów. Całkowita liczba rekordów jest znany tylko, gdy użytkownik zostanie przeniesiona poza ostatniego rekordu. Ze względu na wydajność, licznik nie jest aktualizowany po wywołaniu `MoveLast`. Aby samodzielnie liczba rekordów, należy wywołać `MoveNext` wielokrotnie do `IsEOF` zwraca różną od zera. Dodawanie rekordów za pomocą **CRecordset:AddNew** i **aktualizacji** zwiększa liczbę; usuwanie rekordu za pośrednictwem `CRecordset::Delete` zmniejsza wartość licznika.  
  
##  <a name="getrowsetsize"></a>  CRecordset::GetRowsetSize  
 Pobiera liczbę wierszy, które chcesz pobrać podczas pobierania danego bieżące ustawienia.  
  
```  
DWORD GetRowsetSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba wierszy do pobrania podczas pobierania danego.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli używasz zbiorcze pobieranie z wiersza domyślny rozmiar wierszy po otwarciu zestaw rekordów jest 25; w przeciwnym razie jest 1.  
  
 Aby zaimplementować zbiorcze pobieranie z wiersza, należy określić `CRecordset::useMultiRowFetch` opcji `dwOptions` parametr [Otwórz](#open) funkcji członkowskiej. Aby zmienić ustawienie rozmiaru zestawu wierszy, należy wywołać [SetRowsetSize](#setrowsetsize).  
  
 Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="getrowsfetched"></a>  CRecordset::GetRowsFetched  
 Określa, ile rekordów rzeczywiście zostały pobrane po pobraniu.  
  
```  
DWORD GetRowsFetched() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba wierszy pobrane ze źródła danych po pobraniu danego.  
  
### <a name="remarks"></a>Uwagi  
 Jest to przydatne, gdy zostały zaimplementowane zbiorcze pobieranie z wiersza. Rozmiar zestawu wierszy zazwyczaj wskazuje, ile wierszy będą pobierane z fetch; jednak całkowitą liczbę wierszy w zestawie rekordów również wpływa na liczbę wierszy, które zostaną pobrane w zestawie wierszy. Na przykład, jeśli zestawu rekordów 10 rekordów z ustawieniem rozmiar wierszy 4, następnie zapętlenie przez zestaw rekordów przez wywołanie metody `MoveNext` spowoduje ostatecznego zestawu wierszy o rekordy tylko 2.  
  
 Aby zaimplementować zbiorcze pobieranie z wiersza, należy określić `CRecordset::useMultiRowFetch` opcji `dwOptions` parametr [Otwórz](#open) funkcji członkowskiej. Aby określić rozmiar wierszy, należy wywołać [SetRowsetSize](#setrowsetsize).  
  
 Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDatabase#24](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]  
  
##  <a name="getrowstatus"></a>  CRecordset::GetRowStatus  
 Uzyskuje informacje o stanie dla wiersza w bieżącym zestawie wierszy.  
  
```  
WORD GetRowStatus(WORD wRow) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `wRow`  
 Na podstawie jednej położenie wiersza w bieżącym zestawie wierszy. Ta wartość może należeć do zakresu od 1 do rozmiaru zestawu wierszy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość stanu wiersza. Aby uzyskać więcej informacji zobacz uwagi.  
  
### <a name="remarks"></a>Uwagi  
 `GetRowStatus` Zwraca wartość, która wskazuje zmiany stanu do wiersza od momentu jego ostatniego pobrane ze źródła danych, lub że nie wiersz odpowiadający `wRow` została pobrana. W poniższej tabeli przedstawiono możliwe wartości zwracane.  
  
|Wartość stanu|Opis|  
|------------------|-----------------|  
|`SQL_ROW_SUCCESS`|Wiersz nie ulega zmianie.|  
|`SQL_ROW_UPDATED`|Wiersz został zaktualizowany.|  
|`SQL_ROW_DELETED`|Wiersz został usunięty.|  
|`SQL_ROW_ADDED`|Wiersz został dodany.|  
|`SQL_ROW_ERROR`|Wiersz jest można pobrać niektórych z powodu błędu.|  
|`SQL_ROW_NOROW`|Brak wiersza umożliwiająca `wRow`.|  
  
 Aby uzyskać więcej informacji, zobacz opis funkcji interfejsu API ODBC **procedury SQLExtendedFetch** w zestawie Windows SDK.  
  
##  <a name="getstatus"></a>  CRecordset::GetStatus  
 Określa indeks bieżącego rekordu w zestawie rekordów i czy została napotkana ostatniego rekordu.  
  
```  
void GetStatus(CRecordsetStatus& rStatus) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `rStatus`  
 Odwołanie do **CRecordsetStatus** obiektu. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.  
  
### <a name="remarks"></a>Uwagi  
 `CRecordset` próbuje śledzić indeksu, ale w pewnych okolicznościach to może nie być możliwe. Zobacz [GetRecordCount](#getrecordcount) wyjaśnienie.  
  
 **CRecordsetStatus** struktury ma następujący format:  
  
 `struct CRecordsetStatus`  
  
 `{`  
  
 `long m_lCurrentRecord;`  
  
 `BOOL m_bRecordCountFinal;`  
  
 `};`  
  
 Dwa elementy członkowskie z **CRecordsetStatus** mają następujące znaczenie:  
  
- **m_lCurrentRecord** zawiera liczony od zera indeks bieżącego rekordu do zestawu rekordów, jeśli znane. Jeśli nie można określić indeks tego elementu członkowskiego zawiera **AFX_CURRENT_RECORD_UNDEFINED** -(2). Jeśli `IsBOF` jest **TRUE** (pusty zestaw rekordów lub Próba przewinięcia przed pierwszy rekord), następnie **m_lCurrentRecord** ustawiono **AFX_CURRENT_RECORD_BOF** (-1). Jeśli na pierwszy rekord, następnie jest ustawiona na 0, drugi rekord 1 i tak dalej.  
  
- **m_bRecordCountFinal** Nonzero Jeśli ustalono całkowita liczba rekordów w zestawie rekordów. Zazwyczaj te muszą być spełnione przez uruchomienie na początku zestawu rekordów i wywoływania `MoveNext` do momentu `IsEOF` zwraca różną od zera. Jeśli ten element członkowski jest równy zero, rekord liczba zwrócony przez `GetRecordCount`, jeśli nie -1, jest tylko licznik "znacznik limitu górnego" rekordów.  
  
##  <a name="getsql"></a>  CRecordset::GetSQL  
 Wywołanie tej funkcji Członkowskich uzyskanie instrukcji SQL, którego użyto do wybierania rekordów w zestawie rekordów, gdy została otwarta.  
  
```  
const CString& GetSQL() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A **const** odwołanie do `CString` zawiera instrukcję SQL.  
  
### <a name="remarks"></a>Uwagi  
 Są to zazwyczaj SQL **wybierz** instrukcji. Długość ciągu zwróconego przez `GetSQL` jest tylko do odczytu.  
  
 Długość ciągu zwróconego przez `GetSQL` zwykle różni się od dowolnego ciągu może przekazano do zestawu rekordów w `lpszSQL` parametr **Otwórz** funkcję elementu członkowskiego. Jest to spowodowane zestawu rekordów tworzy pełną instrukcję SQL oparte na przekazany do **Otwórz**, określona z ClassWizard, jaki podano w **m_strFilter** i `m_strSort` elementy członkowskie danych i podano parametrów. Aby szczegółowe informacje dotyczące sposobu zestawu rekordów konstruuje tej instrukcji SQL, zobacz artykuł [zestaw rekordów: jak zestawy rekordów wybierz rekordów (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).  
  
> [!NOTE]
>  Wywołanie tej funkcji Członkowskich tylko po wywołaniu [Otwórz](#open).  
  
##  <a name="gettablename"></a>  CRecordset::GetTableName  
 Pobiera nazwę tabeli SQL, na której oparto zapytania w zestawie rekordów.  
  
```  
const CString& GetTableName() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A **const** odwołanie do `CString` zawierający tabeli nazw, jeśli zestaw rekordów jest oparte na dla tabeli, a w przeciwnym razie ciągiem pustym.  
  
### <a name="remarks"></a>Uwagi  
 `GetTableName` jest prawidłowa, jeśli zestaw rekordów jest oparty na tabeli nie sprzężenia wiele tabel lub wstępnie zdefiniowanego zapytania (procedury składowanej). Nazwa jest tylko do odczytu.  
  
> [!NOTE]
>  Wywołanie tej funkcji Członkowskich tylko po wywołaniu [Otwórz](#open).  
  
##  <a name="isbof"></a>  CRecordset::IsBOF  
 Zwraca wartość niezerową, jeśli zestaw rekordów ma zostać umieszczony przed pierwszy rekord. Brak bieżącego rekordu.  
  
```  
BOOL IsBOF() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli zestaw nie zawiera żadnych rekordów lub jeśli były przewijane wstecz przed pierwszy rekord. w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie funkcji członkowskiej przed przewiń z rekordu do rekordu, aby dowiedzieć się czy przeszły przed pierwszy rekord zestawu rekordów. Można również użyć `IsBOF` wraz z programem `IsEOF` czy zestaw rekordów zawiera rekordy, czy jest pusta. Natychmiast po wywołaniu metody **Otwórz**, jeśli zestaw nie zawiera żadnych rekordów `IsBOF` zwraca różną od zera. Po otwarciu rekordów, który ma co najmniej jeden rekord pierwszy rekord jest bieżącego rekordu i `IsBOF` zwraca wartość 0.  
  
 Jeśli pierwszy rekord jest bieżącego rekordu i wywołania `MovePrev`, `IsBOF` następnie zwróci różną od zera. Jeśli `IsBOF` zwraca różną od zera i można wywołać `MovePrev`, wystąpi błąd. Jeśli `IsBOF` zwraca różną od zera, bieżący rekord jest niezdefiniowane i dowolną akcję, która wymaga bieżącego rekordu spowoduje błąd.  
  
### <a name="example"></a>Przykład  
 W tym przykładzie użyto `IsBOF` i `IsEOF` aby wykryć limitów zestaw rekordów do zestawu rekordów w obu kierunkach przewijania kod.  
  
 [!code-cpp[NVC_MFCDatabase#25](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]  
  
##  <a name="isdeleted"></a>  CRecordset::IsDeleted  
 Określa, czy bieżący rekord został usunięty.  
  
```  
BOOL IsDeleted() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli zestaw rekordów jest ustawiony na usunięty rekord; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli przewiń do rekordu i `IsDeleted` zwraca **TRUE** (niezerowej), następnie należy przewijania do innego rekordu przed wykonaniem innych operacji w zestawie rekordów.  
  
 Wynik `IsDeleted` zależy od wielu czynników, takich jak danego typu zestawu rekordów, czy zestawu rekordów nadaje się do aktualizacji, czy określona **CRecordset::skipDeletedRecords** opcję po otwarciu zestawu rekordów, czy użytkownika pakiety sterowników usunięte rekordy, oraz czy jest wielu użytkowników.  
  
 Aby uzyskać więcej informacji na temat **CRecordset::skipDeletedRecords** i sterownika, pakowanie, zobacz [Otwórz](#open) funkcję elementu członkowskiego.  
  
> [!NOTE]
>  Jeśli zaimplementowano zbiorcze pobieranie z wiersza, powinien nie wywołanie `IsDeleted`. Zamiast tego wywołać [GetRowStatus](#getrowstatus) funkcję elementu członkowskiego. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="iseof"></a>  CRecordset::IsEOF  
 Zwraca wartość niezerową, jeśli zestaw rekordów zawiera została ustawiona za ostatni rekord. Brak bieżącego rekordu.  
  
```  
BOOL IsEOF() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli zestaw nie zawiera żadnych rekordów lub jeśli były przewijane poza ostatni rekord; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie funkcji członkowskiej przewijania z rekordu do rekordu, aby dowiedzieć się czy przeszły poza ostatni rekord zestawu rekordów. Można również użyć `IsEOF` czy zestaw rekordów zawiera rekordy, czy jest pusta. Natychmiast po wywołaniu metody **Otwórz**, jeśli zestaw nie zawiera żadnych rekordów `IsEOF` zwraca różną od zera. Po otwarciu rekordów, który ma co najmniej jeden rekord pierwszy rekord jest bieżącego rekordu i `IsEOF` zwraca wartość 0.  
  
 Jeśli ostatni rekord jest bieżącego rekordu podczas wywoływania `MoveNext`, `IsEOF` następnie zwróci różną od zera. Jeśli `IsEOF` zwraca różną od zera i można wywołać `MoveNext`, wystąpi błąd. Jeśli `IsEOF` zwraca różną od zera, bieżący rekord jest niezdefiniowane i dowolną akcję, która wymaga bieżącego rekordu spowoduje błąd.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [IsBOF](#isbof).  
  
##  <a name="isfielddirty"></a>  CRecordset::IsFieldDirty  
 Określa, czy element członkowski danych określone pole zostało zmienione od [Edytuj](#edit) lub [AddNew](#addnew) została wywołana.  
  
```  
BOOL IsFieldDirty(void* pv);
```  
  
### <a name="parameters"></a>Parametry  
 `pv`  
 Wskaźnik do elementu danych pola, których stan chcesz sprawdzić, lub **NULL** ustalenie, czy dowolna z pól jest zanieczyszczony.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli element członkowski danych określonego pola uległ zmianie od czasu wywołania `AddNew` lub **Edytuj**; w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Dane w wszystkie elementy członkowskie danych pola z zanieczyszczeniu zostanie przeniesiona do rekordu w źródle danych podczas aktualizacji przez wywołanie do bieżącego rekordu [aktualizacji](#update) funkcji członkowskiej klasy `CRecordset` (po wywołaniu **Edytuj**lub `AddNew`).  
  
> [!NOTE]
>  Ta funkcja członkowska nie ma zastosowania na zestawy rekordów, które korzystają z zbiorcze pobieranie z wiersza. Jeśli zaimplementowano zbiorcze pobieranie z wiersza, następnie `IsFieldDirty` zawsze zwraca **FALSE** i spowoduje potwierdzenia nie powiodło się. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Wywoływanie `IsFieldDirty` spowoduje zresetowanie efekty poprzednich wywołań [SetFieldDirty](#setfielddirty) od stanu zanieczyszczone pola jest ponownie oceniane. W `AddNew` przypadku, jeśli bieżąca wartość pola różni się od wartości null pseudo pole Stan jest ustawiony jako zakłócone. W **Edytuj** wielkość liter, jeśli wartość pola różni się od wartość w pamięci podręcznej, stan pola przybiera wartość zanieczyszczone.  
  
 `IsFieldDirty` jest implementowane za pośrednictwem [DoFieldExchange](#dofieldexchange).  
  
 Aby uzyskać więcej informacji o zanieczyszczeniu flagi, zobacz artykuł [zestaw rekordów: jak zestawy rekordów wybierz rekordów (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).  
  
##  <a name="isfieldnull"></a>  CRecordset::IsFieldNull  
 Zwraca wartość niezerową, jeśli określone pole bieżącego rekordu ma wartość Null (nie ma wartości).  
  
```  
BOOL IsFieldNull(void* pv);
```  
  
### <a name="parameters"></a>Parametry  
 `pv`  
 Wskaźnik do elementu danych pola, których stan chcesz sprawdzić, lub **NULL** ustalenie, czy dowolna z pola jest Null.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli element członkowski danych określone pole jest oznaczony jako wartość Null; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji elementu członkowskiego, aby określić, czy element członkowski danych określonego pola rekordów zostały oznaczone jako wartość Null. (W terminologii bazy danych o wartości Null oznacza, że "o wartości" i nie jest taka sama jak **NULL** w języku C++.) Element członkowski danych pola jest oznaczony jako wartość Null, jest interpretowany jako kolumnę bieżącego rekordu, dla którego nie ma żadnej wartości.  
  
> [!NOTE]
>  Ta funkcja członkowska nie ma zastosowania na zestawy rekordów, które korzystają z zbiorcze pobieranie z wiersza. Jeśli zaimplementowano zbiorcze pobieranie z wiersza, następnie `IsFieldNull` zawsze zwraca **FALSE** i spowoduje potwierdzenia nie powiodło się. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 `IsFieldNull` jest implementowane za pośrednictwem [DoFieldExchange](#dofieldexchange).  
  
##  <a name="isfieldnullable"></a>  CRecordset::IsFieldNullable  
 Zwraca wartość niezerową, jeśli określone pole bieżącego rekordu można ustawić wartości null (o wartości).  
  
```  
BOOL IsFieldNullable(void* pv);
```  
  
### <a name="parameters"></a>Parametry  
 `pv`  
 Wskaźnik do elementu danych pola, których stan chcesz sprawdzić, lub **NULL** ustalenie, jeśli żadnego pola można ustawić na wartość Null.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji Członkowskich, aby ustalić, czy element członkowski danych określone pole "nullable" (może być ustawiony na wartość Null; C++ **NULL** nie jest taka sama jak wartość Null, co w terminologii bazy danych, oznacza to "o wartości").  
  
> [!NOTE]
>  Jeśli zaimplementowano zbiorcze pobieranie z wiersza, nie można wywołać `IsFieldNullable`. Zamiast tego wywołać [GetODBCFieldInfo](#getodbcfieldinfo) funkcji członkowskiej, aby określić, czy pole można ustawić na wartość Null. Należy pamiętać, że zawsze można wywołać `GetODBCFieldInfo`, niezależnie od tego, czy zostały zaimplementowane zbiorcze pobieranie z wiersza. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Pola, które nie może mieć wartości Null, musi mieć wartość. Jeśli spróbujesz ustawić na wartość Null, podczas dodawania lub aktualizowania rekordu takiego pola źródła danych odrzuca dodanie lub aktualizacja, i [aktualizacji](#update) spowoduje zgłoszenie wyjątku. Wyjątek występuje po wywołaniu **aktualizacji**, nie w przypadku wywołania [SetFieldNull](#setfieldnull).  
  
 Przy użyciu **NULL** dla pierwszy argument funkcji będą stosowane tylko do funkcji **outputColumn** pól nie **param** pola. Na przykład wywołanie  
  
 [!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 zostanie ustawiona tylko **outputColumn** pól do **NULL**; **param** pól będzie to miało wpływu.  
  
 Do pracy nad **param** pól, należy podać rzeczywiste adres poszczególne **param** chcesz pracować, takich jak:  
  
 [!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 Oznacza to, nie można ustawić wszystkie **param** pól do **NULL**, jak w przypadku **outputColumn** pól.  
  
 `IsFieldNullable` jest implementowane za pośrednictwem [DoFieldExchange](#dofieldexchange).  
  
##  <a name="isopen"></a>  CRecordset::IsOpen  
 Określa, czy zestaw rekordów jest już otwarty.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli podano niezerowe obiekty zestawów rekordów [Otwórz](#open) lub [Requery](#requery) wcześniej została wywołana funkcja elementu członkowskiego i nie została zamknięta zestawu rekordów; w przeciwnym razie wartość 0.  
  
##  <a name="m_hstmt"></a>  CRecordset::m_hstmt  
 Zawiera dojście do struktury danych ODBC instrukcji typu **HSTMT**skojarzonych z zestawu rekordów.  
  
### <a name="remarks"></a>Uwagi  
 Każde zapytanie do źródła danych ODBC jest skojarzony z **HSTMT**.  
  
> [!CAUTION]
>  Nie używaj **m_hstmt** przed [Otwórz](#open) została wywołana.  
  
 Zwykle nie trzeba uzyskać dostępu do **HSTMT** bezpośrednio, ale trzeba bezpośrednie wykonywanie instrukcji SQL. `ExecuteSQL` Funkcji członkowskiej klasy `CDatabase` zawiera przykład za pomocą **m_hstmt**.  
  
##  <a name="m_nfields"></a>  CRecordset::m_nFields  
 Zawiera liczbę elementy członkowskie danych pola w klasie rekordów; oznacza to, że liczba kolumn wybranych przez zestaw rekordów ze źródła danych.  
  
### <a name="remarks"></a>Uwagi  
 Konstruktor dla klasy rekordów musi inicjować `m_nFields` z prawidłową liczbą. Jeśli nie zaimplementowano wiersza zbiorcze pobieranie, ClassWizard zapisuje ten inicjowania dla Ciebie można użyć do zadeklarowania klasy zestawu rekordów. Można również napisać go ręcznie.  
  
 Platformę używa tego numeru do zarządzania interakcji między elementy członkowskie danych pola i odpowiednie kolumny bieżącego rekordu w źródle danych.  
  
> [!CAUTION]
>  Ta liczba musi odpowiadać "kolumn danych wyjściowych" zarejestrowanego w `DoFieldExchange` lub `DoBulkFieldExchange` po wywołaniu [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) z parametrem **CFieldExchange::outputColumn**.  
  
 Można powiązać kolumny dynamicznie, jak wyjaśniono w artykule "zestaw rekordów: dynamiczne powiązanie kolumn danych." Jeśli tak zrobisz, należy zwiększyć liczbę w `m_nFields` do uwzględnienia liczba funkcji RFX lub RFX zbiorczego wywołań Twojej `DoFieldExchange` lub `DoBulkFieldExchange` funkcji członkowskiej dla dynamicznie powiązane kolumny.  
  
 Aby uzyskać więcej informacji, zobacz artykuły [zestaw rekordów: dynamiczne wiązanie danych kolumn (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) i [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Przykład  
 Zapoznaj się z artykułem [wymiana pól rekordów: za pomocą RFX](../../data/odbc/record-field-exchange-using-rfx.md).  
  
##  <a name="m_nparams"></a>  CRecordset::m_nParams  
 Zawiera liczbę elementy członkowskie danych parametru w klasie rekordów; oznacza to, że liczba parametrów przekazany z zapytaniem w zestawie rekordów.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli klasa zestaw rekordów zawiera wszystkie elementy członkowskie danych parametru, Konstruktor klasy musi inicjować `m_nParams` z prawidłową liczbą. Wartość `m_nParams` wartość domyślna to 0. Jeśli dodasz elementy członkowskie danych parametru (które należy wykonać ręcznie) musisz również ręcznie dodać inicjowania w konstruktorze klasy w celu odzwierciedlenia z liczbą parametrów (musi być przynajmniej tak duże jak liczba '' symbole zastępcze w Twojej **m_strFilter**  lub `m_strSort` ciągu).  
  
 Platformę używa tego numeru przy jego parameterizes zapytania w zestawie rekordów.  
  
> [!CAUTION]
>  Ten numer musi odpowiadać numerowi "params" zarejestrowany w `DoFieldExchange` lub `DoBulkFieldExchange` po wywołaniu [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) z wartością parametru **CFieldExchange::inputParam**,  **CFieldExchange::param**, **CFieldExchange::outputParam**, lub **CFieldExchange::inoutParam**.  
  
### <a name="example"></a>Przykład  
  Zobacz artykuły [zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) i [wymiana pól rekordów: za pomocą RFX](../../data/odbc/record-field-exchange-using-rfx.md).  
  
##  <a name="m_pdatabase"></a>  CRecordset::m_pDatabase  
 Zawiera wskaźnik do `CDatabase` obiektu za pomocą których zestaw rekordów jest połączony ze źródłem danych.  
  
### <a name="remarks"></a>Uwagi  
 Ta zmienna jest ustawiona na dwa sposoby. Zazwyczaj przekazać wskaźnik do już połączoną `CDatabase` obiektu podczas konstruowania obiektu zestawu rekordów. W przypadku przekazania **NULL** zamiast `CRecordset` tworzy `CDatabase` obiektu dla Ciebie i łączy go. W obu przypadkach `CRecordset` przechowuje wskaźnika w tej zmiennej.  
  
 Zwykle nie bezpośrednio należy używać wskaźnika przechowywane w **m_pDatabase**. Jeśli piszesz własnych rozszerzeń `CRecordset`, jednak czasami trzeba używać wskaźnika. Na przykład może być potrzebny wskaźnik generowanie własnego `CDBException`s. Lub może być potrzebny go należy zrobić coś korzystającej z tego samego `CDatabase` obiektu, na przykład przeprowadzania transakcji, ustawienia limitów czasu, lub wywoływania `ExecuteSQL` funkcji członkowskiej klasy `CDatabase` do wykonywania instrukcji SQL bezpośrednio.  
  
##  <a name="m_strfilter"></a>  CRecordset::m_strFilter  
 Po utworzenia obiekt zestawu rekordów, ale przed wywołaniem jego **Otwórz** elementu członkowskiego działania, użyj tego elementu członkowskiego danych do przechowywania `CString` zawierający SQL **gdzie** klauzuli.  
  
### <a name="remarks"></a>Uwagi  
 Zestaw rekordów używa tego ciągu do ograniczyć (lub filtrowanie) rekordy zostanie wybrana podczas **Otwórz** lub **Requery** wywołania. Jest to przydatne w przypadku wybierając podzbiór rekordów, takich jak "wszystkich sprzedawców na Kalifornijskiej" ("Stan = urzędu certyfikacji"). Składnia ODBC SQL **gdzie** jest klauzula  
  
 `WHERE search-condition`  
  
 Należy pamiętać, że nie ma **gdzie** — słowo kluczowe w ciągu. Platformę udostępnia go.  
  
 Można również parametryzacja ciągu filtru, umieszczając '' symbole zastępcze w ramach tego deklarującego element członkowski danych parametru w klasie dla każdego symbolu zastępczego i przekazywanie parametrów do zestawu rekordów w czasie wykonywania. Dzięki temu można utworzyć filtr w czasie wykonywania. Aby uzyskać więcej informacji, zobacz artykuł [zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
 Aby uzyskać więcej informacji na temat SQL **gdzie** klauzule, zapoznaj się z artykułem [SQL](../../data/odbc/sql.md). Aby uzyskać więcej informacji na temat wybierania i filtrowanie rekordów, zobacz artykuł [zestaw rekordów: filtrowanie rekordów (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDatabase#30](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]  
  
##  <a name="m_strsort"></a>  CRecordset::m_strSort  
 Po utworzenia obiekt zestawu rekordów, ale przed wywołaniem jego **Otwórz** elementu członkowskiego działania, użyj tego elementu członkowskiego danych do przechowywania `CString` zawierający SQL **ORDER BY** klauzuli.  
  
### <a name="remarks"></a>Uwagi  
 Zestaw rekordów używa tego ciągu do sortowania rekordów jest ona wybierana podczas **Otwórz** lub **Requery** wywołania. Ta funkcja służy do sortowania zestawu rekordów na co najmniej jedną kolumnę. Składnia ODBC SQL **ORDER BY** klauzula jest  
  
 `ORDER BY sort-specification [, sort-specification]...`  
  
 gdzie specyfikacji sortowania jest liczbą całkowitą lub nazwę kolumny. Można również określić kolejność rosnącą lub malejącą (kolejność rosnąca domyślnie), przez dołączenie do listy kolumn w ciągu sort "ASC" lub "Opis". Wybrane rekordy są sortowane najpierw pierwszej kolumny na liście, a następnie sekundy i tak dalej. Na przykład może order zestawu rekordów "Klientów" nazwisko, a następnie imię. Liczba kolumn, które można wyświetlić listę zależy od źródła danych. Aby uzyskać więcej informacji zobacz zestaw Windows SDK.  
  
 Należy pamiętać, że nie ma **ORDER BY** — słowo kluczowe w ciągu. Platformę udostępnia go.  
  
 Aby uzyskać więcej informacji na temat klauzule SQL, zobacz artykuł [SQL](../../data/odbc/sql.md). Aby uzyskać więcej informacji na temat sortowanie rekordów, zobacz artykuł [zestaw rekordów: sortowanie rekordów (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDatabase#31](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]  
  
##  <a name="move"></a>  CRecordset::Move  
 Przenosi bieżący wskaźnik rekordów w zestawie rekordów do przodu lub do tyłu.  
  
```  
virtual void Move(
    long nRows,  
    WORD wFetchType = SQL_FETCH_RELATIVE);
```  
  
### <a name="parameters"></a>Parametry  
 `nRows`  
 Liczba wierszy do przeniesienia do przodu i do tyłu. Wartości dodatnie do przodu, Przenieś stronę końca zestawu rekordów. Wartości ujemne Wstecz, Przenieś stronę początku.  
  
 `wFetchType`  
 Określa zestaw wierszy który **Przenieś** spowoduje pobranie. Aby uzyskać więcej informacji zobacz uwagi.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku przekazania wartości 0 dla `nRows`, **Przenieś** Odświeża bieżący rekord; **Przenieś** zakończy wszystkie bieżące `AddNew` lub **Edytuj** trybie i spowoduje przywrócenie bieżącego rekordu wartości przed `AddNew` lub **Edytuj** została wywołana.  
  
> [!NOTE]
>  W przypadku przenoszenia do zestawu rekordów, nie można pominąć usuniętych rekordów. Zobacz [CRecordset::IsDeleted](#isdeleted) Aby uzyskać więcej informacji. Po otwarciu `CRecordset` z **skipDeletedRecords** opcji set, **Przenieś** potwierdzeń, jeśli `nRows` parametru jest 0. To zachowanie zapobiega odświeżania wierszy, które zostaną usunięte przez inne aplikacje klienckie przy użyciu tych samych danych. Zobacz `dwOption` parametru w [Otwórz](#open) opis **skipDeletedRecords**.  
  
 **Przenieś** zmiana zestawu rekordów przez zestawy wierszy. Na podstawie wartości dla `nRows` i `wFetchType`, **Przenieś** pobiera odpowiednie wierszy i następnie sprawia, że pierwszy rekord w tym zestawie wierszy bieżącego rekordu. Jeśli nie zaimplementowano zbiorcze pobieranie z wiersza, następnie rozmiar zestawu wierszy ma zawsze numer 1. Podczas pobierania zestawu wierszy **Przenieś** bezpośrednio wywołuje [CheckRowsetError](#checkrowseterror) funkcji członkowskiej do obsługi błędów wynikających z pobierania.  
  
 W zależności od wartości należy przekazać **Przenieś** jest odpowiednikiem innych `CRecordset` funkcji elementów członkowskich. W szczególności wartość `wFetchType` może wskazywać funkcji członkowskiej, która jest bardziej intuicyjne i często preferowaną metodą przenoszenie bieżącego rekordu.  
  
 W poniższej tabeli przedstawiono możliwe wartości `wFetchType`, zestaw wierszy który **Przenieś** spowoduje pobranie na podstawie `wFetchType` i `nRows`i dowolnej funkcji Członkowskich równoważne odpowiadający `wFetchType`.  
  
|wFetchType|Pobranych wierszy|Funkcja członkowska równoważne|  
|----------------|--------------------|--------------------------------|  
|`SQL_FETCH_RELATIVE` (wartość domyślna)|Uruchamianie zestawu wierszy `nRows` wiersze z pierwszego wiersza w bieżącym zestawie wierszy.||  
|`SQL_FETCH_NEXT`|Zestaw wierszy dalej; `nRows` jest ignorowana.|[MoveNext](#movenext)|  
|`SQL_FETCH_PRIOR`|Poprzedniego zestawu wierszy; `nRows` jest ignorowana.|[MovePrev](#moveprev)|  
|`SQL_FETCH_FIRST`|Pierwszy zestaw wierszy w zestawie rekordów; `nRows` jest ignorowana.|[MoveFirst](#movefirst)|  
|`SQL_FETCH_LAST`|Ostatni pełny zestaw wierszy w zestawie rekordów; `nRows` jest ignorowana.|[MoveLast](#movelast)|  
|`SQL_FETCH_ABSOLUTE`|Jeśli `nRows` > 0, zestaw wierszy uruchamianie `nRows` wiersze od początku zestawu rekordów. Jeśli `nRows` < 0, zestaw wierszy uruchamianie `nRows` wiersze na końcu zestawu rekordów. Jeśli `nRows` = 0, zwracana jest warunek początku pliku (BOF).|[SetAbsolutePosition](#setabsoluteposition)|  
|`SQL_FETCH_BOOKMARK`|Zestaw wierszy, zaczynając od wiersza, którego wartość zakładki odpowiada `nRows`.|[SetBookmark](#setbookmark)|  
  
> [!NOTE]
>  Dla zestawów rekordów tylko do przodu **Przenieś** jest prawidłowy tylko dla wartości `SQL_FETCH_NEXT` dla `wFetchType`.  
  
> [!CAUTION]
>  Wywoływanie **Przenieś** zgłasza wyjątek, jeśli zestaw nie zawiera żadnych rekordów. Aby ustalić, czy zestaw rekordów zawiera rekordy, należy wywołać [IsBOF](#isbof) i [IsEOF](#iseof).  
  
> [!NOTE]
>  Jeśli były przewijane upłynął na początku lub na końcu zestawu rekordów ( `IsBOF` lub `IsEOF` zwraca różną od zera), wywoływania **Przenieś** prawdopodobnie zgłosi funkcja `CDBException`. Na przykład jeśli `IsEOF` zwraca różną od zera i `IsBOF` nie, następnie `MoveNext` spowoduje zgłoszenie wyjątku, ale `MovePrev` nie.  
  
> [!NOTE]
>  Jeśli należy wywołać **Przenieś** podczas bieżącego rekordu zaktualizowane lub dodane aktualizacje zostaną utracone bez ostrzeżenia.  
  
 Aby uzyskać więcej informacji na temat nawigacji zestawu rekordów, zobacz artykuły [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) i [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Aby uzyskać odpowiednie informacje, zobacz opis funkcji interfejsu API ODBC **procedury SQLExtendedFetch** w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDatabase#28](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]  
  
##  <a name="movefirst"></a>  CRecordset::MoveFirst  
 Sprawia, że pierwszy rekord pierwszy zestaw wierszy bieżącego rekordu.  
  
```  
void MoveFirst();
```  
  
### <a name="remarks"></a>Uwagi  
 Niezależnie od tego, czy zbiorcze pobieranie z wiersza został zaimplementowany będzie zawsze pierwszy rekord w zestawie rekordów.  
  
 Nie trzeba wywołać **MoveFirst** bezpośrednio po otwarciu zestawu rekordów. W tym czasie pierwszy rekord (jeśli istnieje) jest automatycznie bieżącego rekordu.  
  
> [!NOTE]
>  Ta funkcja członkowska nie jest prawidłowy dla zestawów rekordów tylko do przodu.  
  
> [!NOTE]
>  W przypadku przenoszenia do zestawu rekordów, nie można pominąć usuniętych rekordów. Zobacz [IsDeleted](#isdeleted) funkcji członkowskiej, aby uzyskać szczegółowe informacje.  
  
> [!CAUTION]
>  Wywoływanie poszczególnych **Przenieś** funkcje zgłasza wyjątek, jeśli zestaw nie zawiera żadnych rekordów. Aby ustalić, czy zestaw rekordów zawiera rekordy, należy wywołać `IsBOF` i `IsEOF`.  
  
> [!NOTE]
>  Jeśli należy wywołać dowolną z **Przenieś** funkcji podczas bieżącego rekordu zaktualizowane lub dodane aktualizacje zostaną utracone bez ostrzeżenia.  
  
 Aby uzyskać więcej informacji na temat nawigacji zestawu rekordów, zobacz artykuły [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) i [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [IsBOF](#isbof).  
  
##  <a name="movelast"></a>  CRecordset::MoveLast  
 Sprawia, że pierwszy rekord w ostatnich wierszy pełną bieżącego rekordu.  
  
```  
void MoveLast();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli nie zaimplementowano zbiorcze pobieranie z wiersza, zestawu rekordów ma rozmiar wierszy 1, więc `MoveLast` po prostu przenosi do ostatniego rekordu w zestawie rekordów.  
  
> [!NOTE]
>  Ta funkcja członkowska nie jest prawidłowy dla zestawów rekordów tylko do przodu.  
  
> [!NOTE]
>  W przypadku przenoszenia do zestawu rekordów, nie można pominąć usuniętych rekordów. Zobacz [IsDeleted](#isdeleted) funkcji członkowskiej, aby uzyskać szczegółowe informacje.  
  
> [!CAUTION]
>  Wywoływanie poszczególnych **Przenieś** funkcje zgłasza wyjątek, jeśli zestaw nie zawiera żadnych rekordów. Aby ustalić, czy zestaw rekordów zawiera rekordy, należy wywołać `IsBOF` i `IsEOF`.  
  
> [!NOTE]
>  Jeśli należy wywołać dowolną z **Przenieś** funkcji podczas bieżącego rekordu zaktualizowane lub dodane aktualizacje zostaną utracone bez ostrzeżenia.  
  
 Aby uzyskać więcej informacji na temat nawigacji zestawu rekordów, zobacz artykuły [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) i [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [IsBOF](#isbof).  
  
##  <a name="movenext"></a>  CRecordset::MoveNext  
 Sprawia, że pierwszy rekord w zestawie wierszy dalej bieżącego rekordu.  
  
```  
void MoveNext();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli nie zaimplementowano zbiorcze pobieranie z wiersza, zestawu rekordów ma rozmiar wierszy 1, więc `MoveNext` po prostu przechodzi do następnego rekordu.  
  
> [!NOTE]
>  W przypadku przenoszenia do zestawu rekordów, nie można pominąć usuniętych rekordów. Zobacz [IsDeleted](#isdeleted) funkcji członkowskiej, aby uzyskać szczegółowe informacje.  
  
> [!CAUTION]
>  Wywoływanie poszczególnych **Przenieś** funkcje zgłasza wyjątek, jeśli zestaw nie zawiera żadnych rekordów. Aby ustalić, czy zestaw rekordów zawiera rekordy, należy wywołać `IsBOF` i `IsEOF`.  
  
> [!NOTE]
>  Zalecane jest również, że należy wywołać `IsEOF` przed wywołaniem `MoveNext`. Na przykład, jeśli były przewijane poza końcem zestawu rekordów `IsEOF` , którą będzie zwracać niezerowy; kolejne wywołanie `MoveNext` spowoduje zgłoszenie wyjątku.  
  
> [!NOTE]
>  Jeśli należy wywołać dowolną z **Przenieś** funkcji podczas bieżącego rekordu zaktualizowane lub dodane aktualizacje zostaną utracone bez ostrzeżenia.  
  
 Aby uzyskać więcej informacji na temat nawigacji zestawu rekordów, zobacz artykuły [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) i [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [IsBOF](#isbof).  
  
##  <a name="moveprev"></a>  CRecordset::MovePrev  
 Sprawia, że pierwszy rekord w poprzednim wierszy bieżącego rekordu.  
  
```  
void MovePrev();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli nie zaimplementowano zbiorcze pobieranie z wiersza, zestawu rekordów ma rozmiar wierszy 1, więc `MovePrev` po prostu przenosi do poprzedniego rekordu.  
  
> [!NOTE]
>  Ta funkcja członkowska nie jest prawidłowy dla zestawów rekordów tylko do przodu.  
  
> [!NOTE]
>  W przypadku przenoszenia do zestawu rekordów, nie można pominąć usuniętych rekordów. Zobacz [IsDeleted](#isdeleted) funkcji członkowskiej, aby uzyskać szczegółowe informacje.  
  
> [!CAUTION]
>  Wywoływanie poszczególnych **Przenieś** funkcje zgłasza wyjątek, jeśli zestaw nie zawiera żadnych rekordów. Aby ustalić, czy zestaw rekordów zawiera rekordy, należy wywołać `IsBOF` i `IsEOF`.  
  
> [!NOTE]
>  Zalecane jest również, że należy wywołać `IsBOF` przed wywołaniem `MovePrev`. Na przykład, jeśli były przewijane przed początek zestawu rekordów `IsBOF` , którą będzie zwracać niezerowy; kolejne wywołanie `MovePrev` spowoduje zgłoszenie wyjątku.  
  
> [!NOTE]
>  Jeśli należy wywołać dowolną z **Przenieś** funkcji podczas bieżącego rekordu zaktualizowane lub dodane aktualizacje zostaną utracone bez ostrzeżenia.  
  
 Aby uzyskać więcej informacji na temat nawigacji zestawu rekordów, zobacz artykuły [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) i [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [IsBOF](#isbof).  
  
##  <a name="onsetoptions"></a>  CRecordset::OnSetOptions  
 Wywołuje się, by ustawić opcje (używane na wybór) określona w instrukcji ODBC.  
  
```  
virtual void OnSetOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>Parametry  
 `hstmt`  
 **HSTMT** instrukcji ODBC, którego opcje mają być tworzone.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie `OnSetOptions` można ustawić opcje (używane na wybór) określona w instrukcji ODBC. Struktura wywołuje tę funkcję elementu członkowskiego, aby ustawić opcje początkowego zestawu rekordów. `OnSetOptions` Określa źródło danych obsługi przewijanego kursory i współbieżność kursora i odpowiednio ustawia opcje w zestawie rekordów. (Natomiast `OnSetOptions` jest używane dla operacji wyboru `OnSetUpdateOptions` jest używane dla operacji update.)  
  
 Zastąpienie `OnSetOptions` Aby ustawić opcje określonego sterownika lub źródła danych. Na przykład, jeśli źródło danych obsługuje otwieranie w trybie wyłączności, mogą zastąpić `OnSetOptions` mógł korzystać z tej możliwości.  
  
 Aby uzyskać więcej informacji na temat kursorów, zobacz artykuł [ODBC](../../data/odbc/odbc-basics.md).  
  
##  <a name="onsetupdateoptions"></a>  CRecordset::OnSetUpdateOptions  
 Wywołuje się, by ustawić opcje (używane na aktualizację) określona w instrukcji ODBC.  
  
```  
virtual void OnSetUpdateOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>Parametry  
 `hstmt`  
 **HSTMT** instrukcji ODBC, którego opcje mają być tworzone.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie `OnSetUpdateOptions` można ustawić opcje (używane na aktualizację) określona w instrukcji ODBC. Struktura wywołuje funkcji członkowskiej po utworzeniu HSTMT do aktualizowania rekordów w zestawie rekordów. (Natomiast `OnSetOptions` jest używane dla operacji wyboru `OnSetUpdateOptions` jest używane dla operacji update.) `OnSetUpdateOptions` określa obsługi źródła danych dla przewijanego kursory i współbieżność kursora i odpowiednio ustawia opcje w zestawie rekordów.  
  
 Zastąpienie `OnSetUpdateOptions` Aby ustawić opcje instrukcji ODBC, zanim będzie można użyć tej instrukcji dostępu do bazy danych.  
  
 Aby uzyskać więcej informacji na temat kursorów, zobacz artykuł [ODBC](../../data/odbc/odbc-basics.md).  
  
##  <a name="open"></a>  CRecordset::Open  
 Zostanie otwarty zestaw rekordów przez pobieranie tabeli lub wykonywania zapytania, który reprezentuje zestaw rekordów.  
  
```  
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,  
    LPCTSTR lpszSQL = NULL,  
    DWORD dwOptions = none);
```  
  
### <a name="parameters"></a>Parametry  
 `nOpenType`  
 Zaakceptuj wartość domyślną **AFX_DB_USE_DEFAULT_TYPE**, lub użyj jednego z następujących wartości z **wyliczenia OpenType**:  
  
- **CRecordset::dynaset** rekordów z dwukierunkowym przewijania. Członkostwo i kolejność rekordów są ustalane w momencie otwarcia zestawu rekordów, ale zmiany wprowadzone przez innych użytkowników do wartości danych są widoczne, po operacji pobierania. Zestawy dynamiczne są nazywane również oparte na zestawie kluczy zestawów rekordów.  
  
- **CRecordset::snapshot** statycznych rekordów z dwukierunkowym przewijania. Członkostwo i kolejność rekordów są ustalane w momencie otwarcia zestawu rekordów; wartości danych są ustalane w momencie są pobierane rekordy. Zmiany wprowadzone przez innych użytkowników nie są widoczne do czasu zamknięcia i ponownego otwarcia zestawu rekordów.  
  
- **CRecordset::dynamic** rekordów z dwukierunkowym przewijania. Zmiany wprowadzone przez innych użytkowników wartości członkostwa, kolejność i dane są widoczne, po operacji pobierania. Należy pamiętać, że wiele sterowników ODBC nie obsługuje tego typu zestawu rekordów.  
  
- **CRecordset::forwardOnly** zestaw rekordów tylko do odczytu z przewijanie tylko do przodu.  
  
     Aby uzyskać `CRecordset`, wartością domyślną jest **CRecordset::snapshot**. Mechanizm wartości domyślnej pozwala kreatorów Visual C++ do interakcji z obu ODBC `CRecordset` i DAO `CDaoRecordset`, które mają różne wartości domyślnych.  
  
 Aby uzyskać więcej informacji o tych typów rekordów, zobacz artykuł [zestawu rekordów (ODBC)](../../data/odbc/recordset-odbc.md). Aby uzyskać odpowiednie informacje zobacz artykuł "Za pomocą bloku i którą można przewijać kursorów" w zestawie SDK systemu Windows.  
  
> [!CAUTION]
>  Jeśli nie obsługuje żądanego typu, w ramach zgłasza wyjątek.  
  
 `lpszSQL`  
 Wskaźnik ciągu zawierający jedną z następujących czynności:  
  
-   A **NULL** wskaźnika.  
  
-   Nazwa tabeli.  
  
-   SQL **wybierz** instrukcji (opcjonalnie z SQL **gdzie** lub **ORDER BY** klauzuli).  
  
-   A **WYWOŁAĆ** instrukcję, określając nazwę wstępnie zdefiniowanego zapytania (procedury składowanej). Należy zachować ostrożność, nie wstawiaj odstęp między nawias klamrowy i **WYWOŁAĆ** — słowo kluczowe.  
  
 Aby uzyskać więcej informacji na temat tego ciągu zobacz tabelę i Omówienie roli ClassWizard w obszarze uwagi.  
  
> [!NOTE]
>  Kolejność kolumn w zestawie wyników musi być zgodna z kolejnością RFX lub odwołuje się funkcja RFX zbiorczego z [DoFieldExchange](#dofieldexchange) lub [DoBulkFieldExchange](#dobulkfieldexchange) funkcji zastąpienia.  
  
 `dwOptions`  
 Maska bitów, które można określić kombinację wartości wymienionych poniżej. Niektóre z tych wzajemnie się wykluczają. Wartość domyślna to **Brak**.  
  
- **CRecordset::none** nie ustawiono opcji. Wartość tego parametru jest wykluczają się wzajemnie z innych wartości. Domyślnie zestaw rekordów może zostać zaktualizowana przy użyciu [Edytuj](#edit) lub [usunąć](#delete) i umożliwia dodanie nowych rekordów z [AddNew](#addnew). Aktualizacji zależy od źródła danych oraz jako włączona `nOpenType` opcja określono. Optymalizacja dla dodatków zbiorcze nie jest dostępna. Zbiorcze pobieranie z wiersza nie będzie zaimplementowana. Usunięte rekordy nie zostaną pominięte podczas nawigacji zestawu rekordów. Zakładki nie są dostępne. Sprawdzanie automatyczne zanieczyszczone pole jest zaimplementowana.  
  
- **CRecordset::appendOnly** nie zezwalaj na **Edytuj** lub **usunąć** w zestawie rekordów. Zezwalaj na `AddNew` tylko. Ta opcja jest wykluczają się wzajemnie z **CRecordset::readOnly**.  
  
- **CRecordset::readOnly** Otwórz zestaw rekordów jako tylko do odczytu. Ta opcja jest wykluczają się wzajemnie z **CRecordset::appendOnly**.  
  
- **CRecordset::optimizeBulkAdd** Użyj przygotowanej instrukcji SQL w celu zoptymalizowania Dodawanie wielu rekordów w tym samym czasie. Ma zastosowanie tylko wtedy, gdy nie używasz funkcji interfejsu API ODBC **SQLSetPos** można zaktualizować zestawu rekordów. Pierwsza aktualizacja określa pola, które są oznaczonych jako zakłócone. Ta opcja jest wykluczają się wzajemnie z `CRecordset::useMultiRowFetch`.  
  
- `CRecordset::useMultiRowFetch` Implementuje zbiorcze pobieranie z wiersza umożliwia wiele wierszy, które mają zostać pobrane w ramach jednego pobierania operacji. Jest to zaawansowana funkcja mające na celu poprawę wydajności; Zbiorcza wymiana pól rekordów nie jest jednak obsługiwane przez ClassWizard. Ta opcja jest wykluczają się wzajemnie z **CRecordset::optimizeBulkAdd**. Należy pamiętać, że jeśli określisz `CRecordset::useMultiRowFetch`, następnie opcję **CRecordset::noDirtyFieldCheck** zostanie włączona automatycznie (podwójnego buforowania nie będą dostępne); w zestawy rekordów tylko do przodu, opcja  **CRecordset::useExtendedFetch** zostanie włączone automatycznie. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
- **CRecordset::skipDeletedRecords** pominąć wszystkie rekordy usunięte podczas nawigowania do zestawu rekordów. Spowoduje to spowolnienie wydajności w niektórych pobraniach względną. Ta opcja nie jest prawidłowy w zestawy rekordów tylko do przodu. Wywołanie [Przenieś](#move) z `nRows` parametru wartość 0 i **CRecordset::skipDeletedRecords** opcji set, **Przenieś** będzie potwierdzenia. Należy pamiętać, że **CRecordset::skipDeletedRecords** jest podobny do *pakowania sterownik*, co oznacza, że usunięte wiersze zostaną usunięte z tego zestawu rekordów. Jednak jeśli sterownik pakietów rekordów, następnie będzie pomijane tylko te rekordy, które należy usunąć; rekordy zostały usunięte przez innych użytkowników, gdy jest otwarty zestaw rekordów nie będzie pomijane. **CRecordset::skipDeletedRecords** pominie wiersz usunięty przez innych użytkowników.  
  
- **CRecordset::useBookmarks** może używać zakładek w zestawie rekordów, jeśli jest to obsługiwane. Zakładki powolna pobieranie danych, ale poprawić wydajność nawigowanie wśród danych. Nie jest prawidłowa w zestawy rekordów tylko do przodu. Aby uzyskać więcej informacji, zobacz artykuł [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).  
  
- **CRecordset::noDirtyFieldCheck** wyłączyć automatyczne pola zanieczyszczone sprawdzanie (podwójnego buforowania). Zwiększa to wydajność; jednak należy ręcznie oznaczyć pola jako brudne wywołując `SetFieldDirty` i `SetFieldNull` funkcji elementów członkowskich. Należy pamiętać, że podwójnego buforowania w klasie `CRecordset` jest podobny do podwójnego buforowania w klasie `CDaoRecordset`. Jednak w `CRecordset`, nie można włączyć podwójnego buforowania dla poszczególnych pól; należy ją włączyć dla wszystkich pól albo wyłącz go dla wszystkich pól. Należy pamiętać, że jeśli określono opcję `CRecordset::useMultiRowFetch`, następnie **CRecordset::noDirtyFieldCheck** zostanie włączona automatycznie, jednak `SetFieldDirty` i `SetFieldNull` nie można używać dla zestawów rekordów, który implementuje zbiorcze pobieranie z wiersza.  
  
- **CRecordset::executeDirect** nie należy używać przygotowanej instrukcji SQL. Aby uzyskać lepszą wydajność, wybierz tę opcję, jeśli **Requery** nigdy nie zostanie wywołana funkcja elementu członkowskiego.  
  
- **CRecordset::useExtendedFetch** wdrożenie **procedury SQLExtendedFetch** zamiast **SQLFetch**. To jest przeznaczony do implementacji zbiorcze pobieranie z wiersza na zestawy rekordów tylko do przodu. Jeśli określono opcję `CRecordset::useMultiRowFetch` na rekordów, następnie **CRecordset::useExtendedFetch** zostanie włączone automatycznie.  
  
- **CRecordset::userAllocMultiRowBuffers** użytkownika spowoduje przydzielenie buforów magazynu danych. Użyj tej opcji w połączeniu z `CRecordset::useMultiRowFetch` Aby przydzielić własne magazynu; w przeciwnym razie platformę automatycznie przyzna niezbędne magazynu. Aby uzyskać więcej informacji, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Należy pamiętać, że określenie **CRecordset::userAllocMultiRowBuffers** bez określania `CRecordset::useMultiRowFetch` spowoduje potwierdzenia nie powiodło się.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli niezerową `CRecordset` obiekt został pomyślnie otwarty; w przeciwnym razie 0 Jeśli [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) (jeśli jest to nazywane) zwraca wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę funkcję elementu członkowskiego, aby uruchomić zapytanie, zdefiniowany przez zestaw rekordów. Przed wywołaniem **Otwórz**, należy utworzyć obiekt zestawu rekordów.  
  
 Ten zestaw rekordów połączenia ze źródłem danych zależy od tego, jak utworzyć zestaw rekordów przed wywołaniem **Otwórz**. W przypadku przekazania [cdatabase —](../../mfc/reference/cdatabase-class.md) obiekt do Konstruktora zestawu rekordów, która nie została podłączona do źródła danych używa funkcji członkowskiej [GetDefaultConnect](#getdefaultconnect) próby otwarcia obiektu bazy danych. W przypadku przekazania **NULL** do Konstruktora zestawu rekordów, tworzy konstruktora `CDatabase` obiektu, i **Otwórz** próbuje połączyć obiekt bazy danych. Aby uzyskać szczegółowe informacje na zamknięcie zestawu rekordów i połączenia tych różnych okolicznościach, zobacz [Zamknij](#close).  
  
> [!NOTE]
>  Dostęp do źródła danych za pośrednictwem `CRecordset` udostępnić obiektu, jest zawsze. W odróżnieniu od `CDaoRecordset` klasa, nie można użyć `CRecordset` obiekt, aby otworzyć źródła danych z wyłącznego dostępu.  
  
 Podczas wywoływania **Otwórz**, zapytania, zwykle SQL **wybierz** instrukcji, wybiera rekordów w oparciu o kryteria, pokazano w poniższej tabeli.  
  
|Wartość parametru lpszSQL|Wybrane rekordy są określane przez|Przykład|  
|------------------------------------|----------------------------------------|-------------|  
|**NULL**|Długość ciągu zwróconego przez `GetDefaultSQL`.||  
|Nazwa tabeli SQL|Wszystkie kolumny tabeli listy w `DoFieldExchange` lub `DoBulkFieldExchange`.|`"Customer"`|  
|Nazwa wstępnie zdefiniowanego zapytania (procedury składowanej)|Kolumny, które zdefiniowano zapytania do zwrócenia.|`"{call OverDueAccts}"`|  
|**Wybierz** listy kolumn **FROM** listę tabel|Określonych kolumn z określonych tabel.|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|  
  
> [!CAUTION]
>  Pamiętaj, że nie wstawiono dodatkowy odstęp w ciągu SQL. Na przykład, jeśli Wstaw odstęp między nawias klamrowy i **WYWOŁAĆ** — słowo kluczowe, MFC zostanie błędnie interpretuje ciągu SQL jako nazwę tabeli i zastosować go do **wybierz** instrukcję, która spowoduje wyjątek został zgłoszony. Podobnie jeśli wstępnie zdefiniowane zapytanie używa parametru wyjściowego, nie Wstaw odstęp między nawias klamrowy i '' symbolu. Ponadto nie należy umieszczać spacji przed nawias klamrowy w **WYWOŁAĆ** instrukcji lub przed **wybierz** — słowo kluczowe w **wybierz** instrukcji.  
  
 Zwykle procedura służy do przekazywania **NULL** do **Otwórz**; w takim przypadku **Otwórz** wywołania [GetDefaultSQL](#getdefaultsql). Jeśli używasz pochodnego `CRecordset` klasy **GetDefaultSQL** daje nazwy tabel określone w ClassWizard. Zamiast tego można określić inne informacje w `lpszSQL` parametru.  
  
 Niezależnie od przypadku przekazania, **Otwórz** tworzy ostatni ciąg SQL dla zapytania (ciąg może zawierać SQL **gdzie** i **ORDER BY** klauzule dołączany do `lpszSQL` ciągu można Przekroczono), a następnie wykonuje zapytanie. Należy zbadać skonstruowane ciąg przez wywołanie metody [GetSQL](#getsql) po wywołaniu **Otwórz**. Aby dodatkowych szczegółów na temat sposobu konstruuje instrukcji SQL zestawu rekordów i wybiera rekordy, zobacz artykuł [zestaw rekordów: jak zestawy rekordów wybierz rekordów (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).  
  
 Elementy członkowskie danych pola klasy zestawu rekordów, które są powiązane kolumny wybranych danych. Jeśli żadne rekordy nie zostały zwrócone, pierwszy rekord staje się bieżącego rekordu.  
  
 Jeśli chcesz ustawić opcje dla zestawu rekordów, takich jak filtrowania lub sortowania, określ je po konstruowania obiektu zestawu rekordów, ale przed wywołaniem **Otwórz**. Jeśli chcesz odświeżyć rekordy w zestawie rekordów po zestaw rekordów jest już otwarty, należy wywołać [Requery](#requery).  
  
 Aby uzyskać więcej informacji, w tym dodatkowe przykłady, zobacz artykuły [zestawu rekordów (ODBC)](../../data/odbc/recordset-odbc.md), [zestaw rekordów: jak zestawy rekordów wybierz rekordów (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md), i [zestaw rekordów: tworzenie i zamykanie Zestawy rekordów (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).  
  
### <a name="example"></a>Przykład  
 W poniższych przykładach kodu pokazano różne formy **Otwórz** wywołania.  
  
 [!code-cpp[NVC_MFCDatabase#16](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]  
  
##  <a name="refreshrowset"></a>  CRecordset::RefreshRowset  
 Aktualizuje dane i stan wiersza w bieżącym zestawie wierszy.  
  
```  
void RefreshRowset(
    WORD wRow,  
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```  
  
### <a name="parameters"></a>Parametry  
 `wRow`  
 Na podstawie jednej położenie wiersza w bieżącym zestawie wierszy. Ta wartość może należeć do zakresu od 0 do rozmiaru zestawu wierszy.  
  
 `wLockType`  
 Wartość wskazująca, blokowania wiersz po został odświeżony. Aby uzyskać więcej informacji zobacz uwagi.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku przekazania wartości zero dla `wRow`, a następnie zostanie odświeżona po każdym wierszu zestawu wierszy.  
  
 Aby użyć `RefreshRowset`, musi zaimplementowano zbiorcze pobieranie z wiersza, określając **CRecordset::useMulitRowFetch** opcji w [Otwórz](#open) funkcji członkowskiej.  
  
 `RefreshRowset` wywołuje funkcję interfejsu API ODBC **SQLSetPos**. `wLockType` Parametr określa stan blokady wiersza po **SQLSetPos** zostało wykonane. W poniższej tabeli opisano możliwe wartości `wLockType`.  
  
|wLockType|Opis|  
|---------------|-----------------|  
|`SQL_LOCK_NO_CHANGE` (wartość domyślna)|Sterownik lub źródła danych zapewni, że wiersz w tym samym stanie zablokowany lub odblokowany sprzed `RefreshRowset` została wywołana.|  
|`SQL_LOCK_EXCLUSIVE`|Sterownik lub źródła danych wyłącznie blokuje wiersza. Nie wszystkie źródła danych obsługuje ten typ blokady.|  
|`SQL_LOCK_UNLOCK`|Sterownik lub źródła danych odblokowuje wiersza. Nie wszystkie źródła danych obsługuje ten typ blokady.|  
  
 Aby uzyskać więcej informacji na temat **SQLSetPos**, zobacz zestaw Windows SDK. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="requery"></a>  CRecordset::Requery  
 Odtwarza (odświeża) zestawu rekordów.  
  
```  
virtual BOOL Requery();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli zestaw rekordów pomyślnie zostały odbudowane; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli żadne rekordy nie zostały zwrócone, pierwszy rekord staje się bieżącego rekordu.  
  
 Aby zestaw rekordów odzwierciedla dodawania i usuwania, które wykonują źródła danych, należy ponownie zbudować zestawu rekordów przez wywołanie metody **Requery**. Jeśli zestaw rekordów jest dynamiczny, automatycznie odzwierciedla aktualizacje, które użytkownicy dokonać jego istniejące rekordy (ale nie dodatków). Jeśli zestaw rekordów jest migawką, należy wywołać **Requery** uwzględnienie zmian przez innych użytkowników, a także dodawania i usuwania.  
  
 Zestaw dynamiczny lub migawki, należy wywołać **Requery** dowolnej chwili, aby odbudować rekordów przy użyciu nowego filtru lub sortowania lub nowe wartości parametru. Ustaw nowe właściwości filtrowania lub sortowania, przypisując nowych wartości **m_strFilter** i `m_strSort` przed wywołaniem **Requery**. Ustaw nowe parametry przez przypisanie wartości nowe elementy członkowskie danych parametru przed wywołaniem **Requery**. Jeśli filtrowanie i sortowanie ciągów nie uległy zmianie, można użyć ponownie zapytanie, co zwiększa wydajność.  
  
 Jeśli próba odbudować zestaw rekordów nie powiedzie się, zestaw rekordów jest zamknięty. Przed wywołaniem **Requery**, można określić, czy zestaw rekordów można ponowieniu wywołując `CanRestart` funkcję elementu członkowskiego. `CanRestart` nie gwarantuje, że **Requery** powiedzie się.  
  
> [!CAUTION]
>  Wywołanie **Requery** tylko po wywołaniu [Otwórz](#open).  
  
### <a name="example"></a>Przykład  
 W tym przykładzie odbudowuje zestawu rekordów, aby zastosować inny porządek sortowania.  
  
 [!code-cpp[NVC_MFCDatabase#29](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]  
  
##  <a name="setabsoluteposition"></a>  CRecordset::SetAbsolutePosition  
 Umieszcza zestawu rekordów w rekordzie odpowiadającą liczbie określonego rekordu.  
  
```  
void SetAbsolutePosition(long nRows);
```  
  
### <a name="parameters"></a>Parametry  
 `nRows`  
 Na podstawie jednej porządkowym dla bieżącego rekordu w zestawie rekordów.  
  
### <a name="remarks"></a>Uwagi  
 `SetAbsolutePosition` Przenosi bieżący wskaźnik rekord na podstawie tej pozycji porządkowej.  
  
> [!NOTE]
>  Ta funkcja członkowska nie jest prawidłowy w zestawy rekordów tylko do przodu.  
  
 ODBC — zestawy rekordów, aby uzyskać ustawienie położenie bezwzględne 1 oznacza pierwszy rekord w zestawie rekordów; wartość 0 oznacza położenie początku pliku (BOF).  
  
 Można również przekazać wartości ujemnych do `SetAbsolutePosition`. W takim przypadku pozycji w zestawie rekordów jest obliczane na końcu zestawu rekordów. Na przykład `SetAbsolutePosition( -1 )` Przenosi bieżący wskaźnik rekordów do ostatniego rekordu w zestawie rekordów.  
  
> [!NOTE]
>  Położenie bezwzględne nie jest przeznaczony do użycia jako numer rekordu dwuskładnikowego. Zakładki są nadal zalecany sposób zachowania i powrót do określonej pozycji, ponieważ zmiany pozycji rekordu po poprzednim rekordy są usuwane. Ponadto możesz nie mieć pewność, rekord ma to samo położenie bezwzględne Jeśli zestaw rekordów jest utworzony ponownie, ponieważ nie jest gwarantowana kolejność poszczególnych rekordów w zestawie rekordów, chyba że jest tworzony za pomocą instrukcji SQL przy użyciu **ORDER BY** klauzuli.  
  
 Aby uzyskać więcej informacji na temat nawigacji zestawu rekordów i zakładki, zobacz artykuły [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) i [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).  
  
##  <a name="setbookmark"></a>  CRecordset::SetBookmark  
 Umieszcza zestawu rekordów na rekord zawierający zakładką.  
  
```  
void SetBookmark(const CDBVariant& varBookmark);
```  
  
### <a name="parameters"></a>Parametry  
 `varBookmark`  
 Odwołanie do [cdbvariant —](../../mfc/reference/cdbvariant-class.md) obiekt zawierający wartości zakładki dla określonego rekordu.  
  
### <a name="remarks"></a>Uwagi  
 Aby ustalić, czy zakładki są obsługiwane w zestawie rekordów, należy wywołać [CanBookmark](#canbookmark). Aby udostępnić zakładki, jeśli są obsługiwane, należy ustawić **CRecordset::useBookmarks** opcji `dwOptions` parametr [Otwórz](#open) funkcję elementu członkowskiego.  
  
> [!NOTE]
>  Jeśli zakładki są nieobsługiwane lub jest niedostępny, wywoływania `SetBookmark` spowodują wyjątek. Zakładki nie są obsługiwane na zestawy rekordów tylko do przodu.  
  
 Najpierw pobrać zakładki dla bieżącego rekordu, wywołaj [GetBookmark](#getbookmark), który zapisuje wartość zakładki `CDBVariant` obiektu. Później, możesz powrócić do tego rekordu przez wywołanie metody `SetBookmark` przy użyciu wartości zapisane zakładki.  
  
> [!NOTE]
>  Po pewnych operacji zestawu rekordów, należy sprawdzić trwałości zakładki przed wywołaniem `SetBookmark`. Na przykład, jeśli pobrać zakładki z `GetBookmark` , a następnie wywołać **Requery**, zakładki może nie być już prawidłowe. Wywołanie [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) do sprawdzenia, czy można bezpiecznie wywołać `SetBookmark`.  
  
 Aby uzyskać więcej informacji na temat zakładek i nawigacji zestawu rekordów, zobacz artykuły [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) i [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="setfielddirty"></a>  CRecordset::SetFieldDirty  
 Flagi członka danych pola zestawu rekordów, ponieważ zmianie lub bez zmian.  
  
```  
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pv`  
 Zawiera adres elementu członkowskiego danych pole w zestawie rekordów lub **NULL**. Jeśli **NULL**, oflagowane wszystkie elementy członkowskie danych pola w zestawie rekordów. (C++ **NULL** nie jest taka sama jak wartość Null w terminologii bazy danych, co oznacza, że "o wartości".)  
  
 `bDirty`  
 **Wartość TRUE,** element członkowski danych pola jest zostanie oznaczony jako "zakłóconych" (zmienione). W przeciwnym razie **FALSE** element członkowski danych pola jest zostanie oznaczony jako "clean" (bez zmian).  
  
### <a name="remarks"></a>Uwagi  
 Oznaczanie pola jako niezmienione zapewnia to pole nie zostanie zaktualizowana i powoduje mniej ruchu SQL.  
  
> [!NOTE]
>  Ta funkcja członkowska nie ma zastosowania na zestawy rekordów, które korzystają z zbiorcze pobieranie z wiersza. Jeśli zaimplementowano zbiorcze pobieranie z wiersza, następnie `SetFieldDirty` spowoduje potwierdzenia nie powiodło się. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Znaczniki framework zmienione elementy członkowskie danych pola, aby upewnić się, że będą one zapisywane do rekordu w źródle danych przez mechanizm pól rekordów (RFX) programu exchange. Zmiana wartości pola zazwyczaj ustawia pole zanieczyszczone automatycznie, dzięki czemu rzadko trzeba wywołać `SetFieldDirty` samodzielnie, ale czasami warto upewnij się, że kolumn zostanie jawnie zaktualizowane lub wstawić niezależnie od tego, jakie wartości w polu danych element członkowski.  
  
> [!CAUTION]
>  Wywołanie funkcji członkowskiej tylko po wywołaniu [Edytuj](#edit) lub [AddNew](#addnew).  
  
 Przy użyciu **NULL** dla pierwszy argument funkcji będą stosowane tylko do funkcji **outputColumn** pól nie **param** pola. Na przykład wywołanie  
  
 [!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 zostanie ustawiona tylko **outputColumn** pól do **NULL**; **param** pól będzie to miało wpływu.  
  
 Do pracy nad **param** pól, należy podać rzeczywiste adres poszczególne **param** chcesz pracować, takich jak:  
  
 [!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 Oznacza to, nie można ustawić wszystkie **param** pól do **NULL**, jak w przypadku **outputColumn** pól.  
  
##  <a name="setfieldnull"></a>  CRecordset::SetFieldNull  
 Flags element członkowski danych pola zestawu rekordów jako wartości Null (o specjalnie żadna wartość) lub inną niż Null.  
  
```  
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pv`  
 Zawiera adres elementu członkowskiego danych pole w zestawie rekordów lub **NULL**. Jeśli **NULL**, oflagowane wszystkie elementy członkowskie danych pola w zestawie rekordów. (C++ **NULL** nie jest taka sama jak wartość Null w terminologii bazy danych, co oznacza, że "o wartości".)  
  
 `bNull`  
 Różna od zera, jeśli element członkowski danych pole ma być oznaczone jako mający żadna wartość (Null). W przeciwnym razie równa 0, jeśli element członkowski danych pola być oznaczony jako inną niż Null.  
  
### <a name="remarks"></a>Uwagi  
 Podczas dodawania nowego rekordu do zestawu rekordów, wszystkie elementy członkowskie danych pola są początkowo ustawiona na wartość Null i oznaczone jako "zakłóconych" (zmienione). Gdy można pobrać rekordu ze źródła danych, jej kolumn już mieć wartości albo mają wartość Null.  
  
> [!NOTE]
>  Nie wywołuj tej funkcji członkowskiej na zestawy rekordów, które korzystają z zbiorcze pobieranie z wiersza. Jeśli zaimplementowano zbiorcze pobieranie z wiersza, wywoływania `SetFieldNull` powoduje potwierdzenia nie powiodło się. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Jeśli chcesz wyznaczyć pole bieżącego rekordu nie ma wartości, wywołaj specjalnie `SetFieldNull` z `bNull` ustawioną **TRUE** do flagi go jako wartość Null. Jeśli chcesz nadać mu wartość pola została wcześniej oznaczona wartość Null, po prostu ustawić jego nowej wartości. Nie trzeba usunąć flagę Null z `SetFieldNull`. Aby ustalić, czy pole może mieć wartości Null, należy wywołać `IsFieldNullable`.  
  
> [!CAUTION]
>  Wywołanie funkcji członkowskiej tylko po wywołaniu [Edytuj](#edit) lub [AddNew](#addnew).  
  
 Przy użyciu **NULL** dla pierwszy argument funkcji będą stosowane tylko do funkcji **outputColumn** pól nie **param** pola. Na przykład wywołanie  
  
 [!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 zostanie ustawiona tylko **outputColumn** pól do **NULL**; **param** pól będzie to miało wpływu.  
  
 Do pracy nad **param** pól, należy podać rzeczywiste adres poszczególne **param** chcesz pracować, takich jak:  
  
 [!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 Oznacza to, nie można ustawić wszystkie **param** pól do **NULL**, jak w przypadku **outputColumn** pól.  
  
> [!NOTE]
>  Podczas ustawiania parametrów na wartość Null, wywołanie `SetFieldNull` przed zestaw rekordów jest otwarty powoduje potwierdzenia. W takim przypadku wywołania [SetParamNull](#setparamnull).  
  
 `SetFieldNull` jest implementowane za pośrednictwem [DoFieldExchange](#dofieldexchange).  
  
##  <a name="setlockingmode"></a>  CRecordset::SetLockingMode  
 Ustawia tryb blokowania "optymistycznej" blokowania (ustawienie domyślne) lub blokowania "pesymistyczne". Określa sposób blokowania rekordów aktualizacji.  
  
```  
void SetLockingMode(UINT nMode);
```  
  
### <a name="parameters"></a>Parametry  
 `nMode`  
 Zawiera jedną z następujących wartości z **wyliczenia LockMode**:  
  
- **optymistyczne** optymistyczne blokowanie blokuje rekord aktualizowana tylko podczas wywołania **aktualizacji**.  
  
- **pesymistyczne** pesymistyczne blokowanie blokuje rekord natychmiast **Edytuj** nazywa się i będzie zablokowany do momentu **aktualizacji** ukończenia wywołania lub przenieść do nowego rekordu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji Członkowskich, jeśli chcesz określić, które z dwóch strategii blokowanie rekordów aktualizacji korzysta z zestawu rekordów. Domyślnie jest tryb blokowania rekordów **optymistycznej**. Można zmienić, aby zachować ostrożność **pesymistyczne** strategii blokowania. Wywołanie `SetLockingMode` po konstruowania i otworzyć obiektu zestawu rekordów, ale przed wywołaniem **Edytuj**.  
  
##  <a name="setparamnull"></a>  CRecordset::SetParamNull  
 Parametr flag, jako wartość Null (o specjalnie żadna wartość) lub inną niż Null.  
  
```  
void SetParamNull(
    int nIndex,  
    BOOL bNull = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Liczony od zera indeks parametru.  
  
 `bNull`  
 Jeśli **TRUE** (wartość domyślna), parametr jest oznaczony jako wartość Null. W przeciwnym razie wartość parametru z flagą inną niż Null.  
  
### <a name="remarks"></a>Uwagi  
 W odróżnieniu od [SetFieldNull](#setfieldnull), można wywołać `SetParamNull` przed otwarciem zestawu rekordów.  
  
 `SetParamNull` zwykle jest używana z wstępnie zdefiniowanego zapytania (procedury składowane).  
  
##  <a name="setrowsetcursorposition"></a>  CRecordset::SetRowsetCursorPosition  
 Przesuwa kursor do wiersza w bieżącym zestawie wierszy.  
  
```  
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```  
  
### <a name="parameters"></a>Parametry  
 `wRow`  
 Na podstawie jednej położenie wiersza w bieżącym zestawie wierszy. Ta wartość może należeć do zakresu od 1 do rozmiaru zestawu wierszy.  
  
 `wLockType`  
 Wartość wskazująca, blokowania wiersz po został odświeżony. Aby uzyskać więcej informacji zobacz uwagi.  
  
### <a name="remarks"></a>Uwagi  
 Implementując wiersza zbiorcze pobieranie rekordów są pobierane przez zestawy wierszy, gdy pierwszy rekord w pobranych wierszy jest bieżącego rekordu. Aby ustawić inny rekord w zestawie wierszy dla bieżącego rekordu, wywołaj `SetRowsetCursorPosition`. Na przykład można łączyć `SetRowsetCursorPosition` z [GetFieldValue](#getfieldvalue) funkcji członkowskiej dynamicznie pobrać dane z dowolnego rekordu zestawu rekordów.  
  
 Umożliwia `SetRowsetCursorPosition`, musi zaimplementowano zbiorcze pobieranie z wiersza, określając `CRecordset::useMultiRowFetch` opcji `dwOptions` parametru w [Otwórz](#open) funkcji członkowskiej.  
  
 `SetRowsetCursorPosition` wywołuje funkcję interfejsu API ODBC **SQLSetPos**. `wLockType` Parametr określa stan blokady wiersza po **SQLSetPos** zostało wykonane. W poniższej tabeli opisano możliwe wartości `wLockType`.  
  
|wLockType|Opis|  
|---------------|-----------------|  
|`SQL_LOCK_NO_CHANGE` (wartość domyślna)|Sterownik lub źródła danych zapewni, że wiersz w tym samym stanie zablokowany lub odblokowany sprzed `SetRowsetCursorPosition` została wywołana.|  
|`SQL_LOCK_EXCLUSIVE`|Sterownik lub źródła danych wyłącznie blokuje wiersza. Nie wszystkie źródła danych obsługuje ten typ blokady.|  
|`SQL_LOCK_UNLOCK`|Sterownik lub źródła danych odblokowuje wiersza. Nie wszystkie źródła danych obsługuje ten typ blokady.|  
  
 Aby uzyskać więcej informacji na temat **SQLSetPos**, zobacz zestaw Windows SDK. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="setrowsetsize"></a>  CRecordset::SetRowsetSize  
 Określa liczbę rekordów, które chcesz pobrać podczas pobierania.  
  
```  
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```  
  
### <a name="parameters"></a>Parametry  
 *dwNewRowsetSize*  
 Liczba wierszy do pobrania podczas pobierania danego.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członka wirtualnego Określa, ile wierszy chcesz pobrać podczas pobierania pojedynczego, korzystając z zbiorcze pobieranie z wiersza. Aby zaimplementować zbiorcze pobieranie z wiersza, należy ustawić `CRecordset::useMultiRowFetch` opcji `dwOptions` parametr [Otwórz](#open) funkcji członkowskiej.  
  
> [!NOTE]
>  Wywoływanie `SetRowsetSize` bez stosowania zbiorcze pobieranie z wiersza spowoduje potwierdzenia nie powiodło się.  
  
 Wywołanie `SetRowsetSize` przed wywołaniem **Otwórz** do początkowo ustawianie rozmiaru wierszy dla zestawu rekordów. Domyślny rozmiar wierszy podczas implementowania zbiorcze pobieranie z wiersza to 25.  
  
> [!NOTE]
>  Należy zachować ostrożność podczas wywoływania metody `SetRowsetSize`. Jeśli są ręcznie Alokacja magazynu danych (określone przez **CRecordset::userAllocMultiRowBuffers** opcji parametru dwOptions w **Otwórz**), należy sprawdzić, czy konieczne jest ponownie przydzielić bufory magazynu po wywołaniu metody `SetRowsetSize`, ale przed wykonaniem operacji nawigacji żadnych kursora.  
  
 Aby uzyskać bieżące ustawienie rozmiaru zestawu wierszy, należy wywołać [GetRowsetSize](#getrowsetsize).  
  
 Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="update"></a>  CRecordset::Update  
 Kończy `AddNew` lub **Edytuj** operacji zapisując nowe lub zmodyfikowane dane w źródle danych.  
  
```  
virtual BOOL Update();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli jeden rekord został pomyślnie zaktualizowany; w przeciwnym razie 0, jeśli zmieniono żadnych kolumn. Jeśli żadne rekordy nie zostały zaktualizowane, lub jeśli więcej niż jeden rekord został zaktualizowany, jest zwracany wyjątek. Jest zwracany wyjątek, również dla innych błąd w źródle danych.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji Członkowskich po wywołaniu [AddNew](#addnew) lub [Edytuj](#edit) funkcję elementu członkowskiego. To wywołanie jest wymagane do ukończenia `AddNew` lub **Edytuj** operacji.  
  
> [!NOTE]
>  Jeśli zaimplementowano zbiorcze pobieranie z wiersza, nie można wywołać **aktualizacji**. Spowoduje to potwierdzenie nie powiodło się. Chociaż klasa `CRecordset` nie udostępniają mechanizm aktualizacji zbiorczej wiersze danych, można zapisać własnych funkcji przy użyciu funkcji interfejsu API ODBC **SQLSetPos**. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Zarówno `AddNew` i **Edytuj** przygotowanie buforu edycji, w której znajduje się dodane lub zmodyfikowane dane do zapisu w źródle danych. **Aktualizacja** zapisuje dane. Tylko te pola oznaczone lub wykryte jako zmienione zostały zaktualizowane.  
  
 Jeśli źródło danych obsługuje transakcje, możesz wprowadzić **aktualizacji** wywołania (oraz odpowiednie `AddNew` lub **Edytuj** wywołać) częścią transakcji. Aby uzyskać więcej informacji na temat transakcji, zobacz artykuł [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).  
  
> [!CAUTION]
>  Jeśli należy wywołać **aktualizacji** bez uprzedniego wywołania `AddNew` lub **Edytuj**, **aktualizacji** zgłasza `CDBException`. Jeśli wywołujesz `AddNew` lub **Edytuj**, należy wywołać **aktualizacji** przed wywołaniem **Przenieś** operacji lub przed zamknięciem zestawu rekordów lub połączenie ze źródłem danych. W przeciwnym razie wprowadzone zmiany zostaną utracone bez powiadomienia.  
  
 Szczegółowe informacje na temat obsługi **aktualizacji** błędy, zobacz artykuł [zestaw rekordów: jak zestawy rekordów aktualizacji rekordów (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
### <a name="example"></a>Przykład  
 Zapoznaj się z artykułem [transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Cdatabase — klasa](../../mfc/reference/cdatabase-class.md)   
 [Klasa CRecordView](../../mfc/reference/crecordview-class.md)
