---
title: 'TN054: wywoływanie obiektów DAO bezpośrednio podczas używania klas MFC DAO'
ms.date: 06/28/2018
f1_keywords:
- vc.mfc.dao
helpviewer_keywords:
- MFC, DAO and
- passwords [MFC], calling DAO
- security [MFC], DAO
- DAO (Data Access Objects), calling directly
- DAO (Data Access Objects), security
- security [MFC]
- TN054
- DAO (Data Access Objects), and MFC
ms.assetid: f7de7d85-8d6c-4426-aa05-2e617c0da957
ms.openlocfilehash: 938381f55b598911b69bb25bf7af576dfdfb2e4f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505745"
---
# <a name="tn054-calling-dao-directly-while-using-mfc-dao-classes"></a>TN054: wywoływanie obiektów DAO bezpośrednio podczas używania klas MFC DAO

> [!NOTE]
> Środowiska Visual C++ i kreatory nie obsługują DAO (mimo że uwzględniono klas DAO i nadal można użyć). Firma Microsoft zaleca się, że używasz [szablony OLE DB](../data/oledb/ole-db-templates.md) lub [ODBC i MFC](../data/odbc/odbc-and-mfc.md) dla nowych projektów. DAO należy używać tylko w zachowaniu istniejących aplikacji.

Korzystając z klas baz danych MFC DAO, mogą wystąpić sytuacje, w których należy użyć DAO bezpośrednio. Zwykle nie będzie to wymagane, ale MFC udostępnił niektóre mechanizmy pomocnika do ułatwienia wprowadzania bezpośrednie wywołania DAO prostego podczas łączenia użycia klas MFC z bezpośrednim wywołaniem DAO. Co DAO bezpośrednie wywołania do metod obiektu zarządzana MFC DAO wymagać tylko kilka wierszy kodu. Jeśli musisz utworzyć i używać obiektów DAO, które są *nie* zarządzane przez MFC, trzeba będzie zrobić trochę więcej pracy, faktycznie wywołując `Release` obiektu. Ta uwaga techniczna wyjaśnia, kiedy warto wywoływanie obiektów DAO bezpośrednio, co pomocników MFC zrobić, aby pomóc Ci i jak używać interfejsów DAO OLE. Na koniec ta notatka zawiera niektóre funkcje przykład przedstawiający wywoływanie obiektów DAO bezpośrednio dla funkcji zabezpieczeń DAO.

## <a name="when-to-make-direct-dao-calls"></a>Kiedy należy wykonywać wywołania bezpośredniego DAO

Najbardziej typowych sytuacjach wykonanie bezpośrednich wywołań DAO występuje, gdy kolekcje muszą być odświeżane lub gdy w przypadku wdrażania funkcji, które nie zostały opakowane przez MFC. Najbardziej znaczących funkcji, nie jest udostępniany przez MFC jest zabezpieczeń. Jeśli chcesz zaimplementować funkcje zabezpieczeń, należy użyć bezpośrednio obiekty DAO użytkowników i grup. Oprócz zabezpieczeń istnieje tylko kilka innych DAO funkcji nie są obsługiwane przez MFC. Obejmują one funkcje replikacji rekordów klonowania i bazy danych, a także kilka najnowsze dodatki do DAO.

## <a name="a-brief-overview-of-dao-and-mfcs-implementation"></a>Krótkie omówienie wdrożenia DAO i MFC

Zawijania MFC DAO sprawia, że DAO łatwiejsze dzięki obsłudze wiele informacji, więc nie trzeba już martwić się o podstawowe czynności. Obejmuje to Inicjalizacja OLE, tworzenie i zarządzanie obiekty DAO (szczególnie obiekty kolekcji), błąd sprawdzania i dostarczanie interfejsu silnie typizowany, prostsze (nie **VARIANT** lub `BSTR` argumenty). Można wykonywać bezpośrednich wywołań DAO i nadal korzystać z tych funkcji. Wszystkie kodu należy wykonać to wywołanie `Release` dla obiektów utworzonych przez DAO bezpośrednie wywołania i *nie* modyfikować wskaźniki interfejsu, które MFC mogą polegać na, wewnętrznego. Na przykład nie należy modyfikować *m_pDAORecordset* członkiem otwartą `CDaoRecordset` obiektu, chyba że rozumiesz *wszystkich* wewnętrznego konsekwencje. Można jednak użyć *m_pDAORecordset* interfejs wywoływanie obiektów DAO bezpośrednio, aby uzyskać kolekcji pól. W tym przypadku *m_pDAORecordset* nie będzie można zmodyfikować elementu członkowskiego. Po prostu trzeba wywoływać `Release` na obiekt kolekcji pól, po zakończeniu pracy z obiektem.

