---
title: "Łączenie pliku wykonywalnego z biblioteką DLL | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ffbb46c562daa213d91892b09e0938d7fd629132
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="link-an-executable-to-a-dll"></a>Łączenie pliku wykonywalnego z biblioteką DLL  
  
Plik wykonywalny łączy (lub ładuje) biblioteki DLL w jeden z dwóch sposobów:  
  
-   *Konsolidacja niejawna*, których system operacyjny ładuje bibliotekę DLL, po załadowaniu pliku wykonywalnego przy jego użyciu. Plik wykonywalny klienta wywołuje eksportowanych funkcji biblioteki dll, tak jakby funkcje były statycznie połączone i zawartych w pliku wykonywalnego. Konsolidacja niejawna jest czasami nazywany *statyczna obciążenia* lub *Konsolidacja dynamiczna czas ładowania*.  
  
-   *Konsolidacja jawna*, których system operacyjny ładuje bibliotekę DLL na żądanie w czasie wykonywania. Plik wykonywalny, który korzysta z biblioteki DLL przez łączenie jawne należy wywołania funkcji jawnie ładowanie i zwalnianie biblioteki DLL i uzyskać dostęp do funkcji wyeksportowane przez bibliotekę DLL. W przeciwieństwie do wywołania funkcji statycznie połączone biblioteki plik wykonywalny klienta należy wywołać eksportowane funkcje w bibliotece DLL za pomocą wskaźnika funkcji. Konsolidacja jawna jest czasami nazywany *dynamicznego obciążenia* lub *Konsolidacja dynamiczna w czasie wykonywania*.  
  
Plik wykonywalny albo połączeń metoda służy do odesłania do tego samego pliku DLL. Ponadto te metody nie wykluczają; jeden plik wykonywalny niejawnie można połączyć z biblioteki DLL i inny jawnie dołączyć do niego.  
  
<a name="determining-which-linking-method-to-use"></a>  
  
## <a name="determine-which-linking-method-to-use"></a>Określić jakiej metody łączenia użyć  
  
Konsolidacja niejawna lub Konsolidacja jawna jest architektury decyzji, które należy wykonać w aplikacji. Brak zalety i wady każdej metody.  
  
### <a name="implicit-linking"></a>Konsolidacja niejawna  
  
Konsolidacja niejawna występuje, gdy aplikacja kod wywołuje wyeksportowanej funkcji DLL. Kod źródłowy wywołanie pliku wykonywalnego jest kompilowany lub złożony, wywołanie funkcji DLL generuje odwołania do funkcji zewnętrznej w kodzie obiektu. Aby rozwiązać ten odwołanie zewnętrzne, aplikacji musi łączyć się z biblioteki importu (pliku lib), dostarczone przez producenta biblioteki dll.  
  
Importuj biblioteki zawiera tylko kod załadować biblioteki DLL i wdrożenie wywołania funkcji w bibliotece DLL. Znajdowanie funkcji zewnętrznej biblioteki importu informuje konsolidator, że kod dla tej funkcji jest w bibliotece DLL. Aby rozwiązać zewnętrznych odwołań do bibliotek DLL, konsolidator po prostu dodaje informacje do pliku wykonywalnego, który informuje system, gdzie można znaleźć kod biblioteki DLL, podczas uruchamiania procesu.  
  
Podczas uruchamiania systemu program, który zawiera dynamicznie połączony odwołania, używa informacji w pliku wykonywalnego programu zlokalizować wymagana biblioteki dll. Jeśli nie może odnaleźć biblioteki DLL, system kończy proces i wyświetla okno dialogowe, który zgłasza błąd. W przeciwnym razie system mapuje moduły biblioteki DLL do przestrzeni adresowej procesu.  
  
Jeśli którekolwiek z bibliotek DLL mieć funkcję punktu wejścia dla kodu inicjowanie i kończenie działania takie jak `DllMain`, system operacyjny wywołuje funkcję. Określa jeden z parametrów przekazanych do funkcji punkt wejścia kodu, który wskazuje plik DLL, który jest dołączenie do procesu. Jeśli funkcja punktu wejścia nie zwróci wartość TRUE, system kończy proces i zgłosi błąd.  
  
Na koniec system modyfikuje kodu wykonywalnego procesu, podaj adres początkowy dla funkcji DLL.  
  
