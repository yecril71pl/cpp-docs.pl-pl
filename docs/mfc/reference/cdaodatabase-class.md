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
ms.openlocfilehash: debba137878da49921df83da7630003a7d62db2f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369018"
---
# <a name="cdaodatabase-class"></a>Klasa CDaoDatabase

Reprezentuje połączenie z bazą danych programu Access przy użyciu obiektów dostępu do danych (DAO). DAO jest obsługiwany przez pakiet Office 2013. DAO 3.6 jest ostateczną wersją i jest uważana za przestarzałą.

## <a name="syntax"></a>Składnia

```
class CDaoDatabase : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoDatabase::CDaoDatabase](#cdaodatabase)|Konstruuje `CDaoDatabase` obiekt. Wywołanie, `Open` aby połączyć obiekt z bazą danych.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoDatabase::CanTransact](#cantransact)|Zwraca wartość niezerową, jeśli baza danych obsługuje transakcje.|
|[Baza danych CDDaoDatabase::CanUpdate](#canupdate)|Zwraca wartość niezerową, `CDaoDatabase` jeśli obiekt jest aktualizowany (nie tylko do odczytu).|
|[Baza danych CDDaoDatabase::Zamknij](#close)|Zamyka połączenie z bazą danych.|
|[Baza danych CDDaoDatabase::Tworzenie](#create)|Tworzy podstawowy obiekt bazy danych DAO `CDaoDatabase` i inicjuje obiekt.|
|[Baza danych CDDaoDatabase::CreateRelation](#createrelation)|Definiuje nową relację między tabelami w bazie danych.|
|[CDaoDatabase::DeleteQueryDef](#deletequerydef)|Usuwa obiekt querydef zapisany w kolekcji QueryDefs bazy danych.|
|[CDaoDatabase::DeleteRelation](#deleterelation)|Usuwa istniejącą relację między tabelami w bazie danych.|
|[CDaoDatabase::DeleteTableDef](#deletetabledef)|Usuwa definicję tabeli w bazie danych. Spowoduje to usunięcie rzeczywistej tabeli i wszystkich jej danych.|
|[Baza danych CDDaoDatabase::Wykonanie](#execute)|Wykonuje kwerendę akcji. Wywołanie `Execute` kwerendy, która zwraca wyniki zgłasza wyjątek.|
|[Baza danych CDDaoDatabase::GetConnect](#getconnect)|Zwraca ciąg połączenia używany `CDaoDatabase` do łączenia obiektu z bazą danych. Używany do ODBC.|
|[Baza danych CDDaoDatabase::GetName](#getname)|Zwraca nazwę aktualnie używanej bazy danych.|
|[CDaoDatabase::GetQueryDefCount](#getquerydefcount)|Zwraca liczbę zapytań zdefiniowanych dla bazy danych.|
|[Baza danych CDDaoDatabase::GetQueryDefInfo](#getquerydefinfo)|Zwraca informacje o określonej kwerendzie zdefiniowanej w bazie danych.|
|[CDaoDatabase::GetQueryTimeout](#getquerytimeout)|Zwraca liczbę sekund, po których operacje kwerendy bazy danych upończe limit czasu. Wpływa na wszystkie kolejne operacje otwierania, dodawania nowych, aktualizacji i edycji oraz `Execute` inne operacje na źródłach danych ODBC (tylko) takie jak wywołania.|
|[CDaoDatabase::GetRecordsAffected](#getrecordsaffected)|Zwraca liczbę rekordów, których dotyczy ostatnia aktualizacja, edycja lub `Execute`dodanie operacji lub wywołanie .|
|[Baza danych CDDaoDatabase::GetRelationCount](#getrelationcount)|Zwraca liczbę relacji zdefiniowanych między tabelami w bazie danych.|
|[Baza danych CDDaoDatabase::GetRelationInfo](#getrelationinfo)|Zwraca informacje o określonej relacji zdefiniowanej między tabelami w bazie danych.|
|[Baza danych CDDaoDatabase::GetTableDefCount](#gettabledefcount)|Zwraca liczbę tabel zdefiniowanych w bazie danych.|
|[Baza danych CDDaoDatabase::GetTableDefInfo](#gettabledefinfo)|Zwraca informacje o określonej tabeli w bazie danych.|
|[Baza danych CDDaoDatabase::GetVersion](#getversion)|Zwraca wersję aparatu bazy danych skojarzoną z bazą danych.|
|[CDaoDatabase::IsOpen](#isopen)|Zwraca wartość niezerową, `CDaoDatabase` jeśli obiekt jest aktualnie połączony z bazą danych.|
|[Baza danych CDDaoDatabase::Otwórz](#open)|Ustanawia połączenie z bazą danych.|
|[CDaoDatabase::SetQueryTimeout](#setquerytimeout)|Ustawia liczbę sekund, po których operacje kwerendy bazy danych (tylko na źródłach danych ODBC) upochnie. Wpływa na wszystkie kolejne operacje otwierania, dodawania nowych, aktualizacji i usuwania.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[Baza danych CDDaoDatabase::m_pDAODatabase](#m_pdaodatabase)|Wskaźnik do bazowego obiektu bazy danych DAO.|
|[Baza danych CDDaoDatabase::m_pWorkspace](#m_pworkspace)|Wskaźnik do obiektu [CDaoWorkspace,](../../mfc/reference/cdaoworkspace-class.md) który zawiera bazę danych i definiuje jego przestrzeń transakcji.|

## <a name="remarks"></a>Uwagi

Aby uzyskać informacje na temat obsługiwanych formatów bazy danych, zobacz funkcję elementu członkowskiego [GetName.](../../mfc/reference/cdaoworkspace-class.md#getname) W danym "obszarze `CDaoDatabase` roboczym", reprezentowanym przez obiekt [CDaoWorkspace,](../../mfc/reference/cdaoworkspace-class.md) można mieć jeden lub więcej obiektów aktywnych naraz. Obszar roboczy przechowuje kolekcję obiektów otwartej bazy danych, o nazwie Databases kolekcji.

## <a name="usage"></a>Sposób użycia

Obiekty bazy danych można tworzyć niejawnie podczas tworzenia obiektów zawierającego rekordy. Ale można również jawnie tworzyć obiekty bazy danych. Aby użyć istniejącej bazy `CDaoDatabase`danych jawnie z , wykonaj jedną z następujących czynności:

- Konstruuj `CDaoDatabase` obiekt, przekazując wskaźnik do otwartego obiektu [CDaoWorkspace.](../../mfc/reference/cdaoworkspace-class.md)

- Lub skonstruować `CDaoDatabase` obiekt bez określania obszaru roboczego (MFC tworzy tymczasowy obiekt obszaru roboczego).

Aby utworzyć nowy microsoft jet (. baza danych MDB), `CDaoDatabase` konstruuj obiekt i wywołaj jego funkcję [Create](#create) member. *Nie* `Open` dzwonić `Create`po .

Aby otworzyć istniejącą bazę danych, skonstruuj `CDaoDatabase` obiekt i wywołaj jego funkcję [otwórz](#open) element członkowski.

Każda z tych technik dołącza obiekt bazy danych DAO do kolekcji bazy danych obszaru roboczego i otwiera połączenie z danymi. Podczas konstruowania [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)lub [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) obiektów do pracy w połączonej bazie `CDaoDatabase` danych, przekazać konstruktorów dla tych obiektów wskaźnik do obiektu. Po zakończeniu korzystania z połączenia, wywołać [Zamknij](#close) element członkowski funkcji i zniszczyć `CDaoDatabase` obiekt. `Close`zamyka wszystkie zestawy rekordów, które nie zostały wcześniej zamknięte.

## <a name="transactions"></a>Transakcje

Przetwarzanie transakcji bazy danych jest dostarczane na poziomie obszaru roboczego — zobacz [BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans), [CommitTrans](../../mfc/reference/cdaoworkspace-class.md#committrans)i [Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback) funkcji członkowskich klasy `CDaoWorkspace`.

## <a name="odbc-connections"></a>Połączenia ODBC

Zalecanym sposobem pracy ze źródłami danych ODBC jest dołączenie tabel zewnętrznych do programu Microsoft Jet (. bazy danych MDB).

## <a name="collections"></a>Kolekcje

Każda baza danych przechowuje własne kolekcje tabledef, querydef, recordset i relation obiektów. Klasa `CDaoDatabase` dostarcza funkcje członkowskie do manipulowania tymi obiektami.

> [!NOTE]
> Obiekty są przechowywane w DAO, a nie w obiekcie bazy danych MFC. MFC dostarcza klasy dla obiektów tabledef, querydef i recordset, ale nie dla obiektów relacji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CDaoDatabase`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="cdaodatabasecantransact"></a><a name="cantransact"></a>CDaoDatabase::CanTransact

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy baza danych zezwala na transakcje.

