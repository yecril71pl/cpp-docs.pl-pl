---
title: Klasa CDaoWorkspace | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b249f8069ba12772d21d170b67236a5f013290ac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33377217"
---
# <a name="cdaoworkspace-class"></a>Klasa CDaoWorkspace
Zarządza sesji bazy danych o nazwie, chroniony hasłem z logowania do wylogowania przez pojedynczego użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDaoWorkspace : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDaoWorkspace::CDaoWorkspace](#cdaoworkspace)|Tworzy obiekt obszaru roboczego. Następnie wywołaj **Utwórz** lub **Otwórz**.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDaoWorkspace::Append](#append)|Dołącza nowo utworzonego obszaru roboczego do kolekcji obszarów roboczych aparatu bazy danych.|  
|[CDaoWorkspace::BeginTrans](#begintrans)|Rozpoczyna nową transakcję, która ma zastosowanie do wszystkich baz danych Otwórz w obszarze roboczym.|  
|[CDaoWorkspace::Close](#close)|Zamyka obszaru roboczego i wszystkie obiekty, które zawiera. Transakcje oczekujące są przywracane.|  
|[CDaoWorkspace::CommitTrans](#committrans)|Kończy bieżącej transakcji i zapisuje zmiany.|  
|[CDaoWorkspace::CompactDatabase](#compactdatabase)|Kompaktuje lub stanowi duplikat bazy danych.|  
|[CDaoWorkspace::Create](#create)|Tworzy nowy obiekt DAO obszaru roboczego.|  
|[CDaoWorkspace::GetDatabaseCount](#getdatabasecount)|Zwraca liczbę obiektów bazy danych DAO w kolekcji baz danych obszaru roboczego.|  
|[CDaoWorkspace::GetDatabaseInfo](#getdatabaseinfo)|Zwraca informacje o określonej bazy danych DAO zdefiniowana w kolekcji baz danych obszaru roboczego.|  
|[CDaoWorkspace::GetIniPath](#getinipath)|Zwraca lokalizację bazy danych programu Microsoft Jet aparatu inicjowania ustawień w rejestrze systemu Windows.|  
|[CDaoWorkspace::GetIsolateODBCTrans](#getisolateodbctrans)|Zwraca wartość wskazującą, czy wiele transakcji, które dotyczą tego samego źródła danych ODBC są izolowane za pośrednictwem wymuszone wiele połączeń ze źródłem danych.|  
|[CDaoWorkspace::GetLoginTimeout](#getlogintimeout)|Zwraca liczbę sekund, zanim wystąpi błąd, gdy użytkownik próbuje zalogować się do bazy danych ODBC.|  
|[CDaoWorkspace::GetName](#getname)|Zwraca nazwę użytkownika dla obiekt workspace.|  
|[CDaoWorkspace::GetUserName](#getusername)|Zwraca, że podana nazwa użytkownika podczas tworzenia obszaru roboczego. Jest to nazwa właściciela obszaru roboczego.|  
|[CDaoWorkspace::GetVersion](#getversion)|Zwraca ciąg zawierający wersję aparatu bazy danych skojarzony z obszaru roboczego.|  
|[CDaoWorkspace::GetWorkspaceCount](#getworkspacecount)|Zwraca liczbę obiektów DAO obszaru roboczego w kolekcji obszarów roboczych aparatu bazy danych.|  
|[CDaoWorkspace::GetWorkspaceInfo](#getworkspaceinfo)|Zwraca informacje dotyczące określonego obszaru roboczego DAO zdefiniowana w kolekcji obszarów roboczych aparatu bazy danych.|  
|[CDaoWorkspace::Idle](#idle)|Umożliwia aparat bazy danych do wykonania zadania w tle.|  
|[CDaoWorkspace::IsOpen](#isopen)|Zwraca wartość niezerową, jeśli obszar roboczy jest Otwórz.|  
|[CDaoWorkspace::Open](#open)|Otwiera jawnie obiektu obszaru roboczego skojarzonego z jego DAO domyślny obszar roboczy.|  
|[CDaoWorkspace::RepairDatabase](#repairdatabase)|Próby naprawienia uszkodzenia bazy danych.|  
|[CDaoWorkspace::Rollback](#rollback)|Kończy bieżącej transakcji i nie powoduje zapisania zmian.|  
|[CDaoWorkspace::SetDefaultPassword](#setdefaultpassword)|Ustawia hasło korzystającego z aparatem bazy danych, gdy tworzony jest obiekt obszaru roboczego bez określonego hasła.|  
|[CDaoWorkspace::SetDefaultUser](#setdefaultuser)|Ustawia nazwę użytkownika używaną przez aparat bazy danych podczas tworzenia obiektu obszaru roboczego bez określonej nazwy użytkownika.|  
|[CDaoWorkspace::SetIniPath](#setinipath)|Ustawia lokalizację bazy danych programu Microsoft Jet aparatu inicjowania ustawień w rejestrze systemu Windows.|  
|[CDaoWorkspace::SetIsolateODBCTrans](#setisolateodbctrans)|Określa, czy wiele transakcji, które dotyczą tego samego źródła danych ODBC są izolowane, powodując, że wiele połączeń ze źródłem danych.|  
|[CDaoWorkspace::SetLoginTimeout](#setlogintimeout)|Ustawia liczbę sekund, zanim wystąpi błąd, gdy użytkownik próbuje zalogować się do źródła danych ODBC.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDaoWorkspace::m_pDAOWorkspace](#m_pdaoworkspace)|Wskazuje obszaru roboczego obiekt DAO.|  
  
## <a name="remarks"></a>Uwagi  
 W większości przypadków nie będzie wiele obszarów roboczych, a nie należy do tworzenia obiektów roboczym jawne; Po otwarciu obiekty bazy danych i zestaw rekordów, używają DAO przez domyślny obszar roboczy. Jednak w razie potrzeby można uruchomić wiele sesji w czasie przez tworzenie obiektów dodatkowe obszaru roboczego. Każdy obiekt obszaru roboczego może zawierać wielu obiektów bazy danych w jego własnej kolekcji baz danych. W MFC obszar roboczy jest głównie Menedżera transakcji, określenie zestaw baz danych, otwórz wszystko w tym samym "miejsca transakcji".  
  
> [!NOTE]
>  Klasy baz danych DAO różnią się od klasy baz danych MFC oparte na otwarte połączenie bazy danych (ODBC). Wszystkie nazwy klasy bazy danych DAO mają prefiks "CDao". Ogólnie rzecz biorąc klas MFC DAO w oparciu nadają się bardziej niż klas MFC ODBC — na podstawie. Klasy oparte na DAO dostęp do danych za pomocą aparatu bazy danych programu Microsoft Jet, w tym sterowników ODBC. Obsługują one również operacji języka definicji danych (DDL), takich jak tworzenie baz danych i dodawanie tabel i pól za pośrednictwem klas, bez konieczności wywoływanie obiektów DAO bezpośrednio.  
  
## <a name="capabilities"></a>Możliwości  
 Klasa `CDaoWorkspace` udostępnia następujące:  
  
-   Jawny dostęp, jeśli to konieczne, domyślny obszar roboczy, utworzone przez inicjowanie aparatu bazy danych. Zwykle użyć DAO przez domyślny obszar roboczy niejawnie przez tworzenie obiektów bazy danych i zestaw rekordów.  
  
-   Otwórz obszar transakcji, w którym transakcje dotyczą wszystkich baz danych w obszarze roboczym. Możesz utworzyć dodatkowych obszarów roboczych do zarządzania spacje w osobnej transakcji.  
  
-   Interfejs na wiele właściwości podstawowej aparatu bazy danych programu Microsoft Jet (zobacz funkcji statycznych elementów członkowskich). Otwieranie lub tworzenie obszaru roboczego lub statycznej funkcji członkowskiej przed wywołaniem otworzyć lub utworzyć, aparat bazy danych.  
  
-   Dostęp do kolekcji obszarów roboczych aparat bazy danych, który przechowuje wszystkie aktywne obszary robocze, które zostały dołączone do niego. Można również tworzyć i Praca z obszarami roboczymi bez ich dodanie do kolekcji.  
  
## <a name="security"></a>Zabezpieczenia  
 MFC nie implementuje kolekcji użytkowników i grup w DAO, które są używane do kontroli zabezpieczeń. Jeśli potrzebujesz tych aspektów DAO należy zaprogramować je samodzielnie za pomocą bezpośrednich wywołań interfejsów DAO. Aby uzyskać informacje, zobacz [54 Uwaga techniczna](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).  
  
## <a name="usage"></a>Użycie  
 Można użyć klasy `CDaoWorkspace` do:  
  
-   Otwierać domyślny obszar roboczy.  
  
     Zwykle używanie domyślny obszar roboczy jest niejawnie — podczas otwierania nowych [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) lub [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) obiektów. Konieczne może być jawnie do niego dostęp, ale — na przykład do właściwości aparatu bazy danych programu access lub kolekcji obszarów roboczych. Zobacz "Użycia niejawnego domyślny obszar roboczy" poniżej.  
  
-   Tworzenie nowych obszarów roboczych. Wywołanie [Append](#append) Jeśli chcesz dodać je do kolekcji obszarów roboczych.  
  
-   Otwórz istniejący obszar roboczy w kolekcji obszarów roboczych.  
  
 Tworzenie nowego obszaru roboczego, które jeszcze nie istnieje w kolekcji jest opisany w obszarach roboczych [Utwórz](#create) funkcję elementu członkowskiego. Obszar roboczy obiekty nie są zachowywane w żaden sposób między sesjami aparat datababase. Jeśli aplikacja łączy MFC statycznie, końcowy aplikacji uninitializes aparatu bazy danych. Jeśli aplikacja łączy dynamicznie z MFC, aparat bazy danych nie jest zainicjowany podczas biblioteki MFC DLL zostanie zwolniona.  
  
 Jawnie otwierania domyślny obszar roboczy, lub Otwórz istniejący obszar roboczy w kolekcji obszarów roboczych została opisana w sekcji [Otwórz](#open) funkcję elementu członkowskiego.  
  
 Kończenie sesji obszaru roboczego, zamykając obszaru roboczego z [Zamknij](#close) funkcję elementu członkowskiego. **Zamknij** zamyka żadnych baz danych nie zostało zamknięte wcześniej, wycofywanie wszystkie niezatwierdzone transakcje.  
  
## <a name="transactions"></a>Transakcje  
 Obiekty DAO zarządza transakcji poziomie obszaru roboczego. w związku z tym transakcji w obszarze roboczym z wieloma bazami danych otwórz mają zastosowanie do wszystkich baz danych. Na przykład, jeśli dwie bazy danych ma niezatwierdzone aktualizacjami wywołanie [CommitTrans](#committrans), wszystkie aktualizacje zostają zatwierdzone. Jeśli chcesz ograniczyć transakcji do pojedynczej bazy danych, należy obiektu oddzielne obszaru roboczego dla niego.  
  
## <a name="implicit-use-of-the-default-workspace"></a>Jawne użycie domyślny obszar roboczy  
 MFC używa DAO przez domyślny obszar roboczy niejawnie w następujących okolicznościach:  
  
-   Jeśli tworzysz nową `CDaoDatabase` obiekt, ale nie za pomocą istniejącej `CDaoWorkspace` obiekt MFC tworzy tymczasowy obszar roboczy obiekt, co odpowiada DAO przez domyślny obszar roboczy. W takim przypadku wielu baz danych, wszystkie obiekty bazy danych są skojarzone z domyślny obszar roboczy. Dostępny obszar roboczy bazy danych za pośrednictwem `CDaoDatabase` element członkowski danych.  
  
-   Podobnie jeśli tworzysz `CDaoRecordset` obiektu bez podawania wskaźnik do `CDaoDatabase` obiekt MFC tworzy obiekt tymczasowej bazy danych i przez rozszerzenie, obiektu tymczasowego obszaru roboczego. Zestaw rekordów bazy danych, a pośrednio obszaru roboczego, może dostęp za pośrednictwem `CDaoRecordset` element członkowski danych.  
  
## <a name="other-operations"></a>Inne operacje  
 Inne operacje bazy danych są również podane, takich jak naprawy uszkodzenia bazy danych lub kompaktowania bazy danych.  
  
 Aby uzyskać informacje dotyczące wywoływanie obiektów DAO bezpośrednio i DAO zabezpieczeń, zobacz [54 Uwaga techniczna](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoWorkspace`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  
  
##  <a name="append"></a>  CDaoWorkspace::Append  
 Wywołanie funkcji członkowskiej po wywołaniu metody [Utwórz](#create).  
  
```  
virtual void Append();
```  
  
### <a name="remarks"></a>Uwagi  
 **Dołącz** dołącza obiektu nowo utworzonego obszaru roboczego do kolekcji obszarów roboczych aparatu bazy danych. Obszary robocze nie są zachowywane między sesjami aparatu bazy danych; są one przechowywane tylko w pamięci, a nie na dysku. Nie masz do dołączenia obszaru roboczego; Jeśli nie chcesz, możesz go nadal używać.  
  
 Obszar roboczy dołączany pozostaje w kolekcji obszarów roboczych, aktywnie stanie otwartym czasu wywołania jego [Zamknij](#close) funkcję elementu członkowskiego.  
  
 Powiązane informacje zobacz temat "Dołącz Method" w pomocy DAO.  
  
##  <a name="begintrans"></a>  CDaoWorkspace::BeginTrans  
 Wywołanie tej funkcji Członkowskich zainicjować transakcji.  
  
```  
void BeginTrans();
```  
  
### <a name="remarks"></a>Uwagi  
 Po wywołaniu metody **BeginTrans**, aktualizacje należy do struktury danych lub bazy danych zostały wprowadzone podczas zatwierdzania transakcji. Ponieważ obszar roboczy definiuje odstęp pojedynczej transakcji, transakcja ma zastosowanie do wszystkich otwartych baz danych w obszarze roboczym. Istnieją dwa sposoby sfinalizowanie transakcji:  
  
-   Wywołanie [CommitTrans](#committrans) funkcji członkowskiej zatwierdzić transakcji i zapisać zmian w źródle danych.  
  
-   Lub zadzwoń [wycofywania](#rollback) funkcji członkowskiej anulowania transakcji.  
  
 Zamykanie obiektu obszaru roboczego lub bazy danych, gdy transakcja jest w stanie oczekiwania wycofuje wszystkie transakcje oczekujące.  
  
 Jeśli potrzebujesz do izolacji transakcji dla jednego źródła danych ODBC od tych na innego źródła danych ODBC, zobacz [SetIsolateODBCTrans](#setisolateodbctrans) funkcję elementu członkowskiego.  
  
##  <a name="cdaoworkspace"></a>  CDaoWorkspace::CDaoWorkspace  
 Konstruuje `CDaoWorkspace` obiektu.  
  
```  
CDaoWorkspace();
```  
  
### <a name="remarks"></a>Uwagi  
 Po konstruowania obiektu języka C++, dostępne są dwie opcje:  
  
-   Wywołanie obiektu [Otwórz](#open) funkcji członkowskiej, Otwórz obszar roboczy domyślne lub Otwórz istniejący obiekt w kolekcji obszarów roboczych.  
  
-   Lub wywołania obiektu [Utwórz](#create) funkcji członkowskiej, aby utworzyć nowy obiekt DAO obszaru roboczego. Zostanie uruchomiony jawnie nowej sesji obszaru roboczego, które mogą odwoływać się do za pośrednictwem `CDaoWorkspace` obiektu. Po wywołaniu **Utwórz**, można wywołać [Append](#append) Jeśli chcesz dodać do kolekcji obszarów roboczych aparat bazy danych obszaru roboczego.  
  
 Zobacz Omówienie klasy [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) uzyskać informacje potrzebne do utworzenia jawnie `CDaoWorkspace` obiektu. Zazwyczaj można używać obszarów roboczych niejawnie tworzonych podczas otwierania [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) obiektu bez określania obszaru roboczego lub po otwarciu [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) obiektu bez określania obiektu bazy danych. Obiekty MFC DAO utworzone w ten sposób używają DAO przez domyślny obszar roboczy, które po utworzeniu i ponownie.  
  
 Aby zwolnić obszaru roboczego i zawartych w nim obiektów, wywołania obiektu obszaru roboczego [Zamknij](#close) funkcję elementu członkowskiego.  
  
##  <a name="close"></a>  CDaoWorkspace::Close  
 Wywołanie tej funkcji elementu członkowskiego, aby zamknąć obiekt obszaru roboczego.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Uwagi  
 Zamykanie obiektu Otwórz obszar roboczy zwalnia obiekt DAO i, jeśli obszar roboczy jest członkiem kolekcji obszarów roboczych spowoduje usunięcie go z kolekcji. Wywoływanie **Zamknij** jest dobrym rozwiązaniem programowania.  
  
> [!CAUTION]
>  Zamykanie obiektu obszaru roboczego zamyka wszystkie otwarte bazy danych w obszarze roboczym. Powoduje to open żadnych zestawów rekordów w bazach danych, jak również zamknięte, a wszystkie oczekujące edycje lub aktualizacje są przywracane. Aby uzyskać odpowiednie informacje, zobacz [CDaoDatabase::Close](../../mfc/reference/cdaodatabase-class.md#close), [CDaoRecordset::Close](../../mfc/reference/cdaorecordset-class.md#close), [CDaoTableDef::Close](../../mfc/reference/cdaotabledef-class.md#close), i [CDaoQueryDef::Close](../../mfc/reference/cdaoquerydef-class.md#close) funkcji elementów członkowskich.  
  
 Obszar roboczy obiekty nie są trwałe; istnieją one tylko wtedy, gdy istnieją odwołania do nich. Oznacza to, że po zakończeniu sesji aparatu bazy danych obszaru roboczego i jego kolekcja baz danych nie są zachowywane. Należy je ponownie utworzyć w następnej sesji przez ponownie otworzyć obszaru roboczego, a baz danych.  
  
 Powiązane informacje zobacz temat "Metody Close" w pomocy DAO.  
  
##  <a name="committrans"></a>  CDaoWorkspace::CommitTrans  
 Wywołanie tej funkcji członkowskich można zatwierdzić transakcji — Zapisywanie grupy zmian i aktualizacji do jednego lub więcej baz danych w obszarze roboczym.  
  
```  
void CommitTrans();
```  
  
### <a name="remarks"></a>Uwagi  
 Transakcja składa się z szeregu zmiany do bazy danych lub jego struktury, począwszy od wywołania [BeginTrans](#begintrans). Po zakończeniu transakcji, albo Zatwierdź go lub go zbiorczego (Anuluj zmiany) z [wycofywania](#rollback). Domyślnie bez transakcji rekordy są aktualizacje zatwierdzone natychmiast. Wywoływanie **BeginTrans** powoduje, że zobowiązań aktualizacje na opóźnione wywołania **CommitTrans**.  
  
> [!CAUTION]
>  W ramach jednego obszaru roboczego transakcje są zawsze globalne do obszaru roboczego i nie są ograniczone do tylko jednej bazy danych lub zestawu rekordów. Jeśli wykonywania operacji na więcej niż jednej bazy danych lub zestawu rekordów w ramach transakcji obszaru roboczego, **CommitTrans** zatwierdzeń wszystkie oczekujące aktualizacje, i **wycofywania** przywraca wszystkie operacje na tych baz danych i zestawy rekordów.  
  
 Podczas zamykania bazy danych lub obszar roboczy o transakcje oczekujące, wszystkie wycofywania transakcji.  
  
> [!NOTE]
>  To nie jest mechanizm dwufazowe. Jeśli jedna aktualizacja nie można przekazać, inne nadal będzie zatwierdzić.  
  
##  <a name="compactdatabase"></a>  CDaoWorkspace::CompactDatabase  
 Wywołanie tej funkcji Członkowskich kompaktowania określonego programu Microsoft Jet (. Baza danych MDB).  
  
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
 `lpszSrcName`  
 Nazwa istniejącej zamknięty bazy danych. Jest pełna ścieżka i nazwa pliku, taką jak "C:\\\MYDB. MDB". Jeśli nazwa pliku ma rozszerzenie, należy ją określić. Jeśli sieć obsługuje jednolitego konwencji nazewnictwa (UNC), można dodawać ścieżkę sieciową, taką jak "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB". (Podwójnych odwróconych są wymagane w ciągach ścieżki, ponieważ "\\" jest znak ucieczki C++.)  
  
 `lpszDestName`  
 Pełna ścieżka skompaktowanego bazy danych, które tworzysz. Można również określić ścieżkę sieciową jako z `lpszSrcName`. Nie można użyć `lpszDestName` argumentu, aby określić tego samego pliku bazy danych jako `lpszSrcName`.  
  
 `lpszPassword`  
 Hasło stosowany podczas kompaktowania bazy danych chronionej hasłem. Należy pamiętać, że jeśli używasz wersji `CompactDatabase` pobierającej hasła, musisz podać wszystkie parametry. Ponadto ponieważ jest to parametr connect, wymaga specjalnego formatowania, w następujący sposób:; PWD = `lpszPassword`. Na przykład:; PWD = "Wszystkiego". (Wymagana jest wiodące średnikami).  
  
 `lpszLocale`  
 Służy do określania kolejności sortowania do tworzenia wyrażenia ciągu `lpszDestName`. W przypadku pominięcia tego argumentu akceptując wartości domyślne z **dbLangGeneral** (patrz poniżej), ustawienia regionalne nowej bazy danych jest takie samo jak stare bazy danych. Możliwe wartości to:  
  
- **dbLangGeneral** angielski, niemiecki, francuski, portugalski, włoski i hiszpański Modern  
  
- **dbLangArabic** arabski  
  
- **dbLangCyrillic** rosyjski  
  
- **dbLangCzech** czeski  
  
- **dbLangDutch** holenderski  
  
- **dbLangGreek** grecki  
  
- **dbLangHebrew** (wersja hebrajska)  
  
- **dbLangHungarian** węgierski  
  
- **dbLangIcelandic** islandzkim  
  
- **dbLangNordic** języki nordyckie (Microsoft Jet aparatu bazy danych wersji 1.0 tylko)  
  
- **dbLangNorwdan** norweski i duński  
  
- **dbLangPolish** Polski  
  
- **dbLangSpanish** hiszpański (tradycyjny)  
  
- **dbLangSwedfin** szwedzki i fiński  
  
- **dbLangTurkish** turecki  
  
 `nOptions`  
 Określa jedną lub więcej opcji dla docelowej bazy danych, `lpszDestName`. W przypadku pominięcia tego argumentu akceptując wartości domyślne `lpszDestName` będzie mieć tego samego szyfrowania i tej samej wersji co `lpszSrcName`. Możesz połączyć ze sobą **dbEncrypt** lub **dbDecrypt** opcji jedną z opcji wersji przy użyciu operatora bitowego OR. Możliwe wartości, które określają format bazy danych, a nie wersji aparatu bazy danych, to:  
  
- **dbEncrypt** szyfrowania podczas kompaktowania bazy danych.  
  
- **dbDecrypt** odszyfrować podczas kompaktowania bazy danych.  
  
- **dbVersion10** tworzenie używa aparatu bazy danych programu Microsoft Jet w wersji 1.0 podczas kompaktowania bazy danych.  
  
- **dbVersion11** tworzenie używa aparatu bazy danych programu Microsoft Jet w wersji 1.1 podczas kompaktowania bazy danych.  
  
- **dbVersion20** tworzenie używa aparatu bazy danych programu Microsoft Jet w wersji 2.0 podczas kompaktowania bazy danych.  
  
- **dbVersion30** tworzenie używa aparatu bazy danych programu Microsoft Jet w wersji 3.0 podczas kompaktowania bazy danych.  
  
 Można użyć **dbEncrypt** lub **dbDecrypt** w argumencie Opcje, aby określić, czy można zaszyfrować lub odszyfrować bazy danych, ponieważ jest on skompaktować. W przypadku pominięcia stała szyfrowania lub jeśli zawiera zarówno **dbDecrypt** i **dbEncrypt**, `lpszDestName` będą mieć tego samego szyfrowania jako `lpszSrcName`. Można jedną stałe wersji w argumencie Opcje określ wersję formatu danych skompaktowanego bazy danych. Stała ta dotyczy tylko wersji formatu danych `lpszDestName`. Można określić tylko jedną wersję stała. W przypadku pominięcia stałą wersji `lpszDestName` będzie mieć tej samej wersji co `lpszSrcName`. Można compact `lpszDestName` tylko do wersji, która jest taka sama lub nowsza niż `lpszSrcName`.  
  
> [!CAUTION]
>  Jeśli bazy danych nie są szyfrowane, jest to możliwe, nawet jeśli implementuje zabezpieczeń użytkownika/hasło, bezpośrednio odczytać plik binarny dysku, który stanowi bazy danych.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku zmiany danych w bazie danych, plik bazy danych może ulec fragmentacji i używać więcej miejsca na dysku niż to konieczne. Okresowo należy je bazy danych defragmentacji pliku bazy danych. Skompaktowanego baza danych jest zwykle mniejsze. Można również zmienić kolejność sortowania, szyfrowanie lub wersję formatu danych podczas kopiowania i baza danych.  
  
> [!CAUTION]
>  `CompactDatabase` Funkcji członkowskiej nie poprawnie przekonwertuje pełnej bazy danych programu Microsoft Access z jednej wersji do innego. Ten format danych zostanie przekonwertowany. Microsoft zdefiniowane dostępu do obiektów, takich jak formularzy i raportów, nie są konwertowane. Jednak dane zostanie prawidłowo skonwertowany.  
  
> [!TIP]
>  Można również użyć `CompactDatabase` można skopiować pliku bazy danych.  
  
 Aby uzyskać więcej informacji na temat kompaktowania baz danych zobacz temat "CompactDatabase Method" w pomocy DAO.  
  
##  <a name="create"></a>  CDaoWorkspace::Create  
 Wywołanie tej funkcji Członkowskich, aby utworzyć nowy obiekt DAO obszaru roboczego i powiązać ją z MFC `CDaoWorkspace` obiektu.  
  
```  
virtual void Create(
    LPCTSTR lpszName,  
    LPCTSTR lpszUserName,  
    LPCTSTR lpszPassword);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Ciąg znaków do 14, który unikatowej nazwy dla nowego obiektu obszaru roboczego. Należy podać nazwę. Aby uzyskać odpowiednie informacje zobacz temat "Właściwości Name" w pomocy DAO.  
  
 *lpszUserName*  
 Nazwa użytkownika właściciela obszaru roboczego. Aby poznać wymagania, zobacz `lpszDefaultUser` parametr [SetDefaultUser](#setdefaultuser) funkcji członkowskiej. Powiązane informacje zobacz temat "Właściwości nazwy użytkownika" w pomocy DAO.  
  
 `lpszPassword`  
 Hasło dla nowego obiektu obszaru roboczego. Hasło może zawierać maksymalnie 14 znaków i może zawierać dowolne znaki poza ASCII 0 (null). Hasła jest rozróżniana wielkość liter. Powiązane informacje zobacz temat "Hasło Property" w pomocy DAO.  
  
### <a name="remarks"></a>Uwagi  
 Ogólny proces tworzenia jest:  
  
1.  Utworzyć [CDaoWorkspace](#cdaoworkspace) obiektu.  
  
2.  Wywołanie obiektu **Utwórz** funkcji członkowskiej do tworzenia podstawowej roboczego DAO. Należy określić nazwę obszaru roboczego.  
  
3.  Opcjonalnie wywołać [Append](#append) Jeśli chcesz dodać do kolekcji obszarów roboczych aparat bazy danych obszaru roboczego. Możesz pracować z obszaru roboczego bez dołączenie jej.  
  
 Po **Utwórz** wywołania obiektu obszaru roboczego jest w stanie otwartym, gotowy do użycia. Nie wywołuj **Otwórz** po **Utwórz**. Nie wywołuj **Utwórz** Jeśli obszaru roboczego już istnieje w kolekcji obszarów roboczych. **Utwórz** aparat bazy danych nie już została zainicjowana dla aplikacji.  
  
##  <a name="getdatabasecount"></a>  CDaoWorkspace::GetDatabaseCount  
 Wywołanie tej funkcji Członkowskich, aby pobrać liczbę obiektów bazy danych DAO w kolekcji baz danych obszaru roboczego — liczba otwartych baz danych w obszarze roboczym.  
  
```  
short GetDatabaseCount();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba otwartych baz danych w obszarze roboczym.  
  
### <a name="remarks"></a>Uwagi  
 `GetDatabaseCount` jest przydatne w przypadku pętli wszystkich określonych baz danych w kolekcji baz danych obszaru roboczego. Aby uzyskać informacje dotyczące danego bazy danych w kolekcji, zobacz [GetDatabaseInfo](#getdatabaseinfo). Zwykle jest używane do wywoływania `GetDatabaseCount` liczbę otwartych baz danych, następnie użyć tego numeru jako indeks pętli powtarzane wywołania `GetDatabaseInfo`.  
  
##  <a name="getdatabaseinfo"></a>  CDaoWorkspace::GetDatabaseInfo  
 Wywołanie tej funkcji Członkowskich uzyskać różne rodzaje informacji o otwarcie bazy danych, w obszarze roboczym.  
  
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
 `nIndex`  
 Liczony od zera indeks w kolekcji baz danych obszaru roboczego, wyszukiwanie według indeksu obiektu bazy danych.  
  
 `dbinfo`  
 Odwołanie do [cdaodatabaseinfo —](../../mfc/reference/cdaodatabaseinfo-structure.md) obiekt, który zwraca żądane informacje.  
  
 `dwInfoOptions`  
 Opcje, które określają, które informacje o bazie danych do pobrania. Dostępne opcje są wyświetlane tutaj wraz z co spowodują one funkcja zwracająca:  
  
- `AFX_DAO_PRIMARY_INFO` (Ustawienie domyślne) Nazwa nadaje się do aktualizacji, transakcje  
  
- `AFX_DAO_SECONDARY_INFO` Informacje o podstawowym plus: wersja, kolejność sortowania, limit czasu zapytania  
  
- `AFX_DAO_ALL_INFO` Głównych i dodatkowych informacji plus: połączenie  
  
 `lpszName`  
 Nazwa obiektu bazy danych wyszukiwania według nazwy. Nazwa to ciąg znaków do 14 unikatowej nazwy dla nowego obiektu obszaru roboczego.  
  
### <a name="remarks"></a>Uwagi  
 Jedna wersja funkcji umożliwia wyszukiwanie bazy danych przez indeks. Druga wersja umożliwia wyszukiwania według nazwy bazy danych.  
  
 Opis informacje zwracane w `dbinfo`, zobacz [cdaodatabaseinfo —](../../mfc/reference/cdaodatabaseinfo-structure.md) struktury. Ta struktura ma elementów członkowskich, które odpowiadają informacje wymienione powyżej w opisie `dwInfoOptions`. Gdy użytkownik żąda informacji o jeden poziom, można pobrać informacji o żadnych poprzednich poziomach.  
  
##  <a name="getinipath"></a>  CDaoWorkspace::GetIniPath  
 Wywołanie tej funkcji Członkowskich do uzyskania lokalizacji bazy danych programu Microsoft Jet aparatu inicjowania ustawień w rejestrze systemu Windows.  
  
```  
static CString PASCAL GetIniPath();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) zawierający lokalizacji w rejestrze.  
  
### <a name="remarks"></a>Uwagi  
 Lokalizacja służy do uzyskiwania informacji na temat ustawień aparatu bazy danych. Zwrócone informacje jest rzeczywistą nazwą podklucza rejestru.  
  
 Aby uzyskać odpowiednie informacje zobacz tematy "IniPath Property" i "Dostosowywanie systemu Windows rejestru ustawienia dla Data Access" w pomocy DAO.  
  
##  <a name="getisolateodbctrans"></a>  CDaoWorkspace::GetIsolateODBCTrans  
 Wywołanie tej funkcji Członkowskich, aby uzyskać bieżącą wartość właściwości DAO IsolateODBCTrans dla obszaru roboczego.  
  
```  
BOOL GetIsolateODBCTrans();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli ODBC — transakcje są izolowane; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 W niektórych sytuacjach konieczne może mieć wiele równoczesnych transakcji oczekujących na tej samej bazy danych ODBC. Aby to zrobić, należy otworzyć oddzielne obszar roboczy dla każdej transakcji. Należy pamiętać, że chociaż każdego obszaru roboczego może mieć własną połączenia ODBC w bazie danych, to zmniejsza wydajność systemu. Ponieważ izolacji transakcji nie jest zazwyczaj wymagane, są domyślnie udostępnione ODBC — połączenia z wielu obiektów roboczym otwarty przez tego samego użytkownika.  
  
 Niektóre serwery ODBC, takich jak Microsoft SQL Server, nie zezwalają na jedno połączenie równoczesnych transakcji. Jeśli potrzebujesz więcej niż jednej transakcji równocześnie oczekujących bazy danych, ustaw właściwość IsolateODBCTrans na **TRUE** w każdym obszarze roboczym zaraz po jego otwarciu. Dzięki temu oddzielnego połączenia ODBC dla każdego obszaru roboczego.  
  
 Powiązane informacje zobacz temat "IsolateODBCTrans Property" w pomocy DAO.  
  
##  <a name="getlogintimeout"></a>  CDaoWorkspace::GetLoginTimeout  
 Wywołanie tej funkcji Członkowskich, aby uzyskać bieżącą wartość właściwości DAO LoginTimeout dla obszaru roboczego.  
  
```  
static short PASCAL GetLoginTimeout();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba sekund, zanim wystąpi błąd podczas próby logowania do bazy danych ODBC.  
  
### <a name="remarks"></a>Uwagi  
 Ta wartość reprezentuje liczbę sekund, zanim wystąpi błąd podczas próby logowania do bazy danych ODBC. Domyślne ustawienie LoginTimeout to 20 sekund. Gdy LoginTimeout jest ustawiona na 0, nie przekroczony limit czasu i komunikację ze źródłem danych może przestać odpowiadać.  
  
 Próbujesz zalogować się do bazy danych ODBC, takich jak Microsoft SQL Server, połączenie może zakończyć się niepowodzeniem w wyniku błędy sieciowe lub ponieważ na serwerze nie jest uruchomiona. Zamiast oczekiwania dla domyślnej 20 sekund nawiązywania połączenia, można określić czas oczekiwania aparatu bazy danych, przed generuje błąd. Logowanie do serwera odbywa się niejawnie jako część szereg różnych zdarzeń, takie jak uruchomienie kwerendy w bazie danych serwera zewnętrznego.  
  
 Powiązane informacje zobacz temat "LoginTimeout Property" w pomocy DAO.  
  
##  <a name="getname"></a>  CDaoWorkspace::GetName  
 Wywołanie tej funkcji członkowskich można uzyskać nazwy użytkownika podstawowych obiektu obszaru roboczego DAO `CDaoWorkspace` obiektu.  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) zawierające nazwę użytkownika obiekt DAO obszaru roboczego.  
  
### <a name="remarks"></a>Uwagi  
 Nazwa jest przydatne w przypadku uzyskiwania dostępu do obiektu DAO obszaru roboczego w kolekcji obszarów roboczych aparat bazy danych o nazwie.  
  
 Aby uzyskać odpowiednie informacje zobacz temat "Właściwości Name" w pomocy DAO.  
  
##  <a name="getusername"></a>  CDaoWorkspace::GetUserName  
 Wywołanie tej funkcji członkowskich można uzyskać nazwy właściciela obszaru roboczego.  
  
```  
CString GetUserName();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) reprezentujący właściciela obiektu obszaru roboczego.  
  
### <a name="remarks"></a>Uwagi  
 Można pobrać lub ustawić uprawnień dla właściciela obszaru roboczego, wywołanie DAO bezpośrednio, aby sprawdzić ustawienie właściwości uprawnienia; Określa, jakie uprawnienia, które użytkownik ma. Aby pracować z uprawnieniami, potrzebny jest SYSTEM. Plik MDA.  
  
 Informacje o wywołującym DAO bezpośrednio, zobacz [54 Uwaga techniczna](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md). Powiązane informacje zobacz temat "Właściwości nazwy użytkownika" w pomocy DAO.  
  
##  <a name="getversion"></a>  CDaoWorkspace::GetVersion  
 Wywołanie tej funkcji członkowskich można ustalić wersji aparatu bazy danych programu Microsoft Jet w użyciu.  
  
```  
static CString PASCAL GetVersion();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) wskazujący wersję aparatu bazy danych skojarzony z obiektem.  
  
### <a name="remarks"></a>Uwagi  
 Wartość zwracana reprezentuje numer wersji w postaci "major.minor"; na przykład "3.0". Numer wersji produktu (na przykład 3.0) składa się z numerem wersji (3), okres i numer wersji (0).  
  
 Powiązane informacje zobacz temat "Właściwość Version" w pomocy DAO.  
  
##  <a name="getworkspacecount"></a>  CDaoWorkspace::GetWorkspaceCount  
 Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę obiektów DAO obszaru roboczego w kolekcji obszarów roboczych aparatu bazy danych.  
  
```  
short GetWorkspaceCount();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba otwartych obszarów roboczych w kolekcji obszarów roboczych.  
  
### <a name="remarks"></a>Uwagi  
 Ten licznik nie uwzględnia wszystkie otwarte obszary robocze nie są dołączane do kolekcji. `GetWorkspaceCount` jest to przydatne w przypadku pętli wszystkich zdefiniowanych obszarów roboczych w kolekcji obszarów roboczych. Aby uzyskać informacje dotyczące danego obszaru roboczego w kolekcji, zobacz [GetWorkspaceInfo](#getworkspaceinfo). Zwykle jest używane do wywoływania `GetWorkspaceCount` liczbę otwartych obszarów roboczych, następnie użyć tego numeru jako indeks pętli powtarzane wywołania `GetWorkspaceInfo`.  
  
##  <a name="getworkspaceinfo"></a>  CDaoWorkspace::GetWorkspaceInfo  
 Wywołanie tej funkcji Członkowskich uzyskać różne rodzaje informacji o Otwórz obszar roboczy w sesji.  
  
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
 `nIndex`  
 Liczony od zera indeks w kolekcji obszarów roboczych, wyszukiwanie według indeksu obiektu bazy danych.  
  
 `wkspcinfo`  
 Odwołanie do [cdaoworkspaceinfo —](../../mfc/reference/cdaoworkspaceinfo-structure.md) obiekt, który zwraca żądane informacje.  
  
 `dwInfoOptions`  
 Opcje, które określają, które informacje o obszaru roboczego do pobrania. Dostępne opcje są wyświetlane tutaj wraz z co spowodują one funkcja zwracająca:  
  
- `AFX_DAO_PRIMARY_INFO` (Ustawienie domyślne) Nazwa  
  
- `AFX_DAO_SECONDARY_INFO` Informacje o podstawowym plus: nazwa użytkownika  
  
- `AFX_DAO_ALL_INFO` Głównych i dodatkowych informacji plus: izolowania ODBCTrans  
  
 `lpszName`  
 Nazwa obiektu obszaru roboczego do wyszukiwania według nazwy. Nazwa to ciąg znaków do 14 unikatowej nazwy dla nowego obiektu obszaru roboczego.  
  
### <a name="remarks"></a>Uwagi  
 Opis informacje zwracane w `wkspcinfo`, zobacz [cdaoworkspaceinfo —](../../mfc/reference/cdaoworkspaceinfo-structure.md) struktury. Ta struktura ma elementów członkowskich, które odpowiadają informacje wymienione powyżej w opisie `dwInfoOptions`. Gdy użytkownik żąda informacji o jeden poziom, można pobrać informacji o również poprzednich poziomach.  
  
##  <a name="idle"></a>  CDaoWorkspace::Idle  
 Wywołanie **bezczynny** aby zapewnić możliwość wykonania zadania w tle, które mogą nie być aktualne z powodu intensywnego przetwarzania danych aparatu bazy danych.  
  
```  
static void PASCAL Idle(int nAction = dbFreeLocks);
```  
  
### <a name="parameters"></a>Parametry  
 `nAction`  
 Akcja do wykonania podczas przetwarzania bezczynności. Obecnie jest jedyną prawidłową akcję **dbFreeLocks**.  
  
### <a name="remarks"></a>Uwagi  
 Dotyczy to często środowisk wielozadaniowości wielodostępnym, w których istnieje nie jest wystarczająco dużo czasu przetwarzania tła, aby zapewnić aktualność wszystkie rekordy w zestawie rekordów.  
  
> [!NOTE]
>  Wywoływanie **bezczynny** nie jest konieczne w przypadku baz danych utworzonych za pomocą aparatu bazy danych programu Microsoft Jet w wersji 3.0. Użyj **bezczynny** tylko dla baz danych utworzonych w starszych wersjach.  
  
 Zazwyczaj odczytu blokad zostaną usunięte i danymi w obiektach zestaw rekordów typu lokalnego dynamiczny jest aktualizowany tylko wtedy, gdy występują żadnych innych akcji (w tym ruchów myszy). Jeśli okresowo wywoływać **bezczynny**, podasz aparat bazy danych z czasem przetwarzania przez zwolnienie zadania w tle odnaleźć niepotrzebne odczytu blokad. Określanie **dbFreeLocks** stałej jako argumentu opóźnienie przetwarzania do czasu zwolnienia wszystkich blokad odczytu.  
  
 Funkcji członkowskiej nie jest potrzebna w środowiskach pojedynczego użytkownika, chyba że jest uruchomionych wiele wystąpień aplikacji. **Bezczynny** funkcji członkowskiej może zwiększyć wydajność w środowisku wielodostępnym, ponieważ wymusi aparat bazy danych można opróżnić danych na dysku, zwolnienie blokady w pamięci. Można również zwolnić blokady odczytu, wykonując operacje częścią transakcji.  
  
 Powiązane informacje zobacz temat "W stanie bezczynności Method" w pomocy DAO.  
  
##  <a name="isopen"></a>  CDaoWorkspace::IsOpen  
 Wywołanie tej funkcji elementu członkowskiego, aby określić, czy `CDaoWorkspace` obiekt jest otwarty — oznacza to, czy obiekt MFC został zainicjowany przez wywołanie do [Otwórz](#open) lub wywołanie [Utwórz](#create).  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli obiekt obszaru roboczego jest otwarty; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Można wywołać żadnego elementu członkowskiego funkcje obszaru roboczego, który jest w stanie otwartym.  
  
##  <a name="m_pdaoworkspace"></a>  CDaoWorkspace::m_pDAOWorkspace  
 Wskaźnik do obszaru roboczego obiekt DAO.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego elementu członkowskiego danych, jeśli konieczne bezpośredni dostęp do obiektu źródłowego DAO. Możesz wywołać obiekt DAO interfejsy przez ten wskaźnik.  
  
 Informacje o uzyskiwaniu dostępu do obiektów DAO bezpośrednio, zobacz [54 Uwaga techniczna](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).  
  
##  <a name="open"></a>  CDaoWorkspace::Open  
 Otwiera jawnie obiektu obszaru roboczego skojarzonego z jego DAO domyślny obszar roboczy.  
  
```  
virtual void Open(LPCTSTR lpszName = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Nazwę obiektu DAO obszaru roboczego, aby otworzyć — ciąg znaków do 14 unikatowej nazwy obszaru roboczego. Zaakceptuj wartość domyślną **NULL** jawnie otworzyć domyślny obszar roboczy. Nazewnictwa wymagania, zobacz `lpszName` parametr [Utwórz](#create). Aby uzyskać odpowiednie informacje zobacz temat "Właściwości Name" w pomocy DAO.  
  
### <a name="remarks"></a>Uwagi  
 Po konstruowania `CDaoWorkspace` obiektów, wywołania tej funkcji członkowskiej, wykonaj jedną z następujących czynności:  
  
-   Otwierać domyślny obszar roboczy. Przekaż **NULL** dla `lpszName`.  
  
-   Otwórz istniejącą `CDaoWorkspace` obiektu, jest członkiem kolekcji obszarów roboczych według nazwy. Podaj prawidłową nazwę istniejącego obiektu obszaru roboczego.  
  
 **Otwórz** umieszcza obiekt workspace otwarte i również inicjuje aparatu bazy danych, jeśli go nie już została zainicjowana dla aplikacji.  
  
 Mimo że wiele `CDaoWorkspace` elementu członkowskiego funkcji można wywołać tylko po otwarciu obszaru roboczego, następujące funkcje Członkowskie, które działają na aparacie bazy danych, są dostępne po wykonaniu konstrukcji obiektu języka C++, ale przed wywołaniem **Otwórz** :  
  
||||  
|-|-|-|  
|[Utwórz](#create)|[GetVersion](#getversion)|[SetDefaultUser](#setdefaultuser)|  
|[GetIniPath](#getinipath)|[W stanie bezczynności](#idle)|[SetIniPath](#setinipath)|  
|[GetLoginTimeout](#getlogintimeout)|[SetDefaultPassword](#setdefaultpassword)|[SetLoginTimeout](#setlogintimeout)|  
  
##  <a name="repairdatabase"></a>  CDaoWorkspace::RepairDatabase  
 Wywołanie tej funkcji Członkowskich, jeśli chcesz podjąć próbę naprawy uszkodzenia bazy danych, który uzyskuje dostęp do aparatu bazy danych programu Microsoft Jet.  
  
```  
static void PASCAL RepairDatabase(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Ścieżkę i nazwę istniejącego pliku bazy danych aparatu Microsoft Jet. Jeśli pominięto ścieżkę, przeszukiwane będą tylko bieżący katalog. Jeśli system obsługuje jednolitego konwencji nazewnictwa (UNC), również można określić ścieżkę sieci, takich jak: "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB". (Podwójnych odwróconych są wymagane w ciągu ścieżki, ponieważ "\\" jest znak ucieczki C++.)  
  
### <a name="remarks"></a>Uwagi  
 Należy zamknąć bazy danych, określonej przez `lpszName` przed jego naprawy. W środowisku wielodostępnym inni użytkownicy nie mogą mieć `lpszName` otworzyć, gdy są naprawianie go. Jeśli `lpszName` nie został zamknięty lub nie jest dostępna wyłącznie do użytku, wystąpi błąd.  
  
 Ta funkcja członkowska próbuje naprawić bazę danych, która została oznaczona jako prawdopodobnie uszkodzony przez operację zapisu niekompletne. Może to wystąpić, jeśli został nieoczekiwanie zamknięty aplikacji przy użyciu aparatu bazy danych programu Microsoft Jet z powodu problemu zasilania komputera lub awaria sprzętu. Po ukończeniu operacji i wywołanie [Zamknij](../../mfc/reference/cdaodatabase-class.md#close) funkcji członkowskiej lub zamknij aplikację w zwykły sposób, bazy danych nie zostanie oznaczona jako jest prawdopodobnie uszkodzony.  
  
> [!NOTE]
>  Po naprawie bazy danych, jest również dobrym pomysłem jest compact za pomocą [CompactDatabase](#compactdatabase) funkcji członkowskiej defragmentacji pliku i aby odzyskać miejsce na dysku.  
  
 Aby uzyskać więcej informacji o naprawianiu baz danych zobacz temat "RepairDatabase Method" w pomocy DAO.  
  
##  <a name="rollback"></a>  CDaoWorkspace::Rollback  
 Wywołanie tej funkcji Członkowskich zakończenia bieżącej transakcji i przywrócić wszystkie bazy danych w obszarze roboczym do stanu przed transakcja została rozpoczęta.  
  
```  
void Rollback();
```  
  
### <a name="remarks"></a>Uwagi  
  
> [!CAUTION]
>  W ramach jednego obiektu obszaru roboczego transakcje są zawsze globalne do obszaru roboczego i nie są ograniczone do tylko jednej bazy danych lub zestawu rekordów. Jeśli wykonywania operacji na więcej niż jednej bazy danych lub zestawu rekordów w ramach transakcji obszaru roboczego, **wycofywania** przywraca wszystkie operacje we wszystkich tych baz danych i zestawy rekordów.  
  
 Jeśli obiekt obszar roboczy zostanie zamknięty bez zapisywania i wycofanie wszystkich oczekujących transakcji, transakcje są automatycznie wycofana. Jeśli należy wywołać [CommitTrans](#committrans) lub **wycofywania** bez wywoływania pierwszego elementu [BeginTrans](#begintrans), wystąpi błąd.  
  
> [!NOTE]
>  Po rozpoczęciu transakcji aparatu bazy danych rejestruje jego operacji w pliku przechowywane w katalogu określonym przez zmienną środowiskową TEMP na stacji roboczej. Jeśli plik dziennika transakcji zmagazynowane dostępny magazyn na dysku TEMP, aparatu bazy danych spowoduje MFC zgłosić `CDaoException` (błąd DAO 2004). W tym punkcie, jeśli wywołujesz **CommitTrans**nieokreśloną liczbę operacji są zatwierdzone, ale pozostałych niezakończona operacji zostaną utracone i operacja ma być uruchomiony ponownie. Wywoływanie **wycofywania** zwalnia dziennik transakcji i wycofuje wszystkie operacje w transakcji.  
  
##  <a name="setdefaultpassword"></a>  CDaoWorkspace::SetDefaultPassword  
 Wywołanie tej funkcji członkowskich można ustawić domyślne hasło korzystającego z aparatem bazy danych, gdy tworzony jest obiekt obszaru roboczego bez określonego hasła.  
  
```  
static void PASCAL SetDefaultPassword(LPCTSTR lpszPassword);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszPassword`  
 Domyślne hasło. Hasło może zawierać maksymalnie 14 znaków i może zawierać dowolne znaki poza ASCII 0 (null). Hasła jest rozróżniana wielkość liter.  
  
### <a name="remarks"></a>Uwagi  
 Domyślne hasło, które można ustawić ma zastosowanie do nowych obszarów roboczych, utworzonych po wywołaniu. Podczas tworzenia kolejnych obszarów roboczych, nie należy określić hasło w [Utwórz](#create) wywołania.  
  
 Aby użyć tej funkcji Członkowskich:  
  
1.  Utworzyć `CDaoWorkspace` obiekt, ale nie należy wywoływać **Utwórz**.  
  
2.  Wywołanie `SetDefaultPassword` i, jeśli chcesz [SetDefaultUser](#setdefaultuser).  
  
3.  Wywołanie **Utwórz** dla tego obiektu obszaru roboczego lub kolejne bez określania hasła.  
  
 Domyślnie właściwość DefaultUser ma wartość "Administrator" i właściwość DefaultPassword jest ustawiona na ciąg pusty ("").  
  
 Aby uzyskać więcej informacji o zabezpieczeniach zobacz temat "Właściwości uprawnień" w pomocy DAO. Aby uzyskać odpowiednie informacje zobacz tematy "DefaultPassword właściwości" i "DefaultUser" w pomocy DAO.  
  
##  <a name="setdefaultuser"></a>  CDaoWorkspace::SetDefaultUser  
 Wywołanie tej funkcji członkowskich można ustawić domyślną nazwę użytkownika używaną przez aparat bazy danych podczas tworzenia obiektu obszaru roboczego bez określonej nazwy użytkownika.  
  
```  
static void PASCAL SetDefaultUser(LPCTSTR lpszDefaultUser);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszDefaultUser`  
 Domyślna nazwa użytkownika. Nazwę użytkownika można 1-20 znaków i zawierać znaki alfabetyczne, znaki akcentowane cyfry, spacje i symbole z wyjątkiem: "(znaki cudzysłowu) / (ukośnik), \ (ukośnik odwrotny) \[ \] (nawiasy kwadratowe): (dwukropek), &#124; () potok) \< (mniej — niż znak), > (większa — niż znak), + (znak plus) = (równa logowania), (średnik), (przecinek) (znak zapytania) * (gwiazdka), początkowe spacje i znaki kontrolne (ASCII 00 do ASCII 31). Powiązane informacje zobacz temat "Właściwości nazwy użytkownika" w pomocy DAO.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna nazwa użytkownika, który można ustawić ma zastosowanie do nowych obszarów roboczych, utworzonych po wywołaniu. Podczas tworzenia kolejnych obszarów roboczych, nie trzeba określić nazwę użytkownika w [Utwórz](#create) wywołania.  
  
 Aby użyć tej funkcji Członkowskich:  
  
1.  Utworzyć `CDaoWorkspace` obiekt, ale nie należy wywoływać **Utwórz**.  
  
2.  Wywołanie `SetDefaultUser` i, jeśli chcesz [SetDefaultPassword](#setdefaultpassword).  
  
3.  Wywołanie **Utwórz** dla tego obiektu obszaru roboczego lub kolejne bez określania nazwy użytkownika.  
  
 Domyślnie właściwość DefaultUser ma wartość "Administrator" i właściwość DefaultPassword jest ustawiona na ciąg pusty ("").  
  
 Aby uzyskać odpowiednie informacje zobacz tematy "DefaultUser właściwości" i "DefaultPassword" w pomocy DAO.  
  
##  <a name="setinipath"></a>  CDaoWorkspace::SetIniPath  
 Wywołanie tej funkcji Członkowskich, aby określić lokalizację ustawień rejestru systemu Windows dla aparatu bazy danych programu Microsoft Jet.  
  
```  
static void PASCAL SetIniPath(LPCTSTR lpszRegistrySubKey);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszRegistrySubkey*  
 Ciąg zawierający nazwę podklucza rejestru systemu Windows w lokalizacji Ustawienia aparatu bazy danych programu Microsoft Jet lub parametrów potrzebnych do zainstalowania ISAM baz danych.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie `SetIniPath` tylko wtedy, gdy należy określić ustawienia specjalne. Aby uzyskać więcej informacji zobacz temat "IniPath Property" w pomocy DAO.  
  
> [!NOTE]
>  Wywołanie `SetIniPath` podczas instalacji aplikacji, nie po uruchomieniu aplikacji. `SetIniPath` musi zostać wywołana przed otwarciem wszystkie obszary robocze, baz danych lub zestawów rekordów; w przeciwnym razie MFC zgłasza wyjątek.  
  
 Mechanizm ten umożliwia konfigurowanie aparatu bazy danych przy użyciu ustawień rejestru dostarczane przez użytkownika. Zakres tego atrybutu jest ograniczony do aplikacji i nie można zmienić bez ponownego uruchamiania aplikacji.  
  
##  <a name="setisolateodbctrans"></a>  CDaoWorkspace::SetIsolateODBCTrans  
 Wywołanie tej funkcji członkowskich można ustawić wartości właściwości DAO IsolateODBCTrans dla obszaru roboczego.  
  
```  
void SetIsolateODBCTrans(BOOL bIsolateODBCTrans);
```  
  
### <a name="parameters"></a>Parametry  
 *bIsolateODBCTrans*  
 Przekaż **TRUE** Jeśli chcesz rozpocząć izolowanie ODBC — transakcje. Przekaż **FALSE** Jeśli chcesz zatrzymać izolowanie ODBC — transakcje.  
  
### <a name="remarks"></a>Uwagi  
 W niektórych sytuacjach konieczne może mieć wiele równoczesnych transakcji oczekujących na tej samej bazy danych ODBC. Aby to zrobić, należy otworzyć oddzielne obszar roboczy dla każdej transakcji. Chociaż każdego obszaru roboczego może mieć własną połączenia ODBC w bazie danych, to zmniejsza wydajność systemu. Ponieważ izolacji transakcji nie jest zazwyczaj wymagane, są domyślnie udostępnione ODBC — połączenia z wielu obiektów roboczym otwarty przez tego samego użytkownika.  
  
 Niektóre serwery ODBC, takich jak Microsoft SQL Server, nie zezwalają na jedno połączenie równoczesnych transakcji. Jeśli potrzebujesz więcej niż jednej transakcji równocześnie oczekujących bazy danych, ustaw właściwość IsolateODBCTrans na **TRUE** w każdym obszarze roboczym zaraz po jego otwarciu. Dzięki temu oddzielnego połączenia ODBC dla każdego obszaru roboczego.  
  
##  <a name="setlogintimeout"></a>  CDaoWorkspace::SetLoginTimeout  
 Wywołanie tej funkcji członkowskich można ustawić wartości właściwości DAO LoginTimeout dla obszaru roboczego.  
  
```  
static void PASCAL SetLoginTimeout(short nSeconds);
```  
  
### <a name="parameters"></a>Parametry  
 `nSeconds`  
 Liczba sekund, zanim wystąpi błąd podczas próby logowania do bazy danych ODBC.  
  
### <a name="remarks"></a>Uwagi  
 Ta wartość reprezentuje liczbę sekund, zanim wystąpi błąd podczas próby logowania do bazy danych ODBC. Domyślne ustawienie LoginTimeout to 20 sekund. Gdy LoginTimeout jest ustawiona na 0, nie przekroczony limit czasu i komunikację ze źródłem danych może przestać odpowiadać.  
  
 Próbujesz zalogować się do bazy danych ODBC, takich jak Microsoft SQL Server, połączenie może zakończyć się niepowodzeniem w wyniku błędy sieciowe lub ponieważ na serwerze nie jest uruchomiona. Zamiast oczekiwania dla domyślnej 20 sekund nawiązywania połączenia, można określić czas oczekiwania aparatu bazy danych, przed generuje błąd. Logowanie do serwera odbywa się niejawnie jako część szereg różnych zdarzeń, takie jak uruchomienie kwerendy w bazie danych serwera zewnętrznego. Wartość limitu czasu jest określany przez bieżące ustawienie właściwości LoginTimeout.  
  
 Powiązane informacje zobacz temat "LoginTimeout Property" w pomocy DAO.  
  
## <a name="see-also"></a>Zobacz też  
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)   
 [Cdaorecordset — klasa](../../mfc/reference/cdaorecordset-class.md)   
 [Klasa CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)   
 [Klasa CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)   
 [Klasa CDaoException](../../mfc/reference/cdaoexception-class.md)