Podobnie jak pozostałe kodu programu kod biblioteki DLL jest zamapowany do przestrzeni adresowej procesu podczas uruchamiania procesu i jest ładowany do pamięci tylko w razie potrzeby. W związku z tym `PRELOAD` i `LOADONCALL` kodu atrybutów używanych przez .def — pliki do kontroli ładowania w poprzednich wersjach systemu Windows nie będzie mieć znaczenie.  
  
### <a name="explicit-linking"></a>Konsolidacja jawna  
  
Większość aplikacji używa Konsolidacja niejawna, ponieważ jest to metoda easiest połączeń do użycia. Istnieją jednak razy, gdy konieczne jest konsolidacja jawna. Poniżej przedstawiono niektóre typowe przyczyny, aby użyć Konsolidacja jawna:  
  
-   Aplikacja nie może określić nazwy biblioteki DLL ładowaną do czasu wykonywania. Na przykład aplikacja może uzyskać nazwy biblioteki DLL i funkcje wyeksportowane z pliku konfiguracji podczas uruchamiania.  
  
-   Proces, który używa Konsolidacja niejawna zostało przerwane przez system operacyjny, jeśli biblioteka DLL nie zostanie znaleziony podczas uruchamiania procesu. Proces, który używa Konsolidacja jawna nie zostanie zakończony w tej sytuacji i spróbować odzyskać sprawność po błędzie. Na przykład proces może powiadamia użytkownika o błędzie i użytkownik, określ inną ścieżkę do pliku DLL.  
  
-   Proces, który używa Konsolidacja niejawna również zostanie zakończony, jeśli dowolny z bibliotek DLL jest połączona, mają `DllMain` funkcji, który zakończy się niepowodzeniem. Proces, który używa Konsolidacja jawna nie zostało przerwane w tej sytuacji.  
  
-   Aplikacja, która niejawnie łączy wiele bibliotek DLL może działać powoli, można uruchomić, ponieważ system Windows ładuje wszystkie biblioteki dll, podczas ładowania aplikacji. Aby zwiększyć wydajność uruchamiania, aplikację można połączyć niejawnie tylko te biblioteki DLL wymagane natychmiast po ładowania i poczekaj, aż inne biblioteki DLL są wymagane, aby utworzyć link do ich jawnie.  
  
-   Konsolidacja jawna eliminuje potrzebę łączenie aplikacji za pomocą biblioteki importu. Jeśli zmiany w bibliotece DLL powodują porządkowe eksportu zmienić, aplikacje używające Konsolidacja jawna nie trzeba Połącz ponownie, jeśli wywołanie `GetProcAddress` przy użyciu nazwy funkcji, a nie wartość porządkową, podczas gdy aplikacje używające Konsolidacja niejawna musi ponownie połączyć nową bibliotekę importu.  
  
Poniżej przedstawiono dwa zagrożenia Konsolidacja jawna pod uwagę:  
  
-   Jeśli plik DLL, który ma `DllMain` funkcję punktu wejścia, system operacyjny wywołuje funkcję w kontekście wątku, który wywołuje `LoadLibrary`. Funkcja punktu wejścia nie jest wywoływana, gdy biblioteka DLL jest już dołączony do procesu z powodu poprzedniego wywołania `LoadLibrary` który nie został bez odpowiedniego wywołania `FreeLibrary` funkcji. Konsolidacja jawna może spowodować problemy, jeśli korzysta z biblioteki DLL `DllMain` funkcji można wykonać inicjowania dla każdego wątku procesu, ponieważ już istnieje wątków podczas `LoadLibrary` (lub `AfxLoadLibrary`) jest nazywany nie jest zainicjowany.  
  