```
BOOL CanTransact();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli baza danych obsługuje transakcje; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Transakcje są zarządzane w obszarze roboczym bazy danych.

## <a name="cdaodatabasecanupdate"></a><a name="canupdate"></a>Baza danych CDDaoDatabase::CanUpdate

Wywołanie tej funkcji elementu `CDaoDatabase` członkowskiego, aby ustalić, czy obiekt zezwala na aktualizacje.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, `CDaoDatabase` jeśli obiekt zezwala na aktualizacje; w przeciwnym razie 0, wskazując, że przeszedł true w `CDaoDatabase` *bCzytylko* podczas otwarcia obiektu lub że sama baza danych jest tylko do odczytu. Zobacz funkcję [Otwórz](#open) element członkowski.

### <a name="remarks"></a>Uwagi

Aby uzyskać informacje na temat możliwości aktualizacji bazy danych, zobacz temat "Właściwości aktuiwalne" w Pomocy DAO.

## <a name="cdaodatabasecdaodatabase"></a><a name="cdaodatabase"></a>CDaoDatabase::CDaoDatabase

Konstruuje `CDaoDatabase` obiekt.

```
CDaoDatabase(CDaoWorkspace* pWorkspace = NULL);
```

### <a name="parameters"></a>Parametry

*pPrzestrzeń robocza*<br/>
Wskaźnik do `CDaoWorkspace` obiektu, który będzie zawierał nowy obiekt bazy danych. Jeśli zaakceptujesz domyślną wartość NULL, konstruktor utworzy obiekt tymczasowy, `CDaoWorkspace` który używa domyślnego obszaru roboczego DAO. Wskaźnik do obiektu obszaru roboczego można uzyskać za pośrednictwem [m_pWorkspace](#m_pworkspace) elementu członkowskiego danych.

### <a name="remarks"></a>Uwagi

Po skonstruowaniu obiektu, jeśli tworzysz nowy Microsoft Jet (. baza danych MDB), wywołaj funkcję [create](#create) elementu członkowskiego obiektu. Jeśli zamiast tego otwierasz istniejącą bazę danych, należy wywołać funkcję [elementu członkowskiego Open](#open) obiektu.

Po zakończeniu z obiektu, należy wywołać jego [Close](#close) `CDaoDatabase` funkcji elementu członkowskiego, a następnie zniszczyć obiekt.

Zagoscjenie obiektu w `CDaoDatabase` klasie dokumentu może okazać się wygodne.

> [!NOTE]
> Obiekt `CDaoDatabase` jest również tworzony niejawnie, jeśli otworzysz obiekt [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) bez przekazywania wskaźnika do istniejącego `CDaoDatabase` obiektu. Ten obiekt bazy danych jest zamykany po zamknięciu obiektu pliku recordset.

## <a name="cdaodatabaseclose"></a><a name="close"></a>Baza danych CDDaoDatabase::Zamknij

Wywołanie tej funkcji elementu członkowskiego, aby odłączyć się od bazy danych i zamknąć wszystkie otwarte zestawy rekordów, tabledefs i querydefs skojarzone z bazą danych.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Jest dobrą praktyką, aby zamknąć te obiekty samodzielnie przed wywołaniem tej funkcji elementu członkowskiego. Zamknięcie `CDaoDatabase` obiektu powoduje usunięcie go z kolekcji Bazy danych w skojarzonym [obszarze roboczym](../../mfc/reference/cdaoworkspace-class.md). Ponieważ `Close` nie niszczy `CDaoDatabase` obiektu, można ponownie użyć obiektu, otwierając tę samą bazę danych lub inną bazę danych.

> [!CAUTION]
> Wywołanie [Update](../../mfc/reference/cdaorecordset-class.md#update) update funkcji elementu członkowskiego (jeśli są `Close` oczekujące zmiany) i funkcji elementu członkowskiego na wszystkich otwartych obiektów aktujmów przed zamknięciem bazy danych. Po zamknięciu funkcji, która deklaruje [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) lub `CDaoDatabase` obiektów na stosie, baza danych jest zamknięta, wszelkie niezapisane zmiany zostaną utracone, wszystkie oczekujące transakcje są przywracane, a wszelkie oczekujące zmiany do danych zostaną utracone.

> [!CAUTION]
> Jeśli spróbujesz zamknąć obiekt bazy danych, gdy wszystkie obiekty pliku recordset są otwarte lub jeśli spróbujesz zamknąć obiekt obszaru roboczego, gdy wszystkie obiekty bazy danych należące do tego określonego obszaru roboczego są otwarte, te obiekty wakusu będą zamknięte, a wszelkie oczekujące aktualizacje lub zmiany zostaną wycofane. Jeśli spróbujesz zamknąć obiekt obszaru roboczego, gdy wszystkie obiekty bazy danych należące do niego są otwarte, operacja zamyka wszystkie obiekty bazy danych należące do tego określonego obiektu obszaru roboczego, co może spowodować zamknięcie niezamkniętych obiektów zestawów rekordów. Jeśli obiekt bazy danych nie zostanie zamknięty, MFC zgłasza błąd potwierdzenia w kompilacjach debugowania.

Jeśli obiekt bazy danych jest zdefiniowany poza zakresem funkcji i zakończysz działanie funkcji bez zamykania, obiekt bazy danych pozostanie otwarty, dopóki jawnie zamknięty lub moduł, w którym jest zdefiniowany, jest poza zakresem.

## <a name="cdaodatabasecreate"></a><a name="create"></a>Baza danych CDDaoDatabase::Tworzenie

Aby utworzyć nowy microsoft jet (. Baza danych MDB), wywołaj tę `CDaoDatabase` funkcję elementu członkowskiego po skonstruowaniu obiektu.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int dwOptions = 0);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
Wyrażenie ciągu, które jest nazwą pliku bazy danych, który tworzysz. Może to być pełna ścieżka i nazwa pliku,\\takie jak "C: \MYDB. MDB". Należy podać nazwę. Jeśli nie podasz rozszerzenia nazwy pliku, . MDB jest dołączany. Jeśli sieć obsługuje jednolitą konwencję nazewnictwa (UNC), można również\\\\\\określić\\ścieżkę\\sieciową,\\taką jak " \MYSERVER \MYSHARE \MYDIR \MYDB". Tylko Microsoft Jet (. Pliki bazy danych MDB) można tworzyć za pomocą tej funkcji członkowskiej. (Podwójne ukośniki odwrotne są wymagane w\\literałach ciągów, ponieważ " " jest znakiem ucieczki języka C++).

*lpszLocale (lpszLocale)*<br/>
Wyrażenie ciągu używane do określania kolejności sortowania do tworzenia bazy danych. Wartością domyślną jest `dbLangGeneral`. Możliwe wartości:

- `dbLangGeneral`Angielski, niemiecki, francuski, portugalski, włoski i współczesny hiszpański

- `dbLangArabic`Arabski

- `dbLangCyrillic`Rosyjski

- `dbLangCzech`Czeski

- `dbLangDutch`Holenderski

- `dbLangGreek`Grecki

- `dbLangHebrew`Hebrajski

- `dbLangHungarian`Węgierski

- `dbLangIcelandic`Islandzki

- `dbLangNordic`Języki nordyckie (tylko aparat baz danych Microsoft Jet w wersji 1.0)

- `dbLangNorwdan`Norweski i duński

- `dbLangPolish`Polski

- `dbLangSpanish`Tradycyjny hiszpański

- `dbLangSwedfin`Szwedzki i fiński

- `dbLangTurkish`Turecki

*Dwoptions*<br/>
Liczba całkowita wskazująca jedną lub więcej opcji. Możliwe wartości:

- `dbEncrypt`Tworzenie zaszyfrowanej bazy danych.

- `dbVersion10`Utwórz bazę danych z bazą danych Microsoft Jet w wersji 1.0.

- `dbVersion11`Utwórz bazę danych z bazą danych Microsoft Jet w wersji 1.1.

- `dbVersion20`Utwórz bazę danych z bazą danych Microsoft Jet w wersji 2.0.

- `dbVersion30`Utwórz bazę danych z bazą danych Microsoft Jet w wersji 3.0.

Jeśli pominięto stałą szyfrowania, zostanie utworzona niezaszyfrowana baza danych. Można określić tylko jedną stałą wersji. Jeśli pominięto stałą wersji, zostanie utworzona baza danych korzystająca z bazy danych Microsoft Jet w wersji 3.0.

> [!CAUTION]
> Jeśli baza danych nie jest szyfrowana, jest możliwe, nawet jeśli zaimplementujesz zabezpieczenia użytkownika/hasła, aby bezpośrednio odczytać plik dysku binarnego, który stanowi bazę danych.

### <a name="remarks"></a>Uwagi

`Create`tworzy plik bazy danych i podstawowy obiekt bazy danych DAO i inicjuje obiekt C++. Obiekt jest dołączany do kolekcji bazy danych skojarzonego obszaru roboczego. Obiekt bazy danych jest w stanie otwartym; nie `Open*` dzwonić `Create`po .

> [!NOTE]
> Za `Create`pomocą programu można utworzyć tylko program Microsoft Jet (. bazy danych MDB). Nie można tworzyć baz danych ISAM ani baz danych ODBC.

## <a name="cdaodatabasecreaterelation"></a><a name="createrelation"></a>Baza danych CDDaoDatabase::CreateRelation

Wywołanie tej funkcji elementu członkowskiego, aby ustanowić relację między jednym lub więcej pól w tabeli podstawowej w bazie danych i co najmniej jedno pole w tabeli obcej (inna tabela w bazie danych).

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

*Lpszname*<br/>
Unikatowa nazwa obiektu relacji. Nazwa musi zaczynać się od litery i może zawierać maksymalnie 40 znaków. Może zawierać liczby i znaki podkreślenia, ale nie może zawierać znaków interpunkcyjnych ani spacji.

*lpszTable (tabela)*<br/>
Nazwa tabeli podstawowej w relacji. Jeśli tabela nie istnieje, MFC zgłasza wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

*lpszForeignTable*<br/>
Nazwa tabeli obcej w relacji. Jeśli tabela nie istnieje, MFC zgłasza `CDaoException`wyjątek typu .

*lPrzyszłądki*<br/>
Długa wartość zawierająca informacje o typie relacji. Ta wartość służy do wymuszania więzów integralności, między innymi. Operator bitowy OR **(&#124;) **służy do łączenia dowolnej z następujących wartości (o ile kombinacja ma sens):

- `dbRelationUnique`Relacja jest jeden do jednego.

- `dbRelationDontEnforce`Relacja nie jest wymuszana (nie ma integralności referencyjnej).

- `dbRelationInherited`Relacja istnieje w bazie danych, która zawiera dwie dołączone tabele.

- `dbRelationUpdateCascade`Aktualizacje będą kaskadowe (więcej informacji na temat kaskad, zobacz Uwagi).

- `dbRelationDeleteCascade`Usunięcia będą kaskadowo.

*lpszField (lpszField)*<br/>
Wskaźnik do ciągu zakończonego zerem zawierającego nazwę pola w tabeli podstawowej (nazwanego przez *lpszTable*).

*lpszForeignField (lpszForeignField)*<br/>
Wskaźnik do ciągu zakończonego zerem zawierającego nazwę pola w tabeli obcej (nazwanego przez *lpszForeignTable*).

*relinfo (relinfo)*<br/>
Odwołanie do obiektu [CDaoRelationInfo,](../../mfc/reference/cdaorelationinfo-structure.md) który zawiera informacje o relacji, którą chcesz utworzyć.

### <a name="remarks"></a>Uwagi

Relacja nie może obejmować kwerendy lub dołączonej tabeli z zewnętrznej bazy danych.

Użyj pierwszej wersji funkcji, gdy relacja obejmuje jedno pole w każdej z dwóch tabel. Użyj drugiej wersji, gdy relacja obejmuje wiele pól. Maksymalna liczba pól w relacji wynosi 14.

Ta akcja tworzy podstawowy obiekt relacji DAO, ale jest to szczegóły implementacji MFC, ponieważ hermetyzacja obiektów relacji MFC jest zawarta w klasie `CDaoDatabase`. MFC nie dostarcza klasy dla relacji.

Jeśli atrybuty obiektu relacji zostaną ustawione w celu aktywowania operacji kaskadowych, aparat bazy danych automatycznie zaktualizuje lub usunie rekordy w jednej lub większej liczbie innych tabel po wprowadzeniu zmian w powiązanych tabelach kluczy podstawowych.

Załóżmy na przykład, że ustanowisz relację usuwania kaskadowego między tabelą Klienci a tabelą Zamówienia. Po usunięciu rekordów z tabeli Klienci rekordy w tabeli Zamówienia związane z tym odbiorcą są również usuwane. Ponadto w przypadku ustanowienia relacji usuwania kaskadowego między tabelą Zamówienia a innymi tabelami rekordy z tych tabel są automatycznie usuwane po usunięciu rekordów z tabeli Klienci.

Aby uzyskać powiązane informacje, zobacz temat "CreateRelation Method" w Pomocy DAO.

## <a name="cdaodatabasedeletequerydef"></a><a name="deletequerydef"></a>CDaoDatabase::DeleteQueryDef

Wywołanie tej funkcji elementu członkowskiego, aby usunąć `CDaoDatabase` określony querydef — zapisane zapytanie — z kolekcji QueryDefs obiektu.

```
void DeleteQueryDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
Nazwa zapisanej kwerendy do usunięcia.

