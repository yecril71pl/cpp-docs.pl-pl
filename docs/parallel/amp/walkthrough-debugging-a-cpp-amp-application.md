---
title: 'Przewodnik: Debugowanie aplikacji C++ amp'
ms.date: 04/23/2019
helpviewer_keywords:
- debugging, C++ Accelerated Massive Parallelism
- C++ AMP, debugging
- C++ Accelerated Massive Parallelism, debugging
- debugging, C++ AMP
ms.assetid: 40e92ecc-f6ba-411c-960c-b3047b854fb5
ms.openlocfilehash: 0c9fb5588cfd44c83d8fe72c7c4aede0fedab672
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "69631598"
---
# <a name="walkthrough-debugging-a-c-amp-application"></a>Przewodnik: Debugowanie aplikacji C++ amp

W tym temacie pokazano, jak debugować aplikację, która C++ używa przyspieszonej ogromnej równoległości (C++ amp), aby skorzystać z procesora graficznego (GPU). Korzysta ona z programu redukcji równoległej, który sumuje w górę dużą tablicę liczb całkowitych. W instruktażu przedstawiono następujące zagadnienia:

- Uruchamianie debugera GPU.

- Sprawdzanie wątków procesora GPU w oknie wątków GPU.

- Korzystając z okna **stosów równoległych** , można jednocześnie obserwować stosy wywołań wielu wątków procesora GPU.

- Korzystając z okna **czujki równoległej** , można sprawdzić wartości pojedynczego wyrażenia w wielu wątkach w tym samym czasie.

- Oflagowanie, zamrażanie, odblokowywanie i grupowanie wątków procesora GPU.

- Wykonywanie wszystkich wątków kafelka do określonej lokalizacji w kodzie.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem tego instruktażu:

- Zapoznaj się z [ C++ omówieniem amp](../../parallel/amp/cpp-amp-overview.md).

- Upewnij się, że numery wierszy są wyświetlane w edytorze tekstu. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie numerów wierszy w edytorze](/visualstudio/ide/reference/how-to-display-line-numbers-in-the-editor).

- Upewnij się, że używasz systemu Windows 8 lub Windows Server 2012 do obsługi debugowania na emulatorze oprogramowania. 

[!INCLUDE[note_settings_general](../../mfc/includes/note_settings_general_md.md)]

### <a name="to-create-the-sample-project"></a>Aby utworzyć projekt przykładowy

Instrukcje dotyczące tworzenia projektu różnią się w zależności od używanej wersji programu Visual Studio. Upewnij się, że wybrano poprawną wersję w lewym górnym rogu tej strony.

::: moniker range="vs-2019"

### <a name="to-create-the-sample-project-in-visual-studio-2019"></a>Aby utworzyć przykładowy projekt w programie Visual Studio 2019

1. Na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt** , aby otworzyć okno dialogowe **Tworzenie nowego projektu** .

1. W górnej części okna dialogowego Ustaw **Język** na **C++** , ustaw platformę na **system Windows**i ustaw **Typ projektu** na **Console**. 

1. Z listy filtrowane typy projektów wybierz pozycję **Aplikacja konsolowa** , a następnie wybierz przycisk **dalej**. Na następnej stronie wprowadź `AMPMapReduce` wartość w polu **Nazwa** , aby określić nazwę projektu, i w razie potrzeby określ lokalizację projektu.

   ![Nadaj nazwę projektowi](../../build/media/mathclient-project-name-2019.png "Nadaj nazwę projektowi")

1. Wybierz przycisk **Utwórz** , aby utworzyć projekt klienta.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-the-sample-project-in-visual-studio-2017-or-visual-studio-2015"></a>Aby utworzyć przykładowy projekt w programie Visual Studio 2017 lub Visual Studio 2015

1. Uruchom program Visual Studio.

1. Na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

1. W obszarze **zainstalowane** w okienku szablony wybierz pozycję **Wizualizacja C++** .

