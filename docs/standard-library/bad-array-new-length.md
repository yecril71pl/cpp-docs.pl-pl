---
title: Klasa bad_array_new_length
ms.date: 11/04/2016
f1_keywords:
- new/std::bad_alloc
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
ms.openlocfilehash: b00042513364ac04b62ac7e1943d912dcb78f212
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459488"
---
# <a name="badarraynewlength-class"></a>Klasa bad_array_new_length

Klasa zawiera opis zgłoszonego wyjątku, aby wskazać, że żądanie alokacji nie zakończyło się niepowodzeniem z powodu rozmiaru tablicy mniejszego niż zero lub większego od jego limitu.

## <a name="syntax"></a>Składnia

```cpp
class bad_array_new_length : public bad_alloc {
    public: bad_array_new_length() noexcept;
    const char* what() const noexcept override;
};
```

## <a name="remarks"></a>Uwagi

Wartość zwrócona przez `what` to ciąg języka C zdefiniowany przez implementację. Żadna z funkcji Członkowskich nie zgłasza żadnych wyjątków.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<nowe >

## <a name="see-also"></a>Zobacz także

[Klasa wyjątku](../standard-library/exception-class.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
