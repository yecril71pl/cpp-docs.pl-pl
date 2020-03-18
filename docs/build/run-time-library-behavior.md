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
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417314"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>Biblioteki DLL i C++ zachowanie biblioteki w czasie wykonywania wizualizacji

Podczas tworzenia biblioteki dołączanej dynamicznie (DLL) za pomocą programu Visual Studio, konsolidator obejmuje bibliotekę wykonawczą (VCRuntime) C++ wizualizacji. VCRuntime zawiera kod wymagany do zainicjowania i zakończenia pliku wykonywalnegoC++ C/. W przypadku połączenia z biblioteką DLL kod VCRuntime zapewnia wewnętrzną funkcję punktu wejścia biblioteki DLL o nazwie `_DllMainCRTStartup`, która obsługuje komunikaty systemu operacyjnego Windows do biblioteki DLL w celu dołączenia lub odłączenia od procesu lub wątku. Funkcja `_DllMainCRTStartup` wykonuje podstawowe zadania, takie jak Konfiguracja zabezpieczeń buforu stosu, inicjowanie i kończenie biblioteki wykonawczej języka C (CRT) oraz wywołania konstruktorów i destruktorów dla obiektów statycznych i globalnych. `_DllMainCRTStartup` również wywołuje funkcje haka dla innych bibliotek, takich jak WinRT, MFC i ATL, aby wykonać własne inicjalizacje i zakończenie. Bez tego inicjalizacji CRT i inne biblioteki, a także zmienne statyczne, zostałyby pozostawione w stanie niezainicjowanym. Te same VCRuntime wewnętrzne procedury inicjowania i zakończenia są wywoływane, czy biblioteka DLL korzysta ze statycznie połączonej CRT czy dynamicznie połączonej biblioteki DLL.

## <a name="default-dll-entry-point-_dllmaincrtstartup"></a>_DllMainCRTStartup domyślnego punktu wejścia biblioteki DLL

W systemie Windows wszystkie biblioteki DLL mogą zawierać opcjonalną funkcję punktu wejścia, zazwyczaj nazywaną `DllMain`, która jest wywoływana dla inicjalizacji i zakończenia. Pozwala to na przydzielenie lub zwolnienie dodatkowych zasobów zgodnie z wymaganiami. System Windows wywołuje funkcję punktu wejścia w czterech sytuacjach: dołączanie procesu, odłączanie procesu, dołączanie wątku i odłączanie wątku. Podczas ładowania biblioteki DLL do przestrzeni adresowej procesu, gdy aplikacja, która korzysta z niej jest załadowana, lub gdy aplikacja żąda biblioteki DLL w czasie wykonywania, system operacyjny tworzy oddzielną kopię danych biblioteki DLL. Jest to tzw. *proces Attach*. *Dołączanie do wątku* występuje, gdy proces, w którym załadowano plik dll, tworzy nowy wątek. *Odłączanie wątku* występuje po zakończeniu wątku, a *odłączenie procesu* polega na tym, że biblioteka DLL nie jest już wymagana i jest dostarczana przez aplikację. System operacyjny wykonuje oddzielne wywołanie do punktu wejścia biblioteki DLL dla każdego z tych zdarzeń, przekazując argument *przyczyny* dla każdego typu zdarzenia. Na przykład system operacyjny wysyła `DLL_PROCESS_ATTACH` jako argument *przyczyny* do dołączenia do procesu sygnału.

Biblioteka VCRuntime zapewnia funkcję punktu wejścia o nazwie `_DllMainCRTStartup` do obsługi domyślnych operacji inicjowania i kończenia. Po dołączeniu do procesu funkcja `_DllMainCRTStartup` konfiguruje sprawdzanie zabezpieczeń buforów, inicjuje metodę CRT i inne biblioteki, inicjuje informacje o typie w czasie wykonywania, inicjuje i wywołuje konstruktory dla danych statycznych i nielokalnych, inicjuje magazyny lokalne wątków, zwiększa wewnętrzny licznik statyczny dla każdego dołączania, a następnie wywołuje `DllMain`dostarczone przez użytkownika lub bibliotekę. Po odłączeniu do procesu funkcja przechodzi przez te kroki wstecz. Wywołuje `DllMain`, zmniejsza licznik wewnętrzny, wywołuje destruktory, wywołuje funkcje zakończenia CRT i zarejestrowano funkcje `atexit` i powiadamia wszystkie inne biblioteki o zakończeniu. Gdy licznik załączników spadnie do zera, funkcja zwraca `FALSE`, aby wskazać systemowi Windows, że biblioteka DLL może zostać zwolniona. Funkcja `_DllMainCRTStartup` jest również wywoływana podczas dołączania wątku i odłączania wątku. W takich przypadkach kod VCRuntime nie ma żadnych dodatkowych inicjalizacji ani Nieprzerwania, a jedynie wywołuje `DllMain`, aby przekazać komunikat. Jeśli `DllMain` zwraca `FALSE` z dołączania do procesu, sygnalizując błąd, `_DllMainCRTStartup` wywołania `DllMain` ponownie i przekaże `DLL_PROCESS_DETACH` jako argument *przyczyny* , następnie przechodzi przez resztę procesu zakończenia.

