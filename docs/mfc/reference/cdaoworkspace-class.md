---
title: Klasa CDaoWorkspace
ms.date: 11/04/2016
f1_keywords:
- CDaoWorkspace
- AFXDAO/CDaoWorkspace
- AFXDAO/CDaoWorkspace::CDaoWorkspace
- AFXDAO/CDaoWorkspace::Append
- AFXDAO/CDaoWorkspace::BeginTrans
- AFXDAO/CDaoWorkspace::Close
- AFXDAO/CDaoWorkspace::CommitTrans
- AFXDAO/CDaoWorkspace::CompactDatabase
- AFXDAO/CDaoWorkspace::Create
- AFXDAO/CDaoWorkspace::GetDatabaseCount
- AFXDAO/CDaoWorkspace::GetDatabaseInfo
- AFXDAO/CDaoWorkspace::GetIniPath
- AFXDAO/CDaoWorkspace::GetIsolateODBCTrans
- AFXDAO/CDaoWorkspace::GetLoginTimeout
- AFXDAO/CDaoWorkspace::GetName
- AFXDAO/CDaoWorkspace::GetUserName
- AFXDAO/CDaoWorkspace::GetVersion
- AFXDAO/CDaoWorkspace::GetWorkspaceCount
- AFXDAO/CDaoWorkspace::GetWorkspaceInfo
- AFXDAO/CDaoWorkspace::Idle
- AFXDAO/CDaoWorkspace::IsOpen
- AFXDAO/CDaoWorkspace::Open
- AFXDAO/CDaoWorkspace::RepairDatabase
- AFXDAO/CDaoWorkspace::Rollback
- AFXDAO/CDaoWorkspace::SetDefaultPassword
- AFXDAO/CDaoWorkspace::SetDefaultUser
- AFXDAO/CDaoWorkspace::SetIniPath
- AFXDAO/CDaoWorkspace::SetIsolateODBCTrans
- AFXDAO/CDaoWorkspace::SetLoginTimeout
- AFXDAO/CDaoWorkspace::m_pDAOWorkspace
helpviewer_keywords:
- CDaoWorkspace [MFC], CDaoWorkspace
- CDaoWorkspace [MFC], Append
- CDaoWorkspace [MFC], BeginTrans
- CDaoWorkspace [MFC], Close
- CDaoWorkspace [MFC], CommitTrans
- CDaoWorkspace [MFC], CompactDatabase
- CDaoWorkspace [MFC], Create
- CDaoWorkspace [MFC], GetDatabaseCount
- CDaoWorkspace [MFC], GetDatabaseInfo
- CDaoWorkspace [MFC], GetIniPath
- CDaoWorkspace [MFC], GetIsolateODBCTrans
- CDaoWorkspace [MFC], GetLoginTimeout
- CDaoWorkspace [MFC], GetName
- CDaoWorkspace [MFC], GetUserName
- CDaoWorkspace [MFC], GetVersion
- CDaoWorkspace [MFC], GetWorkspaceCount
- CDaoWorkspace [MFC], GetWorkspaceInfo
- CDaoWorkspace [MFC], Idle
- CDaoWorkspace [MFC], IsOpen
- CDaoWorkspace [MFC], Open
- CDaoWorkspace [MFC], RepairDatabase
- CDaoWorkspace [MFC], Rollback
- CDaoWorkspace [MFC], SetDefaultPassword
- CDaoWorkspace [MFC], SetDefaultUser
- CDaoWorkspace [MFC], SetIniPath
- CDaoWorkspace [MFC], SetIsolateODBCTrans
- CDaoWorkspace [MFC], SetLoginTimeout
- CDaoWorkspace [MFC], m_pDAOWorkspace
ms.assetid: 64f60de6-4df1-4d4a-a65b-c489b5257d52
ms.openlocfilehash: c1d235035cee9342c8c54c7aaa4e05a96d5a37e3
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303475"
---
# <a name="cdaoworkspace-class"></a>Klasa CDaoWorkspace

Zarządza nazwaną, chronioną hasłem sesją bazy danych z logowania do wylogowania przez pojedynczego użytkownika. Obiekty DAO są obsługiwane przez pakiet Office 2013. Element DAO 3,6 jest wersją ostateczną i jest uznawany za przestarzały.

## <a name="syntax"></a>Składnia

