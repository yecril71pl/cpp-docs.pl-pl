---
title: Błąd krytyczny C1081
ms.date: 11/04/2016
f1_keywords:
- C1081
helpviewer_keywords:
- C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
ms.openlocfilehash: f3c9f9bde5da7fb120accbb9a8d72e5715ab9d2b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62229422"
---
# <a name="fatal-error-c1081"></a>Błąd krytyczny C1081

'symbol': Nazwa pliku jest za długa

Długość nazwy ścieżki pliku przekracza `_MAX_PATH` (zdefiniowanej przez STDLIB.h jako 260 znaków). Skróć nazwę pliku.

Wywołanie CL.exe z krótkiej nazwy pliku, kompilator może trzeba będzie wygenerować pełną nazwę ścieżki. Na przykład `cl -c myfile.cpp` może spowodować, że kompilator do wygenerowania:

```
D:\<very-long-directory-path>\myfile.cpp
```