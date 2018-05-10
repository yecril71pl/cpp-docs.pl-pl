---
title: ctype_byname — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocale/std::ctype_byname
dev_langs:
- C++
helpviewer_keywords:
- ctype_byname class
ms.assetid: a5cec021-a1f8-425f-8757-08e6f064b604
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a7ebfb2d5bc4543665054208e37e1f993270e5f3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="ctypebyname-class"></a>ctype_byname — Klasa

Klasy pochodne szablonu opisano obiekt, który może służyć jako zestaw reguł ctype danego ustawień regionalnych, włączenie klasyfikacji znaków i konwersja znaków między przypadku i natywnego oraz ustawień regionalnych określonych zestawów znaków.

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

Jego zachowanie jest określany przez nazwany ustawień regionalnych `_Locname`. Każdy Konstruktor inicjuje jego obiektu podstawowego z [ctype](../standard-library/ctype-class.md)\<CharType > ( `_Refs`) lub jej odpowiedniku dla klasy podstawowej `ctype<char>`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
