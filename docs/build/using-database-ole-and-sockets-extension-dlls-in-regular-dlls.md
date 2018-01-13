---
title: "Przy użyciu bazy danych, OLE i MFC gniazda biblioteki DLL rozszerzeń w zwykłych bibliotekach DLL MFC | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- DLLs [C++], initializing
- DLLs [C++], extension
- DLLs [C++], regular
ms.assetid: 9f1d14a7-9e2a-4760-b3b6-db014fcdb7ff
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0042dd5dc6049447868cf5ca5ea1112b3695f3a3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="using-database-ole-and-sockets-mfc-extension-dlls-in-regular-mfc-dlls"></a>Przy użyciu bazy danych, OLE i MFC gniazda biblioteki DLL rozszerzeń w zwykłych bibliotekach DLL MFC
Jeśli z rozszerzeniem MFC DLL z regularne biblioteki DLL MFC rozszerzenia MFC DLL nie jest dostępna w **CDynLinkLibrary** obiekt łańcucha regularne biblioteki DLL MFC może działać w co najmniej jeden zbiór problemów pokrewnych. Ponieważ obsługuje wersje debugowania MFC bazy danych, OLE i gniazda biblioteki DLL są zaimplementowane jako biblioteki DLL rozszerzeń MFC, można napotkać funkcje podobne problemy, jeśli używasz tych MFC, nawet jeśli nie jest jawnie używana żadnego własne biblioteki DLL rozszerzeń MFC. Niektóre symptomy są:  
  
-   Podczas próby deserializacji obiektu typu klasy określone w rozszerzenia MFC DLL, komunikat "Ostrzeżenie: nie można załadować CYourClass z archiwum. Klasa nie zdefiniowano". zostanie wyświetlony w oknie Debugowanie śledzenia i obiektu kończy się niepowodzeniem do serializacji.  
  
-   Może być wyjątek wskazujący zły klasy.  
  
-   Zasobów przechowywanych w bibliotece DLL rozszerzenia MFC nie można załadować, ponieważ `AfxFindResourceHandle` zwraca **NULL** lub zasobu nieprawidłowe dojście.  
  
-   `DllGetClassObject`, `DllCanUnloadNow`i `UpdateRegistry`, `Revoke`, `RevokeAll`, i `RegisterAll` funkcji Członkowskich `COleObjectFactory` nie można zlokalizować fabrykę klas zdefiniowanych w bibliotece DLL rozszerzenia MFC.  
  
-   `AfxDoForAllClasses`nie działa dla wszystkich klas w bibliotece DLL rozszerzenia MFC.  
  
-   Standardowa baza danych MFC, gniazda lub zasobów OLE nie można załadować. Na przykład **AfxLoadString**(**AFX_IDP_SQL_CONNECT_FAIL**) zwraca pusty ciąg, nawet wtedy, gdy regularne biblioteki DLL MFC prawidłowo przy użyciu klasy baz danych MFC.  
  
 Rozwiązanie tych problemów jest utworzenie i eksportowanie funkcji inicjowania rozszerzenia MFC DLL, która tworzy **CDynLinkLibrary** obiektu. Wywołanie tej funkcji inicjowania dokładnie po z każdym regularne biblioteki DLL MFC, która używa biblioteki DLL rozszerzenia MFC.  
  
## <a name="mfc-ole-mfc-database-or-dao-or-mfc-sockets-support"></a>MFC OLE, bazy danych MFC (lub DAO), lub obsługa gniazda MFC  
 Jeśli używasz dowolnego MFC OLE, bazy danych MFC (lub DAO) lub MFC Sockets obsługuje odpowiednio regularne biblioteki DLL MFC, debugowania MFC rozszerzenia MFC DLL MFCOxxD.dll MFCDxxD.dll i MFCNxxD.dll (gdzie xx jest numer wersji) są automatycznie połączone. Dla każdego z tych bibliotek DLL, które są używane, należy wywołać funkcję inicjowania wstępnie zdefiniowane.  
  
 Do obsługi bazy danych, dodaj wywołanie do `AfxDbInitModule` do biblioteki regularne DLL MFC `CWinApp::InitInstance` funkcji. Upewnij się, to wywołanie występuje przed wywołaniem dowolnej klasy podstawowej ani żadnym z dodanych kod, który uzyskuje dostęp do MFCDxxD.dll. Ta funkcja nie przyjmuje żadnych parametrów i zwraca typ void.  
  
 Obsługa OLE, dodaj wywołanie do `AfxOleInitModule` do biblioteki regularne DLL MFC `CWinApp::InitInstance`. Należy pamiętać, że **COleControlModule InitInstance** wywołania funkcji `AfxOleInitModule` już, tak więc jeśli budowania kontrolkę OLE i używasz `COleControlModule`, to wywołanie nie należy dodawać `AfxOleInitModule`.  
  
 Obsługa gniazda, dodaj wywołanie do `AfxNetInitModule` do biblioteki regularne DLL MFC `CWinApp::InitInstance`.  
  
 Zauważ, że kompilacje wersji biblioteki MFC dll i aplikacji należy używać oddzielnych biblioteki DLL dla bazy danych, gniazda, lub obsługa OLE. Jednak jest bezpiecznie wywoływać te funkcje inicjowania w trybie wersji.  
  
