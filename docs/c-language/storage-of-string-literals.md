---
title: Magazynowanie literałów ciągu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- string literals, storage
ms.assetid: ba5e4d2c-d456-44b3-a8ca-354af547ac50
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 111acab00783de67dcb3ecc8b9d45fe112332158
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019527"
---
# <a name="storage-of-string-literals"></a>Magazynowanie literałów ciągu

Znaki literału ciągu są przechowywane w kolejności w lokalizacjach pamięci ciągłej. Sekwencja unikowa (takie jak **\\ \\** lub  **\\"**) w ramach literału ciągu jest liczona jako jeden znak. Znak null (reprezentowane przez **\0** sekwencji unikowej) jest automatycznie dołączany do pisania, a końcu każdego ciągu literału. (Ten problem wystąpi podczas [fazie tłumaczenia](../preprocessor/phases-of-translation.md) 7.) Należy pamiętać, że kompilator nie może przechowywać dwie identyczne ciągi pod dwoma różnymi adresami. [/GF](../build/reference/gf-eliminate-duplicate-strings.md) wymusza na kompilatorze umieszcza pojedynczej kopii identycznych ciągów w pliku wykonywalnego.

## <a name="remarks"></a>Uwagi

**Microsoft Specific**

Ciągi mają statyczny czas magazynowania. Zobacz [klasy magazynu](../c-language/c-storage-classes.md) informacji o czas trwania przechowywania.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Literały ciągu języka C](../c-language/c-string-literals.md)