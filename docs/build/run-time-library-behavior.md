---
title: Biblioteki dll i zachowanie biblioteki wykonawczej języka Visual C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- _DllMainCRTStartup
- CRT_INIT
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce61765a5226a6ff5689cde3a511a12db86aa8f7
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720905"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>Biblioteki dll i zachowanie biblioteki wykonawczej języka Visual C++

Gdy tworzysz biblioteki dołączane dynamicznie (DLL) przy użyciu języka Visual C++ domyślnie konsolidator zawiera Biblioteka środowiska uruchomieniowego Visual C++ (VCRuntime). VCRuntime zawiera kod wymagany do rozpoczęcia i zakończenia wykonywalne języka C/C++. Jeśli połączone do biblioteki DLL, kod VCRuntime zawiera wewnętrzny funkcję punktu wejścia biblioteki DLL o nazwie `_DllMainCRTStartup` obsługująca komunikaty systemu operacyjnego Windows, plik dll, który umożliwia dołączanie do lub odłączyć od procesu i wątku. `_DllMainCRTStartup` Funkcja wykonuje podstawowe zadania, takie jak konfigurowanie C biblioteki wykonawczej (CRT) inicjowanie i kończenie działania zabezpieczeń bufora stosu i wywołuje konstruktory i destruktory dla obiektów globalnych i statycznych. `_DllMainCRTStartup` Ponadto wywołuje funkcje punktów zaczepienia dla innych bibliotek, takich jak WinRT, MFC i ATL, aby wykonać swoje własne inicjowanie i kończenie działania. Bez ten proces inicjowania, CRT i inne biblioteki, a także zmiennych statycznych pozostanie w stanie niezainicjowanym. Ten sam inicjowania wewnętrznego VCRuntime i zakończenie procedury są nazywane czy biblioteka DLL będzie używać CRT połączone statycznie lub dynamicznie połączone DLL CRT.

## <a name="default-dll-entry-point-dllmaincrtstartup"></a>Domyślne _DllMainCRTStartup punkt wejścia biblioteki DLL

W Windows, wszystkie biblioteki dll mogą zawierać funkcji opcjonalnych punktu wejścia, zwykle nazywane `DllMain`, która jest wywołana dla inicjowania i zakończenia. Daje to możliwość alokacji lub zwolnienia dodatkowych zasobów, zgodnie z potrzebami. Windows wywołuje funkcję punktu wejścia w czterech sytuacjach: załączanie procesu, odłączanie procesu, załączanie wątku i odłączanie wątku. Podczas ładowania biblioteki DLL do przestrzeni adresowej procesu po załadowaniu aplikacji, która używa lub gdy aplikacja żąda biblioteki DLL w czasie wykonywania, system operacyjny tworzy oddzielną kopię danych biblioteki DLL. Jest to nazywane *załączanie procesu*. *Załączanie wątku* występuje, gdy proces biblioteki DLL jest ładowany w tworzy nowy wątek. *Odłączanie wątku* występuje, gdy wątek się kończy, i *odłączanie procesu* biblioteki DLL nie jest już wymagane i jest wydane przez aplikację. System operacyjny wywołuje oddzielny punkt wejścia biblioteki DLL dla każdego z tych zdarzeń, przekazując *Przyczyna* argument dla każdego typu zdarzenia. Na przykład system operacyjny wysyła `DLL_PROCESS_ATTACH` jako *Przyczyna* argumentu w celu sygnalizowania, że proces dołączania.

Biblioteka VCRuntime udostępnia funkcję punktu wejścia o nazwie `_DllMainCRTStartup` na obsługę operacji inicjowanie i kończenie działania domyślne. Na temat procesu dołączania, `_DllMainCRTStartup` funkcja konfiguruje sprawdzenia zabezpieczeń buforu, inicjuje CRT i inne biblioteki, inicjuje informacje typu run-time, inicjuje i wywołuje konstruktory danych statycznych i inną niż lokalna, inicjuje lokalny magazyn wątków , zwiększa Licznik wewnętrzny statyczny dla każdego dołączenia, a następnie wywołuje, dostarczone przez użytkownika lub biblioteki- `DllMain`. W procesie odłączania, funkcja przechodzi przez te kroki w odwrotnej kolejności. Wywołuje `DllMain`zmniejsza wewnętrznego licznika wywołuj destruktory, zakończenie wywołania CRT, funkcje i zarejestrowany `atexit` funkcje i powiadamia innych bibliotek, zakończenia. Gdy licznik załącznika zbliża się do zera, funkcja zwraca `FALSE` do wskazania Windows, czy można zwolnić bibliotekę DLL. `_DllMainCRTStartup` Funkcja jest również nazywany podczas wątku Dołączanie i odłączanie wątku. W takich przypadkach nie żadne dodatkowe inicjowania lub zakończenia na swój własny kod VCRuntime i po prostu wywołuje funkcję `DllMain` do przekazywania wiadomości wzdłuż. Jeśli `DllMain` zwraca `FALSE` z procesu dołączania, sygnalizujących niepowodzenie, `_DllMainCRTStartup` wywołania `DllMain` ponownie i przekazuje `DLL_PROCESS_DETACH` jako *Przyczyna* argumentów, następnie przechodzi przez pozostałą część Zakończenie procesu.

