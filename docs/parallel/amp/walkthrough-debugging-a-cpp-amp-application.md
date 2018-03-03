---
title: "Wskazówki: Debugowanie aplikacji C++ AMP | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- debugging, C++ Accelerated Massive Parallelism
- C++ AMP, debugging
- C++ Accelerated Massive Parallelism, debugging
- debugging, C++ AMP
ms.assetid: 40e92ecc-f6ba-411c-960c-b3047b854fb5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8cfc12a238ccaff90fa7c22e8a67d8e10d0796e6
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="walkthrough-debugging-a-c-amp-application"></a>Wskazówki: debugowanie aplikacji C++ AMP
W tym temacie przedstawiono sposób debugowania aplikacji, która używa C++ Accelerated Massive Parallelism (C++ AMP), aby móc korzystać z procesor graficzny (GPU). Używa programu redukcji równoległe podsumowuje dużą tablicę liczb całkowitych. W instruktażu przedstawiono następujące zagadnienia:  
  
-   Uruchamianie debugera GPU.  
  
-   Sprawdzanie wątki GPU okno wątków GPU.  
  
-   Korzystanie z okna stosów równoległych jednocześnie obserwować stosy wywołań wielu wątków GPU.  
  
-   Korzystanie z okna czujki równoległej do zbadania wartości pojedyncze wyrażenie przez wiele wątków jednocześnie.  
  
-   Flagowanie, zamrażanie rozgrzewania i grupowanie wątków GPU.  
  
-   Wykonywanie wszystkie wątki kafelka do określonej lokalizacji w kodzie.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Przed skorzystaniem z tego przewodnika:  
  
-   Odczyt [Przegląd C++ AMP](../../parallel/amp/cpp-amp-overview.md).  
  
-   Upewnij się, że wiersz liczby są wyświetlane w edytorze tekstu. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie numerów wierszy w edytorze](/visualstudio/ide/reference/how-to-display-line-numbers-in-the-editor).  
  
-   Upewnij się, że używasz [!INCLUDE[win8](../../build/reference/includes/win8_md.md)] lub [!INCLUDE[winserver8](../../build/reference/includes/winserver8_md.md)] do obsługi debugowania na emulator oprogramowania.  
  
 [!INCLUDE[note_settings_general](../../mfc/includes/note_settings_general_md.md)]  
  
### <a name="to-create-the-sample-project"></a>Aby utworzyć przykładowy projekt  
  
1.  Uruchom program Visual Studio.  
  
2.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
3.  W obszarze **zainstalowana** w okienku szablonów wybierz **Visual C++**.  
  
4.  Wybierz **aplikacji konsoli Win32**, typ `AMPMapReduce` w **nazwa** polu, a następnie wybierz pozycję **OK** przycisku.  
  
5.  Wybierz **dalej** przycisku.  
  
6.  Wyczyść **Prekompilowanego nagłówka** pole wyboru, a następnie wybierz pozycję **Zakończ** przycisku.  
  
7.  W **Eksploratora rozwiązań**, usunąć stdafx.h, targetver.h i stdafx.cpp z projektu.  
  
