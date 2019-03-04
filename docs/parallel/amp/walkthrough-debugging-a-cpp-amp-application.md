---
title: 'Przewodnik: Debugowanie aplikacji C++ AMP'
ms.date: 11/19/2018
helpviewer_keywords:
- debugging, C++ Accelerated Massive Parallelism
- C++ AMP, debugging
- C++ Accelerated Massive Parallelism, debugging
- debugging, C++ AMP
ms.assetid: 40e92ecc-f6ba-411c-960c-b3047b854fb5
ms.openlocfilehash: 5312ba7354c28286cafb092711d66d56a920581a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57286916"
---
# <a name="walkthrough-debugging-a-c-amp-application"></a>Przewodnik: Debugowanie aplikacji C++ AMP

W tym temacie pokazano, jak można debugować aplikację, która używa C++ Accelerated Massive Parallelism (C++ AMP), aby móc korzystać z jednostki przetwarzania grafiki (GPU). Używa programu równoległych redukcji, która będzie sumować dużą tablicę liczb całkowitych. W instruktażu przedstawiono następujące zagadnienia:

- Uruchamianie debugera GPU.

- Sprawdzanie wątków GPU okno wątków GPU.

- Za pomocą **stosów równoległych** okna, aby równocześnie, obserwowanie stosy wywołań wielu wątków procesora GPU.

- Za pomocą **równoległego wyrażenia kontrolnego** okna, aby sprawdzić wartości pojedynczego wyrażenia przez wiele wątków, w tym samym czasie.

- Flagowanie, blokowanie, rozgrzewania i grupowanie wątków GPU.

- Wykonanie wszystkich wątków fragmentu do określonej lokalizacji w kodzie.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem tego instruktażu:

- Odczyt [Przegląd C++ AMP](../../parallel/amp/cpp-amp-overview.md).

- Upewnij się, że wiersz liczby są wyświetlane w edytorze tekstów. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie numerów wierszy w edytorze](/visualstudio/ide/reference/how-to-display-line-numbers-in-the-editor).

- Upewnij się, że korzystasz z systemu Windows 8 lub Windows Server 2012, aby zapewnić obsługę debugowania na emulatorze oprogramowania.

[!INCLUDE[note_settings_general](../../mfc/includes/note_settings_general_md.md)]

### <a name="to-create-the-sample-project"></a>Aby utworzyć projekt przykładowy

1. Uruchom program Visual Studio.

2. Na pasku menu wybierz **pliku** > **New** > **projektu**.

3. W obszarze **zainstalowane** w okienku szablonów wybierz **Visual C++**.

4. Wybierz **Aplikacja konsoli Win32**, typ `AMPMapReduce` w **nazwa** , a następnie wybierz **OK** przycisku.

5. Wybierz **dalej** przycisku.

6. Wyczyść **prekompilowany nagłówek** pole wyboru, a następnie wybierz **Zakończ** przycisku.

7. W **Eksploratora rozwiązań**, stdafx.h, targetver.h i stdafx.cpp Usuń z projektu.

8. Otwórz AMPMapReduce.cpp i zastąp jego zawartość następującym kodem.

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

9. Na pasku menu wybierz **pliku** > **Zapisz wszystko**.

10. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **AMPMapReduce**, a następnie wybierz **właściwości**.

11. W **stron właściwości** dialogowego **właściwości konfiguracji**, wybierz **C/C++** > **prekompilowanych nagłówków**.

12. Dla **wstępnie skompilowany nagłówek** wybierz **nie przy użyciu prekompilowanych nagłówków**, a następnie wybierz **OK** przycisku.

13. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.

## <a name="debugging-the-cpu-code"></a>Debugowanie kodu procesora CPU

W tej procedurze lokalny debuger Windows użyje się upewnić, że kod procesora CPU w tej aplikacji jest prawidłowy. Segment kodu procesora CPU w tej aplikacji, która jest szczególnie interesujące jest `for` pętli w `reduction_sum_gpu_kernel` funkcji. Kontroluje oparta na drzewie równoległych redukcji uruchamianą w procesorze GPU.

### <a name="to-debug-the-cpu-code"></a>Do debugowania kodu procesora CPU

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **AMPMapReduce**, a następnie wybierz **właściwości**.