## <a name="description-of-helpers-to-make-dao-calls-easier"></a>Opis pomocników umożliwiają DAO wywołuje łatwiejsze

Pomocnicy podane umożliwiają wywoływanie obiektów DAO łatwiejsze są tego samego wątków, które są używane wewnętrznie w klasach bazy danych DAO MFC. Pomocnicy te są używane do sprawdzania kodów powrotnych, podczas wprowadzania bezpośrednie wywołanie DAO, rejestrowania danych wyjściowych debugowania, sprawdzanie błędów oczekiwanego i zgłaszanie wyjątków odpowiednie, jeśli to konieczne. Istnieją dwa podstawowe funkcje pomocnicze i cztery makra, mapowane na jeden z tych dwóch wątków. Najlepsze wyjaśnienie jest po prostu odczytywać kodu. Zobacz **DAO_CHECK**, **DAO_CHECK_ERROR**, **DAO_CHECK_MEM**, i **DAO_TRACE** w AFXDAO. H, aby zobaczyć makra, a **AfxDaoCheck** i **AfxDaoTrace** w DAOCORE. CPP.

## <a name="using-the-dao-ole-interfaces"></a>Za pomocą DAO interfejsy OLE

Interfejsy OLE dla każdego obiektu w hierarchii obiektów DAO są definiowane w pliku nagłówkowym DBDAOINT. Godz., który znajduje się w katalogu \Program Files\Microsoft 2003\VC7\include programu Visual Studio .NET. Te interfejsy zawierają metody, które umożliwiają wykonywanie operacji w całej hierarchii DAO.

Dla wielu metod w interfejsach DAO, konieczne będzie manipulowania `BSTR` obiektu (prefiks długość ciągu używany w automatyzacji OLE). `BSTR` Obiekt jest zwykle zhermetyzowany wewnątrz **VARIANT** typu danych. Klasy MFC `COleVariant` sama dziedziczy **VARIANT** typu danych. W zależności od tego, czy kompilujesz projekt ANSI lub Unicode, interfejsów DAO zwróci ANSI lub Unicode `BSTR`s. Dwa makra V_BSTR i V_BSTRT, są przydatne do zapewnienia, że interfejs DAO pobiera `BSTR` oczekiwanego typu.

Wyodrębnia V_BSTR *bstrVal* członkiem `COleVariant`. To makro jest zwykle używana, gdy potrzebujesz przekazać zawartość `COleVariant` do metody interfejsu DAO. Poniższy fragment kodu przedstawia, deklaracje i rzeczywistego użycia dla dwóch metod interfejsu DAO DAOUser, wykorzystujące makro V_BSTR:

```cpp
COleVariant varOldName;
COleVariant varNewName(_T("NewUser"), VT_BSTRT);

// Code to assign pUser to a valid value omitted
DAOUser *pUser = NULL;

// These method declarations were taken from DBDAOINT.H
// STDMETHOD(get_Name) (THIS_ BSTR FAR* pbstr) PURE;
// STDMETHOD(put_Name) (THIS_ BSTR bstr) PURE;

DAO_CHECK(pUser->get_Name(&V_BSTR (&varOldName)));
DAO_CHECK(pUser->put_Name(V_BSTR (&varNewName)));
```

Należy pamiętać, że `VT_BSTRT` argumentu określonym w `COleVariant` Konstruktor powyżej gwarantuje, że zawsze będą ANSI `BSTR` w `COleVariant` Jeśli kompilujesz wersję ANSI i Unicode aplikacji `BSTR` wersja Unicode Twoja aplikacja. Jest to, co oczekuje DAO.

Inne makro V_BSTRT, który wyodrębnia ANSI lub Unicode *bstrVal* członkiem `COleVariant` w zależności od typu kompilacji (ANSI lub Unicode). Poniższy kod przedstawia sposób wyodrębniania `BSTR` wartość z `COleVariant` do `CString`:

