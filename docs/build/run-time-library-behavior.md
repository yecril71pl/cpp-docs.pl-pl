---
title: Zachowanie biblioteki wykonawczej DLL i Visual C++
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
ms.openlocfilehash: 2f2ffb13e6a80b144298bbf8cd76b5666a10b4dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335661"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>Zachowanie biblioteki wykonawczej DLL i Visual C++

Podczas tworzenia biblioteki dynamicznej (DLL) przy użyciu programu Visual Studio, domyślnie konsolidator zawiera bibliotekę wykonawczą programu Visual C++ (VCRuntime). VCRuntime zawiera kod wymagany do zainicjowania i zakończenia pliku wykonywalnego C/C++. Po połączeniu z biblioteką DLL, kod VCRuntime zapewnia wewnętrzną funkcję punktu wejścia biblioteki DLL, `_DllMainCRTStartup` która obsługuje komunikaty systemu operacyjnego Windows do biblioteki DLL, aby dołączyć lub odłączyć z procesu lub wątku. Funkcja `_DllMainCRTStartup` wykonuje podstawowe zadania, takie jak konfiguracja zabezpieczeń buforu stosu, inicjowanie i zakończenie biblioteki wykonywania C (CRT) oraz wywołania konstruktorów i destruktorów obiektów statycznych i globalnych. `_DllMainCRTStartup`również wywołuje funkcje haka dla innych bibliotek, takich jak WinRT, MFC i ATL do wykonywania własnych inicjowania i zakończenia. Bez tej inicjalizacji CRT i innych bibliotek, a także zmiennych statycznych, pozostanie w stanie niezainicjowanym. Te same procedury inicjowania wewnętrznego i zakończenia VCRuntime są wywoływane niezależnie od tego, czy biblioteka DLL używa statycznie połączonego crt lub dynamicznie połączonej biblioteki DLL CRT.

## <a name="default-dll-entry-point-_dllmaincrtstartup"></a>Domyślny punkt wejścia biblioteki DLL _DllMainCRTStartup

W systemie Windows wszystkie biblioteki DLL mogą zawierać `DllMain`opcjonalną funkcję punktu wejścia, zwykle nazywaną , która jest wywoływana zarówno do inicjowania, jak i zakończenia. Daje to możliwość przydzielenia lub zwolnienia dodatkowych zasobów w razie potrzeby. System Windows wywołuje funkcję punktu wejścia w czterech sytuacjach: proces dołączania, odłączania procesu, dołączania wątku i odłączania wątku. Gdy biblioteka DLL jest ładowana do przestrzeni adresowej procesu, gdy aplikacja, która go używa jest ładowana lub gdy aplikacja żąda biblioteki DLL w czasie wykonywania, system operacyjny tworzy oddzielną kopię danych DLL. Nazywa się to *procesem dołączania*. *Dołączanie wątku* występuje, gdy proces DLL jest ładowany w tworzy nowy wątek. *Odłączyć wątku* występuje, gdy wątek kończy się i *odłączyć proces* jest, gdy biblioteka DLL nie jest już wymagane i jest zwalniany przez aplikację. System operacyjny wykonuje oddzielne wywołanie punktu wejścia biblioteki DLL dla każdego z tych zdarzeń, przekazując argument *przyczyny* dla każdego typu zdarzenia. Na przykład system operacyjny `DLL_PROCESS_ATTACH` wysyła jako argument *przyczyny* do przyłączenia procesu sygnału.

Biblioteka VCRuntime udostępnia funkcję punktu `_DllMainCRTStartup` wejścia wywoływaną do obsługi domyślnych operacji inicjowania i zakończenia. Podczas dołączania `_DllMainCRTStartup` procesu funkcja konfiguruje kontrole zabezpieczeń buforu, inicjuje CRT i inne biblioteki, inicjuje informacje o typie w czasie wykonywania, inicjuje i wywołuje konstruktory danych statycznych i nielokalnych, inicjuje magazyn lokalny wątku, zwiększa wewnętrzny licznik statyczny dla każdego dołączania, a następnie wywołuje dostarczone przez `DllMain`użytkownika lub bibliotekę . Podczas odłączenia procesu funkcja przechodzi przez te kroki w odwrotnej kolejności. Wywołuje, `DllMain`zmniejsza licznik wewnętrzny, wywołuje destruktory, wywołuje funkcje `atexit` zakończenia CRT i zarejestrowanych funkcji i powiadamia inne biblioteki zakończenia. Gdy licznik załączników zostanie zerem, funkcja zwraca wartość `FALSE` wskazującą systemowi Windows, że biblioteka DLL może zostać zwolniona. Funkcja `_DllMainCRTStartup` jest również wywoływana podczas dołączania gwintu i odłączania gwintu. W takich przypadkach kod VCRuntime nie ma dodatkowej inicjowania `DllMain` lub zakończenia na własną rękę i po prostu wywołuje przekazać wiadomość wzdłuż. Jeśli `DllMain` `FALSE` zwraca z procesu dołączyć, `_DllMainCRTStartup` `DllMain` sygnalizacji `DLL_PROCESS_DETACH` awarii, wywołuje ponownie i przechodzi jako argument *przyczyny,* a następnie przechodzi przez resztę procesu zakończenia.

