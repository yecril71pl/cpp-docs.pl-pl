---
title: Biblioteki DLL i C++ zachowanie biblioteki w czasie wykonywania wizualizacji
ms.date: 08/19/2019
f1_keywords:
- _DllMainCRTStartup
- CRT_INIT
helpviewer_keywords:
- DLLs [C++], entry point function
- process detach [C++]
- process attach [C++]
- DLLs [C++], run-time library behavior
- DllMain function
- _CRT_INIT macro
- _DllMainCRTStartup method
- run-time [C++], DLL startup sequence
- DLLs [C++], startup sequence
ms.assetid: e06f24ab-6ca5-44ef-9857-aed0c6f049f2
ms.openlocfilehash: 572a0ba70c1ba2d46d2d9fd6d8ac543a77bbbc01
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630369"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>Biblioteki DLL i C++ zachowanie biblioteki w czasie wykonywania wizualizacji

Podczas tworzenia biblioteki dołączanej dynamicznie (DLL) za pomocą programu Visual Studio, konsolidator obejmuje bibliotekę wykonawczą (VCRuntime) C++ wizualizacji. VCRuntime zawiera kod wymagany do zainicjowania i zakończenia pliku wykonywalnegoC++ C/. W przypadku połączenia z biblioteką DLL kod VCRuntime zawiera wewnętrzną funkcję `_DllMainCRTStartup` punktu wejścia biblioteki DLL, która obsługuje komunikaty systemu operacyjnego Windows w bibliotece DLL w celu dołączenia lub odłączenia od procesu lub wątku. `_DllMainCRTStartup` Funkcja wykonuje podstawowe zadania, takie jak Konfiguracja zabezpieczeń buforu stosu, inicjowanie i kończenie biblioteki uruchomieniowej języka C (CRT) oraz wywołania konstruktorów i destruktorów dla obiektów statycznych i globalnych. `_DllMainCRTStartup`Program wywołuje również funkcje haka dla innych bibliotek, takich jak WinRT, MFC i ATL, do wykonywania własnych operacji inicjowania i kończenia. Bez tego inicjalizacji CRT i inne biblioteki, a także zmienne statyczne, zostałyby pozostawione w stanie niezainicjowanym. Te same VCRuntime wewnętrzne procedury inicjowania i zakończenia są wywoływane, czy biblioteka DLL korzysta ze statycznie połączonej CRT czy dynamicznie połączonej biblioteki DLL.

## <a name="default-dll-entry-point-_dllmaincrtstartup"></a>Domyślna _DllMainCRTStartup punktu wejścia biblioteki DLL

W systemie Windows wszystkie biblioteki DLL mogą zawierać opcjonalną funkcję punktu wejścia, zazwyczaj wywoływaną `DllMain`, która jest wywoływana dla inicjalizacji i zakończenia. Pozwala to na przydzielenie lub zwolnienie dodatkowych zasobów zgodnie z wymaganiami. System Windows wywołuje funkcję punktu wejścia w czterech sytuacjach: dołączanie procesu, odłączanie procesu, dołączanie wątku i odłączanie wątku. Podczas ładowania biblioteki DLL do przestrzeni adresowej procesu, gdy aplikacja, która korzysta z niej jest załadowana, lub gdy aplikacja żąda biblioteki DLL w czasie wykonywania, system operacyjny tworzy oddzielną kopię danych biblioteki DLL. Jest to tzw. *proces Attach*. Dołączanie do *wątku* występuje, gdy proces, w którym załadowano plik dll, tworzy nowy wątek. *Odłączanie wątku* występuje po zakończeniu wątku, a *odłączenie procesu* polega na tym, że biblioteka DLL nie jest już wymagana i jest dostarczana przez aplikację. System operacyjny wykonuje oddzielne wywołanie do punktu wejścia biblioteki DLL dla każdego z tych zdarzeń, przekazując argument *przyczyny* dla każdego typu zdarzenia. Na przykład, system operacyjny wysyła `DLL_PROCESS_ATTACH` jako argument *przyczyny* do dołączania do procesu sygnału.

