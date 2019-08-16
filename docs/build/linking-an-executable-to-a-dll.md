---
title: Łączenie pliku wykonywalnego z biblioteką DLL
ms.date: 11/04/2016
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
ms.openlocfilehash: c4f9ea7a3606612189e85401b75a0577896fd90e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493226"
---
# <a name="link-an-executable-to-a-dll"></a>Łączenie pliku wykonywalnego z biblioteką DLL

Plik wykonywalny łączy się z (lub ładuje) do biblioteki DLL na jeden z dwóch sposobów:

- *Niejawne łączenie*, gdzie system operacyjny ładuje bibliotekę DLL, gdy plik wykonywalny, przy użyciu którego jest ładowany. Plik wykonywalny klienta wywołuje eksportowane funkcje biblioteki DLL tak, jakby funkcje były statycznie połączone i zawarte w pliku wykonywalnym. Niejawne łączenie jest czasami określane jako *statyczne ładowanie* lub *dynamiczne łączenie w czasie ładowania*.

- *Jawne łączenie*, gdzie system operacyjny ładuje bibliotekę DLL na żądanie w czasie wykonywania. Plik wykonywalny, który korzysta z biblioteki DLL przez jawne łączenie musi wykonywać wywołania funkcji w celu jawnego ładowania i zwalniania biblioteki DLL oraz do uzyskiwania dostępu do funkcji wyeksportowanych przez DLL. W przeciwieństwie do wywołań funkcji w bibliotece połączonej statycznie plik wykonywalny klienta musi wywoływać eksportowane funkcje w bibliotece DLL za pomocą wskaźnika funkcji. Jawne łączenie jest czasami określane jako *dynamiczne ładowanie* lub *dynamiczne łączenie w czasie wykonywania*.

Plik wykonywalny może używać metody łączenia do łączenia z tą samą biblioteką DLL. Ponadto te metody nie wykluczają się wzajemnie. jeden plik wykonywalny może być niejawnie połączony z biblioteką DLL i może być jawnie dołączany do niego.

<a name="determining-which-linking-method-to-use"></a>

## <a name="link-an-executable-to-a-dll"></a>Łączenie pliku wykonywalnego z biblioteką DLL

Czy używać niejawnego łączenia lub jawnego łączenia to decyzja architektury, którą należy podjąć w przypadku aplikacji. Każda metoda ma zalety i wady.

### <a name="implicit-linking"></a>Niejawne łączenie

Niejawne łączenie występuje, gdy kod aplikacji wywołuje wyeksportowaną funkcję DLL. Gdy kod źródłowy wywołującego pliku wykonywalnego jest kompilowany lub montowany, wywołanie funkcji DLL generuje odwołanie do funkcji zewnętrznej w kodzie obiektu. Aby można było rozpoznać to odwołanie zewnętrzne, aplikacja musi połączyć się z biblioteką importu (plik. lib) dostarczoną przez twórcę biblioteki DLL.

Biblioteka importowa zawiera tylko kod do załadowania biblioteki DLL i zaimplementowania wywołań funkcji w bibliotece DLL. Znalezienie zewnętrznej funkcji w bibliotece import informuje konsolidator, że kod tej funkcji znajduje się w bibliotece DLL. Aby rozpoznać odwołania zewnętrzne do bibliotek DLL, konsolidator po prostu dodaje informacje do pliku wykonywalnego, który informuje system, gdzie znaleźć kod biblioteki DLL podczas uruchamiania procesu.

Gdy system uruchamia program, który zawiera dynamicznie połączone odwołania, używa informacji w pliku wykonywalnym programu w celu zlokalizowania wymaganych bibliotek DLL. Jeśli nie można zlokalizować biblioteki DLL, system kończy proces i wyświetla okno dialogowe, które zgłasza błąd. W przeciwnym razie system mapuje moduły DLL na przestrzeń adresową procesu.

Jeśli dowolna z bibliotek DLL ma funkcję punktu wejścia do inicjacji i zakończenia kodu `DllMain`, np., system operacyjny wywołuje funkcję. Jeden z parametrów przesłanych do funkcji punktu wejścia określa kod, który wskazuje, że biblioteka DLL jest dołączana do procesu. Jeśli funkcja punktu wejścia nie zwraca wartości TRUE, system zakończy proces i zgłosi błąd.

Na koniec system modyfikuje kod wykonywalny procesu, aby zapewnić początkowe adresy dla funkcji DLL.

