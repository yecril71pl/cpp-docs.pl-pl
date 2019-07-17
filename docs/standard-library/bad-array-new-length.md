---
title: bad_array_new_length klasy
ms.date: 11/04/2016
f1_keywords:
- new/std::bad_alloc
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
ms.openlocfilehash: 823da1555119735e9aa1c46aa4db2e3a47affdec
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68267962"
---
# <a name="badarraynewlength-class"></a>bad_array_new_length klasy

Klasa opisuje wyjątek generowany w celu wskazania, że żądanie alokacji nie powiodła się ze względu na rozmiar tablicy, mniejsze od zera lub większa niż limit.

## <a name="syntax"></a>Składnia

```cpp
class bad_array_new_length : public bad_alloc {
    public: bad_array_new_length() noexcept;
    const char* what() const noexcept override;
};
```

## <a name="remarks"></a>Uwagi

Wartość zwrócona przez obiekt `what` jest ciągiem C zdefiniowanych w implementacji. Żadna z funkcji elementu członkowskiego generuje żadnych wyjątków.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<nowe >

## <a name="see-also"></a>Zobacz także

[exception, klasa](../standard-library/exception-class.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
