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
ms.openlocfilehash: 52aaa4970ef483988194691eb6b870cbfe51f494
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377115"
---
# <a name="cdaoworkspace-class"></a>Klasa CDaoWorkspace

Zarządza nazwaną, chroniną hasłem sesją bazy danych od logowania do wylogowywania przez jednego użytkownika. DAO jest obsługiwany przez pakiet Office 2013. DAO 3.6 jest ostateczną wersją i jest uważana za przestarzałą.

## <a name="syntax"></a>Składnia

```
class CDaoWorkspace : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoWorkspace::CDaoWorkspace](#cdaoworkspace)|Konstruuje obiekt obszaru roboczego. Następnie zadzwoń `Create` `Open`lub .|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoWorkspace::Dołącz](#append)|Dołącza nowo utworzony obszar roboczy do kolekcji Workspaces aparatu bazy danych.|
|[Obszar roboczy CDao::BeginTrans](#begintrans)|Rozpoczyna nową transakcję, która ma zastosowanie do wszystkich baz danych otwartych w obszarze roboczym.|
|[CDaoWorkspace::Zamknij](#close)|Zamyka obszar roboczy i wszystkie obiekty, które zawiera. Oczekujące transakcje są przywracane.|
|[CDaoWorkspace::CommitTrans](#committrans)|Kończy bieżącą transakcję i zapisuje zmiany.|
|[CDaoWorkspace::CompactDatabase](#compactdatabase)|Kompaktywuje (lub duplikuje) bazę danych.|
|[Obszar CDaoWorkspace::Tworzenie](#create)|Tworzy nowy obiekt obszaru roboczego DAO.|
|[Obszar roboczy CDao::GetDatabaseCount](#getdatabasecount)|Zwraca liczbę obiektów bazy danych DAO w kolekcji Bazy danych obszaru roboczego.|
|[CDaoWorkspace::GetDatabaseInfo](#getdatabaseinfo)|Zwraca informacje o określonej bazie danych DAO zdefiniowanej w kolekcji Bazy danych obszaru roboczego.|
|[Obszar roboczy CDao::GetIniPath](#getinipath)|Zwraca lokalizację ustawień inicjowania aparatu bazy danych Microsoft Jet w rejestrze systemu Windows.|
|[CDaoWorkspace::GetIsolateODBCTrans](#getisolateodbctrans)|Zwraca wartość, która wskazuje, czy wiele transakcji, które obejmują to samo źródło danych ODBC są izolowane przez wymuszone wiele połączeń ze źródłem danych.|
|[CDaoWorkspace::GetLoginTimeout](#getlogintimeout)|Zwraca liczbę sekund przed wystąpieniem błędu, gdy użytkownik próbuje zalogować się do bazy danych ODBC.|
|[Obszar roboczy CDao::GetName](#getname)|Zwraca nazwę zdefiniowaną przez użytkownika obiektu obszaru roboczego.|
|[Obszar roboczy CDao::GetUserName](#getusername)|Zwraca nazwę użytkownika określoną podczas tworzenia obszaru roboczego. Jest to nazwa właściciela obszaru roboczego.|
|[CDaoWorkspace::GetVersion](#getversion)|Zwraca ciąg zawierający wersję aparatu bazy danych skojarzoną z obszarem roboczym.|
|[CDaoWorkspace::GetWorkspaceCount](#getworkspacecount)|Zwraca liczbę obiektów obszaru roboczego DAO w kolekcji Workspaces aparatu bazy danych.|
|[CDaoWorkspace::GetWorkspaceInfo](#getworkspaceinfo)|Zwraca informacje o określonym obszarze roboczym DAO zdefiniowanym w kolekcji Workspaces aparatu bazy danych.|
|[CDaoWorkspace::Idle](#idle)|Umożliwia aparatowi bazy danych wykonywanie zadań w tle.|
|[CDaoWorkspace::IsOpen](#isopen)|Zwraca wartość niezerowa, jeśli obszar roboczy jest otwarty.|
|[CDaoWorkspace::Otwórz](#open)|Jawnie otwiera obiekt obszaru roboczego skojarzony z domyślnym obszarem roboczym DAO.|
|[CDaoWorkspace::RepairDatabase](#repairdatabase)|Próbuje naprawić uszkodzoną bazę danych.|
|[OBSZAR ROBOCZY CD::Wycofywanie](#rollback)|Kończy bieżącą transakcję i nie zapisuje zmian.|
|[CDaoWorkspace::SetDefaultPassword](#setdefaultpassword)|Ustawia hasło używane przez aparat bazy danych podczas tworzenia obiektu obszaru roboczego bez określonego hasła.|
|[CDaoWorkspace::SetDefaultUser](#setdefaultuser)|Ustawia nazwę użytkownika używaną przez aparat bazy danych podczas tworzenia obiektu obszaru roboczego bez określonej nazwy użytkownika.|
|[Obszar roboczy CDao::SetIniPath](#setinipath)|Ustawia lokalizację ustawień inicjowania aparatu bazy danych Microsoft Jet w rejestrze systemu Windows.|
|[CDaoWorkspace::SetIsolateODBCTrans](#setisolateodbctrans)|Określa, czy wiele transakcji, które obejmują to samo źródło danych ODBC są izolowane przez wymuszanie wielu połączeń ze źródłem danych.|
|[Obszar roboczy CDao::SetLoginTimeout](#setlogintimeout)|Ustawia liczbę sekund przed wystąpieniem błędu, gdy użytkownik próbuje zalogować się do źródła danych ODBC.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDaoWorkspace::m_pDAOWorkspace](#m_pdaoworkspace)|Wskazuje podstawowy obiekt obszaru roboczego DAO.|

## <a name="remarks"></a>Uwagi

W większości przypadków nie będzie potrzebnych wielu obszarów roboczych i nie trzeba będzie tworzyć jawnych obiektów obszaru roboczego; po otwarciu bazy danych i obiektów akcesetów używają domyślnego obszaru roboczego DAO. Jednak w razie potrzeby można uruchomić wiele sesji naraz, tworząc dodatkowe obiekty obszaru roboczego. Każdy obiekt obszaru roboczego może zawierać wiele otwartych obiektów bazy danych w swojej kolekcji bazy danych. W MFC obszar roboczy jest przede wszystkim menedżer transakcji, określając zestaw otwartych baz danych w tym samym "przestrzeni transakcji".

> [!NOTE]
> Klasy bazy danych DAO różnią się od klas bazy danych MFC na podstawie łączności otwartej bazy danych (ODBC). Wszystkie nazwy klas bazy danych DAO mają prefiks "CDao". Ogólnie rzecz biorąc klasy MFC oparte na DAO są bardziej zdolne niż klasy MFC na podstawie ODBC. Klasy oparte na DAO uzyskują dostęp do danych za pośrednictwem aparatu bazy danych Microsoft Jet, w tym sterowników ODBC. Obsługują one również operacje języka DDL (Data Definition Language), takie jak tworzenie baz danych i dodawanie tabel i pól za pośrednictwem klas, bez konieczności bezpośredniego wywoływania DAO.

## <a name="capabilities"></a>Możliwości

Klasa `CDaoWorkspace` zapewnia następujące informacje:

- Jawny dostęp, w razie potrzeby, do domyślnego obszaru roboczego, utworzone przez zainicjowanie aparatu bazy danych. Zazwyczaj domyślny obszar roboczy DAO jest niejawnie przez tworzenie baz danych i obiektów akcesetów.

- Przestrzeń transakcji, w której transakcje mają zastosowanie do wszystkich baz danych otwartych w obszarze roboczym. Można utworzyć dodatkowe obszary robocze do zarządzania oddzielnymi przestrzeniami transakcji.

- Interfejs do wielu właściwości podstawowego aparatu bazy danych Microsoft Jet (zobacz funkcje statycznego elementu członkowskiego). Otwarcie lub utworzenie obszaru roboczego lub wywołanie funkcji statycznego elementu członkowskiego przed otwarciem lub utworzeniem inicjuje aparat bazy danych.

- Dostęp do kolekcji Workspaces aparatu bazy danych, która przechowuje wszystkie aktywne obszary robocze, które zostały do niego dołączone. Można również tworzyć i pracować z obszarami roboczymi bez dołączania ich do kolekcji.

## <a name="security"></a>Zabezpieczenia

MFC nie implementuje użytkowników i grup kolekcji w DAO, które są używane do kontroli zabezpieczeń. Jeśli potrzebujesz tych aspektów DAO, musisz zaprogramować je samodzielnie za pośrednictwem bezpośrednich połączeń do interfejsów DAO. Aby uzyskać więcej informacji, zobacz [uwaga techniczna 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="usage"></a>Sposób użycia

Klasy można `CDaoWorkspace` użyć do:

- Jawnie otwórz domyślny obszar roboczy.

   Zazwyczaj użycie domyślnego obszaru roboczego jest niejawne — po otwarciu nowych obiektów [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) lub [CDaoRecordset.](../../mfc/reference/cdaorecordset-class.md) Ale może być konieczne, aby uzyskać do niego jawnie — na przykład, aby uzyskać dostęp do właściwości aparatu bazy danych lub Workspaces kolekcji. Zobacz "Niejawne użycie domyślnego obszaru roboczego" poniżej.

- Tworzenie nowych obszarów roboczych. Zadzwoń [Dołącz,](#append) jeśli chcesz dodać je do kolekcji Obszary robocze.

- Otwórz istniejący obszar roboczy w kolekcji Obszary robocze.

Tworzenie nowego obszaru roboczego, który jeszcze nie istnieje w kolekcji Workspaces jest opisane w funkcji [Utwórz](#create) element członkowski. Obiekty obszaru roboczego nie utrzymują się w żaden sposób między sesjami aparatu bazy danych. Jeśli aplikacja łączy MFC statycznie, zakończenie aplikacji uninitializes aparatu bazy danych. Jeśli aplikacja łączy się z MFC dynamicznie, aparat bazy danych jest niezainicjowany, gdy biblioteka DLL MFC jest zwalniana.

Jawnie otwarcie domyślnego obszaru roboczego lub otwarcie istniejącego obszaru roboczego w kolekcji Obszary robocze jest opisane w funkcji [Otwórz](#open) element członkowski.

Zakończ sesję obszaru roboczego, zamykając obszar roboczy za pomocą funkcji [Zamknij](#close) element członkowski. `Close`zamyka wszystkie bazy danych, które nie zostały wcześniej zamknięte, cofanie wszelkich niezakończonej transakcji.

## <a name="transactions"></a>Transakcje

DAO zarządza transakcjami na poziomie obszaru roboczego; w związku z tym transakcje w obszarze roboczym z wieloma otwartymi bazami danych mają zastosowanie do wszystkich baz danych. Na przykład jeśli dwie bazy danych mają niezakończone aktualizacje i wywołasz [CommitTrans,](#committrans)wszystkie aktualizacje są zatwierdzane. Jeśli chcesz ograniczyć transakcje do pojedynczej bazy danych, potrzebujesz dla niego osobnego obiektu obszaru roboczego.

## <a name="implicit-use-of-the-default-workspace"></a>Niejawne korzystanie z domyślnego obszaru roboczego

MFC używa domyślnego obszaru roboczego DAO niejawnie w następujących okolicznościach:

- Jeśli utworzysz `CDaoDatabase` nowy obiekt, ale nie `CDaoWorkspace` zrobisz tego za pośrednictwem istniejącego obiektu, MFC utworzy tymczasowy obiekt obszaru roboczego, który odpowiada domyślnemu obszarowi roboczemu DAO. Jeśli to zrobisz dla wielu baz danych, wszystkie obiekty bazy danych są skojarzone z domyślnym obszarem roboczym. Dostęp do obszaru roboczego bazy `CDaoDatabase` danych można uzyskać za pośrednictwem elementu członkowskiego danych.

- Podobnie w przypadku utworzenia `CDaoRecordset` obiektu bez dostarczania `CDaoDatabase` wskaźnika do obiektu, MFC tworzy obiekt tymczasowej bazy danych i, co za tym idzie, tymczasowy obiekt obszaru roboczego. Można uzyskać dostęp do bazy danych zestaw rekordów, a `CDaoRecordset` pośrednio jego obszaru roboczego, za pośrednictwem elementu członkowskiego danych.

## <a name="other-operations"></a>Inne operacje

Dostępne są również inne operacje bazy danych, takie jak naprawa uszkodzonej bazy danych lub kompaktowanie bazy danych.

Aby uzyskać informacje na temat bezpośredniego wywoływania DAO i zabezpieczeń DAO, zobacz [Uwaga techniczna 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CDaoWorkspace`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="cdaoworkspaceappend"></a><a name="append"></a>CDaoWorkspace::Dołącz

