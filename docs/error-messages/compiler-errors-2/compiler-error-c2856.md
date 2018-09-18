---
title: Błąd kompilatora C2856 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2856
dev_langs:
- C++
helpviewer_keywords:
- C2856
ms.assetid: fe616c51-124e-49e3-9dd8-883ec1660680
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: df6226bfd2fc11f05f894091f4ff02c145d09e11
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072721"
---
# <a name="compiler-error-c2856"></a>Błąd kompilatora C2856

\#pragma hdrstop nie może być wewnątrz bloku #if

`hdrstop` Pragma nie może być umieszczona w treści bloku kompilacji warunkowej.

Przenieś `#pragma hdrstop` instrukcję, aby obszar, który nie jest zawarta w `#if/#endif` bloku.