8.  Otwórz AMPMapReduce.cpp i zastąp jego zawartość następującym kodem.  
  
 ```cpp  
    // AMPMapReduce.cpp defines the entry point for the program.  
    // The program performs a parallel-sum reduction that computes the sum of an array of integers.   
  
    #include <stdio.h>  
    #include <tchar.h>  
    #include <amp.h>  
  
    const int BLOCK_DIM = 32;  
  
    using namespace concurrency;  
  
    void sum_kernel_tiled(tiled_index<BLOCK_DIM> t_idx, array<int, 1> &A, int stride_size) restrict(amp)  
    {  
        tile_static int localA[BLOCK_DIM];  
  
        index<1> globalIdx = t_idx.global * stride_size;  
        index<1> localIdx = t_idx.local;  
  
        localA[localIdx[0]] =  A[globalIdx];  
  
        t_idx.barrier.wait();  
  
        // Aggregate all elements in one tile into the first element.  
        for (int i = BLOCK_DIM / 2; i > 0; i /= 2)   
        {  
            if (localIdx[0] < i)   
            {  
  
                localA[localIdx[0]] += localA[localIdx[0] + i];  
            }  
  
            t_idx.barrier.wait();  
        }  
  
        if (localIdx[0] == 0)  
        {  
            A[globalIdx] = localA[0];  
        }  
    }  
  
    int size_after_padding(int n)  
    {  
        // The extent might have to be slightly bigger than num_stride to   
        // be evenly divisible by BLOCK_DIM. You can do this by padding with zeros.  
        // The calculation to do this is BLOCK_DIM * ceil(n / BLOCK_DIM)  
        return ((n - 1) / BLOCK_DIM + 1) * BLOCK_DIM;  
    }  
  
    int reduction_sum_gpu_kernel(array<int, 1> input)   
    {  
        int len = input.extent[0];  
  
        //Tree-based reduction control that uses the CPU.  
        for (int stride_size = 1; stride_size < len; stride_size *= BLOCK_DIM)   
        {  
            // Number of useful values in the array, given the current  
            // stride size.  
            int num_strides = len / stride_size;    
  
            extent<1> e(size_after_padding(num_strides));  
  
            // The sum kernel that uses the GPU.  
            parallel_for_each(extent<1>(e).tile<BLOCK_DIM>(), [&input, stride_size] (tiled_index<BLOCK_DIM> idx) restrict(amp)  
            {  
                sum_kernel_tiled(idx, input, stride_size);  
            });  
        }  
  
        array_view<int, 1> output = input.section(extent<1>(1));  
        return output[0];  
    }  
  
    int cpu_sum(const std::vector<int> &arr) {  
        int sum = 0;  
        for (size_t i = 0; i < arr.size(); i++) {  
            sum += arr[i];  
        }  
        return sum;  
    }  
  
    std::vector<int> rand_vector(unsigned int size) {  
        srand(2011);  
  
        std::vector<int> vec(size);  
        for (size_t i = 0; i < size; i++) {  
            vec[i] = rand();  
        }  
        return vec;  
    }  
  
    array<int, 1> vector_to_array(const std::vector<int> &vec) {  
        array<int, 1> arr(vec.size());  
        copy(vec.begin(), vec.end(), arr);  
        return arr;  
    }  
  
    int _tmain(int argc, _TCHAR* argv[])  
    {  
        std::vector<int> vec = rand_vector(10000);  
        array<int, 1> arr = vector_to_array(vec);  
  
        int expected = cpu_sum(vec);  
        int actual = reduction_sum_gpu_kernel(arr);  
  
        bool passed = (expected == actual);  
        if (!passed) {  
            printf("Actual (GPU): %d, Expected (CPU): %d", actual, expected);  
        }  
        printf("sum: %s\n", passed  "Passed!" : "Failed!");   
  
        getchar();  
  
        return 0;  
    }  
  
 ```  
  
9. Na pasku menu wybierz **pliku**, **Zapisz wszystko**.  
  
10. W **Eksploratora rozwiązań**, otwórz menu skrótów **AMPMapReduce**, a następnie wybierz pozycję **właściwości**.  
  
11. W **strony właściwości** okna dialogowego, w obszarze **właściwości konfiguracji**, wybierz **C/C++**, **prekompilowanych nagłówków**.  
  
12. Dla **Prekompilowanego nagłówka** właściwości, wybierz opcję **nie przy użyciu prekompilowanych nagłówków**, a następnie wybierz pozycję **OK** przycisku.  
  
13. Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**.  
  
## <a name="debugging-the-cpu-code"></a>Debugowanie kodu Procesora  
 W tej procedurze lokalnego debugera systemu Windows umożliwia upewnij się, że kod procesora CPU w tej aplikacji jest prawidłowa. Segment kodu procesora CPU w tej aplikacji, która jest szczególnie interesujące jest `for` pętli w `reduction_sum_gpu_kernel` funkcji. Kontroluje skrócenie równoległych oparta na drzewie uruchamianego na procesorze GPU.  
  
### <a name="to-debug-the-cpu-code"></a>Do debugowania kodu Procesora  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów **AMPMapReduce**, a następnie wybierz pozycję **właściwości**.  
  
