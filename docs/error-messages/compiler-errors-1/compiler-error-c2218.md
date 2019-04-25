---
title: Błąd kompilatora C2218
ms.date: 11/04/2016
f1_keywords:
- C2218
helpviewer_keywords:
- C2218
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
ms.openlocfilehash: 5a9d897686fc915c9892fa2bcd51fa3ca3c8b05e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165680"
---
# <a name="compiler-error-c2218"></a>Błąd kompilatora C2218

"__vectorcall" nie można używać z "/ arch: IA32"

`__vectorcall` Konwencja wywołania jest obsługiwana tylko w kodzie macierzystym na procesorach x86 i x64, obejmujących Streaming SIMD Extensions 2 (SSE2) i nowszych. Aby uzyskać więcej informacji, zobacz [__vectorcall](../../cpp/vectorcall.md).

Aby naprawić ten błąd, zmień opcje kompilatora z docelowym instrukcji SSE2, AVX i AVX2 ustawia. Aby uzyskać więcej informacji, zobacz [/arch (x86)](../../build/reference/arch-x86.md).