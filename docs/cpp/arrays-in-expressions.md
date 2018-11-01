---
title: Tablice w wyrażeniach
ms.date: 11/04/2016
helpviewer_keywords:
- expressions [C++], arrays in
- arrays [C++], in expressions
ms.assetid: 6e5a795b-d6bd-4e39-b313-6a20d47c4d4b
ms.openlocfilehash: 0f2ef43c2a5bc4f8a44378c21d6d53b14f07ea07
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478172"
---
# <a name="arrays-in-expressions"></a>Tablice w wyrażeniach

Kiedy identyfikator typu tablicowego zostanie wyświetlony w wyrażeniu innych niż `sizeof`, adresu (**&**), lub inicjowania odwołania, jest konwertowany na wskaźnik do pierwszego elementu tablicy. Na przykład:

```cpp
char szError1[] = "Error: Disk drive not ready.";
char *psz = szError1;
```

Wskaźnik `psz` wskazuje na pierwszy element tablicy `szError1`. Należy pamiętać, że indeksy tablic, w przeciwieństwie do wskaźników, nie są modyfikowane przez l wartościami. W związku z tym następujące przypisanie jest niedozwolone:

```cpp
szError1 = psz;
```

## <a name="see-also"></a>Zobacz także

[Tablice](../cpp/arrays-cpp.md)