Biblioteka VCRuntime zapewnia funkcję punktu wejścia o nazwie `_DllMainCRTStartup` do obsługi domyślnych operacji inicjowania i kończenia. W przypadku dołączania `_DllMainCRTStartup` do procesu funkcja konfiguruje sprawdzanie zabezpieczeń buforów, inicjuje środowisko CRT i inne biblioteki, inicjuje informacje o typie w czasie wykonywania, inicjuje i wywołuje konstruktory dla danych statycznych i nielokalnych, inicjuje lokalne magazyny wątków , zwiększa wewnętrzny licznik statyczny dla każdego dołączania, a następnie wywołuje dostarczone `DllMain`przez użytkownika lub biblioteki. Po odłączeniu do procesu funkcja przechodzi przez te kroki wstecz. Wywołuje `DllMain`, zmniejsza wewnętrzny licznik, wywołuje destruktory, wywołuje funkcje zakończenia CRT i zarejestrowane `atexit` funkcje i powiadamia wszystkie inne biblioteki o zakończeniu. Gdy licznik załączników przechodzi do zera, funkcja zwraca `FALSE` do systemu Windows, że biblioteka DLL może zostać zwolniona. `_DllMainCRTStartup` Funkcja jest również wywoływana podczas dołączania wątku i odłączania wątku. W takich przypadkach kod VCRuntime nie ma żadnych dodatkowych inicjalizacji ani nie kończy się samodzielnie, a jedynie wywołuje `DllMain` do przekazywania wiadomości. Jeśli `DllMain` funkcja `FALSE` zwraca z dołączania do procesu, `_DllMainCRTStartup` sygnalizuje awarię `DLL_PROCESS_DETACH` , wywołuje `DllMain` ponownie i przekazuje jako argument *przyczyny* , następnie przechodzi przez resztę procesu zakończenia.

Podczas kompilowania bibliotek DLL w programie Visual Studio domyślny punkt `_DllMainCRTStartup` wejścia dostarczony przez VCRuntime jest automatycznie łączony. Nie trzeba określać funkcji punktu wejścia dla biblioteki DLL przy użyciu opcji konsolidatora [/entry (symbol punktu wejścia)](reference/entry-entry-point-symbol.md) .

> [!NOTE]
> Chociaż istnieje możliwość określenia innej funkcji punktu wejścia dla biblioteki DLL przy użyciu opcji/entry: konsolidatora, firma Microsoft nie zaleca tego, ponieważ funkcja punktu wejścia musiałaby zduplikować wszystkie elementy, które `_DllMainCRTStartup` w tej samej kolejności. VCRuntime udostępnia funkcje, które umożliwiają duplikowanie zachowania. Można na przykład wywołać [__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md) natychmiast po dołączeniu do procesu, aby obsługiwał opcję sprawdzania bufora [(sprawdzanie zabezpieczeń bufora)](reference/gs-buffer-security-check.md) . Można wywołać `_CRT_INIT` funkcję, przekazując te same parametry co funkcja punktu wejścia, aby wykonać pozostałe funkcje inicjacji lub zakończenia biblioteki DLL.

<a name="initializing-a-dll"></a>

## <a name="initialize-a-dll"></a>Inicjowanie biblioteki DLL

Biblioteka DLL może mieć kod inicjujący, który musi zostać wykonany w przypadku załadowania biblioteki DLL. Aby można było wykonywać własne funkcje inicjowania i kończenia biblioteki DLL, program `_DllMainCRTStartup` wywołuje funkcję o nazwie `DllMain` , którą można podać. `DllMain` Wymagany jest podpis dla punktu wejścia biblioteki DLL. Domyślne wywołania `_DllMainCRTStartup` `DllMain` funkcji punktu wejścia przy użyciu tych samych parametrów, które są przesyłane przez system Windows. Domyślnie, jeśli nie podasz `DllMain` funkcji, program Visual Studio udostępnia ją dla Ciebie i łączy ją w `_DllMainCRTStartup` taki sposób, aby zawsze miał coś do wywołania. Oznacza to, że jeśli nie trzeba inicjować biblioteki DLL, nie ma żadnych specjalnych, które należy wykonać podczas kompilowania biblioteki DLL.

