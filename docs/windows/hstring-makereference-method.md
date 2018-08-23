---
title: HString::MakeReference, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::MakeReference
dev_langs:
- C++
ms.assetid: 9e1fd2b2-66ad-4a50-b647-a20ab10e522f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 061b3be0e642bb8e7406f54a469723c70559d85a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610164"
---
# <a name="hstringmakereference-method"></a>HString::MakeReference — Metoda

Tworzy `HStringReference` obiekt z określonego parametru ciągu.

## <a name="syntax"></a>Składnia

```cpp
template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[ sizeDest]);

    template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[sizeDest],
              unsigned int len);
```

### <a name="parameters"></a>Parametry

*sizeDest*  
Parametr szablonu, który określa rozmiar docelowy `HStringReference` buforu.

*str*  
Odwołanie do ciągu znaków dwubajtowych.

*Len*  
Maksymalna długość *str* bufora parametru w tej operacji. Jeśli *len* parametr nie jest określony, całą *str* parametr jest używany.

## <a name="return-value"></a>Wartość zwracana

`HStringReference` Obiektu, którego wartość jest taka sama, jak określa *str* parametru.

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz też

[HString, klasa](../windows/hstring-class.md)