```cpp
COleVariant varName(_T("MyName"), VT_BSTRT);
CString str = V_BSTRT(&varName);
```

Makra V_BSTRT, wraz z innymi technikami, aby otworzyć inne typy, które są przechowywane w `COleVariant`, przedstawiono w przykładzie DAOVIEW. W szczególności w odbywa się to tłumaczenie `CCrack::strVARIANT` metody. Tej metody, jeśli jest to możliwe, tłumaczy wartość `COleVariant` jako wystąpienia elementu `CString`.

## <a name="simple-example-of-a-direct-call-to-dao"></a>Prosty przykład bezpośrednie wywołanie DAO

Mogą wystąpić sytuacje, gdy jest to konieczne odświeżyć kolekcji obiektów DAO. Zazwyczaj nie powinno to być konieczne, ale jest prostą procedurę, jeśli to konieczne. Przykładem po kolekcji może wymagać odświeżenia jest podczas działania w środowisku wielodostępnym, w których wielu użytkowników, tworzenie nowych tabledefs —. W tym przypadku kolekcji tabledefs — mogą stać się nieaktualne. Aby odświeżyć kolekcji, po prostu musisz wywołać `Refresh` metody obiektu w określonej kolekcji i sprawdzanie dla błędów:

```cpp
DAO_CHECK(pMyDaoDatabase->m_pDAOTableDefs->Refresh());
```

Należy zauważyć, że obecnie wszystkie interfejsy obiektu kolekcji DAO szczegóły implementacji nieudokumentowane klas baz danych MFC DAO.

## <a name="using-dao-directly-for-dao-security-features"></a>Przy użyciu obiektów DAO bezpośrednio dla funkcji zabezpieczeń DAO

Klasy bazy danych MFC DAO DAO funkcji zabezpieczeń nie jest zawijany. Należy wywołać metody interfejsów DAO, aby korzystać z niektórych funkcji zabezpieczeń DAO. Poniższa funkcja ustawia systemowej bazy danych, a następnie zmienia hasło użytkownika. Ta funkcja wywołuje trzy inne funkcje, które następnie są zdefiniowane.

```cpp
void ChangeUserPassword()
{
    // Specify path to the Microsoft Access *// system database
    CString strSystemDB =
        _T("c:\\Program Files\\MSOffice\\access\\System.mdw");

    // Set system database before MFC initilizes DAO
    // NOTE: An MFC module uses only one instance
    // of a DAO database engine object. If you have
    // called a DAO object in your application prior
    // to calling the function below, you must call
    // AfxDaoTerm to destroy the existing database
    // engine object. Otherwise, the database engine
    // object already in use will be reused, and setting
    // a system datbase will have no effect.
    //
    // If you have used a DAO object prior to calling
    // this function it is important that DAO be
    // terminated with AfxDaoTerm since an MFC
    // module only gets one copy of the database engine
    // and that engine will be reused if it hasn't been
    // terminated. In other words, if you do not call
    // AfxDaoTerm and there is currently a database
    // initialized, setting the system database will
    // have no effect.
    SetSystemDB(strSystemDB);

    // User name and password manually added
    // by using Microsoft Access
    CString strUserName = _T("NewUser");
    CString strOldPassword = _T("Password");
    CString strNewPassword = _T("NewPassword");

    // Set default user so that MFC will be able
    // to log in by default using the user name and
    // password from the system database
    SetDefaultUser(strUserName, strOldPassword);

    // Change the password. You should be able to
    // call this function from anywhere in your
    // MFC application
    ChangePassword(strUserName, strOldPassword, strNewPassword);

    // ...
}
```

W następnych czterech przykładach pokazano sposób:

- Ustaw systemowej bazy danych DAO (. Plik MDW).

- Ustaw domyślny użytkownik i hasło.

- Zmień hasło użytkownika.

- Zmień hasło. Pliku MDB.

### <a name="setting-the-system-database"></a>Ustawienie systemowej bazy danych

Poniżej znajduje się funkcja próbki, można ustawić systemowej bazy danych, który będzie używany przez aplikację. Ta funkcja musi zostać wywołana przed wykonaniem innych wywołań DAO.