1. Wybierz pozycję **aplikacja konsoli Win32**, `AMPMapReduce` wpisz w polu **Nazwa** , a następnie wybierz przycisk **OK** .

1. Wybierz **dalej** przycisku.

1. Wyczyść pole wyboru **prekompilowany nagłówek** , a następnie wybierz przycisk **Zakończ** .

1. W **Eksplorator rozwiązań**Usuń *stdafx. h*, *targetver. h*i *stdafx. cpp* z projektu.

::: moniker-end

Ponown

8. Otwórz AMPMapReduce. cpp i Zastąp jego zawartość następującym kodem.

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

9. Na pasku menu wybierz kolejno opcje **plik** > **Zapisz wszystko**.

10. W **Eksplorator rozwiązań**Otwórz menu skrótów dla **AMPMapReduce**, a następnie wybierz polecenie **Właściwości**.

11. W oknie dialogowym **strony właściwości** w obszarze **Właściwości konfiguracji**wybierz pozycję **C/C++**  > prekompilowane nagłówki.

12. Dla właściwości **prekompilowanego nagłówka** wybierz opcję **nie używa prekompilowanych nagłówków**, a następnie wybierz przycisk **OK** .

13. Na pasku menu wybierz polecenie **Kompiluj** > **kompilację rozwiązania**.

## <a name="debugging-the-cpu-code"></a>Debugowanie kodu procesora

W tej procedurze zostanie użyty lokalny debuger systemu Windows, aby upewnić się, że kod procesora w tej aplikacji jest prawidłowy. Segment kodu procesora CPU w tej aplikacji, który jest szczególnie interesujący, `for` jest pętlą `reduction_sum_gpu_kernel` w funkcji. Steruje równoległą redukcją opartą na drzewie, która jest uruchamiana na procesorze GPU.

### <a name="to-debug-the-cpu-code"></a>Aby debugować kod procesora CPU

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla **AMPMapReduce**, a następnie wybierz polecenie **Właściwości**.

2. W oknie dialogowym **strony właściwości** , w obszarze **Właściwości konfiguracji**, wybierz **debugowanie**. Sprawdź, czy na liście **debuger do uruchomienia** wybrano **lokalny debuger systemu Windows** .

3. Wróć do **edytora kodu**.

4. Ustaw punkty przerwania w wierszach kodu pokazanych na poniższej ilustracji (około wierszy 67 wiersz 70).

   ![Punkty przerwania procesora CPU](../../parallel/amp/media/campcpubreakpoints.png "Punkty przerwania procesora CPU") <br/>
   Punkty przerwania procesora CPU

5. Na pasku menu wybierz **Debuguj** > **Rozpocznij debugowanie**.

6. W oknie **zmiennych lokalnych** Obserwuj wartość `stride_size` ustawienia do momentu, aż zostanie osiągnięty punkt przerwania w wierszu 70.

7. Na pasku menu wybierz **Debuguj** > **Zatrzymaj debugowanie**.

## <a name="debugging-the-gpu-code"></a>Debugowanie kodu GPU

W tej sekcji pokazano, jak debugować kod procesora GPU, który jest kodem zawartym w `sum_kernel_tiled` funkcji. Kod GPU oblicza sumę liczb całkowitych dla każdego "bloku" równolegle.

### <a name="to-debug-the-gpu-code"></a>Aby debugować kod procesora GPU

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla **AMPMapReduce**, a następnie wybierz polecenie **Właściwości**.

2. W oknie dialogowym **strony właściwości** , w obszarze **Właściwości konfiguracji**, wybierz **debugowanie**.

3. Na liście **debuger do uruchomienia** wybierz pozycję **lokalny debuger systemu Windows**.

4. Na liście **Typ debugera** Sprawdź, czy jest wybrana wartość **Autowybór** .

    Wartość **domyślna to.** W systemach starszych niż Windows 10 **procesora GPU jest tylko** wymagana wartość zamiast **Auto.**

