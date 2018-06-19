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
ms.openlocfilehash: 49a77234b679fd61d801bb78d751891467d6b4e0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412078"
---
# <a name="containers-modern-c"></a>Kontenery (Modern C++)

Domyślnie używają [wektor](../standard-library/vector-class.md) jako preferowany sekwencyjnych kontenera w języku C++. Jest to równoważne `List<T>` w językach .NET.

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

Użyj [mapy](../standard-library/map-class.md) (nie `unordered_map`) jako domyślny kontener asocjacyjnej. Użyj [ustawić](../standard-library/set-class.md), [multimap](../standard-library/multimap-class.md), i [multiset](../standard-library/multiset-class.md) wymiar degeneracji & w wielu przypadkach.

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

W razie potrzeby optymalizacji wydajności wziąć pod uwagę:

- [Tablicy](../standard-library/array-class-stl.md) wpisz podczas osadzania jest ważne, na przykład jako element członkowski klasy.

- Nieuporządkowane asocjacyjnej kontenerów, takich jak [unordered_map](../standard-library/unordered-map-class.md). Mają one element niższe obciążenie i stała czas wyszukiwania, ale może być trudniejsza umożliwia prawidłowe i efektywne.

- Sortowane **wektor**. Aby uzyskać więcej informacji, zobacz [algorytmy](../cpp/algorithms-modern-cpp.md).

Nie używaj tablic w stylu języka C. Dla starszych interfejsów API, które wymagają bezpośredni dostęp do danych, użyj metody dostępu takiego jak `f(vec.data(), vec.size());` zamiast tego.

Aby uzyskać więcej informacji na temat kontenerów, zobacz [standardowe kontenery biblioteki C++](../standard-library/stl-containers.md).

## <a name="see-also"></a>Zobacz także

[Zapraszamy ponownie do języka C++](../cpp/welcome-back-to-cpp-modern-cpp.md)  
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)  
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)  