Podczas kompilowania bibliotek DLL w programie Visual Studio domyślny punkt wejścia `_DllMainCRTStartup` dostarczany przez VCRuntime jest automatycznie łączony. Nie trzeba określać funkcji punktu wejścia dla biblioteki DLL przy użyciu opcji konsolidatora [/entry (symbol punktu wejścia)](reference/entry-entry-point-symbol.md) .

> [!NOTE]
> Chociaż istnieje możliwość określenia innej funkcji punktu wejścia dla biblioteki DLL przy użyciu opcji/ENTRY: konsolidatora, firma Microsoft nie zaleca tego, ponieważ funkcja punktu wejścia będzie musiała duplikować wszystkie elementy, które `_DllMainCRTStartup` robią w tej samej kolejności. VCRuntime udostępnia funkcje, które umożliwiają duplikowanie zachowania. Na przykład można wywołać [__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md) natychmiast po dołączeniu do procesu, aby obsługiwał opcję sprawdzania bufora [(sprawdzanie zabezpieczeń bufora)](reference/gs-buffer-security-check.md) . Można wywołać funkcję `_CRT_INIT`, przekazując te same parametry co funkcja punktu wejścia, aby wykonać pozostałe funkcje inicjacji lub zakończenia biblioteki DLL.

<a name="initializing-a-dll"></a>

## <a name="initialize-a-dll"></a>Inicjowanie biblioteki DLL

Biblioteka DLL może mieć kod inicjujący, który musi zostać wykonany w przypadku załadowania biblioteki DLL. Aby można było wykonywać własne funkcje inicjowania i kończenia biblioteki DLL, `_DllMainCRTStartup` wywołuje funkcję o nazwie `DllMain`, którą można podać. `DllMain` musi mieć sygnaturę wymaganą dla punktu wejścia biblioteki DLL. Domyślna funkcja punktu wejścia `_DllMainCRTStartup` wywołań `DllMain` przy użyciu tych samych parametrów, które zostały przesłane przez system Windows. Domyślnie, jeśli nie podasz funkcji `DllMain`, program Visual Studio udostępnia ją dla Ciebie i łączy ją w taki sposób, aby `_DllMainCRTStartup` zawsze miał coś do wywołania. Oznacza to, że jeśli nie trzeba inicjować biblioteki DLL, nie ma żadnych specjalnych, które należy wykonać podczas kompilowania biblioteki DLL.

