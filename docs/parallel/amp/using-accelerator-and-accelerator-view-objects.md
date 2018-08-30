---
title: Używanie akceleratora i obiektów accelerator_view | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: ebbb33a4f17f5b4d458c4add4d59040d698dd4b8
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43222197"
---
# <a name="using-accelerator-and-acceleratorview-objects"></a>Używanie akceleratora i obiektów accelerator_view
Możesz użyć [akceleratora](../../parallel/amp/reference/accelerator-class.md) i [accelerator_view](../../parallel/amp/reference/accelerator-view-class.md) klasy do określenia urządzenia lub emulatora do uruchamiania kodu C++ AMP. System może mieć kilka urządzeń lub emulatorów różniących się ilość pamięci, obsługę pamięci współdzielonej, obsługę debugowania lub wsparcia podwójnej precyzji. C++ Accelerated Massive Parallelism (C++ AMP) udostępnia interfejsy API, który służy do dostępnych akceleratorów, ustawienie jednego z nich jako domyślny, określenia wielu accelerator_views dla wielu wywołań parallel_for_each i wykonywania specjalnych zadań debugowania.  
  
## <a name="using-the-default-accelerator"></a>Używanie akceleratora domyślnego  
 
Środowisko wykonawcze C++ AMP wybiera akcelerator domyślny, chyba że zostanie napisany kod wybierający konkretny akcelerator. Środowisko wykonawcze wybiera akcelerator domyślny w następujący sposób:  
  
1. Jeśli aplikacja jest uruchomiona w trybie debugowania, akcelerator obsługuje debugowanie.  
  
2. W przeciwnym razie akcelerator, który jest określony przez zmienną środowiskową CPPAMP_DEFAULT_ACCELERATOR, jeśli jest ustawiona.  
  
3. W przeciwnym razie urządzenie emulowane.  
  
4. W przeciwnym razie urządzenie, które ma największą ilość dostępnej pamięci.  
  
5. W przeciwnym razie urządzenie, które nie jest dołączony do wyświetlenia.  
  
Ponadto środowisko wykonawcze określa `access_type` z `access_type_auto` dla akceleratora domyślnego. Oznacza to, że akcelerator domyślny używa pamięci współużytkowanej, jeśli jest on obsługiwany i jeśli jego Charakterystyka wydajności (przepustowość i czas oczekiwania) są znane jako takie same jak Dedykowana pamięć (nieudostępniana).  
  
Można określić właściwości domyślnego akceleratora przez skonstruowanie domyślnego akceleratora i zbadanie jego właściwości. Poniższy przykład kodu drukuje ścieżkę, ilość pamięci akceleratora, obsługę pamięci współdzielonej, obsługę podwójnej precyzji i ograniczoną obsługę podwójnej precyzji akceleratora domyślnego.  
  
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
  
### <a name="cppampdefaultaccelerator-environment-variable"></a>Zmienna środowiskowa Cppamp_default_accelerator  
Można ustawić zmienną środowiskową CPPAMP_DEFAULT_ACCELERATOR, aby określić `accelerator::device_path` akceleratora domyślnego. Ścieżka jest zależna od sprzętu. Poniższy kod używa `accelerator::get_all` funkcji, aby pobrać listę dostępnych akceleratorów, a następnie wyświetla ścieżkę i charakterystykę każdego akceleratora.  
  
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
 
