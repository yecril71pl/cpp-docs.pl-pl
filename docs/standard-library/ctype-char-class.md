---
title: CType&lt;char&gt; klasy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- ctype<char>
- locale/std::ctype<char>
dev_langs:
- C++
helpviewer_keywords:
- ctype<char> class
ms.assetid: ee30acb4-a743-405e-b3d4-13602092da84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5293c01428f16b1be6901c970b9af470ef8ed1da
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083337"
---
# <a name="ctypeltchargt-class"></a>CType&lt;char&gt; klasy

Klasa jest jawną specjalizacją klasy szablonu `ctype\<CharType>` na typ **char**, opisująca obiekt, który może służyć jako zestaw reguł ustawień regionalnych w celu scharakteryzowania różnych właściwości znaku typu **char**.

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

Jawna specjalizacja różni się od klasy szablonu, na kilka sposobów:

- Obiekt klasy ctype < `char`> przechowuje wskaźnik do pierwszego elementu w tabeli Maska ctype, tablicę UCHAR_MAX + 1 elementów typu `ctype_base::mask`. Przechowuje obiekt Boolean wskazującą, czy można usunąć tablicy (przy użyciu `operator delete[]`) podczas ctype\< **Elem**> niszczony jest obiekt.

- Jej jedyny Konstruktor publiczny umożliwia określenie `tab`, tabeli Maska ctype i `del`, logiczna obiekt, który ma wartość true, jeśli tablica ma być usuwane, gdy ctype < `char`> obiekt jest niszczony, a także liczbę odwołań Parametr system plików refs.

- Chroniona funkcja elementu członkowskiego `table` zwraca tabelę maski ctype przechowywanych.

- Obiekt statyczny element członkowski `table_size` określa minimalną liczbę elementów w tabeli Maska ctype.

- Funkcja chronionego członka statycznego `classic_table`(funkcja zwraca tabelę maski ctype odpowiednie dla ustawień regionalnych "C".

- Brak funkcji chronionych składowych wirtualnych nie [do_is —](../standard-library/ctype-class.md#do_is), [do_scan_is —](../standard-library/ctype-class.md#do_scan_is), lub [do_scan_not —](../standard-library/ctype-class.md#do_scan_not). Z odpowiednimi funkcjami publicznego elementu członkowskiego wykonywać operacje równoważne, samodzielnie.

Funkcje elementów członkowskich [do_narrow —](../standard-library/ctype-class.md#do_narrow) i [do_widen —](../standard-library/ctype-class.md#do_widen) kopiowanie elementów niezmieniony.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[facet — klasa](locale-class.md#facet_class)<br/>
[ctype_base, klasa](../standard-library/ctype-base-class.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
