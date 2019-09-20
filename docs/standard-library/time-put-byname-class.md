---
title: time_put_byname — Klasa
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_put_byname
helpviewer_keywords:
- time_put_byname class
ms.assetid: e08c2348-64d2-4ace-98b1-1496e14c7b1a
ms.openlocfilehash: 2da2bf4ea1c709b820c1a82dc20e288634139a83
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460001"
---
# <a name="time_put_byname-class"></a>time_put_byname — Klasa

Klasa pochodna szablonu opisuje obiekt, który może być używany jako zestaw reguł ustawień regionalnych `time_put` typu \< CharType, OutputIterator >.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType, class OutIt = ostreambuf_iterator<CharType, char_traits<CharType>>>
class time_put_byname : public time_put<CharType, OutputIterator>
{
public:
    explicit time_put_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit time_put_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~time_put_byname();

};
```

### <a name="parameters"></a>Parametry

*_Locname*\
Nazwa ustawień regionalnych.

*_Refs*\
Początkowa liczba odwołań.

## <a name="remarks"></a>Uwagi

Jego zachowanie zależy od nazwanych [o nazwie
](../standard-library/locale-class.md#name) ustawień regionalnych *_Locname*. Każdy Konstruktor inicjuje swój obiekt podstawowy z [time_put](../standard-library/time-put-class.md#time_put)\<CharType, OutputIterator > (`_Refs`).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ustawień regionalnych

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
