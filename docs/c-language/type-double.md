---
title: Typ double
ms.date: 11/04/2016
helpviewer_keywords:
- mantissas, floating-point variables
- type double
- portability [C++], type double
- double data type
ms.assetid: 17c85b24-1475-4d41-a03c-ddf2d6561d34
ms.openlocfilehash: 42f8ed943fd9d034d5cae8cb057e094363b27d8e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532265"
---
# <a name="type-double"></a>Typ double

Wartości podwójnej precyzji z typem double muszą 8 bajtów. Format jest podobny do formatu float, z tą różnicą, że ma ona wykładnik 1023 nadmiarowe 11-bitowe i mantysy 52-bitowych, a także dorozumianych 1 bit wyższego rzędu. Format ten zapewnia szeroką gamę około 1.7E-308 do 1.7E + 308 dla typu double.

**Microsoft Specific**

Typ double zawiera 64 bitów: 1 znaku, 11 dla wykładnik i 52 dla mantysa. Jej zakres jest +/-1.7E308 z dokładnością co najmniej 15 cyfr.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Magazyn typów podstawowych](../c-language/storage-of-basic-types.md)