---
title: Konwersje przypisań | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- conversions, assignment
- assignment conversions
ms.assetid: 4ee01013-de32-4aae-b12e-0051d0cde927
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90e77f4bd1eddaa11762b9449a54cb7127498bae
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038183"
---
# <a name="assignment-conversions"></a>Konwersje przypisań

W operacji przypisania typ wartości jest przypisane jest konwertowany na typ zmiennej, która odbiera przypisania. C umożliwia konwersje przez przypisanie między typów całkowitych i zmiennoprzecinkowych, nawet wtedy, gdy informacje są tracone w konwersji. Metodę konwersji zależy od typów, które są związane z przypisania, zgodnie z opisem w [zwykle konwersje arytmetyczne](../c-language/usual-arithmetic-conversions.md) i w poniższych sekcjach:

- [Konwersje z podpisanych typów całkowitych](../c-language/conversions-from-signed-integral-types.md)

- [Konwersje z niepodpisanych typów całkowitych](../c-language/conversions-from-unsigned-integral-types.md)

- [Konwersje z typów zmiennoprzecinkowych](../c-language/conversions-from-floating-point-types.md)

- [Konwersje do i z typów wskaźnika](../c-language/conversions-to-and-from-pointer-types.md)

- [Konwersje z innych typów](../c-language/conversions-from-other-types.md)

Kwalifikatory typów nie wpływają na istoty konwersji mimo że **const** l wartością, nie można użyć po lewej stronie przypisania.

## <a name="see-also"></a>Zobacz też

[Konwersje typów](../c-language/type-conversions-c.md)