2. W **stron właściwości** dialogowego **właściwości konfiguracji**, wybierz **debugowanie**. Upewnij się, że **lokalny debuger Windows** wybrano **debuger do uruchomienia** listy.

3. Wróć do **Edytor kodu**.

4. Ustaw punkty przerwania w wierszach kodu pokazano na poniższej ilustracji (około 67 wierszy wiersz 70).

   ![Punkty przerwania Procesora](../../parallel/amp/media/campcpubreakpoints.png "punktów przerwania procesora CPU") <br/>
   Punkty przerwania procesora CPU

5. Na pasku menu wybierz **debugowania** > **Rozpocznij debugowanie**.

6. W **lokalne** okna, sprawdź wartość `stride_size` aż do osiągnięcia punktu przerwania w wierszu 70.

7. Na pasku menu wybierz **debugowania** > **Zatrzymaj debugowanie**.

## <a name="debugging-the-gpu-code"></a>Debugowanie kodu GPU

W tej sekcji pokazano, jak debugowanie kodu GPU, czyli kod zawarty w `sum_kernel_tiled` funkcji. Kodu GPU oblicza sumę liczb całkowitych dla każdego "bloku" równolegle.

### <a name="to-debug-the-gpu-code"></a>Debugowanie kodu GPU

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **AMPMapReduce**, a następnie wybierz **właściwości**.

2. W **stron właściwości** dialogowego **właściwości konfiguracji**, wybierz **debugowanie**.

3. W **debuger do uruchomienia** listy wybierz **lokalny debuger Windows**.

4. W **typ debugera** listy, upewnij się, że **automatycznie** jest zaznaczone.

    **Automatyczne** jest wartością domyślną. Przed systemem Windows 10 **tylko GPU** jest wymaganą wartością zamiast **automatycznie**.

5. Wybierz **OK** przycisku.

6. Ustaw punkt przerwania w wierszu 30, jak pokazano na poniższej ilustracji.

   ![Punkty przerwania GPU](../../parallel/amp/media/campgpubreakpoints.png "punktów przerwania procesora GPU") <br/>
   Punktu przerwania GPU

7. Na pasku menu wybierz **debugowania** > **Rozpocznij debugowanie**. Punkty przerwania w kodzie procesora CPU w wierszach 67 i 70 znaków nie są wykonywane podczas debugowania, ponieważ te wiersze kodu są wykonywane na Procesorze GPU.

### <a name="to-use-the-gpu-threads-window"></a>Aby korzystanie z okna wątków GPU

1. Aby otworzyć **wątków GPU** okna, na pasku menu wybierz **debugowania** > **Windows** > **wątków GPU**.

   Możesz sprawdzić stan procesora GPU wątki w **wątków GPU** zostanie wyświetlone okno.