Sygnatura użyta dla `DllMain`:

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```

Niektóre biblioteki zawijają `DllMain` tę funkcję. Na przykład w zwykłej bibliotece MFC DLL należy zaimplementować `CWinApp` funkcje `InitInstance` obiektu i `ExitInstance` elementu członkowskiego, aby wykonać inicjalizację i zakończenie wymagane przez bibliotekę DLL. Aby uzyskać więcej informacji, zobacz sekcję [Inicjowanie zwykłych BIBLIOTEK MFC DLL](#initializing-regular-dlls) .

> [!WARNING]
> Istnieją znaczne ograniczenia dotyczące tego, co można bezpiecznie zrobić w punkcie wejścia biblioteki DLL. Zobacz [Ogólne najlepsze rozwiązania](/windows/win32/Dlls/dynamic-link-library-best-practices) dotyczące konkretnych interfejsów API systemu Windows, które nie są `DllMain`bezpieczne do wywołania w programie. Jeśli potrzebujesz wszystkiego, ale najprostsza Inicjalizacja, zrób to w funkcji inicjacji biblioteki DLL. Można wymagać, aby aplikacje wywoływały funkcję inicjującą `DllMain` po uruchomieniu i przed wywołaniem innych funkcji w bibliotece DLL.

<a name="initializing-non-mfc-dlls"></a>

### <a name="initialize-ordinary-non-mfc-dlls"></a>Inicjowanie zwykłych bibliotek DLL (innych niż MFC)

Aby wykonać własne inicjalizacje w zwykłych bibliotekach DLL (innych niż MFC), które używają punktu `_DllMainCRTStartup` wejścia dostarczonego przez VCRuntime, kod źródłowy biblioteki DLL musi zawierać `DllMain`funkcję o nazwie. Poniższy kod przedstawia podstawowy szkielet pokazujący, jak wygląda definicja `DllMain` może wyglądać następująco:

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved)  // reserved
{
    // Perform actions based on the reason for calling.
    switch (reason)
    {
    case DLL_PROCESS_ATTACH:
        // Initialize once for each new process.
        // Return FALSE to fail DLL load.
        break;

    case DLL_THREAD_ATTACH:
        // Do thread-specific initialization.
        break;

    case DLL_THREAD_DETACH:
        // Do thread-specific cleanup.
        break;

    case DLL_PROCESS_DETACH:
        // Perform any necessary cleanup.
        break;
    }
    return TRUE;  // Successful DLL_PROCESS_ATTACH.
}
```

> [!NOTE]
> W starszej dokumentacji Windows SDK należy określić rzeczywistą nazwę funkcji punktu wejścia biblioteki DLL w wierszu polecenia konsolidatora z opcją/ENTRY. W programie Visual Studio nie trzeba używać opcji/ENTRY, jeśli nazwa funkcji punktu wejścia to `DllMain`. W rzeczywistości, jeśli używasz opcji/entry i nazwij funkcję punktu wejścia inną niż `DllMain`, CRT nie zostanie prawidłowo zainicjowany, chyba że funkcja punktu wejścia wykonuje te same `_DllMainCRTStartup` wywołania inicjacji.

<a name="initializing-regular-dlls"></a>

### <a name="initialize-regular-mfc-dlls"></a>Inicjowanie zwykłych bibliotek DLL MFC

Ze `CWinApp` względu na to, że regularne biblioteki MFC DLL mają obiekt, powinny wykonywać zadania inicjowania i kończenia w tej samej lokalizacji co aplikacja MFC `InitInstance` : `ExitInstance` w programie i funkcji członkowskich klasy `CWinApp`pochodnej biblioteki DLL określonej. Ponieważ `DllMain` MFC udostępnia funkcję, która jest wywoływana przez `_DllMainCRTStartup` dla `DLL_PROCESS_ATTACH` i `DLL_PROCESS_DETACH`, nie należy pisać własnej `DllMain` funkcji. Funkcja udostępniona `DllMain` przez MFC jest wywoływana `InitInstance` podczas ładowania biblioteki DLL i wywołuje `ExitInstance` ją przed wyładowaniem biblioteki DLL.

