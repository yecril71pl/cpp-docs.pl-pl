---
title: Łączenie pliku wykonywalnego z biblioteką DLL
ms.date: 08/22/2019
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
ms.openlocfilehash: 2f907fedcaaf9897749ee0eb6a7ea5a33e1af679
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821385"
---
# <a name="link-an-executable-to-a-dll"></a>Łączenie pliku wykonywalnego z biblioteką DLL

Plik wykonywalny łączy się z (lub ładuje) do biblioteki DLL na jeden z dwóch sposobów:

- *Niejawne łączenie*, gdzie system operacyjny ładuje bibliotekę DLL w tym samym czasie, co plik wykonywalny, który go używa. Plik wykonywalny klienta wywołuje wyeksportowane funkcje biblioteki DLL w taki sam sposób jak w przypadku, gdy funkcje zostały statycznie połączone i zawarte w pliku wykonywalnym. Niejawne łączenie jest czasami określane jako *statyczne ładowanie* lub *dynamiczne łączenie w czasie ładowania*.

- *Jawne łączenie*, gdzie system operacyjny ładuje bibliotekę DLL na żądanie w czasie wykonywania. Plik wykonywalny, który korzysta z biblioteki DLL przez jawne łączenie, musi jawnie ładować i zwalniać bibliotekę DLL. Musi również skonfigurować wskaźnik funkcji, aby uzyskać dostęp do każdej funkcji, która używa z biblioteki DLL. W przeciwieństwie do wywołań funkcji w bibliotece połączonej statycznie lub niejawnie połączonej biblioteki DLL, plik wykonywalny klienta musi wywoływać eksportowane funkcje w jawnie połączonej bibliotece DLL za pomocą wskaźników funkcji. Jawne łączenie jest czasami określane jako *dynamiczne ładowanie* lub *dynamiczne łączenie w czasie wykonywania*.

Plik wykonywalny może używać metody łączenia do łączenia z tą samą biblioteką DLL. Ponadto te metody nie wykluczają się wzajemnie. jeden plik wykonywalny może być niejawnie połączony z biblioteką DLL, a inny może zostać jawnie dołączony do niego.

<a name="determining-which-linking-method-to-use"></a>

## <a name="determine-which-linking-method-to-use"></a>Określanie, która Metoda łączenia ma być używana

Czy używać niejawnego łączenia lub jawnego łączenia to decyzja architektury, którą należy podjąć w przypadku aplikacji. Każda metoda ma zalety i wady.

### <a name="implicit-linking"></a>Niejawne łączenie

Niejawne łączenie występuje, gdy kod aplikacji wywołuje wyeksportowaną funkcję DLL. Gdy kod źródłowy wywołującego pliku wykonywalnego jest kompilowany lub montowany, wywołanie funkcji DLL generuje odwołanie do funkcji zewnętrznej w kodzie obiektu. Aby można było rozpoznać to odwołanie zewnętrzne, aplikacja musi połączyć się z biblioteką importu (plik. lib) dostarczoną przez twórcę biblioteki DLL.

Biblioteka importowa zawiera tylko kod do załadowania biblioteki DLL i zaimplementowania wywołań funkcji w bibliotece DLL. Znalezienie zewnętrznej funkcji w bibliotece import informuje konsolidator, że kod tej funkcji znajduje się w bibliotece DLL. Aby rozpoznać odwołania zewnętrzne do bibliotek DLL, konsolidator po prostu dodaje informacje do pliku wykonywalnego, który informuje system, gdzie znaleźć kod biblioteki DLL podczas uruchamiania procesu.

Gdy system uruchamia program, który zawiera dynamicznie połączone odwołania, używa informacji w pliku wykonywalnym programu w celu zlokalizowania wymaganych bibliotek DLL. Jeśli nie można zlokalizować biblioteki DLL, system zakończy proces i wyświetli okno dialogowe, które zgłosi błąd. W przeciwnym razie system mapuje moduły DLL na przestrzeń adresową procesu.

Jeśli dowolna z bibliotek DLL ma funkcję punktu wejścia do inicjacji i zakończenia kodu, takiej jak `DllMain`, system operacyjny wywoła funkcję. Jeden z parametrów przesłanych do funkcji punktu wejścia określa kod, który wskazuje, że biblioteka DLL jest dołączana do procesu. Jeśli funkcja punktu wejścia nie zwraca wartości TRUE, system zakończy proces i zgłosi błąd.

