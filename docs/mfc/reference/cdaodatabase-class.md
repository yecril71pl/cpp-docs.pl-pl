---
title: Klasa CDaoDatabase
ms.date: 11/04/2016
f1_keywords:
- CDaoDatabase
- AFXDAO/CDaoDatabase
- AFXDAO/CDaoDatabase::CDaoDatabase
- AFXDAO/CDaoDatabase::CanTransact
- AFXDAO/CDaoDatabase::CanUpdate
- AFXDAO/CDaoDatabase::Close
- AFXDAO/CDaoDatabase::Create
- AFXDAO/CDaoDatabase::CreateRelation
- AFXDAO/CDaoDatabase::DeleteQueryDef
- AFXDAO/CDaoDatabase::DeleteRelation
- AFXDAO/CDaoDatabase::DeleteTableDef
- AFXDAO/CDaoDatabase::Execute
- AFXDAO/CDaoDatabase::GetConnect
- AFXDAO/CDaoDatabase::GetName
- AFXDAO/CDaoDatabase::GetQueryDefCount
- AFXDAO/CDaoDatabase::GetQueryDefInfo
- AFXDAO/CDaoDatabase::GetQueryTimeout
- AFXDAO/CDaoDatabase::GetRecordsAffected
- AFXDAO/CDaoDatabase::GetRelationCount
- AFXDAO/CDaoDatabase::GetRelationInfo
- AFXDAO/CDaoDatabase::GetTableDefCount
- AFXDAO/CDaoDatabase::GetTableDefInfo
- AFXDAO/CDaoDatabase::GetVersion
- AFXDAO/CDaoDatabase::IsOpen
- AFXDAO/CDaoDatabase::Open
- AFXDAO/CDaoDatabase::SetQueryTimeout
- AFXDAO/CDaoDatabase::m_pDAODatabase
- AFXDAO/CDaoDatabase::m_pWorkspace
helpviewer_keywords:
- CDaoDatabase [MFC], CDaoDatabase
- CDaoDatabase [MFC], CanTransact
- CDaoDatabase [MFC], CanUpdate
- CDaoDatabase [MFC], Close
- CDaoDatabase [MFC], Create
- CDaoDatabase [MFC], CreateRelation
- CDaoDatabase [MFC], DeleteQueryDef
- CDaoDatabase [MFC], DeleteRelation
- CDaoDatabase [MFC], DeleteTableDef
- CDaoDatabase [MFC], Execute
- CDaoDatabase [MFC], GetConnect
- CDaoDatabase [MFC], GetName
- CDaoDatabase [MFC], GetQueryDefCount
- CDaoDatabase [MFC], GetQueryDefInfo
- CDaoDatabase [MFC], GetQueryTimeout
- CDaoDatabase [MFC], GetRecordsAffected
- CDaoDatabase [MFC], GetRelationCount
- CDaoDatabase [MFC], GetRelationInfo
- CDaoDatabase [MFC], GetTableDefCount
- CDaoDatabase [MFC], GetTableDefInfo
- CDaoDatabase [MFC], GetVersion
- CDaoDatabase [MFC], IsOpen
- CDaoDatabase [MFC], Open
- CDaoDatabase [MFC], SetQueryTimeout
- CDaoDatabase [MFC], m_pDAODatabase
- CDaoDatabase [MFC], m_pWorkspace
ms.assetid: 8ff5b342-964d-449d-bef1-d0ff56aadf6d
ms.openlocfilehash: 6bdabafc905b1ae5d6ed9a1fcd83ab1982871c3b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50439287"
---
# <a name="cdaodatabase-class"></a>Klasa CDaoDatabase

Reprezentuje połączenie z bazą danych, dzięki któremu można działać na danych.

## <a name="syntax"></a>Składnia

