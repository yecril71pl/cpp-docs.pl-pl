---
title: nullopt_t, struktura
ms.date: 08/04/2019
f1_keywords:
- optional/std::nullopt_t
- optional/std::nullopt
ms.openlocfilehash: 1f453a5d75de3f6dedb133d55c094a4f4274e08f
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957042"
---
# <a name="nullopt_t-struct"></a>nullopt_t, struktura

Typ jest unikatowym, pustym typem używanym do wskazania, że obiekt opcjonalny nie zawiera wartości. [](optional-class.md) `nullopt_t`

Stała `nullopt` typu `nullopt_t` wskazuje ,żetypmaniezainicjowanystan.`optional` Może służyć do inicjowania `optional` obiektu lub porównywania z jednym.

## <a name="syntax"></a>Składnia

```cpp
struct nullopt_t;
inline constexpr nullopt_t nullopt{ /*implementation-defined*/ };
```

## <a name="see-also"></a>Zobacz także

[\<> opcjonalne](optional.md)\
[Klasa opcjonalna](optional-class.md)
