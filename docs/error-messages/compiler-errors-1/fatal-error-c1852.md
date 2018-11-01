---
title: Błąd krytyczny C1852
ms.date: 11/04/2016
f1_keywords:
- C1852
helpviewer_keywords:
- C1852
ms.assetid: fa011004-b8d6-46f1-ba80-4785e4ce137f
ms.openlocfilehash: 895c2fc988c9566f9e50b1ac1a18eb4dc1c6661a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601503"
---
# <a name="fatal-error-c1852"></a>Błąd krytyczny C1852

"filename" nie jest prawidłowym prekompilowanym plikiem nagłówkowym

Plik nie jest prekompilowanego nagłówka.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. Nieprawidłowy plik określony za pomocą **/Yu** lub **#pragma hdrstop**.

1. Kompilator zakłada rozszerzenie pliku .pch, jeśli nie określono inaczej.