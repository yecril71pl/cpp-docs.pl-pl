---
title: Klasa CDaoDatabase
ms.date: 09/17/2019
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
ms.openlocfilehash: 683f3f9ebb09d69461e4f9026841363c452f4793
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096175"
---
# <a name="cdaodatabase-class"></a>Klasa CDaoDatabase

Reprezentuje połączenie z bazą danych programu Access za pomocą obiektów dostępu do danych (DAO). Obiekty DAO są obsługiwane przez pakiet Office 2013. Element DAO 3,6 jest wersją ostateczną i jest uznawany za przestarzały.

## <a name="syntax"></a>Składnia

```
class CDaoDatabase : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoDatabase::CDaoDatabase](#cdaodatabase)|Konstruuje `CDaoDatabase` obiekt. Wywołaj `Open` , aby połączyć obiekt z bazą danych.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoDatabase:: gettransact](#cantransact)|Zwraca wartość różną od zera, jeśli baza danych obsługuje transakcje.|
|[CDaoDatabase:: Update](#canupdate)|Zwraca wartość różną od zera `CDaoDatabase` , jeśli obiekt jest aktualizowalny (nie tylko do odczytu).|
|[CDaoDatabase:: Close](#close)|Zamyka połączenie z bazą danych.|
|[CDaoDatabase:: Create](#create)|Tworzy źródłowy obiekt bazy danych DAO i inicjuje `CDaoDatabase` obiekt.|
|[CDaoDatabase::CreateRelation](#createrelation)|Definiuje nową relację między tabelami w bazie danych.|
|[CDaoDatabase::DeleteQueryDef](#deletequerydef)|Usuwa obiekt querydef zapisany w kolekcji QueryDefs bazy danych.|
|[CDaoDatabase::DeleteRelation](#deleterelation)|Usuwa istniejące relacje między tabelami w bazie danych.|
|[CDaoDatabase::DeleteTableDef](#deletetabledef)|Usuwa definicję tabeli w bazie danych. Spowoduje to usunięcie rzeczywistej tabeli i wszystkich jej danych.|
|[CDaoDatabase:: Execute](#execute)|Wykonuje zapytanie akcji. Wywołanie `Execute` zapytania, które zwraca wyniki, zgłasza wyjątek.|
|[CDaoDatabase::GetConnect](#getconnect)|Zwraca parametry połączenia używane do łączenia `CDaoDatabase` obiektu z bazą danych. Używany do ODBC.|
|[CDaoDatabase:: GetName](#getname)|Zwraca nazwę aktualnie używanej bazy danych.|
|[CDaoDatabase::GetQueryDefCount](#getquerydefcount)|Zwraca liczbę zapytań zdefiniowanych dla bazy danych.|
|[CDaoDatabase::GetQueryDefInfo](#getquerydefinfo)|Zwraca informacje dotyczące określonego zapytania zdefiniowanego w bazie danych.|
|[CDaoDatabase::GetQueryTimeout](#getquerytimeout)|Zwraca liczbę sekund, po upływie których przekroczenie limitu czasu operacji zapytania bazy danych. Wpływa na wszystkie kolejne operacje otwierania, dodawania nowych, aktualizacji i edycji oraz inne operacje na źródłach danych ODBC (tylko), `Execute` takie jak wywołania.|
|[CDaoDatabase::GetRecordsAffected](#getrecordsaffected)|Zwraca liczbę rekordów objętych ostatnią operacją Update, Edit lub Add lub przez wywołanie metody `Execute`.|
|[CDaoDatabase::GetRelationCount](#getrelationcount)|Zwraca liczbę relacji zdefiniowanych między tabelami w bazie danych.|
|[CDaoDatabase::GetRelationInfo](#getrelationinfo)|Zwraca informacje o określonej relacji zdefiniowanej między tabelami w bazie danych.|
|[CDaoDatabase::GetTableDefCount](#gettabledefcount)|Zwraca liczbę tabel zdefiniowanych w bazie danych.|
|[CDaoDatabase::GetTableDefInfo](#gettabledefinfo)|Zwraca informacje o określonej tabeli w bazie danych.|
|[CDaoDatabase:: GetVersion](#getversion)|Zwraca wersję aparatu bazy danych skojarzoną z bazą danych.|
|[CDaoDatabase:: IsOpen](#isopen)|Zwraca wartość różną od zera `CDaoDatabase` , jeśli obiekt jest obecnie połączony z bazą danych.|
|[CDaoDatabase:: Open](#open)|Nawiązuje połączenie z bazą danych.|
|[CDaoDatabase::SetQueryTimeout](#setquerytimeout)|Ustawia liczbę sekund, po upływie których przekroczenie limitu czasu operacji zapytań bazy danych (tylko w źródłach danych ODBC). Dotyczy wszystkich kolejnych operacji otwierania, dodawania nowych, aktualizowania i usuwania.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDaoDatabase::m_pDAODatabase](#m_pdaodatabase)|Wskaźnik do bazowego obiektu bazy danych DAO.|
|[CDaoDatabase::m_pWorkspace](#m_pworkspace)|Wskaźnik do obiektu [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) , który zawiera bazę danych i definiuje jego przestrzeń transakcji.|

## <a name="remarks"></a>Uwagi

Aby uzyskać informacje o obsługiwanych formatach bazy danych, zobacz Funkcja elementu członkowskiego [GetName](../../mfc/reference/cdaoworkspace-class.md#getname) . Może istnieć jeden lub więcej `CDaoDatabase` obiektów aktywnych jednocześnie w danym obszarze roboczym, reprezentowane przez obiekt [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) . Obszar roboczy obsługuje kolekcję otwartych obiektów bazy danych o nazwie kolekcja baz danych.

## <a name="usage"></a>Użycie

Obiekty bazy danych można tworzyć niejawnie, podczas tworzenia obiektów zestawu rekordów. Możesz również jawnie tworzyć obiekty bazy danych. Aby jawnie `CDaoDatabase`użyć istniejącej bazy danych, wykonaj jedną z następujących czynności:

- Konstruowanie obiektu, przekazanie wskaźnika do otwartego obiektu [CDaoWorkspace.](../../mfc/reference/cdaoworkspace-class.md) `CDaoDatabase`

- Lub konstruowanie `CDaoDatabase` obiektu bez określania obszaru roboczego (MFC tworzy tymczasowy obiekt obszaru roboczego).

Aby utworzyć nowy program Microsoft Jet (. MDB), konstruowanie `CDaoDatabase` obiektu i wywoływanie jego funkcji [tworzenia](#create) elementu członkowskiego. *Nie* wywołuj `Open` po. `Create`

Aby otworzyć istniejącą bazę danych, Utwórz `CDaoDatabase` obiekt i Wywołaj jego [otwartą](#open) funkcję członkowską.

Każda z tych technik dołącza obiekt bazy danych DAO do kolekcji baz danych obszaru roboczego i otwiera połączenie z danymi. Po utworzeniu obiektów [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)lub [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) do działania w połączonej bazie danych, należy przekazać konstruktory dla tych `CDaoDatabase` obiektów wskaźnikiem do obiektu. Po zakończeniu korzystania z połączenia wywołaj funkcję [Zamknij](#close) element członkowski i zniszcz `CDaoDatabase` obiekt. `Close`zamyka wszystkie zestawy rekordów, które nie zostały wcześniej zamknięte.

## <a name="transactions"></a>Transakcje

Przetwarzanie transakcji bazy danych jest dostarczane na poziomie obszaru roboczego — Zobacz funkcje składowe [BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans), [CommitTrans](../../mfc/reference/cdaoworkspace-class.md#committrans)i [Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback) klasy `CDaoWorkspace`.

## <a name="odbc-connections"></a>Połączenia ODBC

Zalecanym sposobem pracy ze źródłami danych ODBC jest dołączenie tabel zewnętrznych do aparatu Microsoft Jet (. MDB).

## <a name="collections"></a>Kolekcje

Każda baza danych przechowuje własne kolekcje obiektów tabledef, querydef, zestaw rekordów i relacji. Klasy `CDaoDatabase` dostarcza funkcje członkowskie do manipulowania tymi obiektami.

> [!NOTE]
>  Obiekty są przechowywane w obiekcie DAO, a nie w obiektach bazy danych MFC. MFC dostarcza klasy dla obiektów tabledef, querydef i recordset, ale nie dla obiektów relacji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CDaoDatabase`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao. h

