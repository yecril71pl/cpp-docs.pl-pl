---
title: Łączenie pliku wykonywalnego z biblioteką DLL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- run time [C++], linking
- dynamic load linking [C++]
- linking [C++], DLLs
- DLLs [C++], linking
- implicit linking [C++]
- explicit linking [C++]
- executable files [C++], linking to DLLs
- loading DLLs [C++]
ms.assetid: 7592e276-dd6e-4a74-90c8-e1ee35598ea3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 49973d203670eaa2aa0988d9de04784d13eaec09
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43196690"
---
# <a name="link-an-executable-to-a-dll"></a>Łączenie pliku wykonywalnego z biblioteką DLL  
  
Plik wykonywalny łączy (lub ładuje) biblioteki DLL na jeden z dwóch sposobów:  
  
-   *Niejawna Konsolidacja*, gdy system operacyjny ładuje DLL po załadowaniu wykonywalnego użycia. Plik wykonywalny klient wywołuje eksportowanych funkcji DLL tak, jakby funkcje zostały statycznie połączone i zawarte w pliku wykonywalnym. Niejawna Konsolidacja czasami nazywa się *statycznego wczytywnia* lub *dynamicznego łączania w czasie ładowania*.  
  
-   *Jawne tworzenie łączy*, gdy system operacyjny ładuje DLL na żądanie w czasie wykonywania. Plik wykonywalny, który korzysta z biblioteki DLL przez jawne tworzenie łączy musi wykonać wywołania funkcji, aby jawnie załadować i rozładować DLL i uzyskać dostęp do funkcji eksportowanych przez DLL. W przeciwieństwie do wywołania funkcji w statycznie połączoną bibliotekę klient wykonywalny musi wywołać eksportowane funkcji w bibliotece DLL za pomocą wskaźnika funkcji. Jawne tworzenie łączy nazywa się czasem jako *dynamicznego obciążenia* lub *dynamicznego łączania w czasie wykonywania*.  
  
Plik wykonywalny można użyć jednej z metod łączenia połączyć z tej samej bibliotece DLL. Ponadto te metody nie są wzajemnie się wykluczają; jeden plik wykonywalny można niejawnie połączyć z biblioteką DLL i innym można jawnie do niej dołączyć.  
  
<a name="determining-which-linking-method-to-use"></a>  
  
## <a name="determine-which-linking-method-to-use"></a>Określić, której metody łączenia użyjesz  
  
Czy ma być używany z jawnymi łączami lub jawnego łączenia jest architektury decyzji, które należy wykonać w aplikacji. Istnieją zalety i wady każdej metody.  
  
### <a name="implicit-linking"></a>Niejawna Konsolidacja  
  
Niejawna Konsolidacja występuje, gdy kod aplikacji wywołuje wyeksportowanej funkcji DLL. Kodu źródłowego dla pliku wykonywalnego wywoływania to skompilowany lub składany, wywołanie funkcji DLL generuje odwołanie do funkcji zewnętrznej w kod obiektu. Aby rozwiązać ten odwołanie zewnętrzne, aplikacja musi łączyć się z biblioteką importu (plik .lib) zapewniane przez twórcę DLL.  
  
Importuj biblioteki zawiera tylko kod można załadować biblioteki DLL i zaimplementować wywołania funkcji w bibliotece DLL. Znajdowanie funkcji zewnętrznej biblioteki importu informuje konsolidator, że kod dla tej funkcji jest w bibliotece DLL. Aby rozwiązać zewnętrzne odwołania do bibliotek DLL, konsolidator po prostu dodaje informacje do pliku wykonywalnego, który informuje system, gdzie można znaleźć kod biblioteki DLL, podczas uruchamiania procesu.  
  
Po uruchomieniu programu, który zawiera dynamicznie połączony odwołania system używa informacji w pliku wykonywalnego programu do zlokalizowania wymaganych bibliotek DLL. Jeśli nie może odnaleźć biblioteki DLL, system kończy proces i wyświetlane jest okno dialogowe, które zgłasza błąd. W przeciwnym razie system mapuje moduły biblioteki DLL do przestrzeni adresowej procesu.  
  
Jeśli dowolny z bibliotek DLL ma funkcję punktu wejścia, inicjowanie i kończenie działania kodu takie jak `DllMain`, system operacyjny wywołuje funkcję. Określa jeden z parametrów przekazanych do funkcji punktu wejścia, że kod, który wskazuje biblioteki DLL jest dołączenie do procesu. Jeśli funkcja punktu wejścia zwraca wartość TRUE, system kończy proces i zgłasza błąd.  
  
Na koniec system modyfikuje kodu wykonywalnego procesu, podaj początkowy adresy dla funkcji DLL.  
  
Podobnie jak pozostałej części kodu programu kod biblioteki DLL jest mapowany do przestrzeni adresowej procesu podczas uruchamiania procesu i jest ładowany do pamięci tylko wtedy, gdy jest to wymagane. W rezultacie `PRELOAD` i `LOADONCALL` atrybuty kodu posługują się .def — pliki do kontroli ładowania w poprzednich wersjach systemu Windows nie jest już mają znaczenie.  
  