Zwykła Biblioteka MFC DLL może śledzić wiele wątków, wywołując [Funkcja TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) i [TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue) w `InitInstance` funkcji. Te funkcje umożliwiają bibliotece DLL śledzenie danych specyficznych dla wątku.

W zwykłej bibliotece MFC DLL, która dynamicznie łączy się z MFC, jeśli używasz dowolnej biblioteki MFC OLE, MFC Database (lub DAO) lub MFC Sockets support odpowiednio, debugowanie MFC Extension dll MFCO*wersja*d. dll, MFCD*wersja*d. dll i MFCN*wersja*d. dll ( gdzie *wersja* jest numerem wersji) jest automatycznie łączona. Musisz wywołać jedną z następujących wstępnie zdefiniowanych funkcji inicjujących dla każdej z tych bibliotek DLL, które są używane w zwykłych bibliotekach DLL `CWinApp::InitInstance`MFC.

|Typ obsługi MFC|Funkcja inicjacji do wywołania|
|-------------------------|-------------------------------------|
|MFC OLE (MFCO*wersja*D. dll)|`AfxOleInitModule`|
|Baza danych MFC (MFCD*wersja*D. dll)|`AfxDbInitModule`|
|Gniazda MFC (MFCN*wersja*D. dll)|`AfxNetInitModule`|

<a name="initializing-extension-dlls"></a>

### <a name="initialize-mfc-extension-dlls"></a>Inicjuj biblioteki DLL rozszerzenia MFC

Ponieważ biblioteki DLL rozszerzenia MFC nie mają `CWinApp`obiektu pochodnego (jako zwykłych bibliotek DLL MFC), należy dodać kod inicjalizacji i zakończenia `DllMain` do funkcji generowanej przez kreatora MFC DLL.

Kreator udostępnia Poniższy kod dla bibliotek DLL rozszerzeń MFC. W kodzie, `PROJNAME` jest symbolem zastępczym dla nazwy projektu.

```cpp
#include "pch.h" // For Visual Studio 2017 and earlier, use "stdafx.h"
#include <afxdllx.h>

#ifdef _DEBUG
#define new DEBUG_NEW
#undef THIS_FILE
static char THIS_FILE[] = __FILE__;
#endif
static AFX_EXTENSION_MODULE PROJNAMEDLL = { NULL, NULL };

extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
   if (dwReason == DLL_PROCESS_ATTACH)
   {
      TRACE0("PROJNAME.DLL Initializing!\n");

      // MFC extension DLL one-time initialization
      AfxInitExtensionModule(PROJNAMEDLL,
                                 hInstance);

      // Insert this DLL into the resource chain
      new CDynLinkLibrary(Dll3DLL);
   }
   else if (dwReason == DLL_PROCESS_DETACH)
   {
      TRACE0("PROJNAME.DLL Terminating!\n");
   }
   return 1;   // ok
}
```

Utworzenie nowego `CDynLinkLibrary` obiektu podczas inicjowania pozwala na eksportowanie `CRuntimeClass` obiektów lub zasobów do aplikacji klienckiej biblioteki DLL rozszerzenia MFC.

Jeśli biblioteka DLL rozszerzenia MFC ma być używana z co najmniej jednej zwykłej biblioteki DLL MFC, należy wyeksportować funkcję inicjującą, która tworzy `CDynLinkLibrary` obiekt. Ta funkcja musi być wywołana z każdej zwykłej biblioteki DLL MFC, która używa biblioteki MFC DLL. Odpowiednie miejsce do wywołania tej funkcji inicjującej znajduje się w `InitInstance` funkcji członkowskiej regularnego obiektu pochodnego `CWinApp`biblioteki MFC DLL przed użyciem dowolnej z wyeksportowanych klas lub funkcji biblioteki DLL rozszerzenia MFC.

`CRuntimeClass` `AfxInitExtensionModule` `CDynLinkLibrary` `COleObjectFactory` W wyniku wygenerowania kreatora biblioteki MFC DLL wywołanie przechwytuje klasy uruchomieniowe modułu (struktury), a także jego fabryki obiektów do użycia podczas tworzenia obiektu. `DllMain` Należy sprawdzić wartość zwracaną przez `AfxInitExtensionModule`; Jeśli zwracana jest wartość zerowa z `AfxInitExtensionModule` `DllMain` , zwraca zero z funkcji.

