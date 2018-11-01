---
title: Błąd kompilatora C2856
ms.date: 11/04/2016
f1_keywords:
- C2856
helpviewer_keywords:
- C2856
ms.assetid: fe616c51-124e-49e3-9dd8-883ec1660680
ms.openlocfilehash: 1e515f250c8ab9d1008ded91b99176f1d86d7cd1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499609"
---
# <a name="compiler-error-c2856"></a>Błąd kompilatora C2856

\#pragma hdrstop nie może być wewnątrz bloku #if

`hdrstop` Pragma nie może być umieszczona w treści bloku kompilacji warunkowej.

Przenieś `#pragma hdrstop` instrukcję, aby obszar, który nie jest zawarta w `#if/#endif` bloku.