### <a name="explicit-linking"></a>Jawne tworzenie łączy  
  
Większość aplikacji używa jawnymi łączami, ponieważ jest on metody easiest łączenia użyjesz. Istnieją jednak razy, gdy konieczne jest jawne tworzenie łączy. Poniżej przedstawiono niektóre typowe przyczyny Użyj jawnego łączenia:  
  
-   Aplikacja nie może określić nazwę biblioteki DLL, która ładuje do czasu wykonywania. Na przykład aplikacja może uzyskać nazwy biblioteki DLL i eksportowanych funkcji z pliku konfiguracji podczas uruchamiania.  
  
-   Proces, który korzysta z jawnymi łączami jest zakończony przez system operacyjny, jeśli biblioteka DLL nie zostanie znaleziony podczas uruchamiania procesu. Proces, który korzysta z jawnymi łączami, nie ma znacznika kończącego w tej sytuacji i mogą próbować odzyskać sprawność po błędzie. Na przykład ten proces może powiadomić użytkownika o błędzie i użytkownik określił inną ścieżkę do pliku DLL.  
  
-   Proces, który korzysta z jawnymi łączami również zostanie zakończony, jeśli dowolny z biblioteki DLL jest połączona, mają `DllMain` funkcja, która kończy się niepowodzeniem. Proces, który korzysta z jawnymi łączami, nie jest zakończony w takiej sytuacji.  
  
-   Aplikacja, która niejawnie łączy wiele bibliotek DLL może działać powoli, można uruchomić, ponieważ Windows ładuje wszystkie biblioteki dll, podczas ładowania aplikacji. Aby zwiększyć wydajność uruchamiania, aplikację można połączyć niejawnie tylko tych bibliotek DLL wymagane natychmiast po ładowania i zaczekaj, aż inne biblioteki DLL są wymagane, aby połączyć je jawnie.  
  
-   Jawne tworzenie łączy eliminuje potrzebę do łączenia aplikacji za pomocą biblioteki importu. Jeśli zmiany w bibliotece DLL spowoduje eksportowe liczebniki porządkowe zmienić, aplikacje, które używają jawnego łączenia nie trzeba Połącz ponownie, jeśli wywołują `GetProcAddress` przy użyciu nazwy funkcji i nie wartości porządkowe, natomiast musi ponownie połączyć aplikacje, które używają niejawna Konsolidacja Nowa biblioteka importu.  
  
Poniżej przedstawiono dwa zagrożenia z jawnymi łączami, w których trzeba pamiętać:  
  
-   Jeśli biblioteka DLL ma `DllMain` funkcję punktu wejścia, system operacyjny wywołuje funkcję w kontekście wątku, który wywołał `LoadLibrary`. Funkcja punktu wejścia nie jest wywoływana, jeśli biblioteka DLL jest już dołączony do procesu ze względu na poprzednie wywołanie `LoadLibrary` który miał nie odpowiedniego wywołania `FreeLibrary` funkcji. Jawne tworzenie łączy może powodować problemy, jeśli korzysta z biblioteki DLL `DllMain` funkcję, aby wykonać inicjowania na każdy wątek procesu, ponieważ wątki z już istniejącymi podczas `LoadLibrary` (lub `AfxLoadLibrary`) jest wywoływana nie zainicjowano.  
  
