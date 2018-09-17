---
title: time_put_byname — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xloctime/std::time_put_byname
dev_langs:
- C++
helpviewer_keywords:
- time_put_byname class
ms.assetid: e08c2348-64d2-4ace-98b1-1496e14c7b1a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62d78fb7c2b9cbaee62baf59636303f90177cf7b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699598"
---
# <a name="timeputbyname-class"></a>time_put_byname — Klasa

Klasa pochodna szablonu opisująca obiekt, który może służyć jako zestaw reguł ustawień regionalnych typu `time_put` \< CharType, OutputIterator >.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType, class OutIt = ostreambuf_iterator<CharType, char_traits<CharType>>>
class time_put_byname : public time_put<CharType, OutputIterator>
{
public:
    explicit time_put_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit time_put_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~time_put_byname();

};
```

### <a name="parameters"></a>Parametry

*_Locname*<br/>
Nazwy ustawień regionalnych.

*_Refs*<br/>
Licznik odwołań początkowej.

## <a name="remarks"></a>Uwagi

Jego zachowanie jest określana przez [o nazwie](../standard-library/locale-class.md#name) ustawień regionalnych *_Locname*. Każdy Konstruktor inicjuje jego podstawowego obiektu z [time_put](../standard-library/time-put-class.md#time_put)\<CharType, OutputIterator > (`_Refs`).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
