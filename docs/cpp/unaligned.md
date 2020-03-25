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
ms.openlocfilehash: 5f93aaa79fd7c3664ecf80d5007d5954002bce4a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160648"
---
# <a name="__unaligned"></a>__unaligned

**Specyficzne dla firmy Microsoft**. Gdy deklarujesz wskaźnik z modyfikatorem **__unaligned** , kompilator zakłada, że wskaźnik adresuje dane, które nie są wyrównane. W związku z tym jest generowany kod odpowiedni dla platformy w celu obsługi niewyrównanych odczytów i zapisów za pomocą wskaźnika.

## <a name="remarks"></a>Uwagi

Ten modyfikator opisuje wyrównanie danych rozmieszczonych przez wskaźnik; przyjmuje się, że sam wskaźnik jest wyrównany.

Konieczność słowa kluczowego **__unaligned** zależy od platformy i środowiska. Niepowodzenie oznaczania danych może spowodować problemy z wydajnością przed awariami sprzętowymi. Modyfikator **__unaligned** jest nieprawidłowy dla platformy x86.

W celu zapewnienia zgodności z poprzednimi wersjami **_unaligned** jest synonimem dla **__unaligned** , chyba że opcja kompilatora [/za \(Wyłącz rozszerzenia językowe)](../build/reference/za-ze-disable-language-extensions.md) .

Aby uzyskać więcej informacji na temat wyrównania, zobacz:

- [align](../cpp/align-cpp.md)

- [Operator __alignof](../cpp/alignof-operator.md)

- [pakiet](../preprocessor/pack.md)

- [/Zp (Wyrównanie składowej struktury)](../build/reference/zp-struct-member-alignment.md)

- [Przykłady wyrównania struktury](../build/x64-software-conventions.md#examples-of-structure-alignment)

## <a name="see-also"></a>Zobacz też

[Słowa kluczowe](../cpp/keywords-cpp.md)
