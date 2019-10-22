---
title: moneypunct_byname — Klasa
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::moneypunct_byname
helpviewer_keywords:
- moneypunct_byname class
ms.assetid: e8a544d2-6aee-420d-b513-deb385c9b416
ms.openlocfilehash: c687bc870e4d78cfe9174eb04ea09c34d6a9c955
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687657"
---
# <a name="moneypunct_byname-class"></a>moneypunct_byname — Klasa

Szablon klasy pochodnej, który opisuje obiekt, który może być `moneypunct` aspektem danego ustawienia regionalnego, umożliwiając formatowanie pola wejściowego pieniężnego lub pola walutowych danych wyjściowych.

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

Jego zachowanie zależy od nazwanych ustawień regionalnych `_Locname`. Każdy Konstruktor inicjuje swój obiekt podstawowy z [moneypunct](../standard-library/moneypunct-class.md#moneypunct) \<CharType, Intl > (`_Refs`).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<locale >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
