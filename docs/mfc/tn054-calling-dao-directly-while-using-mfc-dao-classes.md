---
title: "TN054: Wywoływanie obiektów DAO bezpośrednio podczas używania klas MFC DAO | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.dao
dev_langs: C++
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
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: de49cec931878cbfe06939269721b17a37a66202
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="tn054-calling-dao-directly-while-using-mfc-dao-classes"></a>TN054: wywoływanie obiektów DAO bezpośrednio podczas używania klas MFC DAO
> [!NOTE]
>  Środowiska Visual C++ i kreatorów nie obsługują DAO (mimo że uwzględniono klasy DAO i nadal można ich używać). Firma Microsoft zaleca użycie [szablony OLE DB](../data/oledb/ole-db-templates.md) lub [ODBC i MFC](../data/odbc/odbc-and-mfc.md) dla nowych projektów. Obiekty DAO należy używać tylko w zachowaniu istniejących aplikacji.  
  
 Podczas korzystania z klasami baz danych MFC DAO, mogą wystąpić sytuacje, w których należy użyć DAO bezpośrednio. Zazwyczaj nie będzie to wymagane, ale MFC udostępnił niektórych mechanizmów pomocnika do ułatwienia tworzenia bezpośrednie wywołania DAO proste podczas łączenia z bezpośrednim odwołaniem DAO użycia klas MFC. Tworzenie bezpośrednich DAO wywołania metod obiektu zarządzanego MFC DAO należy włączyć tylko kilka wierszy kodu. Jeśli musisz utworzyć i użyć obiektów DAO, które są *nie* zarządza MFC, trzeba będzie wykonać nieco więcej pracy faktycznie wywołując **wersji** obiektu. Ta uwaga techniczna wyjaśniono, kiedy warto wywołanie DAO bezpośrednio, pomocników MFC czynności ułatwiające i jak używać interfejsów DAO OLE. Ponadto ta uwaga zawiera niektóre funkcje przykład przedstawiający sposób wywołania DAO bezpośrednio do DAO funkcje zabezpieczeń.  
  
## <a name="when-to-make-direct-dao-calls"></a>Kiedy do nawiązywania połączeń bezpośrednich DAO  
 Najbardziej typowe sytuacje wymagające dokonywania bezpośrednie wywołania DAO występuje, gdy kolekcje wymagają odświeżenia lub podczas wdrażania funkcji nie zostały opakowane przez MFC. Zabezpieczenia są najważniejszych funkcji, które nie są udostępniane przez MFC. Jeśli chcesz wdrożyć funkcje zabezpieczeń, należy korzystać bezpośrednio obiekt DAO użytkowników i grup. Oprócz zabezpieczeń istnieje tylko kilka innych DAO funkcji nie są obsługiwane przez MFC. Obejmują one zestaw rekordów klonowania i bazy danych funkcje replikacji, a także kilka późne dodatki do DAO.  
  
## <a name="a-brief-overview-of-dao-and-mfcs-implementation"></a>Krótki przegląd wdrożenia DAO i MFC  
 Zawijanie MFC DAO łatwiejsze przy użyciu obsługi wielu szczegółów, dzięki czemu nie trzeba martwić podstawowe czynności ułatwia DAO. Obejmuje to Zainicjowanie OLE, tworzenie i zarządzanie obiekty DAO (szczególnie obiekty kolekcji), błąd sprawdzania i udostępnia interfejsem jednoznacznie, prostszy (nie **VARIANT** lub `BSTR` argumenty). Możesz bezpośrednie wywoływanie DAO i nadal korzystać z tych funkcji. Kod należy wykonać wywołanie jest **wersji** dla obiektów utworzonych przez bezpośrednie DAO wywołuje i *nie* zmodyfikuj te z nich wskaźniki interfejsu, które MFC mogą polegać na wewnętrznie. Na przykład nie należy modyfikować **m_pDAORecordset** członkiem otwarty `CDaoRecordset` obiekt bez zrozumienia *wszystkie* konsekwencje wewnętrznego. Można jednak użyć **m_pDAORecordset** interfejsu wywoływanie obiektów DAO bezpośrednio do pobrania z kolekcji pól. W takim przypadku **m_pDAORecordset** nie będzie można zmodyfikować elementu członkowskiego. Po prostu trzeba wywoływać **wersji** w obiekcie kolekcji pól po zakończeniu pracy z obiektem.  
  
