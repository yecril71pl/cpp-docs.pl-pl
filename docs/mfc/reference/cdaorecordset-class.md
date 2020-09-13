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
ms.openlocfilehash: 4a1026c6b652bc5141855670db3b1ee34e7974b9
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040278"
---
# <a name="cdaorecordset-class"></a>Klasa CDaoRecordset

Reprezentuje zestaw rekordów wybranych ze źródła danych.

## <a name="syntax"></a>Składnia

```cpp
class CDaoRecordset : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoRecordset:: CDaoRecordset](#cdaorecordset)|Konstruuje `CDaoRecordset` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoRecordset:: AddNew](#addnew)|Przygotowuje się do dodania nowego rekordu. Wywołaj [aktualizację](#update) , aby ukończyć Dodawanie.|
|[CDaoRecordset:: dołączanie](#canappend)|Zwraca wartość różną od zera, jeśli nowe rekordy można dodać do zestawu rekordów za pośrednictwem funkcji elementu członkowskiego [AddNew](#addnew) .|
|[CDaoRecordset:: wypisano](#canbookmark)|Zwraca wartość różną od zera, jeśli zestaw rekordów obsługuje zakładki.|
|[CDaoRecordset:: CancelUpdate](#cancelupdate)|Anuluje wszystkie oczekujące aktualizacje z powodu operacji [edycji](#edit) lub [parametru AddNew](#addnew) .|
|[CDaoRecordset:: restart](#canrestart)|Zwraca wartość różną od zera [, jeśli można wywołać kwerendę,](#requery) aby ponownie uruchomić zapytanie zestawu rekordów.|
|[CDaoRecordset:: Scroll](#canscroll)|Zwraca wartość różną od zera, jeśli można przewijać rekordy.|
|[CDaoRecordset:: gettransact](#cantransact)|Zwraca wartość różną od zera, jeśli źródło danych obsługuje transakcje.|
|[CDaoRecordset:: Update](#canupdate)|Zwraca wartość różną od zera, jeśli zestaw rekordów można zaktualizować (można dodawać, aktualizować lub usuwać rekordy).|
|[CDaoRecordset:: Close](#close)|Zamyka zestaw rekordów.|
|[CDaoRecordset::D Usuń](#delete)|Usuwa bieżący rekord z zestawu rekordów. Po usunięciu należy jawnie przewinąć do innego rekordu.|
|[CDaoRecordset::D oFieldExchange](#dofieldexchange)|Wywołuje się, by wymienić dane (w obu kierunkach) między elementami członkowskimi danych pola zestawu rekordów i odpowiednim rekordem w źródle danych. Implementuje wymianę pól rekordów DAO (DFX).|
|[CDaoRecordset:: Edit](#edit)|Przygotowuje się do zmian w bieżącym rekordzie. Wywołaj `Update` , aby ukończyć edycję.|
|[CDaoRecordset:: FillCache](#fillcache)|Wypełnia wszystkie lub część lokalnej pamięci podręcznej dla obiektu zestawu rekordów, który zawiera dane ze źródła danych ODBC.|
|[CDaoRecordset:: find](#find)|Lokalizuje pierwszą, następną, poprzednią lub ostatnią lokalizację określonego ciągu w zestawie rekordów typu zestaw dynamiczny, który spełnia określone kryteria i powoduje, że rejestruje bieżący rekord.|
|[CDaoRecordset:: FindFirst](#findfirst)|Lokalizuje pierwszy rekord w zestawie dynamicznym typu lub typie migawki, który spełnia określone kryteria i powoduje, że rejestruje bieżący rekord.|
|[CDaoRecordset:: FindLast](#findlast)|Lokalizuje ostatni rekord w zestawie dynamicznym typu lub typie migawki, który spełnia określone kryteria i powoduje, że rejestruje bieżący rekord.|
|[CDaoRecordset:: ZnajdźNastępny](#findnext)|Lokalizuje następny rekord w zestawie dynamicznym typu lub typie migawki, który spełnia określone kryteria i powoduje, że rejestruje bieżący rekord.|
|[CDaoRecordset:: FindPrev](#findprev)|Lokalizuje poprzedni rekord w zestawie dynamicznym typu lub typie migawki, który spełnia określone kryteria i powoduje, że rejestruje bieżący rekord.|
|[CDaoRecordset:: GetAbsolutePosition](#getabsoluteposition)|Zwraca numer rekordu bieżącego rekordu obiektu zestawu rekordów.|
|[CDaoRecordset:: GetBookmark](#getbookmark)|Zwraca wartość, która reprezentuje zakładkę dla rekordu.|
|[CDaoRecordset:: GetCacheSize](#getcachesize)|Zwraca wartość określającą liczbę rekordów w zestawie rekordów typu zestaw dynamiczny zawierający dane, które mają być buforowane lokalnie ze źródła danych ODBC.|
|[CDaoRecordset:: GetCacheStart](#getcachestart)|Zwraca wartość określającą zakładkę pierwszego rekordu w zestawie rekordów, który ma zostać zbuforowany.|
|[CDaoRecordset:: GetCurrentIndex](#getcurrentindex)|Zwraca `CString` zawierającą nazwę indeksu ostatnio użytego w indeksowanym typie tabeli `CDaoRecordset` .|
|[CDaoRecordset:: GetDateCreated](#getdatecreated)|Zwraca datę i godzinę utworzenia bazowej tabeli bazowej obiektu. `CDaoRecordset`|
|[CDaoRecordset:: GetDateLastUpdated](#getdatelastupdated)|Zwraca datę i godzinę ostatniej zmiany dokonanej w projekcie tabeli bazowej bazowej `CDaoRecordset` obiektu.|
|[CDaoRecordset:: GetDefaultDBName](#getdefaultdbname)|Zwraca nazwę domyślnego źródła danych.|
|[CDaoRecordset:: GetDefaultSQL](#getdefaultsql)|Wywołuje się, by uzyskać domyślny ciąg SQL do wykonania.|
|[CDaoRecordset:: geteditmode](#geteditmode)|Zwraca wartość wskazującą stan edycji bieżącego rekordu.|
|[CDaoRecordset:: GetFieldCount](#getfieldcount)|Zwraca wartość reprezentującą liczbę pól w zestawie rekordów.|
|[CDaoRecordset:: GetFieldInfo](#getfieldinfo)|Zwraca określone rodzaje informacji o polach w zestawie rekordów.|
|[CDaoRecordset:: GetFieldValue —](#getfieldvalue)|Zwraca wartość pola w zestawie rekordów.|
|[CDaoRecordset:: GetIndexCount](#getindexcount)|Pobiera liczbę indeksów w tabeli bazowej zestawu rekordów.|
|[CDaoRecordset:: GetIndexInfo](#getindexinfo)|Zwraca różne rodzaje informacji o indeksie.|
|[CDaoRecordset:: GetLastModifiedBookmark](#getlastmodifiedbookmark)|Służy do określenia ostatnio dodanego lub zaktualizowanego rekordu.|
|[CDaoRecordset:: getlockmode](#getlockingmode)|Zwraca wartość wskazującą typ blokowania, który jest stosowany podczas edycji.|
|[CDaoRecordset:: GetName](#getname)|Zwraca `CString` nazwę zestawu rekordów.|
|[CDaoRecordset:: GetParamValue](#getparamvalue)|Pobiera bieżącą wartość określonego parametru przechowywanego w źródłowym obiekcie DAOParameter.|
|[CDaoRecordset:: GetPercentPosition](#getpercentposition)|Zwraca pozycję bieżącego rekordu jako procentową łączną liczbę rekordów.|
|[CDaoRecordset:: GetRecordCount](#getrecordcount)|Zwraca liczbę rekordów, do których można uzyskać dostęp w obiekcie zestawu rekordów.|
|[CDaoRecordset:: GetSQL](#getsql)|Pobiera ciąg SQL używany do wybierania rekordów dla zestawu rekordów.|
|[CDaoRecordset:: GetType](#gettype)|Wywołuje się, by określić typ zestawu rekordów: typu tabeli, typu dynamicznego lub typu migawki.|
|[CDaoRecordset:: GetValidationRule](#getvalidationrule)|Zwraca `CString` zawierającą wartość, która sprawdza poprawność danych w miarę ich wprowadzania do pola.|
|[CDaoRecordset:: GetValidationText](#getvalidationtext)|Pobiera tekst wyświetlany, gdy reguła walidacji nie jest spełniony.|
|[CDaoRecordset:: IsBOF](#isbof)|Zwraca wartość różną od zera, jeśli zestaw rekordów został umieszczony przed pierwszym rekordem. Brak bieżącego rekordu.|
|[CDaoRecordset:: IsDeleted](#isdeleted)|Zwraca wartość różną od zera, jeśli zestaw rekordów został umieszczony w usuniętym rekordzie.|
|[CDaoRecordset:: IsEOF](#iseof)|Zwraca wartość różną od zera, jeśli zestaw rekordów został umieszczony po ostatnim rekordzie. Brak bieżącego rekordu.|
|[CDaoRecordset:: IsFieldDirty](#isfielddirty)|Zwraca wartość różną od zera, jeśli określone pole w bieżącym rekordzie zostało zmienione.|
|[CDaoRecordset:: IsFieldNull](#isfieldnull)|Zwraca wartość różną od zera, jeśli określone pole w bieżącym rekordzie ma wartość null (bez wartości).|
|[CDaoRecordset:: IsFieldNullable](#isfieldnullable)|Zwraca wartość różną od zera, jeśli określone pole w bieżącym rekordzie można ustawić na wartość null (bez wartości).|
|[CDaoRecordset:: IsOpen](#isopen)|Zwraca wartość różną od zera, jeśli funkcja [Open](#open) została wcześniej wywołana.|
|[CDaoRecordset:: Move](#move)|Ustawia zestaw rekordów na określoną liczbę rekordów z bieżącego rekordu w dowolnym kierunku.|
|[CDaoRecordset:: MoveFirst](#movefirst)|Ustawia bieżący rekord pierwszego rekordu w zestawie rekordów.|
|[CDaoRecordset:: MoveLast](#movelast)|Określa położenie bieżącego rekordu w ostatnim rekordzie w zestawie rekordów.|
|[CDaoRecordset:: MoveNext](#movenext)|Określa położenie bieżącego rekordu w następnym rekordzie w zestawie rekordów.|
|[CDaoRecordset:: MovePrev](#moveprev)|Określa położenie bieżącego rekordu w poprzednim rekordzie w zestawie rekordów.|
|[CDaoRecordset:: Open](#open)|Tworzy nowy zestaw rekordów z tabeli, zestawu dynamicznego lub migawki.|
|[CDaoRecordset:: Requery](#requery)|Uruchamia ponownie zapytanie zestawu rekordów w celu odświeżenia wybranych rekordów.|
|[CDaoRecordset:: Seek](#seek)|Lokalizuje rekord w indeksowanym typie tabeli obiekt zestawu rekordów, który spełnia określone kryteria dla bieżącego indeksu i sprawia, że rejestruje bieżący rekord.|
|[CDaoRecordset:: SetAbsolutePosition](#setabsoluteposition)|Ustawia numer rekordu bieżącego rekordu obiektu zestawu rekordów.|
|[CDaoRecordset:: SetBookmark](#setbookmark)|Ustawia zestaw rekordów dla rekordu zawierającego określoną zakładkę.|
|[CDaoRecordset:: SetCacheSize](#setcachesize)|Ustawia wartość określającą liczbę rekordów w zestawie rekordów typu zestaw dynamiczny zawierający dane, które mają być buforowane lokalnie ze źródła danych ODBC.|
|[CDaoRecordset:: SetCacheStart](#setcachestart)|Ustawia wartość określającą zakładkę pierwszego rekordu w zestawie rekordów, który ma zostać zbuforowany.|
|[CDaoRecordset:: SetCurrentIndex](#setcurrentindex)|Wywołuje się, by ustawić indeks w zestawie rekordów typu tabeli.|
|[CDaoRecordset:: SetFieldDirty](#setfielddirty)|Oznacza określone pole w bieżącym rekordzie jako zmienione.|
|[CDaoRecordset:: SetFieldNull](#setfieldnull)|Ustawia wartość określonego pola w bieżącym rekordzie na null (bez wartości).|
|[CDaoRecordset:: SetFieldValue](#setfieldvalue)|Ustawia wartość pola w zestawie rekordów.|
|[CDaoRecordset:: SetFieldValueNull](#setfieldvaluenull)|Ustawia wartość pola w zestawie rekordów na wartość null. (bez wartości).|
|[CDaoRecordset:: setlockmode](#setlockingmode)|Ustawia wartość wskazującą typ blokowania, które mają zostać zastosowane podczas edycji.|
|[CDaoRecordset:: SetParamValue](#setparamvalue)|Ustawia bieżącą wartość określonego parametru przechowywanego w źródłowym obiekcie DAOParameter|
|[CDaoRecordset:: SetParamValueNull](#setparamvaluenull)|Ustawia bieżącą wartość określonego parametru na null (bez wartości).|
|[CDaoRecordset:: SetPercentPosition](#setpercentposition)|Ustawia pozycję bieżącego rekordu na lokalizację odpowiadającą wartości procentowej całkowitej liczby rekordów w zestawie rekordów.|
|[CDaoRecordset:: Update](#update)|Wykonuje `AddNew` operację lub `Edit` , zapisując nowe lub edytowane dane w źródle danych.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDaoRecordset:: m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)|Zawiera flagę wskazującą, czy pola są automatycznie oznaczane jako zmienione.|
|[CDaoRecordset:: m_nFields](#m_nfields)|Zawiera liczbę elementów członkowskich danych pola w klasie zestawu rekordów oraz liczbę kolumn wybranych przez zestaw rekordów ze źródła danych.|
|[CDaoRecordset:: m_nParams](#m_nparams)|Zawiera liczbę elementów członkowskich danych parametrów w klasie zestawu rekordów — liczbę parametrów przesłanych z zapytaniem zestawu rekordów|
|[CDaoRecordset:: m_pDAORecordset](#m_pdaorecordset)|Wskaźnik do interfejsu DAO bazowego obiektu zestawu rekordów.|
|[CDaoRecordset:: m_pDatabase](#m_pdatabase)|Źródłowa baza danych dla tego zestawu wyników. Zawiera wskaźnik do obiektu [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) .|
|[CDaoRecordset:: m_strFilter](#m_strfilter)|Zawiera ciąg używany do konstruowania instrukcji SQL **WHERE** .|
|[CDaoRecordset:: m_strSort](#m_strsort)|Zawiera ciąg służący do konstruowania instrukcji SQL **order by** .|

## <a name="remarks"></a>Uwagi

Obiekty "zestawy rekordów" `CDaoRecordset` są dostępne w następujących trzech formach:

- Zestawy rekordów typu tabela reprezentują tabelę bazową, która służy do badania, dodawania, zmieniania lub usuwania rekordów z pojedynczej tabeli bazy danych.

- Zestawy rekordów typu zestaw dynamiczny są wynikiem zapytania, które może mieć aktualizowalne rekordy. Te zestawy rekordów to zestaw rekordów, których można użyć do badania, dodawania, zmieniania lub usuwania rekordów źródłowej tabeli lub tabel bazy danych. Zestawy rekordów typu dynamicznego mogą zawierać pola z co najmniej jednej tabeli w bazie danych.

- Zestawy rekordów typu Snapshot to statyczna kopia zestawu rekordów, za pomocą której można znaleźć dane lub wygenerować raporty. Te zestawy rekordów mogą zawierać pola z co najmniej jednej tabeli w bazie danych, ale nie można ich zaktualizować.

Każdy formularz zestawu rekordów reprezentuje zestaw rekordów ustalonych w momencie otwarcia zestawu rekordów. Podczas przewijania do rekordu w zestawie rekordów typu tabela lub zestawu rekordów typu zestaw dynamiczny odzwierciedla zmiany wprowadzone do rekordu po otwarciu zestawu rekordów przez innych użytkowników lub inne zestawy rekordów w aplikacji. (Nie można zaktualizować zestawu rekordów typu snapshot). Można użyć `CDaoRecordset` bezpośrednio lub utworzyć klasę zestawu rekordów specyficznych dla aplikacji z `CDaoRecordset` . Następnie można wykonywać czynności takie jak:

- Przewijaj rekordy.

- Ustawianie indeksu i szybkie wyszukiwanie rekordów przy użyciu funkcji [wyszukiwania](#seek) (tylko zestawy rekordów typu "Tabela").

- Znajdowanie rekordów na podstawie porównania ciągów: "<", " \<=", "=", "> =" lub ">" (zestawy rekordów typu dynamicznego i typów migawek).

- Aktualizowanie rekordów i Określanie trybu blokowania (z wyjątkiem zestawów rekordów typu snapshot).

- Filtruj zestaw rekordów, aby ograniczyć, które rekordy wybierają z tych, które są dostępne w źródle danych.

- Posortuj zestaw rekordów.

- Sparametryzuj zestaw rekordów, aby dostosować jego wybór o informacje nieznane do czasu wykonywania.

Klasa `CDaoRecordset` dostarcza interfejs podobny do klasy `CRecordset` . Główną różnicą jest to, że Klasa `CDaoRecordset` uzyskuje dostęp do danych za pośrednictwem obiektu dostępu do danych (DAO) opartego na technologii OLE. Klasa `CRecordset` uzyskuje dostęp do systemu DBMS za pośrednictwem Open Database Connectivity (ODBC) i sterownika ODBC dla tego systemu DBMS.

> [!NOTE]
> Klasy bazy danych DAO różnią się od klas baz danych MFC opartych na Open Database Connectivity (ODBC). Wszystkie nazwy klas baz danych DAO mają prefiks "CDao". Nadal można uzyskać dostęp do źródeł danych ODBC przy użyciu klas DAO; klasy DAO zazwyczaj oferują znakomite możliwości, ponieważ są specyficzne dla aparatu bazy danych Microsoft Jet.

Można użyć `CDaoRecordset` bezpośrednio lub utworzyć klasę z `CDaoRecordset` . Aby użyć klasy zestawu rekordów w obu przypadkach, Otwórz bazę danych i Skonstruuj obiekt zestawu rekordów, przekazując konstruktora wskaźnik do `CDaoDatabase` obiektu. Możesz również skonstruować `CDaoRecordset` obiekt i pozwolić MFC utworzyć `CDaoDatabase` obiekt tymczasowy. Następnie wywołaj funkcję [otwierającego](#open) elementu członkowskiego zestawu rekordów, określając, czy obiekt jest zestawem rekordów typu tabeli, zestawem rekordów typu dynamicznego lub zestawem rekordów typu migawka. Wywołanie `Open` powoduje wybranie danych z bazy danych i pobranie pierwszego rekordu.

Użyj funkcji składowych i składowych danych obiektu, aby przewijać rekordy i pracować nad nimi. Dostępne operacje zależą od tego, czy obiekt jest zestawem rekordów typu tabeli, zestawem rekordów typu dynamicznego, czy zestawem rekordów typu migawki oraz czy jest możliwe do aktualizacji lub tylko do odczytu — zależy to od możliwości źródła danych bazy danych lub Open Database Connectivity (ODBC). Aby odświeżyć rekordy, które mogły zostać zmienione lub dodane od czasu `Open` wywołania, wywołaj funkcję elementu członkowskiego [PonówKwerendę](#requery) obiektu. Wywołaj `Close` funkcję członkowską obiektu i zniszcz obiekt po zakończeniu pracy z nim.

`CDaoRecordset` używa wymiany pól rekordów DAO (DFX) do obsługi odczytywania i aktualizowania pól rekordów za pomocą elementów członkowskich języka C++, które są bezpieczne dla typu `CDaoRecordset` `CDaoRecordset` klasy pochodnej. Możesz również zaimplementować dynamiczne powiązanie kolumn w bazie danych bez używania mechanizmu DFX przy użyciu [GetFieldValue —](#getfieldvalue) i [SetFieldValue](#setfieldvalue).

Aby uzyskać powiązane informacje, zobacz temat "obiekt Recordset" w pomocy DAO.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CDaoRecordset`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao. h

## <a name="cdaorecordsetaddnew"></a><a name="addnew"></a> CDaoRecordset:: AddNew

Wywołaj tę funkcję elementu członkowskiego, aby dodać nowy rekord do typu tabeli lub zestawu rekordów typu dynamicznego.

```cpp
virtual void AddNew();
```

### <a name="remarks"></a>Uwagi