Wywołanie tej funkcji członkowskiej po [wywołaniu Create](#create).

```
virtual void Append();
```

### <a name="remarks"></a>Uwagi

`Append`dołącza nowo utworzony obiekt obszaru roboczego do kolekcji Workspaces aparatu bazy danych. Obszary robocze nie utrzymują się między sesjami aparatu bazy danych; są one przechowywane tylko w pamięci, a nie na dysku. Nie trzeba dołączać obszaru roboczego; jeśli nie, nadal możesz z niego korzystać.

Dołączona przestrzeń robocza pozostaje w workspaces kolekcji, w stanie aktywnym, otwarte, dopóki nie wywołasz jego [Zamknij](#close) funkcji elementu członkowskiego.

Aby uzyskać powiązane informacje, zobacz temat "Dołącz metodę" w Pomocy DAO.

## <a name="cdaoworkspacebegintrans"></a><a name="begintrans"></a>Obszar roboczy CDao::BeginTrans

Wywołanie tej funkcji elementu członkowskiego, aby zainicjować transakcję.

```
void BeginTrans();
```

### <a name="remarks"></a>Uwagi

Po wywołaniu `BeginTrans`, aktualizacje wprowadzone do danych lub struktury bazy danych zaa uczynek podczas zatwierdzania transakcji. Ponieważ obszar roboczy definiuje pojedynczą przestrzeń transakcji, transakcja ma zastosowanie do wszystkich otwartych baz danych w obszarze roboczym. Transakcja można wykonać na dwa sposoby:

- Wywołanie CommitTrans funkcji [członkowskiej,](#committrans) aby zatwierdzić transakcję i zapisać zmiany w źródle danych.

- Lub wywołać funkcję elementu członkowskiego [wycofywania,](#rollback) aby anulować transakcję.

Zamykanie obiektu obszaru roboczego lub obiektu bazy danych, gdy transakcja jest oczekująca, wycofuje wszystkie oczekujące transakcje.

Jeśli chcesz izolować transakcje na jednym źródle danych ODBC od tych na innym źródle danych ODBC, zobacz [SetIsolateODBCTrans](#setisolateodbctrans) funkcji elementu członkowskiego.

## <a name="cdaoworkspacecdaoworkspace"></a><a name="cdaoworkspace"></a>CDaoWorkspace::CDaoWorkspace

Konstruuje `CDaoWorkspace` obiekt.

```
CDaoWorkspace();
```

### <a name="remarks"></a>Uwagi

Po skonstruowaniu obiektu C++ dostępne są dwie opcje:

- Wywołanie funkcji [otwórz](#open) element członkowski obiektu, aby otworzyć domyślny obszar roboczy lub otworzyć istniejący obiekt w kolekcji Workspaces.

- Możesz też wywołać funkcję [create](#create) elementu członkowskiego obiektu, aby utworzyć nowy obiekt obszaru roboczego DAO. To jawnie rozpoczyna nową sesję obszaru roboczego, do `CDaoWorkspace` której można się odwoływać za pośrednictwem obiektu. Po `Create`wywołaniu , można wywołać [Dołącz,](#append) jeśli chcesz dodać obszar roboczy do kolekcji workspaces aparatu bazy danych.

Zobacz omówienie klasy dla [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) informacji o tym, `CDaoWorkspace` kiedy trzeba jawnie utworzyć obiekt. Zazwyczaj używa się obszarów roboczych utworzonych niejawnie podczas otwierania obiektu [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) bez określania obszaru roboczego lub po otwarciu obiektu [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) bez określania obiektu bazy danych. Obiekty DAO MFC utworzone w ten sposób używają domyślnego obszaru roboczego DAO, który jest tworzony raz i ponownie używany.

Aby zwolnić obszar roboczy i jego zawarte obiekty, należy wywołać funkcję [zamknij](#close) element członkowski obiektu obszaru roboczego.

## <a name="cdaoworkspaceclose"></a><a name="close"></a>CDaoWorkspace::Zamknij

Wywołanie tej funkcji elementu członkowskiego, aby zamknąć obiekt obszaru roboczego.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Zamknięcie obiektu otwartego obszaru roboczego zwalnia podstawowy obiekt DAO i, jeśli obszar roboczy jest członkiem kolekcji Workspaces, usuwa go z kolekcji. Wywołanie `Close` jest dobrą praktyką programowania.

> [!CAUTION]
> Zamknięcie obiektu obszaru roboczego zamyka wszystkie otwarte bazy danych w obszarze roboczym. Powoduje to, że wszystkie zestawy rekordów są również otwierane w zamkniętych bazach danych, a wszelkie oczekujące zmiany lub aktualizacje są przywracane. Aby uzyskać informacje pokrewne, zobacz [funkcje elementów członkowskich CDaoDatabase::Zamknij](../../mfc/reference/cdaodatabase-class.md#close), [CDaoRecordset::Zamknij](../../mfc/reference/cdaorecordset-class.md#close), [CDaoTableDef::Close](../../mfc/reference/cdaotabledef-class.md#close)i [CDaoQueryDef::Zamknij](../../mfc/reference/cdaoquerydef-class.md#close) funkcje członkowskie.

Obiekty obszaru roboczego nie są trwałe; istnieją tylko wtedy, gdy istnieją odwołania do nich. Oznacza to, że po zakończeniu sesji aparatu bazy danych obszar roboczy i jego kolekcja baz danych nie są zachowywane. Należy ponownie utworzyć je dla następnej sesji, ponownie otwierając obszar roboczy i bazy danych.

Aby uzyskać powiązane informacje, zobacz temat "Zamknij metodę" w Pomocy DAO.

## <a name="cdaoworkspacecommittrans"></a><a name="committrans"></a>CDaoWorkspace::CommitTrans

Wywołanie tej funkcji elementu członkowskiego, aby zatwierdzić transakcję — zapisz grupę zmian i aktualizacji do jednej lub więcej baz danych w obszarze roboczym.

```
void CommitTrans();
```

### <a name="remarks"></a>Uwagi

Transakcja składa się z serii zmian w danych bazy danych lub jej struktury, począwszy od wywołania [BeginTrans](#begintrans). Po zakończeniu transakcji zatwierdz ją lub wycofaj (anuluj zmiany) za pomocą [przycisku Wycofywanie](#rollback). Domyślnie bez transakcji aktualizacje rekordów są zatwierdzane natychmiast. Wywołanie `BeginTrans` powoduje, że zobowiązanie aktualizacji `CommitTrans`jest opóźnione, dopóki nie zadzwonisz .

> [!CAUTION]
> W ramach jednego obszaru roboczego transakcje są zawsze globalne w obszarze roboczym i nie są ograniczone tylko do jednej bazy danych lub pliku rekordów. Jeśli operacje są wykonywane na więcej niż jednej bazie `CommitTrans` danych lub waletu w ramach transakcji obszaru roboczego, zatwierdza wszystkie oczekujące aktualizacje i `Rollback` przywraca wszystkie operacje w tych bazach danych i zestawy rekordów.

Po zamknięciu bazy danych lub obszaru roboczego z oczekujących transakcji, wszystkie transakcje są przywracane.

> [!NOTE]
> Nie jest to mechanizm zatwierdzania dwufazowego. Jeśli jedna aktualizacja nie zostanie zatwierdzą, inne nadal będą zatwierdzać.

## <a name="cdaoworkspacecompactdatabase"></a><a name="compactdatabase"></a>CDaoWorkspace::CompactDatabase

Wywołanie tej funkcji elementu członkowskiego do kompaktowania określonego programu Microsoft Jet (. bazy danych MDB).

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

*lpszsrcName*<br/>
Nazwa istniejącej, zamkniętej bazy danych. Może to być pełna ścieżka i nazwa pliku,\\takie jak "C: \MYDB. MDB". Jeśli nazwa pliku ma rozszerzenie, należy je określić. Jeśli sieć obsługuje jednolitą konwencję nazewnictwa (UNC), można również\\\\\\określić\\ścieżkę\\sieciową,\\taką jak " \MYSERVER \MYSHARE \MYDIR \MYDB. MDB". (Podwójne ukośnie są wymagane w ciągach\\ścieżki, ponieważ " " jest znakiem ucieczki języka C++).

*lpszDestName*<br/>
Pełna ścieżka zwartej bazy danych, którą tworzysz. Można również określić ścieżkę sieciową, tak jak w *lpszSrcName*. Nie można użyć argumentu *lpszDestName,* aby określić ten sam plik bazy danych co *lpszSrcName*.

*lpszPassword*<br/>
Hasło używane, gdy chcesz skompaktować bazę danych chroniona hasłem. Należy zauważyć, `CompactDatabase` że jeśli używasz wersji, która przyjmuje hasło, należy podać wszystkie parametry. Ponadto, ponieważ jest to parametr connect, wymaga specjalnego formatowania, w następujący sposób: ; PWD = *lpszPassword*. Na przykład: ; PWD="Szczęśliwy". (Wymagany jest średnik wiodący).

*lpszLocale (lpszLocale)*<br/>
Wyrażenie ciągu używane do określania kolejności sortowania w celu utworzenia *pliku lpszDestName*. Jeśli ten argument zostanie pominięty przez `dbLangGeneral` zaakceptowanie wartości domyślnej (zobacz poniżej), ustawienia regionalne nowej bazy danych są takie same jak w starej bazie danych. Możliwe wartości:

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

*nOpcje*<br/>
Wskazuje jedną lub więcej opcji docelowej bazy danych, *lpszDestName*. Jeśli ten argument zostanie pominięty, akceptując wartość domyślną, *lpszDestName* będzie miał takie samo szyfrowanie i tę samą wersję co *lpszSrcName*. Można połączyć `dbEncrypt` `dbDecrypt` lub opcję z jedną z opcji wersji za pomocą operatora bitowego OR. Możliwe wartości, które określają format bazy danych, a nie wersję aparatu bazy danych, są:

- `dbEncrypt`Szyfruj bazę danych podczas kompaktowania.

- `dbDecrypt`Odszyfruj bazę danych podczas kompaktowania.

- `dbVersion10`Utwórz bazę danych, która używa aparatu bazy danych Microsoft Jet w wersji 1.0 podczas kompaktowania.

- `dbVersion11`Utwórz bazę danych, która używa aparatu bazy danych Microsoft Jet w wersji 1.1 podczas kompaktowania.

- `dbVersion20`Utwórz bazę danych, która używa aparatu bazy danych Microsoft Jet w wersji 2.0 podczas kompaktowania.

- `dbVersion30`Utwórz bazę danych, która używa aparatu bazy danych Microsoft Jet w wersji 3.0 podczas kompaktowania.

Można użyć `dbEncrypt` `dbDecrypt` lub w arguracji opcji, aby określić, czy szyfrować lub odszyfrować bazę danych, ponieważ jest skompaktowana. Jeśli pominiesz stałą szyfrowania `dbDecrypt` `dbEncrypt`lub jeśli dołączysz zarówno i *, lpszDestName* będzie miał takie samo szyfrowanie jak *lpszSrcName*. Można użyć jednej ze stałych wersji w argumule opcji, aby określić wersję formatu danych dla zg kompaktowanych baz danych. Ta stała dotyczy tylko wersji formatu danych *lpszDestName*. Można określić tylko jedną stałą wersji. Jeśli pominiesz stałą wersji, *lpszDestName* będzie miał tę samą wersję co *lpszSrcName*. Możesz zwarte *lpszDestName* tylko do wersji, która jest taka sama lub późniejsza niż *lpszSrcName*.

> [!CAUTION]
> Jeśli baza danych nie jest szyfrowana, jest możliwe, nawet jeśli zaimplementujesz zabezpieczenia użytkownika/hasła, aby bezpośrednio odczytać plik dysku binarnego, który stanowi bazę danych.

### <a name="remarks"></a>Uwagi

Podczas zmiany danych w bazie danych plik bazy danych może stać się pofragmentowany i zużywać więcej miejsca na dysku niż jest to konieczne. Okresowo należy skompaktować bazę danych, aby zdefragmentować plik bazy danych. Zgęskiona baza danych jest zwykle mniejsza. Podczas kopiowania i kompaktowania bazy danych można również zmienić kolejność sortowania, szyfrowanie lub wersję formatu danych.

> [!CAUTION]
> Funkcja `CompactDatabase` elementu członkowskiego nie będzie poprawnie konwertować pełną bazę danych programu Microsoft Access z jednej wersji na inną. Konwertowany jest tylko format danych. Obiekty zdefiniowane przez program Microsoft Access, takie jak formularze i raporty, nie są konwertowane. Jednak dane są poprawnie konwertowane.

> [!TIP]
> Można również `CompactDatabase` użyć do skopiowania pliku bazy danych.

Aby uzyskać więcej informacji na temat kompaktowania baz danych, zobacz temat "CompactDatabase Method" w Pomocy DAO.

## <a name="cdaoworkspacecreate"></a><a name="create"></a>Obszar CDaoWorkspace::Tworzenie

Wywołanie tej funkcji elementu członkowskiego, aby utworzyć nowy obiekt `CDaoWorkspace` obszaru roboczego DAO i skojarzyć go z obiektem MFC.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszUserName,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
Ciąg z maksymalnie 14 znakami, który jednoznacznie nazywa nowy obiekt obszaru roboczego. Należy podać nazwę. Aby uzyskać powiązane informacje, zobacz temat "Właściwość nazw" w Pomocy DAO.

*lpszUserName*<br/>
Nazwa użytkownika właściciela obszaru roboczego. Aby uzyskać wymagania, zobacz *lpszDefaultUser* parametr do [SetDefaultUser](#setdefaultuser) funkcji elementu członkowskiego. Aby uzyskać powiązane informacje, zobacz temat "Właściwość UserName" w Pomocy DAO.

*lpszPassword*<br/>
Hasło nowego obiektu obszaru roboczego. Hasło może mieć długość do 14 znaków i może zawierać dowolny znak z wyjątkiem ASCII 0 (null). W hasłach rozróżniana jest wielkość liter. Aby uzyskać powiązane informacje, zobacz temat "Właściwość hasła" w Pomocy DAO.

### <a name="remarks"></a>Uwagi

Ogólny proces tworzenia jest:

1. Konstruuj obiekt [CDaoWorkspace.](#cdaoworkspace)

1. Wywołanie funkcji `Create` elementu członkowskiego obiektu, aby utworzyć podstawowy obszar roboczy DAO. Należy określić nazwę obszaru roboczego.

1. Opcjonalnie wywołać [Dołącz,](#append) jeśli chcesz dodać obszar roboczy do kolekcji obszarów roboczych aparatu bazy danych. Można pracować z obszarem roboczym bez dołączania go.

Po `Create` wywołaniu obiekt obszaru roboczego jest w stanie otwartym, gotowy do użycia. Nie dzwonisz `Open` `Create`po . Nie należy `Create` wywoływać, jeśli obszar roboczy już istnieje w workspaces kolekcji. `Create`inicjuje aparat bazy danych, jeśli nie został jeszcze zainicjowany dla aplikacji.

## <a name="cdaoworkspacegetdatabasecount"></a><a name="getdatabasecount"></a>Obszar roboczy CDao::GetDatabaseCount

Wywołanie tej funkcji elementu członkowskiego, aby pobrać liczbę obiektów bazy danych DAO w kolekcji bazy danych obszaru roboczego — liczba otwartych baz danych w obszarze roboczym.

```
short GetDatabaseCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba otwartych baz danych w obszarze roboczym.

### <a name="remarks"></a>Uwagi

`GetDatabaseCount`jest przydatne, jeśli trzeba pętli przez wszystkie zdefiniowane bazy danych w kolekcji baz danych obszaru roboczego. Aby uzyskać informacje o danej bazie danych w kolekcji, zobacz [GetDatabaseInfo](#getdatabaseinfo). Typowym zastosowaniem `GetDatabaseCount` jest wywołanie liczby otwartych baz danych, a następnie użycie `GetDatabaseInfo`tego numeru jako indeksu pętli dla powtarzających się wywołań .

## <a name="cdaoworkspacegetdatabaseinfo"></a><a name="getdatabaseinfo"></a>CDaoWorkspace::GetDatabaseInfo

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać różne rodzaje informacji o bazie danych otwarte w obszarze roboczym.

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

*Nindex*<br/>
Indeks od zera obiektu bazy danych w kolekcji Bazy danych obszaru roboczego, do wyszukiwania według indeksu.

*dbinfo*<br/>
Odwołanie do obiektu [CDaoDatabaseInfo,](../../mfc/reference/cdaodatabaseinfo-structure.md) który zwraca żądane informacje.

*dwInfoOptions (NpfoOptions)*<br/>
Opcje określające informacje o bazie danych do pobrania. Dostępne opcje są wymienione tutaj wraz z tym, co powodują, że funkcja do powrotu:

- AFX_DAO_PRIMARY_INFO (domyślna) nazwa, możliwe do aktualizacji, transakcje

- AFX_DAO_SECONDARY_INFO Informacje podstawowe plus: Wersja, Kolejność sortowania, Limit czasu kwerendy

- AFX_DAO_ALL_INFO Informacje podstawowe i dodatkowe plus: Połącz

*Lpszname*<br/>
Nazwa obiektu bazy danych, do wyszukiwania według nazwy. Nazwa jest ciągiem z maksymalnie 14 znakami, który jednoznacznie nazywa nowy obiekt obszaru roboczego.

### <a name="remarks"></a>Uwagi

Jedna wersja funkcji umożliwia wyszukywę bazy danych według indeksu. Druga wersja umożliwia wyszukywanie bazy danych według nazwy.

Aby uzyskać opis informacji zwróconych w *dbinfo*, zobacz [CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md) struktury. Ta struktura ma elementy, które odpowiadają elementom informacji wymienionych powyżej w opisie *dwInfoOptions*. Gdy poprosisz o informacje na jednym poziomie, otrzymujesz informacje o wcześniejszych poziomach.

## <a name="cdaoworkspacegetinipath"></a><a name="getinipath"></a>Obszar roboczy CDao::GetIniPath

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać lokalizację ustawień inicjowania aparatu bazy danych Microsoft Jet w rejestrze systemu Windows.

```
static CString PASCAL GetIniPath();
```

### <a name="return-value"></a>Wartość zwracana

[CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierający lokalizację rejestru.

### <a name="remarks"></a>Uwagi

Lokalizacji można użyć, aby uzyskać informacje o ustawieniach aparatu bazy danych. Zwracane informacje to w rzeczywistości nazwa podklucza rejestru.

Aby uzyskać powiązane informacje, zobacz tematy "Właściwość IniPath" i "Dostosowywanie ustawień rejestru systemu Windows dla dostępu do danych" w Pomocy DAO.

## <a name="cdaoworkspacegetisolateodbctrans"></a><a name="getisolateodbctrans"></a>CDaoWorkspace::GetIsolateODBCTrans

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać bieżącą wartość właściwości DAO IsolateODBCTrans dla obszaru roboczego.

```
BOOL GetIsolateODBCTrans();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli transakcje ODBC są izolowane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

W niektórych sytuacjach może być konieczne wiele jednoczesnych transakcji oczekujących na tej samej bazie danych ODBC. Aby to zrobić, należy otworzyć oddzielny obszar roboczy dla każdej transakcji. Należy pamiętać, że chociaż każdy obszar roboczy może mieć własne połączenie ODBC z bazą danych, spowalnia to wydajność systemu. Ponieważ izolacja transakcji zwykle nie jest wymagana, połączenia ODBC z wielu obiektów obszaru roboczego otwieranych przez tego samego użytkownika są współużytkowane domyślnie.

Niektóre serwery ODBC, takie jak Microsoft SQL Server, nie zezwalają na jednoczesne transakcje na jednym połączeniu. Jeśli musisz mieć więcej niż jedną transakcję w czasie oczekiwania na taką bazę danych, ustaw właściwość IsolateODBCTrans na TRUE w każdym obszarze roboczym, gdy tylko ją otworzysz. Wymusza to oddzielne połączenie ODBC dla każdego obszaru roboczego.

Aby uzyskać powiązane informacje, zobacz temat "IzolowanieodBCTrans właściwość" w Pomocy DAO.

## <a name="cdaoworkspacegetlogintimeout"></a><a name="getlogintimeout"></a>CDaoWorkspace::GetLoginTimeout

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać bieżącą wartość właściwości DAO LoginTimeout dla obszaru roboczego.

```
static short PASCAL GetLoginTimeout();
```

### <a name="return-value"></a>Wartość zwracana

Liczba sekund przed wystąpieniem błędu podczas próby zalogowania się do bazy danych ODBC.

### <a name="remarks"></a>Uwagi

Ta wartość reprezentuje liczbę sekund przed wystąpieniem błędu podczas próby zalogowania się do bazy danych ODBC. Domyślne ustawienie LoginTimeout wynosi 20 sekund. Gdy LoginTimeout jest ustawiona na 0, nie występuje limit czasu i komunikacji ze źródłem danych może przestać odpowiadać.

Podczas próby zalogowania się do bazy danych ODBC, takiej jak Microsoft SQL Server, połączenie może zakończyć się niepowodzeniem w wyniku błędów sieciowych lub ponieważ serwer nie jest uruchomiony. Zamiast czekać na połączenie domyślne 20 sekund, można określić, jak długo aparat bazy danych czeka, zanim wywoła błąd. Logowanie się do serwera odbywa się niejawnie jako część wielu różnych zdarzeń, takich jak uruchamianie kwerendy w bazie danych serwera zewnętrznego.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość logintimeout" w Pomocy DAO.

## <a name="cdaoworkspacegetname"></a><a name="getname"></a>Obszar roboczy CDao::GetName

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać zdefiniowaną przez `CDaoWorkspace` użytkownika nazwę obiektu obszaru roboczego DAO leżącego u podstaw obiektu.

```
CString GetName();
```

### <a name="return-value"></a>Wartość zwracana

[CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierający zdefiniowaną przez użytkownika nazwę obiektu obszaru roboczego DAO.

### <a name="remarks"></a>Uwagi

Nazwa jest przydatna do uzyskiwania dostępu do obiektu obszaru roboczego DAO w kolekcji workspaces aparatu bazy danych według nazwy.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość nazw" w Pomocy DAO.

## <a name="cdaoworkspacegetusername"></a><a name="getusername"></a>Obszar roboczy CDao::GetUserName

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać nazwę właściciela obszaru roboczego.

```
CString GetUserName();
```

### <a name="return-value"></a>Wartość zwracana

[CString,](../../atl-mfc-shared/reference/cstringt-class.md) który reprezentuje właściciela obiektu obszaru roboczego.

### <a name="remarks"></a>Uwagi

Aby uzyskać lub ustawić uprawnienia dla właściciela obszaru roboczego, zadzwoń do DAO bezpośrednio, aby sprawdzić ustawienie właściwości Uprawnienia; określa uprawnienia, które ma użytkownik. Do pracy z uprawnieniami potrzebny jest system. mda.

Aby uzyskać informacje na temat bezpośredniego dzwonienia do DAO, zobacz [Uwaga techniczna 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md). Aby uzyskać powiązane informacje, zobacz temat "Właściwość UserName" w Pomocy DAO.

## <a name="cdaoworkspacegetversion"></a><a name="getversion"></a>CDaoWorkspace::GetVersion

Wywołanie tej funkcji elementu członkowskiego, aby określić wersję aparatu bazy danych Microsoft Jet w użyciu.

```
static CString PASCAL GetVersion();
```

### <a name="return-value"></a>Wartość zwracana

A [CString,](../../atl-mfc-shared/reference/cstringt-class.md) który wskazuje wersję aparatu bazy danych skojarzone z obiektem.

### <a name="remarks"></a>Uwagi

Zwracana wartość reprezentuje numer wersji w formularzu "major.minor"; na przykład "3.0". Numer wersji produktu (na przykład 3.0) składa się z numeru wersji (3), kropki i numeru wydania (0).

Aby uzyskać powiązane informacje, zobacz temat "Właściwość wersji" w Pomocy DAO.

## <a name="cdaoworkspacegetworkspacecount"></a><a name="getworkspacecount"></a>CDaoWorkspace::GetWorkspaceCount

Wywołanie tej funkcji elementu członkowskiego, aby pobrać liczbę obiektów obszaru roboczego DAO w kolekcji workspaces aparatu bazy danych.

```
short GetWorkspaceCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba otwartych obszarów roboczych w kolekcji Obszary robocze.

### <a name="remarks"></a>Uwagi

Ta liczba nie obejmuje żadnych otwartych obszarów roboczych, które nie są dołączane do kolekcji. `GetWorkspaceCount`jest przydatne, jeśli trzeba pętli przez wszystkie zdefiniowane obszary robocze w workspaces kolekcji. Aby uzyskać informacje o danym obszarze roboczym w kolekcji, zobacz [GetWorkspaceInfo](#getworkspaceinfo). Typowym zastosowaniem `GetWorkspaceCount` jest wywołanie liczby otwartych obszarów roboczych, a następnie użycie `GetWorkspaceInfo`tego numeru jako indeksu pętli dla powtarzających się wywołań .

## <a name="cdaoworkspacegetworkspaceinfo"></a><a name="getworkspaceinfo"></a>CDaoWorkspace::GetWorkspaceInfo

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać różne rodzaje informacji o obszarze roboczym otwartym w sesji.

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

*Nindex*<br/>
Indeks od zera obiektu bazy danych w kolekcji Workspaces, do wyszukiwania według indeksu.

*wkspcinfo*<br/>
Odwołanie do obiektu [CDaoWorkspaceInfo,](../../mfc/reference/cdaoworkspaceinfo-structure.md) który zwraca żądane informacje.

*dwInfoOptions (NpfoOptions)*<br/>
Opcje określające informacje o obszarze roboczym do pobrania. Dostępne opcje są wymienione tutaj wraz z tym, co powodują, że funkcja do powrotu:

- AFX_DAO_PRIMARY_INFO (domyślna) nazwa

- AFX_DAO_SECONDARY_INFO Informacje podstawowe plus: Nazwa użytkownika

- AFX_DAO_ALL_INFO Informacje podstawowe i dodatkowe plus: Izolowanie ODBCTrans

*Lpszname*<br/>
Nazwa obiektu obszaru roboczego, do wyszukiwania według nazwy. Nazwa jest ciągiem z maksymalnie 14 znakami, który jednoznacznie nazywa nowy obiekt obszaru roboczego.

### <a name="remarks"></a>Uwagi

Aby uzyskać opis informacji zwróconych w *wkspcinfo*, zobacz [CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md) struktury. Ta struktura ma elementy, które odpowiadają elementom informacji wymienionych powyżej w opisie *dwInfoOptions*. Gdy poprosisz o informacje na jednym poziomie, otrzymasz również informacje dotyczące wcześniejszych poziomów.

## <a name="cdaoworkspaceidle"></a><a name="idle"></a>CDaoWorkspace::Idle

Wywołanie, `Idle` aby zapewnić aparat bazy danych z możliwością wykonywania zadań w tle, które mogą nie być aktualne z powodu intensywnego przetwarzania danych.

```
static void PASCAL Idle(int nAction = dbFreeLocks);
```

### <a name="parameters"></a>Parametry

*nAkcja*<br/>
Działanie do podjęcia podczas przetwarzania bezczynnego. Obecnie jedyną prawidłową `dbFreeLocks`akcją jest .

### <a name="remarks"></a>Uwagi

Jest to często prawdziwe w środowiskach wielozadaniowych, w których nie ma wystarczającej ilości czasu przetwarzania w tle, aby zachować wszystkie rekordy w rekordach bieżących.

> [!NOTE]
> Wywołanie `Idle` nie jest konieczne w bazach danych utworzonych w wersji 3.0 aparatu bazy danych Microsoft Jet. Używaj `Idle` tylko dla baz danych utworzonych we wcześniejszych wersjach.

Zazwyczaj blokady odczytu są usuwane, a dane w lokalnych obiektach zestawu rekordów typu dynaset są aktualizowane tylko wtedy, gdy nie występują żadne inne akcje (w tym ruchy myszy). Jeśli co jakiś `Idle`czas wywołać, należy zapewnić aparat bazy danych z czasem, aby nadrobić zaległości w zadaniach przetwarzania w tle, zwalniając niepotrzebne blokady odczytu. Określenie stałej `dbFreeLocks` jako argument opóźnia przetwarzanie, dopóki nie zostaną zwolnione wszystkie blokady odczytu.

Ta funkcja elementu członkowskiego nie jest potrzebna w środowiskach z jednym użytkownikiem, chyba że wiele wystąpień aplikacji są uruchomione. Funkcja `Idle` elementu członkowskiego może zwiększyć wydajność w środowisku wielodojowym, ponieważ wymusza aparat bazy danych do opróżniania danych na dysku, zwalniając blokady w pamięci. Można również zwolnić odczyt blokady przez operacje część transakcji.

Aby uzyskać powiązane informacje, zobacz temat "Metoda bezczynnia" w Pomocy DAO.

## <a name="cdaoworkspaceisopen"></a><a name="isopen"></a>CDaoWorkspace::IsOpen

Wywołanie tej funkcji elementu `CDaoWorkspace` członkowskiego, aby ustalić, czy obiekt jest otwarty — to znaczy, czy obiekt MFC został zainicjowany przez wywołanie [Open](#open) lub wywołanie [Create](#create).

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli obiekt obszaru roboczego jest otwarty; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Można wywołać dowolną z funkcji członkowskich obszaru roboczego, który jest w stanie otwartym.

## <a name="cdaoworkspacem_pdaoworkspace"></a><a name="m_pdaoworkspace"></a>CDaoWorkspace::m_pDAOWorkspace

Wskaźnik do leżącego w nim obiektu obszaru roboczego DAO.

### <a name="remarks"></a>Uwagi

Użyj tego elementu członkowskiego danych, jeśli potrzebujesz bezpośredniego dostępu do bazowego obiektu DAO. Interfejsy obiektu DAO można wywołać za pomocą tego wskaźnika.

Aby uzyskać informacje o bezpośrednim dostępie do obiektów DAO, zobacz [Uwaga techniczna 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="cdaoworkspaceopen"></a><a name="open"></a>CDaoWorkspace::Otwórz

Jawnie otwiera obiekt obszaru roboczego skojarzony z domyślnym obszarem roboczym DAO.

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
Nazwa obiektu obszaru roboczego DAO do otwarcia — ciąg z maksymalnie 14 znakami, który jednoznacznie nadaje nazwę obszarowi roboczemu. Zaakceptuj wartość domyślną NULL, aby jawnie otworzyć domyślny obszar roboczy. Aby zapoznać się z wymaganiami dotyczącymi nazewnictwa, zobacz parametr *lpszName* dla [create](#create). Aby uzyskać powiązane informacje, zobacz temat "Właściwość nazw" w Pomocy DAO.

### <a name="remarks"></a>Uwagi

Po skonstruowaniu `CDaoWorkspace` obiektu, wywołać tę funkcję elementu członkowskiego, aby wykonać jedną z następujących czynności:

- Jawnie otwórz domyślny obszar roboczy. Przekaż NULL dla *lpszName*.

- Otwórz istniejący `CDaoWorkspace` obiekt, członek kolekcji Workspaces, według nazwy. Przekaż prawidłową nazwę istniejącego obiektu obszaru roboczego.

`Open`umieszcza obiekt obszaru roboczego w stanie otwartym, a także inicjuje aparat bazy danych, jeśli nie został jeszcze zainicjowany dla aplikacji.

Chociaż `CDaoWorkspace` wiele funkcji członkowskich można wywołać tylko po otwarciu obszaru roboczego, następujące funkcje członkowskie, które działają na silniku `Open`bazy danych, są dostępne po budowie obiektu C++, ale przed wywołaniem:

||||
|-|-|-|
|[Utwórz](#create)|[Wersja GetVersion](#getversion)|[SetDefaultUżyciek](#setdefaultuser)|
|[GetIniPath (GetIniPath)](#getinipath)|[Okresy](#idle)|[Ścieżka SetIniPath](#setinipath)|
|[GetLoginTimeout (Czasomierz)](#getlogintimeout)|[SetDefaultPassword](#setdefaultpassword)|[SetLoginTimeout (Ustawianie czasu)](#setlogintimeout)|

## <a name="cdaoworkspacerepairdatabase"></a><a name="repairdatabase"></a>CDaoWorkspace::RepairDatabase

Wywołanie tej funkcji elementu członkowskiego, jeśli chcesz spróbować naprawić uszkodzoną bazę danych, która uzyskuje dostęp do aparatu bazy danych Microsoft Jet.

```
static void PASCAL RepairDatabase(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
Ścieżka i nazwa pliku dla istniejącego pliku bazy danych aparatu Microsoft Jet. Jeśli pominięto ścieżkę, przeszukiwany jest tylko bieżący katalog. Jeśli system obsługuje jednolitą konwencję nazewnictwa (UNC), można również\\\\\\określić ścieżkę sieciową, taką jak: " \MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB". (Podwójne ukośnie są wymagane w ciągu\\ścieżki, ponieważ " " jest znakiem ucieczki C++.)

### <a name="remarks"></a>Uwagi

Przed naprawą należy zamknąć bazę danych określoną przez *lpszName.* W środowisku wielodojowym inni użytkownicy nie mogą mieć *lpszName* otwarte podczas naprawy. Jeśli *lpszName* nie jest zamknięty lub nie jest dostępny do wyłącznego użytku, występuje błąd.

Ta funkcja elementu członkowskiego próbuje naprawić bazę danych, która została oznaczona jako prawdopodobnie uszkodzona przez operację zapisu niekompletnego. Taka możliwość może wystąpić, jeśli aplikacja korzystająca z aparatu bazy danych Microsoft Jet zostanie nieoczekiwanie zamknięta z powodu awarii zasilania lub problemu ze sprzętem komputerowym. Jeśli zakończysz operację i wywołasz funkcję [Zamknij](../../mfc/reference/cdaodatabase-class.md#close) element członkowski lub zamkniesz aplikację w zwykły sposób, baza danych nie zostanie oznaczona jako prawdopodobnie uszkodzona.

> [!NOTE]
> Po naprawie bazy danych warto również skompaktować ją za pomocą funkcji elementu członkowskiego [CompactDatabase](#compactdatabase) w celu defragmentacji pliku i odzyskania miejsca na dysku.

Aby uzyskać więcej informacji na temat naprawy baz danych, zobacz temat "RepairDatabase Method" w Pomocy DAO.

## <a name="cdaoworkspacerollback"></a><a name="rollback"></a>OBSZAR ROBOCZY CD::Wycofywanie

Wywołanie tej funkcji elementu członkowskiego, aby zakończyć bieżącą transakcję i przywrócić wszystkie bazy danych w obszarze roboczym do ich stanu przed rozpoczęciem transakcji.

```
void Rollback();
```

### <a name="remarks"></a>Uwagi

> [!CAUTION]
> W obrębie jednego obiektu obszaru roboczego transakcje są zawsze globalne w obszarze roboczym i nie są ograniczone tylko do jednej bazy danych lub pliku recordset. Jeśli operacje są wykonywane na więcej niż jednej bazie `Rollback` danych lub wyliczanego w ramach transakcji obszaru roboczego, przywraca wszystkie operacje we wszystkich tych bazach danych i zestawy rekordów.

Jeśli zamkniesz obiekt obszaru roboczego bez zapisywania lub wycofywania żadnych oczekujących transakcji, transakcje są automatycznie przywracane. Jeśli wywołasz [CommitTrans](#committrans) lub `Rollback` bez pierwszego wywołania [BeginTrans](#begintrans), wystąpi błąd.

> [!NOTE]
> Po rozpoczęciu transakcji aparat bazy danych rejestruje swoje operacje w pliku przechowywanym w katalogu określonym przez zmienną środowiskową TEMP na stacji roboczej. Jeśli plik dziennika transakcji wyczerpie dostępnego magazynu na dysku TEMP, `CDaoException` aparat bazy danych spowoduje MFC do zrzucenia (błąd DAO 2004). W tym momencie, `CommitTrans`jeśli wywołasz, nieokreślona liczba operacji są zatwierdzane, ale pozostałe nieukończone operacje zostaną utracone, a operacja musi zostać ponownie uruchomiona. Wywołanie `Rollback` zwalnia dziennik transakcji i wycofuje wszystkie operacje w transakcji.

## <a name="cdaoworkspacesetdefaultpassword"></a><a name="setdefaultpassword"></a>CDaoWorkspace::SetDefaultPassword

Wywołanie tej funkcji elementu członkowskiego, aby ustawić domyślne hasło używane przez aparat bazy danych, gdy obiekt obszaru roboczego jest tworzony bez określonego hasła.

```
static void PASCAL SetDefaultPassword(LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parametry

*lpszPassword*<br/>
Hasło domyślne. Hasło może mieć długość do 14 znaków i może zawierać dowolny znak z wyjątkiem ASCII 0 (null). W hasłach rozróżniana jest wielkość liter.

### <a name="remarks"></a>Uwagi

Ustawione domyślne hasło ma zastosowanie do nowych obszarów roboczych utworzonych po wywołaniu. Podczas tworzenia kolejnych obszarów roboczych nie trzeba określać hasła w [wywołaniu Utwórz.](#create)

Aby użyć tej funkcji elementu członkowskiego:

1. Konstruuj `CDaoWorkspace` obiekt, `Create`ale nie wywołaj .

1. Zadzwoń `SetDefaultPassword` i, jeśli chcesz, [SetDefaultUser](#setdefaultuser).

1. Wywołanie `Create` tego obiektu obszaru roboczego lub kolejnych, bez określania hasła.

Domyślnie właściwość DefaultUser jest ustawiona na "admin", a właściwość DefaultPassword jest ustawiona na pusty ciąg ("").

Aby uzyskać więcej informacji na temat zabezpieczeń, zobacz temat "Właściwość uprawnień" w Pomocy DAO. Aby uzyskać powiązane informacje, zobacz tematy "DefaultPassword Property" i "DefaultUser Property" w Pomocy DAO.

## <a name="cdaoworkspacesetdefaultuser"></a><a name="setdefaultuser"></a>CDaoWorkspace::SetDefaultUser

Wywołanie tej funkcji elementu członkowskiego, aby ustawić domyślną nazwę użytkownika, która używa aparat bazy danych, gdy obiekt obszaru roboczego jest tworzony bez określonej nazwy użytkownika.

```
static void PASCAL SetDefaultUser(LPCTSTR lpszDefaultUser);
```

### <a name="parameters"></a>Parametry

*lpszDefaultUżyciek*<br/>
Domyślna nazwa użytkownika. Nazwa użytkownika może mieć długość od 1 do 20 znaków i zawierać znaki alfabetyczne, znaki akcentowane, liczby, spacje i symbole \[ \] z wyjątkiem: " (cudzysłowy), \< / (ukośnik do przodu), \ (ukośnik odwrotny), (nawiasy), : (dwukropek), &#124; (fajka), (znak mniej niż), > (znak większy), + (znak plus), = (znak równy), ; (średnik), , ( przecinek), (znak zapytania), \* (gwiazdka), spacje wiodące i znaki kontrolne (ASCII 00 do ASCII 31). Aby uzyskać powiązane informacje, zobacz temat "Właściwość UserName" w Pomocy DAO.

### <a name="remarks"></a>Uwagi

Ustawiona domyślna nazwa użytkownika ma zastosowanie do nowych obszarów roboczych utworzonych po wywołaniu. Podczas tworzenia kolejnych obszarów roboczych nie trzeba określać nazwy użytkownika w [wywołaniu Utwórz.](#create)

Aby użyć tej funkcji elementu członkowskiego:

1. Konstruuj `CDaoWorkspace` obiekt, `Create`ale nie wywołaj .

1. Zadzwoń `SetDefaultUser` i, jeśli chcesz, [SetDefaultPassword](#setdefaultpassword).

1. Wywołanie `Create` tego obiektu obszaru roboczego lub kolejnych, bez określania nazwy użytkownika.

Domyślnie właściwość DefaultUser jest ustawiona na "admin", a właściwość DefaultPassword jest ustawiona na pusty ciąg ("").

Aby uzyskać powiązane informacje, zobacz tematy "DefaultUser Property" i "DefaultPassword Property" w Pomocy DAO.

## <a name="cdaoworkspacesetinipath"></a><a name="setinipath"></a>Obszar roboczy CDao::SetIniPath

Wywołanie tej funkcji elementu członkowskiego, aby określić lokalizację ustawień rejestru systemu Windows dla aparatu bazy danych Microsoft Jet.

```
static void PASCAL SetIniPath(LPCTSTR lpszRegistrySubKey);
```

### <a name="parameters"></a>Parametry

*lpszRegistrySubkey*<br/>
Ciąg zawierający nazwę podklucza rejestru systemu Windows dla lokalizacji ustawień aparatu bazy danych Microsoft Jet lub parametrów wymaganych do zainstalowania baz danych ISAM.

### <a name="remarks"></a>Uwagi

Zadzwoń `SetIniPath` tylko wtedy, gdy musisz określić specjalne ustawienia. Aby uzyskać więcej informacji, zobacz temat "Właściwość IniPath" w Pomocy DAO.

> [!NOTE]
> Wywołanie `SetIniPath` podczas instalacji aplikacji, a nie po uruchomieniu aplikacji. `SetIniPath`przed otwarciem jakichkolwiek obszarów roboczych, baz danych lub rekordów; w przeciwnym razie MFC zgłasza wyjątek.

Za pomocą tego mechanizmu można skonfigurować aparat bazy danych z ustawieniami rejestru dostarczonymi przez użytkownika. Zakres tego atrybutu jest ograniczony do aplikacji i nie można go zmienić bez ponownego uruchomienia aplikacji.

## <a name="cdaoworkspacesetisolateodbctrans"></a><a name="setisolateodbctrans"></a>CDaoWorkspace::SetIsolateODBCTrans

Wywołanie tej funkcji elementu członkowskiego, aby ustawić wartość właściwości DAO IsolateODBCTrans dla obszaru roboczego.

```
void SetIsolateODBCTrans(BOOL bIsolateODBCTrans);
```

### <a name="parameters"></a>Parametry

*bIsolateODBCTrans*<br/>
Przekaż true, jeśli chcesz rozpocząć izolowanie transakcji ODBC. Przekaż FALSE, jeśli chcesz zatrzymać izolowanie transakcji ODBC.

### <a name="remarks"></a>Uwagi

W niektórych sytuacjach może być konieczne wiele jednoczesnych transakcji oczekujących na tej samej bazie danych ODBC. Aby to zrobić, należy otworzyć oddzielny obszar roboczy dla każdej transakcji. Mimo że każdy obszar roboczy może mieć własne połączenie ODBC z bazą danych, spowalnia to wydajność systemu. Ponieważ izolacja transakcji zwykle nie jest wymagana, połączenia ODBC z wielu obiektów obszaru roboczego otwieranych przez tego samego użytkownika są współużytkowane domyślnie.

Niektóre serwery ODBC, takie jak Microsoft SQL Server, nie zezwalają na jednoczesne transakcje na jednym połączeniu. Jeśli musisz mieć więcej niż jedną transakcję w czasie oczekiwania na taką bazę danych, ustaw właściwość IsolateODBCTrans na TRUE w każdym obszarze roboczym, gdy tylko ją otworzysz. Wymusza to oddzielne połączenie ODBC dla każdego obszaru roboczego.

## <a name="cdaoworkspacesetlogintimeout"></a><a name="setlogintimeout"></a>Obszar roboczy CDao::SetLoginTimeout

Wywołanie tej funkcji elementu członkowskiego, aby ustawić wartość właściwości DAO LoginTimeout dla obszaru roboczego.

```
static void PASCAL SetLoginTimeout(short nSeconds);
```

### <a name="parameters"></a>Parametry

*nSekundy*<br/>
Liczba sekund przed wystąpieniem błędu podczas próby zalogowania się do bazy danych ODBC.

### <a name="remarks"></a>Uwagi

Ta wartość reprezentuje liczbę sekund przed wystąpieniem błędu podczas próby zalogowania się do bazy danych ODBC. Domyślne ustawienie LoginTimeout wynosi 20 sekund. Gdy LoginTimeout jest ustawiona na 0, nie występuje limit czasu i komunikacji ze źródłem danych może przestać odpowiadać.

Podczas próby zalogowania się do bazy danych ODBC, takiej jak Microsoft SQL Server, połączenie może zakończyć się niepowodzeniem w wyniku błędów sieciowych lub ponieważ serwer nie jest uruchomiony. Zamiast czekać na połączenie domyślne 20 sekund, można określić, jak długo aparat bazy danych czeka, zanim wywoła błąd. Logowanie się do serwera odbywa się niejawnie jako część wielu różnych zdarzeń, takich jak uruchamianie kwerendy w bazie danych serwera zewnętrznego. Wartość limitu czasu jest określana przez bieżące ustawienie właściwości LoginTimeout.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość logintimeout" w Pomocy DAO.

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)<br/>
[Klasa CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)<br/>
[Klasa CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)<br/>
[Klasa CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)<br/>
[Klasa CDaoException](../../mfc/reference/cdaoexception-class.md)