## <a name="description-of-helpers-to-make-dao-calls-easier"></a>Opis pomocników dokonanie DAO wywołuje łatwiejsze  
 Pomocnicy podane umożliwią wywoływanie obiektów DAO łatwiejsze są tego samego wątków, które są używane wewnętrznie w klasach bazy danych DAO MFC. Te pomocników są używane do sprawdzenia kodów powrotnych podczas nawiązywania bezpośredniego połączenia DAO, rejestrowania danych wyjściowych debugowania, sprawdzanie błędów oczekiwanego i zgłaszanie wyjątków odpowiednie, jeśli to konieczne. Istnieją dwa podstawowe funkcje pomocnicze i cztery makra, które mapują na jeden z tych dwóch pomocników. Najlepsze wyjaśnienie jest po prostu odczytać kodu. Zobacz **DAO_CHECK**, **DAO_CHECK_ERROR**, **DAO_CHECK_MEM**, i **DAO_TRACE** w AFXDAO. H Zobacz makra, i zobaczyć **AfxDaoCheck** i **AfxDaoTrace** w DAOCORE. CPP.  
  
## <a name="using-the-dao-ole-interfaces"></a>Za pomocą DAO interfejsy OLE  
 Interfejsy modelu OLE dla każdego obiektu w hierarchii obiektów DAO są zdefiniowane w pliku nagłówka DBDAOINT. H, który znajduje się w katalogu \Program Files\Microsoft 2003\VC7\include programu Visual Studio .NET. Te interfejsy Podaj metody, dzięki którym można manipulować w całej hierarchii DAO.  
  
 Dla wielu metod w interfejsach DAO, konieczne będzie manipulowania `BSTR` obiektu (prefiks długości ciągu używany w automatyzacji OLE). `BSTR` Obiektu zwykle jest hermetyzowany wewnątrz **VARIANT** — typ danych. Klasy MFC `COleVariant` sam dziedziczy **VARIANT** — typ danych. W zależności od tego, czy w przypadku kompilowania projektu dla ANSI lub Unicode, interfejsów DAO zwróci ANSI lub Unicode `BSTR`s. Makra dwóch **V_BSTR** i **V_BSTRT**, są używane do zapewnienia, że interfejs DAO pobiera `BSTR` oczekiwanego typu.  
  
 **V_BSTR** wyodrębni **bstrVal** członkiem `COleVariant`. To makro jest zwykle używana, gdy trzeba przekazać zawartość `COleVariant` do metody interfejsu DAO. Poniższy fragment kodu przedstawia deklaracje i rzeczywistego użycia dla dwóch metod interfejsu DAO DAOUser wykorzystującego **V_BSTR** makra:  
  
```  
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
  
 Należy pamiętać, że `VT_BSTRT` określona w argumencie `COleVariant` Konstruktor powyżej gwarantuje, że będzie ANSI `BSTR` w `COleVariant` Jeśli kompilacji wersja ANSI Unicode i aplikacji `BSTR` wersji Unicode aplikacji. Jest to DAO oczekuje.  
  
 Inne makro **V_BSTRT**, wyodrębni ANSI lub Unicode **bstrVal** członkiem `COleVariant` w zależności od typu kompilacji (ANSI lub Unicode). Poniższy kod ilustruje sposób wyodrębnić `BSTR` wartość z `COleVariant` do `CString`:  
  
```  
COleVariant varName(_T("MyName"), VT_BSTRT);

