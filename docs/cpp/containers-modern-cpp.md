---
title: Kontenery (Modern C++)
ms.date: 01/18/2018
ms.topic: conceptual
ms.openlocfilehash: 37b540132fc9ddc03d5eaafd33c545b5db5e7935
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926257"
---
# <a name="containers-modern-c"></a>Kontenery (Modern C++)

Domyślnie użyj [wektora](../standard-library/vector-class.md) jako preferowanego kontenera sekwencyjnego w C++. Jest to odpowiednik `List<T>` w językach .NET.

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

Użyj [mapy](../standard-library/map-class.md) (nie `unordered_map`) jako domyślnego kontenera asocjacyjnego. Używaj [zestawu](../standard-library/set-class.md), [multimap](../standard-library/multimap-class.md)i [zestawów wielokrotnych](../standard-library/multiset-class.md) w celu wygenerowania wielu przypadków &.

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

W przypadku konieczności optymalizacji wydajności należy rozważyć użycie:

- Typ [tablicy](../standard-library/array-class-stl.md) podczas osadzania jest ważny, na przykład jako element członkowski klasy.

- Nieuporządkowane Kontenery asocjacyjne, takie jak [unordered_map](../standard-library/unordered-map-class.md). Są to mniejsze obciążenie poszczególnych elementów i wyszukiwanie w czasie stałym, ale mogą być trudniejsze do użycia poprawnie i wydajnie.

- Posortowane `vector`. Aby uzyskać więcej informacji, [](../cpp/algorithms-modern-cpp.md)Zobacz algorytmy.

Nie używaj tablic stylów języka C. W przypadku starszych interfejsów API, które wymagają bezpośredniego dostępu do danych, należy użyć metod `f(vec.data(), vec.size());` dostępu, takich jak zamiast.

Aby uzyskać więcej informacji na temat kontenerów, zobacz [ C++ Kontenery biblioteki standardowej](../standard-library/stl-containers.md).

## <a name="see-also"></a>Zobacz także

[Witaj z powrotem w języku C++ (Modern C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)