Podczas tworzenia biblioteki dll w programie Visual C++, domyślny punkt wejścia `_DllMainCRTStartup` dostarczonych przez VCRuntime jest automatycznie konsolidowana. Nie należy określić funkcję punktu wejścia dla biblioteki DLL przy użyciu [/Entry (symbol punktu wejścia)](../build/reference/entry-entry-point-symbol.md) — opcja konsolidatora.

> [!NOTE]
> Choć jest możliwe określić inną funkcję punktu wejścia dla biblioteki DLL przy użyciu / Entry: — opcja konsolidatora, nie jest zalecane, ponieważ funkcja punktu wejścia będzie już potrzeby duplikowania wszystko, co który `_DllMainCRTStartup` jest w tej samej kolejności. VCRuntime udostępnia funkcje, które pozwalają na zduplikowane jego zachowanie. Na przykład, można wywołać [__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md) natychmiast na temat procesu dołączania do obsługi [/GS (Sprawdzanie zabezpieczeń bufora)](../build/reference/gs-buffer-security-check.md) buforu opcję sprawdzania. Możesz wywołać `_CRT_INIT` funkcję, przekazując te same parametry jako funkcję punktu wejścia do wykonania pozostałej części funkcji DLL inicjowania lub zakończenia.

<a name="initializing-a-dll"></a>

## <a name="initialize-a-dll"></a>Zainicjuj bibliotekę DLL

Biblioteka DLL może być kod inicjujący, który musi być wykonany kiedy DLL się ładuje. Aby wykonać swoje własne inicjowanie i kończenie działania funkcji DLL `_DllMainCRTStartup` wywołuje funkcję o nazwie `DllMain` który można udostępnić. Twoje `DllMain` musi mieć podpis wymagane dla punktu wejścia biblioteki DLL. Funkcja punktu wejścia domyślne `_DllMainCRTStartup` wywołania `DllMain` z tymi samymi parametrami przekazywane przez Windows. Domyślnie, jeśli nie podasz `DllMain` funkcja dostępna w Visual C++ i łączy je w tak, aby `_DllMainCRTStartup` zawsze ma coś do wywołania. Oznacza to, że jeśli nie musisz zainicjować bibliotekę DLL, nie ma specjalne, należy wykonać podczas kompilowania biblioteki DLL.

