---
title: Klasa CDaoRecordset
ms.date: 08/27/2018
f1_keywords:
- CDaoRecordset
- AFXDAO/CDaoRecordset
- AFXDAO/CDaoRecordset::CDaoRecordset
- AFXDAO/CDaoRecordset::AddNew
- AFXDAO/CDaoRecordset::CanAppend
- AFXDAO/CDaoRecordset::CanBookmark
- AFXDAO/CDaoRecordset::CancelUpdate
- AFXDAO/CDaoRecordset::CanRestart
- AFXDAO/CDaoRecordset::CanScroll
- AFXDAO/CDaoRecordset::CanTransact
- AFXDAO/CDaoRecordset::CanUpdate
- AFXDAO/CDaoRecordset::Close
- AFXDAO/CDaoRecordset::Delete
- AFXDAO/CDaoRecordset::DoFieldExchange
- AFXDAO/CDaoRecordset::Edit
- AFXDAO/CDaoRecordset::FillCache
- AFXDAO/CDaoRecordset::Find
- AFXDAO/CDaoRecordset::FindFirst
- AFXDAO/CDaoRecordset::FindLast
- AFXDAO/CDaoRecordset::FindNext
- AFXDAO/CDaoRecordset::FindPrev
- AFXDAO/CDaoRecordset::GetAbsolutePosition
- AFXDAO/CDaoRecordset::GetBookmark
- AFXDAO/CDaoRecordset::GetCacheSize
- AFXDAO/CDaoRecordset::GetCacheStart
- AFXDAO/CDaoRecordset::GetCurrentIndex
- AFXDAO/CDaoRecordset::GetDateCreated
- AFXDAO/CDaoRecordset::GetDateLastUpdated
- AFXDAO/CDaoRecordset::GetDefaultDBName
- AFXDAO/CDaoRecordset::GetDefaultSQL
- AFXDAO/CDaoRecordset::GetEditMode
- AFXDAO/CDaoRecordset::GetFieldCount
- AFXDAO/CDaoRecordset::GetFieldInfo
- AFXDAO/CDaoRecordset::GetFieldValue
- AFXDAO/CDaoRecordset::GetIndexCount
- AFXDAO/CDaoRecordset::GetIndexInfo
- AFXDAO/CDaoRecordset::GetLastModifiedBookmark
- AFXDAO/CDaoRecordset::GetLockingMode
- AFXDAO/CDaoRecordset::GetName
- AFXDAO/CDaoRecordset::GetParamValue
- AFXDAO/CDaoRecordset::GetPercentPosition
- AFXDAO/CDaoRecordset::GetRecordCount
- AFXDAO/CDaoRecordset::GetSQL
- AFXDAO/CDaoRecordset::GetType
- AFXDAO/CDaoRecordset::GetValidationRule
- AFXDAO/CDaoRecordset::GetValidationText
- AFXDAO/CDaoRecordset::IsBOF
- AFXDAO/CDaoRecordset::IsDeleted
- AFXDAO/CDaoRecordset::IsEOF
- AFXDAO/CDaoRecordset::IsFieldDirty
- AFXDAO/CDaoRecordset::IsFieldNull
- AFXDAO/CDaoRecordset::IsFieldNullable
- AFXDAO/CDaoRecordset::IsOpen
- AFXDAO/CDaoRecordset::Move
- AFXDAO/CDaoRecordset::MoveFirst
- AFXDAO/CDaoRecordset::MoveLast
- AFXDAO/CDaoRecordset::MoveNext
- AFXDAO/CDaoRecordset::MovePrev
- AFXDAO/CDaoRecordset::Open
- AFXDAO/CDaoRecordset::Requery
- AFXDAO/CDaoRecordset::Seek
- AFXDAO/CDaoRecordset::SetAbsolutePosition
- AFXDAO/CDaoRecordset::SetBookmark
- AFXDAO/CDaoRecordset::SetCacheSize
- AFXDAO/CDaoRecordset::SetCacheStart
- AFXDAO/CDaoRecordset::SetCurrentIndex
- AFXDAO/CDaoRecordset::SetFieldDirty
- AFXDAO/CDaoRecordset::SetFieldNull
- AFXDAO/CDaoRecordset::SetFieldValue
- AFXDAO/CDaoRecordset::SetFieldValueNull
- AFXDAO/CDaoRecordset::SetLockingMode
- AFXDAO/CDaoRecordset::SetParamValue
- AFXDAO/CDaoRecordset::SetParamValueNull
- AFXDAO/CDaoRecordset::SetPercentPosition
- AFXDAO/CDaoRecordset::Update
- AFXDAO/CDaoRecordset::m_bCheckCacheForDirtyFields
- AFXDAO/CDaoRecordset::m_nFields
- AFXDAO/CDaoRecordset::m_nParams
- AFXDAO/CDaoRecordset::m_pDAORecordset
- AFXDAO/CDaoRecordset::m_pDatabase
- AFXDAO/CDaoRecordset::m_strFilter
- AFXDAO/CDaoRecordset::m_strSort
helpviewer_keywords:
- CDaoRecordset [MFC], CDaoRecordset
- CDaoRecordset [MFC], AddNew
- CDaoRecordset [MFC], CanAppend
- CDaoRecordset [MFC], CanBookmark
- CDaoRecordset [MFC], CancelUpdate
- CDaoRecordset [MFC], CanRestart
- CDaoRecordset [MFC], CanScroll
- CDaoRecordset [MFC], CanTransact
- CDaoRecordset [MFC], CanUpdate
- CDaoRecordset [MFC], Close
- CDaoRecordset [MFC], Delete
- CDaoRecordset [MFC], DoFieldExchange
- CDaoRecordset [MFC], Edit
- CDaoRecordset [MFC], FillCache
- CDaoRecordset [MFC], Find
- CDaoRecordset [MFC], FindFirst
- CDaoRecordset [MFC], FindLast
- CDaoRecordset [MFC], FindNext
- CDaoRecordset [MFC], FindPrev
- CDaoRecordset [MFC], GetAbsolutePosition
- CDaoRecordset [MFC], GetBookmark
- CDaoRecordset [MFC], GetCacheSize
- CDaoRecordset [MFC], GetCacheStart
- CDaoRecordset [MFC], GetCurrentIndex
- CDaoRecordset [MFC], GetDateCreated
- CDaoRecordset [MFC], GetDateLastUpdated
- CDaoRecordset [MFC], GetDefaultDBName
- CDaoRecordset [MFC], GetDefaultSQL
- CDaoRecordset [MFC], GetEditMode
- CDaoRecordset [MFC], GetFieldCount
- CDaoRecordset [MFC], GetFieldInfo
- CDaoRecordset [MFC], GetFieldValue
- CDaoRecordset [MFC], GetIndexCount
- CDaoRecordset [MFC], GetIndexInfo
- CDaoRecordset [MFC], GetLastModifiedBookmark
- CDaoRecordset [MFC], GetLockingMode
- CDaoRecordset [MFC], GetName
- CDaoRecordset [MFC], GetParamValue
- CDaoRecordset [MFC], GetPercentPosition
- CDaoRecordset [MFC], GetRecordCount
- CDaoRecordset [MFC], GetSQL
- CDaoRecordset [MFC], GetType
- CDaoRecordset [MFC], GetValidationRule
- CDaoRecordset [MFC], GetValidationText
- CDaoRecordset [MFC], IsBOF
- CDaoRecordset [MFC], IsDeleted
- CDaoRecordset [MFC], IsEOF
- CDaoRecordset [MFC], IsFieldDirty
- CDaoRecordset [MFC], IsFieldNull
- CDaoRecordset [MFC], IsFieldNullable
- CDaoRecordset [MFC], IsOpen
- CDaoRecordset [MFC], Move
- CDaoRecordset [MFC], MoveFirst
- CDaoRecordset [MFC], MoveLast
- CDaoRecordset [MFC], MoveNext
- CDaoRecordset [MFC], MovePrev
- CDaoRecordset [MFC], Open
- CDaoRecordset [MFC], Requery
- CDaoRecordset [MFC], Seek
- CDaoRecordset [MFC], SetAbsolutePosition
- CDaoRecordset [MFC], SetBookmark
- CDaoRecordset [MFC], SetCacheSize
- CDaoRecordset [MFC], SetCacheStart
- CDaoRecordset [MFC], SetCurrentIndex
- CDaoRecordset [MFC], SetFieldDirty
- CDaoRecordset [MFC], SetFieldNull
- CDaoRecordset [MFC], SetFieldValue
- CDaoRecordset [MFC], SetFieldValueNull
- CDaoRecordset [MFC], SetLockingMode
- CDaoRecordset [MFC], SetParamValue
- CDaoRecordset [MFC], SetParamValueNull
- CDaoRecordset [MFC], SetPercentPosition
- CDaoRecordset [MFC], Update
- CDaoRecordset [MFC], m_bCheckCacheForDirtyFields
- CDaoRecordset [MFC], m_nFields
- CDaoRecordset [MFC], m_nParams
- CDaoRecordset [MFC], m_pDAORecordset
- CDaoRecordset [MFC], m_pDatabase
- CDaoRecordset [MFC], m_strFilter
- CDaoRecordset [MFC], m_strSort
ms.assetid: 2322067f-1027-4662-a5d7-aa2fc7488630
ms.openlocfilehash: 6a1475d1b0bc083cfd180ea5a211e752c973e2f8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754681"
---
# <a name="cdaorecordset-class"></a>Klasa CDaoRecordset

Reprezentuje zestaw rekordów wybranych ze źródła danych.

## <a name="syntax"></a>Składnia

```
class CDaoRecordset : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoRecordset::CDaoRecordset](#cdaorecordset)|Konstruuje `CDaoRecordset` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoRecordset::AddNew](#addnew)|Przygotowuje się do dodania nowego rekordu. Wywołanie [update,](#update) aby zakończyć dodawanie.|
|[CDaoRecordset::CanAppend](#canappend)|Zwraca wartość niezerową, jeśli nowe rekordy mogą być dodawane do pliku recordset za pomocą funkcji [AddNew](#addnew) element członkowski.|
|[CDaoRecordset::CanBookmark](#canbookmark)|Zwraca wartość niezerową, jeśli zestaw rekordów obsługuje zakładki.|
|[CDaoRecordset::Anulujupdate](#cancelupdate)|Anuluje wszelkie oczekujące aktualizacje z powodu operacji [Edytuj](#edit) lub [DodajNew.](#addnew)|
|[Zestaw CDaoRecordset::CanRestart](#canrestart)|Zwraca wartość niezerowa, jeśli można wywołać ponowne uruchomienie [kwerendy](#requery) wzemie.|
|[CDaoRecordset::CanScroll](#canscroll)|Zwraca wartość niezerowa, jeśli można przewijać rekordy.|
|[CDaoRecordset::CanTransact](#cantransact)|Zwraca wartość niezerową, jeśli źródło danych obsługuje transakcje.|
|[CDaoRecordset::CanUpdate](#canupdate)|Zwraca wartość niezerową, jeśli można zaktualizować plan records (można dodawać, aktualizować lub usuwać rekordy).|
|[CDaoRecordset::Zamknij](#close)|Zamyka rekord.|
|[CDaoRecordset::Delete](#delete)|Usuwa bieżący rekord z rekordu. Po usunięciu należy jawnie przewinąć do innego rekordu.|
|[CDaoRecordset::DoFieldExchange](#dofieldexchange)|Wywoływana do wymiany danych (w obu kierunkach) między członkami pola danych zbioru rekordów a odpowiednim rekordem w źródle danych. Implementuje wymianę pól rekordów DAO (DFX).|
|[Zestaw rekordów CD::Edytuj](#edit)|Przygotowuje się do zmian w bieżącym rekordzie. Wywołanie, `Update` aby zakończyć edycję.|
|[CDaoRecordset::FillCache](#fillcache)|Wypełnia całość lub część lokalnej pamięci podręcznej dla obiektu zestaw rekordów, który zawiera dane ze źródła danych ODBC.|
|[CDaoRecordset::Znajdź](#find)|Lokalizuje pierwszą, następną, poprzednią lub ostatnią lokalizację określonego ciągu w zestawie rekordów typu dynaset, która spełnia określone kryteria i sprawia, że rekord ten jest bieżącym rekordem.|
|[CDaoRecordset::ZnajdźPowierasz](#findfirst)|Lokalizuje pierwszy rekord w zestawie rekordów typu dynaset lub migawki, który spełnia określone kryteria i sprawia, że rekord ten jest bieżącym rekordem.|
|[CDaoRecordset::FindLast](#findlast)|Lokalizuje ostatni rekord w zestawie rekordów typu dynaset lub migawki, który spełnia określone kryteria i sprawia, że rekord ten jest bieżącym rekordem.|
|[Zestaw CDaoRecordset::FindNext](#findnext)|Lokalizuje następny rekord w zestawie rekordów typu dynaset lub migawki, który spełnia określone kryteria i sprawia, że rekord ten jest bieżącym rekordem.|
|[Zestaw CDaoRecordset::FindPrev](#findprev)|Lokalizuje poprzedni rekord w zestawie rekordów typu dynaset lub migawki, który spełnia określone kryteria i sprawia, że rekord ten jest bieżącym rekordem.|
|[CDaoRecordset::GetAbsolutePosition](#getabsoluteposition)|Zwraca numer rekordu bieżącego rekordu obiektu zestawu rekordów.|
|[CDaoRecordset::GetBookmark](#getbookmark)|Zwraca wartość reprezentującą zakładkę w rekordzie.|
|[CDaoRecordset::GetCachESize](#getcachesize)|Zwraca wartość określającą liczbę rekordów w zestawie rekordów typu dynaset zawierającą dane, które mają być buforowane lokalnie ze źródła danych ODBC.|
|[Zestaw CDaoRecordset::GetCacheStart](#getcachestart)|Zwraca wartość określającą zakładkę pierwszego rekordu w zamówiórie rekordów, który ma być buforowany.|
|[CDaoRecordset::GetCurrentIndex](#getcurrentindex)|Zwraca `CString` nazwę indeksu ostatnio używanego w indeksowanym typie `CDaoRecordset`tabeli .|
|[CDaoRecordset::GetDateTworzone](#getdatecreated)|Zwraca datę i godzinę utworzenia `CDaoRecordset` tabeli bazowej leżącej u podstaw obiektu|
|[CDaoRecordset::GetDateLastUpdated](#getdatelastupdated)|Zwraca datę i godzinę ostatniej zmiany wprowadzonej do projektu tabeli bazowej leżącej `CDaoRecordset` u podstaw obiektu.|
|[CDaoRecordset::GetDefaultDBName](#getdefaultdbname)|Zwraca nazwę domyślnego źródła danych.|
|[CDaoRecordset::GetDefaultSQL](#getdefaultsql)|Wywoływany, aby uzyskać domyślny ciąg SQL do wykonania.|
|[CDaoRecordset::GetEditMode](#geteditmode)|Zwraca wartość wskazującą stan edycji bieżącego rekordu.|
|[CDaoRecordset::GetFieldCount](#getfieldcount)|Zwraca wartość reprezentującą liczbę pól w zamówiórze.|
|[CDaoRecordset::GetFieldInfo](#getfieldinfo)|Zwraca określone rodzaje informacji o polach w zakułach rekordów.|
|[Zestaw CDaoRecordset::GetFieldValue](#getfieldvalue)|Zwraca wartość pola w liście rekordów.|
|[CDaoRecordset::GetIndexCount](#getindexcount)|Pobiera liczbę indeksów w tabeli leżącej u podstaw zestawu rekordów.|
|[CDaoRecordset::GetIndexInfo](#getindexinfo)|Zwraca różne rodzaje informacji o indeksie.|
|[CDaoRecordset::GetLastModifiedBookmark](#getlastmodifiedbookmark)|Służy do określania ostatnio dodanego lub zaktualizowanego rekordu.|
|[CDaoRecordset::GetLockingMode](#getlockingmode)|Zwraca wartość, która wskazuje typ blokowania, który obowiązuje podczas edycji.|
|[Zestaw CDaoRecordset::GetName](#getname)|Zwraca `CString` nazwę zawierającą rekord.|
|[Zestaw CDaoRecordset::GetParamValue](#getparamvalue)|Pobiera bieżącą wartość określonego parametru przechowywanego w podstawowym obiekcie DAOParameter.|
|[Zestaw CDaoRecordset::GetPercentPosition](#getpercentposition)|Zwraca pozycję bieżącego rekordu jako procent całkowitej liczby rekordów.|
|[CDaoRecordset::GetRecordCount](#getrecordcount)|Zwraca liczbę rekordów dostępnych w obiekcie zestawu rekordów.|
|[Zestaw CDaoRecordset::GetSQL](#getsql)|Pobiera ciąg SQL używany do wybierania rekordów dla pliku recordset.|
|[Zestaw CDaoRecordset::GetType](#gettype)|Wywoływana w celu określenia typu zestawu rekordów: typu tabeli, typu dynaset lub typu migawki.|
|[CDaoRecordset::GetValidationRule](#getvalidationrule)|Zwraca `CString` zawierającą wartość, która sprawdza poprawność danych w miarę ich wprowadzania w polu.|
|[CDaoRecordset::GetValidationText](#getvalidationtext)|Pobiera tekst, który jest wyświetlany, gdy reguła sprawdzania poprawności nie jest spełniony.|
|[CDaoRecordset::IsBOF](#isbof)|Zwraca wartość niezerowa, jeśli grupa rekordów została mieszczona przed pierwszym rekordem. Nie ma bieżącego rekordu.|
|[CDaoRecordset::JestDeletowany](#isdeleted)|Zwraca wartość wartość niezerową, jeśli plan rekordów jest umieszczony na usuniętym rekordzie.|
|[CDaoRecordset::IsEOF](#iseof)|Zwraca wartość niezerowa, jeśli po ostatnim rekordzie został umieszczony po ostatnim rekordzie. Nie ma bieżącego rekordu.|
|[CDaoRecordset::IsFieldDirty](#isfielddirty)|Zwraca wartość wartość niezerowa, jeśli określone pole w bieżącym rekordzie zostało zmienione.|
|[CDaoRecordset::IsFieldNull](#isfieldnull)|Zwraca wartość niezerową, jeśli określone pole w bieżącym rekordzie to Null (bez wartości).|
|[CDaoRecordset::IsFieldNullable](#isfieldnullable)|Zwraca wartość wartość niezerową, jeśli określone pole w bieżącym rekordzie można ustawić na Null (bez wartości).|
|[CDaoRecordset::IsOpen](#isopen)|Zwraca wartość niezerowa, jeśli [open](#open) został wywołany wcześniej.|
|[Zestaw CDaoRecordset::Przenieś](#move)|Umieszcza zestawu rekordów do określonej liczby rekordów z bieżącego rekordu w obu kierunkach.|
|[Zestaw CDaoRecordset::MoveFirst](#movefirst)|Umieszcza bieżący rekord w pierwszym rekordzie w rekordzie.|
|[Zestaw CDaoRecordset::MoveLast](#movelast)|Umieszcza bieżący rekord w ostatnim rekordzie w rekordzie.|
|[Zestaw CDaoRecordset::MoveNext](#movenext)|Umieszcza bieżący rekord w następnym rekordzie w ach .|
|[Zestaw CDaoRecordset::MovePrev](#moveprev)|Umieszcza bieżący rekord w poprzednim rekordzie w zamówiórze.|
|[CDaoRecordset::Otwórz](#open)|Tworzy nowy zestaw rekordów z tabeli, dynaset lub migawki.|
|[CDaoRecordset::Kwerenda requery](#requery)|Ponownie uruchamia kwerendę wstawki rekordów, aby odświeżyć wybrane rekordy.|
|[CDaoRecordset::Szukaj](#seek)|Lokalizuje rekord w obiekcie indeksowanego typu recordset, który spełnia określone kryteria dla bieżącego indeksu i sprawia, że rekord ten jest bieżącym rekordem.|
|[CDaoRecordset::SetAbsolutePosition](#setabsoluteposition)|Ustawia numer rekordu bieżącego rekordu obiektu zestawu rekordów.|
|[CDaoRecordset::SetBookmark](#setbookmark)|Umieszcza go w rekordzie zawierającym określoną zakładkę.|
|[CDaoRecordset::SetCacheSize](#setcachesize)|Ustawia wartość określającą liczbę rekordów w zestawie rekordów typu dynaset zawierającą dane, które mają być buforowane lokalnie ze źródła danych ODBC.|
|[Zestaw CDaoRecordset::SetCacheStart](#setcachestart)|Ustawia wartość określającą zakładkę pierwszego rekordu w secie rekordów, która ma być buforowana.|
|[CDaoRecordset::SetCurrentIndex](#setcurrentindex)|Wywołany wobec ustawić an indeks u pewien tabela- typ zestawie rekordów.|
|[CDaoRecordset::SetFieldDirty](#setfielddirty)|Oznacza określone pole w bieżącym rekordzie jako zmienione.|
|[CDaoRecordset::SetFieldNull](#setfieldnull)|Ustawia wartość określonego pola w bieżącym rekordzie na Null (bez wartości).|
|[Zestaw CDaoRecordset::SetFieldValue](#setfieldvalue)|Ustawia wartość pola w liście rekordów.|
|[CDaoRecordset::SetFieldValueNull](#setfieldvaluenull)|Ustawia wartość pola w liście rekordów na Wartość Null. (nie mając żadnej wartości).|
|[CDaoRecordset::SetLockingMode](#setlockingmode)|Ustawia wartość, która wskazuje typ blokowania, który ma być wprowadzony w życie podczas edycji.|
|[Zestaw CDaoRecordset::SetParamValue](#setparamvalue)|Ustawia bieżącą wartość określonego parametru przechowywanego w leżącym na nim obiekcie DAOParameter|
|[CDaoRecordset::SetParamValueNull](#setparamvaluenull)|Ustawia bieżącą wartość określonego parametru na Null (bez wartości).|
|[CDaoRecordset::SetPercentPosition](#setpercentposition)|Ustawia położenie bieżącego rekordu na lokalizację odpowiadającą procentowi całkowitej liczby rekordów w zamówiórie.|
|[CDaoRecordset::Aktualizacja](#update)|Kończy `AddNew` operację, `Edit` zapisując nowe lub edytowane dane w źródle danych.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDaoRecordset::m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)|Zawiera flagę wskazującą, czy pola są automatycznie oznaczane jako zmienione.|
|[CDaoRecordset::m_nFields](#m_nfields)|Zawiera liczbę elementów członkowskich danych pól w klasie zestawu rekordów oraz liczbę kolumn wybranych przez zestaw rekordów ze źródła danych.|
|[CDaoRecordset::m_nParams](#m_nparams)|Zawiera liczbę elementów członkowskich danych parametrów w klasie zestawu rekordów — liczba parametrów przekazanych wraz z kwerendą zestawu rekordów|
|[CDaoRecordset::m_pDAORecordset](#m_pdaorecordset)|Wskaźnik do interfejsu DAO leżącego u podstaw obiektu aktujdy.|
|[CDaoRecordset::m_pDatabase](#m_pdatabase)|Źródłowa baza danych dla tego zestawu wyników. Zawiera wskaźnik do obiektu [CDaoDatabase.](../../mfc/reference/cdaodatabase-class.md)|
|[CDaoRecordset::m_strFilter](#m_strfilter)|Zawiera ciąg używany do konstruowania instrukcji SQL **WHERE.**|
|[CDaoRecordset::m_strSort](#m_strsort)|Zawiera ciąg używany do konstruowania instrukcji **SQL ORDER BY.**|

## <a name="remarks"></a>Uwagi

Znane jako "zestawy `CDaoRecordset` rekordów", obiekty są dostępne w następujących trzech formach:

- Zestawy rekordów typu tabeli reprezentują tabelę bazową, której można używać do sprawdzania, dodawania, zmieniania lub usuwania rekordów z pojedynczej tabeli bazy danych.

- Zestawy rekordów typu Dynaset są wynikiem kwerendy, która może mieć rekordy, które mogą być aktualizowane. Te zestawy rekordów to zestaw rekordów, których można używać do sprawdzania, dodawania, zmieniania lub usuwania rekordów z podstawowej tabeli lub tabel bazy danych. Zestawy rekordów typu Dynaset mogą zawierać pola z jednej lub kilku tabel w bazie danych.

- Zestawy rekordów typu migawki są statyczną kopią zestawu rekordów, których można użyć do znajdowania danych lub generowania raportów. Te zestawy rekordów mogą zawierać pola z jednej lub więcej tabel w bazie danych, ale nie można ich zaktualizować.

Każda forma zestawu rekordów reprezentuje zestaw rekordów ustalonych w momencie otwarcia zestawu rekordów. Podczas przewijania do rekordu w zestawie rekordów typu tabeli lub zestawie rekordów typu dynaset odzwierciedla on zmiany wprowadzone w rekordzie po otwarciu zestawu rekordów przez innych użytkowników lub przez inne zestawy rekordów w aplikacji. (Nie można zaktualizować a snapshot-type recordset). Można użyć `CDaoRecordset` bezpośrednio lub wyprowadzić klasę pliku recordset specyficzne dla aplikacji z programu `CDaoRecordset`. Następnie można wykonywać czynności takie jak:

- Przewiń rekordy.

- Ustaw indeks i szybko wyszukuj rekordy przy użyciu [funkcji Szukaj](#seek) (tylko zestawy rekordów typu tabeli).

- Znajdź rekordy na podstawie porównania ciągów: "<", "\<=", "=", ">=" lub ">" (zestawy rekordów typu dynaset i migawki).

- Zaktualizuj rekordy i określ tryb blokowania (z wyjątkiem zestawów rekordów typu migawki).

- Filtruj zestaw rekordów, aby ograniczyć rekordy, które wybiera spośród rekordów dostępnych w źródle danych.

- Sortowanie pliku recordset.

- Parametryzacja pliku recordset, aby dostosować jego wybór z informacjami nie znanymi do czasu wykonywania.

Klasa `CDaoRecordset` dostarcza interfejs podobny do `CRecordset`tego klasy . Główną różnicą `CDaoRecordset` jest to, że klasa uzyskuje dostęp do danych za pośrednictwem obiektu dostępu do danych (DAO) na podstawie OLE. Klasa `CRecordset` uzyskuje dostęp do dbms za pośrednictwem open database connectivity (ODBC) i sterownik ODBC dla tego dbms.

> [!NOTE]
> Klasy bazy danych DAO różnią się od klas bazy danych MFC na podstawie łączności otwartej bazy danych (ODBC). Wszystkie nazwy klas bazy danych DAO mają prefiks "CDao". Nadal można uzyskać dostęp do źródeł danych ODBC z klasami DAO; klasy DAO zazwyczaj oferują doskonałe możliwości, ponieważ są one specyficzne dla aparatu bazy danych Microsoft Jet.

Można użyć `CDaoRecordset` bezpośrednio lub wyprowadzić klasę `CDaoRecordset`z programu . Aby użyć klasy pliku recordset w obu przypadkach, otwórz bazę danych i skonstruuj obiekt pliku recordset, przekazując konstruktorowi wskaźnik do `CDaoDatabase` obiektu. Można również skonstruować `CDaoRecordset` obiekt i pozwolić `CDaoDatabase` MFC utworzyć obiekt tymczasowy dla Ciebie. Następnie wywołaj funkcję [elementu](#open) członkowskiego Open zestawu rekordów, określając, czy obiekt jest zestawem rekordów typu tabeli, zestawem rekordów typu dynaset, czy zestawem rekordów typu migawka. Wywołanie `Open` wybiera dane z bazy danych i pobiera pierwszy rekord.

Użyj funkcji elementów członkowskich obiektu i elementów członkowskich danych, aby przewijać rekordy i działać na nich. Dostępne operacje zależą od tego, czy obiekt jest zestawem rekordów typu tabeli, zestawem rekordów typu dynaset, czy zestawem rekordów typu migawka i czy jest on można aktualizować, czy tylko do odczytu — zależy to od możliwości źródła danych bazy danych lub open database connectivity (ODBC). Aby odświeżyć rekordy, które mogły `Open` zostać zmienione lub dodane od czasu wywołania, należy wywołać funkcję elementu członkowskiego [requery](#requery) obiektu. Wywołaj funkcję `Close` elementu członkowskiego obiektu i zniszcz obiekt po zakończeniu.

`CDaoRecordset`używa wymiany pól rekordów DAO (DFX) do obsługi odczytu i aktualizowania pól `CDaoRecordset` `CDaoRecordset`rekordów za pośrednictwem bezpiecznych dla typów członków C++ klasy lub klasy pochodnej. Dynamiczne powiązanie kolumn w bazie danych można również zaimplementować bez użycia mechanizmu DFX przy użyciu [funkcji GetFieldValue](#getfieldvalue) i [SetFieldValue](#setfieldvalue).

Aby uzyskać powiązane informacje, zobacz temat "Obiekt tablicy rekordów" w Pomocy DAO.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CDaoRecordset`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="cdaorecordsetaddnew"></a><a name="addnew"></a>CDaoRecordset::AddNew

