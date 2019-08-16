---
title: Używanie akceleratora i obiektów accelerator_view
ms.date: 11/04/2016
ms.assetid: 18f0dc66-8236-4420-9f46-1a14f2c3fba1
ms.openlocfilehash: 80d9c26f636cc736f90eacddea07a8fc31caff93
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512887"
---
# <a name="using-accelerator-and-accelerator_view-objects"></a>Używanie akceleratora i obiektów accelerator_view

Korzystając z klas [akceleratora](../../parallel/amp/reference/accelerator-class.md) i [accelerator_view](../../parallel/amp/reference/accelerator-view-class.md) , można określić urządzenie lub emulator do uruchamiania kodu C++ amp. System może mieć kilka urządzeń lub emulatorów, które różnią się ilością pamięci, obsługą pamięci współdzielonej, obsługą debugowania lub obsługą podwójnej precyzji. C++Przyspieszenie ogromnej współbieżnościC++ (amp) udostępnia interfejsy API, których można użyć do badania dostępnych akceleratorów, ustawić jedną jako domyślną, określić wiele accelerator_views dla wielu wywołań w parallel_for_each i wykonywać specjalne zadania debugowania.

## <a name="using-the-default-accelerator"></a>Korzystanie z akceleratora domyślnego

Środowisko C++ uruchomieniowe amp wybiera akcelerator domyślny, chyba że napiszesz kod w celu wybrania określonego. Środowisko uruchomieniowe wybiera akcelerator domyślny w następujący sposób:

1. Jeśli aplikacja jest uruchomiona w trybie debugowania, akcelerator obsługujący debugowanie.

2. W przeciwnym razie akcelerator, który jest określony przez zmienną środowiskową CPPAMP_DEFAULT_ACCELERATOR, jeśli jest ustawiony.

3. W przeciwnym razie urządzenie nieemulowane.

4. W przeciwnym razie urządzenie, które ma największą ilość dostępnej pamięci.

5. W przeciwnym razie urządzenie, które nie jest dołączone do ekranu.

Ponadto środowisko uruchomieniowe określa `access_type` `access_type_auto` wartość dla domyślnego akceleratora. Oznacza to, że akcelerator domyślny używa pamięci współdzielonej, jeśli jest obsługiwana, a jego charakterystyki wydajności (przepustowość i czas oczekiwania) są takie same, jak w przypadku dedykowanej (nieudostępnionej) pamięci.

Możesz określić właściwości domyślnego akceleratora, tworząc akcelerator domyślny i sprawdzając jego właściwości. Poniższy przykład kodu drukuje ścieżkę, ilość pamięci akceleratora, obsługę pamięci udostępnionej, obsługę podwójnej precyzji i ograniczoną obsługę podwójnej precyzji domyślnego akceleratora.

```cpp
void default_properties() {
    accelerator default_acc;
    std::wcout << default_acc.device_path << "\n";
    std::wcout << default_acc.dedicated_memory << "\n";
    std::wcout << (accs[i].supports_cpu_shared_memory ?
        "CPU shared memory: true" : "CPU shared memory: false") << "\n";
    std::wcout << (accs[i].supports_double_precision ?
        "double precision: true" : "double precision: false") << "\n";
    std::wcout << (accs[i].supports_limited_double_precision ?
        "limited double precision: true" : "limited double precision: false") << "\n";
}
```

### <a name="cppamp_default_accelerator-environment-variable"></a>Zmienna środowiskowa CPPAMP_DEFAULT_ACCELERATOR

Możesz ustawić zmienną środowiskową CPPAMP_DEFAULT_ACCELERATOR, aby określić `accelerator::device_path` akcelerator domyślny. Ścieżka jest zależna od sprzętu. Poniższy kod używa funkcji, `accelerator::get_all` aby pobrać listę dostępnych akceleratorów, a następnie wyświetlić ścieżkę i charakterystykę każdego akceleratora.

```cpp
void list_all_accelerators()
{
    std::vector<accelerator> accs = accelerator::get_all();

    for (int i = 0; i <accs.size(); i++) {
        std::wcout << accs[i].device_path << "\n";
        std::wcout << accs[i].dedicated_memory << "\n";
        std::wcout << (accs[i].supports_cpu_shared_memory ?
            "CPU shared memory: true" : "CPU shared memory: false") << "\n";
        std::wcout << (accs[i].supports_double_precision ?
            "double precision: true" : "double precision: false") << "\n";
        std::wcout << (accs[i].supports_limited_double_precision ?
            "limited double precision: true" : "limited double precision: false") << "\n";
    }
}
```

