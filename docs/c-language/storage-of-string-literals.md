---
title: Magazynowanie literałów ciągu
ms.date: 11/04/2016
helpviewer_keywords:
- string literals, storage
ms.assetid: ba5e4d2c-d456-44b3-a8ca-354af547ac50
ms.openlocfilehash: 0d505479f0844122826a2f07b57eaa69f33932e8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157867"
---
# <a name="storage-of-string-literals"></a>Magazynowanie literałów ciągu

Znaki literału ciągu są przechowywane w kolejności w lokalizacjach pamięci ciągłej. Sekwencja unikowa (takie jak **\\ \\** lub  **\\"**) w ramach literału ciągu jest liczona jako jeden znak. Znak null (reprezentowane przez **\0** sekwencji unikowej) jest automatycznie dołączany do pisania, a końcu każdego ciągu literału. (Ten problem wystąpi podczas [fazie tłumaczenia](../preprocessor/phases-of-translation.md) 7.) Należy pamiętać, że kompilator nie może przechowywać dwie identyczne ciągi pod dwoma różnymi adresami. [/GF](../build/reference/gf-eliminate-duplicate-strings.md) wymusza na kompilatorze umieszcza pojedynczej kopii identycznych ciągów w pliku wykonywalnego.

## <a name="remarks"></a>Uwagi

**Microsoft Specific**

Ciągi mają statyczny czas magazynowania. Zobacz [klasy magazynu](../c-language/c-storage-classes.md) informacji o czas trwania przechowywania.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Literały ciągu języka C](../c-language/c-string-literals.md)