Podobnie jak w przypadku reszty kodu programu, kod biblioteki DLL jest mapowany do przestrzeni adresowej procesu podczas uruchamiania procesu i jest ładowany do pamięci tylko wtedy, gdy jest to konieczne. W rezultacie `PRELOAD` `LOADONCALL` atrybuty kodu używane przez pliki. def do kontrolowania ładowania w poprzednich wersjach systemu Windows nie mają już znaczenia.

### <a name="explicit-linking"></a>Jawne łączenie

Większość aplikacji używa niejawnego łączenia, ponieważ jest to najprostsza metoda łączenia. Jednak istnieją sytuacje, w których wymagane jest jawne łączenie. Poniżej przedstawiono kilka typowych powodów użycia jawnego łączenia:

- Aplikacja nie zna nazwy biblioteki DLL ładowanej do czasu wykonywania. Na przykład aplikacja może uzyskać nazwę biblioteki DLL i eksportowane funkcje z pliku konfiguracji podczas uruchamiania.

- Proces, który używa niejawnego łączenia, zostaje zakończony przez system operacyjny, jeśli nie można odnaleźć biblioteki DLL podczas uruchamiania procesu. Proces używający jawnego łączenia nie jest zakończony w tej sytuacji i może próbować odzyskać sprawność po błędzie. Na przykład proces może powiadomić użytkownika o błędzie i określić inną ścieżkę do biblioteki DLL.

- Proces, który używa niejawnego łączenia, również zostaje zakończony, jeśli dowolna z bibliotek DLL, `DllMain` z którym jest połączona, zawiera funkcję, która nie powiodła się. Proces używający jawnego łączenia nie jest zakończony w tej sytuacji.

- Aplikacja, która niejawnie łączy się z wieloma bibliotekami DLL, może być wolnie uruchamiana, ponieważ system Windows ładuje wszystkie biblioteki DLL po załadowaniu aplikacji. Aby zwiększyć wydajność uruchamiania, aplikacja może połączyć się niejawnie tylko z tymi bibliotekami DLL, które są wymagane natychmiast po załadowaniu, i poczekaj, aż inne biblioteki DLL są wymagane do jawnego łączenia z nimi.

- Jawne łączenie eliminuje konieczność łączenia aplikacji za pomocą biblioteki importu. Jeśli zmiany w bibliotece DLL powodują zmianę liczby porządkowej eksportu, aplikacje używające jawnego łączenia nie muszą ponownie łączyć się w przypadku wywołania `GetProcAddress` przy użyciu nazwy funkcji i nie wartości porządkowej, natomiast aplikacje, które używają niejawnego łączenia, muszą ponownie połączyć się z Nowa biblioteka importu.

Poniżej przedstawiono dwa zagrożenia związane z jawnym łączeniem:

- Jeśli biblioteka DLL ma `DllMain` funkcję punktu wejścia, system operacyjny wywołuje funkcję w kontekście wątku, który wywołał. `LoadLibrary` Funkcja punktu wejścia nie jest wywoływana, jeśli biblioteka DLL jest już dołączona do procesu ze względu na poprzednie wywołanie `LoadLibrary` , które nie miało odpowiadającego wywołania `FreeLibrary` funkcji. Jawne łączenie może spowodować problemy, jeśli biblioteka DLL używa `DllMain` funkcji do wykonania inicjalizacji dla każdego wątku procesu, ponieważ wątki, które już istnieją `LoadLibrary` , gdy `AfxLoadLibrary`(lub) są wywoływane nie są inicjowane.

- Jeśli biblioteka DLL deklaruje dane z zakresu statycznego jako `__declspec(thread)`, może to spowodować błąd ochrony, jeśli zostanie jawnie połączona. Po załadowaniu pliku DLL przez wywołanie do `LoadLibrary`programu powoduje ono błąd ochrony zawsze wtedy, gdy kod odwołuje się do tych danych. (Dane zakresu statycznego obejmują zarówno globalne, jak i lokalne elementy statyczne). W związku z tym podczas tworzenia biblioteki DLL należy unikać używania lokalnego magazynu wątków lub poinformować użytkowników DLL o potencjalną pułapek dynamicznej ładowania biblioteki DLL. Aby uzyskać więcej informacji, zobacz [Używanie lokalnego magazynu wątków w bibliotece dołączanej dynamicznie (Windows SDK)](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library).

<a name="linking-implicitly"></a>

## <a name="link-an-executable-to-a-dll"></a>Łączenie pliku wykonywalnego z biblioteką DLL