Na koniec system modyfikuje kod wykonywalny procesu, aby zapewnić początkowe adresy dla funkcji DLL.

Podobnie jak w przypadku reszty kodu programu, moduł ładujący mapuje kod DLL do przestrzeni adresowej procesu podczas uruchamiania procesu. System operacyjny ładuje go do pamięci tylko wtedy, gdy jest to konieczne. W rezultacie atrybuty kodu `PRELOAD` i `LOADONCALL` używane przez pliki. def do kontrolowania ładowania w poprzednich wersjach systemu Windows nie mają już znaczenia.

### <a name="explicit-linking"></a>Jawne łączenie

Większość aplikacji używa niejawnego łączenia, ponieważ jest to najprostsza metoda łączenia. Jednak istnieją sytuacje, w których wymagane jest jawne łączenie. Poniżej przedstawiono kilka typowych powodów użycia jawnego łączenia:

- Aplikacja nie zna nazwy biblioteki DLL ładowanej do czasu wykonywania. Na przykład aplikacja może uzyskać nazwę biblioteki DLL i eksportowane funkcje z pliku konfiguracji podczas uruchamiania.

- Proces, który używa niejawnego łączenia, zostaje zakończony przez system operacyjny, jeśli nie można odnaleźć biblioteki DLL podczas uruchamiania procesu. Proces używający jawnego łączenia nie jest zamykany w tej sytuacji i może próbować odzyskać sprawność po błędzie. Na przykład proces może powiadomić użytkownika o błędzie i określić inną ścieżkę do biblioteki DLL.

- Proces, który używa niejawnego łączenia, zostaje również zakończony, jeśli dowolna z bibliotek DLL, z którym jest połączona, zawiera funkcję `DllMain`, która kończy się niepowodzeniem. Proces używający jawnego łączenia nie jest zamykany w tej sytuacji.

- Aplikacja, która niejawnie łączy się z wieloma bibliotekami DLL, może być wolnie uruchamiana, ponieważ system Windows ładuje wszystkie biblioteki DLL po załadowaniu aplikacji. Aby zwiększyć wydajność uruchamiania, aplikacja może używać tylko niejawnego łączenia bibliotek DLL wymaganych natychmiast po załadowaniu. Może używać jawnego łączenia do ładowania innych bibliotek DLL tylko wtedy, gdy są one niezbędne.

- Jawne łączenie eliminuje konieczność łączenia aplikacji za pomocą biblioteki importu. Jeśli zmiany w bibliotece DLL powodują zmianę liczby porządkowej eksportu, aplikacje nie muszą ponownie łączyć się, jeśli wywołują `GetProcAddress` przy użyciu nazwy funkcji, a nie wartości porządkowej. Aplikacje korzystające z niejawnego łączenia muszą nadal ponownie łączyć się z zmienioną biblioteką importu.

Poniżej przedstawiono dwa zagrożenia związane z jawnym łączeniem:

- Jeśli biblioteka DLL ma funkcję punktu wejścia `DllMain`, system operacyjny wywołuje funkcję w kontekście wątku, który wywołał `LoadLibrary`. Funkcja punktu wejścia nie jest wywoływana, jeśli biblioteka DLL jest już dołączona do procesu ze względu na poprzednie wywołanie `LoadLibrary`, które nie ma odpowiadającego wywołania funkcji `FreeLibrary`. Jawne konsolidacje mogą spowodować problemy, jeśli biblioteka DLL używa funkcji `DllMain` do zainicjowania każdego wątku procesu, ponieważ wszystkie wątki, które już istnieją w przypadku wywołania `LoadLibrary` (lub `AfxLoadLibrary`) nie zostały zainicjowane.

- Jeśli biblioteka DLL deklaruje dane z zakresu statycznego jako `__declspec(thread)`, może to spowodować błąd ochrony, jeśli jest jawnie połączony. Gdy biblioteka DLL zostanie załadowana przez wywołanie do `LoadLibrary`, powoduje błąd ochrony zawsze wtedy, gdy kod odwołuje się do tych danych. (Dane zakresu statycznego obejmują zarówno globalne, jak i lokalne elementy statyczne). Dlatego podczas tworzenia biblioteki DLL należy unikać używania magazynu wątków lokalnych. Jeśli nie jest to możliwe, Powiadom użytkowników biblioteki DLL o potencjalną pułapek dynamicznej ładowania biblioteki DLL. Aby uzyskać więcej informacji, zobacz [Używanie lokalnego magazynu wątków w bibliotece dołączanej dynamicznie (Windows SDK)](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library).

