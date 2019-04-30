---
title: Kontenery (Modern C++)
ms.date: 1/18/2018
ms.topic: conceptual
ms.openlocfilehash: 2da57bfca8b04f50a223dddfb886835c69f746a4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392339"
---
# <a name="containers-modern-c"></a>Kontenery (Modern C++)

Domyślnie używają [wektor](../standard-library/vector-class.md) jako preferowany kontenera sekwencyjnego w języku C++. Jest to równoważne `List<T>` w językach .NET.

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

Użyj [mapy](../standard-library/map-class.md) (nie `unordered_map`) jako domyślnego kontenera zespolonego. Użyj [ustaw](../standard-library/set-class.md), [multimap](../standard-library/multimap-class.md), i [multiset](../standard-library/multiset-class.md) wymiar degeneracji & wielu przypadków.

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

Gdy potrzebna jest Optymalizacja wydajności, należy wziąć pod uwagę przy użyciu:

- [Tablicy](../standard-library/array-class-stl.md) wpisz podczas osadzania jest ważna, na przykład, jako członek klasy.

- Takie jak nieuporządkowane kontenery asocjacyjne [unordered_map](../standard-library/unordered-map-class.md). Mają one element niższe obciążenie i wyszukiwanie w czasie stałym, ale może być trudniejsze do użytku prawidłowo i efektywnie.

- Sortowane `vector`. Aby uzyskać więcej informacji, zobacz [algorytmy](../cpp/algorithms-modern-cpp.md).

Nie używaj tablice stylu C. Dla starszych interfejsów API, które muszą bezpośredni dostęp do danych, użyj metody dostępu takich jak `f(vec.data(), vec.size());` zamiast tego.

Aby uzyskać więcej informacji na temat kontenerów, zobacz [standardowych kontenerów biblioteki języka C++](../standard-library/stl-containers.md).

## <a name="see-also"></a>Zobacz także

[Witaj z powrotem w języku C++ (Modern C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)