### <a name="remarks"></a>Uwagi

Następnie ta kwerenda nie jest już zdefiniowana w bazie danych.

Aby uzyskać informacje dotyczące tworzenia obiektów querydef, zobacz klasa [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Obiekt querydef staje się skojarzony z `CDaoDatabase` określonym `CDaoQueryDef` obiektem podczas konstruowania obiektu, przekazując go wskaźnik do obiektu bazy danych.

## <a name="cdaodatabasedeleterelation"></a><a name="deleterelation"></a>CDaoDatabase::DeleteRelation

Wywołanie tej funkcji elementu członkowskiego, aby usunąć istniejącą relację z kolekcji Relacje obiektu bazy danych.

```
void DeleteRelation(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
Nazwa relacji do usunięcia.

### <a name="remarks"></a>Uwagi

Później relacja już nie istnieje.

Aby uzyskać powiązane informacje, zobacz temat "Metoda usuwania" w Pomocy DAO.

## <a name="cdaodatabasedeletetabledef"></a><a name="deletetabledef"></a>CDaoDatabase::DeleteTableDef

Wywołanie tej funkcji elementu członkowskiego, aby usunąć `CDaoDatabase` określoną tabelę i wszystkie jego dane z kolekcji TableDefs obiektu.

```
void DeleteTableDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
Nazwa tabledef do usunięcia.

### <a name="remarks"></a>Uwagi

Następnie ta tabela nie jest już zdefiniowana w bazie danych.

> [!NOTE]
> Należy zachować szczególną ostrożność, aby nie usuwać tabel systemowych.

Aby uzyskać informacje na temat tworzenia obiektów tabledef, zobacz klasę [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md). Obiekt tabledef staje się skojarzony z `CDaoDatabase` określonym `CDaoTableDef` obiektem podczas konstruowania obiektu, przekazując go wskaźnik do obiektu bazy danych.

Aby uzyskać powiązane informacje, zobacz temat "Metoda usuwania" w Pomocy DAO.

## <a name="cdaodatabaseexecute"></a><a name="execute"></a>Baza danych CDDaoDatabase::Wykonanie

Wywołanie tej funkcji elementu członkowskiego, aby uruchomić kwerendę akcji lub wykonać instrukcję SQL w bazie danych.

```
void Execute(
    LPCTSTR lpszSQL,
    int nOptions = dbFailOnError);
```

### <a name="parameters"></a>Parametry

*Lpszsql*<br/>
Wskaźnik do ciągu zakończonego zerem zawierającego prawidłowe polecenie SQL do wykonania.

*nOpcje*<br/>
Liczba całkowita określająca opcje związane z integralnością kwerendy. Można użyć operatora bitowego OR **(&#124;**) do połączenia dowolnej z następujących stałych (pod warunkiem, że kombinacja ma sens — na przykład nie można połączyć `dbInconsistent` z): `dbConsistent`

- `dbDenyWrite`Odmów uprawnień do zapisu innym użytkownikom.

- `dbInconsistent`(Domyślnie) Niespójne aktualizacje.

- `dbConsistent`Spójne aktualizacje.

- `dbSQLPassThrough`Przekazywanie SQL. Powoduje, że instrukcja SQL mają być przekazywane do źródła danych ODBC do przetwarzania.

- `dbFailOnError`Wycofywanie aktualizacji w przypadku wystąpienia błędu.

- `dbSeeChanges`Wygeneruj błąd czasu wykonywania, jeśli inny użytkownik zmienia edytowane dane.

> [!NOTE]
> Jeśli `dbInconsistent` oba `dbConsistent` i są uwzględnione lub jeśli żadna z nich nie jest uwzględniona, wynikiem jest wartość domyślna. Aby uzyskać wyjaśnienie tych stałych, zobacz temat "Execute Method" w Pomocy DAO.

### <a name="remarks"></a>Uwagi

`Execute`działa tylko dla kwerend akcji lub zapytań przekazywania SQL, które nie zwracają wyników. Nie działa dla kwerend select, które zwracają rekordy.

Aby uzyskać definicję i informacje o kwerendach akcji, zobacz tematy "Action Query" i "Execute Method" w Pomocy DAO.

> [!TIP]
> Biorąc pod uwagę syntaktycznie poprawne instrukcji `Execute` SQL i odpowiednie uprawnienia, funkcja elementu członkowskiego nie zakończy się niepowodzeniem, nawet jeśli nie jeden wiersz może być modyfikowany lub usunięty. W związku z `dbFailOnError` tym zawsze `Execute` należy użyć tej opcji podczas korzystania z funkcji elementu członkowskiego, aby uruchomić kwerendę aktualizacji lub usuwania. Ta opcja powoduje, że MFC zgłosić wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md) i wycofuje wszystkie pomyślne zmiany, jeśli którykolwiek z rekordów, których dotyczy problem są zablokowane i nie można zaktualizować lub usunąć. Należy pamiętać, że `GetRecordsAffected` zawsze można wywołać, aby zobaczyć, ile rekordów zostały naruszone.

Wywołanie funkcji elementu członkowskiego [GetRecordsAffected](#getrecordsaffected) obiektu bazy danych w celu `Execute` określenia liczby rekordów, których dotyczy ostatnie wywołanie. Na przykład `GetRecordsAffected` zwraca informacje o liczbie rekordów usuniętych, zaktualizowanych lub wstawionych podczas wykonywania kwerendy akcji. Zwrócona liczba nie będzie odzwierciedlać zmian w powiązanych tabelach, gdy aktualizacje kaskadowe lub usuwane są w mocy.

`Execute`nie zwraca pliku recordset. Użycie `Execute` w kwerendzie, która wybiera rekordy powoduje, `CDaoException`że MFC zgłasza wyjątek typu . (Nie ma `ExecuteSQL` funkcji elementu `CDatabase::ExecuteSQL`członkowskiego analogiczne do .)

## <a name="cdaodatabasegetconnect"></a><a name="getconnect"></a>Baza danych CDDaoDatabase::GetConnect

Wywołanie tej funkcji elementu członkowskiego, aby `CDaoDatabase` pobrać ciąg połączenia używany do łączenia obiektu z bazą danych ODBC lub ISAM.

```
CString GetConnect();
```

### <a name="return-value"></a>Wartość zwracana

Parametry połączenia, jeśli [Open](#open) został pomyślnie wywołany w źródle danych ODBC; w przeciwnym razie pusty ciąg. Dla microsoft jet (. Baza danych MDB), ciąg jest zawsze pusty, chyba `dbSQLPassThrough` że ustawisz go do użycia z opcją używaną z funkcją [Wykonaj](#execute) element członkowski lub używaną do otwierania zestawu rekordów.

### <a name="remarks"></a>Uwagi

Ciąg zawiera informacje o źródle otwartej bazy danych lub bazy danych używanej w kwerendzie przekazowej. Parametry połączenia składają się ze specyfikatora typu bazy danych i zero lub więcej parametrów oddzielonych średnikami.

> [!NOTE]
> Za pomocą klas DAO MFC do łączenia się ze źródłem danych za pośrednictwem ODBC jest mniej wydajne niż łączenie za pośrednictwem dołączonej tabeli.

> [!NOTE]
> Parametry połączenia są używane do przekazywania dodatkowych informacji do odbc i niektórych sterowników ISAM w razie potrzeby. Nie jest używany do . bazy danych MDB. W przypadku tabel bazowych bazy danych Microsoft Jet parametry połączenia są pustym ciągiem (""), z wyjątkiem sytuacji, gdy jest on używany do kwerendy przekazywania SQL, jak opisano w obszarze Zwracana wartość powyżej.

Zobacz [Otwórz](#open) funkcję elementu członkowskiego, aby uzyskać opis sposobu tworzenia ciągu połączenia. Po ustawieniu ciągu połączenia `Open` w wywołaniu można go później użyć do sprawdzenia tego ustawienia w celu określenia typu, ścieżki, identyfikatora użytkownika, hasła lub źródła danych ODBC bazy danych.

## <a name="cdaodatabasegetname"></a><a name="getname"></a>Baza danych CDDaoDatabase::GetName

Wywołanie tej funkcji elementu członkowskiego, aby pobrać nazwę aktualnie otwartej bazy danych, która jest nazwą istniejącego pliku bazy danych lub nazwą zarejestrowanego źródła danych ODBC.

```
CString GetName();
```

### <a name="return-value"></a>Wartość zwracana

Pełna ścieżka i nazwa pliku bazy danych, jeśli zakończy się pomyślnie; w przeciwnym razie pusty [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Uwagi

Jeśli sieć obsługuje jednolitą konwencję nazewnictwa (UNC), można również\\\\\\określić ścieżkę sieciową , na przykład " \MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB". (Podwójne ukośniki odwrotne są wymagane w\\literałach ciągów, ponieważ " " jest znakiem ucieczki języka C++).

Można na przykład wyświetlić tę nazwę w nagłówku. Jeśli wystąpi błąd podczas pobierania nazwy, MFC zgłasza wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

> [!NOTE]
> Aby uzyskać lepszą wydajność podczas uzyskiwania dostępu do zewnętrznych baz danych, zaleca się dołączanie tabel zewnętrznej bazy danych do bazy danych Microsoft Jet (. MDB), a nie łączenie się bezpośrednio ze źródłem danych.

Typ bazy danych jest wskazywany przez plik lub katalog, który ścieżka wskazuje, w następujący sposób:

|Nazwa ścieżki wskazuje na..|Typ bazy danych|
|--------------------------|-------------------|
|. Plik MDB|Baza danych Microsoft Jet (Microsoft Access)|
|Katalog zawierający plik . Pliki(-a) DBF|Baza danych dBASE|
|Katalog zawierający plik . Plik XLS|Baza danych programu Microsoft Excel|
|Katalog zawierający plik . Pliki(-a) PDX|Baza danych Paradox|
|Katalog zawierający odpowiednio sformatowane pliki tekstowej bazy danych|Baza danych formatu tekstu|

W przypadku baz danych ODBC, takich jak SQL Server i Oracle, parametry połączenia bazy danych identyfikują nazwę źródła danych (DSN), która jest zarejestrowana przez ODBC.

## <a name="cdaodatabasegetquerydefcount"></a><a name="getquerydefcount"></a>CDaoDatabase::GetQueryDefCount

Wywołanie tej funkcji elementu członkowskiego, aby pobrać liczbę zapytań zdefiniowanych w kolekcji QueryDefs bazy danych.

```
short GetQueryDefCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba zapytań zdefiniowanych w bazie danych.

### <a name="remarks"></a>Uwagi

`GetQueryDefCount`jest przydatne, jeśli trzeba pętli przez wszystkie querydefs w QueryDefs kolekcji. Aby uzyskać informacje o danej kwerendzie w kolekcji, zobacz [GetQueryDefInfo](#getquerydefinfo).

## <a name="cdaodatabasegetquerydefinfo"></a><a name="getquerydefinfo"></a>Baza danych CDDaoDatabase::GetQueryDefInfo

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać różne rodzaje informacji o kwerendzie zdefiniowane w bazie danych.

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

*Nindex*<br/>
Indeks wstępnie zdefiniowanej kwerendy w kolekcji QueryDefs bazy danych, do wyszukiwania według indeksu.

*querydefinfo*<br/>
Odwołanie do [obiektu CDaoQueryDefInfo,](../../mfc/reference/cdaoquerydefinfo-structure.md) który zwraca żądane informacje.

*dwInfoOptions (NpfoOptions)*<br/>
Opcje określające informacje o ach recordset do pobrania. Dostępne opcje są wymienione w tym miejscu wraz z tym, co powoduje, że funkcja zwraca o recordset:

- AFX_DAO_PRIMARY_INFO (domyślna) nazwa, typ

- AFX_DAO_SECONDARY_INFO Informacje podstawowe plus: Data utworzenia, Data ostatniej aktualizacji, Rekordy zwrotów, Aktualizacja

- AFX_DAO_ALL_INFO Informacje podstawowe i pomocnicze plus: SQL, Connect, ODBCTimeout

*Lpszname*<br/>
Ciąg zawierający nazwę kwerendy zdefiniowanej w bazie danych, do wyszukiwania według nazwy.

### <a name="remarks"></a>Uwagi

Dwie wersje funkcji są dostarczane, dzięki czemu można wybrać kwerendę przez indeks w kolekcji QueryDefs bazy danych lub przez nazwę kwerendy.

Aby uzyskać opis informacji zwracanych w *querydefinfo*, zobacz [CDaoQueryDefInfo](../../mfc/reference/cdaoquerydefinfo-structure.md) struktury. Ta struktura ma elementy, które odpowiadają elementom informacji wymienionych powyżej w opisie *dwInfoOptions*. Jeśli poprosisz o jeden poziom informacji, otrzymasz również wcześniejsze poziomy informacji.

## <a name="cdaodatabasegetquerytimeout"></a><a name="getquerytimeout"></a>CDaoDatabase::GetQueryTimeout

Wywołanie tej funkcji elementu członkowskiego, aby pobrać bieżącą liczbę sekund, aby zezwolić przed kolejnymi operacjami w połączonej bazie danych są upłyane limit czasu.

```
short GetQueryTimeout();
```

### <a name="return-value"></a>Wartość zwracana

Krótka liczba całkowita zawierająca wartość limitu czasu w sekundach.

### <a name="remarks"></a>Uwagi

Operacja może się przeterminować z powodu problemów z dostępem do sieci, nadmiernego czasu przetwarzania zapytań i tak dalej. Gdy to ustawienie jest w mocy, ma wpływ na wszystkie operacje otwierania, dodawania `CDaoDatabase` nowych, aktualizacji i usuwania na wszystkich zestawy rekordów skojarzone z tym obiektem. Bieżące ustawienie limitu czasu można zmienić, wywołując [setquerytimeout](#setquerytimeout). Zmiana wartości limitu czasu kwerendy dla pliku recordset po otwarciu nie powoduje zmiany wartości dla pliku recordset. Na przykład kolejne operacje [move](../../mfc/reference/cdaorecordset-class.md#move) nie używają nowej wartości. Wartość domyślna jest początkowo ustawiana podczas inicjowania aparatu bazy danych.

Domyślna wartość limitów czasu kwerendy pochodzi z rejestru systemu Windows. Jeśli nie ma ustawienia rejestru, wartość domyślna to 60 sekund. Nie wszystkie bazy danych obsługują możliwość ustawienia wartości limitu czasu kwerendy. Jeśli ustawisz wartość limitu czasu kwerendy 0, nie występuje limit czasu; i komunikacja z bazą danych może przestać odpowiadać. To zachowanie może być przydatne podczas tworzenia. Jeśli wywołanie nie powiedzie się, MFC zgłasza wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

Aby uzyskać powiązane informacje, zobacz temat "Właściwość QueryTimeout" w Pomocy DAO.

## <a name="cdaodatabasegetrecordsaffected"></a><a name="getrecordsaffected"></a>CDaoDatabase::GetRecordsAffected

Wywołanie tej funkcji elementu członkowskiego, aby określić liczbę rekordów, których dotyczy ostatnie wywołanie funkcji [Wykonaj](#execute) element członkowski.

```
long GetRecordsAffected();
```

### <a name="return-value"></a>Wartość zwracana

Długa liczba całkowita zawierająca liczbę rekordów, których to dotyczy.

### <a name="remarks"></a>Uwagi

Zwrócona wartość obejmuje liczbę rekordów usuniętych, zaktualizowanych lub `Execute`wstawionych przez kwerendę akcji uruchomioną za pomocą programu . Zwrócona liczba nie będzie odzwierciedlać zmian w powiązanych tabelach, gdy aktualizacje kaskadowe lub usuwane są w mocy.

Aby uzyskać powiązane informacje, zobacz temat "RecordsAffected Property" w Pomocy DAO.

## <a name="cdaodatabasegetrelationcount"></a><a name="getrelationcount"></a>Baza danych CDDaoDatabase::GetRelationCount

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać liczbę relacji zdefiniowanych między tabelami w bazie danych.

```
short GetRelationCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba relacji zdefiniowanych między tabelami w bazie danych.

### <a name="remarks"></a>Uwagi

`GetRelationCount`jest przydatne, jeśli trzeba pętli przez wszystkie zdefiniowane relacje w kolekcji Relacje bazy danych. Aby uzyskać informacje o danej relacji w kolekcji, zobacz [GetRelationInfo](#getrelationinfo).

Aby zilustrować pojęcie relacji, należy wziąć pod uwagę dostawcy tabeli i produkty tabeli, które mogą mieć relację jeden do wielu. W tej relacji jeden dostawca może dostarczyć więcej niż jeden produkt. Inne relacje są jeden do jednego i wiele do wielu.

## <a name="cdaodatabasegetrelationinfo"></a><a name="getrelationinfo"></a>Baza danych CDDaoDatabase::GetRelationInfo

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać informacje o określonej relacji w kolekcji Relacje bazy danych.

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

*Nindex*<br/>
Indeks obiektu relacji w kolekcji Relacje bazy danych, do wyszukiwania według indeksu.

*relinfo (relinfo)*<br/>
Odwołanie do obiektu [CDaoRelationInfo,](../../mfc/reference/cdaorelationinfo-structure.md) który zwraca żądane informacje.

*dwInfoOptions (NpfoOptions)*<br/>
Opcje określające informacje o relacji do pobrania. Dostępne opcje są wymienione tutaj wraz z tym, co powodują, że funkcja zwraca o relacji:

- AFX_DAO_PRIMARY_INFO (domyślna) nazwa, tabela, tabela zagraniczna

- AFX_DAO_SECONDARY_INFO atrybuty, informacje o polu

Informacje o polu jest [obiektem CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md) zawierającym pola z tabeli podstawowej, w które uczestniczy relation.

*Lpszname*<br/>
Ciąg zawierający nazwę obiektu relacji, dla wyszukiwania według nazwy.

### <a name="remarks"></a>Uwagi

Dwie wersje tej funkcji zapewniają dostęp według indeksu lub nazwy. Aby uzyskać opis informacji zwróconych w *relinfo*, zobacz [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) struktury. Ta struktura ma elementy, które odpowiadają elementom informacji wymienionych powyżej w opisie *dwInfoOptions*. Jeśli poprosisz o informacje na jednym poziomie, otrzymasz również informacje na dowolnym wcześniejszym poziomie.

> [!NOTE]
> Jeśli atrybuty obiektu relacji zostaną ustawione w`dbRelationUpdateCascades` celu `dbRelationDeleteCascades`aktywowania operacji kaskadowych ( lub), aparat bazy danych Microsoft Jet automatycznie zaktualizuje lub usunie rekordy w jednej lub większej liczbie innych tabel po wprowadzeniu zmian w powiązanych tabelach kluczy podstawowych. Załóżmy na przykład, że ustanowisz relację usuwania kaskadowego między tabelą Klienci a tabelą Zamówienia. Po usunięciu rekordów z tabeli Klienci rekordy w tabeli Zamówienia związane z tym odbiorcą są również usuwane. Ponadto w przypadku ustanowienia relacji usuwania kaskadowego między tabelą Zamówienia a innymi tabelami rekordy z tych tabel są automatycznie usuwane po usunięciu rekordów z tabeli Klienci.

## <a name="cdaodatabasegettabledefcount"></a><a name="gettabledefcount"></a>Baza danych CDDaoDatabase::GetTableDefCount

Wywołanie tej funkcji elementu członkowskiego, aby pobrać liczbę tabel zdefiniowanych w bazie danych.

```
short GetTableDefCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba tabledefs zdefiniowane w bazie danych.

### <a name="remarks"></a>Uwagi

`GetTableDefCount`jest przydatne, jeśli trzeba pętli przez wszystkie tabledefs w bazie danych TableDefs kolekcji. Aby uzyskać informacje o danej tabeli w kolekcji, zobacz [GetTableDefInfo](#gettabledefinfo).

## <a name="cdaodatabasegettabledefinfo"></a><a name="gettabledefinfo"></a>Baza danych CDDaoDatabase::GetTableDefInfo

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać różne rodzaje informacji o tabeli zdefiniowanej w bazie danych.

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

*Nindex*<br/>
Indeks obiektu tabledef w kolekcji TableDefs bazy danych, do wyszukiwania według indeksu.

*tabledefinfo*<br/>
Odwołanie do obiektu [CDaoTableDefInfo,](../../mfc/reference/cdaotabledefinfo-structure.md) który zwraca żądane informacje.

*dwInfoOptions (NpfoOptions)*<br/>
Opcje określające informacje o tabeli do pobrania. Dostępne opcje są wymienione tutaj wraz z tym, co powodują, że funkcja zwraca o relacji:

- AFX_DAO_PRIMARY_INFO (domyślna) nazwa, możliwe do aktualizacji, atrybuty

- AFX_DAO_SECONDARY_INFO Informacje podstawowe plus: Data utworzenia, Data ostatniej aktualizacji, Nazwa tabeli źródłowych, Połącz

- AFX_DAO_ALL_INFO informacje podstawowe i dodatkowe plus: Reguła sprawdzania poprawności, Tekst sprawdzania poprawności, Liczba rekordów

*Lpszname*<br/>
Nazwa obiektu tabledef, dla wyszukiwania według nazwy.

### <a name="remarks"></a>Uwagi

Dwie wersje funkcji są dostarczane, dzięki czemu można wybrać tabelę według indeksu w kolekcji TableDefs bazy danych lub przez nazwę tabeli.

Aby uzyskać opis informacji zwracanych w *tabledefinfo*, zobacz [CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md) struktury. Ta struktura ma elementy, które odpowiadają elementom informacji wymienionych powyżej w opisie *dwInfoOptions*. Jeśli poprosisz o informacje na jednym poziomie, otrzymasz informacje o każdym wcześniejszym poziomie.

> [!NOTE]
> Opcja AFX_DAO_ALL_INFO zawiera informacje, które można uzyskać wolno. W takim przypadku zliczanie rekordów w tabeli może być bardzo czasochłonne, jeśli istnieje wiele rekordów.

## <a name="cdaodatabasegetversion"></a><a name="getversion"></a>Baza danych CDDaoDatabase::GetVersion

Wywołanie tej funkcji elementu członkowskiego, aby określić wersję pliku bazy danych Microsoft Jet.

```
CString GetVersion();
```

### <a name="return-value"></a>Wartość zwracana

A [CString,](../../atl-mfc-shared/reference/cstringt-class.md) który wskazuje wersję pliku bazy danych skojarzonego z obiektem.

### <a name="remarks"></a>Uwagi

Zwracana wartość reprezentuje numer wersji w formularzu "major.minor"; na przykład "3.0". Numer wersji produktu (na przykład 3.0) składa się z numeru wersji (3), kropki i numeru wydania (0). Dotychczasowe wersje to 1.0, 1.1, 2.0 i 3.0.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość wersji" w Pomocy DAO.

## <a name="cdaodatabaseisopen"></a><a name="isopen"></a>CDaoDatabase::IsOpen

Wywołanie tej funkcji elementu `CDaoDatabase` członkowskiego, aby ustalić, czy obiekt jest obecnie otwarty w bazie danych.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, `CDaoDatabase` jeśli obiekt jest aktualnie otwarty; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

## <a name="cdaodatabasem_pdaodatabase"></a><a name="m_pdaodatabase"></a>Baza danych CDDaoDatabase::m_pDAODatabase

Zawiera wskaźnik do interfejsu OLE dla obiektu bazy `CDaoDatabase` danych DAO leżącego u podstaw obiektu.

### <a name="remarks"></a>Uwagi

Użyj tego wskaźnika, jeśli chcesz uzyskać bezpośredni dostęp do interfejsu DAO.

Aby uzyskać informacje na temat bezpośredniego dzwonienia do DAO, zobacz [Uwaga techniczna 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="cdaodatabasem_pworkspace"></a><a name="m_pworkspace"></a>Baza danych CDDaoDatabase::m_pWorkspace

Zawiera wskaźnik do obiektu [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) zawierającego obiekt bazy danych.

### <a name="remarks"></a>Uwagi

Użyj tego wskaźnika, jeśli chcesz uzyskać dostęp do obszaru roboczego bezpośrednio — na przykład, aby uzyskać wskaźniki do innych obiektów bazy danych w kolekcji bazy danych obszaru roboczego.

## <a name="cdaodatabaseopen"></a><a name="open"></a>Baza danych CDDaoDatabase::Otwórz

Należy wywołać tę funkcję elementu członkowskiego, `CDaoDatabase` aby zainicjować nowo skonstruowany obiekt, który reprezentuje istniejącą bazę danych.

```
virtual void Open(
    LPCTSTR lpszName,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T(""));
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
Wyrażenie ciągu, które jest nazwą istniejącego programu Microsoft Jet (. MDB). Jeśli nazwa pliku ma rozszerzenie, jest to wymagane. Jeśli sieć obsługuje jednolitą konwencję nazewnictwa (UNC), można również\\\\\\określić\\ścieżkę\\sieciową,\\taką jak " \MYSERVER \MYSHARE \MYDIR \MYDB. MDB". (Podwójne ukośniki odwrotne są wymagane w\\literałach ciągów, ponieważ " " jest znakiem ucieczki języka C++).

Niektóre zagadnienia mają zastosowanie podczas korzystania *z lpszName*. Jeśli:

- Odwołuje się do bazy danych, która jest już otwarta dla wyłącznego dostępu przez innego użytkownika, MFC zgłasza wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md). Zalewka tego wyjątku, aby poinformować użytkownika, że baza danych jest niedostępna.

- Jest pustym ciągiem ("") i *lpszConnect* jest "ODBC;", okno dialogowe z listą wszystkich zarejestrowanych nazw źródeł danych ODBC jest wyświetlany, dzięki czemu użytkownik może wybrać bazę danych. Należy unikać bezpośrednich połączeń ze źródłami danych ODBC; zamiast tego użyj dołączonej tabeli.

- W przeciwnym razie nie odwołuje się do istniejącej bazy danych lub prawidłowej nazwy źródła danych ODBC, MFC zgłasza wyjątek typu `CDaoException`.

> [!NOTE]
> Aby uzyskać szczegółowe informacje na temat kodów błędów DAO, zobacz DAOERR. H. Aby uzyskać powiązane informacje, zobacz temat "Błędy dostępu do danych do zalewkowalnych" w Pomocy DAO.

*bWyłącze*<br/>
Wartość logiczna, która jest TRUE, jeśli baza danych ma być otwarty dla wyłącznego (nonshared) dostępu i FALSE, jeśli baza danych ma być otwarty dla dostępu współdzielonego. Jeśli pominięto ten argument, baza danych zostanie otwarta dla dostępu współdzielonego.

*bCzytyNie*<br/>
Wartość logiczna, która jest TRUE, jeśli baza danych ma być otwarty dla dostępu tylko do odczytu i FALSE, jeśli baza danych ma być otwarty dla dostępu do odczytu/zapisu. Jeśli pominięto ten argument, baza danych jest otwierana dla dostępu do odczytu/zapisu. Wszystkie zależne zestawy rekordów dziedziczą ten atrybut.

*lpszConnect*<br/>
Wyrażenie ciągu używane do otwierania bazy danych. Ten ciąg stanowi argumenty odbc connect. Aby dostarczyć ciąg źródłowy, należy podać wyłączne i tylko do odczytu argumenty. Jeśli baza danych jest bazą danych Microsoft Jet (. MDB), ten ciąg jest pusty (""). Składnia wartości domyślnej — **_T**("") — zapewnia możliwość przenoszenia dla unicode, a także kompilacji ANSI aplikacji.

### <a name="remarks"></a>Uwagi

`Open`kojarzy bazę danych z podstawowym obiektem DAO. Nie można użyć obiektu bazy danych do konstruowania recordset, tabledef lub querydef obiektów, dopóki nie zostanie zainicjowany. `Open`dołącza obiekt bazy danych do kolekcji bazy danych skojarzonego obszaru roboczego.

Należy stosować następujące parametry:

- Jeśli otwierasz microsoft jet (. MDB) bazy danych, użyj parametru *lpszName* i przeprować pusty ciąg parametru *lpszConnect* lub przekazać ciąg hasła formularza "; PWD=password", jeśli baza danych jest chroniona hasłem (. tylko bazy danych MDB).

- Jeśli otwierasz źródło danych ODBC, przekaż prawidłowy ciąg połączenia ODBC w *lpszConnect* i pusty ciąg w *lpszName*.

Aby uzyskać powiązane informacje, zobacz temat "Metoda OpenDatabase" w Pomocy DAO.

> [!NOTE]
> Aby uzyskać lepszą wydajność podczas uzyskiwania dostępu do zewnętrznych baz danych, w tym baz danych ISAM i źródeł danych ODBC, zaleca się dołączanie tabel zewnętrznej bazy danych do bazy danych aparatu Microsoft Jet (. MDB), a nie łączenie się bezpośrednio ze źródłem danych.

Jest możliwe dla próby połączenia limit czasu, jeśli, na przykład, host DBMS jest niedostępny. Jeśli próba połączenia `Open` nie powiedzie się, zgłasza wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

Pozostałe uwagi dotyczą tylko baz danych ODBC:

Jeśli baza danych jest bazą danych `Open` ODBC, a parametry w wywołaniu nie zawierają wystarczających informacji, aby nawiązać połączenie, sterownik ODBC otwiera okno dialogowe w celu uzyskania niezbędnych informacji od użytkownika. Połączenie `Open`, parametry *połączenia, lpszConnect*, jest przechowywane prywatnie i jest dostępne przez wywołanie funkcji elementu członkowskiego [GetConnect.](#getconnect)

Jeśli chcesz, możesz otworzyć własne okno dialogowe przed wywołaniem, `Open` aby uzyskać informacje od użytkownika, takie jak `Open`hasło, a następnie dodać te informacje do ciągu połączenia, który przekazujesz do programu . Możesz też zapisać przekazywana przez Aplikację (być może w rejestrze systemu Windows), aby `Open` można `CDaoDatabase` było go ponownie użyć przy następnym wywołaniu obiektu przez aplikację.

Można również użyć ciągu połączenia dla wielu poziomów autoryzacji `CDaoDatabase` logowania (każdy dla innego obiektu) lub do przekazywania innych informacji specyficznych dla bazy danych.

## <a name="cdaodatabasesetquerytimeout"></a><a name="setquerytimeout"></a>CDaoDatabase::SetQueryTimeout

Wywołanie tej funkcji elementu członkowskiego, aby zastąpić domyślną liczbę sekund, aby zezwolić przed kolejnymi operacjami na limit czasu połączonej bazy danych.

```
void SetQueryTimeout(short nSeconds);
```

### <a name="parameters"></a>Parametry

*nSekundy*<br/>
Liczba sekund, aby zezwolić przed kwerendy próby przesunięcia.

### <a name="remarks"></a>Uwagi

Operacja może się przekreślić z powodu problemów z dostępem do sieci, nadmiernego czasu przetwarzania zapytań i tak dalej. Wywołanie `SetQueryTimeout` przed otwarciem pliku recordset lub przed wywołaniem [programu Recordset AddNew](../../mfc/reference/cdaorecordset-class.md#addnew), [Update](../../mfc/reference/cdaorecordset-class.md#update)lub Delete funkcji [członkowskich,](../../mfc/reference/cdaorecordset-class.md#delete) jeśli chcesz zmienić wartość limitu czasu kwerendy. Ustawienie ma wpływ na `AddNew`wszystkie `Update`kolejne `Delete` [otwarte](../../mfc/reference/cdaorecordset-class.md#open), i wywołuje `CDaoDatabase` wszystkie zestawy rekordów skojarzone z tym obiektem. Zmiana wartości limitu czasu kwerendy dla pliku recordset po otwarciu nie powoduje zmiany wartości dla pliku recordset. Na przykład kolejne operacje [move](../../mfc/reference/cdaorecordset-class.md#move) nie używają nowej wartości.

Domyślna wartość limitów czasu kwerendy wynosi 60 sekund. Nie wszystkie bazy danych obsługują możliwość ustawienia wartości limitu czasu kwerendy. Jeśli ustawisz wartość limitu czasu kwerendy 0, nie występuje limit czasu; komunikacja z bazą danych może przestać odpowiadać. To zachowanie może być przydatne podczas tworzenia.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość QueryTimeout" w Pomocy DAO.

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)<br/>
[Klasa CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)<br/>
[Klasa CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)<br/>
[Klasa CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)<br/>
[Klasa CDatabase](../../mfc/reference/cdatabase-class.md)<br/>
[Klasa CDaoException](../../mfc/reference/cdaoexception-class.md)
