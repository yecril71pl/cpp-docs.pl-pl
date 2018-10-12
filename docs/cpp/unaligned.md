---
title: __unaligned | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/10/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __unaligned_cpp
- __unaligned
- _unaligned
dev_langs:
- C++
helpviewer_keywords:
- __unaligned keyword [C++]
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 444bc3372b22676cacb3ee89b9c0ad92000cedcc
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161221"
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

- [Przykłady wyrównania struktury](../build/examples-of-structure-alignment.md)

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)