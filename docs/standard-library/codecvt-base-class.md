---
title: codecvt_base — Klasa
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::codecvt_base
helpviewer_keywords:
- codecvt_base class
ms.assetid: 7e95c083-91b4-4b3f-8918-0d4ea244a040
ms.openlocfilehash: 6f957c39f9c78fd182b7ba2a14bdab7f27db56ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405303"
---
# <a name="codecvtbase-class"></a>codecvt_base — Klasa

Klasa bazowa dla klasy codecvt, która służy do definiowania typu wyliczenia, określane jako `result`, który jest używany jako typ zwracany dla funkcji składowych zestawu reguł, aby wskazać wynik konwersji.

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

Klasa opisuje wyliczenie, które są wspólne dla wszystkich specjalizacje szablonu klasy [codecvt](../standard-library/codecvt-class.md). Wynik wyliczenia w tym artykule opisano możliwe wartości zwracane z [do_in](../standard-library/codecvt-class.md#do_in) lub [do_out](../standard-library/codecvt-class.md#do_out):

- `ok` Jeśli konwersja między kodowaniem znaków wewnętrznych i zewnętrznych zakończy się powodzeniem.

- `partial` Jeśli miejsce docelowe nie jest wystarczająco duży dla konwersja powiodła się.

- `error` Jeśli sekwencja źródłowa jest ill sformułowana.

- `noconv` Jeśli funkcja nie wykonuje żadnych konwersji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
