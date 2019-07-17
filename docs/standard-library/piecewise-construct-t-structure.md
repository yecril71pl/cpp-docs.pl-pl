---
title: piecewise_contruct_t struktury
ms.date: 11/04/2016
f1_keywords:
- utility/std::piecewise_contruct_t
helpviewer_keywords:
- piecewise_contruct_t class
- piecewise_contruct_t structure
ms.openlocfilehash: 6a9a6af97ca5c7751d64cd1fa70c9d9eba87da7c
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68267863"
---
# <a name="piecewisecontructt-structure"></a>piecewise_contruct_t struktury

Struktura `piecewise_construct_t` jest typem pustą strukturą używane, aby zachować oddzielne Konstruktor i przeciążenie funkcji. W szczególności `pair` ma konstruktora z `piecewise_construct_t` jako pierwszy argument, a następnie dwa `tuple` argumentów.

## <a name="syntax"></a>Składnia

```cpp
struct piecewise_construct_t { explicit piecewise_construct_t() = default; };

inline constexpr piecewise_construct_t piecewise_construct{};
```