Podczas tworzenia bibliotek DLL w programie `_DllMainCRTStartup` Visual Studio domyślny punkt wejścia dostarczony przez VCRuntime jest połączony automatycznie. Nie trzeba określać funkcji punktu wejścia dla biblioteki DLL przy użyciu opcji konsolidatora [/ENTRY (entry point symbol).](reference/entry-entry-point-symbol.md)

> [!NOTE]
> Chociaż jest możliwe, aby określić inną funkcję punktu wejścia dla biblioteki DLL przy użyciu /ENTRY: konsolidator opcji, `_DllMainCRTStartup` nie zaleca się, ponieważ funkcja punktu wejścia musiałby powielać wszystko, co robi, w tej samej kolejności. VCRuntime udostępnia funkcje, które umożliwiają duplikowanie jego zachowania. Na przykład można wywołać [__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md) natychmiast przy dołączaniu procesu do obsługi [/GS (sprawdzanie zabezpieczeń buforu)](reference/gs-buffer-security-check.md) opcja sprawdzania buforu. Można wywołać `_CRT_INIT` funkcję, przekazując te same parametry co funkcję punktu wejścia, aby wykonać pozostałe funkcje inicjowania biblioteki DLL lub zakończenia.

<a name="initializing-a-dll"></a>

## <a name="initialize-a-dll"></a>Inicjowanie biblioteki DLL

Biblioteka DLL może mieć kod inicjowania, który musi zostać wykonany po załadowaniu biblioteki DLL. Aby wykonać własne funkcje inicjowania i `_DllMainCRTStartup` zakończenia biblioteki `DllMain` DLL, wywołuje funkcję o nazwie, którą można podać. Musi `DllMain` mieć podpis wymagany dla punktu wejścia biblioteki DLL. Domyślna funkcja `_DllMainCRTStartup` punktu `DllMain` wejścia wywołuje przy użyciu tych samych parametrów przekazanych przez system Windows. Domyślnie, jeśli nie podasz `DllMain` funkcji, Visual Studio zapewnia jeden dla `_DllMainCRTStartup` Ciebie i łączy go w tak, że zawsze ma coś do wywołania. Oznacza to, że jeśli nie trzeba inicjować biblioteki DLL, nie ma nic specjalnego, co musisz zrobić podczas tworzenia biblioteki DLL.