5. Wybierz **OK** przycisku.

6. Ustaw punkt przerwania w wierszu 30, jak pokazano na poniższej ilustracji.

   ![Punkty przerwania procesora GPU](../../parallel/amp/media/campgpubreakpoints.png "Punkty przerwania procesora GPU") <br/>
   Punkt przerwania procesora GPU

7. Na pasku menu wybierz **Debuguj** > **Rozpocznij debugowanie**. Punkty przerwania w kodzie procesora CPU w wierszach 67 i 70 nie są wykonywane podczas debugowania GPU, ponieważ te wiersze kodu są wykonywane na PROCESORAch.

### <a name="to-use-the-gpu-threads-window"></a>Aby użyć okna wątków procesora GPU

1. Aby otworzyć okno **wątki GPU** , na pasku menu wybierz **Debuguj** > **wątki procesora GPU** **systemu Windows** > .

   W wyświetlonym oknie **wątki GPU** można sprawdzić stan wątków procesora GPU.

2. Zadokuj okno **wątków GPU** w dolnej części programu Visual Studio. Wybierz przycisk **Rozwiń wątek przełącznika** , aby wyświetlić pola tekstowe kafelka i wątku. Okno **wątki GPU** przedstawia łączną liczbę aktywnych i zablokowanych wątków procesora GPU, jak pokazano na poniższej ilustracji.

   ![Okno wątków GPU z 4 aktywnymi wątkami](../../parallel/amp/media/campc.png "Okno wątków GPU z 4 aktywnymi wątkami") <br/>
   Okno wątków GPU

   Istnieją 313 kafelki przydzielono dla tego obliczenia. Każdy kafelek zawiera 32 wątków. Ponieważ Debugowanie lokalnego procesora GPU odbywa się na emulatorze oprogramowania, istnieją cztery aktywne wątki procesora GPU. Cztery wątki wykonują instrukcje jednocześnie, a następnie przechodzą do następnej instrukcji.

   W oknie **wątki GPU** są aktywne cztery wątki GPU i 28 wątków GPU zablokowanych w instrukcji [tile_barrier:: wait](reference/tile-barrier-class.md#wait) zdefiniowanej w wierszu o godzinie 21 (`t_idx.barrier.wait();`). Wszystkie wątki procesora GPU 32 należą do pierwszego kafelka `tile[0]`,. Strzałka wskazuje wiersz, który zawiera bieżący wątek. Aby przełączyć się do innego wątku, użyj jednej z następujących metod:

    - W wierszu dla wątku do przełączenia w oknie **wątki GPU** Otwórz menu skrótów, a następnie wybierz polecenie **Przełącz do wątku**. Jeśli wiersz reprezentuje więcej niż jeden wątek, przejdziesz do pierwszego wątku według współrzędnych wątku.

    - Wprowadź wartości kafelka i wątku wątku w odpowiednich polach tekstowych, a następnie wybierz przycisk **Przełącz wątek** .

   W oknie **stos wywołań** jest wyświetlany stos wywołań bieżącego wątku procesora GPU.

### <a name="to-use-the-parallel-stacks-window"></a>Aby użyć okna stosów równoległych

1. Aby otworzyć okno **stosów równoległych** , na pasku menu wybierz kolejno opcje **Debuguj** > **równoległe stosy** **systemu Windows** > .

   Można użyć okna **stosów równoległych** , aby jednocześnie zbadać ramki stosu wielu wątków procesora GPU.

2. Zadokuj okno **stosów równoległych** w dolnej części programu Visual Studio.

3. Upewnij się, że na liście w lewym górnym rogu wybrano **wątki** . Na poniższej ilustracji okno **stosów równoległych** przedstawia widok skoncentrowanych stosów wywołań procesora GPU, które zostały wyświetlone w oknie **wątki GPU** .

   ![Okno stosów równoległych z 4 aktywnymi wątkami](../../parallel/amp/media/campd.png "Okno stosów równoległych z 4 aktywnymi wątkami") <br/>
   Okno stosów równoległych

   32 wątków przeszedł `_kernel_stub` z do instrukcji lambda `parallel_for_each` w `sum_kernel_tiled` wywołaniu funkcji, a następnie do funkcji, w której występuje ograniczenie równoległe. 28 z 32 wątków postępuje zgodnie z instrukcją [tile_barrier:: wait](reference/tile-barrier-class.md#wait) i pozostaje zablokowana w wierszu 22, podczas gdy pozostałe 4 wątki pozostają aktywne w `sum_kernel_tiled` funkcji w wierszu 30.

   Można sprawdzić właściwości wątku procesora GPU, które są dostępne w oknie **wątki GPU** w rozbudowanej etykietki danych okna **stosów równoległych** . Aby to zrobić, umieść wskaźnik myszy na klatce stosu **sum_kernel_tiled**. Na poniższej ilustracji przedstawiono etykietki danych.

   ![Okno etykietki danych dla stosów równoległych](../../parallel/amp/media/campe.png "Okno etykietki danych dla stosów równoległych") <br/>
   Etykietki danych wątku procesora GPU

   Aby uzyskać więcej informacji o oknie **stosów równoległych** , zobacz [Korzystanie z okna stosów równoległych](/visualstudio/debugger/using-the-parallel-stacks-window).

### <a name="to-use-the-parallel-watch-window"></a>Aby użyć okno wyrażeń kontrolnych równoległego

1. Aby otworzyć okno **czujki równoległej**  > , na pasku menu wybierz kolejno opcje **Debuguj** > **równoległe** > **równoległe**Obejrzyj**czujka 1**.

   Można użyć okna **czujki równoległej** do sprawdzenia wartości wyrażenia w wielu wątkach.

2. Zadokuj okno **równoległego czujki 1** w dolnej części programu Visual Studio. W tabeli okna **czujki równoległej** istnieją 32 wierszy. Każdy odnosi się do wątku procesora GPU, który pojawił się zarówno w oknie wątków procesora GPU, jak i w oknie **stosów równoległych** . Teraz można wprowadzać wyrażenia, których wartości mają być sprawdzane we wszystkich wątkach procesora GPU 32.

3. Wybierz nagłówek **Dodaj czujki** , wprowadź `localIdx`, a następnie wybierz klawisz **Enter** .

4. Zaznacz ponownie nagłówek **Dodaj kolumnę czujki** , wpisz `globalIdx`, a następnie wybierz klawisz **Enter** .

5. Zaznacz ponownie nagłówek **Dodaj kolumnę czujki** , wpisz `localA[localIdx[0]]`, a następnie wybierz klawisz **Enter** .

   Można sortować według określonego wyrażenia, wybierając odpowiedni nagłówek kolumny.

   Wybierz nagłówek kolumny **locale [localIdx [0]]** , aby posortować kolumnę. Na poniższej ilustracji przedstawiono wyniki sortowania według wartości **locale [localIdx [0]]** .

   ![Okno wyrażeń kontrolnych równoległe z posortowanymi wynikami](../../parallel/amp/media/campf.png "Okno wyrażeń kontrolnych równoległe z posortowanymi wynikami") <br/>
   Wyniki sortowania

   Możesz wyeksportować zawartość okna **czujki równoległej** do programu Excel, wybierając przycisk **programu Excel** , a następnie wybierając pozycję **Otwórz w programie Excel**. Jeśli na komputerze deweloperskim jest zainstalowany program Excel, spowoduje to otwarcie arkusza programu Excel zawierającego zawartość.

6. W prawym górnym rogu okna **czujki równoległej** istnieje kontrolka filtru, której można użyć do filtrowania zawartości przy użyciu wyrażeń logicznych. Wprowadź `localA[localIdx[0]] > 20000` wartość w polu tekstowym kontrolka filtru, a następnie wybierz klawisz **Enter** .

   Okno zawiera teraz tylko wątki, w których `localA[localIdx[0]]` wartość jest większa niż 20000. Zawartość jest nadal posortowana według `localA[localIdx[0]]` kolumny, która jest wykonanym wcześniej akcją sortowania.

## <a name="flagging-gpu-threads"></a>Oflagowanie wątków procesora GPU

Można oznaczyć określone wątki procesora GPU przez Oflagowanie ich w oknie **wątki GPU** , okno **czujki równoległej** lub etykietki danych w oknie **stosów równoległych** . Jeśli wiersz w oknie wątków GPU zawiera więcej niż jeden wątek, oflagowanie tego wiersza oznacza wszystkie wątki zawarte w wierszu.

### <a name="to-flag-gpu-threads"></a>Aby oflagować wątki GPU

1. Wybierz nagłówek kolumny **[Thread]** w oknie **równoległe czujka 1** , aby posortować według indeksu kafelków i indeksu wątku.

2. Na pasku menu wybierz **Debuguj** > **Kontynuuj**, co spowoduje, że cztery wątki, które były aktywne do postępu do następnej bariery (zdefiniowane w wierszu 32 AMPMapReduce. cpp).

3. Wybierz symbol flagi po lewej stronie wiersza zawierającego cztery wątki, które są teraz aktywne.

   Na poniższej ilustracji przedstawiono cztery aktywne wątki oflagowane w oknie **wątki GPU** .

   ![Okno wątków GPU z oflagowanymi wątkami](../../parallel/amp/media/campg.png "Okno wątków GPU z oflagowanymi wątkami") <br/>
   Aktywne wątki w oknie wątków GPU

   Okno **czujki równoległej** i etykietki danych okna **stosów równoległych** wskazują wątki oflagowane.

4. Jeśli chcesz skupić się na czterech wątkach, które zostały oflagowane, możesz pokazać, w **wątkach procesora GPU**, **równoległe**i **równoległe stosy** okna, tylko Oflagowane wątki.

   Wybierz przycisk **Pokaż tylko Oflagowane** na dowolnym z okien lub na pasku narzędzi **Lokalizacja debugowania** . Na poniższej ilustracji przedstawiono przycisk **Pokaż tylko Oflagowane** na pasku narzędzi **Lokalizacja debugowania** .

   ![Pasek narzędzi lokalizacji debugowania z ikoną Pokaż tylko Oflagowane](../../parallel/amp/media/camph.png "Pasek narzędzi lokalizacji debugowania z ikoną Pokaż tylko Oflagowane") <br/>
   **Pokaż przycisk tylko Oflagowane**

   Teraz **wątki procesora GPU**, **zegarki równoległe**i **stosy równoległe** wyświetlają tylko Oflagowane wątki.

## <a name="freezing-and-thawing-gpu-threads"></a>Zamrażanie i odblokowywanie wątków procesora GPU

Wątki procesora GPU (zawieszające) i odblokowywanie (wznawianie) można zablokować z okna **wątki GPU** lub z okna **równoległego czujka** . Można zablokować i odmrozić wątki procesora w ten sam sposób; Aby uzyskać więcej informacji [, zobacz How to: Użyj okna](/visualstudio/debugger/how-to-use-the-threads-window)wątki.

### <a name="to-freeze-and-thaw-gpu-threads"></a>Aby zamrozić i odblokować wątki GPU

1. Wybierz przycisk **Pokaż tylko Oflagowane** , aby wyświetlić wszystkie wątki.

2. Na pasku menu wybierz **Debuguj** > **Kontynuuj**.

3. Otwórz menu skrótów dla aktywnego wiersza, a następnie wybierz polecenie **Zablokuj**.

   Na poniższej ilustracji okna **wątki GPU** przedstawiono zamrożone wszystkie cztery wątki.

   ![Okna wątków procesora GPU przedstawiające zamrożone wątki](../../parallel/amp/media/campk.png "Okna wątków procesora GPU przedstawiające zamrożone wątki") <br/>
   Zablokowane wątki w oknie **wątków GPU**

   Analogicznie, okno **czujki równoległej** pokazuje, że wszystkie cztery wątki są zamrożone.

4. Na pasku menu wybierz **Debuguj** > **Kontynuuj** , aby zezwolić na następnych cztery wątki GPU na postęp poza barierą w wierszu 22 i aby osiągnąć punkt przerwania w wierszu 30. Okno **wątki GPU** pokazuje, że cztery poprzednio zamrożone wątki pozostają zamrożone i w stanie aktywnym.

5. Na pasku menu wybierz **Debuguj**, **Kontynuuj**.

6. W oknie **czujki równoległej** można również odmrożenie pojedynczych lub wielu wątków procesora GPU.

### <a name="to-group-gpu-threads"></a>Aby zgrupować wątki procesora GPU

1. W menu skrótów dla jednego z wątków w oknie **wątki GPU** wybierz pozycję **Grupuj według**, **adres**.

   Wątki w oknie **wątki GPU** są pogrupowane według adresu. Adres odpowiada instrukcji zawartej w demontażu, gdzie znajduje się każda grupa wątków. 24 wątki są w wierszu 22, gdzie jest wykonywana [metoda tile_barrier:: wait](reference/tile-barrier-class.md#wait) . 12 wątków znajduje się w instrukcji dla bariery w wierszu 32. Cztery z tych wątków są oflagowane. Osiem wątków znajduje się w punkcie przerwania w wierszu 30. Cztery z tych wątków są zamrożone. Na poniższej ilustracji przedstawiono pogrupowane wątki w oknie **wątki GPU** .

   ![Okno wątków GPU z wątkami pogrupowanymi według adresu](../../parallel/amp/media/campl.png "Okno wątków GPU z wątkami pogrupowanymi według adresu") <br/>
   Zgrupowane wątki w oknie **wątków GPU**

2. Możesz również wykonać operację **Grupuj według** , otwierając menu skrótów dla siatki danych w oknie **czujki równoległej** , wybierając pozycję **Grupuj według**, a następnie wybierając element menu, który odnosi się do tego, jak chcesz grupować wątki.

## <a name="running-all-threads-to-a-specific-location-in-code"></a>Uruchamianie wszystkich wątków w określonej lokalizacji w kodzie

Wszystkie wątki w danym kafelku są uruchamiane z wierszem zawierającym kursor przy użyciu opcji **Uruchom bieżący kafelek do kursora**.

### <a name="to-run-all-threads-to-the-location-marked-by-the-cursor"></a>Aby uruchomić wszystkie wątki do lokalizacji oznaczonej przez kursor

1. W menu skrótów dla zamrożonych **wątków wybierz polecenie**Odblokuj.

2. W **edytorze kodu**, umieść kursor w wierszu 30.

3. W menu skrótów dla **edytora kodu**wybierz polecenie **Uruchom bieżący kafelek do kursora**.

   24 wątki, które zostały wcześniej zablokowane w przeszkodzie w wierszu 21, zostały zapostępować zgodnie z wierszem 32. Jest to wyświetlane w oknie **wątki GPU** .

## <a name="see-also"></a>Zobacz także

[Przegląd C++ AMP](../../parallel/amp/cpp-amp-overview.md)<br/>
[Debugowanie kodu GPU](/visualstudio/debugger/debugging-gpu-code)<br/>
[Instrukcje: Korzystanie z okna wątków procesora GPU](/visualstudio/debugger/how-to-use-the-gpu-threads-window)<br/>
[Instrukcje: Korzystanie z okna równoległego wyrażenia kontrolnego](/visualstudio/debugger/how-to-use-the-parallel-watch-window)<br/>
[Analizowanie C++ kodu amp przy użyciu wizualizatora współbieżności](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/03/09/analyzing-c-amp-code-with-the-concurrency-visualizer/)
