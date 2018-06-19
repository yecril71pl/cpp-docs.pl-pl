---
title: Za pomocą akceleratora i obiektów accelerator_view | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 18f0dc66-8236-4420-9f46-1a14f2c3fba1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9e0f86467de8256eaecbfbf42765de551a1e2f6e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690614"
---
# <a name="using-accelerator-and-acceleratorview-objects"></a>Używanie akceleratora i obiektów accelerator_view
Można użyć [akceleratora](../../parallel/amp/reference/accelerator-class.md) i [accelerator_view](../../parallel/amp/reference/accelerator-view-class.md) klas, aby określić urządzenia lub emulatora do uruchomienia kodu C++ AMP na. System może mieć kilka urządzeń lub emulatory, które różnią się według ilości pamięci, obsługi pamięci udostępnionej, obsługę debugowania lub obsługę podwójnej precyzji. C++ Accelerated Massive Parallelism (C++ AMP) udostępnia interfejsy API, który służy do badania dostępne akceleratorów, Ustaw jako domyślny, określ accelerator_views wiele do wielu wywołań parallel_for_each i wykonać specjalne zadania debugowania.  
  
## <a name="using-the-default-accelerator"></a>Przy użyciu domyślnego akceleratora  
 Środowiska uruchomieniowego C++ AMP wybiera akceleratora domyślną, chyba że napisać kod, aby wybrać określoną. Środowisko uruchomieniowe wybierze akceleratora domyślne w następujący sposób:  
  
1.  Jeśli aplikacja działa w trybie debugowania, akceleratora obsługujący debugowania.  
  
2.  W przeciwnym razie akcelerator, który jest określony przez zmienną środowiskową CPPAMP_DEFAULT_ACCELERATOR, jeśli jest ustawiona.  
  
3.  W przeciwnym razie urządzenia z systemem innym niż emulowane.  
  
4.  W przeciwnym razie urządzenia, które ma największą ilość dostępnej pamięci.  
  
5.  W przeciwnym razie urządzenia, który nie jest dołączony do wyświetlenia.  
  
 Ponadto określa środowisko uruchomieniowe `access_type` z `access_type_auto` dla domyślnego akceleratora. Oznacza to, domyślnego akceleratora używa pamięci współużytkowanej, jeśli jest obsługiwana i jeśli wiadomo, że jej charakterystyki wydajności (przepustowości i opóźnień) być taki sam jak dedykowanej pamięci (z systemem innym niż udostępniana).  
  
 Właściwości klawiszy skrótów domyślne można określić, tworząc akceleratora domyślne i sprawdzenie jego właściwości. Poniższy przykład kodu wyświetla ścieżkę, ilość pamięci akceleratora, obsługi pamięci udostępnionej, obsługę podwójnej precyzji i ograniczoną obsługę podwójnej precyzji domyślnego akceleratora.  
  
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
  
