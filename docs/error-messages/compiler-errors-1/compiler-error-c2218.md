---
title: Błąd kompilatora C2218 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2218
dev_langs:
- C++
helpviewer_keywords:
- C2218
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52c449381c6e8a7391706ed6097bc38576bc69fe
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041288"
---
# <a name="compiler-error-c2218"></a>Błąd kompilatora C2218

"__vectorcall" nie można używać z "/ arch: IA32"

`__vectorcall` Konwencja wywołania jest obsługiwana tylko w kodzie macierzystym na procesorach x86 i x64, obejmujących Streaming SIMD Extensions 2 (SSE2) i nowszych. Aby uzyskać więcej informacji, zobacz [__vectorcall](../../cpp/vectorcall.md).

Aby naprawić ten błąd, zmień opcje kompilatora z docelowym instrukcji SSE2, AVX i AVX2 ustawia. Aby uzyskać więcej informacji, zobacz [/arch (x86)](../../build/reference/arch-x86.md).