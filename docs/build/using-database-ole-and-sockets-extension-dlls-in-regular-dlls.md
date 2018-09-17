---
title: Przy użyciu bazy danych, OLE i MFC gniazd biblioteki DLL rozszerzeń w zwykłych bibliotekach MFC dll | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], initializing
- DLLs [C++], extension
- DLLs [C++], regular
ms.assetid: 9f1d14a7-9e2a-4760-b3b6-db014fcdb7ff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b8fe2c57991ffd15f135fab39c185b6a68f2e9c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701995"
---
# <a name="using-database-ole-and-sockets-mfc-extension-dlls-in-regular-mfc-dlls"></a>Przy użyciu bazy danych, OLE i MFC gniazd biblioteki DLL rozszerzeń w zwykłych bibliotekach MFC dll

Korzystając z rozszerzenia MFC biblioteki DLL z regularnej biblioteki DLL MFC, jeżeli rozszerzenia MFC biblioteki DLL nie jest dostępna w **CDynLinkLibrary** obiektu łańcucha regularne biblioteki DLL MFC, może wystąpić co najmniej jeden zestaw problemów pokrewnych. Ponieważ obsługuje wersje do debugowania bazy danych MFC, OLE i gniazda biblioteki DLL są implementowane jako biblioteki DLL rozszerzeń MFC, można napotkać podobny problem, jeśli używasz tych MFC funkcji, nawet wtedy, gdy użytkownik nie jawnie korzystania z własnych biblioteki DLL rozszerzeń MFC. Występują pewne objawy:

- Podczas próby deserializacji obiektu typu klasy zdefiniowane w rozszerzeń MFC DLL, komunikat "Ostrzeżenie: nie można załadować CYourClass z archiwum. Klasa nie jest zdefiniowany." pojawia się okno debugowania śledzenia i obiekt kończy się niepowodzeniem do serializacji.

- Może zostać wygenerowany wyjątek wskazujący zły klasy.

- Zasobów przechowywanych w bibliotece DLL rozszerzenia MFC nie można załadować, ponieważ `AfxFindResourceHandle` zwraca **NULL** lub zasobów nieprawidłowe dojście.

- `DllGetClassObject`, `DllCanUnloadNow`i `UpdateRegistry`, `Revoke`, `RevokeAll`, i `RegisterAll` funkcje elementów członkowskich `COleObjectFactory` z lokalizowaniem fabrykę klas zdefiniowanych w rozszerzenia MFC biblioteki DLL.

- `AfxDoForAllClasses` nie działa dla wszystkich klas w bibliotece DLL rozszerzenia MFC.

- Database w warstwie standardowa MFC gniazd i zasoby OLE nie można załadować. Na przykład **AfxLoadString**(**AFX_IDP_SQL_CONNECT_FAIL**) zwraca pusty ciąg, nawet w przypadku zwykłej biblioteki MFC DLL jest prawidłowo przy użyciu klas MFC baz danych.

Rozwiązanie tych problemów jest utworzenie i eksportowanie funkcji inicjowania rozszerzenia MFC biblioteki DLL, która tworzy **CDynLinkLibrary** obiektu. Wywołaj tę funkcję inicjowania, dokładnie tak, gdy z każdego zwykłej biblioteki MFC DLL używającą biblioteki DLL rozszerzenia MFC.

## <a name="mfc-ole-mfc-database-or-dao-or-mfc-sockets-support"></a>OLE w MFC, baza danych MFC (lub DAO), lub MFC gniazd pomocy technicznej

Jeśli używasz dowolnego MFC OLE, baza danych MFC (lub DAO) lub MFC gniazd pomocy technicznej w swojej zwykłej biblioteki MFC DLL, odpowiednio, MFC debugowania rozszerzenia MFC biblioteki DLL MFCOxxD.dll MFCDxxD.dll i MFCNxxD.dll (gdzie xx jest numer wersji) są automatycznie łączone. Dla każdego z tych bibliotek DLL, które są używane, należy wywołać funkcję inicjowania wstępnie zdefiniowane.

Do obsługi bazy danych, dodaj wywołanie `AfxDbInitModule` do swojej zwykłej biblioteki MFC DLL w `CWinApp::InitInstance` funkcji. Upewnij się, to wywołanie występuje przed wywołaniem dowolnej klasy podstawowej lub wszyscy dodani kod, który uzyskuje dostęp do MFCDxxD.dll. Ta funkcja nie przyjmuje żadnych parametrów i zwraca wartość void.

Obsługę OLE, dodaj wywołanie `AfxOleInitModule` do swojej zwykłej biblioteki MFC DLL w `CWinApp::InitInstance`. Należy pamiętać, że **COleControlModule InitInstance** wywołaniach funkcji `AfxOleInitModule` , więc jeśli tworzysz kontrolkę OLE i korzystają z `COleControlModule`, to wywołanie nie należy dodawać `AfxOleInitModule`.

Obsługę gniazda, dodaj wywołanie `AfxNetInitModule` do swojej zwykłej biblioteki MFC DLL w `CWinApp::InitInstance`.

