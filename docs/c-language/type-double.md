---
title: Typ double | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- mantissas, floating-point variables
- type double
- portability [C++], type double
- double data type
ms.assetid: 17c85b24-1475-4d41-a03c-ddf2d6561d34
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d3384c801f4ed7424711b0f51a42706650b75c41
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062049"
---
# <a name="type-double"></a>Typ double

Wartości podwójnej precyzji z typem double muszą 8 bajtów. Format jest podobny do formatu float, z tą różnicą, że ma ona wykładnik 1023 nadmiarowe 11-bitowe i mantysy 52-bitowych, a także dorozumianych 1 bit wyższego rzędu. Format ten zapewnia szeroką gamę około 1.7E-308 do 1.7E + 308 dla typu double.

**Microsoft Specific**

Typ double zawiera 64 bitów: 1 znaku, 11 dla wykładnik i 52 dla mantysa. Jej zakres jest +/-1.7E308 z dokładnością co najmniej 15 cyfr.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Magazyn typów podstawowych](../c-language/storage-of-basic-types.md)