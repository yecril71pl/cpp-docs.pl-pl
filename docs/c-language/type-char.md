---
title: Typ char | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- type char
- unsigned char keyword [C]
- char keyword [C]
ms.assetid: a5da0866-e780-4793-be87-15a8426e7ea0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eec964d9b81ee93f888bbd4152f06f6bdf51b6d0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053833"
---
# <a name="type-char"></a>Typ char

`char` Typ jest używany do przechowywania elementu członkowskiego zestawu znaków reprezentowanych wartości liczby całkowitej. Wartość całkowita to w kodzie ASCII określonego znaku.

**Microsoft Specific**

Znak wartości typu `unsigned char` ma zakres od 0 do 0xFF szesnastkowe. A **podpisany char** ma zakres od 0x80 do 0x7F. Te zakresy wykonuje translację elementu 0 do 255 dziesiętnego i od -128 do + 127 dziesiętną, odpowiednio. /J — opcja kompilatora zmienia domyślny z **podpisany** do `unsigned`.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Magazyn typów podstawowych](../c-language/storage-of-basic-types.md)