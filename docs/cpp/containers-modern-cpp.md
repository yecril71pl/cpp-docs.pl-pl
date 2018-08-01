---
title: Kontenery (Modern C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 1/18/2018
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d740bb36c1d574e474058c05d900d605c71e55f0
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406337"
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
 [Witamy z powrotem w C++](../cpp/welcome-back-to-cpp-modern-cpp.md)  
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)  
 [Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)  