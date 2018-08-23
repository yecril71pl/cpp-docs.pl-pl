---
title: Tablica i WriteOnlyArray (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: ef7cc5f9-cae6-4636-8220-f789e5b6aea4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: adad70bfa069a43382c06f60dea53bc2e53ff187
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606115"
---
# <a name="array-and-writeonlyarray-ccx"></a>Tablica i WriteOnlyArray (C + +/ CX)
Można bez ograniczeń wykorzystywać regularne tablice stylu C lub [std::array](../standard-library/array-class-stl.md) w języku C + +/ CX program (mimo że [std::vector](../standard-library/vector-class.md) często jest lepszym rozwiązaniem), ale w dowolnym interfejsem API, który jest publikowany w metadanych, należy przekonwertować tablicy stylu C lub vector do [Platform::Array](../cppcx/platform-array-class.md) lub [Platform::WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md) typu, w zależności od tego, w jaki sposób jest używany. [Platform::Array](../cppcx/platform-array-class.md) typu nie jest wydajne ani jak [std::vector](../standard-library/vector-class.md), więc generalnie nie należy jej użycia w kodu wewnętrznego, który wykonuje wiele operacji na tablicy elementy.  
  
 Następujące typy tablicy mogą być przekazywane między interfejsem ABI:  
  
1.  Const Platform::Array ^  
  
2.  Platform::Array ^ *  
  
3.  Platform::WriteOnlyArray  
  
4.  Zwraca wartość Platform::Array ^  
  
 Można użyć tych typów tablicy do zaimplementowania trzy rodzaje wzorców tablicy, które są definiowane przez środowisko wykonawcze Windows.  
  
 PassArray  
 Używane, gdy obiekt wywołujący przekazuje tablicę do metody. Typ parametru wejściowego C++ jest `const` [Platform::Array](../cppcx/platform-array-class.md)\<T >.  
  
 FillArray  
 Używany, gdy wywołanie metody do wypełnienia tablicy. Typ parametru wejściowego C++ jest [Platform::WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md)\<T >.  
  
 ReceiveArray  
 Używany, gdy obiekt wywołujący otrzymuje tablicę, która metoda przydziela. W języku C + +/ CX może zwracać tablicy wartości zwracanej jako tablica ^ lub można przywrócić go jako parametru wyjściowego pisania tablicy ^ *.  
  
## <a name="passarray-pattern"></a>Wzorzec PassArray  
 Jeśli metoda nie powoduje modyfikacji go kod klienta przekazuje tablicę do metody, C++, metoda akceptuje tablicy jako const tablicy ^. Na poziomie interfejsem binarnym (ABI) aplikacji środowiska wykonawczego Windows jest to nazywane PassArray. Następny przykład pokazuje, jak przekazać tablicę, która jest przydzielany w języku JavaScript do funkcji języka C++, która odczytuje z niego.  
  
 [!code-javascript[cx_arrays#101](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_1.js)]  
  
 Poniższy fragment kodu przedstawia metodę C++:  
  
 [!code-cpp[cx_arrays#01](../cppcx/codesnippet/CPP/js-array/class1.cpp#01)]  
  
## <a name="receivearray-pattern"></a>Wzorzec ReceiveArray  
 We wzorcu ReceiveArray kod klienta deklaruje tablicę i przekazuje go do metody, które przydziela pamięć i inicjuje ją. Typ parametru wejściowego C++ jest wskaźnik do hat: `Array<T>^*`. Poniższy przykład pokazuje sposób deklarowania obiektu tablicy w języku JavaScript i przekazać go do funkcji języka C++, który przydziela pamięć, inicjuje elementy i zwraca go do języka JavaScript. JavaScript traktuje przydzielanej tablicy jako wartość zwracaną, ale funkcja C++ traktuje je jako parametrem out.  
  
 [!code-javascript[cx_arrays#102](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_3.js)]  
  
 Poniższy fragment kodu przedstawia dwa sposoby, aby wdrożyć metodę C++:  
  
 [!code-cpp[cx_arrays#02](../cppcx/codesnippet/CPP/js-array/class1.cpp#02)]  
  
## <a name="fill-arrays"></a>Wypełnij tablic  
 Kiedy chcesz przydzielić tablicy w obiekcie wywołującym, zainicjować i go modyfikować w / / wywoływany, użyj `WriteOnlyArray`. W kolejnym przykładzie pokazano sposób implementacji funkcji języka C++, który używa `WriteOnlyArray` i wywołać go z języka JavaScript.  
  
 [!code-javascript[cx_arrays#103](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_5.js)]  
  
 Poniższy fragment kodu pokazuje, jak zaimplementować metodę C++:  
  
 [!code-cpp[cx_arrays#03](../cppcx/codesnippet/CPP/js-array/class1.cpp#03)]  
  
## <a name="array-conversions"></a>Konwersje tablic  
 W tym przykładzie pokazano, jak używać [Platform::Array](../cppcx/platform-array-class.md) do konstruowania inne rodzaje kolekcji:  
  
 [!code-cpp[cx_arrays#05](../cppcx/codesnippet/CPP/js-array/class1.cpp#05)]  
  
 W kolejnym przykładzie pokazano sposób tworzenia [Platform::Array](../cppcx/platform-array-class.md) ze stylu C macierz, a następnie przywrócić go z publiczną metodę.  
  
 [!code-cpp[cx_arrays#06](../cppcx/codesnippet/CPP/js-array/class1.cpp#06)]  
  
## <a name="jagged-arrays"></a>Tablice nieregularne  
 System typów środowiska wykonawczego Windows nie obsługuje pojęcie Tablice nieregularne i dlatego nie można używać `IVector<Platform::Array<T>>` jako parametr wartość lub metoda zwracany w publicznej metodzie. Aby przekazać tablicę nieregularną lub sekwencji między interfejsem ABI, należy użyć `IVector<IVector<T>^>`.  
  
## <a name="use-arrayreference-to-avoid-copying-data"></a>Użyj ArrayReference w celu uniknięcia kopiowania danych  
 W niektórych scenariuszach, gdzie dane są przekazywane między ABI do [Platform::Array](../cppcx/platform-array-class.md), a ostatecznie chce przetwarzać dane w tablicy stylu C w celu zwiększenia wydajności, można użyć [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) Aby uniknąć operacji kopiowania dodatkowych. Podczas przekazywania [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) jako argumentu do parametru, który przyjmuje `Platform::Array`, `ArrayReference` będą przechowywane dane bezpośrednio do tablicy stylu C, który określisz. Tylko należy pamiętać, że `ArrayReference` ma nie blokadę na źródle danych, więc jeśli zmodyfikowane lub usunięte w innym wątku przed zakończeniem wywołanie danych, wyniki będzie niezdefiniowane.  
  
 Poniższy fragment kodu przedstawia sposób kopiowania wyników [DataReader](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.datareader.aspx) operacji na `Platform::Array` (zwyczajowego wzorca) i następnie zastąp `ArrayReference` do kopiowania danych bezpośrednio do tablicy stylu C:  
  
 [!code-cpp[cx_arrays#07](../cppcx/codesnippet/CPP/js-array/class1.h#07)]  
  
## <a name="avoid-exposing-an-array-as-a-property"></a>Należy unikać udostępnianie tablicę jako właściwość  
 Ogólnie rzecz biorąc, należy unikać udostępnianie `Platform::Array` wpisać jako właściwości w klasie ref, ponieważ zwracany jest całej tablicy, nawet wtedy, gdy kod klienta jest tylko próba uzyskania dostępu pojedynczy element. Gdy trzeba udostępnić kontenerem sekwencyjnym jako właściwość w klasie ref publicznych [Windows::Foundation::IVector](http://msdn.microsoft.com/library/windows/apps/br206631.aspx) jest lepszym rozwiązaniem. Prywatne lub wewnętrzne interfejsów API, (które nie są publikowane w metadanych), należy wziąć pod uwagę przy użyciu standardowych kontener C++, takich jak [std::vector](../standard-library/vector-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [System typów](../cppcx/type-system-c-cx.md)   
 [Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)