## <a name="selecting-an-accelerator"></a>Wybieranie akceleratora

Aby wybrać akcelerator, użyj `accelerator::get_all` metody do pobrania listy dostępnych akceleratorów, a następnie wybierz jeden na podstawie jego właściwości. Ten przykład pokazuje, jak wybrać akcelerator, który ma najwięcej pamięci:

```cpp
void pick_with_most_memory()
{
    std::vector<accelerator> accs = accelerator::get_all();
    accelerator acc_chosen = accs[0];

    for (int i = 0; i <accs.size(); i++) {
        if (accs[i].dedicated_memory> acc_chosen.dedicated_memory) {
            acc_chosen = accs[i];
        }
    }

    std::wcout << "The accelerator with the most memory is "
        << acc_chosen.device_path << "\n"
        << acc_chosen.dedicated_memory << ".\n";
}
```

> [!NOTE]
> Jednym z akceleratorów, które są zwracane przez `accelerator::get_all` program, jest akcelerator procesora. Nie można wykonać kodu w akceleratorze procesora CPU. Aby odfiltrować akcelerator procesora, należy porównać wartość właściwości [device_path](reference/accelerator-class.md#device_path) akceleratora, który jest zwracany przez `accelerator::get_all` wartość akceleratora [:: cpu_accelerator](reference/accelerator-class.md#cpu_accelerator). Aby uzyskać więcej informacji, zobacz sekcję "Akceleratory specjalne" w tym artykule.

## <a name="shared-memory"></a>Pamięć współdzielona

Pamięć współdzielona jest pamięcią, do której można uzyskać dostęp zarówno przy użyciu procesora, jak i akceleratora. Użycie pamięci współużytkowanej eliminuje lub znacznie zmniejsza obciążenie związane z kopiowaniem danych między PROCESORem a akceleratorem. Mimo że pamięć jest udostępniona, dostęp do niej nie jest możliwy jednocześnie przez procesor i akcelerator, a tym samym powoduje niezdefiniowane zachowanie. Właściwość akceleratora [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory) zwraca **wartość true** , Jeśli akcelerator obsługuje pamięć współużytkowaną, a właściwość [default_cpu_access_type](reference/accelerator-class.md#default_cpu_access_type) pobiera domyślną [access_type](reference/concurrency-namespace-enums-amp.md#access_type) dla pamięci przydzielonej na `accelerator`— na przykład **Tablica** `accelerator`s skojarzona z obiektami lub `array_view` `accelerator`, które są dostępne w.

Środowisko C++ uruchomieniowe amp automatycznie wybiera najlepsze wartości domyślne `access_type` dla każdej `accelerator`z nich, ale Charakterystyka wydajności (przepustowość i czas oczekiwania) pamięci współdzielonej może być gorsza niż w przypadku dedykowanej (nieudostępnionej) akceleratora pamięci, gdy Odczytywanie z procesora, zapisywanie z procesora CPU lub obu. Jeśli pamięć współdzielona pełni rolę dedykowanej pamięci do odczytu i zapisu z procesora CPU, domyślnie `access_type_read_write`środowisko uruchomieniowe to; w przeciwnym razie środowisko uruchomieniowe wybierze bardziej bardziej `access_type`ostrożne i umożliwi aplikacji zastąpienie go, jeśli dostęp do pamięci wzorce jego jądra obliczeń korzystają z innego `access_type`.

Poniższy przykład kodu pokazuje, jak ustalić, czy akcelerator domyślny obsługuje pamięć współużytkowaną, a następnie zastępuje swój domyślny typ dostępu i tworzy `accelerator_view` z niego.

```cpp
#include <amp.h>
#include <iostream>

using namespace Concurrency;

int main()
{
    accelerator acc = accelerator(accelerator::default_accelerator);

    // Early out if the default accelerator doesn’t support shared memory.
    if (!acc.supports_cpu_shared_memory)
    {
        std::cout << "The default accelerator does not support shared memory" << std::endl;
        return 1;
    }

    // Override the default CPU access type.
    acc.set_default_cpu_access_type(access_type_read_write);

    // Create an accelerator_view from the default accelerator. The
    // accelerator_view reflects the default_cpu_access_type of the
    // accelerator it’s associated with.
    accelerator_view acc_v = acc.default_view;
}
```

Zawsze `accelerator_view` odzwierciedla`accelerator` element skojarzony z i nie `access_type`zapewnia interfejsu do przesłonięcia lub zmiany. `default_cpu_access_type`

## <a name="changing-the-default-accelerator"></a>Zmiana domyślnego akceleratora

Akcelerator domyślny można zmienić, wywołując `accelerator::set_default` metodę. Akcelerator domyślny można zmienić tylko raz dla wykonywania aplikacji i należy go zmienić przed wykonaniem dowolnego kodu na procesorze GPU. Wszystkie kolejne wywołania funkcji do zmiany akceleratora zwracają **wartość false**. Jeśli chcesz użyć innego akceleratora w wywołaniu `parallel_for_each`, zapoznaj się z sekcją "używanie wielu akceleratorów" w tym artykule. Poniższy przykład kodu ustawia akcelerator domyślny na taki, który nie jest emulowany, nie jest połączony z ekranem i obsługuje podwójną precyzję.

```cpp
bool pick_accelerator()
{
    std::vector<accelerator> accs = accelerator::get_all();
    accelerator chosen_one;

    auto result = std::find_if(accs.begin(), accs.end(),
        [] (const accelerator& acc) {
            return !acc.is_emulated &&
                acc.supports_double_precision &&
                !acc.has_display;
        });

    if (result != accs.end()) {
        chosen_one = *(result);
    }

    std::wcout <<chosen_one.description <<std::endl;
    bool success = accelerator::set_default(chosen_one.device_path);
    return success;
}
```

## <a name="using-multiple-accelerators"></a>Korzystanie z wielu akceleratorów

Istnieją dwa sposoby użycia wielu akceleratorów w aplikacji:

- Można przekazać `accelerator_view` obiekty do wywołań metody [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) .

- Można skonstruować obiekt **Array** przy użyciu określonego `accelerator_view` obiektu. Środowisko uruchomieniowe C + amp pobierze `accelerator_view` obiekt z przechwyconego obiektu **Array** w wyrażeniu lambda.

## <a name="special-accelerators"></a>Akceleratory specjalne

Ścieżki urządzeń z trzema specjalnymi akceleratorami są dostępne jako właściwości `accelerator` klasy:

- [Akcelerator::D element członkowski danych irect3d_ref](reference/accelerator-class.md#direct3d_ref): Ten akcelerator jednowątkowy używa oprogramowania na PROCESORze do emulowania ogólnej karty graficznej. Jest on używany domyślnie do debugowania, ale nie jest użyteczny w środowisku produkcyjnym, ponieważ jest wolniejszy niż akceleratory sprzętowe. Ponadto jest on dostępny tylko w zestawie SDK programu DirectX i Windows SDK i nie jest mało prawdopodobne, aby można go było zainstalować na komputerach klientów. Aby uzyskać więcej informacji, zobacz [Debugowanie kodu GPU](/visualstudio/debugger/debugging-gpu-code).

- [accelerator::direct3d_warp Data Member](reference/accelerator-class.md#direct3d_warp): Ten akcelerator zawiera alternatywne rozwiązanie do wykonywania C++ kodu amp na wielordzeniowych procesorach korzystających z Streaming SIMD EXTENSIONS (SSE).

- [Akcelerator:: cpu_accelerator, składowa danych](reference/accelerator-class.md#cpu_accelerator): Ten akcelerator służy do konfigurowania tablic tymczasowych. Nie można wykonać C++ kodu amp. Aby uzyskać więcej informacji, zapoznaj się z [tablicami przemieszczania w C++ temacie amp](https://blogs.msdn.microsoft.com/nativeconcurrency/2011/11/09/staging-arrays-in-c-amp/) post na blogu dotyczącym programowania równoległego w kodzie natywnym.

## <a name="interoperability"></a>Współdziałanie

Środowisko C++ uruchomieniowe amp obsługuje współdziałanie między `accelerator_view` klasą i interfejsem [ID3D11Device](/windows/win32/api/d3d11/nn-d3d11-id3d11device)Direct3D. Metoda [create_accelerator_view](reference/concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view) `IUnknown` przyjmuje`accelerator_view` interfejs i zwraca obiekt. Metoda [get_device](reference/concurrency-direct3d-namespace-functions-amp.md#get_device) `accelerator_view` przyjmuje`IUnknown` obiekt i zwraca interfejs.

## <a name="see-also"></a>Zobacz także

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Debugowanie kodu GPU](/visualstudio/debugger/debugging-gpu-code)<br/>
[accelerator_view, klasa](../../parallel/amp/reference/accelerator-view-class.md)