Jest to podpis `DllMain`używany do:

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```

Niektóre biblioteki `DllMain` zawijają tę funkcję. Na przykład w zwykłej biblioteki DLL MFC zaimplementuj `CWinApp` funkcje obiektu `InitInstance` i `ExitInstance` elementu członkowskiego do wykonywania inicjowania i zakończenia wymagane przez bibliotekę DLL. Aby uzyskać więcej informacji, zobacz [inicjowanie regularnych bibliotek DLL MFC](#initializing-regular-dlls) sekcji.

> [!WARNING]
> Istnieją znaczne ograniczenia dotyczące tego, co można bezpiecznie zrobić w punkcie wejścia biblioteki DLL. Zobacz [Ogólne najlepsze wskazówki](/windows/win32/Dlls/dynamic-link-library-best-practices) dotyczące określonych interfejsów API `DllMain`systemu Windows, które są niebezpieczne do wywołania . Jeśli potrzebujesz niczego, ale najprostsze inicjowanie następnie zrobić to w funkcji inicjowania dla biblioteki DLL. Można wymagać od aplikacji do `DllMain` wywołania funkcji inicjowania po uruchomieniu i przed wywołaniem innych funkcji w dll.

<a name="initializing-non-mfc-dlls"></a>

### <a name="initialize-ordinary-non-mfc-dlls"></a>Inicjowanie zwykłych bibliotek DLL (innych niż MFC)

Aby wykonać własną inicjalizację zwykłych bibliotek DLL (innych niż MFC), które używają punktu wejścia dostarczonego przez `_DllMainCRTStartup` VCRuntime, kod źródłowy biblioteki DLL musi zawierać funkcję o nazwie `DllMain`. Poniższy kod przedstawia podstawowy szkielet pokazujący, jak może wyglądać definicja: `DllMain`

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
> Starsza dokumentacja zestawu SDK systemu Windows mówi, że rzeczywista nazwa funkcji punktu wejścia biblioteki DLL musi być określona w wierszu polecenia konsolidatora z opcją /ENTRY. W programie Visual Studio nie trzeba używać opcji /ENTRY, jeśli nazwa `DllMain`funkcji punktu wejścia jest . W rzeczywistości jeśli używasz /ENTRY opcji i nazwę funkcji `DllMain`punktu wejścia coś innego niż , CRT nie zostanie zainicjowany poprawnie, `_DllMainCRTStartup` chyba że funkcja punktu wejścia sprawia, że te same wywołania inicjowania, który sprawia, że.

<a name="initializing-regular-dlls"></a>

### <a name="initialize-regular-mfc-dlls"></a>Inicjowanie zwykłych bibliotek DLL MFC

Ponieważ zwykłe biblioteki DLL `CWinApp` MFC mają obiekt, powinny wykonywać swoje zadania inicjowania i `InitInstance` `ExitInstance` zakończenia w tej samej `CWinApp`lokalizacji co aplikacja MFC: w funkcjach i elementach członkowskich klasy pochodnej biblioteki DLL. Ponieważ MFC `DllMain` zapewnia funkcję, `_DllMainCRTStartup` która `DLL_PROCESS_ATTACH` `DLL_PROCESS_DETACH`jest wywoływana przez `DllMain` for i , nie należy pisać własną funkcję. Funkcja dostarczona `DllMain` mfc `InitInstance` wywołuje, gdy biblioteka `ExitInstance` DLL jest ładowany i wywołuje przed dll jest zwalniany.

Regularne biblioteki DLL MFC można śledzić wiele wątków, wywołując [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) i [TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue) w jego `InitInstance` funkcji. Te funkcje umożliwiają DLL do śledzenia danych specyficznych dla wątku.

W zwykłej biblioteki DLL MFC, która dynamicznie łączy się z MFC, jeśli używasz dowolnego MFC OLE, MFC Database (lub DAO) lub MFC Sockets wsparcia, odpowiednio, debugowania DLL rozszerzenie MFC biblioteki DCO*wersja*D.dll,*MFCD wersja*D.dll i*MFCN wersja*D.dll (gdzie *wersja* jest numer wersji) są połączone automatycznie. Należy wywołać jedną z następujących wstępnie zdefiniowanych funkcji inicjowania dla każdej z tych bibliotek DLL, których używasz w zwykłej biblioteki `CWinApp::InitInstance`DLL MFC.

|Typ obsługi MFC|Funkcja inicjowania do wywołania|
|-------------------------|-------------------------------------|
|MFC OLE *(wersja*MFCO D.dll)|`AfxOleInitModule`|
|Baza danych MFC *(wersja*MFCD D.dll)|`AfxDbInitModule`|
|Gniazda MFC *(wersja*MFCN D.dll)|`AfxNetInitModule`|

<a name="initializing-extension-dlls"></a>

### <a name="initialize-mfc-extension-dlls"></a>Inicjowanie bibliotek DLL rozszerzenia MFC

Ponieważ biblioteki DLL rozszerzenia MFC nie mają obiektu pochodnego `CWinApp`(podobnie jak zwykłe biblioteki DLL MFC), należy dodać kod inicjowania i zakończenia do `DllMain` funkcji, którą generuje Kreator bibliotek DLL MFC.

Kreator udostępnia następujący kod bibliotek DLL rozszerzenia MFC. W kodzie `PROJNAME` jest symbolem zastępczym dla nazwy projektu.

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

Tworzenie nowego `CDynLinkLibrary` obiektu podczas inicjowania umożliwia DLL `CRuntimeClass` rozszerzenia MFC do eksportowania obiektów lub zasobów do aplikacji klienckiej.

Jeśli zamierzasz użyć biblioteki DLL rozszerzenia MFC z co najmniej jednej zwykłej bibliotek dll `CDynLinkLibrary` MFC, należy wyeksportować funkcję inicjowania, która tworzy obiekt. Ta funkcja musi być wywoływana z każdej zwykłej bibliotek DLL MFC, które używają biblioteki DLL rozszerzenia MFC. Odpowiednie miejsce do wywołania tej funkcji `InitInstance` inicjowania znajduje się w `CWinApp`funkcji członkowskiej zwykłego obiektu pochodnego biblioteki DLL MFC przed użyciem jakichkolwiek eksportowanych klas lub funkcji DLL rozszerzenia MFC.

W `DllMain` kreatorze MLL, który generuje Kreatora `AfxInitExtensionModule` biblioteki DLL MFC,`CRuntimeClass` wywołanie przechwytuje klasy wykonywania modułu`COleObjectFactory` (struktury) oraz `CDynLinkLibrary` jego fabryki obiektów (obiekty) do użycia podczas tworzenia obiektu. Należy sprawdzić wartość zwracaną `AfxInitExtensionModule`; jeśli zwracana jest `AfxInitExtensionModule`wartość zero z `DllMain` , zwraca zero z funkcji.

Jeśli biblioteka DLL rozszerzenia MFC będzie jawnie połączona z `AfxLoadLibrary` plikiem wykonywalnym (co `AfxTermExtensionModule` `DLL_PROCESS_DETACH`oznacza wywołania wykonywalne do łącza do biblioteki DLL), należy dodać wywołanie na . Ta funkcja umożliwia MFC oczyścić bibliotekę DLL rozszerzenia MFC, gdy każdy proces odłącza się od biblioteki DLL rozszerzenia MFC `AfxFreeLibrary` (co się dzieje, gdy proces kończy działanie lub gdy biblioteka DLL jest zwalniana w wyniku wywołania). Jeśli biblioteka DLL rozszerzenia MFC będzie niejawnie `AfxTermExtensionModule` połączony z aplikacją, wywołanie nie jest konieczne.

Aplikacje, które jawnie łączą się z `AfxTermExtensionModule` bibliotekami DLL rozszerzenia MFC, muszą wywoływać podczas zwalniania biblioteki DLL. Powinny one `AfxLoadLibrary` również `AfxFreeLibrary` używać i (zamiast funkcji `LoadLibrary` `FreeLibrary`Win32 i), jeśli aplikacja używa wielu wątków. Przy `AfxLoadLibrary` `AfxFreeLibrary` użyciu i zapewnia, że kod uruchamiania i zamykania, który jest wykonywany, gdy biblioteka DLL rozszerzenia MFC jest ładowany i zwalniane nie powoduje uszkodzenia globalnego stanu MFC.

Ponieważ mfcx0.dll jest w pełni `DllMain` zainicjowany przez czas jest wywoływany, `DllMain` można przydzielić pamięć i wywołać funkcje MFC w ramach (w przeciwieństwie do 16-bitowej wersji MFC).

DLL rozszerzenia można zająć wielowątkowość, `DLL_THREAD_DETACH` obsługując `DllMain` `DLL_THREAD_ATTACH` i przypadków w funkcji. Przypadki te są `DllMain` przekazywane do gdy wątki dołączyć i odłączyć od biblioteki DLL. Wywołanie [TlsAlloc,](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) gdy biblioteka DLL jest dołączanie umożliwia DLL do obsługi indeksów magazynu lokalnego wątku (TLS) dla każdego wątku dołączonego do biblioteki DLL.

Należy zauważyć, że plik nagłówka Afxdllx.h zawiera specjalne definicje struktur używanych w `AFX_EXTENSION_MODULE` `CDynLinkLibrary`bibliotekach DLL rozszerzenia MFC, takich jak definicja i . Należy dołączyć ten plik nagłówka w dll rozszerzenia MFC.

> [!NOTE]
> Ważne jest, aby nie definiować ani `_AFX_NO_XXX` nie definiuj żadnych makr w *pch.h* (*stdafx.h* w programie Visual Studio 2017 i wcześniejszych). Te makra istnieją tylko w celu sprawdzenia, czy określona platforma docelowa obsługuje tę funkcję, czy nie. Można napisać program, aby sprawdzić te makra (na `#ifndef _AFX_NO_OLE_SUPPORT`przykład), ale program nigdy nie powinien definiować lub undefine tych makr.

Przykładowa funkcja inicjowania obsługująca wielowątkowość jest zawarta w [użyciu lokalnego magazynu wątku w bibliotece łącza dynamicznego](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library) w zestawie Windows SDK. Należy zauważyć, że przykład zawiera `LibMain`funkcję punktu wejścia o `DllMain` nazwie , ale należy nazwać tę funkcję, tak aby działała z bibliotekami w czasie wykonywania MFC i C.

## <a name="see-also"></a>Zobacz też

[Tworzenie bibliotek DLL języka C/C++ w programie Visual Studio](dlls-in-visual-cpp.md)<br/>
[Punkt wejścia DllMain](/windows/win32/Dlls/dllmain)<br/>
[Najważniejsze wskazówki dotyczące biblioteki łączy dynamicznych](/windows/win32/Dlls/dynamic-link-library-best-practices)