##  <a name="cantransact"></a>CDaoDatabase:: gettransact

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy baza danych zezwala na transakcje.

```
BOOL CanTransact();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli baza danych obsługuje transakcje; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Transakcje są zarządzane w obszarze roboczym bazy danych.

##  <a name="canupdate"></a>CDaoDatabase:: Update

Wywołaj tę funkcję elementu członkowskiego, `CDaoDatabase` aby określić, czy obiekt zezwala na aktualizacje.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli `CDaoDatabase` obiekt zezwala na aktualizacje; w przeciwnym razie wartość 0 wskazuje, że wartość true w *bReadOnly* została przeprowadzona `CDaoDatabase` podczas otwierania obiektu lub że sama baza danych jest tylko do odczytu. Zobacz [Otwórz](#open) funkcję członkowską.

### <a name="remarks"></a>Uwagi

Aby uzyskać informacje dotyczące możliwość aktualizacji bazy danych, zobacz temat "Aktualizowalna właściwość" w pomocy DAO.

##  <a name="cdaodatabase"></a>CDaoDatabase::CDaoDatabase

Konstruuje `CDaoDatabase` obiekt.

```
CDaoDatabase(CDaoWorkspace* pWorkspace = NULL);
```

### <a name="parameters"></a>Parametry

*pWorkspace*<br/>
Wskaźnik do `CDaoWorkspace` obiektu, który będzie zawierać nowy obiekt bazy danych. W przypadku zaakceptowania domyślnej wartości null Konstruktor tworzy obiekt tymczasowy `CDaoWorkspace` , który używa domyślnego obszaru roboczego DAO. Możesz uzyskać wskaźnik do obiektu obszaru roboczego za pośrednictwem elementu członkowskiego danych [m_pWorkspace](#m_pworkspace) .

### <a name="remarks"></a>Uwagi

Po skonstruowaniu obiektu, jeśli tworzysz nowy program Microsoft Jet (. MDB), wywołaj funkcję [tworzenia](#create) elementu członkowskiego obiektu. Jeśli jesteś, otwierając istniejącą bazę danych, wywołaj funkcję [otwierającego](#open) elementu członkowskiego obiektu.

Po zakończeniu pracy z obiektem należy wywołać jego [zamykającą](#close) funkcję członkowską, a następnie zniszczyć `CDaoDatabase` obiekt.

Może być wygodne osadzenie `CDaoDatabase` obiektu w klasie dokumentu.

> [!NOTE]
>  Obiekt jest również tworzony niejawnie, jeśli otworzysz obiekt [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) bez przekazywania wskaźnika do istniejącego `CDaoDatabase` obiektu. `CDaoDatabase` Ten obiekt bazy danych jest zamykany po zamknięciu obiektu zestawu rekordów.

##  <a name="close"></a>CDaoDatabase:: Close

Wywołaj tę funkcję elementu członkowskiego, aby rozłączyć się z bazą danych i zamknąć wszystkie otwarte zestawy rekordów, tabledefs i querydef skojarzone z bazą danych.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Dobrym sposobem jest zamknięcie tych obiektów samodzielnie przed wywołaniem tej funkcji elementu członkowskiego. Zamknięcie obiektu spowoduje usunięcie go z kolekcji baz danych w skojarzonym [obszarze roboczym.](../../mfc/reference/cdaoworkspace-class.md) `CDaoDatabase` Ponieważ `Close` nie niszczy tego `CDaoDatabase` obiektu, można ponownie użyć tego obiektu, otwierając tę samą bazę danych lub inną bazę danych.

> [!CAUTION]
>  Wywołaj funkcję elementu członkowskiego [aktualizacji](../../mfc/reference/cdaorecordset-class.md#update) (jeśli istnieją oczekujące zmiany) `Close` i funkcję członkowską dla wszystkich otwartych obiektów zestawu rekordów przed zamknięciem bazy danych. Jeśli zakończysz funkcję, która [](../../mfc/reference/cdaorecordset-class.md) deklaruje `CDaoDatabase` CDaoRecordset lub obiekty na stosie, baza danych zostanie ZAMKNIĘTA, wszystkie niezapisane zmiany zostaną utracone, wszystkie oczekujące transakcje zostaną wycofane i wszystkie oczekujące zmiany danych zostaną utracone.

> [!CAUTION]
>  Jeśli spróbujesz zamknąć obiekt bazy danych w czasie, gdy wszystkie obiekty zestawu rekordów są otwarte lub jeśli spróbujesz zamknąć obiekt obszaru roboczego, gdy wszystkie obiekty bazy danych należące do tego określonego obszaru roboczego są otwarte, te obiekty zestawu rekordów zostaną zamknięte i wszystkie oczekujące aktualizacje lub zmiany będą wycofany. Jeśli spróbujesz zamknąć obiekt obszaru roboczego, gdy wszystkie obiekty bazy danych należące do niego są otwarte, operacja zamknie wszystkie obiekty bazy danych należące do tego określonego obiektu obszaru roboczego, co może spowodować zamknięcie niezamkniętych obiektów zestawu rekordów. Jeśli obiekt bazy danych nie zostanie zamknięty, MFC zgłosi błąd potwierdzenia w kompilacjach debugowania.

Jeśli obiekt bazy danych jest zdefiniowany poza zakresem funkcji i zamykasz funkcję bez jej zamykania, obiekt bazy danych pozostanie otwarty do momentu jawnego zamknięcia lub moduł, w którym jest zdefiniowany, jest poza zakresem.

##  <a name="create"></a>CDaoDatabase:: Create

Aby utworzyć nowy program Microsoft Jet (. MDB), Wywołaj tę funkcję elementu członkowskiego po utworzeniu `CDaoDatabase` obiektu.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int dwOptions = 0);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Wyrażenie ciągu, który jest nazwą tworzonego pliku bazy danych. Może to być pełna ścieżka i nazwa pliku, na przykład "C:\\\MYDB. MDB ". Należy podać nazwę. Jeśli nie podasz rozszerzenia nazwy pliku,. Dołączany jest MDB. Jeśli sieć obsługuje ujednolicone konwencje nazewnictwa (UNC), można również określić ścieżkę sieciową, taką jak "\\\\\\\\\MYSERVER\\\MYSHARE\\\mydir \MYDB". Tylko Microsoft Jet (. Pliki bazy danych MDB) można utworzyć za pomocą tej funkcji elementu członkowskiego. (W literałach ciągu są wymagane podwójne ukośniki odwrotne,\\ C++ ponieważ "" jest znakiem ucieczki).

*lpszLocale*<br/>
Wyrażenie ciągu używane do określenia kolejności sortowania na potrzeby tworzenia bazy danych. Wartość domyślna to `dbLangGeneral`. Możliwe wartości to:

- `dbLangGeneral`Angielski, niemiecki, francuski, portugalski, włoski i nowoczesny hiszpański

- `dbLangArabic`Arabski

- `dbLangCyrillic`Rosyjski

- `dbLangCzech`Czeski

- `dbLangDutch`Holenderski

- `dbLangGreek`Grecki

- `dbLangHebrew`Hebrajski

- `dbLangHungarian`Węgierski

- `dbLangIcelandic`Islandzki

- `dbLangNordic`Języki nordyckie (tylko aparat bazy danych Microsoft Jet w wersji 1,0)

- `dbLangNorwdan`Norweski i duński

- `dbLangPolish`Polski

- `dbLangSpanish`Tradycyjny hiszpański

- `dbLangSwedfin`Szwedzki i fiński

- `dbLangTurkish`Turecki

*dwOptions*<br/>
Liczba całkowita, która wskazuje co najmniej jedną opcję. Możliwe wartości to:

- `dbEncrypt`Utwórz zaszyfrowaną bazę danych.

- `dbVersion10`Utwórz bazę danych z bazą danych Microsoft Jet w wersji 1,0.

- `dbVersion11`Utwórz bazę danych z bazą danych Microsoft Jet w wersji 1,1.

- `dbVersion20`Utwórz bazę danych z bazą danych Microsoft Jet w wersji 2,0.

- `dbVersion30`Utwórz bazę danych z bazą danych Microsoft Jet w wersji 3,0.

W przypadku pominięcia stałej szyfrowania zostanie utworzona niezaszyfrowana baza danych. Można określić tylko jedną stałą wersji. W przypadku pominięcia stałej wersji zostanie utworzona baza danych, która korzysta z bazy danych Microsoft Jet w wersji 3,0.

> [!CAUTION]
>  Jeśli baza danych nie jest zaszyfrowana, możliwe jest nawet w przypadku zaimplementowania zabezpieczeń użytkownika/hasła, aby bezpośrednio odczytać plik dysku binarnego stanowiący bazę danych.

### <a name="remarks"></a>Uwagi

`Create`tworzy plik bazy danych i źródłowy obiekt bazy danych DAO i inicjuje C++ obiekt. Obiekt jest dołączany do kolekcji baz danych skojarzonego obszaru roboczego. Obiekt bazy danych jest w stanie otwartym; Nie wywołuj `Open*` po `Create`.

> [!NOTE]
>  W `Create`programie można tworzyć tylko Microsoft Jet (. MDB). Nie można tworzyć baz danych ISAM ani baz danych ODBC.

##  <a name="createrelation"></a>CDaoDatabase:: isrelation

Wywołaj tę funkcję elementu członkowskiego, aby ustanowić relację między jednym lub większą liczbą pól w tabeli podstawowej w bazie danych i co najmniej jednym polem w tabeli obcej (innej tabeli w bazie danych).

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
Unikatowa nazwa obiektu relacji. Nazwa musi zaczynać się od litery i może zawierać maksymalnie 40 znaków. Może zawierać cyfry i znaki podkreślenia, ale nie może zawierać znaków interpunkcyjnych ani spacji.

*lpszTable*<br/>
Nazwa tabeli podstawowej w relacji. Jeśli tabela nie istnieje, MFC zgłasza wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

*lpszForeignTable*<br/>
Nazwa tabeli obcej w relacji. Jeśli tabela nie istnieje, MFC zgłasza wyjątek typu `CDaoException`.

*lAttributes*<br/>
Długa wartość zawierająca informacje o typie relacji. Możesz użyć tej wartości, aby wymusić integralność referencyjną, między innymi. Można użyć operatora bitowego lub ( **&#124;** ), aby połączyć dowolne z następujących wartości (o ile ma to zastosowanie w kombinacji):

- `dbRelationUnique`Relacja to jeden do jednego.

- `dbRelationDontEnforce`Relacja nie jest wymuszana (bez integralności referencyjnej).

- `dbRelationInherited`Relacja istnieje w nieaktualnej bazie danych, która zawiera dwie dołączone tabele.

- `dbRelationUpdateCascade`Aktualizacje będą kaskadowo (Aby uzyskać więcej informacji na temat kaskad, zobacz uwagi).

- `dbRelationDeleteCascade`Usunięcia zostaną kaskadowo.

*lpszField*<br/>
Wskaźnik do ciągu zakończonego wartością null zawierający nazwę pola w tabeli podstawowej (nazwana przez *lpszTable*).

*lpszForeignField*<br/>
Wskaźnik do ciągu zakończonego wartością null zawierający nazwę pola w tabeli obcej (nazwana przez *lpszForeignTable*).

*relinfo*<br/>
Odwołanie do obiektu [CDaoRelationInfo —](../../mfc/reference/cdaorelationinfo-structure.md) , który zawiera informacje o relacji, którą chcesz utworzyć.

### <a name="remarks"></a>Uwagi

Relacja nie może zawierać zapytania ani dołączonej tabeli z zewnętrznej bazy danych.

Użyj pierwszej wersji funkcji, gdy relacja obejmuje jedno pole w każdej z dwóch tabel. Użyj drugiej wersji, gdy relacja obejmuje wiele pól. Maksymalna liczba pól w relacji wynosi 14.

Ta akcja powoduje utworzenie bazowego obiektu relacji DAO, ale jest to szczegóły implementacji MFC, ponieważ hermetyzacja obiektów relacji MFC jest zawarta w `CDaoDatabase`klasie. MFC nie dostarcza klasy dla relacji.

Jeśli ustawisz atrybuty obiektu relacji w celu aktywowania operacji kaskadowych, aparat bazy danych automatycznie zaktualizuje lub usunie rekordy w jednej lub kilku innych tabelach, gdy zmiany zostaną wprowadzone do powiązanych tabel klucza podstawowego.

Załóżmy na przykład, że ustanawiasz relację usuwania kaskadowego między tabelą Klienci a tabelą Orders. Po usunięciu rekordów z tabeli Customers rekordy w tabeli Orders powiązanej z tym klientem również zostaną usunięte. Ponadto, jeśli ustanawiasz kaskadowe relacje usuwania między tabelą Orders i innymi tabelami, rekordy z tych tabel są automatycznie usuwane po usunięciu rekordów z tabeli Customers.

Aby uzyskać powiązane informacje, zobacz temat "Metoda" norelation "w pomocy DAO.

##  <a name="deletequerydef"></a>CDaoDatabase::D eleteQueryDef

Wywołaj tę funkcję elementu członkowskiego, aby usunąć określony `CDaoDatabase` obiekt querydef — zapisane zapytanie — z kolekcji querydef obiektu.

```
void DeleteQueryDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Nazwa zapisanego zapytania do usunięcia.

