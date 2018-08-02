---
title: __unaligned | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __unaligned_cpp
dev_langs:
- C++
helpviewer_keywords:
- __unaligned keyword [C++]
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e2690e52bb6145da5525c0e268c5ded8da3aa661
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466764"
---
# <a name="unaligned"></a>__unaligned

**Specyficzne dla firmy Microsoft**. Kiedy Deklarujesz wskaźnika za pomocą **__unaligned** modyfikator, kompilator zakłada, że wskaźnik adresów danych, który nie jest wyrównany. W związku z tym odpowiednich platform kod jest generowany w celu obsługi niewyrównanych odczytuje i zapisuje za pomocą wskaźnika.

## <a name="remarks"></a>Uwagi

Ten modyfikator opisuje wyrównanie danych adresowany przez wskaźnik; wskaźnik, sama zakłada się, że można wyrównać.

Konieczność **__unaligned** — słowo kluczowe jest zależna od platformy i środowiska. Nie można oznaczyć odpowiednio danych może spowodować problemy z zakresu od spadku wydajności na awarie sprzętu. **__Unaligned** modyfikator nie jest prawidłowa dla x86 platformy.

Aby uzyskać więcej informacji na temat wyrównania zobacz:

- [align](../cpp/align-cpp.md)

- [Operator __alignof](../cpp/alignof-operator.md)

- [pakiet](../preprocessor/pack.md)

- [/Zp (Wyrównanie składowej struktury)](../build/reference/zp-struct-member-alignment.md)

- [Przykłady wyrównania struktury](../build/examples-of-structure-alignment.md)

## <a name="see-also"></a>Zobacz także
 [Słowa kluczowe](../cpp/keywords-cpp.md)