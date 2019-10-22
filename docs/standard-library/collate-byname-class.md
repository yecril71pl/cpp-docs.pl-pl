---
title: collate_byname — Klasa
ms.date: 11/04/2016
f1_keywords:
- locale/std::collate_byname
helpviewer_keywords:
- collate_byname class
ms.assetid: 3dc380df-867c-4763-b60e-ba62a8e63ca7
ms.openlocfilehash: 3e9a256ac7bdb5f6d077746fe2a08990ed41e931
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688271"
---
# <a name="collate_byname-class"></a>collate_byname — Klasa

Szablon klasy pochodnej, który opisuje obiekt, który może być używany jako zestaw reguł sortowania dla danego ustawienia regionalnego, umożliwiając pobieranie informacji specyficznych dla obszaru kulturowego dotyczących Konwencji sortowania ciągów.

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

*_Locname* \
Nazwane ustawienia regionalne.

*_Refs* \
Początkowa liczba odwołań.

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje obiekt, który może obsłużyć jako zestaw [reguł ustawień regionalnych](../standard-library/locale-class.md#facet_class) typu [COLLATE](../standard-library/collate-class.md#collate) \<CharType >. Jego zachowanie zależy od nazwanych [o nazwie
](../standard-library/locale-class.md#name) ustawień regionalnych *_Locname*. Każdy Konstruktor inicjuje swój obiekt podstawowy z [sortowaniem](../standard-library/collate-class.md#collate) \<CharType > (`_Refs`).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<locale >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
