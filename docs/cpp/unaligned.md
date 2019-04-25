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
ms.openlocfilehash: 8eb1b93aa55601125600b6c69d9bff3d9ca43aa3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62244119"
---
# <a name="unaligned"></a>__unaligned

**Specyficzne dla firmy Microsoft**. Kiedy Deklarujesz wskaźnika za pomocą **__unaligned** modyfikator, kompilator zakłada, że wskaźnik adresów danych, który nie jest wyrównany. W związku z tym odpowiednich platform kod jest generowany w celu obsługi niewyrównanych odczytuje i zapisuje za pomocą wskaźnika.

## <a name="remarks"></a>Uwagi

Ten modyfikator opisuje wyrównanie danych adresowany przez wskaźnik; wskaźnik, sama zakłada się, że można wyrównać.

Konieczność **__unaligned** — słowo kluczowe jest zależna od platformy i środowiska. Nie można oznaczyć odpowiednio danych może spowodować problemy z zakresu od spadku wydajności na awarie sprzętu. **__Unaligned** modyfikator nie jest prawidłowa dla x86 platformy.

W celu zgodności z poprzednimi wersjami **_unaligned** jest synonimem dla **__unaligned** chyba że — opcja kompilatora [/Za \(Wyłącz rozszerzenia językowe)](../build/reference/za-ze-disable-language-extensions.md) został określony.

Aby uzyskać więcej informacji na temat wyrównania zobacz:

- [align](../cpp/align-cpp.md)

- [Operator __alignof](../cpp/alignof-operator.md)

- [pakiet](../preprocessor/pack.md)

- [/Zp (Wyrównanie składowej struktury)](../build/reference/zp-struct-member-alignment.md)

- [Przykłady wyrównania struktury](../build/x64-software-conventions.md#examples-of-structure-alignment)

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)