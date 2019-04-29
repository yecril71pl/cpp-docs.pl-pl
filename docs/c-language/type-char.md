---
title: Typ char
ms.date: 11/04/2016
helpviewer_keywords:
- type char
- unsigned char keyword [C]
- char keyword [C]
ms.assetid: a5da0866-e780-4793-be87-15a8426e7ea0
ms.openlocfilehash: bc8d3bef85b82d5bb5c2575b3bc6c6d8a4887140
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345048"
---
# <a name="type-char"></a>Typ char

`char` Typ jest używany do przechowywania elementu członkowskiego zestawu znaków reprezentowanych wartości liczby całkowitej. Wartość całkowita to w kodzie ASCII określonego znaku.

**Microsoft Specific**

Znak wartości typu `unsigned char` ma zakres od 0 do 0xFF szesnastkowe. A **podpisany char** ma zakres od 0x80 do 0x7F. Te zakresy wykonuje translację elementu 0 do 255 dziesiętnego i od -128 do + 127 dziesiętną, odpowiednio. /J — opcja kompilatora zmienia domyślny z **podpisany** do `unsigned`.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Magazyn typów podstawowych](../c-language/storage-of-basic-types.md)
