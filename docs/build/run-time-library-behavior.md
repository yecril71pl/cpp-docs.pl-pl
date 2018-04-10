---
title: Biblioteki dll i zachowanie biblioteki wykonawczej programu Visual C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 75bf84eeaf9277c5cf037c4fa59c28d109d95856
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>Biblioteki dll i zachowanie biblioteki wykonawczej programu Visual C++  
  
Podczas tworzenia biblioteki dołączanej dynamicznie (DLL) przy użyciu programu Visual C++, domyślnie, konsolidator obejmuje biblioteki wykonawczej programu Visual C++ (VCRuntime). VCRuntime zawiera kod wymagany do rozpoczęcia i zakończenia wykonywalny C/C++. Gdy są połączone do biblioteki DLL, kod VCRuntime stanowi Wewnętrzna funkcja punktu wejścia biblioteki DLL wywoływana `_DllMainCRTStartup` obsługująca komunikatów systemu operacyjnego do pliku DLL umożliwia dołączanie do lub odłączyć od proces lub wątek. `_DllMainCRTStartup` Funkcji wykonuje podstawowe zadania, takie jak ustawianie C Biblioteka run-time (CRT) inicjowanie i kończenie działania zabezpieczeń bufora stosu i wywołań konstruktory i destruktory dla obiektów globalnych i statyczne. `_DllMainCRTStartup`również wywołania funkcje punktów zaczepienia innych bibliotek WinRT, MFC i ATL wykonać własne inicjowanie i kończenie działania programu. Bez tego inicjowania, CRT i innych bibliotek, a także zmiennych statycznych pozostanie w stanie niezainicjowanym. Tej samej inicjacji wewnętrzny VCRuntime i zakończenie procedury są nazywane czy biblioteki DLL używa statycznie połączone CRT lub połączone dynamicznie biblioteki DLL CRT.  
  
## <a name="default-dll-entry-point-dllmaincrtstartup"></a>Domyślna _DllMainCRTStartup punktu wejścia biblioteki DLL  
  
W systemie Windows, wszystkie biblioteki dll może zawierać funkcji opcjonalnych punktu wejścia, zwykle nazywane `DllMain`, która jest wywoływana dla zarówno inicjowanie i kończenie działania. Daje możliwość przydzielić lub zwolnij dodatkowe zasoby, zgodnie z potrzebami. System Windows wywołuje funkcję punktu wejścia w czterech sytuacji: dołączanie procesu, odłączyć procesu, wątku dołączania i odłączania wątku. Podczas ładowania biblioteki DLL do przestrzeni adresowej procesu, po załadowaniu aplikacji, która używa on lub gdy aplikacja zażąda biblioteki DLL w czasie wykonywania, system operacyjny tworzy kopię oddzielnego danych biblioteki DLL. Ta metoda jest wywoływana *dołączanie procesu*. *Dołącz wątku* występuje, gdy proces plik DLL, który jest ładowany w tworzy nowego wątku. *Odłącz wątku* występuje, gdy zakończenie wątku, i *odłączanie procesu* jest, gdy biblioteka DLL nie jest już potrzebne i został wydany przez aplikację. System operacyjny sprawia, że wymaga oddzielnego wywołania do punktu wejścia biblioteki DLL dla każdego z tych zdarzeń, przekazywanie *Przyczyna* argument dla każdego typu zdarzenia. Na przykład system operacyjny wysyła `DLL_PROCESS_ATTACH` jako *Przyczyna* argumentu w celu zasygnalizowania procesu dołączania.  
  
Biblioteka VCRuntime zawiera funkcję punktu wejścia o nazwie `_DllMainCRTStartup` do obsługi operacji domyślne inicjowanie i kończenie działania. Dla procesu, który należy dołączyć, `_DllMainCRTStartup` funkcja konfiguruje sprawdzanie zabezpieczeń bufora, inicjuje CRT i innych bibliotek, inicjuje informacje typu run-time, inicjuje i wymaga konstruktorów statycznych i innego niż lokalne dane, inicjuje lokalny magazyn wątków , zwiększa wewnętrzny statyczny licznika dla każdego attach, a następnie wywołuje lub biblioteki dostarczone przez użytkownika `DllMain`. W procesie odłączyć, funkcja przechodzi przez te kroki odwrotnie. Wywołuje `DllMain`, zmniejsza wewnętrznego licznika wywołuj destruktory, przerwanie wywołania CRT funkcje i zarejestrowany `atexit` funkcje i powiadamia innych bibliotek zakończenia. Gdy licznik załącznika przechodzi do zera, funkcja zwraca `FALSE` wskazująca systemu Windows, czy można zwolnić bibliotekę DLL. `_DllMainCRTStartup` Funkcja jest również nazywany podczas wątku dołączania i odłączania wątku. W takich przypadkach nie żadne dodatkowe inicjowania lub zakończenie samodzielnie kodu VCRuntime, a po prostu wywołuje `DllMain` do przekazywania wiadomości wzdłuż. Jeśli `DllMain` zwraca `FALSE` z procesu dołączania, sygnalizujących niepowodzenie, `_DllMainCRTStartup` wywołania `DllMain` ponownie i przekazuje `DLL_PROCESS_DETACH` jako *Przyczyna* argumentu, następnie przechodzi przez reszty Zakończenie procesu.  
  