### <a name="cppampdefaultaccelerator-environment-variable"></a>Zmienna środowiskowa CPPAMP_DEFAULT_ACCELERATOR  
 Można ustawić zmiennej środowiskowej CPPAMP_DEFAULT_ACCELERATOR, aby określić `accelerator::device_path` domyślnego akceleratora. Ścieżka jest zależne od sprzętu. Poniższy kod używa `accelerator::get_all` funkcji, aby pobrać listę dostępnych akceleratorów, a następnie wyświetla ścieżkę i właściwości każdego akceleratora.  
  
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
 Aby wybrać akceleratora, użyj `accelerator::get_all` metodę, aby pobrać listę dostępnych akceleratorów, a następnie wybierz jedno na podstawie jego właściwości. W tym przykładzie pokazano, jak i wybierz akcelerator, który ma najwięcej pamięci:  
  
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
>  Jeden z akceleratorów, które są zwracane przez `accelerator::get_all` to akcelerator procesora CPU. Nie można wykonać kod na akceleratora procesora CPU. Aby filtrować akceleratora procesora CPU, porównanie wartości [device_path —](reference/accelerator-class.md#device_path) właściwości klawiszy skrótów, który jest zwracany przez `accelerator::get_all` z wartością [Accelerator::cpu_accelerator —](reference/accelerator-class.md#cpu_accelerator). Aby uzyskać więcej informacji zobacz sekcję "Specjalne akceleratorów" w tym artykule.  
  
## <a name="shared-memory"></a>Pamięci współużytkowanej  
 Pamięci współużytkowanej jest pamięci dostępnej dla procesora CPU i akceleratora. Użycie pamięci współużytkowanej eliminuje lub znacznie zmniejsza obciążenie związane z kopiowanie danych między procesora CPU i akceleratora. Choć jest udostępniana pamięć, jest niedostępny jednocześnie przez procesor CPU i akceleratora i powoduje to niezdefiniowane zachowanie. Właściwości klawiszy skrótów [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory) zwraca `true` Jeśli akceleratora obsługuje pamięci współużytkowanej i [default_cpu_access_type](reference/accelerator-class.md#default_cpu_access_type) właściwości pobiera domyślne [access_type](reference/concurrency-namespace-enums-amp.md#access_type) pamięci przydzielona w `accelerator`— na przykład `array`s skojarzone z `accelerator`, lub `array_view` obiektów dostępny na `accelerator`. 
  
 Środowiska uruchomieniowego C++ AMP automatycznie wybiera najlepsze domyślne `access_type` dla każdego `accelerator`, ale charakterystyki wydajności (przepustowości i opóźnień) pamięci współużytkowanej może być gorsza niż w przypadku dedykowanego akceleratora (z systemem innym niż udostępniana) pamięci podczas odczytu z Procesora, zapisywanie z Procesora, lub obie. Jeśli pamięci współużytkowanej wykonuje oraz dedykowanej pamięci do odczytu i zapisu z Procesora, środowisko uruchomieniowe domyślnie `access_type_read_write`; w przeciwnym razie środowiska uruchomieniowego wybiera domyślny więcej zachowawcze `access_type`i umożliwia jej zastąpienie, jeśli pamięć dostępu do aplikacji wzorce jego jądra obliczeń korzystać z innego `access_type`.  
  
 Poniższy przykład kodu pokazuje sposób określania, czy domyślnego akceleratora obsługuje pamięci współużytkowanej, a następnie zastępuje jego domyślny typ dostępu i tworzy `accelerator_view` z niego.  
  
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
  
 `accelerator_view` Zawsze odzwierciedla `default_cpu_access_type` z `accelerator` skojarzonej z nim i zapewnia interfejs nie można zastąpić lub zmienić jego `access_type`.  
  
## <a name="changing-the-default-accelerator"></a>Zmiana domyślnego akceleratora  
 Można zmienić domyślnego akceleratora przez wywołanie metody `accelerator::set_default` metody. Akceleratora domyślne można zmienić tylko po każdej aplikacji i wykonywanie muszą go zmienić przed wykonaniem żadnego kodu na procesorze GPU. Zwróć wszystkie wywołania funkcji kolejne zmiany akceleratora `false`. Jeśli chcesz użyć innego akceleratora w wywołaniu `parallel_for_each`, przeczytaj informacje w sekcji "Używanie wielu akceleratorów" w tym artykule. Poniższy przykład kodu, który nie jest emulowana, nie jest podłączony do wyświetlania i obsługuje podwójnej precyzji ustawia domyślnego akceleratora.  
  
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
  
## <a name="using-multiple-accelerators"></a>Używanie wielu akceleratorów  
 Istnieją dwa sposoby używania wielu akceleratory w aplikacji:  

-   Można przekazać `accelerator_view` obiektów do wywołania metody [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) metody.  
  
-   Można utworzyć `array` przy użyciu określonego `accelerator_view` obiektu. Środowisko uruchomieniowe C + AMP pobierze `accelerator_view` przechwyconego obiektu `array` obiektu w wyrażeniu lambda.  
  
## <a name="special-accelerators"></a>Specjalne akceleratorów  
 Ścieżki urządzeń trzech specjalnych akceleratorów są dostępne jako właściwości `accelerator` klasy:  
  
- [Accelerator::direct3d_ref — członek danych](reference/accelerator-class.md#direct3d_ref): tego akceleratora jednowątkowe przy użyciu oprogramowania na Procesorze emulować to karta Ogólne. Jest on używany domyślnie do debugowania, ale nie jest przydatne w środowisku produkcyjnym, ponieważ jest mniejsza niż akceleratorów sprzętowych. Ponadto jest dostępna tylko w zestawie SDK programu DirectX i zestaw Windows SDK i jest mało prawdopodobne, można zainstalować na komputerach klientów. Aby uzyskać więcej informacji, zobacz [debugowanie kodu GPU](/visualstudio/debugger/debugging-gpu-code).  
  
- [Accelerator::direct3d_warp — członek danych](reference/accelerator-class.md#direct3d_warp): tego akceleratora zapewnia rozwiązanie powrotu do wykonywania kodu C++ AMP w wielordzeniowych procesorów CPU, które używają Streaming SIMD Extensions (SSE).  
  
- [Accelerator::cpu_accelerator — członek danych](reference/accelerator-class.md#cpu_accelerator): tego akceleratora służy do konfigurowania przemieszczania tablic. Nie można go wykonać kod C++ AMP. Aby uzyskać więcej informacji, zobacz [przemieszczania tablic w języku C++ AMP](http://go.microsoft.com/fwlink/p/?linkId=248485) post na Programowanie równoległe w blogu kodu natywnego.  
  
## <a name="interoperability"></a>Współdziałanie  
 Współdziałanie między obsługuje środowiska uruchomieniowego C++ AMP `accelerator_view` klasy i Direct3D [ID3D11Device interfejsu](http://go.microsoft.com/fwlink/p/?linkId=248488). [Create_accelerator_view —](reference/concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view) ma metodę `IUnknown` interfejsu i zwraca `accelerator_view` obiektu. [Get_device](http://msdn.microsoft.com/en-us/8194125e-8396-4d62-aa8a-65831dea8439) ma metodę `accelerator_view` obiektu i zwraca `IUknown` interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [Debugowanie kodu GPU](/visualstudio/debugger/debugging-gpu-code)   
 [accelerator_view, klasa](../../parallel/amp/reference/accelerator-view-class.md)
