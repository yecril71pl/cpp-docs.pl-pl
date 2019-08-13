---
title: Klasa bad_optional_access
ms.date: 08/06/2019
f1_keywords:
- optional/std::bad_optional_access
ms.openlocfilehash: 043b0360c7e0be48267c8f406dbfea50eeb5a8e3
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957098"
---
# <a name="bad_optional_access-class"></a>Klasa bad_optional_access

Definiuje typ obiektów zgłoszonych jako wyjątki, aby zgłosić sytuację, w której podjęto próbę uzyskania dostępu do wartości `optional` obiektu, który nie zawiera wartości.

## <a name="syntax"></a>Składnia

```cpp
class bad_optional_access : public exception
{
public:
    bad_optional_access() noexcept;
    bad_optional_access(const bad_optional_access&) noexcept;
    bad_optional_access& operator=(const bad_optional_access&) noexcept;
    const char* what() const noexcept override;
};
```

## <a name="see-also"></a>Zobacz także

[\<> opcjonalne](optional.md)\
[Klasa opcjonalna](optional-class.md)