Podczas tworzenia biblioteki dll w programie Visual C++, domyślny punkt wejścia `_DllMainCRTStartup` dostarczonych przez VCRuntime jest automatycznie konsolidowana. Nie trzeba określić funkcję punktu wejścia dla biblioteki DLL przy użyciu [/Entry (symbol punktu wejścia)](../build/reference/entry-entry-point-symbol.md) — opcja konsolidatora.  
  
> [!NOTE]
> Gdy jest to możliwe określić inną funkcję punktu wejścia dla biblioteki DLL przy użyciu / Entry: — opcja konsolidatora, nie zaleca się, ponieważ funkcja punkt wejścia musi zduplikowane wszystko, co który `_DllMainCRTStartup` jest w tej samej kolejności. VCRuntime zawiera funkcje, które umożliwiają zduplikowane jego zachowania. Na przykład można wywołać [__security_init_cookie —](../c-runtime-library/reference/security-init-cookie.md) natychmiast na proces dołączania do obsługi [/GS (Sprawdzanie zabezpieczeń bufora)](../build/reference/gs-buffer-security-check.md) buforu opcję sprawdzania. Możesz wywołać `_CRT_INIT` funkcji, przekazując te same parametry jako funkcję punktu wejścia do wykonania pozostałe inicjowanie i kończenie działania funkcji DLL.  
  
<a name="initializing-a-dll"></a>  
  
## <a name="initialize-a-dll"></a>Inicjowanie biblioteki DLL  
  
Biblioteki DLL może być kod inicjujący, który musi być wykonywany podczas ładowania biblioteki DLL. Należy przeprowadzić własne inicjowanie i kończenie działania funkcji DLL, aby `_DllMainCRTStartup` wywołania funkcji o nazwie `DllMain` który można udostępnić. Twoje `DllMain` muszą mieć podpis wymagane dla punktu wejścia biblioteki DLL. Funkcja punktu wejścia domyślne `_DllMainCRTStartup` wywołania `DllMain` przy użyciu tych samych parametrach przekazany przez system Windows. Domyślnie, jeśli nie podasz `DllMain` funkcja dostępna w Visual C++ i łączy go w, aby `_DllMainCRTStartup` zawsze ma coś do wywołania. Oznacza to, że jeśli Inicjowanie biblioteki DLL nie jest wymagane, nie ma specjalnych, musisz wykonać podczas tworzenia biblioteki DLL.  
  
To jest używany dla podpisu `DllMain`:  
  
```cpp  
#include <windows.h>  
  
extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module 
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```  
  
