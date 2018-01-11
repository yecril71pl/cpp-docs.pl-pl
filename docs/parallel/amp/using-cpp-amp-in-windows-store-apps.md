---
title: Korzystanie z C++ AMP w aplikacjach Sklepu Windows | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 85577298-2c28-4209-9470-eb21048615db
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3fa6b42dd4e00f3b5314806933d06b3c1534b4d7
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="using-c-amp-in-windows-store-apps"></a>Korzystanie z C++ AMP w aplikacjach sklepu Windows Store
C++ AMP (C++ Accelerated Massive Parallelism) można używać w sieci [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji do wykonywania obliczeń w procesora GPU (przetwarzania graficzny) lub innych akceleratorów obliczeniową. Jednak C++ AMP nie udostępnia interfejsy API do pracy bezpośrednio z typów środowiska wykonawczego systemu Windows i środowiska wykonawczego systemu Windows nie udostępnia otokę dla C++ AMP. Jeśli używasz typów środowiska wykonawczego systemu Windows w kodzie — łącznie z tymi, które zostały utworzone samodzielnie — muszą być konwertowane na typy, które są zgodne z C++ AMP.  
  
## <a name="performance-considerations"></a>Zagadnienia dotyczące wydajności  
 Jeśli używasz [!INCLUDE[cppwrt](../../build/reference/includes/cppwrt_md.md)] ([!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]) do utworzenia sieci [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji, firma Microsoft zaleca się używanie typów zwykły stare dane (POD) oraz ciągłe magazynu — na przykład `std::vector` lub tablic w stylu języka C — dla danych, które będą używane z C++ AMP. To może pomóc osiągnąć większą wydajność niż przy użyciu typów innych niż POD lub Windows RT kontenerów, ponieważ nie organizowanie nie ma wystąpić.  
  
 Jądra C++ AMP, dostęp do danych przechowywanych w ten sposób tylko zawijać `std::vector` lub macierz pamięci masowej w `concurrency::array_view` , a następnie użyć widoku tablicy w `concurrency::parallel_for_each` Pętla:  
  
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
 Podczas pracy z interfejsami API środowiska wykonawczego systemu Windows może chcesz użyć C++ AMP danych, które są przechowywane w kontenerze środowiska wykonawczego systemu Windows, takich jak `Platform::Array<T>^` lub złożone typy danych, takich jak klasy lub struktury, które są zadeklarowane za pomocą `ref` — słowo kluczowe lub `value`</C4>—słowokluczowe. W takich sytuacjach należy wykonywania dodatkowej pracy, aby udostępnić dane C++ AMP.  
  
### <a name="platformarrayt-where-t-is-a-pod-type"></a>Platform::Array\<T > ^, gdzie T jest typ POD  
 Jeśli wystąpią `Platform::Array<T>^` i T jest typem POD, jego powiązany magazyn można dostęp tylko za pomocą `get` funkcji członkowskiej:  
  
```cpp  
Platform::Array<float>^ arr; // Assume that this was returned by a Windows Runtime API  
concurrency::array_view<float, 1> av(arr->Length, &arr->get(0));
```  
  
 Jeśli T nie jest typem POD, użyj techniki, które jest opisane w poniższej sekcji, to użycie danych z C++ AMP.  
  
### <a name="windows-runtime-types-ref-classes-and-value-classes"></a>Typy środowiska wykonawczego systemu Windows: klasy odniesienia i klasy wartości  
 C++ AMP nie obsługuje złożone typy danych. Obejmuje to typów innych niż POD i żadnych typów, które są zadeklarowane za pomocą `ref` — słowo kluczowe lub `value` — słowo kluczowe. Użycie nieobsługiwanego typu `restrict(amp)` wygenerowaniu kontekstu, błąd kompilacji.  
  
 W przypadku wystąpienia nieobsługiwanego typu można skopiować interesujące części jego danych do `concurrency::array` obiektu. Oprócz udostępniania danych dla C++ AMP korzystać, tej metody ręcznego kopiowania także może zwiększyć wydajność, maksymalizując lokalizację danych i zapewniając, że dane, które nie będą używane nie jest skopiowany do akceleratora. Dalsze wydajność można poprawić za pomocą *przemieszczania tablicy*, który jest specjalny rodzaj `concurrency::array` zapewnia wskazówkę obsługi AMP tablicy powinien być zoptymalizowany pod kątem częste transferu między nim a tablic w określony akceleratora.  
  
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
 [Tworzenie pierwszej aplikacji Sklepu Windows w języku C++](http://go.microsoft.com/fwlink/p/?linkid=249073)   
 [Tworzenie składników środowiska wykonawczego systemu Windows w języku C++](http://go.microsoft.com/fwlink/p/?linkid=249076)