CString str = V_BSTRT(&varName);
```  
  
 **V_BSTRT** makra, wraz z innych technik, aby otworzyć inne typy, które są przechowywane w `COleVariant`, przedstawiono w przykładzie DAOVIEW. W szczególności tłumaczenie jest wykonywane w **CCrack::strVARIANT** metody. Tej metody, jeśli to możliwe, tłumaczy wartość `COleVariant` w wystąpienie klasy `CString`.  
  
## <a name="simple-example-of-a-direct-call-to-dao"></a>Prosty przykład bezpośrednie wywołanie DAO  
 Sytuacjach może wystąpić, gdy jest to niezbędne odświeżyć kolekcji obiektów DAO. Zazwyczaj nie powinna być konieczne, ale jest prostą procedurę, w razie potrzeby. Przykład gdy kolekcja może wymagać odświeżenia to podczas pracy w środowisku wielodostępnym z wieloma użytkownikami, tworzenie nowych tabledefs —. W takim przypadku tabledefs — kolekcja, mogą stać się przestarzałe. Aby odświeżyć kolekcji, po prostu należy wywołać **Odśwież** metodę obiektu danej kolekcji i zaznacz pole wyboru dla błędów:  
  
```  
DAO_CHECK(pMyDaoDatabase->  
    m_pDAOTableDefs->Refresh());
```  
  
 Należy zauważyć, że obecnie wszystkie interfejsy obiektu kolekcji DAO szczegóły implementacji nieudokumentowanej klas MFC DAO bazy danych.  
  
## <a name="using-dao-directly-for-dao-security-features"></a>Przy użyciu obiektów DAO bezpośrednio dla funkcji zabezpieczeń DAO  
 Klasy baz danych MFC DAO DAO funkcje zabezpieczeń nie jest zawijany. Należy wywołać metody interfejsów DAO, aby korzystać z niektórych funkcji zabezpieczeń DAO. Następująca funkcja ustawia systemowej bazy danych, a następnie zmienia hasło użytkownika. Ta funkcja wymaga trzech innych funkcji, które następnie są zdefiniowane.  
  
```  
void ChangeUserPassword()  
{ *// Specify path to the Microsoft Access *// system database  
    CString strSystemDB = 
    _T("c:\\Program Files\\MSOffice\\access\\System.mdw");

 *// Set system database before MFC initilizes DAO *// NOTE: An MFC module uses only one instance *// of a DAO database engine object. If you have *// called a DAO object in your application prior *// to calling the function below,
    you must call *// AfxDaoTerm to destroy the existing database *// engine object. Otherwise,
    the database engine *// object already in use will be reused,
    and setting *// a system datbase will have no effect. *// *// If you have used a DAO object prior to calling *// this function it is important that DAO be *// terminated with AfxDaoTerm since an MFC *// module only gets one copy of the database engine *// and that engine will be reused if it hasn't been *// terminated. In other words,
    if you do not call *// AfxDaoTerm and there is currently a database *// initialized,
    setting the system database will *// have no affect.  
 
    SetSystemDB(strSystemDB);

 *// User name and password manually added *// by using Microsoft Access  
    CString strUserName = _T("NewUser");

    CString strOldPassword = _T("Password");

    CString strNewPassword = _T("NewPassword");

 *// Set default user so that MFC will be able *// to log in by default using the user name and *// password from the system database  
    SetDefaultUser(strUserName,
    strOldPassword);

 *// Change the password. You should be able to *// call this function from anywhere in your *// MFC application  
    ChangePassword(strUserName,
    strOldPassword,   
    strNewPassword);

 
 .  
 .  
 .  
 
}  
```  
  
 Następnie cztery przykłady pokazują, jak:  
  
-   Ustaw systemowej bazy danych DAO (. Plik MDW).  
  
-   Ustaw domyślnego użytkownika i hasło.  
  
-   Zmień hasło użytkownika.  
  
-   Zmiany hasła. Plik MDB.  
  
### <a name="setting-the-system-database"></a>Ustawienie systemowej bazy danych  
 Poniżej znajdują się przykładowe funkcji, aby ustawić systemowej bazy danych, który będzie używany przez aplikację. Ta funkcja musi być wywołana przed wszystkie inne DAO wywołań.  
  
```  
// Set the system database that the   
// DAO database engine will use  
 
