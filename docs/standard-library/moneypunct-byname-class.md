---
title: moneypunct_byname — Klasa
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::moneypunct_byname
helpviewer_keywords:
- moneypunct_byname class
ms.assetid: e8a544d2-6aee-420d-b513-deb385c9b416
ms.openlocfilehash: 47c9d2281973cb57288bfdcf865926fb6dd9ed0e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460213"
---
# <a name="moneypunctbyname-class"></a>moneypunct_byname — Klasa

Klasa pochodna szablonu opisująca obiekt, który może być używany jako `moneypunct` zestaw reguł dla danego ustawienia regionalnego, umożliwiając formatowanie pola wejściowego pieniężnego lub pola walutowych danych wyjściowych.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType, bool Intl = false>
class moneypunct_byname : public moneypunct<CharType, Intl>
{
public:
    explicit moneypunct_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit moneypunct_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~moneypunct_byname();

};
```

## <a name="remarks"></a>Uwagi

Jego zachowanie zależy od nazwanych ustawień regionalnych `_Locname`. Każdy Konstruktor inicjuje swój obiekt podstawowy z [moneypunct](../standard-library/moneypunct-class.md#moneypunct)\<CharType, Intl > ( `_Refs`).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ustawień regionalnych

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