Jeśli biblioteka DLL rozszerzenia MFC zostanie jawnie połączona z plikiem wykonywalnym (oznacza to, `AfxLoadLibrary` że pliki wykonywalne są wywoływane w celu połączenia z biblioteką DLL `AfxTermExtensionModule` ) `DLL_PROCESS_DETACH`, należy dodać wywołanie do usługi. Ta funkcja umożliwia MFC Oczyszczanie biblioteki DLL rozszerzenia MFC, gdy każdy proces odłącza się od biblioteki DLL rozszerzenia MFC (co się stanie w przypadku zakończenia procesu lub gdy biblioteka DLL zostanie zwolniona w wyniku `AfxFreeLibrary` wywołania). Jeśli biblioteka DLL rozszerzenia MFC będzie niejawnie łączona z aplikacją, wywołanie `AfxTermExtensionModule` nie jest konieczne.

Aplikacje, które jawnie łączą się z bibliotekami `AfxTermExtensionModule` DLL rozszerzenia MFC, muszą być wywoływane podczas zwalniania biblioteki DLL. Należy także używać `AfxLoadLibrary` i `AfxFreeLibrary` (zamiast funkcji `LoadLibrary` Win32 i `FreeLibrary`), jeśli aplikacja używa wielu wątków. Przy `AfxLoadLibrary` użyciu `AfxFreeLibrary` i zapewnia, że kod uruchamiania i zamykania, który jest wykonywany, gdy biblioteka DLL rozszerzenia MFC jest załadowana i zwolniona, nie powoduje uszkodzenia globalnego stanu MFC.

Ponieważ MFCx0. dll jest w pełni inicjowany przez czas `DllMain` , można przydzielić pamięć i wywoływać funkcje MFC w ramach `DllMain` (w przeciwieństwie do 16-bitowej wersji MFC).

Biblioteki DLL rozszerzeń mogą wymagać wielowątkowości przez obsługę `DLL_THREAD_ATTACH` przypadków i `DLL_THREAD_DETACH` w `DllMain` funkcji. Te przypadki są przesyłane do `DllMain` momentu dołączenia wątków i odłączenia ich od biblioteki DLL. Wywołanie [Funkcja TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) , gdy biblioteka DLL jest dołączana, umożliwia biblioteki DLL obsługę indeksów lokalnego magazynu wątków (TLS) dla każdego wątku dołączonego do biblioteki DLL.

Należy zauważyć, że plik nagłówka AFXDLLX. h zawiera specjalne definicje struktur używanych w bibliotekach DLL rozszerzenia MFC, takich jak definicja `AFX_EXTENSION_MODULE` dla `CDynLinkLibrary`i. Należy dołączyć ten plik nagłówka do biblioteki DLL rozszerzenia MFC.

> [!NOTE]
>  Ważne jest, aby nie definiować ani nie definiować żadnych `_AFX_NO_XXX` makr w *PCH. h* (*stdafx. h* w programie Visual Studio 2017 i wcześniejszych). Te makra istnieją tylko w celu sprawdzenia, czy konkretna platforma docelowa obsługuje tę funkcję. Można napisać program, aby sprawdzić te makra (na przykład `#ifndef _AFX_NO_OLE_SUPPORT`), ale program nigdy nie definiuje ani nie definiuje tych makr.

Przykładowa funkcja inicjująca, która obsługuje wielowątkowość, jest dołączana do [użycia lokalnego magazynu wątków w bibliotece dołączanej dynamicznie](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library) w Windows SDK. Należy zauważyć, że przykład zawiera funkcję punktu wejścia o nazwie `LibMain`, ale należy nazwać tę funkcję `DllMain` , aby działała z bibliotekami wykonawczymi MFC i C.

## <a name="see-also"></a>Zobacz także

[Tworzenie C/C++ dll w Visual Studio](dlls-in-visual-cpp.md)<br/>
[Punkt wejścia DllMain](/windows/win32/Dlls/dllmain)<br/>
[Najlepsze rozwiązania dotyczące biblioteki dołączanej dynamicznie](/windows/win32/Dlls/dynamic-link-library-best-practices)
