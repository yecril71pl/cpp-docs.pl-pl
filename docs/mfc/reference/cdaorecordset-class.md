---
title: Klasa CDaoRecordset | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08e5433cfd7d1627babb4750c94396602a8f276c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400539"
---
# <a name="cdaorecordset-class"></a>Cdaorecordset — klasa

Reprezentuje zestaw rekordów wybranych ze źródła danych.

## <a name="syntax"></a>Składnia

```
class CDaoRecordset : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoRecordset::CDaoRecordset](#cdaorecordset)|Konstruuje `CDaoRecordset` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoRecordset::AddNew](#addnew)|Przygotowuje do dodawania nowego rekordu. Wywołaj [aktualizacji](#update) aby zakończyć operację dodawania.|
|[CDaoRecordset::CanAppend](#canappend)|Zwraca wartość różną od zera, jeśli nowe rekordy można dodać do zestawu rekordów za pomocą [działają funkcje AddNew](#addnew) funkcja elementu członkowskiego.|
|[CDaoRecordset::CanBookmark](#canbookmark)|Zwraca wartość różną od zera, jeśli zestaw rekordów obsługuje zakładek.|
|[CDaoRecordset::CancelUpdate](#cancelupdate)|Anuluje wszystkie oczekujące aktualizacje ze względu na [Edytuj](#edit) lub [działają funkcje AddNew](#addnew) operacji.|
|[CDaoRecordset::CanRestart](#canrestart)|Zwraca wartość różną od zera, jeśli [Requery](#requery) można wywołać w celu ponownie uruchomić zapytanie w zestawie rekordów.|
|[CDaoRecordset::CanScroll](#canscroll)|Zwraca wartość różną od zera, jeśli można przewijać rekordów.|
|[CDaoRecordset::CanTransact](#cantransact)|Zwraca wartość różną od zera, jeśli źródło danych obsługuje transakcji.|
|[CDaoRecordset::CanUpdate](#canupdate)|Zwraca wartość różną od zera, jeśli zestaw rekordów, które mogą być aktualizowane (można dodać, zaktualizować lub usunąć rekordy).|
|[CDaoRecordset::Close](#close)|Zamyka zestawu rekordów.|
|[CDaoRecordset::Delete](#delete)|Usunięcie bieżącego rekordu w zestawie. Należy jawnie przewiń do innego rekordu, po usunięciu.|
|[CDaoRecordset::DoFieldExchange](#dofieldexchange)|Wywoływane w celu wymiany danych (w obu kierunkach) między elementy członkowskie danych pola zestawu rekordów i odpowiedni rekord w źródle danych. Implementuje DAO rekord pola wymiany (DXF).|
|[CDaoRecordset::Edit](#edit)|Przygotowuje się do zmian w bieżącym rekordzie. Wywołaj `Update` można ukończyć edycję.|
|[CDaoRecordset::FillCache](#fillcache)|Wypełnienie wszystkich lub częścią lokalnej pamięci podręcznej dla obiektu zestawu rekordów, która zawiera dane ze źródła danych ODBC.|
|[CDaoRecordset::Find](#find)|Lokalizuje pierwszy, następnie poprzedniego lub ostatnia lokalizacja określonego ciągu w zestawie rekordów dynamicznego, który spełni określone kryteria i sprawia, że służące do rejestrowania bieżącego rekordu.|
|[CDaoRecordset::FindFirst](#findfirst)|Lokalizuje pierwszy rekord w dynamicznego lub zestawu rekordów typu migawka, który spełni określone kryteria i sprawia, że służące do rejestrowania bieżącego rekordu.|
|[CDaoRecordset::FindLast](#findlast)|Znajduje ostatni rekord w dynamicznego lub zestawu rekordów typu migawka, który spełni określone kryteria i sprawia, że służące do rejestrowania bieżącego rekordu.|
|[CDaoRecordset::FindNext](#findnext)|Lokalizuje następnego rekordu w dynamicznego lub zestawu rekordów typu migawka, który spełni określone kryteria i sprawia, że służące do rejestrowania bieżącego rekordu.|
|[CDaoRecordset::FindPrev](#findprev)|Lokalizuje poprzedniego rekordu w dynamicznego lub zestawu rekordów typu migawka, który spełni określone kryteria i sprawia, że służące do rejestrowania bieżącego rekordu.|
|[CDaoRecordset::GetAbsolutePosition](#getabsoluteposition)|Zwraca liczbę rekordów obiektem rekordem bieżącego rekordu.|
|[CDaoRecordset::GetBookmark](#getbookmark)|Zwraca wartość, która reprezentuje zakładki do rekordu.|
|[CDaoRecordset::GetCacheSize](#getcachesize)|Zwraca wartość, która określa liczbę rekordów w zestawie rekordów dynamicznego zawierające dane lokalne przechowywanie w pamięci podręcznej ze źródła danych ODBC.|
|[CDaoRecordset::GetCacheStart](#getcachestart)|Zwraca wartość, która określa zakładki pierwszego rekordu w zestawie rekordów przechowywanie w pamięci podręcznej.|
|[CDaoRecordset::GetCurrentIndex](#getcurrentindex)|Zwraca `CString` zawierający nazwę indeksu najbardziej ostatnio używane na indeksowane, typ tabeli `CDaoRecordset`.|
|[CDaoRecordset::GetDateCreated](#getdatecreated)|Zwraca datę i godzinę, w tabeli podstawowej bazowego `CDaoRecordset` został utworzony obiekt|
|[CDaoRecordset::GetDateLastUpdated](#getdatelastupdated)|Zwraca datę i godzinę ostatniej zmiany wprowadzone do projektów podstawowy w tabeli podstawowej `CDaoRecordset` obiektu.|
|[CDaoRecordset::GetDefaultDBName](#getdefaultdbname)|Zwraca nazwę domyślnego źródła danych.|
|[CDaoRecordset::GetDefaultSQL](#getdefaultsql)|Wywołuje się, by pobrać domyślny ciąg SQL do wykonania.|
|[CDaoRecordset::GetEditMode](#geteditmode)|Zwraca wartość, która wskazuje stan edycji dla bieżącego rekordu.|
|[CDaoRecordset::GetFieldCount](#getfieldcount)|Zwraca wartość, która reprezentuje liczbę pól w zestawie rekordów.|
|[CDaoRecordset::GetFieldInfo](#getfieldinfo)|Zwraca określonych rodzajów informacji o polach w zestawie rekordów.|
|[CDaoRecordset::GetFieldValue](#getfieldvalue)|Zwraca wartość pola w zestawie rekordów.|
|[CDaoRecordset::GetIndexCount](#getindexcount)|Pobiera liczbę indeksów w tabeli podstawowy zestaw rekordów.|
|[CDaoRecordset::GetIndexInfo](#getindexinfo)|Zwraca różne rodzaje informacji na temat indeksu.|
|[CDaoRecordset::GetLastModifiedBookmark](#getlastmodifiedbookmark)|Używany do określenia najbardziej ostatnio dodane lub zaktualizowane rekordu.|
|[CDaoRecordset::GetLockingMode](#getlockingmode)|Zwraca wartość wskazującą typ blokady jest włączona, podczas edycji.|
|[CDaoRecordset::GetName](#getname)|Zwraca `CString` zawierający nazwę zestawu rekordów.|
|[CDaoRecordset::GetParamValue](#getparamvalue)|Pobiera bieżącą wartość określonego parametru przechowywana w obiekcie DAOParameter bazowego.|
|[CDaoRecordset::GetPercentPosition](#getpercentposition)|Zwraca pozycję bieżącego rekordu w postaci procentu całkowitej liczbie rekordów.|
|[CDaoRecordset::GetRecordCount](#getrecordcount)|Zwraca liczbę rekordów, dostępne w obiekcie zestawu rekordów.|
|[CDaoRecordset::GetSQL](#getsql)|Pobiera ciąg SQL używany do wybierania rekordów dla zestawu rekordów.|
|[CDaoRecordset::GetType](#gettype)|Wywoływane w celu określenia rodzaju zestaw rekordów: typ tabeli, dynamicznego lub typu migawka.|
|[CDaoRecordset::GetValidationRule](#getvalidationrule)|Zwraca `CString` zawierające wartość, która sprawdza poprawność danych wprowadzoną w polu.|
|[CDaoRecordset::GetValidationText](#getvalidationtext)|Pobiera tekst, który jest wyświetlany, gdy reguła sprawdzania poprawności nie jest spełniony.|
|[CDaoRecordset::IsBOF](#isbof)|Zwraca wartość różną od zera, jeśli zestaw rekordów ma został umieszczony przed pierwszym rekordzie. Nie ma bieżącego rekordu.|
|[CDaoRecordset::IsDeleted](#isdeleted)|Zwraca wartość różną od zera, jeśli zestaw rekordów jest ustawiony na rekordzie usunięte.|
|[CDaoRecordset::IsEOF](#iseof)|Zwraca wartość różną od zera, jeśli zestaw rekordów zawiera został umieszczony po ostatnim rekordzie. Nie ma bieżącego rekordu.|
|[CDaoRecordset::IsFieldDirty](#isfielddirty)|Zwraca wartość różną od zera, jeśli określone pole w bieżącym rekordzie została zmieniona.|
|[CDaoRecordset::IsFieldNull](#isfieldnull)|Zwraca wartość różną od zera, jeśli określone pole w bieżącym rekordzie ma wartość Null, (o żadnej wartości).|
|[CDaoRecordset::IsFieldNullable](#isfieldnullable)|Zwraca wartość różną od zera, jeśli określone pole w bieżącym rekordzie można ustawić wartości null (o żadnej wartości).|
|[CDaoRecordset::IsOpen](#isopen)|Zwraca wartość różną od zera, jeśli [Otwórz](#open) został wcześniej wywołany.|
|[CDaoRecordset::Move](#move)|Ustawia zestaw rekordów do określonej liczby rekordów z bieżącego rekordu w dowolnym kierunku.|
|[CDaoRecordset::MoveFirst](#movefirst)|Umieszcza bieżącego rekordu na pierwszy rekord w zestawie rekordów.|
|[CDaoRecordset::MoveLast](#movelast)|Umieszcza bieżącego rekordu na ostatni rekord w zestawie rekordów.|
|[CDaoRecordset::MoveNext](#movenext)|Umieszcza bieżącego rekordu na następnego rekordu w zestawie rekordów.|
|[CDaoRecordset::MovePrev](#moveprev)|Umieszcza bieżącego rekordu na poprzedniej rekordu w zestawie rekordów.|
|[CDaoRecordset::Open](#open)|Tworzy nowy zestaw rekordów z tabeli, zestaw dynamiczny lub migawki.|
|[CDaoRecordset::Requery](#requery)|Uruchamia zapytanie w zestawie rekordów ponownie, aby odświeżyć wybrane rekordy.|
|[CDaoRecordset::Seek](#seek)|Lokalizuje rekordu w obiekcie zestawu rekordów indeksowany typ tabeli, który spełni określone kryteria dla bieżącego indeksu i sprawia, że służące do rejestrowania bieżącego rekordu.|
|[CDaoRecordset::SetAbsolutePosition](#setabsoluteposition)|Ustawia numer obiektem rekordem bieżącego rekordu.|
|[CDaoRecordset::SetBookmark](#setbookmark)|Ustawia zestaw rekordów na rekord zawierający zakładką.|
|[CDaoRecordset::SetCacheSize](#setcachesize)|Ustawia wartość, która określa liczbę rekordów w zestawie rekordów dynamicznego zawierające dane lokalne przechowywanie w pamięci podręcznej ze źródła danych ODBC.|
|[CDaoRecordset::SetCacheStart](#setcachestart)|Ustawia wartość określającą zakładki pierwszego rekordu w zestawie rekordów przechowywanie w pamięci podręcznej.|
|[CDaoRecordset::SetCurrentIndex](#setcurrentindex)|Wywołuje się, by ustawić indeks w zestawie rekordów typ tabeli.|
|[CDaoRecordset::SetFieldDirty](#setfielddirty)|Oznacza określonego pola w bieżącym rekordzie, wraz ze zmianą.|
|[CDaoRecordset::SetFieldNull](#setfieldnull)|Ustawia wartość określonego pola w bieżącym rekordzie, wartości null (o żadnej wartości).|
|[CDaoRecordset::SetFieldValue](#setfieldvalue)|Ustawia wartość pola w zestawie rekordów.|
|[CDaoRecordset::SetFieldValueNull](#setfieldvaluenull)|Ustawia wartość pola w zestawie rekordów na wartość Null. (o: Brak wartości).|
|[CDaoRecordset::SetLockingMode](#setlockingmode)|Ustawia wartość wskazującą typ blokady do umieszczenia w życie podczas edycji.|
|[CDaoRecordset::SetParamValue](#setparamvalue)|Ustawia bieżącą wartość określonego parametru przechowywana w obiekcie DAOParameter podstawowej|
|[CDaoRecordset::SetParamValueNull](#setparamvaluenull)|Ustawia bieżącą wartość określonego parametru o wartości Null (o żadnej wartości).|
|[CDaoRecordset::SetPercentPosition](#setpercentposition)|Ustawia położenie bieżącego rekordu do lokalizacji, odpowiadające na wartość procentową całkowitej liczby rekordów w zestawie rekordów.|
|[CDaoRecordset::Update](#update)|Kończy `AddNew` lub `Edit` operacji, zapisując dane nowe lub zmodyfikowane w źródle danych.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDaoRecordset::m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)|Zawiera flagę wskazującą, czy pola są automatycznie oznaczane jako zmienione.|
|[CDaoRecordset::m_nFields](#m_nfields)|Zawiera liczbę elementy członkowskie danych pola w klasie zestawu rekordów i liczba kolumn wybranych przez zestaw rekordów ze źródła danych.|
|[CDaoRecordset::m_nParams](#m_nparams)|Zawiera liczbę elementy członkowskie danych parametru w klasie rekordów — liczba parametrów przekazana z zapytaniem zestawu rekordów|
|[CDaoRecordset::m_pDAORecordset](#m_pdaorecordset)|Wskaźnik do interfejsu DAO bazowy obiekt zestawu rekordów.|
|[CDaoRecordset::m_pDatabase](#m_pdatabase)|Ustaw źródłowej bazy danych dla tego wyniku. Zawiera wskaźnik do [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) obiektu.|
|[CDaoRecordset::m_strFilter](#m_strfilter)|Zawiera ciąg używany do budowy SQL **gdzie** instrukcji.|
|[CDaoRecordset::m_strSort](#m_strsort)|Zawiera ciąg używany do budowy SQL **ORDER BY** instrukcji.|

## <a name="remarks"></a>Uwagi

Znana jako "zestawy rekordów," `CDaoRecordset` obiekty są dostępne w następujących trzech formach:

- Zestawy rekordów typ tabeli reprezentują tabeli podstawowej, która umożliwia zbadać, dodawania, zmieniania i usuwania rekordów z tabeli pojedynczej bazy danych.

- Zestawy rekordów dynamicznego są wynikiem zapytania, które mogą mieć aktualizowalnych rekordy. Te zestawy rekordów są zestawu rekordów, których można użyć, aby sprawdzić, dodać, zmienić lub usuwania rekordów z tabeli źródłowej bazy danych lub tabel. Zestawy rekordów dynamicznego mogą zawierać pola z co najmniej jedną tabelę w bazie danych.

- Typ migawki zestawów rekordów są statyczne kopię zestawu rekordów, które służy do wyszukiwania danych lub generowania raportów. Te zestawy rekordów mogą zawierać pola z co najmniej jedną tabelę w bazie danych, ale nie można zaktualizować.

Każdy formularz rekordów reprezentuje zestaw rekordów ustalony w czasie, który zostanie otwarty zestaw rekordów. Podczas przewijania do rekordu w zestawie rekordów typ tabeli lub dynamicznego zestawu rekordów odzwierciedla zmian wprowadzonych do rekordu, po otwarciu zestawu rekordów przez innych użytkowników lub innych zestawów rekordów w aplikacji. (Nie można zaktualizować zestawu rekordów typu migawka.) Możesz użyć `CDaoRecordset` bezpośrednio lub pochodzić z klasy specyficzne dla aplikacji w zestawie rekordów z `CDaoRecordset`. Następnie możesz:

- Przewijania rekordów.

- Ustaw indeks i szybko wyszukać rekordy przy użyciu [Seek](#seek) (tylko zestawy rekordów typ tabeli).

- Znajdowanie rekordów na podstawie porównania ciągów: "<","\<=", "=", "> =", lub ">" (dynamicznego i zestawów rekordów typu Migawka).

- Aktualizowanie rekordów i określić tryb blokowania (oprócz zestawów rekordów typu Migawka).

- Filtruj zestaw rekordów, aby ograniczyć rekordy, które wybierze od tych, które są dostępne w źródle danych.

- Sortuj zestawu rekordów.

- Parametryzacja zestawu rekordów, aby dostosować jego zaznaczenie z informacjami o nieznany do czasu wykonywania.

Klasa `CDaoRecordset` dostarcza interfejs podobny do klasy `CRecordset`. Główna różnica polega na tej klasy `CDaoRecordset` uzyskuje dostęp do danych za pośrednictwem dostępu do obiektu DAO (Data) oparte na OLE. Klasa `CRecordset` uzyskuje dostęp do systemu DBMS za pośrednictwem interfejsu Open Database Connectivity (ODBC) i sterownik ODBC dla tego systemu DBMS.

> [!NOTE]
> Klasy bazy danych DAO różnią się od klas baz danych MFC, które są oparte na Open Database Connectivity (ODBC). Wszystkie nazwy klasy bazy danych DAO mają prefiks "CDao". Możesz nadal dostęp do źródła danych ODBC przy użyciu klas DAO; klasy DAO ogólnie oferują możliwości wyższego poziomu, ponieważ są one specyficzne dla aparatu bazy danych Microsoft Jet.

Można użyć `CDaoRecordset` bezpośrednio lub wyprowadzić klasę z `CDaoRecordset`. Aby użyć klasy zestawu rekordów w obu przypadkach, otworzyć bazę danych i skonstruować obiekt zestawu rekordów, przekazując konstruktora wskaźnik do Twojej `CDaoDatabase` obiektu. Można także skonstruować `CDaoRecordset` obiektu i umożliwiają utworzenie tymczasowego MFC `CDaoDatabase` obiekt dla Ciebie. Następnie wywołaj zestawu rekordów [Otwórz](#open) funkcji członkowskiej, określając, czy obiekt jest zestaw rekordów typ tabeli, dynamicznego zestawu rekordów lub zestawu rekordów typu migawka. Wywoływanie `Open` wybiera dane z bazy danych i pobiera pierwszy rekord.

Użyj obiektu elementu członkowskiego funkcji i danych elementów członkowskich do przewijania rekordów i działają na nich. Operacje dostępne są zależne od tego, czy obiekt jest zestaw rekordów typ tabeli, dynamicznego zestawu rekordów lub zestawu rekordów typu migawka i czy jest można aktualizować tylko do odczytu — zależy to od możliwości bazy danych lub Open Database Connectivity (ODBC) źródło danych. Aby odświeżyć rekordy, które mogą zostały zmienione lub dodane od `Open` wywołań, wywołań obiektu [Requery](#requery) funkcja elementu członkowskiego. Wywołanie obiektu `Close` element członkowski funkcji i zniszcz obiekt, po zapoznaniu się z nim.

`CDaoRecordset` używa wymiany pól rekordów DAO (DXF) w celu obsługują odczytywanie i aktualizowanie pola rekordu za pośrednictwem bezpiecznego typu C++ członkowie Twojego `CDaoRecordset` lub `CDaoRecordset`-klasy pochodnej. Możesz również wdrożyć dynamiczne powiązanie kolumn w bazie danych, bez użycia za pomocą mechanizmu DFX [getfieldvalue —](#getfieldvalue) i [SetFieldValue](#setfieldvalue).

Aby uzyskać powiązane informacje zobacz temat "Obiekt zestawu rekordów" w Pomocy programu DAO.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CDaoRecordset`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

##  <a name="addnew"></a>  CDaoRecordset::AddNew

Wywołaj tę funkcję elementu członkowskiego, aby dodać nowy rekord do zestawu rekordów typu tabeli lub dynamicznego.

```
virtual void AddNew();
```

### <a name="remarks"></a>Uwagi