```
class CDaoDatabase : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoDatabase::CDaoDatabase](#cdaodatabase)|Konstruuje `CDaoDatabase` obiektu. Wywołaj `Open` ustanowić połączenia obiektu do bazy danych.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoDatabase::CanTransact](#cantransact)|Zwraca wartość różną od zera, jeśli baza danych obsługuje transakcji.|
|[CDaoDatabase::CanUpdate](#canupdate)|Zwraca wartość różną od zera, jeśli `CDaoDatabase` nadaje obiektu (nie tylko do odczytu).|
|[CDaoDatabase::Close](#close)|Zamyka połączenie z bazą danych.|
|[CDaoDatabase::Create](#create)|Tworzy obiekt bazy danych DAO i inicjuje `CDaoDatabase` obiektu.|
|[CDaoDatabase::CreateRelation](#createrelation)|Definiuje nowej relacji między tabelami w bazie danych.|
|[CDaoDatabase::DeleteQueryDef](#deletequerydef)|Usuwa obiekt querydef zapisane w bazie danych querydefs — kolekcja.|
|[CDaoDatabase::DeleteRelation](#deleterelation)|Usuwa istniejącej relacji między tabelami w bazie danych.|
|[CDaoDatabase::DeleteTableDef](#deletetabledef)|Usuwa definicję tabeli w bazie danych. Spowoduje to usunięcie tabeli rzeczywiste i wszystkie jej dane.|
|[CDaoDatabase::Execute](#execute)|Wykonuje zapytanie akcji. Wywoływanie `Execute` dla zapytania, które zwraca wyniki zgłasza wyjątek.|
|[CDaoDatabase::GetConnect](#getconnect)|Zwraca ciąg połączenia używany do łączenia `CDaoDatabase` obiektu do bazy danych. Używane dla ODBC.|
|[CDaoDatabase::GetName](#getname)|Zwraca nazwę bazy danych obecnie w użyciu.|
|[CDaoDatabase::GetQueryDefCount](#getquerydefcount)|Zwraca liczbę zapytań zdefiniowanych dla bazy danych.|
|[CDaoDatabase::GetQueryDefInfo](#getquerydefinfo)|Zwraca informacje dotyczące określonego zapytania w bazie danych.|
|[CDaoDatabase::GetQueryTimeout](#getquerytimeout)|Zwraca liczbę sekund, po której bazy danych zapytania operacje przekroczy limit czasu. Ma wpływ na wszystkie kolejne Otwórz, Dodaj nowy, aktualizacji i Edytuj operations i innych operacji na źródeł danych ODBC (tylko) takich jak `Execute` wywołania.|
|[CDaoDatabase::GetRecordsAffected](#getrecordsaffected)|Zwraca liczbę rekordów wpływ Ostatnia aktualizacja, edytować lub dodawać operacji lub przez wywołanie `Execute`.|
|[CDaoDatabase::GetRelationCount](#getrelationcount)|Zwraca liczbę zdefiniowanych relacjach między tabelami w bazie danych.|
|[CDaoDatabase::GetRelationInfo](#getrelationinfo)|Zwraca informacje o określonej relacji zdefiniowanych między tabelami w bazie danych.|
|[CDaoDatabase::GetTableDefCount](#gettabledefcount)|Zwraca liczbę tabel w bazie danych.|
|[CDaoDatabase::GetTableDefInfo](#gettabledefinfo)|Zwraca informacje o określonej tabeli w bazie danych.|
|[CDaoDatabase::GetVersion](#getversion)|Zwraca wersję aparatu bazy danych skojarzonej z bazą danych.|
|[CDaoDatabase::IsOpen](#isopen)|Zwraca wartość różną od zera, jeśli `CDaoDatabase` obiektu jest obecnie połączony z bazą danych.|
|[CDaoDatabase::Open](#open)|Nawiązuje połączenie z bazą danych.|
|[CDaoDatabase::SetQueryTimeout](#setquerytimeout)|Ustawia liczbę sekund, po której bazy danych zapytania operacje (źródła danych ODBC tylko) przekroczy limit czasu. Ma wpływ na wszystkie kolejne Otwórz, Dodaj nowy, aktualizacji i operacje usuwania.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDaoDatabase::m_pDAODatabase](#m_pdaodatabase)|Wskaźnik do podstawowego obiektu bazy danych DAO.|
|[CDaoDatabase::m_pWorkspace](#m_pworkspace)|Wskaźnik do [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) obiekt, który zawiera bazę danych i umożliwia zdefiniowanie jego przestrzeni transakcji.|

## <a name="remarks"></a>Uwagi

Aby uzyskać informacji na temat obsługiwanych formatów bazy danych, zobacz [getname —](../../mfc/reference/cdaoworkspace-class.md#getname) funkcja elementu członkowskiego. Może mieć co najmniej jeden `CDaoDatabase` obiektów, które są aktywne w danym momencie w danego "obszaru roboczego," reprezentowany przez [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) obiektu. Obszar roboczy przechowuje kolekcję obiektów otwartą bazę danych o nazwie kolekcji baz danych.

> [!NOTE]
>  Klasy bazy danych MFC DAO różnią się od klas baz danych MFC ODBC — na podstawie. Wszystkie nazwy klasy bazy danych DAO mają prefiks "CDao". Klasa `CDaoDatabase` dostarcza interfejs podobny do klasy ODBC [CDatabase](../../mfc/reference/cdatabase-class.md). Główną różnicą jest to, że `CDatabase` uzyskuje dostęp do systemu DBMS za pośrednictwem interfejsu Open Database Connectivity (ODBC) i sterownik ODBC dla tego systemu DBMS. `CDaoDatabase` uzyskuje dostęp do danych za pośrednictwem dostępu do obiektu DAO (Data) opartą na aparacie bazy danych Microsoft Jet. Ogólnie rzecz biorąc klasy MFC, w oparciu o DAO sprzętowi więcej niż klas MFC, w oparciu o ODBC; klasy oparte na DAO można uzyskać dostęp do danych, w tym za pomocą sterowników ODBC, za pomocą ich własnych aparatu bazy danych. Klasy oparte na DAO obsługują także operacji języka definicji danych (DDL), takich jak dodawanie tablic przy użyciu klas, bez konieczności wywoływanie obiektów DAO bezpośrednio.

## <a name="usage"></a>Użycie

Obiekty bazy danych można utworzyć niejawnie, podczas tworzenia obiektów zestawu rekordów. Ale można również jawnie tworzyć obiekty bazy danych. Aby Użyj istniejącej bazy danych w sposób jawny przy użyciu `CDaoDatabase`, wykonaj jedną z następujących czynności:

- Konstruowania `CDaoDatabase` obiektu, przekazując wskaźnik do otwartego [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) obiektu.

- Lub konstrukcji `CDaoDatabase` obiektu bez określenia obszaru roboczego (MFC tworzy obiekt tymczasowy obszar roboczy).

Aby utworzyć nowy Microsoft Jet (. Baza danych MDB), konstruowania `CDaoDatabase` obiektu, a następnie wywołać jej [Utwórz](#create) funkcja elementu członkowskiego. Czy *nie* wywołania `Open` po `Create`.

Aby otworzyć istniejącej bazy danych, należy utworzyć `CDaoDatabase` obiektu, a następnie wywołać jej [Otwórz](#open) funkcja elementu członkowskiego.

Dowolną z poniższych metod dołącza obiektu bazy danych DAO kolekcji baz danych obszaru roboczego i otwiera połączenie z danymi. Jeśli następnie konstruowania [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md), lub [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) obiektów do działania w podłączonej bazie danych, Przekaż konstruktorów tych obiektów wskaźnik do Twojej `CDaoDatabase` obiektu. Po zakończeniu wprowadzania zmian przy użyciu połączenia, należy wywołać [Zamknij](#close) element członkowski funkcji i zniszcz `CDaoDatabase` obiektu. `Close` Zamyka wszystkie zestawy rekordów, które wcześniej nie zostało zamknięte.

## <a name="transactions"></a>Transakcje

Przetwarzanie transakcji bazy danych jest dostarczane na poziomie obszaru roboczego — zobacz [BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans), [CommitTrans](../../mfc/reference/cdaoworkspace-class.md#committrans), i [wycofywania](../../mfc/reference/cdaoworkspace-class.md#rollback) funkcji elementów członkowskich klasy `CDaoWorkspace` .

## <a name="odbc-connections"></a>Połączenia ODBC

Dołączanie tabel zewnętrznych do programu Microsoft Jet jest zalecany sposób pracy ze źródłami danych ODBC (. Baza danych MDB).

## <a name="collections"></a>Kolekcje

Każda baza danych przechowuje swoje własne kolekcje tabledef "," querydef "," zestawu rekordów "i" relacji obiektów. Klasa `CDaoDatabase` dostarcza funkcji elementów członkowskich do manipulowania tymi obiektami.

> [!NOTE]
>  Obiekty są przechowywane w DAO, nie w obiekcie bazy danych MFC. MFC dostarcza klas tabledef querydef i zestawie rekordów, ale nie dla relacji obiektów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CDaoDatabase`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

##  <a name="cantransact"></a>  CDaoDatabase::CanTransact

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy baza danych umożliwia transakcji.