Aby wybrać akcelerator, użyj `accelerator::get_all` metodę, aby pobrać listę dostępnych akceleratorów, a następnie wybierz jeden na podstawie jego właściwości. Ten przykład pokazuje, jak wybrać akcelerator, który ma najwięcej pamięci:  
  
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
> Jeden z akceleratorów, które są zwracane przez `accelerator::get_all` to akcelerator procesora CPU. Nie można wykonać kodu na akceleratorze Procesora. Aby odfiltrować accelerator procesora CPU, porównaj wartość [device_path](reference/accelerator-class.md#device_path) właściwość akceleratora, który jest zwracany przez `accelerator::get_all` z wartością [accelerator::cpu_accelerator](reference/accelerator-class.md#cpu_accelerator). Aby uzyskać więcej informacji zobacz sekcję "Specjalne akceleratory" w tym artykule.  
  
## <a name="shared-memory"></a>Pamięć współużytkowana  
 
Pamięć współużytkowana jest pamięcią, która może zostać oceniony przez Procesor ani akcelerator. Wykorzystanie pamięci współdzielonej eliminuje lub znacznie zmniejsza obciążenie kopiowania danych między procesorem a akceleratorem. Mimo że pamięć jest udostępniona, nie są dostępne w współbieżnie przez Procesor ani akcelerator, a czynność ta powoduje niezdefiniowane zachowanie. Właściwość akceleratora [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory) zwraca **true** Jeśli akcelerator obsługuje pamięć współużytkowaną, a [default_cpu_access_type](reference/accelerator-class.md#default_cpu_access_type) pobiera właściwość Wartość domyślna [access_type](reference/concurrency-namespace-enums-amp.md#access_type) dla pamięci przydzielonej na `accelerator`— na przykład **tablicy**związane z `accelerator`, lub `array_view` obiektami `accelerator`. 
  
Środowisko wykonawcze C++ AMP automatycznie wybiera najlepsze domyślne `access_type` dla każdego `accelerator`, ale cechy wydajności (przepustowość i czas oczekiwania) pamięci współużytkowanej, może być gorsza niż w przypadku dedykowanego (nieudostępnianego) akceleratora pamięci podczas odczytywania z procesora CPU, zapisu z CPU lub dla obu. Jeśli Pamięć współużytkowana działa jak Dedykowana pamięć dla odczytu i zapisu z Procesora, środowisko uruchomieniowe, wartość domyślna to `access_type_read_write`; w przeciwnym razie środowisko wykonawcze wybiera bardziej konserwatywnego domyślne `access_type`i umożliwia jej zastąpienie, jeśli pamięć już dostępu do aplikacji wzorce jej jąder obliczeniowych odniosą korzyści z innego `access_type`.  
  
Poniższy przykład kodu pokazuje, jak ustalić, czy akcelerator domyślny obsługuje pamięć współużytkowaną, a następnie zastępuje domyślny typ dostępu i tworzy `accelerator_view` z niego.  
  
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
  
`accelerator_view` Zawsze odzwierciedla `default_cpu_access_type` z `accelerator` jest skojarzony i zapewnia interfejs do nadpisania lub zmienić jego `access_type`.  
  
## <a name="changing-the-default-accelerator"></a>Zmienianie akceleratora domyślnego  
 
Akcelerator domyślny można zmienić, wywołując `accelerator::set_default` metody. Akcelerator domyślny można zmienić tylko wtedy, gdy na aplikację wykonywania i można go zmienić przed wykonaniem jakiegokolwiek kodu na procesorze GPU. Wszystkie kolejne wywołania funkcji zmiany akceleratora zwracają **false**. Jeśli chcesz użyć innego akceleratora w wywołaniu `parallel_for_each`, zapoznaj się z sekcją "Używanie wielu akceleratorów" w tym artykule. Poniższy przykład kodu ustawia akcelerator domyślny, który nie jest emulowana, nie jest podłączony do wyświetlania i obsługuje podwójną precyzję.  
  
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
 
Istnieją dwa sposoby użycia wielu akceleratorów w aplikacji:  

- Możesz przekazać `accelerator_view` obiekty do wywołania [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) metody.  
  
- Można skonstruować **tablicy** obiekt, za pomocą określonego `accelerator_view` obiektu. Środowisko wykonawcze C + AMP wybierze `accelerator_view` obiektu z przechwyconych **tablicy** obiektu w wyrażeniu lambda.  
  
## <a name="special-accelerators"></a>Akceleratory specjalne  
 
Ścieżki urządzenia dla trzech akceleratorów specjalnych są dostępne jako właściwości `accelerator` klasy:  
  
- [Accelerator::direct3d_ref — element członkowski danych](reference/accelerator-class.md#direct3d_ref): ten akcelerator jednowątkowy używa oprogramowania CPU do emulowania rodzajowej karty graficznej. Jest on używany domyślnie do debugowania, ale nie jest przydatne w środowisku produkcyjnym, ponieważ jest wolniejszy niż akceleratory sprzętowe. Ponadto jest dostępna tylko w zestawie DirectX SDK i zestaw Windows SDK i jest mało prawdopodobne, należy zainstalować na komputerach klientów. Aby uzyskać więcej informacji, zobacz [debugowania kodu GPU](/visualstudio/debugger/debugging-gpu-code).  
  
- [Accelerator::direct3d_warp — element członkowski danych](reference/accelerator-class.md#direct3d_warp): Akcelerator ten dostarcza rozwiązanie alternatywne do wykonywania kodu C++ AMP na wielordzeniowych procesorach, które używają rozszerzenia SSE (Streaming SIMD).  
  
- [Accelerator::cpu_accelerator — członek danych](reference/accelerator-class.md#cpu_accelerator): Akcelerator ten można użyć do tworzenia tablic tymczasowych. Nie może wykonywać kodu C++ AMP. Aby uzyskać więcej informacji, zobacz [tablice tymczasowe w bibliotece C++ AMP](http://go.microsoft.com/fwlink/p/?linkId=248485) opublikuj wpis na blogu programowania równoległego w kodzie natywnym.  
  
## <a name="interoperability"></a>Współdziałanie  
 
Środowisko wykonawcze C++ AMP wspiera współdziałanie między `accelerator_view` klasy a występującym w Direct3D [interfejsu ID3D11Device](http://go.microsoft.com/fwlink/p/?linkId=248488). [Create_accelerator_view —](reference/concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view) metoda przyjmuje `IUnknown` interfejsu i zwraca `accelerator_view` obiektu. [Get_device](https://msdn.microsoft.com/8194125e-8396-4d62-aa8a-65831dea8439) metoda przyjmuje `accelerator_view` obiektu i zwraca `IUknown` interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 
[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
[Debugowanie kodu GPU](/visualstudio/debugger/debugging-gpu-code)   
[accelerator_view, klasa](../../parallel/amp/reference/accelerator-view-class.md)