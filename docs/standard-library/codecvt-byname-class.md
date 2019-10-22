---
title: codecvt_byname — Klasa
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::codecvt_byname
helpviewer_keywords:
- codecvt_byname class
ms.assetid: b63b6c04-f60c-47b9-8e30-a933f24a8ffb
ms.openlocfilehash: b48f01126eba7082230fc5e19150d42d1dfad2f3
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688294"
---
# <a name="codecvt_byname-class"></a>codecvt_byname — Klasa

Szablon klasy pochodnej, który opisuje obiekt, który może być używany jako zestaw reguł sortowania danych ustawień regionalnych, umożliwiając pobieranie informacji specyficznych dla obszaru kulturowego dotyczące konwersji.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType, class Byte, class StateType>
class codecvt_byname: public codecvt<CharType, Byte, StateType> {
public:
    explicit codecvt_byname(
    const char* _Locname,
    size_t _Refs = 0);
```

```cpp
explicit codecvt_byname(
    const string& _Locname,
    size_t _Refs = 0);
```

```cpp
protected:
    virtual ~codecvt_byname();

};
```

### <a name="parameters"></a>Parametry

*_Locname* \
Nazwane ustawienia regionalne.

*_Refs* \
Początkowa liczba odwołań.

## <a name="remarks"></a>Uwagi

Zestawy reguł byname są tworzone automatycznie podczas konstruowania nazwanych ustawień regionalnych.

Jego zachowanie zależy od nazwanych ustawień regionalnych *_Locname*. Każdy Konstruktor inicjuje swój obiekt podstawowy z [codecvt](../standard-library/codecvt-class.md) \<CharType, Byte, statetype > (`_Refs`).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<locale >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
