---
title: Korzystanie z bibliotek DLL rozszerzeń MFC w bazie danych, OLE i Sockets w zwykłych bibliotekach DLL MFC
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], initializing
- DLLs [C++], extension
- DLLs [C++], regular
ms.assetid: 9f1d14a7-9e2a-4760-b3b6-db014fcdb7ff
ms.openlocfilehash: 3d516f7923144f0e24bda676147ed529546def25
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213765"
---
# <a name="using-database-ole-and-sockets-mfc-extension-dlls-in-regular-mfc-dlls"></a>Korzystanie z bibliotek DLL rozszerzeń MFC w bazie danych, OLE i Sockets w zwykłych bibliotekach DLL MFC

W przypadku korzystania z biblioteki MFC DLL z zwykłej biblioteki MFC DLL, jeśli biblioteka DLL rozszerzenia MFC nie jest podłączona do łańcucha obiektów **CDynLinkLibrary** zwykłej biblioteki MFC DLL, można uruchomić co najmniej jeden zestaw pokrewnych problemów. Ponieważ wersje debugowania baz danych MFC, OLE i Sockets obsługują biblioteki DLL rozszerzenia MFC, można zobaczyć podobne problemy, jeśli używasz tych funkcji MFC, nawet jeśli nie korzystasz jawnie z własnych bibliotek DLL rozszerzenia MFC. Niektóre objawy są następujące:

- Podczas próby deserializacji obiektu typu klasy zdefiniowanego w bibliotece DLL rozszerzenia MFC komunikat "Ostrzeżenie: nie można załadować CYourClass z archiwum. Nie zdefiniowano klasy ". pojawia się w oknie debugowanie śledzenia i nie można serializować obiektu.

- Może zostać zgłoszony wyjątek wskazujący na nieprawidłową klasę.

- Nie można załadować zasobów przechowywanych w bibliotece DLL rozszerzenia MFC, ponieważ `AfxFindResourceHandle` zwraca **wartość null** lub nieprawidłowe dojście do zasobu.

- `DllGetClassObject`, `DllCanUnloadNow` , i `UpdateRegistry` `Revoke` `RevokeAll` `RegisterAll` funkcje elementu członkowskiego `COleObjectFactory` nie mogą znaleźć fabryki klasy zdefiniowanej w bibliotece DLL rozszerzenia MFC.

- `AfxDoForAllClasses`nie działa dla żadnej klasy z biblioteki DLL rozszerzenia MFC.

- Nie można załadować standardowej bazy danych MFC, gniazd lub zasobów OLE. Na przykład **AfxLoadString**(**AFX_IDP_SQL_CONNECT_FAIL**) zwraca pusty ciąg, nawet wtedy, gdy zwykła Biblioteka MFC DLL jest prawidłowo używana z klasami baz danych MFC.

Rozwiązaniem tego problemu jest utworzenie i wyeksportowanie funkcji inicjalizacji w bibliotece DLL rozszerzenia MFC, która tworzy obiekt **CDynLinkLibrary** . Wywołaj tę funkcję inicjującą dokładnie raz z każdej zwykłej biblioteki MFC DLL, która używa biblioteki MFC DLL rozszerzenia.

## <a name="mfc-ole-mfc-database-or-dao-or-mfc-sockets-support"></a>Obsługa MFC OLE, MFC Database (lub DAO) lub MFC Sockets

W przypadku korzystania z obsługi bibliotek MFC OLE, MFC Database (lub DAO) lub MFC Sockets w zwykłej bibliotece MFC DLL, odpowiednio, biblioteki DLL rozszerzenia MFC debugowania MFC MFCOxxD.dll, MFCDxxD.dll i MFCNxxD.dll (gdzie XX jest numerem wersji) są połączone automatycznie. Musisz wywołać wstępnie zdefiniowaną funkcję inicjującą dla każdej z tych bibliotek DLL, które są używane.

Aby zapewnić obsługę bazy danych, należy dodać wywołanie do `AfxDbInitModule` funkcji regularnej biblioteki DLL MFC `CWinApp::InitInstance` . Upewnij się, że to wywołanie występuje przed dowolnymi wywołaniami klasy bazowej lub dodanym kodem, który uzyskuje dostęp do MFCDxxD.dll. Ta funkcja nie przyjmuje parametrów i zwraca wartość void.

W przypadku obsługi OLE Dodaj wywołanie do `AfxOleInitModule` zwykłych bibliotek DLL MFC `CWinApp::InitInstance` . Należy zauważyć, że funkcja **COleControlModule InitInstance** wywołuje się `AfxOleInitModule` już, więc jeśli TWORZYSZ kontrolkę OLE i używasz `COleControlModule` , nie należy dodawać tego wywołania do `AfxOleInitModule` .

W przypadku obsługi gniazd Dodaj wywołanie do `AfxNetInitModule` zwykłych bibliotek DLL MFC `CWinApp::InitInstance` .

Zwróć uwagę na to, że kompilacja wydania bibliotek DLL i aplikacji MFC nie korzysta z oddzielnych bibliotek DLL dla obsługi baz danych, gniazd i OLE. Jednak bezpieczne jest wywoływanie tych funkcji inicjujących w trybie wydania.

## <a name="cdynlinklibrary-objects"></a>CDynLinkLibrary — obiekty

Podczas każdej operacji wymienionej na początku tego tematu MFC musi wyszukać żądaną wartość lub obiekt. Na przykład podczas deserializacji MFC musi przeszukiwać wszystkie aktualnie dostępne klasy uruchomieniowe w celu dopasowania obiektów w archiwum przy użyciu ich właściwej klasy czasu wykonywania.

