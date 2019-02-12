---
title: Typ double
ms.date: 11/04/2016
helpviewer_keywords:
- mantissas, floating-point variables
- type double
- portability [C++], type double
- double data type
ms.assetid: 17c85b24-1475-4d41-a03c-ddf2d6561d34
ms.openlocfilehash: 43e6cc444f4d6a973fc58b5ce550e468066aca1b
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151861"
---
# <a name="type-double"></a>Typ double

Wartości podwójnej precyzji z typem double muszą 8 bajtów. Format jest podobny do formatu float, z tą różnicą, że ma ona wykładnik 1023 nadmiarowe 11-bitowe i mantysy 52-bitowych, a także dorozumianych 1 bit wyższego rzędu. Format ten zapewnia szeroką gamę około 1.7E-308 do 1.7E + 308 dla typu double.

**Microsoft Specific**

Typ double zawiera 64-bitowy: 1 znaku, 11 dla wykładnik i 52 dla mantysa. Jej zakres jest +/-1.7E308 z dokładnością co najmniej 15 cyfr.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Magazyn typów podstawowych](../c-language/storage-of-basic-types.md)
