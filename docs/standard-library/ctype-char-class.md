---
title: ctype &lt; char — &gt; Klasa
ms.date: 11/04/2016
f1_keywords:
- ctype<char>
- locale/std::ctype<char>
helpviewer_keywords:
- ctype<char> class
ms.assetid: ee30acb4-a743-405e-b3d4-13602092da84
ms.openlocfilehash: d2c74ef46babe388cfa6d649e8b4501b7c235bb9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220967"
---
# <a name="ctypeltchargt-class"></a>ctype &lt; char — &gt; Klasa

Klasa jest jawną specjalizacją szablonu klasy `ctype\<CharType>` do wpisywania **`char`** opisującą obiekt, który może stanowić zestaw reguł ustawień regionalnych w celu scharakteryzowania różnych właściwości znaku typu **`char`** .

## <a name="syntax"></a>Składnia

```cpp
template <>
class ctype<char>
: public ctype_base
{
public:
    typedef char _Elem;
    typedef _Elem char_type;
    bool is(
    mask _Maskval,
    _Elem _Ch) const;

    const _Elem* is(
    const _Elem* first,
    const _Elem* last,
    mask* dest) const;

    const _Elem* scan_is(
    mask _Maskval,
    const _Elem* first,
    const _Elem* last) const;

    const _Elem* scan_not(
    mask _Maskval,
    const _Elem* first,
    const _Elem* last) const;

    _Elem tolower(
    _Elem _Ch) const;

    const _Elem* tolower(
    _Elem* first,
    const _Elem* last) const;

    _Elem toupper(
    _Elem _Ch) const;

    const _Elem* toupper(
    _Elem* first,
    const _Elem* last) const;

    _Elem widen(
    char _Byte) const;

    const _Elem* widen(
    const char* first,
    const char* last,
    _Elem* dest) const;

    const _Elem* _Widen_s(
    const char* first,
    const char* last,
    _Elem* dest,
    size_t dest_size) const;

    _Elem narrow(
    _Elem _Ch,
    char _Dflt = '\0') const;

    const _Elem* narrow(
    const _Elem* first,
    const _Elem* last,
    char _Dflt,
    char* dest) const;

    const _Elem* _Narrow_s(
    const _Elem* first,
    const _Elem* last,
    char _Dflt,
    char* dest,
    size_t dest_size) const;

    static locale::id& id;
    explicit ctype(
    const mask* _Table = 0,
    bool _Deletetable = false,
    size_t _Refs = 0);

protected:
    virtual ~ctype();
//other protected members
};
```

## <a name="remarks"></a>Uwagi

Jawna specjalizacja różni się od szablonu klasy na kilka sposobów:

- Obiekt klasy `ctype<char>` przechowuje wskaźnik do pierwszego elementu tabeli maski CType, tablicę elementów typu UCHAR_MAX + 1 `ctype_base::mask` . Przechowuje również obiekt logiczny, który wskazuje, czy tablica powinna zostać usunięta (przy użyciu `operator delete[]` ), gdy \< **Elem**> obiekt CType zostanie zniszczony.

- Jego jedyny Konstruktor publiczny pozwala określić `tab` , tabelę masek CType i `del` , obiekt logiczny, który ma wartość true, jeśli tablica powinna zostać usunięta `ctype<char>` , gdy obiekt jest niszczony, a także odwołań do parametrów liczby odwołań.

- Funkcja chronionego elementu członkowskiego `table` zwraca przechowywaną tabelę masek CType.

- Statyczny Obiekt członkowski `table_size` określa minimalną liczbę elementów w tabeli maski CType.

- Chroniona funkcja statyczna elementu członkowskiego `classic_table` (zwraca tabelę maski CType odpowiednią dla ustawień regionalnych "C".

- Brak chronionych wirtualnych funkcji Członkowskich [do_is](../standard-library/ctype-class.md#do_is), [do_scan_is](../standard-library/ctype-class.md#do_scan_is)lub [do_scan_not](../standard-library/ctype-class.md#do_scan_not). Odpowiednie publiczne funkcje Członkowskie wykonują równoważne operacje.

Funkcje składowe [do_narrow](../standard-library/ctype-class.md#do_narrow) i [do_widen](../standard-library/ctype-class.md#do_widen) kopiowania elementów bez zmian.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<locale>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[facet — Klasa](locale-class.md#facet_class)\
[Klasa ctype_base](../standard-library/ctype-base-class.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