```
BOOL CanTransact();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli baza danych obsługuje; transakcje: w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Transakcje są zarządzane w obszarze roboczym bazy danych.

##  <a name="canupdate"></a>  CDaoDatabase::CanUpdate

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy `CDaoDatabase` obiektu zezwala na aktualizacje.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość różną od zera `CDaoDatabase` obiektu zezwala na aktualizacje; w przeciwnym razie 0, wskazujący, że administrator przekazać wartość TRUE w *bReadOnly* po otwarciu `CDaoDatabase` obiektu lub że sama baza danych jest tylko do odczytu. Zobacz [Otwórz](#open) funkcja elementu członkowskiego.

### <a name="remarks"></a>Uwagi

Aby uzyskać informacje o aktualizacji bazy danych zobacz temat "Można zaktualizować właściwości" w Pomocy programu DAO.

##  <a name="cdaodatabase"></a>  CDaoDatabase::CDaoDatabase

Konstruuje `CDaoDatabase` obiektu.

```
CDaoDatabase(CDaoWorkspace* pWorkspace = NULL);
```

### <a name="parameters"></a>Parametry

*pWorkspace*<br/>
Wskaźnik do `CDaoWorkspace` obiektu, który będzie zawierał nowy obiekt bazy danych. Jeśli użytkownik zaakceptuje domyślna wartość NULL, Konstruktor tworzy tymczasową `CDaoWorkspace` obiektu, który używa domyślnego obszaru roboczego DAO. Możesz uzyskać wskaźnik do obiektu obszar roboczy za pomocą [m_pWorkspace](#m_pworkspace) element członkowski danych.

### <a name="remarks"></a>Uwagi

Po konstruowanie obiektu, jeśli tworzysz nowy Microsoft Jet (. MDB) bazy danych, należy wywołać obiekt [Utwórz](#create) funkcja elementu członkowskiego. Jeśli, zamiast tego otworzyć istniejącą bazę danych, wywołanie obiektu [Otwórz](#open) funkcja elementu członkowskiego.

Po zakończeniu za pomocą obiektu, należy wywołać jej [Zamknij](#close) element członkowski funkcji, a następnie zniszcz `CDaoDatabase` obiektu.

Użytkownik może okazać się przydatna do osadzenia `CDaoDatabase` obiektów w klasie dokumentów.

> [!NOTE]
>  A `CDaoDatabase` obiektu tworzona jest również niejawnie po otwarciu [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obiekt bez przekazywania wskaźnika do istniejącego `CDaoDatabase` obiektu. Tego obiektu bazy danych jest zamknięty, gdy zamkniesz obiekt zestawu rekordów.

##  <a name="close"></a>  CDaoDatabase::Close

Wywołaj tę funkcję elementu członkowskiego, aby rozłączyć z bazy danych i zamknij wszelkie otwarty zestaw rekordów, tabledefs — i querydefs — skojarzonego z bazą danych.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Jest dobrą praktyką, aby zamknąć te obiekty są sobie przed wywołaniem tej funkcji elementu członkowskiego. Zamykanie `CDaoDatabase` obiektu spowoduje usunięcie go z kolekcji baz danych w skojarzonej [obszaru roboczego](../../mfc/reference/cdaoworkspace-class.md). Ponieważ `Close` nie niszczy `CDaoDatabase` obiektu, można ponownie użyć obiektu przez otwarcie tej samej bazy danych lub innej bazy danych.

> [!CAUTION]
>  Wywołaj [aktualizacji](../../mfc/reference/cdaorecordset-class.md#update) funkcji składowej (jeśli istnieją oczekujące zmiany) i `Close` funkcja elementu członkowskiego na wszystkich obiektach otwarty zestaw rekordów, zanim zamkniesz bazy danych. Jeśli zakończysz funkcja, która deklaruje [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) lub `CDaoDatabase` obiekty na stosie, baza danych jest zamknięty, wszelkie niezapisane zmiany zostaną utracone, wszystkie oczekujące transakcje są wycofywane i wszelkie oczekujące zmiany w danych zostaną utracone.

> [!CAUTION]
>  Jeśli zostanie podjęta próba zamknięcia obiektu bazy danych, gdy wszystkie obiekty w zestawie rekordów są otwarte lub spróbuj zamknąć obiekt workspace, gdy wszystkie obiekty bazy danych należące do określonego obszaru roboczego są otwarte, te obiekty rekordów zostaną zamknięte, a wszystkie oczekujące aktualizacje i zmiany będą wycofane. Jeśli zostanie podjęta próba zamknięcia obiektu obszaru roboczego, gdy wszystkie obiekty bazy danych należące do niej są otwarte, operacja zamyka wszystkie obiekty bazy danych należące do tego obiektu określony obszar roboczy, co może spowodować obiektów niezamknięty zestawu rekordów jest zamknięty. Jeśli obiekt bazy danych nie jest zamknięty, MFC zgłasza błąd potwierdzenia w kompilacjach do debugowania.

Jeśli obiekt bazy danych jest zdefiniowane poza zakresem funkcji i zakończyć funkcji bez jego zamknięciem, obiekt bazy danych pozostanie otwarty, aż jawnie zamknięty lub moduł, w którym jest zdefiniowany jest poza zakresem.

##  <a name="create"></a>  CDaoDatabase::Create

Aby utworzyć nowy Microsoft Jet (. MDB) bazy danych, wywołania tej funkcji elementu członkowskiego, po konstruowania `CDaoDatabase` obiektu.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int dwOptions = 0);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Wyrażenie ciągu, która jest nazwą pliku bazy danych, który tworzysz. Może być pełną ścieżkę i nazwę pliku, taką jak "C:\\\MYDB. MDB". Musisz podać nazwę. Jeśli nie podasz z rozszerzeniem nazwy pliku. Jest dołączany MDB. Jeśli sieć obsługuje jednolitego konwencji nazewnictwa (UNC), można również określić ścieżkę sieciową, taką jak "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB". Tylko Microsoft Jet (. Pliki bazy danych MDB) mogą być tworzone za pomocą tej funkcji elementu członkowskiego. (Ułamkowe odwrócone są wymagane w literałach ciągu, ponieważ "\\" jest znakiem ucieczki C++.)

*lpszLocale*<br/>
Wyrażenie ciągu, można określić kolejność sortowania do utworzenia bazy danych. Wartość domyślna to `dbLangGeneral`. Możliwe wartości to:

- `dbLangGeneral` Angielskim, niemieckim, francuskim, portugalskim, włoski i nowoczesne hiszpański

- `dbLangArabic` Arabski

- `dbLangCyrillic` Rosyjski

- `dbLangCzech` Czeski

- `dbLangDutch` Holenderski

- `dbLangGreek` Grecki

- `dbLangHebrew` Hebrajski

- `dbLangHungarian` Węgierski

- `dbLangIcelandic` Islandzki

- `dbLangNordic` Języki Nordycki (Microsoft Jet aparatu bazy danych wersji 1.0 tylko)

- `dbLangNorwdan` Norweski i duński

- `dbLangPolish` Polski

- `dbLangSpanish` Hiszpański (tradycyjny)

- `dbLangSwedfin` Szwedzki i fiński

- `dbLangTurkish` Turecki

*dwOptions*<br/>
Liczba całkowita, która wskazuje, co najmniej jedną opcję. Możliwe wartości to:

- `dbEncrypt` Utwórz szyfrowanej bazy danych.

- `dbVersion10` Tworzenie bazy danych z bazy danych Microsoft Jet w wersji 1.0.

- `dbVersion11` Tworzenie bazy danych z bazy danych Microsoft Jet w wersji 1.1.

- `dbVersion20` Tworzenie bazy danych z bazy danych Microsoft Jet w wersji 2.0.

- `dbVersion30` Tworzenie bazy danych z bazy danych Microsoft Jet w wersji 3.0.

Jeżeli pominięto stała szyfrowania niezaszyfrowane baza danych jest tworzona. Można określić tylko jedną wersję stałą. Jeżeli pominięto stałą wersji bazy danych, która korzysta z bazy danych Microsoft Jet w wersji 3.0 jest tworzony.

> [!CAUTION]
>  Jeśli bazy danych nie jest zaszyfrowany, jest to możliwe, nawet w przypadku zaimplementowania bezpieczeństwa użytkownika i hasło, bezpośrednio odczytywać plik binarny dysku, który stanowi bazy danych.

### <a name="remarks"></a>Uwagi

`Create` Tworzy plik bazy danych i obiekcie podstawowej bazy danych DAO i inicjuje obiektu języka C++. Obiekt jest dołączany do kolekcji baz danych skojarzone obszarów roboczych. Obiekt bazy danych jest w stanie otwarcia; Nie wywołuj `Open*` po `Create`.

> [!NOTE]
>  Za pomocą `Create`, można utworzyć tylko Microsoft Jet (. Bazy danych MDB). Nie można utworzyć bazy danych ISAM lub baz danych ODBC.

##  <a name="createrelation"></a>  CDaoDatabase::CreateRelation

Wywołaj tę funkcję elementu członkowskiego, aby ustanowić relację między jedno lub więcej pól w tabeli podstawowej w bazie danych i jedno lub więcej pól w tabeli obcej (innej tabeli w bazie danych).

```
void CreateRelation(
    LPCTSTR lpszName,
    LPCTSTR lpszTable,
    LPCTSTR lpszForeignTable,
    long lAttributes,
    LPCTSTR lpszField,
    LPCTSTR lpszForeignField);