## <a name="cdynlinklibrary-objects"></a>Obiekty CDynLinkLibrary  
 Podczas każdej operacji wymienionych na początku tego tematu MFC należy wyszukać żądaną wartość lub obiekt. Na przykład podczas deserializacji, MFC musi przeszukać wszystkie aktualnie dostępne klasy środowiska wykonawczego odpowiadające obiektów w archiwum z ich odpowiednich klasie czasu wykonywania.  
  
 W ramach wyszukiwania, MFC skanowania za pomocą wszystkich dll rozszerzenia MFC używany przez krótki łańcuch **CDynLinkLibrary** obiektów. **CDynLinkLibrary** obiekty automatycznie dołączyć do łańcucha, podczas ich tworzenia i są tworzone przez każdy bibliotekę DLL rozszerzenia MFC z kolei podczas inicjowania. Ponadto każdy moduł (aplikacji lub regularnych bibliotek DLL MFC) ma własną łańcuch **CDynLinkLibrary** obiektów.  
  
 Rozszerzenia MFC DLL do pobrania przewodowej do **CDynLinkLibrary** łańcucha, należy utworzyć **CDynLinkLibrary** obiektu w kontekście każdy moduł, który korzysta z biblioteki DLL rozszerzenia MFC. W związku z tym jeśli rozszerzenia MFC DLL będzie można używać z regularne biblioteki DLL MFC, musi ona inicjowania wyeksportowanej funkcji, która tworzy **CDynLinkLibrary** obiektu. Co regularne biblioteki DLL MFC, która używa rozszerzenia MFC DLL musi wywoływać funkcję inicjowania wyeksportowane.  
  
 Jeśli rozszerzenia MFC DLL ma być używane z aplikacji MFC (.exe) i nigdy nie regularną bibliotekę DLL MFC, wystarczy utworzyć **CDynLinkLibrary** obiekt bibliotece MFC DLL rozszerzenia w `DllMain`. Jest to, co oznacza kod biblioteki DLL rozszerzenia MFC Kreator biblioteki DLL MFC. Podczas ładowania biblioteki DLL rozszerzenia MFC niejawnie `DllMain` ładuje i wykonuje przed uruchomieniem kiedykolwiek aplikacji. Wszelkie **CDynLinkLibrary** tworzenie są połączone w łańcuch domyślne czy biblioteki MFC DLL rezerwuje aplikacji MFC.  
  
 Należy pamiętać, że dobrym pomysłem wielu **CDynLinkLibrary** obiektów z jedną bibliotekę DLL rozszerzenia MFC w jednym łańcucha, zwłaszcza, jeśli biblioteka DLL rozszerzenia MFC zostanie dynamicznie zwolniona z pamięci. Nie należy wywoływać funkcję inicjowania więcej niż jeden raz z dowolnym jeden moduł.  
  
## <a name="sample-code"></a>Przykładowy kod  
 Ten przykładowy kod przyjęto założenie, że regularne biblioteki DLL MFC jest niejawnie łączenie z biblioteki DLL rozszerzenia MFC. Jest to osiągane przez łączenie z biblioteki importu (lib) biblioteki DLL rozszerzenia MFC podczas kompilowania regularne biblioteki DLL MFC.  
  
 Następujące wiersze powinny być w źródle bibliotekę DLL rozszerzenia MFC:  
  
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
  
 Dodaj wywołanie do `InitInstance` członkiem `CWinApp`-pochodnych obiektu w każdej regularnych biblioteki MFC DLL rozszerzenia MFC DLL:  
  
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
  
-   [Inicjowanie biblioteki DLL rozszerzenia MFC](../build/run-time-library-behavior.md#initializing-extension-dlls)  
  
-   [Inicjowanie MFC dll](../build/run-time-library-behavior.md#initializing-regular-dlls)  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [Biblioteki DLL rozszerzeń MFC](../build/extension-dlls.md)  
  
-   [Zwykłe biblioteki DLL MFC połączone statycznie z MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [Zwykłe biblioteki DLL MFC połączone dynamicznie z MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Używanie MFC jako części biblioteki DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
  
-   [Wersja biblioteki DLL MFC](../mfc/tn033-dll-version-of-mfc.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki DLL rozszerzeń MFC](../build/extension-dlls.md)