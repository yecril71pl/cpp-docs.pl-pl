---
title: messages_byname — Klasa
ms.date: 11/04/2016
f1_keywords:
- xlocmes/std::messages_byname
helpviewer_keywords:
- messages_byname class
ms.assetid: c6c64841-3e80-43c8-b54c-fed41833ad6b
ms.openlocfilehash: 56d8931cb404d9c0f3f5113f8b2ca0f1158209f2
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689331"
---
# <a name="messages_byname-class"></a>messages_byname — Klasa

Szablon klasy pochodnej opisuje obiekt, który może stanowić zestaw aspektów komunikatów dla danego ustawienia regionalnego, umożliwiając pobieranie zlokalizowanych komunikatów.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType>
class messages_byname : public messages<CharType> {
public:
    explicit messages_byname(
    const char *_Locname,
    size_t _Refs = 0);

    explicit messages_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~messages_byname();

};
```

### <a name="parameters"></a>Parametry

*_Locname* \
Nazwane ustawienia regionalne.

*_Refs* \
Początkowa liczba odwołań.

## <a name="remarks"></a>Uwagi

Jego zachowanie zależy od nazwanych ustawień regionalnych *_Locname*. Każdy Konstruktor inicjuje swój obiekt podstawowy z [komunikatami](../standard-library/messages-class.md#messages) \<CharType > (`_Refs`).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<locale >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
