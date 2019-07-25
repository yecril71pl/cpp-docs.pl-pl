---
title: ctype_byname — Klasa
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::ctype_byname
helpviewer_keywords:
- ctype_byname class
ms.assetid: a5cec021-a1f8-425f-8757-08e6f064b604
ms.openlocfilehash: 0b0f33781cc9f1f54661a44a5434c94316432a45
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457894"
---
# <a name="ctypebyname-class"></a>ctype_byname — Klasa

Klasa pochodna szablonu opisuje obiekt, który może być używany jako zestaw reguł CType dla danego ustawienia regionalnego, co umożliwia klasyfikację znaków i konwersję znaków między zestawami znaków w przypadku i natywnym.

## <a name="syntax"></a>Składnia

```cpp
template <class _Elem>
class ctype_byname : public ctype<_Elem>
{
public:
    explicit ctype_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit ctype_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual __CLR_OR_THIS_CALL ~ctype_byname();

};
```

## <a name="remarks"></a>Uwagi

Jego zachowanie zależy od nazwanych ustawień regionalnych `_Locname`. Każdy Konstruktor inicjuje swój obiekt podstawowy z [CType](../standard-library/ctype-class.md)\<CharType > ( `_Refs`) lub odpowiednikiem klasy `ctype<char>`bazowej.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ustawień regionalnych

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