2. Zadokuj **wątków GPU** okna w dolnej części programu Visual Studio. Wybierz **rozwiń przełącznika wątku** przycisk, aby wyświetlić pola tekstowe fragmentu i wątku. **Wątków GPU** okno całkowita liczba aktywnych i zablokowane wątki GPU pokazuje, jak pokazano na poniższej ilustracji.

   ![Okno wątków GPU z 4 aktywnych wątków](../../parallel/amp/media/campc.png "okno wątków GPU z 4 aktywnych wątków") <br/>
   Okno wątków GPU

   Istnieją Kafelki 313 przydzielone to obliczenie. Każdy Kafelek zawiera 32 wątków. Ponieważ lokalne debugowanie GPU odbywa się na emulatorze oprogramowania, istnieją cztery Aktywne wątki GPU. Cztery wątki wykonania instrukcji jednocześnie, a następnie przejdź razem do następnej instrukcji.

   W **wątków GPU** oknie cztery wątki GPU są aktywne i blokowane wątki GPU 28 [tile_barrier::wait](reference/tile-barrier-class.md#wait) instrukcji zdefiniowany z numerem o wierszu 21 (`t_idx.barrier.wait();`). Wszystkie wątki GPU 32 należą do pierwszego fragmentu `tile[0]`. Strzałka wskazuje na wiersz, który zawiera bieżący wątek. Aby przełączyć się do innego wątku, należy użyć jednej z następujących metod:

    - W wierszu dla wątku przełączyć się do w **wątków GPU** okna, otwórz menu skrótów i wybierz polecenie **Przełącz do wątku**. Jeśli wiersz reprezentuje więcej niż jeden wątek, zostanie przełączona w pierwszym wątku, zgodnie z współrzędne wątku.

    - Wprowadź wartości fragmentu i wątku wątku w odpowiednich polach tekstowych, a następnie wybierz **wątku przełącznika** przycisku.

   **Stos wywołań** jest wyświetlana w oknie stosu wywołań bieżącego wątku procesora GPU.

### <a name="to-use-the-parallel-stacks-window"></a>Aby korzystanie z okna stosów równoległych

1. Aby otworzyć **stosów równoległych** okna, na pasku menu wybierz **debugowania** > **Windows** > **stosów równoległych**.

   Możesz użyć **stosów równoległych** okna, aby sprawdzić jednocześnie ramek stosu wielu wątków GPU.

2. Zadokuj **stosów równoległych** okna w dolnej części programu Visual Studio.

3. Upewnij się, że **wątków** jest zaznaczony na liście w lewym górnym rogu. Na poniższej ilustracji **stosów równoległych** okno pokazuje widok koncentruje się na stosie wywołań wątków GPU, które zostały użyte w **wątków GPU** okna.

   ![Okno stosów równoległych z 4 aktywnych wątków](../../parallel/amp/media/campd.png "okna stosów równoległych z 4 aktywnych wątków") <br/>
   Okno stosów równoległych

   32 wątków zakończył się z `_kernel_stub` do instrukcji lambda w `parallel_for_each` wywołania funkcji i następnie `sum_kernel_tiled` funkcji, w którym występuje równoległych redukcji. do osiągnięcia postępu 28 poza 32 wątków [tile_barrier::wait](reference/tile-barrier-class.md#wait) instrukcji i zostaną zablokowane w wierszu 22, natomiast inne wątki 4 pozostają aktywne w `sum_kernel_tiled` funkcji w wierszu 30.

   Możesz sprawdzić właściwości wątek GPU, które są dostępne w **wątków GPU** okna w rozbudowane DataTip z **stosów równoległych** okna. Aby to zrobić, Zatrzymaj wskaźnik myszy na ramce stosu **sum_kernel_tiled**. Poniższa ilustracja przedstawia DataTip.

   ![Etykietki danych dla okna stosów równoległych](../../parallel/amp/media/campe.png "etykietki danych dla okna stosów równoległych") <br/>
   Wątek GPU etykietki danych

   Aby uzyskać więcej informacji na temat **stosów równoległych** okna, zobacz [przy użyciu Parallel Stacks Window](/visualstudio/debugger/using-the-parallel-stacks-window).

### <a name="to-use-the-parallel-watch-window"></a>Aby korzystanie z okna równoległego wyrażenia kontrolnego

1. Aby otworzyć **równoległego wyrażenia kontrolnego** okna, na pasku menu wybierz **debugowania** > **Windows** > **równoległego wyrażenia kontrolnego**  >  **Równoległe wyrażenie kontrolne 1**.

   Możesz użyć **równoległego wyrażenia kontrolnego** okna, aby sprawdzić wartości wyrażenia w wielu wątkach.

2. Zadokuj **równoległa Czujka 1** okna do dolnej części programu Visual Studio. Istnieją 32 wierszy w tabeli **równoległego wyrażenia kontrolnego** okna. Każdy odpowiada wątek GPU, które pojawiło się w oknie wątków GPU i **stosów równoległych** okna. Teraz możesz wprowadzić wartości, którego ma zostać sprawdzony przez wszystkie wątki GPU 32 wyrażeń.

3. Wybierz **Dodaj czujkę** nagłówek kolumny, wprowadź `localIdx`, a następnie wybierz **Enter** klucza.

4. Wybierz **Dodaj czujkę** nagłówek kolumny ponownie, typ `globalIdx`, a następnie wybierz **Enter** klucza.

5. Wybierz **Dodaj czujkę** nagłówek kolumny ponownie, typ `localA[localIdx[0]]`, a następnie wybierz **Enter** klucza.

   Można sortować według określonego wyrażenia, wybierając odpowiedni nagłówek kolumny.

   Wybierz **localA [localIdx [0]]** nagłówek kolumny, aby posortować kolumnę. Na poniższej ilustracji przedstawiono wyniki sortowanie według **localA [localIdx [0]]**.

   ![Równoległe okno czujki z posortowane wyniki](../../parallel/amp/media/campf.png "okno czujki równoległej z posortowane wyniki") <br/>
   Wyniki sortowania

   Możesz wyeksportować zawartość **równoległego wyrażenia kontrolnego** okna programu Excel, wybierając **Excel** przycisk, a następnie wybierając **Otwórz w programie Excel**. Jeśli masz zainstalowany na komputerze deweloperskim w programie Excel, spowoduje to otwarcie arkusza programu Excel, który zawiera zawartość.

6. W prawym górnym rogu **równoległego wyrażenia kontrolnego** okna, jest formant filtru, który służy do filtrowania zawartości za pomocą wyrażeń logicznych. Wprowadź `localA[localIdx[0]] > 20000` w tekście formant filtru pole, a następnie wybierz **Enter** klucza.

   Okno zawiera teraz tylko wątki, w którym `localA[localIdx[0]]` wartość jest większa niż 20000. Zawartość nadal są posortowane według `localA[localIdx[0]]` kolumny, która jest akcja sortowania wcześniej wykonanymi.

## <a name="flagging-gpu-threads"></a>Flagowanie wątków GPU

Możesz oznaczyć określone wątki GPU, oznaczając je flagą **wątków GPU** oknie **równoległego wyrażenia kontrolnego** okna lub DataTip w **stosów równoległych** okna. Jeśli wiersza w okno wątków GPU zawiera więcej niż jeden wątek, oznaczając flagą wiersza flagi wszystkie wątki, które są zawarte w tym wierszu.

### <a name="to-flag-gpu-threads"></a>Flagi wątków GPU

1. Wybierz **[wątek]** nagłówek kolumny w **równoległa Czujka 1** okna, aby posortować według indeks wątku i Kafelek.

2. Na pasku menu wybierz **debugowania** > **Kontynuuj**, co powoduje, że cztery wątki, były aktywne do postępu do następnego zapory (zdefiniowany w wierszu 32 AMPMapReduce.cpp).

3. Wybierz symbol flagi po lewej stronie wiersza, który zawiera cztery wątki, które są już aktywne.

   Na poniższej ilustracji przedstawiono cztery aktywnych wątków oflagowanych w **wątków GPU** okna.

   ![Okno wątków GPU z oflagowane wątki](../../parallel/amp/media/campg.png "okno wątków GPU z oflagowane wątki") <br/>
   Aktywne wątki w okno wątków GPU

   **Równoległego wyrażenia kontrolnego** okna i DataTip z **stosów równoległych** okna zarówno wskazują oflagowane wątki.

4. Jeśli chcesz skupić się na cztery wątki, które możesz oznaczone, można wybrać do wyświetlenia w **wątków GPU**, **równoległego wyrażenia kontrolnego**, i **stosów równoległych** windows tylko oflagowane wątki.

   Wybierz **Pokaż tylko oflagowane** przycisk na dowolnym systemu windows lub na **Lokalizacja debugowania** paska narzędzi. Poniższa ilustracja przedstawia **Pokaż tylko oflagowane** znajdujący się na **Lokalizacja debugowania** paska narzędzi.

   ![Pasek narzędzi lokalizacji z ikoną Pokaż tylko oflagowane debugowania](../../parallel/amp/media/camph.png "narzędzi debugowania lokalizacji z ikoną Pokaż tylko oflagowane") <br/>
   **Pokaż tylko oflagowane** przycisku

   Teraz **wątków GPU**, **równoległego wyrażenia kontrolnego**, i **stosów równoległych** tylko oflagowane wątki wyświetlania systemu windows.

## <a name="freezing-and-thawing-gpu-threads"></a>Zawiesza się i odblokowania wątków GPU

Można zablokować (zawieszenie) i Odblokuj wątki procesora GPU (Wznów) albo **wątków GPU** okna lub **równoległego wyrażenia kontrolnego** okna. Można Zablokuj i Odblokuj wątki procesora CPU w taki sam sposób; Aby uzyskać informacje, zobacz [jak: Korzystanie z okna wątków](/visualstudio/debugger/how-to-use-the-threads-window).

### <a name="to-freeze-and-thaw-gpu-threads"></a>Blokowanie i odblokowywanie wątków GPU

1. Wybierz **Pokaż tylko oflagowane** przycisk, aby wyświetlić wszystkie wątki.

2. Na pasku menu wybierz **debugowania** > **Kontynuuj**.

3. Otwórz menu skrótów dla aktywnego wiersza, a następnie wybierz **Freeze**.

   Poniższa ilustracja z **wątków GPU** okno pokazuje, że wszystkie cztery wątki są zablokowane.

   ![Windows wątków GPU przedstawiający zablokowane wątki](../../parallel/amp/media/campk.png "windows wątków GPU przedstawiający zablokowane wątki") <br/>
   Zablokowane wątki **wątków GPU** okna

   Podobnie **równoległego wyrażenia kontrolnego** okno pokazuje, że wszystkie cztery wątki są zablokowane.

4. Na pasku menu wybierz **debugowania** > **Kontynuuj** umożliwia czterech kolejnych wątków GPU postępu ostatnie barierę w wierszu 22 i dotarcie do punktu przerwania w wierszu 30. **Wątków GPU** okno zawiera pozostawienie cztery wątki wcześniej zamrożone, zamrożone i znajduje się w stanie aktywnym.

5. Na pasku menu wybierz **debugowania**, **Kontynuuj**.

6. Z **równoległego wyrażenia kontrolnego** okna, można także odblokowania osoby lub wielu wątków procesora GPU.

### <a name="to-group-gpu-threads"></a>Do grupy wątków GPU

1. W menu skrótów dla jednej z wątków w **wątków GPU** oknie Wybierz **Group By**, **adres**.

   Wątki w **wątków GPU** okna są pogrupowane według adresu. Adres odnosi się do instrukcji, w którym znajduje się każda grupa wątków dezasemblacji. 24 wątki są w wierszu 22 gdzie [tile_barrier::wait — metoda](reference/tile-barrier-class.md#wait) jest wykonywany. 12 wątków znajdują się w instrukcji barierę w wierszu 32. Cztery te wątki są oflagowane. Osiem wątki są w punkcie przerwania w wierszu 30. Cztery te wątki są zablokowane. Na poniższej ilustracji przedstawiono pogrupowanych wątki **wątków GPU** okna.

   ![Okno wątków GPU z wątkami, pogrupowane według adresu](../../parallel/amp/media/campl.png "okno wątków GPU z wątkami, pogrupowane według adresu") <br/>
   Pogrupowane w wątki w **wątków GPU** okna

2. Można również wykonać **Group By** operacji, otwierając menu skrótów dla siatki danych z **równoległego wyrażenia kontrolnego** okna, wybierając **Group By**, a następnie wybierając z menu element, który odnosi się do sposobu grupa wątków.

## <a name="running-all-threads-to-a-specific-location-in-code"></a>Uruchamianie wszystkich wątków do określonej lokalizacji w kodzie

Uruchom wszystkie wątki we fragmencie danego na wiersz zawierający kursor przy użyciu **Uruchom bieżący Kafelek do kursora**.

### <a name="to-run-all-threads-to-the-location-marked-by-the-cursor"></a>Aby uruchomić wszystkie wątki w lokalizacji oznaczone przez kursor

1. W menu skrótów dla zamrożone wątków wybierz **Odblokuj**.

2. W **Edytor kodu**, umieść kursor w wierszu 30.

3. W menu skrótów dla **Edytor kodu**, wybierz **Uruchom bieżący Kafelek do kursora**.

   24 wątków, które wcześniej zostały zablokowane w barierę w wierszu 21 osiągnięcia postępu do wiersza 32. Jest to pokazane w **wątków GPU** okna.

## <a name="see-also"></a>Zobacz także

[Przegląd C++ AMP](../../parallel/amp/cpp-amp-overview.md)<br/>
[Debugowanie kodu GPU](/visualstudio/debugger/debugging-gpu-code)<br/>
[Instrukcje: Korzystanie z okna wątków procesora GPU](/visualstudio/debugger/how-to-use-the-gpu-threads-window)<br/>
[Instrukcje: Korzystanie z okna równoległego wyrażenia kontrolnego](/visualstudio/debugger/how-to-use-the-parallel-watch-window)<br/>
[Analizowanie kodu C++ AMP w narzędziu Concurrency Visualizer](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/03/09/analyzing-c-amp-code-with-the-concurrency-visualizer/)