-   Jeśli biblioteka DLL deklaruje dane statyczne zakresu jako `__declspec(thread)`, może spowodować błąd ochrony w przypadku, gdy jawnie połączony. Po załadowaniu pliku DLL za pomocą wywołania `LoadLibrary`, powoduje błąd ochrony, zawsze wtedy, gdy kod odwołuje się do tych danych. (Dane statyczne zakres obejmuje zarówno globalne i lokalne elementy statyczne). W związku z tym podczas tworzenia biblioteki DLL, należy albo Unikaj używania magazynu wątków lokalnych lub informować użytkowników DLL o potencjalne pułapki związane z dynamiczne ładowanie biblioteki DLL. Aby uzyskać więcej informacji, zobacz [przy użyciu pamięci lokalnej wątku w Biblioteka dołączana dynamicznie (Windows SDK)](https://msdn.microsoft.com/library/windows/desktop/ms686997).  
  
<a name="linking-implicitly"></a>  
  
## <a name="how-to-link-implicitly-to-a-dll"></a>Jak połączyć niejawnie biblioteki DLL  
  
Aby korzystać z biblioteki DLL, łącząc niejawne, pliki wykonywalne klienta musisz uzyskać te pliki z dostawcą biblioteki DLL:  
  
-   Co najmniej jeden nagłówek pliki (.h) zawierające deklaracje wyeksportowane dane, funkcje i/lub klasy C++ w bibliotece DLL. Klasy, funkcje i dane eksportowanych przez DLL musi być oznaczona jako `__declspec(dllimport)` w pliku nagłówkowym. Aby uzyskać więcej informacji, zobacz [dllexport i dllimport](../cpp/dllexport-dllimport.md).  
  
-   Importuj biblioteki do połączenia w programie wykonywalnym. Podczas kompilowania biblioteki DLL, konsolidator tworzy bibliotekę importu. Aby uzyskać więcej informacji, zobacz [. Pliki LIB](../build/reference/dot-lib-files-as-linker-input.md).  
  
-   Rzeczywisty plik DLL.  
  
Aby korzystać z biblioteki DLL przez jawnymi łączami, wykonywalny musi zawierać pliki nagłówkowe, które deklarują danych, funkcji lub klasy C++ eksportowanych przez DLL w każdym pliku źródłowego, który zawiera wywołania do klasy wyeksportowane dane, funkcje i. Z punktu widzenia kodowania wywołania do eksportowanych funkcji są tak samo jak inne wywołania funkcji.  
  
Aby skompilować wywoływania pliku wykonywalnego, należy połączyć z biblioteką importu. Jeśli używasz zewnętrznego pliku reguł programu make lub system kompilacji, należy określić nazwę pliku biblioteki importu, gdzie listę innych plikach obiektowych (.obj) lub bibliotek, które możesz połączyć.  
  
System operacyjny musi umożliwiać można zlokalizować pliku biblioteki DLL, podczas ładowania pliku wykonywalnego wywoływania. Oznacza to, czy aplikacja musi wdrożyć lub sprawdzał biblioteki DLL, gdy jest zainstalowana aplikacja.   
  
<a name="linking-explicitly"></a>  
  
## <a name="how-to-link-explicitly-to-a-dll"></a>Jak połączyć jawnie biblioteki DLL  
  
Aby korzystać z biblioteki DLL przez jawne tworzenie łączy, aplikacje należy wywołania jawnie załadować biblioteki DLL w czasie wykonywania funkcji. Aby jawnie utworzyć łącze do biblioteki DLL, aplikacja musi:  
  
-   Wywołaj [LoadLibrary](loadlibrary-and-afxloadlibrary.md), `LoadLibraryEx`, lub podobną funkcję, aby załadować biblioteki DLL i uzyskać uchwytu modułu.  
  
-   Wywołaj [GetProcAddress](getprocaddress.md) uzyskać wskaźnik funkcji do każdego wyeksportowane funkcja wywołująca aplikację. Ponieważ aplikacje wywoływać funkcje biblioteki DLL, za pomocą wskaźnika, kompilator nie generuje odwołania zewnętrzne, więc nie ma potrzeby do łączenia z biblioteką importu. Jednakże, konieczne jest posiadanie `typedef` lub `using` instrukcję, która definiuje sygnatury wywołania funkcji eksportowanych, które można wywoływać.   
  
-   Wywołaj [FreeLibrary](freelibrary-and-afxfreelibrary.md) po zakończeniu wprowadzania biblioteki DLL.  
  
Na przykład wywołuje tę przykładową funkcję `LoadLibrary` można załadować biblioteki DLL o nazwie "Mojadll" wywołuje `GetProcAddress` uzyskać wskaźnik do funkcji o nazwie "DLLFunc1" wywołuje funkcję i zapisuje wynik, a następnie wywołuje `FreeLibrary` wyładować bibliotekę DLL. 
  
```C  
#include "windows.h"

typedef HRESULT (CALLBACK* LPFNDLLFUNC1)(DWORD,UINT*);  

HRESULT LoadAndCallSomeFunction(DWORD dwParam1, UINT * puParam2)  
{
    HINSTANCE hDLL;               // Handle to DLL  
    LPFNDLLFUNC1 lpfnDllFunc1;    // Function pointer  
    HRESULT hrReturnVal;  
      
    hDLL = LoadLibrary("MyDLL");  
    if (NULL != hDLL)  
    {  
        lpfnDllFunc1 = (LPFNDLLFUNC1)GetProcAddress(hDLL, "DLLFunc1");  
        if (NULL != lpfnDllFunc1)  
        {  
            // call the function  
            hrReturnVal = lpfnDllFunc1(dwParam1, puParam2);  
        }  
        else  
        {  
            // report the error  
            hrReturnVal = ERROR_DELAY_LOAD_FAILED;  
        }
        FreeLibrary(hDLL);
    }
    else
    {
        hrReturnVal = ERROR_DELAY_LOAD_FAILED;
    }  
    return hrReturnVal;
}
```  
  
W odróżnieniu od w tym przykładzie w większości przypadków należy wywołać `LoadLibrary` i `FreeLibrary` tylko raz w aplikacji dla danej biblioteki DLL, zwłaszcza, jeśli chcesz wywołać wiele funkcji w bibliotece DLL, lub zadzwoń do biblioteki DLL funkcje wielokrotnie.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?  
  
-   [Praca z bibliotekami importowanymi oraz plikami eksportowanymi](../build/reference/working-with-import-libraries-and-export-files.md)  
  
-   [Kolejności przeszukiwania bibliotek dołączanych dynamicznie](/windows/desktop/Dlls/dynamic-link-library-search-order)  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki DLL w programie Visual C++](../build/dlls-in-visual-cpp.md)