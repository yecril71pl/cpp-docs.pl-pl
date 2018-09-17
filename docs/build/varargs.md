---
title: VarArgs | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aac0c54b-0a2d-4a22-b1de-ee41381a3eb1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8305eaddf87a2e67b797bedff1944dbcbbbdbd41
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713651"
---
# <a name="varargs"></a>Elementy vararg

Jeśli parametry są przekazywane za pośrednictwem varargs (na przykład wielokropka argumentów), zasadniczo przekazywanie normalne parametru dotyczy, tym rozlanie argumenty piątym i kolejnych. Odpowiada za ponownie wywoływany argumenty zrzutu, które ma zajęty adres w ich. Tylko wartości zmiennoprzecinkowych liczba całkowita i zmiennoprzecinkowa rejestr będzie zawierać wartości zmiennoprzecinkowej w przypadku, gdy wywoływany oczekuje, że wartość w rejestrach liczby całkowitej.

## <a name="see-also"></a>Zobacz też

[Konwencja wywoływania](../build/calling-convention.md)