---
title: Klasa bad_array_new_length
ms.date: 11/04/2016
f1_keywords:
- new/std::bad_array_new_length
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
ms.openlocfilehash: c4f4f58f7b28960bbacf695a675fbe4f20a54192
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443705"
---
# <a name="bad_array_new_length-class"></a>Klasa bad_array_new_length

Klasa zawiera opis zgłoszonego wyjątku, aby wskazać, że żądanie alokacji nie zakończyło się niepowodzeniem z powodu rozmiaru tablicy mniejszego niż zero lub większego od jego limitu.

## <a name="syntax"></a>Składnia

```cpp
class bad_array_new_length : public bad_alloc {
    public: bad_array_new_length() noexcept;
    const char* what() const noexcept override;
};
```

## <a name="remarks"></a>Uwagi

Wartość zwracana przez `what` jest ciągiem w języku C zdefiniowanym przez implementację. Żadna z funkcji Członkowskich nie zgłasza żadnych wyjątków.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<nowe >

## <a name="see-also"></a>Zobacz też

\ [klasy wyjątku](../standard-library/exception-class.md)
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