2.  W **strony właściwości** okna dialogowego, w obszarze **właściwości konfiguracji**, wybierz **debugowanie**. Sprawdź, czy **lokalnego debugera systemu Windows** wybrano **debugera, aby uruchomić** listy.  
  
3.  Powrócić do edytora kodu.  
  
4.  Ustaw punkty przerwania w wierszach kodu pokazano na poniższej ilustracji (około wierszy 67 wiersz 70).  
  
     ![Punkty przerwania Procesora](../../parallel/amp/media/campcpubreakpoints.png "campcpubreakpoints")  
Punkty przerwania Procesora  
  
5.  Na pasku menu wybierz **debugowania**, **Rozpocznij debugowanie**.  
  
6.  W **zmiennych lokalnych** okna, sprawdź wartość `stride_size` aż do osiągnięcia punktu przerwania w wierszu 70.  
  
7.  Na pasku menu wybierz **debugowania**, **Zatrzymaj debugowanie**.  
  
## <a name="debugging-the-gpu-code"></a>Debugowanie kodu GPU  
 W tej sekcji przedstawiono sposób debugowania kodu procesora GPU, który jest kod źródłowy znajdujący się w `sum_kernel_tiled` funkcji. Kodu GPU oblicza sumę liczb całkowitych dla każdego "bloku" równolegle.  
  
### <a name="to-debug-the-gpu-code"></a>Debugowanie kodu GPU  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów **AMPMapReduce**, a następnie wybierz pozycję **właściwości**.  
  
2.  W **strony właściwości** okna dialogowego, w obszarze **właściwości konfiguracji**, wybierz **debugowanie**.  
  
3.  W **debugera, aby uruchomić** listy, wybierz **lokalnego debugera systemu Windows**.  
  
4.  W **typ debugera** listy, wybierz **GPU tylko**.  
  
5.  Wybierz **OK** przycisku.  
  
6.  Ustaw punkt przerwania w wierszu 30, jak pokazano na poniższej ilustracji.  
  
     ![Punkty przerwania procesora GPU](../../parallel/amp/media/campgpubreakpoints.png "campgpubreakpoints")  
Punkt przerwania procesora GPU  
  
7.  Na pasku menu wybierz **debugowania**, **Rozpocznij debugowanie**. Punkty przerwania w kodzie procesora CPU w wierszach 67 i 70 nie są wykonywane podczas debugowania, ponieważ te wiersze kodu są wykonywane na Procesorze GPU.  
  
### <a name="to-use-the-gpu-threads-window"></a>Aby korzystanie z okna wątków GPU  
  
1.  Aby otworzyć okno wątków GPU na pasku menu wybierz **debugowania**, **Windows**, **wątki GPU**.  
  
     Możesz sprawdzić stan wątków GPU zostanie wyświetlone okno wątków GPU.  
  
2.  Dokowanie okna wątków GPU w dolnej części programu Visual Studio. Wybierz **rozwiń przełącznika wątku** przycisk, aby wyświetlić pola tekstowe kafelków i wątku. Okno wątków GPU pokazuje łączna liczba wątków GPU active i zablokowane, jak pokazano na poniższej ilustracji.  
  
     ![Okno wątków GPU z 4 Aktywne wątki](../../parallel/amp/media/campc.png "campc")  
