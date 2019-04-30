---
title: ctype_byname — Klasa
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::ctype_byname
helpviewer_keywords:
- ctype_byname class
ms.assetid: a5cec021-a1f8-425f-8757-08e6f064b604
ms.openlocfilehash: d998747045ece765269ddb013b525b8c06fcdf8b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394172"
---
# <a name="ctypebyname-class"></a>ctype_byname — Klasa

Klasa pochodna szablonu opisująca obiekt, który może służyć jako zestaw reguł ctype danych ustawień regionalnych, umożliwiając klasyfikację znaków i konwersję znaków między przypadek i natywnego i ustawienia regionalne określone zestawy znaków.

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

Jego zachowanie jest określana przez nazwany ustawień regionalnych `_Locname`. Każdy Konstruktor inicjuje jego podstawowego obiektu z [ctype](../standard-library/ctype-class.md)\<CharType > ( `_Refs`) lub odpowiednik dla klasy podstawowej `ctype<char>`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