Jest to podpis używany do `DllMain`:

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```

Niektóre biblioteki zawijają funkcję `DllMain`. Na przykład w zwykłej bibliotece MFC DLL należy zaimplementować `InitInstance` `CWinApp` obiektu i `ExitInstance` funkcje członkowskie, aby wykonać inicjalizację i zakończenie wymagane przez bibliotekę DLL. Aby uzyskać więcej informacji, zobacz sekcję [Inicjowanie zwykłych BIBLIOTEK MFC DLL](#initializing-regular-dlls) .

> [!WARNING]
> Istnieją znaczne ograniczenia dotyczące tego, co można bezpiecznie zrobić w punkcie wejścia biblioteki DLL. Zobacz [Ogólne najlepsze rozwiązania](/windows/win32/Dlls/dynamic-link-library-best-practices) dotyczące konkretnych interfejsów API systemu Windows, które nie są bezpieczne do wywołania w `DllMain`. Jeśli potrzebujesz wszystkiego, ale najprostsza Inicjalizacja, zrób to w funkcji inicjacji biblioteki DLL. Można wymagać, aby aplikacje wywoływały funkcję inicjującą po uruchomieniu `DllMain` i przed wywołaniem innych funkcji w bibliotece DLL.

<a name="initializing-non-mfc-dlls"></a>

### <a name="initialize-ordinary-non-mfc-dlls"></a>Inicjowanie zwykłych bibliotek DLL (innych niż MFC)

Aby wykonać własne inicjalizacje w zwykłych bibliotekach DLL (innych niż MFC), które używają VCRuntime `_DllMainCRTStartup` punkt wejścia, kod źródłowy biblioteki DLL musi zawierać funkcję o nazwie `DllMain`. Poniższy kod przedstawia podstawowy szkielet pokazujący, jak może wyglądać definicja `DllMain`:

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
> W starszej dokumentacji Windows SDK należy określić rzeczywistą nazwę funkcji punktu wejścia biblioteki DLL w wierszu polecenia konsolidatora z opcją/ENTRY. W programie Visual Studio nie trzeba używać opcji/ENTRY, jeśli nazwa funkcji punktu wejścia jest `DllMain`. W rzeczywistości, jeśli używasz opcji/ENTRY i nazwij funkcję punktu wejścia inną niż `DllMain`, CRT nie zostanie prawidłowo zainicjowany, chyba że funkcja punktu wejścia wykonuje te same wywołania inicjacji, które `_DllMainCRTStartup`.

<a name="initializing-regular-dlls"></a>

### <a name="initialize-regular-mfc-dlls"></a>Inicjowanie zwykłych bibliotek DLL MFC

Ponieważ regularne biblioteki MFC DLL mają obiekt `CWinApp`, powinny wykonywać zadania inicjowania i kończenia w tej samej lokalizacji, w której znajduje się aplikacja MFC: w `InitInstance` i `ExitInstance` funkcjach członkowskich klasy pochodnej `CWinApp`biblioteki DLL. Ponieważ MFC udostępnia funkcję `DllMain`, która jest wywoływana przez `_DllMainCRTStartup` dla `DLL_PROCESS_ATTACH` i `DLL_PROCESS_DETACH`, nie należy pisać własnej funkcji `DllMain`. Wywołania funkcji `DllMain` dostarczone przez MFC `InitInstance` w przypadku załadowania biblioteki DLL i wywołania `ExitInstance` przed odładowaniem biblioteki DLL.

Zwykła Biblioteka MFC DLL może śledzić wiele wątków, wywołując [Funkcja TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) i [TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue) w funkcji `InitInstance`. Te funkcje umożliwiają bibliotece DLL śledzenie danych specyficznych dla wątku.

W zwykłej bibliotece MFC DLL, która łączy się dynamicznie z MFC, jeśli używasz dowolnej biblioteki MFC OLE, MFC Database (lub DAO) lub MFC Sockets support, odpowiednio, debugowanie rozszerzenia MFC DLL MFCO*wersja*d. dll, MFCD*wersja*d. dll i MFCN*wersja*d. dll (gdzie *wersja* jest numerem wersji) są automatycznie łączone. Musisz wywołać jedną z następujących wstępnie zdefiniowanych funkcji inicjujących dla każdej z tych bibliotek DLL, które są używane w `CWinApp::InitInstance`zwykłych bibliotek DLL MFC.

|Typ obsługi MFC|Funkcja inicjacji do wywołania|
|-------------------------|-------------------------------------|
|MFC OLE (MFCO*wersja*D. dll)|`AfxOleInitModule`|
|Baza danych MFC (MFCD*wersja*D. dll)|`AfxDbInitModule`|
|Gniazda MFC (MFCN*wersja*D. dll)|`AfxNetInitModule`|

<a name="initializing-extension-dlls"></a>

### <a name="initialize-mfc-extension-dlls"></a>Inicjuj biblioteki DLL rozszerzenia MFC

Ponieważ biblioteki DLL rozszerzenia MFC nie mają obiektu pochodnego `CWinApp`(jak zwykłych bibliotek DLL MFC), należy dodać kod inicjalizacji i zakończenia do funkcji `DllMain`, którą generuje Kreator MFC DLL.

Kreator udostępnia Poniższy kod dla bibliotek DLL rozszerzeń MFC. W kodzie `PROJNAME` jest symbolem zastępczym dla nazwy projektu.

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

Tworzenie nowego obiektu `CDynLinkLibrary` podczas inicjowania pozwala na eksportowanie `CRuntimeClass` obiektów lub zasobów do aplikacji klienckiej biblioteki DLL rozszerzenia MFC.

Jeśli biblioteka DLL rozszerzenia MFC ma być używana z co najmniej jednej zwykłej biblioteki DLL MFC, należy wyeksportować funkcję inicjującą, która tworzy obiekt `CDynLinkLibrary`. Ta funkcja musi być wywołana z każdej zwykłej biblioteki DLL MFC, która używa biblioteki MFC DLL. Odpowiednie miejsce do wywołania tej funkcji inicjującej znajduje się w `InitInstance` funkcja członkowska zwykłego `CWinApp`biblioteki MFC DLL, przed użyciem dowolnej z wyeksportowanych klas lub funkcji biblioteki DLL rozszerzenia MFC.

W `DllMain` wygenerowanej przez kreatora MFC DLL, wywołanie `AfxInitExtensionModule` przechwytuje klasy czasu wykonywania modułu (struktury`CRuntimeClass`), a także jego fabryki obiektów (`COleObjectFactory` obiektów) do użycia podczas tworzenia obiektu `CDynLinkLibrary`. Należy sprawdzić wartość zwracaną przez `AfxInitExtensionModule`; Jeśli wartość zerowa jest zwracana z `AfxInitExtensionModule`, zwróć zero z funkcji `DllMain`.

Jeśli biblioteka DLL rozszerzenia MFC zostanie jawnie połączona z plikiem wykonywalnym (oznacza to, że wywołania wykonywalne `AfxLoadLibrary` do łączenia z biblioteką DLL), należy dodać wywołanie do `AfxTermExtensionModule` na `DLL_PROCESS_DETACH`. Ta funkcja umożliwia MFC czyszczenie biblioteki DLL rozszerzenia MFC, gdy każdy proces odłącza się od biblioteki DLL rozszerzenia MFC (co się stanie w przypadku zakończenia procesu lub gdy biblioteka DLL zostanie zwolniona w wyniku wywołania `AfxFreeLibrary`). Jeśli biblioteka DLL rozszerzenia MFC będzie niejawnie łączona z aplikacją, wywołanie do `AfxTermExtensionModule` nie jest konieczne.

Aplikacje, które jawnie łączą się z bibliotekami DLL rozszerzenia MFC, muszą wywoływać `AfxTermExtensionModule` podczas zwalniania biblioteki DLL. Powinni również używać `AfxLoadLibrary` i `AfxFreeLibrary` (zamiast funkcji Win32 `LoadLibrary` i `FreeLibrary`), jeśli aplikacja używa wielu wątków. Użycie `AfxLoadLibrary` i `AfxFreeLibrary` zapewnia, że kod uruchamiania i zamykania, który jest wykonywany, gdy biblioteka DLL rozszerzenia MFC zostanie załadowana i zwolniona, nie powoduje uszkodzenia globalnego stanu MFC.

Ponieważ MFCx0. dll jest w pełni inicjowany przez czas, który `DllMain` jest wywoływany, można przydzielić pamięć i wywoływać funkcje MFC w ramach `DllMain` (w przeciwieństwie do 16-bitowej wersji MFC).

Biblioteki DLL rozszerzeń mogą wymagać wielowątkowości przez obsługę `DLL_THREAD_ATTACH` i `DLL_THREAD_DETACH` przypadków w funkcji `DllMain`. Te przypadki są przesyłane do `DllMain`, gdy wątki dołączają i łączą się z biblioteką DLL. Wywołanie [Funkcja TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) , gdy biblioteka DLL jest dołączana, umożliwia biblioteki DLL obsługę indeksów lokalnego magazynu wątków (TLS) dla każdego wątku dołączonego do biblioteki DLL.

Należy zauważyć, że plik nagłówka AFXDLLX. h zawiera specjalne definicje struktur używanych w bibliotekach DLL rozszerzenia MFC, takich jak definicja `AFX_EXTENSION_MODULE` i `CDynLinkLibrary`. Należy dołączyć ten plik nagłówka do biblioteki DLL rozszerzenia MFC.

> [!NOTE]
>  Ważne jest, aby nie definiować ani nie definiować żadnych `_AFX_NO_XXX` makr w *PCH. h* (*stdafx. h* w programie Visual Studio 2017 i wcześniejszych). Te makra istnieją tylko w celu sprawdzenia, czy konkretna platforma docelowa obsługuje tę funkcję. Można napisać program, aby sprawdzić te makra (na przykład `#ifndef _AFX_NO_OLE_SUPPORT`), ale program nigdy nie definiuje ani nie definiuje tych makr.

Przykładowa funkcja inicjująca, która obsługuje wielowątkowość, jest dołączana do [użycia lokalnego magazynu wątków w bibliotece dołączanej dynamicznie](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library) w Windows SDK. Należy zauważyć, że przykład zawiera funkcję punktu wejścia o nazwie `LibMain`, ale należy nazwać tę funkcję `DllMain` tak, aby działała z bibliotekami uruchomieniowymi MFC i C.

## <a name="see-also"></a>Zobacz też

[Tworzenie C/C++ dll w Visual Studio](dlls-in-visual-cpp.md)<br/>
[Punkt wejścia DllMain](/windows/win32/Dlls/dllmain)<br/>
[Najlepsze rozwiązania dotyczące biblioteki dołączanej dynamicznie](/windows/win32/Dlls/dynamic-link-library-best-practices)
