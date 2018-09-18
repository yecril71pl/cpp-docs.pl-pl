---
title: Naked (C) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- naked keyword [C], storage-class attribute
- naked keyword [C]
- prolog code
- epilog code
ms.assetid: 23b1209b-93ba-46ad-a60f-2327c1933eaf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd6665bafb0041989e99a3a766204555f969d16c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062153"
---
# <a name="naked-c"></a>Naked (C)

**Microsoft Specific**

Atrybut "naked" klasę magazynu jest rozszerzeniem specyficzne dla firmy Microsoft dla języka C. Kompilator generuje kod bez kodu prologu i epilogu funkcji zadeklarowana z atrybutem "naked" klasy magazynowania. Funkcji "naked" są przydatne, gdy trzeba napisać własne sekwencji kodu prologu/epilogu przy użyciu kodu asemblera wbudowanego. Funkcje naked są przydatne przy pisaniu sterowniki urządzeń wirtualnych.

Określone informacje o korzystaniu z atrybutem "naked" można wyświetlić [funkcji "naked"](../c-language/naked-functions.md).

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Rozszerzone atrybuty klasy magazynu języka C](../c-language/c-extended-storage-class-attributes.md)