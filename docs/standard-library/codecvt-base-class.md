---
title: codecvt_base — Klasa
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::codecvt_base
helpviewer_keywords:
- codecvt_base class
ms.assetid: 7e95c083-91b4-4b3f-8918-0d4ea244a040
ms.openlocfilehash: 6fca9b2130407b165a7a7bfb1fb2a9ec81774e20
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689893"
---
# <a name="codecvt_base-class"></a>codecvt_base — Klasa

Klasa bazowa dla klasy codecvt, która jest używana do definiowania typu wyliczenia, określanego jako `result`, używanego jako zwracany typ dla funkcji składowych aspektu, aby wskazać wynik konwersji.

## <a name="syntax"></a>Składnia

```cpp
class codecvt_base : public locale::facet {
public:
    enum result {ok, partial, error, noconv};
    codecvt_base( size_t _Refs = 0);
    bool always_noconv() const;
    int max_length() const;
    int encoding() const;
    ~codecvt_base()

protected:
    virtual bool do_always_noconv() const;
    virtual int do_max_length() const;
    virtual int do_encoding() const;
};
```

## <a name="remarks"></a>Uwagi

Klasa opisuje Wyliczenie wspólne dla wszystkich specjalizacji szablonu klasy [codecvt](../standard-library/codecvt-class.md). Wynik wyliczenia zawiera opis możliwych wartości zwracanych z [do_in](../standard-library/codecvt-class.md#do_in) lub [do_out](../standard-library/codecvt-class.md#do_out):

- `ok`, jeśli konwersja między wewnętrznymi i zewnętrznymi kodowaniem znaków zostanie zakończona pomyślnie.

- `partial`, jeśli miejsce docelowe nie jest wystarczająco duże, aby konwersja powiodła się.

- `error`, jeśli sekwencja źródłowa jest źle sformułowana.

- `noconv`, jeśli funkcja nie wykonuje konwersji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<locale >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
