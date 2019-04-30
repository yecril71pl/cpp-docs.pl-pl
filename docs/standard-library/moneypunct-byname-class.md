---
title: moneypunct_byname — Klasa
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::moneypunct_byname
helpviewer_keywords:
- moneypunct_byname class
ms.assetid: e8a544d2-6aee-420d-b513-deb385c9b416
ms.openlocfilehash: 003ba2136e779c444c7edad9b1759a861a8b0803
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383558"
---
# <a name="moneypunctbyname-class"></a>moneypunct_byname — Klasa

Klasa pochodna szablonu opisująca obiekt, który może służyć jako `moneypunct` aspekt danych ustawień regionalnych, umożliwiając formatowanie pieniężnych danych wejściowych, pole lub pola pieniężnych danych wyjściowych.

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

Jego zachowanie jest określana przez nazwany ustawień regionalnych `_Locname`. Każdy Konstruktor inicjuje jego podstawowego obiektu z [moneypunct](../standard-library/moneypunct-class.md#moneypunct)\<CharType, Intl > ( `_Refs`).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