W ramach tych wyszukiwań MFC są skanowane za pomocą wszystkich bibliotek DLL rozszerzeń MFC używanych przez przeciągnięcie łańcucha obiektów **CDynLinkLibrary** . Obiekty **CDynLinkLibrary** są automatycznie dołączane do łańcucha podczas ich konstruowania i są tworzone przez każdą bibliotekę DLL rozszerzenia MFC z kolei podczas inicjacji. Ponadto każdy moduł (aplikacja lub zwykła Biblioteka DLL MFC) ma własny łańcuch obiektów **CDynLinkLibrary** .

Aby biblioteka DLL rozszerzenia MFC mogła zostać przełączona do łańcucha **CDynLinkLibrary** , musi utworzyć obiekt **CDynLinkLibrary** w kontekście każdego modułu, który używa biblioteki DLL rozszerzenia MFC. W związku z tym, jeśli biblioteka DLL rozszerzenia MFC ma być używana od zwykłych bibliotek DLL MFC, musi dostarczyć wyeksportowaną funkcję inicjującą, która tworzy obiekt **CDynLinkLibrary** . Każda zwykła Biblioteka DLL MFC, która używa biblioteki DLL rozszerzenia MFC, musi wywoływać wyeksportowaną funkcję inicjującą.

Jeśli biblioteka DLL rozszerzenia MFC ma być używana tylko z aplikacji MFC (exe) i nigdy nie ze zwykłej biblioteki MFC DLL, wystarczy utworzyć obiekt **CDynLinkLibrary** w bibliotece DLL rozszerzenia MFC `DllMain` . Jest to kod DLL rozszerzenia MFC DLL kreatora MFC. Podczas ładowania biblioteki DLL rozszerzenia MFC niejawnie, `DllMain` ładuje i wykonuje przed uruchomieniem aplikacji. Wszystkie operacje tworzenia **CDynLinkLibrary** są połączone z domyślnym łańcuchem, który Biblioteka MFC DLL rezerwuje dla aplikacji MFC.

Należy zauważyć, że nie ma potrzeby posiadania wielu obiektów **CDynLinkLibrary** z jednej biblioteki DLL rozszerzenia MFC w jednym łańcuchu, zwłaszcza jeśli biblioteka DLL rozszerzenia MFC zostanie dynamicznie zwolniona z pamięci. Nie wywołuj funkcji inicjalizacji więcej niż raz z jednego modułu.

## <a name="sample-code"></a>Przykładowy kod

W tym przykładowym kodzie przyjęto założenie, że zwykła Biblioteka MFC DLL jest niejawnie łączona z biblioteką DLL rozszerzenia MFC. Jest to realizowane przez połączenie z biblioteką importu (. lib) biblioteki DLL rozszerzenia MFC podczas kompilowania zwykłej biblioteki MFC DLL.

Następujące wiersze powinny znajdować się w źródle biblioteki DLL rozszerzenia MFC:

```
// YourExtDLL.cpp:

// standard MFC extension DLL routines
#include "afxdllx.h"

static AFX_EXTENSION_MODULE NEAR extensionDLL = { NULL, NULL };

extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
    if (dwReason == DLL_PROCESS_ATTACH)
    {
        // MFC extension DLL one-time initialization
        if (!AfxInitExtensionModule(extensionDLL, hInstance))
           return 0;
    }
    return 1;   // ok
}

// Exported DLL initialization is run in context of
// application or regular MFC DLL
extern "C" void WINAPI InitYourExtDLL()
{
    // create a new CDynLinkLibrary for this app
    new CDynLinkLibrary(extensionDLL);

    // add other initialization here
}
```

Należy pamiętać, aby wyeksportować funkcję **InitYourExtDLL** . Można to zrobić za pomocą **`__declspec(dllexport)`** lub w pliku dll. def w następujący sposób:

```
// YourExtDLL.Def:
LIBRARY      YOUREXTDLL
CODE         PRELOAD MOVEABLE DISCARDABLE
DATA         PRELOAD SINGLE
EXPORTS
    InitYourExtDLL
```

Dodaj wywołanie do `InitInstance` elementu członkowskiego `CWinApp` obiektu pochodnego w każdej zwykłej bibliotece MFC DLL przy użyciu biblioteki DLL rozszerzenia MFC:

```
// YourRegularDLL.cpp:

class CYourRegularDLL : public CWinApp
{
public:
    virtual BOOL InitInstance(); // Initialization
    virtual int ExitInstance();  // Termination

    // nothing special for the constructor
    CYourRegularDLL(LPCTSTR pszAppName) : CWinApp(pszAppName) { }
};

BOOL CYourRegularDLL::InitInstance()
{
    // any DLL initialization goes here
    TRACE0("YOUR regular MFC DLL initializing\n");

    // wire any MFC extension DLLs into CDynLinkLibrary chain
    InitYourExtDLL();

    return TRUE;
}
```

### <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Inicjowanie biblioteki DLL rozszerzenia MFC](run-time-library-behavior.md#initializing-extension-dlls)

- [Inicjowanie zwykłych bibliotek DLL MFC](run-time-library-behavior.md#initializing-regular-dlls)

### <a name="what-do-you-want-to-know-more-about"></a>Jak chcesz dowiedzieć się więcej?

- [Biblioteki DLL rozszerzeń MFC](extension-dlls.md)

- [Regularne biblioteki MFC DLL statycznie połączone z MFC](regular-dlls-statically-linked-to-mfc.md)

- [Regularne biblioteki DLL MFC połączone dynamicznie z MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Używanie MFC jako części biblioteki DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [Wersja biblioteki DLL MFC](../mfc/tn033-dll-version-of-mfc.md)

## <a name="see-also"></a>Zobacz także

[Biblioteki DLL rozszerzeń MFC](extension-dlls.md)