```
class CDaoWorkspace : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoWorkspace::CDaoWorkspace](#cdaoworkspace)|Konstruuje obiekt obszaru roboczego. Następnie Wywołaj `Create` lub `Open`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoWorkspace:: Append](#append)|Dołącza nowo utworzony obszar roboczy do kolekcji obszarów roboczych aparatu bazy danych.|
|[CDaoWorkspace::BeginTrans](#begintrans)|Rozpoczyna nową transakcję, która ma zastosowanie do wszystkich baz danych otwartych w obszarze roboczym.|
|[CDaoWorkspace:: Close](#close)|Zamyka obszar roboczy i wszystkie obiekty, które zawiera. Oczekujące transakcje są wycofywane.|
|[CDaoWorkspace::CommitTrans](#committrans)|Kończy bieżącą transakcję i zapisuje zmiany.|
|[CDaoWorkspace::CompactDatabase](#compactdatabase)|Kompaktuje lub duplikuje bazę danych.|
|[CDaoWorkspace:: Create](#create)|Tworzy nowy obiekt obszaru roboczego DAO.|
|[CDaoWorkspace::GetDatabaseCount](#getdatabasecount)|Zwraca liczbę obiektów DAO Database w kolekcji baz danych obszaru roboczego.|
|[CDaoWorkspace::GetDatabaseInfo](#getdatabaseinfo)|Zwraca informacje o określonej bazie danych DAO zdefiniowanej w kolekcji baz danych obszaru roboczego.|
|[CDaoWorkspace::GetIniPath](#getinipath)|Zwraca lokalizację ustawień inicjalizacji aparatu bazy danych Microsoft Jet w rejestrze systemu Windows.|
|[CDaoWorkspace::GetIsolateODBCTrans](#getisolateodbctrans)|Zwraca wartość wskazującą, czy wiele transakcji obejmujących to samo źródło danych ODBC jest izolowanych za pośrednictwem wymuszonych wielu połączeń ze źródłem danych.|
|[CDaoWorkspace::GetLoginTimeout](#getlogintimeout)|Zwraca liczbę sekund przed wystąpieniem błędu, gdy użytkownik próbuje zalogować się do bazy danych ODBC.|
|[CDaoWorkspace:: GetName](#getname)|Zwraca zdefiniowaną przez użytkownika nazwę obiektu obszaru roboczego.|
|[CDaoWorkspace:: GetUserName](#getusername)|Zwraca nazwę użytkownika określoną podczas tworzenia obszaru roboczego. To jest nazwa właściciela obszaru roboczego.|
|[CDaoWorkspace:: GetVersion](#getversion)|Zwraca ciąg zawierający wersję aparatu bazy danych skojarzonego z obszarem roboczym.|
|[CDaoWorkspace::GetWorkspaceCount](#getworkspacecount)|Zwraca liczbę obiektów obszaru roboczego DAO w kolekcji obszarów roboczych aparatu bazy danych.|
|[CDaoWorkspace::GetWorkspaceInfo](#getworkspaceinfo)|Zwraca informacje o określonym obszarze roboczym DAO zdefiniowanym w kolekcji obszarów roboczych aparatu bazy danych.|
|[CDaoWorkspace::Idle](#idle)|Umożliwia aparatowi bazy danych wykonywanie zadań w tle.|
|[CDaoWorkspace:: IsOpen](#isopen)|Zwraca wartość różną od zera, jeśli obszar roboczy jest otwarty.|
|[CDaoWorkspace:: Open](#open)|Jawnie otwiera obiekt obszaru roboczego skojarzony z domyślnym obszarem roboczym DAO.|
|[CDaoWorkspace::RepairDatabase](#repairdatabase)|Podejmuje próbę naprawienia uszkodzonej bazy danych.|
|[CDaoWorkspace:: Rollback](#rollback)|Zamyka bieżącą transakcję i nie zapisuje zmian.|
|[CDaoWorkspace::SetDefaultPassword](#setdefaultpassword)|Ustawia hasło używane przez aparat bazy danych podczas tworzenia obiektu obszaru roboczego bez określonego hasła.|
|[CDaoWorkspace::SetDefaultUser](#setdefaultuser)|Ustawia nazwę użytkownika używaną przez aparat bazy danych podczas tworzenia obiektu obszaru roboczego bez określonej nazwy użytkownika.|
|[CDaoWorkspace::SetIniPath](#setinipath)|Ustawia lokalizację ustawień inicjalizacji aparatu bazy danych Microsoft Jet w rejestrze systemu Windows.|
|[CDaoWorkspace::SetIsolateODBCTrans](#setisolateodbctrans)|Określa, czy wiele transakcji obejmujących to samo źródło danych ODBC jest izolowanych przez wymuszenie wielu połączeń ze źródłem danych.|
|[CDaoWorkspace::SetLoginTimeout](#setlogintimeout)|Ustawia liczbę sekund przed wystąpieniem błędu, gdy użytkownik próbuje zalogować się do źródła danych ODBC.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDaoWorkspace::m_pDAOWorkspace](#m_pdaoworkspace)|Wskazuje podstawowy obiekt obszaru roboczego DAO.|

## <a name="remarks"></a>Uwagi

W większości przypadków nie będziesz potrzebować wielu obszarów roboczych i nie będzie konieczne tworzenie jawnych obiektów obszaru roboczego. Po otwarciu bazy danych i obiektów zestawu rekordów są one używane w domyślnym obszarze roboczym DAO. Jednak w razie konieczności można uruchomić wiele sesji jednocześnie przez utworzenie dodatkowych obiektów obszaru roboczego. Każdy obiekt obszaru roboczego może zawierać wiele obiektów Open Database w swoich własnych kolekcjach baz danych. W MFC, obszar roboczy jest przede wszystkim menedżerem transakcji, co umożliwia określenie zestawu otwartych baz danych w tej samej "przestrzeni transakcji".

> [!NOTE]
>  Klasy bazy danych DAO różnią się od klas baz danych MFC opartych na Open Database Connectivity (ODBC). Wszystkie nazwy klas baz danych DAO mają prefiks "CDao". Ogólnie rzecz biorąc, klasy MFC oparte na obiektach DAO są bardziej możliwością niż klasy MFC oparte na ODBC. Klasy oparte na DAO uzyskują dostęp do danych za pośrednictwem aparatu bazy danych Microsoft Jet, w tym sterowników ODBC. Obsługują one również operacje języka definicji danych (DDL), takie jak tworzenie baz danych i Dodawanie tabel i pól za pośrednictwem klas, bez konieczności bezpośredniego wywoływania obiektów DAO.

## <a name="capabilities"></a>możliwość

`CDaoWorkspace` klasy oferuje następujące elementy:

- Jawny dostęp, w razie potrzeby, do domyślnego obszaru roboczego, tworzony przez inicjowanie aparatu bazy danych. Zwykle używasz domyślnego obszaru roboczego DAO niejawnie przez tworzenie bazy danych i obiektów zestawu rekordów.

- Obszar transakcji, w którym transakcje są stosowane do wszystkich baz danych otwartych w obszarze roboczym. Można utworzyć dodatkowe obszary robocze do zarządzania oddzielnymi miejscami do obsługi transakcji.

- Interfejs z wieloma właściwościami aparatu bazy danych Microsoft Jet (zobacz statyczne funkcje członkowskie). Otwieranie lub tworzenie obszaru roboczego lub wywoływanie statycznej funkcji członkowskiej przed otwarciem lub utworzeniem, inicjowanie aparatu bazy danych.

- Dostęp do kolekcji obszarów roboczych aparatu bazy danych, w której są przechowywane wszystkie aktywne obszary robocze, które zostały do niej dołączone. Możesz również tworzyć i współpracować z obszarami roboczymi bez konieczności dołączania ich do kolekcji.

## <a name="security"></a>Zabezpieczenia

MFC nie implementuje kolekcji użytkowników i grup w programie DAO, które są używane na potrzeby kontroli zabezpieczeń. Jeśli potrzebujesz tych aspektów obiektów DAO, musisz je zaprogramować przez bezpośrednie wywołania interfejsów DAO. Aby uzyskać więcej informacji, zobacz [Uwagi techniczne 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="usage"></a>Użycie

Klasy `CDaoWorkspace` można użyć do:

- Jawnie Otwórz domyślny obszar roboczy.

   Zwykle korzystanie z domyślnego obszaru roboczego jest niejawne — podczas otwierania nowych obiektów [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) . Może jednak być konieczne uzyskanie dostępu do niego jawnie — na przykład w celu uzyskania dostępu do właściwości aparatu bazy danych lub kolekcji obszarów roboczych. Zobacz "niejawne użycie domyślnego obszaru roboczego" poniżej.

- Utwórz nowe obszary robocze. Połącz [się](#append) , jeśli chcesz dodać je do kolekcji obszarów roboczych.

- Otwórz istniejący obszar roboczy w kolekcji obszarów roboczych.

Tworzenie nowego obszaru roboczego, który nie istnieje jeszcze w kolekcji obszarów roboczych, jest opisany w obszarze [Tworzenie](#create) elementu członkowskiego. Obiekty obszaru roboczego nie są w żaden sposób utrwalane między sesjami aparatu datababase. Jeśli aplikacja łączy elementy MFC statycznie, zakończenie aplikacji odinicjuje aparat bazy danych. Jeśli aplikacja łączy się z MFC dynamicznie, aparat bazy danych jest niezainicjowany, gdy biblioteka MFC DLL zostanie zwolniona.

Jawne otworzenie domyślnego obszaru roboczego lub otwarcie istniejącego obszaru roboczego w kolekcji obszarów roboczych jest opisane w obszarze [Otwórz](#open) funkcję członkowską.

Zakończ sesję obszaru roboczego, zamykając obszar roboczy za pomocą funkcji [Zamknij](#close) element członkowski. `Close` zamyka wszystkie bazy danych, które nie zostały wcześniej zamknięte, wycofywanie wszelkich niezatwierdzonych transakcji.

## <a name="transactions"></a>Transakcje

DAO zarządza transakcjami na poziomie obszaru roboczego; w związku z tym transakcje w obszarze roboczym z wieloma otwartymi bazami danych mają zastosowanie do wszystkich baz danych. Na przykład jeśli dwie bazy danych mają niezatwierdzone aktualizacje i wywołajesz [CommitTrans](#committrans), wszystkie aktualizacje zostaną zatwierdzone. Jeśli chcesz ograniczyć liczbę transakcji do pojedynczej bazy danych, wymagany jest osobny obiekt obszaru roboczego.

## <a name="implicit-use-of-the-default-workspace"></a>Niejawne użycie domyślnego obszaru roboczego

MFC używa domyślnego obszaru roboczego DAO niejawnie w następujących okolicznościach:

- W przypadku utworzenia nowego obiektu `CDaoDatabase`, ale nie do wykonania za pomocą istniejącego obiektu `CDaoWorkspace`, MFC tworzy tymczasowy obiekt obszaru roboczego, który odnosi się do domyślnego obszaru roboczego DAO. Jeśli to zrobisz dla wielu baz danych, wszystkie obiekty bazy danych są skojarzone z domyślnym obszarem roboczym. Możesz uzyskać dostęp do obszaru roboczego bazy danych za pomocą elementu członkowskiego danych `CDaoDatabase`.

- Podobnie, jeśli utworzysz obiekt `CDaoRecordset` bez podawania wskaźnika do obiektu `CDaoDatabase`, MFC tworzy tymczasowy obiekt bazy danych i, według rozszerzenia, tymczasowy obiekt obszaru roboczego. Możesz uzyskać dostęp do bazy danych zestawu rekordów i pośrednio jej obszaru roboczego za pomocą elementu członkowskiego danych `CDaoRecordset`.

## <a name="other-operations"></a>Inne operacje

Dostępne są również inne operacje bazy danych, takie jak naprawa uszkodzonej bazy danych lub kompaktowanie bazy danych.

Aby uzyskać informacje o wywoływaniu obiektów DAO bezpośrednio i o zabezpieczeniach DAO, zobacz [Uwagi techniczne 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CDaoWorkspace`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao. h