Okno wątków GPU  
  
     Brak 313 Kafelki przydzielone dla tego obliczenia. Każdego kafelka zawiera 32 wątków. Ponieważ występuje lokalnego debugowania GPU w emulatorze oprogramowania, dostępne są cztery Aktywne wątki GPU. Cztery wątków jednocześnie wykonać instrukcje, a następnie przejdź razem do następnej instrukcji.  
  
     Okno wątków GPU istnieją cztery wątki GPU aktywne i 28 wątki GPU blokowane na [tile_barrier::wait](reference/tile-barrier-class.md#wait) instrukcji zdefiniowanych na temat wiersza 21 (`t_idx.barrier.wait();`). Wszystkie wątki GPU 32 należą do pierwszego fragmentu `tile[0]`. Strzałka wskazuje na wiersz, który zawiera bieżącego wątku. Aby przełączyć się do innego wątku, użyj jednej z następujących metod:  

  
    -   W wierszu dla wątku przełączyć się do okna wątków GPU, otwórz menu skrótów i wybierz polecenie **Przełącz do wątku**. Jeśli wiersz reprezentuje więcej niż jeden wątek, nastąpi przełączenie do pierwszego wątku zgodnie z współrzędne wątku.  
  
    -   Wprowadź wartości kafelków i wątku wątku w odpowiednich polach tekstowych, a następnie wybierz pozycję **wątku przełącznika** przycisku.  
  
     Stos wywołań okna zawiera stos wywołań bieżącego wątku procesora GPU.  
  
### <a name="to-use-the-parallel-stacks-window"></a>Aby korzystanie z okna stosów równoległych  
  
1.  Aby otworzyć okno stosów równoległych na pasku menu wybierz **debugowania**, **Windows**, **stosów równoległych**.  
  
     Okno stosów równoległych jednocześnie sprawdzić ramek stosu wielu wątków GPU.  
  
2.  Dokowanie okna stosów równoległych w dolnej części programu Visual Studio.  
  
3.  Upewnij się, że **wątków** jest zaznaczony na liście w lewym górnym rogu. Na poniższej ilustracji z okna stosów równoległych przedstawiono koncentruje się na stosie wywołań wątków GPU, które widać w okno wątków GPU.  
  
     ![Okno stosów równoległych z 4 Aktywne wątki](../../parallel/amp/media/campd.png "campd")  
Okno stosów równoległych  
  
     32 wątków zakończył się z `_kernel_stub` instrukcji lambda w `parallel_for_each` wywołanie funkcji, a następnie do `sum_kernel_tiled` funkcji, gdzie występuje redukcji równoległych. do osiągnięcia postępu 28 poza 32 wątków [tile_barrier::wait](reference/tile-barrier-class.md#wait) instrukcji i pozostają zablokowane w wierszu 22, podczas gdy inne wątki 4 pozostają aktywne w `sum_kernel_tiled` funkcji w wierszu 30.  

  
     Możesz sprawdzić właściwości wątek GPU, które są dostępne w oknie zaawansowanych etykietek danych z okna stosów równoległych wątków GPU. Aby to zrobić, Zatrzymaj wskaźnik myszy na ramce stosu **sum_kernel_tiled**. Na poniższej ilustracji przedstawiono etykietek danych.  
  
     ![Etykietek danych dla okna stosów równoległych](../../parallel/amp/media/campe.png "campe")  
Wątek GPU etykietek danych  
  
     Aby uzyskać więcej informacji na temat okna stosów równoległych, zobacz [za pomocą okna stosów równoległych](/visualstudio/debugger/using-the-parallel-stacks-window).  
  
### <a name="to-use-the-parallel-watch-window"></a>Aby korzystanie z okna czujki równoległej  
  
1.  Aby otworzyć okno czujki równoległej na pasku menu wybierz **debugowania**, **Windows**, **czujki równoległej**, **1 czujki równoległej**.  
  
     Okno czujki równoległej sprawdzić wartości wyrażenia przez wiele wątków.  
  
2.  Dokowanie okna 1 czujki równoległej do dolnej części programu Visual Studio. Istnieje 32 wierszy w tabeli z okna czujki równoległej. Każdy odpowiada wątku procesora GPU, który pojawił się zarówno z okna wątków GPU, jak i z okna stosów równoległych. Teraz możesz wprowadzić wyrażenia wartości, których chcesz sprawdzić przez wszystkie wątki GPU 32.  
  
3.  Wybierz **Dodaj wyrażenie kontrolne** nagłówek kolumny, wprowadź `localIdx`, a następnie wybierz klawisz Enter.  
  
4.  Wybierz **Dodaj wyrażenie kontrolne** nagłówek kolumny ponownie, wpisz `globalIdx`, a następnie wybierz klawisz Enter.  
  
5.  Wybierz **Dodaj wyrażenie kontrolne** nagłówek kolumny ponownie, wpisz `localA[localIdx[0]]`, a następnie wybierz klawisz Enter.  
  
     Można sortować według określonego wyrażenia, wybierając nagłówek odpowiadającej mu kolumny.  
  
     Wybierz **localA [localIdx [0]]** nagłówek kolumny, aby posortować kolumnę. Na poniższej ilustracji przedstawiono wyniki sortowanie według **localA [localIdx [0]]**.  
  
     ![Okno czujki równoległych sortowane wyniki](../../parallel/amp/media/campf.png "campf")  
 Wyniki sortowania  
  
     Możesz wyeksportować zawartość okna czujki równoległej do programu Excel, wybierając przycisk programu Excel, a następnie wybierając **Otwórz w programie Excel**. Jeśli masz zainstalowanego na komputerze dewelopera programu Excel, spowoduje to otwarcie arkusza programu Excel z zawartością.  
  
6.  W prawym górnym rogu okna czujki równoległej istnieje formant filtru, który umożliwia filtrowanie zawartości przy użyciu wyrażeń logicznych. Wprowadź `localA[localIdx[0]] > 20000` w tekst formantu filtru polu, a następnie wybierz klawisz Enter.  
  
     Okno teraz zawiera tylko wątków, na którym `localA[localIdx[0]]` wartość jest większa niż 20000. Zawartość nadal jest sortowana według `localA[localIdx[0]]` kolumny, która jest sortowania akcji podczas wcześniej wykonywanej operacji.  
  
## <a name="flagging-gpu-threads"></a>Flagowanie wątków GPU  
 Możesz oznaczyć określonych wątków GPU przez flagowanie je w okno wątków GPU, z okna czujki równoległej lub etykietek danych w oknie stosów równoległych. Jeśli wiersz z okna wątków GPU zawiera więcej niż jeden wątek, oflagowanie tego wiersza flagi wszystkie wątki, które są zawarte w tym wierszu.  
  
### <a name="to-flag-gpu-threads"></a>Flagi wątków GPU  
  
1.  Wybierz **[wątku]** nagłówek kolumny w oknie 1 czujki równoległej, aby posortować według indeks wątku i kafelka.  
  
2.  Na pasku menu wybierz **debugowania**, **Kontynuuj**, co powoduje, że cztery wątki który były aktywne do postępu do następnego zapory (zdefiniowany w wierszu 32 AMPMapReduce.cpp).  
  
3.  Wybierz flagą symbol po lewej stronie wiersza, który zawiera cztery wątków, które są obecnie aktywne.  
  
     Na poniższej ilustracji przedstawiono cztery oflagowane wątki aktywne okno wątków GPU.  
  
     ![Okno wątków GPU z oflagowane wątki](../../parallel/amp/media/campg.png "campg")  
Aktywne wątki okno wątków GPU  
  
     Okno czujki równoległej i etykietek danych z okna stosów równoległych zarówno wskazują oflagowane wątki.  
  
4.  Jeśli chcesz skupić się na cztery wątki oflagowane można Pokaż wątki GPU, czujki równoległej i windows stosów równoległych tylko oflagowane wątki.  
  
     Przycisk Pokaż tylko oflagowane w dowolnym oknie lub na **debugowania lokalizacji** paska narzędzi. Poniższa ilustracja przedstawia przycisk Pokaż tylko oflagowane na **debugowania lokalizacji** paska narzędzi.  
  
     ![Debugowanie lokalizacji narzędzi z ikoną Pokaż tylko oflagowane](../../parallel/amp/media/camph.png "camph")  
Pokaż tylko oflagowane przycisk  
  
     Wątków GPU, czujki równoległej i stosów równoległych systemu windows jest teraz wyświetlany tylko oflagowane wątki.  
  
## <a name="freezing-and-thawing-gpu-threads"></a>Zamrażanie i odblokowania wątków GPU  
 Można zablokować (Wstrzymaj) i odblokowania wątki GPU (Wznów) z okna wątków GPU lub z okna czujki równoległej. Można zablokować i odblokować wątków CPU ten sam sposób; Aby uzyskać informacje, zobacz [porady: Korzystanie z okna wątków](/visualstudio/debugger/how-to-use-the-threads-window).  
  
### <a name="to-freeze-and-thaw-gpu-threads"></a>Aby zablokować i odblokować wątków GPU  
  
1.  Wybierz **Pokaż tylko oflagowane** przycisk, aby wyświetlić wszystkie wątki.  
  
2.  Na pasku menu wybierz **debugowania**, **Kontynuuj**.  
  
3.  Otwórz menu skrótów dla aktywnego wiersza, a następnie wybierz pozycję **Zablokuj**.  
  
     Poniższa ilustracja okno wątków GPU pokazuje, że wszystkie cztery wątki są zablokowane.  
  
     ![Windows wątki GPU przedstawiający zablokowane wątki](../../parallel/amp/media/campk.png "campk")  
Zablokowane wątki okno wątków GPU  
  
     Okno czujki równoległej pokazuje również, że wszystkie cztery wątki są zablokowane.  
  
4.  Na pasku menu wybierz **debugowania**, **Kontynuuj** umożliwia obok cztery wątki GPU postępu poza bariery w wierszu 22 i dotarcie do punktu przerwania w wierszu 30. Okno wątków GPU pokazuje pozostawienie cztery wcześniej zablokowane wątki zablokowane i w stanie aktywnym.  
  
5.  Na pasku menu wybierz **debugowania**, **Kontynuuj**.  
  
6.  Z okna czujki równoległej możesz także odblokowania osoba lub wiele wątków GPU.  
  
### <a name="to-group-gpu-threads"></a>Do grupy wątków GPU  
  
1.  Menu skrótów dla jednego z wątków w **wątki GPU** okna, wybierz **Group By**, **adres**.  
  
     Wątki okno wątków GPU są pogrupowane według adresu. Adres odnosi się do instrukcji, w którym znajduje się każdej grupy wątków dezasemblacji. 24 wątki są w wierszu 22 gdzie [tile_barrier::wait — metoda](reference/tile-barrier-class.md#wait) jest wykonywana. 12 wątków znajduje się w instrukcji bariery w wierszu 32. Cztery wątki te są oznaczane. Osiem wątki są punkt przerwania w wierszu 30. Cztery wątki te są zablokowane. Na poniższej ilustracji przedstawiono grupowanych wątków w okno wątków GPU.  

  
     ![Okno wątków GPU z wątkami pogrupowane według adresu](../../parallel/amp/media/campl.png "campl")  
Wątki zgrupowane w okno wątków GPU  
  
2.  Można również wykonywać **Group By** operacji przez otwarcie menu skrótów okna czujki równoległej siatki danych wybieranie **Group By**, a następnie wybierając element menu, który odpowiada sposób do grupy wątków.  
  
## <a name="running-all-threads-to-a-specific-location-in-code"></a>Uruchamianie wszystkich wątków do określonej lokalizacji w kodzie  
 Uruchom wszystkie wątki na kafelku dany wiersz, który zawiera kursor przy użyciu **Uruchom bieżący Kafelek do kursora**.  
  
### <a name="to-run-all-threads-to-the-location-marked-by-the-cursor"></a>Aby uruchomić wszystkie wątki do lokalizacji oznaczony przez kursor  
  
1.  W menu skrótów dla zamrożonych wątków wybierz **odblokowania**.  
  
2.  W edytorze kodu, umieść kursor w wierszu 30.  
  
3.  Menu skrótów dla edytora kodu, wybierz **Uruchom bieżący Kafelek do kursora**.  
  
     24 wątków, które wcześniej zostały zablokowane w bariery w wierszu 21 osiągnięcia postępu do wiersza 32. Przedstawiono to w **wątki GPU** okna.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd C++ AMP](../../parallel/amp/cpp-amp-overview.md)   
 [Debugowanie kodu GPU](/visualstudio/debugger/debugging-gpu-code)   
 [Porady: Korzystanie z okna wątków GPU](/visualstudio/debugger/how-to-use-the-gpu-threads-window)   
 [Porady: Korzystanie z okna czujki równoległej](/visualstudio/debugger/how-to-use-the-parallel-watch-window)   
 [Analizowanie kodu C++ AMP z narzędzia Concurrency Visualizer](http://go.microsoft.com/fwlink/p/?linkid=253987&clcid=0x409)

