---
title: Wartości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 24003f89-220f-4f93-be7a-b650c26157d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8bef044535d2f5a5b337823b1798feaea48745d7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106281"
---
# <a name="values"></a>Wartości

**ANSI 3.1.2.5** oświadczenia i zestawy wartości różnych typów liczb zmiennoprzecinkowych

**Float** typ zawiera 32 bity: 1 w przypadku logowania, 8 wykładnika potęgi i 23 dla mantysa. Jej zakres jest +/-3.4E38 z dokładnością co najmniej 7 cyfr.

**Double** typ zawiera 64 bitów: 1 w przypadku logowania, 11 dla wykładnik i 52 dla mantysa. Jej zakres jest +/-1.7E308 z dokładnością co najmniej 15 cyfr.

**Typu long double** typ zawiera 80 bitów: 1 znaku, 15 wykładnika potęgi i 64 dla mantysa. Jej zakres jest +/-1.2E4932 z dokładnością co najmniej 19 cyfr. Należy pamiętać, że kompilator Microsoft C: reprezentacja typu **typu long double** jest taka sama jak typ **double**.

## <a name="see-also"></a>Zobacz też

[Obliczenia matematyczne na liczbach zmiennoprzecinkowych](../c-language/floating-point-math.md)