To jest podpis używany dla `DllMain`:

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```

OPAKOWYWANIE niektóre biblioteki `DllMain` funkcji dla Ciebie. Na przykład w regularnej biblioteki DLL MFC, należy zaimplementować `CWinApp` obiektu `InitInstance` i `ExitInstance` elementów członkowskich do wykonania, inicjowanie i kończenie działania wymagane przez bibliotekę DLL. Aby uzyskać więcej informacji, zobacz [zainicjować zwykłe biblioteki DLL MFC](#initializing-regular-dlls) sekcji.

> [!WARNING]
> Istnieją limity znaczące bezpiecznie jak w punkcie wejścia biblioteki DLL. Zobacz [— najlepsze praktyki ogólne](/windows/desktop/Dlls/dynamic-link-library-best-practices) dla określonych niebezpieczne wywołania interfejsów API w Windows `DllMain`. Jeśli potrzebujesz wszystko, ale następnie najprostszym inicjowania to zrobić w funkcji inicjowania biblioteki dll. Możesz wymagać od aplikacji, aby wywołać funkcję inicjowania po `DllMain` ma uruchamiania i przed ich wywołania innych funkcji w bibliotece DLL.

<a name="initializing-non-mfc-dlls"></a>

### <a name="initialize-ordinary-non-mfc-dlls"></a>Zainicjuj bibliotekę DLL zwykłych (inne niż MFC)

Do wykonywania własnych inicjowania w bibliotekach DLL zwykłych (inne niż MFC), korzystających z dostarczanego VCRuntime `_DllMainCRTStartup` punktu wejścia kodu źródłowego DLL musi zawierać funkcję o nazwie `DllMain`. Poniższy kod przedstawia podstawowy szkielet, jakie definicję Pokazywanie `DllMain` może wyglądać jak:

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
> Ze starszą dokumentacją. zestaw Windows SDK mówi, że rzeczywista nazwa funkcję punktu wejścia biblioteki DLL muszą określać na wiersza polecenia z opcją/Entry konsolidatora. Za pomocą języka Visual C++, nie trzeba korzystać z opcji/Entry, jeśli nazwa funkcji punktu wejścia jest `DllMain`. W rzeczywistości użycie opcji/Entry i nazwę punktu wejścia funkcji coś innego niż `DllMain`, CRT nie uzyskać prawidłowo zainicjowana, chyba że funkcję punktu wejścia dzięki tego samego wywołania inicjowania `_DllMainCRTStartup` sprawia, że.

<a name="initializing-regular-dlls"></a>

### <a name="initialize-regular-mfc-dlls"></a>Zainicjuj regularną bibliotekę DLL MFC

Ponieważ ma zwykłych bibliotekach MFC dll `CWinApp` obiektu powinien wykonują swoje zadania inicjowanie i kończenie działania w tej samej lokalizacji co aplikację MFC: w `InitInstance` i `ExitInstance` funkcji elementów członkowskich, które biblioteki dll `CWinApp`-pochodne Klasa. Ponieważ biblioteka MFC zawiera `DllMain` funkcja, która jest wywoływana przez `_DllMainCRTStartup` dla `DLL_PROCESS_ATTACH` i `DLL_PROCESS_DETACH`, nie należy napisać własny `DllMain` funkcji. MFC — pod warunkiem `DllMain` wywołaniach funkcji `InitInstance` Jeśli biblioteka DLL jest ładowany i wywołuje `ExitInstance` przed biblioteki DLL jest zwalniana.

Zwykłej biblioteki MFC DLL można zachować informacje o wielu wątków, wywołując [TlsAlloc](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsalloc) i [TlsGetValue](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue) w jego `InitInstance` funkcji. Te funkcje umożliwiają biblioteki DLL do śledzenia danych specyficznych wątku.

Regularne biblioteki DLL MFC, która łączy dynamicznie MFC, jeśli używasz dowolnego MFC OLE, baza danych MFC (lub DAO) lub obsługują MFC gniazd, odpowiednio, debugowania rozszerzenia MFC biblioteki DLL MFCO*wersji*D.dll, MFCD*wersji*D.dll i MFCN*wersji*D.dll (gdzie *wersji* jest numer wersji) jest automatycznie konsolidowana. Musi wywołać jedną z następujących funkcji inicjowania wstępnie zdefiniowane dla każdego z tych bibliotek DLL, których używasz w swojej zwykłej biblioteki MFC DLL w `CWinApp::InitInstance`.

|Typ obsługi MFC|Funkcja inicjowania do wywołania|
|-------------------------|-------------------------------------|
|MFC OLE (MFCO*wersji*D.dll)|`AfxOleInitModule`|
|Baza danych MFC (MFCD*wersji*D.dll)|`AfxDbInitModule`|
|MFC gniazd (MFCN*wersji*D.dll)|`AfxNetInitModule`|

<a name="initializing-extension-dlls"></a>

### <a name="initialize-mfc-extension-dlls"></a>Inicjowanie biblioteki DLL rozszerzeń MFC

Ponieważ rozszerzenia MFC biblioteki DLL nie mają `CWinApp`-pochodnych obiektu (podobnie jak zwykłych bibliotekach MFC dll), należy dodać swój kod, inicjowanie i kończenie działania, aby `DllMain` funkcja, która generuje kreatora MFC DLL.

Kreator udostępnia następujący kod do biblioteki DLL rozszerzeń MFC. W kodzie `PROJNAME` jest symbolem zastępczym dla nazwy projektu.

```cpp
#include "stdafx.h"
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

Tworzenie nowego `CDynLinkLibrary` obiekt podczas inicjowania umożliwia rozszerzenia MFC biblioteki DLL, aby wyeksportować `CRuntimeClass` obiektów lub zasobów do aplikacji klienckiej.

Jeśli zamierzasz używać rozszerzenia MFC biblioteki DLL z co najmniej jeden zwykłych bibliotekach MFC dll, należy wyeksportować funkcję inicjowania, która tworzy `CDynLinkLibrary` obiektu. Ta funkcja musi zostać wywołany z każdej zwykłych bibliotekach MFC dll, który za pomocą rozszerzenia MFC biblioteki DLL. Znajduje się w odpowiednim miejscu, aby wywołać tę funkcję inicjowania `InitInstance` funkcji składowej typu MFC DLL regularne `CWinApp`-pochodzi obiekt przed rozpoczęciem korzystania z dowolnego z wyeksportowanej klasy lub funkcje MFC DLL rozszerzenia.

