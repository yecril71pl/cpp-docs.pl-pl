---
title: 'TN054: Bezpośrednie wywoływanie obiektów DAO przy użyciu klas MFC DAO'
ms.date: 09/17/2019
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
ms.openlocfilehash: cef9852f762a64579e11fe4b0d8606bfc9d36709
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095976"
---
# <a name="tn054-calling-dao-directly-while-using-mfc-dao-classes"></a>TN054: Bezpośrednie wywoływanie obiektów DAO przy użyciu klas MFC DAO

> [!NOTE]
> Obiekty DAO są używane z bazami danych programu Access i są obsługiwane za pomocą pakietu Office 2013. 3,6 jest wersją ostateczną i jest uznawana za przestarzałą. Środowisko i C++ kreatory wizualne nie obsługują obiektów DAO (mimo że klasy DAO są dołączone i nadal można ich używać). Firma Microsoft zaleca korzystanie z [szablonów OLE DB](../data/oledb/ole-db-templates.md) lub [ODBC oraz MFC](../data/odbc/odbc-and-mfc.md) dla nowych projektów. Obiektów DAO należy używać tylko w przypadku zarządzania istniejącymi aplikacjami.

W przypadku korzystania z klas baz danych MFC DAO mogą wystąpić sytuacje, w których konieczne jest bezpośrednie używanie DAO. Zwykle nie jest to przypadek, ale MFC udostępnia pewne mechanizmy pomocnika, które ułatwiają bezpośrednie wywoływanie obiektów DAO podczas łączenia użycia klas MFC z bezpośrednim wywołaniem DAO. Bezpośrednie wywołania DAO do metod obiektu DAO zarządzanego przez MFC powinny wymagać tylko kilku wierszy kodu. Jeśli trzeba utworzyć i używać obiektów DAO, które *nie* są zarządzane przez MFC, trzeba będzie wykonać nieco więcej pracy przez faktyczne wywołanie `Release` obiektu. Ta Uwaga techniczna wyjaśnia, kiedy można chcieć bezpośrednio wywołać obiekt DAO, jakie pomocniki MFC mogą Ci pomóc oraz jak używać interfejsów DAO OLE. Na koniec ta Uwaga zawiera kilka przykładowych funkcji, które pokazują, jak wywołać DAO bezpośrednio dla funkcji zabezpieczeń DAO.

## <a name="when-to-make-direct-dao-calls"></a>Kiedy mają być bezpośrednie wywołania DAO

Najczęstsze sytuacje wykonywania bezpośrednich wywołań DAO odbywają się, gdy kolekcje muszą zostać odświeżone lub w przypadku implementowania funkcji nieopakowanych przez MFC. Najbardziej znaczącą funkcją niedostępną przez MFC jest zabezpieczenia. W celu zaimplementowania funkcji zabezpieczeń należy bezpośrednio używać obiektów użytkowników i grup DAO (). Oprócz zabezpieczeń istnieje tylko kilka innych funkcji DAO, które nie są obsługiwane przez MFC. Należą do nich klonowanie rekordów i funkcje replikacji bazy danych, a także kilka późnych uzupełnień do obiektu DAO.

## <a name="a-brief-overview-of-dao-and-mfcs-implementation"></a>Krótkie omówienie implementacji obiektów DAO i MFC