Aby skorzystać z biblioteki DLL przez niejawne konsolidacje, pliki wykonywalne klienta muszą uzyskać tych plików od dostawcy biblioteki DLL:

- Jeden lub więcej plików nagłówkowych (plików h), które zawierają deklaracje wyeksportowanych danych, funkcji i/ C++ lub klas w bibliotece DLL. Klasy, funkcje i dane eksportowane przez bibliotekę DLL muszą być oznaczone jako `__declspec(dllimport)` plik nagłówkowy. Aby uzyskać więcej informacji, zobacz [dllexport, dllimport](../cpp/dllexport-dllimport.md).

- Biblioteka importowana do połączenia w pliku wykonywalnym. Konsolidator tworzy bibliotekę importu podczas kompilowania biblioteki DLL. Aby uzyskać więcej informacji, zobacz [. Pliki LIB](reference/dot-lib-files-as-linker-input.md).

- Rzeczywisty plik DLL.

Aby użyć biblioteki DLL przez niejawne łączenie, plik wykonywalny musi zawierać pliki nagłówkowe, które deklarują dane C++ , funkcje lub klasy eksportowane przez DLL w każdym pliku źródłowym, który zawiera wywołania wyeksportowanych danych, funkcji i klas. Z punktu widzenia kodowania wywołania eksportowanych funkcji są podobne do innych wywołań funkcji.

Aby skompilować wywołujący plik wykonywalny, należy połączyć się z biblioteką importu. Jeśli używasz zewnętrznego systemu plików reguł programu make lub kompilacji, określ nazwę pliku biblioteki importu, w której będą się łączyć inne pliki lub biblioteki obiektów (. obj).

System operacyjny musi być w stanie zlokalizować plik DLL podczas ładowania wywołującego pliku wykonywalnego. Oznacza to, że aplikacja musi wdrożyć lub sprawdzić istnienie biblioteki DLL, gdy aplikacja jest zainstalowana.

<a name="linking-explicitly"></a>

## <a name="how-to-link-explicitly-to-a-dll"></a>Jak jawnie łączyć się z biblioteką DLL

Aby użyć biblioteki DLL przez jawne łączenie, aplikacje muszą wykonać wywołanie funkcji, aby jawnie załadować bibliotekę DLL w czasie wykonywania. Aby jawnie połączyć się z biblioteką DLL, aplikacja musi:

- Wywołaj metodę `LoadLibraryEx` [LoadLibrary](loadlibrary-and-afxloadlibrary.md)lub podobną funkcję w celu załadowania biblioteki DLL i uzyskania dojścia do modułu.

- Wywołaj funkcję [GetProcAddress](getprocaddress.md) , aby uzyskać wskaźnik funkcji do każdej wyeksportowanej funkcji, która jest wywoływana przez aplikację. Ponieważ aplikacje wywołują funkcje DLL za pomocą wskaźnika, kompilator nie generuje odwołań zewnętrznych, dlatego nie ma potrzeby łączenia z biblioteką importu. Jednak należy mieć `typedef` instrukcję or `using` , która definiuje sygnaturę wywołania wyeksportowanych funkcji, które są wywoływane.

- Wywołaj [FreeLibrary](freelibrary-and-afxfreelibrary.md) po zakończeniu z biblioteką DLL.

Na przykład Ta przykładowa funkcja wywołuje `LoadLibrary` do załadowania biblioteki DLL o nazwie "MyDLL" `GetProcAddress` , wywołuje, aby uzyskać wskaźnik do funkcji o nazwie "DLLFunc1", wywołuje funkcję i zapisuje wynik, a następnie wywołuje `FreeLibrary` metodę zwolnienia biblioteki DLL.

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

W przeciwieństwie do tego przykładu, w większości przypadków należy `LoadLibrary` wywoływać i `FreeLibrary` tylko raz w aplikacji dla danej biblioteki DLL, zwłaszcza jeśli chcesz wielokrotnie wywoływać wiele funkcji w bibliotece DLL lub wywołać funkcje DLL.

## <a name="what-do-you-want-to-know-more-about"></a>Jak chcesz dowiedzieć się więcej?

- [Praca z bibliotekami importowanymi oraz plikami eksportowanymi](reference/working-with-import-libraries-and-export-files.md)

- [Kolejność wyszukiwania biblioteki dołączanej dynamicznie](/windows/win32/Dlls/dynamic-link-library-search-order)

## <a name="see-also"></a>Zobacz także

[Tworzenie C/C++ dll w Visual Studio](dlls-in-visual-cpp.md)