void SetSystemDB(CString& strSystemMDB)  
{  
    COleVariant varSystemDB(strSystemMDB, VT_BSTRT);

 *// Initialize DAO for MFC  
    AfxDaoInit();
DAODBEngine* pDBEngine = AfxDaoGetEngine();

 
    ASSERT(pDBEngine != NULL);

 *// Call put_SystemDB method to set the *// system database for DAO engine  
    DAO_CHECK(pDBEngine->put_SystemDB(varSystemDB.bstrVal));

} 
```  
  
### <a name="setting-the-default-user-and-password"></a>Ustawienie domyślne użytkownika i hasło  
 Aby ustawić domyślnego użytkownika i hasło dla systemowej bazy danych, użyj następujących funkcji:  
  
```  
void SetDefaultUser(CString& strUserName,
    CString& strPassword)  
{  
    COleVariant varUserName(strUserName,
    VT_BSTRT);

    COleVariant varPassword(strPassword,
    VT_BSTRT);

 
    DAODBEngine* pDBEngine = AfxDaoGetEngine();
ASSERT(pDBEngine != NULL);

 *// Set default user:  
    DAO_CHECK(pDBEngine->put_DefaultUser(varUserName.bstrVal));

 *// Set default password:  
    DAO_CHECK(pDBEngine->put_DefaultPassword(varPassword.bstrVal));

} 
```  
  
### <a name="changing-a-users-password"></a>Zmiana hasła użytkownika  
 Aby zmienić hasło użytkownika, należy użyć następujących funkcji:  
  
```  
void ChangePassword(CString &strUserName,   
    CString &strOldPassword,   
    CString &strNewPassword)  
{ *// Create (open) a workspace  
    CDaoWorkspace wsp;  
    CString strWspName = _T("Temp Workspace");

 
    wsp.Create(strWspName, strUserName,  
    strOldPassword);

 wsp.Append();

 *// Determine how many objects there are *// in the Users collection  
    short nUserCount;  
    short nCurrentUser;  
    DAOUser *pUser = NULL;  
    DAOUsers *pUsers = NULL;  
 *// Side-effect is implicit OLE AddRef() *// on DAOUser object:  
    DAO_CHECK(wsp.m_pDAOWorkspace->get_Users(&pUsers));

 *// Side-effect is implicit OLE AddRef() *// on DAOUsers object  
    DAO_CHECK(pUsers->getcount(&nUserCount));

 *// Traverse through the list of users *// and change password for the userid *// used to create/open the workspace  
    for(nCurrentUser = 0; nCurrentUser <nUserCount;  
    nCurrentUser++) 
 {  
    COleVariant varIndex(nCurrentUser, VT_I2);

    COleVariant varName;  
 *// Retrieve information for user nCurrentUser  
    DAO_CHECK(pUsers->get_Item(varIndex, &pUser));

 *// Retrieve name for user nCurrentUser  
    DAO_CHECK(pUser->get_Name(&V_BSTR(&varName)));

 
    CString strTemp = V_BSTRT(&varName);

 *// If there is a match, change the password  
    if(strTemp == strUserName)  
 {  
    COleVariant varOldPwd(strOldPassword,   
    VT_BSTRT);

 COleVariant  varNewPwd(strNewPassword,   
    VT_BSTRT);

 
    DAO_CHECK(pUser->NewPassword(V_BSTR(&varOldPwd), 
    V_BSTR(&varNewPwd)));

 
    TRACE("\t Password is changed\n");

 }  
 }  
 *// Clean up: decrement the usage count *// on the OLE objects  
    pUser->Release();
pUsers->Release();

 
    wsp.Close();

} 
```  
  
### <a name="changing-the-password-of-an-mdb-file"></a>Zmiana hasła. Plik MDB  
 Aby zmienić hasło. MDB plików, użyj następujących funkcji:  
  
```  
void SetDBPassword(LPCTSTR pDB,
    LPCTSTR pszOldPassword,
    LPCTSTR pszNewPassword)  
{  
    CDaoDatabase db;  
    CString strConnect(_T(";pwd="));

 *// the database must be opened as exclusive *// to set a password  
    db.Open(pDB,
    TRUE,
    FALSE,   
    strConnect + pszOldPassword);

 
    COleVariant NewPassword(pszNewPassword,
    VT_BSTRT),  
    OldPassword(pszOldPassword,
    VT_BSTRT);

 
    DAO_CHECK(db.m_pDAODatabase->NewPassword(V_BSTR(&OldPassword), 
    V_BSTR(&NewPassword)));

 
    db.Close();

} 
```  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