Zauważ, że kompilacji wersji biblioteki MFC DLL a aplikacje nie używają oddzielnych bibliotek DLL dla bazy danych, gniazda, lub obsługuje OLE. Jednak jest bezpieczny do wywołania tych funkcji inicjowania w trybie wydania.

## <a name="cdynlinklibrary-objects"></a>Obiekty CDynLinkLibrary

Podczas każdej operacji, o których wspomniano na początku tego tematu MFC musi Wyszukaj żądaną wartość lub obiektu. Na przykład podczas deserializacji MFC musi przeszukać wszystkie aktualnie dostępne klasy środowiska wykonawczego dopasowania obiektów w warstwie archiwum, przy użyciu ich odpowiednie klasy środowiska wykonawczego.

W ramach wyszukiwania, MFC skanuje za pośrednictwem wszystkie rozszerzone dll MFC używane przez zalet łańcuch **CDynLinkLibrary** obiektów. **CDynLinkLibrary** obiekty automatycznie dołączyć łańcuch, podczas ich tworzenia i są tworzone przez każdego rozszerzenia MFC biblioteki DLL z kolei podczas inicjowania. Ponadto każdy moduł (aplikacji lub zwykłej biblioteki MFC DLL) ma swój własny łańcuch **CDynLinkLibrary** obiektów.

Rozszerzenia MFC biblioteki DLL, aby pobrać połączonymi w **CDynLinkLibrary** łańcucha, należy utworzyć **CDynLinkLibrary** obiektu w kontekście każdego modułu, który korzysta z biblioteki DLL rozszerzenia MFC. W związku z tym, jeśli rozszerzenia MFC biblioteki DLL będzie można korzystać w zwykłych bibliotekach MFC dll, musi mieć funkcję inicjowania wyeksportowanej, która tworzy **CDynLinkLibrary** obiektu. Co regularnej biblioteki DLL MFC, który używa rozszerzeń MFC DLL musi wywołać funkcję inicjowania wyeksportowany.

Jeśli rozszerzenia MFC biblioteki DLL ma być używane z aplikacji MFC (.exe) i nigdy nie zwykłej biblioteki MFC DLL, a następnie jest wystarczające, aby utworzyć **CDynLinkLibrary** obiektu w bibliotece MFC DLL rozszerzenia firmy `DllMain`. Jest to, jak działa rozszerzenie biblioteki MFC DLL Kreatora MFC DLL kodu. Podczas ładowania biblioteki DLL rozszerzenia MFC niejawnie `DllMain` ładuje i uruchamia przed uruchomieniem kiedykolwiek aplikacji. Wszelkie **CDynLinkLibrary** tworzenie są połączonymi w łańcuch domyślne czy biblioteki MFC DLL rezerwuje dla aplikacji MFC.

Należy pamiętać, że to zły pomysł, aby ustawić wiele **CDynLinkLibrary** obiektów z jednego rozszerzenia MFC biblioteki DLL w jednym łańcucha, zwłaszcza, jeśli biblioteka DLL rozszerzenia MFC będzie dynamicznie zwolniony z pamięci. Nie wywołuj funkcji inicjowania więcej niż jeden raz z dowolnym jeden moduł.

## <a name="sample-code"></a>Przykładowy kod

Ten przykładowy kod zakłada, że zwykłej biblioteki MFC DLL jest niejawnie łączenie z biblioteki DLL rozszerzenia MFC. Jest to realizowane przez połączenie do biblioteki importu (.lib) rozszerzenia MFC biblioteki DLL, podczas kompilowania zwykłej biblioteki MFC DLL.

Źródło rozszerzenia MFC biblioteki DLL powinny być następujące wiersze:

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

Pamiętaj wyeksportować **InitYourExtDLL** funkcji. Można to zrobić przy użyciu **__declspec(dllexport)** lub w pliku .def biblioteki DLL w następujący sposób:

```
// YourExtDLL.Def:
LIBRARY      YOUREXTDLL
CODE         PRELOAD MOVEABLE DISCARDABLE
DATA         PRELOAD SINGLE
EXPORTS
    InitYourExtDLL
```

Dodaj wywołanie do `InitInstance` członkiem `CWinApp`-pochodzi obiekt w każdym zwykłej biblioteki MFC DLL za pomocą rozszerzenia MFC biblioteki DLL:

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

- [Inicjowanie biblioteki DLL rozszerzenia MFC](../build/run-time-library-behavior.md#initializing-extension-dlls)

- [Zainicjuj regularną bibliotekę DLL MFC](../build/run-time-library-behavior.md#initializing-regular-dlls)

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [Biblioteki DLL rozszerzeń MFC](../build/extension-dlls.md)

- [Zwykłe biblioteki DLL MFC połączone statycznie z MFC](../build/regular-dlls-statically-linked-to-mfc.md)

- [Zwykłe biblioteki DLL MFC połączone dynamicznie z MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)

- [Używanie MFC jako części biblioteki DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [Wersja dll biblioteki MFC](../mfc/tn033-dll-version-of-mfc.md)

## <a name="see-also"></a>Zobacz też

[Biblioteki DLL rozszerzeń MFC](../build/extension-dlls.md)