##  <a name="append"></a>CDaoWorkspace:: Append

Wywołaj tę funkcję elementu członkowskiego po wywołaniu metody [Create](#create).

```
virtual void Append();
```

### <a name="remarks"></a>Uwagi

`Append` dołącza nowo utworzony obiekt obszaru roboczego do kolekcji obszarów roboczych aparatu bazy danych. Obszary robocze nie są zachowywane między sesjami aparatu bazy danych; są one przechowywane tylko w pamięci, a nie na dysku. Nie trzeba dołączać obszaru roboczego; Jeśli tego nie zrobisz, można nadal z niej korzystać.

Dołączany obszar roboczy pozostaje w kolekcji obszarów roboczych w aktywnym stanie otwartym, dopóki nie zostanie wywołana funkcja [zamykającego](#close) elementu członkowskiego.

Aby uzyskać powiązane informacje, zobacz temat "Metoda dołączania" w pomocy DAO.

##  <a name="begintrans"></a>CDaoWorkspace::BeginTrans

Wywołaj tę funkcję elementu członkowskiego, aby zainicjować transakcję.

```
void BeginTrans();
```

### <a name="remarks"></a>Uwagi

Po podaniu `BeginTrans`aktualizacje wprowadzane do danych lub struktury bazy danych zaczną obowiązywać po zatwierdzeniu transakcji. Ze względu na to, że obszar roboczy definiuje pojedynczy obszar transakcji, transakcja dotyczy wszystkich otwartych baz danych w obszarze roboczym. Istnieją dwa sposoby wykonania transakcji:

- Wywołaj funkcję elementu członkowskiego [CommitTrans](#committrans) , aby zatwierdzić transakcję i zapisać zmiany w źródle danych.

- Lub wywołaj funkcję [wycofywania](#rollback) elementu członkowskiego, aby anulować transakcję.

Zamknięcie obiektu obszaru roboczego lub obiektu bazy danych w czasie oczekiwania transakcji powoduje wycofanie wszystkich oczekujących transakcji.

Jeśli konieczne jest odizolowanie transakcji na jednym źródle danych ODBC od tych w innym źródle danych ODBC, zobacz funkcja członkowska [SetIsolateODBCTrans](#setisolateodbctrans) .

##  <a name="cdaoworkspace"></a>CDaoWorkspace::CDaoWorkspace

Konstruuje obiekt `CDaoWorkspace`.

```
CDaoWorkspace();
```

### <a name="remarks"></a>Uwagi

Po skonstruowaniu C++ obiektu dostępne są dwie opcje:

- Wywołaj funkcję [Open](#open) member obiektu, aby otworzyć domyślny obszar roboczy lub otworzyć istniejący obiekt w kolekcji obszarów roboczych.

- Lub wywołaj funkcję [Utwórz](#create) element członkowski obiektu, aby utworzyć nowy obiekt obszaru roboczego DAO. Ta funkcja jawnie uruchamia nową sesję obszaru roboczego, do której można się odwoływać za pośrednictwem obiektu `CDaoWorkspace`. Po wywołaniu `Create`można wywołać [dołączenie](#append) , jeśli chcesz dodać obszar roboczy do kolekcji obszarów roboczych aparatu bazy danych.

Zapoznaj się z omówieniem klasy [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) , aby uzyskać informacje o tym, kiedy należy jawnie utworzyć obiekt `CDaoWorkspace`. Zazwyczaj można używać obszarów roboczych utworzonych niejawnie podczas otwierania obiektu [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) bez określania obszaru roboczego lub po otwarciu obiektu [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) bez określania obiektu bazy danych. Obiekty MFC DAO utworzone w ten sposób używają domyślnego obszaru roboczego DAO, który jest tworzony raz i ponownie używany.

Aby zwolnić obszar roboczy i zawarte w nim obiekty, wywołaj funkcję [zamykania](#close) elementu członkowskiego obiektu obszaru roboczego.

##  <a name="close"></a>CDaoWorkspace:: Close

Wywołaj tę funkcję elementu członkowskiego, aby zamknąć obiekt obszaru roboczego.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Zamknięcie otwartego obiektu obszaru roboczego powoduje zwolnienie bazowego obiektu DAO i, jeśli obszar roboczy jest członkiem kolekcji obszarów roboczych, usuwa go z kolekcji. Wywoływanie `Close` jest dobrym sposobem programowania.

> [!CAUTION]
>  Zamknięcie obiektu obszaru roboczego zamyka wszystkie otwarte bazy danych w obszarze roboczym. Powoduje to, że wszystkie zestawy rekordów są otwarte w bazach danych, a wszystkie oczekujące edycje lub aktualizacje zostaną wycofane. Aby uzyskać powiązane informacje, zobacz funkcje członkowskie [CDaoDatabase:: Close](../../mfc/reference/cdaodatabase-class.md#close), [CDaoRecordset:: Close](../../mfc/reference/cdaorecordset-class.md#close), [CDaoTableDef::](../../mfc/reference/cdaotabledef-class.md#close)Close i [CDaoQueryDef::](../../mfc/reference/cdaoquerydef-class.md#close) Close.

Obiekty obszaru roboczego nie są trwałe; istnieją one tylko wtedy, gdy istnieją odwołania do nich. Oznacza to, że po zakończeniu sesji aparatu bazy danych obszar roboczy i jego kolekcja baz danych nie są zachowywane. Należy je ponownie utworzyć dla następnej sesji, otwierając obszar roboczy i bazy danych ponownie.

Aby uzyskać powiązane informacje, zobacz temat "metoda Close" w pomocy DAO.

##  <a name="committrans"></a>CDaoWorkspace::CommitTrans

Wywołaj tę funkcję elementu członkowskiego, aby zatwierdzić transakcję — Zapisz grupę edycji i aktualizacji w co najmniej jednej bazie danych w obszarze roboczym.

```
void CommitTrans();
```

### <a name="remarks"></a>Uwagi

Transakcja składa się z serii zmian danych lub struktury bazy danych, rozpoczynając od wywołania [BeginTrans](#begintrans). Po zakończeniu transakcji Zatwierdź ją lub Wycofaj (Anuluj zmiany) z [wycofywaniem](#rollback). Domyślnie, bez transakcji, aktualizacje rekordów są zatwierdzane natychmiast. Wywołanie `BeginTrans` powoduje, że zobowiązania aktualizacji są opóźniane do momentu wywołania `CommitTrans`.

> [!CAUTION]
>  W ramach jednego obszaru roboczego transakcje są zawsze globalne dla obszaru roboczego i nie są ograniczone tylko do jednej bazy danych lub zestawu rekordów. Jeśli wykonujesz operacje na więcej niż jednej bazie danych lub zestawach rekordów w ramach transakcji obszaru roboczego, `CommitTrans` zatwierdzi wszystkie oczekujące aktualizacje i `Rollback` przywraca wszystkie operacje na tych bazach danych i zestawach rekordów.

Po zamknięciu bazy danych lub obszaru roboczego z oczekującymi transakcjami są wycofywane wszystkie transakcje.

> [!NOTE]
>  Nie jest to dwufazowe mechanizm zatwierdzania. Jeśli jedna aktualizacja nie zostanie zatwierdzona, inne nadal będą zatwierdzane.

##  <a name="compactdatabase"></a>CDaoWorkspace::CompactDatabase

Wywołaj tę funkcję elementu członkowskiego, aby skompaktować określony program Microsoft Jet (. MDB).

```
static void PASCAL CompactDatabase(
    LPCTSTR lpszSrcName,
    LPCTSTR lpszDestName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int nOptions = 0);

static void PASCAL CompactDatabase(
    LPCTSTR lpszSrcName,
    LPCTSTR lpszDestName,
    LPCTSTR lpszLocale,
    int nOptions,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parametry

*lpszSrcName*<br/>
Nazwa istniejącej, zamkniętej bazy danych. Może to być pełna ścieżka i nazwa pliku, na przykład "C:\\\MYDB. MDB ". Jeśli nazwa pliku ma rozszerzenie, należy je określić. Jeśli sieć obsługuje ujednolicone konwencje nazewnictwa (UNC), można również określić ścieżkę sieciową, taką jak "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB ". (W ciągach ścieżki są wymagane podwójne ukośniki odwrotne, ponieważ "\\" C++ jest znakiem ucieczki).

*lpszDestName*<br/>
Pełna ścieżka kompaktowej bazy danych, która jest tworzona. Możesz również określić ścieżkę sieciową, tak jak w przypadku *lpszSrcName*. Nie można użyć argumentu *lpszDestName* do określenia tego samego pliku bazy danych jako *lpszSrcName*.

*lpszPassword*<br/>
Hasło używane, gdy chcesz skompaktować chronioną hasłem bazę danych. Należy pamiętać, że w przypadku korzystania z wersji `CompactDatabase`, która pobiera hasło, należy podać wszystkie parametry. Ponadto, ponieważ jest to parametr Connect, wymaga specjalnego formatowania w następujący sposób:; PWD = *lpszPassword*. Na przykład:; PWD = "szczęśliwa". (Wiodący średnik jest wymagany).

*lpszLocale*<br/>
Wyrażenie ciągu używane do określenia kolejności sortowania na potrzeby tworzenia *lpszDestName*. Jeśli ten argument zostanie pominięty przez zaakceptowanie wartości domyślnej `dbLangGeneral` (patrz poniżej), ustawienia regionalne nowej bazy danych są takie same jak w przypadku starej bazy danych. Możliwe wartości to:

- `dbLangGeneral` angielski, niemiecki, francuski, portugalski, włoski i nowoczesny hiszpański

- `dbLangArabic` arabski

- `dbLangCyrillic` rosyjski

- `dbLangCzech` Czeska

- `dbLangDutch` holenderski

- `dbLangGreek` grecki

- `dbLangHebrew` hebrajski

- `dbLangHungarian` węgierski

- `dbLangIcelandic` islandzki

- `dbLangNordic` Języki nordyckie (tylko wersja 1,0 aparatu bazy danych Microsoft Jet)

- `dbLangNorwdan` norweski i duński

- `dbLangPolish` Polski

- `dbLangSpanish` tradycyjny hiszpański

- `dbLangSwedfin` szwedzki i fiński

- `dbLangTurkish` turecki

*nOptions*<br/>
Wskazuje co najmniej jedną opcję dla docelowej bazy danych *lpszDestName*. Jeśli ten argument zostanie pominięty przez zaakceptowanie wartości domyślnej, *lpszDestName* będzie mieć to samo szyfrowanie i taką samą wersję jak *lpszSrcName*. Możesz połączyć opcję `dbEncrypt` lub `dbDecrypt` z jedną z opcji wersji za pomocą operatora bitowego lub. Możliwe wartości, które określają format bazy danych, a nie wersję aparatu bazy danych, to:

- `dbEncrypt` Szyfruj bazę danych podczas kompaktowania.

- `dbDecrypt` odszyfrować bazy danych podczas kompaktowania.

- `dbVersion10` utworzyć bazę danych, która korzysta z aparatu bazy danych Microsoft Jet w wersji 1,0 podczas kompaktowania.

- `dbVersion11` utworzyć bazę danych, która korzysta z aparatu bazy danych Microsoft Jet w wersji 1,1 podczas kompaktowania.

- `dbVersion20` utworzyć bazę danych, która korzysta z aparatu bazy danych Microsoft Jet w wersji 2,0 podczas kompaktowania.

- `dbVersion30` utworzyć bazę danych, która korzysta z aparatu bazy danych Microsoft Jet w wersji 3,0 podczas kompaktowania.

W argumencie opcje można użyć `dbEncrypt` lub `dbDecrypt`, aby określić, czy podczas kompaktowania ma być szyfrowana czy odszyfrowana. W przypadku pominięcia stałej szyfrowania lub dołączenia obu `dbDecrypt` i `dbEncrypt`, *lpszDestName* będzie miało takie samo szyfrowanie jak *lpszSrcName*. Możesz użyć jednej z stałych wersji w argumencie opcji, aby określić wersję formatu danych dla kompaktowej bazy danych. Ta stała ma wpływ tylko na wersję formatu danych *lpszDestName*. Można określić tylko jedną stałą wersji. W przypadku pominięcia stałej wersji *lpszDestName* będzie mieć taką samą wersję jak *lpszSrcName*. *LpszDestName* można skompaktować tylko do wersji, która jest taka sama lub nowsza niż *lpszSrcName*.

> [!CAUTION]
>  Jeśli baza danych nie jest zaszyfrowana, możliwe jest nawet w przypadku zaimplementowania zabezpieczeń użytkownika/hasła, aby bezpośrednio odczytać plik dysku binarnego stanowiący bazę danych.

### <a name="remarks"></a>Uwagi

Podczas zmieniania danych w bazie danych, plik bazy danych może zostać pofragmentowany i użycie większej ilości miejsca na dysku. Okresowo należy kompaktować bazę danych, aby zdefragmentować plik bazy danych. Kompaktowanie bazy danych jest zazwyczaj mniejsze. Możesz również zmienić kolejność sortowania, szyfrowanie lub wersję formatu danych podczas kopiowania i kompaktowania bazy danych.

> [!CAUTION]
>  Funkcja członkowska `CompactDatabase` nie będzie poprawnie skonwertować kompletnej bazy danych programu Microsoft Access z jednej wersji na inną. Konwertowany jest tylko format danych. Obiekty zdefiniowane przez program Microsoft Access, takie jak formularze i raporty, nie są konwertowane. Jednak dane są poprawnie konwertowane.

> [!TIP]
>  Możesz również użyć `CompactDatabase`, aby skopiować plik bazy danych.

Aby uzyskać więcej informacji na temat kompaktowania baz danych, zobacz temat "Metoda CompactDatabase" w pomocy DAO.

##  <a name="create"></a>CDaoWorkspace:: Create

Wywołaj tę funkcję elementu członkowskiego, aby utworzyć nowy obiekt obszaru roboczego DAO i skojarzyć go z obiektem MFC `CDaoWorkspace`.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszUserName,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Ciąg z maksymalnie 14 znakami, które jednoznacznie nazywają nowym obiektem obszaru roboczego. Należy podać nazwę. Aby uzyskać powiązane informacje, zobacz temat "Nazwa właściwości" w pomocy DAO.

*lpszUserName*<br/>
Nazwa użytkownika właściciela obszaru roboczego. Aby uzyskać wymagania, zobacz parametr *lpszDefaultUser* w funkcji członkowskiej [SetDefaultUser](#setdefaultuser) . Aby uzyskać powiązane informacje, zobacz temat "UserName Property" w pomocy DAO.

*lpszPassword*<br/>
Hasło dla nowego obiektu obszaru roboczego. Hasło może składać się z maksymalnie 14 znaków i może zawierać dowolny znak z wyjątkiem ASCII 0 (null). W hasłach jest rozróżniana wielkość liter. Aby uzyskać powiązane informacje, zobacz temat "Właściwość hasła" w pomocy DAO.

### <a name="remarks"></a>Uwagi

Ogólny proces tworzenia:

1. Utwórz obiekt [CDaoWorkspace](#cdaoworkspace) .

1. Wywołaj funkcję członkowską `Create` obiektu, aby utworzyć podstawowy obszar roboczy DAO. Należy określić nazwę obszaru roboczego.

1. Opcjonalnie możesz wywołać [dołączenie](#append) , jeśli chcesz dodać obszar roboczy do kolekcji obszarów roboczych aparatu bazy danych. Możesz współpracować z obszarem roboczym bez dołączania go.

Po wywołaniu `Create` obiekt obszaru roboczego jest w stanie otwartym, gotowy do użycia. Nie Wywołaj `Open` po `Create`. Nie dzwonimy `Create`, jeśli obszar roboczy już istnieje w kolekcji obszarów roboczych. `Create` inicjuje aparat bazy danych, jeśli nie został jeszcze zainicjowany dla aplikacji.

##  <a name="getdatabasecount"></a>CDaoWorkspace::GetDatabaseCount

Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę obiektów bazy danych DAO w kolekcji baz danych obszaru roboczego — liczbę otwartych baz danych w obszarze roboczym.

```
short GetDatabaseCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba otwartych baz danych w obszarze roboczym.

### <a name="remarks"></a>Uwagi

`GetDatabaseCount` jest przydatne, jeśli zachodzi potrzeba przepętlenia między wszystkimi zdefiniowanymi bazami danych w kolekcji baz danych obszaru roboczego. Aby uzyskać informacje o danej bazie danych w kolekcji, zobacz [GetDatabaseInfo](#getdatabaseinfo). Typowym zastosowaniem jest wywołanie `GetDatabaseCount` dla liczby otwartych baz danych, a następnie użycie tej liczby jako indeksu pętli dla powtarzających się wywołań do `GetDatabaseInfo`.

##  <a name="getdatabaseinfo"></a>CDaoWorkspace::GetDatabaseInfo

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać różne rodzaje informacji o bazie danych otwartej w obszarze roboczym.

```
void GetDatabaseInfo(
    int nIndex,
    CDaoDatabaseInfo& dbinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetDatabaseInfo(
    LPCTSTR lpszName,
    CDaoDatabaseInfo& dbinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks (liczony od zera) obiektu bazy danych w kolekcji baz danych obszaru roboczego dla wyszukiwania według indeksu.

*dbinfo*<br/>
Odwołanie do obiektu [CDaoDatabaseInfo —](../../mfc/reference/cdaodatabaseinfo-structure.md) , który zwraca żądane informacje.

*dwInfoOptions*<br/>
Opcje określające, które informacje o bazie danych mają zostać pobrane. Dostępne opcje są wymienione tutaj wraz z tym, co powodują, że funkcja zwraca:

- AFX_DAO_PRIMARY_INFO (domyślnie) nazwa, aktualizowalne, transakcje

- AFX_DAO_SECONDARY_INFO informacje podstawowe oraz: wersja, kolejność sortowania, limit czasu zapytania

- AFX_DAO_ALL_INFO informacje podstawowe i pomocnicze oraz: Connect

*lpszName*<br/>
Nazwa obiektu bazy danych dla wyszukiwania według nazwy. Nazwa jest ciągiem zawierającym maksymalnie 14 znaków, które jednoznacznie nazywają nowym obiektem obszaru roboczego.

### <a name="remarks"></a>Uwagi

Jedna wersja funkcji pozwala wyszukiwać bazę danych według indeksu. Inna wersja pozwala wyszukiwać bazę danych według nazwy.

Aby uzyskać opis informacji zwracanych w temacie *dbInfo*, zobacz [CDaoDatabaseInfo —](../../mfc/reference/cdaodatabaseinfo-structure.md) Structure. Ta struktura zawiera elementy członkowskie, które odpowiadają elementom informacji wymienionych powyżej w opisie *dwInfoOptions*. Jeśli zażądasz informacji na jednym poziomie, uzyskasz również informacje na temat wszystkich wcześniejszych poziomów.

##  <a name="getinipath"></a>CDaoWorkspace::GetIniPath

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać lokalizację ustawień inicjalizacji aparatu bazy danych Microsoft Jet w rejestrze systemu Windows.

```
static CString PASCAL GetIniPath();
```

### <a name="return-value"></a>Wartość zwracana

[CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierający lokalizację rejestru.

### <a name="remarks"></a>Uwagi

Możesz użyć lokalizacji, aby uzyskać informacje o ustawieniach dla aparatu bazy danych. Zwrócone informacje są w rzeczywistości nazwą podklucza rejestru.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość IniPath" i "Dostosowywanie ustawień rejestru systemu Windows na potrzeby dostępu do danych" w pomocy DAO.

##  <a name="getisolateodbctrans"></a>CDaoWorkspace::GetIsolateODBCTrans

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać bieżącą wartość właściwości DAO IsolateODBCTrans dla obszaru roboczego.

```
BOOL GetIsolateODBCTrans();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli transakcje ODBC są izolowane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

W niektórych sytuacjach może być konieczne wykonanie wielu jednoczesnych transakcji w tej samej bazie danych ODBC. W tym celu należy otworzyć osobny obszar roboczy dla każdej transakcji. Należy pamiętać, że chociaż każdy obszar roboczy może mieć własne połączenie ODBC z bazą danych, spowalnia to wydajność systemu. Ponieważ izolacja transakcji nie jest zwykle wymagana, połączenia ODBC z wielu obiektów obszaru roboczego otwartych przez tego samego użytkownika są domyślnie udostępniane.

Niektóre serwery ODBC, takie jak Microsoft SQL Server, nie umożliwiają jednoczesnych transakcji w ramach jednego połączenia. Jeśli musisz mieć więcej niż jedną transakcję jednocześnie w zależności od tej bazy danych, ustaw Właściwość IsolateODBCTrans na wartość TRUE w każdym obszarze roboczym zaraz po jej otwarciu. Powoduje to wymuszenie oddzielnego połączenia ODBC dla każdego obszaru roboczego.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość IsolateODBCTrans" w pomocy DAO.

##  <a name="getlogintimeout"></a>CDaoWorkspace::GetLoginTimeout

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać bieżącą wartość właściwości DAO LoginTimeout dla obszaru roboczego.

```
static short PASCAL GetLoginTimeout();
```

### <a name="return-value"></a>Wartość zwracana

Liczba sekund przed wystąpieniem błędu podczas próby zalogowania się do bazy danych ODBC.

### <a name="remarks"></a>Uwagi

Ta wartość reprezentuje liczbę sekund przed wystąpieniem błędu podczas próby zalogowania się do bazy danych ODBC. Domyślne ustawienie LoginTimeout to 20 sekund. Gdy LoginTimeout jest ustawiona na 0, nie ma limitu czasu i komunikacja ze źródłem danych może przestać odpowiadać.

Podczas próby zalogowania się do bazy danych ODBC, takiej jak Microsoft SQL Server, połączenie może zakończyć się niepowodzeniem z powodu błędów sieciowych lub serwer nie działa. Zamiast czekać na połączenie domyślne przez 20 sekund, możesz określić, jak długo aparat bazy danych ma oczekiwać przed wygenerowaniem błędu. Logowanie na serwerze odbywa się niejawnie jako część wielu różnych zdarzeń, takich jak uruchamianie zapytania w bazie danych serwera zewnętrznego.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość LoginTimeout" w pomocy DAO.

##  <a name="getname"></a>CDaoWorkspace:: GetName

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać zdefiniowaną przez użytkownika nazwę obiektu obszaru roboczego DAO bazowego obiektu `CDaoWorkspace`.

```
CString GetName();
```

### <a name="return-value"></a>Wartość zwracana

[CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierający zdefiniowaną przez użytkownika nazwę obiektu obszaru roboczego DAO.

### <a name="remarks"></a>Uwagi

Nazwa jest przydatna do uzyskiwania dostępu do obiektu obszaru roboczego DAO w kolekcji obszarów roboczych aparatu bazy danych według nazwy.

Aby uzyskać powiązane informacje, zobacz temat "Nazwa właściwości" w pomocy DAO.

##  <a name="getusername"></a>CDaoWorkspace:: GetUserName

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać nazwę właściciela obszaru roboczego.

```
CString GetUserName();
```

### <a name="return-value"></a>Wartość zwracana

[CString](../../atl-mfc-shared/reference/cstringt-class.md) reprezentujący właściciela obiektu obszaru roboczego.

### <a name="remarks"></a>Uwagi

Aby uzyskać lub ustawić uprawnienia dla właściciela obszaru roboczego, wywołaj DAO bezpośrednio, aby sprawdzić ustawienie właściwości uprawnienia. Określa, jakie uprawnienia użytkownik ma. Aby można było korzystać z uprawnień, wymagany jest SYSTEM. Plik MDA.

Aby uzyskać informacje dotyczące bezpośredniego wywoływania obiektów DAO, zobacz [Uwagi techniczne 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md). Aby uzyskać powiązane informacje, zobacz temat "UserName Property" w pomocy DAO.

##  <a name="getversion"></a>CDaoWorkspace:: GetVersion

Wywołaj tę funkcję elementu członkowskiego, aby określić używaną wersję aparatu bazy danych Microsoft Jet.

```
static CString PASCAL GetVersion();
```

### <a name="return-value"></a>Wartość zwracana

[CString](../../atl-mfc-shared/reference/cstringt-class.md) wskazujący wersję aparatu bazy danych skojarzoną z obiektem.

### <a name="remarks"></a>Uwagi

Zwracana wartość reprezentuje numer wersji w postaci "główna. pomocnicza"; na przykład "3,0". Numer wersji produktu (na przykład 3,0) składa się z numeru wersji (3), kropki i numeru wydania (0).

Aby uzyskać powiązane informacje, zobacz temat "Właściwość wersji" w pomocy DAO.

##  <a name="getworkspacecount"></a>CDaoWorkspace::GetWorkspaceCount

Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę obiektów obszaru roboczego DAO w kolekcji obszarów roboczych aparatu bazy danych.

```
short GetWorkspaceCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba otwartych obszarów roboczych w kolekcji obszarów roboczych.

### <a name="remarks"></a>Uwagi

Ta liczba nie obejmuje żadnych otwartych obszarów roboczych, które nie są dołączane do kolekcji. `GetWorkspaceCount` jest przydatne, jeśli zachodzi potrzeba przepętlenia przez wszystkie zdefiniowane obszary robocze w kolekcji obszarów roboczych. Aby uzyskać informacje na temat danego obszaru roboczego w kolekcji, zobacz [GetWorkspaceInfo](#getworkspaceinfo). Typowym użyciem jest wywołanie `GetWorkspaceCount` dla liczby otwartych obszarów roboczych, a następnie użycie tego numeru jako indeksu pętli dla powtarzających się wywołań do `GetWorkspaceInfo`.

##  <a name="getworkspaceinfo"></a>CDaoWorkspace::GetWorkspaceInfo

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać różne rodzaje informacji o obszarze roboczym otwartym w sesji.

```
void GetWorkspaceInfo(
    int nIndex,
    CDaoWorkspaceInfo& wkspcinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetWorkspaceInfo(
    LPCTSTR lpszName,
    CDaoWorkspaceInfo& wkspcinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks (liczony od zera) obiektu bazy danych w kolekcji obszarów roboczych w celu wyszukania według indeksu.

*wkspcinfo*<br/>
Odwołanie do obiektu [CDaoWorkspaceInfo —](../../mfc/reference/cdaoworkspaceinfo-structure.md) , który zwraca żądane informacje.

*dwInfoOptions*<br/>
Opcje określające, które informacje o obszarze roboczym mają być pobierane. Dostępne opcje są wymienione tutaj wraz z tym, co powodują, że funkcja zwraca:

- Nazwa AFX_DAO_PRIMARY_INFO (wartość domyślna)

- AFX_DAO_SECONDARY_INFO informacje podstawowe oraz: Nazwa użytkownika

- AFX_DAO_ALL_INFO informacje podstawowe i pomocnicze oraz: Izoluj ODBCTrans

*lpszName*<br/>
Nazwa obiektu obszaru roboczego dla wyszukiwania według nazwy. Nazwa jest ciągiem zawierającym maksymalnie 14 znaków, które jednoznacznie nazywają nowym obiektem obszaru roboczego.

### <a name="remarks"></a>Uwagi

Aby uzyskać opis informacji zwracanych w *wkspcinfo*, zobacz [CDaoWorkspaceInfo —](../../mfc/reference/cdaoworkspaceinfo-structure.md) Structure. Ta struktura zawiera elementy członkowskie, które odpowiadają elementom informacji wymienionych powyżej w opisie *dwInfoOptions*. Jeśli zażądasz informacji na jednym poziomie, uzyskasz również informacje o wcześniejszych poziomach.

##  <a name="idle"></a>CDaoWorkspace:: Idle

Wywołaj `Idle`, aby zapewnić aparatowi bazy danych możliwość wykonywania zadań w tle, które mogą nie być aktualne z powodu intensywnego przetwarzania danych.

```
static void PASCAL Idle(int nAction = dbFreeLocks);
```

### <a name="parameters"></a>Parametry

*Nwynik akcji*<br/>
Akcja do wykonania podczas przetwarzania bezczynności. Obecnie jedyną prawidłową akcją jest `dbFreeLocks`.

### <a name="remarks"></a>Uwagi

Jest to często prawdziwe w przypadku wielu użytkowników i wielozadaniowych środowisk, w których nie jest wystarczająco dużo czasu przetwarzania w tle, aby zachować wszystkie rekordy w bieżącym zestawie rekordów.

> [!NOTE]
>  Wywoływanie `Idle` nie jest konieczne w przypadku baz danych utworzonych przy użyciu wersji 3,0 aparatu bazy danych Microsoft Jet. Używaj `Idle` tylko dla baz danych utworzonych przy użyciu wcześniejszych wersji.

Zazwyczaj blokady odczytu są usuwane, a dane w lokalnych zestawach rekordów typu dynamiczny typ są aktualizowane tylko wtedy, gdy nie są wykonywane żadne inne akcje (w tym ruchy myszy). W przypadku okresowego wywoływania `Idle`należy udostępnić aparat bazy danych z czasem, aby uzyskać informacje na temat zadań przetwarzania w tle, zwalniając niepotrzebne blokady odczytu. Określanie stałej `dbFreeLocks` jako argumentu opóźnia przetwarzanie do momentu wydania wszystkich blokad odczytu.

Ta funkcja członkowska nie jest wymagana w środowiskach jednego użytkownika, chyba że jest uruchomionych wiele wystąpień aplikacji. Funkcja członkowska `Idle` może zwiększyć wydajność w środowisku wielodostępnym, ponieważ wymusza, aby aparat bazy danych opróżniał dane na dysk, zwalniając blokady w pamięci. Można również zwolnić blokady odczytu przez utworzenie części operacji transakcji.

Aby uzyskać powiązane informacje, zobacz temat "Metoda bezczynności" w pomocy DAO.

##  <a name="isopen"></a>CDaoWorkspace:: IsOpen

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy obiekt `CDaoWorkspace` jest otwarty — to znaczy czy obiekt MFC został zainicjowany przez wywołanie do [otwarcia](#open) lub wywołanie do [utworzenia](#create).

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli obiekt obszaru roboczego jest otwarty; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Można wywołać dowolną z funkcji Członkowskich obszaru roboczego, który jest w stanie otwartym.

##  <a name="m_pdaoworkspace"></a>CDaoWorkspace:: m_pDAOWorkspace

Wskaźnik do bazowego obiektu obszaru roboczego DAO.

### <a name="remarks"></a>Uwagi

Użyj tego elementu członkowskiego danych, jeśli potrzebujesz bezpośredniego dostępu do bazowego obiektu DAO. Można wywołać interfejsy obiektu DAO za pomocą tego wskaźnika.

Aby uzyskać informacje na temat bezpośredniego dostępu do obiektów DAO, zobacz [Uwagi techniczne 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

##  <a name="open"></a>CDaoWorkspace:: Open

Jawnie otwiera obiekt obszaru roboczego skojarzony z domyślnym obszarem roboczym DAO.

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Nazwa obiektu obszaru roboczego DAO do otwarcia — ciąg z maksymalnie 14 znakami, które jednoznacznie nazywają obszar roboczy. Zaakceptuj wartość domyślną NULL, aby jawnie otworzyć domyślny obszar roboczy. Wymagania dotyczące nazewnictwa znajdują się w temacie *lpszName* Parameter for [Create](#create). Aby uzyskać powiązane informacje, zobacz temat "Nazwa właściwości" w pomocy DAO.

### <a name="remarks"></a>Uwagi

Po skonstruowaniu obiektu `CDaoWorkspace` Wywołaj tę funkcję elementu członkowskiego, aby wykonać jedną z następujących czynności:

- Jawnie Otwórz domyślny obszar roboczy. Przekaż wartość NULL dla *lpszName*.

- Otwórz istniejący obiekt `CDaoWorkspace`, składową kolekcji obszarów roboczych według nazwy. Przekaż prawidłową nazwę istniejącego obiektu obszaru roboczego.

`Open` umieszcza obiekt obszaru roboczego w stanie otwartym, a także inicjuje aparat bazy danych, jeśli nie został jeszcze zainicjowany dla aplikacji.

Chociaż wiele `CDaoWorkspace` funkcji Członkowskich można wywołać tylko po otwarciu obszaru roboczego, następujące funkcje członkowskie, które działają w aparacie bazy danych, są dostępne po utworzeniu C++ obiektu, ale przed wywołaniem `Open`:

||||
|-|-|-|
|[Utwórz](#create)|[GetVersion](#getversion)|[SetDefaultUser](#setdefaultuser)|
|[GetIniPath](#getinipath)|[Okresie](#idle)|[SetIniPath](#setinipath)|
|[GetLoginTimeout](#getlogintimeout)|[SetDefaultPassword](#setdefaultpassword)|[SetLoginTimeout](#setlogintimeout)|

##  <a name="repairdatabase"></a>CDaoWorkspace::RepairDatabase

Wywołaj tę funkcję elementu członkowskiego, jeśli chcesz podjąć próbę naprawienia uszkodzonej bazy danych, która uzyskuje dostęp do aparatu bazy danych Microsoft Jet.

```
static void PASCAL RepairDatabase(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Ścieżka i nazwa pliku dla istniejącego pliku bazy danych aparatu Microsoft Jet. Jeśli pominięto ścieżkę, przeszukiwany jest tylko bieżący katalog. Jeśli system obsługuje ujednoliconą konwencję nazewnictwa (UNC), można również określić ścieżkę sieciową, taką jak: "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB ". (W ciągu ścieżki są wymagane podwójne ukośniki odwrotne, ponieważ "\\" jest C++ znakiem ucieczki).

### <a name="remarks"></a>Uwagi

Przed naprawieniem należy zamknąć bazę danych określoną przez *lpszName* . W środowisku wielodostępnym inni użytkownicy nie mogą mieć otwartych *lpszName* podczas naprawiania go. Jeśli *lpszName* nie jest zamknięty lub nie jest dostępny do wyłącznego użytku, wystąpi błąd.

Ta funkcja członkowska podejmuje próbę naprawienia bazy danych, która została oznaczona jako potencjalnie uszkodzona przez niekompletną operację zapisu. Taka sytuacja może wystąpić, jeśli aplikacja wykorzystująca aparat bazy danych Microsoft Jet zostanie nieoczekiwanie zamknięta z powodu awarii lub sprzętu komputerowego. Jeśli wykonasz operację i wywołajesz funkcję [zamykającego](../../mfc/reference/cdaodatabase-class.md#close) elementu członkowskiego lub aplikacja zostanie zamknięta w zwykły sposób, baza danych nie zostanie oznaczona jako prawdopodobnie uszkodzona.

> [!NOTE]
>  Po naprawieniu bazy danych warto również skompaktować ją przy użyciu funkcji składowej [CompactDatabase](#compactdatabase) , aby zdefragmentować plik i odzyskać miejsce na dysku.

Aby uzyskać więcej informacji na temat naprawiania baz danych, zobacz temat "Metoda RepairDatabase" w pomocy DAO.

##  <a name="rollback"></a>CDaoWorkspace:: Rollback

Wywołaj tę funkcję elementu członkowskiego, aby zakończyć bieżącą transakcję i przywrócić wszystkie bazy danych w obszarze roboczym do ich stanu przed rozpoczęciem transakcji.

```
void Rollback();
```

### <a name="remarks"></a>Uwagi

> [!CAUTION]
>  W ramach jednego obiektu obszaru roboczego transakcje są zawsze globalne dla obszaru roboczego i nie są ograniczone tylko do jednej bazy danych lub zestawu rekordów. Jeśli wykonujesz operacje na więcej niż jednej bazie danych lub zestawach rekordów w ramach transakcji obszaru roboczego, `Rollback` przywraca wszystkie operacje na wszystkich bazach danych i zestawach rekordów.

Jeśli zamkniesz obiekt obszaru roboczego bez zapisywania lub wycofywania oczekujących transakcji, transakcje są automatycznie wycofywane. Jeśli wywołasz [CommitTrans](#committrans) lub `Rollback` bez uprzedniego wywołania [BeginTrans](#begintrans), wystąpi błąd.

> [!NOTE]
>  Po rozpoczęciu transakcji aparat bazy danych rejestruje jego operacje w pliku przechowywanym w katalogu określonym przez zmienną środowiskową TEMP na stacji roboczej. Jeśli plik dziennika transakcji spowoduje wyczerpanie dostępnego magazynu na dysku TYMCZASOWYm, aparat bazy danych może zgłosić `CDaoException` (błąd DAO 2004). W tym momencie, jeśli wywołasz `CommitTrans`, zostanie zatwierdzona nieokreślona liczba operacji, ale pozostałe nieukończone operacje zostaną utracone, a operacja musi zostać uruchomiona ponownie. Wywołanie `Rollback` zwalnia dziennik transakcji i wycofuje wszystkie operacje w transakcji.

##  <a name="setdefaultpassword"></a>CDaoWorkspace::SetDefaultPassword

Wywołaj tę funkcję elementu członkowskiego, aby ustawić domyślne hasło używane przez aparat bazy danych podczas tworzenia obiektu obszaru roboczego bez określonego hasła.

```
static void PASCAL SetDefaultPassword(LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parametry

*lpszPassword*<br/>
Hasło domyślne. Hasło może składać się z maksymalnie 14 znaków i może zawierać dowolny znak z wyjątkiem ASCII 0 (null). W hasłach jest rozróżniana wielkość liter.

### <a name="remarks"></a>Uwagi

Ustawione domyślne hasło dotyczy nowych obszarów roboczych utworzonych po wywołaniu. Podczas tworzenia kolejnych obszarów roboczych nie trzeba określać hasła w wywołaniu [Create](#create) .

Aby użyć tej funkcji elementu członkowskiego:

1. Konstruowanie obiektu `CDaoWorkspace`, ale nie wywoływanie `Create`.

1. Wywołaj `SetDefaultPassword` i, jeśli chcesz, [SetDefaultUser](#setdefaultuser).

1. Wywołaj `Create` dla tego obiektu obszaru roboczego lub kolejne z nich bez określania hasła.

Domyślnie właściwość DefaultUser jest ustawiona na wartość "admin", a właściwość DefaultPassword jest ustawiona na pusty ciąg ("").

Aby uzyskać więcej informacji o zabezpieczeniach, zapoznaj się z tematem "Właściwość Permissions" w pomocy DAO. Aby uzyskać powiązane informacje, zobacz tematy "Właściwość DefaultPassword" i "DefaultUser Property" w pomocy DAO.

##  <a name="setdefaultuser"></a>CDaoWorkspace::SetDefaultUser

Wywołaj tę funkcję elementu członkowskiego, aby ustawić domyślną nazwę użytkownika używaną przez aparat bazy danych podczas tworzenia obiektu obszaru roboczego bez określonej nazwy użytkownika.

```
static void PASCAL SetDefaultUser(LPCTSTR lpszDefaultUser);
```

### <a name="parameters"></a>Parametry

*lpszDefaultUser*<br/>
Domyślna nazwa użytkownika. Nazwa użytkownika może składać się z maksymalnie 1-20 znaków i zawierać znaki alfanumeryczne, znaki akcentowane, cyfry, spacje i symbole z wyjątkiem: "(znaki cudzysłowu),/(ukośnik odwrotny), \ (ukośnik odwrotny), \[ \] (nawias),: &#124; (dwukropek), (potok), \< (znak mniejszości), > (znak większości), + (znak plus), = (znak równości); (średnik),, (przecinek), (znak zapytania), \* (gwiazdka), spacje wiodące i znaki kontrolne (ASCII 00 do ASCII 31). Aby uzyskać powiązane informacje, zobacz temat "UserName Property" w pomocy DAO.

### <a name="remarks"></a>Uwagi

Wybrana domyślna nazwa użytkownika ma zastosowanie do nowych obszarów roboczych utworzonych po wywołaniu. Podczas tworzenia kolejnych obszarów roboczych nie trzeba określać nazwy użytkownika w wywołaniu metody [Create](#create) .

Aby użyć tej funkcji elementu członkowskiego:

1. Konstruowanie obiektu `CDaoWorkspace`, ale nie wywoływanie `Create`.

1. Wywołaj `SetDefaultUser` i, jeśli chcesz, [SetDefaultPassword](#setdefaultpassword).

1. Wywołaj `Create` dla tego obiektu obszaru roboczego lub kolejnych z nich, bez określania nazwy użytkownika.

Domyślnie właściwość DefaultUser jest ustawiona na wartość "admin", a właściwość DefaultPassword jest ustawiona na pusty ciąg ("").

Aby uzyskać powiązane informacje, zobacz tematy "Właściwość DefaultUser" i "DefaultPassword Property" w pomocy DAO.

##  <a name="setinipath"></a>CDaoWorkspace::SetIniPath

Wywołaj tę funkcję elementu członkowskiego, aby określić lokalizację ustawień rejestru systemu Windows dla aparatu bazy danych Microsoft Jet.

```
static void PASCAL SetIniPath(LPCTSTR lpszRegistrySubKey);
```

### <a name="parameters"></a>Parametry

*lpszRegistrySubkey*<br/>
Ciąg zawierający nazwę podklucza rejestru systemu Windows dla lokalizacji ustawień lub parametrów aparatu bazy danych Microsoft Jet wymaganych do instalowalnych baz danych ISAM.

### <a name="remarks"></a>Uwagi

Wywołaj `SetIniPath` tylko wtedy, gdy musisz określić ustawienia specjalne. Aby uzyskać więcej informacji, zobacz temat "Właściwość IniPath" w pomocy DAO.

> [!NOTE]
>  Wywołaj `SetIniPath` podczas instalacji aplikacji, a nie w momencie uruchomienia aplikacji. Aby można było otworzyć wszystkie obszary robocze, bazy danych lub zestawy rekordów, należy wywołać `SetIniPath`. w przeciwnym razie MFC zgłasza wyjątek.

Za pomocą tego mechanizmu można skonfigurować aparat bazy danych przy użyciu ustawień rejestru dostarczonych przez użytkownika. Zakres tego atrybutu jest ograniczony do aplikacji i nie można go zmienić bez ponownego uruchomienia aplikacji.

##  <a name="setisolateodbctrans"></a>CDaoWorkspace::SetIsolateODBCTrans

Wywołaj tę funkcję elementu członkowskiego, aby ustawić wartość właściwości DAO IsolateODBCTrans dla obszaru roboczego.

```
void SetIsolateODBCTrans(BOOL bIsolateODBCTrans);
```

### <a name="parameters"></a>Parametry

*bIsolateODBCTrans*<br/>
Jeśli chcesz rozpocząć izolowanie transakcji ODBC, przekaż wartość TRUE. Jeśli chcesz zatrzymać izolowanie transakcji ODBC, przekaż wartość FALSE.

### <a name="remarks"></a>Uwagi

W niektórych sytuacjach może być konieczne wykonanie wielu jednoczesnych transakcji w tej samej bazie danych ODBC. W tym celu należy otworzyć osobny obszar roboczy dla każdej transakcji. Mimo że każdy obszar roboczy może mieć własne połączenie ODBC z bazą danych, zmniejsza to wydajność systemu. Ponieważ izolacja transakcji nie jest zwykle wymagana, połączenia ODBC z wielu obiektów obszaru roboczego otwartych przez tego samego użytkownika są domyślnie udostępniane.

Niektóre serwery ODBC, takie jak Microsoft SQL Server, nie umożliwiają jednoczesnych transakcji w ramach jednego połączenia. Jeśli musisz mieć więcej niż jedną transakcję jednocześnie w zależności od tej bazy danych, ustaw Właściwość IsolateODBCTrans na wartość TRUE w każdym obszarze roboczym zaraz po jej otwarciu. Powoduje to wymuszenie oddzielnego połączenia ODBC dla każdego obszaru roboczego.

##  <a name="setlogintimeout"></a>CDaoWorkspace::SetLoginTimeout

Wywołaj tę funkcję elementu członkowskiego, aby ustawić wartość właściwości DAO LoginTimeout dla obszaru roboczego.

```
static void PASCAL SetLoginTimeout(short nSeconds);
```

### <a name="parameters"></a>Parametry

*nSeconds*<br/>
Liczba sekund przed wystąpieniem błędu podczas próby zalogowania się do bazy danych ODBC.

### <a name="remarks"></a>Uwagi

Ta wartość reprezentuje liczbę sekund przed wystąpieniem błędu podczas próby zalogowania się do bazy danych ODBC. Domyślne ustawienie LoginTimeout to 20 sekund. Gdy LoginTimeout jest ustawiona na 0, nie ma limitu czasu i komunikacja ze źródłem danych może przestać odpowiadać.

Podczas próby zalogowania się do bazy danych ODBC, takiej jak Microsoft SQL Server, połączenie może zakończyć się niepowodzeniem z powodu błędów sieciowych lub serwer nie działa. Zamiast czekać na połączenie domyślne przez 20 sekund, możesz określić, jak długo aparat bazy danych ma oczekiwać przed wygenerowaniem błędu. Logowanie na serwerze odbywa się niejawnie jako część wielu różnych zdarzeń, takich jak uruchamianie zapytania w bazie danych serwera zewnętrznego. Wartość limitu czasu jest określana na podstawie bieżącego ustawienia właściwości LoginTimeout.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość LoginTimeout" w pomocy DAO.

## <a name="see-also"></a>Zobacz także

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)<br/>
[Klasa CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)<br/>
[Klasa CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)<br/>
[Klasa CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)<br/>
[Klasa CDaoException](../../mfc/reference/cdaoexception-class.md)