```cpp
// Set the system database that the
// DAO database engine will use

void SetSystemDB(CString& strSystemMDB)
{
    COleVariant varSystemDB(strSystemMDB, VT_BSTRT);

    // Initialize DAO for MFC
    AfxDaoInit();
    DAODBEngine* pDBEngine = AfxDaoGetEngine();

    ASSERT(pDBEngine != NULL);

    // Call put_SystemDB method to set the *// system database for DAO engine
    DAO_CHECK(pDBEngine->put_SystemDB(varSystemDB.bstrVal));
}
```

### <a name="setting-the-default-user-and-password"></a>Ustawienia domyślne użytkownika i hasło

Aby ustawić domyślny użytkownik i hasło dla systemowej bazy danych, użyj następującej funkcji:

```cpp
void SetDefaultUser(CString& strUserName,
    CString& strPassword)
{
    COleVariant varUserName(strUserName, VT_BSTRT);
    COleVariant varPassword(strPassword, VT_BSTRT);

    DAODBEngine* pDBEngine = AfxDaoGetEngine();
    ASSERT(pDBEngine != NULL);

    // Set default user:
    DAO_CHECK(pDBEngine->put_DefaultUser(varUserName.bstrVal));

    // Set default password:
    DAO_CHECK(pDBEngine->put_DefaultPassword(varPassword.bstrVal));
}
```

### <a name="changing-a-users-password"></a>Zmiana hasła użytkownika

Aby zmienić hasło użytkownika, użyj następującej funkcji:

```cpp
void ChangePassword(CString &strUserName,
    CString &strOldPassword,
    CString &strNewPassword)
{
    // Create (open) a workspace
    CDaoWorkspace wsp;
    CString strWspName = _T("Temp Workspace");

    wsp.Create(strWspName, strUserName, strOldPassword);
    wsp.Append();

    // Determine how many objects there are *// in the Users collection
    short nUserCount;
    short nCurrentUser;
    DAOUser *pUser = NULL;
    DAOUsers *pUsers = NULL;

    // Side-effect is implicit OLE AddRef()
    // on DAOUser object:
    DAO_CHECK(wsp.m_pDAOWorkspace->get_Users(&pUsers));

    // Side-effect is implicit OLE AddRef()
    // on DAOUsers object
    DAO_CHECK(pUsers->getcount(&nUserCount));

    // Traverse through the list of users
    // and change password for the userid
    // used to create/open the workspace
    for(nCurrentUser = 0; nCurrentUser <nUserCount; nCurrentUser++)
    {
        COleVariant varIndex(nCurrentUser, VT_I2);
        COleVariant varName;

        // Retrieve information for user nCurrentUser
        DAO_CHECK(pUsers->get_Item(varIndex, &pUser));

        // Retrieve name for user nCurrentUser
        DAO_CHECK(pUser->get_Name(&V_BSTR(&varName)));

        CString strTemp = V_BSTRT(&varName);

        // If there is a match, change the password
        if (strTemp == strUserName)
        {
            COleVariant varOldPwd(strOldPassword, VT_BSTRT);
            COleVariant varNewPwd(strNewPassword, VT_BSTRT);

            DAO_CHECK(pUser->NewPassword(V_BSTR(&varOldPwd),
                V_BSTR(&varNewPwd)));

            TRACE("\t Password is changed\n");
        }
    }
    // Clean up: decrement the usage count
    // on the OLE objects
    pUser->Release();
    pUsers->Release();
    wsp.Close();
}
```

### <a name="changing-the-password-of-an-mdb-file"></a>Zmiana hasła. Plik MDB

Aby zmienić hasło. MDB plików, należy użyć następujących funkcji:

```cpp
void SetDBPassword(LPCTSTR pDB,
    LPCTSTR pszOldPassword,
    LPCTSTR pszNewPassword)
{
    CDaoDatabase db;
    CString strConnect(_T(";pwd="));

    // the database must be opened as exclusive
    // to set a password
    db.Open(pDB, TRUE, FALSE, strConnect + pszOldPassword);

    COleVariant NewPassword(pszNewPassword, VT_BSTRT),
                OldPassword(pszOldPassword, VT_BSTRT);

    DAO_CHECK(db.m_pDAODatabase->NewPassword(V_BSTR(&OldPassword),
        V_BSTR(&NewPassword)));

    db.Close();
}
```

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
