---
title: Typ char
ms.date: 11/04/2016
helpviewer_keywords:
- type char
- unsigned char keyword [C]
- char keyword [C]
ms.assetid: a5da0866-e780-4793-be87-15a8426e7ea0
ms.openlocfilehash: bc8d3bef85b82d5bb5c2575b3bc6c6d8a4887140
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152212"
---
# <a name="type-char"></a>Typ char

`char` Typ jest używany do przechowywania elementu członkowskiego zestawu znaków reprezentowanych wartości liczby całkowitej. Wartość całkowita to w kodzie ASCII określonego znaku.

**Microsoft Specific**

Znak wartości typu `unsigned char` ma zakres od 0 do 0xFF szesnastkowe. A **podpisany char** ma zakres od 0x80 do 0x7F. Te zakresy wykonuje translację elementu 0 do 255 dziesiętnego i od -128 do + 127 dziesiętną, odpowiednio. /J — opcja kompilatora zmienia domyślny z **podpisany** do `unsigned`.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Magazyn typów podstawowych](../c-language/storage-of-basic-types.md)