Pakowanie obiektów DAO przy użyciu obiektów DAO ułatwia obsługę wielu szczegółów, dzięki czemu nie trzeba martwić się o niewiele rzeczy. Obejmuje to inicjalizację OLE, tworzenie obiektów DAO i zarządzanie nimi (zwłaszcza obiektów kolekcji), sprawdzanie błędów i dostarczanie silnie określonego typu, prostszy interfejs (bez **wariantów** ani `BSTR` argumentów). Możesz wykonywać bezpośrednie wywołania DAO i nadal korzystać z tych funkcji. Cały kod musi być wywoływany `Release` dla wszystkich obiektów utworzonych przez bezpośrednie wywołania DAO i *nie* modyfikuje żadnego ze wskaźników interfejsu, które mogą opierać się na bibliotece MFC. Na przykład nie należy modyfikować elementu członkowskiego *m_pDAORecordset* otwartego `CDaoRecordset` obiektu, chyba że rozumiesz *wszystkie* konsekwencje wewnętrzne. Można jednak użyć interfejsu *m_pDAORecordset* do wywołania DAO bezpośrednio w celu pobrania kolekcji Fields. W takim przypadku nie można modyfikować elementu członkowskiego *m_pDAORecordset* . Po zakończeniu pracy z obiektem wystarczy wywołać `Release` obiekt kolekcji Fields.

## <a name="description-of-helpers-to-make-dao-calls-easier"></a>Opis pomocników ułatwiających wykonywanie wywołań DAO

Pomocniki zapewniane w celu ułatwienia wywoływania obiektów DAO są tymi samymi pomocnikami, które są używane wewnętrznie w klasach baz danych MFC DAO. Ci pomocnicy są używani do sprawdzania kodów powrotu podczas wykonywania bezpośredniego wywołania DAO, rejestrowania danych wyjściowych debugowania, sprawdzania pod kątem oczekiwanych błędów i zgłaszania odpowiednich wyjątków w razie potrzeby. Istnieją dwie podstawowe funkcje pomocnika i cztery makra, które są mapowane na jeden z tych dwóch pomocników. Najlepszym wyjaśnieniem jest po prostu odczytanie kodu. Zobacz **DAO_CHECK**, **DAO_CHECK_ERROR**, **DAO_CHECK_MEM**i **DAO_TRACE** in AFXDAO. H, aby wyświetlić makra, i zobacz **AfxDaoCheck** i **AfxDaoTrace** in DAOCORE. CPP.

## <a name="using-the-dao-ole-interfaces"></a>Używanie interfejsów DAO OLE

Interfejsy OLE dla każdego obiektu w hierarchii obiektów DAO są zdefiniowane w pliku nagłówka DBDAOINT. H znajduje się w katalogu \Program Files\Microsoft Visual Studio .NET 2003 \ VC7\include. Te interfejsy zapewniają metody, które umożliwiają manipulowanie całą hierarchią DAO.

Dla wielu metod w interfejsach DAO konieczne będzie manipulowanie `BSTR` obiektem (ciągu z prefiksem, używanym w automatyzacji OLE). Obiekt jest zwykle hermetyzowany w ramach typu danych **Variant.** `BSTR` Sama Klasa `COleVariant` MFC dziedziczy z typu danych **Variant** . W zależności od tego, czy tworzysz projekt dla ANSI lub Unicode, interfejsy DAO będą zwracać ANSI lub Unicode `BSTR`s. Dwa makra, V_BSTR i V_BSTRT, są przydatne do zapewnienia, że interfejs DAO pobiera `BSTR` oczekiwany typ.

V_BSTR wyodrębni element `COleVariant`członkowski *bstrVal* . To makro jest zwykle używane, gdy konieczne jest przekazanie zawartości `COleVariant` do metody interfejsu DAO. Poniższy fragment kodu przedstawia deklaracje i rzeczywiste użycie dwóch metod interfejsu DAO DAOUser, które wykorzystują makro V_BSTR:

```cpp
COleVariant varOldName;
COleVariant varNewName(_T("NewUser"), VT_BSTRT);

// Code to assign pUser to a valid value omitted DAO 3.6 is the final version and it is considered obsolete.User *pUser = NULL;

// These method declarations were taken from DBDAOINT.H
// STDMETHOD(get_Name) (THIS_ BSTR FAR* pbstr) PURE;
// STDMETHOD(put_Name) (THIS_ BSTR bstr) PURE;
DAO 3.6 is the final version and it is considered obsolete._CHECK(pUser->get_Name(&V_BSTR (&varOldName))); DAO 3.6 is the final version and it is considered obsolete._CHECK(pUser->put_Name(V_BSTR (&varNewName)));
```

