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
ms.openlocfilehash: 7e6210f8c1b1fd1bd19efb74ca68c7a1bed3f7f1
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39209134"
---
# <a name="cdaoworkspace-class"></a>Klasa CDaoWorkspace
Zarządza sesję o nazwie bazy danych chronionej hasłem z logowania do wylogowania przez pojedynczego użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDaoWorkspace : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDaoWorkspace::CDaoWorkspace](#cdaoworkspace)|Tworzy obiekt obszaru roboczego. Następnie wywołaj `Create` lub `Open`.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDaoWorkspace::Append](#append)|Dołącza nowo utworzonego obszaru roboczego do kolekcji obszarów roboczych z aparatem bazy danych.|  
|[CDaoWorkspace::BeginTrans](#begintrans)|Rozpoczyna nową transakcję, która ma zastosowanie do wszystkich baz danych otwartych w obszarze roboczym.|  
|[CDaoWorkspace::Close](#close)|Zamyka obszar roboczy i wszystkie obiekty, które zawiera. Oczekujące transakcje są wycofywane.|  
|[CDaoWorkspace::CommitTrans](#committrans)|Kończy bieżącą transakcję i zapisuje zmiany.|  
|[CDaoWorkspace::CompactDatabase](#compactdatabase)|Kompaktuje lub jest duplikatem bazy danych.|  
|[CDaoWorkspace::Create](#create)|Tworzy nowy obiekt DAO obszaru roboczego.|  
|[CDaoWorkspace::GetDatabaseCount](#getdatabasecount)|Zwraca liczbę obiektów bazy danych DAO w kolekcji baz danych obszaru roboczego.|  
|[CDaoWorkspace::GetDatabaseInfo](#getdatabaseinfo)|Zwraca informacje o określonej bazy danych DAO zdefiniowany w kolekcji baz danych obszaru roboczego.|  
|[CDaoWorkspace::GetIniPath](#getinipath)|Zwraca lokalizację bazy danych Microsoft Jet aparatu inicjowania ustawień w rejestrze systemu Windows.|  
|[CDaoWorkspace::GetIsolateODBCTrans](#getisolateodbctrans)|Zwraca wartość wskazującą, czy wiele transakcji dotyczących tego samego źródła danych ODBC są izolowane za pośrednictwem wymuszone wielu połączeń ze źródłem danych.|  
|[CDaoWorkspace::GetLoginTimeout](#getlogintimeout)|Zwraca liczbę sekund, zanim wystąpi błąd, gdy użytkownik próbuje zalogować się do bazy danych ODBC.|  
|[CDaoWorkspace::GetName](#getname)|Zwraca nazwę użytkownika dla obiektu obszaru roboczego.|  
|[CDaoWorkspace::GetUserName](#getusername)|Zwraca wartość Nazwa użytkownika określona podczas tworzenia obszaru roboczego. Jest to nazwa właściciela obszaru roboczego.|  
|[CDaoWorkspace::GetVersion](#getversion)|Zwraca ciąg, który zawiera wersję aparatu bazy danych skojarzone z obszarem roboczym.|  
|[CDaoWorkspace::GetWorkspaceCount](#getworkspacecount)|Zwraca liczbę obiektów w obszarze roboczym DAO w kolekcji obszarów roboczych z aparatem bazy danych.|  
|[CDaoWorkspace::GetWorkspaceInfo](#getworkspaceinfo)|Zwraca informacje dotyczące określonego obszaru roboczego DAO zdefiniowany w kolekcji obszarów roboczych z aparatem bazy danych.|  
|[CDaoWorkspace::Idle](#idle)|Umożliwia aparatu bazy danych do wykonywania zadań w tle.|  
|[CDaoWorkspace::IsOpen](#isopen)|Zwraca wartość różną od zera, jeśli obszar roboczy jest Otwórz.|  
|[CDaoWorkspace::Open](#open)|Jawnie zostanie otwarty obiekt obszar roboczy, skojarzone z jego DAO domyślnego obszaru roboczego.|  
|[CDaoWorkspace::RepairDatabase](#repairdatabase)|Próbuje naprawić uszkodzonej bazy danych.|  
|[CDaoWorkspace::Rollback](#rollback)|Kończy bieżącą transakcję i zapisuj zmian.|  
|[CDaoWorkspace::SetDefaultPassword](#setdefaultpassword)|Określa hasło, która używa aparatu bazy danych, gdy tworzony jest obiekt w obszarze roboczym bez określonego hasła.|  
|[CDaoWorkspace::SetDefaultUser](#setdefaultuser)|Ustawia nazwę użytkownika, która używa aparatu bazy danych, gdy tworzony jest obiekt w obszarze roboczym bez określonej nazwy użytkownika.|  
|[CDaoWorkspace::SetIniPath](#setinipath)|Ustawia lokalizację bazy danych Microsoft Jet aparatu inicjowania ustawień w rejestrze systemu Windows.|  
|[CDaoWorkspace::SetIsolateODBCTrans](#setisolateodbctrans)|Określa, czy wiele transakcji dotyczących tego samego źródła danych ODBC są izolowane, wymuszając wielu połączeń ze źródłem danych.|  
|[CDaoWorkspace::SetLoginTimeout](#setlogintimeout)|Ustawia liczbę sekund, zanim wystąpi błąd, gdy użytkownik próbuje zalogować się do źródła danych ODBC.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDaoWorkspace::m_pDAOWorkspace](#m_pdaoworkspace)|Wskazuje obiekt DAO, aby obszar roboczy.|  
  
## <a name="remarks"></a>Uwagi  
 W większości przypadków wiele obszarów roboczych nie będą potrzebne, i nie należy do tworzenia obiektów jawne obszaru roboczego; Po otwarciu obiektów bazy danych i zestaw rekordów, używają firmy DAO domyślnego obszaru roboczego. Jednak jeśli to konieczne, można uruchamiać wiele sesji w danym momencie przez tworzenie obiektów dodatkowy obszar roboczy. Każdy obiekt obszaru roboczego może zawierać wiele obiektów otwartą bazę danych w jego własnej kolekcji baz danych. W MFC obszar roboczy to przede wszystkim Menedżera transakcji, określanie zestawu baz danych, otwórz wszystko w tym samym "transakcji przestrzenią".  
  
> [!NOTE]
>  Klasy bazy danych DAO różnią się od klas baz danych MFC, które są oparte na Open Database Connectivity (ODBC). Wszystkie nazwy klasy bazy danych DAO mają prefiks "CDao". Ogólnie rzecz biorąc klas MFC DAO w oparciu nadają się bardziej niż klas MFC, w oparciu o ODBC. Klasy oparte na DAO dostęp do danych za pomocą aparatu bazy danych Microsoft Jet, w tym sterowników ODBC. Obsługują one również operacji języka definicji danych (DDL), takich jak tworzenie baz danych i dodawanie tabel i pól za pośrednictwem klasy, bez konieczności wywoływanie obiektów DAO bezpośrednio.  
  
## <a name="capabilities"></a>Możliwości  
 Klasa `CDaoWorkspace` udostępnia następujące:  
  
-   Jawny dostęp, jeśli to konieczne, do domyślnego obszaru roboczego, utworzone przez inicjowanie aparatu bazy danych. Zwykle użyć DAO w domyślnym obszarze roboczym niejawnie przez tworzenie obiektów bazy danych i zestaw rekordów.  
  
-   Otwórz obszar transakcji, w którym transakcje mają zastosowanie do wszystkich baz danych w obszarze roboczym. Możesz utworzyć dodatkowe obszary robocze do zarządzania miejsca do magazynowania w oddzielnej transakcji.  
  
-   Interfejs wiele właściwości podstawowego aparatu bazy danych Microsoft Jet (patrz funkcji statycznych elementów członkowskich). Otwieranie lub tworzenie obszaru roboczego lub wywoływania statycznej funkcji członkowskiej przed Otwórz lub Utwórz, inicjuje aparat bazy danych.  
  
-   Dostęp do kolekcji obszarów roboczych z aparatem bazy danych, która przechowuje wszystkie aktywne obszary robocze, które zostały dołączone do niego. Można również tworzyć i Praca z obszarami roboczymi bez dodając je do kolekcji.  
  
## <a name="security"></a>Zabezpieczenia  
 MFC nie implementuje kolekcje użytkowników i grup w DAO, które są używane do kontroli zabezpieczeń. Jeśli potrzebujesz tych aspektów DAO, należy zaprogramować je samodzielnie za pomocą bezpośrednich wywołań interfejsów DAO. Aby uzyskać informacje, zobacz [techniczne 54 Uwaga](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).  
  
## <a name="usage"></a>Użycie  
 Można użyć klasy `CDaoWorkspace` do:  
  
-   Jawnie Otwórz domyślnego obszaru roboczego.  
  
     Korzystanie z domyślnego obszaru roboczego jest zazwyczaj niejawne — po otwarciu nowego [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obiektów. Ale możesz potrzebować dostępu do niego jawnie — na przykład, aby właściwości aparatu bazy danych programu access lub kolekcji obszarów roboczych. Zobacz "Użycia niejawnego domyślnego obszaru roboczego" poniżej.  
  
-   Tworzenie nowych obszarów roboczych. Wywołaj [Append](#append) Jeśli chcesz dodać je do kolekcji obszarów roboczych.  
  
-   Otwórz istniejący obszar roboczy w kolekcji obszarów roboczych.  
  
 Tworzenie nowego obszaru roboczego, który jeszcze nie istnieje w kolekcji jest opisany w obszarach roboczych [Utwórz](#create) funkcja elementu członkowskiego. Obszar roboczy obiekty nie są zachowywane w jakikolwiek sposób między sesjami aparatu datababase. Jeśli aplikacja łączy się z MFC statycznie, zakończeniem aplikacji deinicjuje aparatu bazy danych. Jeśli aplikacja łączy dynamicznie z MFC, aparat bazy danych została zainicjowana, gdy biblioteki MFC DLL jest zwalniana.  
  
 Jawnie Otwieranie domyślnego obszaru roboczego lub otwierania istniejącego obszaru roboczego w kolekcji obszarów roboczych została opisana w sekcji [Otwórz](#open) funkcja elementu członkowskiego.  
  
 Kończenie sesji obszaru roboczego, zamykając obszar roboczy z [Zamknij](#close) funkcja elementu członkowskiego. `Close` Zamyka wszystkie bazy danych, które nie zostało zamknięte wcześniej, wycofywanie ewentualnych transakcji niezatwierdzonych.  
  
## <a name="transactions"></a>Transakcje  
 DAO zarządza transakcji na poziomie obszaru roboczego. Dzięki temu transakcji w obszarze roboczym z wieloma bazami danych otwórz mają zastosowanie do wszystkich baz danych. Na przykład, jeśli dwie bazy danych mają niezatwierdzonych aktualizacje i możesz wywołać [CommitTrans](#committrans), wszystkie aktualizacje są zatwierdzone. Jeśli chcesz ograniczyć transakcji w jednej bazie danych, należy obiekt oddzielny obszar roboczy dla niego.  
  
## <a name="implicit-use-of-the-default-workspace"></a>Jawne użycie domyślnego obszaru roboczego  
 MFC używa domyślnego obszaru roboczego w DAO niejawnie w następujących okolicznościach:  
  
-   Jeśli tworzysz nową `CDaoDatabase` obiektu, ale nie zostanie za pomocą istniejącego `CDaoWorkspace` obiektu MFC tworzy obiekt tymczasowy obszar roboczy, co odpowiada firmy DAO domyślnego obszaru roboczego. Jeśli tak zrobisz dla wielu baz danych, wszystkie obiekty bazy danych są skojarzone z domyślnego obszaru roboczego. Możesz uzyskać dostęp przez obszar roboczy bazy danych za pośrednictwem `CDaoDatabase` element członkowski danych.  
  
-   Podobnie jeśli tworzysz `CDaoRecordset` obiektu bez podawania wskaźnik do `CDaoDatabase` obiektu MFC tworzy obiekt tymczasowej bazy danych i przy użyciu rozszerzenia, obiekt tymczasowy obszar roboczy. Dostępny zestaw rekordów bazy danych, a pośrednio obszaru roboczego, za pośrednictwem `CDaoRecordset` element członkowski danych.  
  
## <a name="other-operations"></a>Inne operacje  
 Inne operacje bazy danych również są dostarczone, takich jak naprawianie uszkodzonej bazy danych lub kompaktowanie bazy danych.  
  
 Aby uzyskać informacje dotyczące wywoływanie obiektów DAO bezpośrednio o bezpieczeństwie DAO, zobacz [techniczne 54 Uwaga](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoWorkspace`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  
  
##  <a name="append"></a>  CDaoWorkspace::Append  
 Wywołaj tę funkcję elementu członkowskiego, po wywołaniu metody [Utwórz](#create).  
  
```  
virtual void Append();
```  
  
### <a name="remarks"></a>Uwagi  
 `Append` dołącza obiektu nowo utworzonego obszaru roboczego do kolekcji obszarów roboczych z aparatem bazy danych. Obszary robocze nie są zachowywane między sesjami aparatu bazy danych; są one przechowywane tylko w pamięci, a nie na dysku. Nie masz do dołączenia do obszaru roboczego; Jeśli tego nie zrobisz, możesz go nadal używać.  
  
 Obszar roboczy dołączonych pozostaje w kolekcji obszarów roboczych, w aktywny, otwarte, dopóki nie zostanie wywołana jego [Zamknij](#close) funkcja elementu członkowskiego.  
  
 Aby uzyskać powiązane informacje zobacz temat "Dołącz metody" w Pomocy programu DAO.  
  
##  <a name="begintrans"></a>  CDaoWorkspace::BeginTrans  
 Wywołaj tę funkcję elementu członkowskiego, aby zainicjować transakcji.  
  
```  
void BeginTrans();
```  
  
### <a name="remarks"></a>Uwagi  
 Po wywołaniu metody `BeginTrans`, aktualizacje wprowadzone do struktury danych lub bazy danych zostały wprowadzone podczas zatwierdzania transakcji. Ponieważ obszaru roboczego definiuje odstęp pojedynczej transakcji, transakcja ma zastosowanie do wszystkich otwartych baz danych w obszarze roboczym. Istnieją dwa sposoby wykonania transakcji:  
  
-   Wywołaj [CommitTrans](#committrans) funkcję elementu członkowskiego, aby zatwierdzić transakcji, a następnie zapisz zmiany w źródle danych.  
  
-   Lub zadzwoń [wycofywania](#rollback) funkcja elementu członkowskiego, aby anulować transakcji.  
  
 Zamykanie obiekt obszaru roboczego lub obiektu bazy danych, gdy transakcja jest w stanie oczekiwania wycofuje wszystkie oczekujące transakcje.  
  
 Jeśli potrzebujesz do izolowania transakcji w jednym źródle danych ODBC od tych w innym źródle danych ODBC, zobacz [SetIsolateODBCTrans](#setisolateodbctrans) funkcja elementu członkowskiego.  
  
##  <a name="cdaoworkspace"></a>  CDaoWorkspace::CDaoWorkspace  
 Konstruuje `CDaoWorkspace` obiektu.  
  
```  
CDaoWorkspace();
```  
  
### <a name="remarks"></a>Uwagi  
 Po konstruowanie obiektu języka C++, masz dwie opcje:  
  
-   Wywołanie obiektu [Otwórz](#open) funkcja elementu członkowskiego, Otwórz obszar roboczy domyślne lub Otwórz istniejący obiekt w kolekcji obszarów roboczych.  
  
-   Lub zadzwoń do obiektu [Utwórz](#create) funkcji elementu członkowskiego, aby utworzyć nowy obiekt DAO obszaru roboczego. To jawnie uruchamia nową sesję obszar roboczy, którego może dotyczyć za pośrednictwem `CDaoWorkspace` obiektu. Po wywołaniu `Create`, można wywołać [Append](#append) Jeśli chcesz dodać obszaru roboczego do kolekcji obszarów roboczych z aparatem bazy danych.  
  
 Zobacz Omówienie klasy [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) informacji o podczas należy jawnie utworzyć `CDaoWorkspace` obiektu. Zazwyczaj używasz obszary robocze utworzone niejawnie po otwarciu [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) obiektu bez określenia obszaru roboczego lub po otwarciu [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obiektu bez określania obiektu bazy danych. Obiekty MFC DAO utworzone w ten sposób użyć DAO firmy domyślnego obszaru roboczego, który jest utworzona jeden raz i ponownie.  
  
 Aby zwolnić obszar roboczy i zawartych w nim obiektów, należy wywołać obiekt workspace [Zamknij](#close) funkcja elementu członkowskiego.  
  
##  <a name="close"></a>  CDaoWorkspace::Close  
 Wywołaj tę funkcję elementu członkowskiego, aby zamknąć obiekt obszaru roboczego.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Uwagi  
 Zamknięcie obiektu Otwórz obszar roboczy zwalnia obiekt DAO i, jeśli obszar roboczy jest elementem członkowskim kolekcji obszarów roboczych spowoduje usunięcie go z kolekcji. Wywoływanie `Close` jest dobrą praktyką programowania.  
  
> [!CAUTION]
>  Zamykanie obiekt workspace zamyka wszystkie otwarte bazy danych w obszarze roboczym. Skutkuje to wszelkie open zestawów rekordów w bazach danych, również zamknięte, a wszystkie oczekujące zmiany lub aktualizacje zostaną wycofane. Aby uzyskać powiązane informacje, zobacz [CDaoDatabase::Close](../../mfc/reference/cdaodatabase-class.md#close), [CDaoRecordset::Close](../../mfc/reference/cdaorecordset-class.md#close), [CDaoTableDef::Close](../../mfc/reference/cdaotabledef-class.md#close), i [CDaoQueryDef::Close](../../mfc/reference/cdaoquerydef-class.md#close) funkcji elementów członkowskich.  
  
 Obszar roboczy obiekty nie są trwałe; istnieją one tylko wtedy, gdy istnieją odwołania do nich. Oznacza to, że po zakończeniu sesji aparatu bazy danych obszaru roboczego i jego baz danych kolekcji nie są zachowywane. Należy je ponownie utworzyć dla następnej sesji, otwierając obszar roboczy i bazy danych ponownie.  
  
 Aby uzyskać powiązane informacje zobacz temat "Metody Close" w Pomocy programu DAO.  
  
##  <a name="committrans"></a>  CDaoWorkspace::CommitTrans  
 Wywołaj tę funkcję elementu członkowskiego, można zatwierdzić transakcji — Zapisywanie grupy zmian i aktualizacji dla jednego lub więcej baz danych w obszarze roboczym.  
  
```  
void CommitTrans();
```  
  
### <a name="remarks"></a>Uwagi  
 Transakcji zawiera serię zmian do bazy danych lub jego struktury, począwszy od wywołania [BeginTrans](#begintrans). Po ukończeniu transakcji albo Zatwierdź lub Wycofaj je z powrotem (Anuluj zmiany) za pomocą [wycofywania](#rollback). Domyślnie, bez transakcji aktualizacje rekordów są zatwierdzone natychmiast. Wywoływanie `BeginTrans` powoduje, że zaangażowanie aktualizacje opóźnione, dopóki nie zostanie wywołana `CommitTrans`.  
  
> [!CAUTION]
>  W ramach jednego obszaru roboczego transakcje są zawsze globalne do obszaru roboczego i nie są ograniczone do tylko jednej bazy danych lub zestawu rekordów. W przypadku wykonywania operacji na więcej niż jedną bazę danych lub zestaw rekordów w obrębie transakcji obszaru roboczego `CommitTrans` zatwierdzeń wszystkie oczekujące aktualizacje, i `Rollback` przywraca wszystkie operacje na tych baz danych i zestawy rekordów.  
  
 Podczas zamykania bazy danych lub obszar roboczy z oczekujące transakcje, wszystkie wycofywania transakcji.  
  
> [!NOTE]
>  Nie jest to mechanizm dwufazowego zatwierdzania. W przypadku niepowodzenia jednej aktualizacji do zatwierdzenia, inne nadal będą zatwierdzenia.  
  
##  <a name="compactdatabase"></a>  CDaoWorkspace::CompactDatabase  
 Wywołaj tę funkcję elementu członkowskiego do kompaktowania określonego Microsoft Jet (. Baza danych MDB).  
  
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
 *lpszSrcName*  
 Nazwa istniejącej zamknięte bazy danych. Może być pełną ścieżkę i nazwę pliku, taką jak "C:\\\MYDB. MDB". Jeśli nazwa pliku ma rozszerzenie, należy określić go. Jeśli sieć obsługuje jednolitego konwencji nazewnictwa (UNC), można również określić ścieżkę sieciową, taką jak "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB". (Ułamkowe odwrócone są wymagane w ciągach ścieżki, ponieważ "\\" jest znakiem ucieczki C++.)  
  
 *lpszDestName*  
 Pełna ścieżka skompaktowany bazy danych, który tworzysz. Można również określić ścieżkę sieciową jako za pomocą *lpszSrcName*. Nie można użyć *lpszDestName* argumentu, aby określić ten sam plik bazy danych jako *lpszSrcName*.  
  
 *lpszPassword*  
 Hasło używane, gdy chcesz kompaktowanie bazy danych chronionej hasłem. Należy pamiętać, że jeśli używasz wersji `CompactDatabase` przyjmującej hasła, należy podać wszystkie parametry. Ponadto, ponieważ jest to parametr connect, wymaga specjalne formatowanie, w następujący sposób:; PWD = *lpszPassword*. Na przykład:; PWD = "Szczęśliwego". (Wymagane jest wiodącym średnikami).  
  
 *lpszLocale*  
 Wyrażenie ciągu używany do określenia kolejności sortowania do utworzenia *lpszDestName*. Jeśli ten argument zostanie pominięty, akceptując wartości domyślne dla `dbLangGeneral` (patrz poniżej), ustawienia regionalne nowej bazy danych jest taka sama jak w przypadku starej bazy danych. Możliwe wartości to:  
  
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
  
 *nOptions*  
 Określa jedną lub więcej opcji dla docelowej bazy danych, *lpszDestName*. Jeśli ten argument zostanie pominięty, akceptując wartości domyślne, *lpszDestName* będzie miał ten sam szyfrowania i tej samej wersji co *lpszSrcName*. Można połączyć `dbEncrypt` lub `dbDecrypt` opcji z jedną z opcji wersji za pomocą operatora bitowego OR. Możliwe wartości, które określają format bazy danych, a nie wersja aparatu bazy danych, to:  
  
- `dbEncrypt` Szyfrowanie bazy danych podczas kompaktowania.  
  
- `dbDecrypt` Odszyfrowywanie bazy danych podczas kompaktowania.  
  
- `dbVersion10` Utwórz bazę danych, która używa aparatu bazy danych Microsoft Jet w wersji 1.0, podczas kompaktowania.  
  
- `dbVersion11` Utwórz bazę danych, która używa aparatu bazy danych Microsoft Jet w wersji 1.1 podczas kompaktowania.  
  
- `dbVersion20` Utwórz bazę danych, która używa aparatu bazy danych Microsoft Jet w wersji 2.0 podczas kompaktowania.  
  
- `dbVersion30` Utwórz bazę danych, która używa aparatu bazy danych Microsoft Jet w wersji 3.0 podczas kompaktowania.  
  
 Możesz użyć `dbEncrypt` lub `dbDecrypt` w argumencie Opcje, aby określić, czy można zaszyfrować lub odszyfrować bazy danych, ponieważ ona jest kompaktowana. Jeśli pominiesz stałą szyfrowania lub zawiera zarówno `dbDecrypt` i `dbEncrypt`, *lpszDestName* będzie miał ten sam szyfrowanie jako *lpszSrcName*. Można użyć jednej ze stałych wersji w argumencie Opcje do określenia wersji danych format skompaktowany bazy danych. Stała ta dotyczy tylko wersję formatu danych *lpszDestName*. Można określić tylko jedną wersję stałą. Jeżeli pominięto stałą wersji *lpszDestName* będzie mieć tej samej wersji co *lpszSrcName*. Można skompaktować *lpszDestName* tylko do wersji, która jest taka sama lub nowsza niż *lpszSrcName*.  
  
> [!CAUTION]
>  Jeśli bazy danych nie jest zaszyfrowany, jest to możliwe, nawet w przypadku zaimplementowania bezpieczeństwa użytkownika i hasło, bezpośrednio odczytywać plik binarny dysku, który stanowi bazy danych.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku zmiany danych w bazie danych, plik bazy danych może ulec fragmentacji i używać więcej miejsca na dysku, niż jest to konieczne. Okresowo należy je bazy danych do defragmentowania pliku bazy danych. Skompaktowany bazy danych jest zwykle mniejsze. Możesz również zmienić kolejność sortowania, szyfrowanie lub wersję formatu danych, gdy kopiowanie i kompaktowanie bazy danych.  
  
> [!CAUTION]
>  `CompactDatabase` Funkcji składowej nie poprawnie przekonwertuje pełnej bazy danych Microsoft Access z jednej wersji do innego. Jest konwertowany tylko format danych. Microsoft dostęp zdefiniowany obiektów, takich jak formularze i raporty, nie są przekształcane. Dane są poprawnie przekonwertować.  
  
> [!TIP]
>  Można również użyć `CompactDatabase` można skopiować plik bazy danych.  
  
 Aby uzyskać więcej informacji na temat kompaktowania baz danych zobacz temat "CompactDatabase metody" w Pomocy programu DAO.  
  
##  <a name="create"></a>  CDaoWorkspace::Create  
 Wywołaj tę funkcję elementu członkowskiego, aby utworzyć nowy obiekt DAO obszaru roboczego i skojarzyć go z MFC `CDaoWorkspace` obiektu.  
  
```  
virtual void Create(
    LPCTSTR lpszName,  
    LPCTSTR lpszUserName,  
    LPCTSTR lpszPassword);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszName*  
 Ciąg z maksymalnie 14 znaków, który unikatowo nazwy nowego obiektu w obszarze roboczym. Musisz podać nazwę. Aby uzyskać powiązane informacje zobacz temat "Nazwa właściwości" w Pomocy programu DAO.  
  
 *lpszUserName*  
 Nazwa użytkownika właściciela obszaru roboczego. Aby poznać wymagania, zobacz *lpszDefaultUser* parametru, aby [SetDefaultUser](#setdefaultuser) funkcja elementu członkowskiego. Aby uzyskać powiązane informacje zobacz temat "Właściwości nazwy użytkownika" w Pomocy programu DAO.  
  
 *lpszPassword*  
 Hasło dla nowego obiektu w obszarze roboczym. Hasło może zawierać maksymalnie 14 znaków i może zawierać dowolny znak z wyjątkiem ASCII od 0 (null). Hasła jest rozróżniana wielkość liter. Aby uzyskać powiązane informacje zobacz temat "Property hasło" w Pomocy programu DAO.  
  
### <a name="remarks"></a>Uwagi  
 Ogólny proces tworzenia jest:  
  
1.  Konstruowania [CDaoWorkspace](#cdaoworkspace) obiektu.  
  
2.  Wywołanie obiektu `Create` funkcja elementu członkowskiego, aby utworzyć podstawowy obszar roboczy DAO. Należy określić nazwę obszaru roboczego.  
  
3.  Opcjonalnie wywołać [Append](#append) Jeśli chcesz dodać obszaru roboczego do kolekcji obszarów roboczych z aparatem bazy danych. Możesz pracować z obszarem roboczym, bez dołączenie jej.  
  
 Po `Create` wywołanie, obiekt obszar roboczy jest w stanie otwarcia, gotowy do użycia. Nie wywołuj `Open` po `Create`. Nie wywołuj `Create` Jeśli obszar roboczy już istnieje w kolekcji obszarów roboczych. `Create` Inicjuje aparat bazy danych, jeśli go nie został zainicjowany dla swojej aplikacji.  
  
##  <a name="getdatabasecount"></a>  CDaoWorkspace::GetDatabaseCount  
 Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę obiektów bazy danych DAO kolekcji baz danych obszaru roboczego — liczba otwartych baz danych w obszarze roboczym.  
  
```  
short GetDatabaseCount();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba otwartych baz danych w obszarze roboczym.  
  
### <a name="remarks"></a>Uwagi  
 `GetDatabaseCount` jest przydatne, jeśli potrzebujesz pętli wszystkich zdefiniowanych baz danych w kolekcji baz danych obszaru roboczego. Aby uzyskać informacje dotyczące danego bazy danych w kolekcji, zobacz [GetDatabaseInfo](#getdatabaseinfo). Zwykle jest używane do wywoływania `GetDatabaseCount` dla liczby baz danych, Otwórz, następnie użyć tego numeru jako indeks pętli wielokrotnego wywołania `GetDatabaseInfo`.  
  
##  <a name="getdatabaseinfo"></a>  CDaoWorkspace::GetDatabaseInfo  
 Wywołaj tę funkcję elementu członkowskiego, aby uzyskać różne rodzaje informacji na temat bazy danych, jeśli jest on otwarty w obszarze roboczym.  
  
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
 *nIndex*  
 Liczony od zera indeks obiektu bazy danych w kolekcji baz danych obszaru roboczego do wyszukiwania według indeksu.  
  
 *dbinfo*  
 Odwołanie do [cdaodatabaseinfo —](../../mfc/reference/cdaodatabaseinfo-structure.md) obiektów, które zwraca żądane informacje.  
  
 *dwInfoOptions*  
 Opcje, które określają, które informacje o bazie danych do pobrania. Dostępne opcje są wymienione w tym miejscu oraz co mogą spowodować, że funkcja zwróci:  
  
- Nazwa AFX_DAO_PRIMARY_INFO (ustawienie domyślne), można zaktualizować, transakcji  
  
- AFX_DAO_SECONDARY_INFO głównej informacje oraz: limit czasu zapytania wersji, w przypadku kolejność sortowania  
  
- AFX_DAO_ALL_INFO głównych i dodatkowych informacji plus: łączenie  
  
 *lpszName*  
 Nazwa obiektu bazy danych do wyszukiwania według nazwy. Nazwa jest ciągiem z maksymalnie 14 znaków, który jednoznacznie nazwy nowego obiektu w obszarze roboczym.  
  
### <a name="remarks"></a>Uwagi  
 Jednej wersji funkcji pozwala wyszukiwać bazy danych za pomocą indeksu. Druga wersja służy do wyszukiwania według nazwy bazy danych.  
  
 Aby uzyskać opis informacje zwracane w *dbinfo*, zobacz [cdaodatabaseinfo —](../../mfc/reference/cdaodatabaseinfo-structure.md) struktury. Ta struktura zawiera elementy członkowskie, które odnoszą się do elementów wymienionych powyżej w opisie informacji *dwInfoOptions*. W przypadku żądania informacji o jeden poziom, otrzymasz informacje dotyczące wszelkich poprzednich poziomach.  
  
##  <a name="getinipath"></a>  CDaoWorkspace::GetIniPath  
 Wywołaj tę funkcję elementu członkowskiego, aby uzyskać lokalizację bazy danych Microsoft Jet aparatu inicjowania ustawień w rejestrze systemu Windows.  
  
```  
static CString PASCAL GetIniPath();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierający lokalizacja w rejestrze.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać informacje dotyczące ustawień dla aparatu bazy danych, można użyć lokalizacji. Zwracane informacje dotyczą jest faktycznie nazwa podklucza rejestru.  
  
 Aby uzyskać powiązane informacje zobacz tematy "IniPath właściwość" i "Dostosowywanie Windows rejestru ustawień do Data Access" w Pomocy programu DAO.  
  
##  <a name="getisolateodbctrans"></a>  CDaoWorkspace::GetIsolateODBCTrans  
 Wywołaj tę funkcję elementu członkowskiego, aby uzyskać bieżącą wartość właściwości DAO IsolateODBCTrans dla obszaru roboczego.  
  
```  
BOOL GetIsolateODBCTrans();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli ODBC — transakcje są izolowane; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 W niektórych sytuacjach konieczne może mieć wielu jednoczesnych transakcji oczekujących na tej samej bazy danych ODBC. Aby to zrobić, należy otworzyć oddzielny obszar roboczy dla każdej transakcji. Należy pamiętać, że mimo że każdy obszar roboczy może mieć własną ODBC połączenia z bazą danych, to spowalnia wydajność systemu. Ponieważ izolacji transakcji nie jest zazwyczaj wymagane, połączenia ODBC z wielu obiektów obszaru roboczego otwierane przez tego samego użytkownika są udostępnione domyślnie.  
  
 Niektóre serwery ODBC, takich jak Microsoft SQL Server, nie zezwalają na jednoczesnych transakcji na pojedyncze połączenie. Jeśli potrzebujesz więcej niż jednej transakcji w czasie oczekiwania względem bazy danych, ustaw właściwość IsolateODBCTrans wartość TRUE w każdym obszarze roboczym zaraz po jego otwarciu. Wymusza w osobnym połączeniu ODBC dla każdego obszaru roboczego.  
  
 Aby uzyskać powiązane informacje zobacz temat "IsolateODBCTrans Property" w Pomocy programu DAO.  
  
##  <a name="getlogintimeout"></a>  CDaoWorkspace::GetLoginTimeout  
 Wywołaj tę funkcję elementu członkowskiego, aby uzyskać bieżącą wartość właściwości DAO LoginTimeout dla obszaru roboczego.  
  
```  
static short PASCAL GetLoginTimeout();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba sekund, zanim wystąpi błąd podczas próby logowania do bazy danych ODBC.  
  
### <a name="remarks"></a>Uwagi  
 Ta wartość reprezentuje liczbę sekund, zanim wystąpi błąd podczas próby logowania do bazy danych ODBC. Domyślne ustawienie LoginTimeout to 20 sekund. Gdy LoginTimeout jest równa 0, nie przekroczony limit czasu i komunikację ze źródłem danych może przestać odpowiadać.  
  
 Próbujesz zalogować się do bazy danych ODBC, takich jak Microsoft SQL Server, połączenie może zakończyć się niepowodzeniem w wyniku błędy sieciowe lub ponieważ serwer nie jest uruchomiona. Bez czekania domyślnie 20 sekund do połączenia, można określić, jak długo silnik bazy danych przed oczekuje generuje błąd. Logowanie do serwera odbywa się niejawnie jako część szereg różnych zdarzeniami, na przykład uruchomienie kwerendy w bazie danych serwera zewnętrznego.  
  
 Aby uzyskać powiązane informacje zobacz temat "LoginTimeout Property" w Pomocy programu DAO.  
  
##  <a name="getname"></a>  CDaoWorkspace::GetName  
 Wywołaj tę funkcję elementu członkowskiego, aby uzyskać nazwę użytkownika DAO obszar roboczy obiektu bazowego `CDaoWorkspace` obiektu.  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierający nazwę użytkownika obiektu DAO obszaru roboczego.  
  
### <a name="remarks"></a>Uwagi  
 Nazwa jest przydatne w przypadku uzyskiwania dostępu do obiektu DAO obszaru roboczego w kolekcji obszarów roboczych z aparatem bazy danych według nazwy.  
  
 Aby uzyskać powiązane informacje zobacz temat "Nazwa właściwości" w Pomocy programu DAO.  
  
##  <a name="getusername"></a>  CDaoWorkspace::GetUserName  
 Wywołaj tę funkcję elementu członkowskiego, aby uzyskać nazwę właściciela obszaru roboczego.  
  
```  
CString GetUserName();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) reprezentujący właściciela obiektu obszaru roboczego.  
  
### <a name="remarks"></a>Uwagi  
 Do pobierania lub ustawiania uprawnień dla właściciela obszaru roboczego, wywoływanie obiektów DAO bezpośrednio, aby sprawdzić uprawnienia ustawienie właściwości; Określa, jakie uprawnienia tego użytkownika. Aby pracować z uprawnieniami, potrzebny jest SYSTEM. Plik MDA.  
  
 Aby uzyskać informacje o wywołującym DAO bezpośrednio, zobacz [techniczne 54 Uwaga](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md). Aby uzyskać powiązane informacje zobacz temat "Właściwości nazwy użytkownika" w Pomocy programu DAO.  
  
##  <a name="getversion"></a>  CDaoWorkspace::GetVersion  
 Wywołaj tę funkcję elementu członkowskiego, można określić wersji aparatu bazy danych Microsoft Jet w użyciu.  
  
```  
static CString PASCAL GetVersion();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) który wskazuje wersję aparatu bazy danych skojarzony z obiektem.  
  
### <a name="remarks"></a>Uwagi  
 Wartość zwracana reprezentuje numer wersji w postaci "major.minor"; na przykład "3.0". Numer wersji produktu (na przykład 3.0) składa się z numerem wersji (3), okres i numer wersji (0).  
  
 Aby uzyskać powiązane informacje zobacz temat "Właściwość Version" w Pomocy programu DAO.  
  
##  <a name="getworkspacecount"></a>  CDaoWorkspace::GetWorkspaceCount  
 Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę obiektów obszaru roboczego DAO w kolekcji obszarów roboczych z aparatem bazy danych.  
  
```  
short GetWorkspaceCount();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba otwartych obszarów roboczych w kolekcji obszarów roboczych.  
  
### <a name="remarks"></a>Uwagi  
 Ta liczba nie obejmuje żadnych otwartych obszarów roboczych nie są dołączane do kolekcji. `GetWorkspaceCount` jest przydatne, jeśli potrzebujesz pętli wszystkich określonych obszarów roboczych w kolekcji obszarów roboczych. Aby uzyskać informacje dotyczące danego obszaru roboczego w kolekcji, zobacz [GetWorkspaceInfo](#getworkspaceinfo). Zwykle jest używane do wywoływania `GetWorkspaceCount` liczbę otwartych obszarów roboczych, następnie użyć tego numeru jako indeks pętli wielokrotnego wywołania `GetWorkspaceInfo`.  
  
##  <a name="getworkspaceinfo"></a>  CDaoWorkspace::GetWorkspaceInfo  
 Wywołaj tę funkcję elementu członkowskiego, aby uzyskać różne rodzaje informacji na temat Otwórz obszar roboczy w sesji.  
  
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
 *nIndex*  
 Liczony od zera indeks obiektu bazy danych w kolekcji obszarów roboczych do wyszukiwania według indeksu.  
  
 *wkspcinfo*  
 Odwołanie do [cdaoworkspaceinfo —](../../mfc/reference/cdaoworkspaceinfo-structure.md) obiektów, które zwraca żądane informacje.  
  
 *dwInfoOptions*  
 Opcje, które określają, które informacje na temat obszaru roboczego do pobrania. Dostępne opcje są wymienione w tym miejscu oraz co mogą spowodować, że funkcja zwróci:  
  
- Nazwa AFX_DAO_PRIMARY_INFO (ustawienie domyślne)  
  
- AFX_DAO_SECONDARY_INFO głównej informacje oraz: nazwa użytkownika  
  
- AFX_DAO_ALL_INFO głównych i dodatkowych informacji plus: izolowania ODBCTrans  
  
 *lpszName*  
 Nazwa obiektu obszaru roboczego do wyszukiwania według nazwy. Nazwa jest ciągiem z maksymalnie 14 znaków, który jednoznacznie nazwy nowego obiektu w obszarze roboczym.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać opis informacje zwracane w *wkspcinfo*, zobacz [cdaoworkspaceinfo —](../../mfc/reference/cdaoworkspaceinfo-structure.md) struktury. Ta struktura zawiera elementy członkowskie, które odnoszą się do elementów wymienionych powyżej w opisie informacji *dwInfoOptions*. W przypadku żądania informacji o jeden poziom, otrzymasz informacje o poprzednich poziomach także.  
  
##  <a name="idle"></a>  CDaoWorkspace::Idle  
 Wywołaj `Idle` aby zapewnić możliwość wykonywania zadań w tle, które mogą nie być aktualne z powodu intensywnego przetwarzania danych aparatu bazy danych.  
  
```  
static void PASCAL Idle(int nAction = dbFreeLocks);
```  
  
### <a name="parameters"></a>Parametry  
 *nAkcja została*  
 Akcję do wykonania podczas przetwarzania w stanie bezczynności. Obecnie jest jedyną prawidłową akcję `dbFreeLocks`.  
  
### <a name="remarks"></a>Uwagi  
 Często jest to istotne w wielodostępnym, wielozadaniowość środowiskach, w których nie ma wystarczająco dużo czasu przetwarzania tła, aby zapewnić aktualność wszystkie rekordy w zestawie rekordów.  
  
> [!NOTE]
>  Wywoływanie `Idle` nie jest konieczne przy użyciu bazy danych utworzone w wersji 3.0 aparatu bazy danych Microsoft Jet. Użyj `Idle` tylko dla baz danych utworzonych w starszych wersjach.  
  
 Zwykle przeczytaj blokady są usuwane i danymi w obiektach rekordów lokalnego dynamicznego jest aktualizowana tylko wtedy, gdy występują żadnych innych akcji (w tym ruchów myszy). Jeśli wywołasz okresowo `Idle`, należy podać, aparat bazy danych przy użyciu czasu nadrób zaległości w tle zadania przetwarzania zwalniając niepotrzebne odczytywania blokad. Określanie `dbFreeLocks` stałej jako argumentu opóźnia, przetwarzanie, dopóki nie zostaną zwolnione wszystkie blokady odczytu.  
  
 Ta funkcja elementu członkowskiego nie jest potrzebna w środowiskach pojedynczego użytkownika, chyba że są uruchomione wiele wystąpień aplikacji. `Idle` Funkcji składowej może zwiększyć wydajność w środowisku wielodostępnym, ponieważ wymusza aparatu bazy danych, do opróżniania danych na dysku, zwalniania blokady w pamięci. Można również zwolnić blokady odczytu, dzięki czemu operacje częścią transakcji.  
  
 Aby uzyskać powiązane informacje zobacz temat "Bezczynności metody" w Pomocy programu DAO.  
  
##  <a name="isopen"></a>  CDaoWorkspace::IsOpen  
 Wywołanie tej funkcji elementu członkowskiego, aby określić, czy `CDaoWorkspace` obiekt jest otwarty — oznacza to, czy obiekt MFC została zainicjowana przez wywołanie [Otwórz](#open) lub wywołanie [Utwórz](#create).  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli obiekt obszaru roboczego jest otwarte w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Możesz wywołać dowolny element członkowski funkcje obszaru roboczego, który jest w stanie otwartym.  
  
##  <a name="m_pdaoworkspace"></a>  CDaoWorkspace::m_pDAOWorkspace  
 Wskaźnik do bazowego obiektu DAO w obszarze roboczym.  
  
### <a name="remarks"></a>Uwagi  
 Ten element członkowski danych należy użyć, jeśli potrzebujesz bezpośredni dostęp do bazowego obiektu DAO. Możesz wywołać obiekt DAO interfejsy, za pomocą tego wskaźnika.  
  
 Aby uzyskać informacje na temat uzyskiwania dostępu do obiektów DAO bezpośrednio, zobacz [techniczne 54 Uwaga](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).  
  
##  <a name="open"></a>  CDaoWorkspace::Open  
 Jawnie zostanie otwarty obiekt obszar roboczy, skojarzone z jego DAO domyślnego obszaru roboczego.  
  
```  
virtual void Open(LPCTSTR lpszName = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszName*  
 Nazwa obiekt DAO obszar roboczy, aby otworzyć — ciąg z maksymalnie 14 znaków, który unikatowo nazwy obszaru roboczego. Zaakceptuj wartość domyślną wartość NULL, aby otworzyć jawnie domyślnego obszaru roboczego. Aby uzyskać wymagania nazewnictwa, zobacz *lpszName* parametr [Utwórz](#create). Aby uzyskać powiązane informacje zobacz temat "Nazwa właściwości" w Pomocy programu DAO.  
  
### <a name="remarks"></a>Uwagi  
 Po konstruowanie `CDaoWorkspace` obiektu, wywołaj tę funkcję elementu członkowskiego, wykonaj jedną z następujących czynności:  
  
-   Jawnie Otwórz domyślnego obszaru roboczego. Przekaż wartość NULL *lpszName*.  
  
-   Otwórz istniejący `CDaoWorkspace` obiektu, jest członkiem kolekcji obszarów roboczych według nazwy. Przekaż prawidłową nazwę istniejącego obiektu obszaru roboczego.  
  
 `Open` polega na spakowaniu obiekt obszaru roboczego do stanu rozwartego, a także inicjuje aparat bazy danych, jeśli go nie został zainicjowany dla aplikacji.  
  
 Chociaż wiele `CDaoWorkspace` element członkowski funkcji można go wywołać jedynie po otwarciu obszaru roboczego, następujące funkcje elementów członkowskich, które działają na aparacie bazy danych, są dostępne po konstrukcji obiektu języka C++, ale przed wywołaniem do `Open`:  
  
||||  
|-|-|-|  
|[Utwórz](#create)|[GetVersion](#getversion)|[SetDefaultUser](#setdefaultuser)|  
|[GetIniPath](#getinipath)|[Bezczynności (%)](#idle)|[SetIniPath](#setinipath)|  
|[GetLoginTimeout](#getlogintimeout)|[SetDefaultPassword](#setdefaultpassword)|[SetLoginTimeout](#setlogintimeout)|  
  
##  <a name="repairdatabase"></a>  CDaoWorkspace::RepairDatabase  
 Wywołaj tę funkcję elementu członkowskiego, jeśli chcesz podjąć próbę naprawy uszkodzenia bazy danych, który uzyskuje dostęp do aparatu bazy danych Microsoft Jet.  
  
```  
static void PASCAL RepairDatabase(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszName*  
 Ścieżka i nazwa pliku dla istniejącego pliku bazy danych aparatu Microsoft Jet. Jeżeli pominięto ścieżkę, przeszukiwany jest bieżący katalog. Jeśli system obsługuje jednolitego konwencji nazewnictwa (UNC), można również określić ścieżkę sieciową, takie jak: "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB". (Ułamkowe odwrócone są wymagane w ciąg ścieżki, ponieważ "\\" jest znakiem ucieczki C++.)  
  
### <a name="remarks"></a>Uwagi  
 Należy zamknąć bazy danych, określonego przez *lpszName* przed go naprawić. W środowisku wielodostępnym, inni użytkownicy nie mogą mieć *lpszName* otworzyć, gdy są naprawy go. Jeśli *lpszName* nie jest zamknięty lub nie jest dostępny do wyłącznego użytku, wystąpi błąd.  
  
 Ta funkcja elementu członkowskiego próbuje naprawić bazę danych, która została oznaczona jako jest prawdopodobnie uszkodzony przez operację zapisu niekompletne. Może to wystąpić, jeśli w aplikacji przy użyciu aparatu bazy danych Microsoft Jet jest został nieoczekiwanie zamknięty z powodu problemu sprzętu komputera lub awaria zasilania. Jeśli wykonujesz operację i wywołanie [Zamknij](../../mfc/reference/cdaodatabase-class.md#close) funkcja elementu członkowskiego lub Wyjdź z aplikacji w zwykły sposób, baza danych nie zostanie oznaczona jako jest prawdopodobnie uszkodzony.  
  
> [!NOTE]
>  Po naprawie bazę danych, jest również dobrym pomysłem jest compact go za pomocą [CompactDatabase](#compactdatabase) funkcja elementu członkowskiego defragmentacji pliku, jak i do odzyskiwania miejsca na dysku.  
  
 Aby uzyskać więcej informacji na temat naprawiania bazy danych zobacz temat "RepairDatabase metody" w Pomocy programu DAO.  
  
##  <a name="rollback"></a>  CDaoWorkspace::Rollback  
 Wywołaj tę funkcję elementu członkowskiego, aby zakończyć bieżącej transakcji i przywrócić wszystkie bazy danych w obszarze roboczym do ich warunek, zanim transakcja została rozpoczęta.  
  
```  
void Rollback();
```  
  
### <a name="remarks"></a>Uwagi  
  
> [!CAUTION]
>  W jeden obiekt obszaru roboczego transakcje są zawsze globalne do obszaru roboczego i nie są ograniczone do tylko jednej bazy danych lub zestawu rekordów. W przypadku wykonywania operacji na więcej niż jedną bazę danych lub zestaw rekordów w obrębie transakcji obszaru roboczego `Rollback` przywraca wszystkie operacje na wszystkich tych baz danych i zestawy rekordów.  
  
 Jeśli obiekt obszar roboczy zostanie zamknięty bez zapisywania ani wycofywanie wszystkie oczekujące transakcje, transakcje są automatycznie przywracane. Jeśli wywołasz [CommitTrans](#committrans) lub `Rollback` bez wywoływania pierwszy [BeginTrans](#begintrans), wystąpi błąd.  
  
> [!NOTE]
>  Po rozpoczęciu transakcji aparatu bazy danych rejestruje jej operacje w pliku przechowywane w katalogu określonym przez zmienną środowiskową TEMP na stacji roboczej. Jeśli plik dziennika transakcji przekroczy dostępny magazyn na dysku tymczasowego, aparat bazy danych spowoduje, że MFC, aby zgłosić `CDaoException` (DAO błąd 2004). Jeśli na tym etapie, należy wywołać `CommitTrans`nieokreśloną liczbę operacji dokłada wszelkich starań, ale pozostałe operacje niewykonanej zostaną utracone i musi zostać uruchomiona ponownie wykonać operację. Wywoływanie `Rollback` zwalnia dziennik transakcji i wycofanie wszystkich operacji w transakcji.  
  
##  <a name="setdefaultpassword"></a>  CDaoWorkspace::SetDefaultPassword  
 Wywołaj tę funkcję elementu członkowskiego, aby ustawić domyślne hasło, która używa aparatu bazy danych, gdy tworzony jest obiekt w obszarze roboczym bez określonego hasła.  
  
```  
static void PASCAL SetDefaultPassword(LPCTSTR lpszPassword);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszPassword*  
 Domyślne hasło. Hasło może zawierać maksymalnie 14 znaków i może zawierać dowolny znak z wyjątkiem ASCII od 0 (null). Hasła jest rozróżniana wielkość liter.  
  
### <a name="remarks"></a>Uwagi  
 Hasło domyślnego, który został ustawiony ma zastosowanie do nowych obszarów roboczych, utworzonych po wywołaniu. Podczas tworzenia kolejnych obszarów roboczych, nie należy określić hasło w [Utwórz](#create) wywołania.  
  
 Aby użyć tej funkcji elementu członkowskiego:  
  
1.  Konstruowania `CDaoWorkspace` obiektu, ale nie należy wywoływać metody `Create`.  
  
2.  Wywołaj `SetDefaultPassword` i, jeśli chcesz [SetDefaultUser](#setdefaultuser).  
  
3.  Wywołaj `Create` dla tego obiektu w obszarze roboczym lub kolejne, nie określając hasła.  
  
 Domyślnie właściwość domyślny ma wartość "admin", a właściwość DefaultPassword jest ustawiona na ciąg pusty ("").  
  
 Aby uzyskać więcej informacji o zabezpieczeniach zobacz temat "Property uprawnień" w Pomocy programu DAO. Aby uzyskać powiązane informacje zobacz tematy "DefaultPassword właściwości" i "domyślny" w Pomocy programu DAO.  
  
##  <a name="setdefaultuser"></a>  CDaoWorkspace::SetDefaultUser  
 Wywołaj tę funkcję elementu członkowskiego, aby ustawić domyślną nazwę użytkownika, która używa aparatu bazy danych, gdy tworzony jest obiekt w obszarze roboczym bez określonej nazwy użytkownika.  
  
```  
static void PASCAL SetDefaultUser(LPCTSTR lpszDefaultUser);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszDefaultUser*  
 Domyślna nazwa użytkownika. Nazwa użytkownika może mieć 1-20 znaków i zawierać znaki alfabetyczne, znaki akcentowane, liczby, spacje i symbole, z wyjątkiem: "(cudzysłów) / (ukośnik), \ (ukośnik odwrotny), \[ \] (nawiasy kwadratowe): (dwukropek), &#124; () potok) \< (mniej — znak), > (większe — znak), + (znak plus), = (równa logowania); (średnik), (przecinkami) (znak zapytania) \* (gwiazdka), wiodące spacje i znaki sterujące (ASCII 00 do ASCII 31). Aby uzyskać powiązane informacje zobacz temat "Właściwości nazwy użytkownika" w Pomocy programu DAO.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna nazwa użytkownika, który został ustawiony ma zastosowanie do nowych obszarów roboczych, utworzonych po wywołaniu. Podczas tworzenia kolejnych obszarów roboczych, nie należy określić nazwę użytkownika w [Utwórz](#create) wywołania.  
  
 Aby użyć tej funkcji elementu członkowskiego:  
  
1.  Konstruowania `CDaoWorkspace` obiektu, ale nie należy wywoływać metody `Create`.  
  
2.  Wywołaj `SetDefaultUser` i, jeśli chcesz [SetDefaultPassword](#setdefaultpassword).  
  
3.  Wywołaj `Create` dla tego obiektu w obszarze roboczym lub kolejne, nie określając nazwę użytkownika.  
  
 Domyślnie właściwość domyślny ma wartość "admin", a właściwość DefaultPassword jest ustawiona na ciąg pusty ("").  
  
 Aby uzyskać powiązane informacje zobacz tematy "Domyślny właściwości" i "DefaultPassword" w Pomocy programu DAO.  
  
##  <a name="setinipath"></a>  CDaoWorkspace::SetIniPath  
 Wywołaj tę funkcję elementu członkowskiego, aby określić lokalizację Windows ustawienia rejestru dla aparatu bazy danych Microsoft Jet.  
  
```  
static void PASCAL SetIniPath(LPCTSTR lpszRegistrySubKey);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszRegistrySubkey*  
 Ciąg zawierający nazwę Windows podklucz rejestru do lokalizacji Ustawienia aparatu bazy danych Microsoft Jet lub parametrów wymaganych do zainstalowania ISAM baz danych.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj `SetIniPath` tylko wtedy, gdy należy określić ustawienia specjalne. Aby uzyskać więcej informacji zobacz temat "IniPath Property" w Pomocy programu DAO.  
  
> [!NOTE]
>  Wywołaj `SetIniPath` podczas instalacji aplikacji, nie po uruchomieniu aplikacji. `SetIniPath` musi zostać wywołana przed otwarciem żadnych obszarów roboczych, baz danych lub zestawów rekordów; w przeciwnym razie MFC zgłasza wyjątek.  
  
 Mechanizm ten umożliwia konfigurowanie aparatu bazy danych przy użyciu ustawień rejestru wprowadzonych przez użytkownika. Zakres tego atrybutu jest ograniczony do aplikacji i nie można zmienić bez ponownego uruchamiania aplikacji.  
  
##  <a name="setisolateodbctrans"></a>  CDaoWorkspace::SetIsolateODBCTrans  
 Wywołaj tę funkcję elementu członkowskiego, aby ustawić wartość właściwości DAO IsolateODBCTrans dla obszaru roboczego.  
  
```  
void SetIsolateODBCTrans(BOOL bIsolateODBCTrans);
```  
  
### <a name="parameters"></a>Parametry  
 *bIsolateODBCTrans*  
 Przekaż wartość TRUE, jeśli chcesz rozpocząć izolowanie ODBC — transakcje. Przekaż wartość FALSE zatrzymać izolowanie ODBC — transakcje.  
  
### <a name="remarks"></a>Uwagi  
 W niektórych sytuacjach konieczne może mieć wielu jednoczesnych transakcji oczekujących na tej samej bazy danych ODBC. Aby to zrobić, należy otworzyć oddzielny obszar roboczy dla każdej transakcji. Mimo że każdy obszar roboczy może mieć własną ODBC połączenia z bazą danych, to zmniejsza wydajność systemu. Ponieważ izolacji transakcji nie jest zazwyczaj wymagane, połączenia ODBC z wielu obiektów obszaru roboczego otwierane przez tego samego użytkownika są udostępnione domyślnie.  
  
 Niektóre serwery ODBC, takich jak Microsoft SQL Server, nie zezwalają na jednoczesnych transakcji na pojedyncze połączenie. Jeśli potrzebujesz więcej niż jednej transakcji w czasie oczekiwania względem bazy danych, ustaw właściwość IsolateODBCTrans wartość TRUE w każdym obszarze roboczym zaraz po jego otwarciu. Wymusza w osobnym połączeniu ODBC dla każdego obszaru roboczego.  
  
##  <a name="setlogintimeout"></a>  CDaoWorkspace::SetLoginTimeout  
 Wywołaj tę funkcję elementu członkowskiego, aby ustawić wartość właściwości DAO LoginTimeout dla obszaru roboczego.  
  
```  
static void PASCAL SetLoginTimeout(short nSeconds);
```  
  
### <a name="parameters"></a>Parametry  
 *nSekund*  
 Liczba sekund, zanim wystąpi błąd podczas próby logowania do bazy danych ODBC.  
  
### <a name="remarks"></a>Uwagi  
 Ta wartość reprezentuje liczbę sekund, zanim wystąpi błąd podczas próby logowania do bazy danych ODBC. Domyślne ustawienie LoginTimeout to 20 sekund. Gdy LoginTimeout jest równa 0, nie przekroczony limit czasu i komunikację ze źródłem danych może przestać odpowiadać.  
  
 Próbujesz zalogować się do bazy danych ODBC, takich jak Microsoft SQL Server, połączenie może zakończyć się niepowodzeniem w wyniku błędy sieciowe lub ponieważ serwer nie jest uruchomiona. Bez czekania domyślnie 20 sekund do połączenia, można określić, jak długo silnik bazy danych przed oczekuje generuje błąd. Logowanie się do serwera odbywa się niejawnie jako część szereg różnych zdarzeniami, na przykład uruchomienie kwerendy w bazie danych serwera zewnętrznego. Wartość limitu czasu jest określana przez bieżące ustawienie właściwości LoginTimeout.  
  
 Aby uzyskać powiązane informacje zobacz temat "LoginTimeout Property" w Pomocy programu DAO.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CObject](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)   
 [Cdaorecordset — klasa](../../mfc/reference/cdaorecordset-class.md)   
 [Klasa CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)   
 [Klasa CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)   
 [Klasa CDaoException](../../mfc/reference/cdaoexception-class.md)
