---
title: ctype_byname — Klasa
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::ctype_byname
helpviewer_keywords:
- ctype_byname class
ms.assetid: a5cec021-a1f8-425f-8757-08e6f064b604
ms.openlocfilehash: dcaaff45fb33155710f788af4ceb657eff97464e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689735"
---
# <a name="ctype_byname-class"></a>ctype_byname — Klasa

Szablon klasy pochodnej opisuje obiekt, który może być używany jako zestaw reguł CType dla danego ustawienia regionalnego, co umożliwia klasyfikację znaków i konwersję znaków między zestawami znaków w przypadku i natywnym i lokalnym.

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

Jego zachowanie zależy od nazwanych ustawień regionalnych `_Locname`. Każdy Konstruktor inicjuje swój obiekt podstawowy z [ctype](../standard-library/ctype-class.md) \<CharType > (`_Refs`) lub odpowiednikiem klasy bazowej `ctype<char>`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<locale >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