Zawijaj niektórych bibliotek `DllMain` funkcji dla Ciebie. Na przykład w regularną bibliotekę DLL MFC, należy zaimplementować `CWinApp` obiektu `InitInstance` i `ExitInstance` funkcji Członkowskich przeprowadzić inicjowanie i kończenie działania wymagane przez biblioteki DLL. Aby uzyskać więcej informacji, zobacz [inicjowanie zwykłych bibliotek DLL MFC](#initializing-regular-dlls) sekcji.  
  
> [!WARNING]
> Istnieją znaczne ograniczenia na bezpiecznie jak w punkcie wejścia biblioteki DLL. Zobacz [— najlepsze praktyki ogólne](https://msdn.microsoft.com/library/windows/desktop/dn633971#general_best_practices) dla poszczególnych interfejsów API systemu Windows będące niebezpieczny do wywołania `DllMain`. Jeśli potrzebujesz cokolwiek, ale następnie najprostszym inicjowania to zrobić w funkcji inicjowania biblioteki dll. Możesz wymagać aplikacje do wywołania funkcji inicjowania po `DllMain` ma uruchamiania i przed ich wywołaniem innych funkcji w bibliotece DLL.  
  
<a name="initializing-non-mfc-dlls"></a>  
  
### <a name="initialize-ordinary-non-mfc-dlls"></a>Inicjowanie bibliotek DLL niestandardowych (z systemem innym niż MFC)  
  
W celu wykonania własne inicjowania w zwykłych (z systemem innym niż MFC) biblioteki dll, korzystających z dostarczonych VCRuntime `_DllMainCRTStartup` punktu wejścia biblioteki DLL kodu źródłowego musi zawierać funkcji o nazwie `DllMain`. Poniższy kod przedstawia podstawowy szkielet przedstawiający jakie definicji `DllMain` może wyglądać tak:  
  
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
> Starszą dokumentacją zestawu Windows SDK mówi, że rzeczywistą nazwą funkcję punktu wejścia biblioteki DLL musi określony w wierszu polecenia z opcją/Entry konsolidatora. Z programem Visual C++, nie trzeba użyć opcji/Entry, jeśli nazwa funkcji punktu wejścia jest `DllMain`. W rzeczywistości użycie opcji/Entry i nazwę punktu wejścia funkcji coś innego niż `DllMain`, CRT nie pobrać poprawnie zainicjowane, chyba że funkcja punktu wejścia wykonuje samej wywołań inicjowania `_DllMainCRTStartup` sprawia, że.  
  
<a name="initializing-regular-dlls"></a>  
  
### <a name="initialize-regular-mfc-dlls"></a>Inicjowanie MFC dll  
  
Ponieważ regularne biblioteki DLL MFC `CWinApp` obiektu, powinny one wykonywanie zadań inicjowanie i kończenie działania w tej samej lokalizacji co aplikacji MFC: w `InitInstance` i `ExitInstance` funkcji Członkowskich DLL `CWinApp`-pochodnych Klasa. Ponieważ zapewnia MFC `DllMain` funkcja, która jest wywoływana przez `_DllMainCRTStartup` dla `DLL_PROCESS_ATTACH` i `DLL_PROCESS_DETACH`, nie należy zapisać swoje własne `DllMain` funkcji. Podane MFC `DllMain` wywołania funkcji `InitInstance` po załadowaniu biblioteki DLL i wywołuje `ExitInstance` przed biblioteki DLL jest zwalniany.  
  
Regularne biblioteki DLL MFC można zachować informacje o wiele wątków wywołując [TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801) i [TlsGetValue](http://msdn.microsoft.com/library/windows/desktop/ms686812) w jego `InitInstance` funkcji. Te funkcje umożliwiają biblioteki DLL w celu śledzenia danych właściwe dla wątków.  
  
W regularnych bibliotek DLL MFC, łączącą dynamicznie z MFC, jeśli używasz dowolnego MFC OLE, bazy danych MFC (lub DAO) lub MFC Sockets obsługuje odpowiednio debugowania rozszerzenia MFC DLL MFCO*wersji*D.dll, MFCD*wersji*D.dll i MFCN*wersji*D.dll (gdzie *wersji* jest numer wersji) jest automatycznie konsolidowana. Należy wywołać jedną z następujących funkcji inicjowania wstępnie zdefiniowane dla każdej te biblioteki dll, które są używane w bibliotece regularne DLL MFC `CWinApp::InitInstance`.  
  
|Typ obsługi MFC|Funkcja inicjowania do wywołania|  
|-------------------------|-------------------------------------|  
|MFC OLE (MFCO*wersji*D.dll)|`AfxOleInitModule`|  
|Baza danych MFC (MFCD*wersji*D.dll)|`AfxDbInitModule`|  
|Sockets w MFC (MFCN*wersji*D.dll)|`AfxNetInitModule`|  
  
<a name="initializing-extension-dlls"></a>  
  
### <a name="initialize-mfc-extension-dlls"></a>Inicjowanie biblioteki DLL rozszerzeń MFC  
  
Ponieważ rozszerzenia MFC DLL nie mają `CWinApp`-pochodnych obiektu (tak jak MFC dll), należy dodać kodu inicjowanie i kończenie działania do `DllMain` funkcji, które generuje Kreator biblioteki DLL MFC.  
  
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
  
Tworzenie nowego `CDynLinkLibrary` obiekt podczas inicjowania umożliwia rozszerzenia MFC DLL, aby wyeksportować `CRuntimeClass` obiektów lub zasobów do aplikacji klienckiej.  
  
Jeśli zamierzasz użyć rozszerzenia MFC DLL z co najmniej jeden regularne biblioteki DLL MFC, należy wyeksportować błędu funkcji inicjowania, która tworzy `CDynLinkLibrary` obiektu. Tego funkcja musi być wywołana z każdej korzystające z biblioteki DLL rozszerzenia MFC DLL MFC. Znajduje się w odpowiednim miejscu, aby wywołać tę funkcję inicjowania `InitInstance` funkcji członkowskiej klasy MFC DLL regularne `CWinApp`-pochodnych obiektu przed użyciem dowolnej z wyeksportowanej klasy lub funkcje MFC DLL rozszerzenia.  
  
W `DllMain` czy generuje Kreator biblioteki DLL MFC, wywołanie `AfxInitExtensionModule` przechwytuje klasy czasu wykonywania modułu (`CRuntimeClass` struktury) oraz jego fabryk obiektu (`COleObjectFactory` obiektów) do użycia podczas `CDynLinkLibrary` tworzony jest obiekt. Należy sprawdzić wartość zwrotną z `AfxInitExtensionModule`; Jeśli wartość zero, jest zwracana z `AfxInitExtensionModule`, zwracać zera z Twojej `DllMain` funkcji.  
  
Jeśli bibliotekę DLL rozszerzenia MFC zostanie jawnie połączony plik wykonywalny (co oznacza wykonywalnego wywołania `AfxLoadLibrary` do odesłania do biblioteki DLL), należy dodać wywołanie `AfxTermExtensionModule` na `DLL_PROCESS_DETACH`. Ta funkcja umożliwia MFC wyczyścić bibliotekę DLL rozszerzenia MFC, gdy każdy proces odłącza z biblioteki DLL rozszerzenia MFC (które ma miejsce, gdy kończy proces lub gdy biblioteka DLL jest zwalnianie w `AfxFreeLibrary` wywołania). Jeśli bibliotekę DLL rozszerzenia MFC zostaną połączone niejawnie aplikacji wywołanie `AfxTermExtensionModule` nie jest konieczne.  
  
Aplikacje, które jawnie musi wywołać link do biblioteki DLL rozszerzenia MFC `AfxTermExtensionModule` podczas zwalniania biblioteki DLL. Ponadto powinny używać `AfxLoadLibrary` i `AfxFreeLibrary` (zamiast funkcji Win32 `LoadLibrary` i `FreeLibrary`) Jeśli aplikacja używa wielu wątków. Przy użyciu `AfxLoadLibrary` i `AfxFreeLibrary` upewnia się, że uruchamiania i wyłączania kod, który wykonuje się, gdy rozszerzenie MFC DLL jest załadowany i zwolniony nieuszkodzone stan globalny MFC.  
  
Ponieważ MFCx0.dll jest w pełni zainicjowany w czasie `DllMain` jest wywoływana, można przydzielić pamięci i wywoływać funkcje MFC w `DllMain` (w przeciwieństwie do 16-bitowych wersji MFC).  
  
Biblioteki DLL rozszerzeń zająć się wielowątkowość Obsługa `DLL_THREAD_ATTACH` i `DLL_THREAD_DETACH` przypadki, w `DllMain` funkcji. Te przypadki są przekazywane do `DllMain` po wątków dołączania i odłączania z biblioteki DLL. Wywoływanie [TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801) gdy biblioteka DLL jest dołączenie umożliwia biblioteki DLL, obsługa wątku indeksy magazynu lokalnego (TLS) dla każdego wątku dołączone do pliku DLL.  
  
Należy pamiętać, że plik nagłówka Afxdllx.h zawiera specjalne definicje struktury używane w bibliotekach DLL rozszerzenia MFC, np. definicji `AFX_EXTENSION_MODULE` i `CDynLinkLibrary`. Ten plik nagłówka, należy uwzględnić w bibliotekę DLL rozszerzenia MFC.  
  
> [!NOTE]
>  Należy pamiętać, że można zdefiniować ani Usuń jedną z `_AFX_NO_XXX` makra w pliku Stdafx.h. Te makra istnieje tylko w celu sprawdzenia, czy platforma dany element docelowy obsługuje tej funkcji. Można napisać programu, aby sprawdzić te makra (na przykład `#ifndef _AFX_NO_OLE_SUPPORT`), ale program nigdy nie należy zdefiniować lub Usuń definicje makr.  
  
Funkcja inicjowania próbki uchwyty wielowątkowość jest zawarte w [za pomocą wątku magazynu lokalnego w bibliotece dll](http://msdn.microsoft.com/library/windows/desktop/ms686997) w zestawie Windows SDK. Należy pamiętać, że próbka zawiera funkcję punktu wejścia o nazwie `LibMain`, ale należy nazwę tej funkcji `DllMain` , która działa z biblioteki wykonawczej MFC i C.  
  
## <a name="see-also"></a>Zobacz też  
  
[Biblioteki DLL w programie Visual C++](../build/dlls-in-visual-cpp.md)  
[Punkt wejścia funkcji DllMain](https://msdn.microsoft.com/library/windows/desktop/ms682583.aspx)  
[Biblioteka DLL najlepsze rozwiązania](https://msdn.microsoft.com/library/windows/desktop/dn633971.aspx)  