Wywołanie tej funkcji elementu członkowskiego, aby dodać nowy rekord do zestawu rekordów typu tabeli lub dynaset.

```
virtual void AddNew();
```

### <a name="remarks"></a>Uwagi

Pola rekordu są początkowo null. (W terminologii bazy danych Null oznacza "bez wartości" i nie jest taka sama jak NULL w języku C++.) Aby wykonać operację, należy [wywołać](#update) update funkcji elementu członkowskiego. `Update`zapisuje zmiany w źródle danych.

> [!CAUTION]
> Jeśli edytujesz rekord, a następnie `Update`przewiniesz do innego rekordu bez wywoływania, zmiany zostaną utracone bez ostrzeżenia.

Jeśli rekord zostanie dodany do zestawu rekordów typu dynaset, wywołując [AddNew,](#addnew)rekord jest widoczny w zestawie rekordów i `CDaoRecordset` uwzględniany w tabeli źródłowej, gdzie staje się widoczny dla wszystkich nowych obiektów.

Położenie nowego rekordu zależy od typu rekordu:

- W zestawie rekordów typu dynaset, w którym nowy rekord jest wstawiany, nie jest gwarantowana. To zachowanie zmieniło się w programie Microsoft Jet 3.0 ze względu na wydajność i współbieżność. Jeśli twoim celem jest uczynienie nowo dodanego rekordu bieżącym rekordem, pobierz zakładkę ostatniego zmodyfikowanego rekordu i przejdź do tej zakładki:

[!code-cpp[NVC_MFCDatabase#1](../../mfc/codesnippet/cpp/cdaorecordset-class_1.cpp)]

- W tablicy rekordów typu, dla których określono indeks, rekordy są zwracane w ich właściwym miejscu w kolejności sortowania. Jeśli nie określono indeksu, nowe rekordy są zwracane na końcu pliku recordset.

Rekord, który był aktualny `AddNew` przed użyciem, pozostaje aktualny. Jeśli chcesz, aby nowy rekord był bieżący, a zestaw rekordów obsługuje zakładki, wywołaj [SetBookmark](#setbookmark) do zakładki identyfikowanej przez ustawienie właściwości LastModified leżącego u podstaw obiektu zestawu rekordów DAO. Jest to przydatne do określania wartości pól licznika (automatycznego przyrostu) w dodanym rekordzie. Aby uzyskać więcej informacji, zobacz [GetLastModifiedBookmark](#getlastmodifiedbookmark).

Jeśli baza danych obsługuje transakcje, `AddNew` można dokonać połączenia część transakcji. Aby uzyskać więcej informacji o transakcjach, zobacz klasę [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md). Należy zauważyć, że należy wywołać [CDaoWorkspace::BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans) przed wywołaniem `AddNew`.

Niezgodne z prawem `AddNew` jest wywołanie pliku recordset, którego funkcja [open](#open) member nie została wywołana. A `CDaoException` jest generowany, `AddNew` jeśli wywołasz dla pliku recordset, który nie może być dołączona. Można określić, czy plik rekordów można aktualizować, wywołując program [CanAppend](#canappend).

Znaki ramowe zmieniły elementy członkowskie danych pól, aby upewnić się, że zostaną one zapisane w rekordzie w źródle danych przez mechanizm wymiany pól rekordu DAO (DFX). Zmiana wartości pola zazwyczaj ustawia pole zabrudzone automatycznie, więc rzadko trzeba wywołać [SetFieldDirty](#setfielddirty) samodzielnie, ale czasami warto upewnić się, że kolumny będą jawnie aktualizowane lub wstawiane niezależnie od wartości, która znajduje się w polu elementu członkowskiego danych. Mechanizm DFX wykorzystuje również pseudo **null**. Aby uzyskać więcej informacji, zobacz [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Jeśli mechanizm podwójnego buforowania nie jest używany, zmiana wartości pola nie powoduje automatycznego ustawiania pola jako zabrudzone. W takim przypadku konieczne będzie jawne ustawienie pola zabrudzone. Flaga zawarta w [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) steruje automatycznym sprawdzaniem pola.

> [!NOTE]
> Jeśli rekordy są buforowane podwójnie (oznacza to, że `CancelUpdate` włączone jest automatyczne sprawdzanie pola), wywołanie przywróci zmienne członkowskie do wartości, które miały przed `AddNew` lub `Edit` został wywołany.

Aby uzyskać powiązane informacje, zobacz tematy "AddNew Method", "CancelUpdate Method", "LastModified Property" i "EditMode Property" w Pomocy DAO.

## <a name="cdaorecordsetcanappend"></a><a name="canappend"></a>CDaoRecordset::CanAppend

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy wcześniej otwarty plik recordset umożliwia dodawanie nowych rekordów przez wywołanie [AddNew](#addnew) funkcji elementu członkowskiego.

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli recordset umożliwia dodawanie nowych rekordów; w przeciwnym razie 0. `CanAppend`powróci 0, jeśli otworzysz plik recordset jako tylko do odczytu.

### <a name="remarks"></a>Uwagi

Aby uzyskać powiązane informacje, zobacz temat "Dołącz metodę" w Pomocy DAO.

## <a name="cdaorecordsetcanbookmark"></a><a name="canbookmark"></a>CDaoRecordset::CanBookmark

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy wcześniej otwarty plik recordset umożliwia indywidualne oznaczanie rekordów przy użyciu zakładek.

```
BOOL CanBookmark();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli zestaw rekordów obsługuje zakładki, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli używasz zestawy rekordów oparte wyłącznie na tabelach aparatu bazy danych Microsoft Jet, zakładki mogą być używane z wyjątkiem rekordów typu migawka oflagowanych jako przewijane zestawy rekordów tylko do przodu. Inne produkty bazy danych (zewnętrzne źródła danych ODBC) mogą nie obsługiwać zakładek.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość do różnania zakładek" w Pomocy DAO.

## <a name="cdaorecordsetcancelupdate"></a><a name="cancelupdate"></a>CDaoRecordset::Anulujupdate

Funkcja `CancelUpdate` elementu członkowskiego anuluje wszelkie oczekujące aktualizacje z powodu operacji [Edytuj](#edit) lub [Dodaj Nie chcesz.](#addnew)

```
virtual void CancelUpdate();
```

### <a name="remarks"></a>Uwagi

Na przykład jeśli aplikacja `Edit` wywołuje `AddNew` funkcję lub element członkowski i nie `Edit` nazywa `AddNew` [update](#update), `CancelUpdate` anuluje wszelkie zmiany wprowadzone po lub został wywołany.

> [!NOTE]
> Jeśli rekordy są buforowane podwójnie (oznacza to, że `CancelUpdate` włączone jest automatyczne sprawdzanie pola), wywołanie przywróci zmienne członkowskie do wartości, które miały przed `AddNew` lub `Edit` został wywołany.

Jeśli nie `Edit` ma `AddNew` żadnych `CancelUpdate` lub operacji oczekujących, powoduje MFC zgłosić wyjątek. Wywołanie Funkcji elementu członkowskiego [GetEditMode,](#geteditmode) aby ustalić, czy istnieje oczekująca operacja, która może zostać anulowana.

Aby uzyskać powiązane informacje, zobacz temat "CancelUpdate Method" w Pomocy DAO.

## <a name="cdaorecordsetcanrestart"></a><a name="canrestart"></a>Zestaw CDaoRecordset::CanRestart

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy plik recordset `Requery` umożliwia ponowne uruchomienie kwerendy (aby odświeżyć swoje rekordy) przez wywołanie funkcji elementu członkowskiego.

```
BOOL CanRestart();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, `Requery` jeśli można wywołać, aby ponownie uruchomić kwerendę pliku recordset, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zestawy rekordów typu tabeli nie obsługują `Requery`.

Jeśli `Requery` nie jest obsługiwany, zadzwoń [Zamknij,](#close) a następnie [Otwórz,](#open) aby odświeżyć dane. Po zmianie `Requery` wartości parametrów można wywołać wywołanie aktualizacji podstawowej kwerendy parametrów obiektu recordset.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość do ponownego uruchomienia" w Pomocy DAO.

## <a name="cdaorecordsetcanscroll"></a><a name="canscroll"></a>CDaoRecordset::CanScroll

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy rekordet umożliwia przewijanie.

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli można przewijać rekordy, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli wywołasz `dbForwardOnly` [Open](#open) with, plan rekordów może przewijać tylko do przodu.

Aby uzyskać powiązane informacje, zobacz temat "Pozycjonowanie bieżącego wskaźnika rekordu z DAO" w Pomocy DAO.

## <a name="cdaorecordsetcantransact"></a><a name="cantransact"></a>CDaoRecordset::CanTransact

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy rekordet zezwala na transakcje.

```
BOOL CanTransact();
```

### <a name="return-value"></a>Wartość zwracana

Wartość niezerowa, jeśli bazowe źródło danych obsługuje transakcje, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać powiązane informacje, zobacz temat "Właściwość transakcji" w Pomocy DAO.

## <a name="cdaorecordsetcanupdate"></a><a name="canupdate"></a>CDaoRecordset::CanUpdate

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy plik recordset może być aktualizowany.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli plik records można zaktualizować (dodać, zaktualizować i usunąć rekordy), w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zestaw rekordów może być tylko do odczytu, jeśli bazowe `dbReadOnly` źródło danych jest tylko do odczytu lub jeśli określono dla *nOptions,* gdy został wywołany [Otwórz](#open) dla zbioru rekordów.

Aby uzyskać powiązane informacje, zobacz tematy "AddNew Method", "Edit Method", "Delete Method", "Update Method" i "Updatable Property" w Pomocy DAO.

## <a name="cdaorecordsetcdaorecordset"></a><a name="cdaorecordset"></a>CDaoRecordset::CDaoRecordset

Konstruuje `CDaoRecordset` obiekt.

```
CDaoRecordset(CDaoDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>Parametry

*pDatabase (baza danych)*<br/>
Zawiera wskaźnik do obiektu [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) lub wartości NULL. Jeśli nie NULL `CDaoDatabase` i `Open` funkcja elementu członkowskiego obiektu nie został wywołany, aby połączyć go ze źródłem danych, zestaw rekordów próbuje otworzyć go dla Ciebie podczas własnego [open](#open) wywołania. Jeśli przekażesz `CDaoDatabase` wartość NULL, obiekt zostanie skonstruowany i połączony przy użyciu informacji o `CDaoRecordset`źródle danych określonych w przypadku uzyskania klasy zestawu rekordów z programu .

### <a name="remarks"></a>Uwagi

Można użyć `CDaoRecordset` bezpośrednio lub wyprowadzić klasę specyficzną dla aplikacji z programu `CDaoRecordset`. ClassWizard służy do uzyskiwania klas recordset.

> [!NOTE]
> Jeśli wyprowadzisz `CDaoRecordset` klasę, klasa pochodna musi dostarczyć własny konstruktor. W konstruktorze klasy pochodnej wywołać `CDaoRecordset::CDaoRecordset`konstruktora , przekazując odpowiednie parametry wraz z nim.

Przekaż wartość NULL do konstruktora pliku recordset, `CDaoDatabase` aby obiekt został automatycznie skonstruowany i połączony. Jest to przydatny skrót, który nie wymaga `CDaoDatabase` konstruowania i łączenia obiektu przed skonstruowaniem zestawu rekordów. Jeśli `CDaoDatabase` obiekt nie jest otwarty, zostanie również utworzony obiekt [CDaoWorkspace,](../../mfc/reference/cdaoworkspace-class.md) który używa domyślnego obszaru roboczego. Aby uzyskać więcej informacji, zobacz [CDaoDatabase::CDaoDatabase](../../mfc/reference/cdaodatabase-class.md#cdaodatabase).

## <a name="cdaorecordsetclose"></a><a name="close"></a>CDaoRecordset::Zamknij

Zamknięcie `CDaoRecordset` obiektu powoduje usunięcie go z kolekcji otwartych rekordów w skojarzonej bazie danych.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Ponieważ `Close` nie niszczy `CDaoRecordset` obiektu, można ponownie użyć `Open` obiektu, wywołując to samo źródło danych lub inne źródło danych.

Wszystkie oczekujące [instrukcje AddNew](#addnew) lub [Edit](#edit) są anulowane, a wszystkie oczekujące transakcje są przywracane. Jeśli chcesz zachować oczekujące dodatki lub zmiany, `Close` zadzwoń do [Update](#update) przed wywołaniem dla każdego pliku rekordów.

Możesz zadzwonić `Open` ponownie `Close`po wywołaniu . Dzięki temu można ponownie użyć obiektu akcesetu. Lepszą alternatywą jest [wywołanie Requery](#requery), jeśli to możliwe.

Aby uzyskać powiązane informacje, zobacz temat "Zamknij metodę" w Pomocy DAO.

## <a name="cdaorecordsetdelete"></a><a name="delete"></a>CDaoRecordset::Delete

Wywołanie tej funkcji elementu członkowskiego w celu usunięcia bieżącego rekordu w otwartym obiekcie zestawu rekordów typu dynaset lub tabeli.

```
virtual void Delete();
```

### <a name="remarks"></a>Uwagi

Po pomyślnym usunięciu elementy członkowskie danych pola zestawu rekordów są ustawione na wartość Null i należy jawnie wywołać jedną z funkcji elementu członkowskiego nawigacji zestawu rekordów ( [Move](#move), [Seek](#seek), [SetBookmark](#setbookmark)i tak dalej), aby przenieść usunięty rekord. Podczas usuwania rekordów z akcesu musi znajdować się `Delete`bieżący rekord w ustawie rekordów przed wywołaniem; w przeciwnym razie MFC zgłasza wyjątek.

`Delete`usuwa bieżący rekord i sprawia, że jest niedostępny. Chociaż nie można edytować ani używać usuniętego rekordu, pozostaje on aktualny. Jednak po przejściu do innego rekordu nie można ponownie wprowadzić usuniętego rekordu.

> [!CAUTION]
> W uiszczeniu musi być aktualizowany numer rekordu, a w `Delete`uszczylnej akuscie musi znajdować się prawidłowy prąd rekordu podczas wywoływania . Na przykład, jeśli usuniesz rekord, ale nie `Delete` przewiń do nowego rekordu przed ponownym wywołaniem, `Delete` zrzuci [CDaoException](../../mfc/reference/cdaoexception-class.md).

Można cofnąć usunięcie rekordu, jeśli używasz transakcji i wywołasz funkcję elementu członkowskiego [CDaoWorkspace::Rollback.](../../mfc/reference/cdaoworkspace-class.md#rollback) Jeśli tabela bazowa jest tabelą podstawową w relacji usuwania kaskadowego, usunięcie bieżącego rekordu może również spowodować usunięcie jednego lub kilku rekordów w tabeli obcej. Aby uzyskać więcej informacji, zobacz definicję "kaskadowe usuwanie" w Pomocy DAO.

W `AddNew` `Edit`przeciwieństwie do `Delete` i , wywołanie `Update`nie następuje wywołanie .

Aby uzyskać powiązane informacje, zobacz tematy "AddNew Method", "Edit Method", "Delete Method", "Update Method" i "Updatable Property" w Pomocy DAO.

## <a name="cdaorecordsetdofieldexchange"></a><a name="dofieldexchange"></a>CDaoRecordset::DoFieldExchange

Struktura wywołuje tę funkcję elementu członkowskiego do automatycznej wymiany danych między elementami członkowskimi danych pola obiektu zestaw rekordów i odpowiednich kolumn bieżącego rekordu w źródle danych.

```
virtual void DoFieldExchange(CDaoFieldExchange* pFX);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Zawiera wskaźnik do `CDaoFieldExchange` obiektu. Struktura będzie już skonfigurować ten obiekt, aby określić kontekst dla operacji wymiany pola.

### <a name="remarks"></a>Uwagi

Wiąże również elementy członkowskie danych parametru, jeśli istnieją, do symboli zastępczych parametrów w ciągu instrukcji SQL dla wyboru zestawie rekordów. Wymiana danych pól, zwana wymianą pól rekordów DAO (DFX), działa w obu kierunkach: od elementów członkowskich danych pola obiektu recordset do pól rekordu w źródle danych oraz z rekordu w źródle danych do obiektu zestaw rekordów. Jeśli kolumny są wiążące dynamicznie, nie są `DoFieldExchange`wymagane do zaimplementowania .

Jedyną czynnością, którą zwykle `DoFieldExchange` należy podjąć w celu zaimplementowania dla pochodnej klasy zestaw rekordów jest utworzenie klasy z ClassWizard i określić nazwy i typy danych elementów członkowskich danych pola. Można również dodać kod do tego, co pisze ClassWizard, aby określić elementy członkowskie danych parametrów. Jeśli wszystkie pola mają być powiązane dynamicznie, ta funkcja będzie nieaktywna, chyba że określisz elementy członkowskie danych parametrów.

Podczas deklarowania pochodnej klasy tablicy rekordów za pomocą ClassWizard `DoFieldExchange` kreator zapisuje dla Ciebie zastąpienie, które przypomina poniższy przykład:

[!code-cpp[NVC_MFCDatabase#2](../../mfc/codesnippet/cpp/cdaorecordset-class_2.cpp)]

## <a name="cdaorecordsetedit"></a><a name="edit"></a>Zestaw rekordów CD::Edytuj

Wywołanie tej funkcji elementu członkowskiego, aby umożliwić zmiany w bieżącym rekordzie.

```
virtual void Edit();
```

### <a name="remarks"></a>Uwagi

Po wywołaniu `Edit` funkcji elementu członkowskiego zmiany wprowadzone w polach bieżącego rekordu są kopiowane do buforu kopii. Po dokonaniu żądanych zmian w `Update` rekordzie, zadzwoń, aby zapisać zmiany. `Edit`zapisuje wartości elementów członkowskich danych zbioru rekordów. Jeśli wywołasz `Edit`, wprowadzać `Edit` zmiany, a następnie wywołać ponownie, wartości `Edit` rekordu są przywracane do tego, co było przed pierwszym wywołaniem.

> [!CAUTION]
> Jeśli edytujesz rekord, a następnie wykonasz dowolną `Update`operację, która zostanie przesunięta do innego rekordu bez pierwszego wywołania, zmiany zostaną utracone bez ostrzeżenia. Ponadto po zamknięciu pliku recordset lub nadrzędnej bazy danych edytowany rekord zostanie odrzucony bez ostrzeżenia.

W niektórych przypadkach można zaktualizować kolumnę, czyniąc ją Null (zawierającą żadnych danych). Aby to zrobić, należy wywołać `SetFieldNull` z parametrem TRUE, aby oznaczyć pole Null; powoduje to również, że kolumna ma zostać zaktualizowana. Jeśli chcesz, aby pole zostało zapisane w źródle danych, nawet `SetFieldDirty` jeśli jego wartość nie uległa zmianie, wywołanie z parametrem TRUE. Działa to nawet wtedy, gdy pole miało wartość Null.

Znaki ramowe zmieniły elementy członkowskie danych pól, aby upewnić się, że zostaną one zapisane w rekordzie w źródle danych przez mechanizm wymiany pól rekordu DAO (DFX). Zmiana wartości pola zazwyczaj ustawia pole zabrudzone automatycznie, więc rzadko trzeba wywołać [SetFieldDirty](#setfielddirty) samodzielnie, ale czasami warto upewnić się, że kolumny będą jawnie aktualizowane lub wstawiane niezależnie od wartości, która znajduje się w polu elementu członkowskiego danych. Mechanizm DFX wykorzystuje również pseudo **null**. Aby uzyskać więcej informacji, zobacz [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Jeśli mechanizm podwójnego buforowania nie jest używany, zmiana wartości pola nie powoduje automatycznego ustawiania pola jako zabrudzone. W takim przypadku konieczne będzie jawne ustawienie pola zabrudzone. Flaga zawarta w [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) steruje automatycznym sprawdzaniem pola.

Gdy obiekt pliku recordset jest pesymistycznie zablokowany w środowisku wielodojowym, rekord pozostaje zablokowany od czasu, `Edit` gdy jest używany do czasu zakończenia aktualizacji. Jeśli plik recordset jest optymistycznie zablokowany, rekord jest zablokowany i porównywany z wstępnie edytowanym rekordem tuż przed jego zaktualizowaniem w bazie danych. Jeśli rekord został zmieniony `Edit`od `Update` czasu wywołania, operacja kończy się niepowodzeniem i MFC zgłasza wyjątek. Tryb blokowania można zmienić `SetLockingMode`za pomocą pliku .

> [!NOTE]
> Optymistyczne blokowanie jest zawsze używane w formatach zewnętrznej bazy danych, takich jak ODBC i instalowalny program ISAM.

Bieżący rekord pozostaje aktualny `Edit`po wywołaniu . Aby `Edit`wywołać , musi istnieć bieżący rekord. Jeśli nie ma bieżącego rekordu lub zestaw rekordów nie odwołuje się do otwartego obiektu zestawu rekordów typu tabeli lub dynaset, występuje wyjątek. Wywołanie `Edit` `CDaoException` powoduje, że mają być wyrzucane w następujących warunkach:

- Nie ma bieżącego rekordu.

- Baza danych lub plik recordset jest tylko do odczytu.

- Żadne pola w rekordzie nie są aktualizowane.

- Baza danych lub plik recordset został otwarty do wyłącznego użytku przez innego użytkownika.

- Inny użytkownik zablokował stronę zawierającą rekord.

Jeśli źródło danych obsługuje transakcje, można `Edit` dokonać wywołania część transakcji. Należy pamiętać, `CDaoWorkspace::BeginTrans` że `Edit` należy wywołać przed wywołaniem i po otwarciu pliku recordset. Należy również `CDaoWorkspace::CommitTrans` zauważyć, że wywołanie nie zastępuje wywoływania, `Update` aby zakończyć `Edit` operację. Aby uzyskać więcej informacji o `CDaoWorkspace`transakcjach, zobacz klasa .

Aby uzyskać powiązane informacje, zobacz tematy "AddNew Method", "Edit Method", "Delete Method", "Update Method" i "Updatable Property" w Pomocy DAO.

## <a name="cdaorecordsetfillcache"></a><a name="fillcache"></a>CDaoRecordset::FillCache

Wywołanie tej funkcji elementu członkowskiego w pamięci podręcznej określonej liczby rekordów z zestawu rekordów.

```cpp
void FillCache(
    long* pSize = NULL,
    COleVariant* pBookmark = NULL);
```

### <a name="parameters"></a>Parametry

*pSize (rozmiar)*<br/>
Określa liczbę wierszy do wypełnienia w pamięci podręcznej. Jeśli ten parametr zostanie pominięty, wartość jest określana przez ustawienie właściwości CacheSize leżącego u podstaw obiektu DAO.

*pBookmark (Znak książki)*<br/>
[COleVariant](../../mfc/reference/colevariant-class.md) określający zakładkę. Pamięć podręczna jest wypełniona, zaczynając od rekordu wskazanego przez tę zakładkę. Jeśli pominięto ten parametr, pamięć podręczna jest wypełniona począwszy od rekordu wskazanego przez cachestart właściwości podstawowego obiektu DAO.

### <a name="remarks"></a>Uwagi

Buforowanie zwiększa wydajność aplikacji, która pobiera lub pobiera dane z serwera zdalnego. Pamięć podręczna to miejsce w pamięci lokalnej, w których znajdują się dane ostatnio pobrane z serwera przy założeniu, że dane będą prawdopodobnie wymagane ponownie, gdy aplikacja jest uruchomiona. Gdy wymagane są dane, aparat bazy danych Microsoft Jet najpierw sprawdza pamięć podręczną dla danych, a nie pobiera ją z serwera, co zajmuje więcej czasu. Korzystanie z buforowania danych na źródłach danych innych niż ODBC nie ma wpływu, ponieważ dane nie są zapisywane w pamięci podręcznej.

Zamiast czekać na pamięć podręczną, które mają być wypełnione rekordami, ponieważ są one pobierane, można jawnie wypełnić pamięci podręcznej w dowolnym momencie, wywołując funkcję `FillCache` elementu członkowskiego. Jest to szybszy sposób wypełniania pamięci podręcznej, ponieważ `FillCache` pobiera kilka rekordów jednocześnie zamiast jednego naraz. Na przykład podczas wyświetlania każdego zrzutu ekranu rekordów można `FillCache` wywołać aplikację, aby pobrać następny zrzut ekranu rekordów.

Każda baza danych ODBC dostępna za pomocą obiektów zestawu rekordów może mieć lokalną pamięć podręczną. Aby utworzyć pamięć podręczną, otwórz obiekt zestaw rekordów ze `SetCacheSize` `SetCacheStart` zdalnego źródła danych, a następnie zadzwoń do funkcji i członków zbioru rekordów. Jeśli *lSize* i *lBookmark* utworzyć zakres, który jest częściowo `SetCacheSize` `SetCacheStart`lub całkowicie poza zakresem określonym przez i , część zestaw rekordów poza tym zakresem jest ignorowana i nie jest ładowany do pamięci podręcznej. Jeśli `FillCache` żąda więcej rekordów niż pozostają w zdalnym źródle danych, tylko pozostałe rekordy są pobierane i nie jest zgłaszany wyjątek.

Rekordy pobrane z pamięci podręcznej nie odzwierciedlają zmian wprowadzonych równocześnie do danych źródłowych przez innych użytkowników.

`FillCache`pobiera tylko rekordy, które nie zostały jeszcze zapisane w pamięci podręcznej. Aby wymusić aktualizację wszystkich buforowanych `SetCacheSize` danych, należy wywołać funkcję elementu członkowskiego `SetCacheSize` z parametrem *lSize* równym 0, wywołać ponownie z `FillCache`parametrem *lSize* równym rozmiarowi pierwotnie żądanej pamięci podręcznej, a następnie wywołać .

Aby uzyskać powiązane informacje, zobacz temat "FillCache Method" w Pomocy DAO.

## <a name="cdaorecordsetfind"></a><a name="find"></a>CDaoRecordset::Znajdź

Wywołanie tej funkcji elementu członkowskiego, aby zlokalizować określonego ciągu w zestawie rekordów typu dynaset- lub snapshot przy użyciu operatora porównania.

```
virtual BOOL Find(
    long lFindType,
    LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lFindType (Typ odnajdywania)*<br/>
Wartość wskazująca typ operacji Znajdź żądaną. Możliwe wartości są następujące:

- AFX_DAO_NEXT Znajdź następną lokalizację pasującego ciągu.

- AFX_DAO_PREV Znajdź poprzednią lokalizację pasującego ciągu.

- AFX_DAO_FIRST Znajdź pierwszą lokalizację pasującego ciągu.

- AFX_DAO_LAST Znajdź ostatnią lokalizację pasującego ciągu.

*lpszFilter*<br/>
Wyrażenie ciągu (takie jak klauzula **WHERE** w instrukcji SQL bez słowa **WHERE)** używane do lokalizowania rekordu. Przykład:

[!code-cpp[NVC_MFCDatabase#3](../../mfc/codesnippet/cpp/cdaorecordset-class_3.cpp)]

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli pasujące rekordy są znalezione, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Można znaleźć pierwsze, następne, poprzednie lub ostatnie wystąpienie ciągu. `Find`jest funkcją wirtualną, dzięki czemu można ją zastąpić i dodać własną implementację. `FindFirst`Funkcje `FindLast` `FindNext`, `FindPrev` i element `Find` członkowski wywołują funkcję elementu członkowskiego, dzięki czemu można sterować `Find` zachowaniem wszystkich operacji Znajdź.

Aby zlokalizować rekord w tablicy rekordowej, należy wywołać funkcję [Szukaj](#seek) elementu członkowskiego.

> [!TIP]
> Im mniejszy zestaw rekordów, tym `Find` bardziej skuteczny będzie. Ogólnie rzecz biorąc, a zwłaszcza w przypadku danych ODBC, lepiej jest utworzyć nową kwerendę, która pobiera tylko rekordy, które chcesz.

Aby uzyskać powiązane informacje, zobacz temat "FindFirst, FindLast, FindNext, FindPrevious Methods" w Pomocy DAO.

## <a name="cdaorecordsetfindfirst"></a><a name="findfirst"></a>CDaoRecordset::ZnajdźPowierasz

Wywołanie tej funkcji elementu członkowskiego, aby znaleźć pierwszy rekord, który pasuje do określonego warunku.

```
BOOL FindFirst(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lpszFilter*<br/>
Wyrażenie ciągu (takie jak klauzula **WHERE** w instrukcji SQL bez słowa **WHERE)** używane do lokalizowania rekordu.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli pasujące rekordy są znalezione, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Funkcja `FindFirst` elementu członkowskiego rozpoczyna wyszukiwanie od początku pliku recordset i wyszukuje do końca pliku recordset.

Jeśli chcesz uwzględnić wszystkie rekordy w wyszukiwaniu (nie tylko te, które spełniają określony warunek), użyj jednej z operacji Przenieś, aby przejść z rekordu do rekordu. Aby zlokalizować rekord w tablicy rekordowej, należy wywołać `Seek` funkcję elementu członkowskiego.

Jeśli rekord spełniający kryteria nie znajduje się, bieżący wskaźnik `FindFirst` rekordu jest nieokreślony i zwraca wartość zero. Jeśli plik recordset zawiera więcej niż jeden rekord, `FindFirst` który spełnia kryteria, `FindNext` lokalizuje pierwsze wystąpienie, lokalizuje następne wystąpienie i tak dalej.

> [!CAUTION]
> Jeśli edytujesz bieżący rekord, pamiętaj, aby `Update` zapisać zmiany, wywołując funkcję elementu członkowskiego przed przejściem do innego rekordu. Jeśli przejdziesz do innego rekordu bez aktualizacji, zmiany zostaną utracone bez ostrzeżenia.

Funkcje `Find` członkowskie wyszukują z lokalizacji i w kierunku określonym w poniższej tabeli:

|Znajdź operacje|Rozpocznij|Kierunek wyszukiwania|
|---------------------|-----------|----------------------|
|`FindFirst`|Początek księgi rekordów|Koniec rekordów|
|`FindLast`|Koniec rekordów|Początek księgi rekordów|
|`FindNext`|Bieżący rekord|Koniec rekordów|
|`FindPrevious`|Bieżący rekord|Początek księgi rekordów|

> [!NOTE]
> Podczas wywoływania `FindLast`aparat bazy danych Microsoft Jet w pełni wypełnia swój rekord przed rozpoczęciem wyszukiwania, jeśli nie zostało to jeszcze zrobione. Pierwsze wyszukiwanie może trwać dłużej niż kolejne wyszukiwania.

Korzystanie z jednej z operacji Znajdź `MoveFirst` nie `MoveNext`jest takie samo jak wywołanie lub , jednak, który po prostu sprawia, że pierwszy lub następny rekord bieżący bez określania warunku. Operację Znajdź można wykonać za pomocą operacji Przenoszenie.

Podczas korzystania z operacji Znajdź należy pamiętać o następujących zachowaniach:

- Jeśli `Find` zwraca wartość niezerowa, bieżący rekord nie jest zdefiniowany. W takim przypadku należy umieścić bieżący wskaźnik rekordu z powrotem do prawidłowego rekordu.

- Nie można użyć operacji Znajdź z przewijanym do przodu kiełkowym rekordem migawki.

- Podczas wyszukiwania pól zawierających daty należy używać formatu daty stanów Zjednoczonych (miesiąc-dzień-rok), nawet jeśli nie jest używana amerykańska wersja aparatu bazy danych microsoft jet; w przeciwnym razie nie można znaleźć pasujących rekordów.

- Podczas pracy z bazami danych ODBC i dużych zestawów dynamiki można zauważyć, że korzystanie z operacji Znajdź jest powolne, szczególnie podczas pracy z dużymi zestawami rekordów. Można zwiększyć wydajność przy użyciu zapytań SQL z dostosowanych **klauzul ORDERBY** lub **WHERE,** kwerendy parametry lub `CDaoQuerydef` obiekty, które pobierają określone rekordy indeksowane.

Aby uzyskać powiązane informacje, zobacz temat "FindFirst, FindLast, FindNext, FindPrevious Methods" w Pomocy DAO.

## <a name="cdaorecordsetfindlast"></a><a name="findlast"></a>CDaoRecordset::FindLast

Wywołanie tej funkcji elementu członkowskiego, aby znaleźć ostatni rekord, który pasuje do określonego warunku.

```
BOOL FindLast(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lpszFilter*<br/>
Wyrażenie ciągu (takie jak klauzula **WHERE** w instrukcji SQL bez słowa **WHERE)** używane do lokalizowania rekordu.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli pasujące rekordy są znalezione, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Funkcja `FindLast` elementu członkowskiego rozpoczyna wyszukiwanie na końcu pliku rekordów i przeszukuje wstecz w kierunku początku pliku recordset.

Jeśli chcesz uwzględnić wszystkie rekordy w wyszukiwaniu (nie tylko te, które spełniają określony warunek), użyj jednej z operacji Przenieś, aby przejść z rekordu do rekordu. Aby zlokalizować rekord w tablicy rekordowej, należy wywołać `Seek` funkcję elementu członkowskiego.

Jeśli rekord spełniający kryteria nie znajduje się, bieżący wskaźnik `FindLast` rekordu jest nieokreślony i zwraca wartość zero. Jeśli plik recordset zawiera więcej niż jeden rekord, `FindFirst` który spełnia kryteria, `FindNext` lokalizuje pierwsze wystąpienie, lokalizuje następne wystąpienie po pierwszym wystąpieniu i tak dalej.

> [!CAUTION]
> Jeśli edytujesz bieżący rekord, upewnij się, `Update` że zmiany zostały zapisane przez wywołanie funkcji elementu członkowskiego przed przejściem do innego rekordu. Jeśli przejdziesz do innego rekordu bez aktualizacji, zmiany zostaną utracone bez ostrzeżenia.

Korzystanie z jednej z operacji Znajdź `MoveFirst` nie `MoveNext`jest takie samo jak wywołanie lub , jednak, który po prostu sprawia, że pierwszy lub następny rekord bieżący bez określania warunku. Operację Znajdź można wykonać za pomocą operacji Przenoszenie.

Podczas korzystania z operacji Znajdź należy pamiętać o następujących zachowaniach:

- Jeśli `Find` zwraca wartość niezerowa, bieżący rekord nie jest zdefiniowany. W takim przypadku należy umieścić bieżący wskaźnik rekordu z powrotem do prawidłowego rekordu.

- Nie można użyć operacji Znajdź z przewijanym do przodu kiełkowym rekordem migawki.

- Podczas wyszukiwania pól zawierających daty należy używać formatu daty stanów Zjednoczonych (miesiąc-dzień-rok), nawet jeśli nie jest używana amerykańska wersja aparatu bazy danych microsoft jet; w przeciwnym razie nie można znaleźć pasujących rekordów.

- Podczas pracy z bazami danych ODBC i dużych zestawów dynamiki można zauważyć, że korzystanie z operacji Znajdź jest powolne, szczególnie podczas pracy z dużymi zestawami rekordów. Można zwiększyć wydajność przy użyciu zapytań SQL z dostosowanych **klauzul ORDERBY** lub **WHERE,** kwerendy parametry lub `CDaoQuerydef` obiekty, które pobierają określone rekordy indeksowane.

Aby uzyskać powiązane informacje, zobacz temat "FindFirst, FindLast, FindNext, FindPrevious Methods" w Pomocy DAO.

## <a name="cdaorecordsetfindnext"></a><a name="findnext"></a>Zestaw CDaoRecordset::FindNext

Wywołanie tej funkcji elementu członkowskiego, aby znaleźć następny rekord, który pasuje do określonego warunku.

```
BOOL FindNext(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lpszFilter*<br/>
Wyrażenie ciągu (takie jak klauzula **WHERE** w instrukcji SQL bez słowa **WHERE)** używane do lokalizowania rekordu.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli pasujące rekordy są znalezione, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Funkcja `FindNext` elementu członkowskiego rozpoczyna wyszukiwanie w bieżącym rekordzie i wyszukuje do końca rekordu.

Jeśli chcesz uwzględnić wszystkie rekordy w wyszukiwaniu (nie tylko te, które spełniają określony warunek), użyj jednej z operacji Przenieś, aby przejść z rekordu do rekordu. Aby zlokalizować rekord w tablicy rekordowej, należy wywołać `Seek` funkcję elementu członkowskiego.

Jeśli rekord spełniający kryteria nie znajduje się, bieżący wskaźnik `FindNext` rekordu jest nieokreślony i zwraca wartość zero. Jeśli plik recordset zawiera więcej niż jeden rekord, `FindFirst` który spełnia kryteria, `FindNext` lokalizuje pierwsze wystąpienie, lokalizuje następne wystąpienie i tak dalej.

> [!CAUTION]
> Jeśli edytujesz bieżący rekord, upewnij się, `Update` że zmiany zostały zapisane przez wywołanie funkcji elementu członkowskiego przed przejściem do innego rekordu. Jeśli przejdziesz do innego rekordu bez aktualizacji, zmiany zostaną utracone bez ostrzeżenia.

Korzystanie z jednej z operacji Znajdź `MoveFirst` nie `MoveNext`jest takie samo jak wywołanie lub , jednak, który po prostu sprawia, że pierwszy lub następny rekord bieżący bez określania warunku. Operację Znajdź można wykonać za pomocą operacji Przenoszenie.

Podczas korzystania z operacji Znajdź należy pamiętać o następujących zachowaniach:

- Jeśli `Find` zwraca wartość niezerowa, bieżący rekord nie jest zdefiniowany. W takim przypadku należy umieścić bieżący wskaźnik rekordu z powrotem do prawidłowego rekordu.

- Nie można użyć operacji Znajdź z przewijanym do przodu kiełkowym rekordem migawki.

- Podczas wyszukiwania pól zawierających daty należy używać formatu daty stanów Zjednoczonych (miesiąc-dzień-rok), nawet jeśli nie jest używana amerykańska wersja aparatu bazy danych microsoft jet; w przeciwnym razie nie można znaleźć pasujących rekordów.

- Podczas pracy z bazami danych ODBC i dużych zestawów dynamiki można zauważyć, że korzystanie z operacji Znajdź jest powolne, szczególnie podczas pracy z dużymi zestawami rekordów. Można zwiększyć wydajność przy użyciu zapytań SQL z dostosowanych **klauzul ORDERBY** lub **WHERE,** kwerendy parametry lub `CDaoQuerydef` obiekty, które pobierają określone rekordy indeksowane.

Aby uzyskać powiązane informacje, zobacz temat "FindFirst, FindLast, FindNext, FindPrevious Methods" w Pomocy DAO.

## <a name="cdaorecordsetfindprev"></a><a name="findprev"></a>Zestaw CDaoRecordset::FindPrev

Wywołanie tej funkcji elementu członkowskiego, aby znaleźć poprzedni rekord, który pasuje do określonego warunku.

```
BOOL FindPrev(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lpszFilter*<br/>
Wyrażenie ciągu (takie jak klauzula **WHERE** w instrukcji SQL bez słowa **WHERE)** używane do lokalizowania rekordu.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli pasujące rekordy są znalezione, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Funkcja `FindPrev` elementu członkowskiego rozpoczyna wyszukiwanie w bieżącym rekordzie i przeszukuje wstecz w kierunku początku rekordu.

Jeśli chcesz uwzględnić wszystkie rekordy w wyszukiwaniu (nie tylko te, które spełniają określony warunek), użyj jednej z operacji Przenieś, aby przejść z rekordu do rekordu. Aby zlokalizować rekord w tablicy rekordowej, należy wywołać `Seek` funkcję elementu członkowskiego.

Jeśli rekord spełniający kryteria nie znajduje się, bieżący wskaźnik `FindPrev` rekordu jest nieokreślony i zwraca wartość zero. Jeśli plik recordset zawiera więcej niż jeden rekord, `FindFirst` który spełnia kryteria, `FindNext` lokalizuje pierwsze wystąpienie, lokalizuje następne wystąpienie i tak dalej.

> [!CAUTION]
> Jeśli edytujesz bieżący rekord, upewnij się, `Update` że zmiany zostały zapisane przez wywołanie funkcji elementu członkowskiego przed przejściem do innego rekordu. Jeśli przejdziesz do innego rekordu bez aktualizacji, zmiany zostaną utracone bez ostrzeżenia.

Korzystanie z jednej z operacji Znajdź `MoveFirst` nie `MoveNext`jest takie samo jak wywołanie lub , jednak, który po prostu sprawia, że pierwszy lub następny rekord bieżący bez określania warunku. Operację Znajdź można wykonać za pomocą operacji Przenoszenie.

Podczas korzystania z operacji Znajdź należy pamiętać o następujących zachowaniach:

- Jeśli `Find` zwraca wartość niezerowa, bieżący rekord nie jest zdefiniowany. W takim przypadku należy umieścić bieżący wskaźnik rekordu z powrotem do prawidłowego rekordu.

- Nie można użyć operacji Znajdź z przewijanym do przodu kiełkowym rekordem migawki.

- Podczas wyszukiwania pól zawierających daty należy używać formatu daty stanów Zjednoczonych (miesiąc-dzień-rok), nawet jeśli nie jest używana amerykańska wersja aparatu bazy danych microsoft jet; w przeciwnym razie nie można znaleźć pasujących rekordów.

- Podczas pracy z bazami danych ODBC i dużych zestawów dynamiki można zauważyć, że korzystanie z operacji Znajdź jest powolne, szczególnie podczas pracy z dużymi zestawami rekordów. Można zwiększyć wydajność przy użyciu zapytań SQL z dostosowanych **klauzul ORDERBY** lub **WHERE,** kwerendy parametry lub `CDaoQuerydef` obiekty, które pobierają określone rekordy indeksowane.

Aby uzyskać powiązane informacje, zobacz temat "FindFirst, FindLast, FindNext, FindPrevious Methods" w Pomocy DAO.

## <a name="cdaorecordsetgetabsoluteposition"></a><a name="getabsoluteposition"></a>CDaoRecordset::GetAbsolutePosition

Zwraca numer rekordu bieżącego rekordu obiektu zestawu rekordów.

```
long GetAbsolutePosition();
```

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita od 0 do liczby rekordów w tablicy rekordów. Odpowiada pozycji porządkowej bieżącego rekordu w zakuł rekordy.

### <a name="remarks"></a>Uwagi

Wartość właściwości AbsolutePosition bazowego obiektu DAO jest oparta na wartości zero; ustawienie 0 odnosi się do pierwszego rekordu w ustawie rekordzie. Liczbę wypełnionych rekordów w akubinacie rekordy można określić, wywołując [plik GetRecordCount](#getrecordcount). Wywołanie `GetRecordCount` może zająć trochę czasu, ponieważ musi uzyskać dostęp do wszystkich rekordów, aby określić liczbę.

Jeśli nie ma bieżącego rekordu, jak wtedy, gdy nie ma żadnych rekordów w pliku recordset, - 1 jest zwracany. Jeśli bieżący rekord zostanie usunięty, wartość właściwości AbsolutePosition nie jest zdefiniowana, a MFC zgłasza wyjątek, jeśli odwołuje się do niego. W przypadku zestawów rekordów typu dynaset nowe rekordy są dodawane na końcu sekwencji.

> [!NOTE]
> Ta właściwość nie jest przeznaczona do użycia jako numer rekordu zastępczego. Zakładki są nadal zalecanym sposobem zachowania i powrotu do danej pozycji i są jedynym sposobem na umieszczenie bieżącego rekordu we wszystkich typach obiektów znacznika rekordu. W szczególności pozycja danego rekordu zmienia się, gdy rekordy poprzedzające go są usuwane. Nie ma również pewności, że dany rekord będzie miał taką samą pozycję bezwzględną, jeśli znak rekordów zostanie ponownie utworzony, ponieważ kolejność poszczególnych rekordów w zestawie rekordów nie jest gwarantowana, chyba że zostanie utworzona za pomocą instrukcji SQL przy użyciu klauzuli **ORDERBY.**

> [!NOTE]
> Ta funkcja elementu członkowskiego jest prawidłowa tylko dla zestawów rekordów typu dynaset i migawki.

Aby uzyskać powiązane informacje, zobacz temat "AbsolutePosition Property" w Pomocy DAO.

## <a name="cdaorecordsetgetbookmark"></a><a name="getbookmark"></a>CDaoRecordset::GetBookmark

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać wartość zakładki w określonym rekordzie.

```
COleVariant GetBookmark();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość reprezentującą zakładkę w bieżącym rekordzie.

### <a name="remarks"></a>Uwagi

Gdy obiekt zestaw rekordów jest tworzony lub otwierany, każdy z jego rekordów ma już unikatową zakładkę, jeśli je obsługuje. Wywołanie, `CanBookmark` aby ustalić, czy zestaw rekordów obsługuje zakładki.

Zakładkę dla bieżącego rekordu można zapisać, przypisując wartość zakładki do `COleVariant` obiektu. Aby szybko powrócić do tego rekordu w dowolnym momencie po przejściu do innego rekordu, wywołanie `SetBookmark` z parametrem odpowiadającym wartości tego `COleVariant` obiektu.

> [!NOTE]
> Wywołanie [ponownego zapytania](#requery) zmienia zakładki DAO.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość zakładek" w Pomocy DAO.

## <a name="cdaorecordsetgetcachesize"></a><a name="getcachesize"></a>CDaoRecordset::GetCachESize

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać liczbę rekordów w pamięci podręcznej.

```
long GetCacheSize();
```

### <a name="return-value"></a>Wartość zwracana

Wartość określająca liczbę rekordów w zestawie rekordów typu dynaset zawierającego dane, które mają być buforowane lokalnie ze źródła danych ODBC.

### <a name="remarks"></a>Uwagi

Buforowanie danych zwiększa wydajność aplikacji, która pobiera dane z serwera zdalnego za pośrednictwem obiektów zestawu rekordów typu dynaset. Pamięć podręczna to miejsce w pamięci lokalnej, w których dane są ostatnio pobierane z serwera w przypadku, gdy dane zostaną ponownie żądane, gdy aplikacja jest uruchomiona. Gdy wymagane są dane, aparat bazy danych Microsoft Jet najpierw sprawdza pamięć podręczną dla żądanych danych, zamiast pobierać je z serwera, co zajmuje więcej czasu. Dane, które nie pochodzą ze źródła danych ODBC nie są zapisywane w pamięci podręcznej.

Każde źródło danych ODBC, takie jak tabela dołączone, może mieć lokalną pamięć podręczną.

Aby uzyskać powiązane informacje, zobacz temat "CacheSize, CacheStart Properties" w Pomocy DAO.

## <a name="cdaorecordsetgetcachestart"></a><a name="getcachestart"></a>Zestaw CDaoRecordset::GetCacheStart

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać wartość zakładki pierwszego rekordu w zestaw rekordów do buforowania.

```
COleVariant GetCacheStart();
```

### <a name="return-value"></a>Wartość zwracana

A, `COleVariant` który określa zakładkę pierwszego rekordu w zestaw rekordów do buforowania.

### <a name="remarks"></a>Uwagi

Aparat bazy danych Microsoft Jet żąda rekordów w zakresie pamięci podręcznej z pamięci podręcznej i żąda rekordów poza zakresem pamięci podręcznej z serwera.

> [!NOTE]
> Rekordy pobrane z pamięci podręcznej nie odzwierciedlają zmian wprowadzonych równocześnie w danych źródłowych przez innych użytkowników.

Aby uzyskać powiązane informacje, zobacz temat "CacheSize, CacheStart Properties" w Pomocy DAO.

## <a name="cdaorecordsetgetcurrentindex"></a><a name="getcurrentindex"></a>CDaoRecordset::GetCurrentIndex

Wywołanie tej funkcji elementu członkowskiego, aby określić indeks `CDaoRecordset` aktualnie używany w obiekcie typu tabela indeksowana.

```
CString GetCurrentIndex();
```

### <a name="return-value"></a>Wartość zwracana

A `CString` zawierający nazwę indeksu aktualnie używanego z tablicą rekordów. Zwraca pusty ciąg, jeśli nie ustawiono indeksu.

### <a name="remarks"></a>Uwagi

Ten indeks jest podstawą do zamawiania rekordów w tablicy typu recordset i jest używany przez [funkcję Szukaj](#seek) elementu członkowskiego do lokalizowania rekordów.

Obiekt `CDaoRecordset` może mieć więcej niż jeden indeks, ale można użyć tylko jeden indeks naraz (chociaż [obiekt CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) może mieć kilka indeksów zdefiniowane na nim).

Aby uzyskać powiązane informacje, zobacz temat "Obiekt indeksu" i definicję "bieżący indeks" w Pomocy DAO.

## <a name="cdaorecordsetgetdatecreated"></a><a name="getdatecreated"></a>CDaoRecordset::GetDateTworzone

Wywołanie tej funkcji elementu członkowskiego, aby pobrać datę i godzinę utworzenia tabeli bazowej.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) zawierający datę i godzinę utworzenia tabeli bazowej.

### <a name="remarks"></a>Uwagi

Ustawienia daty i godziny są uzyskiwane z komputera, na którym utworzono tabelę bazową.

Aby uzyskać powiązane informacje, zobacz temat "DateCreated, LastUpdated Properties" w Pomocy DAO.

## <a name="cdaorecordsetgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDaoRecordset::GetDateLastUpdated

Wywołanie tej funkcji elementu członkowskiego, aby pobrać datę i godzinę ostatniego zaktualizowanie schematu.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) zawierający datę i godzinę ostatniej aktualizacji struktury tabeli bazowej (schematu).

### <a name="remarks"></a>Uwagi

Ustawienia daty i godziny są uzyskiwane z komputera, na którym ostatnio zaktualizowano strukturę tabeli podstawowej (schematu).

Aby uzyskać powiązane informacje, zobacz temat "DateCreated, LastUpdated Properties" w Pomocy DAO.

## <a name="cdaorecordsetgetdefaultdbname"></a><a name="getdefaultdbname"></a>CDaoRecordset::GetDefaultDBName

Wywołanie tej funkcji elementu członkowskiego, aby określić nazwę bazy danych dla tego pliku recordset.

```
virtual CString GetDefaultDBName();
```

### <a name="return-value"></a>Wartość zwracana

A, `CString` który zawiera ścieżkę i nazwę bazy danych, z której pochodzi ten plik recordset.

### <a name="remarks"></a>Uwagi

Jeśli plik recordset jest tworzony bez wskaźnika do [bazy danych CDDaoDatabase,](../../mfc/reference/cdaodatabase-class.md)ta ścieżka jest używana przez plan rekordów do otwierania domyślnej bazy danych. Domyślnie ta funkcja zwraca pusty ciąg. Gdy ClassWizard wywodzi `CDaoRecordset`nowy rekord z , utworzy tę funkcję dla Ciebie.

Poniższy przykład ilustruje użycie podwójnego ukośnika odwrotnego (\\\\) w ciągu, zgodnie z wymogami dla ciągu, który ma być interpretowany poprawnie.

[!code-cpp[NVC_MFCDatabase#4](../../mfc/codesnippet/cpp/cdaorecordset-class_4.cpp)]

## <a name="cdaorecordsetgetdefaultsql"></a><a name="getdefaultsql"></a>CDaoRecordset::GetDefaultSQL

Struktura wywołuje tę funkcję elementu członkowskiego, aby uzyskać domyślną instrukcję SQL, na której opiera się zestawie rekordów.

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>Wartość zwracana

A, `CString` który zawiera domyślną instrukcję SQL.

### <a name="remarks"></a>Uwagi

Może to być nazwa tabeli lub instrukcja SQL **SELECT.**

Pośrednio zdefiniować domyślną instrukcję SQL, deklarując klasę zestawie rekordów z ClassWizard i ClassWizard wykonuje to zadanie dla Ciebie.

Jeśli przekażesz zerowy ciąg SQL do [Open,](#open)ta funkcja jest wywoływana w celu określenia nazwy tabeli lub sql dla pliku recordset.

## <a name="cdaorecordsetgeteditmode"></a><a name="geteditmode"></a>CDaoRecordset::GetEditMode

Wywołanie tej funkcji elementu członkowskiego, aby określić stan edycji, która jest jedną z następujących wartości:

```
short GetEditMode();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość wskazującą stan edycji bieżącego rekordu.

### <a name="remarks"></a>Uwagi

|Wartość|Opis|
|-----------|-----------------|
|`dbEditNone`|Nie jest w toku żadna operacja edycji.|
|`dbEditInProgress`|`Edit`został powołany.|
|`dbEditAdd`|`AddNew`został powołany.|

Aby uzyskać powiązane informacje, zobacz temat "Właściwość EditMode" w Pomocy DAO.

## <a name="cdaorecordsetgetfieldcount"></a><a name="getfieldcount"></a>CDaoRecordset::GetFieldCount

Wywołanie tej funkcji elementu członkowskiego, aby pobrać liczbę pól (kolumn) zdefiniowanych w ach.

```
short GetFieldCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba pól w tablicy rekordów.

### <a name="remarks"></a>Uwagi

Aby uzyskać powiązane informacje, zobacz temat "Count Property" w Pomocy DAO.

## <a name="cdaorecordsetgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoRecordset::GetFieldInfo

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać informacje o polach w ach.

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
Indeks od zera wstępnie zdefiniowanego pola w kolekcji Fields zbioru rekordów do wyszukiwania według indeksu.

*Fieldinfo*<br/>
Odwołanie do struktury [CDaoFieldInfo.](../../mfc/reference/cdaofieldinfo-structure.md)

*dwInfoOptions (NpfoOptions)*<br/>
Opcje określające informacje o ach recordset do pobrania. Dostępne opcje są wymienione tutaj wraz z tym, co powodują, że funkcja do powrotu. Aby uzyskać najlepszą wydajność, pobierz tylko ten poziom potrzebnych informacji:

- `AFX_DAO_PRIMARY_INFO`(Domyślnie) Nazwa, typ, rozmiar, atrybuty

- `AFX_DAO_SECONDARY_INFO`Informacje podstawowe, plus: Pozycja porządkowa, wymagane, Zezwalaj na długość zerową, Kolejność sortowania, Nazwa obca, Pole źródłowe, Tabela źródłowa

- `AFX_DAO_ALL_INFO`Informacje podstawowe i pomocnicze oraz: wartość domyślna, reguła sprawdzania poprawności, tekst sprawdzania poprawności

*Lpszname*<br/>
Nazwa pola.

### <a name="remarks"></a>Uwagi

Jedna wersja funkcji umożliwia wyszukywę pola według indeksu. Druga wersja umożliwia wyszukywanie pola według nazwy.

Aby uzyskać opis zwróconych informacji, zobacz [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) struktury. Ta struktura ma elementy, które odpowiadają elementom informacji wymienionych powyżej w opisie *dwInfoOptions*. Gdy poprosisz o informacje na jednym poziomie, otrzymujesz informacje o wcześniejszych poziomach.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość atrybutów" w Pomocy DAO.

## <a name="cdaorecordsetgetfieldvalue"></a><a name="getfieldvalue"></a>Zestaw CDaoRecordset::GetFieldValue

Wywołanie tej funkcji elementu członkowskiego, aby pobrać dane w zbiorze rekordów.

```
virtual void GetFieldValue(
    LPCTSTR lpszName,
    COleVariant& varValue);

virtual void GetFieldValue(
    int nIndex,
    COleVariant& varValue);

virtual COleVariant GetFieldValue(LPCTSTR lpszName);
virtual COleVariant GetFieldValue(int nIndex);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
Wskaźnik do ciągu zawierającego nazwę pola.

*wartość varValue*<br/>
Odwołanie do `COleVariant` obiektu, który będzie przechowywać wartość pola.

*Nindex*<br/>
Indeks od zera pola w kolekcji Fields zbioru rekordów do wyszukiwania według indeksu.

### <a name="return-value"></a>Wartość zwracana

Dwie wersje `GetFieldValue` tej zwracaj wartość zwraca [COleVariant](../../mfc/reference/colevariant-class.md) obiektu, który zawiera wartość pola.

### <a name="remarks"></a>Uwagi

Można wyszukać pole według nazwy lub położenia porządkowego.

> [!NOTE]
> Jest bardziej wydajne, aby wywołać jedną z `COleVariant` wersji tej funkcji elementu członkowskiego, który przyjmuje `COleVariant` odwołanie do obiektu jako parametr, zamiast wywoływania wersji, która zwraca obiekt. Te ostatnie wersje tej funkcji są przechowywane w celu zapewnienia zgodności z powrotem.

Użyj `GetFieldValue` i [SetFieldValue](#setfieldvalue) dynamicznie powiązać pola w czasie wykonywania, a nie statycznie wiążące kolumny przy użyciu mechanizmu [DoFieldExchange.](#dofieldexchange)

`GetFieldValue`i `DoFieldExchange` mechanizm można połączyć w celu poprawy wydajności. Na przykład `GetFieldValue` użyj do pobrania wartości, która jest potrzebna tylko na żądanie, i przypisać to wywołanie do przycisku "Więcej informacji" w interfejsie.

Aby uzyskać powiązane informacje, zobacz tematy "Obiekt pola" i "Właściwość wartości" w Pomocy DAO.

## <a name="cdaorecordsetgetindexcount"></a><a name="getindexcount"></a>CDaoRecordset::GetIndexCount

Wywołanie tej funkcji elementu członkowskiego, aby określić liczbę indeksów dostępnych w tablicy rekordów typu.

```
short GetIndexCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba indeksów w zakuł rekord.

### <a name="remarks"></a>Uwagi

`GetIndexCount`jest przydatne do pętli przez wszystkie indeksy w pliku recordset. W tym celu `GetIndexCount` należy używać w połączeniu z [GetIndexInfo](#getindexinfo). Jeśli wywołasz tę funkcję elementu członkowskiego na dynaset typu lub migawki typu recordsets, MFC zgłasza wyjątek.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość atrybutów" w Pomocy DAO.

## <a name="cdaorecordsetgetindexinfo"></a><a name="getindexinfo"></a>CDaoRecordset::GetIndexInfo

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać różne rodzaje informacji o indeksie zdefiniowanym w tabeli podstawowej leżącej u podstaw pliku recordset.

```cpp
void GetIndexInfo(
    int nIndex,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetIndexInfo(
    LPCTSTR lpszName,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks od zera w kolekcji Indeksy tabeli, do wyszukiwania według pozycji numerycznej.

*indexinfo*<br/>
Odwołanie do struktury [CDaoIndexInfo.](../../mfc/reference/cdaoindexinfo-structure.md)

*dwInfoOptions (NpfoOptions)*<br/>
Opcje określające informacje o indeksie do pobrania. Dostępne opcje są wymienione tutaj wraz z tym, co powodują, że funkcja do powrotu. Aby uzyskać najlepszą wydajność, pobierz tylko ten poziom potrzebnych informacji:

- `AFX_DAO_PRIMARY_INFO`(Domyślnie) Nazwa, informacje o polu, pola

- `AFX_DAO_SECONDARY_INFO`Informacje podstawowe, plus: Podstawowy, Unikatowy, Klastrowany, IgnoreNulls, Wymagane, Obce

- `AFX_DAO_ALL_INFO`Informacje podstawowe i pomocnicze, plus: Liczba odrębnych

*Lpszname*<br/>
Wskaźnik do nazwy obiektu indeksu, do wyszukiwania według nazwy.

### <a name="remarks"></a>Uwagi

Jedna wersja funkcji umożliwia wyszukywę indeksu według jego pozycji w kolekcji. Druga wersja umożliwia wyszukywanie indeksu według nazwy.

Aby uzyskać opis zwróconych informacji, zobacz [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) struktury. Ta struktura ma elementy, które odpowiadają elementom informacji wymienionych powyżej w opisie *dwInfoOptions*. Gdy poprosisz o informacje na jednym poziomie, otrzymujesz informacje o wcześniejszych poziomach.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość atrybutów" w Pomocy DAO.

## <a name="cdaorecordsetgetlastmodifiedbookmark"></a><a name="getlastmodifiedbookmark"></a>CDaoRecordset::GetLastModifiedBookmark

Wywołanie tej funkcji elementu członkowskiego, aby pobrać zakładkę ostatnio dodanego lub zaktualizowanego rekordu.

```
COleVariant GetLastModifiedBookmark();
```

### <a name="return-value"></a>Wartość zwracana

Zawiera `COleVariant` zakładkę, która wskazuje ostatnio dodany lub zmieniony rekord.

### <a name="remarks"></a>Uwagi

Gdy obiekt zestaw rekordów jest tworzony lub otwierany, każdy z jego rekordów ma już unikatową zakładkę, jeśli je obsługuje. Wywołanie [GetBookmark,](#getbookmark) aby ustalić, czy zestaw rekordów obsługuje zakładki. Jeśli plik recordset nie obsługuje zakładek, a `CDaoException` jest generowany.

Po dodaniu rekordu pojawia się on na końcu rekordu i nie jest bieżącym rekordem. Aby nowy rekord był `GetLastModifiedBookmark` bieżący, `SetBookmark` zadzwoń, a następnie zadzwoń, aby powrócić do nowo dodanego rekordu.

Aby uzyskać powiązane informacje, zobacz temat "LastModified Property" w Pomocy DAO.

## <a name="cdaorecordsetgetlockingmode"></a><a name="getlockingmode"></a>CDaoRecordset::GetLockingMode

Wywołanie tej funkcji elementu członkowskiego, aby określić typ blokowania w życie dla pliku recordset.

```
BOOL GetLockingMode();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli typ blokowania jest pesymistyczny, w przeciwnym razie 0 dla optymistycznego blokowania rekordu.

### <a name="remarks"></a>Uwagi

Gdy obowiązuje pesymistyczna blokada, strona danych zawierająca edytowany rekord jest zablokowana natychmiast po wywołaniu funkcji [Edytuj](#edit) element członkowski. Strona jest odblokowywała się po [wywołaniu](#update) funkcji aktualizuj lub [zamknij](#close) element członkowski lub dowolnej operacji Przenieś lub Znajdź.

Gdy obowiązuje blokowanie optymistyczne, strona danych zawierająca rekord jest zablokowana tylko `Update` wtedy, gdy rekord jest aktualizowany za pomocą funkcji elementu członkowskiego.

Podczas pracy ze źródłami danych ODBC tryb blokowania jest zawsze optymistyczny.

Aby uzyskać powiązane informacje, zobacz tematy "LockEdits Właściwość" i "Zachowanie blokowania w aplikacjach wielu użytkowników" w Pomocy DAO.

## <a name="cdaorecordsetgetname"></a><a name="getname"></a>Zestaw CDaoRecordset::GetName

Wywołanie tej funkcji elementu członkowskiego, aby pobrać nazwę pliku recordset.

```
CString GetName();
```

### <a name="return-value"></a>Wartość zwracana

A `CString` zawierający nazwę pliku recordset.

### <a name="remarks"></a>Uwagi

Nazwa tablicy rekordów musi zaczynać się od litery i może zawierać maksymalnie 40 znaków. Może zawierać liczby i znaki podkreślenia, ale nie może zawierać znaków interpunkcyjnych ani spacji.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość nazw" w Pomocy DAO.

## <a name="cdaorecordsetgetparamvalue"></a><a name="getparamvalue"></a>Zestaw CDaoRecordset::GetParamValue

Wywołanie tej funkcji elementu członkowskiego, aby pobrać bieżącą wartość określonego parametru przechowywanego w podstawowym obiekcie DAOParameter.

```
virtual COleVariant GetParamValue(int nIndex);
virtual COleVariant GetParamValue(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Położenie numeryczne parametru w leżącym na nim obiekcie DAOParameter.

*Lpszname*<br/>
Nazwa parametru, którego wartość ma.

### <a name="return-value"></a>Wartość zwracana

Obiekt klasy [COleVariant,](../../mfc/reference/colevariant-class.md) który zawiera wartość parametru.

### <a name="remarks"></a>Uwagi

Można uzyskać dostęp do parametru według nazwy lub jego położenia numerycznego w kolekcji.

Aby uzyskać powiązane informacje, zobacz temat "Obiekt parametrów" w Pomocy DAO.

## <a name="cdaorecordsetgetpercentposition"></a><a name="getpercentposition"></a>Zestaw CDaoRecordset::GetPercentPosition

Podczas pracy z zestawem rekordów typu dynaset lub `GetPercentPosition` migawka, jeśli wywołasz przed pełnym zapełnieniem zestawu rekordów, ilość ruchu jest względna do liczby rekordów, do których dostęp uzyskał dostęp, jak wskazuje wywołanie [GetRecordCount](#getrecordcount).

```
float GetPercentPosition();
```

### <a name="return-value"></a>Wartość zwracana

Liczba z przedziału od 0 do 100, która wskazuje przybliżoną lokalizację bieżącego rekordu w obiekcie zestawu rekordów na podstawie procentu rekordów w tablicy rekordów.

### <a name="remarks"></a>Uwagi

Można przejść do ostatniego rekordu, wywołując [MoveLast,](#movelast) aby ukończyć populację wszystkich rekordów, ale może to zająć znaczną ilość czasu.

Można wywołać `GetPercentPosition` wszystkie trzy typy obiektów tablicy rekordów, w tym tabele bez indeksów. Jednak nie można `GetPercentPosition` wywołać na migawki przewijania tylko do przodu lub na akcesie rekord otwarty z kwerendy przekazującej dla zewnętrznej bazy danych. Jeśli nie ma bieżącego rekordu lub bieżący `CDaoException` rekord został usunięty, jest generowany.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość percentposition" w Pomocy DAO.

## <a name="cdaorecordsetgetrecordcount"></a><a name="getrecordcount"></a>CDaoRecordset::GetRecordCount

Wywołanie tej funkcji elementu członkowskiego, aby dowiedzieć się, ile rekordów w zestaw rekordów zostały dostępne.

```
long GetRecordCount();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę rekordów dostępnych w obiekcie zestawu rekordów.

### <a name="remarks"></a>Uwagi

`GetRecordCount`nie wskazuje, ile rekordów znajduje się w zestawie rekordów typu dynaset lub migawki, dopóki nie zostaną dostępne wszystkie rekordy. To wywołanie funkcji elementu członkowskiego może zająć dużo czasu, aby zakończyć.

Po uzyskaniu dostępu do ostatniego rekordu zwracana jest wartość zwracana, która wskazuje całkowitą liczbę nieusuniętych rekordów w tablicy rekordów. Aby wymusić dostęp do ostatniego `MoveLast` rekordu, należy wywołać funkcję lub `FindLast` element członkowski dla zestawu rekordów. Można również użyć licznika SQL, aby określić przybliżoną liczbę rekordów, które zwróci zapytanie.

Gdy aplikacja usuwa rekordy w zestawie rekordów typu dynaset, wartość zwracana `GetRecordCount` zmniejsza się. Jednak rekordy usunięte przez innych użytkowników `GetRecordCount` nie są odzwierciedlane przez dopóki bieżący rekord nie zostanie umieszczony w usuniętym rekordzie. Jeśli wykonasz transakcję, która wpływa na liczbę rekordów, a następnie wycofasz transakcję, `GetRecordCount` nie będzie odzwierciedlać rzeczywistej liczby pozostałych rekordów.

Zmiany w `GetRecordCount` tabelach źródłowych nie mają wpływu na wartość z zestawy rekordów typu migawki.

Wartość z `GetRecordCount` zestawu rekordów typu tabeli odzwierciedla przybliżoną liczbę rekordów w tabeli i jest natychmiast zmieniana, gdy rekordy tabel są dodawane i usuwane.

A recordset bez rekordów zwraca wartość 0. Podczas pracy z dołączonymi tabelami `GetRecordCount` lub bazami danych ODBC zawsze zwraca - 1. Wywołanie `Requery` funkcji elementu członkowskiego na a `GetRecordCount` recordset resetuje wartość tak, jakby kwerenda została ponownie wykonana.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość RecordCount" w Pomocy DAO.

## <a name="cdaorecordsetgetsql"></a><a name="getsql"></a>Zestaw CDaoRecordset::GetSQL

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać instrukcję SQL, która została użyta do wybrania rekordów zestawie rekordów rekordów podczas jego otwarcia.

```
CString GetSQL() const;
```

### <a name="return-value"></a>Wartość zwracana

A, `CString` który zawiera instrukcję SQL.

### <a name="remarks"></a>Uwagi

Zazwyczaj będzie to instrukcja SQL **SELECT.**

Ciąg zwracany `GetSQL` przez zazwyczaj różni się od dowolnego ciągu, który mógł zostać przekazany do pliku recordset w parametrze *lpszSQL* do funkcji [otwórz](#open) element członkowski. Dzieje się tak, ponieważ zestaw rekordów konstruuje `Open`pełną instrukcję SQL na podstawie tego, do czego został przekazany , co zostało określone za pomocą ClassWizard i co można określić w [m_strFilter](#m_strfilter) i [m_strSort](#m_strsort) elementów członkowskich danych.

> [!NOTE]
> Wywołanie tej funkcji `Open`elementu członkowskiego dopiero po wywołaniu .

Aby uzyskać powiązane informacje, zobacz temat "Właściwość SQL" w Pomocy DAO.

## <a name="cdaorecordsetgettype"></a><a name="gettype"></a>Zestaw CDaoRecordset::GetType

Wywołanie tej funkcji elementu członkowskiego po otwarciu pliku recordset w celu określenia typu obiektu pliku recordset.

```
short GetType();
```

### <a name="return-value"></a>Wartość zwracana

Jedna z następujących wartości wskazująca typ a recordset:

- `dbOpenTable`Aplikuj rekord typu tabeli

- `dbOpenDynaset`Zestaw rekordów typu Dynaset

- `dbOpenSnapshot`Apecie typu migawka

### <a name="remarks"></a>Uwagi

Aby uzyskać powiązane informacje, zobacz temat "Typ właściwości" w Pomocy DAO.

## <a name="cdaorecordsetgetvalidationrule"></a><a name="getvalidationrule"></a>CDaoRecordset::GetValidationRule

Wywołanie tej funkcji elementu członkowskiego, aby określić regułę używaną do sprawdzania poprawności danych.

```
CString GetValidationRule();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt `CString` zawierający wartość, która sprawdza poprawność danych w rekordzie, ponieważ jest zmieniany lub dodawany do tabeli.

### <a name="remarks"></a>Uwagi

Ta reguła jest oparta na tekście i jest stosowana za każdym razem, gdy tabela bazowa jest zmieniana. Jeśli dane nie są legalne, MFC zgłasza wyjątek. Zwrócony komunikat o błędzie jest tekst validationtext właściwości obiektu pola bazowego, jeśli określono, lub tekst wyrażenia określonego przez ValidationRule właściwości obiektu pola źródłowego. Można wywołać [GetValidationText,](#getvalidationtext) aby uzyskać tekst komunikatu o błędzie.

Na przykład pole w rekordzie, które wymaga dnia miesiąca może mieć regułę sprawdzania poprawności, taką jak "DZIEŃ MIĘDZY 1 A 31".

Aby uzyskać powiązane informacje, zobacz temat "ValidationRule Property" w Pomocy DAO.

## <a name="cdaorecordsetgetvalidationtext"></a><a name="getvalidationtext"></a>CDaoRecordset::GetValidationText

Wywołanie tej funkcji elementu członkowskiego, aby pobrać tekst ValidationText właściwości obiektu pola źródłowego.

```
CString GetValidationText();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt `CString` zawierający tekst wiadomości, który jest wyświetlany, jeśli wartość pola nie spełnia reguły sprawdzania poprawności obiektu pola źródłowego.

### <a name="remarks"></a>Uwagi

Aby uzyskać powiązane informacje, zobacz temat "ValidationText Property" w Pomocy DAO.

## <a name="cdaorecordsetisbof"></a><a name="isbof"></a>CDaoRecordset::IsBOF

Wywołanie tej funkcji elementu członkowskiego przed przewinięciem z rekordu do rekordu, aby dowiedzieć się, czy zostały one przed pierwszym rekordem rekordu rekordu.

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość niezerowa, jeśli grupa rekordów nie zawiera żadnych rekordów lub jeśli przewinąłeś do tyłu przed pierwszym rekordem; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Można również `IsBOF` wywołać `IsEOF` wraz z, aby ustalić, czy plik recordset zawiera żadnych rekordów lub jest pusty. Natychmiast po `Open`wywołaniu , jeśli plik `IsBOF` recordset nie zawiera żadnych rekordów, zwraca wartość niezerowa. Po otwarciu pliku recordset, który ma co najmniej jeden `IsBOF` rekord, pierwszym rekordem jest bieżący rekord i zwraca wartość 0.

Jeśli pierwszy rekord jest bieżący `MovePrev`rekord `IsBOF` i wywołanie , następnie zwróci nonzero. Jeśli `IsBOF` zwraca nonzero `MovePrev`i wywołać, wyjątek. Jeśli `IsBOF` zwraca wartość niezerową, bieżący rekord jest niezdefiniowany, a każda akcja wymagająca bieżącego rekordu spowoduje wyjątek.

Wpływ określonych metod `IsBOF` `IsEOF` na ustawienia i ustawienia:

- Wywołanie `Open*` wewnętrznie sprawia, że pierwszy rekord w `MoveFirst`nastawie rekord bieżący przez wywołanie . W związku `Open` z tym wywołanie `IsBOF` pustego zestawu rekordów powoduje i `IsEOF` zwracać nonzero. (Zobacz poniższą tabelę, aby `MoveFirst` uzyskać `MoveLast` zachowanie nieudanego lub wywołaniem).

- Wszystkie operacje Move, które pomyślnie `IsBOF` `IsEOF` zlokalizować rekord spowodować zarówno i zwrócić 0.

- Wywołanie `AddNew` następuje `Update` wywołanie, które pomyślnie wstawia nowy rekord `IsBOF` spowoduje `IsEOF` zwrócić 0, ale tylko wtedy, gdy jest już niezerowy. Stan zawsze `IsEOF` pozostanie niezmieniony. Zgodnie z definicją aparatu bazy danych Microsoft Jet bieżący wskaźnik rekordu pustego pliku znajduje się na końcu pliku, więc każdy nowy rekord jest wstawiany po bieżącym rekordzie.

- Każde `Delete` wywołanie, nawet jeśli usunie jedyny pozostały rekord z aeutu, nie zmieni wartości `IsBOF` lub `IsEOF`.

W tej tabeli przedstawiono, które operacje `IsBOF` /  `IsEOF`przenoszenia są dozwolone z różnymi kombinacjami programu .

||MoveFirst, MoveLast|Moveprev<br /><br /> Przenoszenie < 0|Ruch 0|Movenext<br /><br /> Przenoszenie > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`=niezerowy,<br /><br /> `IsEOF`=0|Dozwolone|Wyjątek|Wyjątek|Dozwolone|
|`IsBOF`=0,<br /><br /> `IsEOF`= niezerowy|Dozwolone|Dozwolone|Wyjątek|Wyjątek|
|Zarówno nonzero|Wyjątek|Wyjątek|Wyjątek|Wyjątek|
|Zarówno 0|Dozwolone|Dozwolone|Dozwolone|Dozwolone|

Zezwolenie move operacji nie oznacza, że operacja pomyślnie zlokalizować rekord. Wskazuje tylko, że próba wykonania określonej move operacji jest dozwolone i nie wygeneruje wyjątek. Wartość funkcji `IsBOF` i `IsEOF` elementów członkowskich może ulec zmianie w wyniku próby przeniesienia.

Wpływ operacji przenoszenia, które nie lokalizują `IsBOF` rekordu `IsEOF` na wartość i ustawienia, jest pokazany w poniższej tabeli.

||Isbof|Iseof|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|Niezerowa|Niezerowa|
|`Move`0|Bez zmian|Bez zmian|
|`MovePrev`, `Move` < 0|Niezerowa|Bez zmian|
|`MoveNext`, `Move` > 0|Bez zmian|Niezerowa|

Aby uzyskać powiązane informacje, zobacz temat "BOF, Właściwości EOF" w Pomocy DAO.

## <a name="cdaorecordsetisdeleted"></a><a name="isdeleted"></a>CDaoRecordset::JestDeletowany

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy bieżący rekord został usunięty.

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>Wartość zwracana

Pozycja niezerowa, jeśli znak rekordów jest umieszczony na usuniętym rekordzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli przewiniesz `IsDeleted` do rekordu i zwróci wartość TRUE (niezerowa), należy przewinąć do innego rekordu, zanim będzie można wykonać inne operacje na macie rekord.

> [!NOTE]
> Nie trzeba sprawdzać usuniętego stanu rekordów w migawkach lub w pasku rekordów typu tabeli. Ponieważ rekordów nie można usunąć z migawki, nie ma potrzeby wywoływania `IsDeleted`. W przypadku zestawy rekordów typu tabeli usunięte rekordy są faktycznie usuwane z tablicy rekordów. Po usunięciu rekordu przez użytkownika, innego użytkownika lub inny w innym zadaniu nie można przewinąć z powrotem do tego rekordu. W związku z tym nie `IsDeleted`ma potrzeby, aby zadzwonić .

Po usunięciu rekordu z zestawu dynaset jest on usuwany z zestawu rekordów i nie można go przewijać z powrotem do tego rekordu. Jeśli jednak rekord w zestawie dynamiki zostanie usunięty przez innego użytkownika lub inny zestaw `IsDeleted` rekordów na podstawie tej samej tabeli, zwróci wartość TRUE podczas późniejszego przewijania do tego rekordu.

Aby uzyskać powiązane informacje, zobacz tematy "Delete Method", "LastModified Property" i "EditMode Property" w Pomocy DAO.

## <a name="cdaorecordsetiseof"></a><a name="iseof"></a>CDaoRecordset::IsEOF

Wywołanie tej funkcji elementu członkowskiego podczas przewijania z rekordu do rekordu, aby dowiedzieć się, czy wyszedłeś poza ostatni rekord rekordu rekordu rekordu.

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli rekord nie zawiera żadnych rekordów lub jeśli przewinął poza ostatni rekord; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Można również `IsEOF` wywołać, aby ustalić, czy plik recordset zawiera żadnych rekordów lub jest pusty. Natychmiast po `Open`wywołaniu , jeśli plik `IsEOF` recordset nie zawiera żadnych rekordów, zwraca wartość niezerowa. Po otwarciu pliku recordset, który ma co najmniej jeden `IsEOF` rekord, pierwszym rekordem jest bieżący rekord i zwraca wartość 0.

Jeśli ostatni rekord jest bieżącym rekordem `IsEOF` podczas wywoływania, `MoveNext`następnie zwróci nonzero. Jeśli `IsEOF` zwraca nonzero `MoveNext`i wywołać, wyjątek. Jeśli `IsEOF` zwraca wartość niezerową, bieżący rekord jest niezdefiniowany, a każda akcja wymagająca bieżącego rekordu spowoduje wyjątek.

Wpływ określonych metod `IsBOF` `IsEOF` na ustawienia i ustawienia:

- Wywołanie `Open` wewnętrznie sprawia, że pierwszy rekord w `MoveFirst`nastawie rekord bieżący przez wywołanie . W związku `Open` z tym wywołanie `IsBOF` pustego zestawu rekordów powoduje i `IsEOF` zwracać nonzero. (Zobacz poniższą tabelę, aby `MoveFirst` uzyskać zachowanie połączenia nie powiodło się).

- Wszystkie operacje Move, które pomyślnie `IsBOF` `IsEOF` zlokalizować rekord spowodować zarówno i zwrócić 0.

- Wywołanie `AddNew` następuje `Update` wywołanie, które pomyślnie wstawia nowy rekord `IsBOF` spowoduje `IsEOF` zwrócić 0, ale tylko wtedy, gdy jest już niezerowy. Stan zawsze `IsEOF` pozostanie niezmieniony. Zgodnie z definicją aparatu bazy danych Microsoft Jet bieżący wskaźnik rekordu pustego pliku znajduje się na końcu pliku, więc każdy nowy rekord jest wstawiany po bieżącym rekordzie.

- Każde `Delete` wywołanie, nawet jeśli usunie jedyny pozostały rekord z aeutu, nie zmieni wartości `IsBOF` lub `IsEOF`.

W tej tabeli przedstawiono, które operacje `IsBOF` /  `IsEOF`przenoszenia są dozwolone z różnymi kombinacjami programu .

||MoveFirst, MoveLast|Moveprev<br /><br /> Przenoszenie < 0|Ruch 0|Movenext<br /><br /> Przenoszenie > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`=niezerowy,<br /><br /> `IsEOF`=0|Dozwolone|Wyjątek|Wyjątek|Dozwolone|
|`IsBOF`=0,<br /><br /> `IsEOF`= niezerowy|Dozwolone|Dozwolone|Wyjątek|Wyjątek|
|Zarówno nonzero|Wyjątek|Wyjątek|Wyjątek|Wyjątek|
|Zarówno 0|Dozwolone|Dozwolone|Dozwolone|Dozwolone|

Zezwolenie move operacji nie oznacza, że operacja pomyślnie zlokalizować rekord. Wskazuje tylko, że próba wykonania określonej move operacji jest dozwolone i nie wygeneruje wyjątek. Wartość funkcji `IsBOF` i `IsEOF` element członkowski może ulec zmianie w wyniku próby przeniesienia.

Wpływ operacji przenoszenia, które nie lokalizują `IsBOF` rekordu `IsEOF` na wartość i ustawienia, jest pokazany w poniższej tabeli.

||Isbof|Iseof|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|Niezerowa|Niezerowa|
|`Move`0|Bez zmian|Bez zmian|
|`MovePrev`, `Move` < 0|Niezerowa|Bez zmian|
|`MoveNext`, `Move` > 0|Bez zmian|Niezerowa|

Aby uzyskać powiązane informacje, zobacz temat "BOF, Właściwości EOF" w Pomocy DAO.

## <a name="cdaorecordsetisfielddirty"></a><a name="isfielddirty"></a>CDaoRecordset::IsFieldDirty

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy określony element członkowski danych pola dynaset został oznaczony jako "brudny" (zmieniony).

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
Wskaźnik do elementu członkowskiego danych pola, którego stan chcesz sprawdzić, lub NULL, aby ustalić, czy którekolwiek z pól są zabrudzone.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli określony element członkowski danych pola jest oznaczony jako zabrudzony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Dane we wszystkich elementach członkowskich danych brudnego pola zostaną przesłane do rekordu w źródle `Update` danych, `CDaoRecordset` gdy bieżący `Edit` `AddNew`rekord zostanie zaktualizowany przez wywołanie funkcji elementu członkowskiego (po wywołaniu lub ). Dzięki tej wiedzy można podjąć dalsze kroki, takie jak odsłanianie elementu członkowskiego danych pola, aby oznaczyć kolumnę, aby nie została zapisana w źródle danych.

`IsFieldDirty`jest wdrażany `DoFieldExchange`za pośrednictwem .

## <a name="cdaorecordsetisfieldnull"></a><a name="isfieldnull"></a>CDaoRecordset::IsFieldNull

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy określony element członkowski danych pola zestaw rekordów został oznaczony jako Null.

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
Wskaźnik do elementu członkowskiego danych pola, którego stan chcesz sprawdzić, lub NULL, aby ustalić, czy którekolwiek z pól ma wartość Null.

### <a name="return-value"></a>Wartość zwracana

Wartość niezerowa, jeśli określony element członkowski danych pola jest oznaczony jako Null; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

(W terminologii bazy danych Null oznacza "bez wartości" i nie jest taka sama jak NULL w języku C++.) Jeśli element członkowski danych pola jest oflagowany jako Null, jest interpretowany jako kolumna bieżącego rekordu, dla której nie ma wartości.

> [!NOTE]
> W niektórych `IsFieldNull` sytuacjach za pomocą może być nieefektywne, jak pokazano w poniższym przykładzie kodu:

[!code-cpp[NVC_MFCDatabase#5](../../mfc/codesnippet/cpp/cdaorecordset-class_5.cpp)]

> [!NOTE]
> Jeśli używasz wiązania rekordu dynamicznego, `CDaoRecordset`bez wyprowadzania z , należy użyć VT_NULL, jak pokazano w przykładzie.

## <a name="cdaorecordsetisfieldnullable"></a><a name="isfieldnullable"></a>CDaoRecordset::IsFieldNullable

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy określony element członkowski danych pola jest "nullable" (można ustawić na wartość Null; C++ NULL nie jest taki sam jak Null, co w terminologii bazy danych oznacza "nie mając żadnej wartości").

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
Wskaźnik do elementu członkowskiego danych pola, którego stan chcesz sprawdzić, lub NULL, aby ustalić, czy którekolwiek z pól ma wartość Null.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli określony element członkowski danych pola może być null; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pole, które nie może być null musi mieć wartość. Jeśli spróbujesz ustawić takie pole na Null podczas dodawania lub aktualizowania rekordu, `Update` źródło danych odrzuca dodawanie lub aktualizację i zgłasza wyjątek. Wyjątek występuje, `Update`gdy dzwonisz `SetFieldNull`, a nie podczas wywoływania .

## <a name="cdaorecordsetisopen"></a><a name="isopen"></a>CDaoRecordset::IsOpen

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy plik recordset jest otwarty.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Wartość zwracana

Opcja niezerowa, jeśli funkcja `Open` `Requery` obiektu lub elementu członkowskiego jest wcześniej wywoływana, a plan rekordów nie został zamknięty; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

## <a name="cdaorecordsetm_bcheckcachefordirtyfields"></a><a name="m_bcheckcachefordirtyfields"></a>CDaoRecordset::m_bCheckCacheForDirtyFields

Zawiera flagę wskazującą, czy pola buforowane są automatycznie oznaczane jako zabrudzone (zmienione) i Null.

### <a name="remarks"></a>Uwagi

Flaga domyślnie true. Ustawienie w tym element członkowski danych kontroluje cały mechanizm podwójnego buforowania. Jeśli flaga zostanie ustawiona na WARTOŚĆ TRUE, można wyłączyć buforowanie na zasadzie "pole po polu" przy użyciu mechanizmu DFX. Jeśli ustawisz flagę na `SetFieldDirty` FAŁSZ, musisz zadzwonić i `SetFieldNull` siebie.

Ustaw ten element `Open`członkowski danych przed wywołaniem . Mechanizm ten jest przede wszystkim dla łatwości użytkowania. Wydajność może być wolniejsza z powodu podwójnego buforowania pól w miarę wysuwania zmian.

## <a name="cdaorecordsetm_nfields"></a><a name="m_nfields"></a>CDaoRecordset::m_nFields

Zawiera liczbę elementów członkowskich danych pól w klasie zestawu rekordów oraz liczbę kolumn wybranych przez zestaw rekordów ze źródła danych.

### <a name="remarks"></a>Uwagi

Konstruktor dla klasy zestawu rekordów musi zainicjować `m_nFields` z poprawną liczbą pól statycznie powiązanych. ClassWizard zapisuje tę inicjację dla Ciebie, gdy używasz go do deklarowania klasy pliku recordset. Można również napisać go ręcznie.

Struktura używa tego numeru do zarządzania interakcją między elementami członkowskich danych pola i odpowiednimi kolumnami bieżącego rekordu w źródle danych.

> [!NOTE]
> Numer ten musi odpowiadać liczbie kolumn `DoFieldExchange` wyjściowych zarejestrowanych po wywołaniu `SetFieldType` z parametrem `CDaoFieldExchange::outputColumn`.

Kolumny można wiązać dynamicznie `CDaoRecordset::GetFieldValue` za `CDaoRecordset::SetFieldValue`pomocą i . Jeśli to zrobisz, nie trzeba zwiększać liczby, `m_nFields` aby odzwierciedlić liczbę `DoFieldExchange` wywołań funkcji DFX w funkcji członkowskiej.

## <a name="cdaorecordsetm_nparams"></a><a name="m_nparams"></a>CDaoRecordset::m_nParams

Zawiera liczbę elementów członkowskich danych parametrów w klasie zestawu rekordów — liczbę parametrów przekazanych wraz z kwerendą zestawu rekordów.

### <a name="remarks"></a>Uwagi

Jeśli klasa zestawu rekordów ma żadnych elementów członkowskich danych parametrów, konstruktor dla klasy musi zainicjować *m_nParams* z poprawną liczbą. Wartość *domyślna wartość m_nParams* wynosi 0. W przypadku dodawania elementów członkowskich danych parametrów — które należy wykonać ręcznie — należy również ręcznie dodać inicjalizację w konstruktorze klasy, aby odzwierciedlić liczbę parametrów (które muszą być co najmniej tak duże, jak liczba symboli zastępczych '' w *ciągu m_strFilter* lub *m_strSort).*

Struktura używa tej liczby, gdy parametryzuje kwerendę zestawu rekordów.

> [!NOTE]
> Numer ten musi odpowiadać liczbie "params" `DoFieldExchange` zarejestrowanych `SetFieldType` po `CFieldExchange::param`wywołaniu z parametrem .

Aby uzyskać powiązane informacje, zobacz temat "Obiekt parametrów" w Pomocy DAO.

## <a name="cdaorecordsetm_pdaorecordset"></a><a name="m_pdaorecordset"></a>CDaoRecordset::m_pDAORecordset

Zawiera wskaźnik do interfejsu OLE dla obiektu dao `CDaoRecordset` recordset leżącego u podstaw obiektu.

### <a name="remarks"></a>Uwagi

Użyj tego wskaźnika, jeśli chcesz uzyskać bezpośredni dostęp do interfejsu DAO.

Aby uzyskać powiązane informacje, zobacz temat "Obiekt tablicy rekordów" w Pomocy DAO.

## <a name="cdaorecordsetm_pdatabase"></a><a name="m_pdatabase"></a>CDaoRecordset::m_pDatabase

Zawiera wskaźnik do `CDaoDatabase` obiektu, za pomocą którego zestaw rekordów jest połączony ze źródłem danych.

### <a name="remarks"></a>Uwagi

Ta zmienna jest ustawiona na dwa sposoby. Zazwyczaj wskaźnik jest przekazywać do `CDaoDatabase` już otwartego obiektu podczas konstruowania obiektu pliku recordset. Jeśli zamiast tego przekażesz wartość NULL, `CDaoRecordset` utworzy `CDaoDatabase` obiekt i otworzy go. W obu przypadkach `CDaoRecordset` przechowuje wskaźnik w tej zmiennej.

Zwykle nie trzeba bezpośrednio używać wskaźnika przechowywanego w `m_pDatabase`pliku . Jeśli jednak piszesz własne `CDaoRecordset`rozszerzenia, może być konieczne użycie wskaźnika. Na przykład może być potrzebny wskaźnik, `CDaoException`jeśli rzucisz własne (s).

Aby uzyskać powiązane informacje, zobacz temat "Obiekt bazy danych" w Pomocy DAO.

## <a name="cdaorecordsetm_strfilter"></a><a name="m_strfilter"></a>CDaoRecordset::m_strFilter

Zawiera ciąg, który jest używany do konstruowania **klauzuli WHERE** instrukcji SQL.

### <a name="remarks"></a>Uwagi

Nie zawiera słowa zastrzeżonego **WHERE** do filtrowania pliku recordset. Użycie tego elementu członkowskiego danych nie ma zastosowania do zestawów rekordów typu tabeli. Użycie nie `m_strFilter` ma wpływu podczas otwierania `CDaoQueryDef` pliku recordset za pomocą wskaźnika.

Podczas filtrowania pól zawierających daty należy używać formatu daty stanów Zjednoczonych (miesiąc-dzień- rok), nawet jeśli aparat bazy danych microsoft jet nie jest używany w wersji amerykańskiej; w przeciwnym razie dane mogą nie być filtrowane zgodnie z oczekiwaniami.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość filtrowania" w Pomocy DAO.

## <a name="cdaorecordsetm_strsort"></a><a name="m_strsort"></a>CDaoRecordset::m_strSort

Zawiera ciąg zawierający klauzulę **ORDERBY** instrukcji SQL bez słów zastrzeżonych **ORDERBY**.

### <a name="remarks"></a>Uwagi

Można sortować na dynaset- i migawki typu recordset obiektów.

Nie można sortować obiektów typu table recordset. Aby określić kolejność sortowania zestawu rekordów typu tabeli, należy wywołać polecenie [SetCurrentIndex](#setcurrentindex).

Użycie *m_strSort* nie ma wpływu podczas otwierania aktuijów za pomocą wskaźnika. `CDaoQueryDef`

Aby uzyskać powiązane informacje, zobacz temat "Sortowanie właściwości" w Pomocy DAO.

## <a name="cdaorecordsetmove"></a><a name="move"></a>Zestaw CDaoRecordset::Przenieś

Wywołanie tej funkcji elementu członkowskiego, aby umieścić rekordy *lRows* records z bieżącego rekordu.

```
virtual void Move(long lRows);
```

### <a name="parameters"></a>Parametry

*lRows ( lrows )*<br/>
Liczba rekordów do przodu lub do tyłu. Wartości dodatnie poruszają się do przodu, pod koniec pliku recordset. Wartości ujemne przesuwają się do tyłu, w kierunku początku.

### <a name="remarks"></a>Uwagi

Można poruszać się do przodu lub do tyłu. `Move( 1 )`odpowiada `MoveNext`i `Move( -1 )` odpowiada . `MovePrev`

> [!CAUTION]
> Wywołanie `Move` dowolnej z funkcji zgłasza wyjątek, jeśli plik recordset nie ma rekordów. Ogólnie rzecz biorąc `IsBOF` `IsEOF` wywołać zarówno i przed Move operacji, aby ustalić, czy rekord ma żadnych rekordów. Po `Open` wywołaniu `Requery`lub , `IsBOF` `IsEOF`zadzwoń albo lub .

> [!NOTE]
> Jeśli przewinąłeś poza początek lub koniec `IsBOF` pliku `IsEOF` recordset ( lub `Move` zwracasz `CDaoException`wartość niezerową), wywołanie jest rzutem pliku .

> [!NOTE]
> Jeśli wywołasz dowolną `Move` z funkcji, gdy bieżący rekord jest aktualizowany lub dodawany, aktualizacje zostaną utracone bez ostrzeżenia.

Po wywołaniu `Move` migawki przewijania tylko do przodu, *lRows* parametr musi być dodatnią liczebną całkowitej i zakładki nie są dozwolone, więc można przejść tylko do przodu.

Aby nawiązać pierwszy, ostatni, następny lub poprzedni rekord w nastawie rekordu bieżącego, `MoveFirst`wywołanie funkcji `MoveLast`, `MoveNext`, lub `MovePrev` elementu członkowskiego.

Aby uzyskać powiązane informacje, zobacz tematy "Move Method" i "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" w Pomocy DAO.

## <a name="cdaorecordsetmovefirst"></a><a name="movefirst"></a>Zestaw CDaoRecordset::MoveFirst

Wywołanie tej funkcji elementu członkowskiego, aby pierwszy rekord w pliku recordset (jeśli istnieje) bieżący rekord.

```cpp
void MoveFirst();
```

### <a name="remarks"></a>Uwagi

Nie trzeba dzwonić `MoveFirst` natychmiast po otwarciu pliku recordset. W tym czasie pierwszy rekord (jeśli istnieje) jest automatycznie bieżącym rekordem.

> [!CAUTION]
> Wywołanie `Move` dowolnej z funkcji zgłasza wyjątek, jeśli plik recordset nie ma rekordów. Ogólnie rzecz biorąc `IsBOF` `IsEOF` wywołać zarówno i przed Move operacji, aby ustalić, czy rekord ma żadnych rekordów. Po `Open` wywołaniu `Requery`lub , `IsBOF` `IsEOF`zadzwoń albo lub .

> [!NOTE]
> Jeśli wywołasz dowolną `Move` z funkcji, gdy bieżący rekord jest aktualizowany lub dodawany, aktualizacje zostaną utracone bez ostrzeżenia.

Funkcje `Move` można przenosić z rekordu do rekordu bez stosowania warunku. Operacje Znajdź można znaleźć, aby zlokalizować rekordy w obiekcie zestawu rekordów typu dynaset lub snapshot, które spełniają określony warunek. Aby zlokalizować rekord w obiekcie tablicy `Seek`rekordów, należy wywołać polecenie .

Jeśli plik recordset odwołuje się do tablicy rekordów, ruch następuje po bieżącym indeksie tabeli. Bieżący indeks można ustawić przy użyciu właściwości Index leżącego u podstaw obiektu DAO. Jeśli nie ustawisz bieżącego indeksu, kolejność zwracanych rekordów jest niezdefiniowana.

Jeśli wywołasz `MoveLast` obiekt pliku recordset na podstawie kwerendy SQL lub querydef, kwerenda jest zmuszony do zakończenia i obiekt pliku recordset jest w pełni wypełniony.

Nie można `MoveFirst` wywołać lub element `MovePrev` członkowski funkcji z migawki przewijania tylko do przodu.

Aby przenieść położenie bieżącego rekordu w obiekcie zestawu rekordów określoną `Move`liczbę rekordów do przodu lub do tyłu, zadzwoń .

Aby uzyskać powiązane informacje, zobacz tematy "Move Method" i "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" w Pomocy DAO.

## <a name="cdaorecordsetmovelast"></a><a name="movelast"></a>Zestaw CDaoRecordset::MoveLast

Wywołanie tej funkcji elementu członkowskiego, aby ostatni rekord (jeśli istnieje) w pliku recordset bieżącego rekordu.

```cpp
void MoveLast();
```

### <a name="remarks"></a>Uwagi

> [!CAUTION]
> Wywołanie `Move` dowolnej z funkcji zgłasza wyjątek, jeśli plik recordset nie ma rekordów. Ogólnie rzecz biorąc `IsBOF` `IsEOF` wywołać zarówno i przed Move operacji, aby ustalić, czy rekord ma żadnych rekordów. Po `Open` wywołaniu `Requery`lub , `IsBOF` `IsEOF`zadzwoń albo lub .

> [!NOTE]
> Jeśli wywołasz dowolną `Move` z funkcji, gdy bieżący rekord jest aktualizowany lub dodawany, aktualizacje zostaną utracone bez ostrzeżenia.

Funkcje `Move` można przenosić z rekordu do rekordu bez stosowania warunku. Operacje Znajdź można znaleźć, aby zlokalizować rekordy w obiekcie zestawu rekordów typu dynaset lub snapshot, które spełniają określony warunek. Aby zlokalizować rekord w obiekcie tablicy `Seek`rekordów, należy wywołać polecenie .

Jeśli plik recordset odwołuje się do tablicy rekordów, ruch następuje po bieżącym indeksie tabeli. Bieżący indeks można ustawić przy użyciu właściwości Index leżącego u podstaw obiektu DAO. Jeśli nie ustawisz bieżącego indeksu, kolejność zwracanych rekordów jest niezdefiniowana.

Jeśli wywołasz `MoveLast` obiekt pliku recordset na podstawie kwerendy SQL lub querydef, kwerenda jest zmuszony do zakończenia i obiekt pliku recordset jest w pełni wypełniony.

Aby przenieść położenie bieżącego rekordu w obiekcie zestawu rekordów określoną `Move`liczbę rekordów do przodu lub do tyłu, zadzwoń .

Aby uzyskać powiązane informacje, zobacz tematy "Move Method" i "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" w Pomocy DAO.

## <a name="cdaorecordsetmovenext"></a><a name="movenext"></a>Zestaw CDaoRecordset::MoveNext

Wywołanie tej funkcji elementu członkowskiego, aby następny rekord w pliku recordset bieżącego rekordu.

```cpp
void MoveNext();
```

### <a name="remarks"></a>Uwagi

Zaleca się wywołanie `IsBOF` przed podjęciem próby przejścia do poprzedniego rekordu. Wywołanie `MovePrev` spowoduje rzut `CDaoException` `IsBOF` jeśli zwraca nonzero, wskazując, że masz już przewijane przed pierwszym rekordem lub że żadne rekordy nie zostały wybrane przez plik recordset.

> [!CAUTION]
> Wywołanie `Move` dowolnej z funkcji zgłasza wyjątek, jeśli plik recordset nie ma rekordów. Ogólnie rzecz biorąc `IsBOF` `IsEOF` wywołać zarówno i przed Move operacji, aby ustalić, czy rekord ma żadnych rekordów. Po `Open` wywołaniu `Requery`lub , `IsBOF` `IsEOF`zadzwoń albo lub .

> [!NOTE]
> Jeśli wywołasz dowolną `Move` z funkcji, gdy bieżący rekord jest aktualizowany lub dodawany, aktualizacje zostaną utracone bez ostrzeżenia.

Funkcje `Move` można przenosić z rekordu do rekordu bez stosowania warunku. Operacje Znajdź można znaleźć, aby zlokalizować rekordy w obiekcie zestawu rekordów typu dynaset lub snapshot, które spełniają określony warunek. Aby zlokalizować rekord w obiekcie tablicy `Seek`rekordów, należy wywołać polecenie .

Jeśli plik recordset odwołuje się do tablicy rekordów, ruch następuje po bieżącym indeksie tabeli. Bieżący indeks można ustawić przy użyciu właściwości Index leżącego u podstaw obiektu DAO. Jeśli nie ustawisz bieżącego indeksu, kolejność zwracanych rekordów jest niezdefiniowana.

Aby przenieść położenie bieżącego rekordu w obiekcie zestawu rekordów określoną `Move`liczbę rekordów do przodu lub do tyłu, zadzwoń .

Aby uzyskać powiązane informacje, zobacz tematy "Move Method" i "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" w Pomocy DAO.

## <a name="cdaorecordsetmoveprev"></a><a name="moveprev"></a>Zestaw CDaoRecordset::MovePrev

Wywołanie tej funkcji elementu członkowskiego, aby poprzedni rekord w pliku recordset bieżącego rekordu.

```cpp
void MovePrev();
```

### <a name="remarks"></a>Uwagi

Zaleca się wywołanie `IsBOF` przed podjęciem próby przejścia do poprzedniego rekordu. Wywołanie `MovePrev` spowoduje rzut `CDaoException` `IsBOF` jeśli zwraca nonzero, wskazując, że masz już przewijane przed pierwszym rekordem lub że żadne rekordy nie zostały wybrane przez plik recordset.

> [!CAUTION]
> Wywołanie `Move` dowolnej z funkcji zgłasza wyjątek, jeśli plik recordset nie ma rekordów. Ogólnie rzecz biorąc `IsBOF` `IsEOF` wywołać zarówno i przed Move operacji, aby ustalić, czy rekord ma żadnych rekordów. Po `Open` wywołaniu `Requery`lub , `IsBOF` `IsEOF`zadzwoń albo lub .

> [!NOTE]
> Jeśli wywołasz dowolną `Move` z funkcji, gdy bieżący rekord jest aktualizowany lub dodawany, aktualizacje zostaną utracone bez ostrzeżenia.

Funkcje `Move` można przenosić z rekordu do rekordu bez stosowania warunku. Operacje Znajdź można znaleźć, aby zlokalizować rekordy w obiekcie zestawu rekordów typu dynaset lub snapshot, które spełniają określony warunek. Aby zlokalizować rekord w obiekcie tablicy `Seek`rekordów, należy wywołać polecenie .

Jeśli plik recordset odwołuje się do tablicy rekordów, ruch następuje po bieżącym indeksie tabeli. Bieżący indeks można ustawić przy użyciu właściwości Index leżącego u podstaw obiektu DAO. Jeśli nie ustawisz bieżącego indeksu, kolejność zwracanych rekordów jest niezdefiniowana.

Nie można `MoveFirst` wywołać lub element `MovePrev` członkowski funkcji z migawki przewijania tylko do przodu.

Aby przenieść położenie bieżącego rekordu w obiekcie zestawu rekordów określoną `Move`liczbę rekordów do przodu lub do tyłu, zadzwoń .

Aby uzyskać powiązane informacje, zobacz tematy "Move Method" i "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" w Pomocy DAO.

## <a name="cdaorecordsetopen"></a><a name="open"></a>CDaoRecordset::Otwórz

Aby pobrać rekordy dla pliku recordset, należy wywołać tę funkcję członkow.

```
virtual void Open(
    int nOpenType = AFX_DAO_USE_DEFAULT_TYPE,
    LPCTSTR lpszSQL = NULL,
    int nOptions = 0);

virtual void Open(
    CDaoTableDef* pTableDef,
    int nOpenType = dbOpenTable,
    int nOptions = 0);

virtual void Open(
    CDaoQueryDef* pQueryDef,
    int nOpenType = dbOpenDynaset,
    int nOptions = 0);
```

### <a name="parameters"></a>Parametry

*nOtwartyty*<br/>
Jedna z następujących wartości:

- `dbOpenDynaset`Zestaw rekordów typu dynaset z dwukierunkowym przewijaniem. Domyślnie włączone.

- `dbOpenTable`Aplikaty typu tabela z przewijaniem dwukierunkowym.

- `dbOpenSnapshot`A snapshot-type recordset with dwukierunkowe przewijanie.

*Lpszsql*<br/>
Wskaźnik ciągu zawierający jedną z następujących czynności:

- Wskaźnik NULL.

- Nazwa jednego lub więcej tabledefs i/lub querydefs (rozdzielone przecinkami).

- Instrukcja SQL **SELECT** (opcjonalnie z klauzulą SQL **WHERE** lub **ORDERBY).**

- Kwerenda przekazywalna.

*nOpcje*<br/>
Co najmniej jedna z poniższych opcji. Wartość domyślna to 0. Dopuszczalne są następujące wartości:

- `dbAppendOnly`Można dołączać tylko nowe rekordy (tylko zestaw rekordów typu dynaset). Ta opcja oznacza dosłownie, że rekordy mogą być dołączane tylko. Klasy bazy danych MFC ODBC mają opcję tylko do dołączania, która umożliwia pobieranie i dołączanie rekordów.

- `dbForwardOnly`Plik recordset jest migawką przewijaną tylko do przodu.

- `dbSeeChanges`Wygeneruj wyjątek, jeśli inny użytkownik zmienia edytowane dane.

- `dbDenyWrite`Inni użytkownicy nie mogą modyfikować ani dodawać rekordów.

- `dbDenyRead`Inni użytkownicy nie mogą wyświetlać rekordów (tylko tablica rekordów).

- `dbReadOnly`Można wyświetlać tylko rekordy; inni użytkownicy mogą je modyfikować.

- `dbInconsistent`Niespójne aktualizacje są dozwolone (tylko zestaw rekordów typu dynaset).

- `dbConsistent`Dozwolone są tylko spójne aktualizacje (tylko zestaw rekordów typu dynaset).

> [!NOTE]
> Stałe `dbConsistent` i `dbInconsistent` wzajemnie się wykluczają. Można użyć jednego lub drugiego, ale nie obu `Open`w danym wystąpieniu programu .

*pTableDef (Niem.*<br/>
Wskaźnik do obiektu [CDaoTableDef.](../../mfc/reference/cdaotabledef-class.md) Ta wersja jest prawidłowa tylko dla rekordów typu tabeli. Podczas korzystania z `CDaoDatabase` tej opcji wskaźnik `CDaoRecordset` używany do konstruowania nie jest używany; zamiast bazy danych, w którym znajduje się tabledef jest używany.

*pQueryDef (niem.*<br/>
Wskaźnik do obiektu [CDaoQueryDef.](../../mfc/reference/cdaoquerydef-class.md) Ta wersja jest prawidłowa tylko dla zestawów rekordów typu dynaset i migawki. Podczas korzystania z `CDaoDatabase` tej opcji wskaźnik `CDaoRecordset` używany do konstruowania nie jest używany; zamiast bazy danych, w którym znajduje się querydef jest używany.

### <a name="remarks"></a>Uwagi

Przed `Open`wywołaniem należy skonstruować obiekt pliku recordset. Istnieje kilka sposobów, aby to zrobić:

- Podczas konstruowania obiektu obiektu pliku recordset należy przekazać wskaźnik do `CDaoDatabase` obiektu, który jest już otwarty.

- Podczas konstruowania obiektu obiektu pliku recordset należy przekazać wskaźnik do `CDaoDatabase` obiektu, który nie jest otwarty. Plan recordset `CDaoDatabase` otwiera obiekt, ale nie zamyka go po zamknięciu obiektu.

- Podczas konstruowania obiektu obiektu pliku recordset należy przekazać wskaźnik NULL. Obiekt zestawów `GetDefaultDBName` rekordów wywołuje nazwę programu Microsoft Access . MDB, aby otworzyć. Następnie akces `CDaoDatabase` otwiera obiekt i zachowuje go jako otwarty tak długo, jak długo jest otwarty. Po wywołaniu `Close` na recordset, `CDaoDatabase` obiekt jest również zamknięty.

    > [!NOTE]
    >  Gdy zestaw rekordów `CDaoDatabase` otworzy obiekt, otworzy źródło danych z nierozłącznym dostępem.

Dla `Open` wersji, która używa parametru *lpszSQL,* po otwarciu pliku records można pobrać rekordy na jeden z kilku sposobów. Pierwszą opcją jest mieć funkcje `DoFieldExchange`DFX w pliku . Drugą opcją jest użycie powiązania `GetFieldValue` dynamicznego przez wywołanie funkcji elementu członkowskiego. Opcje te mogą być realizowane oddzielnie lub w połączeniu. Jeśli są one połączone, trzeba będzie przekazać w instrukcji `Open`SQL siebie na wywołanie .

W przypadku korzystania z `Open` drugiej wersji, `CDaoTableDef` w której przekazujesz obiekt, wynikowe kolumny `DoFieldExchange` będą dostępne do powiązania za pośrednictwem mechanizmu DFX i/lub powiązania dynamicznie za pośrednictwem `GetFieldValue`programu .

> [!NOTE]
> Można wywołać `Open` tylko `CDaoTableDef` przy użyciu obiektu dla zestawy rekordów typu tabeli.

Podczas korzystania `Open` z trzeciej wersji, `CDaoQueryDef` w której przekazujesz w obiekcie, ta kwerenda zostanie wykonana, `DoFieldExchange` a wynikowe kolumny będą dostępne do `GetFieldValue`powiązania za pośrednictwem mechanizmu DFX i/lub powiązania dynamicznie za pośrednictwem programu .

> [!NOTE]
> Można wywołać `Open` tylko `CDaoQueryDef` przy użyciu obiektu dla dynaset typu i migawki typu recordsets.

Dla pierwszej wersji, `Open` która `lpszSQL` używa parametru, rekordy są wybierane na podstawie kryteriów przedstawionych w poniższej tabeli.

|Wartość parametru `lpszSQL`|Wybrane rekordy są określane przez|Przykład|
|--------------------------------------|----------------------------------------|-------------|
|NULL|Ciąg zwrócony `GetDefaultSQL`przez .||
|Oddzielona przecinkami lista co najmniej jednej nazwy tabledefs i/lub querydef.|Wszystkie kolumny reprezentowane `DoFieldExchange`w pliku .|`"Customer"`|
|**WYBIERZ** listę kolumn **FROM z** listy tabeli|Określone kolumny z określonych tabledef(s) i/lub querydef(s).|`"SELECT CustId, CustName`<br /><br /> `FROM Customer"`|

Zwykle procedura jest przekazać `Open`NULL do ; w takim `Open` przypadku `GetDefaultSQL`wywołanie , nadrzędna funkcja elementu członkowskiego, który `CDaoRecordset`ClassWizard generuje podczas tworzenia klasy pochodnej. Ta wartość daje tabledef(s) i/lub querydef name(s) określone w ClassWizard. Zamiast tego można określić inne informacje w parametrze *lpszSQL.*

`Open` Cokolwiek przekażesz, konstruuje końcowy ciąg SQL dla kwerendy (ciąg może mieć klauzule SQL **WHERE** i **ORDERBY** dołączone do ciągu *lpszSQL,* który przeszedłeś), a następnie wykonuje kwerendę. Można sprawdzić skonstruowany ciąg, `GetSQL` wywołując `Open`po wywołaniu .

Elementy członkowskie danych pól klasy zestaw rekordów są powiązane z kolumnami wybranych danych. Jeśli wszystkie rekordy są zwracane, pierwszy rekord staje się bieżącym rekordem.

Jeśli chcesz ustawić opcje dla zestawu rekordów, takie jak `m_strSort` `m_strFilter` filtr lub sortowanie, ustaw lub `Open`po skonstruowaniu obiektu zestawu rekordów, ale przed wywołaniem . Jeśli chcesz odświeżyć rekordy w forcie rekordów po `Requery`jego otwarciu, zadzwoń do .

Jeśli wywołasz `Open` zestaw rekordów typu dynaset lub migawka lub jeśli źródło danych odwołuje się do instrukcji SQL lub `dbOpenTable` tabledef reprezentującej dołączoną tabelę, nie można użyć dla argumentu typu; jeśli to zrobisz, MFC zgłasza wyjątek. Aby ustalić, czy obiekt tabledef reprezentuje dołączoną tabelę, należy utworzyć obiekt [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) i wywołać jego funkcję elementu członkowskiego [GetConnect.](../../mfc/reference/cdaotabledef-class.md#getconnect)

Użyj `dbSeeChanges` flagi, jeśli chcesz podlewki zmian wprowadzonych przez innego użytkownika lub innego programu na komputerze podczas edycji lub usuwania tego samego rekordu. Na przykład jeśli dwóch użytkowników rozpocząć edycję tego samego `Update` rekordu, pierwszy użytkownik do wywołania funkcji elementu członkowskiego powiedzie się. Gdy `Update` jest wywoływana przez `CDaoException` drugiego użytkownika, a jest generowany. Podobnie jeśli drugi użytkownik próbuje `Delete` wywołać, aby usunąć rekord i został już zmieniony `CDaoException` przez pierwszego użytkownika, występuje.

Zazwyczaj jeśli użytkownik pobiera `CDaoException` to podczas aktualizowania, kod należy odświeżyć zawartość pól i pobrać nowo zmodyfikowane wartości. Jeśli wyjątek występuje w procesie usuwania, kod może wyświetlić nowe dane rekordu dla użytkownika i komunikat wskazujący, że dane zostały niedawno zmienione. W tym momencie kod można zażądać potwierdzenia, że użytkownik nadal chce usunąć rekord.

> [!TIP]
> Użyj opcji przewijania tylko`dbForwardOnly`do przodu ( ), aby zwiększyć wydajność, gdy aplikacja tworzy pojedynczy przebieg za pośrednictwem zestawu rekordów otwartego ze źródła danych ODBC.

Aby uzyskać powiązane informacje, zobacz temat "OpenRecordset Method" w Pomocy DAO.

## <a name="cdaorecordsetrequery"></a><a name="requery"></a>CDaoRecordset::Kwerenda requery

Wywołanie tej funkcji elementu członkowskiego, aby odbudować (odświeżyć) rekord.

```
virtual void Requery();
```

### <a name="remarks"></a>Uwagi

Jeśli wszystkie rekordy są zwracane, pierwszy rekord staje się bieżącym rekordem.

Aby zestaw rekordów odzwierciedlał dodatki i usunięcia dokonane przez użytkownika lub innych użytkowników w źródle danych, `Requery`należy odbudować zestaw rekordów, wywołując program . Jeśli zestaw rekordów jest zestawem dynaset, automatycznie odzwierciedla aktualizacje, które użytkownik lub inni użytkownicy dokonują do istniejących rekordów (ale nie dodatków). Jeśli plik recordset jest migawką, należy wywołać, `Requery` aby odzwierciedlić zmiany wprowadzone przez innych użytkowników, a także uzupełnienia i usunięcia.

W przypadku zestawu dynaset lub `Requery` migawki wywołaj w dowolnym momencie, gdy chcesz odbudować zestaw rekordów przy użyciu wartości parametrów. Ustaw nowy filtr lub [m_strFilter](#m_strfilter) posortuj, ustawiając m_strFilter `Requery`i [m_strSort](#m_strsort) przed wywołaniem . Ustaw nowe parametry, przypisując nowe wartości `Requery`członkom danych parametrów przed wywołaniem .

Jeśli próba odbudowania pliku recordset zakończy się niepowodzeniem, jest on zamykany. Przed wywołaniem `Requery`można określić, czy rekord może zostać ponowniequerowany, wywołując funkcję elementu członkowskiego [CanRestart.](#canrestart) `CanRestart`nie gwarantuje, `Requery` że się uda.

> [!CAUTION]
> Zadzwoń `Requery` tylko po `Open`wywołaniu .

> [!NOTE]
> Wywołanie [ponownego zapytania](#requery) zmienia zakładki DAO.

Nie można wywołać `Requery` zestawu rekordów typu dynaset lub `CanRestart` migawki, jeśli wywołanie zwraca wartość 0, ani nie można go używać w zestawie rekordów typu tabeli.

Jeśli `IsBOF` zarówno `IsEOF` i zwracaj od `Requery`zera po wywołaniu, kwerenda nie zwróciła żadnych rekordów, a zestaw rekordów nie będzie zawierał żadnych danych.

Aby uzyskać powiązane informacje, zobacz temat "Metoda kwerendy" w Pomocy DAO.

## <a name="cdaorecordsetseek"></a><a name="seek"></a>CDaoRecordset::Szukaj

Wywołanie tej funkcji elementu członkowskiego, aby zlokalizować rekord w obiekcie indexed table-type recordset, który spełnia określone kryteria dla bieżącego indeksu i uczynić ten rekord bieżącym rekordem.

```
BOOL Seek(
    LPCTSTR lpszComparison,
    COleVariant* pKey1,
    COleVariant* pKey2 = NULL,
    COleVariant* pKey3 = NULL);

BOOL Seek(
    LPCTSTR lpszComparison,
    COleVariant* pKeyArray,
    WORD nKeys);
```

### <a name="parameters"></a>Parametry

*lpszComparison*<br/>
Jedno z następujących wyrażeń ciągu: "<", "\<=", "=", ">=" lub ">".

*PKey1 (własn.)*<br/>
Wskaźnik do [COleVariant,](../../mfc/reference/colevariant-class.md) którego wartość odpowiada pierwszepole w indeksie. Wymagany.

*Klawisze2*<br/>
Wskaźnik do, `COleVariant` którego wartość odpowiada drugiemu polu w indeksie, jeśli istnieje. Wartość domyślna to NULL.

*pKey3*<br/>
Wskaźnik do, `COleVariant` którego wartość odpowiada trzeciepole w indeksie, jeśli istnieje. Wartość domyślna to NULL.

*pKeyArray (własówce)*<br/>
Wskaźnik do tablicy wariantów. Rozmiar tablicy odpowiada liczbie pól w indeksie.

*klawisze nKeys*<br/>
Liczba całkowita odpowiadająca rozmiar tablicy, która jest liczbą pól w indeksie.

> [!NOTE]
> Nie należy określać symboli wieloznacznych w kluczach. Symbole wieloznaczne spowoduje, `Seek` że nie zwróci pasujące rekordy.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli pasujące rekordy są znalezione, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj drugiej (tablicowej) `Seek` wersji do obsługi indeksów czterech pól lub więcej.

`Seek`umożliwia wyszukiwanie indeksu o wysokiej wydajności w zestawy rekordów typu tabeli. Bieżący indeks należy ustawić, wywołując przed `SetCurrentIndex` wywołaniem `Seek`. Jeśli indeks identyfikuje nonunique pole klucza `Seek` lub pola, lokalizuje pierwszy rekord, który spełnia kryteria. Jeśli nie ustawisz indeksu, zostanie zgłoszony wyjątek.

Należy zauważyć, że jeśli nie tworzysz pliku `COleVariant` rekordów UNICODE, obiekty muszą być jawnie zadeklarowane ANSI. Można to zrobić za pomocą [COleVariant:::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** forma konstruktora z *vtSrc* ustawiony na `VT_BSTRT` (ANSI) lub za pomocą `COleVariant` funkcji [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** z *vtSrc* ustawiony na `VT_BSTRT`.

Podczas wywoływania `Seek`, należy przekazać jedną lub więcej wartości klucza i\<operator porównania ("<", " =", "=", ">=" lub ">"). `Seek`przeszukuje określone pola kluczy i lokalizuje pierwszy rekord, który spełnia kryteria określone przez *lpszComparison* i *pKey1*. Po znalezieniu zwraca `Seek` wartość niezerowa i powoduje, że rekord jest bieżący. Jeśli `Seek` nie uda się `Seek` zlokalizować dopasowania, zwraca zero, a bieżący rekord jest niezdefiniowany. Podczas korzystania z DAO bezpośrednio, należy jawnie sprawdzić NoMatch właściwości.

Jeśli `lpszComparison` jest "=", ">=" lub ">", `Seek` rozpoczyna się na początku indeksu. Jeśli *lpszComparison* jest "<" lub "<=", `Seek` rozpoczyna się na końcu indeksu i wyszukuje wstecz, chyba że na końcu znajdują się zduplikowane wpisy indeksu. W takim `Seek` przypadku rozpoczyna się od dowolnego wpisu wśród zduplikowanych wpisów indeksu na końcu indeksu.

Nie musi być bieżący rekord podczas `Seek`korzystania .

Aby zlokalizować rekord w zestawie rekordów typu dynaset lub snapshot, który spełnia określony warunek, należy użyć operacji Znajdź. Aby uwzględnić wszystkie rekordy, a nie tylko te, które spełniają określony warunek, użyj operacji Przenieś, aby przejść z rekordu do rekordu.

Nie można `Seek` wywołać dołączonej tabeli dowolnego typu, ponieważ dołączone tabele muszą być otwierane jako zestawy rekordów typu dynaset lub snapshot. Jednak jeśli wywołasz `CDaoDatabase::Open` bezpośrednio otworzyć instalowalną bazę `Seek` danych ISAM, można wywołać na tabelach w tej bazie danych, chociaż wydajność może być niska.

Aby uzyskać powiązane informacje, zobacz temat "Szukaj metody" w Pomocy DAO.

## <a name="cdaorecordsetsetabsoluteposition"></a><a name="setabsoluteposition"></a>CDaoRecordset::SetAbsolutePosition

Ustawia względną liczbę rekordów bieżącego rekordu obiektu zestawu rekordów.

```cpp
void SetAbsolutePosition(long lPosition);
```

### <a name="parameters"></a>Parametry

*lPozycja*<br/>
Odpowiada pozycji porządkowej bieżącego rekordu w zakuł rekordy.

### <a name="remarks"></a>Uwagi

Wywołanie `SetAbsolutePosition` umożliwia umieszczenie bieżącego wskaźnika rekordu do określonego rekordu na podstawie jego położenia porządkowego w zestawie rekordów typu dynaset lub migawki. Bieżący numer rekordu można również określić, dzwoniąc do [getabsolutePosition](#getabsoluteposition).

> [!NOTE]
> Ta funkcja elementu członkowskiego jest prawidłowa tylko dla zestawów rekordów typu dynaset i migawki.

Wartość właściwości AbsolutePosition bazowego obiektu DAO jest oparta na wartości zero; ustawienie 0 odnosi się do pierwszego rekordu w ustawie rekordzie. Ustawienie wartości większej niż liczba wypełnionych rekordów powoduje, że MFC zgłasza wyjątek. Liczbę wypełnionych rekordów w akulicie `GetRecordCount` można określić, wywołując funkcję elementu członkowskiego.

Jeśli bieżący rekord zostanie usunięty, wartość właściwości AbsolutePosition nie jest zdefiniowana, a MFC zgłasza wyjątek, jeśli odwołuje się do niego. Nowe rekordy są dodawane na końcu sekwencji.

> [!NOTE]
> Ta właściwość nie jest przeznaczona do użycia jako numer rekordu zastępczego. Zakładki są nadal zalecanym sposobem zachowania i powrotu do danej pozycji i są jedynym sposobem na umieszczenie bieżącego rekordu we wszystkich typach obiektów znaczników rekordów obsługujących zakładki. W szczególności pozycja danego rekordu zmienia się, gdy rekordy poprzedzające go są usuwane. Nie ma również pewności, że dany rekord będzie miał taką samą pozycję bezwzględną, jeśli znak rekordów zostanie ponownie utworzony, ponieważ kolejność poszczególnych rekordów w zestawie rekordów nie jest gwarantowana, chyba że zostanie utworzona za pomocą instrukcji SQL przy użyciu klauzuli **ORDERBY.**

Aby uzyskać powiązane informacje, zobacz temat "AbsolutePosition Property" w Pomocy DAO.

## <a name="cdaorecordsetsetbookmark"></a><a name="setbookmark"></a>CDaoRecordset::SetBookmark

Wywołanie tej funkcji elementu członkowskiego, aby umieścić rekord w rekordzie zawierającym określoną zakładkę.

```cpp
void SetBookmark(COleVariant varBookmark);
```

### <a name="parameters"></a>Parametry

*varBookmark (znak zdj.*<br/>
A [COleVariant](../../mfc/reference/colevariant-class.md) obiekt zawierający wartość zakładki dla określonego rekordu.

### <a name="remarks"></a>Uwagi

Gdy obiekt pliku recordset jest tworzony lub otwierany, każdy z jego rekordów ma już unikatową zakładkę. Zakładkę bieżącego rekordu można pobrać, `GetBookmark` wywołując i zapisując `COleVariant` wartość w obiekcie. Później można powrócić do tego `SetBookmark` rekordu, wywołując przy użyciu zapisanej wartości zakładki.

> [!NOTE]
> Wywołanie [ponownego zapytania](#requery) zmienia zakładki DAO.

Należy zauważyć, że jeśli nie tworzysz pliku `COleVariant` rekordów UNICODE, obiekt musi być jawnie zadeklarowany ansi. Można to zrobić za pomocą [COleVariant:::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** forma konstruktora z *vtSrc* ustawiony na `VT_BSTRT` (ANSI) lub za pomocą `COleVariant` funkcji [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** z *vtSrc* ustawiony na `VT_BSTRT`.

Aby uzyskać powiązane informacje, zobacz tematy "Właściwość zakładek" i Właściwość do zakładek" w Pomocy DAO.

## <a name="cdaorecordsetsetcachesize"></a><a name="setcachesize"></a>CDaoRecordset::SetCacheSize

Wywołanie tej funkcji elementu członkowskiego, aby ustawić liczbę rekordów, które mają być buforowane.

```cpp
void SetCacheSize(long lSize);
```

### <a name="parameters"></a>Parametry

*lSize (rozmiar)*<br/>
Określa liczbę rekordów. Typowa wartość to 100. Ustawienie 0 wyłącza buforowanie. Ustawienie musi zawierać od 5 do 1200 rekordów. Pamięć podręczna może używać znacznej ilości pamięci.

### <a name="remarks"></a>Uwagi

Pamięć podręczna to miejsce w pamięci lokalnej, w których dane są ostatnio pobierane z serwera w przypadku, gdy dane zostaną ponownie żądane, gdy aplikacja jest uruchomiona. Buforowanie danych zwiększa wydajność aplikacji, która pobiera dane z serwera zdalnego za pośrednictwem obiektów zestawu rekordów typu dynaset. Gdy wymagane są dane, aparat bazy danych Microsoft Jet najpierw sprawdza pamięć podręczną dla żądanych danych, zamiast pobierać je z serwera, co zajmuje więcej czasu. Dane, które nie pochodzą ze źródła danych ODBC nie są zapisywane w pamięci podręcznej.

Każde źródło danych ODBC, takie jak tabela dołączone, może mieć lokalną pamięć podręczną. Aby utworzyć pamięć podręczną, otwórz obiekt zestaw rekordów `SetCacheSize` `SetCacheStart` ze zdalnego źródła `FillCache` danych, zadzwoń do funkcji i członków, a następnie zadzwoń do funkcji elementu członkowskiego lub przejdź przez rekordy za pomocą jednej z operacji Przenieś. Parametr *lSize* funkcji `SetCacheSize` elementu członkowskiego może być oparty na liczbie rekordów, z którymi aplikacja może pracować w tym samym czasie. Na przykład jeśli używasz zestaw rekordów jako źródła danych, które mają być `SetCacheSize` wyświetlane na ekranie, można przekazać *lSize* parametr jako 20 do wyświetlania 20 rekordów w tym samym czasie.

Aby uzyskać powiązane informacje, zobacz temat "CacheSize, CacheStart Properties" w Pomocy DAO.

## <a name="cdaorecordsetsetcachestart"></a><a name="setcachestart"></a>Zestaw CDaoRecordset::SetCacheStart

Wywołanie tej funkcji elementu członkowskiego, aby określić zakładkę pierwszego rekordu w zestawrekordu do buforowania.

```cpp
void SetCacheStart(COleVariant varBookmark);
```

### <a name="parameters"></a>Parametry

*varBookmark (znak zdj.*<br/>
A [COleVariant,](../../mfc/reference/colevariant-class.md) który określa zakładkę pierwszego rekordu w zestaw rekordów do buforowania.

### <a name="remarks"></a>Uwagi

Można użyć wartości zakładki dowolnego rekordu dla parametru `SetCacheStart` *varBookmark* funkcji elementu członkowskiego. Należy utworzyć rekord, który chcesz uruchomić pamięć podręczną z bieżącym rekordem, ustanowić zakładkę dla tego rekordu `SetCacheStart` za pomocą [SetBookmark](#setbookmark)i przekazać wartość zakładki jako parametr funkcji elementu członkowskiego.

Aparat bazy danych Microsoft Jet żąda rekordów w zakresie pamięci podręcznej z pamięci podręcznej i żąda rekordów poza zakresem pamięci podręcznej z serwera.

Rekordy pobrane z pamięci podręcznej nie odzwierciedlają zmian wprowadzonych równocześnie w danych źródłowych przez innych użytkowników.

Aby wymusić aktualizację wszystkich buforowanych danych, należy przekazać parametr *lSize* `SetCacheSize` jako 0, wywołać `SetCacheSize` ponownie z rozmiarem pamięci podręcznej pierwotnie żądane, a następnie wywołać funkcję `FillCache` elementu członkowskiego.

Należy zauważyć, że jeśli nie tworzysz pliku `COleVariant` rekordów UNICODE, obiekt musi być jawnie zadeklarowany ansi. Można to zrobić za pomocą [COleVariant:::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** forma konstruktora z *vtSrc* ustawiony na `VT_BSTRT` (ANSI) lub za pomocą `COleVariant` funkcji [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** z *vtSrc* ustawiony na `VT_BSTRT`.

Aby uzyskać powiązane informacje, zobacz temat CacheSize, CacheStart Properties" w Pomocy DAO.

## <a name="cdaorecordsetsetcurrentindex"></a><a name="setcurrentindex"></a>CDaoRecordset::SetCurrentIndex

Wywołanie tej funkcji elementu członkowskiego, aby ustawić indeks na zestawie rekordów typu tabeli.

```cpp
void SetCurrentIndex(LPCTSTR lpszIndex);
```

### <a name="parameters"></a>Parametry

*lpszIndex*<br/>
Wskaźnik zawierający nazwę indeksu, który ma zostać ustawiony.

### <a name="remarks"></a>Uwagi

Rekordy w tabelach bazowych nie są przechowywane w określonej kolejności. Ustawienie indeksu zmienia kolejność rekordów zwracanych z bazy danych, ale nie wpływa na kolejność przechowywania rekordów. Określony indeks musi być już zdefiniowany. Jeśli spróbujesz użyć obiektu indeksu, który nie istnieje lub jeśli indeks nie jest ustawiony podczas wywoływania [Seek](#seek), MFC zgłasza wyjątek.

Nowy indeks tabeli można utworzyć, wywołując [program CDaoTableDef::CreateIndex](../../mfc/reference/cdaotabledef-class.md#createindex) i dołączając nowy indeks do kolekcji Indeksy podstawowej tabeli, wywołując [rekord CDaoTableDef::Dołącz](../../mfc/reference/cdaotabledef-class.md#append), a następnie ponownie otwierający zbiór rekordów.

Rekordy zwrócone z tablicy rekordów można zamówić tylko przez indeksy zdefiniowane dla podstawowej tabledef. Aby sortować rekordy w innej kolejności, można otworzyć zestaw rekordów typu dynaset lub migawka przy użyciu klauzuli SQL **ORDERBY** przechowywanej w [pliku CDaoRecordset::m_strSort](#m_strsort).

Aby uzyskać powiązane informacje, zobacz temat "Obiekt indeksu" i definicję "bieżący indeks" w Pomocy DAO.

## <a name="cdaorecordsetsetfielddirty"></a><a name="setfielddirty"></a>CDaoRecordset::SetFieldDirty

Wywołanie tej funkcji elementu członkowskiego, aby oznaczyć element członkowski danych pola zestaw rekordów jako zmieniony lub niezmieniony.

```cpp
void SetFieldDirty(
    void* pv,
    BOOL bDirty = TRUE);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
Zawiera adres elementu członkowskiego danych pola w liście rekordów lub wartości NULL. Jeśli null, wszystkie elementy członkowskie danych pola w liście rekordów są oflagowane. (C++ NULL nie jest taki sam jak Null w terminologii bazy danych, co oznacza "bez wartości.")

*bDirty*<br/>
PRAWDA, jeśli element członkowski danych pola ma być oznaczony jako "brudny" (zmieniony). W przeciwnym razie FALSE, jeśli element członkowski danych pola ma być oflagowany jako "czysty" (bez zmian).

### <a name="remarks"></a>Uwagi

Oznaczanie pól jako niezmienionych gwarantuje, że pole nie zostanie zaktualizowane.

Znaki ramowe zmieniły elementy członkowskie danych pól, aby upewnić się, że zostaną one zapisane w rekordzie w źródle danych przez mechanizm wymiany pól rekordu DAO (DFX). Zmiana wartości pola zazwyczaj ustawia pole zabrudzone automatycznie, więc rzadko `SetFieldDirty` trzeba wywołać siebie, ale czasami warto upewnić się, że kolumny będą jawnie aktualizowane lub wstawiane niezależnie od wartości, która znajduje się w polu elementu członkowskiego danych. Mechanizm DFX wykorzystuje również pseudonull. Aby uzyskać więcej informacji, zobacz [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Jeśli mechanizm podwójnego buforowania nie jest używany, zmiana wartości pola nie powoduje automatycznego ustawiania pola jako zabrudzone. W takim przypadku konieczne będzie jawne ustawienie pola jako zabrudzone. Flaga zawarta w [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) steruje automatycznym sprawdzaniem pola.

> [!NOTE]
> Wywołanie tej funkcji członkowskiej dopiero po [wywołaniu Edytuj](#edit) lub [DodajNew](#addnew).

Użycie wartości NULL dla pierwszego argumentu funkcji `outputColumn` spowoduje zastosowanie funkcji do `CDaoFieldExchange`wszystkich pól, a nie pól **param** w pliku . Na przykład wezwanie do

[!code-cpp[NVC_MFCDatabase#6](../../mfc/codesnippet/cpp/cdaorecordset-class_6.cpp)]

ustawi `outputColumn` tylko pola na NULL; **pola param** nie ulegnie to zmniejszyć.

Aby pracować na **param**, należy podać rzeczywisty adres poszczególnych **param,** które chcesz pracować, takich jak:

[!code-cpp[NVC_MFCDatabase#7](../../mfc/codesnippet/cpp/cdaorecordset-class_7.cpp)]

Oznacza to, że nie można ustawić wszystkich pól `outputColumn` **param** na NULL, jak w polach.

`SetFieldDirty`jest wdrażany `DoFieldExchange`za pośrednictwem .

## <a name="cdaorecordsetsetfieldnull"></a><a name="setfieldnull"></a>CDaoRecordset::SetFieldNull

Wywołanie tej funkcji elementu członkowskiego, aby oznaczyć element członkowski danych pola w zbiorze rekordów jako Null (w szczególności nie posiadające wartości) lub jako nie-Null.

```cpp
void SetFieldNull(
    void* pv,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
Zawiera adres elementu członkowskiego danych pola w liście rekordów lub wartości NULL. Jeśli null, wszystkie elementy członkowskie danych pola w liście rekordów są oflagowane. (C++ NULL nie jest taki sam jak Null w terminologii bazy danych, co oznacza "bez wartości.")

*bBull (Angielski)*<br/>
Wartość niezerowa, jeśli element członkowski danych pola ma być oflagowany jako nie posiadający żadnej wartości (Null). W przeciwnym razie 0, jeśli element członkowski danych pola ma być oflagowany jako inny niż Null.

### <a name="remarks"></a>Uwagi

`SetFieldNull`jest używany dla pól `DoFieldExchange` związanych w mechanizmie.

Po dodaniu nowego rekordu do zestawu rekordów wszystkie elementy członkowskie danych pola są początkowo ustawione na wartość Null i oznaczone jako "brudne" (zmienione). Podczas pobierania rekordu ze źródła danych jego kolumny mają już wartości lub są null. Jeśli nie jest właściwe, aby pole Null, [CDaoException](../../mfc/reference/cdaoexception-class.md) jest generowany.

Jeśli używasz mechanizmu podwójnego buforowania, na przykład, jeśli wyraźnie chcesz wyznaczyć pole bieżącego rekordu `SetFieldNull` jako nie posiadające wartości, wywołanie z *bNull* ustawioną na WARTOŚĆ TRUE, aby oznaczyć go jako Null. Jeśli pole zostało wcześniej oznaczone jako Null i teraz chcesz nadać mu wartość, po prostu ustaw jego nową wartość. Nie trzeba usuwać flagi Null `SetFieldNull`za pomocą pliku . Aby ustalić, czy pole może być null, [wywołanie IsFieldNullable](#isfieldnullable).

Jeśli mechanizm podwójnego buforowania nie jest używany, zmiana wartości pola nie powoduje automatycznego ustawiania pola jako brudnego i niezerowego. Należy w szczególności ustawić pola brudne i inne niż Null. Flaga zawarta w [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) steruje automatycznym sprawdzaniem pola.

Mechanizm DFX wykorzystuje pseudonull. Aby uzyskać więcej informacji, zobacz [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

> [!NOTE]
> Wywołanie tej funkcji członkowskiej dopiero po [wywołaniu Edytuj](#edit) lub [DodajNew](#addnew).

Użycie wartości NULL dla pierwszego argumentu funkcji `outputColumn` spowoduje zastosowanie funkcji tylko `CDaoFieldExchange`do pól, a nie pól **param** w pliku . Na przykład wezwanie do

[!code-cpp[NVC_MFCDatabase#8](../../mfc/codesnippet/cpp/cdaorecordset-class_8.cpp)]

ustawi `outputColumn` tylko pola na NULL; **pola param** nie ulegnie to zmniejszyć.

## <a name="cdaorecordsetsetfieldvalue"></a><a name="setfieldvalue"></a>Zestaw CDaoRecordset::SetFieldValue

Wywołanie tej funkcji elementu członkowskiego, aby ustawić wartość pola, albo przez położenie porządkowe lub zmieniając wartość ciągu.

```
virtual void SetFieldValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);

virtual void SetFieldValue(
    int nIndex,
    const COleVariant& varValue);

void SetFieldValue(
    LPCTSTR lpszName,
    LPCTSTR lpszValue);

void SetFieldValue(
    int nIndex,
    LPCTSTR lpszValue);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
Wskaźnik do ciągu zawierającego nazwę pola.

*wartość varValue*<br/>
Odwołanie do [obiektu COleVariant](../../mfc/reference/colevariant-class.md) zawierającego wartość zawartości pola.

*Nindex*<br/>
Liczba całkowita reprezentująca położenie porządkowe pola w kolekcji Fields zbioru rekordów (zero.).

*lpszValue*<br/>
Wskaźnik do ciągu zawierającego wartość zawartości pola.

### <a name="remarks"></a>Uwagi

Użyj `SetFieldValue` i [GetFieldValue](#getfieldvalue) dynamicznie powiązać pola w czasie wykonywania, a nie statycznie wiążące kolumny przy użyciu mechanizmu [DoFieldExchange.](#dofieldexchange)

Należy zauważyć, że jeśli nie tworzysz pliku rekordów UNICODE, `SetFieldValue` należy użyć `COleVariant` formularza, który `COleVariant` nie zawiera parametru lub obiekt musi być jawnie zadeklarowany ANSI. Można to zrobić za pomocą [COleVariant:::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** forma konstruktora z *vtSrc* ustawiony na `VT_BSTRT` (ANSI) lub za pomocą `COleVariant` funkcji [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** z *vtSrc* ustawiony na `VT_BSTRT`.

Aby uzyskać powiązane informacje, zobacz tematy "Obiekt pola" i "Właściwość wartości" w Pomocy DAO.

## <a name="cdaorecordsetsetfieldvaluenull"></a><a name="setfieldvaluenull"></a>CDaoRecordset::SetFieldValueNull

Wywołanie tej funkcji elementu członkowskiego, aby ustawić pole na wartość Null.

```cpp
void SetFieldValueNull(int nIndex);
void SetFieldValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks pola w zestawie rekordów, do wyszukiwania według indeksu od zera.

*Lpszname*<br/>
Nazwa pola w zestawie rekordów, dla wyszukiwania według nazwy.

### <a name="remarks"></a>Uwagi

C++ NULL nie jest taki sam jak Null, co w terminologii bazy danych oznacza "bez wartości."

Aby uzyskać powiązane informacje, zobacz tematy "Obiekt pola" i "Właściwość wartości" w Pomocy DAO.

## <a name="cdaorecordsetsetlockingmode"></a><a name="setlockingmode"></a>CDaoRecordset::SetLockingMode

Wywołanie tej funkcji elementu członkowskiego, aby ustawić typ blokowania dla zestawu rekordów.

```cpp
void SetLockingMode(BOOL bPessimistic);
```

### <a name="parameters"></a>Parametry

*bPesymistyczne*<br/>
Flaga wskazująca typ blokowania.

### <a name="remarks"></a>Uwagi

Gdy obowiązuje pesymistyczna blokada, strona 2K zawierająca edytowany rekord jest zablokowana `Edit` natychmiast po wywołaniu funkcji elementu członkowskiego. Strona jest odblokowywała się po wywołaniu funkcji `Update` lub `Close` członka lub dowolnej operacji Przenieś lub Znajdź.

Gdy obowiązuje blokowanie optymistyczne, strona 2K zawierająca rekord jest zablokowana tylko `Update` wtedy, gdy rekord jest aktualizowany za pomocą funkcji elementu członkowskiego.

Jeśli strona jest zablokowana, żaden inny użytkownik nie może edytować rekordów na tej samej stronie. Jeśli wywołasz `SetLockingMode` i przekażesz wartość niezerową, a inny użytkownik ma już `Edit`zablokowaną stronę, wyjątek jest zgłaszany podczas wywoływania . Inni użytkownicy mogą odczytywać dane z zablokowanych stron.

Jeśli wywołasz `SetLockingMode` z wartością `Update` zero, a później wywołać, gdy strona jest zablokowana przez innego użytkownika, wystąpi wyjątek. Aby wyświetlić zmiany wprowadzone w rekordzie przez innego użytkownika `SetBookmark` (i utracić zmiany), należy wywołać funkcję elementu członkowskiego z wartością zakładki bieżącego rekordu.

Podczas pracy ze źródłami danych ODBC tryb blokowania jest zawsze optymistyczny.

## <a name="cdaorecordsetsetparamvalue"></a><a name="setparamvalue"></a>Zestaw CDaoRecordset::SetParamValue

Wywołanie tej funkcji elementu członkowskiego, aby ustawić wartość parametru w zestawie rekordów w czasie wykonywania.

```
virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);

virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Położenie numeryczne parametru w querydef's Parameters collection.

*var*<br/>
Wartość do ustawionego; patrz Uwagi.

*Lpszname*<br/>
Nazwa parametru, którego wartość ma zostać ustawiona.

### <a name="remarks"></a>Uwagi

Parametr musi już zostać ustanowiony jako część ciągu SQL pliku recordset. Można uzyskać dostęp do parametru według nazwy lub jego pozycji indeksu w kolekcji.

Określ wartość ustawioną `COleVariant` jako obiekt. Aby uzyskać informacje na temat ustawiania żądanej wartości i typu w obiekcie, `COleVariant` zobacz klasa [COleVariant](../../mfc/reference/colevariant-class.md). Należy zauważyć, że jeśli nie tworzysz pliku `COleVariant` rekordów UNICODE, obiekt musi być jawnie zadeklarowany ansi. Można to zrobić za pomocą [COleVariant:::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** forma konstruktora z *vtSrc* ustawiony na `VT_BSTRT` (ANSI) lub za pomocą `COleVariant` funkcji [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** z *vtSrc* ustawiony na `VT_BSTRT`.

## <a name="cdaorecordsetsetparamvaluenull"></a><a name="setparamvaluenull"></a>CDaoRecordset::SetParamValueNull

Wywołanie tej funkcji elementu członkowskiego, aby ustawić parametr na wartość Null.

```cpp
void SetParamValueNull(int nIndex);
void SetParamValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks pola w zestawie rekordów, do wyszukiwania według indeksu od zera.

*Lpszname*<br/>
Nazwa pola w zestawie rekordów, dla wyszukiwania według nazwy.

### <a name="remarks"></a>Uwagi

C++ NULL nie jest taki sam jak Null, co w terminologii bazy danych oznacza "bez wartości."

## <a name="cdaorecordsetsetpercentposition"></a><a name="setpercentposition"></a>CDaoRecordset::SetPercentPosition

Wywołanie tej funkcji elementu członkowskiego, aby ustawić wartość, która zmienia przybliżoną lokalizację bieżącego rekordu w obiekcie zestawu rekordów na podstawie procentu rekordów w zestawie rekordów.

```cpp
void SetPercentPosition(float fPosition);
```

### <a name="parameters"></a>Parametry

*fPozycja*<br/>
Liczba z 0 do 100.

### <a name="remarks"></a>Uwagi

Podczas pracy z zestawem rekordów typu dynaset lub migawka najpierw wypełnij zestaw rekordów, przechodząc do ostatniego rekordu przed wywołaniem . `SetPercentPosition` Jeśli wywołasz `SetPercentPosition` przed pełnym zapełnieniem zestawu rekordów, ilość ruchu jest w stosunku do liczby rekordów, do których dostęp uzyskał dostęp, zgodnie z wartością [GetRecordCount](#getrecordcount). Możesz przejść do ostatniego `MoveLast`rekordu, dzwoniąc .

Po wywołaniu `SetPercentPosition`rekord w przybliżonym położeniu odpowiadającym tej wartości staje się bieżący.

> [!NOTE]
> Wywołanie `SetPercentPosition` przeniesienia bieżącego rekordu do określonego rekordu w ach nie jest zalecane. Zamiast tego zadzwoń do funkcji elementu członkowskiego [SetBookmark.](#setbookmark)

Aby uzyskać powiązane informacje, zobacz temat "Właściwość percentposition" w Pomocy DAO.

## <a name="cdaorecordsetupdate"></a><a name="update"></a>CDaoRecordset::Aktualizacja

Wywołanie tej funkcji elementu `AddNew` członkowskiego `Edit` po wywołaniu funkcji lub elementu członkowskiego.

```
virtual void Update();
```

### <a name="remarks"></a>Uwagi

To wywołanie jest wymagane `AddNew` `Edit` do ukończenia operacji lub.

Zarówno `AddNew` `Edit` i przygotować bufor edycji, w którym dodane lub edytowane dane są umieszczane do zapisywania w źródle danych. `Update`zapisuje dane. Aktualizowane są tylko te pola oznaczone lub wykryte jako zmienione.

Jeśli źródło danych obsługuje transakcje, można `Update` nawiązać połączenie `AddNew` `Edit` (i jego odpowiednie lub wywołanie) część transakcji.

> [!CAUTION]
> Jeśli `Update` dzwonisz bez pierwszego `AddNew` `Edit`połączenia `Update` albo `CDaoException`lub , rzuca . Jeśli `AddNew` zadzwonisz `Edit`lub , `Update` musisz zadzwonić przed wywołaniem [MoveNext](#movenext) lub zamknąć zestaw rekordów lub połączenie ze źródłem danych. W przeciwnym razie zmiany zostaną utracone bez powiadomienia.

Gdy obiekt pliku recordset jest pesymistycznie zablokowany w środowisku wielodojowym, rekord pozostaje zablokowany od czasu, `Edit` gdy jest używany do czasu zakończenia aktualizacji. Jeśli plik recordset jest optymistycznie zablokowany, rekord jest zablokowany i porównywany z wstępnie edytowanym rekordem tuż przed jego zaktualizowaniem w bazie danych. Jeśli rekord został zmieniony `Edit`od `Update` czasu wywołania, operacja kończy się niepowodzeniem i MFC zgłasza wyjątek. Tryb blokowania można zmienić `SetLockingMode`za pomocą pliku .

> [!NOTE]
> Optymistyczne blokowanie jest zawsze używane w formatach zewnętrznej bazy danych, takich jak ODBC i instalowalny program ISAM.

Aby uzyskać powiązane informacje, zobacz tematy "AddNew Method", "CancelUpdate Method", "Delete Method", "LastModified Property", "Update Method" i "EditMode Property" w Pomocy DAO.

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)<br/>
[Klasa CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)<br/>
[Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)<br/>
[Klasa CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)<br/>
