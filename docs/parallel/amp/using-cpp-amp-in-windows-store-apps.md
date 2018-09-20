---
title: Korzystanie z C++ AMP w aplikacjach platformy uniwersalnej systemu Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 85577298-2c28-4209-9470-eb21048615db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: faa26db2df606502bf4a80f21d7a5be4bafc1f9e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377803"
---
# <a name="using-c-amp-in-uwp-apps"></a>Korzystanie z C++ AMP w aplikacjach platformy UWP

C++ AMP (C++ Accelerated Massive Parallelism) w aplikacji platformy uniwersalnej Windows (UWP) umożliwia wykonywanie obliczeń na procesorze GPU (jednostka przetwarzania grafiki) lub innych akceleratorach obliczeniowych. Jednak C++ AMP nie zapewnia interfejsu API do pracy bezpośrednio z typami środowiska wykonawczego Windows i środowisko wykonawcze Windows nie zapewnia otoki dla C++ AMP. Kiedy używasz typów środowiska wykonawczego Windows w swoim kodzie — włączając te, utworzone przez Ciebie — musisz konwertować je na typy, które są kompatybilne z C++ AMP.

## <a name="performance-considerations"></a>Zagadnienia dotyczące wydajności

Jeśli używasz rozszerzeń składnik Visual C++ C + +/ CX do tworzenia aplikacji uniwersalnych platformy Windows (UWP), zalecamy użycie typów zwykły stare dane (POD) wraz z ciągłym magazynowaniem — na przykład `std::vector` lub tablice stylu C — dla danych, który ma być używane z C++ AMP. Może to pomóc Ci osiągnąć wyższą wydajność niż przy użyciu typów non-POD lub kontenerów Windows RT, ponieważ musi występować szeregowanie nie.

W jądrze C++ AMP, dostęp do danych przechowywanych w ten sposób, należy po prostu zawinąć `std::vector` lub magazyn tablic w `concurrency::array_view` , a następnie użyć widoku tablicy w `concurrency::parallel_for_each` Pętla:

```cpp
// simple vector addition example
std::vector<int> data0(1024, 1);
std::vector<int> data1(1024, 2);
std::vector<int> data_out(data0.size(), 0);

concurrency::array_view<int, 1> av0(data0.size(), data0);
concurrency::array_view<int, 1> av1(data1.size(), data1);
concurrency::array_view<int, 1> av2(data_out.size(), data2);

av2.discard_data();

concurrency::parallel_for_each(av0.extent, [=](concurrency::index<1> idx) restrict(amp)
    {
        av2[idx] = av0[idx] + av1[idx];
    });
```

## <a name="marshaling-windows-runtime-types"></a>Szeregowanie typów środowiska wykonawczego systemu Windows

Podczas pracy z interfejsami API środowiska wykonawczego Windows, warto używać C++ AMP na dane, które są przechowywane w kontenerze środowiska wykonawczego Windows, takich jak `Platform::Array<T>^` lub złożonych typach danych takich jak klasy lub struktury, które są zadeklarowane za pomocą **ref** słowo kluczowe lub **wartość** — słowo kluczowe. W takich sytuacjach należy wykonać dodatkową pracę, aby udostępnić dane C++ AMP.

### <a name="platformarrayt-where-t-is-a-pod-type"></a>Platform::Array\<T > ^, gdzie T jest typem POD

Gdy wystąpi `Platform::Array<T>^` i T jest typem POD, dostęp do jego podstawowej magazynu przy użyciu `get` funkcja elementu członkowskiego:

```cpp
Platform::Array<float>^ arr; // Assume that this was returned by a Windows Runtime API
concurrency::array_view<float, 1> av(arr->Length, &arr->get(0));
```

Jeśli T nie jest typem POD, użyj metody opisanej w poniższej sekcji, za pomocą danych z C++ AMP.

### <a name="windows-runtime-types-ref-classes-and-value-classes"></a>Typy środowiska wykonawczego systemu Windows: klasy odniesienia i klasy wartości

Wzmacniacz C++ nie obsługuje złożonych typów danych. Obejmuje to typy non-POD i wszystkie typy, które są zadeklarowane za pomocą **ref** — słowo kluczowe lub **wartość** — słowo kluczowe. Jeśli nieobsługiwany typ jest używany w `restrict(amp)` kontekstu, błąd kompilacji jest generowany.

Kiedy napotykasz nieobsługiwany typ, możesz skopiować interesujące części jego danych do `concurrency::array` obiektu. Oprócz udostępnienia danych dla języka C++ AMP do konsumpcji, to podejście ręcznego kopiowania może również zwiększyć wydajność maksymalizując miejscowość danych i zapewniając, że dane, które nie będą używane nie zostaną skopiowane do akceleratora. Możesz podnieść wydajność jeszcze bardziej używając *przemieszczania tablicy*, która jest specjalną postać `concurrency::array` , dostarcza wskazówkę obiektowi środowisko wykonawcze AMP, który optymalizacji tablicy dla częstych transferów między nim a innymi tablicami w określonym akceleratorze.

```cpp
// pixel_color.h
ref class pixel_color sealed
{
public:
    pixel_color(Platform::String^ color_name, int red, int green, int blue)
    {
        name = color_name;
        r = red;
        g = green;
        b = blue;
    }

    property Platform::String^ name;
    property int r;
    property int g;
    property int b;
};

// Some other file

std::vector<pixel_color^> pixels (256);

for (pixel_color ^pixel : pixels)
{
    pixels.push_back(ref new pixel_color("blue", 0, 0, 255));
}

// Create the accelerators
auto cpuAccelerator = concurrency::accelerator(concurrency::accelerator::cpu_accelerator);
auto devAccelerator = concurrency::accelerator(concurrency::accelerator::default_accelerator);

// Create the staging arrays
concurrency::array<float, 1> red_vec(256, cpuAccelerator.default_view, devAccelerator.default_view);
concurrency::array<float, 1>  blue_vec(256, cpuAccelerator.default_view, devAccelerator.default_view);

// Extract data from the complex array of structs into staging arrays.
concurrency::parallel_for(0, 256, [&](int i)
    {
        red_vec[i] = pixels[i]->r;
        blue_vec[i] = pixels[i]->b;
    });

// Array views are still used to copy data to the accelerator
concurrency::array_view<float, 1> av_red(red_vec);
concurrency::array_view<float, 1> av_blue(blue_vec);

// Change all pixels from blue to red.
concurrency::parallel_for_each(av_red.extent, [=](index<1> idx) restrict(amp)
    {
        av_red[idx] = 255;
        av_blue[idx] = 0;
    });
```

## <a name="see-also"></a>Zobacz też

[Tworzenie pierwszej aplikacji platformy uniwersalnej systemu Windows przy użyciu języka C++](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)<br/>
[Tworzenie składników środowiska wykonawczego Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)