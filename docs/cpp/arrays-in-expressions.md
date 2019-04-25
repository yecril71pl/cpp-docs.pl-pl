---
title: Tablice w wyrażeniach
ms.date: 11/04/2016
helpviewer_keywords:
- expressions [C++], arrays in
- arrays [C++], in expressions
ms.assetid: 6e5a795b-d6bd-4e39-b313-6a20d47c4d4b
ms.openlocfilehash: 0f2ef43c2a5bc4f8a44378c21d6d53b14f07ea07
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62184383"
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