W `DllMain` , generuje kreatora MFC DLL, wywołanie `AfxInitExtensionModule` przechwytuje klasy czasu wykonywania modułu (`CRuntimeClass` struktury) oraz jego fabryk obiektu (`COleObjectFactory` obiektów) do użycia podczas `CDynLinkLibrary` obiekt zostanie utworzony. Należy sprawdzić wartość zwracaną przez `AfxInitExtensionModule`; Jeśli zwracana jest wartość zero z `AfxInitExtensionModule`, zwracają wartość zero z Twojej `DllMain` funkcji.

Jeśli biblioteka DLL rozszerzenia MFC zostanie jawnie połączony plik wykonywalny (co oznacza wykonywalny wywołuje `AfxLoadLibrary` połączyć z biblioteki DLL), należy dodać wywołanie `AfxTermExtensionModule` na `DLL_PROCESS_DETACH`. Dzięki tej funkcji MFC, aby wyczyścić rozszerzenia MFC biblioteki DLL, gdy każdy proces odłączy się od rozszerzenia MFC biblioteki DLL (której się dzieje, gdy kończy proces lub zwalnianie biblioteki DLL na `AfxFreeLibrary` wywołania). Jeśli biblioteka DLL rozszerzenia MFC zostaną połączone niejawnie aplikacji wywołanie `AfxTermExtensionModule` nie jest konieczne.

Aplikacje, które jawnie wywołać łącze do biblioteki DLL rozszerzeń MFC `AfxTermExtensionModule` podczas zwalnianie biblioteki DLL. Należy również użyć `AfxLoadLibrary` i `AfxFreeLibrary` (zamiast funkcji Win32 `LoadLibrary` i `FreeLibrary`) Jeśli aplikacja korzysta z wielu wątków. Za pomocą `AfxLoadLibrary` i `AfxFreeLibrary` zapewnia, że kod uruchamiania i zamykania, który wykonuje, gdy rozszerzenia MFC biblioteki DLL jest ładowany i zwolnione nie doprowadzić do uszkodzenia globalne MFC.

Ponieważ MFCx0.dll jest w pełni zainicjowany przez czas `DllMain` jest wywoływana, można przydzielić pamięci i wywoływać funkcje MFC w ramach `DllMain` (w przeciwieństwie do 16-bitową wersję MFC).

Biblioteki DLL rozszerzeń zająć się wielowątkowość obsługi `DLL_THREAD_ATTACH` i `DLL_THREAD_DETACH` przypadki, w `DllMain` funkcji. Te przypadki są przekazywane do `DllMain` po wątków Dołączanie i odłączanie od biblioteki DLL. Wywoływanie [TlsAlloc](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsalloc) podczas dołączania się biblioteki DLL umożliwia biblioteki DLL zachować wątku (TLS) w magazynie lokalnym indeksów dla każdego wątku, dołączone do biblioteki DLL.

Należy pamiętać, że plik nagłówkowy Afxdllx.h zawiera specjalne definicje struktury używanych w bibliotek DLL rozszerzeń MFC, takich jak definicja `AFX_EXTENSION_MODULE` i `CDynLinkLibrary`. Tego pliku nagłówkowego należy uwzględnić w Biblioteka DLL rozszerzenia MFC.

> [!NOTE]
>  Jest ważne, że możesz zdefiniować ani Usuń definicje, żadnego z `_AFX_NO_XXX` makr w pliku Stdafx.h. Te makra istnieje wyłącznie na potrzeby sprawdzania, czy platforma dany element docelowy obsługuje tę funkcję. Można napisać program, aby sprawdzić te makra (na przykład `#ifndef _AFX_NO_OLE_SUPPORT`), ale program nigdy nie należy zdefiniować lub Usuń definicje makr.

Funkcja inicjowania próbki, która obsługuje wielowątkowość znajduje się w [za pomocą wątku lokalnego magazynu w bibliotece dll](/windows/desktop/Dlls/using-thread-local-storage-in-a-dynamic-link-library) w zestawie Windows SDK. Należy pamiętać, że przykład zawiera funkcję punktu wejścia o nazwie `LibMain`, ale należy nazwać tę funkcję, `DllMain` , która działa z biblioteki wykonawczej MFC i C.

## <a name="see-also"></a>Zobacz też

[Biblioteki DLL w programie Visual C++](../build/dlls-in-visual-cpp.md)<br/>
[Punkt wejścia funkcji DllMain](/windows/desktop/Dlls/dllmain)<br/>
[Biblioteka dołączana dynamicznie najlepszych rozwiązań](/windows/desktop/Dlls/dynamic-link-library-best-practices)