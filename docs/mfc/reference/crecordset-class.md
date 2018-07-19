---
title: Klasa CRecordset | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: e23b4d3521e4068d8f7cee8aa6041d57375ec1b2
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37851479"
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
|[CRecordset::CRecordset](#crecordset)|Konstruuje `CRecordset` obiektu. Klasa pochodna, musisz podać konstruktora, który wywołuje ten zestaw.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRecordset::AddNew](#addnew)|Przygotowuje do dodawania nowego rekordu. Wywołaj `Update` aby zakończyć operację dodawania.|  
|[CRecordset::CanAppend](#canappend)|Zwraca wartość różną od zera, jeśli nowe rekordy można dodać do zestawu rekordów za pomocą `AddNew` funkcja elementu członkowskiego.|  
|[CRecordset::CanBookmark](#canbookmark)|Zwraca wartość różną od zera, jeśli zestaw rekordów obsługuje zakładek.|  
|[CRecordset::Cancel](#cancel)|Anulowanie operacji asynchronicznej lub proces z drugiego wątku.|  
|[CRecordset::CancelUpdate](#cancelupdate)|Anuluje wszystkie oczekujące aktualizacje ze względu na `AddNew` lub `Edit` operacji.|  
|[CRecordset::CanRestart](#canrestart)|Zwraca wartość różną od zera, jeśli `Requery` można wywołać w celu ponownie uruchomić zapytanie w zestawie rekordów.|  
|[CRecordset::CanScroll](#canscroll)|Zwraca wartość różną od zera, jeśli można przewijać rekordów.|  
|[CRecordset::CanTransact](#cantransact)|Zwraca wartość różną od zera, jeśli źródło danych obsługuje transakcji.|  
|[CRecordset::CanUpdate](#canupdate)|Zwraca wartość różną od zera, jeśli zestaw rekordów, które mogą być aktualizowane (można dodać, zaktualizować lub usunąć rekordy).|  
|[CRecordset::CheckRowsetError](#checkrowseterror)|Wywoływane w celu obsługi błędów wygenerowanych podczas pobierania rekordów.|  
|[CRecordset::Close](#close)|Zamyka zestawu rekordów i HSTMT ODBC skojarzonych z nim.|  
|[CRecordset::Delete](#delete)|Usunięcie bieżącego rekordu w zestawie. Należy jawnie przewiń do innego rekordu, po usunięciu.|  
|[CRecordset::DoBulkFieldExchange](#dobulkfieldexchange)|Wywołuje się, by wymienić zbiorczo wiersze danych ze źródła danych do zestawu rekordów. Implementuje zbiorczo wymiana pól rekordów (zbiorcze RFX).|  
|[CRecordset::DoFieldExchange](#dofieldexchange)|Wywoływane w celu wymiany danych (w obu kierunkach) między elementy członkowskie danych pola zestawu rekordów i odpowiedni rekord w źródle danych. Implementuje rejestrowanie wymiana pól (RFX).|  
|[CRecordset::Edit](#edit)|Przygotowuje się do zmian w bieżącym rekordzie. Wywołaj `Update` można ukończyć edycję.|  
|[CRecordset::FlushResultSet](#flushresultset)|Zwraca wartość różną od zera, jeśli inny wynik, ustaw można pobrać, korzystając z wstępnie zdefiniowanego zapytania.|  
|[CRecordset::GetBookmark](#getbookmark)|Przypisuje wartość zakładki rekordu do obiektu parametru.|  
|[CRecordset::GetDefaultConnect](#getdefaultconnect)|Wywołuje się, by pobrać domyślny ciąg połączenia.|  
|[CRecordset::GetDefaultSQL](#getdefaultsql)|Wywołuje się, by pobrać domyślny ciąg SQL do wykonania.|  
|[CRecordset::GetFieldValue](#getfieldvalue)|Zwraca wartość pola w zestawie rekordów.|  
|[CRecordset::GetODBCFieldCount](#getodbcfieldcount)|Zwraca liczbę pól w zestawie rekordów.|  
|[CRecordset::GetODBCFieldInfo](#getodbcfieldinfo)|Zwraca informacje dotyczące pól określonych typów w zestawie rekordów.|  
|[CRecordset::GetRecordCount](#getrecordcount)|Zwraca liczbę rekordów w zestawie rekordów.|  
|[CRecordset::GetRowsetSize](#getrowsetsize)|Zwraca liczbę rekordów, które chcesz pobrać podczas pobierania jednego.|  
|[CRecordset::GetRowsFetched](#getrowsfetched)|Zwraca wartość rzeczywista liczba pobieranych podczas pobierania wierszy.|  
|[CRecordset::GetRowStatus](#getrowstatus)|Zwraca stan wiersza po pobraniu.|  
|[CRecordset::GetSQL](#getsql)|Pobiera ciąg SQL używany do wybierania rekordów dla zestawu rekordów.|  
|[CRecordset::GetStatus](#getstatus)|Pobiera stan zestaw rekordów: indeks bieżącego rekordu i czy został uzyskany końcowej liczby rekordów.|  
|[CRecordset::GetTableName](#gettablename)|Pobiera nazwę tabeli, na którym bazuje zestaw rekordów.|  
|[CRecordset::IsBOF](#isbof)|Zwraca wartość różną od zera, jeśli zestaw rekordów ma został umieszczony przed pierwszym rekordzie. Nie ma bieżącego rekordu.|  
|[CRecordset::IsDeleted](#isdeleted)|Zwraca wartość różną od zera, jeśli zestaw rekordów jest ustawiony na rekordzie usunięte.|  
|[CRecordset::IsEOF](#iseof)|Zwraca wartość różną od zera, jeśli zestaw rekordów zawiera został umieszczony po ostatnim rekordzie. Nie ma bieżącego rekordu.|  
|[CRecordset::IsFieldDirty](#isfielddirty)|Zwraca wartość różną od zera, jeśli określone pole w bieżącym rekordzie została zmieniona.|  
|[CRecordset::IsFieldNull](#isfieldnull)|Zwraca wartość różną od zera, jeśli określone pole w bieżącym rekordzie ma wartość null (nie ma wartości).|  
|[CRecordset::IsFieldNullable](#isfieldnullable)|Zwraca wartość różną od zera, jeśli określone pole w bieżącym rekordzie można ustawić na wartość null (o żadnej wartości).|  
|[CRecordset::IsOpen](#isopen)|Zwraca wartość różną od zera, jeśli `Open` został wcześniej wywołany.|  
|[CRecordset::Move](#move)|Ustawia zestaw rekordów do określonej liczby rekordów z bieżącego rekordu w dowolnym kierunku.|  
|[CRecordset::MoveFirst](#movefirst)|Umieszcza bieżącego rekordu na pierwszy rekord w zestawie rekordów. Test dla `IsBOF` pierwszy.|  
|[CRecordset::MoveLast](#movelast)|Umieszcza bieżącego rekordu na ostatni rekord lub ostatni zestaw wierszy. Test dla `IsEOF` pierwszy.|  
|[CRecordset::MoveNext](#movenext)|Umieszcza bieżącego rekordu na następny rekord lub następnego zestawu wierszy. Test dla `IsEOF` pierwszy.|  
|[CRecordset::MovePrev](#moveprev)|Umieszcza bieżącego rekordu na poprzedni rekord lub poprzedniego zestawu wierszy. Test dla `IsBOF` pierwszy.|  
|[CRecordset::OnSetOptions](#onsetoptions)|Wywołuje się, by ustawić opcje (używany po wybraniu) dla określonej instrukcji ODBC.|  
|[CRecordset::OnSetUpdateOptions](#onsetupdateoptions)|Wywołuje się, by ustawić opcje (używane na aktualizację) dla określonej instrukcji ODBC.|  
|[CRecordset::Open](#open)|Zostanie otwarty zestaw rekordów, pobieranie tabeli lub wykonywania zapytania, które reprezentuje zestaw rekordów.|  
|[CRecordset::RefreshRowset](#refreshrowset)|Odświeża dane i stan określonego wiersze.|  
|[CRecordset::Requery](#requery)|Uruchamia zapytanie w zestawie rekordów ponownie, aby odświeżyć wybrane rekordy.|  
|[CRecordset::SetAbsolutePosition](#setabsoluteposition)|Ustawia zestaw rekordów rekord odpowiadający numerowi określonego rekordu.|  
|[CRecordset::SetBookmark](#setbookmark)|Ustawia zestaw rekordów na określony przez zakładkę rekord.|  
|[CRecordset::SetFieldDirty](#setfielddirty)|Oznacza określonego pola w bieżącym rekordzie, wraz ze zmianą.|  
|[CRecordset::SetFieldNull](#setfieldnull)|Ustawia wartość określonego pola w bieżącym rekordzie, wartość null, (o żadnej wartości).|  
|[CRecordset::SetLockingMode](#setlockingmode)|Ustawia tryb blokowania "optymistycznej" Blokowanie (ustawienie domyślne) lub "pesymistycznego" blokowania. Określa, jak rekordy są blokowane aktualizacji.|  
|[CRecordset::SetParamNull](#setparamnull)|Ustawia określony parametr o wartości null (o żadnej wartości).|  
|[CRecordset::SetRowsetCursorPosition](#setrowsetcursorposition)|Umieszcza kursor w wierszu określonym w zestawie wierszy.|  
|[CRecordset::SetRowsetSize](#setrowsetsize)|Określa liczbę rekordów, które chcesz pobrać podczas pobierania.|  
|[CRecordset::Update](#update)|Kończy `AddNew` lub `Edit` operacji, zapisując dane nowe lub zmodyfikowane w źródle danych.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRecordset::m_hstmt](#m_hstmt)|Zawiera dojście instrukcji ODBC dla zestawu rekordów. Typ `HSTMT`.|  
|[CRecordset::m_nFields](#m_nfields)|Zawiera liczbę elementów członkowskich danych pole w zestawie rekordów. Typ `UINT`.|  
|[CRecordset::m_nParams](#m_nparams)|Zawiera liczbę elementy członkowskie danych parametru w zestawie rekordów. Typ `UINT`.|  
|[CRecordset::m_pDatabase](#m_pdatabase)|Zawiera wskaźnik do `CDatabase` obiektu za pomocą których zestaw rekordów jest połączony ze źródłem danych.|  
|[CRecordset::m_strFilter](#m_strfilter)|Zawiera `CString` języka SQL (Structured Query), który określa `WHERE` klauzuli. Używane jako filtr, aby wybrać tylko te rekordy, które spełniają określone kryteria.|  
|[CRecordset::m_strSort](#m_strsort)|Zawiera `CString` SQL, który określa `ORDER BY` klauzuli. Używane do kontrolowania sposobu sortowania.|  
  
## <a name="remarks"></a>Uwagi  
 Znana jako "zestawy rekordów," `CRecordset` obiekty są zazwyczaj używane w dwóch formach: zestawów dynamicznych i migawek. Dynamiczny jest synchronizowany z aktualizacjami dane wprowadzone przez innych użytkowników. Migawka jest widok statyczny danych. Każdy formularz reprezentuje zestaw rekordów ustalony w czasie, który zostanie otwarty zestaw rekordów, ale podczas przewijania rekord w dynamiczny odzwierciedla zmian później w rekordzie przez innych użytkowników lub innych zestawów rekordów w aplikacji.  
  
> [!NOTE]
>  Jeśli pracujesz z klas obiektów dostępu do danych (DAO), a nie klasy Open Database Connectivity (ODBC), należy użyć klasy [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) zamiast tego. Aby uzyskać więcej informacji, zobacz artykuł [omówienie: programowania bazy danych](../../data/data-access-programming-mfc-atl.md).  
  
 Aby pracować z dowolnego typu zestawu rekordów, zwykle pochodną klasy specyficzne dla aplikacji w zestawie rekordów z `CRecordset`. Zestawy rekordów wybrać rekordy ze źródła danych, a następnie:  
  
-   Przewijania rekordów.  
  
-   Aktualizowanie rekordów i określić tryb blokowania.  
  
-   Filtruj zestaw rekordów, aby ograniczyć rekordy, które wybierze od tych, które są dostępne w źródle danych.  
  
-   Sortuj zestawu rekordów.  
  
-   Parametryzacja zestawu rekordów, aby dostosować jego zaznaczenie z informacjami o nieznany do czasu wykonywania.  
  
 Aby użyć klasy, otwórz bazę danych, a następnie skonstruować obiekt zestawu rekordów, przekazując konstruktora wskaźnik do Twojej `CDatabase` obiektu. Następnie wywołaj zestawu rekordów `Open` funkcja elementu członkowskiego, w którym można określić, czy obiekt jest dynamiczny lub migawki. Wywoływanie `Open` wybiera dane ze źródła danych. Po otwarciu obiekt zestawu rekordów, użyj jego element członkowski funkcji i danych elementów członkowskich do przewijania rekordów i działają na nich. Operacje dostępne są zależne od tego, czy obiekt jest dynamiczny lub migawki, czy można aktualizować lub tylko do odczytu (to zależy od możliwości źródła danych Open Database Connectivity (ODBC)), oraz tego, czy udało Ci się wdrożyć zbiorcze pobieranie z wiersza. Aby odświeżyć rekordy, które mogą zostały zmienione lub dodane od `Open` wywołań, wywołań obiektu `Requery` funkcja elementu członkowskiego. Wywołanie obiektu `Close` element członkowski funkcji i zniszcz obiekt, po zapoznaniu się z nim.  
  
 W pochodnej `CRecordset` klasy, (RFX). wymiana pól rekordów lub zbiorcza wymiana pól rekordów (zbiorcze RFX) jest używana do obsługi odczytywanie i aktualizowanie pola rekordu.  
  
 Aby uzyskać więcej informacji na temat zestawów rekordów i rekordu wymiana pól, zobacz artykuły [omówienie: programowania bazy danych](../../data/data-access-programming-mfc-atl.md), [zestawu rekordów (ODBC)](../../data/odbc/recordset-odbc.md), [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC) ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md), i [(RFX). wymiana pól rekordów](../../data/odbc/record-field-exchange-rfx.md). Aby skupić się na zestawów dynamicznych i migawek, zobacz artykuły [dynamiczny](../../data/odbc/dynaset.md) i [migawki](../../data/odbc/snapshot.md).  
  
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
 Należy wywołać [Requery](#requery) funkcji elementu członkowskiego, aby wyświetlić nowo dodanego rekordu. Pola rekordu są początkowo o wartości Null. (W terminologii bazy danych o wartości Null oznacza, że "po żadnej wartości" i nie jest taka sama jak wartość NULL w języku C++) Aby zakończyć operację, należy wywołać [aktualizacji](#update) funkcja elementu członkowskiego. `Update` Zapisuje zmiany w źródle danych.  
  
> [!NOTE]
>  Jeśli zaimplementowano zbiorcze pobieranie z wiersza, nie można wywołać `AddNew`. Spowoduje to potwierdzenie nie powiodło się. Chociaż klasa `CRecordset` nie zapewnia mechanizm aktualizacji zbiorczej wiersze danych, można napisać własne funkcje za pomocą funkcji interfejsu API ODBC `SQLSetPos`. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 `AddNew` przygotowuje nowy, pusty rekord przy użyciu elementy członkowskie danych pola w zestawie rekordów. Po wywołaniu metody `AddNew`, ustaw wartości, które mają w elementy członkowskie danych pola w zestawie rekordów. (Nie trzeba wywoływać [Edytuj](#edit) funkcja elementu członkowskiego, w tym celu; użyj `Edit` tylko w przypadku istniejących rekordach.) Gdy zostanie następnie wywołana `Update`, zmienione wartości elementów członkowskich danych pola są zapisywane w źródle danych.  
  
> [!CAUTION]
>  Jeśli przewiniesz w do nowego rekordu przed wywołaniem `Update`nowy rekord zostanie utracony i biorąc pod uwagę bez ostrzeżenia.  
  
 Jeśli źródło danych obsługuje transakcje, możesz wprowadzać swoje `AddNew` wywołać częścią transakcji. Aby uzyskać więcej informacji na temat transakcji Zobacz klasy [CDatabase](../../mfc/reference/cdatabase-class.md). Należy zauważyć, że należy wywołać [CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) przed wywołaniem `AddNew`.  
  
> [!NOTE]
>  Dla zestawów dynamicznych nowe rekordy są dodawane do zestawu rekordów jako ostatni rekord. Dodano rekordów nie są dodawane do migawki należy wywołać `Requery` odświeżyć zestaw rekordów.  
  
 Jest to niedozwolone wywołanie `AddNew` dla zestawu rekordów którego `Open` nie została wywołana funkcja elementu członkowskiego. A `CDBException` jest generowany, jeśli wywołujesz `AddNew` dla zestawu rekordów, który nie może dołączyć do. Można określić, czy zestaw rekordów nadaje się przez wywołanie metody [CanAppend](#canappend).  
  
 Aby uzyskać więcej informacji, zobacz następujące artykuły: [zestaw rekordów: jak zestawy rekordów uaktualniają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md), [zestaw rekordów: Dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), i [(transakcji ODBC)](../../data/odbc/transaction-odbc.md).  
  
### <a name="example"></a>Przykład  
 Zapoznaj się z artykułem [transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
##  <a name="canappend"></a>  CRecordset::CanAppend  
 Określa, czy wcześniej otwarty zestaw rekordów można dodawać nowych rekordów.  
  
```  
BOOL CanAppend() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli zestaw rekordów zezwala na dodawanie nowych rekordów; w przeciwnym razie 0. `CanAppend` Zwraca wartość 0 Jeśli otwarty zestaw rekordów jako tylko do odczytu.  
  
##  <a name="canbookmark"></a>  CRecordset::CanBookmark  
 Określa, czy zestaw rekordów służy do oznaczania rekordów, korzystanie z zakładek.  
  
```  
BOOL CanBookmark() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli zestaw rekordów obsługuje zakładki; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest niezależna od `CRecordset::useBookmarks` opcji *dwOptions* parametru [Otwórz](#open) funkcja elementu członkowskiego. `CanBookmark` Wskazuje, czy dany sterownik ODBC i kursora typu obsługi zakładek. `CRecordset::useBookmarks` Wskazuje, czy zakładki będzie dostępny, pod warunkiem są obsługiwane.  
  
> [!NOTE]
>  Zakładki nie są obsługiwane w zestawach rekordów tylko do przodu.  
  
 Aby uzyskać więcej informacji na temat zakładek i nawigacji zestawu rekordów, zobacz artykuły [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) i [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="cancel"></a>  CRecordset::Cancel  
 Żądania, że źródło danych anulować operację asynchroniczną w toku lub proces z drugiego wątku.  
  
```  
void Cancel();
```  
  
### <a name="remarks"></a>Uwagi  
 Pamiętaj, że klasach MFC ODBC nie jest już używać asynchronicznego przetwarzania; do wykonania operacji asynchroniczne, należy bezpośrednio wywołać funkcji interfejsu API ODBC `SQLSetConnectOption`. Aby uzyskać więcej informacji, zobacz temat "Wykonywanie funkcji asynchronicznie", w *ODBC SDK przewodnik*.  
  
##  <a name="cancelupdate"></a>  CRecordset::CancelUpdate  
 Anuluje wszystkie oczekujące aktualizacje, spowodowane [Edytuj](#edit) lub [działają funkcje AddNew](#addnew) operacji przed [aktualizacji](#update) jest wywoływana.  
  
```  
void CancelUpdate();
```  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ta funkcja elementu członkowskiego nie ma zastosowania w zestawy rekordów, które korzystają z zbiorcze pobieranie z wiersza, ponieważ takie zestawy rekordów nie może wywołać `Edit`, `AddNew`, lub `Update`. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Jeśli włączono automatyczne pola zanieczyszczone sprawdzanie `CancelUpdate` spowoduje przywrócenie zmienne Członkowskie wartości mieli oni przed `Edit` lub `AddNew` została wywołana; w przeciwnym razie, pozostanie zmiany wartości. Domyślnie pole Automatyczne sprawdzanie jest włączone, po otwarciu zestawu rekordów. Aby ją wyłączyć, należy określić `CRecordset::noDirtyFieldCheck` w *dwOptions* parametru [Otwórz](#open) funkcja elementu członkowskiego.  
  
 Aby uzyskać więcej informacji na temat aktualizowania danych, zobacz artykuł [zestaw rekordów: Dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md).  
  
##  <a name="canrestart"></a>  CRecordset::CanRestart  
 Określa, czy zestaw rekordów zezwala na ponowne uruchomienie jej zapytanie (na przykład aby odświeżyć swoje rekordy) przez wywołanie metody `Requery` funkcja elementu członkowskiego.  
  
```  
BOOL CanRestart() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli dozwolone jest ponowne wykonanie kwerendy w przeciwnym razie 0.  
  
##  <a name="canscroll"></a>  CRecordset::CanScroll  
 Określa, czy zestaw rekordów umożliwia przewijanie.  
  
```  
BOOL CanScroll() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli zestaw rekordów umożliwia przewijanie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat przewijania, zobacz artykuł [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="cantransact"></a>  CRecordset::CanTransact  
 Określa, czy zestaw rekordów zezwala na transakcji.  
  
```  
BOOL CanTransact() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli zestaw rekordów umożliwia; transakcje: w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz artykuł [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="canupdate"></a>  CRecordset::CanUpdate  
 Określa, czy zestaw rekordów może być aktualizowana.  
  
```  
BOOL CanUpdate() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli zestaw rekordów, mogą być aktualizowane; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Zestaw rekordów może być tylko do odczytu, jeśli bazowe źródło danych jest tylko do odczytu, lub jeśli określono `CRecordset::readOnly` w *dwOptions* parametru po otwarciu zestawu rekordów.  
  
##  <a name="checkrowseterror"></a>  CRecordset::CheckRowsetError  
 Wywoływane w celu obsługi błędów wygenerowanych podczas pobierania rekordów.  
  
```  
virtual void CheckRowsetError(RETCODE nRetCode);
```  
  
### <a name="parameters"></a>Parametry  
 *nRetCode*  
 Funkcja interfejsu API ODBC zwrócony kod. Aby uzyskać więcej informacji zobacz uwagi.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja wirtualna elementu członkowskiego obsługuje błędy, które występują, gdy rekordy są pobierane, jest przydatne podczas zbiorcze pobieranie z wiersza. Warto wziąć pod uwagę zastępowanie `CheckRowsetError` zaimplementować własną obsługę błędów.  
  
 `CheckRowsetError` jest wywoływana automatycznie w ramach operacji nawigacji kursora, takich jak `Open`, `Requery`, lub dowolnego `Move` operacji. Jest przekazywana wartość zwracaną funkcji interfejsu API ODBC `SQLExtendedFetch`. Poniższa tabela zawiera listę możliwych wartości dla *nRetCode* parametru.  
  
|nRetCode|Opis|  
|--------------|-----------------|  
|SQL_SUCCESS|Funkcja została ukończona pomyślnie; nie dodatkowe informacje są dostępne.|  
|WARTOŚĆ SQL_SUCCESS_WITH_INFO|Funkcja została ukończona pomyślnie, prawdopodobnie z błąd niekrytyczny. Dodatkowe informacje można uzyskać przez wywołanie metody `SQLError`.|  
|SQL_NO_DATA_FOUND|Pobrano wszystkie wiersze z zestawu wyników.|  
|WARTOŚĆ SQL_ERROR|Funkcja nie powiodło się. Dodatkowe informacje można uzyskać przez wywołanie metody `SQLError`.|  
|SQL_INVALID_HANDLE|Funkcja nie powiodło się z powodu nieprawidłowych dojścia, dojścia połączenia lub dojście instrukcji. Oznacza to błąd programistyczny. Nie dodatkowe informacje są dostępne z `SQLError`.|  
|SQL_STILL_EXECUTING|Nadal trwa wykonywanie funkcji, które zostało uruchomione asynchronicznie. Należy pamiętać, że domyślnie MFC nigdy nie będzie przekazywać tę wartość, aby `CheckRowsetError`; MFC, będą nadal wywoływania `SQLExtendedFetch` dopóki nie zwróci SQL_STILL_EXECUTING.|  
  
 Aby uzyskać więcej informacji na temat `SQLError`, zobacz dokumentację Windows SDK. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="close"></a>  CRecordset::Close  
 Zamyka zestawu rekordów.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Uwagi  
 ODBC HSTMT i całej pamięci RAM przydzielone dla zestawu rekordów bez alokacji. Zwykle po wywołaniu `Close`, Usuń obiekty zestawów rekordów w języku C++, jeśli został przydzielony przy użyciu **nowe**.  
  
 Możesz wywołać `Open` ponownie po wywołaniu `Close`. Dzięki temu można ponownie użyć obiekt zestawu rekordów. Alternatywą jest wywołanie `Requery`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDatabase#17](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]  
  
##  <a name="crecordset"></a>  CRecordset::CRecordset  
 Konstruuje `CRecordset` obiektu.  
  
```  
CRecordset(CDatabase* pDatabase = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *pDatabase*  
 Zawiera wskaźnik do `CDatabase` obiekt lub wartość NULL. Jeśli nie ma wartości NULL i `CDatabase` obiektu `Open` połączyć się ze źródłem danych nie została wywołana funkcja elementu członkowskiego, próbuje otworzyć go dla Ciebie podczas swój własny zestaw rekordów `Open` wywołania. W przypadku przekazania wartości NULL, `CDatabase` obiekt jest konstruowany i połączone przy użyciu informacje o źródle danych, które zostały określone, gdy pochodne klasy zestawu rekordów z ClassWizard.  
  
### <a name="remarks"></a>Uwagi  
 Można użyć `CRecordset` bezpośrednio lub pochodzić z klasy specyficzne dla aplikacji z `CRecordset`. ClassWizard umożliwia pochodzi z klasy zestawu rekordów.  
  
> [!NOTE]
>  Klasa pochodna *musi* podać swój własny konstruktora. W konstruktorze klasy pochodnej, wywołanie konstruktora `CRecordset::CRecordset`, przekazując odpowiednie parametry wzdłuż do niego.  
  
 Przekazać wartości NULL do Konstruktora zestawu rekordów mieć `CDatabase` obiekt skonstruowany i połączone dla Ciebie automatycznie. Jest to przydatne skrótowa, która nie wymaga to utworzyć i połączyć `CDatabase` obiektu przed konstruowanie rekordów.  
  
### <a name="example"></a>Przykład  
 Aby uzyskać więcej informacji, zobacz artykuł [zestaw rekordów: deklarowanie klasy dla tabeli (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).  
  
##  <a name="delete"></a>  CRecordset::Delete  
 Usunięcie bieżącego rekordu.  
  
```  
virtual void Delete();
```  
  
### <a name="remarks"></a>Uwagi  
 Po pomyślnym usunięciu, elementy członkowskie danych pola w zestawie rekordów są ustawione na wartość Null i musi jawnie wywołać jedną z `Move` funkcji, aby opuścić usunięty rekord. Po przeniesieniu poza usunięto rekord nie jest możliwość powrotu do niego. Jeśli źródło danych obsługuje transakcje, można wprowadzić `Delete` wywołać częścią transakcji. Aby uzyskać więcej informacji, zobacz artykuł [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).  
  
> [!NOTE]
>  Jeśli zaimplementowano zbiorcze pobieranie z wiersza, nie można wywołać `Delete`. Spowoduje to potwierdzenie nie powiodło się. Chociaż klasa `CRecordset` nie zapewnia mechanizm aktualizacji zbiorczej wiersze danych, można napisać własne funkcje za pomocą funkcji interfejsu API ODBC `SQLSetPos`. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
> [!CAUTION]
>  Zestaw rekordów musi być nadaje się do aktualizacji i musi być prawidłowy rekord bieżący w zestawie rekordów po wywołaniu `Delete`; w przeciwnym razie wystąpi błąd. Na przykład, jeśli możesz usunąć rekord, ale nie przewiń do nowego rekordu przed wywołaniem `Delete` ponownie `Delete` zgłasza [CDBException](../../mfc/reference/cdbexception-class.md).  
  
 W odróżnieniu od [działają funkcje AddNew](#addnew) i [Edytuj](#edit), wywołanie `Delete` nie następuje po wywołaniu [aktualizacji](#update). Jeśli `Delete` wywołanie zakończy się niepowodzeniem, pola danych elementów członkowskich są pozostawione bez zmian.  
  
### <a name="example"></a>Przykład  
 Ten przykład przedstawia zestaw rekordów tworzone na ramce funkcji. Przykład zakłada się istnienie `m_dbCust`, zmienną składową typu `CDatabase` już połączono ze źródłem danych.  
  
 [!code-cpp[NVC_MFCDatabase#18](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]  
  
##  <a name="dobulkfieldexchange"></a>  CRecordset::DoBulkFieldExchange  
 Wywołuje się, by wymienić zbiorczo wiersze danych ze źródła danych do zestawu rekordów. Implementuje zbiorczo wymiana pól rekordów (zbiorcze RFX).  
  
```  
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```  
  
### <a name="parameters"></a>Parametry  
 *Plik pFX*  
 Wskaźnik do [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) obiektu. Struktura będzie już skonfigurowano ten obiekt do określenia kontekstu dla operacji wymiany pól.  
  
### <a name="remarks"></a>Uwagi  
 Po zaimplementowaniu zbiorcze pobieranie z wiersza struktura wywołuje tę funkcję elementu członkowskiego, aby automatycznie przesyłać dane ze źródła danych do obiektu zestawu rekordów. `DoBulkFieldExchange` Jeśli parametr symbole zastępcze w ciągu instrukcji SQL dla zaznaczenia w zestawie rekordów także wiąże się z Twojego elementy członkowskie danych parametru.  
  
 Jeśli nie jest zaimplementowana zbiorcze pobieranie z wiersza, struktura wywołuje [dofieldexchange —](#dofieldexchange). Aby zaimplementować zbiorcze pobieranie z wiersza, należy określić `CRecordset::useMultiRowFetch` opcji *dwOptions* parametru w [Otwórz](#open) funkcja elementu członkowskiego.  
  
> [!NOTE]
> `DoBulkFieldExchange` jest dostępna tylko wtedy, gdy używasz klasy pochodzącej od `CRecordset`. Jeśli utworzono obiekt zestawu rekordów bezpośrednio z `CRecordset`, należy wywołać [getfieldvalue —](#getfieldvalue) funkcja elementu członkowskiego w celu pobrania danych.  
  
 Zbiorcza wymiana pól rekordów (zbiorcze RFX) jest podobny do wymiana pól rekordów (RFX). Dane są przesyłane automatycznie ze źródła danych, obiektowi zestawu rekordów. Jednak nie można wywołać `AddNew`, `Edit`, `Delete`, lub `Update` Aby przetransferować zmiany wprowadzone do źródła danych. Klasa `CRecordset` aktualnie nie zapewnia mechanizm aktualizacji zbiorczej wiersze danych; Jednakże, można napisać własne funkcje za pomocą funkcji interfejsu API ODBC `SQLSetPos`.  
  
 Należy pamiętać, że ClassWizard nie obsługuje zbiorcza wymiana pól rekordów; Dlatego konieczne jest przesłonięcie `DoBulkFieldExchange` ręcznie, pisząc wywołania funkcji zbiorcze RFX. Aby uzyskać więcej informacji o tych funkcjach, zobacz temat [funkcje wymiany pól rekordów](../../mfc/reference/record-field-exchange-functions.md).  
  
 Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Aby uzyskać powiązane informacje, zobacz artykuł [wymiany pól rekordu (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
##  <a name="dofieldexchange"></a>  CRecordset::DoFieldExchange  
 Wywoływane w celu wymiany danych (w obu kierunkach) między elementy członkowskie danych pola zestawu rekordów i odpowiedni rekord w źródle danych. Implementuje rejestrowanie wymiana pól (RFX).  
  
```  
virtual void DoFieldExchange(CFieldExchange* pFX);
```  
  
### <a name="parameters"></a>Parametry  
 *Plik pFX*  
 Wskaźnik do [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) obiektu. Struktura będzie już skonfigurowano ten obiekt do określenia kontekstu dla operacji wymiany pól.  
  
### <a name="remarks"></a>Uwagi  
 Gdy zbiorcze pobieranie z wiersza nie jest zaimplementowana, struktura wywołuje tę funkcję elementu członkowskiego, aby automatycznie wymianę danych między elementy członkowskie danych pola obiektu zestawu rekordów i odpowiednie kolumny bieżącego rekordu w źródle danych. `DoFieldExchange` Jeśli parametr symbole zastępcze w ciągu instrukcji SQL dla zaznaczenia w zestawie rekordów także wiąże się z Twojego elementy członkowskie danych parametru.  
  
 Jeśli zaimplementowano zbiorcze pobieranie z wiersza struktura wywołuje [dobulkfieldexchange —](#dobulkfieldexchange). Aby zaimplementować zbiorcze pobieranie z wiersza, należy określić `CRecordset::useMultiRowFetch` opcji *dwOptions* parametru w [Otwórz](#open) funkcja elementu członkowskiego.  
  
> [!NOTE]
> `DoFieldExchange` jest dostępna tylko wtedy, gdy używasz klasy pochodzącej od `CRecordset`. Jeśli utworzono obiekt zestawu rekordów bezpośrednio z `CRecordset`, należy wywołać [getfieldvalue —](#getfieldvalue) funkcja elementu członkowskiego w celu pobrania danych.  
  
 Wymiana danych pola, zwane wymiana pól rekordów (RFX) działa w obu kierunkach: z obiekty zestawów rekordów elementy członkowskie danych pola do pól rekordu w źródle danych, a także z rekordu w źródle danych do obiektu zestawu rekordów.  
  
 Jedyną akcją, zazwyczaj należy wykonać w celu zaimplementowania `DoFieldExchange` dla rekordów pochodnej klasy ma utworzyć klasę z ClassWizard i określić nazwy i typy danych elementów członkowskich danych pola. Może również dodać kod, w jaki ClassWizard zapisuje, aby określić elementy członkowskie danych parametru lub radzenia sobie z dowolnej kolumny, które można powiązać dynamicznie. Aby uzyskać więcej informacji, zobacz artykuł [zestaw rekordów: dynamiczne powiązanie danych kolumn (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
 Kiedy Deklarujesz klasy pochodnej rekordów z ClassWizard, kreator zapisuje zastąpieniu obiektu `DoFieldExchange` , który przypomina poniższy przykład:  
  
 [!code-cpp[NVC_MFCDatabase#19](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]  
  
 Aby uzyskać więcej informacji na temat funkcji RFX, zobacz temat [funkcje wymiany pól rekordów](../../mfc/reference/record-field-exchange-functions.md).  
  
 Dalsze przykłady i szczegóły dotyczące `DoFieldExchange`, zapoznaj się z artykułem [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Aby uzyskać ogólne informacje na temat RFX, zobacz artykuł [wymiana pól rekordów](../../data/odbc/record-field-exchange-rfx.md).  
  
##  <a name="edit"></a>  CRecordset::Edit  
 Umożliwia zmiany bieżącego rekordu.  
  
```  
virtual void Edit();
```  
  
### <a name="remarks"></a>Uwagi  
 Po wywołaniu metody `Edit`, można zmienić, elementy członkowskie danych pola bezpośrednio resetowania ich wartości. Operacja została wykonana, jeśli następnie wywołać [aktualizacji](#update) funkcja elementu członkowskiego, aby zapisać zmiany w źródle danych.  
  
> [!NOTE]
>  Jeśli zaimplementowano zbiorcze pobieranie z wiersza, nie można wywołać `Edit`. Spowoduje to potwierdzenie nie powiodło się. Chociaż klasa `CRecordset` nie zapewnia mechanizm aktualizacji zbiorczej wiersze danych, można napisać własne funkcje za pomocą funkcji interfejsu API ODBC `SQLSetPos`. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 `Edit` zapisuje wartości elementów członkowskich danych w zestawie rekordów. Jeśli wywołasz `Edit`, wprowadzić zmiany, następnie wywołać `Edit` ponownie rekordu wartości zostaną przywrócone do były przed pierwszym `Edit` wywołania.  
  
 W niektórych przypadkach można zaktualizować kolumny czyniąc ją o wartości Null (zawierający żadnych danych). Aby to zrobić, należy wywołać [SetFieldNull](#setfieldnull) z parametrem wartość PRAWDA, aby znak pola o wartości Null; to również powoduje, że kolumny do zaktualizowania. Jeśli chcesz, aby pole zapisywane do źródła danych, nawet jeśli jego wartość nie została zmieniona, wywołaj [SetFieldDirty](#setfielddirty) z parametrem wartość TRUE. Dzieje się tak nawet wtedy, gdy pole ma wartość Null.  
  
 Jeśli źródło danych obsługuje transakcje, można wprowadzić `Edit` wywołać częścią transakcji. Należy zauważyć, że należy wywołać [CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) przed wywołaniem `Edit` i po otwarciu zestawu rekordów. Należy również zauważyć, że wywołanie [CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) nie jest alternatywą do wywoływania `Update` do ukończenia `Edit` operacji. Aby uzyskać więcej informacji na temat transakcji Zobacz klasy [CDatabase](../../mfc/reference/cdatabase-class.md).  
  
 W zależności od bieżącej tryb blokowania rekordu aktualizowana może być zablokowany przez `Edit` dopóki nie zostanie wywołana `Update` lub przewinąć do innego rekordu lub może być zablokowany tylko podczas `Edit` wywołania. Możesz zmienić tryb blokowania z [SetLockingMode](#setlockingmode).  
  
 Przywróceniu poprzedniej wartości bieżącego rekordu, przewijania do nowego rekordu przed wywołaniem `Update`. A `CDBException` jest generowany, jeśli wywołujesz `Edit` dla zestawu rekordów, którego nie można zaktualizować lub jeśli nie ma bieżącego rekordu.  
  
 Aby uzyskać więcej informacji, zobacz artykuły [transakcja (ODBC)](../../data/odbc/transaction-odbc.md) i [zestaw rekordów: blokowanie rekordów (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDatabase#20](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]  
  
##  <a name="flushresultset"></a>  CRecordset::FlushResultSet  
 Pobiera następny zestaw wyników wstępnie zdefiniowanego zapytania (procedura składowana), jeśli istnieje wiele zestawów wyników.  
  
```  
BOOL FlushResultSet();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli istnieją większej liczby zestawów wyników, które mają zostać pobrane; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać `FlushResultSet` tylko po zakończeniu całkowicie umieść kursor w bieżącym zestawie wyników. Należy pamiętać, że podczas pobierania następnego wyniku, ustaw przez wywołanie metody `FlushResultSet`, kursor nie jest prawidłowy w tym zestawie wyników; należy wywołać [MoveNext](#movenext) funkcja elementu członkowskiego po wywołaniu `FlushResultSet`.  
  
 Jeśli wstępnie zdefiniowanego zapytania korzysta z parametru wyjściowego lub parametrów wejściowych/wyjściowych, należy wywołać `FlushResultSet` dopóki zwróci `FALSE` (wartość 0), aby można było uzyskać te wartości parametrów.  
  
 `FlushResultSet` wywołuje funkcję interfejsu API ODBC `SQLMoreResults`. Jeśli `SQLMoreResults` zwraca wartość SQL_ERROR lub SQL_INVALID_HANDLE, następnie `FlushResultSet` spowoduje zgłoszenie wyjątku. Aby uzyskać więcej informacji na temat `SQLMoreResults`, zobacz dokumentację Windows SDK.  
  
 Twoja procedura składowana musi mieć powiązane pola, jeśli chcesz aby zadzwonić do `FlushResultSet`.  
  
### <a name="example"></a>Przykład  
 Poniższy kod zakłada, że `COutParamRecordset` jest `CRecordset`-pochodnego obiektu oparte na wstępnie zdefiniowanego zapytania z parametrem wejściowym i parametr wyjściowy, a posiadanie wielu zestawów wyników. Należy pamiętać, struktura [dofieldexchange —](#dofieldexchange) zastąpienia.  
  
 [!code-cpp[NVC_MFCDatabase#21](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDatabase#22](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]  
  
##  <a name="getbookmark"></a>  CRecordset::GetBookmark  
 Pobiera wartość zakładki dla bieżącego rekordu.  
  
```  
void GetBookmark(CDBVariant& varBookmark);
```  
  
### <a name="parameters"></a>Parametry  
 *varBookmark*  
 Odwołanie do [CDBVariant](../../mfc/reference/cdbvariant-class.md) obiekt reprezentujący zakładkę w bieżącym rekordzie.  
  
### <a name="remarks"></a>Uwagi  
 Aby ustalić, czy zakładki są obsługiwane w zestawie rekordów, należy wywołać [CanBookmark](#canbookmark). Aby udostępnić zakładek, jeśli są one obsługiwane, należy ustawić `CRecordset::useBookmarks` opcji *dwOptions* parametru [Otwórz](#open) funkcja elementu członkowskiego.  
  
> [!NOTE]
>  Jeśli zakładki są nieobsługiwane lub jest niedostępny, wywołanie `GetBookmark` spowodują wyjątek. Zakładki nie są obsługiwane w zestawach rekordów tylko do przodu.  
  
 `GetBookmark` przypisuje wartość zakładki w bieżącym rekordzie, aby `CDBVariant` obiektu. Aby powrócić do tego rekordu w dowolnym momencie po przejściu do innego rekordu, należy wywołać [setbookmark —](#setbookmark) z odpowiednimi `CDBVariant` obiektu.  
  
> [!NOTE]
>  Po niektórych operacjach rekordów zakładek może nie być już prawidłowa. Na przykład, jeśli wywołasz `GetBookmark` następuje `Requery`, nie może być możliwość powrotu do rekordu z `SetBookmark`. Wywołaj [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) do sprawdzenia, czy można bezpiecznie wywołać `SetBookmark`.  
  
 Aby uzyskać więcej informacji na temat zakładek i nawigacji zestawu rekordów, zobacz artykuły [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) i [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="getdefaultconnect"></a>  CRecordset::GetDefaultConnect  
 Wywołuje się, by pobrać domyślny ciąg połączenia.  
  
```  
virtual CString GetDefaultConnect();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Element `CString` zawierający domyślne parametry połączenia.  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje tę funkcję elementu członkowskiego, aby uzyskać domyślne parametry połączenia dla źródła danych, na którym bazuje zestaw rekordów. ClassWizard implementuje tę funkcję, automatycznie identyfikując tego samego źródła danych, którego używasz w ClassWizard Aby uzyskać informacje o tabele i kolumny. Prawdopodobnie znajdziesz go wygodne opierać się na to połączenie domyślne podczas tworzenia aplikacji. Jednak połączenie domyślne mogą nie być odpowiednie dla użytkowników aplikacji. Jeśli tak jest rzeczywiście, należy ponownie tę funkcję, odrzucając wersji ClassWizard firmy. Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz artykuł [źródła danych (ODBC)](../../data/odbc/data-source-odbc.md).  
  
##  <a name="getdefaultsql"></a>  CRecordset::GetDefaultSQL  
 Wywołuje się, by pobrać domyślny ciąg SQL do wykonania.  
  
```  
virtual CString GetDefaultSQL();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Element `CString` zawiera domyślną instrukcję SQL.  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje tę funkcję elementu członkowskiego, aby pobrać domyślną instrukcję SQL, na którym bazuje zestaw rekordów. Może to być nazwa tabeli lub SQL **wybierz** instrukcji.  
  
 Możesz pośrednio należy zdefiniować domyślną instrukcję SQL od zadeklarowania klasy zestawu rekordów z ClassWizard i ClassWizard wykonuje to zadanie.  
  
 Jeśli potrzebujesz parametry instrukcji SQL na własny użytek, wywołaj `GetSQL`, która zwraca instrukcję SQL używany do wybierania rekordów w zestawie rekordów, gdy został on otwarty. Możesz edytować domyślny ciąg SQL w swojej klasy zastępowania metody `GetDefaultSQL`. Na przykład można określić wywołanie za pomocą wstępnie zdefiniowanego zapytania **WYWOŁANIA** instrukcji. (Uwaga, jednak, że jeśli edytujesz `GetDefaultSQL`, musisz także zmodyfikować `m_nFields` odpowiadać liczbie kolumn w źródle danych.)  
  
 Aby uzyskać więcej informacji, zobacz artykuł [zestaw rekordów: deklarowanie klasy dla tabeli (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).  
  
> [!CAUTION]
>  Nazwa tabeli jest pusta, jeśli struktura nie może zidentyfikować nazwę tabeli, jeśli podano wiele nazw tabel lub **WYWOŁANIA** nie można zinterpretować instrukcji. Należy pamiętać, że podczas korzystania **WYWOŁANIA** instrukcji, nie należy wstawić odstęp między nawiasów klamrowych i **WYWOŁANIA** — słowo kluczowe, ani nie należy wstawić odstęp przed klamrowym lub przed  **Wybierz** — słowo kluczowe w **wybierz** instrukcji.  
  
##  <a name="getfieldvalue"></a>  CRecordset::GetFieldValue  
 Pobiera dane z pola w bieżącym rekordzie.  
  
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
 *lpszName*  
 Nazwa pola.  
  
 *varValu*e  
 Odwołanie do [CDBVariant](../../mfc/reference/cdbvariant-class.md) obiekt, który będzie przechowywać wartość pola.  
  
 *nFieldType*  
 Typ danych ODBC C pola. Przy użyciu wartości domyślnej, DEFAULT_FIELD_TYPE, wymusza `GetFieldValue` można ustalić typu danych C z typu danych SQL na podstawie następującej tabeli. W przeciwnym razie można określić dane bezpośrednio wpisać lub wybrać zgodny typ danych; na przykład można przechowywać dane dowolnego typu do SQL_C_CHAR.  
  
|Typ danych C|Typ danych SQL|  
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
  
 Aby uzyskać więcej informacji na temat typów danych ODBC zobacz tematy "Typy danych SQL" i "Typy danych C" w dodatku D zestawu Windows SDK.  
  
 *nIndex*  
 Liczony od zera indeks pola.  
  
 *strValue*  
 Odwołanie do [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiekt, który będzie przechowywać wartość pola przekonwertowane na tekst, niezależnie od typu danych pola.  
  
### <a name="remarks"></a>Uwagi  
 Pola można wyszukiwać według nazwy lub indeksu. Wartość pola można przechowywać w jednej `CDBVariant` obiektu lub `CString` obiektu.  
  
 Jeśli zaimplementowano zbiorcze pobieranie z wiersza, bieżący rekord jest zawsze ustawiony na pierwszego rekordu w zestawie wierszy. Aby użyć `GetFieldValue` rekord w ramach danego zestawu wierszy, najpierw musisz wywołać [SetRowsetCursorPosition](#setrowsetcursorposition) funkcja elementu członkowskiego, aby przenieść kursor do żądanego wiersza, w tym zestawie wierszy. Następnie wywołaj `GetFieldValue` dla tego wiersza. Aby zaimplementować zbiorcze pobieranie z wiersza, należy określić `CRecordset::useMultiRowFetch` opcji *dwOptions* parametru w [Otwórz](#open) funkcja elementu członkowskiego.  
  
 Możesz użyć `GetFieldValue` można dynamicznie pobrać pól w czasie wykonywania, a nie statycznie powiązania ich w czasie projektowania. Na przykład, jeśli zadeklarowano obiektem rekordem bezpośrednio z `CRecordset`, należy użyć `GetFieldValue` można pobrać danych pola; wymiana pól rekordów (RFX) lub zbiorcza wymiana pól rekordów (zbiorcze RFX) nie jest zaimplementowana.  
  
> [!NOTE]
>  Jeśli zadeklarować obiekt zestawu rekordów bez pochodząca od `CRecordset`, nie masz załadowana Biblioteka kursorów ODBC. Biblioteka kursorów wymaga, aby zestaw rekordów miał co najmniej jednej kolumny powiązanej; Jednak jeśli używasz `CRecordset` bezpośrednio, żadna z tych kolumn są powiązane. Funkcje elementów członkowskich [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) i [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) kontrolować, czy Biblioteka kursorów zostanie załadowany.  
  
 `GetFieldValue` wywołuje funkcję interfejsu API ODBC `SQLGetData`. Jeśli sterownik generuje wartość SQL_NO_TOTAL rzeczywista długość wartości pola `GetFieldValue` zgłasza wyjątek. Aby uzyskać więcej informacji na temat `SQLGetData`, zobacz dokumentację Windows SDK.  
  
### <a name="example"></a>Przykład  
 Następujący przykładowy kod przedstawia wywołania `GetFieldValue` dla obiektu zestawu rekordów jest zadeklarowany bezpośrednio z `CRecordset`.  
  
 [!code-cpp[NVC_MFCDatabase#23](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]  
  
> [!NOTE]
>  W odróżnieniu od klasy DAO `CDaoRecordset`, `CRecordset` nie ma `SetFieldValue` funkcja elementu członkowskiego. Jeśli tworzysz obiekt bezpośrednio z `CRecordset`, jest efektywne tylko do odczytu.  
  
 Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="getodbcfieldcount"></a>  CRecordset::GetODBCFieldCount  
 Pobiera całkowitą liczbę pól w obiekt zestawu rekordów.  
  
```  
short GetODBCFieldCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba pól w zestawie rekordów.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat tworzenia zestawów rekordów, zobacz artykuł [zestaw rekordów: tworzenie i zamykanie zestawów rekordów (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).  
  
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
 *lpszName*  
 Nazwa pola.  
  
 *FieldInfo*  
 Odwołanie do `CODBCFieldInfo` struktury.  
  
 *nIndex*  
 Liczony od zera indeks pola.  
  
### <a name="remarks"></a>Uwagi  
 Jednej wersji funkcji umożliwia wyszukiwanie pól według nazwy. Druga wersja umożliwia wyszukiwanie pola przez indeks.  
  
 Opis o zwrócone informacje, zobacz [codbcfieldinfo —](../../mfc/reference/codbcfieldinfo-structure.md) struktury.  
  
 Aby uzyskać więcej informacji na temat tworzenia zestawów rekordów, zobacz artykuł [zestaw rekordów: tworzenie i zamykanie zestawów rekordów (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).  
  
##  <a name="getrecordcount"></a>  CRecordset::GetRecordCount  
 Określa rozmiar zestawu rekordów.  
  
```  
long GetRecordCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba rekordów w zestawie rekordów; 0, jeśli zestaw rekordów nie zawiera żadnych rekordów; lub -1, jeśli nie można określić liczbę rekordów.  
  
### <a name="remarks"></a>Uwagi  
  
> [!CAUTION]
>  Liczba rekordów jest przechowywane jako "znacznik limitu górnego," najwyższym numerze rekord jeszcze widoczny, gdy użytkownik przesuwa się między rekordami. Całkowita liczba rekordów jest znane tylko po użytkownik został przeniesiony poza ostatnim rekordzie. Ze względu na wydajność, licznik nie jest aktualizowany po wywołaniu `MoveLast`. Aby samodzielnie Policz rekordy, należy wywołać `MoveNext` wielokrotnie do momentu `IsEOF` zwraca wartość różną od zera. Dodawanie rekordu za pośrednictwem `CRecordset:AddNew` i `Update` zwiększa się liczba; usuwanie rekordu za pośrednictwem `CRecordset::Delete` zmniejsza liczbę.  
  
##  <a name="getrowsetsize"></a>  CRecordset::GetRowsetSize  
 Pobiera bieżące ustawienie liczby wierszy, które chcesz pobrać podczas pobierania danego.  
  
```  
DWORD GetRowsetSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba wierszy do pobrania podczas pobierania danego.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli używasz zbiorcze pobieranie z wiersza domyślny rozmiar wierszy, po otwarciu zestawu rekordów jest 25; w przeciwnym razie jest 1.  
  
 Aby zaimplementować zbiorcze pobieranie z wiersza, należy określić `CRecordset::useMultiRowFetch` opcji *dwOptions* parametru [Otwórz](#open) funkcja elementu członkowskiego. Aby zmienić ustawienie rozmiaru wierszy, należy wywołać [SetRowsetSize](#setrowsetsize).  
  
 Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="getrowsfetched"></a>  CRecordset::GetRowsFetched  
 Określa liczbę rekordów rzeczywiście zostały pobrane po pobraniu.  
  
```  
DWORD GetRowsFetched() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba wierszy pobranego ze źródła danych po pobraniu danego.  
  
### <a name="remarks"></a>Uwagi  
 Jest to przydatne, jeśli udało Ci się wdrożyć zbiorcze pobieranie z wiersza. Rozmiar zestawu wierszy zwykle wskazuje, ile wierszy, które będą pobierane z fetch; jednak łączną liczbę wierszy w zestawie rekordów wpływa również na liczbę wierszy, które zostaną pobrane w zestawie wierszy. Na przykład, jeśli rekordów zawiera 10 rekordów z ustawieniem rozmiar wierszy wynoszącą 4, następnie zapętlenie przez zestaw rekordów, wywołując `MoveNext` spowoduje ostatecznego zestawu wierszy o rekordów tylko 2.  
  
 Aby zaimplementować zbiorcze pobieranie z wiersza, należy określić `CRecordset::useMultiRowFetch` opcji *dwOptions* parametru [Otwórz](#open) funkcja elementu członkowskiego. Aby określić rozmiar wierszy, należy wywołać [SetRowsetSize](#setrowsetsize).  
  
 Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDatabase#24](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]  
  
##  <a name="getrowstatus"></a>  CRecordset::GetRowStatus  
 Uzyskuje informacje o stanie dla wiersza w bieżącym zestawie wierszy.  
  
```  
WORD GetRowStatus(WORD wRow) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *wRow*  
 Liczonego od jednego położenie wiersza w bieżącym zestawie wierszy. Wartość ta może wynosić od 1 do rozmiaru zestawu wierszy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość stanu wiersza. Aby uzyskać więcej informacji zobacz uwagi.  
  
### <a name="remarks"></a>Uwagi  
 `GetRowStatus` Zwraca wartość, która wskazuje zmiany stanu do wiersza, od momentu jego ostatniego pobrane ze źródła danych lub które nie wiersz odpowiadający *wRow* została pobrana. Poniższa tabela zawiera listę możliwych wartości zwracanych.  
  
|Wartość stanu|Opis|  
|------------------|-----------------|  
|SQL_ROW_SUCCESS|Wiersz jest bez zmian.|  
|SQL_ROW_UPDATED|Wiersz został zaktualizowany.|  
|SQL_ROW_DELETED|Wiersz został usunięty.|  
|SQL_ROW_ADDED|Wiersz został dodany.|  
|SQL_ROW_ERROR|Wiersz jest można pobrać niektórych z powodu błędu.|  
|SQL_ROW_NOROW|Istnieje bez wiersza, który odpowiada *wRow*.|  
  
 Aby uzyskać więcej informacji, zobacz opis funkcji interfejsu API ODBC `SQLExtendedFetch` w zestawie Windows SDK.  
  
##  <a name="getstatus"></a>  CRecordset::GetStatus  
 Określa indeks bieżącego rekordu w zestawie rekordów i tego, czy ostatni rekord został napotkany.  
  
```  
void GetStatus(CRecordsetStatus& rStatus) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *rStatus*  
 Odwołanie do `CRecordsetStatus` obiektu. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.  
  
### <a name="remarks"></a>Uwagi  
 `CRecordset` próbuje śledzić indeksu, ale w pewnych okolicznościach może to nie być możliwe. Zobacz [getrecordcount —](#getrecordcount) objaśnienia.  
  
 `CRecordsetStatus` Struktura ma następującą postać:  
  
 `struct CRecordsetStatus`  
  
 `{`  
  
 `long m_lCurrentRecord;`  
  
 `BOOL m_bRecordCountFinal;`  
  
 `};`  
  
 Dwa elementy członkowskie `CRecordsetStatus` mają następujące znaczenie:  
  
- `m_lCurrentRecord` Zawiera liczony od zera indeks bieżącego rekordu w zestawie rekordów, jeśli jest znany. Jeśli nie można określić indeksu tego elementu członkowskiego zawiera AFX_CURRENT_RECORD_UNDEFINED-(2). Jeśli `IsBOF` jest TRUE (pusty zestaw rekordów lub próba przewiń przed pierwszym rekordzie), a następnie `m_lCurrentRecord` jest ustawiona na AFX_CURRENT_RECORD_BOF (-1). Jeśli na pierwszy rekord następnie jest ustawiona na wartość 0, drugi Zarejestruj 1 i tak dalej.  
  
- `m_bRecordCountFinal` Różna od zera, jeśli ustalono, całkowita liczba rekordów w zestawie rekordów. Zazwyczaj te muszą być spełnione, zaczynając od początku zestawu rekordów i wywoływania `MoveNext` aż `IsEOF` zwraca wartość różną od zera. Jeśli ten element członkowski wynosi zero, rekord są wliczani, ponieważ zwracany przez `GetRecordCount`, jeśli nie -1, jest tylko "znacznik limitu górnego" liczbę rekordów.  
  
##  <a name="getsql"></a>  CRecordset::GetSQL  
 Wywołaj tę funkcję elementu członkowskiego, aby pobrać instrukcji SQL, który został użyty do wybierania rekordów w zestawie rekordów, gdy został on otwarty.  
  
```  
const CString& GetSQL() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A **const** odwołanie do `CString` zawiera instrukcję SQL.  
  
### <a name="remarks"></a>Uwagi  
 Są to zazwyczaj SQL **wybierz** instrukcji. Ciąg zwracany przez `GetSQL` jest tylko do odczytu.  
  
 Ciąg zwracany przez `GetSQL` zwykle różni się od dowolny ciąg może być przekazana do zestawu rekordów w *lpszSQL* parametr `Open` funkcja elementu członkowskiego. Jest to spowodowane zestawu rekordów tworzy pełną instrukcję SQL, oparte na przekazany do `Open`, określony za pomocą ClassWizard, co określono w `m_strFilter` i `m_strSort` składowych danych i wszystkie parametry wiążące określona. Szczegółowe informacje o jak zestaw rekordów tworzy tej instrukcji SQL, zobacz artykuł [zestaw rekordów: jak zestawy rekordów wybierz rekordów (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).  
  
> [!NOTE]
>  Wywołaj tę funkcję elementu członkowskiego tylko po wywołaniu [Otwórz](#open).  
  
##  <a name="gettablename"></a>  CRecordset::GetTableName  
 Pobiera nazwę tabeli SQL, na którym opiera się zapytania w zestawie rekordów.  
  
```  
const CString& GetTableName() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A **const** odwołanie do `CString` zawierający tabeli nazwy, jeśli zestaw rekordów jest w oparciu o tabelę; w przeciwnym razie pusty ciąg.  
  
### <a name="remarks"></a>Uwagi  
 `GetTableName` jest prawidłowa tylko jeśli zestaw rekordów jest oparty na tabelę nie dołączania wielu tabel lub wstępnie zdefiniowanego zapytania (procedura składowana). Nazwa jest tylko do odczytu.  
  
> [!NOTE]
>  Wywołaj tę funkcję elementu członkowskiego tylko po wywołaniu [Otwórz](#open).  
  
##  <a name="isbof"></a>  CRecordset::IsBOF  
 Zwraca wartość różną od zera, jeśli zestaw rekordów ma został umieszczony przed pierwszym rekordzie. Nie ma bieżącego rekordu.  
  
```  
BOOL IsBOF() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli zestaw rekordów nie zawiera żadnych rekordów lub mieć przewiniesz wstecz przed pierwszym rekordzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę funkcję elementu członkowskiego, zanim przewiń z rekordu do rekordu, aby dowiedzieć się, czy wykonano przed pierwszym rekordzie zestawu rekordów. Można również użyć `IsBOF` wraz z `IsEOF` ustalenie, czy zestaw rekordów zawiera jakiekolwiek rekordy lub jest pusty. Natychmiast, po wywołaniu metody `Open`, jeśli zestaw rekordów nie zawiera żadnych rekordów `IsBOF` zwraca wartość różną od zera. Po otwarciu zestawu rekordów, który ma co najmniej jeden rekord, pierwszy rekord jest bieżący rekord oraz `IsBOF` zwraca wartość 0.  
  
 Jeśli pierwszy rekord jest bieżący rekord i wywołania `MovePrev`, `IsBOF` następnie zwraca wartość różną od zera. Jeśli `IsBOF` zwraca wartość różną od zera i wywołać `MovePrev`, wystąpi błąd. Jeśli `IsBOF` zwraca wartość różną od zera, bieżący rekord jest niezdefiniowane i dowolną akcję, która wymaga bieżącego rekordu spowoduje wystąpienie błędu.  
  
### <a name="example"></a>Przykład  
 W tym przykładzie użyto `IsBOF` i `IsEOF` wykrywania limity zestawu rekordów, jak kod Przewija zestaw rekordów w obu kierunkach.  
  
 [!code-cpp[NVC_MFCDatabase#25](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]  
  
##  <a name="isdeleted"></a>  CRecordset::IsDeleted  
 Określa, czy bieżący rekord został usunięty.  
  
```  
BOOL IsDeleted() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli zestaw rekordów jest ustawiony na rekordzie usunięte; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Po przewinięciu rekord a `IsDeleted` zwraca wartość TRUE (niezerową), a następnie musi przewiń do innego rekordu, zanim będzie można wykonywać inne operacje zestawu rekordów.  
  
 Wynik `IsDeleted` zależy od wielu czynników, takich jak typu zestawu rekordów, czy rekordów nadaje się, czy określono `CRecordset::skipDeletedRecords` opcji po otwarciu zestawu rekordów, czy Twoje pakiety sterowników usunięte rekordy i czy są dostępne wielu użytkowników.  
  
 Aby uzyskać więcej informacji na temat `CRecordset::skipDeletedRecords` i sterownik pakowania, zobacz [Otwórz](#open) funkcja elementu członkowskiego.  
  
> [!NOTE]
>  Jeśli zaimplementowano zbiorcze pobieranie z wiersza, nie należy wywołać `IsDeleted`. Zamiast tego należy wywołać [getrowstatus —](#getrowstatus) funkcja elementu członkowskiego. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="iseof"></a>  CRecordset::IsEOF  
 Zwraca wartość różną od zera, jeśli zestaw rekordów zawiera został umieszczony po ostatnim rekordzie. Nie ma bieżącego rekordu.  
  
```  
BOOL IsEOF() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli zestaw rekordów nie zawiera żadnych rekordów lub jeśli przewiniesz poza ostatnim rekordzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę funkcję elementu członkowskiego, przewijania z rekordu, rekord, aby dowiedzieć się, czy wykonano poza ostatnim rekordzie zestawu rekordów. Można również użyć `IsEOF` ustalenie, czy zestaw rekordów zawiera jakiekolwiek rekordy lub jest pusty. Natychmiast, po wywołaniu metody `Open`, jeśli zestaw rekordów nie zawiera żadnych rekordów `IsEOF` zwraca wartość różną od zera. Po otwarciu zestawu rekordów, który ma co najmniej jeden rekord, pierwszy rekord jest bieżący rekord oraz `IsEOF` zwraca wartość 0.  
  
 Jeśli ostatni rekord jest bieżący rekord po wywołaniu `MoveNext`, `IsEOF` następnie zwraca wartość różną od zera. Jeśli `IsEOF` zwraca wartość różną od zera i wywołać `MoveNext`, wystąpi błąd. Jeśli `IsEOF` zwraca wartość różną od zera, bieżący rekord jest niezdefiniowane i dowolną akcję, która wymaga bieżącego rekordu spowoduje wystąpienie błędu.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [IsBOF](#isbof).  
  
##  <a name="isfielddirty"></a>  CRecordset::IsFieldDirty  
 Określa, czy element członkowski danych określonego pola zostały zmienione od czasu [Edytuj](#edit) lub [działają funkcje AddNew](#addnew) została wywołana.  
  
```  
BOOL IsFieldDirty(void* pv);
```  
  
### <a name="parameters"></a>Parametry  
 *Wa*  
 Wskaźnik do składowej danych pola, którego stan chcesz sprawdzić lub wartość NULL, aby ustalić, czy dowolna z pól jest zanieczyszczony.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli określone pole składowej danych uległy zmianie od czasu wywołania `AddNew` lub `Edit`; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Dane we wszystkich elementach danych zanieczyszczone pola zostanie przeniesiona do rekordu w źródle danych podczas aktualizacji bieżący rekord przez wywołanie [aktualizacji](#update) funkcji składowej typu `CRecordset` (po wywołaniu `Edit` lub `AddNew`).  
  
> [!NOTE]
>  Ta funkcja elementu członkowskiego nie ma zastosowania w zestawy rekordów, które korzystają z zbiorcze pobieranie z wiersza. Jeśli zaimplementowano zbiorcze pobieranie z wiersza, następnie `IsFieldDirty` zawsze zwraca wartość FALSE, a powoduje potwierdzenie nie powiodło się. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Wywoływanie `IsFieldDirty` spowoduje zresetowanie efekty poprzednich wywołań [SetFieldDirty](#setfielddirty) stanu zanieczyszczone tego pola jest ponownie oceniane. W `AddNew` przypadku, gdy bieżącą wartość pola różni się od wartości null pseudo pole Stan jest ustawiony zanieczyszczeniu. W `Edit` zamierzone, Zapisz, jeśli wartość pola różni się od wartość w pamięci podręcznej, stan pola zostanie ustawiony zanieczyszczeniu.  
  
 `IsFieldDirty` jest implementowane za pomocą [dofieldexchange —](#dofieldexchange).  
  
 Aby uzyskać więcej informacji o zanieczyszczeniu flagi artykuł [zestaw rekordów: jak zestawy rekordów wybierz rekordów (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).  
  
##  <a name="isfieldnull"></a>  CRecordset::IsFieldNull  
 Zwraca wartość różną od zera, jeśli określone pole w bieżącym rekordzie ma wartość Null (nie ma wartości).  
  
```  
BOOL IsFieldNull(void* pv);
```  
  
### <a name="parameters"></a>Parametry  
 *Wa*  
 Wskaźnik do składowej danych pola, którego stan chcesz sprawdzić lub wartość NULL, aby sprawdzić, czy są dowolne z pól o wartości Null.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli element członkowski danych określone pole jest oznaczone jako Null; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę funkcję elementu członkowskiego, aby ustalić, czy określone pole składowej danych, które zestawu rekordów został oflagowany jako wartości Null. (W terminologii bazy danych o wartości Null oznacza, że "po żadnej wartości" i nie jest taka sama jak wartość NULL w języku C++) Element członkowski danych pola jest oznaczony jako wartość Null, jest interpretowany jako kolumnę bieżącego rekordu, dla których nie ma żadnej wartości.  
  
> [!NOTE]
>  Ta funkcja elementu członkowskiego nie ma zastosowania w zestawy rekordów, które korzystają z zbiorcze pobieranie z wiersza. Jeśli zaimplementowano zbiorcze pobieranie z wiersza, następnie `IsFieldNull` zawsze zwraca wartość FALSE, a powoduje potwierdzenie nie powiodło się. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 `IsFieldNull` jest implementowane za pomocą [dofieldexchange —](#dofieldexchange).  
  
##  <a name="isfieldnullable"></a>  CRecordset::IsFieldNullable  
 Zwraca wartość różną od zera, jeśli określone pole w bieżącym rekordzie można ustawić wartości null (o żadnej wartości).  
  
```  
BOOL IsFieldNullable(void* pv);
```  
  
### <a name="parameters"></a>Parametry  
 *Wa*  
 Wskaźnik do składowej danych pola, którego stan chcesz sprawdzić lub wartość NULL, aby określić, jeśli dowolne pole można ustawić na wartość Null.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę funkcję elementu członkowskiego, aby ustalić, czy określone pole składowej danych "nullable" (może być ustawiona na wartość Null; C++ o wartości NULL nie jest taka sama jak wartość Null, oznacza to, w terminologii bazy danych "posiadanie żadnej wartości").  
  
> [!NOTE]
>  Jeśli zaimplementowano zbiorcze pobieranie z wiersza, nie można wywołać `IsFieldNullable`. Zamiast tego należy wywołać [GetODBCFieldInfo](#getodbcfieldinfo) funkcja elementu członkowskiego, aby ustalić, czy pole można ustawić na wartość Null. Należy zauważyć, że zawsze można wywołać `GetODBCFieldInfo`, niezależnie od tego, czy udało Ci się wdrożyć zbiorcze pobieranie z wiersza. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Pola, które nie może mieć wartości Null, musi mieć wartość. Jeśli spróbujesz ustawić takiego pola na wartość Null, podczas dodawania lub aktualizowania rekordu źródła danych odrzuci dodanie lub aktualizacja, i [aktualizacji](#update) spowoduje zgłoszenie wyjątku. Wyjątek występuje po wywołaniu `Update`, nie wtedy, gdy wywołujesz [SetFieldNull](#setfieldnull).  
  
 Użycie wartości NULL dla pierwszego argumentu funkcji zostaną zastosowane tylko do funkcji `outputColumn` pól nie `param` pola. Na przykład wywołanie  
  
 [!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 ustawi tylko `outputColumn` pola na wartość NULL; `param` pola będzie to miało wpływu.  
  
 Do pracy nad `param` pól, należy podać rzeczywistego adresu poszczególnych `param` chcesz pracować, takich jak:  
  
 [!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 Oznacza to, nie można ustawić wszystkie `param` pola na wartość NULL, jak w przypadku `outputColumn` pola.  
  
 `IsFieldNullable` jest implementowane za pomocą [dofieldexchange —](#dofieldexchange).  
  
##  <a name="isopen"></a>  CRecordset::IsOpen  
 Określa, czy zestaw rekordów już otwarte.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli obiekty zestawów rekordów [Otwórz](#open) lub [Requery](#requery) wcześniej została wywołana funkcja elementu członkowskiego i nie została zamknięta zestawu rekordów; w przeciwnym razie 0.  
  
##  <a name="m_hstmt"></a>  CRecordset::m_hstmt  
 Zawiera dojście do struktury danych ODBC oświadczenie typu HSTMT, skojarzony zestaw rekordów.  
  
### <a name="remarks"></a>Uwagi  
 Każde zapytanie do źródła danych ODBC jest skojarzony z HSTMT.  
  
> [!CAUTION]
>  Nie używaj `m_hstmt` przed [Otwórz](#open) została wywołana.  
  
 Zwykle nie trzeba uzyskać bezpośredni dostęp HSTMT, ale możesz go potrzebować direct wykonywania instrukcji SQL. `ExecuteSQL` Funkcji składowej klasy typu `CDatabase` stanowi przykład użycia `m_hstmt`.  
  
##  <a name="m_nfields"></a>  CRecordset::m_nFields  
 Zawiera liczbę elementy członkowskie danych pola w klasie rekordów; oznacza to, że liczba kolumn wybranych przez zestaw rekordów ze źródła danych.  
  
### <a name="remarks"></a>Uwagi  
 Konstruktor dla klasy zestaw rekordów musi inicjować `m_nFields` z prawidłową liczbą. Jeśli nie zaimplementowano wiersz zbiorcze pobieranie, ClassWizard zapisuje ten proces inicjowania dla Ciebie służy do deklarowania klasy zestawu rekordów. Można go także zapisać ręcznie.  
  
 Środowisko wykorzystuje tę liczbę do zarządzania interakcją między elementy członkowskie danych pola i odpowiednie kolumny bieżącego rekordu w źródle danych.  
  
> [!CAUTION]
>  Ta liczba musi odpowiadać liczba "kolumn wyjściowych" zarejestrowanego w `DoFieldExchange` lub `DoBulkFieldExchange` po wywołaniu [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) z parametrem `CFieldExchange::outputColumn`.  
  
 Kolumny można powiązać dynamicznie, zgodnie z opisem w artykule "zestaw rekordów: dynamiczne powiązanie kolumn danych." Jeśli tak zrobisz, musisz zwiększyć liczby w `m_nFields` aby odzwierciedlić liczba funkcji RFX lub zbiorcze RFX wywołań swojej `DoFieldExchange` lub `DoBulkFieldExchange` funkcję członkowską dynamicznie powiązane kolumny.  
  
 Aby uzyskać więcej informacji, zobacz artykuły [zestaw rekordów: dynamiczne powiązanie danych kolumn (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) i [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Przykład  
 Zapoznaj się z artykułem [wymiana pól rekordów: za pomocą RFX](../../data/odbc/record-field-exchange-using-rfx.md).  
  
##  <a name="m_nparams"></a>  CRecordset::m_nParams  
 Zawiera liczbę elementy członkowskie danych parametru w klasie rekordów; oznacza to liczba parametrów są przekazywane z zapytaniem zestawu rekordów.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli klasa zestaw rekordów zawiera wszystkie elementy członkowskie danych parametru, Konstruktor dla klasy należy zainicjować `m_nParams` z prawidłową liczbą. Wartość `m_nParams` wartość domyślna to 0. Jeśli dodasz elementy członkowskie danych parametru, (które należy wykonać ręcznie) należy również ręcznie dodać inicjalizacji w konstruktorze klasy, aby odzwierciedlić liczba parametrów (musi być przynajmniej tak duże jak liczba '' symbole zastępcze w swojej `m_strFilter` lub `m_strSort`ciągu).  
  
 Struktura używa tego numeru, gdy go parametryzuje dane zapytania w zestawie rekordów.  
  
> [!CAUTION]
>  Ta liczba musi odpowiadać liczbę "params" zarejestrowanego w `DoFieldExchange` lub `DoBulkFieldExchange` po wywołaniu [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) z wartością parametru `CFieldExchange::inputParam`, `CFieldExchange::param`, `CFieldExchange::outputParam`, lub `CFieldExchange::inoutParam`.  
  
### <a name="example"></a>Przykład  
  Zobacz artykuły [zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) i [wymiana pól rekordów: za pomocą RFX](../../data/odbc/record-field-exchange-using-rfx.md).  
  
##  <a name="m_pdatabase"></a>  CRecordset::m_pDatabase  
 Zawiera wskaźnik do `CDatabase` obiektu za pomocą których zestaw rekordów jest połączony ze źródłem danych.  
  
### <a name="remarks"></a>Uwagi  
 Ta zmienna jest ustawiona na dwa sposoby. Zazwyczaj należy przekazać wskaźnik do już połączoną `CDatabase` obiektu podczas konstruowania obiektu zestawu rekordów. Jeśli zamiast tego należy przekazać NULL `CRecordset` tworzy `CDatabase` obiekt dla Ciebie i łączy ją. W obu przypadkach `CRecordset` przechowuje wskaźnik w tej zmiennej.  
  
 Zwykle nie bezpośrednio należy użyć wskaźnika przechowywania w `m_pDatabase`. Jeśli piszesz własne rozszerzenia `CRecordset`, jednak czasami trzeba za pomocą wskaźnika. Na przykład może być potrzebny wskaźnika można zgłaszać własne `CDBException`s. Lub możesz go potrzebować, jeśli chcesz zrobić coś korzystając z tych samych `CDatabase` obiektu, takie jak uruchamianie transakcji, ustawienie przekroczeń limitu czasu, lub podczas wywoływania `ExecuteSQL` funkcji składowej klasy typu `CDatabase` do wykonywania instrukcji SQL bezpośrednio.  
  
##  <a name="m_strfilter"></a>  CRecordset::m_strFilter  
 Po utworzenia obiekt zestawu rekordów, ale przed wywołaniem jego `Open` element członkowski funkcji, ten element członkowski danych umożliwiają przechowywanie `CString` zawierający SQL **gdzie** klauzuli.  
  
### <a name="remarks"></a>Uwagi  
 Zestaw rekordów używa tego ciągu do ograniczenia (lub filtr) rejestruje go wybierze podczas `Open` lub `Requery` wywołania. Jest to przydatne do wybierania podzestaw rekordów, takich jak "wszyscy sprzedawcy w Kalifornii" ("stan = pl"). Składnia ODBC SQL **gdzie** klauzula jest  
  
 `WHERE search-condition`  
  
 Należy zauważyć, że nie zostanie uwzględniony **gdzie** — słowo kluczowe w ciągu. Struktura dostarcza je.  
  
 Można również parametryzacja ciągu filtru przez umieszczenie '' symbole zastępcze w wywołaniach, deklarowania element członkowski danych parametru w swojej klasie dla każdego symbolu zastępczego i przekazywanie parametrów do zestawu rekordów w czasie wykonywania. Dzięki temu można utworzyć filtr w czasie wykonywania. Aby uzyskać więcej informacji, zobacz artykuł [zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
 Aby uzyskać więcej informacji na temat SQL **gdzie** zdań, zapoznaj się z artykułem [SQL](../../data/odbc/sql.md). Aby uzyskać więcej informacji na temat wybierania i filtrowania rekordów, zobacz artykuł [zestaw rekordów: filtrowanie rekordów (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDatabase#30](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]  
  
##  <a name="m_strsort"></a>  CRecordset::m_strSort  
 Po utworzenia obiekt zestawu rekordów, ale przed wywołaniem jego `Open` element członkowski funkcji, ten element członkowski danych umożliwiają przechowywanie `CString` zawierający SQL **ORDER BY** klauzuli.  
  
### <a name="remarks"></a>Uwagi  
 Zestaw rekordów używa tego ciągu, aby sortować rekordy go wybierze podczas `Open` lub `Requery` wywołania. Ta funkcja umożliwia sortowanie rekordów na co najmniej jedną kolumnę. Składnia ODBC SQL **ORDER BY** klauzula jest  
  
 `ORDER BY sort-specification [, sort-specification]...`  
  
 gdzie specyfikacji sortowania jest liczbą całkowitą lub nazwę kolumny. Można również określić kolejność kolejności rosnącej lub malejącej (kolejności rosnącej domyślnie), dodając do listy kolumn w ciąg sortowania "ASC" lub "Opis". Wybrane rekordy będą sortowane najpierw pierwsza kolumna na liście, a następnie drugiej i tak dalej. Na przykład może zamówić zestawu rekordów "Klientów", nazwisko, a następnie imię. Liczba kolumn, które można wyświetlić listę zależy od źródła danych. Aby uzyskać więcej informacji zobacz zestaw Windows SDK.  
  
 Należy zauważyć, że nie zostanie uwzględniony **ORDER BY** — słowo kluczowe w ciągu. Struktura dostarcza je.  
  
 Aby uzyskać więcej informacji na temat klauzule SQL, zobacz artykuł [SQL](../../data/odbc/sql.md). Aby uzyskać więcej informacji na temat sortowanie rekordów, zobacz artykuł [zestaw rekordów: sortowanie rekordów (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDatabase#31](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]  
  
##  <a name="move"></a>  CRecordset::Move  
 Przenosi bieżący wskaźnik rekordu w zestawie rekordów do przodu lub do tyłu.  
  
```  
virtual void Move(
    long nRows,  
    WORD wFetchType = SQL_FETCH_RELATIVE);
```  
  
### <a name="parameters"></a>Parametry  
 *nRows*  
 Liczba wierszy do przechodzenia do przodu lub Wstecz. Wartości dodatnich Przesuń do przodu, pod koniec zestawu rekordów. Wartości ujemne do tyłu, kierunku początku.  
  
 *wFetchType*  
 Określa zestaw wierszy, `Move` powoduje pobranie. Aby uzyskać więcej informacji zobacz uwagi.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku przekazania wartości 0 dla *nRows*, `Move` Odświeża bieżący rekord; `Move` zakończy wszystkie bieżące `AddNew` lub `Edit` tryb co powoduje przywrócenie wartości bieżącego rekordu przed `AddNew` lub `Edit` została wywołana.  
  
> [!NOTE]
>  Po przeniesieniu za pośrednictwem zestawu rekordów, nie można pominąć usuniętych rekordów. Zobacz [CRecordset::IsDeleted](#isdeleted) Aby uzyskać więcej informacji. Po otwarciu `CRecordset` z `skipDeletedRecords` zestaw, opcji `Move` potwierdzenia, jeśli *nRows* parametr ma wartość 0. To zachowanie zapobiega odświeżania wierszy, które są usuwane przez inne aplikacje klienckie przy użyciu tych samych danych. Zobacz *dwOption* parametru w [Otwórz](#open) opis `skipDeletedRecords`.  
  
 `Move` powoduje przeniesienie zestawu rekordów przez zestawy wierszy. Na podstawie wartości dla *nRows* i *wFetchType*, `Move` pobiera odpowiednie zestawu wierszy, a następnie udostępnia pierwszego rekordu w tym zestawie wierszy bieżącego rekordu. Jeśli nie zaimplementowano zbiorcze pobieranie z wiersza, następnie rozmiar wierszy ma zawsze numer 1. Podczas pobierania zestawu wierszy `Move` bezpośrednio wywołuje [CheckRowsetError](#checkrowseterror) funkcję elementu członkowskiego, aby obsługiwać błędy wynikające z fetch.  
  
 W zależności od wartości, należy przekazać `Move` jest równoważna z innymi `CRecordset` funkcji elementów członkowskich. W szczególności wartość *wFetchType* może wskazywać, funkcja elementu członkowskiego, która jest bardziej intuicyjne i często preferowaną metodą przeniesienie bieżącego rekordu.  
  
 Poniższa tabela zawiera listę możliwych wartości dla *wFetchType*, zestaw wierszy, `Move` powoduje pobranie na podstawie *wFetchType* i *nRows*i dowolnego równoważne element członkowski odpowiadający funkcja *wFetchType*.  
  
|wFetchType|Pobrano wierszy|Funkcja składowa równoważne|  
|----------------|--------------------|--------------------------------|  
|SQL_FETCH_RELATIVE (wartość domyślna)|Początkowy zestaw wierszy *nRows* wiersze z pierwszego wiersza w bieżącym zestawie wierszy.||  
|SQL_FETCH_NEXT|Następny zestaw wierszy; *nRows* jest ignorowana.|[MoveNext](#movenext)|  
|SQL_FETCH_PRIOR|Poprzednie wierszy; *nRows* jest ignorowana.|[Moveprev —](#moveprev)|  
|SQL_FETCH_FIRST|Pierwszy zestaw wierszy w zestawie rekordów; *nRows* jest ignorowana.|[MoveFirst](#movefirst)|  
|SQL_FETCH_LAST|Ostatnie kompletny zestaw wierszy w zestawie rekordów; *nRows* jest ignorowana.|[MoveLast](#movelast)|  
|SQL_FETCH_ABSOLUTE|Jeśli *nRows* > 0, zestawu wierszy od *nRows* wiersze na początku wybrać odpowiedni zestaw rekordów. Jeśli *nRows* < 0, zestawu wierszy od *nRows* wiersze na końcu zestawu rekordów. Jeśli *nRows* = 0, zwracana jest warunek początku pliku (BOF).|[Setabsoluteposition —](#setabsoluteposition)|  
|SQL_FETCH_BOOKMARK|Począwszy od wiersza, którego wartość zakładki odnosi się do zestawu wierszy *nRows*.|[SetBookmark](#setbookmark)|  
  
> [!NOTE]
>  Dla zestawów rekordów tylko do przodu `Move` obowiązuje tylko z wartością SQL_FETCH_NEXT dla *wFetchType*.  
  
> [!CAUTION]
>  Wywoływanie `Move` zgłasza wyjątek, jeśli zestaw rekordów nie zawiera żadnych rekordów. Aby ustalić, czy zestaw rekordów zawiera wszystkie rekordy, należy wywołać [IsBOF](#isbof) i [IsEOF](#iseof).  
  
> [!NOTE]
>  Jeśli przewiniesz w przeszłości na początku lub na końcu zestawu rekordów (`IsBOF` lub `IsEOF` zwraca wartość różną od zera), wywoływania `Move` funkcji prawdopodobnie spowoduje zgłoszenie `CDBException`. Na przykład jeśli `IsEOF` zwraca wartość różną od zera i `IsBOF` nie, następnie `MoveNext` spowoduje zgłoszenie wyjątku, ale `MovePrev` nie będzie.  
  
> [!NOTE]
>  Jeśli wywołasz `Move` podczas bieżącego rekordu zaktualizowano lub dodano i aktualizacje zostaną utracone bez ostrzeżenia.  
  
 Aby uzyskać więcej informacji o nawigacji zestawu rekordów, zobacz artykuły [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) i [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Aby uzyskać powiązane informacje, zobacz opis funkcji interfejsu API ODBC `SQLExtendedFetch` w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDatabase#28](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]  
  
##  <a name="movefirst"></a>  CRecordset::MoveFirst  
 Sprawia, że pierwszy rekord w pierwszym zestawie wierszy bieżącego rekordu.  
  
```  
void MoveFirst();
```  
  
### <a name="remarks"></a>Uwagi  
 Niezależnie od tego, czy zbiorcze pobieranie z wiersza został zaimplementowany będzie zawsze pierwszego rekordu w zestawie rekordów.  
  
 Nie trzeba wywoływać `MoveFirst` bezpośrednio po otwarciu zestawu rekordów. W tym czasie pierwszego rekordu (jeśli istnieje) jest automatycznie bieżącego rekordu.  
  
> [!NOTE]
>  Ta funkcja elementu członkowskiego jest nieprawidłowy dla zestawów rekordów tylko do przodu.  
  
> [!NOTE]
>  Po przeniesieniu za pośrednictwem zestawu rekordów, nie można pominąć usuniętych rekordów. Zobacz [IsDeleted](#isdeleted) funkcja elementu członkowskiego, aby uzyskać szczegółowe informacje.  
  
> [!CAUTION]
>  Wywołanie dowolnego z `Move` funkcje zgłasza wyjątek, jeśli zestaw rekordów nie zawiera żadnych rekordów. Aby ustalić, czy zestaw rekordów zawiera wszystkie rekordy, należy wywołać `IsBOF` i `IsEOF`.  
  
> [!NOTE]
>  Jeśli należy wywołać dowolną z `Move` funkcji podczas bieżącego rekordu zaktualizowano lub dodano i aktualizacje zostaną utracone bez ostrzeżenia.  
  
 Aby uzyskać więcej informacji o nawigacji zestawu rekordów, zobacz artykuły [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) i [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [IsBOF](#isbof).  
  
##  <a name="movelast"></a>  CRecordset::MoveLast  
 Sprawia, że pierwszy rekord w ostatnich wierszy pełną bieżącego rekordu.  
  
```  
void MoveLast();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli nie zaimplementowano zbiorcze pobieranie z wiersza, rekordów wierszy rozmiar wynosi 1, więc `MoveLast` po prostu przenosi do ostatniego rekordu w zestawie rekordów.  
  
> [!NOTE]
>  Ta funkcja elementu członkowskiego jest nieprawidłowy dla zestawów rekordów tylko do przodu.  
  
> [!NOTE]
>  Po przeniesieniu za pośrednictwem zestawu rekordów, nie można pominąć usuniętych rekordów. Zobacz [IsDeleted](#isdeleted) funkcja elementu członkowskiego, aby uzyskać szczegółowe informacje.  
  
> [!CAUTION]
>  Wywołanie dowolnego z `Move` funkcje zgłasza wyjątek, jeśli zestaw rekordów nie zawiera żadnych rekordów. Aby ustalić, czy zestaw rekordów zawiera wszystkie rekordy, należy wywołać `IsBOF` i `IsEOF`.  
  
> [!NOTE]
>  Jeśli należy wywołać dowolną z `Move` funkcji podczas bieżącego rekordu zaktualizowano lub dodano i aktualizacje zostaną utracone bez ostrzeżenia.  
  
 Aby uzyskać więcej informacji o nawigacji zestawu rekordów, zobacz artykuły [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) i [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [IsBOF](#isbof).  
  
##  <a name="movenext"></a>  CRecordset::MoveNext  
 Sprawia, że pierwszy rekord w zestawie następnego wierszy bieżącego rekordu.  
  
```  
void MoveNext();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli nie zaimplementowano zbiorcze pobieranie z wiersza, rekordów wierszy rozmiar wynosi 1, więc `MoveNext` po prostu przechodzi do następnego rekordu.  
  
> [!NOTE]
>  Po przeniesieniu za pośrednictwem zestawu rekordów, nie można pominąć usuniętych rekordów. Zobacz [IsDeleted](#isdeleted) funkcja elementu członkowskiego, aby uzyskać szczegółowe informacje.  
  
> [!CAUTION]
>  Wywołanie dowolnego z `Move` funkcje zgłasza wyjątek, jeśli zestaw rekordów nie zawiera żadnych rekordów. Aby ustalić, czy zestaw rekordów zawiera wszystkie rekordy, należy wywołać `IsBOF` i `IsEOF`.  
  
> [!NOTE]
>  Zalecane jest również, że wywołanie `IsEOF` przed wywołaniem `MoveNext`. Na przykład, jeśli przewiniesz poza końcem zestawu rekordów `IsEOF` zwraca wartość różną od zera; kolejne wywołanie `MoveNext` spowoduje zgłoszenie wyjątku.  
  
> [!NOTE]
>  Jeśli należy wywołać dowolną z `Move` funkcji podczas bieżącego rekordu zaktualizowano lub dodano i aktualizacje zostaną utracone bez ostrzeżenia.  
  
 Aby uzyskać więcej informacji o nawigacji zestawu rekordów, zobacz artykuły [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) i [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [IsBOF](#isbof).  
  
##  <a name="moveprev"></a>  CRecordset::MovePrev  
 Sprawia, że pierwszy rekord w poprzednim zestawie wierszy bieżącego rekordu.  
  
```  
void MovePrev();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli nie zaimplementowano zbiorcze pobieranie z wiersza, rekordów wierszy rozmiar wynosi 1, więc `MovePrev` po prostu przenosi do poprzedniego rekordu.  
  
> [!NOTE]
>  Ta funkcja elementu członkowskiego jest nieprawidłowy dla zestawów rekordów tylko do przodu.  
  
> [!NOTE]
>  Po przeniesieniu za pośrednictwem zestawu rekordów, nie można pominąć usuniętych rekordów. Zobacz [IsDeleted](#isdeleted) funkcja elementu członkowskiego, aby uzyskać szczegółowe informacje.  
  
> [!CAUTION]
>  Wywołanie dowolnego z `Move` funkcje zgłasza wyjątek, jeśli zestaw rekordów nie zawiera żadnych rekordów. Aby ustalić, czy zestaw rekordów zawiera wszystkie rekordy, należy wywołać `IsBOF` i `IsEOF`.  
  
> [!NOTE]
>  Zalecane jest również, że wywołanie `IsBOF` przed wywołaniem `MovePrev`. Jeśli przewiniesz w przód od początku zestawu rekordów, na przykład `IsBOF` zwraca wartość różną od zera; kolejne wywołanie `MovePrev` spowoduje zgłoszenie wyjątku.  
  
> [!NOTE]
>  Jeśli należy wywołać dowolną z `Move` funkcji podczas bieżącego rekordu zaktualizowano lub dodano i aktualizacje zostaną utracone bez ostrzeżenia.  
  
 Aby uzyskać więcej informacji o nawigacji zestawu rekordów, zobacz artykuły [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) i [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [IsBOF](#isbof).  
  
##  <a name="onsetoptions"></a>  CRecordset::OnSetOptions  
 Wywołuje się, by ustawić opcje (używany po wybraniu) dla określonej instrukcji ODBC.  
  
```  
virtual void OnSetOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>Parametry  
 *hstmt*  
 HSTMT instrukcji ODBC, których opcje mają być tworzone.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj `OnSetOptions` można ustawić opcje (używany po wybraniu) dla określonej instrukcji ODBC. Struktura wywołuje tę funkcję elementu członkowskiego, aby ustawić opcje początkowego zestawu rekordów. `OnSetOptions` Określa źródło danych obsługę przewijany kursorów i współbieżność kursora i w związku z tym ustawia opcje zestawu rekordów. (Natomiast `OnSetOptions` jest używany dla operacji zaznaczania i `OnSetUpdateOptions` jest używany dla operacji aktualizacji.)  
  
 Zastąp `OnSetOptions` Aby ustawić opcje określonego sterownika lub źródła danych. Na przykład, jeśli źródła danych obsługuje otwieranie w trybie wyłączności, mogą zastąpić `OnSetOptions` z zalet tej możliwości.  
  
 Aby uzyskać więcej informacji na temat kursorów, zobacz artykuł [ODBC](../../data/odbc/odbc-basics.md).  
  
##  <a name="onsetupdateoptions"></a>  CRecordset::OnSetUpdateOptions  
 Wywołuje się, by ustawić opcje (używane na aktualizację) dla określonej instrukcji ODBC.  
  
```  
virtual void OnSetUpdateOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>Parametry  
 *hstmt*  
 HSTMT instrukcji ODBC, których opcje mają być tworzone.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj `OnSetUpdateOptions` można ustawić opcje (używane na aktualizację) dla określonej instrukcji ODBC. Struktura wywołuje tej funkcji elementu członkowskiego, po utworzeniu HSTMT do aktualizowania rekordów w zestawie rekordów. (Natomiast `OnSetOptions` jest używany dla operacji zaznaczania i `OnSetUpdateOptions` jest używany dla operacji aktualizacji.) `OnSetUpdateOptions` Określa źródło danych obsługę przewijany kursorów i współbieżność kursora i w związku z tym ustawia opcje zestawu rekordów.  
  
 Zastąp `OnSetUpdateOptions` Aby ustawić opcje instrukcji ODBC, przed którymi instrukcja umożliwia dostęp do bazy danych.  
  
 Aby uzyskać więcej informacji na temat kursorów, zobacz artykuł [ODBC](../../data/odbc/odbc-basics.md).  
  
##  <a name="open"></a>  CRecordset::Open  
 Zostanie otwarty zestaw rekordów, pobieranie tabeli lub wykonywania zapytania, które reprezentuje zestaw rekordów.  
  
```  
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,  
    LPCTSTR lpszSQL = NULL,  
    DWORD dwOptions = none);
```  
  
### <a name="parameters"></a>Parametry  
 *nOpenType*  
 Zaakceptuj wartość domyślną, AFX_DB_USE_DEFAULT_TYPE lub użyj jednego z następujących wartości z kolekcji `enum OpenType`:  
  
- `CRecordset::dynaset` Zestaw rekordów za pomocą dwukierunkowych przewijania. Członkostwo i kolejność rekordów są ustalane w momencie zestawu rekordów jest otwarty, ale zmiany wprowadzone przez innych użytkowników do wartości danych są widoczne, po operacji pobierania. Zestawy dynamiczne są również nazywane oparte na zestawie kluczy zestawy rekordów.  
  
- `CRecordset::snapshot` Statyczny zestaw rekordów za pomocą dwukierunkowych przewijania. Członkostwo i kolejność rekordów są ustalane w momencie otwarcia zestawu rekordów; wartości danych są określone, gdy rekordy są dołączone. Zmiany wprowadzone przez innych użytkowników nie są widoczne do czasu zamknięcia i ponownego otwarcia zestawu rekordów.  
  
- `CRecordset::dynamic` Zestaw rekordów za pomocą dwukierunkowych przewijania. Zmiany wprowadzone przez innych użytkowników do wartości członkostwa, kolejność i dane są widoczne, po operacji pobierania. Należy pamiętać, że wiele sterowników ODBC nie obsługują tego typu zestawu rekordów.  
  
- `CRecordset::forwardOnly` Tylko do odczytu rekordów przy użyciu tylko do przodu przewijania.  
  
     Aby uzyskać `CRecordset`, wartość domyślna to `CRecordset::snapshot`. Mechanizm wartość domyślną pozwala kreatorów Visual C++, aby korzystać z obu ODBC `CRecordset` i DAO `CDaoRecordset`, które mają różne ustawienia domyślne.  
  
 Aby uzyskać więcej informacji o tych typach rekordów, zobacz artykuł [zestawu rekordów (ODBC)](../../data/odbc/recordset-odbc.md). Aby uzyskać powiązane informacje zobacz artykuł "Za pomocą bloku i przewijany kursorów" w zestawie Windows SDK.  
  
> [!CAUTION]
>  Jeśli żądanego typu nie jest obsługiwana, w ramach zgłasza wyjątek.  
  
 *lpszSQL*  
 Wskaźnik ciągu, zawierające jedną z następujących czynności:  
  
-   Wskaźnik o wartości NULL.  
  
-   Nazwa tabeli.  
  
-   SQL **wybierz** — instrukcja (opcjonalnie wraz z SQL **gdzie** lub **ORDER BY** klauzuli).  
  
-   A **WYWOŁANIA** instrukcję, określając nazwę wstępnie zdefiniowanego zapytania (procedura składowana). Należy zachować ostrożność, nie wstawiaj odstęp między nawiasów klamrowych i **WYWOŁANIA** — słowo kluczowe.  
  
 Aby uzyskać więcej informacji na temat tych parametrów zobacz tabelę i dyskusji w ClassWizard rolę w ramach uwagi.  
  
> [!NOTE]
>  Kolejność kolumn w zestawie wyników musi być zgodna z kolejnością RFX lub zbiorcze RFX funkcja wywołuje swojej [dofieldexchange —](#dofieldexchange) lub [dobulkfieldexchange —](#dobulkfieldexchange) funkcji zastąpienie.  
  
 *dwOptions*  
 Maska bitów, które można określić kombinacja wartości z poniższej listy. Niektóre z tych wzajemnie się wykluczają. Wartość domyślna to **Brak**.  
  
- `CRecordset::none` Brak ustawionych opcji. Wartości tego parametru jest wzajemnie wykluczających się przy użyciu wszystkich pozostałych wartości. Domyślnie zestaw rekordów, mogą być aktualizowane przy użyciu [Edytuj](#edit) lub [Usuń](#delete) i umożliwia dołączanie nowych rekordów z [działają funkcje AddNew](#addnew). Aktualizacji zależy od źródła danych oraz jak na *nOpenType* opcji, które określisz. Optymalizacja dodatki zbiorcze nie jest dostępna. Zbiorcze pobieranie z wiersza nie będzie zaimplementowana. Usunięte rekordy nie zostaną pominięte podczas nawigacji zestawu rekordów. Zakładki nie są dostępne. Sprawdzanie automatyczne zanieczyszczone pola jest zaimplementowana.  
  
- `CRecordset::appendOnly` Nie zezwalaj na `Edit` lub `Delete` na zestaw rekordów. Zezwalaj na `AddNew` tylko. Ta opcja jest wzajemnie wykluczających się przy użyciu `CRecordset::readOnly`.  
  
- `CRecordset::readOnly` Otwórz zestaw rekordów jako tylko do odczytu. Ta opcja jest wzajemnie wykluczających się przy użyciu `CRecordset::appendOnly`.  
  
- `CRecordset::optimizeBulkAdd` Przygotowana instrukcja SQL umożliwia optymalizowanie Dodawanie wielu rekordów w tym samym czasie. Ma zastosowanie tylko wtedy, gdy nie używasz funkcji interfejsu API ODBC `SQLSetPos` można zaktualizować zestawu rekordów. Pierwszą aktualizacją określa pola, które są oznaczone zanieczyszczeniu. Ta opcja jest wzajemnie wykluczających się przy użyciu `CRecordset::useMultiRowFetch`.  
  
- `CRecordset::useMultiRowFetch` Implementowanie zbiorcze pobieranie z wiersza Aby zezwolić na wiele wierszy, które mają zostać pobrane w ramach jednego pobierania operacji. Jest to zaawansowana funkcja mające na celu poprawę wydajności; Zbiorcza wymiana pól rekordów nie jest obsługiwana przez ClassWizard. Ta opcja jest wzajemnie wykluczających się przy użyciu `CRecordset::optimizeBulkAdd`. Należy pamiętać, że jeśli określisz `CRecordset::useMultiRowFetch`, następnie opcję `CRecordset::noDirtyFieldCheck` zostanie włączona automatycznie (podwójnego buforowania nie będą dostępne); na zestawy rekordów tylko do przodu, opcja `CRecordset::useExtendedFetch` zostanie włączone automatycznie. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
- `CRecordset::skipDeletedRecords` Pomiń wszystkie usunięte rekordy, podczas przechodzenia przez zestaw rekordów. Spowoduje to spowolnienie działania, w niektórych pobraniach względnych. Ta opcja nie jest prawidłowy w zestawy rekordów tylko do przodu. Jeśli wywołasz [przenieść](#move) z *nRows* parametrem ustawionym na wartość 0 i `CRecordset::skipDeletedRecords` zestaw, opcji `Move` będzie potwierdzenia. Należy pamiętać, że `CRecordset::skipDeletedRecords` przypomina *pakowania sterownik*, co oznacza, że usunięte wiersze są usuwane z zestawu rekordów. Jednakże jeśli sterownik pakietów rekordów, następnie pominie ona tylko te rekordy, które można usunąć; nie pominie ona rekordy zostały usunięte przez innych użytkowników, gdy zestaw rekordów jest otwarty. `CRecordset::skipDeletedRecords` pominie wiersz usunięty przez innych użytkowników.  
  
- `CRecordset::useBookmarks` Może używać zakładek zestawu rekordów, jeśli jest obsługiwany. Zakładki wolne pobierania danych, ale poprawić wydajność nawigowanie wśród danych. Nie jest prawidłowy na zestawy rekordów tylko do przodu. Aby uzyskać więcej informacji, zobacz artykuł [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).  
  
- `CRecordset::noDirtyFieldCheck` Wyłącz automatyczne pola zanieczyszczone sprawdzanie (podwójnego buforowania). Poprawi to wydajność; jednak należy ręcznie oznaczyć pola jako zakłóconych, wywołując `SetFieldDirty` i `SetFieldNull` funkcji elementów członkowskich. Należy pamiętać, że podwójnego buforowania w klasie `CRecordset` jest podobny do podwójnego buforowania w klasie `CDaoRecordset`. Jednak w `CRecordset`, nie można włączyć podwójnego buforowania dla poszczególnych pól; należy ją włączyć dla wszystkich pól lub ją wyłączyć dla wszystkich pól. Należy pamiętać, że jeśli określisz opcję `CRecordset::useMultiRowFetch`, następnie `CRecordset::noDirtyFieldCheck` zostanie włączona automatycznie; jednak `SetFieldDirty` i `SetFieldNull` nie można używać w zestawach rekordów, który implementuje zbiorcze pobieranie z wiersza.  
  
- `CRecordset::executeDirect` Nie należy używać przygotowanej instrukcji SQL. W celu zwiększenia wydajności, wybierz tę opcję, jeśli `Requery` nigdy nie zostanie wywołana funkcja elementu członkowskiego.  
  
- `CRecordset::useExtendedFetch` Implementowanie `SQLExtendedFetch` zamiast `SQLFetch`. To jest przeznaczona do implementowania zbiorcze pobieranie z wiersza w zestawach rekordów tylko do przodu. Jeśli określisz opcję `CRecordset::useMultiRowFetch` na rekordów, następnie `CRecordset::useExtendedFetch` zostanie włączone automatycznie.  
  
- `CRecordset::userAllocMultiRowBuffers` Użytkownik przyzna buforów magazynu danych. Użyj tej opcji w połączeniu z `CRecordset::useMultiRowFetch` Jeśli chcesz przydzielić własny magazyn; w przeciwnym razie ramach spowoduje automatyczne przydzielanie magazynu konieczne. Aby uzyskać więcej informacji, zobacz artykuł [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Należy pamiętać, że określenie `CRecordset::userAllocMultiRowBuffers` bez określania `CRecordset::useMultiRowFetch` spowoduje niepowodzenie asercji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli `CRecordset` obiekt był otwarty pomyślnie; w przeciwnym razie 0, jeśli [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) (jeśli jest to nazywane) zwraca wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę funkcję elementu członkowskiego, aby uruchomić zapytanie zdefiniowane przez zestaw rekordów. Przed wywołaniem `Open`, należy utworzyć obiekt zestawu rekordów.  
  
 Ten zestaw rekordów połączenia ze źródłem danych zależy od tego, jak utworzyć zestaw rekordów przed wywołaniem `Open`. W przypadku przekazania [CDatabase](../../mfc/reference/cdatabase-class.md) obiekt do Konstruktora zestawu rekordów, która nie została połączona ze źródłem danych korzysta z tej funkcji elementu członkowskiego [getdefaultconnect —](#getdefaultconnect) próby otwarcia obiektu bazy danych. Jeśli przekażesz wartości NULL do Konstruktora zestawu rekordów, Konstruktor konstruuje `CDatabase` obiekt dla Ciebie, i `Open` próbuje nawiązać połączenie z obiektu bazy danych. Szczegółowe informacje na temat zamykania zestawu rekordów i połączenie tych różnych okolicznościach, [Zamknij](#close).  
  
> [!NOTE]
>  Dostęp do źródła danych za pośrednictwem `CRecordset` obiekt zawsze jest udostępniony. W odróżnieniu od `CDaoRecordset` klasy, nie można użyć `CRecordset` obiekt, aby otworzyć źródła danych za pomocą wyłącznego dostępu.  
  
 Gdy wywołujesz `Open`, zapytania, zwykle SQL **wybierz** instrukcji, wybiera rekordy, w oparciu o kryteria, pokazano w poniższej tabeli.  
  
|Wartość parametru lpszSQL|Wybrane rekordy są określane przez|Przykład|  
|------------------------------------|----------------------------------------|-------------|  
|NULL|Ciąg zwracany przez `GetDefaultSQL`.||  
|Nazwa tabeli SQL|Wszystkie kolumny w tabeli listy w `DoFieldExchange` lub `DoBulkFieldExchange`.|`"Customer"`|  
|Nazwa wstępnie zdefiniowanego zapytania (procedura składowana)|Kolumny, które zdefiniowano zapytanie do zwrócenia.|`"{call OverDueAccts}"`|  
|**Wybierz** listy kolumn **FROM** listy tabel|Określone kolumny z określonej tabele.|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|  
  
> [!CAUTION]
>  Należy zachować ostrożność, że nie należy wstawiać dodatkowych spacji w ciągu SQL. Na przykład, jeśli wstawianie odstępów między nawiasów klamrowych i **WYWOŁANIA** — słowo kluczowe, MFC zostanie błędnie interpretuje ciąg SQL jako nazwę tabeli i dołączyć je do **wybierz** instrukcji, co spowoduje, że zgłaszanego wyjątku. Podobnie, jeśli wstępnie zdefiniowane zapytanie używa parametru wyjściowego, nie wstawiaj odstęp między nawiasów klamrowych i '' symboli. Ponadto nie należy wstawić odstęp przed klamrowym w **WYWOŁANIA** instrukcji lub przed **wybierz** — słowo kluczowe w **wybierz** instrukcji.  
  
 Procedura zwykle służy do przekazywania wartości NULL, aby `Open`; w takim przypadku `Open` wywołania [GetDefaultSQL](#getdefaultsql). Jeśli używasz pochodnej `CRecordset` klasy `GetDefaultSQL` zapewnia nazwy tabel określone w ClassWizard. Zamiast tego możesz określić inne informacje w `lpszSQL` parametru.  
  
 Niezależnie od przekazania, `Open` tworzy ostatni ciąg SQL dla zapytania (ciąg może zawierać SQL **gdzie** i **ORDER BY** klauzule dołączany do `lpszSQL` ciągów, które przekazałeś), a następnie wykonuje Zapytanie. Zbudowany ciągu można sprawdzić przez wywołanie metody [GetSQL](#getsql) po wywołaniu *`Open`. Aby uzyskać więcej informacji o tworzy instrukcji SQL zestawu rekordów i wybiera rekordy, zobacz artykuł [zestaw rekordów: jak zestawy rekordów wybierz rekordów (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).  
  
 Elementy członkowskie danych pola klasy zestawu rekordów, które są powiązane kolumny wybranych danych. Jeśli zwracane są wszystkie rekordy, pierwszy rekord staje się bieżącym rekordem.  
  
 Jeśli chcesz ustawić opcje dla zestawu rekordów, takich jak filtrowanie lub sortowanie, określ je po konstruujesz obiekty zestawów rekordów, ale przed wywołaniem `Open`. Jeśli chcesz odświeżyć rekordy w zestawie rekordów po zestawu rekordów jest już otwarty, wywołaj [Requery](#requery).  
  
 Aby uzyskać więcej informacji, w tym dodatkowe przykłady, zobacz artykuły [zestawu rekordów (ODBC)](../../data/odbc/recordset-odbc.md), [zestaw rekordów: jak zestawy rekordów wybierz rekordów (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md), i [zestaw rekordów: tworzenie i zamykanie Zestawy rekordów (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).  
  
### <a name="example"></a>Przykład  
 W poniższych przykładach kodu pokazano różne rodzaje `Open` wywołania.  
  
 [!code-cpp[NVC_MFCDatabase#16](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]  
  
##  <a name="refreshrowset"></a>  CRecordset::RefreshRowset  
 Aktualizuje dane i stan dla wiersza w bieżącym zestawie wierszy.  
  
```  
void RefreshRowset(
    WORD wRow,  
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```  
  
### <a name="parameters"></a>Parametry  
 *wRow*  
 Liczonego od jednego położenie wiersza w bieżącym zestawie wierszy. Wartość ta może wynosić od 0 do rozmiaru zestawu wierszy.  
  
 *wLockType*  
 Wartość wskazująca, jak zablokować wiersz po została odświeżona. Aby uzyskać więcej informacji zobacz uwagi.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku przekazania wartości zero dla *wRow*, a następnie zostaną odświeżone każdego wiersza w zestawie wierszy.  
  
 Aby użyć `RefreshRowset`, musi zaimplementowano zbiorcze pobieranie z wiersza, określając `CRecordset::useMulitRowFetch` opcji [Otwórz](#open) funkcja elementu członkowskiego.  
  
 `RefreshRowset` wywołuje funkcję interfejsu API ODBC `SQLSetPos`. *WLockType* parametr określa stan blokady wiersz po `SQLSetPos` został wykonany. W poniższej tabeli opisano możliwe wartości *wLockType*.  
  
|wLockType|Opis|  
|---------------|-----------------|  
|SQL_LOCK_NO_CHANGE (wartość domyślna)|Sterownik lub źródła danych gwarantuje, że wiersz jest ten sam stan zablokowane lub odblokowany, sprzed `RefreshRowset` została wywołana.|  
|SQL_LOCK_EXCLUSIVE|Sterownik lub źródła danych, które wyłącznie blokuje wiersza. Nie wszystkie źródła danych obsługuje ten typ blokady.|  
|SQL_LOCK_UNLOCK|Sterownik lub źródła danych odblokowuje wiersza. Nie wszystkie źródła danych obsługuje ten typ blokady.|  
  
 Aby uzyskać więcej informacji na temat `SQLSetPos`, zobacz dokumentację Windows SDK. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="requery"></a>  CRecordset::Requery  
 Ponownie kompiluje (odświeżanie) zestawu rekordów.  
  
```  
virtual BOOL Requery();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli zestaw rekordów został pomyślnie odbudowany; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli zwracane są wszystkie rekordy, pierwszy rekord staje się bieżącym rekordem.  
  
 Aby zestaw rekordów odzwierciedlić dodawania i usuwania, które wykorzystują źródła danych, należy przebudować zestaw rekordów, wywołując `Requery`. Jeśli zestaw rekordów jest dynamiczny, automatycznie odzwierciedla aktualizacji, które użytkownicy dokonać jego istniejące rekordy (ale nie dodatków). Jeśli zestaw rekordów jest migawką, należy wywołać `Requery` uwzględnienie zmian przez innych użytkowników, a także dodanych i usuniętych.  
  
 Dynamiczny lub migawki, należy wywołać `Requery` ilekroć chcesz ponownie skompilować rekordów przy użyciu nowego filtru lub sortowania lub nowych wartości parametrów. Ustaw nową właściwość filtrowania lub sortowania, przypisujące nowe wartości do `m_strFilter` i `m_strSort` przed wywołaniem `Requery`. Ustaw nowe parametry, przypisujące nowe wartości do elementów członkowskich danych parametru przed wywołaniem `Requery`. Jeśli filtrowania i sortowania ciągów nie ulegną zmianie, można ponownie użyć zapytania, co zwiększa wydajność.  
  
 Jeśli nie można ponownie utworzyć zestaw rekordów, zestaw rekordów jest zamknięty. Przed wywołaniem `Requery`, można określić, czy zestaw rekordów można ponowieniu przez wywołanie metody `CanRestart` funkcja elementu członkowskiego. `CanRestart` nie gwarantuje, że `Requery` zakończy się powodzeniem.  
  
> [!CAUTION]
>  Wywołaj `Requery` tylko wtedy, gdy wywołujesz [Otwórz](#open).  
  
### <a name="example"></a>Przykład  
 W tym przykładzie ponownie kompiluje zestaw rekordów, aby zastosować porządek sortowania.  
  
 [!code-cpp[NVC_MFCDatabase#29](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]  
  
##  <a name="setabsoluteposition"></a>  CRecordset::SetAbsolutePosition  
 Ustawia zestaw rekordów rekord odpowiadający numerowi określonego rekordu.  
  
```  
void SetAbsolutePosition(long nRows);
```  
  
### <a name="parameters"></a>Parametry  
 *nRows*  
 Liczonego od jednego porządkowym dla bieżącego rekordu w zestawie rekordów.  
  
### <a name="remarks"></a>Uwagi  
 `SetAbsolutePosition` Przenosi bieżący wskaźnik rekord na podstawie tego porządkowego położenia.  
  
> [!NOTE]
>  Ta funkcja elementu członkowskiego jest nieprawidłowy na zestawy rekordów tylko do przodu.  
  
 Dla zestawów rekordów ODBC to ustawienie odpowiadają położeniu bezwzględnemu 1 odwołuje się do pierwszego rekordu w zestawie rekordów; Ustawienie wartości 0 odwołuje się do położenia (BOF) na początku pliku.  
  
 Można również przekazać wartość ujemną, aby `SetAbsolutePosition`. W tym przypadku pozycja w zestawie rekordów jest oceniany na końcu zestawu rekordów. Na przykład `SetAbsolutePosition( -1 )` Przenosi bieżący wskaźnik rekordów do ostatniego rekordu w zestawie rekordów.  
  
> [!NOTE]
>  Położenie bezwzględne nie mają służyć jako numer rekordu zastępczy. Zakładki są nadal zalecany sposób przechowywania i powrocie do danej pozycji, ponieważ rekord zmiany pozycji po poprzednim rekordy zostaną usunięte. Ponadto możesz nie mieć pewność, że danego rekordu będzie miał tym samym położeniu bezwzględnym, jeśli zestaw rekordów jest utworzony ponownie, ponieważ kolejność poszczególnych rekordów w zestawie rekordów nie jest gwarantowane, chyba że zostanie utworzona za pomocą instrukcji języka SQL przy użyciu **ORDER BY** klauzuli.  
  
 Aby uzyskać więcej informacji o nawigacji zestawu rekordów i zakładki, zobacz artykuły [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) i [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).  
  
##  <a name="setbookmark"></a>  CRecordset::SetBookmark  
 Ustawia zestaw rekordów na rekord zawierający zakładką.  
  
```  
void SetBookmark(const CDBVariant& varBookmark);
```  
  
### <a name="parameters"></a>Parametry  
 *varBookmark*  
 Odwołanie do [CDBVariant](../../mfc/reference/cdbvariant-class.md) obiekt zawierający wartość zakładki dla określonego rekordu.  
  
### <a name="remarks"></a>Uwagi  
 Aby ustalić, czy zakładki są obsługiwane w zestawie rekordów, należy wywołać [CanBookmark](#canbookmark). Aby udostępnić zakładek, jeśli są one obsługiwane, należy ustawić `CRecordset::useBookmarks` opcji *dwOptions* parametru [Otwórz](#open) funkcja elementu członkowskiego.  
  
> [!NOTE]
>  Jeśli zakładki są nieobsługiwane lub jest niedostępny, wywołanie `SetBookmark` spowodują wyjątek. Zakładki nie są obsługiwane w zestawach rekordów tylko do przodu.  
  
 Aby najpierw pobrać zakładki w bieżącym rekordzie, należy wywołać [getbookmark —](#getbookmark), co pozwala na zaoszczędzenie wartość zakładki do `CDBVariant` obiektu. Później możesz powrócić do tego rekordu, wywołując `SetBookmark` przy użyciu wartości zapisanej zakładki.  
  
> [!NOTE]
>  Po niektórych operacjach zestawu rekordów, należy sprawdzić trwałości zakładkę przed wywołaniem `SetBookmark`. Na przykład, jeśli pobieranie zakładki z `GetBookmark` , a następnie wywołać `Requery`, zakładka może nie być już prawidłowa. Wywołaj [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) do sprawdzenia, czy można bezpiecznie wywołać `SetBookmark`.  
  
 Aby uzyskać więcej informacji na temat zakładek i nawigacji zestawu rekordów, zobacz artykuły [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) i [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="setfielddirty"></a>  CRecordset::SetFieldDirty  
 Flagi element członkowski danych pola zestawu rekordów, ponieważ zmianie lub bez zmian.  
  
```  
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *Wa*  
 Zawiera adres element członkowski danych pole w zestawie rekordów lub wartość NULL. Jeśli ma wartość NULL, są oznaczane wszystkie elementy członkowskie danych pola w zestawie rekordów. (C++ o wartości NULL nie jest taka sama jak wartość Null w terminologii bazy danych, co oznacza, że "po żadnej wartości.")  
  
 *bDirty*  
 Wartość TRUE, jeśli element członkowski danych pola zostanie oznaczony jako "zakłóconych" (zmieniono). W przeciwnym razie wartość FALSE, jeśli element członkowski danych pola zostanie oznaczony jako "Wyczyść" (bez zmian).  
  
### <a name="remarks"></a>Uwagi  
 Oznaczanie pól jako niezmieniony zapewnia, jest to pole nie jest aktualizowany i powoduje mniej ruchu SQL.  
  
> [!NOTE]
>  Ta funkcja elementu członkowskiego nie ma zastosowania w zestawy rekordów, które korzystają z zbiorcze pobieranie z wiersza. Jeśli zaimplementowano zbiorcze pobieranie z wiersza, następnie `SetFieldDirty` spowoduje niepowodzenie asercji. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Znaczniki framework zmienione elementy członkowskie danych pola, aby upewnić się, że będą one zapisywane do rekordu w źródle danych przez mechanizm pól rekordów (RFX) programu exchange. Zazwyczaj zmianę wartości pola ustawia pole zanieczyszczone automatycznie, dzięki czemu będą rzadko należy wywołać `SetFieldDirty` samodzielnie, ale czasami chcieć upewnij się, że kolumny będą jawnie zaktualizowane lub wstawione niezależnie od tego, jaka wartość w polu danych element członkowski.  
  
> [!CAUTION]
>  Wywołaj tę funkcję elementu członkowskiego, tylko wtedy, gdy wywołujesz [Edytuj](#edit) lub [działają funkcje AddNew](#addnew).  
  
 Użycie wartości NULL dla pierwszego argumentu funkcji zostaną zastosowane tylko do funkcji `outputColumn` pól nie `param` pola. Na przykład wywołanie  
  
 [!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 ustawi tylko `outputColumn` pola na wartość NULL; `param` pola będzie to miało wpływu.  
  
 Do pracy nad `param` pól, należy podać rzeczywistego adresu poszczególnych `param` chcesz pracować, takich jak:  
  
 [!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 Oznacza to, nie można ustawić wszystkie `param` pola na wartość NULL, jak w przypadku `outputColumn` pola.  
  
##  <a name="setfieldnull"></a>  CRecordset::SetFieldNull  
 Element członkowski danych pola zestawu rekordów flagi, jako wartość Null (konkretnie o żadna wartość) lub inną niż Null.  
  
```  
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *Wa*  
 Zawiera adres element członkowski danych pole w zestawie rekordów lub wartość NULL. Jeśli ma wartość NULL, są oznaczane wszystkie elementy członkowskie danych pola w zestawie rekordów. (C++ o wartości NULL nie jest taka sama jak wartość Null w terminologii bazy danych, co oznacza, że "po żadnej wartości.")  
  
 *bNull*  
 Różna od zera, jeśli element członkowski danych pola oflagowane jako mające żadnej wartości (Null). W przeciwnym razie 0, jeśli element członkowski danych pola jest być oznaczony jako inna niż Null.  
  
### <a name="remarks"></a>Uwagi  
 Po dodaniu nowego rekordu do zestawu rekordów, wszystkie elementy członkowskie danych pola są początkowo ustawiona na wartość Null i oznaczone jako "zakłóconych" (zmieniono). Po pobraniu rekord ze źródła danych jego kolumn już mają wartości lub mają wartość Null.  
  
> [!NOTE]
>  Nie wywołuj tej funkcji elementu członkowskiego na zestawy rekordów, które korzystają z zbiorcze pobieranie z wiersza. Jeśli zaimplementowano zbiorcze pobieranie z wiersza, wywołanie `SetFieldNull` powoduje potwierdzenie nie powiodło się. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Jeśli chcesz wyznaczyć pole bieżącego rekordu nie ma wartości, wywołaj specjalnie `SetFieldNull` z *bNull* ustawieniu wartości PRAWDA Oznacz ją jako wartość Null. Jeśli chcesz nadać mu wartość pola został wcześniej oznaczony o wartości Null, wystarczy ustawić dla jej nową wartość. Nie masz do usuwania flagi o wartości Null za pomocą `SetFieldNull`. Aby ustalić, czy pole może mieć wartości Null, należy wywołać `IsFieldNullable`.  
  
> [!CAUTION]
>  Wywołaj tę funkcję elementu członkowskiego, tylko wtedy, gdy wywołujesz [Edytuj](#edit) lub [działają funkcje AddNew](#addnew).  
  
 Użycie wartości NULL dla pierwszego argumentu funkcji zostaną zastosowane tylko do funkcji `outputColumn` pól nie `param` pola. Na przykład wywołanie  
  
 [!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 ustawi tylko `outputColumn` pola na wartość NULL; `param` pola będzie to miało wpływu.  
  
 Do pracy nad `param` pól, należy podać rzeczywistego adresu poszczególnych `param` chcesz pracować, takich jak:  
  
 [!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 Oznacza to, nie można ustawić wszystkie `param` pola na wartość NULL, jak w przypadku `outputColumn` pola.  
  
> [!NOTE]
>  Po ustawieniu parametrów na wartość Null, wywołanie `SetFieldNull` przed zestaw rekordów jest otwarty powoduje potwierdzenie. W takim przypadku wywołania [SetParamNull](#setparamnull).  
  
 `SetFieldNull` jest implementowane za pomocą [dofieldexchange —](#dofieldexchange).  
  
##  <a name="setlockingmode"></a>  CRecordset::SetLockingMode  
 Ustawia tryb blokowania "optymistycznej" Blokowanie (ustawienie domyślne) lub "pesymistycznego" blokowania. Określa, jak rekordy są blokowane aktualizacji.  
  
```  
void SetLockingMode(UINT nMode);
```  
  
### <a name="parameters"></a>Parametry  
 *nMode*  
 Zawiera jedną z następujących wartości z `enum LockMode`:  
  
- `optimistic` Optymistyczne blokowanie blokuje rekordu aktualizowana tylko podczas wywołania `Update`.  
  
- `pessimistic` Pesymistycznego blokowania blokuje rekord zaraz `Edit` nosi nazwę i zachowuje zablokowany do momentu `Update` ukończenia wywołania lub przenieść do nowego rekordu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę funkcję elementu członkowskiego, jeśli chcesz określić, które z dwóch strategii blokowania rekordów aktualizacji korzysta z zestawu rekordów. Domyślnie jest tryb blokowania rekordów `optimistic`. Można to zmienić, aby zachować ostrożność `pessimistic` strategii blokowania. Wywołaj `SetLockingMode` po utworzyć i otworzyć obiekt zestawu rekordów, ale przed wywołaniem `Edit`.  
  
##  <a name="setparamnull"></a>  CRecordset::SetParamNull  
 Flagi parametr jako wartości Null (konkretnie o żadna wartość) lub inną niż Null.  
  
```  
void SetParamNull(
    int nIndex,  
    BOOL bNull = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Liczony od zera indeks parametru.  
  
 *bNull*  
 Jeśli wartość TRUE (wartość domyślna), parametr jest oznaczony jako wartość Null. W przeciwnym razie parametr zostanie oflagowana jako inna niż Null.  
  
### <a name="remarks"></a>Uwagi  
 W odróżnieniu od [SetFieldNull](#setfieldnull), można wywołać `SetParamNull` przed otwarciem zestawu rekordów.  
  
 `SetParamNull` Zazwyczaj jest używana z wstępnie zdefiniowanych zapytań (procedur składowanych).  
  
##  <a name="setrowsetcursorposition"></a>  CRecordset::SetRowsetCursorPosition  
 Przenosi kursor do wiersza w bieżącym zestawie wierszy.  
  
```  
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```  
  
### <a name="parameters"></a>Parametry  
 *wRow*  
 Liczonego od jednego położenie wiersza w bieżącym zestawie wierszy. Wartość ta może wynosić od 1 do rozmiaru zestawu wierszy.  
  
 *wLockType*  
 Wartość wskazująca, jak zablokować wiersz po została odświeżona. Aby uzyskać więcej informacji zobacz uwagi.  
  
### <a name="remarks"></a>Uwagi  
 Implementując wiersz zbiorcze pobieranie rekordów są pobierane przez zestawy wierszy, gdzie pierwszy rekord w pobrano wierszy jest bieżącego rekordu. Aby można było wprowadzić innego rekordu w zestawie wierszy w bieżącym rekordzie, należy wywołać `SetRowsetCursorPosition`. Na przykład można połączyć `SetRowsetCursorPosition` z [getfieldvalue —](#getfieldvalue) funkcję elementu członkowskiego, aby dynamicznie pobrać dane z dowolnego rekordu rekordów.  
  
 Do użycia `SetRowsetCursorPosition`, musi mieć zaimplementowano zbiorcze pobieranie z wiersza, określając `CRecordset::useMultiRowFetch` opcji *dwOptions* parametru w [Otwórz](#open) funkcja elementu członkowskiego.  
  
 `SetRowsetCursorPosition` wywołuje funkcję interfejsu API ODBC `SQLSetPos`. *WLockType* parametr określa stan blokady wiersz po `SQLSetPos` został wykonany. W poniższej tabeli opisano możliwe wartości *wLockType*.  
  
|wLockType|Opis|  
|---------------|-----------------|  
|SQL_LOCK_NO_CHANGE (wartość domyślna)|Sterownik lub źródła danych gwarantuje, że wiersz jest ten sam stan zablokowane lub odblokowany, sprzed `SetRowsetCursorPosition` została wywołana.|  
|SQL_LOCK_EXCLUSIVE|Sterownik lub źródła danych, które wyłącznie blokuje wiersza. Nie wszystkie źródła danych obsługuje ten typ blokady.|  
|SQL_LOCK_UNLOCK|Sterownik lub źródła danych odblokowuje wiersza. Nie wszystkie źródła danych obsługuje ten typ blokady.|  
  
 Aby uzyskać więcej informacji na temat `SQLSetPos`, zobacz dokumentację Windows SDK. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="setrowsetsize"></a>  CRecordset::SetRowsetSize  
 Określa liczbę rekordów, które chcesz pobrać podczas pobierania.  
  
```  
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```  
  
### <a name="parameters"></a>Parametry  
 *dwNewRowsetSize*  
 Liczba wierszy do pobrania podczas pobierania danego.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja wirtualna elementu członkowskiego Określa, ile wierszy chcesz pobrać podczas pobierania jednego, korzystając z zbiorcze pobieranie z wiersza. Aby zaimplementować zbiorcze pobieranie z wiersza, należy ustawić `CRecordset::useMultiRowFetch` opcji *dwOptions* parametru [Otwórz](#open) funkcja elementu członkowskiego.  
  
> [!NOTE]
>  Wywoływanie `SetRowsetSize` bez implementacji zbiorcze pobieranie z wiersza spowoduje niepowodzenie asercji.  
  
 Wywołaj `SetRowsetSize` przed wywołaniem `Open` początkowo ustawić rozmiar wierszy dla zestawu rekordów. Domyślny rozmiar wierszy podczas implementowania zbiorcze pobieranie z wiersza to 25.  
  
> [!NOTE]
>  Należy zachować ostrożność podczas wywoływania `SetRowsetSize`. Jeśli są ręcznie Alokacja magazynu danych (zgodnie z określonym `CRecordset::userAllocMultiRowBuffers` opcji parametru dwOptions w `Open`), należy sprawdzić, czy należy ponownie przydzielić bufory pamięci masowej, po wywołaniu metody `SetRowsetSize`, ale zanim zajdzie wykonać żadnych operacji nawigacji kursora.  
  
 Aby uzyskać bieżące ustawienie rozmiaru wierszy, należy wywołać [GetRowsetSize](#getrowsetsize).  
  
 Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="update"></a>  CRecordset::Update  
 Kończy `AddNew` lub `Edit` operacji, zapisując dane nowe lub zmodyfikowane w źródle danych.  
  
```  
virtual BOOL Update();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli jeden rekord został pomyślnie zaktualizowany; w przeciwnym razie 0, jeśli żadna kolumna nie uległy zmianie. Jeśli żadne rekordy nie zostały zaktualizowane, lub jeśli więcej niż jeden rekord został zaktualizowany, jest zgłaszany wyjątek. Jest również wyjątek dla innych błędów w źródle danych.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę funkcję elementu członkowskiego po wywołaniu [działają funkcje AddNew](#addnew) lub [Edytuj](#edit) funkcja elementu członkowskiego. To wywołanie jest wymagane do ukończenia `AddNew` lub `Edit` operacji.  
  
> [!NOTE]
>  Jeśli zaimplementowano zbiorcze pobieranie z wiersza, nie można wywołać `Update`. Spowoduje to potwierdzenie nie powiodło się. Chociaż klasa `CRecordset` nie zapewnia mechanizm aktualizacji zbiorczej wiersze danych, można napisać własne funkcje za pomocą funkcji interfejsu API ODBC `SQLSetPos`. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Zarówno `AddNew` i `Edit` przygotowanie buforu edycji, w której umieszczony jest dodane lub zmodyfikowane dane do zapisania na źródle danych. `Update` zapisuje dane. Tylko w tych polach wykrycia zgodnie zmieniona lub oznaczona są aktualizowane.  
  
 Jeśli źródło danych obsługuje transakcje, można wprowadzić `Update` wywołania (i odpowiadającymi mu dostawcami `AddNew` lub `Edit` wywołania) wchodzi w skład transakcji. Aby uzyskać więcej informacji na temat transakcji, zobacz artykuł [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).  
  
> [!CAUTION]
>  Jeśli wywołasz `Update` bez uprzedniego wywołania `AddNew` lub `Edit`, `Update` zgłasza `CDBException`. Jeśli wywołasz `AddNew` lub `Edit`, należy wywołać `Update` przed wywołaniem `Move` operacji lub przed zamknięciem zestawu rekordów lub połączenia ze źródłem danych. W przeciwnym razie zmiany zostaną utracone bez powiadomienia.  
  
 Aby uzyskać szczegółowe informacje na temat obsługi `Update` błędów, zobacz artykuł [zestaw rekordów: jak zestawy rekordów uaktualniają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
### <a name="example"></a>Przykład  
 Zapoznaj się z artykułem [transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CObject](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CDatabase](../../mfc/reference/cdatabase-class.md)   
 [Klasa CRecordView](../../mfc/reference/crecordview-class.md)