<a name="linking-implicitly"></a>

## <a name="how-to-use-implicit-linking"></a>Jak używać niejawnego łączenia

Aby skorzystać z biblioteki DLL przez niejawne konsolidacje, pliki wykonywalne klienta muszą uzyskać tych plików od dostawcy biblioteki DLL:

- Jeden lub więcej plików nagłówkowych (plików h), które zawierają deklaracje wyeksportowanych danych, funkcji i C++ klas w bibliotece DLL. Klasy, funkcje i dane eksportowane przez bibliotekę DLL muszą być oznaczone jako `__declspec(dllimport)` w pliku nagłówkowym. Aby uzyskać więcej informacji, zobacz [dllexport, dllimport](../cpp/dllexport-dllimport.md).

- Biblioteka importowana do połączenia w pliku wykonywalnym. Konsolidator tworzy bibliotekę importu podczas kompilowania biblioteki DLL. Aby uzyskać więcej informacji, zobacz [lib plików jako dane wejściowe konsolidatora](reference/dot-lib-files-as-linker-input.md).

- Rzeczywisty plik DLL.

Aby użyć danych, funkcji i klas w bibliotece DLL przez niejawne łączenie, każdy plik źródłowy klienta musi zawierać pliki nagłówkowe, które je deklarują. Z punktu widzenia kodowania wywołania eksportowanych funkcji są podobne do innych wywołań funkcji.

Aby skompilować plik wykonywalny klienta, należy połączyć z biblioteką importu biblioteki DLL. W przypadku korzystania z zewnętrznego pliku reguł programu make lub systemu kompilacji należy określić bibliotekę importu wraz z innymi plikami obiektów lub bibliotekami, które są łączone.

System operacyjny musi być w stanie zlokalizować plik DLL podczas ładowania wywołującego pliku wykonywalnego. Oznacza to, że podczas instalowania aplikacji należy wdrożyć lub sprawdzić istnienie biblioteki DLL.

<a name="linking-explicitly"></a>

## <a name="how-to-link-explicitly-to-a-dll"></a>Jak jawnie łączyć się z biblioteką DLL

Aby użyć biblioteki DLL przez jawne łączenie, aplikacje muszą wykonać wywołanie funkcji, aby jawnie załadować bibliotekę DLL w czasie wykonywania. Aby jawnie połączyć się z biblioteką DLL, aplikacja musi:

- Wywołaj [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) lub podobną funkcję, aby załadować bibliotekę DLL i uzyskać uchwyt modułu.

- Wywołaj funkcję [GetProcAddress](getprocaddress.md) , aby uzyskać wskaźnik funkcji do każdej wyeksportowanej funkcji, która jest wywoływana przez aplikację. Ponieważ aplikacje wywołują funkcje DLL za pomocą wskaźnika, kompilator nie generuje odwołań zewnętrznych, dlatego nie ma potrzeby łączenia z biblioteką importu. Jednakże należy mieć instrukcję `typedef` lub `using`, która definiuje sygnaturę wywołania wyeksportowanych funkcji.

- Wywołaj [FreeLibrary](freelibrary-and-afxfreelibrary.md) po zakończeniu z biblioteką DLL.

Na przykład Ta przykładowa funkcja wywołuje `LoadLibrary` do załadowania biblioteki DLL o nazwie "MyDLL", wywołuje `GetProcAddress`, aby uzyskać wskaźnik do funkcji o nazwie "DLLFunc1", wywołuje funkcję i zapisuje wynik, a następnie wywołuje `FreeLibrary` do zwolnienia biblioteki DLL.

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

W przeciwieństwie do tego przykładu, w większości przypadków należy wywoływać `LoadLibrary` i `FreeLibrary` tylko raz w aplikacji dla danej biblioteki DLL. Jest to szczególnie prawdziwe, jeśli chcesz wywołać wiele funkcji w bibliotece DLL lub wielokrotnie wywoływać funkcje DLL.

## <a name="what-do-you-want-to-know-more-about"></a>Jak chcesz dowiedzieć się więcej?

- [Praca z bibliotekami importowanymi oraz plikami eksportowanymi](reference/working-with-import-libraries-and-export-files.md)

- [Kolejność wyszukiwania biblioteki dołączanej dynamicznie](/windows/win32/Dlls/dynamic-link-library-search-order)

## <a name="see-also"></a>Zobacz także

[Tworzenie C/C++ dll w Visual Studio](dlls-in-visual-cpp.md)