Pola rekordu są początkowo puste. (W terminologii bazy danych wartość null oznacza brak wartości i nie jest taka sama jak wartość NULL w języku C++). Aby ukończyć operację, należy wywołać funkcję elementu członkowskiego [aktualizacji](#update) . `Update` zapisuje zmiany w źródle danych.

> [!CAUTION]
> Jeśli edytujesz rekord, a następnie przewiniesz do innego rekordu bez wywoływania `Update` , zmiany zostaną utracone bez ostrzeżenia.

W przypadku dodania rekordu do zestawu typu zestaw dynamiczny przez wywołanie metody [AddNew](#addnew), rekord jest widoczny w zestawie rekordów i uwzględniony w tabeli źródłowej, w której staną się widoczne dla nowych `CDaoRecordset` obiektów.

Pozycja nowego rekordu zależy od typu zestawu rekordów:

- W zestawie danych typu zestaw dynamiczny, gdzie wstawiony nowy rekord nie jest gwarantowany. To zachowanie zostało zmienione w programie Microsoft Jet 3,0 z powodu wydajności i współbieżności. Jeśli chcesz, aby nowo dodany rekord był nowym rekordem, zapoznaj się z zakładką ostatnio zmodyfikowanego rekordu i przejdź do tej zakładki:

[!code-cpp[NVC_MFCDatabase#1](../../mfc/codesnippet/cpp/cdaorecordset-class_1.cpp)]

- W zestawie rekordów typu tabela, dla którego został określony indeks, rekordy są zwracane w odpowiednim miejscu w kolejności sortowania. Jeśli indeks nie został określony, nowe rekordy są zwracane na końcu zestawu rekordów.

Rekord, który był aktualny przed użyciem, `AddNew` pozostaje aktualny. Jeśli chcesz, aby nowy rekord był bieżący, a zestaw rekordów obsługuje zakładki, wywołaj metodę [SetBookmark](#setbookmark) do zakładki identyfikowanej przez ustawienie właściwości LastModified bazowego obiektu zestawu rekordów DAO. Takie działanie jest przydatne w przypadku określania wartości pól licznika (Autouzupełnianie) w dodanym rekordzie. Aby uzyskać więcej informacji, zobacz [GetLastModifiedBookmark](#getlastmodifiedbookmark).

Jeśli baza danych obsługuje transakcje, możesz `AddNew` wywoływać część transakcji. Aby uzyskać więcej informacji na temat transakcji, zobacz Klasa [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md). Należy pamiętać, że należy wywołać [CDaoWorkspace:: BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans) przed wywołaniem metody `AddNew` .

Wywołanie `AddNew` zestawu rekordów, którego funkcja [Open](#open) member nie została wywołana, jest niedozwolone. `CDaoException`Jest zgłaszany w przypadku wywołania `AddNew` zestawu rekordów, którego nie można dołączyć. Można określić, czy zestaw rekordów ma być aktualizowalny przez wywołanie funkcji [dołączania](#canappend).

Struktura oznacza zmienione elementy członkowskie danych pola, aby upewnić się, że zostaną one zamienione na rekord źródła danych przez mechanizm wymiany pól rekordów DAO (DFX). Zmiana wartości pola na ogół ustawia pole jako zanieczyszczone automatycznie, więc rzadko trzeba wywołać [SetFieldDirty](#setfielddirty) , ale czasami warto upewnić się, że kolumny będą jawnie aktualizowane lub wstawiane niezależnie od tego, jaka wartość znajduje się w polu elementu członkowskiego danych. Mechanizm DFX wykorzystuje również użycie **pseudo wartości null**. Aby uzyskać więcej informacji, zobacz [CDaoFieldExchange:: m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Jeśli mechanizm podwójnego buforowania nie jest używany, zmiana wartości pola nie powoduje automatycznego ustawienia pola jako zanieczyszczonego. W takim przypadku konieczne będzie jawne ustawienie wartości pola zanieczyszczony. Flaga znajdująca się w [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) kontroluje to automatyczne sprawdzanie pól.

> [!NOTE]
> Jeśli rekordy są podwójnie buforowane (oznacza to, że automatyczne sprawdzanie pola jest włączone), wywołanie `CancelUpdate` przywróci Zmienne Członkowskie do wartości, które miały przed `AddNew` lub `Edit` została wywołana.

Aby uzyskać powiązane informacje, zobacz tematy "Metoda AddNew", "Metoda CancelUpdate", "Właściwość LastModified" i "EditMode Property" w pomocy DAO.

## <a name="cdaorecordsetcanappend"></a><a name="canappend"></a> CDaoRecordset:: dołączanie

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy poprzednio otwarty zestaw rekordów pozwala dodawać nowe rekordy, wywołując funkcję elementu członkowskiego [AddNew](#addnew) .

```cpp
BOOL CanAppend() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli zestaw rekordów zezwala na dodawanie nowych rekordów; w przeciwnym razie 0. `CanAppend` Program zwróci wartość 0, jeśli zestaw rekordów został otwarty jako tylko do odczytu.

### <a name="remarks"></a>Uwagi

Aby uzyskać powiązane informacje, zobacz temat "Metoda dołączania" w pomocy DAO.

## <a name="cdaorecordsetcanbookmark"></a><a name="canbookmark"></a> CDaoRecordset:: wypisano

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy poprzednio otwarty zestaw rekordów umożliwia pojedyncze oznaczenie rekordów przy użyciu zakładek.

```cpp
BOOL CanBookmark();
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli zestaw rekordów obsługuje zakładki, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli używasz zestawów rekordów opartych wyłącznie na tabelach aparatu bazy danych Microsoft Jet, można używać zakładek z wyjątkiem zestawów rekordów typu migawka oflagowanych jako przewijane zestawy rekordów. Inne produkty bazy danych (zewnętrzne źródła danych ODBC) mogą nie obsługiwać zakładek.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość z zakładkami" w pomocy DAO.

## <a name="cdaorecordsetcancelupdate"></a><a name="cancelupdate"></a> CDaoRecordset:: CancelUpdate

`CancelUpdate`Funkcja członkowska anuluje wszystkie oczekujące aktualizacje z powodu operacji [edycji](#edit) lub [parametru AddNew](#addnew) .

```cpp
virtual void CancelUpdate();
```

### <a name="remarks"></a>Uwagi

Na przykład, jeśli aplikacja wywołuje `Edit` `AddNew` funkcję lub i nie ma metody [Update](#update), `CancelUpdate` anuluje wszelkie zmiany wykonane po `Edit` `AddNew` wywołaniu lub.

> [!NOTE]
> Jeśli rekordy są podwójnie buforowane (oznacza to, że automatyczne sprawdzanie pola jest włączone), wywołanie `CancelUpdate` przywróci Zmienne Członkowskie do wartości, które miały przed `AddNew` lub `Edit` została wywołana.

Jeśli nie ma żadnej `Edit` `AddNew` operacji lub operacja jest w stanie oczekiwania, `CancelUpdate` powoduje zgłoszenie wyjątku przez MFC. Wywołaj funkcję elementu członkowskiego [Geteditmode](#geteditmode) , aby określić, czy istnieje oczekująca operacja, która może zostać anulowana.

Aby uzyskać powiązane informacje, zobacz temat "Metoda CancelUpdate" w pomocy DAO.

## <a name="cdaorecordsetcanrestart"></a><a name="canrestart"></a> CDaoRecordset:: restart

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy zestaw rekordów umożliwia ponowne uruchomienie zapytania (w celu odświeżenia jego rekordów) przez wywołanie `Requery` funkcji elementu członkowskiego.

```cpp
BOOL CanRestart();
```

### <a name="return-value"></a>Wartość zwracana

Różna od zera `Requery` , jeśli można wywołać, aby ponownie uruchomić zapytanie zestawu rekordów, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zestawy rekordów typu tabela nie są obsługiwane `Requery` .

Jeśli `Requery` nie jest obsługiwana, wywołaj polecenie [Zamknij](#close) , a następnie [Otwórz](#open) , aby odświeżyć dane. Można wywołać, `Requery` Aby zaktualizować zapytanie parametryczne obiektu zestawu rekordów po zmianie wartości parametrów.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość ponownego uruchomienia" w pomocy DAO.

## <a name="cdaorecordsetcanscroll"></a><a name="canscroll"></a> CDaoRecordset:: Scroll

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy zestaw rekordów umożliwia przewijanie.

```cpp
BOOL CanScroll() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli można przewijać rekordy, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli wywołasz polecenie [Otwórz](#open) za pomocą `dbForwardOnly` , zestaw rekordów może przewijać do przodu.

Aby uzyskać powiązane informacje, zobacz temat "pozycjonowanie bieżącego rekordu ze wskaźnikiem DAO" w pomocy DAO.

## <a name="cdaorecordsetcantransact"></a><a name="cantransact"></a> CDaoRecordset:: gettransact

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy zestaw rekordów zezwala na transakcje.

```cpp
BOOL CanTransact();
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli bazowe źródło danych obsługuje transakcje, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać powiązane informacje, zobacz temat "Właściwość Transactions" w pomocy DAO.

## <a name="cdaorecordsetcanupdate"></a><a name="canupdate"></a> CDaoRecordset:: Update

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy zestaw rekordów może zostać zaktualizowany.

```cpp
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli zestaw rekordów może być aktualizowany (Dodawanie, aktualizowanie i usuwanie rekordów), w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zestaw rekordów może być tylko do odczytu, jeśli bazowe źródło danych jest tylko do odczytu lub jeśli określono `dbReadOnly` dla *nOptions* po wywołaniu metody [Open](#open) dla zestawu rekordów.

Aby uzyskać powiązane informacje, zobacz tematy "Metoda AddNew", "Edytuj metodę", "Delete Method", "Metoda aktualizacji" i "aktualizowalne właściwości" w pomocy DAO.

## <a name="cdaorecordsetcdaorecordset"></a><a name="cdaorecordset"></a> CDaoRecordset:: CDaoRecordset

Konstruuje `CDaoRecordset` obiekt.

```cpp
CDaoRecordset(CDaoDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>Parametry

*pDatabase*<br/>
Zawiera wskaźnik do obiektu [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) lub wartość null. Jeśli wartość nie jest równa NULL, a `CDaoDatabase` `Open` funkcja członkowska obiektu nie została wywołana, aby połączyć ją ze źródłem danych, zestaw rekordów próbuje otworzyć go dla Ciebie w ramach własnego [otwartego](#open) wywołania. Jeśli przejdziesz wartość NULL, `CDaoDatabase` obiekt jest konstruowany i połączony z użyciem informacji o źródle danych, które zostały określone, jeśli Klasa zestawu rekordów pochodzi od `CDaoRecordset` .

### <a name="remarks"></a>Uwagi

Można użyć `CDaoRecordset` bezpośrednio lub utworzyć klasę specyficzną dla aplikacji z `CDaoRecordset` . Możesz użyć ClassWizard, aby utworzyć klasy zestawu rekordów.

> [!NOTE]
> W przypadku wyprowadzania `CDaoRecordset` klasy Klasa pochodna musi dostarczyć własnego konstruktora. W konstruktorze klasy pochodnej Wywołaj konstruktora `CDaoRecordset::CDaoRecordset` , przekazując odpowiednie parametry do niego.

Przekaż wartość NULL do konstruktora zestawu rekordów, aby `CDaoDatabase` obiekt został skonstruowany i połączony automatycznie. Jest to przydatny skrót, który nie wymaga konstruowania i łączenia `CDaoDatabase` obiektu przed rozpoczęciem tworzenia zestawu rekordów. Jeśli `CDaoDatabase` obiekt nie jest otwarty, zostanie również utworzony obiekt [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) , który używa domyślnego obszaru roboczego. Aby uzyskać więcej informacji, zobacz [CDaoDatabase:: CDaoDatabase](../../mfc/reference/cdaodatabase-class.md#cdaodatabase).

## <a name="cdaorecordsetclose"></a><a name="close"></a> CDaoRecordset:: Close

Zamknięcie `CDaoRecordset` obiektu spowoduje usunięcie go z kolekcji otwartych zestawów rekordów w skojarzonej bazie danych.

```cpp
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Ponieważ nie `Close` niszczy tego `CDaoRecordset` obiektu, można ponownie użyć obiektu przez wywołanie tego `Open` samego źródła danych lub innego źródła danych.

Wszystkie oczekujące instrukcje [AddNew](#addnew) lub [Edit](#edit) są anulowane i wszystkie oczekujące transakcje są wycofywane. Jeśli chcesz zachować oczekujące operacje dodawania lub edycji, wywołaj [aktualizację](#update) przed wywołaniem `Close` dla każdego zestawu rekordów.

Możesz wywołać `Open` ponownie po wywołaniu `Close` . Pozwala to ponownie wykorzystać obiekt zestawu rekordów. Lepszym rozwiązaniem jest wywołanie [kwerendy](#requery), jeśli to możliwe.

Aby uzyskać powiązane informacje, zobacz temat "metoda Close" w pomocy DAO.

## <a name="cdaorecordsetdelete"></a><a name="delete"></a> CDaoRecordset::D Usuń

Wywołaj tę funkcję elementu członkowskiego, aby usunąć bieżący rekord w otwartym obiekcie zestawu rekordów typu dynamiczny lub typu tabela.

```cpp
virtual void Delete();
```

### <a name="remarks"></a>Uwagi

Po pomyślnym usunięciu elementy członkowskie danych pola zestawu rekordów są ustawiane na wartość null i należy jawnie wywołać jedną z funkcji elementów członkowskich nawigacji zestawu rekordów ( [Przenieś](#move), [Szukaj](#seek), [SetBookmark](#setbookmark)itd.) w celu przeniesienia usuniętego rekordu. Po usunięciu rekordów z zestawu rekordów w zestawie rekordów musi istnieć bieżący rekord przed wywołaniem `Delete` ; w przeciwnym razie MFC zgłasza wyjątek.

`Delete` usuwa bieżący rekord i sprawia, że jest niedostępny. Chociaż nie można edytować ani używać usuniętego rekordu, pozostaje on aktualny. Jednak po przejściu do innego rekordu nie można zmienić rekordu, który został usunięty ponownie.

> [!CAUTION]
> Zestaw rekordów musi być aktualizowalny, a podczas wywoływania musi istnieć prawidłowy rekord w zestawie rekordów `Delete` . Na przykład, jeśli usuniesz rekord, ale nie przewiniesz do nowego rekordu przed ponownym wywołaniem `Delete` , `Delete` zgłosi [CDaoException](../../mfc/reference/cdaoexception-class.md).

Możesz cofnąć usunięcie rekordu, jeśli używasz transakcji i wywołujesz funkcję elementu członkowskiego [CDaoWorkspace:: Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback) . Jeśli tabela podstawowa jest tabelą podstawową w relacji usuwania kaskadowego, usunięcie bieżącego rekordu może również spowodować usunięcie jednego lub większej liczby rekordów w tabeli obcej. Aby uzyskać więcej informacji, zobacz Definicja "Kaskada Delete" w pomocy DAO.

W przeciwieństwie do `AddNew` i `Edit` , wywołanie `Delete` nie następuje po wywołaniu metody `Update` .

Aby uzyskać powiązane informacje, zobacz tematy "Metoda AddNew", "Edytuj metodę", "Delete Method", "Metoda aktualizacji" i "aktualizowalne właściwości" w pomocy DAO.

## <a name="cdaorecordsetdofieldexchange"></a><a name="dofieldexchange"></a> CDaoRecordset::D oFieldExchange

Struktura wywołuje tę funkcję elementu członkowskiego, aby automatycznie wymieniać dane między elementami członkowskimi obiektu zestawu rekordów i odpowiednimi kolumnami bieżącego rekordu w źródle danych.

```cpp
virtual void DoFieldExchange(CDaoFieldExchange* pFX);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Zawiera wskaźnik do `CDaoFieldExchange` obiektu. Platforma ma już skonfigurowany ten obiekt, aby określić kontekst dla operacji wymiany pól.

### <a name="remarks"></a>Uwagi

Wiąże się on również z elementami członkowskimi danych parametru, jeśli istnieją, do zastępczych parametrów w ciągu instrukcji SQL dla wyboru zestawu rekordów. Wymiana danych pól, nazywana wymianą pól rekordów DAO (DFX), działa w obu kierunkach: od elementów członkowskich danych pola obiektu recordset do pól rekordu w źródle danych i z rekordu źródła danych do obiektu zestawu rekordów. W przypadku dynamicznego wiązania kolumn nie trzeba implementować programu `DoFieldExchange` .

Jedyną akcją, którą należy zwykle wykonać w celu wdrożenia `DoFieldExchange` dla pochodnej klasy zestawu rekordów, jest utworzenie klasy z ClassWizard i określenie nazw i typów danych elementów członkowskich danych pola. Możesz również dodać kod do ClassWizard zapisów, aby określić elementy członkowskie danych parametru. Jeśli wszystkie pola mają być powiązane dynamicznie, ta funkcja będzie nieaktywna, chyba że określisz elementy członkowskie danych parametru.

Po zadeklarowaniu pochodnej klasy zestawu rekordów przy użyciu ClassWizard kreator zapisuje przesłonięcie `DoFieldExchange` dla Ciebie, co przypomina następujący przykład:

[!code-cpp[NVC_MFCDatabase#2](../../mfc/codesnippet/cpp/cdaorecordset-class_2.cpp)]

## <a name="cdaorecordsetedit"></a><a name="edit"></a> CDaoRecordset:: Edit

Wywołaj tę funkcję elementu członkowskiego, aby zezwolić na zmiany w bieżącym rekordzie.

```cpp
virtual void Edit();
```

### <a name="remarks"></a>Uwagi

Po wywołaniu `Edit` funkcji członkowskiej zmiany wprowadzone do pól bieżącego rekordu są kopiowane do buforu kopiowania. Po wprowadzeniu odpowiednich zmian do rekordu, należy wywołać, `Update` Aby zapisać zmiany. `Edit` zapisuje wartości elementów członkowskich danych zestawu rekordów. Jeśli wywołasz `Edit` , wprowadzisz zmiany, a następnie wywołajesz `Edit` ponownie, wartości rekordu są przywracane do tych, które były przed pierwszym `Edit` wywołaniem.

> [!CAUTION]
> Jeśli edytujesz rekord, a następnie wykonasz dowolną operację przenoszone do innego rekordu bez uprzedniego wywołania `Update` , zmiany zostaną utracone bez ostrzeżenia. Ponadto, jeśli zamkniesz zestaw rekordów lub nadrzędną bazę danych, edytowany rekord zostanie odrzucony bez ostrzeżenia.

W niektórych przypadkach możesz chcieć zaktualizować kolumnę, wprowadzając wartość null (bez danych). Aby to zrobić, należy wywołać `SetFieldNull` z parametrem true, aby oznaczyć pole jako puste; spowoduje to również zaktualizowanie kolumny. Jeśli chcesz, aby pole było zapisywane w źródle danych, mimo że jego wartość nie zmieniła się, wywołaj `SetFieldDirty` z parametrem true. Działa to nawet wtedy, gdy pole ma wartość null.

Struktura oznacza zmienione elementy członkowskie danych pola, aby upewnić się, że zostaną one zamienione na rekord źródła danych przez mechanizm wymiany pól rekordów DAO (DFX). Zmiana wartości pola na ogół ustawia pole jako zanieczyszczone automatycznie, więc rzadko trzeba wywołać [SetFieldDirty](#setfielddirty) , ale czasami warto upewnić się, że kolumny będą jawnie aktualizowane lub wstawiane niezależnie od tego, jaka wartość znajduje się w polu elementu członkowskiego danych. Mechanizm DFX wykorzystuje również użycie **pseudo wartości null**. Aby uzyskać więcej informacji, zobacz [CDaoFieldExchange:: m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Jeśli mechanizm podwójnego buforowania nie jest używany, zmiana wartości pola nie powoduje automatycznego ustawienia pola jako zanieczyszczonego. W takim przypadku konieczne będzie jawne ustawienie wartości pola zanieczyszczony. Flaga znajdująca się w [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) kontroluje to automatyczne sprawdzanie pól.

Gdy obiekt zestawu rekordów jest pessimistically zablokowany w środowisku wielodostępnym, rekord pozostaje zablokowany od czasu `Edit` do momentu ukończenia aktualizacji. Jeśli zestaw rekordów jest optymistycznie zablokowany, rekord jest zablokowany i porównywany z wstępnie edytowanym rekordem tuż przed zaktualizowaniem w bazie danych. Jeśli rekord został zmieniony od momentu wywołania `Edit` , `Update` operacja kończy się niepowodzeniem, a MFC zgłasza wyjątek. Tryb blokowania można zmienić za pomocą `SetLockingMode` .

> [!NOTE]
> Optymistyczne blokowanie jest zawsze używane w formatach zewnętrznych baz danych, takich jak ODBC i Instalowalna ISAM.

Bieżący rekord pozostaje aktualny po wywołaniu `Edit` . Aby wywołać `Edit` , musi istnieć bieżący rekord. Jeśli nie ma bieżącego rekordu lub zestaw rekordów nie odwołuje się do otwartego obiektu typu tabela lub zestaw typu dynamiczny, wystąpi wyjątek. Wywoływanie `Edit` powoduje, że jest `CDaoException` zgłaszany w następujących warunkach:

- Brak bieżącego rekordu.

- Baza danych lub zestaw rekordów jest tylko do odczytu.

- Żadne pola w rekordzie nie są aktualizowalne.

- Baza danych lub zestaw rekordów został otwarty do wyłącznego użytku przez innego użytkownika.

- Inny użytkownik zablokował stronę zawierającą Twój rekord.

Jeśli źródło danych obsługuje transakcje, można utworzyć `Edit` część wywołania transakcji. Należy pamiętać, że należy wywołać `CDaoWorkspace::BeginTrans` przed wywołaniem `Edit` i po otwarciu zestawu rekordów. Należy również zauważyć, że wywołanie `CDaoWorkspace::CommitTrans` nie zastępuje wywołania, `Update` Aby ukończyć `Edit` operację. Aby uzyskać więcej informacji na temat transakcji, zobacz Klasa `CDaoWorkspace` .

Aby uzyskać powiązane informacje, zobacz tematy "Metoda AddNew", "Edytuj metodę", "Delete Method", "Metoda aktualizacji" i "aktualizowalne właściwości" w pomocy DAO.

## <a name="cdaorecordsetfillcache"></a><a name="fillcache"></a> CDaoRecordset:: FillCache

Wywołaj tę funkcję elementu członkowskiego, aby buforować określoną liczbę rekordów z zestawu rekordów.

```cpp
void FillCache(
    long* pSize = NULL,
    COleVariant* pBookmark = NULL);
```

### <a name="parameters"></a>Parametry

*pSize*<br/>
Określa liczbę wierszy do wypełnienia w pamięci podręcznej. Jeśli pominięto ten parametr, wartość jest określana przez ustawienie właściwości CacheSize bazowego obiektu DAO.

*pBookmark*<br/>
[COleVariant](../../mfc/reference/colevariant-class.md) określający zakładkę. Pamięć podręczna jest wypełniana począwszy od rekordu wskazanego przez tę zakładkę. Jeśli pominięto ten parametr, pamięć podręczna zostanie wypełniona z rekordu wskazanego przez właściwość CacheStart bazowego obiektu DAO.

### <a name="remarks"></a>Uwagi

Buforowanie zwiększa wydajność aplikacji pobierającej lub pobierającej dane z serwera zdalnego. Pamięć podręczna jest spacją w pamięci lokalnej, która przechowuje dane ostatnio pobrane z serwera w założeniu, że dane będą prawdopodobnie ponownie żądane, gdy aplikacja jest uruchomiona. Gdy dane są żądane, aparat bazy danych Microsoft Jet najpierw sprawdza pamięć podręczną dla danych zamiast pobierać ją z serwera, co zajmuje więcej czasu. Używanie buforowania danych w źródłach danych innych niż ODBC nie ma żadnego efektu, ponieważ dane nie są zapisywane w pamięci podręcznej.

Zamiast czekać na wypełnienie pamięci podręcznej przy użyciu rekordów, które są pobierane, można jawnie wypełnić pamięć podręczną w dowolnym momencie, wywołując `FillCache` funkcję elementu członkowskiego. Jest to szybszy sposób wypełnienia pamięci podręcznej, ponieważ program `FillCache` Pobiera kilka rekordów jednocześnie zamiast jednego. Na przykład podczas wyświetlania poszczególnych ekranów rekordów można wywołać aplikację, `FillCache` Aby pobrać następny ekran z rekordami.

Dowolna baza danych ODBC, do której uzyskuje dostęp z obiektami zestawu rekordów, może mieć lokalną pamięć podręczną Aby utworzyć pamięć podręczną, Otwórz obiekt zestawu rekordów ze zdalnego źródła danych, a następnie Wywołaj `SetCacheSize` `SetCacheStart` funkcje i składowe zestawu rekordów. Jeśli *lSize* i *lBookmark* tworzą zakres, który jest częściowo lub w całości spoza zakresu określonego przez `SetCacheSize` i `SetCacheStart` , część zestawu rekordów spoza tego zakresu jest ignorowana i nie jest załadowana do pamięci podręcznej. Jeśli `FillCache` żądania większej liczby rekordów są pozostawać w zdalnym źródle danych, pobierane są tylko pozostałe rekordy i nie jest zgłaszany żaden wyjątek.

Rekordy pobrane z pamięci podręcznej nie odzwierciedlają zmian wprowadzonych jednocześnie do danych źródłowych przez innych użytkowników.

`FillCache` Pobiera tylko te rekordy, które nie są już buforowane. Aby wymusić aktualizację wszystkich danych w pamięci podręcznej, wywołaj `SetCacheSize` funkcję członkowską z parametrem *lSize* równym 0, wywołaj `SetCacheSize` ponownie parametr *lSize* , który jest równy rozmiarowi pierwotnie zażądanej pamięci podręcznej, a następnie Wywołaj polecenie `FillCache` .

Aby uzyskać powiązane informacje, zobacz temat "Metoda FillCache" w pomocy DAO.

## <a name="cdaorecordsetfind"></a><a name="find"></a> CDaoRecordset:: find

Wywołaj tę funkcję elementu członkowskiego, aby zlokalizować określony ciąg w zestawie rekordów typu "dynamiczny" lub "snapshot-Type" przy użyciu operatora porównania.

```cpp
virtual BOOL Find(
    long lFindType,
    LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lFindType*<br/>
Wartość wskazująca żądany typ operacji wyszukiwania. Możliwe wartości są następujące:

- AFX_DAO_NEXT znaleźć kolejnej lokalizacji pasującego ciągu.

- AFX_DAO_PREV znaleźć poprzedniej lokalizacji pasującego ciągu.

- AFX_DAO_FIRST znaleźć pierwszej lokalizacji pasującego ciągu.

- AFX_DAO_LAST znaleźć ostatniej lokalizacji pasującego ciągu.

*lpszFilter*<br/>
Wyrażenie ciągu (takie jak klauzula **WHERE** w instrukcji SQL bez słowa **WHERE**) użytego do zlokalizowania rekordu. Na przykład:

[!code-cpp[NVC_MFCDatabase#3](../../mfc/codesnippet/cpp/cdaorecordset-class_3.cpp)]

### <a name="return-value"></a>Wartość zwracana

Nierówna zero, jeśli znaleziono pasujące rekordy, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Można znaleźć pierwsze, następne, poprzednie lub ostatnie wystąpienie ciągu. `Find` jest funkcją wirtualną, dlatego można ją zastąpić i dodać własną implementację. `FindFirst`Funkcje, `FindLast` , `FindNext` i `FindPrev` składowe wywołują `Find` funkcję członkowską, więc można użyć `Find` do sterowania zachowaniem wszystkich operacji znajdowania.

Aby zlokalizować rekord w zestawie rekordów typu tabeli, wywołaj funkcję [wyszukiwania](#seek) elementu członkowskiego.

> [!TIP]
> Im mniejszy zestaw rekordów, tym bardziej efektywna `Find` będzie. Ogólnie rzecz biorąc, szczególnie w przypadku danych ODBC, lepiej jest utworzyć nowe zapytanie, które pobiera tylko potrzebne rekordy.

Aby uzyskać powiązane informacje, zobacz temat "FindFirst, FindLast, ZnajdźNastępny, FindPrevious Methods" w pomocy DAO.

## <a name="cdaorecordsetfindfirst"></a><a name="findfirst"></a> CDaoRecordset:: FindFirst

Wywołaj tę funkcję elementu członkowskiego, aby znaleźć pierwszy rekord zgodny z określonym warunkiem.

```cpp
BOOL FindFirst(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lpszFilter*<br/>
Wyrażenie ciągu (takie jak klauzula **WHERE** w instrukcji SQL bez słowa **WHERE**) użytego do zlokalizowania rekordu.

### <a name="return-value"></a>Wartość zwracana

Nierówna zero, jeśli znaleziono pasujące rekordy, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`FindFirst`Funkcja członkowska rozpoczyna wyszukiwanie od początku zestawu rekordów i wyszukuje na końcu zestawu rekordów.

Jeśli chcesz uwzględnić wszystkie rekordy w wyszukiwaniu (nie tylko te, które spełniają określony warunek), użyj jednej z operacji przenoszenia, aby przejść z rekordu do rekordu. Aby zlokalizować rekord w zestawie rekordów typu tabeli, wywołaj `Seek` funkcję członkowską.

Jeśli rekord pasujący do kryteriów nie znajduje się, wskaźnik bieżącego rekordu nie zostanie określony i `FindFirst` zwróci zero. Jeśli zestaw rekordów zawiera więcej niż jeden rekord spełniający kryteria, `FindFirst` lokalizuje pierwsze wystąpienie, `FindNext` lokalizuje następne wystąpienie i tak dalej.

> [!CAUTION]
> Jeśli edytujesz bieżący rekord, pamiętaj o zapisaniu zmian, wywołując `Update` funkcję członkowską przed przejściem do innego rekordu. Jeśli przejdziesz do innego rekordu bez aktualizacji, zmiany zostaną utracone bez ostrzeżenia.

`Find`Funkcja członkowska wyszukuje w lokalizacji i w kierunku określonym w poniższej tabeli:

|Operacje znajdowania|Rozpocznij|Kierunek wyszukiwania|
|---------------------|-----------|----------------------|
|`FindFirst`|Początek zestawu rekordów|Koniec zestawu rekordów|
|`FindLast`|Koniec zestawu rekordów|Początek zestawu rekordów|
|`FindNext`|Bieżący rekord|Koniec zestawu rekordów|
|`FindPrevious`|Bieżący rekord|Początek zestawu rekordów|

> [!NOTE]
> Po wywołaniu `FindLast` , aparat bazy danych Microsoft Jet w pełni wypełnia zestaw rekordów przed rozpoczęciem wyszukiwania, jeśli nie zostało to jeszcze zrobione. Pierwsze wyszukiwanie może trwać dłużej niż kolejne wyszukiwania.

Użycie jednej z operacji znajdowania nie jest takie samo jak wywołanie `MoveFirst` lub `MoveNext` , które po prostu tworzy pierwszy lub następny rekord, bez określania warunku. Możesz wykonać operację wyszukiwania z operacją przenoszenia.

Przy użyciu operacji znajdowania należy pamiętać o następujących kwestiach:

- Jeśli `Find` zwraca wartość różną od zera, bieżący rekord nie jest zdefiniowany. W takim przypadku musisz pomieścić bieżący wskaźnik rekordu z powrotem do prawidłowego rekordu.

- Nie można użyć operacji Find z przewijanym typem migawek tylko do przodu.

- Należy użyć formatu daty w Stanach Zjednoczonych (miesiąc-dzień-rok) podczas wyszukiwania pól zawierających daty, nawet jeśli nie jest używana amerykańska wersja aparatu bazy danych Microsoft Jet. w przeciwnym razie nie można znaleźć pasujących rekordów.

- Podczas pracy z bazami danych ODBC i dużymi dynamicznymi zestawami można stwierdzić, że użycie operacji znajdowania jest wolne, szczególnie podczas pracy z dużymi zestawami rekordów. Można zwiększyć wydajność przy użyciu zapytań SQL z dostosowanymi klauzulami **ORDERBY** lub **WHERE** , kwerendami parametrycznymi lub `CDaoQuerydef` obiektami, które pobierają określone indeksowane rekordy.

Aby uzyskać powiązane informacje, zobacz temat "FindFirst, FindLast, ZnajdźNastępny, FindPrevious Methods" w pomocy DAO.

## <a name="cdaorecordsetfindlast"></a><a name="findlast"></a> CDaoRecordset:: FindLast

Wywołaj tę funkcję elementu członkowskiego, aby znaleźć ostatni rekord zgodny z określonym warunkiem.

```cpp
BOOL FindLast(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lpszFilter*<br/>
Wyrażenie ciągu (takie jak klauzula **WHERE** w instrukcji SQL bez słowa **WHERE**) użytego do zlokalizowania rekordu.

### <a name="return-value"></a>Wartość zwracana

Nierówna zero, jeśli znaleziono pasujące rekordy, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`FindLast`Funkcja członkowska rozpoczyna wyszukiwanie na końcu zestawu rekordów i przeszukuje wstecz w kierunku początku zestawu rekordów.

Jeśli chcesz uwzględnić wszystkie rekordy w wyszukiwaniu (nie tylko te, które spełniają określony warunek), użyj jednej z operacji przenoszenia, aby przejść z rekordu do rekordu. Aby zlokalizować rekord w zestawie rekordów typu tabeli, wywołaj `Seek` funkcję członkowską.

Jeśli rekord pasujący do kryteriów nie znajduje się, wskaźnik bieżącego rekordu nie zostanie określony i `FindLast` zwróci zero. Jeśli zestaw rekordów zawiera więcej niż jeden rekord spełniający kryteria, `FindFirst` lokalizuje pierwsze wystąpienie, `FindNext` lokalizuje następne wystąpienie po pierwszym wystąpieniu itd.

> [!CAUTION]
> Jeśli edytujesz bieżący rekord, pamiętaj, aby zapisać zmiany, wywołując `Update` funkcję członkowską przed przejściem do innego rekordu. Jeśli przejdziesz do innego rekordu bez aktualizacji, zmiany zostaną utracone bez ostrzeżenia.

Użycie jednej z operacji znajdowania nie jest takie samo jak wywołanie `MoveFirst` lub `MoveNext` , które po prostu tworzy pierwszy lub następny rekord, bez określania warunku. Możesz wykonać operację wyszukiwania z operacją przenoszenia.

Przy użyciu operacji znajdowania należy pamiętać o następujących kwestiach:

- Jeśli `Find` zwraca wartość różną od zera, bieżący rekord nie jest zdefiniowany. W takim przypadku musisz pomieścić bieżący wskaźnik rekordu z powrotem do prawidłowego rekordu.

- Nie można użyć operacji Find z przewijanym typem migawek tylko do przodu.

- Należy użyć formatu daty w Stanach Zjednoczonych (miesiąc-dzień-rok) podczas wyszukiwania pól zawierających daty, nawet jeśli nie jest używana amerykańska wersja aparatu bazy danych Microsoft Jet. w przeciwnym razie nie można znaleźć pasujących rekordów.

- Podczas pracy z bazami danych ODBC i dużymi dynamicznymi zestawami można stwierdzić, że użycie operacji znajdowania jest wolne, szczególnie podczas pracy z dużymi zestawami rekordów. Można zwiększyć wydajność przy użyciu zapytań SQL z dostosowanymi klauzulami **ORDERBY** lub **WHERE** , kwerendami parametrycznymi lub `CDaoQuerydef` obiektami, które pobierają określone indeksowane rekordy.

Aby uzyskać powiązane informacje, zobacz temat "FindFirst, FindLast, ZnajdźNastępny, FindPrevious Methods" w pomocy DAO.

## <a name="cdaorecordsetfindnext"></a><a name="findnext"></a> CDaoRecordset:: ZnajdźNastępny

Wywołaj tę funkcję elementu członkowskiego, aby znaleźć następny rekord zgodny z określonym warunkiem.

```cpp
BOOL FindNext(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lpszFilter*<br/>
Wyrażenie ciągu (takie jak klauzula **WHERE** w instrukcji SQL bez słowa **WHERE**) użytego do zlokalizowania rekordu.

### <a name="return-value"></a>Wartość zwracana

Nierówna zero, jeśli znaleziono pasujące rekordy, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`FindNext`Funkcja członkowska rozpoczyna wyszukiwanie w bieżącym rekordzie i wyszukuje na końcu zestawu rekordów.

Jeśli chcesz uwzględnić wszystkie rekordy w wyszukiwaniu (nie tylko te, które spełniają określony warunek), użyj jednej z operacji przenoszenia, aby przejść z rekordu do rekordu. Aby zlokalizować rekord w zestawie rekordów typu tabeli, wywołaj `Seek` funkcję członkowską.

Jeśli rekord pasujący do kryteriów nie znajduje się, wskaźnik bieżącego rekordu nie zostanie określony i `FindNext` zwróci zero. Jeśli zestaw rekordów zawiera więcej niż jeden rekord spełniający kryteria, `FindFirst` lokalizuje pierwsze wystąpienie, `FindNext` lokalizuje następne wystąpienie i tak dalej.

> [!CAUTION]
> Jeśli edytujesz bieżący rekord, pamiętaj, aby zapisać zmiany, wywołując `Update` funkcję członkowską przed przejściem do innego rekordu. Jeśli przejdziesz do innego rekordu bez aktualizacji, zmiany zostaną utracone bez ostrzeżenia.

Użycie jednej z operacji znajdowania nie jest takie samo jak wywołanie `MoveFirst` lub `MoveNext` , które po prostu tworzy pierwszy lub następny rekord, bez określania warunku. Możesz wykonać operację wyszukiwania z operacją przenoszenia.

Przy użyciu operacji znajdowania należy pamiętać o następujących kwestiach:

- Jeśli `Find` zwraca wartość różną od zera, bieżący rekord nie jest zdefiniowany. W takim przypadku musisz pomieścić bieżący wskaźnik rekordu z powrotem do prawidłowego rekordu.

- Nie można użyć operacji Find z przewijanym typem migawek tylko do przodu.

- Należy użyć formatu daty w Stanach Zjednoczonych (miesiąc-dzień-rok) podczas wyszukiwania pól zawierających daty, nawet jeśli nie jest używana amerykańska wersja aparatu bazy danych Microsoft Jet. w przeciwnym razie nie można znaleźć pasujących rekordów.

- Podczas pracy z bazami danych ODBC i dużymi dynamicznymi zestawami można stwierdzić, że użycie operacji znajdowania jest wolne, szczególnie podczas pracy z dużymi zestawami rekordów. Można zwiększyć wydajność przy użyciu zapytań SQL z dostosowanymi klauzulami **ORDERBY** lub **WHERE** , kwerendami parametrycznymi lub `CDaoQuerydef` obiektami, które pobierają określone indeksowane rekordy.

Aby uzyskać powiązane informacje, zobacz temat "FindFirst, FindLast, ZnajdźNastępny, FindPrevious Methods" w pomocy DAO.

## <a name="cdaorecordsetfindprev"></a><a name="findprev"></a> CDaoRecordset:: FindPrev

Wywołaj tę funkcję elementu członkowskiego, aby znaleźć poprzedni rekord zgodny z określonym warunkiem.

```cpp
BOOL FindPrev(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lpszFilter*<br/>
Wyrażenie ciągu (takie jak klauzula **WHERE** w instrukcji SQL bez słowa **WHERE**) użytego do zlokalizowania rekordu.

### <a name="return-value"></a>Wartość zwracana

Nierówna zero, jeśli znaleziono pasujące rekordy, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`FindPrev`Funkcja członkowska rozpoczyna wyszukiwanie w bieżącym rekordzie i wyszukuje wstecz w kierunku początku zestawu rekordów.

Jeśli chcesz uwzględnić wszystkie rekordy w wyszukiwaniu (nie tylko te, które spełniają określony warunek), użyj jednej z operacji przenoszenia, aby przejść z rekordu do rekordu. Aby zlokalizować rekord w zestawie rekordów typu tabeli, wywołaj `Seek` funkcję członkowską.

Jeśli rekord pasujący do kryteriów nie znajduje się, wskaźnik bieżącego rekordu nie zostanie określony i `FindPrev` zwróci zero. Jeśli zestaw rekordów zawiera więcej niż jeden rekord spełniający kryteria, `FindFirst` lokalizuje pierwsze wystąpienie, `FindNext` lokalizuje następne wystąpienie i tak dalej.

> [!CAUTION]
> Jeśli edytujesz bieżący rekord, pamiętaj, aby zapisać zmiany, wywołując `Update` funkcję członkowską przed przejściem do innego rekordu. Jeśli przejdziesz do innego rekordu bez aktualizacji, zmiany zostaną utracone bez ostrzeżenia.

Użycie jednej z operacji znajdowania nie jest takie samo jak wywołanie `MoveFirst` lub `MoveNext` , które po prostu tworzy pierwszy lub następny rekord, bez określania warunku. Możesz wykonać operację wyszukiwania z operacją przenoszenia.

Przy użyciu operacji znajdowania należy pamiętać o następujących kwestiach:

- Jeśli `Find` zwraca wartość różną od zera, bieżący rekord nie jest zdefiniowany. W takim przypadku musisz pomieścić bieżący wskaźnik rekordu z powrotem do prawidłowego rekordu.

- Nie można użyć operacji Find z przewijanym typem migawek tylko do przodu.

- Należy użyć formatu daty w Stanach Zjednoczonych (miesiąc-dzień-rok) podczas wyszukiwania pól zawierających daty, nawet jeśli nie jest używana amerykańska wersja aparatu bazy danych Microsoft Jet. w przeciwnym razie nie można znaleźć pasujących rekordów.

- Podczas pracy z bazami danych ODBC i dużymi dynamicznymi zestawami można stwierdzić, że użycie operacji znajdowania jest wolne, szczególnie podczas pracy z dużymi zestawami rekordów. Można zwiększyć wydajność przy użyciu zapytań SQL z dostosowanymi klauzulami **ORDERBY** lub **WHERE** , kwerendami parametrycznymi lub `CDaoQuerydef` obiektami, które pobierają określone indeksowane rekordy.

Aby uzyskać powiązane informacje, zobacz temat "FindFirst, FindLast, ZnajdźNastępny, FindPrevious Methods" w pomocy DAO.

## <a name="cdaorecordsetgetabsoluteposition"></a><a name="getabsoluteposition"></a> CDaoRecordset:: GetAbsolutePosition

Zwraca numer rekordu bieżącego rekordu obiektu zestawu rekordów.

```cpp
long GetAbsolutePosition();
```

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita z zakresu od 0 do liczby rekordów w zestawie rekordów. Odnosi się do pozycji porządkowej bieżącego rekordu w zestawie rekordów.

### <a name="remarks"></a>Uwagi

Wartość właściwości AbsolutePosition bazowego obiektu DAO jest zależna od zera. ustawienie wartości 0 oznacza pierwszy rekord w zestawie rekordów. Możesz określić liczbę wypełnionych rekordów w zestawie rekordów, wywołując [GetRecordCount](#getrecordcount). Wywoływanie `GetRecordCount` może zająć trochę czasu, ponieważ musi on mieć dostęp do wszystkich rekordów, aby określić liczbę.

Jeśli nie ma bieżącego rekordu, ponieważ nie ma żadnych rekordów w zestawie rekordów, zwracany jest 1. Jeśli bieżący rekord zostanie usunięty, wartość właściwości AbsolutePosition nie jest zdefiniowana, a MFC zgłasza wyjątek, jeśli istnieje odwołanie. W przypadku zestawów rekordów typu dynamicznego do końca sekwencji dodawane są nowe rekordy.

> [!NOTE]
> Ta właściwość nie jest przeznaczona do użycia jako numer rekordu zastępczego. Zakładki są nadal zalecanym sposobem zachowywania i powrotu do danego położenia i są jedynym sposobem pozycjonowania bieżącego rekordu we wszystkich typach obiektów zestawu rekordów. W szczególności pozycja danego rekordu zmienia się, gdy rekordy, które poprzedzają, są usuwane. Nie ma również gwarancji, że dany rekord będzie miał tę samą bezwzględną pozycję, jeśli zestaw rekordów zostanie ponownie utworzony, ponieważ kolejność poszczególnych rekordów w zestawie rekordów nie jest gwarantowana, chyba że zostanie utworzona za pomocą instrukcji SQL przy użyciu klauzuli **ORDERBY** .

> [!NOTE]
> Ta funkcja członkowska jest prawidłowa tylko dla zestawów rekordów typu dynamiczny i typu migawka.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość AbsolutePosition" w pomocy DAO.

## <a name="cdaorecordsetgetbookmark"></a><a name="getbookmark"></a> CDaoRecordset:: GetBookmark

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wartość zakładki w określonym rekordzie.

```cpp
COleVariant GetBookmark();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość reprezentującą zakładkę dla bieżącego rekordu.

### <a name="remarks"></a>Uwagi

Gdy obiekt zestawu rekordów zostanie utworzony lub otwarty, każdy z jego rekordów ma już unikatową zakładkę, jeśli je obsługuje. Wywołaj, `CanBookmark` Aby określić, czy zestaw rekordów obsługuje zakładki.

Możesz zapisać zakładkę dla bieżącego rekordu, przypisując wartość zakładki do `COleVariant` obiektu. Aby szybko wrócić do tego rekordu w dowolnym momencie po przejściu do innego rekordu, należy wywołać `SetBookmark` parametr odpowiadający wartości tego `COleVariant` obiektu.

> [!NOTE]
> Wywołanie zmian [kwerendy](#requery) dla zakładki DAO.

Aby uzyskać powiązane informacje, zobacz temat "właściwość zakładki" w pomocy DAO.

## <a name="cdaorecordsetgetcachesize"></a><a name="getcachesize"></a> CDaoRecordset:: GetCacheSize

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać liczbę buforowanych rekordów.

```cpp
long GetCacheSize();
```

### <a name="return-value"></a>Wartość zwracana

Wartość określająca liczbę rekordów w zestawie rekordów typu zestaw dynamiczny zawierający dane, które mają być lokalnie buforowane ze źródła danych ODBC.

### <a name="remarks"></a>Uwagi

Buforowanie danych zwiększa wydajność aplikacji, która pobiera dane z serwera zdalnego za pośrednictwem obiektów zestawu rekordów typu dynamicznego. Pamięć podręczna to miejsce w pamięci lokalnej, w którym znajdują się dane ostatnio pobierane z serwera w przypadku, gdy aplikacja będzie ponownie żądała danych. Gdy dane są żądane, aparat bazy danych Microsoft Jet najpierw sprawdza pamięć podręczną pod kątem żądanych danych zamiast pobierać je z serwera, co zajmuje więcej czasu. Dane, które nie pochodzą ze źródła danych ODBC, nie są zapisywane w pamięci podręcznej.

Każde źródło danych ODBC, takie jak dołączona tabela, może mieć lokalną pamięć podręczną.

Aby uzyskać powiązane informacje, zobacz temat "CacheSize, CacheStart Properties" w pomocy DAO.

## <a name="cdaorecordsetgetcachestart"></a><a name="getcachestart"></a> CDaoRecordset:: GetCacheStart

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wartość zakładki pierwszego rekordu w zestawie rekordów, który ma zostać zbuforowany.

```cpp
COleVariant GetCacheStart();
```

### <a name="return-value"></a>Wartość zwracana

A `COleVariant` określa zakładkę pierwszego rekordu w zestawie rekordów, który ma zostać zbuforowany.

### <a name="remarks"></a>Uwagi

Aparat bazy danych Microsoft Jet żąda rekordów w zakresie pamięci podręcznej z pamięci podręcznej i żąda rekordów poza zakresem pamięci podręcznej z serwera.

> [!NOTE]
> Rekordy pobrane z pamięci podręcznej nie odzwierciedlają zmian wprowadzonych jednocześnie do danych źródłowych przez innych użytkowników.

Aby uzyskać powiązane informacje, zobacz temat "CacheSize, CacheStart Properties" w pomocy DAO.

## <a name="cdaorecordsetgetcurrentindex"></a><a name="getcurrentindex"></a> CDaoRecordset:: GetCurrentIndex

Wywołaj tę funkcję elementu członkowskiego, aby określić aktualnie używany indeks w obiekcie typu indeksowanej tabeli `CDaoRecordset` .

```cpp
CString GetCurrentIndex();
```

### <a name="return-value"></a>Wartość zwracana

A `CString` zawiera nazwę indeksu, który jest aktualnie używany z zestawem rekordów typu tabela. Zwraca pusty ciąg, jeśli nie ustawiono indeksu.

### <a name="remarks"></a>Uwagi

Ten indeks jest podstawą do porządkowania rekordów w zestawie rekordów typu tabela i jest używany przez funkcję elementu członkowskiego [wyszukiwania](#seek) do lokalizowania rekordów.

`CDaoRecordset`Obiekt może mieć więcej niż jeden indeks, ale może korzystać tylko z jednego indeksu jednocześnie (mimo że obiekt [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) może mieć zdefiniowaną kilka indeksów).

Aby uzyskać powiązane informacje, zobacz temat "indeks obiektu" i definicja "bieżący indeks" w pomocy DAO.

## <a name="cdaorecordsetgetdatecreated"></a><a name="getdatecreated"></a> CDaoRecordset:: GetDateCreated

Wywołaj tę funkcję elementu członkowskiego, aby pobrać datę i godzinę utworzenia tabeli bazowej.

```cpp
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) zawierający datę i godzinę utworzenia tabeli podstawowej.

### <a name="remarks"></a>Uwagi

Ustawienia daty i godziny są wyprowadzane z komputera, na którym utworzono tabelę bazową.

Aby uzyskać powiązane informacje, zobacz temat "DateCreated, LastUpdated Properties" w pomocy DAO.

## <a name="cdaorecordsetgetdatelastupdated"></a><a name="getdatelastupdated"></a> CDaoRecordset:: GetDateLastUpdated

Wywołaj tę funkcję elementu członkowskiego, aby pobrać datę i godzinę ostatniej aktualizacji schematu.

```cpp
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) zawierający datę i godzinę ostatniej aktualizacji struktury tabeli bazowej (schematu).

### <a name="remarks"></a>Uwagi

Ustawienia daty i godziny są wyprowadzane z komputera, na którym została ostatnio zaktualizowana struktura tabeli bazowej (schemat).

Aby uzyskać powiązane informacje, zobacz temat "DateCreated, LastUpdated Properties" w pomocy DAO.

## <a name="cdaorecordsetgetdefaultdbname"></a><a name="getdefaultdbname"></a> CDaoRecordset:: GetDefaultDBName

Wywołaj tę funkcję elementu członkowskiego, aby określić nazwę bazy danych dla tego zestawu rekordów.

```cpp
virtual CString GetDefaultDBName();
```

### <a name="return-value"></a>Wartość zwracana

A `CString` , który zawiera ścieżkę i nazwę bazy danych, z której pochodzi ten zestaw rekordów.

### <a name="remarks"></a>Uwagi

Jeśli zestaw rekordów jest tworzony bez wskaźnika do elementu [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md), ta ścieżka jest używana przez zestaw rekordów, aby otworzyć domyślną bazę danych. Domyślnie ta funkcja zwraca pusty ciąg. Gdy ClassWizard dziedziczy nowy zestaw rekordów z `CDaoRecordset` , utworzy tę funkcję.

Poniższy przykład ilustruje użycie podwójnego ukośnika odwrotnego ( \\ \\ ) w ciągu, tak jak jest to wymagane, aby ciąg był poprawnie interpretowany.

[!code-cpp[NVC_MFCDatabase#4](../../mfc/codesnippet/cpp/cdaorecordset-class_4.cpp)]

## <a name="cdaorecordsetgetdefaultsql"></a><a name="getdefaultsql"></a> CDaoRecordset:: GetDefaultSQL

Struktura wywołuje tę funkcję elementu członkowskiego, aby uzyskać domyślną instrukcję SQL, na której bazuje zestaw rekordów.

```cpp
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>Wartość zwracana

A `CString` , który zawiera domyślną instrukcję języka SQL.

### <a name="remarks"></a>Uwagi

Może to być nazwa tabeli lub instrukcja **SELECT** języka SQL.

Można pośrednio zdefiniować domyślną instrukcję SQL, deklarując klasę zestawu rekordów z ClassWizard i ClassWizard wykonuje to zadanie.

Jeśli przekażesz pusty ciąg SQL do [otwarcia](#open), ta funkcja jest wywoływana, aby określić nazwę tabeli lub kod SQL dla zestawu rekordów.

## <a name="cdaorecordsetgeteditmode"></a><a name="geteditmode"></a> CDaoRecordset:: geteditmode

Wywołaj tę funkcję elementu członkowskiego, aby określić stan edycji, która jest jedną z następujących wartości:

```cpp
short GetEditMode();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość wskazującą stan edycji bieżącego rekordu.

### <a name="remarks"></a>Uwagi

|Wartość|Opis|
|-----------|-----------------|
|`dbEditNone`|Operacja edytowania nie jest w toku.|
|`dbEditInProgress`|`Edit` został wywołany.|
|`dbEditAdd`|`AddNew` został wywołany.|

Aby uzyskać powiązane informacje, zobacz temat "EditMode Property" w pomocy DAO.

## <a name="cdaorecordsetgetfieldcount"></a><a name="getfieldcount"></a> CDaoRecordset:: GetFieldCount

Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę pól (kolumn) zdefiniowanych w zestawie rekordów.

```cpp
short GetFieldCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba pól w zestawie rekordów.

### <a name="remarks"></a>Uwagi

Aby uzyskać powiązane informacje, zobacz temat "Count Property" w pomocy DAO.

## <a name="cdaorecordsetgetfieldinfo"></a><a name="getfieldinfo"></a> CDaoRecordset:: GetFieldInfo

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać informacje o polach w zestawie rekordów.

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

*nIndex*<br/>
Indeks (liczony od zera) wstępnie zdefiniowanego pola w kolekcji pól zestawu rekordów dla wyszukiwania według indeksu.

*FieldInfo*<br/>
Odwołanie do struktury [CDaoFieldInfo —](../../mfc/reference/cdaofieldinfo-structure.md) .

*dwInfoOptions*<br/>
Opcje określające, które informacje o zestawie rekordów mają być pobierane. Dostępne opcje są wymienione w tym miejscu wraz z tym, co spowoduje zwrócenie funkcji. Aby uzyskać najlepszą wydajność, Pobierz tylko wymagany poziom informacji:

- `AFX_DAO_PRIMARY_INFO` Wartooć Nazwa, typ, rozmiar, atrybuty

- `AFX_DAO_SECONDARY_INFO` Informacje podstawowe, plus: pozycja porządkowa, wymagane, Zezwalaj na zerową długość, kolejność sortowania, Nazwa obca, pole źródłowe, tabela źródłowa

- `AFX_DAO_ALL_INFO` Informacje podstawowe i pomocnicze oraz: wartość domyślna, reguła walidacji, tekst walidacji

*lpszName*<br/>
Nazwa pola.

### <a name="remarks"></a>Uwagi

Jedna wersja funkcji pozwala wyszukiwać pola według indeksu. Inna wersja pozwala wyszukiwać pola według nazwy.

Aby uzyskać opis zwracanych informacji, zobacz strukturę [CDaoFieldInfo —](../../mfc/reference/cdaofieldinfo-structure.md) . Ta struktura zawiera elementy członkowskie, które odpowiadają elementom informacji wymienionych powyżej w opisie *dwInfoOptions*. Jeśli zażądasz informacji na jednym poziomie, uzyskasz również informacje na temat wszystkich wcześniejszych poziomów.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość Attributes" w pomocy DAO.

## <a name="cdaorecordsetgetfieldvalue"></a><a name="getfieldvalue"></a> CDaoRecordset:: GetFieldValue —

Wywołaj tę funkcję elementu członkowskiego, aby pobrać dane w zestawie rekordów.

```cpp
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
Odwołanie do `COleVariant` obiektu, w którym będzie przechowywana wartość pola.

*nIndex*<br/>
Indeks (liczony od zera) pola w kolekcji pól zestawu rekordów dla wyszukiwania według indeksu.

### <a name="return-value"></a>Wartość zwracana

Dwie wersje `GetFieldValue` , które zwracają wartość zwracają obiekt [COleVariant](../../mfc/reference/colevariant-class.md) , który zawiera wartość pola.

### <a name="remarks"></a>Uwagi

Można wyszukać pole według nazwy lub pozycji porządkowej.

> [!NOTE]
> Bardziej wydajne jest wywołanie jednej z wersji tej funkcji członkowskiej, która przyjmuje `COleVariant` odwołanie do obiektu jako parametr, zamiast wywoływania wersji, która zwraca `COleVariant` obiekt. Te ostatnie wersje tej funkcji są utrzymywane w celu zapewnienia zgodności z poprzednimi wersjami.

Używaj `GetFieldValue` i [SetFieldValue](#setfieldvalue) do dynamicznego wiązania pól w czasie wykonywania zamiast statycznego powiązania kolumn przy użyciu mechanizmu [DoFieldExchange](#dofieldexchange) .

`GetFieldValue``DoFieldExchange`mechanizm można łączyć w celu zwiększenia wydajności. Na przykład użyj, `GetFieldValue` Aby pobrać wartość, która jest potrzebna tylko na żądanie, i przypisz to wywołanie do przycisku "więcej informacji" w interfejsie.

Aby uzyskać powiązane informacje, zobacz tematy "obiekt pola" i "wartość właściwości" w pomocy DAO.

## <a name="cdaorecordsetgetindexcount"></a><a name="getindexcount"></a> CDaoRecordset:: GetIndexCount

Wywołaj tę funkcję elementu członkowskiego, aby określić liczbę indeksów dostępnych w zestawie rekordów typu tabela.

```cpp
short GetIndexCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba indeksów w zestawie rekordów typu tabela.

### <a name="remarks"></a>Uwagi

`GetIndexCount` jest przydatne do zapętlania przez wszystkie indeksy w zestawie rekordów. W tym celu należy użyć `GetIndexCount` programu w połączeniu z [GetIndexInfo](#getindexinfo). Jeśli wywołujesz tę funkcję elementu członkowskiego w zestawach rekordów typu dynamiczny lub typu migawek, MFC zgłosi wyjątek.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość Attributes" w pomocy DAO.

## <a name="cdaorecordsetgetindexinfo"></a><a name="getindexinfo"></a> CDaoRecordset:: GetIndexInfo

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać różne rodzaje informacji o indeksie zdefiniowanym w podstawowej tabeli bazowej zestawu rekordów.

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

*nIndex*<br/>
Indeks (liczony od zera) w kolekcji indeksów tabeli dla wyszukiwania według pozycji liczbowej.

*indexinfo*<br/>
Odwołanie do struktury [CDaoIndexInfo —](../../mfc/reference/cdaoindexinfo-structure.md) .

*dwInfoOptions*<br/>
Opcje określające, które informacje o indeksie mają zostać pobrane. Dostępne opcje są wymienione w tym miejscu wraz z tym, co spowoduje zwrócenie funkcji. Aby uzyskać najlepszą wydajność, Pobierz tylko wymagany poziom informacji:

- `AFX_DAO_PRIMARY_INFO` Wartooć Nazwa, informacje o polu, pola

- `AFX_DAO_SECONDARY_INFO` Informacje podstawowe oraz: podstawowe, unikatowe, klastrowane, IgnoreNulls, wymagane, obce

- `AFX_DAO_ALL_INFO` Informacje podstawowe i pomocnicze oraz: liczność unikatowych

*lpszName*<br/>
Wskaźnik do nazwy obiektu indeksu dla wyszukiwania według nazwy.

### <a name="remarks"></a>Uwagi

Jedna wersja funkcji pozwala wyszukiwać indeks według pozycji w kolekcji. Inna wersja pozwala wyszukiwać indeks według nazwy.

Aby uzyskać opis zwracanych informacji, zobacz strukturę [CDaoIndexInfo —](../../mfc/reference/cdaoindexinfo-structure.md) . Ta struktura zawiera elementy członkowskie, które odpowiadają elementom informacji wymienionych powyżej w opisie *dwInfoOptions*. Jeśli zażądasz informacji na jednym poziomie, uzyskasz również informacje na temat wszystkich wcześniejszych poziomów.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość Attributes" w pomocy DAO.

## <a name="cdaorecordsetgetlastmodifiedbookmark"></a><a name="getlastmodifiedbookmark"></a> CDaoRecordset:: GetLastModifiedBookmark

Wywołaj tę funkcję elementu członkowskiego, aby pobrać zakładkę ostatnio dodanego lub zaktualizowanego rekordu.

```cpp
COleVariant GetLastModifiedBookmark();
```

### <a name="return-value"></a>Wartość zwracana

`COleVariant`Zawierający zakładkę, która wskazuje ostatnio dodany lub zmieniony rekord.

### <a name="remarks"></a>Uwagi

Gdy obiekt zestawu rekordów zostanie utworzony lub otwarty, każdy z jego rekordów ma już unikatową zakładkę, jeśli je obsługuje. Wywołaj metodę [GetBookmark](#getbookmark) , aby określić, czy zestaw rekordów obsługuje zakładki. Jeśli zestaw rekordów nie obsługuje zakładek, `CDaoException` jest zgłaszany.

Po dodaniu rekordu pojawia się na końcu zestawu rekordów i nie jest bieżącym rekordem. Aby nowy rekord był bieżący, wywołaj, `GetLastModifiedBookmark` a następnie Wywołaj, `SetBookmark` Aby powrócić do nowo dodanego rekordu.

Aby uzyskać powiązane informacje, zobacz temat "LastModified Property" w pomocy DAO.

## <a name="cdaorecordsetgetlockingmode"></a><a name="getlockingmode"></a> CDaoRecordset:: getlockmode

Wywołaj tę funkcję elementu członkowskiego, aby określić typ blokowania w celu zastosowania zestawu rekordów.

```cpp
BOOL GetLockingMode();
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli typ blokowania jest pesymistyczny, w przeciwnym razie, w przypadku blokowania rekordów optymistycznych.

### <a name="remarks"></a>Uwagi

Gdy trwa pesymistyczne blokowanie, strona danych zawierająca edytowany rekord jest zablokowana zaraz po wywołaniu funkcji [Edytuj](#edit) członka. Strona jest odblokowana po wywołaniu funkcji [aktualizacji](#update) lub [zamknięcia](#close) elementu członkowskiego albo dowolnej operacji przenoszenia lub wyszukiwania.

Gdy optymistyczne blokowanie jest obowiązujące, strona danych zawierająca rekord jest zablokowana tylko w czasie, gdy rekord jest aktualizowany za pomocą `Update` funkcji składowej.

Podczas pracy ze źródłami danych ODBC tryb blokowania jest zawsze optymistyczny.

Aby uzyskać powiązane informacje, zobacz tematy "Właściwość LockEdits" i "Blokowanie zachowania w aplikacjach wielodostępnych" w pomocy DAO.

## <a name="cdaorecordsetgetname"></a><a name="getname"></a> CDaoRecordset:: GetName

Wywołaj tę funkcję elementu członkowskiego, aby pobrać nazwę zestawu rekordów.

```cpp
CString GetName();
```

### <a name="return-value"></a>Wartość zwracana

A `CString` zawiera nazwę zestawu rekordów.

### <a name="remarks"></a>Uwagi

Nazwa zestawu rekordów musi rozpoczynać się od litery i może zawierać maksymalnie 40 znaków. Może zawierać cyfry i znaki podkreślenia, ale nie może zawierać znaków interpunkcyjnych ani spacji.

Aby uzyskać powiązane informacje, zobacz temat "Nazwa właściwości" w pomocy DAO.

## <a name="cdaorecordsetgetparamvalue"></a><a name="getparamvalue"></a> CDaoRecordset:: GetParamValue

Wywołaj tę funkcję elementu członkowskiego, aby pobrać bieżącą wartość określonego parametru przechowywanego w źródłowym obiekcie DAOParameter.

```cpp
virtual COleVariant GetParamValue(int nIndex);
virtual COleVariant GetParamValue(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Pozycja liczbowa parametru w źródłowym obiekcie DAOParameter.

*lpszName*<br/>
Nazwa parametru, którego wartość ma zostać wybrana.

### <a name="return-value"></a>Wartość zwracana

Obiekt klasy [COleVariant](../../mfc/reference/colevariant-class.md) , który zawiera wartość parametru.

### <a name="remarks"></a>Uwagi

Możesz uzyskać dostęp do parametru według nazwy lub jego pozycji liczbowej w kolekcji.

Aby uzyskać powiązane informacje, zobacz temat "obiekt parametru" w pomocy DAO.

## <a name="cdaorecordsetgetpercentposition"></a><a name="getpercentposition"></a> CDaoRecordset:: GetPercentPosition

Podczas pracy z zestawem rekordów typu dynamicznego lub typu migawek, jeśli wywołujesz `GetPercentPosition` przed pełnym zapełnieniem zestawu rekordów, ilość ruchu jest określana względem liczby rekordów, do których dostęp jest wskazywany przez wywołanie [GetRecordCount](#getrecordcount).

```cpp
float GetPercentPosition();
```

### <a name="return-value"></a>Wartość zwracana

Liczba z zakresu od 0 do 100, która wskazuje przybliżoną lokalizację bieżącego rekordu w obiekcie zestawu rekordów na podstawie procentu rekordów w zestawie rekordów.

### <a name="remarks"></a>Uwagi

Możesz przenieść do ostatniego rekordu, wywołując [MoveLast](#movelast) , aby zakończyć populację wszystkich zestawów rekordów, ale może to potrwać znaczną ilość czasu.

Możesz wywoływać `GetPercentPosition` wszystkie trzy typy obiektów zestawu rekordów, w tym tabele bez indeksów. Nie można jednak wywoływać `GetPercentPosition` tylko migawek przewijanych tylko do przodu lub w zestawie rekordów otwartym z zapytania przekazującego względem zewnętrznej bazy danych. Jeśli nie ma bieżącego rekordu lub został usunięty bieżący rekord, `CDaoException` jest zgłaszany.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość PercentPosition" w pomocy DAO.

## <a name="cdaorecordsetgetrecordcount"></a><a name="getrecordcount"></a> CDaoRecordset:: GetRecordCount

Wywołaj tę funkcję elementu członkowskiego, aby dowiedzieć się, ile rekordów w zestawie rekordów jest dostępnych.

```cpp
long GetRecordCount();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę rekordów, do których można uzyskać dostęp w obiekcie zestawu rekordów.

### <a name="remarks"></a>Uwagi

`GetRecordCount` nie wskazuje, ile rekordów znajduje się w zestawie rekordów typu dynamicznego lub typu migawek, dopóki nie zostanie uzyskany dostęp do wszystkich rekordów. Wykonanie tego wywołania funkcji elementu członkowskiego może zająć dużo czasu.

Po uzyskaniu dostępu do ostatniego rekordu wartość zwracana wskazuje całkowitą liczbę nieusuniętych rekordów w zestawie rekordów. Aby wymusić uzyskanie dostępu do ostatniego rekordu, wywołaj `MoveLast` `FindLast` funkcję lub element członkowski zestawu rekordów. Można również użyć liczby SQL, aby określić przybliżoną liczbę rekordów zwracanych przez zapytanie.

Ponieważ aplikacja usuwa rekordy w zestawie rekordów typu dynamicznego, wartość zwracaną `GetRecordCount` maleje. Rekordy usunięte przez innych użytkowników nie są jednak uwzględniane, `GetRecordCount` dopóki bieżący rekord nie zostanie umieszczony w usuniętym rekordzie. Jeśli zostanie wykonana transakcja wpływająca na liczbę rekordów, a następnie wycofanie transakcji, program `GetRecordCount` nie będzie odzwierciedlał rzeczywistej liczby pozostałych rekordów.

`GetRecordCount`Zmiany w tabelach źródłowych nie wpływają na wartość z zestawu rekordów typu migawka.

Wartość `GetRecordCount` z zestawu rekordów typu tabela odzwierciedla przybliżoną liczbę rekordów w tabeli i jest modyfikowana natychmiast po dodaniu i usunięciu rekordów tabeli.

Zestaw rekordów bez rekordów zwraca wartość 0. Podczas pracy z dołączonymi tabelami lub bazami danych ODBC `GetRecordCount` zawsze zwraca-1. Wywołanie `Requery` funkcji elementu członkowskiego na zestawie rekordów resetuje wartość `GetRecordCount` tak, jakby zapytanie zostało wykonane ponownie.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość RecordCount" w pomocy DAO.

## <a name="cdaorecordsetgetsql"></a><a name="getsql"></a> CDaoRecordset:: GetSQL

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać instrukcję SQL, która została użyta do wybrania rekordów zestawu rekordów, gdy została otwarta.

```cpp
CString GetSQL() const;
```

### <a name="return-value"></a>Wartość zwracana

A `CString` , który zawiera instrukcję języka SQL.

### <a name="remarks"></a>Uwagi

Zwykle będzie to instrukcja **SELECT** języka SQL.

Ciąg zwracany przez `GetSQL` jest zwykle różny od dowolnego ciągu, który mógł zostać przekazana do zestawu rekordów w parametrze *lpszSQL* do funkcji [Open](#open) member. Wynika to z faktu, że zestaw rekordów tworzy pełną instrukcję SQL na podstawie tego, co zostało przesłane do `Open` , co zostało określone za pomocą ClassWizard i co można określić w elementach członkowskich danych [m_strFilter](#m_strfilter) i [m_strSort](#m_strsort) .

> [!NOTE]
> Wywołaj tę funkcję elementu członkowskiego tylko po wywołaniu `Open` .

Aby uzyskać powiązane informacje, zobacz temat "Właściwość SQL" w pomocy DAO.

## <a name="cdaorecordsetgettype"></a><a name="gettype"></a> CDaoRecordset:: GetType

Wywołaj tę funkcję elementu członkowskiego po otwarciu zestawu rekordów, aby określić typ obiektu zestawu rekordów.

```cpp
short GetType();
```

### <a name="return-value"></a>Wartość zwracana

Jedną z następujących wartości, która wskazuje typ zestawu rekordów:

- `dbOpenTable` Zestaw rekordów typu tabela

- `dbOpenDynaset` Zestaw rekordów typu dynamicznego

- `dbOpenSnapshot` Zestaw rekordów typu Snapshot

### <a name="remarks"></a>Uwagi

Aby uzyskać powiązane informacje, zobacz temat "Type Property" w pomocy DAO.

## <a name="cdaorecordsetgetvalidationrule"></a><a name="getvalidationrule"></a> CDaoRecordset:: GetValidationRule

Wywołaj tę funkcję elementu członkowskiego, aby określić regułę używaną do sprawdzania poprawności danych.

```cpp
CString GetValidationRule();
```

### <a name="return-value"></a>Wartość zwracana

`CString`Obiekt zawierający wartość, która weryfikuje dane w rekordzie w miarę ich zmiany lub dodania do tabeli.

### <a name="remarks"></a>Uwagi

Ta reguła jest oparta na tekście i jest stosowana przy każdej zmianie źródłowej tabeli. Jeśli dane nie są dozwolone, MFC zgłasza wyjątek. Zwrócony komunikat o błędzie jest tekstem właściwości ValidationText obiektu pola bazowego, jeśli jest określony, lub tekst wyrażenia określonego przez Właściwość ValidationRule obiektu bazowego pola. Możesz wywołać [GetValidationText](#getvalidationtext) , aby uzyskać tekst komunikatu o błędzie.

Na przykład pole w rekordzie, które wymaga dnia miesiąca, może mieć regułę walidacji, taką jak "dzień z zakresu od 1 do 31".

Aby uzyskać powiązane informacje, zobacz temat "Właściwość ValidationRule" w pomocy DAO.

## <a name="cdaorecordsetgetvalidationtext"></a><a name="getvalidationtext"></a> CDaoRecordset:: GetValidationText

Wywołaj tę funkcję elementu członkowskiego, aby pobrać tekst właściwości ValidationText obiektu pola źródłowego.

```cpp
CString GetValidationText();
```

### <a name="return-value"></a>Wartość zwracana

`CString`Obiekt zawierający tekst komunikatu, który jest wyświetlany, jeśli wartość pola nie spełnia reguły walidacji obiektu bazowego pola.

### <a name="remarks"></a>Uwagi

Aby uzyskać powiązane informacje, zobacz temat "Właściwość ValidationText" w pomocy DAO.

## <a name="cdaorecordsetisbof"></a><a name="isbof"></a> CDaoRecordset:: IsBOF

Wywołaj tę funkcję elementu członkowskiego przed przewinięciem rekordu do rekordu, aby dowiedzieć się, czy przed pierwszym rekordem zestawu rekordów został usunięty.

```cpp
BOOL IsBOF() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli zestaw rekordów nie zawiera żadnych rekordów lub przewinie wstecz przed pierwszym rekordem; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Możesz również wywołać metodę, `IsBOF` `IsEOF` Aby określić, czy zestaw rekordów zawiera wszystkie rekordy, czy jest pusty. Natychmiast po wywołaniu `Open` , jeśli zestaw rekordów nie zawiera żadnych rekordów, `IsBOF` zwraca wartość różną od zera. Po otwarciu zestawu rekordów, który ma co najmniej jeden rekord, pierwszy rekord jest bieżącym rekordem i `IsBOF` zwraca 0.

Jeśli pierwszy rekord jest bieżącym rekordem i wywołaniem `MovePrev` , `IsBOF` następnie zwróci wartość różną od zera. Jeśli `IsBOF` zwraca wartość różną od zera i wywołuje `MovePrev` , zostanie zgłoszony wyjątek. Jeśli `IsBOF` zwraca wartość różną od zera, bieżący rekord jest niezdefiniowany, a każda akcja, która wymaga bieżącego rekordu, spowoduje wyjątek.

Wpływ określonych metod `IsBOF` i `IsEOF` ustawień:

- Wywołanie `Open*` wewnętrznie powoduje, że pierwszy rekord w zestawie rekordów jest bieżącym rekordem przez wywołanie `MoveFirst` . W związku z tym, wywołanie `Open` pustego zestawu rekordów powoduje, że `IsBOF` `IsEOF` zwraca wartość różną od zera. (Zapoznaj się z poniższą tabelą dotyczącą zachowania zakończonego niepowodzeniem `MoveFirst` lub `MoveLast` wywołaniem).

- Wszystkie operacje przenoszenia, które pomyślnie lokalizują rekord powodują `IsBOF` , że oba i `IsEOF` zwracają 0.

- `AddNew`Wywołanie `Update` , które pomyślnie wstawia nowy rekord, spowoduje `IsBOF` zwrócenie 0, ale tylko wtedy, gdy `IsEOF` jest już różna od zera. Stan zawsze pozostanie `IsEOF` niezmieniony. Zgodnie z definicją w aparacie bazy danych Microsoft Jet bieżący wskaźnik rekordu pustego zestawu rekordów znajduje się na końcu pliku, więc każdy nowy rekord zostanie wstawiony po bieżącym rekordzie.

- Każde `Delete` wywołanie, nawet jeśli usuwa tylko pozostałe rekordy z zestawu rekordów, nie spowoduje zmiany wartości `IsBOF` ani `IsEOF` .

W tej tabeli przedstawiono, które operacje przenoszenia są dozwolone dla różnych kombinacji `IsBOF` /  `IsEOF` .

|Stan|MoveFirst, MoveLast|MovePrev<br /><br /> Przenieś < 0|Przenieś 0|Element<br /><br /> Przenieś > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`= niezerowe,<br /><br /> `IsEOF`= 0|Dozwolone|Wyjątek|Wyjątek|Dozwolone|
|`IsBOF`= 0,<br /><br /> `IsEOF`= niezerowe|Dozwolone|Dozwolone|Wyjątek|Wyjątek|
|Oba niezerowe|Wyjątek|Wyjątek|Wyjątek|Wyjątek|
|Oba 0|Dozwolone|Dozwolone|Dozwolone|Dozwolone|

Zezwolenie na operację przenoszenia nie oznacza, że operacja spowoduje pomyślne zlokalizowanie rekordu. Wskazuje jedynie, że próba wykonania określonej operacji przenoszenia jest dozwolona i nie wygeneruje wyjątku. Wartość `IsBOF` i `IsEOF` funkcje elementów członkowskich mogą ulec zmianie w wyniku próby przeniesienia.

W poniższej tabeli przedstawiono skutki operacji przenoszenia, które nie odnoszą się do rekordu wartości `IsBOF` i `IsEOF` ustawień.

|Operacje|IsBOF|IsEOF|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|Różną od zera|Różną od zera|
|`Move` 2,0|Bez zmian|Bez zmian|
|`MovePrev`, `Move` < 0|Różną od zera|Bez zmian|
|`MoveNext`, `Move` > 0|Bez zmian|Różną od zera|

Aby uzyskać powiązane informacje, zobacz temat "BOF, EOF Properties" w pomocy DAO.

## <a name="cdaorecordsetisdeleted"></a><a name="isdeleted"></a> CDaoRecordset:: IsDeleted

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy bieżący rekord został usunięty.

```cpp
BOOL IsDeleted() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli zestaw rekordów jest umieszczony na usuniętym rekordzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli przewiniesz do rekordu i `IsDeleted` zwrócisz wartość true (niezerowa), należy przewinąć do innego rekordu przed wykonaniem innych operacji zestawu rekordów.

> [!NOTE]
> Nie musisz sprawdzać stanu usuniętych rekordów w migawce lub typu tabeli zestawu rekordów. Ponieważ nie można usunąć rekordów z migawki, nie ma potrzeby wywoływania `IsDeleted` . W przypadku zestawów rekordów typu "usunięte rekordy" są w rzeczywistości usuwane z zestawu rekordów. Po usunięciu rekordu, innym użytkownikowi lub w innym zestawie rekordów, nie można przewijać z powrotem do tego rekordu. W związku z tym nie ma potrzeby wywoływania `IsDeleted` .

Po usunięciu rekordu z zestawu dynamicznego zostanie on usunięty i nie można go ponownie przewijać do tego rekordu. Jeśli jednak rekord w zestawie dynamicznym zostanie usunięty przez innego użytkownika lub z innego zestawu rekordów na podstawie tej samej tabeli, `IsDeleted` zwróci wartość true w przypadku późniejszego przewinięcia tego rekordu.

Aby uzyskać powiązane informacje, zobacz temat "Delete Method", "Właściwość LastModified" i "EditMode Property" w pomocy DAO.

## <a name="cdaorecordsetiseof"></a><a name="iseof"></a> CDaoRecordset:: IsEOF

Wywołaj tę funkcję elementu członkowskiego podczas przewijania z rekordu do rekordu, aby dowiedzieć się, czy zostały utracone poza ostatnim rekordem zestawu rekordów.

```cpp
BOOL IsEOF() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli zestaw rekordów nie zawiera żadnych rekordów lub przewinie się poza ostatnim rekordem; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Możesz również wywołać, `IsEOF` Aby określić, czy zestaw rekordów zawiera wszystkie rekordy, czy jest pusty. Natychmiast po wywołaniu `Open` , jeśli zestaw rekordów nie zawiera żadnych rekordów, `IsEOF` zwraca wartość różną od zera. Po otwarciu zestawu rekordów, który ma co najmniej jeden rekord, pierwszy rekord jest bieżącym rekordem i `IsEOF` zwraca 0.

Jeśli ostatni rekord jest bieżącym rekordem podczas wywołania, zwróci `MoveNext` `IsEOF` wynik różny od zera. Jeśli `IsEOF` zwraca wartość różną od zera i wywołuje `MoveNext` , zostanie zgłoszony wyjątek. Jeśli `IsEOF` zwraca wartość różną od zera, bieżący rekord jest niezdefiniowany, a każda akcja, która wymaga bieżącego rekordu, spowoduje wyjątek.

Wpływ określonych metod `IsBOF` i `IsEOF` ustawień:

- Wywołanie `Open` wewnętrznie powoduje, że pierwszy rekord w zestawie rekordów jest bieżącym rekordem przez wywołanie `MoveFirst` . W związku z tym, wywołanie `Open` pustego zestawu rekordów powoduje, że `IsBOF` `IsEOF` zwraca wartość różną od zera. (Zapoznaj się z poniższą tabelą zachowania wywołania zakończonego niepowodzeniem `MoveFirst` ).

- Wszystkie operacje przenoszenia, które pomyślnie lokalizują rekord powodują `IsBOF` , że oba i `IsEOF` zwracają 0.

- `AddNew`Wywołanie `Update` , które pomyślnie wstawia nowy rekord, spowoduje `IsBOF` zwrócenie 0, ale tylko wtedy, gdy `IsEOF` jest już różna od zera. Stan zawsze pozostanie `IsEOF` niezmieniony. Zgodnie z definicją w aparacie bazy danych Microsoft Jet bieżący wskaźnik rekordu pustego zestawu rekordów znajduje się na końcu pliku, więc każdy nowy rekord zostanie wstawiony po bieżącym rekordzie.

- Każde `Delete` wywołanie, nawet jeśli usuwa tylko pozostałe rekordy z zestawu rekordów, nie spowoduje zmiany wartości `IsBOF` ani `IsEOF` .

W tej tabeli przedstawiono, które operacje przenoszenia są dozwolone dla różnych kombinacji `IsBOF` /  `IsEOF` .

|Stan|MoveFirst, MoveLast|MovePrev<br /><br /> Przenieś < 0|Przenieś 0|Element<br /><br /> Przenieś > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`= niezerowe,<br /><br /> `IsEOF`= 0|Dozwolone|Wyjątek|Wyjątek|Dozwolone|
|`IsBOF`= 0,<br /><br /> `IsEOF`= niezerowe|Dozwolone|Dozwolone|Wyjątek|Wyjątek|
|Oba niezerowe|Wyjątek|Wyjątek|Wyjątek|Wyjątek|
|Oba 0|Dozwolone|Dozwolone|Dozwolone|Dozwolone|

Zezwolenie na operację przenoszenia nie oznacza, że operacja spowoduje pomyślne zlokalizowanie rekordu. Wskazuje jedynie, że próba wykonania określonej operacji przenoszenia jest dozwolona i nie wygeneruje wyjątku. Wartość `IsBOF` i `IsEOF` funkcje elementów członkowskich mogą ulec zmianie w wyniku próby przeniesienia.

W poniższej tabeli przedstawiono skutki operacji przenoszenia, które nie odnoszą się do rekordu wartości `IsBOF` i `IsEOF` ustawień.

|Operacje|IsBOF|IsEOF|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|Różną od zera|Różną od zera|
|`Move` 2,0|Bez zmian|Bez zmian|
|`MovePrev`, `Move` < 0|Różną od zera|Bez zmian|
|`MoveNext`, `Move` > 0|Bez zmian|Różną od zera|

Aby uzyskać powiązane informacje, zobacz temat "BOF, EOF Properties" w pomocy DAO.

## <a name="cdaorecordsetisfielddirty"></a><a name="isfielddirty"></a> CDaoRecordset:: IsFieldDirty

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy określony element członkowski danych pola typu dynamicznego został oflagowany jako "zanieczyszczony" (zmieniony).

```cpp
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>Parametry

*wa*<br/>
Wskaźnik do elementu członkowskiego danych pola, którego stan chcesz sprawdzić, lub wartość NULL, aby określić, czy dowolne z pól są zanieczyszczone.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli określony element członkowski danych pola jest oflagowany jako zanieczyszczony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Dane we wszystkich danych zanieczyszczonych są transferowane do rekordu w źródle danych, gdy bieżący rekord zostanie zaktualizowany przez wywołanie `Update` funkcji elementu członkowskiego `CDaoRecordset` (po wywołaniu `Edit` lub `AddNew` ). Korzystając z tej wiedzy, można wykonać dalsze czynności, takie jak nieoflagowanie elementu członkowskiego danych pola w celu oznaczenia kolumny, tak aby nie była ona zapisywana w źródle danych.

`IsFieldDirty` jest zaimplementowany przez `DoFieldExchange` .

## <a name="cdaorecordsetisfieldnull"></a><a name="isfieldnull"></a> CDaoRecordset:: IsFieldNull

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy określony element członkowski danych pola zestawu rekordów został oflagowany jako wartość null.

```cpp
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>Parametry

*wa*<br/>
Wskaźnik do elementu członkowskiego danych pola, którego stan chcesz sprawdzić, lub wartość NULL, aby określić, czy którekolwiek z pól mają wartość null.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli określony element członkowski danych pola jest oflagowany jako null; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

(W terminologii bazy danych wartość null oznacza brak wartości i nie jest taka sama jak wartość NULL w języku C++). Jeśli element członkowski danych pola jest oflagowany jako null, jest interpretowany jako kolumna bieżącego rekordu, dla którego nie ma wartości.

> [!NOTE]
> W niektórych sytuacjach korzystanie z programu `IsFieldNull` może być niewydajne, ponieważ ilustruje poniższy przykład kodu:

[!code-cpp[NVC_MFCDatabase#5](../../mfc/codesnippet/cpp/cdaorecordset-class_5.cpp)]

> [!NOTE]
> Jeśli używasz dynamicznego wiązania rekordów, ale nie pochodzą z programu `CDaoRecordset` , upewnij się, że używasz VT_NULL, jak pokazano w przykładzie.

## <a name="cdaorecordsetisfieldnullable"></a><a name="isfieldnullable"></a> CDaoRecordset:: IsFieldNullable

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy określony element członkowski danych pola jest typu "nullable" (można ustawić wartość null; Język C++ o wartości NULL nie jest taki sam jak wartość null, co w terminologii bazy danych oznacza, że nie ma żadnej wartości.

```cpp
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>Parametry

*wa*<br/>
Wskaźnik do elementu członkowskiego danych pola, którego stan chcesz sprawdzić, lub wartość NULL, aby określić, czy którekolwiek z pól mają wartość null.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli określony element członkowski danych pola może być wartością null; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pole, które nie może mieć wartości null, musi mieć wartość. Jeśli podczas dodawania lub aktualizowania rekordu zostanie podjęta próba ustawienia takiego pola na wartość null, źródło danych odrzuci dodanie lub aktualizację i `Update` zgłosi wyjątek. Wyjątek występuje, gdy jest wywoływany `Update` , nie podczas wywoływania `SetFieldNull` .

## <a name="cdaorecordsetisopen"></a><a name="isopen"></a> CDaoRecordset:: IsOpen

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy zestaw rekordów jest otwarty.

```cpp
BOOL IsOpen() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli `Open` wcześniej wywołano obiekt zestawu rekordów lub `Requery` funkcję członkowską, a zestaw rekordów nie został zamknięty; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

## <a name="cdaorecordsetm_bcheckcachefordirtyfields"></a><a name="m_bcheckcachefordirtyfields"></a> CDaoRecordset:: m_bCheckCacheForDirtyFields

Zawiera flagę wskazującą, czy buforowane pola są automatycznie oznaczane jako zanieczyszczone (zmienione) i zerowe.

### <a name="remarks"></a>Uwagi

Domyślna flaga to TRUE. Ustawienie w tym elemencie członkowskim danych kontroluje cały mechanizm podwójnego buforowania. Jeśli ustawisz flagę na wartość TRUE, możesz wyłączyć buforowanie w zależności od pola, korzystając z mechanizmu DFX. Jeśli flaga zostanie ustawiona na FALSE, należy wywołać `SetFieldDirty` i `SetFieldNull` samemu.

Ustaw tego elementu członkowskiego danych przed wywołaniem `Open` . Mechanizm ten jest przeznaczony głównie do łatwego użycia. Wydajność może być wolniejsza ze względu na podwójne buforowanie pól w miarę wprowadzania zmian.

## <a name="cdaorecordsetm_nfields"></a><a name="m_nfields"></a> CDaoRecordset:: m_nFields

Zawiera liczbę elementów członkowskich danych pola w klasie zestawu rekordów oraz liczbę kolumn wybranych przez zestaw rekordów ze źródła danych.

### <a name="remarks"></a>Uwagi

Konstruktor dla klasy zestawu rekordów musi być zainicjowany `m_nFields` z poprawną liczbą pól, które są powiązane statycznie. ClassWizard zapisuje tę inicjalizację w przypadku użycia jej do deklarowania klasy zestawu rekordów. Możesz również napisać je ręcznie.

Struktura używa tej liczby do zarządzania interakcją między elementami członkowskimi danych pola i odpowiednimi kolumnami bieżącego rekordu w źródle danych.

> [!NOTE]
> Ta liczba musi odpowiadać liczbie kolumn wyjściowych zarejestrowanych w trakcie `DoFieldExchange` wywołania `SetFieldType` z parametrem `CDaoFieldExchange::outputColumn` .

Można powiązać kolumny dynamicznie przy użyciu `CDaoRecordset::GetFieldValue` i `CDaoRecordset::SetFieldValue` . Jeśli to zrobisz, nie musisz zwiększać liczby w, `m_nFields` aby odzwierciedlić liczbę wywołań funkcji DFX w `DoFieldExchange` funkcji składowej.

## <a name="cdaorecordsetm_nparams"></a><a name="m_nparams"></a> CDaoRecordset:: m_nParams

Zawiera liczbę elementów członkowskich danych parametrów w klasie zestawu rekordów — liczbę parametrów przesłanych z zapytaniem zestawu rekordów.

### <a name="remarks"></a>Uwagi

Jeśli Klasa zestawu rekordów ma wszystkie elementy członkowskie danych parametrów, Konstruktor dla klasy musi inicjować *m_nParams* o poprawnej liczbie. Wartość *m_nParams* domyślnie równa 0. W przypadku dodawania elementów członkowskich danych parametrów — które należy wykonać ręcznie — należy również ręcznie dodać inicjalizację w konstruktorze klasy, aby odzwierciedlała liczbę parametrów (co musi być co najmniej tak duże jak liczba symboli zastępczych "" w ciągu *m_strFilter* lub *m_strSort* ).

Struktura używa tej liczby podczas parameterizes zapytania zestawu rekordów.

> [!NOTE]
> Ta liczba musi odpowiadać liczbie parametrów "params" zarejestrowanej `DoFieldExchange` po wywołaniu `SetFieldType` z parametrem `CFieldExchange::param` .

Aby uzyskać powiązane informacje, zobacz temat "obiekt parametru" w pomocy DAO.

## <a name="cdaorecordsetm_pdaorecordset"></a><a name="m_pdaorecordset"></a> CDaoRecordset:: m_pDAORecordset

Zawiera wskaźnik do interfejsu OLE dla obiektu zestawu rekordów DAO bazowego `CDaoRecordset` obiektu.

### <a name="remarks"></a>Uwagi

Użyj tego wskaźnika, jeśli musisz bezpośrednio uzyskać dostęp do interfejsu DAO.

Aby uzyskać powiązane informacje, zobacz temat "obiekt Recordset" w pomocy DAO.

## <a name="cdaorecordsetm_pdatabase"></a><a name="m_pdatabase"></a> CDaoRecordset:: m_pDatabase

Zawiera wskaźnik do obiektu, `CDaoDatabase` za pomocą którego zestaw rekordów jest połączony ze źródłem danych.

### <a name="remarks"></a>Uwagi

Ta zmienna jest ustawiana na dwa sposoby. Zwykle przekazuje się wskaźnik do już otwartego `CDaoDatabase` obiektu podczas konstruowania obiektu zestawu rekordów. Jeśli zamiast tego przejdziesz wartość NULL, program `CDaoRecordset` utworzy `CDaoDatabase` obiekt i otworzy go. W obu przypadkach, `CDaoRecordset` zapisuje wskaźnik w tej zmiennej.

Zwykle nie trzeba bezpośrednio używać wskaźnika przechowywanego w `m_pDatabase` . W przypadku pisania własnych rozszerzeń do programu `CDaoRecordset` może być konieczne użycie wskaźnika. Na przykład może być potrzebny wskaźnik, jeśli wygenerujesz własne `CDaoException` elementy.

Aby uzyskać powiązane informacje, zobacz temat "obiekt bazy danych" w pomocy DAO.

## <a name="cdaorecordsetm_strfilter"></a><a name="m_strfilter"></a> CDaoRecordset:: m_strFilter

Zawiera ciąg, który jest używany do konstruowania klauzuli **WHERE** instrukcji języka SQL.

### <a name="remarks"></a>Uwagi

Nie zawiera słowa zastrzeżonego, w **którym** ma zostać przefiltrowany zestaw rekordów. Użycie tego elementu członkowskiego danych nie ma zastosowania do zestawów rekordów typu "Table". Użycie `m_strFilter` nie ma żadnego efektu podczas otwierania zestawu rekordów przy użyciu `CDaoQueryDef` wskaźnika.

Użyj formatu daty w Stanach Zjednoczonych (miesiąc-dzień-rok) w przypadku filtrowania pól zawierających daty, nawet jeśli nie używasz amerykańskiej wersji aparatu bazy danych Microsoft Jet; w przeciwnym razie dane mogą nie być filtrowane zgodnie z oczekiwaniami.

Aby uzyskać powiązane informacje, zobacz temat "właściwości filtru" w pomocy DAO.

## <a name="cdaorecordsetm_strsort"></a><a name="m_strsort"></a> CDaoRecordset:: m_strSort

Zawiera ciąg zawierający klauzulę **ORDERBY** instrukcji SQL bez zarezerwowanych wyrazów **OrderBy**.

### <a name="remarks"></a>Uwagi

Można sortować według obiektów zestawu rekordów typu "dynamiczny" i "snapshot".

Nie można sortować obiektów zestawu rekordów typu tabela. Aby określić kolejność sortowania zestawu rekordów typu tabela, wywołaj [SetCurrentIndex](#setcurrentindex).

Użycie *m_strSort* nie ma wpływu na otwieranie zestawu rekordów przy użyciu `CDaoQueryDef` wskaźnika.

Aby uzyskać powiązane informacje, zobacz temat "Sortuj Właściwość" w pomocy DAO.

## <a name="cdaorecordsetmove"></a><a name="move"></a> CDaoRecordset:: Move

Wywołaj tę funkcję elementu członkowskiego, aby umieścić rekordy *lRows* rekordów z bieżącego rekordu.

```cpp
virtual void Move(long lRows);
```

### <a name="parameters"></a>Parametry

*lRows*<br/>
Liczba rekordów do przeniesienia do przodu lub do tyłu. Wartości dodatnie przesuwają się w przód, w kierunku końca zestawu rekordów. Wartości ujemne przesuwają się do tyłu, w kierunku początku.

### <a name="remarks"></a>Uwagi

Możesz przejść do przodu lub do tyłu. `Move( 1 )` jest odpowiednikiem `MoveNext` i `Move( -1 )` jest równoważne `MovePrev` .

> [!CAUTION]
> Wywołanie którejkolwiek z `Move` funkcji zgłasza wyjątek, jeśli zestaw rekordów nie zawiera żadnych rekordów. Ogólnie rzecz biorąc, wywołaj zarówno, `IsBOF` jak i `IsEOF` przed operacją przenoszenia, aby określić, czy zestaw rekordów zawiera jakieś rekordy. Po wywołaniu `Open` lub `Requery` wywołaniu metody `IsBOF` lub `IsEOF` .

> [!NOTE]
> Jeśli przewiniesz poza początkową lub końcem zestawu rekordów ( `IsBOF` lub `IsEOF` zwraca wartość różną od zera), wywołanie w celu wyrzucania `Move` `CDaoException` .

> [!NOTE]
> Jeśli `Move` podczas aktualizowania lub dodawania bieżącego rekordu zostanie wywołana jakakolwiek funkcja, aktualizacje zostaną utracone bez ostrzeżenia.

Gdy wywołujesz `Move` migawkę przewijaną tylko do przodu, parametr *lRows* musi być dodatnią liczbą całkowitą, a zakładki są niedozwolone, więc można przenieść tylko do przodu.

Aby utworzyć pierwszy, ostatni, następny lub poprzedni rekord w zestawie rekordów dla bieżącego rekordu, wywołaj `MoveFirst` `MoveLast` funkcję,, `MoveNext` , lub `MovePrev` funkcji członkowskiej.

Aby uzyskać powiązane informacje, zobacz temat "Metoda Move" i "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" w pomocy DAO.

## <a name="cdaorecordsetmovefirst"></a><a name="movefirst"></a> CDaoRecordset:: MoveFirst

Wywołaj tę funkcję elementu członkowskiego, aby utworzyć pierwszy rekord w zestawie rekordów (jeśli istnieje) bieżącego rekordu.

```cpp
void MoveFirst();
```

### <a name="remarks"></a>Uwagi

Nie ma potrzeby wywoływania `MoveFirst` natychmiast po otwarciu zestawu rekordów. W tym momencie pierwszy rekord (jeśli istnieje) jest automatycznie bieżącym rekordem.

> [!CAUTION]
> Wywołanie którejkolwiek z `Move` funkcji zgłasza wyjątek, jeśli zestaw rekordów nie zawiera żadnych rekordów. Ogólnie rzecz biorąc, wywołaj zarówno, `IsBOF` jak i `IsEOF` przed operacją przenoszenia, aby określić, czy zestaw rekordów zawiera jakieś rekordy. Po wywołaniu `Open` lub `Requery` wywołaniu metody `IsBOF` lub `IsEOF` .

> [!NOTE]
> Jeśli `Move` podczas aktualizowania lub dodawania bieżącego rekordu zostanie wywołana jakakolwiek funkcja, aktualizacje zostaną utracone bez ostrzeżenia.

Użyj `Move` funkcji, aby przejść z rekordu do rekordu bez zastosowania warunku. Użyj operacji znajdowania w celu zlokalizowania rekordów w obiekcie zestawu rekordów typu dynamiczny lub typu migawka, który spełnia określony warunek. Aby zlokalizować rekord w obiekcie zestawu rekordów typu tabela, wywołaj `Seek` .

Jeśli zestaw rekordów odwołuje się do zestawu rekordów typu tabeli, przemieszczenie następuje po bieżącym indeksie tabeli. Bieżący indeks można ustawić przy użyciu właściwości index bazowego obiektu DAO. Jeśli bieżący indeks nie zostanie ustawiony, kolejność zwróconych rekordów jest niezdefiniowana.

Jeśli wywołasz `MoveLast` obiekt zestawu rekordów na podstawie zapytania SQL lub querydef, zapytanie jest wymuszane do ukończenia, a obiekt zestawu rekordów jest w pełni wypełniony.

Nie można wywołać `MoveFirst` `MovePrev` funkcji składowej ani z migawką przewijaną tylko do przodu.

Aby przenieść położenie bieżącego rekordu w obiekcie zestawu rekordów, należy wywołać określoną liczbę rekordów do przodu lub do tyłu `Move` .

Aby uzyskać powiązane informacje, zobacz temat "Metoda Move" i "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" w pomocy DAO.

## <a name="cdaorecordsetmovelast"></a><a name="movelast"></a> CDaoRecordset:: MoveLast

Wywołaj tę funkcję elementu członkowskiego, aby utworzyć ostatni rekord (jeśli istnieje) w zestawie rekordów dla bieżącego rekordu.

```cpp
void MoveLast();
```

### <a name="remarks"></a>Uwagi

> [!CAUTION]
> Wywołanie którejkolwiek z `Move` funkcji zgłasza wyjątek, jeśli zestaw rekordów nie zawiera żadnych rekordów. Ogólnie rzecz biorąc, wywołaj zarówno, `IsBOF` jak i `IsEOF` przed operacją przenoszenia, aby określić, czy zestaw rekordów zawiera jakieś rekordy. Po wywołaniu `Open` lub `Requery` wywołaniu metody `IsBOF` lub `IsEOF` .

> [!NOTE]
> Jeśli `Move` podczas aktualizowania lub dodawania bieżącego rekordu zostanie wywołana jakakolwiek funkcja, aktualizacje zostaną utracone bez ostrzeżenia.

Użyj `Move` funkcji, aby przejść z rekordu do rekordu bez zastosowania warunku. Użyj operacji znajdowania w celu zlokalizowania rekordów w obiekcie zestawu rekordów typu dynamiczny lub typu migawka, który spełnia określony warunek. Aby zlokalizować rekord w obiekcie zestawu rekordów typu tabela, wywołaj `Seek` .

Jeśli zestaw rekordów odwołuje się do zestawu rekordów typu tabeli, przemieszczenie następuje po bieżącym indeksie tabeli. Bieżący indeks można ustawić przy użyciu właściwości index bazowego obiektu DAO. Jeśli bieżący indeks nie zostanie ustawiony, kolejność zwróconych rekordów jest niezdefiniowana.

Jeśli wywołasz `MoveLast` obiekt zestawu rekordów na podstawie zapytania SQL lub querydef, zapytanie jest wymuszane do ukończenia, a obiekt zestawu rekordów jest w pełni wypełniony.

Aby przenieść położenie bieżącego rekordu w obiekcie zestawu rekordów, należy wywołać określoną liczbę rekordów do przodu lub do tyłu `Move` .

Aby uzyskać powiązane informacje, zobacz temat "Metoda Move" i "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" w pomocy DAO.

## <a name="cdaorecordsetmovenext"></a><a name="movenext"></a> CDaoRecordset:: MoveNext

Wywołaj tę funkcję elementu członkowskiego, aby utworzyć następny rekord w zestawie rekordów w bieżącym rekordzie.

```cpp
void MoveNext();
```

### <a name="remarks"></a>Uwagi

Zaleca się wywołanie `IsBOF` przed podjęciem próby przejścia do poprzedniego rekordu. Wywołanie funkcji zwróci `MovePrev` `CDaoException` `IsBOF` wynik, jeśli zwraca wartość różną od zera, co oznacza, że użytkownik został już przewinięty przed pierwszym rekordem lub że żaden rekord nie został wybrany przez zestaw rekordów.

> [!CAUTION]
> Wywołanie którejkolwiek z `Move` funkcji zgłasza wyjątek, jeśli zestaw rekordów nie zawiera żadnych rekordów. Ogólnie rzecz biorąc, wywołaj zarówno, `IsBOF` jak i `IsEOF` przed operacją przenoszenia, aby określić, czy zestaw rekordów zawiera jakieś rekordy. Po wywołaniu `Open` lub `Requery` wywołaniu metody `IsBOF` lub `IsEOF` .

> [!NOTE]
> Jeśli `Move` podczas aktualizowania lub dodawania bieżącego rekordu zostanie wywołana jakakolwiek funkcja, aktualizacje zostaną utracone bez ostrzeżenia.

Użyj `Move` funkcji, aby przejść z rekordu do rekordu bez zastosowania warunku. Użyj operacji znajdowania w celu zlokalizowania rekordów w obiekcie zestawu rekordów typu dynamiczny lub typu migawka, który spełnia określony warunek. Aby zlokalizować rekord w obiekcie zestawu rekordów typu tabela, wywołaj `Seek` .

Jeśli zestaw rekordów odwołuje się do zestawu rekordów typu tabeli, przemieszczenie następuje po bieżącym indeksie tabeli. Bieżący indeks można ustawić przy użyciu właściwości index bazowego obiektu DAO. Jeśli bieżący indeks nie zostanie ustawiony, kolejność zwróconych rekordów jest niezdefiniowana.

Aby przenieść położenie bieżącego rekordu w obiekcie zestawu rekordów, należy wywołać określoną liczbę rekordów do przodu lub do tyłu `Move` .

Aby uzyskać powiązane informacje, zobacz temat "Metoda Move" i "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" w pomocy DAO.

## <a name="cdaorecordsetmoveprev"></a><a name="moveprev"></a> CDaoRecordset:: MovePrev

Wywołaj tę funkcję elementu członkowskiego, aby utworzyć poprzedni rekord w zestawie rekordów w bieżącym rekordzie.

```cpp
void MovePrev();
```

### <a name="remarks"></a>Uwagi

Zaleca się wywołanie `IsBOF` przed podjęciem próby przejścia do poprzedniego rekordu. Wywołanie funkcji zwróci `MovePrev` `CDaoException` `IsBOF` wynik, jeśli zwraca wartość różną od zera, co oznacza, że użytkownik został już przewinięty przed pierwszym rekordem lub że żaden rekord nie został wybrany przez zestaw rekordów.

> [!CAUTION]
> Wywołanie którejkolwiek z `Move` funkcji zgłasza wyjątek, jeśli zestaw rekordów nie zawiera żadnych rekordów. Ogólnie rzecz biorąc, wywołaj zarówno, `IsBOF` jak i `IsEOF` przed operacją przenoszenia, aby określić, czy zestaw rekordów zawiera jakieś rekordy. Po wywołaniu `Open` lub `Requery` wywołaniu metody `IsBOF` lub `IsEOF` .

> [!NOTE]
> Jeśli `Move` podczas aktualizowania lub dodawania bieżącego rekordu zostanie wywołana jakakolwiek funkcja, aktualizacje zostaną utracone bez ostrzeżenia.

Użyj `Move` funkcji, aby przejść z rekordu do rekordu bez zastosowania warunku. Użyj operacji znajdowania w celu zlokalizowania rekordów w obiekcie zestawu rekordów typu dynamiczny lub typu migawka, który spełnia określony warunek. Aby zlokalizować rekord w obiekcie zestawu rekordów typu tabela, wywołaj `Seek` .

Jeśli zestaw rekordów odwołuje się do zestawu rekordów typu tabeli, przemieszczenie następuje po bieżącym indeksie tabeli. Bieżący indeks można ustawić przy użyciu właściwości index bazowego obiektu DAO. Jeśli bieżący indeks nie zostanie ustawiony, kolejność zwróconych rekordów jest niezdefiniowana.

Nie można wywołać `MoveFirst` `MovePrev` funkcji składowej ani z migawką przewijaną tylko do przodu.

Aby przenieść położenie bieżącego rekordu w obiekcie zestawu rekordów, należy wywołać określoną liczbę rekordów do przodu lub do tyłu `Move` .

Aby uzyskać powiązane informacje, zobacz temat "Metoda Move" i "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" w pomocy DAO.

## <a name="cdaorecordsetopen"></a><a name="open"></a> CDaoRecordset:: Open

Musisz wywołać tę funkcję elementu członkowskiego, aby pobrać rekordy dla zestawu rekordów.

```cpp
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
Jedna z następujących wartości:

- `dbOpenDynaset` Zestaw rekordów typu dynamicznego z przewijaniem dwukierunkowym. Jest to opcja domyślna.

- `dbOpenTable` Zestaw rekordów typu tabela z dwukierunkowym przewijaniem.

- `dbOpenSnapshot` Zestaw rekordów typu migawka z dwukierunkowym przewijaniem.

*lpszSQL*<br/>
Wskaźnik ciągu zawierający jedną z następujących wartości:

- Wskaźnik o wartości NULL.

- Nazwa co najmniej jednego elementu tabledefs i/lub querydef (rozdzielonych przecinkami).

- Instrukcja **SELECT** języka SQL (opcjonalnie z klauzulą **WHERE** lub **ORDERBY** ).

- Kwerenda przekazująca.

*nOptions*<br/>
Co najmniej jedna z opcji wymienionych poniżej. Wartość domyślna to 0. Dopuszczalne są następujące wartości:

- `dbAppendOnly` Można dołączać tylko nowe rekordy (tylko zestaw rekordów typu dynamicznego). Ta opcja oznacza, że można dołączać tylko rekordy. Klasy baz danych MFC ODBC mają opcję tylko do dołączania, która umożliwia pobieranie i dołączanie rekordów.

- `dbForwardOnly` Zestaw rekordów jest migawką przewijaną tylko do przodu.

- `dbSeeChanges` Generuj wyjątek, jeśli inny użytkownik zmienia edytowane dane.

- `dbDenyWrite` Inni użytkownicy nie mogą modyfikować ani dodawać rekordów.

- `dbDenyRead` Inni użytkownicy nie mogą wyświetlać rekordów (tylko zestaw rekordów typu "Tabela").

- `dbReadOnly` Można tylko wyświetlać rekordy; inni użytkownicy mogą je modyfikować.

- `dbInconsistent` Niespójne aktualizacje są dozwolone (tylko zestaw rekordów typu dynamicznego).

- `dbConsistent` Dozwolone są tylko spójne aktualizacje (tylko zestaw rekordów typu dynamicznego).

> [!NOTE]
> Stałe `dbConsistent` i `dbInconsistent` wykluczają się wzajemnie. Można użyć jednego lub drugiego, ale nie obu w danym wystąpieniu `Open` .

*pTableDef*<br/>
Wskaźnik do obiektu [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) . Ta wersja jest prawidłowa tylko dla zestawów rekordów typu "Table". W przypadku korzystania z tej opcji `CDaoDatabase` wskaźnik używany do konstruowania `CDaoRecordset` nie jest używany; zamiast tego baza danych, w której znajduje się tabledef.

*pQueryDef*<br/>
Wskaźnik do obiektu [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) . Ta wersja jest prawidłowa tylko dla zestawów rekordów typu "dynamiczny" i "snapshot-Type". W przypadku korzystania z tej opcji `CDaoDatabase` wskaźnik używany do konstruowania `CDaoRecordset` nie jest używany; zamiast tego baza danych, w której znajduje się program querydef, jest używana.

### <a name="remarks"></a>Uwagi

Przed wywołaniem `Open` należy skonstruować obiekt zestawu rekordów. Można to zrobić na kilka sposobów:

- Podczas konstruowania obiektu zestawu rekordów należy przekazać wskaźnik do `CDaoDatabase` obiektu, który jest już otwarty.

- Podczas konstruowania obiektu zestawu rekordów należy przekazać wskaźnik do `CDaoDatabase` obiektu, który nie jest otwarty. Zestaw rekordów otwiera `CDaoDatabase` obiekt, ale nie zamknie go, gdy obiekt Recordset zostanie zamknięty.

- Podczas konstruowania obiektu zestawu rekordów należy przekazać wskaźnik o wartości NULL. Obiekt recordset wywołuje, `GetDefaultDBName` Aby uzyskać nazwę dostępu do firmy Microsoft. Plik MDB do otwarcia. Zestaw rekordów otwiera następnie `CDaoDatabase` obiekt i pozostaje otwarty, dopóki zestaw rekordów jest otwarty. Gdy wywołujesz `Close` zestaw rekordów, `CDaoDatabase` obiekt jest również zamknięty.

    > [!NOTE]
    >  Gdy zestaw rekordów otwiera `CDaoDatabase` obiekt, otwiera źródło danych z niewyłącznym dostępem.

W przypadku wersji programu `Open` , która używa *lpszSQL* parametru, po otwarciu zestawu rekordów można pobrać rekordy na kilka sposobów. Pierwsza opcja ma mieć funkcje DFX w `DoFieldExchange` . Drugą opcją jest użycie powiązania dynamicznego przez wywołanie `GetFieldValue` funkcji składowej. Te opcje można zaimplementować osobno lub w połączeniu z nimi. Jeśli są połączone, należy przekazać instrukcję SQL samodzielnie do wywołania `Open` .

W przypadku korzystania z drugiej wersji `Open` miejsca, w którym przekazujesz `CDaoTableDef` obiekt, uzyskane kolumny będą dostępne do powiązania przez `DoFieldExchange` mechanizm DFX i/lub powiązać się dynamicznie za pośrednictwem `GetFieldValue` .

> [!NOTE]
> Można wywołać tylko `Open` przy użyciu `CDaoTableDef` obiektu dla zestawów rekordów typu "Table".

W przypadku korzystania z trzeciej wersji `Open` miejsca, w którym przekazuje się `CDaoQueryDef` obiekt, zapytanie zostanie wykonane, a uzyskane kolumny będą dostępne do powiązania przez `DoFieldExchange` mechanizm DFX i/lub powiązać dynamicznie za pośrednictwem `GetFieldValue` .

> [!NOTE]
> Można wywołać tylko `Open` za pomocą `CDaoQueryDef` obiektu dla zestawów rekordów typu dynamiczny i typu Snapshot.

W przypadku pierwszej wersji programu `Open` , która używa `lpszSQL` parametru, rekordy są wybierane na podstawie kryteriów przedstawionych w poniższej tabeli.

|Wartość `lpszSQL` parametru|Wybrane rekordy są określane przez|Przykład|
|--------------------------------------|----------------------------------------|-------------|
|NULL|Ciąg zwracany przez `GetDefaultSQL` .||
|Rozdzielana przecinkami lista nazw tabledefs i/lub querydef.|Wszystkie kolumny reprezentowane w `DoFieldExchange` .|`"Customer"`|
|**Wybierz** kolumnę-list **z** listy tabel|Określone kolumny z określonych tabledef i/lub querydef (s).|`"SELECT CustId, CustName`<br /><br /> `FROM Customer"`|

Typową procedurą jest przekazanie wartości NULL do `Open` ; w takim przypadku `Open` wywołania `GetDefaultSQL` , funkcja członkowskej składowej, która ClassWizard generuje podczas tworzenia `CDaoRecordset` klasy pochodnej. Ta wartość daje nazwy tabledef i/lub querydef określone w ClassWizard. Zamiast tego można określić inne informacje w parametrze *lpszSQL* .

Niezależnie od tego, co zostało przekazane, `Open` konstruuje końcowy ciąg SQL dla zapytania (ciąg może zawierać klauzule **WHERE** i **ORDERBY** , które są dołączone do przekazanego ciągu *lpszSQL* ), a następnie wykonuje zapytanie. Skonstruowany ciąg można odczytać przez wywołanie `GetSQL` po wywołaniu `Open` .

Elementy członkowskie danych pól klasy zestaw rekordów są powiązane z kolumnami wybranych danych. Jeśli wszystkie rekordy są zwracane, pierwszy rekord zostanie bieżącym rekordem.

Jeśli chcesz ustawić opcje dla zestawu rekordów, takie jak filtr lub sortowanie, ustaw `m_strSort` lub `m_strFilter` po utworzeniu obiektu zestawu rekordów, ale przed wywołaniem `Open` . Jeśli chcesz odświeżyć rekordy w zestawie rekordów po tym, jak zestaw rekordów jest już otwarty, wywołaj `Requery` .

W przypadku wywołania `Open` zestawu rekordów typu zestaw dynamiczny lub typu migawka lub jeśli źródło danych odwołuje się do instrukcji SQL lub tabledef, która reprezentuje załączoną tabelę, nie można użyć `dbOpenTable` dla argumentu typu. Jeśli to zrobisz, MFC zgłasza wyjątek. Aby określić, czy obiekt tabledef reprezentuje dołączoną tabelę, Utwórz obiekt [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) i Wywołaj jego funkcję członkowską [GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect) .

Użyj `dbSeeChanges` flagi, jeśli chcesz zapułapać zmiany wprowadzone przez innego użytkownika lub inny program na komputerze podczas edytowania lub usuwania tego samego rekordu. Na przykład jeśli dwóch użytkowników rozpocznie edytowanie tego samego rekordu, pierwszy użytkownik, który wywoła `Update` funkcję członkowską, powiodło się. Gdy `Update` jest wywoływana przez drugiego użytkownika, `CDaoException` jest zgłaszany. Analogicznie, jeśli drugi użytkownik próbuje wywołać `Delete` usunięcie rekordu i został już zmieniony przez pierwszego użytkownika, `CDaoException` wystąpił.

Typowo, jeśli użytkownik jest w `CDaoException` trakcie aktualizowania, kod powinien odświeżyć zawartość pól i pobrać nowo zmodyfikowane wartości. Jeśli wystąpi wyjątek w procesie usuwania, kod może wyświetlić nowego rekordu danych dla użytkownika i komunikat informujący o tym, że dane zostały ostatnio zmienione. W tym momencie kod może zażądać potwierdzenia, że użytkownik nadal chce usunąć rekord.

> [!TIP]
> Użyj opcji przewijania tylko do przodu ( `dbForwardOnly` ), aby zwiększyć wydajność, gdy aplikacja wykonuje pojedynczy przebieg przez zestaw rekordów otwarty ze źródła danych ODBC.

Aby uzyskać powiązane informacje, zobacz temat "Metoda OpenRecordset" w pomocy DAO.

## <a name="cdaorecordsetrequery"></a><a name="requery"></a> CDaoRecordset:: Requery

Wywołaj tę funkcję elementu członkowskiego, aby skompilować ponownie (Odśwież) zestaw rekordów.

```cpp
virtual void Requery();
```

### <a name="remarks"></a>Uwagi

Jeśli wszystkie rekordy są zwracane, pierwszy rekord zostanie bieżącym rekordem.

Aby zestaw rekordów odzwierciedlał operacje dodawania i usuwania, które są używane przez użytkownika lub innych użytkowników do źródła danych, należy ponownie skompilować zestaw rekordów, wywołując metodę `Requery` . Jeśli zestaw rekordów jest dynamiczny, automatycznie odzwierciedla aktualizacje, które zostały wprowadzone przez użytkownika lub innych użytkowników do istniejących rekordów (ale nie do dodania). Jeśli zestaw rekordów jest migawką, należy wywołać, `Requery` aby odzwierciedlić zmiany wprowadzone przez innych użytkowników, a także Dodatki i usunięcia.

W przypadku zestawu dynamicznego lub migawki należy wywołać `Requery` dowolną godzinę, aby ponownie skompilować zestaw rekordów przy użyciu wartości parametrów. Ustaw nowy filtr lub Sortuj według ustawienia [m_strFilter](#m_strfilter) i [m_strSort](#m_strsort) przed wywołaniem `Requery` . Ustaw nowe parametry, przypisując nowe wartości do elementów członkowskich danych przed wywołaniem `Requery` .

Jeśli próba odbudowy zestawu rekordów nie powiedzie się, zestaw rekordów zostanie zamknięty. Przed wywołaniem można `Requery` określić, czy można ponownie zbadać zestaw rekordów, wywołując funkcję członkowską [restart](#canrestart) . `CanRestart` nie gwarantuje, że powiedzie `Requery` się.

> [!CAUTION]
> Wywołanie `Requery` tylko po wywołaniu `Open` .

> [!NOTE]
> Wywołanie zmian [kwerendy](#requery) dla zakładki DAO.

Nie można wywołać `Requery` w zestawie rekordów typu dynamicznego lub typu migawek, jeśli wywołanie `CanRestart` zwraca wartość 0, ani nie można używać go w zestawie rekordów typu tabela.

Jeśli obie `IsBOF` i `IsEOF` zwracają wartość różną od zera po wywołaniu `Requery` , kwerenda nie zwróciła żadnych rekordów i zestaw rekordów nie będzie zawierał żadnych danych.

Aby uzyskać powiązane informacje, zobacz temat "Metoda PonówKwerendę" w pomocy DAO.

## <a name="cdaorecordsetseek"></a><a name="seek"></a> CDaoRecordset:: Seek

Wywołaj tę funkcję elementu członkowskiego, aby zlokalizować rekord w indeksowanym obiekcie zestawu rekordów typu tabela, który spełnia określone kryteria dla bieżącego indeksu, i ustaw ten rekord w bieżącym rekordzie.

```cpp
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
Jedno z następujących wyrażeń ciągów: "<", " \<=", "=", "> =" lub ">".

*pKey1*<br/>
Wskaźnik do elementu [COleVariant](../../mfc/reference/colevariant-class.md) , którego wartość odnosi się do pierwszego pola w indeksie. Wymagany.

*pKey2*<br/>
Wskaźnik do `COleVariant` którego wartość odnosi się do drugiego pola w indeksie, jeśli istnieje. Wartością domyślną jest NULL.

*pKey3*<br/>
Wskaźnik do `COleVariant` którego wartość odnosi się do trzeciego pola w indeksie (jeśli istnieje). Wartością domyślną jest NULL.

*pKeyArray*<br/>
Wskaźnik do tablicy wariantów. Rozmiar tablicy odpowiada liczbie pól w indeksie.

*nKeys*<br/>
Liczba całkowita odpowiadająca rozmiarowi tablicy, czyli liczbie pól w indeksie.

> [!NOTE]
> W kluczach nie należy określać symboli wieloznacznych. Symbole wieloznaczne spowodują `Seek` zwrócenie braku pasujących rekordów.

### <a name="return-value"></a>Wartość zwracana

Nierówna zero, jeśli znaleziono pasujące rekordy, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj drugiej (tablicy) wersji programu, `Seek` Aby obsłużyć indeksy czterech pól lub więcej.

`Seek` umożliwia wyszukiwanie indeksów o wysokiej wydajności w zestawach rekordów typu tabela. Należy ustawić bieżący indeks, wywołując `SetCurrentIndex` przed wywołaniem metody `Seek` . Jeśli indeks identyfikuje pole lub pola klucza nieunikatowego, `Seek` lokalizuje pierwszy rekord, który spełnia kryteria. Jeśli indeks nie zostanie ustawiony, zostanie zgłoszony wyjątek.

Należy pamiętać, że jeśli nie tworzysz zestawu rekordów UNICODE, `COleVariant` obiekty muszą być jawnie zadeklarowane jako ANSI. Można to zrobić za pomocą formy [COleVariant:: COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** konstruktora z *vtSrc* set to `VT_BSTRT` (ANSI) lub przy użyciu `COleVariant` funkcji [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** z *vtSrc* ustawioną na `VT_BSTRT` .

Po wywołaniu należy `Seek` przekazać co najmniej jedną wartość klucza i operator porównania ("<", " \<=", "=", "> =" lub ">"). `Seek` przeszukuje określone pola klucza i lokalizuje pierwszy rekord, który spełnia kryteria określone przez *lpszComparison* i *pKey1*. Po znalezieniu `Seek` zwraca wartość różną od zera i ustawia ten rekord jako bieżący. Jeśli `Seek` nie można znaleźć dopasowania, `Seek` zwraca zero, a bieżący rekord jest niezdefiniowany. W przypadku bezpośredniego używania DAO należy jawnie sprawdzić Właściwość nomatch.

Jeśli `lpszComparison` jest "=", ">=" lub ">", `Seek` rozpoczyna się na początku indeksu. Jeśli *lpszComparison* jest "<" lub "<=", `Seek` rozpocznie się na końcu indeksu i przeszukuje wstecz, chyba że na końcu znajdują się zduplikowane wpisy indeksu. W tym przypadku `Seek` zaczyna się od dowolnego wpisu między zduplikowanymi pozycjami indeksu na końcu indeksu.

W przypadku korzystania z programu nie trzeba być bieżącym rekordem `Seek` .

Aby zlokalizować rekord w zestawie typu dynamicznego lub typu migawek, który spełnia określony warunek, użyj operacji wyszukiwania. Aby uwzględnić wszystkie rekordy, a nie tylko te, które spełniają określony warunek, użyj operacji przenoszenia do przenoszenia z rekordu do rekordu.

Nie można wywołać `Seek` dla dołączonej tabeli dowolnego typu, ponieważ dołączone tabele muszą być otwarte jako zestawy rekordów typu dynamicznego lub typu migawek. Jednak w przypadku wywołania `CDaoDatabase::Open` bezpośredniego otwarcia instalowalnej bazy danych ISAM można wywoływać `Seek` tabele w tej bazie danych, chociaż wydajność może być niska.

Aby uzyskać powiązane informacje, zobacz temat "Metoda wyszukiwania" w pomocy DAO.

## <a name="cdaorecordsetsetabsoluteposition"></a><a name="setabsoluteposition"></a> CDaoRecordset:: SetAbsolutePosition

Ustawia względny numer rekordu dla bieżącego rekordu obiektu zestawu rekordów.

```cpp
void SetAbsolutePosition(long lPosition);
```

### <a name="parameters"></a>Parametry

*lPosition*<br/>
Odnosi się do pozycji porządkowej bieżącego rekordu w zestawie rekordów.

### <a name="remarks"></a>Uwagi

Wywołanie `SetAbsolutePosition` umożliwia umieszczenie bieżącego wskaźnika rekordu do określonego rekordu w oparciu o jego pozycję porządkową w zestawie rekordów typu dynamicznego lub typu migawki. Możesz również określić bieżący numer rekordu, wywołując [GetAbsolutePosition](#getabsoluteposition).

> [!NOTE]
> Ta funkcja członkowska jest prawidłowa tylko dla zestawów rekordów typu dynamiczny i typu migawka.

Wartość właściwości AbsolutePosition bazowego obiektu DAO jest zależna od zera. ustawienie wartości 0 oznacza pierwszy rekord w zestawie rekordów. Ustawienie wartości większej niż liczba wypełnionych rekordów powoduje zgłoszenie wyjątku przez MFC. Możesz określić liczbę wypełnionych rekordów w zestawie rekordów, wywołując `GetRecordCount` funkcję członkowską.

Jeśli bieżący rekord zostanie usunięty, wartość właściwości AbsolutePosition nie jest zdefiniowana, a MFC zgłasza wyjątek, jeśli istnieje odwołanie. Nowe rekordy są dodawane na końcu sekwencji.

> [!NOTE]
> Ta właściwość nie jest przeznaczona do użycia jako numer rekordu zastępczego. Zakładki są nadal zalecanym sposobem zachowywania i powrotu do danego położenia i są jedynym sposobem pozycjonowania bieżącego rekordu dla wszystkich typów obiektów zestawu rekordów, które obsługują zakładki. W szczególności pozycja danego rekordu zmienia się, gdy rekordy, które poprzedzają, są usuwane. Nie ma również gwarancji, że dany rekord będzie miał tę samą bezwzględną pozycję, jeśli zestaw rekordów zostanie ponownie utworzony, ponieważ kolejność poszczególnych rekordów w zestawie rekordów nie jest gwarantowana, chyba że zostanie utworzona za pomocą instrukcji SQL przy użyciu klauzuli **ORDERBY** .

Aby uzyskać powiązane informacje, zobacz temat "Właściwość AbsolutePosition" w pomocy DAO.

## <a name="cdaorecordsetsetbookmark"></a><a name="setbookmark"></a> CDaoRecordset:: SetBookmark

Wywołaj tę funkcję elementu członkowskiego, aby umieścić zestaw rekordów w rekordzie zawierającym określoną zakładkę.

```cpp
void SetBookmark(COleVariant varBookmark);
```

### <a name="parameters"></a>Parametry

*varBookmark*<br/>
Obiekt [COleVariant](../../mfc/reference/colevariant-class.md) zawierający wartość zakładki dla określonego rekordu.

### <a name="remarks"></a>Uwagi

Gdy obiekt zestawu rekordów zostanie utworzony lub otwarty, każdy z jego rekordów ma już unikatową zakładkę. Możesz pobrać zakładkę dla bieżącego rekordu przez wywołanie `GetBookmark` i zapisanie wartości do `COleVariant` obiektu. Później możesz powrócić do tego rekordu, wywołując `SetBookmark` przy użyciu wartości zapisanej zakładki.

> [!NOTE]
> Wywołanie zmian [kwerendy](#requery) dla zakładki DAO.

Należy pamiętać, że jeśli nie tworzysz zestawu rekordów UNICODE, `COleVariant` obiekt musi być jawnie zadeklarowany jako ANSI. Można to zrobić za pomocą formy [COleVariant:: COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** konstruktora z *vtSrc* set to `VT_BSTRT` (ANSI) lub przy użyciu `COleVariant` funkcji [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** z *vtSrc* ustawioną na `VT_BSTRT` .

Aby uzyskać powiązane informacje, zobacz temat "właściwość zakładki" i właściwość z zakładkami "w pomocy DAO.

## <a name="cdaorecordsetsetcachesize"></a><a name="setcachesize"></a> CDaoRecordset:: SetCacheSize

Wywołaj tę funkcję elementu członkowskiego, aby ustawić liczbę rekordów, które mają być buforowane.

```cpp
void SetCacheSize(long lSize);
```

### <a name="parameters"></a>Parametry

*lSize*<br/>
Określa liczbę rekordów. Typową wartością jest 100. Ustawienie wartości 0 powoduje wyłączenie buforowania. Ustawienie musi zawierać się w przedziale od 5 do 1200 rekordów. Pamięć podręczna może wykorzystywać znaczną ilość pamięci.

### <a name="remarks"></a>Uwagi

Pamięć podręczna to miejsce w pamięci lokalnej, w którym znajdują się dane ostatnio pobierane z serwera w przypadku, gdy aplikacja będzie ponownie żądała danych. Buforowanie danych zwiększa wydajność aplikacji, która pobiera dane z serwera zdalnego za pośrednictwem obiektów zestawu rekordów typu dynamicznego. Gdy dane są żądane, aparat bazy danych Microsoft Jet najpierw sprawdza pamięć podręczną pod kątem żądanych danych zamiast pobierać je z serwera, co zajmuje więcej czasu. Dane, które nie pochodzą ze źródła danych ODBC, nie są zapisywane w pamięci podręcznej.

Każde źródło danych ODBC, takie jak dołączona tabela, może mieć lokalną pamięć podręczną. Aby utworzyć pamięć podręczną, Otwórz obiekt zestawu rekordów ze zdalnego źródła danych, wywołaj `SetCacheSize` `SetCacheStart` funkcje i składowe, a następnie Wywołaj `FillCache` funkcję członkowską lub przechodzenie przez rekordy przy użyciu jednej z operacji przenoszenia. Parametr *lSize* `SetCacheSize` funkcji składowej może opierać się na liczbie rekordów, z którymi aplikacja może jednocześnie współdziałać. Na przykład jeśli używasz zestawu rekordów jako źródła danych, które mają być wyświetlane na ekranie, możesz przekazać `SetCacheSize` parametr *lSize* jako 20, aby wyświetlić 20 rekordów jednocześnie.

Aby uzyskać powiązane informacje, zobacz temat "CacheSize, CacheStart Properties" w pomocy DAO.

## <a name="cdaorecordsetsetcachestart"></a><a name="setcachestart"></a> CDaoRecordset:: SetCacheStart

Wywołaj tę funkcję elementu członkowskiego, aby określić zakładkę pierwszego rekordu w zestawie rekordów, który ma zostać zbuforowany.

```cpp
void SetCacheStart(COleVariant varBookmark);
```

### <a name="parameters"></a>Parametry

*varBookmark*<br/>
Element [COleVariant](../../mfc/reference/colevariant-class.md) , który określa zakładkę pierwszego rekordu w zestawie rekordów, który ma zostać zbuforowany.

### <a name="remarks"></a>Uwagi

Można użyć wartości zakładki dowolnego rekordu dla parametru *varBookmark* `SetCacheStart` funkcji członkowskiej. Utwórz rekord, dla którego chcesz uruchomić pamięć podręczną z bieżącym rekordem, Ustanów zakładkę dla tego rekordu przy użyciu elementu [SetBookmark](#setbookmark)i przekaż wartość zakładki jako parametr dla `SetCacheStart` funkcji członkowskiej.

Aparat bazy danych Microsoft Jet żąda rekordów w zakresie pamięci podręcznej z pamięci podręcznej i żąda rekordów poza zakresem pamięci podręcznej z serwera.

Rekordy pobrane z pamięci podręcznej nie odzwierciedlają zmian wprowadzonych jednocześnie do danych źródłowych przez innych użytkowników.

Aby wymusić aktualizację wszystkich danych w pamięci podręcznej, Przekaż parametr *lSize* `SetCacheSize` jako 0, wywołaj `SetCacheSize` ponownie, podając rozmiar pamięci podręcznej, której pierwotnie żądano, a następnie Wywołaj `FillCache` funkcję członkowską.

Należy pamiętać, że jeśli nie tworzysz zestawu rekordów UNICODE, `COleVariant` obiekt musi być jawnie zadeklarowany jako ANSI. Można to zrobić za pomocą formy [COleVariant:: COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** konstruktora z *vtSrc* set to `VT_BSTRT` (ANSI) lub przy użyciu `COleVariant` funkcji [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** z *vtSrc* ustawioną na `VT_BSTRT` .

Aby uzyskać powiązane informacje, zobacz temat CacheSize CacheStart Properties (właściwości) w pomocy DAO.

## <a name="cdaorecordsetsetcurrentindex"></a><a name="setcurrentindex"></a> CDaoRecordset:: SetCurrentIndex

Wywołaj tę funkcję elementu członkowskiego, aby ustawić indeks w zestawie rekordów typu "Table".

```cpp
void SetCurrentIndex(LPCTSTR lpszIndex);
```

### <a name="parameters"></a>Parametry

*lpszIndex*<br/>
Wskaźnik zawierający nazwę indeksu, który ma zostać ustawiony.

### <a name="remarks"></a>Uwagi

Rekordy w tabelach podstawowych nie są przechowywane w żadnej określonej kolejności. Ustawienie indeksu zmienia kolejność rekordów zwracanych z bazy danych, ale nie ma wpływu na kolejność, w jakiej są przechowywane rekordy. Określony indeks musi już być zdefiniowany. Jeśli spróbujesz użyć obiektu indeksu, który nie istnieje, lub jeśli indeks nie zostanie ustawiony po wywołaniu metody [Seek](#seek), MFC zgłasza wyjątek.

Można utworzyć nowy indeks dla tabeli, wywołując metodę [CDaoTableDef:: Create index](../../mfc/reference/cdaotabledef-class.md#createindex) i dołączając nowy indeks do kolekcji Indexs bazowego tabledef przez wywołanie [CDaoTableDef:: Append](../../mfc/reference/cdaotabledef-class.md#append), a następnie ponowne otwarcie zestawu rekordów.

Rekordy zwracane z zestawu rekordów typu "Tabela" można porządkować tylko według indeksów zdefiniowanych dla bazowego tabledef. Aby sortować rekordy w innej kolejności, można otworzyć zestaw rekordów typu dynamiczny lub typ migawki przy użyciu klauzuli **ORDERBY** SQL przechowywanej w [CDaoRecordset:: m_strSort](#m_strsort).

Aby uzyskać powiązane informacje, zobacz temat "indeks obiektu" i definicja "bieżący indeks" w pomocy DAO.

## <a name="cdaorecordsetsetfielddirty"></a><a name="setfielddirty"></a> CDaoRecordset:: SetFieldDirty

Wywołaj tę funkcję elementu członkowskiego, aby oflagować element członkowski danych pola zestawu rekordów jako zmieniony lub niezmieniony.

```cpp
void SetFieldDirty(
    void* pv,
    BOOL bDirty = TRUE);
```

### <a name="parameters"></a>Parametry

*wa*<br/>
Zawiera adres elementu członkowskiego danych pola w zestawie rekordów lub wartości NULL. Jeśli wartość jest równa NULL, wszystkie elementy członkowskie danych pól w zestawie rekordów są oflagowane. (Wartość NULL C++ nie jest taka sama jak wartość null w terminologii bazy danych, co oznacza, że nie ma wartości ")".

*bDirty*<br/>
Ma wartość TRUE, jeśli element członkowski danych Field ma być oflagowany jako "zanieczyszczony" (zmieniony). W przeciwnym razie zwraca wartość FALSE, jeśli element członkowski danych pola ma być oflagowany jako "czysty" (niezmieniony).

### <a name="remarks"></a>Uwagi

Oznaczanie pól jako niezmienionych gwarantuje, że pole nie zostanie zaktualizowane.

Struktura oznacza zmienione elementy członkowskie danych pola, aby upewnić się, że zostaną one zamienione na rekord źródła danych przez mechanizm wymiany pól rekordów DAO (DFX). Zmiana wartości pola na ogół ustawia pole jako zanieczyszczone automatycznie, więc rzadko trzeba będzie wywołać `SetFieldDirty` siebie, ale czasami warto upewnić się, że kolumny będą jawnie aktualizowane lub wstawiane niezależnie od tego, jaka wartość znajduje się w polu elementu członkowskiego danych. Mechanizm DFX korzysta również z PSEUDONULL. Aby uzyskać więcej informacji, zobacz [CDaoFieldExchange:: m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Jeśli mechanizm podwójnego buforowania nie jest używany, zmiana wartości pola nie powoduje automatycznego ustawienia pola jako zanieczyszczonego. W takim przypadku konieczne będzie jawne ustawienie pola jako zanieczyszczone. Flaga znajdująca się w [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) kontroluje to automatyczne sprawdzanie pól.

> [!NOTE]
> Wywołaj tę funkcję elementu członkowskiego tylko po wywołaniu metody [Edit](#edit) lub [AddNew](#addnew).

Użycie wartości NULL dla pierwszego argumentu funkcji spowoduje zastosowanie funkcji do wszystkich `outputColumn` pól, a nie pól **param** w `CDaoFieldExchange` . Na przykład wywołanie

[!code-cpp[NVC_MFCDatabase#6](../../mfc/codesnippet/cpp/cdaorecordset-class_6.cpp)]

ustawi tylko `outputColumn` pola na null; nie wpłynie to na pola **parametrów** .

Aby można było korzystać z **parametru**, należy podać rzeczywisty adres poszczególnych **parametrów** , na przykład:

[!code-cpp[NVC_MFCDatabase#7](../../mfc/codesnippet/cpp/cdaorecordset-class_7.cpp)]

Oznacza to, że nie można ustawić wszystkich pól **param** na null, jak można z `outputColumn` polami.

`SetFieldDirty` jest zaimplementowany przez `DoFieldExchange` .

## <a name="cdaorecordsetsetfieldnull"></a><a name="setfieldnull"></a> CDaoRecordset:: SetFieldNull

Wywołaj tę funkcję elementu członkowskiego, aby oflagować element członkowski danych pola zestawu rekordów jako null (w przypadku braku wartości) lub jako niebędący wartością null.

```cpp
void SetFieldNull(
    void* pv,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parametry

*wa*<br/>
Zawiera adres elementu członkowskiego danych pola w zestawie rekordów lub wartości NULL. Jeśli wartość jest równa NULL, wszystkie elementy członkowskie danych pól w zestawie rekordów są oflagowane. (Wartość NULL C++ nie jest taka sama jak wartość null w terminologii bazy danych, co oznacza, że nie ma wartości ")".

*bNull*<br/>
Różne od zera, jeśli element członkowski danych Field ma być oflagowany jako nieposiadający wartości (null). W przeciwnym razie wartość 0, jeśli element członkowski danych pola ma być oflagowany jako inny niż null.

### <a name="remarks"></a>Uwagi

`SetFieldNull` jest używany w przypadku pól powiązanych z `DoFieldExchange` mechanizmem.

Po dodaniu nowego rekordu do zestawu rekordów wszystkie elementy członkowskie danych pola są początkowo ustawiane na wartość null i oflagowane jako "zanieczyszczone" (zmienione). Gdy pobierasz rekord ze źródła danych, jego kolumny mają już wartości lub mają wartość null. Jeśli nie jest to konieczne, aby pole było puste, zostanie zgłoszone [CDaoException](../../mfc/reference/cdaoexception-class.md) .

Jeśli używasz mechanizmu podwójnego buforowania, na przykład jeśli chcesz wyznaczyć pole bieżącego rekordu jako niemające wartości, wywołaj `SetFieldNull` z *bNull* USTAWIONĄ na wartość true, aby oflagować ją jako wartość null. Jeśli pole zostało wcześniej oznaczone jako puste i teraz chcesz nadać mu wartość, po prostu ustaw jej nową wartość. Nie trzeba usuwać flagi o wartości null przy użyciu `SetFieldNull` . Aby określić, czy pole może mieć wartość null, wywołaj [IsFieldNullable](#isfieldnullable).

Jeśli nie używasz mechanizmu podwójnego buforowania, zmiana wartości pola nie powoduje automatycznego ustawienia pola jako zanieczyszczonego i wartości innej niż null. Należy jawnie ustawić pola zanieczyszczone i inne niż null. Flaga znajdująca się w [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) kontroluje to automatyczne sprawdzanie pól.

Mechanizm DFX korzysta z PSEUDONULL. Aby uzyskać więcej informacji, zobacz [CDaoFieldExchange:: m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

> [!NOTE]
> Wywołaj tę funkcję elementu członkowskiego tylko po wywołaniu metody [Edit](#edit) lub [AddNew](#addnew).

Użycie wartości NULL dla pierwszego argumentu funkcji spowoduje zastosowanie funkcji tylko do pól, a `outputColumn` nie pól **param** w `CDaoFieldExchange` . Na przykład wywołanie

[!code-cpp[NVC_MFCDatabase#8](../../mfc/codesnippet/cpp/cdaorecordset-class_8.cpp)]

ustawi tylko `outputColumn` pola na null; nie wpłynie to na pola **parametrów** .

## <a name="cdaorecordsetsetfieldvalue"></a><a name="setfieldvalue"></a> CDaoRecordset:: SetFieldValue

Wywołaj tę funkcję elementu członkowskiego, aby ustawić wartość pola, w pozycji porządkowej lub zmieniając wartość ciągu.

```cpp
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
Odwołanie do obiektu [COleVariant](../../mfc/reference/colevariant-class.md) zawierającego wartość zawartości pola.

*nIndex*<br/>
Liczba całkowita reprezentująca pozycję porządkową pola w kolekcji pól zestawu rekordów (liczony od zera).

*lpszValue*<br/>
Wskaźnik do ciągu zawierającego wartość zawartości pola.

### <a name="remarks"></a>Uwagi

Używaj `SetFieldValue` i [GetFieldValue —](#getfieldvalue) do dynamicznego wiązania pól w czasie wykonywania zamiast statycznego powiązania kolumn przy użyciu mechanizmu [DoFieldExchange](#dofieldexchange) .

Należy pamiętać, że jeśli nie tworzysz zestawu rekordów UNICODE, musisz użyć formy `SetFieldValue` , która nie zawiera `COleVariant` parametru lub `COleVariant` obiekt musi być jawnie zadeklarowany w formacie ANSI. Można to zrobić za pomocą formy [COleVariant:: COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** konstruktora z *vtSrc* set to `VT_BSTRT` (ANSI) lub przy użyciu `COleVariant` funkcji [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** z *vtSrc* ustawioną na `VT_BSTRT` .

Aby uzyskać powiązane informacje, zobacz tematy "obiekt pola" i "wartość właściwości" w pomocy DAO.

## <a name="cdaorecordsetsetfieldvaluenull"></a><a name="setfieldvaluenull"></a> CDaoRecordset:: SetFieldValueNull

Wywołaj tę funkcję elementu członkowskiego, aby ustawić pole na wartość null.

```cpp
void SetFieldValueNull(int nIndex);
void SetFieldValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks pola w zestawie rekordów dla wyszukiwania według indeksu od zera.

*lpszName*<br/>
Nazwa pola w zestawie rekordów dla wyszukiwania według nazwy.

### <a name="remarks"></a>Uwagi

Język C++ o wartości NULL nie jest taki sam jak wartość null, co w terminologii bazy danych oznacza, że nie ma żadnej wartości.

Aby uzyskać powiązane informacje, zobacz tematy "obiekt pola" i "wartość właściwości" w pomocy DAO.

## <a name="cdaorecordsetsetlockingmode"></a><a name="setlockingmode"></a> CDaoRecordset:: setlockmode

Wywołaj tę funkcję elementu członkowskiego, aby ustawić typ blokowania dla zestawu rekordów.

```cpp
void SetLockingMode(BOOL bPessimistic);
```

### <a name="parameters"></a>Parametry

*bPessimistic*<br/>
Flaga wskazująca typ blokowania.

### <a name="remarks"></a>Uwagi

Gdy trwa pesymistyczne blokowanie, Strona 2K zawierająca edytowany rekord jest zablokowany zaraz po wywołaniu `Edit` funkcji składowej. Strona jest odblokowana po wywołaniu `Update` `Close` funkcji lub operacji przenoszenia lub znajdowania.

Gdy optymistyczne blokowanie jest obowiązujące, Strona 2K zawierająca rekord jest zablokowana tylko w czasie, gdy rekord jest aktualizowany za pomocą `Update` funkcji składowej.

Jeśli strona jest zablokowana, żaden inny użytkownik nie może edytować rekordów na tej samej stronie. Jeśli wywołasz `SetLockingMode` i przekażesz wartość różną od zera, a inny użytkownik ma już zablokowaną stronę, wyjątek jest zgłaszany podczas wywoływania `Edit` . Inni użytkownicy mogą odczytywać dane z zablokowanych stron.

W przypadku wywołania `SetLockingMode` z wartością zerową i późniejszym wywołaniem `Update` , gdy strona jest zablokowana przez innego użytkownika, wystąpi wyjątek. Aby zobaczyć zmiany wprowadzone do rekordu przez innego użytkownika (i utracić zmiany), wywołaj `SetBookmark` funkcję członkowską z wartością zakładki bieżącego rekordu.

Podczas pracy ze źródłami danych ODBC tryb blokowania jest zawsze optymistyczny.

## <a name="cdaorecordsetsetparamvalue"></a><a name="setparamvalue"></a> CDaoRecordset:: SetParamValue

Wywołaj tę funkcję elementu członkowskiego, aby ustawić wartość parametru w zestawie rekordów w czasie wykonywania.

```cpp
virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);

virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Pozycja liczbowa parametru w kolekcji parametrów querydef.

*var*<br/>
Wartość do ustawienia; Zobacz uwagi.

*lpszName*<br/>
Nazwa parametru, którego wartość ma zostać ustawiona.

### <a name="remarks"></a>Uwagi

Parametr musi już zostać ustanowiony jako część ciągu SQL zestawu rekordów. Możesz uzyskać dostęp do parametru według nazwy lub jego pozycji indeksu w kolekcji.

Określ wartość, która ma zostać ustawiona jako `COleVariant` obiekt. Aby uzyskać informacje na temat ustawiania żądanej wartości i typu w `COleVariant` obiekcie, zobacz Klasa [COleVariant](../../mfc/reference/colevariant-class.md). Należy pamiętać, że jeśli nie tworzysz zestawu rekordów UNICODE, `COleVariant` obiekt musi być jawnie zadeklarowany jako ANSI. Można to zrobić za pomocą formy [COleVariant:: COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** konstruktora z *vtSrc* set to `VT_BSTRT` (ANSI) lub przy użyciu `COleVariant` funkcji [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** z *vtSrc* ustawioną na `VT_BSTRT` .

## <a name="cdaorecordsetsetparamvaluenull"></a><a name="setparamvaluenull"></a> CDaoRecordset:: SetParamValueNull

Wywołaj tę funkcję elementu członkowskiego, aby ustawić parametr na wartość null.

```cpp
void SetParamValueNull(int nIndex);
void SetParamValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks pola w zestawie rekordów dla wyszukiwania według indeksu od zera.

*lpszName*<br/>
Nazwa pola w zestawie rekordów dla wyszukiwania według nazwy.

### <a name="remarks"></a>Uwagi

Język C++ o wartości NULL nie jest taki sam jak wartość null, co w terminologii bazy danych oznacza, że nie ma żadnej wartości.

## <a name="cdaorecordsetsetpercentposition"></a><a name="setpercentposition"></a> CDaoRecordset:: SetPercentPosition

Wywołaj tę funkcję elementu członkowskiego, aby ustawić wartość, która zmienia przybliżoną lokalizację bieżącego rekordu w obiekcie zestawu rekordów na podstawie procentu rekordów w zestawie rekordów.

```cpp
void SetPercentPosition(float fPosition);
```

### <a name="parameters"></a>Parametry

*fPosition*<br/>
Liczba z zakresu od 0 do 100.

### <a name="remarks"></a>Uwagi

Podczas pracy z zestawem rekordów typu dynamicznego lub typu migawek, najpierw Wypełnij zestaw rekordów, przechodząc do ostatniego rekordu przed wywołaniem `SetPercentPosition` . W przypadku wywołania `SetPercentPosition` przed pełnym zapełnieniem zestawu rekordów, ilość ruchu jest określana względem liczby rekordów, do których dostęp jest wskazywany przez wartość [GetRecordCount](#getrecordcount). Możesz przenieść do ostatniego rekordu, wywołując metodę `MoveLast` .

Po wywołaniu `SetPercentPosition` , rekord w przybliżonej pozycji odpowiadającej tej wartości stanie się bieżący.

> [!NOTE]
> Wywołanie `SetPercentPosition` przenoszenia bieżącego rekordu do określonego rekordu w zestawie rekordów nie jest zalecane. Zamiast tego wywołaj funkcję członkowską [setzakładka](#setbookmark) .

Aby uzyskać powiązane informacje, zobacz temat "Właściwość PercentPosition" w pomocy DAO.

## <a name="cdaorecordsetupdate"></a><a name="update"></a> CDaoRecordset:: Update

Wywołaj tę funkcję elementu członkowskiego po wywołaniu `AddNew` `Edit` funkcji lub.

```cpp
virtual void Update();
```

### <a name="remarks"></a>Uwagi

To wywołanie jest wymagane do ukończenia `AddNew` operacji lub `Edit` .

Zarówno `AddNew` , jak i `Edit` przygotowując bufor edycji, w którym dodane lub edytowane dane są umieszczane w celu zapisywania do źródła danych. `Update` zapisuje dane. Aktualizowane są tylko pola oznaczone lub wykryte jako zmienione.

Jeśli źródło danych obsługuje transakcje, można wykonać `Update` wywołanie (oraz jego odpowiadające `AddNew` lub `Edit` wywołania) część transakcji.

> [!CAUTION]
> W przypadku wywołania `Update` bez uprzedniego wywołania metody `AddNew` lub `Edit` , `Update` zgłasza `CDaoException` . Jeśli wywołasz `AddNew` lub `Edit` , musisz wywołać `Update` przed wywołaniem [MoveNext](#movenext) lub zamknąć zestaw rekordów lub połączenie ze źródłem danych. W przeciwnym razie zmiany zostaną utracone bez powiadomienia.

Gdy obiekt zestawu rekordów jest pessimistically zablokowany w środowisku wielodostępnym, rekord pozostaje zablokowany od czasu `Edit` do momentu ukończenia aktualizacji. Jeśli zestaw rekordów jest optymistycznie zablokowany, rekord jest zablokowany i porównywany z wstępnie edytowanym rekordem tuż przed zaktualizowaniem w bazie danych. Jeśli rekord został zmieniony od momentu wywołania `Edit` , `Update` operacja kończy się niepowodzeniem, a MFC zgłasza wyjątek. Tryb blokowania można zmienić za pomocą `SetLockingMode` .

> [!NOTE]
> Optymistyczne blokowanie jest zawsze używane w formatach zewnętrznych baz danych, takich jak ODBC i Instalowalna ISAM.

Aby uzyskać powiązane informacje, zobacz tematy "Metoda AddNew", "Metoda CancelUpdate", "Delete Method", "Właściwość LastModified", "Metoda aktualizacji" i "EditMode Property" w pomocy DAO.

## <a name="see-also"></a>Zobacz także

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)<br/>
[Klasa CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)<br/>
[Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)<br/>
[Klasa CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)<br/>
