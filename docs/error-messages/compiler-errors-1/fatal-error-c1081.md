---
title: Błąd krytyczny C1081
ms.date: 11/04/2016
f1_keywords:
- C1081
helpviewer_keywords:
- C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
ms.openlocfilehash: b8630a26d14c68a5f1abe45bb0b8d0141d0dedbb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204194"
---
# <a name="fatal-error-c1081"></a>Błąd krytyczny C1081

"symbol": nazwa pliku jest za długa

Długość nazwy ścieżki pliku jest większa niż `_MAX_PATH` (zdefiniowana przez STDLIB. h jako 260 znaków). Skróć nazwę pliku.

Jeśli wywołamy CL. exe z krótką nazwą pliku, może być konieczne wygenerowanie pełnej nazwy ścieżki w kompilatorze. Na przykład `cl -c myfile.cpp` może spowodować wygenerowanie kompilatora:

```
D:\<very-long-directory-path>\myfile.cpp
```
