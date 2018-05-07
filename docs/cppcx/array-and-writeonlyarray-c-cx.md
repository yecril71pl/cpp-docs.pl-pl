---
title: Tablica i WriteOnlyArray (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: ef7cc5f9-cae6-4636-8220-f789e5b6aea4
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 47c26ef4058cc3116d964740a93f7395c300b92b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="array-and-writeonlyarray-ccx"></a>Tablica i WriteOnlyArray (C + +/ CX)
Za darmo można użyć regularne tablice w stylu języka C lub [std::array](../standard-library/array-class-stl.md) w języku C + +/ CX programu (mimo że [std::vector](../standard-library/vector-class.md) często jest lepszym rozwiązaniem), ale w API, który jest publikowany w metadanych, należy przekonwertować tablicy stylu języka C lub wektorów do [Platform::Array](../cppcx/platform-array-class.md) lub [Platform::WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md) typu, w zależności od tego, jak jest używany. [Platform::Array](../cppcx/platform-array-class.md) typu nie jest tak efektywne ani wydajne jako [std::vector](../standard-library/vector-class.md), więc generalnie nie należy jej użycie w wewnętrzny kod, który wykonuje wiele operacji na tablicy elementy.  
  
 Następujące typy tablicy mogą być przekazywane między interfejsem ABI:  
  
1.  Const Platform::Array ^  
  
2.  Platform::Array ^ *  
  
3.  Platform::WriteOnlyArray  
  
4.  Zwraca wartość Platform::Array ^  
  
 Aby zaimplementować trzy rodzaje tablicy wzorców, które są zdefiniowane przez środowisko wykonawcze systemu Windows jest używanie tych typów tablicy.  
  
 PassArray  
 Używany, gdy obiekt wywołujący tablicy do metody. Typ parametru wejściowego C++ jest `const` [Platform::Array](../cppcx/platform-array-class.md)\<T >.  
  
 FillArray  
 Używany, gdy obiekt wywołujący tablicy dla metody do wypełnienia. Typ parametru wejściowego C++ jest [Platform::WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md)\<T >.  
  
 ReceiveArray  
 Używane, gdy obiekt wywołujący uzyskuje tablicę, która metoda przydziela. W języku C + +/ CX może zwracać tablicy w wartości zwracanej jako tablica ^ lub można przywrócić go jako parametr wyjściowy jako typu tablicy ^ *.  
  
## <a name="passarray-pattern"></a>Wzorzec PassArray  
 Gdy kod klienta przekazuje tablicy do metody C++ i metody nie zostanie zmodyfikowana, metoda akceptuje tablicy jako const Array ^. Na poziomie interfejsu binarne (ABI) aplikacji środowiska wykonawczego systemu Windows jest to nazywane PassArray. Kolejnym przykładzie pokazano, jak przekazać tablicę, która jest przydzielona w języku JavaScript do funkcji języka C++, która odczytuje z niego.  
  
 [!code-javascript[cx_arrays#101](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_1.js)]  
  
 Poniższy fragment kodu przedstawia metodę C++:  
  
 [!code-cpp[cx_arrays#01](../cppcx/codesnippet/CPP/js-array/class1.cpp#01)]  
  
## <a name="receivearray-pattern"></a>Wzorzec ReceiveArray  
 We wzorcu ReceiveArray kod klienta deklaruje tablicę i przekazuje je do metody, która przydziela pamięć i inicjuje go. Typ parametru wejściowego C++ jest jest wskaźnik do hat: `Array<T>^*`. Poniższy przykład pokazuje, jak można zadeklarować tablicy obiektów w języku JavaScript i przekaż go do funkcji języka C++, która przydziela pamięć, inicjuje elementy i zwraca go do języka JavaScript. JavaScript traktuje przydzielone tablicy jako wartości zwracane, ale funkcja C++ traktuje ją jako parametr wyjściowy.  
  
 [!code-javascript[cx_arrays#102](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_3.js)]  
  
 Poniższy fragment kodu przedstawia dwa sposoby zaimplementuj metodę C++:  
  
 [!code-cpp[cx_arrays#02](../cppcx/codesnippet/CPP/js-array/class1.cpp#02)]  
  
## <a name="fill-arrays"></a>Wypełnij tablic  
 Aby przydzielić tablicy w element wywołujący i zainicjować ani modyfikować w elementu wywoływanego wykorzystania `WriteOnlyArray`. W kolejnym przykładzie pokazano implementowania funkcji języka C++, która używa `WriteOnlyArray` i wywołać go z poziomu języka JavaScript.  
  
 [!code-javascript[cx_arrays#103](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_5.js)]  
  
 Poniższy fragment kodu przedstawia sposób implementować metodę C++:  
  
 [!code-cpp[cx_arrays#03](../cppcx/codesnippet/CPP/js-array/class1.cpp#03)]  
  
## <a name="array-conversions"></a>Konwersje tablic  
 Ten przykład przedstawia sposób użycia [Platform::Array](../cppcx/platform-array-class.md) do skonstruowania inne rodzaje kolekcji:  
  
 [!code-cpp[cx_arrays#05](../cppcx/codesnippet/CPP/js-array/class1.cpp#05)]  
  
 W kolejnym przykładzie pokazano sposób tworzenia [Platform::Array](../cppcx/platform-array-class.md) w stylu języka C tablicy i zwracać ją publiczną metodę.  
  
 [!code-cpp[cx_arrays#06](../cppcx/codesnippet/CPP/js-array/class1.cpp#06)]  
  
## <a name="jagged-arrays"></a>Tablice nieregularne  
 System typów środowiska wykonawczego systemu Windows nie obsługuje pojęcia Tablice nieregularne i dlatego nie można używać `IVector<Platform::Array<T>>` jako parametru wartość lub metody zwracany w publicznej metody. Aby przekazać tablicy nieregularnej lub sekwencję sekwencji między interfejsem ABI, należy użyć `IVector<IVector<T>^>`.  
  
## <a name="use-arrayreference-to-avoid-copying-data"></a>Użyj ArrayReference, aby uniknąć kopiowanie danych  
 W niektórych scenariuszach, w którym dane są przekazywane między ABI do [Platform::Array](../cppcx/platform-array-class.md)i chcesz ostatecznie przetwarzania danych w stylu języka C tablicy w celu zwiększenia wydajności, można użyć [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) Aby uniknąć dodatkowych kopii. Podczas przekazywania [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) jako argument do parametru, który przyjmuje `Platform::Array`, `ArrayReference` będą przechowywane dane bezpośrednio do tablicy stylu języka C, który określisz. Tylko należy pamiętać, że `ArrayReference` ma blokady do źródła danych, więc jeśli zmodyfikowanie lub usunąć w innym wątku przed zakończeniem połączenia danych, wyniki będzie niezdefiniowany.  
  
 Poniższy fragment kodu przedstawia sposób skopiować wyniki [DataReader](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.datareader.aspx) operacji do `Platform::Array` (zwykle wzorzec), a następnie, jak zastąpić `ArrayReference` Aby skopiować dane bezpośrednio do tablicy stylu języka C:  
  
 [!code-cpp[cx_arrays#07](../cppcx/codesnippet/CPP/js-array/class1.h#07)]  
  
## <a name="avoid-exposing-an-array-as-a-property"></a>Unikaj udostępnianie tablicy jako właściwość  
 Ogólnie rzecz biorąc, należy unikać udostępnianie `Platform::Array` typu jako właściwość w klasie ref, ponieważ cała tablica jest zwracany, nawet wtedy, gdy kod klienta tylko próbuje uzyskać dostęp pojedynczy element. Gdy chcesz uwidocznić kontenera sekwencji jako właściwości w klasie ref publicznego [Windows::Foundation::IVector](http://msdn.microsoft.com/library/windows/apps/br206631.aspx) jest lepszym rozwiązaniem. Prywatny lub wewnętrzny interfejsów API (które nie są publikowane w metadanych), należy wziąć pod uwagę przy użyciu standardowych kontener C++, takich jak [std::vector](../standard-library/vector-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [System typów](../cppcx/type-system-c-cx.md)   
 [Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)