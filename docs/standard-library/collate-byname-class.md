---
title: collate_byname — Klasa
ms.date: 11/04/2016
f1_keywords:
- locale/std::collate_byname
helpviewer_keywords:
- collate_byname class
ms.assetid: 3dc380df-867c-4763-b60e-ba62a8e63ca7
ms.openlocfilehash: b8ed428da05e706796a981b8ca9d601033156c6f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458624"
---
# <a name="collatebyname-class"></a>collate_byname — Klasa

Klasa pochodna szablonu opisująca obiekt, który może służyć jako zestaw reguł sortowania danych ustawień regionalnych, umożliwiając pobieranie informacji specyficznych dla obszaru kulturowego dotyczących konwencji sortowania ciągów.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType>
class collate_byname : public collate<CharType> {
public:
    explicit collate_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit collate_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~collate_byname();

};
```

### <a name="parameters"></a>Parametry

*_Locname*\
Nazwane ustawienia regionalne.

*_Refs*\
Początkowa liczba odwołań.

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje obiekt, który może obsłużyć jako zestaw [reguł ustawień regionalnych](../standard-library/locale-class.md#facet_class) typu [Sortuj](../standard-library/collate-class.md#collate)\<CharType >. Jego zachowanie zależy od nazwanych [](../standard-library/locale-class.md#name) ustawień regionalnych *_Locname*. Każdy Konstruktor inicjuje swój obiekt podstawowy z [sortowaniem](../standard-library/collate-class.md#collate)\<CharType > `_Refs`().

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ustawień regionalnych

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
