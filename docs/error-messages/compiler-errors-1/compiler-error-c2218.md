---
title: Błąd kompilatora C2218
ms.date: 11/04/2016
f1_keywords:
- C2218
helpviewer_keywords:
- C2218
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
ms.openlocfilehash: db14c37992fc1e2dd409c653d622d3419fcae4f3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206651"
---
# <a name="compiler-error-c2218"></a>Błąd kompilatora C2218

nie można użyć "__vectorcall" z "/arch: IA32"

Konwencja wywoływania `__vectorcall` jest obsługiwana tylko w kodzie natywnym na procesorach x86 i x64, które zawierają Streaming SIMD Extensions 2 (SSE2) i nowsze. Aby uzyskać więcej informacji, zobacz [__vectorcall](../../cpp/vectorcall.md).

Aby naprawić ten błąd, Zmień opcje kompilatora w celu docelową SSE2, AVX lub AVX2 zestawów instrukcji. Aby uzyskać więcej informacji, zobacz [/arch (x86)](../../build/reference/arch-x86.md).