Należy zauważyć, `VT_BSTRT` że argument określony `COleVariant` w konstruktorze zapewnia, że `BSTR` w `COleVariant` przypadku tworzenia wersji ANSI aplikacji i Unicode `BSTR` dla wersji Unicode Twoja aplikacja. Jest to oczekiwany element DAO.

Pozostałe makro, V_BSTRT, wyodrębnia element członkowski `COleVariant` ANSI lub Unicode *bstrVal* , w zależności od typu kompilacji (ANSI lub Unicode). Poniższy kod ilustruje sposób wyodrębnienia `BSTR` wartości `COleVariant` z `CString`:

```cpp
COleVariant varName(_T("MyName"), VT_BSTRT);
CString str = V_BSTRT(&varName);
```

Makro V_BSTRT, wraz z innymi technikami otwierania innych typów, które są przechowywane w `COleVariant`, przedstawiono w przykładzie DAOVIEW. W odróżnieniu od `CCrack::strVARIANT` tego tłumaczenie jest wykonywane w metodzie. Ta metoda, gdzie to możliwe, tłumaczy wartość a `COleVariant` na `CString`wystąpienie.

## <a name="simple-example-of-a-direct-call-to-dao"></a>Prosty przykład wywołania bezpośredniego do DAO

Sytuacje mogą wystąpić, gdy konieczne jest odświeżenie źródłowych obiektów kolekcji DAO. Zwykle nie powinno to być konieczne, ale jest to prosta procedura, jeśli jest to konieczne. Przykład sytuacji, w której może być konieczne odświeżenie kolekcji, gdy działa w środowisku wielodostępnym z wieloma użytkownikami tworzącymi nowe tabledefs. W takim przypadku kolekcja TableDefs może stać się przestarzała. Aby odświeżyć kolekcję, wystarczy wywołać `Refresh` metodę określonego obiektu kolekcji i sprawdzić pod kątem błędów:

```cpp DAO 3.6 is the final version and it is considered obsolete._CHECK(pMyDaoDatabase->m_pDAOTableDefs->Refresh());
```

Należy pamiętać, że obecnie wszystkie interfejsy obiektów kolekcji DAO są nieudokumentowanymi szczegółami implementacji klas baz danych MFC DAO.

## <a name="using-dao-directly-for-dao-security-features"></a>Używanie DAO bezpośrednio dla funkcji zabezpieczeń DAO

Klasy baz danych MFC DAO nie zawijają funkcji zabezpieczeń DAO. Należy wywołać metody interfejsów DAO, aby używać niektórych funkcji zabezpieczeń DAO. Poniższa funkcja ustawia systemową bazę danych, a następnie zmienia hasło użytkownika. Ta funkcja wywołuje trzy inne funkcje, które są następnie zdefiniowane.

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

W następnych czterech przykładach pokazano, jak:

- Ustaw systemową bazę danych DAO (. Plik MDW).

- Ustaw domyślnego użytkownika i hasło.

- Zmień hasło użytkownika.

- Zmień hasło. Plik MDB.

### <a name="setting-the-system-database"></a>Ustawianie systemowej bazy danych

Poniżej znajduje się przykładowa funkcja służąca do ustawiania systemowej bazy danych, która będzie używana przez aplikację. Ta funkcja musi zostać wywołana przed wykonaniem innych wywołań DAO.

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

### <a name="setting-the-default-user-and-password"></a>Ustawianie domyślnego użytkownika i hasła

Aby ustawić domyślnego użytkownika i hasło dla systemowej bazy danych, należy użyć następującej funkcji:

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

Aby zmienić hasło użytkownika, należy użyć następującej funkcji:

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

### <a name="changing-the-password-of-an-mdb-file"></a>Zmienianie hasła. Plik MDB

Aby zmienić hasło. Plik MDB, użyj następującej funkcji:

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
