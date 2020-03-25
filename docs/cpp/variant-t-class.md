---
title: _variant_t — Klasa
ms.date: 11/04/2016
f1_keywords:
- _variant_t
helpviewer_keywords:
- _variant_t class [C++], operators
- _variant_t class
- _variant_t class [C++], member functions
- VARIANT object
- VARIANT object [C++], COM encapsulation
ms.assetid: 6a3cbd4e-0ae8-425e-b4cf-ca0df894c93f
ms.openlocfilehash: e11d31904fd8e54049f69ee4f6530d511c8c7f4e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187755"
---
# <a name="_variant_t-class"></a>_variant_t — Klasa

**Specyficzne dla firmy Microsoft**

Obiekt **_variant_t** hermetyzuje `VARIANT` typ danych. Klasa zarządza alokacją zasobów i cofaniem alokacji i tworzy wywołania funkcji w celu `VariantInit` i `VariantClear`, zgodnie z potrzebami.

### <a name="construction"></a>Zrekonstruowan

|||
|-|-|
|[_variant_t](../cpp/variant-t-variant-t.md)|Konstruuje obiekt **_variant_t** .|

### <a name="operations"></a>Operacje

|||
|-|-|
|[Attach](../cpp/variant-t-attach.md)|Dołącza obiekt `VARIANT` do obiektu **_variant_t** .|
|[Wyczyść](../cpp/variant-t-clear.md)|Czyści obiekt hermetyzowany `VARIANT`.|
|[ChangeType](../cpp/variant-t-changetype.md)|Zmienia typ obiektu **_variant_t** na wskazany `VARTYPE`.|
|[Detach](../cpp/variant-t-detach.md)|Odłącza obiekt hermetyzowany `VARIANT` z tego obiektu **_variant_t** .|
|[Metodami SetString](../cpp/variant-t-setstring.md)|Przypisuje ciąg do tego obiektu **_variant_t** .|

### <a name="operators"></a>Operatory

|||
|-|-|
|[Operator =](../cpp/variant-t-operator-equal.md)|Przypisuje nową wartość do istniejącego obiektu **_variant_t** .|
|[operator = =,! =](../cpp/variant-t-relational-operators.md)|Porównaj dwa **_variant_t** obiekty pod kątem równości lub nierówności.|
|[Ekstraktory](../cpp/variant-t-extractors.md)|Wyodrębnij dane z hermetyzowanego obiektu `VARIANT`.|

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<comutil. h >

**Lib:** comsuppw. lib lub comsuppwd. lib (patrz [/Zc: Wchar_t (Wchar_t jest typem natywnym)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) , aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz też

[Kompilator klas obsługi COM](../cpp/compiler-com-support-classes.md)