void CreateRelation(CDaoRelationInfo& relinfo);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Unikatowa nazwa obiektu relacji. Nazwa musi rozpoczynać się od litery i może zawierać maksymalnie 40 znaków. Może zawierać cyfry i znaki podkreślenia, ale nie może zawierać znaków interpunkcyjnych lub miejsca do magazynowania.

*lpszTable*<br/>
Nazwa tabeli podstawowej w relacji. Jeśli tabela nie istnieje, MFC, zgłasza wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

*lpszForeignTable*<br/>
Nazwa tabeli obcego w relacji. Jeśli tabela nie istnieje, MFC, zgłasza wyjątek typu `CDaoException`.

*lAttributes*<br/>
Wartość typu long zawierający informacje o tym typie relacji. Ta wartość umożliwia wymuszają więzy integralności, między innymi. Możesz użyć operatora bitowego OR ( **&#124;**) aby połączyć dowolny z następujących wartości (tak długo, jak zespół ma sens):

- `dbRelationUnique` Jest to relacja jeden do jednego.

- `dbRelationDontEnforce` Relacja nie jest wymuszane (integralność referencyjna).

- `dbRelationInherited` Relacja istnieje w bazie danych, innych niż bieżące, która zawiera dwie tabele dołączone.

- `dbRelationUpdateCascade` Aktualizacje będą kaskadowo (Aby uzyskać więcej informacji o kaskady, zobacz Uwagi).

- `dbRelationDeleteCascade` Kaskadowo zostaną usunięte.

*lpszField*<br/>
Wskaźnik na ciąg zakończony wartością null zawierający nazwę pola w tabeli podstawowej (o nazwie określonej przez *lpszTable*).

*lpszForeignField*<br/>
Wskaźnik na ciąg zakończony wartością null zawierający nazwę pola w tabeli obcego (o nazwie określonej przez *lpszForeignTable*).

*relinfo*<br/>
Odwołanie do [cdaorelationinfo —](../../mfc/reference/cdaorelationinfo-structure.md) obiekt, który zawiera informacje dotyczące relacji, w której chcesz utworzyć.

### <a name="remarks"></a>Uwagi

Relacja nie może dotyczyć zapytanie lub dołączonej tabeli z zewnętrznej bazy danych.

Gdy relacja obejmuje jedno pole w każdej z dwóch tabel, należy użyć pierwszej wersji funkcji. Gdy relacja obejmuje wiele pól, należy użyć drugiej wersji. Maksymalna liczba pól w relacji jest 14.

Ta akcja spowoduje utworzenie obiektu relacji podstawowej DAO, ale jest to szczegół implementacji MFC, ponieważ hermetyzacja biblioteki MFC relacji obiektów znajduje się w obrębie klasy `CDaoDatabase`. MFC nie dostarcza klasę dla relacji.

Ustaw relację atrybutów obiektu do aktywowania cascade operacji aparatu bazy danych automatycznie aktualizuje lub usuwa rekordy w co najmniej jedną tabelę, podczas wprowadzania zmian w tabelach pokrewnych klucza podstawowego.

Na przykład załóżmy, że możesz ustanowić usuwanie kaskadowe relacji między tabelami Klienci i zamówienia. Podczas usuwania rekordów z tabeli Customers, również zostaną usunięte rekordy w tabeli zamówienia, związane z tego klienta. Ponadto jeśli ustanowisz Kaskadowo usuń relacje między tabeli zamówienia i innymi tabelami, rekordy z tych tabel zostaną automatycznie usunięte podczas usuwania rekordów z tabeli Customers.

Aby uzyskać powiązane informacje zobacz temat "CreateRelation metody" w Pomocy programu DAO.

##  <a name="deletequerydef"></a>  CDaoDatabase::DeleteQueryDef

Wywołaj tę funkcję elementu członkowskiego, aby usunąć określony querydef — zapisane zapytanie — z `CDaoDatabase` obiektu querydefs — kolekcja.

```
void DeleteQueryDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Nazwa zapisanego zapytania, aby usunąć.

### <a name="remarks"></a>Uwagi

Później to zapytanie nie jest już zdefiniowana w bazie danych.

Informacji na temat tworzenia obiektów querydef zawiera klasa [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Obiekt querydef zostaje skojarzony z określonym `CDaoDatabase` obiektu podczas konstruowania `CDaoQueryDef` obiektu, przekazując go wskaźnik do obiektu bazy danych.

##  <a name="deleterelation"></a>  CDaoDatabase::DeleteRelation

Wywołaj tę funkcję elementu członkowskiego, aby usunąć istniejącej relacji z kolekcji relacji obiektu bazy danych.

```
void DeleteRelation(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Nazwa relacji do usunięcia.

### <a name="remarks"></a>Uwagi

Później relacja już istnieje.

Aby uzyskać powiązane informacje zobacz temat "Usuń metody" w Pomocy programu DAO.

##  <a name="deletetabledef"></a>  CDaoDatabase::DeleteTableDef

Wywołaj tę funkcję elementu członkowskiego, można usunąć określonej tabeli i wszystkie jej dane z `CDaoDatabase` obiektu tabledefs — kolekcja.

```
void DeleteTableDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Nazwa tabledef do usunięcia.

### <a name="remarks"></a>Uwagi

Po tej tabeli nie jest już zdefiniowane w bazie danych.

> [!NOTE]
>  Ostrożność bardzo nie można usunąć tabel systemowych.

Informacji na temat tworzenia obiektów tabledef zawiera klasa [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md). Obiekt tabledef zostaje skojarzony z określonym `CDaoDatabase` obiektu podczas konstruowania `CDaoTableDef` obiektu, przekazując go wskaźnik do obiektu bazy danych.

Aby uzyskać powiązane informacje zobacz temat "Usuń metody" w Pomocy programu DAO.

##  <a name="execute"></a>  CDaoDatabase::Execute

Wywołaj tę funkcję elementu członkowskiego, aby uruchomić kwerendę lub wykonaj instrukcję SQL w bazie danych.

```
void Execute(
    LPCTSTR lpszSQL,
    int nOptions = dbFailOnError);
```

### <a name="parameters"></a>Parametry

*lpszSQL*<br/>
Wskaźnik na ciąg zakończony wartością null zawierający prawidłowe polecenie SQL do wykonania.

*nOptions*<br/>
Liczba całkowita, która określa opcje związane z integralności zapytania. Możesz użyć operatora bitowego OR ( **&#124;**) można użyć dowolnej z następujących stałych (pod warunkiem połączenie ma sens — na przykład, użytkownik nie będzie obejmowało `dbInconsistent` z `dbConsistent`):

- `dbDenyWrite` Odmowa uprawnień do zapisu dla innych użytkowników.

- `dbInconsistent` (Ustawienie domyślne) Niespójne aktualizacje.

- `dbConsistent` Zgodne aktualizacje.

- `dbSQLPassThrough` Przekazywane SQL. Powoduje, że instrukcji SQL, które mają być przekazane do źródła danych ODBC do przetworzenia.

- `dbFailOnError` Wycofywanie aktualizacji, jeśli wystąpi błąd.

- `dbSeeChanges` Generowanie błędów czasu wykonywania, jeśli inny użytkownik ulegają zmianie danych, który jest edytowany.

> [!NOTE]
>  Jeśli oba `dbInconsistent` i `dbConsistent` uwzględniono lub jeśli nie jest, wynikiem jest wartość domyślna. Objaśnienia dotyczące tych stałych zobacz temat "Wykonania metody" w Pomocy programu DAO.

### <a name="remarks"></a>Uwagi

`Execute` działa tylko w przypadku akcji zapytania lub przekazywania zapytania SQL, które nie zwracają wartości. Nie działa dla zapytań select, które zwracają rekordy.

Dla definicji i informacji o zapytaniach akcji zobacz tematy "Akcja zapytania" i "Wykonywanie metody" w Pomocy programu DAO.

> [!TIP]
>  Biorąc pod uwagę poprawnych składniowo instrukcji języka SQL i odpowiednie uprawnienia, `Execute` funkcji składowej nie zakończy się niepowodzeniem nawet jeśli nie można modyfikować i usuwać pojedynczy wiersz. W związku z tym, należy zawsze używać `dbFailOnError` opcji w przypadku korzystania z `Execute` funkcję elementu członkowskiego, aby zaktualizować lub usunąć zapytania. Ta opcja powoduje, że MFC, aby zgłosić wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md) i wycofanie wszystkich pomyślnie wprowadzone zmiany, jeśli dowolny zmodyfikowanych rekordów są zablokowane i nie można zaktualizować lub usunąć. Należy zauważyć, że zawsze można wywołać `GetRecordsAffected` się wpłynęłoby to na liczbę rekordów.

Wywołaj [GetRecordsAffected](#getrecordsaffected) funkcja elementu członkowskiego obiektu bazy danych, aby określić liczbę rekordów na najnowszych, ostatnio `Execute` wywołania. Na przykład `GetRecordsAffected` zwraca informacje o liczbie rekordów usunięty, zaktualizowane lub wstawić podczas wykonywania kwerendy funkcjonalnej. Liczba zwracane nie będzie odzwierciedlał zmian w tabelach pokrewnych, gdy cascade aktualizuje lub usuwa są stosowane.

`Execute` Zwraca zestaw rekordów. Za pomocą `Execute` na kwerendzie, która wybiera rekordy powoduje, że MFC, aby zgłosić wyjątek typu `CDaoException`. (Brak nie `ExecuteSQL` analogiczne do funkcji składowej `CDatabase::ExecuteSQL`.)

##  <a name="getconnect"></a>  CDaoDatabase::GetConnect

Wywołaj tę funkcję elementu członkowskiego, aby pobrać parametry połączenia używane do łączenia z `CDaoDatabase` obiektu do bazy danych ODBC lub ISAM.

```
CString GetConnect();
```

### <a name="return-value"></a>Wartość zwracana

Parametrów połączenia Jeśli [Otwórz](#open) została wywołana pomyślnie na źródle danych ODBC; w przeciwnym razie, pusty ciąg. Dla programu Microsoft Jet (. Bazy danych MDB), ciąg jest zawsze pusta, chyba że zostanie ustawiona do użytku z programem `dbSQLPassThrough` używana z opcją [Execute](#execute) funkcja elementu członkowskiego lub używane podczas otwierania zestawu rekordów.

### <a name="remarks"></a>Uwagi

Ciąg zawiera informacje o źródle otwartą bazę danych lub bazy danych używane w zapytania przekazującego. Parametry połączenia składa się ze specyfikatora typu bazy danych i zero lub więcej parametrów, oddzielając je średnikami.

> [!NOTE]
>  Przy użyciu klas MFC DAO nawiązywania połączenia ze źródłem danych za pośrednictwem ODBC jest mniej wydajne niż nawiązywania połączenia za pośrednictwem dołączonej tabeli.

> [!NOTE]
>  Ciąg połączenia jest używany do przekazywania dodatkowych informacji do ODBC i sterownikami niektórych ISAM, zgodnie z potrzebami. Nie jest używana dla. MDB bazy danych. Dla tabel bazowych bazy danych Microsoft Jet, ciąg połączenia jest pustym ciągiem ("") z wyjątkiem sytuacji, gdy zostanie on użyty do zapytania przekazującego SQL zgodnie z opisem w obszarze zwracają wartość powyżej.

Zobacz [Otwórz](#open) funkcja elementu członkowskiego, aby uzyskać opis sposobu tworzenia parametrów połączenia. Gdy ustawiono parametrów połączenia `Open` wywołanie, możesz później służy do Sprawdź ustawienie, aby określić typ, ścieżki, identyfikator, hasła lub ODBC źródło danych użytkownika bazy danych.

##  <a name="getname"></a>  CDaoDatabase::GetName

Wywołaj tę funkcję elementu członkowskiego, aby pobrać nazwę aktualnie otwarte bazy danych, jest to nazwa istniejącego pliku bazy danych lub nazwę zarejestrowanego źródła danych ODBC.

```
CString GetName();
```

### <a name="return-value"></a>Wartość zwracana

Pełna ścieżka i nazwa pliku bazy danych, jeśli to się powiedzie; w przeciwnym razie pusta [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Uwagi

Jeśli sieć obsługuje jednolitego konwencji nazewnictwa (UNC), można również określić ścieżkę sieciową — na przykład "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB". (Ułamkowe odwrócone są wymagane w literałach ciągu, ponieważ "\\" jest znakiem ucieczki C++.)

Na przykład, można wyświetlać tę nazwę w pozycji. Jeśli wystąpi błąd podczas pobierania nazwy, MFC, zgłasza wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

> [!NOTE]
>  Aby uzyskać lepszą wydajność podczas uzyskują dostęp do zewnętrznych baz danych, zalecamy Dołączanie tabel zewnętrznych baz danych do bazy danych Microsoft Jet (. MDB) zamiast bezpośredniego połączenia z źródła danych.

Typ bazy danych jest wskazywany przez plik lub katalog, który wskazuje ścieżkę, do, wykonując następujące czynności:

|Wskazuje nazwę ścieżki...|Typ bazy danych|
|--------------------------|-------------------|
|. Plik MDB|Bazy danych Microsoft Jet (Microsoft Access)|
|Katalog, który zawiera. Pliki DBF|bazy danych programu dBASE|
|Katalog, który zawiera. Plik XLS|Baza danych programu Microsoft Excel|
|Katalog, który zawiera. Pliki PDX|Aparat|
|Katalog zawierający pliki bazy danych odpowiednio sformatowany tekst|Bazę danych w formacie tekstowym|

W przypadku baz danych ODBC, takich jak SQL Server i Oracle parametry połączenia bazy danych określa nazwę źródła danych (DSN), która jest zarejestrowana przez sterownik ODBC.

##  <a name="getquerydefcount"></a>  CDaoDatabase::GetQueryDefCount

Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę zapytań zdefiniowanych w bazie danych querydefs — kolekcja.

```
short GetQueryDefCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba zapytań zdefiniowanych w bazie danych.

### <a name="remarks"></a>Uwagi

`GetQueryDefCount` jest przydatne, jeśli potrzebujesz pętli wszystkich querydefs — w querydefs — kolekcja. Aby uzyskać informacje dotyczące danego zapytania w kolekcji, zobacz [GetQueryDefInfo](#getquerydefinfo).

##  <a name="getquerydefinfo"></a>  CDaoDatabase::GetQueryDefInfo

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać różne rodzaje informacji na temat zapytanie zdefiniowane w bazie danych.

```
void GetQueryDefInfo(
    int nIndex,
    CDaoQueryDefInfo& querydefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetQueryDefInfo(
    LPCTSTR lpszName,
    CDaoQueryDefInfo& querydefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks wstępnie zdefiniowanego zapytania w bazie danych querydefs — kolekcja do wyszukiwania według indeksu.

*querydefinfo*<br/>
Odwołanie do [cdaoquerydefinfo —](../../mfc/reference/cdaoquerydefinfo-structure.md) obiektów, które zwraca żądane informacje.

*dwInfoOptions*<br/>
Opcje, które określają, które informacje o zestawie rekordów do pobrania. Dostępne opcje są wymienione w tym miejscu oraz jakie mogą spowodować, że funkcja ma zwracać zestaw rekordów:

- Nazwa AFX_DAO_PRIMARY_INFO (ustawienie domyślne), typ

- AFX_DAO_SECONDARY_INFO głównej informacje oraz: Data utworzenia, Data ostatniej aktualizacji, zwraca rekordy, aktualizowalne

- AFX_DAO_ALL_INFO głównych i dodatkowych informacji plus: ODBCTimeout SQL, Connect

*lpszName*<br/>
Ciąg zawierający nazwę zapytanie zdefiniowane w bazie danych, wyszukiwanie według nazwy.

### <a name="remarks"></a>Uwagi

Dwie wersje funkcji są dostarczane, można wybrać zapytanie, indeks w kolekcji querydefs — bazy danych lub nazwę kwerendy.

Aby uzyskać opis informacje zwracane w *querydefinfo*, zobacz [cdaoquerydefinfo —](../../mfc/reference/cdaoquerydefinfo-structure.md) struktury. Ta struktura zawiera elementy członkowskie, które odnoszą się do elementów wymienionych powyżej w opisie informacji *dwInfoOptions*. W przypadku żądania informacji o jeden poziom, otrzymują wszelkie wcześniejsze poziomy również informacje o.

##  <a name="getquerytimeout"></a>  CDaoDatabase::GetQueryTimeout

Wywołaj tę funkcję elementu członkowskiego, aby pobrać bieżącą liczbę sekund, zanim kolejne operacje na połączonej bazy danych są przekroczyło limit czasu.

```
short GetQueryTimeout();
```

### <a name="return-value"></a>Wartość zwracana

Krótka liczba całkowita zawierająca wartość limitu czasu w sekundach.

### <a name="remarks"></a>Uwagi

Przekroczono limit czasu może być operacją, ze względu na problemy z dostępem do sieci, czasu przetwarzania zapytania nadmiernego i tak dalej. Gdy to ustawienie jest włączone, ma to wpływ na wszystkie otwarte, Dodaj nowy, aktualizowanie i usuwanie operacji na wszystkie zestawy rekordów skojarzonych z tym `CDaoDatabase` obiektu. Bieżące ustawienie limitu czasu można zmienić, wywołując [SetQueryTimeout](#setquerytimeout). Zmiana wartości limitu czasu zapytania dla zestawu rekordów po otwarciu nie zmienia wartość dla zestawu rekordów. Na przykład, kolejne [przenieść](../../mfc/reference/cdaorecordset-class.md#move) operacji należy używać nowej wartości. Wartością domyślną jest ustawiany podczas inicjowania aparatu bazy danych.

Wartością domyślną dla limitów czasu kwerendy jest pobierana z rejestru Windows. Jeśli nie ma żadnego ustawienia rejestru, wartość domyślna to 60 sekund. Nie wszystkie bazy danych obsługują możliwość ustawiania wartości limitu czasu zapytania. Jeśli ustawisz wartość limitu czasu zapytania, 0, następuje limitu czasu; i komunikacji z bazą danych może przestać odpowiadać. To zachowanie może być przydatne podczas programowania. Jeśli wywołanie zakończy się niepowodzeniem, MFC, zgłasza wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

Aby uzyskać powiązane informacje zobacz temat "QueryTimeout Property" w Pomocy programu DAO.

##  <a name="getrecordsaffected"></a>  CDaoDatabase::GetRecordsAffected

Wywołaj tę funkcję elementu członkowskiego, aby określić liczbę zmodyfikowanych przez wywołanie ostatnich rekordów [Execute](#execute) funkcja elementu członkowskiego.

```
long GetRecordsAffected();
```

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita typu long zawierającą liczbę zmodyfikowanych rekordów.

### <a name="remarks"></a>Uwagi

Wartość zwracana zawiera liczbę rekordów usunięty, zaktualizowane lub wstawione przez akcję uruchomienie zapytania przy użyciu `Execute`. Liczba zwracane nie będzie odzwierciedlał zmian w tabelach pokrewnych, gdy cascade aktualizuje lub usuwa są stosowane.

Aby uzyskać powiązane informacje zobacz temat "RecordsAffected Property" w Pomocy programu DAO.

##  <a name="getrelationcount"></a>  CDaoDatabase::GetRelationCount

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać numer zdefiniowanych relacjach między tabelami w bazie danych.

```
short GetRelationCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba zdefiniowanych relacjach między tabelami w bazie danych.

### <a name="remarks"></a>Uwagi

`GetRelationCount` jest przydatne, jeśli potrzebujesz pętli wszystkich relacji zdefiniowanych w kolekcji relacje bazy danych. Aby uzyskać informacje dotyczące danego relacji w kolekcji, zobacz [GetRelationInfo](#getrelationinfo).

Aby zilustrować koncepcji relację, należy wziąć pod uwagę tabeli dostawcy i tabeli Produkty, które może mieć relacji jeden do wielu. Ta relacja jeden dostawca może dostarczyć więcej niż jeden produkt. Inne relacje są jednego i wiele do wielu.

##  <a name="getrelationinfo"></a>  CDaoDatabase::GetRelationInfo

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać informacje dotyczące określonej relacji w kolekcji relacje bazy danych.

```
void GetRelationInfo(
    int nIndex,
    CDaoRelationInfo& relinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetRelationInfo(
    LPCTSTR lpszName,
    CDaoRelationInfo& relinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks obiektu relacji w zbiorze relacje bazy danych, do wyszukiwania według indeksu.

*relinfo*<br/>
Odwołanie do [cdaorelationinfo —](../../mfc/reference/cdaorelationinfo-structure.md) obiektów, które zwraca żądane informacje.

*dwInfoOptions*<br/>
Opcje, które określają, które informacje o relacji do pobrania. Dostępne opcje są wymienione w tym miejscu wraz z co mogą spowodować, że funkcja ma zwracać relacji:

- Tabela obcego nazwy tabeli, AFX_DAO_PRIMARY_INFO (ustawienie domyślne)

- Atrybuty AFX_DAO_SECONDARY_INFO, informacji o polach

Informacje pola [cdaorelationfieldinfo —](../../mfc/reference/cdaorelationfieldinfo-structure.md) obiekt zawiera pola z tabeli podstawowej uczestniczących w relacji.

*lpszName*<br/>
Ciąg zawierający nazwę obiektu relacji do wyszukiwania według nazwy.

### <a name="remarks"></a>Uwagi

Dwie wersje tej funkcji, zapewniają dostęp przez indeks lub według nazwy. Aby uzyskać opis informacje zwracane w *relinfo*, zobacz [cdaorelationinfo —](../../mfc/reference/cdaorelationinfo-structure.md) struktury. Ta struktura zawiera elementy członkowskie, które odnoszą się do elementów wymienionych powyżej w opisie informacji *dwInfoOptions*. Jeśli żądania informacji o jeden poziom, możesz także uzyskać informacje na wszelkie wcześniejsze poziomach.

> [!NOTE]
>  Jeśli ustawisz relacji atrybutów obiektu do aktywowania cascade operacji (`dbRelationUpdateCascades` lub `dbRelationDeleteCascades`), aparat bazy danych Microsoft Jet automatycznie aktualizuje lub usuwa rekordy w jeden lub więcej innych tabel, gdy zmiany zostaną wprowadzone do związane z kluczem podstawowym tabele. Na przykład załóżmy, że możesz ustanowić usuwanie kaskadowe relacji między tabelami Klienci i zamówienia. Podczas usuwania rekordów z tabeli Customers, również zostaną usunięte rekordy w tabeli zamówienia, związane z tego klienta. Ponadto jeśli ustanowisz Kaskadowo usuń relacje między tabeli zamówienia i innymi tabelami, rekordy z tych tabel zostaną automatycznie usunięte podczas usuwania rekordów z tabeli Customers.

##  <a name="gettabledefcount"></a>  CDaoDatabase::GetTableDefCount

Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę tabel w bazie danych.

```
short GetTableDefCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba tabledefs — w bazie danych.

### <a name="remarks"></a>Uwagi

`GetTableDefCount` jest przydatne, jeśli potrzebujesz pętli wszystkich tabledefs — w bazie danych tabledefs — kolekcja. Aby uzyskać informacje dotyczące danej tabeli w kolekcji, zobacz [GetTableDefInfo](#gettabledefinfo).

##  <a name="gettabledefinfo"></a>  CDaoDatabase::GetTableDefInfo

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać różne rodzaje informacji o tabeli w bazie danych.

```
void GetTableDefInfo(
    int nIndex,
    CDaoTableDefInfo& tabledefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetTableDefInfo(
    LPCTSTR lpszName,
    CDaoTableDefInfo& tabledefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks obiektu tabledef w bazie danych tabledefs — kolekcja do wyszukiwania według indeksu.

*tabledefinfo*<br/>
Odwołanie do [cdaotabledefinfo —](../../mfc/reference/cdaotabledefinfo-structure.md) obiektów, które zwraca żądane informacje.

*dwInfoOptions*<br/>
Opcje, które określają, które informacje dotyczące tabeli do pobrania. Dostępne opcje są wymienione w tym miejscu wraz z co mogą spowodować, że funkcja ma zwracać relacji:

- Atrybuty nazwy AFX_DAO_PRIMARY_INFO (ustawienie domyślne), można zaktualizować,

- AFX_DAO_SECONDARY_INFO głównej informacje oraz: Data utworzenia, Data ostatniej aktualizacji nazwy tabeli źródłowej, Połącz

- AFX_DAO_ALL_INFO głównych i dodatkowych informacji plus: liczba rekordów reguły sprawdzania poprawności, tekst sprawdzania poprawności

*lpszName*<br/>
Nazwa obiektu tabledef wyszukiwania według nazwy.

### <a name="remarks"></a>Uwagi

Dwie wersje funkcji są dostarczane, można wybrać tabelę według indeksu w bazie danych tabledefs — Kolekcja lub nazwę tabeli.

Aby uzyskać opis informacje zwracane w *tabledefinfo*, zobacz [cdaotabledefinfo —](../../mfc/reference/cdaotabledefinfo-structure.md) struktury. Ta struktura zawiera elementy członkowskie, które odnoszą się do elementów wymienionych powyżej w opisie informacji *dwInfoOptions*. W przypadku żądania informacji o jeden poziom, otrzymasz informacje dotyczące wszelkich poprzednich poziomach.

> [!NOTE]
>  Opcja AFX_DAO_ALL_INFO zapewnia informacje, które może działać powoli, można uzyskać. W tym przypadku licząc rekordy w tabeli może być bardzo dużo czasu, jeśli istnieje wiele rekordów.

##  <a name="getversion"></a>  CDaoDatabase::GetVersion

Wywołaj tę funkcję elementu członkowskiego, aby określić wersję pliku bazy danych Microsoft Jet.

```
CString GetVersion();
```

### <a name="return-value"></a>Wartość zwracana

A [CString](../../atl-mfc-shared/reference/cstringt-class.md) który wskazuje wersję pliku bazy danych skojarzony z obiektem.

### <a name="remarks"></a>Uwagi

Wartość zwracana reprezentuje numer wersji w postaci "major.minor"; na przykład "3.0". Numer wersji produktu (na przykład 3.0) składa się z numerem wersji (3), okres i numer wersji (0). Wersje do daty są 1.0, 1.1, 2.0 i 3.0.

Aby uzyskać powiązane informacje zobacz temat "Właściwość Version" w Pomocy programu DAO.

##  <a name="isopen"></a>  CDaoDatabase::IsOpen

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy `CDaoDatabase` obiekt jest obecnie otwarty w bazie danych.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość różną od zera `CDaoDatabase` obiekt jest obecnie otwarty; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

##  <a name="m_pdaodatabase"></a>  CDaoDatabase::m_pDAODatabase

Zawiera wskaźnik do interfejsu OLE dla podstawowych obiektów bazy danych DAO `CDaoDatabase` obiektu.

### <a name="remarks"></a>Uwagi

Jeśli potrzebujesz dostępu do interfejsu DAO bezpośrednio za pomocą tego wskaźnika.

Aby uzyskać informacje o wywołującym DAO bezpośrednio, zobacz [techniczne 54 Uwaga](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

##  <a name="m_pworkspace"></a>  CDaoDatabase::m_pWorkspace

Zawiera wskaźnik do [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) obiekt, który zawiera obiekt bazy danych.

### <a name="remarks"></a>Uwagi

Jeśli potrzebujesz dostępu do obszaru roboczego bezpośrednio za pomocą tego wskaźnika — na przykład, aby uzyskać łącza do innych obiektów bazy danych w kolekcji baz danych obszaru roboczego.

##  <a name="open"></a>  CDaoDatabase::Open

Musisz wywołać tę funkcję elementu członkowskiego, aby zainicjować nowo skonstruowany `CDaoDatabase` obiekt, który reprezentuje istniejącej bazy danych.

```
virtual void Open(
    LPCTSTR lpszName,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T(""));
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Wyrażenie ciągu, które jest nazwą istniejącej Microsoft Jet (. Plik bazy danych MDB). Jeśli nazwa pliku ma rozszerzenie, jest wymagany. Jeśli sieć obsługuje jednolitego konwencji nazewnictwa (UNC), można również określić ścieżkę sieciową, taką jak "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB". (Ułamkowe odwrócone są wymagane w literałach ciągu, ponieważ "\\" jest znakiem ucieczki C++.)

Zagadnienia do rozważenia przy użyciu *lpszName*. Jeśli go:

- Odwołuje się do bazy danych, która jest już otwarty w trybie wyłączności przez innego użytkownika, MFC zgłaszającej wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md). Pułapki tego wyjątku, aby umożliwić użytkownikowi wiedzieć, że baza danych jest niedostępna.

- Jest pustym ciągiem ("") i *lpszConnect* jest "ODBC;", dzięki czemu użytkownik może wybrać bazę danych, wyświetlane jest okno dialogowe, w ofercie wszystkie zarejestrowane nazwy źródeł danych ODBC. Należy unikać bezpośredniego połączenia ze źródłami danych ODBC; Zamiast tego użyj dołączonej tabeli.

- W przeciwnym razie nie odwołuje się do istniejącej bazy danych lub prawidłową nazwę źródła danych ODBC, MFC zgłaszającej wyjątek typu `CDaoException`.

> [!NOTE]
>  Aby uzyskać szczegółowe informacje o kodach błędów DAO Zobacz DAOERR. Plik H. Aby uzyskać powiązane informacje zobacz temat "Możliwe do wychwycenia błędami dostępu do danych" w Pomocy programu DAO.

*bExclusive*<br/>
Wartość logiczna, która ma wartość TRUE, jeśli baza danych ma zostać otwarty dla wyłącznego dostępu (udostępniana) i wartość FALSE, jeśli baza danych ma zostać otwarty w celu zapewnienia dostępu współdzielonego. Jeśli ten argument zostanie pominięty, bazy danych zostanie otwarty w celu zapewnienia dostępu współdzielonego.

*bReadOnly*<br/>
Wartość logiczna, która ma wartość TRUE, jeśli baza danych ma zostać otwarty dla dostęp tylko do odczytu i wartość FALSE, jeśli baza danych ma zostać otwarty do odczytu i zapisu. Jeśli ten argument zostanie pominięty, baza danych zostanie otwarty dostęp do odczytu/zapisu. Wszystkie zależne zestawy rekordów dziedziczenia tego atrybutu.

*lpszConnect*<br/>
Wyrażenie ciągu używany do otwierania bazy danych. Ten ciąg stanowi ODBC połączyć argumentów. Trzeba podać argumenty wyłącznych i tylko do odczytu, aby podać ciąg źródłowy. Jeśli baza danych jest bazą danych Microsoft Jet (. MDB), ten ciąg jest pusty (""). Składnia dla wartości domyślnej — **_T**("") — zawiera przenośność Unicode, a także ANSI kompilacji aplikacji.

### <a name="remarks"></a>Uwagi

`Open` Kojarzy bazy danych z obiektu źródłowego DAO. Obiekt bazy danych nie można użyć do utworzenia zestawu rekordów, tabledef lub querydef obiektów, dopóki nie zostanie zainicjowany. `Open` dołącza kolekcji baz danych obszaru roboczego skojarzonego obiektu bazy danych.

Użyj parametrów w następujący sposób:

- Podczas otwierania programu Microsoft Jet (. Baza danych MDB), użyj *lpszName* parametr i przekazać pusty ciąg dla *lpszConnect* parametru lub przekazać ciągu hasła w postaci "; PWD = hasło ", jeśli baza danych jest chroniony hasłem (. MDB bazy danych tylko).

- Podczas otwierania źródła danych ODBC, należy przekazać prawidłowy ciąg połączenia ODBC w *lpszConnect* oraz do ciągu pustego w *lpszName*.

Aby uzyskać powiązane informacje zobacz temat "OpenDatabase metody" w Pomocy programu DAO.

> [!NOTE]
>  Aby uzyskać lepszą wydajność podczas uzyskiwania dostępu do zewnętrznych baz danych, w tym ISAM baz danych i źródeł danych ODBC, zalecane jest, dołączanie tabel zewnętrznych baz danych do bazy danych aparatu Microsoft Jet (. MDB) zamiast bezpośredniego połączenia z źródła danych.

Istnieje możliwość, przekroczy limit czasu próby połączenia, jeśli na przykład host systemu DBMS jest niedostępny. Jeśli próba połączenia zakończy się niepowodzeniem, `Open` zgłasza wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

Pozostałe uwagi dotyczą tylko baz danych ODBC:

Jeśli baza danych znajduje się baza danych ODBC i parametrów w swojej `Open` wywołania nie zawiera wystarczających informacji, aby nawiązać połączenie, sterownik ODBC powoduje otwarcie okna dialogowego, aby uzyskać niezbędne informacje od użytkownika. Gdy wywołujesz `Open`, parametry połączenia, *lpszConnect*, są przechowywane przez użytkowników i jest dostępna poprzez wywołanie [GetConnect](#getconnect) funkcja elementu członkowskiego.

Jeśli chcesz, możesz otworzyć własne okno dialogowe przed wywołaniem `Open` Aby uzyskać informacje od użytkownika, takie jak hasła, następnie dodać tych informacji do przekazania do ciągu połączenia `Open`. Można też zapisać parametry połączenia przekazywania (być może w rejestrze systemu Windows), więc można używać następnego czasu wywołania aplikacji `Open` na `CDaoDatabase` obiektu.

Umożliwia również parametry połączenia dla autoryzacji logowanie na wielu poziomach (każdy inny `CDaoDatabase` obiekt) lub przekazywać innych informacji specyficznych dla bazy danych.

##  <a name="setquerytimeout"></a>  CDaoDatabase::SetQueryTimeout

Wywołaj tę funkcję elementu członkowskiego, aby zastąpić domyślną liczbę sekund określającą kolejne operacje na limit czasu połączonej bazy danych.

```
void SetQueryTimeout(short nSeconds);
```

### <a name="parameters"></a>Parametry

*nSekund*<br/>
Liczba sekund, aby przed próby kwerendy upłynie limit czasu.

### <a name="remarks"></a>Uwagi

Przekroczono limit czasu może być operacją, ze względu na problemy z dostępem do sieci, czasu przetwarzania zapytania nadmiernego i tak dalej. Wywołaj `SetQueryTimeout` przed otwierającymi nawiasami rekordów lub przed wywołaniem metody w zestawie rekordów [działają funkcje AddNew](../../mfc/reference/cdaorecordset-class.md#addnew), [aktualizacji](../../mfc/reference/cdaorecordset-class.md#update), lub [Usuń](../../mfc/reference/cdaorecordset-class.md#delete) funkcje Członkowskie, jeśli chcesz zmienić kwerendę wartość limitu czasu. To ustawienie ma wpływ na wszystkie kolejne [Otwórz](../../mfc/reference/cdaorecordset-class.md#open), `AddNew`, `Update`, i `Delete` wywołania do żadnych zestawów rekordów skojarzonych z tym `CDaoDatabase` obiektu. Zmiana wartości limitu czasu zapytania dla zestawu rekordów po otwarciu nie zmienia wartość dla zestawu rekordów. Na przykład, kolejne [przenieść](../../mfc/reference/cdaorecordset-class.md#move) operacji należy używać nowej wartości.

Wartością domyślną dla zapytania przekroczeń limitu czasu wynosi 60 sekund. Nie wszystkie bazy danych obsługują możliwość ustawiania wartości limitu czasu zapytania. Jeśli ustawisz wartość limitu czasu zapytania, 0, następuje limitu czasu; Komunikacja z bazą danych może przestać odpowiadać. To zachowanie może być przydatne podczas programowania.

Aby uzyskać powiązane informacje zobacz temat "QueryTimeout Property" w Pomocy programu DAO.

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)<br/>
[Klasa CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)<br/>
[Klasa CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)<br/>
[Klasa CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)<br/>
[Klasa CDatabase](../../mfc/reference/cdatabase-class.md)<br/>
[Klasa CDaoException](../../mfc/reference/cdaoexception-class.md)