### <a name="remarks"></a>Uwagi

Następnie to zapytanie nie jest już zdefiniowane w bazie danych.

Aby uzyskać informacje na temat tworzenia obiektów querydef, zobacz Klasa [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Obiekt querydef zostaje skojarzony z określonym `CDaoDatabase` obiektem podczas `CDaoQueryDef` konstruowania obiektu, przekazując go do obiektu bazy danych.

##  <a name="deleterelation"></a>CDaoDatabase::D eleteRelation

Wywołaj tę funkcję elementu członkowskiego, aby usunąć istniejącą relację z kolekcji relacji obiektu bazy danych.

```
void DeleteRelation(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Nazwa relacji do usunięcia.

### <a name="remarks"></a>Uwagi

Następnie relacja już nie istnieje.

Aby uzyskać powiązane informacje, zobacz temat "Delete Method" w pomocy DAO.

##  <a name="deletetabledef"></a>CDaoDatabase::D eleteTableDef

Wywołaj tę funkcję elementu członkowskiego, aby usunąć określoną tabelę i wszystkie jej dane `CDaoDatabase` z kolekcji TableDefs obiektu.

```
void DeleteTableDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Nazwa tabledef do usunięcia.

### <a name="remarks"></a>Uwagi

Następnie ta tabela nie jest już zdefiniowana w bazie danych.

> [!NOTE]
>  Należy zachować ostrożność, aby nie usuwać tabel systemowych.

Informacje o tworzeniu obiektów tabledef można znaleźć w temacie Class [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md). Obiekt tabledef jest kojarzony z określonym `CDaoDatabase` obiektem podczas `CDaoTableDef` konstruowania obiektu, przekazując mu wskaźnik do obiektu bazy danych.

Aby uzyskać powiązane informacje, zobacz temat "Delete Method" w pomocy DAO.

##  <a name="execute"></a>CDaoDatabase:: Execute

Wywołaj tę funkcję elementu członkowskiego, aby uruchomić zapytanie akcji lub wykonać instrukcję SQL w bazie danych.

```
void Execute(
    LPCTSTR lpszSQL,
    int nOptions = dbFailOnError);
```

### <a name="parameters"></a>Parametry

*lpszSQL*<br/>
Wskaźnik na ciąg zakończony znakiem null zawierający prawidłowe polecenie SQL do wykonania.

*nOptions*<br/>
Liczba całkowita, która określa opcje dotyczące integralności zapytania. Można użyć operatora bitowego lub ( **&#124;** ), aby połączyć dowolne z następujących stałych (pod warunkiem, że połączenie jest sensowne — na przykład nie można łączyć `dbInconsistent` z `dbConsistent`):

- `dbDenyWrite`Odmów uprawnienia do zapisu innym użytkownikom.

- `dbInconsistent`Wartooć Niespójne aktualizacje.

- `dbConsistent`Spójne aktualizacje.

- `dbSQLPassThrough`Przekazywanie SQL. Powoduje przekazanie instrukcji SQL do źródła danych ODBC w celu przetworzenia.

- `dbFailOnError`Wycofywanie aktualizacji w przypadku wystąpienia błędu.

- `dbSeeChanges`Generuj błąd czasu wykonywania, jeśli inny użytkownik zmienia edytowane dane.

> [!NOTE]
>  Jeśli oba `dbInconsistent` elementy `dbConsistent` i są dołączone lub nie są uwzględniane, wynik jest wartością domyślną. Aby uzyskać wyjaśnienie tych stałych, zobacz temat "Metoda Execute" w pomocy DAO.

### <a name="remarks"></a>Uwagi

`Execute`działa tylko w przypadku zapytań akcji lub zapytań przekazujących SQL, które nie zwracają wyników. Nie działa w przypadku zapytań SELECT, które zwracają rekordy.

Aby uzyskać definicję i informacje o zapytaniach akcji, zobacz tematy "zapytanie funkcjonalne" i "metoda wykonywania" w pomocy DAO.

> [!TIP]
>  Za pomocą składniowo prawidłowej instrukcji SQL i odpowiednich uprawnień funkcja `Execute` członkowska nie powiedzie się, nawet jeśli nie można zmodyfikować lub usunąć pojedynczego wiersza. W związku z tym zawsze `dbFailOnError` należy używać opcji przy `Execute` użyciu funkcji składowej do uruchamiania zapytania Update lub DELETE. Ta opcja powoduje, że MFC zgłasza wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md) i wycofuje wszystkie pomyślne zmiany, jeśli którykolwiek z rekordów podlega zablokowanym i nie można go zaktualizować ani usunąć. Należy pamiętać, że zawsze można `GetRecordsAffected` wywołać, aby zobaczyć, ile rekordów miało wpływ.

Wywołaj funkcję członkowską [GetRecordsAffected](#getrecordsaffected) obiektu bazy danych, aby określić liczbę rekordów, których dotyczy ostatnie `Execute` wywołanie. Na przykład `GetRecordsAffected` zwraca informacje o liczbie rekordów usuniętych, zaktualizowanych lub wstawianych podczas wykonywania zapytania akcji. Zwracana liczba nie będzie odzwierciedlać zmian w powiązanych tabelach, gdy są włączone kaskadowe aktualizacje lub usunięcia.

`Execute`nie zwraca zestawu rekordów. Użycie `Execute` w zapytaniu, które wybiera rekordy powoduje zgłoszenie wyjątku typu `CDaoException`przez MFC. (Nie `ExecuteSQL` istnieje funkcja członkowska analogiczna `CDatabase::ExecuteSQL`do.)

##  <a name="getconnect"></a>CDaoDatabase:: GetConnect

Wywołaj tę funkcję elementu członkowskiego, aby pobrać parametry połączenia używane `CDaoDatabase` do połączenia obiektu z bazą danych ODBC lub ISAM.

```
CString GetConnect();
```

### <a name="return-value"></a>Wartość zwracana

Parametry połączenia, jeśli [otwarcie](#open) zostało wywołane pomyślnie na źródle danych ODBC; w przeciwnym razie pusty ciąg. Dla aparatu Microsoft Jet (. MDB), ciąg jest zawsze pusty, chyba że zostanie ustawiony do użycia z `dbSQLPassThrough` opcją używaną z funkcją [Execute](#execute) member lub używaną podczas otwierania zestawu rekordów.

### <a name="remarks"></a>Uwagi

Ten ciąg zawiera informacje dotyczące źródła otwartej bazy danych lub bazy danych używanej w zapytaniu przekazującym. Parametry połączenia składają się ze specyfikatora typu bazy danych i nie mają parametrów oddzielonych średnikami.

> [!NOTE]
>  Używanie klas MFC DAO do nawiązywania połączenia ze źródłem danych za pośrednictwem ODBC jest mniej wydajne niż łączenie za pośrednictwem dołączonej tabeli.

> [!NOTE]
>  Parametry połączenia służą do przekazywania dodatkowych informacji do ODBC i niektórych sterowników ISAM zgodnie z wymaganiami. Nie jest on używany w programie. Bazy danych MDB. W przypadku tabel bazowych bazy danych Microsoft Jet parametry połączenia są pustym ciągiem (""), z wyjątkiem sytuacji, w których jest używana do zapytania przekazującego SQL, zgodnie z opisem w sekcji wartość zwracana powyżej.

Aby uzyskać opis sposobu tworzenia parametrów połączenia, zobacz Funkcja [Open](#open) member. Po ustawieniu parametrów połączenia w `Open` wywołaniu można użyć jej później do sprawdzenia ustawienia w celu określenia typu, ścieżki, identyfikatora użytkownika, hasła lub źródła danych ODBC bazy danych.

##  <a name="getname"></a>CDaoDatabase:: GetName

Wywołaj tę funkcję elementu członkowskiego, aby pobrać nazwę aktualnie otwartej bazy danych, która jest nazwą istniejącego pliku bazy danych lub nazwą zarejestrowanego źródła danych ODBC.

```
CString GetName();
```

### <a name="return-value"></a>Wartość zwracana

Pełna ścieżka i nazwa pliku bazy danych, jeśli to się powiedzie; w przeciwnym razie pusty [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Uwagi

Jeśli sieć obsługuje ujednolicone konwencje nazewnictwa (UNC), można również określić ścieżkę sieciową — na przykład "\\\\\\\\\MYSERVER\\\MYSHARE \mydir\\\MYDB. MDB ". (W literałach ciągu są wymagane podwójne ukośniki odwrotne,\\ C++ ponieważ "" jest znakiem ucieczki).

Możesz na przykład wyświetlić tę nazwę w nagłówku. Jeśli wystąpi błąd podczas pobierania nazwy, MFC zgłasza wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

> [!NOTE]
>  W celu uzyskania lepszej wydajności w przypadku uzyskiwania dostępu do zewnętrznych baz danych zaleca się dołączenie zewnętrznych tabel bazy danych do bazy danych Microsoft Jet (. MDB) zamiast bezpośredniego połączenia ze źródłem danych.

Typ bazy danych jest wskazywany przez plik lub katalog, do którego odwołuje się ścieżka, w następujący sposób:

|Nazwa ścieżki wskazuje..|Typ bazy danych|
|--------------------------|-------------------|
|. Plik MDB|Baza danych Microsoft Jet (Microsoft Access)|
|Katalog, który zawiera. Pliki DBF|Baza danych programu dBASE|
|Katalog, który zawiera. Plik XLS|Baza danych programu Microsoft Excel|
|Katalog, który zawiera. Pliki PDX|Baza danych programu Paradox|
|Katalog zawierający odpowiednio sformatowane pliki bazy danych tekstowych|Baza danych formatu tekstowego|

W przypadku baz danych ODBC, takich jak SQL Server i Oracle, parametry połączenia bazy danych identyfikują nazwę źródła danych (DSN), która jest zarejestrowana przez ODBC.

##  <a name="getquerydefcount"></a>CDaoDatabase::GetQueryDefCount

Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę zapytań zdefiniowanych w kolekcji QueryDefs bazy danych.

```
short GetQueryDefCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba zapytań zdefiniowanych w bazie danych.

### <a name="remarks"></a>Uwagi

`GetQueryDefCount`jest przydatne, jeśli trzeba przepętlać przez wszystkie querydefy w kolekcji QueryDefs. Aby uzyskać informacje na temat danego zapytania w kolekcji, zobacz [GetQueryDefInfo](#getquerydefinfo).

##  <a name="getquerydefinfo"></a>CDaoDatabase::GetQueryDefInfo

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać różne rodzaje informacji o zapytaniu zdefiniowanym w bazie danych.

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
Indeks wstępnie zdefiniowanego zapytania w kolekcji QueryDefs bazy danych dla wyszukiwania według indeksu.

*querydefinfo*<br/>
Odwołanie do obiektu [CDaoQueryDefInfo —](../../mfc/reference/cdaoquerydefinfo-structure.md) , który zwraca żądane informacje.

*dwInfoOptions*<br/>
Opcje określające, które informacje o zestawie rekordów mają być pobierane. Dostępne opcje są wymienione w tym miejscu wraz z tym, co powodują, że funkcja zwraca informacje o zestawie rekordów:

- AFX_DAO_PRIMARY_INFO (domyślnie) nazwa, typ

- AFX_DAO_SECONDARY_INFO podstawowe informacje plus: Data utworzenia, Data ostatniej aktualizacji, zwraca rekordy, aktualizowalne

- AFX_DAO_ALL_INFO informacje podstawowe i pomocnicze oraz: SQL, Connect, ODBCTimeout

*lpszName*<br/>
Ciąg zawierający nazwę zapytania zdefiniowanego w bazie danych dla wyszukiwania według nazwy.

### <a name="remarks"></a>Uwagi

Podano dwie wersje funkcji, aby można było wybrać zapytanie według indeksu w kolekcji QueryDefs bazy danych lub według nazwy zapytania.

Aby uzyskać opis informacji zwracanych w *querydefinfo*, zobacz [CDaoQueryDefInfo —](../../mfc/reference/cdaoquerydefinfo-structure.md) Structure. Ta struktura zawiera elementy członkowskie, które odpowiadają elementom informacji wymienionych powyżej w opisie *dwInfoOptions*. Jeśli zażądasz jednego poziomu informacji, uzyskasz również informacje o wcześniejszych poziomach.

##  <a name="getquerytimeout"></a>CDaoDatabase::GetQueryTimeout

Wywołaj tę funkcję elementu członkowskiego, aby pobrać bieżącą liczbę sekund, która ma być dozwolona przed upływem limitu czasu dla kolejnych operacji w połączonej bazie danych.

```
short GetQueryTimeout();
```

### <a name="return-value"></a>Wartość zwracana

Krótka liczba całkowita zawierająca wartość limitu czasu (w sekundach).

### <a name="remarks"></a>Uwagi

Operacja może przekroczyć limit czasu, ponieważ występują problemy z dostępem do sieci, nadmierny czas przetwarzania zapytania i tak dalej. To ustawienie ma wpływ na wszystkie operacje otwierania, dodawania nowych, aktualizacji i usuwania na wszystkich zestawach rekordów skojarzonych z tym `CDaoDatabase` obiektem. Bieżące ustawienie limitu czasu można zmienić, wywołując [SetQueryTimeout](#setquerytimeout). Zmiana wartości limitu czasu zapytania dla zestawu rekordów po otwarciu nie powoduje zmiany wartości zestawu rekordów. Na przykład kolejne operacje [przenoszenia](../../mfc/reference/cdaorecordset-class.md#move) nie używają nowej wartości. Wartość domyślna jest początkowo ustawiana podczas inicjowania aparatu bazy danych.

Wartość domyślna dla limitów czasu zapytania jest pobierana z rejestru systemu Windows. Jeśli nie ma ustawienia rejestru, wartość domyślna to 60 sekund. Nie wszystkie bazy danych obsługują możliwość ustawiania wartości limitu czasu zapytania. Jeśli ustawisz wartość limitu czasu zapytania równy 0, nie zostanie przekroczony limit czasu. i komunikacja z bazą danych może przestać odpowiadać. Takie zachowanie może być przydatne podczas opracowywania. Jeśli wywołanie nie powiedzie się, MFC zgłosi wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

Aby uzyskać powiązane informacje, zobacz temat "Właściwość QueryTimeout" w pomocy DAO.

##  <a name="getrecordsaffected"></a>CDaoDatabase::GetRecordsAffected

Wywołaj tę funkcję elementu członkowskiego, aby określić liczbę rekordów, na które ma wpływ ostatnie wywołanie funkcji [Execute](#execute) member.

```
long GetRecordsAffected();
```

### <a name="return-value"></a>Wartość zwracana

Długa liczba całkowita zawierająca liczbę rekordów, których to dotyczy.

### <a name="remarks"></a>Uwagi

Zwracana wartość obejmuje liczbę rekordów usuniętych, zaktualizowanych lub wstawianych przez zapytanie akcji z `Execute`. Zwracana liczba nie będzie odzwierciedlać zmian w powiązanych tabelach, gdy są włączone kaskadowe aktualizacje lub usunięcia.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość RecordsAffected" w pomocy DAO.

##  <a name="getrelationcount"></a>CDaoDatabase::GetRelationCount

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać liczbę relacji zdefiniowanych między tabelami w bazie danych.

```
short GetRelationCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba relacji zdefiniowanych między tabelami w bazie danych.

### <a name="remarks"></a>Uwagi

`GetRelationCount`jest przydatne, jeśli musisz zapętlać się przez wszystkie zdefiniowane relacje w kolekcji relacji między bazami danych. Aby uzyskać informacje o danej relacji w kolekcji, zobacz [GetRelationInfo](#getrelationinfo).

Aby zilustrować koncepcję relacji, należy wziąć pod uwagę tabelę dostawcy i tabelę Products, która może mieć relację jeden do wielu. W tej relacji jeden dostawca może dostarczyć więcej niż jeden produkt. Inne relacje to jeden-do-jednego i wiele-do-wielu.

##  <a name="getrelationinfo"></a>CDaoDatabase::GetRelationInfo

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać informacje o określonej relacji w kolekcji relacji bazy danych.

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
Indeks obiektu relacji w kolekcji relacji bazy danych dla wyszukiwania według indeksu.

*relinfo*<br/>
Odwołanie do obiektu [CDaoRelationInfo —](../../mfc/reference/cdaorelationinfo-structure.md) , który zwraca żądane informacje.

*dwInfoOptions*<br/>
Opcje określające, które informacje o relacji mają być pobierane. Dostępne opcje są wymienione w tym miejscu wraz z tym, co powodują, że funkcja zwraca informacje o relacji:

- AFX_DAO_PRIMARY_INFO (domyślnie) nazwa, tabela, Tabela obca

- AFX_DAO_SECONDARY_INFO — atrybuty, informacje o polach

Informacje pola to obiekt [CDaoRelationFieldInfo —](../../mfc/reference/cdaorelationfieldinfo-structure.md) zawierający pola z tabeli podstawowej, w której znajduje się relacja.

*lpszName*<br/>
Ciąg zawierający nazwę obiektu relacji dla wyszukiwania według nazwy.

### <a name="remarks"></a>Uwagi

Dwie wersje tej funkcji zapewniają dostęp przez indeks lub według nazwy. Aby uzyskać opis informacji zwracanych w *relinfo*, zobacz [CDaoRelationInfo —](../../mfc/reference/cdaorelationinfo-structure.md) Structure. Ta struktura zawiera elementy członkowskie, które odpowiadają elementom informacji wymienionych powyżej w opisie *dwInfoOptions*. Jeśli zażądasz informacji na jednym poziomie, możesz również uzyskać informacje na wszystkich wcześniejszych poziomach.

> [!NOTE]
>  Jeśli ustawisz atrybuty obiektu relacji w celu aktywowania operacji kaskadowych`dbRelationUpdateCascades` ( `dbRelationDeleteCascades`lub), aparat bazy danych Microsoft Jet automatycznie zaktualizuje lub usunie rekordy w jednej lub kilku innych tabelach po wprowadzeniu zmian do pokrewnego klucza podstawowego tabelę. Załóżmy na przykład, że ustanawiasz relację usuwania kaskadowego między tabelą Klienci a tabelą Orders. Po usunięciu rekordów z tabeli Customers rekordy w tabeli Orders powiązanej z tym klientem również zostaną usunięte. Ponadto, jeśli ustanawiasz kaskadowe relacje usuwania między tabelą Orders i innymi tabelami, rekordy z tych tabel są automatycznie usuwane po usunięciu rekordów z tabeli Customers.

##  <a name="gettabledefcount"></a>CDaoDatabase::GetTableDefCount

Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę tabel zdefiniowanych w bazie danych.

```
short GetTableDefCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba TableDefs zdefiniowanych w bazie danych.

### <a name="remarks"></a>Uwagi

`GetTableDefCount`jest przydatne, jeśli trzeba przepętlać przez wszystkie tabledefs w kolekcji TableDefs bazy danych. Aby uzyskać informacje o danej tabeli w kolekcji, zobacz [GetTableDefInfo](#gettabledefinfo).

##  <a name="gettabledefinfo"></a>CDaoDatabase::GetTableDefInfo

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać różne rodzaje informacji o tabeli zdefiniowanej w bazie danych.

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
Indeks obiektu tabledef w kolekcji TableDefs bazy danych dla wyszukiwania według indeksu.

*tabledefinfo*<br/>
Odwołanie do obiektu [CDaoTableDefInfo —](../../mfc/reference/cdaotabledefinfo-structure.md) , który zwraca żądane informacje.

*dwInfoOptions*<br/>
Opcje określające, które informacje o tabeli mają być pobierane. Dostępne opcje są wymienione w tym miejscu wraz z tym, co powodują, że funkcja zwraca informacje o relacji:

- AFX_DAO_PRIMARY_INFO (domyślnie): nazwa, aktualizowalna, atrybuty

- AFX_DAO_SECONDARY_INFO podstawowe informacje plus: Data utworzenia, Data ostatniej aktualizacji, nazwa tabeli źródłowej, połączenie

- AFX_DAO_ALL_INFO informacje podstawowe i pomocnicze oraz: Reguła walidacji, tekst walidacji, liczba rekordów

*lpszName*<br/>
Nazwa obiektu tabledef dla wyszukiwania według nazwy.

### <a name="remarks"></a>Uwagi

Podano dwie wersje funkcji, aby można było wybrać tabelę według indeksu w kolekcji TableDefs bazy danych lub według nazwy tabeli.

Aby uzyskać opis informacji zwracanych w *tabledefinfo*, zobacz [CDaoTableDefInfo —](../../mfc/reference/cdaotabledefinfo-structure.md) Structure. Ta struktura zawiera elementy członkowskie, które odpowiadają elementom informacji wymienionych powyżej w opisie *dwInfoOptions*. Jeśli zażądasz informacji na jednym poziomie, uzyskasz również informacje na temat wszystkich wcześniejszych poziomów.

> [!NOTE]
>  Opcja AFX_DAO_ALL_INFO zawiera informacje, które mogą być wolne do uzyskania. W takim przypadku liczenie rekordów w tabeli może być bardzo czasochłonne, jeśli istnieje wiele rekordów.

##  <a name="getversion"></a>CDaoDatabase:: GetVersion

Wywołaj tę funkcję elementu członkowskiego, aby określić wersję pliku bazy danych Microsoft Jet.

```
CString GetVersion();
```

### <a name="return-value"></a>Wartość zwracana

Element [CString](../../atl-mfc-shared/reference/cstringt-class.md) , który wskazuje wersję pliku bazy danych skojarzoną z obiektem.

### <a name="remarks"></a>Uwagi

Zwracana wartość reprezentuje numer wersji w postaci "główna. pomocnicza"; na przykład "3,0". Numer wersji produktu (na przykład 3,0) składa się z numeru wersji (3), kropki i numeru wydania (0). Wersje do dnia są 1,0, 1,1, 2,0 i 3,0.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość wersji" w pomocy DAO.

##  <a name="isopen"></a>CDaoDatabase:: IsOpen

Wywołaj tę funkcję elementu członkowskiego, `CDaoDatabase` aby określić, czy obiekt jest aktualnie otwarty w bazie danych.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli `CDaoDatabase` obiekt jest aktualnie otwarty; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

##  <a name="m_pdaodatabase"></a>CDaoDatabase::m_pDAODatabase

Zawiera wskaźnik do interfejsu OLE dla obiektu bazy danych DAO bazowego `CDaoDatabase` obiektu.

### <a name="remarks"></a>Uwagi

Użyj tego wskaźnika, jeśli musisz bezpośrednio uzyskać dostęp do interfejsu DAO.

Aby uzyskać informacje dotyczące bezpośredniego wywoływania obiektów DAO, zobacz [Uwagi techniczne 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

##  <a name="m_pworkspace"></a>  CDaoDatabase::m_pWorkspace

Zawiera wskaźnik do obiektu [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) , który zawiera obiekt bazy danych.

### <a name="remarks"></a>Uwagi

Użyj tego wskaźnika, jeśli chcesz uzyskać bezpośredni dostęp do obszaru roboczego — na przykład, aby uzyskać wskaźniki do innych obiektów bazy danych w kolekcji baz danych obszaru roboczego.

##  <a name="open"></a>CDaoDatabase:: Open

Należy wywołać tę funkcję elementu członkowskiego, aby zainicjować nowo `CDaoDatabase` skonstruowany obiekt, który reprezentuje istniejącą bazę danych.

```
virtual void Open(
    LPCTSTR lpszName,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T(""));
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Wyrażenie ciągu, który jest nazwą istniejącego aparatu Microsoft Jet (. MDB) plik bazy danych. Jeśli nazwa pliku ma rozszerzenie, jest to wymagane. Jeśli sieć obsługuje ujednolicone konwencje nazewnictwa (UNC), można również określić ścieżkę sieciową, taką jak "\\\\\\\\\MYSERVER\\\MYSHARE\\\mydir \MYDB. MDB ". (W literałach ciągu są wymagane podwójne ukośniki odwrotne,\\ C++ ponieważ "" jest znakiem ucieczki).

W przypadku korzystania z programu *lpszName*należy wziąć pod uwagę pewne zagadnienia. Jeśli:

- Odwołuje się do bazy danych, która jest już otwarta do wyłącznego dostępu przez innego użytkownika, MFC zgłasza wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md). Zalewka tego wyjątku pozwala użytkownikowi wiedzieć, że baza danych jest niedostępna.

- Jest ciągiem pustym ("") i *lpszConnect* jest "ODBC;", zostanie wyświetlone okno dialogowe z listą wszystkich zarejestrowanych nazw źródeł danych ODBC, aby użytkownik mógł wybrać bazę danych. Należy unikać bezpośrednich połączeń ze źródłami danych ODBC; Zamiast tego użyj dołączonej tabeli.

- W przeciwnym razie nie odwołuje się do istniejącej bazy danych lub prawidłowej nazwy źródła danych ODBC, MFC zgłasza `CDaoException`wyjątek typu.

> [!NOTE]
>  Aby uzyskać szczegółowe informacje na temat kodów błędów DAO, zobacz DAOERR. Plik H. Aby uzyskać powiązane informacje, zobacz temat "błędy dostępu do danych z pułapkami" w pomocy programu DAO.

*bExclusive*<br/>
Wartość logiczna prawda, jeśli baza danych ma zostać otwarta dla wyłącznego (nieudostępnionego) i FAŁSZ, jeśli baza danych ma zostać otwarta dla dostępu współdzielonego. Jeśli pominięto ten argument, baza danych zostanie otwarta dla dostępu współdzielonego.

*bReadOnly*<br/>
Wartość logiczna prawda, jeśli baza danych ma być otwierana w trybie tylko do odczytu, a wartość FALSE, jeśli baza danych ma być otwarta do odczytu i zapisu. Jeśli pominięto ten argument, baza danych zostanie otwarta na potrzeby dostępu do odczytu i zapisu. Wszystkie zależne zestawy rekordów dziedziczą ten atrybut.

*lpszConnect*<br/>
Wyrażenie ciągu używane do otwierania bazy danych. Ten ciąg stanowi argumenty połączenia ODBC. Należy podać argumenty wyłączne i tylko do odczytu w celu dostarczenia ciągu źródłowego. Jeśli baza danych jest bazą danych programu Microsoft Jet (. MDB), ten ciąg jest pusty (""). Składnia wartości domyślnej — **_T**("") — oferuje przenośność dla standardu Unicode oraz kompilacje ANSI aplikacji.

### <a name="remarks"></a>Uwagi

`Open`kojarzy bazę danych z podstawowym obiektem DAO. Nie można użyć obiektu bazy danych do konstruowania obiektów zestawu rekordów, tabledef lub querydef do momentu jego zainicjowania. `Open`dołącza obiekt bazy danych do kolekcji baz danych skojarzonego obszaru roboczego.

Użyj parametrów w następujący sposób:

- W przypadku otwierania programu Microsoft Jet (. MDB), użyj parametru *lpszName* i przekaż pusty ciąg dla parametru *lpszConnect* lub Przekaż ciąg hasła w postaci "; PWD = Password ", jeśli baza danych jest chroniona hasłem (. Tylko bazy danych MDB).

- W przypadku otwierania źródła danych ODBC Przekaż prawidłowe parametry połączenia ODBC w *lpszConnect* i pusty ciąg w *lpszName*.

Aby uzyskać powiązane informacje, zobacz temat "Metoda OpenDatabase" w pomocy DAO.

> [!NOTE]
>  W celu uzyskania lepszej wydajności podczas uzyskiwania dostępu do zewnętrznych baz danych, w tym baz danych ISAM i źródeł danych ODBC, zaleca się dołączenie zewnętrznych tabel bazy danych do bazy danych aparatu Microsoft Jet (. MDB) zamiast bezpośredniego połączenia ze źródłem danych.

W przypadku próby nawiązania połączenia w celu przekroczenia limitu czasu, jeśli na przykład Host systemu DBMS jest niedostępny. Jeśli próba połączenia nie powiedzie `Open` się, program zgłosi wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

Pozostałe uwagi dotyczą tylko baz danych ODBC:

Jeśli baza danych jest bazą danych ODBC, a parametry w `Open` wywołaniu nie zawierają wystarczającej ilości informacji do nawiązania połączenia, sterownik ODBC otwiera okno dialogowe umożliwiające uzyskanie niezbędnych informacji od użytkownika. Po wywołaniu `Open`parametry połączenia, *lpszConnect*, są przechowywane prywatnie i są dostępne przez wywołanie funkcji składowej [GetConnect](#getconnect) .

Jeśli chcesz, możesz otworzyć własne okno dialogowe przed wywołaniem `Open` , aby uzyskać informacje od użytkownika, takie jak hasło, a następnie dodać te informacje do parametrów połączenia, które są `Open`przekazywane. Można też zapisać parametry połączenia, które zostały przekazane (prawdopodobnie w rejestrze systemu Windows), aby można było użyć go ponownie podczas następnego wywołania `Open` aplikacji `CDaoDatabase` na obiekcie.

Można również użyć parametrów połączenia dla wielu poziomów autoryzacji logowania (dla różnych `CDaoDatabase` obiektów) lub przekazać inne informacje specyficzne dla bazy danych.

##  <a name="setquerytimeout"></a>CDaoDatabase::SetQueryTimeout

Wywołaj tę funkcję elementu członkowskiego, aby zastąpić domyślną liczbę sekund dozwoloną przed upływem limitu czasu dla kolejnych operacji w połączonej bazie danych.

```
void SetQueryTimeout(short nSeconds);
```

### <a name="parameters"></a>Parametry

*nSeconds*<br/>
Liczba sekund, które mają być dozwolone przed upływem limitu czasu zapytania.

### <a name="remarks"></a>Uwagi

Operacja może przekroczyć limit czasu, ponieważ występują problemy z dostępem do sieci, nadmierny czas przetwarzania zapytania i tak dalej. Wywołaj `SetQueryTimeout` przed otwarciem zestawu rekordów lub przed wywołaniem funkcji [AddNew](../../mfc/reference/cdaorecordset-class.md#addnew), [Update](../../mfc/reference/cdaorecordset-class.md#update)lub [delete](../../mfc/reference/cdaorecordset-class.md#delete) elementu członkowskiego zestawu rekordów, jeśli chcesz zmienić wartość limitu czasu zapytania. Ustawienie ma wpływ na wszystkie [](../../mfc/reference/cdaorecordset-class.md#open)kolejne otwarte `AddNew`, `Update`, i `Delete` wywołania do dowolnego zestawu rekordów skojarzonego z tym `CDaoDatabase` obiektem. Zmiana wartości limitu czasu zapytania dla zestawu rekordów po otwarciu nie powoduje zmiany wartości zestawu rekordów. Na przykład kolejne operacje [przenoszenia](../../mfc/reference/cdaorecordset-class.md#move) nie używają nowej wartości.

Wartość domyślna dla limitów czasu zapytania to 60 sekund. Nie wszystkie bazy danych obsługują możliwość ustawiania wartości limitu czasu zapytania. Jeśli ustawisz wartość limitu czasu zapytania równy 0, nie zostanie przekroczony limit czasu. Komunikacja z bazą danych może przestać odpowiadać. Takie zachowanie może być przydatne podczas opracowywania.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość QueryTimeout" w pomocy DAO.

## <a name="see-also"></a>Zobacz także

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)<br/>
[Klasa CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)<br/>
[Klasa CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)<br/>
[Klasa CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)<br/>
[Klasa CDatabase](../../mfc/reference/cdatabase-class.md)<br/>
[Klasa CDaoException](../../mfc/reference/cdaoexception-class.md)
