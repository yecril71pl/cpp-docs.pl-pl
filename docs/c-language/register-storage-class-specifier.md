---
title: rejestracja specyfikatora klasy magazynowania
ms.date: 11/04/2016
helpviewer_keywords:
- register variables
- register storage class
ms.assetid: 7577bf48-88ec-4191-873c-ef4217a4034e
ms.openlocfilehash: 513213222ee2c598455709a0891977a0949c8555
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229561"
---
# <a name="register-storage-class-specifier"></a>rejestracja specyfikatora klasy magazynowania

**Specyficzne dla firmy Microsoft**

Kompilator języka Microsoft C/C++ nie honoruje żądań użytkowników dotyczących zmiennych rejestru. Jednak w przypadku przenoszenia wszystkie inne semantyki skojarzone ze **`register`** słowem kluczowym są uznawane przez kompilator. Na przykład nie można zastosować jednoargumentowego adresu operatora ( **&** ) do obiektu Register ani **`register`** słowa kluczowego nie można używać w tablicach.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Specyfikatory klasy magazynowania dla deklaracji na poziomie wewnętrznym](../c-language/storage-class-specifiers-for-internal-level-declarations.md)