-   Jeśli biblioteki DLL deklaruje dane statyczne zakres jako `__declspec(thread)`, może spowodować błąd ochrony w przypadku jawnie połączone. Po załadowaniu przez wywołanie do biblioteki DLL `LoadLibrary`, powoduje błąd ochrony zawsze, gdy kod odwołuje się do tych danych. (Dane statyczne zakres obejmuje zarówno globalne i lokalne statycznych elementów). W związku z tym podczas tworzenia biblioteki DLL, należy albo unikać magazynu lokalnego wątku lub informować użytkowników DLL o potencjalnych problemów dynamiczne ładowanie biblioteki DLL. Aby uzyskać więcej informacji, zobacz [w bibliotece dll (SDK systemu Windows) przy użyciu magazynu lokalnego wątku](http://msdn.microsoft.com/library/windows/desktop/ms686997).  
  
<a name="linking-implicitly"></a>  
  
## <a name="how-to-link-implicitly-to-a-dll"></a>Jak połączyć niejawnie z biblioteki DLL  
  
Aby korzystać z biblioteki DLL przez łączenie niejawne, pliki wykonywalne klienta musi uzyskać te pliki z dostawcą biblioteki DLL:  
  
-   Co najmniej jeden nagłówek plików (.h) zawierające deklaracje wyeksportowane dane, funkcje i/lub klasy C++ w bibliotece DLL. Klasy, funkcje i danymi wyeksportowanymi przy biblioteki DLL muszą być oznaczone jako `__declspec(dllimport)` w pliku nagłówka. Aby uzyskać więcej informacji, zobacz [dllexport i dllimport](../cpp/dllexport-dllimport.md).  
  
-   Importuj biblioteki link do pliku wykonywalnego. Konsolidator tworzy bibliotekę importu, podczas tworzenia biblioteki DLL. Aby uzyskać więcej informacji, zobacz [. Plików LIB](../build/reference/dot-lib-files-as-linker-input.md).  
  
-   Rzeczywisty plik DLL.  
  
Aby korzystać z biblioteki DLL przez łączenie niejawne, plik wykonywalny musi zawierać pliki nagłówkowe, które deklaruje dane, funkcji lub klasy C++ wyeksportowane przez biblioteki DLL w każdej plik źródłowy, który zawiera wywołania wyeksportowane dane, funkcje i klasy. Z punktu widzenia kodowania wywołania funkcji wyeksportowanej są tak samo jak inne wywołanie funkcji.  
  
Aby utworzyć wywołanie pliku wykonywalnego, należy połączyć z biblioteki importu. Jeśli używasz zewnętrznego pliku reguł programu make lub systemu kompilacji, określ nazwę pliku biblioteki importu, gdy lista inne pliki obiektu (.obj) lub biblioteki, które połączyć.  
  
System operacyjny musi być zlokalizowany plik DLL ładuje wywołanie pliku wykonywalnego. Oznacza to, że aplikacji musi wdrożyć lub sprawdzenia istnienia biblioteki dll, po zainstalowaniu aplikacji.   
  
<a name="linking-explicitly"></a>  
  
## <a name="how-to-link-explicitly-to-a-dll"></a>Jak połączyć jawnie z biblioteki DLL  
  
Aby korzystać z biblioteki DLL przez łączenie jawne, aplikacje należy funkcji wywołanie w sposób jawny załadować biblioteki DLL w czasie wykonywania. Aby jawnie połączyć biblioteki DLL, aplikacja musi:  
  
-   Wywołanie [LoadLibrary](loadlibrary-and-afxloadlibrary.md), `LoadLibraryEx`, lub podobną funkcję, aby załadować biblioteki DLL i uzyskać uchwytu modułu.  
  
-   Wywołanie [GetProcAddress](getprocaddress.md) uzyskać wskaźnik funkcji do każdego wyeksportowane funkcja wywołująca aplikację. Ponieważ aplikacje wywołaniem funkcji DLL za pomocą wskaźnika kompilator nie generuje odwołań zewnętrznych, więc nie musi połączyć się z biblioteki importowanej. Jednak, musisz mieć `typedef` lub `using` instrukcji, która definiuje sygnatury wywołania wyeksportowanej funkcji, które należy wywołać.   
  
-   Wywołanie [FreeLibrary](freelibrary-and-afxfreelibrary.md) gdy odbywa się za pomocą biblioteki DLL.  
  
Na przykład, wywołania tej funkcji sample `LoadLibrary` można załadować biblioteki DLL o nazwie "Mojadll" wywołuje `GetProcAddress` uzyskać wskaźnika do funkcji o nazwie "DLLFunc1" wywołuje funkcję i zapisuje go, a następnie wywołuje `FreeLibrary` zwolnić biblioteki DLL. 
  
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
  
W odróżnieniu od w tym przykładzie, w większości przypadków należy wywołać `LoadLibrary` i `FreeLibrary` tylko jeden raz w aplikacji dla danej biblioteki DLL, szczególnie w przypadku, gdy ma się połączyć wiele funkcji w bibliotece DLL lub biblioteki DLL wywołania funkcji wielokrotnie.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [Praca z bibliotekami importowanymi oraz plikami eksportowanymi](../build/reference/working-with-import-libraries-and-export-files.md)  
  
-   [Ścieżka wyszukiwania używana przez system Windows do lokalizowania biblioteki DLL](../build/search-path-used-by-windows-to-locate-a-dll.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki dll w programie Visual C++](../build/dlls-in-visual-cpp.md)