Pola rekordu są początkowo o wartości Null. (W terminologii bazy danych o wartości Null oznacza, że "po żadnej wartości" i nie jest taka sama jak wartość NULL w języku C++) Aby zakończyć operację, należy wywołać [aktualizacji](#update) funkcja elementu członkowskiego. `Update` Zapisuje zmiany w źródle danych.

> [!CAUTION]
>  Jeśli edytować rekord, a następnie przewiń listę do innego rekordu bez wywoływania `Update`, wszystkie zmiany zostaną utracone bez ostrzeżenia.

Jeśli dodasz rekord do dynamicznego zestawu rekordów, wywołując [działają funkcje AddNew](#addnew), rekord jest widoczny w zestawie rekordów i zawarty w tabeli podstawowej, gdzie staje się niewidoczna dla każdego nowego `CDaoRecordset` obiektów.

Pozycja nowy rekord, zależy od typu zestawu rekordów:

- Zestaw rekordów, polegający na wstawieniu nowy rekord w typie dynamiczny nie jest gwarantowana. To zachowanie, zmienić za pomocą programu Microsoft Jet 3.0 ze względów wydajności i współbieżności. Jeśli celem jest zapewnienie nowo dodanego rekordu w bieżącym rekordzie, Pobierz zakładki ostatniej modyfikacji rekordu i przejście do zakładki tego:

[!code-cpp[NVC_MFCDatabase#1](../../mfc/codesnippet/cpp/cdaorecordset-class_1.cpp)]

- W zestawie rekordów typ tabeli, dla którego określono indeksu zwracane są rekordy w ich właściwe miejsce, w kolejności sortowania. Jeśli został określony bez indeksu, nowe rekordy są zwracane na końcu zestawu rekordów.

Rekord, który były aktualne, zanim została użyta `AddNew` pozostaje bieżącego. Jeśli chcesz utworzyć nowy rekord bieżący, a zestaw rekordów obsługuje zakładek, wywołanie [setbookmark —](#setbookmark) do zakładki identyfikowane przez ustawienie właściwości LastModified obiektu bazowego zestawu rekordów DAO. To jest przydatne w przypadku określenia wartości dla licznika (automatycznego przyrostu) pola rekordów dodanych. Aby uzyskać więcej informacji, zobacz [GetLastModifiedBookmark](#getlastmodifiedbookmark).

Jeśli baza danych obsługuje transakcje, możesz wprowadzać swoje `AddNew` wywołać częścią transakcji. Aby uzyskać więcej informacji na temat transakcji Zobacz klasy [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md). Należy zauważyć, że należy wywołać [CDaoWorkspace::BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans) przed wywołaniem `AddNew`.

Jest niedozwolone wywołanie `AddNew` dla zestawu rekordów którego [Otwórz](#open) nie została wywołana funkcja elementu członkowskiego. A `CDaoException` jest generowany, jeśli wywołujesz `AddNew` dla zestawu rekordów, które nie można dołączyć. Można określić, czy zestaw rekordów jest można aktualizować, wywołując [CanAppend](#canappend).

Znaczniki framework zmienione elementy członkowskie danych pola, aby upewnić się, że będą one zapisywane do rekordu w źródle danych przez mechanizm wymiany (DXF) pola rekordów DAO. Zazwyczaj zmianę wartości pola ustawia pole zanieczyszczone automatycznie, dzięki czemu będą rzadko należy wywołać [SetFieldDirty](#setfielddirty) samodzielnie, ale czasami chcieć upewnij się, że kolumny zostaną jawnie zaktualizowane lub wstawione niezależnie od tego jakie korzyści jest w pole składowej danych. Mechanizm DFX stosuje również użycie **PSEUDO NULL**. Aby uzyskać więcej informacji, zobacz [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Jeśli nie jest używany mechanizm podwójnego buforowania, następnie zmieniając wartość pola automatycznie nie ustawiono pola oznaczonych jako zakłócone. W tym przypadku będzie trzeba jawnie ustawić pole zanieczyszczeniu. Flaga zawarte w [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) kontrolki, to automatyczne sprawdzanie.

> [!NOTE]
> Jeśli rekordy, które są podwójnie buforowana (oznacza to, że pole Automatyczne sprawdzanie jest włączone), podczas wywoływania `CancelUpdate` spowoduje przywrócenie zmienne Członkowskie wartości mieli oni przed `AddNew` lub `Edit` została wywołana.

Aby uzyskać powiązane informacje zobacz tematy "Działają funkcje AddNew metody", "CancelUpdate metody", "Ostatnia modyfikacja właściwości" i "Trybu edycji właściwości" w Pomocy programu DAO.

##  <a name="canappend"></a>  CDaoRecordset::CanAppend

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy wcześniej otwarty zestaw rekordów można dodawać nowe rekordy, wywołując [działają funkcje AddNew](#addnew) funkcja elementu członkowskiego.

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli zestaw rekordów zezwala na dodawanie nowych rekordów; w przeciwnym razie 0. `CanAppend` Zwraca wartość 0 Jeśli otwarty zestaw rekordów jako tylko do odczytu.

### <a name="remarks"></a>Uwagi

Aby uzyskać powiązane informacje zobacz temat "Dołącz metody" w Pomocy programu DAO.

##  <a name="canbookmark"></a>  CDaoRecordset::CanBookmark

Wywołaj tę funkcję elementu członkowskiego, aby ustalić, czy wcześniej otwarty zestaw rekordów można oznaczyć pojedynczo rekordów, korzystanie z zakładek.

```
BOOL CanBookmark();
```

### <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli zestaw rekordów obsługuje zakładek, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli używasz zestawów rekordów na podstawie całkowicie w tabelach aparatu bazy danych Microsoft Jet zakładek może służyć z wyjątkiem na zestawów rekordów typu migawka oznaczone jako tylko do przodu przewijania zestawów rekordów. Inne produkty bazy danych (zewnętrznego źródła danych ODBC) mogą nie obsługiwać zakładek.

Aby uzyskać powiązane informacje zobacz temat "Bookmarkable Property" w Pomocy programu DAO.

##  <a name="cancelupdate"></a>  CDaoRecordset::CancelUpdate

`CancelUpdate` Funkcja elementu członkowskiego anuluje wszystkie oczekujące aktualizacje ze względu na [Edytuj](#edit) lub [działają funkcje AddNew](#addnew) operacji.

```
virtual void CancelUpdate();
```

### <a name="remarks"></a>Uwagi

Na przykład, jeśli aplikacja wywołuje `Edit` lub `AddNew` funkcja elementu członkowskiego i nie została wywołana [aktualizacji](#update), `CancelUpdate` spowoduje anulowanie wszelkich zmian wprowadzonych po `Edit` lub `AddNew` została wywołana.

> [!NOTE]
>  Jeśli rekordy, które są podwójnie buforowana (oznacza to, że pole Automatyczne sprawdzanie jest włączone), podczas wywoływania `CancelUpdate` spowoduje przywrócenie zmienne Członkowskie wartości mieli oni przed `AddNew` lub `Edit` została wywołana.

Jeśli ma nie `Edit` lub `AddNew` operacji do czasu, `CancelUpdate` powoduje, że MFC, aby zgłosić wyjątek. Wywołaj [GetEditMode](#geteditmode) funkcja elementu członkowskiego, aby ustalić, czy istnieje oczekująca operacja, która może być anulowany.

Aby uzyskać powiązane informacje zobacz temat "CancelUpdate metody" w Pomocy programu DAO.

##  <a name="canrestart"></a>  CDaoRecordset::CanRestart

Wywołaj tę funkcję elementu członkowskiego, aby ustalić, czy zestaw rekordów zezwala na ponowne uruchomienie jej zapytanie (na przykład aby odświeżyć swoje rekordy) przez wywołanie metody `Requery` funkcja elementu członkowskiego.

```
BOOL CanRestart();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość różną od zera `Requery` można wywołać w celu uruchomienia zestawu rekordów zapytanie ponownie, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zestawy rekordów typ tabeli nie obsługują `Requery`.

Jeśli `Requery` jest nieobsługiwana, wywołaj [Zamknij](#close) następnie [Otwórz](#open) odświeżania danych. Możesz wywołać `Requery` można zaktualizować obiektu zestawu rekordów podstawowej parametr zapytania po zmianie wartości parametrów.

Aby uzyskać powiązane informacje zobacz temat "Property ponownego uruchamiania" w Pomocy programu DAO.

##  <a name="canscroll"></a>  CDaoRecordset::CanScroll

Wywołaj tę funkcję elementu członkowskiego, aby ustalić, czy zestaw rekordów umożliwia przewijanie.

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli można przewijać rekordy, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli wywołasz [Otwórz](#open) z `dbForwardOnly`, zestaw rekordów można tylko przewiń do przodu.

Aby uzyskać powiązane informacje zobacz temat "Pozycjonowanie bieżącego rekordu wskaźnika za pomocą DAO" w Pomocy programu DAO.

##  <a name="cantransact"></a>  CDaoRecordset::CanTransact

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy zestaw rekordów zezwala na transakcji.

```
BOOL CanTransact();
```

### <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli bazowe źródło danych obsługuje transakcji, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać powiązane informacje zobacz temat "Property transakcji" w Pomocy programu DAO.

##  <a name="canupdate"></a>  CDaoRecordset::CanUpdate

Wywołaj tę funkcję elementu członkowskiego, aby ustalić, czy zestaw rekordów może być aktualizowana.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli zestaw rekordów, które mogą być aktualizowane (dodawania, aktualizowania i usuwania rekordów), w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zestaw rekordów może być tylko do odczytu, jeśli bazowe źródło danych jest tylko do odczytu, lub jeśli określono `dbReadOnly` dla *nOptions* gdy wywoływana [Otwórz](#open) zestawu rekordów.

Aby uzyskać powiązane informacje zobacz tematy "Działają funkcje AddNew metody", "Edytuj metodę", "Usuń metodę", "Metoda aktualizacji" i "Można zaktualizować właściwości" w Pomocy programu DAO.

##  <a name="cdaorecordset"></a>  CDaoRecordset::CDaoRecordset

Konstruuje `CDaoRecordset` obiektu.

```
CDaoRecordset(CDaoDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>Parametry

*pDatabase*<br/>
Zawiera wskaźnik do [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) obiekt lub wartość NULL. Jeśli nie ma wartości NULL i `CDaoDatabase` obiektu `Open` połączyć się ze źródłem danych nie została wywołana funkcja elementu członkowskiego, próbuje otworzyć go dla Ciebie podczas swój własny zestaw rekordów [Otwórz](#open) wywołania. W przypadku przekazania wartości NULL, `CDaoDatabase` obiekt jest konstruowany i połączone przy użyciu informacje o źródle danych, które zostały określone, jeśli pochodzi z klasy zestawu rekordów `CDaoRecordset`.

### <a name="remarks"></a>Uwagi

Można użyć `CDaoRecordset` bezpośrednio lub pochodzić z klasy specyficzne dla aplikacji z `CDaoRecordset`. ClassWizard umożliwia pochodzi z klasy zestawu rekordów.

> [!NOTE]
>  Przypadku klasy wyprowadzonej `CDaoRecordset` klasy usługi pochodnej klasy należy podać swój własny konstruktora. W konstruktorze klasy pochodnej, wywołanie konstruktora `CDaoRecordset::CDaoRecordset`, przekazując odpowiednie parametry wzdłuż do niego.

Przekazać wartości NULL do Konstruktora zestawu rekordów mieć `CDaoDatabase` obiekt skonstruowany i połączone dla Ciebie automatycznie. Jest to przydatny skrót, który nie wymaga to utworzyć i połączyć `CDaoDatabase` obiektu przed konstruowanie rekordów. Jeśli `CDaoDatabase` obiektu nie jest otwarty, [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) zostanie również utworzony obiekt dla Ciebie, która używa domyślnego obszaru roboczego. Aby uzyskać więcej informacji, zobacz [CDaoDatabase::CDaoDatabase](../../mfc/reference/cdaodatabase-class.md#cdaodatabase).

##  <a name="close"></a>  CDaoRecordset::Close

Zamykanie `CDaoRecordset` obiektu spowoduje usunięcie go z kolekcji otwarty zestaw rekordów w skojarzonej bazy danych.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Ponieważ `Close` nie niszczy `CDaoRecordset` obiektu, można ponownie użyć obiektu przez wywołanie metody `Open` tego samego źródła danych lub innego źródła danych.

Wszystkie oczekujące [działają funkcje AddNew](#addnew) lub [Edytuj](#edit) instrukcje zostały anulowane, a wszystkie oczekujące transakcje są wycofywane. Jeśli chcesz zachować oczekujące dodatki lub zmiany, należy wywołać [aktualizacji](#update) przed wywołaniem `Close` dla każdego zestawu rekordów.

Możesz wywołać `Open` ponownie po wywołaniu `Close`. Dzięki temu można ponownie użyć obiekt zestawu rekordów. Lepszą alternatywą jest wywołanie [Requery](#requery), jeśli to możliwe.

Aby uzyskać powiązane informacje zobacz temat "Metody Close" w Pomocy programu DAO.

##  <a name="delete"></a>  CDaoRecordset::Delete

Wywołaj tę funkcję elementu członkowskiego, aby usunąć bieżący rekord w obiekcie otwarty zestaw rekordów dynamicznego lub typ tabeli.

```
virtual void Delete();
```

### <a name="remarks"></a>Uwagi

Po pomyślnym usunięciu, elementy członkowskie danych pola w zestawie rekordów są ustawione na wartość Null i musi jawnie wywołać jedną z funkcji elementów członkowskich nawigacji zestawu rekordów ( [przenieść](#move), [Seek](#seek), [ Setbookmark —](#setbookmark)i tak dalej), aby opuścić usunięty rekord. Podczas usuwania rekordów z zestawu rekordów, musi istnieć rekord bieżący w zestawie rekordów przed wywołaniem `Delete`; w przeciwnym razie MFC zgłasza wyjątek.

`Delete` Usuwa bieżący rekord i sprawia, że niedostępny. Mimo że nie można edytować ani usuniętego rekordu, pozostaje w bieżącym. Po przejściu do innego rekordu, jednak nie możesz wprowadzać usunięty rekord bieżący ponownie.

> [!CAUTION]
>  Zestaw rekordów musi być nadaje się do aktualizacji i musi być prawidłowy rekord bieżący w zestawie rekordów po wywołaniu `Delete`. Na przykład, jeśli możesz usunąć rekord, ale nie przewiń do nowego rekordu przed wywołaniem `Delete` ponownie `Delete` zgłasza [CDaoException](../../mfc/reference/cdaoexception-class.md).

Jeśli używasz transakcji i wywołania można cofnąć usunięcie rekordu [CDaoWorkspace::Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback) funkcja elementu członkowskiego. Jeśli tabela podstawowa jest tabela podstawowa w cascade usunąć relację, usunięcie bieżącego rekordu może również usunięcie co najmniej jednego rekordu w tabeli obcego. Aby uzyskać więcej informacji zobacz definicję "Kaskadowo usuń" w Pomocy programu DAO.

W odróżnieniu od `AddNew` i `Edit`, wywołanie `Delete` nie następuje po wywołaniu `Update`.

Aby uzyskać powiązane informacje zobacz tematy "Działają funkcje AddNew metody", "Edytuj metodę", "Usuń metodę", "Metoda aktualizacji" i "Można zaktualizować właściwości" w Pomocy programu DAO.

##  <a name="dofieldexchange"></a>  CDaoRecordset::DoFieldExchange

Struktura wywołuje tę funkcję elementu członkowskiego, aby automatycznie wymianę danych między elementy członkowskie danych pola obiektu zestawu rekordów i odpowiednie kolumny bieżącego rekordu w źródle danych.

```
virtual void DoFieldExchange(CDaoFieldExchange* pFX);
```

### <a name="parameters"></a>Parametry

*Plik pFX*<br/>
Zawiera wskaźnik do `CDaoFieldExchange` obiektu. Struktura będzie już skonfigurowano ten obiekt do określenia kontekstu dla operacji wymiany pól.

### <a name="remarks"></a>Uwagi

Wiąże również swoje elementy członkowskie danych parametru, jeśli parametr symbole zastępcze w ciągu instrukcji SQL dla zaznaczenia w zestawie rekordów. Wymiana pola danych, nazywane wymiana pól rekordów DAO (DXF) działa w obu kierunkach: z obiekty zestawów rekordów elementy członkowskie danych pola do pól rekordu w źródle danych, a także z rekordu w źródle danych do obiektu zestawu rekordów. Jeśli dynamicznie powiązanie kolumn nie należy implementować `DoFieldExchange`.

Jedyną akcją, zazwyczaj należy wykonać w celu zaimplementowania `DoFieldExchange` dla rekordów pochodnej klasy ma utworzyć klasę z ClassWizard i określić nazwy i typy danych elementów członkowskich danych pola. Można również dodawać kod do ClassWizard zapisuje określone elementy członkowskie danych parametru. Jeśli wszystkie pola mają być dynamicznie powiązane, ta funkcja będzie nieaktywne, chyba że określisz elementy członkowskie danych parametru.

Kiedy Deklarujesz klasy pochodnej rekordów z ClassWizard, kreator zapisuje zastąpieniu obiektu `DoFieldExchange` , który przypomina poniższy przykład:

[!code-cpp[NVC_MFCDatabase#2](../../mfc/codesnippet/cpp/cdaorecordset-class_2.cpp)]

##  <a name="edit"></a>  CDaoRecordset::Edit

Wywołaj tę funkcję elementu członkowskiego do umożliwienia wprowadzania zmian w bieżącym rekordzie.

```
virtual void Edit();
```

### <a name="remarks"></a>Uwagi

Gdy wywołujesz `Edit` funkcji członkowskiej, zmiany wprowadzone do pól bieżącego rekordu są kopiowane do buforu kopiowania. Po wprowadzeniu odpowiednich zmian w rekordzie wywołać `Update` Aby zapisać zmiany. `Edit` zapisuje wartości elementów członkowskich danych w zestawie rekordów. Jeśli wywołasz `Edit`, wprowadzić zmiany, następnie wywołać `Edit` ponownie rekordu wartości zostaną przywrócone do były przed pierwszym `Edit` wywołania.

> [!CAUTION]
>  Jeśli edytować rekord, a następnie wykonać żadnych operacji, która przechodzi do innego rekordu bez wywoływania pierwszy `Update`, wszystkie zmiany zostaną utracone bez ostrzeżenia. Ponadto jeśli zamkniesz zestawu rekordów lub nadrzędną bazę danych, edytowany rekord jest odrzucany bez ostrzeżenia.

W niektórych przypadkach można zaktualizować kolumny czyniąc ją o wartości Null (zawierający żadnych danych). Aby to zrobić, należy wywołać `SetFieldNull` z parametrem wartość PRAWDA, aby znak pola o wartości Null; to również powoduje, że kolumny do zaktualizowania. Jeśli chcesz, aby pole zapisywane do źródła danych, nawet jeśli jego wartość nie została zmieniona, wywołaj `SetFieldDirty` z parametrem wartość TRUE. Dzieje się tak nawet wtedy, gdy pole ma wartość Null.

Znaczniki framework zmienione elementy członkowskie danych pola, aby upewnić się, że będą one zapisywane do rekordu w źródle danych przez mechanizm wymiany (DXF) pola rekordów DAO. Zazwyczaj zmianę wartości pola ustawia pole zanieczyszczone automatycznie, dzięki czemu będą rzadko należy wywołać [SetFieldDirty](#setfielddirty) samodzielnie, ale czasami chcieć upewnij się, że kolumny zostaną jawnie zaktualizowane lub wstawione niezależnie od tego jakie korzyści jest w pole składowej danych. Mechanizm DFX stosuje również użycie **PSEUDO NULL**. Aby uzyskać więcej informacji, zobacz [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Jeśli nie jest używany mechanizm podwójnego buforowania, następnie zmieniając wartość pola automatycznie nie ustawiono pola oznaczonych jako zakłócone. W tym przypadku będzie trzeba jawnie ustawić pole zanieczyszczeniu. Flaga zawarte w [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) kontrolki, to automatyczne sprawdzanie.

Gdy obiekt zestawu rekordów pessimistically jest zablokowana w środowisku wielodostępnym, rekord jest zablokowany, od momentu `Edit` jest używana przed zakończeniem aktualizację. Jeśli zestaw rekordów optymistycznie jest zablokowany, rekord jest zablokowana i tylko w przypadku, zanim zostaną one zaktualizowane w bazie danych w porównaniu z wstępnie edytowany rekord. Jeśli rekord został zmieniony, ponieważ wywołana `Edit`, `Update` zgłasza wyjątek, operacja zakończy się niepowodzeniem i MFC. Możesz zmienić tryb blokowania z `SetLockingMode`.

> [!NOTE]
>  Zawsze formatów zewnętrznej bazy danych, takich jak ODBC i możliwe do zainstalowania ISAM używane optymistyczne blokowanie.

Bieżący rekord pozostaje bieżącego po wywołaniu metody `Edit`. Aby wywołać `Edit`, musi istnieć bieżącego rekordu. Jeśli nie ma bieżącego rekordu lub zestaw rekordów nie odwołuje się do Otwórz typ tabeli lub obiektu zestawu rekordów dynamicznego, wystąpi wyjątek. Wywoływanie `Edit` powoduje, że `CDaoException` zostanie wygenerowany w następujących warunkach:

- Nie ma bieżącego rekordu.

- Baza danych lub zestawu rekordów jest tylko do odczytu.

- Brak pól w rekordzie są aktualizowalne.

- Baza danych lub zestaw rekordów został otwarty do wyłącznego użytku przez innego użytkownika.

- Inny użytkownik zablokował strony zawierającej rekord.

Jeśli źródło danych obsługuje transakcje, można wprowadzić `Edit` wywołać częścią transakcji. Należy zauważyć, że należy wywołać `CDaoWorkspace::BeginTrans` przed wywołaniem `Edit` i po otwarciu zestawu rekordów. Należy również zauważyć, że wywołanie `CDaoWorkspace::CommitTrans` nie jest alternatywą do wywoływania `Update` do ukończenia `Edit` operacji. Aby uzyskać więcej informacji na temat transakcji Zobacz klasy `CDaoWorkspace`.

Aby uzyskać powiązane informacje zobacz tematy "Działają funkcje AddNew metody", "Edytuj metodę", "Usuń metodę", "Metoda aktualizacji" i "Można zaktualizować właściwości" w Pomocy programu DAO.

##  <a name="fillcache"></a>  CDaoRecordset::FillCache

Wywołaj tę funkcję elementu członkowskiego w pamięci podręcznej określoną liczbę rekordów w zestawie.

```
void FillCache(
    long* pSize = NULL,
    COleVariant* pBookmark = NULL);
```

### <a name="parameters"></a>Parametry

*pSize*<br/>
Określa liczbę wierszy, aby wypełnić z pamięci podręcznej. Jeżeli pominięto ten parametr, wartość jest określana przez ustawienie właściwości CacheSize obiekt DAO.

*pBookmark*<br/>
A [COleVariant](../../mfc/reference/colevariant-class.md) określenie zakładki. Pamięć podręczna jest wypełniony, zaczynając od rekordu wskazywanym przez tę zakładkę. Jeżeli pominięto ten parametr pamięci podręcznej jest wypełniony, począwszy od rekordu, wskazane przez właściwość CacheStart obiekt DAO.

### <a name="remarks"></a>Uwagi

Pamięć podręczna zwiększa wydajność aplikacji, która umożliwia pobranie lub pobiera dane z serwera zdalnego. Pamięć podręczna jest miejsca w pamięci lokalnej, która przechowuje dane ostatnio pobrane z serwera na założeniu, że dane będą prawdopodobnie można żądać jej ponownie po uruchomieniu aplikacji. Jeśli wymagane są dane, aparat bazy danych Microsoft Jet pamięci podręcznej danych najpierw sprawdza zamiast pobierając je z serwera, który jest bardziej czasochłonne. Korzystanie z danych buforowanie na inne niż ODBC — źródła danych nie ma wpływu, ponieważ dane nie są zapisywane w pamięci podręcznej.

Bez czekania pamięci podręcznej w celu wypełnienia z rekordami, ponieważ są one dołączone, możesz jawnie wpisać pamięci podręcznej w dowolnym momencie przez wywołanie metody `FillCache` funkcja elementu członkowskiego. Jest to sposób wypełnienia pamięci podręcznej, ponieważ `FillCache` dostarcza kilka rekordów jednocześnie zamiast pojedynczo. Na przykład podczas każdego screenful rekordy są wyświetlane, możesz mieć wywołania aplikacji `FillCache` do pobrania następnej screenful rekordów.

Wszystkie dostępne z obiektami rekordów bazy danych ODBC może mieć lokalnej pamięci podręcznej. Aby utworzyć pamięć podręczną, otwórz obiekt zestawu rekordów ze źródła danych zdalnych, a następnie wywołaj `SetCacheSize` i `SetCacheStart` funkcji elementów członkowskich zestawu rekordów. Jeśli *lSize* i *lBookmark* utworzyć zakres, który jest całkowicie lub częściowo poza zakres określony przez `SetCacheSize` i `SetCacheStart`, część zestawu rekordów poza tym zakresem są ignorowane i nie jest ładowane do pamięci podręcznej. Jeśli `FillCache` żądań więcej rekordów niż pozostają w zdalne źródło danych, są pobierane tylko te rekordy, pozostałe i jest zgłaszany żaden wyjątek.

Rekordy pobrane z pamięci podręcznej nie odzwierciedlają zmiany wprowadzone współbieżnie źródła danych przez innych użytkowników.

`FillCache` pobiera tylko te rekordy, które nie jest jeszcze w pamięci podręcznej. Aby wymusić aktualizację wszystkich danych w pamięci podręcznej, należy wywołać `SetCacheSize` funkcji składowej z *lSize* parametru równa 0, wywołanie `SetCacheSize` ponownie, używając *lSize* parametr równy rozmiarowi pamięci podręcznej pierwotnie żądaną, a następnie wywołaj `FillCache`.

Aby uzyskać powiązane informacje zobacz temat "FillCache metody" w Pomocy programu DAO.

##  <a name="find"></a>  CDaoRecordset::Find

Wywołaj tę funkcję elementu członkowskiego, aby zlokalizować określonego ciągu w zestawie rekordów dynamiczny lub typ migawki za pomocą operatora porównania.

```
virtual BOOL Find(
    long lFindType,
    LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lFindType*<br/>
Wartość wskazująca typ operacji Znajdź żądane. Możliwe wartości to:

- AFX_DAO_NEXT Znajdź następnej lokalizacji pasującego ciągu.

- AFX_DAO_PREV Znajdź poprzedniej lokalizacji pasującego ciągu.

- AFX_DAO_FIRST Znajdź pierwszej lokalizacji pasującego ciągu.

- AFX_DAO_LAST znaleźć ostatnich lokalizacji pasującego ciągu.

*lpszFilter*<br/>
Wyrażenie ciągu (takich jak **gdzie** klauzuli w instrukcji SQL bez słowa **gdzie**) używana do lokalizowania rekordu. Na przykład:

[!code-cpp[NVC_MFCDatabase#3](../../mfc/codesnippet/cpp/cdaorecordset-class_3.cpp)]

### <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli zostaną znalezione pasujące rekordy, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Po pierwsze, następnie można znaleźć poprzednią lub ostatnie wystąpienie ciągu. `Find` jest funkcją wirtualną, aby można było go zastąpić i Dodaj własną implementację. `FindFirst`, `FindLast`, `FindNext`, I `FindPrev` wywołanie funkcje Członkowskie `Find` funkcja elementu członkowskiego, aby można było używać `Find` do sterowania zachowaniem wszystkich operacji wyszukiwania.

Aby zlokalizować rekordu w zestawie rekordów typ tabeli, należy wywołać [Seek](#seek) funkcja elementu członkowskiego.

> [!TIP]
>  Mniejszy zestaw rekordów, możesz mieć bardziej skuteczna `Find` będzie. Ogólnie rzecz biorąc, a szczególnie w przypadku danych ODBC lepiej jest utworzyć nowe zapytanie, które pobiera tylko rekordy, które chcesz.

Aby uzyskać powiązane informacje zobacz temat "FindNext FindFirst, FindLast, metody FindPrevious" w Pomocy programu DAO.

##  <a name="findfirst"></a>  CDaoRecordset::FindFirst

Wywołaj tę funkcję elementu członkowskiego, aby znaleźć pierwszy rekord, który spełnia określony warunek.

```
BOOL FindFirst(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lpszFilter*<br/>
Wyrażenie ciągu (takich jak **gdzie** klauzuli w instrukcji SQL bez słowa **gdzie**) używana do lokalizowania rekordu.

### <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli zostaną znalezione pasujące rekordy, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`FindFirst` Funkcja elementu członkowskiego, rozpocznie się wyszukiwanie od początku zestawu rekordów i wyszukiwania na końcu zestawu rekordów.

Jeśli chcesz uwzględnić wszystkie rekordy w wyszukiwaniu (nie tylko te, które spełniają określony warunek) użyj jednej z operacji przenoszenia przenoszenia między rekordami. Aby zlokalizować rekordu w zestawie rekordów typ tabeli, należy wywołać `Seek` funkcja elementu członkowskiego.

Jeśli rekord spełniające kryteria nie znajduje się, bieżący wskaźnik rekordu jest nieokreślony, i `FindFirst` zwraca wartość zero. Jeśli zestaw rekordów zawiera więcej niż jeden rekord, który spełnia kryteria, `FindFirst` lokalizuje pierwsze wystąpienie `FindNext` znajduje następne wystąpienie i tak dalej.

> [!CAUTION]
>  Jeśli edytujesz bieżącego rekordu, pamiętaj zapisać zmiany przez wywołanie metody `Update` funkcji składowej przed przejściem do innego rekordu. Jeśli zostanie przeniesiony do innego rekordu bez aktualizowania, zmiany zostaną utracone bez ostrzeżenia.

`Find` Funkcji elementów członkowskich przeszukiwać z lokalizacji i kierunek określony w tabeli poniżej:

|Operacje Znajdź|Rozpocznij|Kierunek wyszukiwania|
|---------------------|-----------|----------------------|
|`FindFirst`|Począwszy od zestawu rekordów|Koniec zestawu rekordów|
|`FindLast`|Koniec zestawu rekordów|Począwszy od zestawu rekordów|
|`FindNext`|Bieżący rekord|Koniec zestawu rekordów|
|`FindPrevious`|Bieżący rekord|Począwszy od zestawu rekordów|

> [!NOTE]
>  Gdy wywołujesz `FindLast`, aparat bazy danych Microsoft Jet wypełnia całkowicie rekordów przed rozpoczęciem wyszukiwania, jeśli to nie ma już zrobione. Pierwszy wyszukiwania może trwać dłużej niż późniejszych wyszukiwań.

Przy użyciu jednej z operacji wyszukiwania nie jest taka sama jak wywołanie `MoveFirst` lub `MoveNext`, jednak co po prostu sprawia, że pierwszy lub następny rekord bieżący bez określania warunku. Można wykonać operacji wyszukiwania za pomocą operacji przenoszenia.

Korzystając z operacji wyszukiwania, należy pamiętać o następujących czynności:

- Jeśli `Find` zwraca wartość różną od zera, bieżący rekord nie jest zdefiniowany. W tym przypadku należy umieść bieżący wskaźnik rekordu ponownie z prawidłowym rekordem.

- Nie można użyć operacji wyszukiwania z przewijaniem typ migawki rekordów.

- Należy używać amerykański format daty (dzień miesiąc rok) podczas wyszukiwania dla pól zawierających daty, nawet jeśli nie używasz wersji US aparatu bazy danych Microsoft Jet; w przeciwnym razie dopasowanie rekordy mogą nie być odnajdowane.

- Podczas pracy z bazami danych ODBC i dużych zestawów dynamicznych, użytkownik może stwierdzić, że za pomocą operacji wyszukiwania jest powolne, szczególnie w przypadku pracy z dużych zestawów rekordów. Może poprawić wydajność, korzystając z zapytań SQL za pomocą dostosowanego **ORDERBY** lub **gdzie** klauzul, parametr zapytania, lub `CDaoQuerydef` obiekty, które pobierają określonych rekordów indeksowanych.

Aby uzyskać powiązane informacje zobacz temat "FindNext FindFirst, FindLast, metody FindPrevious" w Pomocy programu DAO.

##  <a name="findlast"></a>  CDaoRecordset::FindLast

Wywołaj tę funkcję elementu członkowskiego, aby znaleźć ostatni rekord, który spełnia określony warunek.

```
BOOL FindLast(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lpszFilter*<br/>
Wyrażenie ciągu (takich jak **gdzie** klauzuli w instrukcji SQL bez słowa **gdzie**) używana do lokalizowania rekordu.

### <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli zostaną znalezione pasujące rekordy, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`FindLast` Funkcja elementu członkowskiego zaczyna wyszukiwanie na końcu zestawu rekordów i wyszukiwania do tyłu w kierunku początku zestawu rekordów.

Jeśli chcesz uwzględnić wszystkie rekordy w wyszukiwaniu (nie tylko te, które spełniają określony warunek) użyj jednej z operacji przenoszenia przenoszenia między rekordami. Aby zlokalizować rekordu w zestawie rekordów typ tabeli, należy wywołać `Seek` funkcja elementu członkowskiego.

Jeśli rekord spełniające kryteria nie znajduje się, bieżący wskaźnik rekordu jest nieokreślony, i `FindLast` zwraca wartość zero. Jeśli zestaw rekordów zawiera więcej niż jeden rekord, który spełnia kryteria, `FindFirst` lokalizuje pierwsze wystąpienie `FindNext` znajduje następne wystąpienie po pierwszym wystąpieniu i tak dalej.

> [!CAUTION]
>  Jeśli edytujesz bieżącego rekordu, należy zapisać zmiany przez wywołanie metody `Update` funkcji składowej przed przejściem do innego rekordu. Jeśli zostanie przeniesiony do innego rekordu bez aktualizowania, zmiany zostaną utracone bez ostrzeżenia.

Przy użyciu jednej z operacji wyszukiwania nie jest taka sama jak wywołanie `MoveFirst` lub `MoveNext`, jednak co po prostu sprawia, że pierwszy lub następny rekord bieżący bez określania warunku. Można wykonać operacji wyszukiwania za pomocą operacji przenoszenia.

Korzystając z operacji wyszukiwania, należy pamiętać o następujących czynności:

- Jeśli `Find` zwraca wartość różną od zera, bieżący rekord nie jest zdefiniowany. W tym przypadku należy umieść bieżący wskaźnik rekordu ponownie z prawidłowym rekordem.

- Nie można użyć operacji wyszukiwania z przewijaniem typ migawki rekordów.

- Należy używać amerykański format daty (dzień miesiąc rok) podczas wyszukiwania dla pól zawierających daty, nawet jeśli nie używasz wersji US aparatu bazy danych Microsoft Jet; w przeciwnym razie dopasowanie rekordy mogą nie być odnajdowane.

- Podczas pracy z bazami danych ODBC i dużych zestawów dynamicznych, użytkownik może stwierdzić, że za pomocą operacji wyszukiwania jest powolne, szczególnie w przypadku pracy z dużych zestawów rekordów. Może poprawić wydajność, korzystając z zapytań SQL za pomocą dostosowanego **ORDERBY** lub **gdzie** klauzul, parametr zapytania, lub `CDaoQuerydef` obiekty, które pobierają określonych rekordów indeksowanych.

Aby uzyskać powiązane informacje zobacz temat "FindNext FindFirst, FindLast, metody FindPrevious" w Pomocy programu DAO.

##  <a name="findnext"></a>  CDaoRecordset::FindNext

Wywołaj tę funkcję elementu członkowskiego, aby znaleźć następny rekord, który spełnia określony warunek.

```
BOOL FindNext(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lpszFilter*<br/>
Wyrażenie ciągu (takich jak **gdzie** klauzuli w instrukcji SQL bez słowa **gdzie**) używana do lokalizowania rekordu.

### <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli zostaną znalezione pasujące rekordy, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`FindNext` Funkcja elementu członkowskiego rozpocznie się wyszukiwanie od bieżącego rekordu a na koniec przeszukuje-to-end zestawu rekordów.

Jeśli chcesz uwzględnić wszystkie rekordy w wyszukiwaniu (nie tylko te, które spełniają określony warunek) użyj jednej z operacji przenoszenia przenoszenia między rekordami. Aby zlokalizować rekordu w zestawie rekordów typ tabeli, należy wywołać `Seek` funkcja elementu członkowskiego.

Jeśli rekord spełniające kryteria nie znajduje się, bieżący wskaźnik rekordu jest nieokreślony, i `FindNext` zwraca wartość zero. Jeśli zestaw rekordów zawiera więcej niż jeden rekord, który spełnia kryteria, `FindFirst` lokalizuje pierwsze wystąpienie `FindNext` znajduje następne wystąpienie i tak dalej.

> [!CAUTION]
>  Jeśli edytujesz bieżącego rekordu, należy zapisać zmiany przez wywołanie metody `Update` funkcji składowej przed przejściem do innego rekordu. Jeśli zostanie przeniesiony do innego rekordu bez aktualizowania, zmiany zostaną utracone bez ostrzeżenia.

Przy użyciu jednej z operacji wyszukiwania nie jest taka sama jak wywołanie `MoveFirst` lub `MoveNext`, jednak co po prostu sprawia, że pierwszy lub następny rekord bieżący bez określania warunku. Można wykonać operacji wyszukiwania za pomocą operacji przenoszenia.

Korzystając z operacji wyszukiwania, należy pamiętać o następujących czynności:

- Jeśli `Find` zwraca wartość różną od zera, bieżący rekord nie jest zdefiniowany. W tym przypadku należy umieść bieżący wskaźnik rekordu ponownie z prawidłowym rekordem.

- Nie można użyć operacji wyszukiwania z przewijaniem typ migawki rekordów.

- Należy używać amerykański format daty (dzień miesiąc rok) podczas wyszukiwania dla pól zawierających daty, nawet jeśli nie używasz wersji US aparatu bazy danych Microsoft Jet; w przeciwnym razie dopasowanie rekordy mogą nie być odnajdowane.

- Podczas pracy z bazami danych ODBC i dużych zestawów dynamicznych, użytkownik może stwierdzić, że za pomocą operacji wyszukiwania jest powolne, szczególnie w przypadku pracy z dużych zestawów rekordów. Może poprawić wydajność, korzystając z zapytań SQL za pomocą dostosowanego **ORDERBY** lub **gdzie** klauzul, parametr zapytania, lub `CDaoQuerydef` obiekty, które pobierają określonych rekordów indeksowanych.

Aby uzyskać powiązane informacje zobacz temat "FindNext FindFirst, FindLast, metody FindPrevious" w Pomocy programu DAO.

##  <a name="findprev"></a>  CDaoRecordset::FindPrev

Wywołaj tę funkcję elementu członkowskiego, aby znaleźć poprzedni rekord, który odpowiada określony warunek.

```
BOOL FindPrev(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lpszFilter*<br/>
Wyrażenie ciągu (takich jak **gdzie** klauzuli w instrukcji SQL bez słowa **gdzie**) używana do lokalizowania rekordu.

### <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli zostaną znalezione pasujące rekordy, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`FindPrev` Funkcja elementu członkowskiego rozpocznie się wyszukiwanie od bieżącego rekordu a na koniec przeszukuje Wstecz w kierunku początku zestawu rekordów.

Jeśli chcesz uwzględnić wszystkie rekordy w wyszukiwaniu (nie tylko te, które spełniają określony warunek) użyj jednej z operacji przenoszenia przenoszenia między rekordami. Aby zlokalizować rekordu w zestawie rekordów typ tabeli, należy wywołać `Seek` funkcja elementu członkowskiego.

Jeśli rekord spełniające kryteria nie znajduje się, bieżący wskaźnik rekordu jest nieokreślony, i `FindPrev` zwraca wartość zero. Jeśli zestaw rekordów zawiera więcej niż jeden rekord, który spełnia kryteria, `FindFirst` lokalizuje pierwsze wystąpienie `FindNext` znajduje następne wystąpienie i tak dalej.

> [!CAUTION]
>  Jeśli edytujesz bieżącego rekordu, należy zapisać zmiany przez wywołanie metody `Update` funkcji składowej przed przejściem do innego rekordu. Jeśli zostanie przeniesiony do innego rekordu bez aktualizowania, zmiany zostaną utracone bez ostrzeżenia.

Przy użyciu jednej z operacji wyszukiwania nie jest taka sama jak wywołanie `MoveFirst` lub `MoveNext`, jednak co po prostu sprawia, że pierwszy lub następny rekord bieżący bez określania warunku. Można wykonać operacji wyszukiwania za pomocą operacji przenoszenia.

Korzystając z operacji wyszukiwania, należy pamiętać o następujących czynności:

- Jeśli `Find` zwraca wartość różną od zera, bieżący rekord nie jest zdefiniowany. W tym przypadku należy umieść bieżący wskaźnik rekordu ponownie z prawidłowym rekordem.

- Nie można użyć operacji wyszukiwania z przewijaniem typ migawki rekordów.

- Należy używać amerykański format daty (dzień miesiąc rok) podczas wyszukiwania dla pól zawierających daty, nawet jeśli nie używasz wersji US aparatu bazy danych Microsoft Jet; w przeciwnym razie dopasowanie rekordy mogą nie być odnajdowane.

- Podczas pracy z bazami danych ODBC i dużych zestawów dynamicznych, użytkownik może stwierdzić, że za pomocą operacji wyszukiwania jest powolne, szczególnie w przypadku pracy z dużych zestawów rekordów. Może poprawić wydajność, korzystając z zapytań SQL za pomocą dostosowanego **ORDERBY** lub **gdzie** klauzul, parametr zapytania, lub `CDaoQuerydef` obiekty, które pobierają określonych rekordów indeksowanych.

Aby uzyskać powiązane informacje zobacz temat "FindNext FindFirst, FindLast, metody FindPrevious" w Pomocy programu DAO.

##  <a name="getabsoluteposition"></a>  CDaoRecordset::GetAbsolutePosition

Zwraca liczbę rekordów obiektem rekordem bieżącego rekordu.

```
long GetAbsolutePosition();
```

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita z zakresu od 0 do liczby rekordów w zestawie rekordów. Odnosi się do porządkowym bieżącego rekordu w zestawie rekordów.

### <a name="remarks"></a>Uwagi

Wartość właściwości AbsolutePosition obiektu bazowego DAO jest liczony od zera; Ustawienie wartości 0 odwołuje się do pierwszego rekordu w zestawie rekordów. Można określić liczbę rekordów wypełnione w zestawie rekordów, wywołując [getrecordcount —](#getrecordcount). Wywoływanie `GetRecordCount` może zająć trochę czasu, ponieważ musi uzyskać dostęp do wszystkich rekordów w celu określenia liczby.

Jeśli nie ma bieżącego rekordu, jako gdy nie ma żadnych rekordów w zestawie rekordów, - 1 jest zwracana. Jeśli bieżący rekord zostanie usunięty, wartość właściwości AbsolutePosition nie jest zdefiniowana, a MFC zgłasza wyjątek, jeśli odwołuje się do. Dla zestawów rekordów dynamicznego nowe rekordy są dodawane do końca sekwencji.

> [!NOTE]
>  Ta właściwość nie jest przeznaczona do służyć jako numer rekordu zastępczy. Zakładki są nadal zalecany sposób przechowywania i powrocie do podanego położenia i jedynym sposobem na pozycji bieżącego rekordu dla wszystkich typów obiektów zestawu rekordów. W szczególności pozycji danego rekordu zmienia usunięcie rekordów przed nim. Istnieje również ma gwarancji, że rekord będzie miał tym samym położeniu bezwzględnym, jeśli zestaw rekordów jest utworzony ponownie, ponieważ kolejność poszczególnych rekordów w zestawie rekordów nie jest gwarantowane, chyba że zostanie utworzona przy użyciu instrukcji SQL przy użyciu  **ORDERBY** klauzuli.

> [!NOTE]
>  Ta funkcja członkowska jest prawidłowy tylko w przypadku dynamicznego i zestawów rekordów typu migawka.

Aby uzyskać powiązane informacje zobacz temat "AbsolutePosition Property" w Pomocy programu DAO.

##  <a name="getbookmark"></a>  CDaoRecordset::GetBookmark

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wartość zakładki do określonego rekordu.

```
COleVariant GetBookmark();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość reprezentującą zakładkę w bieżącym rekordzie.

### <a name="remarks"></a>Uwagi

Po utworzeniu obiektu zestawu rekordów lub otwarte, każdego z jego rekordów już unikatowe zakładki, gdy je obsługuje. Wywołaj `CanBookmark` do ustalenia, czy zestaw rekordów obsługuje zakładek.

Można zapisać zakładki w bieżącym rekordzie, przypisując wartości zakładki do `COleVariant` obiektu. Aby szybko powrócić do tego rekordu w dowolnym momencie po przejściu do innego rekordu, należy wywołać `SetBookmark` przy użyciu odpowiadający wartości tego parametru `COleVariant` obiektu.

> [!NOTE]
>  Wywoływanie [Requery](#requery) zmienia DAO zakładek.

Aby uzyskać powiązane informacje zobacz temat "Property zakładki" w Pomocy programu DAO.

##  <a name="getcachesize"></a>  CDaoRecordset::GetCacheSize

Wywołanie tej funkcji elementu członkowskiego w celu uzyskania liczby rekordów w pamięci podręcznej.

```
long GetCacheSize();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która określa liczbę rekordów w zestawie rekordów dynamicznego zawierające dane lokalne przechowywanie w pamięci podręcznej ze źródła danych ODBC.

### <a name="remarks"></a>Uwagi

Buforowanie danych zwiększa wydajność aplikacji, która pobiera dane z serwera zdalnego za pośrednictwem obiektów rekordów dynamicznego. Pamięć podręczna to miejsce w pamięci lokalnej, która przechowuje dane ostatnio pobrana z serwera w przypadku, gdy dane będzie wymagane ponownie, gdy aplikacja jest uruchomiona. Jeśli wymagane są dane, aparat bazy danych Microsoft Jet pamięci podręcznej dla żądanych danych najpierw sprawdza zamiast pobierania jej z serwera, który jest bardziej czasochłonne. Dane, które nie pochodzą ze źródła danych ODBC nie jest zapisana w pamięci podręcznej.

Wszystkie źródła danych ODBC, takich jak dołączonej tabeli mogą mieć lokalnej pamięci podręcznej.

Aby uzyskać powiązane informacje zobacz temat "CacheSize CacheStart właściwości", w Pomocy programu DAO.

##  <a name="getcachestart"></a>  CDaoRecordset::GetCacheStart

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wartość zakładki pierwszego rekordu w zestawie rekordów przechowywanie w pamięci podręcznej.

```
COleVariant GetCacheStart();
```

### <a name="return-value"></a>Wartość zwracana

A `COleVariant` określający zakładki pierwszego rekordu w zestawie rekordów przechowywanie w pamięci podręcznej.

### <a name="remarks"></a>Uwagi

Aparat bazy danych Microsoft Jet żądań rekordy w zakresie pamięci podręcznej z pamięci podręcznej i żąda ona rekordy poza obszarem pamięci podręcznej z serwera.

> [!NOTE]
>  Rekordów pobieranych z pamięci podręcznej nie odzwierciedlają zmiany wprowadzone współbieżnie źródła danych przez innych użytkowników.

Aby uzyskać powiązane informacje zobacz temat "CacheSize CacheStart właściwości", w Pomocy programu DAO.

##  <a name="getcurrentindex"></a>  CDaoRecordset::GetCurrentIndex

Wywołaj tę funkcję elementu członkowskiego, aby określić indeks aktualnie w użyciu indeksowanej tabeli `CDaoRecordset` obiektu.

```
CString GetCurrentIndex();
```

### <a name="return-value"></a>Wartość zwracana

Element `CString` zawierający nazwę indeksu, obecnie w użyciu przy użyciu zestawu rekordów typu tabeli. Zwraca pusty ciąg, jeśli został ustawiony Brak indeksu.

### <a name="remarks"></a>Uwagi

Ten indeks jest podstawą kolejność rekordów w zestawie rekordów typ tabeli i jest używany przez [Seek](#seek) funkcję elementu członkowskiego, aby zlokalizować rekordów.

A `CDaoRecordset` obiekt może mieć więcej niż jednego indeksu, ale można użyć tylko jednego indeksu w czasie (mimo że [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) obiekt może mieć wiele indeksów zdefiniowanej).

Aby uzyskać powiązane informacje zobacz temat "Indeksu obiektu", jak i definicja "bieżący indeks" w Pomocy programu DAO.

##  <a name="getdatecreated"></a>  CDaoRecordset::GetDateCreated

Wywołaj tę funkcję elementu członkowskiego, aby pobrać datę i godzinę utworzenia tabeli podstawowej.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Wartość zwracana

A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiekt zawierający datę i godzinę utworzenia tabeli podstawowej.

### <a name="remarks"></a>Uwagi

Ustawienia daty i godziny są uzyskiwane z komputera, na którym została utworzona tabela podstawowa.

Aby uzyskać powiązane informacje zobacz temat "DateCreated LastUpdated właściwości", w Pomocy programu DAO.

##  <a name="getdatelastupdated"></a>  CDaoRecordset::GetDateLastUpdated

Wywołaj tę funkcję elementu członkowskiego, aby pobrać Data i godzina ostatniej aktualizacji schematu.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Wartość zwracana

A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiekt zawierający datę i godzinę ostatniej aktualizacji tabeli podstawowej strukturę (schemat).

### <a name="remarks"></a>Uwagi

Ustawienia daty i godziny są uzyskiwane z komputera ostatniej aktualizacji tabeli podstawowej strukturę (schemat).

Aby uzyskać powiązane informacje zobacz temat "DateCreated LastUpdated właściwości", w Pomocy programu DAO.

##  <a name="getdefaultdbname"></a>  CDaoRecordset::GetDefaultDBName

Wywołaj tę funkcję elementu członkowskiego, aby określić nazwę bazy danych dla tego zestawu rekordów.

```
virtual CString GetDefaultDBName();
```

### <a name="return-value"></a>Wartość zwracana

Element `CString` zawierający ścieżkę i nazwę bazy danych, z którego pochodzi ten zestaw rekordów.

### <a name="remarks"></a>Uwagi

Jeśli zestaw rekordów został utworzony bez wskaźnik do [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md), a następnie ta ścieżka jest używana przez zestaw rekordów można otworzyć domyślnej bazy danych. Domyślnie ta funkcja zwraca pusty ciąg. Gdy ClassWizard pochodzi nowy zestaw rekordów z `CDaoRecordset`, ta funkcja zostanie utworzony automatycznie.

Poniższy przykład ilustruje użycie podwójny ukośnik odwrotny (\\\\) w ciągu, w jakim są wymagane dla ciągu były prawidłowo interpretowane.

[!code-cpp[NVC_MFCDatabase#4](../../mfc/codesnippet/cpp/cdaorecordset-class_4.cpp)]

##  <a name="getdefaultsql"></a>  CDaoRecordset::GetDefaultSQL

Struktura wywołuje tę funkcję elementu członkowskiego, aby pobrać domyślną instrukcję SQL, na którym bazuje zestaw rekordów.

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>Wartość zwracana

Element `CString` zawiera domyślną instrukcję SQL.

### <a name="remarks"></a>Uwagi

Może to być nazwa tabeli lub SQL **wybierz** instrukcji.

Możesz pośrednio należy zdefiniować domyślną instrukcję SQL od zadeklarowania klasy zestawu rekordów z ClassWizard i ClassWizard wykonuje to zadanie.

W przypadku przekazania pusty ciąg SQL do [Otwórz](#open), a następnie ta funkcja jest wywoływana w celu określenia nazwy tabeli lub SQL dla rekordów.

##  <a name="geteditmode"></a>  CDaoRecordset::GetEditMode

Wywołaj tę funkcję elementu członkowskiego do ustalenia stanu edytowania, który będzie miał jedną z następujących wartości:

```
short GetEditMode();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość, która wskazuje stan edycji dla bieżącego rekordu.

### <a name="remarks"></a>Uwagi

|Wartość|Opis|
|-----------|-----------------|
|`dbEditNone`|Nie operacji edycji jest w toku.|
|`dbEditInProgress`|`Edit` została wywołana.|
|`dbEditAdd`|`AddNew` została wywołana.|

Aby uzyskać powiązane informacje zobacz temat "Trybu edycji właściwości" w Pomocy programu DAO.

##  <a name="getfieldcount"></a>  CDaoRecordset::GetFieldCount

Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę pól (kolumn) zdefiniowanych w zestawie rekordów.

```
short GetFieldCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba pól w zestawie rekordów.

### <a name="remarks"></a>Uwagi

Aby uzyskać powiązane informacje zobacz temat "Właściwości liczba" w Pomocy programu DAO.

##  <a name="getfieldinfo"></a>  CDaoRecordset::GetFieldInfo

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać informacje dotyczące pól w zestawie rekordów.

```
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
Liczony od zera indeks wstępnie zdefiniowane pole w zestawie rekordów kolekcji pól, do wyszukiwania według indeksu.

*FieldInfo*<br/>
Odwołanie do [cdaofieldinfo —](../../mfc/reference/cdaofieldinfo-structure.md) struktury.

*dwInfoOptions*<br/>
Opcje, które określają, które informacje o zestawie rekordów do pobrania. Dostępne opcje są wymienione w tym miejscu oraz co mogą spowodować, że funkcja zwróci. Aby uzyskać najlepszą wydajność należy pobrać tylko poziom potrzebnych informacji:

- `AFX_DAO_PRIMARY_INFO` (Ustawienie domyślne) Nazwa, typ, rozmiar, atrybuty

- `AFX_DAO_SECONDARY_INFO` Informacje o podstawowym, plus: numer pozycji, wymagane, Zezwalaj na tabeli źródłowej obcego Nazwa pola źródła zerową długość, kolejność sortowania,

- `AFX_DAO_ALL_INFO` Informacje podstawowe i pomocnicze, plus: tekst sprawdzania poprawności wartości domyślnej reguły walidacji

*lpszName*<br/>
Nazwa pola.

### <a name="remarks"></a>Uwagi

Jednej wersji funkcji umożliwia wyszukiwanie pola przez indeks. Druga wersja służy do wyszukiwania według nazwy pola.

Aby uzyskać opis zwrócone informacje, zobacz [cdaofieldinfo —](../../mfc/reference/cdaofieldinfo-structure.md) struktury. Ta struktura zawiera elementy członkowskie, które odnoszą się do elementów wymienionych powyżej w opisie informacji *dwInfoOptions*. W przypadku żądania informacji o jeden poziom, otrzymasz informacje dotyczące wszelkich poprzednich poziomach.

Aby uzyskać powiązane informacje zobacz temat "Atrybuty właściwości" w Pomocy programu DAO.

##  <a name="getfieldvalue"></a>  CDaoRecordset::GetFieldValue

Wywołaj tę funkcję elementu członkowskiego, aby pobrać dane w zestawie rekordów.

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

*lpszName*<br/>
Wskaźnik do ciągu, który zawiera nazwę pola.

*varValue*<br/>
Odwołanie do `COleVariant` obiekt, który będzie przechowywana wartość pola.

*nIndex*<br/>
Liczony od zera indeks pole w zestawie rekordów kolekcji pól, do wyszukiwania według indeksu.

### <a name="return-value"></a>Wartość zwracana

Dwie wersje `GetFieldValue` , zwrócona wartość zwracaną [COleVariant](../../mfc/reference/colevariant-class.md) obiekt, który zawiera wartość pola.

### <a name="remarks"></a>Uwagi

Pola można wyszukiwać według nazwy lub porządkowym.

> [!NOTE]
>  Jest bardziej wydajne wywołania jednej z wersji ta funkcja elementu członkowskiego, która przyjmuje `COleVariant` odwołanie do obiektu jako parametr zamiast wywoływania wersji, która zwraca `COleVariant` obiektu. Ostatnie wersje tej funkcji są utrzymywane na potrzeby utrzymywania zgodności z poprzednimi wersjami.

Użyj `GetFieldValue` i [SetFieldValue](#setfieldvalue) dynamicznie powiązać pola w czasie wykonywania, a nie statycznie powiązanie kolumn przy użyciu [dofieldexchange —](#dofieldexchange) mechanizm.

`GetFieldValue` i `DoFieldExchange` mechanizm mogą być połączone do zwiększenia wydajności. Na przykład użyć `GetFieldValue` do pobrania wartości, które są potrzebne tylko na żądanie, a następnie przypisz tego wywołania do przycisku "Więcej informacji" w interfejsie.

Aby uzyskać powiązane informacje zobacz tematy "Pola obiektu" i "Wartość właściwości" w Pomocy programu DAO.

##  <a name="getindexcount"></a>  CDaoRecordset::GetIndexCount

Wywołaj tę funkcję elementu członkowskiego, aby określić liczbę dostępnych w zestawie rekordów typ tabeli indeksów.

```
short GetIndexCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba indeksów w zestawie rekordów typ tabeli.

### <a name="remarks"></a>Uwagi

`GetIndexCount` jest przydatne w pętli wszystkich indeksów w zestawie rekordów. W tym celu należy użyć `GetIndexCount` w połączeniu z [GetIndexInfo](#getindexinfo). Jeśli wywołasz tej funkcji elementu członkowskiego na dynamicznego lub typ migawki zestawów rekordów MFC zgłasza wyjątek.

Aby uzyskać powiązane informacje zobacz temat "Atrybuty właściwości" w Pomocy programu DAO.

##  <a name="getindexinfo"></a>  CDaoRecordset::GetIndexInfo

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać różne rodzaje informacji na temat indeksu zdefiniowany w tabeli podstawowej, podstawowy zestaw rekordów.

```
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

*nIndex*<br/>
Liczony od zera indeks w tabeli indeksów kolekcji, wyszukiwanie według pozycji liczbowych.

*indexinfo*<br/>
Odwołanie do [cdaoindexinfo —](../../mfc/reference/cdaoindexinfo-structure.md) struktury.

*dwInfoOptions*<br/>
Opcje, które określają, które informacje o indeksie do pobrania. Dostępne opcje są wymienione w tym miejscu oraz co mogą spowodować, że funkcja zwróci. Aby uzyskać najlepszą wydajność należy pobrać tylko poziom potrzebnych informacji:

- `AFX_DAO_PRIMARY_INFO` (Ustawienie domyślne) Nazwa pola Info, pola

- `AFX_DAO_SECONDARY_INFO` Informacje o podstawowym, plus: podstawowej, unikatowe, Clustered IgnoreNulls, wymagane, obcych

- `AFX_DAO_ALL_INFO` Informacje podstawowe i pomocnicze, a także: liczności unikatowych wartości

*lpszName*<br/>
Wskaźnik na nazwę obiektu indeksu wyszukiwania według nazwy.

### <a name="remarks"></a>Uwagi

Jednej wersji funkcji pozwala wyszukiwać indeksu za pomocą jego pozycji w kolekcji. Druga wersja pozwala indeksu wyszukiwania według nazwy.

Aby uzyskać opis zwrócone informacje, zobacz [cdaoindexinfo —](../../mfc/reference/cdaoindexinfo-structure.md) struktury. Ta struktura zawiera elementy członkowskie, które odnoszą się do elementów wymienionych powyżej w opisie informacji *dwInfoOptions*. W przypadku żądania informacji o jeden poziom, otrzymasz informacje dotyczące wszelkich poprzednich poziomach.

Aby uzyskać powiązane informacje zobacz temat "Atrybuty właściwości" w Pomocy programu DAO.

##  <a name="getlastmodifiedbookmark"></a>  CDaoRecordset::GetLastModifiedBookmark

Wywołaj tę funkcję elementu członkowskiego, aby pobrać zakładki rekordu najbardziej ostatnio dodane lub zaktualizowane.

```
COleVariant GetLastModifiedBookmark();
```

### <a name="return-value"></a>Wartość zwracana

Element `COleVariant` zawierający zakładki, która wskazuje ostatnio dodane lub zmienione rekordu.

### <a name="remarks"></a>Uwagi

Po utworzeniu obiektu zestawu rekordów lub otwarte, każdego z jego rekordów już unikatowe zakładki, gdy je obsługuje. Wywołaj [getbookmark —](#getbookmark) do określenia, czy zestaw rekordów obsługuje zakładek. Jeśli zestaw rekordów nie obsługuje zakładek, `CDaoException` zgłaszany.

Po dodaniu rekordu, pojawia się na końcu zestawu rekordów, a nie jest bieżącym rekordem. Aby wprowadzić nowy rekord bieżący, należy wywołać `GetLastModifiedBookmark` , a następnie wywołać `SetBookmark` aby powrócić do nowo dodanego rekordu.

Aby uzyskać powiązane informacje zobacz temat "LastModified Property" w Pomocy programu DAO.

##  <a name="getlockingmode"></a>  CDaoRecordset::GetLockingMode

Wywołaj tę funkcję elementu członkowskiego, można określić typu w celu blokowania dla zestawu rekordów.

```
BOOL GetLockingMode();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli typ blokady jest pesymistycznego, w przeciwnym razie 0 dla rekordu optymistyczne blokowanie.

### <a name="remarks"></a>Uwagi

Gdy pesymistycznego blokowania jest aktywna, strony danych zawierające rekord, edytowany jest zablokowane, tak szybko, jak należy wywołać [Edytuj](#edit) funkcja elementu członkowskiego. Strona jest odblokowany, gdy wywołujesz [aktualizacji](#update) lub [Zamknij](#close) funkcji członkowskiej lub dowolnych operacji przenoszenia lub wyszukiwania.

Gdy optymistyczne blokowanie obowiązuje strony danych zawierające rekord jest zablokowany, tylko wtedy, gdy rekord jest aktualizowana przy użyciu `Update` funkcja elementu członkowskiego.

Podczas pracy ze źródłami danych ODBC, tryb blokowania jest zawsze optymistyczne.

Aby uzyskać powiązane informacje zobacz tematy "LockEdits Property" i "Blokowanie zachowanie wielodostępnego aplikacjami" w Pomocy programu DAO.

##  <a name="getname"></a>  CDaoRecordset::GetName

Wywołaj tę funkcję elementu członkowskiego, aby pobrać nazwy zestawu rekordów.

```
CString GetName();
```

### <a name="return-value"></a>Wartość zwracana

Element `CString` zawierający nazwę zestawu rekordów.

### <a name="remarks"></a>Uwagi

Nazwa zestawu rekordów musi rozpoczynać się od litery i może zawierać maksymalnie 40 znaków. Może zawierać cyfry i znaki podkreślenia, ale nie może zawierać znaków interpunkcyjnych lub miejsca do magazynowania.

Aby uzyskać powiązane informacje zobacz temat "Nazwa właściwości" w Pomocy programu DAO.

##  <a name="getparamvalue"></a>  CDaoRecordset::GetParamValue

Wywołaj tę funkcję elementu członkowskiego, aby pobrać bieżącą wartość określonego parametru przechowywana w obiekcie DAOParameter bazowego.

```
virtual COleVariant GetParamValue(int nIndex);
virtual COleVariant GetParamValue(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Wartości liczbowych pozycja parametru w obiekt źródłowy DAOParameter.

*lpszName*<br/>
Nazwa parametru żądanymi wartościami.

### <a name="return-value"></a>Wartość zwracana

Obiekt klasy [COleVariant](../../mfc/reference/colevariant-class.md) zawierającą wartość parametru.

### <a name="remarks"></a>Uwagi

Według nazwy lub jego wartości liczbowych pozycji w kolekcji, można uzyskać dostęp do parametru.

Aby uzyskać powiązane informacje zobacz temat "Parametr obiektu" w Pomocy programu DAO.

##  <a name="getpercentposition"></a>  CDaoRecordset::GetPercentPosition

Podczas pracy z dynamicznego lub zestawu rekordów typu migawka, jeśli wywołasz `GetPercentPosition` przed pełni wypełnianie zestawu rekordów, przemieszczenie jest określana względem liczby rekordów dostępne wskazane przez wywołanie metody [getrecordcount —](#getrecordcount).

```
float GetPercentPosition();
```

### <a name="return-value"></a>Wartość zwracana

Liczba od 0 do 100, która określa przybliżona lokalizacja bieżącego rekordu w obiekcie rekordów na podstawie procentu rekordów w zestawie rekordów.

### <a name="remarks"></a>Uwagi

Można przenieść do ostatniego rekordu, wywołując [MoveLast](#movelast) na pełne populacji wszystkich zestawów rekordów, ale to może zająć znaczną ilość czasu.

Możesz wywołać `GetPercentPosition` na wszystkich trzech typów obiektów zestawu rekordów, w tym tabel bez indeksów. Jednak nie można wywołać `GetPercentPosition` tylko do przodu migawek przewijania lub zestaw rekordów otwierane z zapytania przekazującego względem zewnętrznej bazy danych. Jeśli nie ma bieżącego rekordu lub he bieżący rekord został usunięty, `CDaoException` zgłaszany.

Aby uzyskać powiązane informacje zobacz temat "PercentPosition Property" w Pomocy programu DAO.

##  <a name="getrecordcount"></a>  CDaoRecordset::GetRecordCount

Wywołaj tę funkcję elementu członkowskiego, aby dowiedzieć się, jak wiele rekordów w zestawie rekordów były używane.

```
long GetRecordCount();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę rekordów, dostępne w obiekcie zestawu rekordów.

### <a name="remarks"></a>Uwagi

`GetRecordCount` wskazuje liczbę rekordów są zawarte w dynamicznego lub zestawu rekordów typu migawka, dopóki wszystkie rekordy były używane. Wywołanie tej funkcji elementu członkowskiego może zająć znaczną ilość czasu, aby zakończyć.

Po ostatnim rekordzie były używane, zwracana wartość wskazuje sumę Cofnięto usunięcie rekordów w zestawie rekordów. Aby wymusić ostatniego rekordu można uzyskać dostęp, należy wywołać `MoveLast` lub `FindLast` funkcja elementu członkowskiego zestawu rekordów. Liczba SQL umożliwia również określić przybliżoną liczbę rekordów, które zwróci zapytania.

Jak aplikacja służy do usuwania rekordów w zestawie rekordów dynamicznego, wartość zwracana przez `GetRecordCount` zmniejsza. Jednak rekordy zostały usunięte przez innych użytkowników nie są uwzględniane przy `GetRecordCount` aż bieżącego rekordu jest w stanie usunięty rekord. Jeśli wykonywania transakcji, która wpływa na liczbę rekordów, a następnie Wycofaj tę transakcję `GetRecordCount` nie będzie odzwierciedlał rzeczywista liczba pozostałych rekordów.

Wartość `GetRecordCount` z zestawu rekordów typu migawka nie ma wpływu zmian w tabelach źródłowych.

Wartość `GetRecordCount` z typem tabeli zestaw rekordów odzwierciedla przybliżoną liczbę rekordów w tabeli i jest zależna od razu zgodnie z tabeli rekordy są dodawane i usuwane.

Zestaw rekordów z żadne rekordy nie zwraca wartość 0. Podczas pracy z tabelami dołączonych lub baz danych ODBC, `GetRecordCount` zawsze zwraca wartość - 1. Wywoływanie `Requery` funkcja elementu członkowskiego na zestawie rekordów resetuje wartość `GetRecordCount` tak, jakby zapytania były wykonany ponownie.

Aby uzyskać powiązane informacje zobacz temat "Właściwości RecordCount" w Pomocy programu DAO.

##  <a name="getsql"></a>  CDaoRecordset::GetSQL

Wywołaj tę funkcję elementu członkowskiego, aby pobrać instrukcji SQL, który został użyty do wybierania rekordów w zestawie rekordów, gdy został on otwarty.

```
CString GetSQL() const;
```

### <a name="return-value"></a>Wartość zwracana

Element `CString` zawiera instrukcję SQL.

### <a name="remarks"></a>Uwagi

Są to zazwyczaj SQL **wybierz** instrukcji.

Ciąg zwracany przez `GetSQL` zwykle różni się od dowolny ciąg może być przekazana do zestawu rekordów w *lpszSQL* parametr [Otwórz](#open) funkcja elementu członkowskiego. Jest to spowodowane zestawu rekordów tworzy pełną instrukcję SQL, oparte na przekazany do `Open`określony za pomocą ClassWizard i co określono w [m_strFilter](#m_strfilter) i [m_strSort](#m_strsort) składowych danych.

> [!NOTE]
>  Wywołaj tę funkcję elementu członkowskiego tylko po wywołaniu `Open`.

Aby uzyskać powiązane informacje zobacz temat "Właściwości SQL" w Pomocy programu DAO.

##  <a name="gettype"></a>  CDaoRecordset::GetType

Wywołaj tę funkcję elementu członkowskiego, po otwarciu zestawu rekordów można ustalić typu obiektu zestawu rekordów.

```
short GetType();
```

### <a name="return-value"></a>Wartość zwracana

Jeden z następujących wartości, które wskazuje typ zestaw rekordów:

- `dbOpenTable` Typ tabeli rekordów

- `dbOpenDynaset` Dynamicznego zestawu rekordów

- `dbOpenSnapshot` Zestaw rekordów typu migawka

### <a name="remarks"></a>Uwagi

Aby uzyskać powiązane informacje zobacz temat "Właściwość Type" w Pomocy programu DAO.

##  <a name="getvalidationrule"></a>  CDaoRecordset::GetValidationRule

Wywołaj tę funkcję elementu członkowskiego, aby ustalić reguły używane do sprawdzania poprawności danych.

```
CString GetValidationRule();
```

### <a name="return-value"></a>Wartość zwracana

A `CString` obiekt, który zawiera wartość, która sprawdza poprawność danych w rekordzie, ponieważ ona jest zmieniane ani dodawane do tabeli.

### <a name="remarks"></a>Uwagi

Ta reguła jest oparte na tekście i jest stosowany na każdym razem, gdy zostanie zmieniony w tabeli podstawowej. MFC zgłasza wyjątek, jeśli danych jest niedozwolona. Komunikat o błędzie zwracany jest tekst właściwości komunikat obiektu bazowego pola, jeśli zostanie określony, lub wyrażenia, określony przez właściwość ValidationRule obiektu bazowego pola. Możesz wywołać [GetValidationText](#getvalidationtext) uzyskać tekst komunikatu o błędzie.

Na przykład pola w rekordzie, który wymaga dzień miesiąca może mieć reguły sprawdzania poprawności takich jak "BETWEEN dzień 1 do 31."

Aby uzyskać powiązane informacje zobacz temat "ValidationRule Property" w Pomocy programu DAO.

##  <a name="getvalidationtext"></a>  CDaoRecordset::GetValidationText

Wywołaj tę funkcję elementu członkowskiego, aby pobrać tekstu komunikat własności obiektu pola źródłowego.

```
CString GetValidationText();
```

### <a name="return-value"></a>Wartość zwracana

A `CString` obiekt zawierający tekst komunikatu, który jest wyświetlany, gdy wartość pola nie spełnia warunków reguły sprawdzania poprawności obiektu bazowego pola.

### <a name="remarks"></a>Uwagi

Aby uzyskać powiązane informacje zobacz temat "Property komunikat" w Pomocy programu DAO.

##  <a name="isbof"></a>  CDaoRecordset::IsBOF

Wywołaj tę funkcję elementu członkowskiego, zanim przewiń z rekordu do rekordu, aby dowiedzieć się, czy wykonano przed pierwszym rekordzie zestawu rekordów.

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli zestaw rekordów nie zawiera żadnych rekordów lub mieć przewiniesz wstecz przed pierwszym rekordzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Można również wywołać `IsBOF` wraz z `IsEOF` ustalenie, czy zestaw rekordów zawiera jakiekolwiek rekordy lub jest pusty. Natychmiast, po wywołaniu metody `Open`, jeśli zestaw rekordów nie zawiera żadnych rekordów `IsBOF` zwraca wartość różną od zera. Po otwarciu zestawu rekordów, który ma co najmniej jeden rekord, pierwszy rekord jest bieżący rekord oraz `IsBOF` zwraca wartość 0.

Jeśli pierwszy rekord jest bieżący rekord i wywołania `MovePrev`, `IsBOF` następnie zwraca wartość różną od zera. Jeśli `IsBOF` zwraca wartość różną od zera i wywołać `MovePrev`, zgłaszany jest wyjątek. Jeśli `IsBOF` zwraca wartość różną od zera, bieżący rekord jest niezdefiniowane i dowolną akcję, która wymaga bieżącego rekordu spowoduje wyjątek.

Efekt określonych metod `IsBOF` i `IsEOF` ustawienia:

- Wywoływanie `Open*` wewnętrznie sprawia, że pierwszy rekord w zestawie rekordów bieżącego rekordu przez wywołanie metody `MoveFirst`. Dlatego wywołanie `Open` na pusty zestaw rekordów przyczyny `IsBOF` i `IsEOF` zwracać wartość różną od zera. (Zobacz poniższą tabelę zachowanie niepowodzenia `MoveFirst` lub `MoveLast` wywołania.)

- Wszystkie operacje przenoszenia, które pomyślnie Zlokalizuj rekord spowodować, że oba `IsBOF` i `IsEOF` do zwracają 0.

- `AddNew` Następuje wywołanie `Update` spowoduje wywołanie, które pomyślnie Wstawia nowy rekord `IsBOF` do zwrócenia 0, ale tylko wtedy, gdy `IsEOF` już jest różna od zera. Stan `IsEOF` zawsze pozostają bez zmian. Określone przez aparat bazy danych Microsoft Jet bieżący wskaźnik rekordu pusty zestaw rekordów jest na końcu pliku, więc każdy nowy rekord dodaje się po bieżącego rekordu.

- Wszelkie `Delete` wywołania, nawet wtedy, gdy spowoduje usunięcie tylko pozostałych rekordów z zestawu rekordów nie zmieni się wartość `IsBOF` lub `IsEOF`.

W poniższej tabeli przedstawiono operacje przenoszenia dozwolone z różnymi kombinacjami `IsBOF` /  `IsEOF`.

||MoveFirst, MoveLast|Moveprev —,<br /><br /> Przenieś < 0|Przenieść 0|MoveNext,<br /><br /> Przenieś > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`= wartość różną od zera,<br /><br /> `IsEOF`=0|Dozwolone|Wyjątek|Wyjątek|Dozwolone|
|`IsBOF`=0,<br /><br /> `IsEOF`= wartość różną od zera|Dozwolone|Dozwolone|Wyjątek|Wyjątek|
|Zarówno wartość różną od zera|Wyjątek|Wyjątek|Wyjątek|Wyjątek|
|Zarówno 0|Dozwolone|Dozwolone|Dozwolone|Dozwolone|

Zezwalanie operacji przenoszenia nie oznacza to operacja pomyślnie zlokalizuje rekordu. Wskazuje jedynie, próba wykonania określonej operacji przenoszenia jest dozwolone, a nie wygeneruje wyjątku. Wartość `IsBOF` i `IsEOF` funkcje składowe mogą ulec zmianie w wyniku próby przenoszenia.

Wpływ operacji przenoszenia, których nie można odnaleźć rekordu na wartość `IsBOF` i `IsEOF` ustawienia zostały przedstawione w poniższej tabeli.

||IsBOF|IsEOF|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|Wartość różną od zera|Wartość różną od zera|
|`Move` 0|Nie wprowadzono zmian|Nie wprowadzono zmian|
|`MovePrev`, `Move` < 0|Wartość różną od zera|Nie wprowadzono zmian|
|`MoveNext`, `Move` > 0|Nie wprowadzono zmian|Wartość różną od zera|

Aby uzyskać powiązane informacje, zobacz temat "BOF, EOF właściwości" w Pomocy programu DAO.

##  <a name="isdeleted"></a>  CDaoRecordset::IsDeleted

Wywołaj tę funkcję elementu członkowskiego, aby ustalić, czy bieżący rekord został usunięty.

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli zestaw rekordów jest ustawiony na rekordzie usunięte; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Po przewinięciu rekord a `IsDeleted` zwraca wartość TRUE (niezerową), a następnie musi przewiń do innego rekordu, zanim będzie można wykonywać inne operacje zestawu rekordów.

> [!NOTE]
>  Nie potrzebujesz sprawdzić stan usuniętych rekordów w zestawie rekordów migawki lub typ tabeli. Ponieważ nie można usunąć rekordów z migawki, nie ma potrzeby wywołać `IsDeleted`. Dla zestawów rekordów typ tabeli usunięte rekordy są faktycznie usuwane z zestawu rekordów. Gdy rekord został usunięty, przez Ciebie innego użytkownika lub w innym zestawie rekordów, nie przewiń do tego rekordu. W związku z tym, nie ma potrzeby wywołać `IsDeleted`.

Jeśli usuniesz rekord z zestawu dynamicznego, zostanie on usunięty z zestawu rekordów i nie przewiń do tego rekordu. Jednak w przypadku rekordu w dynamiczny zostaną usunięte przez innego użytkownika lub w innym zestawie rekordów na podstawie tej samej tabeli `IsDeleted` zwraca wartość TRUE, gdy później przewiń do tego rekordu.

Aby uzyskać powiązane informacje zobacz tematy "Usuń metodę", "Ostatnia modyfikacja właściwości" i "Trybu edycji właściwości" w Pomocy programu DAO.

##  <a name="iseof"></a>  CDaoRecordset::IsEOF

Wywołaj tę funkcję elementu członkowskiego, przewijania z rekordu, rekord, aby dowiedzieć się, czy wykonano poza ostatnim rekordzie zestawu rekordów.

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli zestaw rekordów nie zawiera żadnych rekordów lub jeśli przewiniesz poza ostatnim rekordzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Można również wywołać `IsEOF` ustalenie, czy zestaw rekordów zawiera jakiekolwiek rekordy lub jest pusty. Natychmiast, po wywołaniu metody `Open`, jeśli zestaw rekordów nie zawiera żadnych rekordów `IsEOF` zwraca wartość różną od zera. Po otwarciu zestawu rekordów, który ma co najmniej jeden rekord, pierwszy rekord jest bieżący rekord oraz `IsEOF` zwraca wartość 0.

Jeśli ostatni rekord jest bieżący rekord po wywołaniu `MoveNext`, `IsEOF` następnie zwraca wartość różną od zera. Jeśli `IsEOF` zwraca wartość różną od zera i wywołać `MoveNext`, zgłaszany jest wyjątek. Jeśli `IsEOF` zwraca wartość różną od zera, bieżący rekord jest niezdefiniowane i dowolną akcję, która wymaga bieżącego rekordu spowoduje wyjątek.

Efekt określonych metod `IsBOF` i `IsEOF` ustawienia:

- Wywoływanie `Open` wewnętrznie sprawia, że pierwszy rekord w zestawie rekordów bieżącego rekordu przez wywołanie metody `MoveFirst`. Dlatego wywołanie `Open` na pusty zestaw rekordów przyczyny `IsBOF` i `IsEOF` zwracać wartość różną od zera. (Zobacz poniższą tabelę zachowanie niepowodzenia `MoveFirst` wywołania.)

- Wszystkie operacje przenoszenia, które pomyślnie Zlokalizuj rekord spowodować, że oba `IsBOF` i `IsEOF` do zwracają 0.

- `AddNew` Następuje wywołanie `Update` spowoduje wywołanie, które pomyślnie Wstawia nowy rekord `IsBOF` do zwrócenia 0, ale tylko wtedy, gdy `IsEOF` już jest różna od zera. Stan `IsEOF` zawsze pozostają bez zmian. Określone przez aparat bazy danych Microsoft Jet bieżący wskaźnik rekordu pusty zestaw rekordów jest na końcu pliku, więc każdy nowy rekord dodaje się po bieżącego rekordu.

- Wszelkie `Delete` wywołania, nawet wtedy, gdy spowoduje usunięcie tylko pozostałych rekordów z zestawu rekordów nie zmieni się wartość `IsBOF` lub `IsEOF`.

W poniższej tabeli przedstawiono operacje przenoszenia dozwolone z różnymi kombinacjami `IsBOF` /  `IsEOF`.

||MoveFirst, MoveLast|Moveprev —,<br /><br /> Przenieś < 0|Przenieść 0|MoveNext,<br /><br /> Przenieś > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`= wartość różną od zera,<br /><br /> `IsEOF`=0|Dozwolone|Wyjątek|Wyjątek|Dozwolone|
|`IsBOF`=0,<br /><br /> `IsEOF`= wartość różną od zera|Dozwolone|Dozwolone|Wyjątek|Wyjątek|
|Zarówno wartość różną od zera|Wyjątek|Wyjątek|Wyjątek|Wyjątek|
|Zarówno 0|Dozwolone|Dozwolone|Dozwolone|Dozwolone|

Zezwalanie operacji przenoszenia nie oznacza to operacja pomyślnie zlokalizuje rekordu. Wskazuje jedynie, próba wykonania określonej operacji przenoszenia jest dozwolone, a nie wygeneruje wyjątku. Wartość `IsBOF` i `IsEOF` funkcje składowe mogą ulec zmianie w wyniku próby przenoszenia.

Wpływ operacji przenoszenia, których nie można odnaleźć rekordu na wartość `IsBOF` i `IsEOF` ustawienia zostały przedstawione w poniższej tabeli.

||IsBOF|IsEOF|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|Wartość różną od zera|Wartość różną od zera|
|`Move` 0|Nie wprowadzono zmian|Nie wprowadzono zmian|
|`MovePrev`, `Move` < 0|Wartość różną od zera|Nie wprowadzono zmian|
|`MoveNext`, `Move` > 0|Nie wprowadzono zmian|Wartość różną od zera|

Aby uzyskać powiązane informacje, zobacz temat "BOF, EOF właściwości" w Pomocy programu DAO.

##  <a name="isfielddirty"></a>  CDaoRecordset::IsFieldDirty

Wywołaj tę funkcję elementu członkowskiego, aby ustalić, czy określone pole składowej danych z zestawu dynamicznego został oflagowany jako "zakłóconych" (zmienić).

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>Parametry

*Wa*<br/>
Wskaźnik do składowej danych pola, którego stan chcesz sprawdzić lub wartość NULL, aby ustalić, czy dowolna z pól jest zanieczyszczony.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli określone pole składowej danych jest oznaczony jako zanieczyszczony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Dane we wszystkich elementach danych zanieczyszczone pola zostanie przeniesiona do rekordu w źródle danych podczas aktualizacji bieżący rekord przez wywołanie `Update` funkcji składowej typu `CDaoRecordset` (po wywołaniu `Edit` lub `AddNew`). Za pomocą tej wiedzy, należy wykonać dalsze czynności, takie jak unflagging pole składowej danych, które można oznaczyć kolumny, więc nie można zapisać do źródła danych.

`IsFieldDirty` jest implementowane za pomocą `DoFieldExchange`.

##  <a name="isfieldnull"></a>  CDaoRecordset::IsFieldNull

Wywołaj tę funkcję elementu członkowskiego, aby ustalić, czy określone pole składowej danych, które zestawu rekordów został oflagowany jako wartości Null.

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>Parametry

*Wa*<br/>
Wskaźnik do składowej danych pola, którego stan chcesz sprawdzić lub wartość NULL, aby sprawdzić, czy są dowolne z pól o wartości Null.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli element członkowski danych określone pole jest oznaczone jako Null; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

(W terminologii bazy danych o wartości Null oznacza, że "po żadnej wartości" i nie jest taka sama jak wartość NULL w języku C++) Element członkowski danych pola jest oznaczony jako wartość Null, jest interpretowany jako kolumnę bieżącego rekordu, dla których nie ma żadnej wartości.

> [!NOTE]
>  W niektórych sytuacjach przy użyciu `IsFieldNull` może być mało wydajne, tak jak pokazano w poniższym przykładzie kodu:

[!code-cpp[NVC_MFCDatabase#5](../../mfc/codesnippet/cpp/cdaorecordset-class_5.cpp)]

> [!NOTE]
>  Jeśli używasz wiązanie dynamiczne rekordów, bez pochodząca od `CDaoRecordset`, należy użyć VT_NULL, jak pokazano w przykładzie.

##  <a name="isfieldnullable"></a>  CDaoRecordset::IsFieldNullable

Wywołaj tę funkcję elementu członkowskiego, aby ustalić, czy określone pole składowej danych "nullable" (może być ustawiona na wartość Null; C++ o wartości NULL nie jest taka sama jak wartość Null, oznacza to, w terminologii bazy danych "posiadanie żadnej wartości").

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>Parametry

*Wa*<br/>
Wskaźnik do składowej danych pola, którego stan chcesz sprawdzić lub wartość NULL, aby sprawdzić, czy są dowolne z pól o wartości Null.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli określone pole składowej danych można wprowadzić wartość Null; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pola, które nie może mieć wartości Null, musi mieć wartość. Jeśli spróbujesz ustawia pole na wartość Null, podczas dodawania lub aktualizowania rekordu źródła danych odrzuci dodanie lub aktualizacja, i `Update` spowoduje zgłoszenie wyjątku. Wyjątek występuje po wywołaniu `Update`, nie wtedy, gdy wywołujesz `SetFieldNull`.

##  <a name="isopen"></a>  CDaoRecordset::IsOpen

Wywołaj tę funkcję elementu członkowskiego, aby ustalić, czy zestaw rekordów jest otwarty.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli obiekty zestawów rekordów `Open` lub `Requery` wcześniej została wywołana funkcja elementu członkowskiego i nie została zamknięta zestawu rekordów; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

##  <a name="m_bcheckcachefordirtyfields"></a>  CDaoRecordset::m_bCheckCacheForDirtyFields

Zawiera flagę wskazującą, czy pola pamięci podręcznej są automatycznie oznaczony jako zakłóconych (zmienione) i Null.

### <a name="remarks"></a>Uwagi

Flaga wartość domyślna to TRUE. Ustawienie to element członkowski danych steruje całego mechanizmu podwójnego buforowania. Jeśli flaga jest ustawiona na wartość TRUE, można wyłączyć buforowanie na podstawie pól pola, przy użyciu mechanizmu DFX. Jeśli flaga jest ustawiona na wartość FALSE, należy wywołać `SetFieldDirty` i `SetFieldNull` samodzielnie.

Ustaw ten element członkowski danych przed wywołaniem `Open`. Ten mechanizm jest przede wszystkim do łatwe w użyciu. Wydajność może być wolniejsze z powodu podwójnego buforowania pól, zostaną wprowadzone zmiany.

##  <a name="m_nfields"></a>  CDaoRecordset::m_nFields

Zawiera liczbę elementy członkowskie danych pola w klasie zestawu rekordów i liczba kolumn wybranych przez zestaw rekordów ze źródła danych.

### <a name="remarks"></a>Uwagi

Konstruktor dla klasy zestaw rekordów musi inicjować `m_nFields` z poprawną liczbę statycznie powiązanych pól. ClassWizard zapisuje ten proces inicjowania dla Ciebie, gdy używasz Aby zadeklarować klasy zestawu rekordów. Można go także zapisać ręcznie.

Środowisko wykorzystuje tę liczbę do zarządzania interakcją między elementy członkowskie danych pola i odpowiednie kolumny bieżącego rekordu w źródle danych.

> [!NOTE]
>  Ta liczba musi odpowiadać liczba kolumn wyjściowych zarejestrowane w `DoFieldExchange` po wywołaniu `SetFieldType` z parametrem `CDaoFieldExchange::outputColumn`.

Można powiązać kolumny dynamicznie przez zasadzie `CDaoRecordset::GetFieldValue` i `CDaoRecordset::SetFieldValue`. Jeśli tak zrobisz, nie trzeba zwiększyć liczby w `m_nFields` aby odzwierciedlić liczba funkcji DFX wywołań swojej `DoFieldExchange` funkcja elementu członkowskiego.

##  <a name="m_nparams"></a>  CDaoRecordset::m_nParams

Zawiera liczbę elementy członkowskie danych parametru w klasie rekordów — liczba parametrów przekazaną za pomocą zapytań w zestawie rekordów.

### <a name="remarks"></a>Uwagi

Jeśli klasa zestaw rekordów zawiera wszystkie elementy członkowskie danych parametru, Konstruktor dla klasy należy zainicjować *m_nparams —* z prawidłową liczbą. Wartość *m_nparams —* wartość domyślna to 0. Jeśli dodasz elementy członkowskie danych parametru — co musisz zrobić ręcznie — musisz również ręcznie dodać inicjalizacji w konstruktorze klasy, aby odzwierciedlić liczba parametrów (musi być przynajmniej tak duże jak liczba '' symbole zastępcze w wywołaniach usługi *m_strFilter*  lub *m_strSort* ciągu).

Struktura używa tego numeru, gdy go parametryzuje dane zapytania w zestawie rekordów.

> [!NOTE]
>  Ta liczba musi odpowiadać liczbę "params" zarejestrowanego w `DoFieldExchange` po wywołaniu `SetFieldType` z parametrem `CFieldExchange::param`.

Aby uzyskać powiązane informacje zobacz temat "Parametr obiektu" w Pomocy programu DAO.

##  <a name="m_pdaorecordset"></a>  CDaoRecordset::m_pDAORecordset

Zawiera wskaźnik do interfejsu OLE do bazowego obiektu zestawu rekordów DAO `CDaoRecordset` obiektu.

### <a name="remarks"></a>Uwagi

Jeśli potrzebujesz dostępu do interfejsu DAO bezpośrednio za pomocą tego wskaźnika.

Aby uzyskać powiązane informacje zobacz temat "Obiekt zestawu rekordów" w Pomocy programu DAO.

##  <a name="m_pdatabase"></a>  CDaoRecordset::m_pDatabase

Zawiera wskaźnik do `CDaoDatabase` obiektu za pomocą których zestaw rekordów jest połączony ze źródłem danych.

### <a name="remarks"></a>Uwagi

Ta zmienna jest ustawiona na dwa sposoby. Zazwyczaj należy przekazać wskaźnik do już otwartych `CDaoDatabase` obiektu podczas konstruowania obiektu zestawu rekordów. Jeśli zamiast tego należy przekazać NULL `CDaoRecordset` tworzy `CDaoDatabase` obiekt dla Ciebie i otwiera go. W obu przypadkach `CDaoRecordset` przechowuje wskaźnik w tej zmiennej.

Zwykle nie bezpośrednio należy użyć wskaźnika przechowywania w `m_pDatabase`. Jeśli piszesz własne rozszerzenia `CDaoRecordset`, jednak czasami trzeba za pomocą wskaźnika. Na przykład może być potrzebny wskaźnika można zgłaszać własne `CDaoException`(s).

Aby uzyskać powiązane informacje zobacz temat "Obiektu bazy danych" w Pomocy programu DAO.

##  <a name="m_strfilter"></a>  CDaoRecordset::m_strFilter

Zawiera ciąg, który służy do konstruowania **gdzie** klauzula instrukcji języka SQL.

### <a name="remarks"></a>Uwagi

Nie zawiera słowo zastrzeżone **gdzie** do filtrowania zestawu rekordów. Użyj tego elementu członkowskiego danych nie ma zastosowania do zestawów rekordów typu tabeli. Korzystanie z `m_strFilter` nie obowiązuje podczas otwierania zestawu rekordów przy użyciu `CDaoQueryDef` wskaźnika.

Użyj formatu daty Stanów Zjednoczonych (dzień miesiąc rok) podczas filtrowania pola zawierające dat, nawet jeśli nie używasz wersji US aparatu bazy danych Microsoft Jet; w przeciwnym razie dane nie mogą być filtrowane, zgodnie z oczekiwaniami.

Aby uzyskać powiązane informacje zobacz temat "Właściwość filtra" w Pomocy programu DAO.

##  <a name="m_strsort"></a>  CDaoRecordset::m_strSort

Zawiera ciąg zawierający **ORDERBY** klauzuli instrukcji SQL bez słowa zastrzeżone **ORDERBY**.

### <a name="remarks"></a>Uwagi

Można sortować na obiektach zestawu rekordów i migawki — dynamicznego.

Nie można posortować obiekty zestawu rekordów typu tabeli. Aby określić kolejność sortowania rekordów typ tabeli, należy wywołać [SetCurrentIndex](#setcurrentindex).

Korzystanie z *m_strSort* nie obowiązuje podczas otwierania zestawu rekordów przy użyciu `CDaoQueryDef` wskaźnika.

Aby uzyskać powiązane informacje zobacz temat "Właściwość sortowania" w Pomocy programu DAO.

##  <a name="move"></a>  CDaoRecordset::Move

Wywołaj tę funkcję elementu członkowskiego, aby umieścić zestaw rekordów *lRows* rekordów z bieżącego rekordu.

```
virtual void Move(long lRows);
```

### <a name="parameters"></a>Parametry

*lRows*<br/>
Liczba rekordów do przechodzenia do przodu lub Wstecz. Wartości dodatnich Przesuń do przodu, pod koniec zestawu rekordów. Wartości ujemne do tyłu, kierunku początku.

### <a name="remarks"></a>Uwagi

Można przenieść do przodu lub Wstecz. `Move( 1 )` jest odpowiednikiem `MoveNext`, i `Move( -1 )` jest odpowiednikiem `MovePrev`.

> [!CAUTION]
>  Wywołanie dowolnego z `Move` funkcje zgłasza wyjątek, jeśli zestaw rekordów nie zawiera żadnych rekordów. Ogólnie rzecz biorąc, wywołaj obydwa `IsBOF` i `IsEOF` przed wykonaniem operacji przenoszenia w celu określenia, czy zestaw rekordów zawiera wszystkie rekordy. Po wywołaniu metody `Open` lub `Requery`, albo wywołaj `IsBOF` lub `IsEOF`.

> [!NOTE]
>  Jeśli przewiniesz w przeszłości na początku lub na końcu zestawu rekordów ( `IsBOF` lub `IsEOF` zwraca wartość różną od zera), po wywołaniu `Move` zgłasza `CDaoException`.

> [!NOTE]
>  Jeśli należy wywołać dowolną z `Move` funkcji podczas bieżącego rekordu zaktualizowano lub dodano i aktualizacje zostaną utracone bez ostrzeżenia.

Gdy wywołujesz `Move` tylko do przodu migawkę przewijania, *lRows* parametr musi być dodatnią liczbą całkowitą i zakładki nie są dozwolone, dzięki czemu można przenosić do przodu tylko.

Aby imię, nazwisko, następnej lub poprzedniej rejestrowanie w zestawie rekordów bieżącego rekordu, wywołania `MoveFirst`, `MoveLast`, `MoveNext`, lub `MovePrev` funkcja elementu członkowskiego.

Aby uzyskać powiązane informacje, zobacz tematy "Przenieś metody" i "MoveNext MoveFirst, MoveLast, metody MovePrevious" w Pomocy programu DAO.

##  <a name="movefirst"></a>  CDaoRecordset::MoveFirst

Wywołaj tę funkcję elementu członkowskiego, aby pierwszy rekord w zestawie rekordów (jeśli istnieje) bieżącego rekordu.

```
void MoveFirst();
```

### <a name="remarks"></a>Uwagi

Nie trzeba wywoływać `MoveFirst` bezpośrednio po otwarciu zestawu rekordów. W tym czasie pierwszego rekordu (jeśli istnieje) jest automatycznie bieżącego rekordu.

> [!CAUTION]
>  Wywołanie dowolnego z `Move` funkcje zgłasza wyjątek, jeśli zestaw rekordów nie zawiera żadnych rekordów. Ogólnie rzecz biorąc, wywołaj obydwa `IsBOF` i `IsEOF` przed wykonaniem operacji przenoszenia w celu określenia, czy zestaw rekordów zawiera wszystkie rekordy. Po wywołaniu metody `Open` lub `Requery`, albo wywołaj `IsBOF` lub `IsEOF`.

> [!NOTE]
>  Jeśli należy wywołać dowolną z `Move` funkcji podczas bieżącego rekordu zaktualizowano lub dodano i aktualizacje zostaną utracone bez ostrzeżenia.

Użyj `Move` funkcji przenoszenia między rekordami bez stosowania warunku. Użyj operacji Znajdź można zlokalizować rekordów w dynamicznego lub obiekty zestawów rekordów typu migawka, który spełnia określony warunek. Aby zlokalizować rekord w obiekcie zestawu rekordów typ tabeli, należy wywołać `Seek`.

Jeśli zestaw rekordów odwołuje się do zestawu rekordów typ tabeli, przenoszenia następuje bieżący indeks tabeli. Można ustawić bieżącego indeksu za pomocą właściwości indeksu obiektu bazowego DAO. Jeśli bieżący indeks nie jest ustawiona, kolejność rekordów zwracany jest niezdefiniowane.

Jeśli wywołasz `MoveLast` na obiekt zestawu rekordów na podstawie zapytania SQL lub querydef, zapytanie jest zmuszony do ukończenia i w pełni zawiera obiekt zestawu rekordów.

Nie można wywołać `MoveFirst` lub `MovePrev` funkcji składowej z przewijaniem migawki tylko do przodu.

Aby przenieść pozycja bieżący rekord w obiekty zestawów rekordów konkretną liczbę rekordów do przodu lub do tyłu, należy wywołać `Move`.

Aby uzyskać powiązane informacje, zobacz tematy "Przenieś metody" i "MoveNext MoveFirst, MoveLast, metody MovePrevious" w Pomocy programu DAO.

##  <a name="movelast"></a>  CDaoRecordset::MoveLast

Wywołaj tę funkcję elementu członkowskiego, aby ostatni rekord (jeśli istnieją) w zestawie rekordów bieżącego rekordu.

```
void MoveLast();
```

### <a name="remarks"></a>Uwagi

> [!CAUTION]
>  Wywołanie dowolnego z `Move` funkcje zgłasza wyjątek, jeśli zestaw rekordów nie zawiera żadnych rekordów. Ogólnie rzecz biorąc, wywołaj obydwa `IsBOF` i `IsEOF` przed wykonaniem operacji przenoszenia w celu określenia, czy zestaw rekordów zawiera wszystkie rekordy. Po wywołaniu metody `Open` lub `Requery`, albo wywołaj `IsBOF` lub `IsEOF`.

> [!NOTE]
>  Jeśli należy wywołać dowolną z `Move` funkcji podczas bieżącego rekordu zaktualizowano lub dodano i aktualizacje zostaną utracone bez ostrzeżenia.

Użyj `Move` funkcji przenoszenia między rekordami bez stosowania warunku. Użyj operacji Znajdź można zlokalizować rekordów w dynamicznego lub obiekty zestawów rekordów typu migawka, który spełnia określony warunek. Aby zlokalizować rekord w obiekcie zestawu rekordów typ tabeli, należy wywołać `Seek`.

Jeśli zestaw rekordów odwołuje się do zestawu rekordów typ tabeli, przenoszenia następuje bieżący indeks tabeli. Można ustawić bieżącego indeksu za pomocą właściwości indeksu obiektu bazowego DAO. Jeśli bieżący indeks nie jest ustawiona, kolejność rekordów zwracany jest niezdefiniowane.

Jeśli wywołasz `MoveLast` na obiekt zestawu rekordów na podstawie zapytania SQL lub querydef, zapytanie jest zmuszony do ukończenia i w pełni zawiera obiekt zestawu rekordów.

Aby przenieść pozycja bieżący rekord w obiekty zestawów rekordów konkretną liczbę rekordów do przodu lub do tyłu, należy wywołać `Move`.

Aby uzyskać powiązane informacje, zobacz tematy "Przenieś metody" i "MoveNext MoveFirst, MoveLast, metody MovePrevious" w Pomocy programu DAO.

##  <a name="movenext"></a>  CDaoRecordset::MoveNext

Wywołaj tę funkcję elementu członkowskiego, aby następnego rekordu w zestawie rekordów bieżącego rekordu.

```
void MoveNext();
```

### <a name="remarks"></a>Uwagi

Zalecane jest, należy wywołać `IsBOF` przed podjęciem próby Przenieś do poprzedniego rekordu. Wywołanie `MovePrev` zgłosi `CDaoException` Jeśli `IsBOF` zwraca wartość różną od zera, wskazując, które były już przewijane przed pierwszy rekord lub że nie wybrano żadnych rekordów przez zestaw rekordów.

> [!CAUTION]
>  Wywołanie dowolnego z `Move` funkcje zgłasza wyjątek, jeśli zestaw rekordów nie zawiera żadnych rekordów. Ogólnie rzecz biorąc, wywołaj obydwa `IsBOF` i `IsEOF` przed wykonaniem operacji przenoszenia w celu określenia, czy zestaw rekordów zawiera wszystkie rekordy. Po wywołaniu metody `Open` lub `Requery`, albo wywołaj `IsBOF` lub `IsEOF`.

> [!NOTE]
>  Jeśli należy wywołać dowolną z `Move` funkcji podczas bieżącego rekordu zaktualizowano lub dodano i aktualizacje zostaną utracone bez ostrzeżenia.

Użyj `Move` funkcji przenoszenia między rekordami bez stosowania warunku. Użyj operacji Znajdź można zlokalizować rekordów w dynamicznego lub obiekty zestawów rekordów typu migawka, który spełnia określony warunek. Aby zlokalizować rekord w obiekcie zestawu rekordów typ tabeli, należy wywołać `Seek`.

Jeśli zestaw rekordów odwołuje się do zestawu rekordów typ tabeli, przenoszenia następuje bieżący indeks tabeli. Można ustawić bieżącego indeksu za pomocą właściwości indeksu obiektu bazowego DAO. Jeśli bieżący indeks nie jest ustawiona, kolejność rekordów zwracany jest niezdefiniowane.

Aby przenieść pozycja bieżący rekord w obiekty zestawów rekordów konkretną liczbę rekordów do przodu lub do tyłu, należy wywołać `Move`.

Aby uzyskać powiązane informacje, zobacz tematy "Przenieś metody" i "MoveNext MoveFirst, MoveLast, metody MovePrevious" w Pomocy programu DAO.

##  <a name="moveprev"></a>  CDaoRecordset::MovePrev

Wywołaj tę funkcję elementu członkowskiego, aby poprzedniego rekordu w zestawie rekordów bieżącego rekordu.

```
void MovePrev();
```

### <a name="remarks"></a>Uwagi

Zalecane jest, należy wywołać `IsBOF` przed podjęciem próby Przenieś do poprzedniego rekordu. Wywołanie `MovePrev` zgłosi `CDaoException` Jeśli `IsBOF` zwraca wartość różną od zera, wskazując, które były już przewijane przed pierwszy rekord lub że nie wybrano żadnych rekordów przez zestaw rekordów.

> [!CAUTION]
>  Wywołanie dowolnego z `Move` funkcje zgłasza wyjątek, jeśli zestaw rekordów nie zawiera żadnych rekordów. Ogólnie rzecz biorąc, wywołaj obydwa `IsBOF` i `IsEOF` przed wykonaniem operacji przenoszenia w celu określenia, czy zestaw rekordów zawiera wszystkie rekordy. Po wywołaniu metody `Open` lub `Requery`, albo wywołaj `IsBOF` lub `IsEOF`.

> [!NOTE]
>  Jeśli należy wywołać dowolną z `Move` funkcji podczas bieżącego rekordu zaktualizowano lub dodano i aktualizacje zostaną utracone bez ostrzeżenia.

Użyj `Move` funkcji przenoszenia między rekordami bez stosowania warunku. Użyj operacji Znajdź można zlokalizować rekordów w dynamicznego lub obiekty zestawów rekordów typu migawka, który spełnia określony warunek. Aby zlokalizować rekord w obiekcie zestawu rekordów typ tabeli, należy wywołać `Seek`.

Jeśli zestaw rekordów odwołuje się do zestawu rekordów typ tabeli, przenoszenia następuje bieżący indeks tabeli. Można ustawić bieżącego indeksu za pomocą właściwości indeksu obiektu bazowego DAO. Jeśli bieżący indeks nie jest ustawiona, kolejność rekordów zwracany jest niezdefiniowane.

Nie można wywołać `MoveFirst` lub `MovePrev` funkcji składowej z przewijaniem migawki tylko do przodu.

Aby przenieść pozycja bieżący rekord w obiekty zestawów rekordów konkretną liczbę rekordów do przodu lub do tyłu, należy wywołać `Move`.

Aby uzyskać powiązane informacje, zobacz tematy "Przenieś metody" i "MoveNext MoveFirst, MoveLast, metody MovePrevious" w Pomocy programu DAO.

##  <a name="open"></a>  CDaoRecordset::Open

Wywołaj tę funkcję elementu członkowskiego, aby pobrać te rekordy, dla zestawu rekordów.

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

*nOpenType*<br/>
Jeden z następujących wartości:

- `dbOpenDynaset` Zestaw rekordów dynamicznego za pomocą dwukierunkowych przewijania. Domyślnie włączone.

- `dbOpenTable` Zestaw rekordów typ tabeli za pomocą dwukierunkowych przewijania.

- `dbOpenSnapshot` Zestaw rekordów typ migawki za pomocą dwukierunkowych przewijania.

*lpszSQL*<br/>
Wskaźnik ciągu, zawierające jedną z następujących czynności:

- Wskaźnik o wartości NULL.

- Nazwa tabledefs — lub querydefs — (rozdzielonych przecinkami).

- SQL **wybierz** — instrukcja (opcjonalnie wraz z SQL **gdzie** lub **ORDERBY** klauzuli).

- Zapytania przekazującego.

*nOptions*<br/>
Co najmniej jedną z czynności wymienionych poniżej. Wartość domyślna to 0. Dopuszczalne są następujące wartości:

- `dbAppendOnly` Można jedynie dołączyć nowych rekordów (tylko w przypadku rekordów dynamicznego). Ta opcja oznacza dosłownie, że rekordy mogą być tylko dołączane. Klasy bazy danych MFC ODBC mają tylko do dołączania opcja umożliwiająca rekordów do pobrania i dołączane.

- `dbForwardOnly` Zestaw rekordów jest tylko do przodu migawki przewijania.

- `dbSeeChanges` Generuje wyjątek, jeśli inny użytkownik jest zmieniającymi się danymi, które edytujesz.

- `dbDenyWrite` Inni użytkownicy nie mogą zmodyfikować lub dodać rekordy.

- `dbDenyRead` Inni użytkownicy nie mogą wyświetlać rekordy (tylko typ tabeli rekordów).

- `dbReadOnly` Może wyświetlać tylko rekordy; inni użytkownicy można modyfikować.

- `dbInconsistent` Niespójne aktualizacje są dozwolone (tylko w przypadku rekordów dynamicznego).

- `dbConsistent` Tylko uaktualnienia zgodne są dozwolone (tylko w przypadku rekordów dynamicznego).

> [!NOTE]
>  Stałe `dbConsistent` i `dbInconsistent` wzajemnie się wykluczają. Możesz użyć jednej lub drugiej, ale nie oba w podanym wystąpieniu `Open`.

*pTableDef*<br/>
Wskaźnik do [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) obiektu. Ta wersja jest prawidłowy tylko w przypadku zestawów rekordów typu tabeli. Przy użyciu tej opcji `CDaoDatabase` wskaźnik użytego do stworzenia `CDaoRecordset` nie jest używany; zamiast bazy danych, w której znajduje się tabledef jest używany.

*pQueryDef*<br/>
Wskaźnik do [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) obiektu. Ta wersja jest prawidłowy tylko w przypadku dynamicznego i zestawów rekordów typu migawka. Przy użyciu tej opcji `CDaoDatabase` wskaźnik użytego do stworzenia `CDaoRecordset` nie jest używany; zamiast bazy danych, w której znajduje się querydef jest używany.

### <a name="remarks"></a>Uwagi

Przed wywołaniem `Open`, należy utworzyć obiekt zestawu rekordów. Istnieje kilka sposobów, aby to zrobić:

- Podczas tworzenia obiektu recordset przekazać wskaźnik do `CDaoDatabase` obiekt, który jest już otwarty.

- Podczas tworzenia obiektu recordset przekazać wskaźnik do `CDaoDatabase` obiektu, który nie jest otwarty. Zostanie otwarty zestaw rekordów `CDaoDatabase` obiektu, ale nie zostanie on zamknięty, po zamknięciu obiekty zestawów rekordów.

- Podczas tworzenia obiektu recordset przekazać wskaźnik o wartości NULL. Wywołuje obiekt zestawu rekordów `GetDefaultDBName` można pobrać nazwy programu Microsoft Access. Plik MDB, aby otworzyć. Następnie zostanie otwarty zestaw rekordów `CDaoDatabase` obiektu i przechowuje ją otworzyć, tak długo, jak zestaw rekordów jest otwarty. Gdy wywołujesz `Close` w zestawie rekordów `CDaoDatabase` obiektu również jest zamknięty.

    > [!NOTE]
    >  Po otwarciu zestawu rekordów `CDaoDatabase` obiektu źródła danych zostanie otwarty z wyłącznego dostępu.

Dla wersji `Open` , który używa *lpszSQL* parametr, po otwarciu zestawu rekordów można pobrać rekordów w jednym z kilku sposobów. Pierwszym z nich jest zapewnienie funkcje DFX swojej `DoFieldExchange`. Drugą opcją jest użycie wiązanie dynamiczne, wywołując `GetFieldValue` funkcja elementu członkowskiego. Te opcje można zaimplementować osobno lub razem. Jeśli są połączone, trzeba będzie przekazać w instrukcji SQL samodzielnie wywołanie `Open`.

Kiedy używasz drugą wersję `Open` gdzie są przekazywane w `CDaoTableDef` obiektu uzyskane kolumny będą dostępne dla możesz powiązać za pośrednictwem `DoFieldExchange` i mechanizm DFX i/lub powiązania dynamicznie za pośrednictwem `GetFieldValue`.

> [!NOTE]
>  Można wywołać tylko `Open` przy użyciu `CDaoTableDef` obiektu dla zestawów rekordów typu tabeli.

Kiedy używasz trzecia wersja `Open` gdzie są przekazywane w `CDaoQueryDef` obiektu, że będzie można wykonać zapytania, a uzyskane kolumny będą dostępne dla możesz powiązać za pośrednictwem `DoFieldExchange` i mechanizm DFX i/lub powiązania dynamicznie za pośrednictwem `GetFieldValue`.

> [!NOTE]
>  Można wywołać tylko `Open` przy użyciu `CDaoQueryDef` obiektu dynamicznego i zestawów rekordów typu migawka.

W pierwszej wersji programu `Open` , który używa `lpszSQL` parametru rekordy, które są wybrane na podstawie kryteria, pokazano w poniższej tabeli.

|Wartość atrybutu `lpszSQL` parametru|Wybrane rekordy są określane przez|Przykład|
|--------------------------------------|----------------------------------------|-------------|
|NULL|Ciąg zwracany przez `GetDefaultSQL`.||
|Rozdzielana przecinkami lista jednego lub więcej tabledefs — i/lub nazwy querydef.|Wszystkie kolumny są reprezentowane w `DoFieldExchange`.|`"Customer"`|
|**Wybierz** listy kolumn **FROM** listy tabel|Określone kolumny z określonej tabledef(s) i/lub querydef(s).|`"SELECT CustId, CustName`<br /><br /> `FROM Customer"`|

Procedura zwykle służy do przekazywania wartości NULL, aby `Open`; w takim przypadku `Open` wywołania `GetDefaultSQL`, możliwym do zastąpienia składowa, która generuje ClassWizard, podczas tworzenia `CDaoRecordset`-klasy pochodnej. Ta wartość zapewnia tabledef(s) i/lub querydef nazwy, które określiłeś w ClassWizard. Zamiast tego możesz określić inne informacje w *lpszSQL* parametru.

Niezależnie od przekazania, `Open` tworzy ostatni ciąg SQL dla zapytania (ciąg może zawierać SQL **gdzie** i **ORDERBY** klauzule dołączany do *lpszSQL* ciągu zostanie przekazane), a następnie wykonuje zapytanie. Zbudowany ciągu można sprawdzić przez wywołanie metody `GetSQL` po wywołaniu `Open`.

Elementy członkowskie danych pola klasy zestawu rekordów, które są powiązane kolumny wybranych danych. Jeśli zwracane są wszystkie rekordy, pierwszy rekord staje się bieżącym rekordem.

Jeśli chcesz ustawić opcje dla zestawu rekordów, takich jak filtrowanie lub sortowanie, ustaw `m_strSort` lub `m_strFilter` po konstruujesz obiekty zestawów rekordów, ale przed wywołaniem `Open`. Jeśli chcesz odświeżyć rekordy w zestawie rekordów po zestawu rekordów jest już otwarty, wywołaj `Requery`.

Jeśli wywołasz `Open` dynamicznego lub zestawu rekordów typu migawka, lub jeśli źródło danych odnosi się do instrukcji SQL lub tabledef, który reprezentuje dołączonej tabeli, nie możesz użyć `dbOpenTable` argumentu typu; Jeśli to zrobisz, MFC zgłasza wyjątek. Aby ustalić, czy obiekt tabledef reprezentuje dołączonej tabeli, należy utworzyć [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) obiektu, a następnie wywołać jej [GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect) funkcja elementu członkowskiego.

Użyj `dbSeeChanges` flagę, jeśli chcesz pułapki zmiany wprowadzone przez innego użytkownika lub innego programu na komputerze podczas edytowania lub usuwania tego samego rekordu. Na przykład gdy dwóch użytkowników edytowana w jednym rekordzie pierwszego użytkownika, aby wywołać `Update` funkcja elementu członkowskiego zakończy się pomyślnie. Gdy `Update` jest wywoływana przez drugi użytkownik `CDaoException` zgłaszany. Podobnie jeśli drugi użytkownik próbuje wywołać `Delete` można usunąć rekord który już został zmieniony przez pierwszego użytkownika `CDaoException` występuje.

Zazwyczaj gdy użytkownik uzyskuje na to `CDaoException` podczas aktualizowania, kod powinien odświeżyć zawartość pól i pobierać wartości zmodyfikowane. Jeśli wystąpi wyjątek w trakcie usuwania, kodu można wyświetlić nowy rekord danych użytkownika i komunikat informujący, że dane zostały niedawno zmienione. W tym momencie kodu mogą poprosić o potwierdzenie, że użytkownik nadal chce usunąć rekord.

> [!TIP]
>  Użyj opcji przewijania tylko do przodu (`dbForwardOnly`) aby zwiększyć wydajność, gdy aplikacja wykonuje pojedynczego przekazywania zestawu rekordów otwarty ze źródła danych ODBC.

Aby uzyskać powiązane informacje zobacz temat "OpenRecordset metody" w Pomocy programu DAO.

##  <a name="requery"></a>  CDaoRecordset::Requery

Wywołaj tę funkcję elementu członkowskiego, aby odbudować (odświeżanie) zestawu rekordów.

```
virtual void Requery();
```

### <a name="remarks"></a>Uwagi

Jeśli zwracane są wszystkie rekordy, pierwszy rekord staje się bieżącym rekordem.

Aby zestaw rekordów odzwierciedlić dodawania i usuwania, które wykorzystują źródła danych, należy przebudować zestaw rekordów, wywołując `Requery`. Jeśli zestaw rekordów jest dynamiczny, automatycznie odzwierciedla aktualizacji, które użytkownicy dokonać jego istniejące rekordy (ale nie dodatków). Jeśli zestaw rekordów jest migawką, należy wywołać `Requery` uwzględnienie zmian przez innych użytkowników, a także dodanych i usuniętych.

Dynamiczny lub migawki, należy wywołać `Requery` ilekroć chcesz ponownie skompilować rekordów przy użyciu wartości parametrów. Ustaw nowe filtrowania lub sortowania, ustawiając [m_strFilter](#m_strfilter) i [m_strSort](#m_strsort) przed wywołaniem `Requery`. Ustaw nowe parametry, przypisujące nowe wartości do elementów członkowskich danych parametru przed wywołaniem `Requery`.

Jeśli nie można ponownie utworzyć zestaw rekordów, zestaw rekordów jest zamknięty. Przed wywołaniem `Requery`, można określić, czy zestaw rekordów można ponowieniu przez wywołanie metody [CanRestart](#canrestart) funkcja elementu członkowskiego. `CanRestart` nie gwarantuje, że `Requery` zakończy się powodzeniem.

> [!CAUTION]
>  Wywołaj `Requery` tylko wtedy, gdy wywołujesz `Open`.

> [!NOTE]
>  Wywoływanie [Requery](#requery) zmienia DAO zakładek.

Nie można wywołać `Requery` dynamicznego lub zestawu rekordów typu migawka, jeśli wywołanie `CanRestart` zwraca wartość 0, nie można użyć go w zestawie rekordów typ tabeli.

Jeśli oba `IsBOF` i `IsEOF` zwracają wartość różną od zera, po wywołaniu metody `Requery`, kwerenda nie zwróciła żadnych rekordów i rekordów będzie zawierać żadnych danych.

Aby uzyskać powiązane informacje zobacz temat "Metoda Requery" w Pomocy programu DAO.

##  <a name="seek"></a>  CDaoRecordset::Seek

Wywołaj tę funkcję elementu członkowskiego do zlokalizowania rekordu w obiekcie zestawu rekordów indeksowany typ tabeli, który spełni określone kryteria dla bieżącego indeksu i upewnij, że rejestrowanie bieżącego rekordu.

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
Jedną z następujących wyrażeń ciągu: "<","\<=", "=", "> =", lub ">".

*pKey1*<br/>
Wskaźnik do [COleVariant](../../mfc/reference/colevariant-class.md) którego wartość odnosi się do pierwszego pola w indeksie. Wymagane.

*pKey2*<br/>
Wskaźnik do `COleVariant` którego wartość odpowiada drugiego pola w indeksie, jeśli istnieje. Wartość domyślna to NULL.

*pKey3*<br/>
Wskaźnik do `COleVariant` którego wartość odpowiada trzecie pole w indeksie, jeśli istnieje. Wartość domyślna to NULL.

*pKeyArray*<br/>
Wskaźnik do tablicy wariantów. Rozmiar tablicy odpowiada liczbę pól w indeksie.

*nKeys*<br/>
Liczba całkowita odpowiadający rozmiar tablicy, czyli liczbę pól w indeksie.

> [!NOTE]
>  W kluczach nie należy określać symboli wieloznacznych. Symbole wieloznaczne spowoduje, że `Seek` do zwrócenia żadnych zgodnych rekordów.

### <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli zostaną znalezione pasujące rekordy, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Przy użyciu drugiej wersji (array) `Seek` indeksy cztery pola lub więcej.

`Seek` Włącza indeks o wysokiej wydajności, wyszukiwanie w zestawach rekordów typ tabeli. Należy ustawić bieżący indeks przez wywołanie metody `SetCurrentIndex` przed wywołaniem `Seek`. Jeśli indeks identyfikuje nieunikatowego pola klucza lub pola, `Seek` lokalizuje pierwszy rekord, który nie spełnia kryteriów. Jeśli indeks nie jest ustawiona, jest zgłaszany wyjątek.

Należy pamiętać, że jeśli zestaw rekordów UNICODE są nietworzenie, `COleVariant` obiektów musi być zadeklarowany w sposób jawny ANSI. Można to zrobić za pomocą [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)**  formularza konstruktora z *vtSrc* równa `VT_BSTRT` (ANSI) lub za pomocą `COleVariant` funkcja [setstring —](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** z *vtSrc* równa `VT_BSTRT`.

Gdy wywołujesz `Seek`, należy przekazać co najmniej jedna wartość klucza i operator porównania ("<","\<=", "=", "> =", lub ">"). `Seek` przeszukuje określone pola klucza i lokalizuje pierwszy rekord, który spełnia kryteria określone przez *lpszComparison* i *pKey1*. Gdy zostanie znaleziony, `Seek` zwraca wartość różną od zera i sprawia, że rekord bieżący. Jeśli `Seek` nie znajdzie dopasowania `Seek` zwraca zero, a bieżący rekord jest niezdefiniowane. Korzystając z obiektów DAO bezpośrednio, możesz jawnie sprawdzić właściwość NoMatch.

Jeśli `lpszComparison` jest "=", "> =", lub ">", `Seek` rozpoczyna się od początku indeksu. Jeśli *lpszComparison* to "<" lub "< =", `Seek` rozpoczyna się na końcu indeksu i wyszukuje Wstecz, o ile nie ma indeksu zduplikowane wpisy na końcu. W tym przypadku `Seek` rozpoczyna się od dowolnego wpis między wpisy zduplikowany indeks, pod koniec indeksu.

Istnieje nie musi być bieżącego rekordu, gdy używasz `Seek`.

Aby zlokalizować rekord w dynamicznego lub zestawu rekordów typu migawka, który spełnia określony warunek, należy użyć operacji wyszukiwania. Aby uwzględnić wszystkie rekordy, nie tylko te, które spełniają określony warunek, użyj operacji przenoszenia do przechodzenia między rekordami.

Nie można wywołać `Seek` w dołączonej tabeli dowolnego typu, ponieważ tabele dołączonych, muszą być otwarte jako dynamicznego lub zestawów rekordów typu migawka. Jednak jeśli wywołasz `CDaoDatabase::Open` otworzyć bezpośrednio do zainstalowania bazy danych ISAM, można wywołać `Seek` w tabelach w tej bazie danych, mimo że wydajność może być wolne.

Aby uzyskać powiązane informacje zobacz temat "Szukaj metody" w Pomocy programu DAO.

##  <a name="setabsoluteposition"></a>  CDaoRecordset::SetAbsolutePosition

Ustawia liczbę rekordów względnych obiektem rekordem bieżącego rekordu.

```
void SetAbsolutePosition(long lPosition);
```

### <a name="parameters"></a>Parametry

*lPosition*<br/>
Odnosi się do porządkowym bieżącego rekordu w zestawie rekordów.

### <a name="remarks"></a>Uwagi

Wywoływanie `SetAbsolutePosition` umożliwia kursora bieżącego rekordu z określonym rekordem, w oparciu o jego porządkowym w dynamicznego lub zestawu rekordów typu migawka. Należy także określić numer bieżącego rekordu, wywołując [GetAbsolutePosition](#getabsoluteposition).

> [!NOTE]
>  Ta funkcja członkowska jest prawidłowy tylko w przypadku dynamicznego i zestawów rekordów typu migawka.

Wartość właściwości AbsolutePosition obiektu bazowego DAO jest liczony od zera; Ustawienie wartości 0 odwołuje się do pierwszego rekordu w zestawie rekordów. Ustawienie wartości jest większa niż liczba powoduje, że rekordy wypełnione MFC, aby zgłosić wyjątek. Można określić liczbę rekordów wypełnione w zestawie rekordów, wywołując `GetRecordCount` funkcja elementu członkowskiego.

Jeśli bieżący rekord zostanie usunięty, wartość właściwości AbsolutePosition nie jest zdefiniowana, a MFC zgłasza wyjątek, jeśli odwołuje się do. Nowe rekordy są dodawane do końca sekwencji.

> [!NOTE]
>  Ta właściwość nie jest przeznaczona do służyć jako numer rekordu zastępczy. Zakładki są nadal zalecany sposób przechowywania i powrocie do podanego położenia i jedynym sposobem na pozycji bieżącego rekordu dla wszystkich typów obiektów zestawu rekordów, które obsługują zakładki. W szczególności pozycji danego rekordu zmienia usunięcie rekordów przed nim. Istnieje również ma gwarancji, że rekord będzie miał tym samym położeniu bezwzględnym, jeśli zestaw rekordów jest utworzony ponownie, ponieważ kolejność poszczególnych rekordów w zestawie rekordów nie jest gwarantowane, chyba że zostanie utworzona przy użyciu instrukcji SQL przy użyciu  **ORDERBY** klauzuli.

Aby uzyskać powiązane informacje zobacz temat "AbsolutePosition Property" w Pomocy programu DAO.

##  <a name="setbookmark"></a>  CDaoRecordset::SetBookmark

Wywołaj tę funkcję elementu członkowskiego, aby umieścić zestaw rekordów na rekord zawierający zakładką.

```
void SetBookmark(COleVariant varBookmark);
```

### <a name="parameters"></a>Parametry

*varBookmark*<br/>
A [COleVariant](../../mfc/reference/colevariant-class.md) obiekt zawierający wartość zakładki dla określonego rekordu.

### <a name="remarks"></a>Uwagi

Po utworzeniu obiektu zestawu rekordów lub otwarte, każdego z jego rekordów już unikatowe zakładki. Możesz pobrać zakładki w bieżącym rekordzie, wywołując `GetBookmark` i zapisując wartość `COleVariant` obiektu. Można było później wrócić do tego rekordu, wywołując `SetBookmark` przy użyciu wartości zapisanej zakładki.

> [!NOTE]
>  Wywoływanie [Requery](#requery) zmienia DAO zakładek.

Należy pamiętać, że jeśli zestaw rekordów UNICODE są nietworzenie, `COleVariant` obiektu musi być zadeklarowany w sposób jawny ANSI. Można to zrobić za pomocą [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)**  formularza konstruktora z *vtSrc* równa `VT_BSTRT` (ANSI) lub za pomocą `COleVariant` funkcja [setstring —](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** z *vtSrc* równa `VT_BSTRT`.

Aby uzyskać powiązane informacje zobacz tematy "Właściwość zakładki" i właściwość Bookmarkable"w Pomocy programu DAO.

##  <a name="setcachesize"></a>  CDaoRecordset::SetCacheSize

Wywołanie tej funkcji elementu członkowskiego, aby ustawić liczbę rekordów w pamięci podręcznej.

```
void SetCacheSize(long lSize);
```

### <a name="parameters"></a>Parametry

*lSize*<br/>
Określa liczbę rekordów. Typowa wartość wynosi 100. Ustawienie wartości 0 powoduje wyłączenie buforowania. Ustawienie musi być między rekordami 5 i 1200. Pamięć podręczna może używać znaczną ilość pamięci.

### <a name="remarks"></a>Uwagi

Pamięć podręczna to miejsce w pamięci lokalnej, która przechowuje dane ostatnio pobrana z serwera w przypadku, gdy dane będzie wymagane ponownie, gdy aplikacja jest uruchomiona. Buforowanie danych zwiększa wydajność aplikacji, która pobiera dane z serwera zdalnego za pośrednictwem obiektów rekordów dynamicznego. Jeśli wymagane są dane, aparat bazy danych Microsoft Jet pamięci podręcznej dla żądanych danych najpierw sprawdza zamiast pobierania jej z serwera, który jest bardziej czasochłonne. Dane, które nie pochodzą ze źródła danych ODBC nie jest zapisana w pamięci podręcznej.

Wszystkie źródła danych ODBC, takich jak dołączonej tabeli mogą mieć lokalnej pamięci podręcznej. Aby utworzyć pamięć podręczną, otwórz obiekt zestawu rekordów ze źródła danych zdalnych wywołań `SetCacheSize` i `SetCacheStart` elementów członkowskich, a następnie wywołania `FillCache` funkcji członkowskiej lub krok rekordy przy użyciu jednej z operacji przenoszenia. *LSize* parametru `SetCacheSize` funkcji składowej może bazować na liczbę rekordów, aplikacja może pracować w tym samym czasie. Na przykład, jeśli używasz zestawu rekordów jako źródła danych mają być wyświetlane na ekranie, można przekazać `SetCacheSize` *lSize* parametru jako 20 do wyświetlenia w tym samym czasie 20 rekordów.

Aby uzyskać powiązane informacje zobacz temat "CacheSize CacheStart właściwości", w Pomocy programu DAO.

##  <a name="setcachestart"></a>  CDaoRecordset::SetCacheStart

Wywołaj tę funkcję elementu członkowskiego, aby określić zakładki pierwszego rekordu w zestawie rekordów przechowywanie w pamięci podręcznej.

```
void SetCacheStart(COleVariant varBookmark);
```

### <a name="parameters"></a>Parametry

*varBookmark*<br/>
A [COleVariant](../../mfc/reference/colevariant-class.md) określający zakładki pierwszego rekordu w zestawie rekordów przechowywanie w pamięci podręcznej.

### <a name="remarks"></a>Uwagi

Możesz użyć wartości zakładki dla dowolnego rekordu dla *varBookmark* parametru `SetCacheStart` funkcja elementu członkowskiego. Rekord, aby uruchomić pamięć podręczną z bieżącym rekordem, ustanawiania zakładki dla tego rekordu za pomocą [setbookmark —](#setbookmark)i przekaż wartość zakładki jako parametr `SetCacheStart` funkcja elementu członkowskiego.

Aparat bazy danych Microsoft Jet żądań rekordy w zakresie pamięci podręcznej z pamięci podręcznej i żąda ona rekordy poza obszarem pamięci podręcznej z serwera.

Rekordów pobieranych z pamięci podręcznej nie odzwierciedlają zmiany wprowadzone współbieżnie źródła danych przez innych użytkowników.

Aby wymusić aktualizację wszystkich danych w pamięci podręcznej, należy przekazać *lSize* parametru `SetCacheSize` jako 0, należy wywołać `SetCacheSize` ponownie z rozmiarem pamięci podręcznej możesz pierwotnie żądaną, a następnie wywołaj `FillCache` funkcja elementu członkowskiego.

Należy pamiętać, że jeśli zestaw rekordów UNICODE są nietworzenie, `COleVariant` obiektu musi być zadeklarowany w sposób jawny ANSI. Można to zrobić za pomocą [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)**  formularza konstruktora z *vtSrc* równa `VT_BSTRT` (ANSI) lub za pomocą `COleVariant` funkcja [setstring —](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** z *vtSrc* równa `VT_BSTRT`.

Aby uzyskać powiązane informacje zobacz temat CacheSize, CacheStart właściwości"w Pomocy programu DAO.

##  <a name="setcurrentindex"></a>  CDaoRecordset::SetCurrentIndex

Wywołaj tę funkcję elementu członkowskiego, aby ustawić indeks w zestawie rekordów typ tabeli.

```
void SetCurrentIndex(LPCTSTR lpszIndex);
```

### <a name="parameters"></a>Parametry

*lpszIndex*<br/>
Wskaźnik, zawierające nazwę indeksu, należy ustawić.

### <a name="remarks"></a>Uwagi

Rekordy w tabeli bazowej nie są przechowywane w określonej kolejności. Indeks ustawień zmienia kolejność rekordów zwróconych z bazy danych, ale nie ma wpływu na kolejność, w której są przechowywane rekordy. Określony indeks musi być już zdefiniowana. Jeśli spróbujesz użyć obiektu indeksu, który nie istnieje lub nie ustawiono indeks, gdy wywołujesz [Seek](#seek), MFC zgłasza wyjątek.

Można utworzyć nowego indeksu dla tabeli przez wywołanie metody [CDaoTableDef::CreateIndex](../../mfc/reference/cdaotabledef-class.md#createindex) i dołączanie nowego indeksu do kolekcji indeksów tabledef podstawowej przez wywołanie metody [CDaoTableDef::Append](../../mfc/reference/cdaotabledef-class.md#append), i następnie ponownie otworzyć zestawu rekordów.

Rekordy, które zwróciło typ tabeli zestawu rekordów może zostać określona tylko przez indeksy zdefiniowane dla podstawowej tabledef. Aby sortować rekordy w niektórych innych kolejności, można otworzyć dynamicznego lub zestawu rekordów typu migawka przy użyciu języka SQL **ORDERBY** klauzuli przechowywane w [CDaoRecordset::m_strSort](#m_strsort).

Aby uzyskać powiązane informacje zobacz temat "Indeksu obiektu", jak i definicja "bieżący indeks" w Pomocy programu DAO.

##  <a name="setfielddirty"></a>  CDaoRecordset::SetFieldDirty

Wywołaj tę funkcję elementu członkowskiego, aby flaga element członkowski danych pól rekordów jako zmienione lub jako niezmieniony.

```
void SetFieldDirty(
    void* pv,
    BOOL bDirty = TRUE);
```

### <a name="parameters"></a>Parametry

*Wa*<br/>
Zawiera adres element członkowski danych pole w zestawie rekordów lub wartość NULL. Jeśli ma wartość NULL, są oznaczane wszystkie elementy członkowskie danych pola w zestawie rekordów. (C++ o wartości NULL nie jest taka sama jak wartość Null w terminologii bazy danych, co oznacza, że "po żadnej wartości.")

*bDirty*<br/>
Wartość TRUE, jeśli element członkowski danych pola zostanie oznaczony jako "zakłóconych" (zmieniono). W przeciwnym razie wartość FALSE, jeśli element członkowski danych pola zostanie oznaczony jako "Wyczyść" (bez zmian).

### <a name="remarks"></a>Uwagi

Oznaczanie pól jako niezmieniony gwarantuje, że pole nie jest aktualizowana.

Znaczniki framework zmienione elementy członkowskie danych pola, aby upewnić się, że będą one zapisywane do rekordu w źródle danych przez mechanizm wymiany (DXF) pola rekordów DAO. Zazwyczaj zmianę wartości pola ustawia pole zanieczyszczone automatycznie, dzięki czemu będą rzadko należy wywołać `SetFieldDirty` samodzielnie, ale czasami chcieć upewnij się, że kolumny będą jawnie zaktualizowane lub wstawione niezależnie od tego, jaka wartość w polu danych element członkowski. Mechanizm DFX stosuje również użycie PSEUDONULL. Aby uzyskać więcej informacji, zobacz [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Jeśli nie jest używany mechanizm podwójnego buforowania, następnie zmieniając wartość pola automatycznie nie ustawiono pola oznaczonych jako zakłócone. W tym przypadku będzie trzeba jawnie ustawić pole oznaczonych jako zakłócone. Flaga zawarte w [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) kontrolki, to automatyczne sprawdzanie.

> [!NOTE]
>  Wywołaj tę funkcję elementu członkowskiego, tylko wtedy, gdy wywołujesz [Edytuj](#edit) lub [działają funkcje AddNew](#addnew).

Użycie wartości NULL dla pierwszego argumentu funkcji dotyczą funkcji wszystkich `outputColumn` pól nie **param** pola w `CDaoFieldExchange`. Na przykład wywołanie

[!code-cpp[NVC_MFCDatabase#6](../../mfc/codesnippet/cpp/cdaorecordset-class_6.cpp)]

ustawi tylko `outputColumn` pola na wartość NULL; **param** pola będzie to miało wpływu.

Do pracy nad **param**, należy podać rzeczywistego adresu poszczególnych **param** chcesz pracować, takich jak:

[!code-cpp[NVC_MFCDatabase#7](../../mfc/codesnippet/cpp/cdaorecordset-class_7.cpp)]

Oznacza to, nie można ustawić wszystkie **param** pola na wartość NULL, jak w przypadku `outputColumn` pola.

`SetFieldDirty` jest implementowane za pomocą `DoFieldExchange`.

##  <a name="setfieldnull"></a>  CDaoRecordset::SetFieldNull

Wywołaj tę funkcję elementu członkowskiego, aby flaga element członkowski danych pól rekordów jako wartości Null (konkretnie o żadna wartość) lub inną niż Null.

```
void SetFieldNull(
    void* pv,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parametry

*Wa*<br/>
Zawiera adres element członkowski danych pole w zestawie rekordów lub wartość NULL. Jeśli ma wartość NULL, są oznaczane wszystkie elementy członkowskie danych pola w zestawie rekordów. (C++ o wartości NULL nie jest taka sama jak wartość Null w terminologii bazy danych, co oznacza, że "po żadnej wartości.")

*bNull*<br/>
Różna od zera, jeśli element członkowski danych pola oflagowane jako mające żadnej wartości (Null). W przeciwnym razie 0, jeśli element członkowski danych pola jest być oznaczony jako inna niż Null.

### <a name="remarks"></a>Uwagi

`SetFieldNull` jest używana w przypadku pól z powiązanych w `DoFieldExchange` mechanizm.

Po dodaniu nowego rekordu do zestawu rekordów, wszystkie elementy członkowskie danych pola są początkowo ustawiona na wartość Null i oznaczone jako "zakłóconych" (zmieniono). Po pobraniu rekord ze źródła danych jego kolumn już mają wartości lub mają wartość Null. Jeśli nie jest odpowiednie w polu wartość Null, [CDaoException](../../mfc/reference/cdaoexception-class.md) zgłaszany.

Jeśli używasz mechanizmu podwójnego buforowania, na przykład, jeśli chcesz wyznaczyć pole bieżącego rekordu nie ma wartości, wywołaj specjalnie `SetFieldNull` z *bNull* ustawieniu wartości PRAWDA Oznacz ją jako wartość Null. Jeśli chcesz nadać mu wartość pola został wcześniej oznaczony o wartości Null, wystarczy ustawić dla jej nową wartość. Nie masz do usuwania flagi o wartości Null za pomocą `SetFieldNull`. Aby ustalić, czy pole może mieć wartości Null, należy wywołać [IsFieldNullable](#isfieldnullable).

Jeśli nie jest używany mechanizm podwójnego buforowania, następnie zmieniając wartość pola automatycznie nie ustawiono pola jako zanieczyszczony i innych niż Null. W szczególności należy ustawić pola zanieczyszczone i innych niż Null. Flaga zawarte w [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) kontrolki, to automatyczne sprawdzanie.

Mechanizm DFX zatrudnia użytkowania PSEUDONULL. Aby uzyskać więcej informacji, zobacz [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

> [!NOTE]
>  Wywołaj tę funkcję elementu członkowskiego, tylko wtedy, gdy wywołujesz [Edytuj](#edit) lub [działają funkcje AddNew](#addnew).

Użycie wartości NULL dla pierwszego argumentu funkcji zostaną zastosowane tylko do funkcji `outputColumn` pól nie **param** pola w `CDaoFieldExchange`. Na przykład wywołanie

[!code-cpp[NVC_MFCDatabase#8](../../mfc/codesnippet/cpp/cdaorecordset-class_8.cpp)]

ustawi tylko `outputColumn` pola na wartość NULL; **param** pola będzie to miało wpływu.

##  <a name="setfieldvalue"></a>  CDaoRecordset::SetFieldValue

Wywołaj tę funkcję elementu członkowskiego, aby ustawić wartości pola, porządkowym lub zmieniając wartość ciągu.

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

*lpszName*<br/>
Wskaźnik do ciągu zawierającego nazwę pola.

*varValue*<br/>
Odwołanie do [COleVariant](../../mfc/reference/colevariant-class.md) obiekt, który zawiera wartość pola zawartość.

*nIndex*<br/>
Liczba całkowita, która reprezentuje porządkowym pole w zestawie rekordów kolekcji Fields (liczony od zera).

*lpszValue*<br/>
Wskaźnik do ciągu zawierającego wartość pola zawartość.

### <a name="remarks"></a>Uwagi

Użyj `SetFieldValue` i [getfieldvalue —](#getfieldvalue) dynamicznie powiązać pola w czasie wykonywania, a nie statycznie powiązanie kolumn przy użyciu [dofieldexchange —](#dofieldexchange) mechanizm.

Należy zwrócić uwagę, jeśli są nietworzenie zestawu rekordów UNICODE, należy użyć formy `SetFieldValue` niezawierające `COleVariant` parametru lub `COleVariant` obiektu musi być zadeklarowany w sposób jawny ANSI. Można to zrobić za pomocą [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)**  formularza konstruktora z *vtSrc* równa `VT_BSTRT` (ANSI) lub za pomocą `COleVariant` funkcja [setstring —](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** z *vtSrc* równa `VT_BSTRT`.

Aby uzyskać powiązane informacje zobacz tematy "Pola obiektu" i "Wartość właściwości" w Pomocy programu DAO.

##  <a name="setfieldvaluenull"></a>  CDaoRecordset::SetFieldValueNull

Wywołaj tę funkcję elementu członkowskiego, aby ustawić pole na wartość Null.

```
void SetFieldValueNull(int nIndex);
void SetFieldValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks pól w zestawie danych do wyszukiwania według indeksu zaczynającego się od zera.

*lpszName*<br/>
Nazwa pola w zestawie rekordów do wyszukiwania według nazwy.

### <a name="remarks"></a>Uwagi

C++ o wartości NULL nie jest taka sama jak wartość Null, oznacza to, w terminologii bazy danych "o wartości nie".

Aby uzyskać powiązane informacje zobacz tematy "Pola obiektu" i "Wartość właściwości" w Pomocy programu DAO.

##  <a name="setlockingmode"></a>  CDaoRecordset::SetLockingMode

Wywołaj tę funkcję elementu członkowskiego, aby ustawić automatyczny typ blokady dla zestawu rekordów.

```
void SetLockingMode(BOOL bPessimistic);
```

### <a name="parameters"></a>Parametry

*bPessimistic*<br/>
Flaga wskazująca typ blokady.

### <a name="remarks"></a>Uwagi

Gdy pesymistycznego blokowania jest aktywna, strona 2K zawierające rekord, edytowany jest zablokowane, tak szybko, jak należy wywołać `Edit` funkcja elementu członkowskiego. Strona jest odblokowany, gdy wywołujesz `Update` lub `Close` funkcji członkowskiej lub dowolnych operacji przenoszenia lub wyszukiwania.

Gdy optymistyczne blokowanie jest aktywna, strona 2K, zawierająca rekord jest zablokowany, tylko wtedy, gdy rekord jest aktualizowana przy użyciu `Update` funkcja elementu członkowskiego.

Jeśli strona jest zablokowany, żaden inny użytkownik może edytować rekordy na tej samej stronie. Jeśli wywołasz `SetLockingMode` i przekazać wartość różną od zera i inny użytkownik ma już strony zablokowane, zgłaszany jest wyjątek podczas wywoływania `Edit`. Inni użytkownicy mogą odczytywać dane z zablokowanych stron.

Jeśli wywołasz `SetLockingMode` z wartością zero i nowszych wywołanie `Update` gdy strona jest zablokowane przez innego użytkownika, wystąpi wyjątek. Aby zobaczyć zmiany wprowadzone do rekordu użytkownika przez innego użytkownika i utracić wprowadzone zmiany, należy wywołać `SetBookmark` funkcji członka z wartość zakładki bieżącego rekordu.

Podczas pracy ze źródłami danych ODBC, tryb blokowania jest zawsze optymistyczne.

##  <a name="setparamvalue"></a>  CDaoRecordset::SetParamValue

Wywołaj tę funkcję elementu członkowskiego, aby ustawić wartości parametru w zestawie danych w czasie wykonywania.

```
virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);


virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Wartości liczbowych pozycja parametru w kolekcji Parameters querydef.

*var*<br/>
Wartość do ustawienia; Zobacz uwagi.

*lpszName*<br/>
Nazwa parametru, której wartość chcesz ustawić.

### <a name="remarks"></a>Uwagi

Parametr musi już zostały określone jako część ciągu SQL zestawu rekordów. Według nazwy lub jej indeks w kolekcji, można uzyskać dostęp do parametru.

Określ wartość do ustawienia jako `COleVariant` obiektu. Informacje o ustawianiu na żądaną wartość i wpisz swoje `COleVariant` obiektów, zobacz klasę [COleVariant](../../mfc/reference/colevariant-class.md). Należy pamiętać, że jeśli zestaw rekordów UNICODE są nietworzenie, `COleVariant` obiektu musi być zadeklarowany w sposób jawny ANSI. Można to zrobić za pomocą [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)**  formularza konstruktora z *vtSrc* równa `VT_BSTRT` (ANSI) lub za pomocą `COleVariant` funkcja [setstring —](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** z *vtSrc* równa `VT_BSTRT`.

##  <a name="setparamvaluenull"></a>  CDaoRecordset::SetParamValueNull

Wywołaj tę funkcję elementu członkowskiego, aby ustawić parametr na wartość Null.

```
void SetParamValueNull(int nIndex);
void SetParamValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks pól w zestawie danych do wyszukiwania według indeksu zaczynającego się od zera.

*lpszName*<br/>
Nazwa pola w zestawie rekordów do wyszukiwania według nazwy.

### <a name="remarks"></a>Uwagi

C++ o wartości NULL nie jest taka sama jak wartość Null, oznacza to, w terminologii bazy danych "o wartości nie".

##  <a name="setpercentposition"></a>  CDaoRecordset::SetPercentPosition

Wywołaj tę funkcję elementu członkowskiego, aby ustawić wartość, która zmienia przybliżona lokalizacja bieżącego rekordu w obiekcie rekordów na podstawie procentu rekordów w zestawie rekordów.

```
void SetPercentPosition(float fPosition);
```

### <a name="parameters"></a>Parametry

*fPosition*<br/>
Liczba od 0 do 100.

### <a name="remarks"></a>Uwagi

Podczas pracy z dynamicznego lub zestawu rekordów typu migawka, przenosząc do ostatniego rekordu przed wywołaniem najpierw wypełnienia zestawu rekordów `SetPercentPosition`. Jeśli wywołasz `SetPercentPosition` przed pełni wypełnianie zestawu rekordów, przemieszczenie jest określana względem liczby rekordów dostępne jako wskazanych przez wartość [getrecordcount —](#getrecordcount). Można przenieść do ostatniego rekordu, wywołując `MoveLast`.

Gdy wywołujesz `SetPercentPosition`, rekord w położeniu przybliżony odpowiadający tej wartości staje się bieżącym.

> [!NOTE]
>  Wywoływanie `SetPercentPosition` przenieść bieżący rekord do określonego rekordu w zestawie rekordów nie jest zalecane. Wywołaj [setbookmark —](#setbookmark) zamiast tego funkcję członkowską.

Aby uzyskać powiązane informacje zobacz temat "PercentPosition Property" w Pomocy programu DAO.

##  <a name="update"></a>  CDaoRecordset::Update

Wywołaj tę funkcję elementu członkowskiego po wywołaniu `AddNew` lub `Edit` funkcja elementu członkowskiego.

```
virtual void Update();
```

### <a name="remarks"></a>Uwagi

To wywołanie jest wymagane do ukończenia `AddNew` lub `Edit` operacji.

Zarówno `AddNew` i `Edit` przygotowanie buforu edycji, w której umieszczony jest dodane lub zmodyfikowane dane do zapisania na źródle danych. `Update` zapisuje dane. Tylko w tych polach wykrycia zgodnie zmieniona lub oznaczona są aktualizowane.

Jeśli źródło danych obsługuje transakcje, można wprowadzić `Update` wywołania (i odpowiadającymi mu dostawcami `AddNew` lub `Edit` wywołania) wchodzi w skład transakcji.

> [!CAUTION]
> Jeśli wywołasz `Update` bez uprzedniego wywołania `AddNew` lub `Edit`, `Update` zgłasza `CDaoException`. Jeśli wywołasz `AddNew` lub `Edit`, należy wywołać `Update` przed wywołaniem [MoveNext](#movenext) lub zamknąć połączenia ze źródłem danych lub zestaw rekordów. W przeciwnym razie zmiany zostaną utracone bez powiadomienia.

Gdy obiekt zestawu rekordów pessimistically jest zablokowana w środowisku wielodostępnym, rekord jest zablokowany, od momentu `Edit` jest używana przed zakończeniem aktualizację. Jeśli zestaw rekordów optymistycznie jest zablokowany, rekord jest zablokowana i tylko w przypadku, zanim zostaną one zaktualizowane w bazie danych w porównaniu z wstępnie edytowany rekord. Jeśli rekord został zmieniony, ponieważ wywołana `Edit`, `Update` zgłasza wyjątek, operacja zakończy się niepowodzeniem i MFC. Możesz zmienić tryb blokowania z `SetLockingMode`.

> [!NOTE]
> Zawsze formatów zewnętrznej bazy danych, takich jak ODBC i możliwe do zainstalowania ISAM używane optymistyczne blokowanie.

Aby uzyskać powiązane informacje zobacz tematy "Działają funkcje AddNew metody", "CancelUpdate metody", "Usuń metodę", "LastModified Property", "Metoda aktualizacji" i "Trybu edycji właściwości" w Pomocy programu DAO.

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)<br/>
[Klasa CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)<br/>
[Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)<br/>
[Klasa CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)<br/>
