---
title: __unaligned
ms.date: 12/17/2018
f1_keywords:
- __unaligned_cpp
- __unaligned
- _unaligned
helpviewer_keywords:
- __unaligned keyword [C++]
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
ms.openlocfilehash: 2ab94a44d08165ca6e8f394278e24d7c8d201398
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223502"
---
# <a name="__unaligned"></a>__unaligned

**Specyficzne dla firmy Microsoft**. Gdy deklarujesz wskaźnik z **`__unaligned`** modyfikatorem, kompilator zakłada, że wskaźnik adresuje dane, które nie są wyrównane. W związku z tym jest generowany kod odpowiedni dla platformy w celu obsługi niewyrównanych odczytów i zapisów za pomocą wskaźnika.

## <a name="remarks"></a>Uwagi

Ten modyfikator opisuje wyrównanie danych rozmieszczonych przez wskaźnik; przyjmuje się, że sam wskaźnik jest wyrównany.

Konieczność **`__unaligned`** słowa kluczowego zależy od platformy i środowiska. Niepowodzenie oznaczania danych może spowodować problemy z wydajnością przed awariami sprzętowymi. **`__unaligned`** Modyfikator jest nieprawidłowy dla platformy x86.

W celu zapewnienia zgodności z poprzednimi wersjami, **`_unaligned`** jest synonimem, **`__unaligned`** Jeśli opcja kompilatora [ `/Za` \( disable rozszerzenia języka](../build/reference/za-ze-disable-language-extensions.md) nie jest określona.

Aby uzyskać więcej informacji na temat wyrównania, zobacz:

- [`align`](../cpp/align-cpp.md)

- [`alignof`Zakład](../cpp/alignof-operator.md)

- [`pack`](../preprocessor/pack.md)

- [`/Zp`(Wyrównanie składowej struktury)](../build/reference/zp-struct-member-alignment.md)

- [Przykłady wyrównania struktury](../build/x64-software-conventions.md#examples-of-structure-alignment)

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)
