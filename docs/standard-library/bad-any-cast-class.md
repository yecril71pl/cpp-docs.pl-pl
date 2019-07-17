---
title: bad_any_cast klasy
ms.date: 04/04/2019
f1_keywords:
- any/std::bad_any_cast
- any/std::bad_any_cast::what
helpviewer_keywords:
- any/std::bad_any_cast
- any/std::bad_any_cast::what
ms.openlocfilehash: 5172281d1918a8b4ac33bcf412bf4be82b04ef56
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68267959"
---
# <a name="badanycast-class"></a>bad_any_cast klasy

Obiekty zgłoszony, który uległ awarii `any_cast`.

## <a name="syntax"></a>Składnia

```cpp
class bad_any_cast
```

### <a name="member-functions"></a>Funkcje Członkowskie

|||
|-|-|
|[Co to](#what)|Zwraca typ.|

## <a name="what"></a> Co to

Zwraca typ.

```cpp
const char* what() const noexcept override;
```
