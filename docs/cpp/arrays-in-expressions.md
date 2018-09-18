---
title: Tablice w wyrażeniach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expressions [C++], arrays in
- arrays [C++], in expressions
ms.assetid: 6e5a795b-d6bd-4e39-b313-6a20d47c4d4b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34f8a45dfa9de9a5a48e13cb6a38f667e5963f2d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068549"
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