---
title: Błąd kompilatora C3507 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3507
dev_langs:
- C++
helpviewer_keywords:
- C3507
ms.assetid: 75f89767-f6f9-40f6-9820-81a49e09abdf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8375f96c0a35e01a2a93866157c0156cf22a4993
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46105168"
---
# <a name="compiler-error-c3507"></a>Błąd kompilatora C3507

Identyfikator ProgID może zawierać nie więcej niż 39 znaków 'id'; nie zawierać żadnych znaków interpunkcyjnych z wyjątkiem '.'; ani rozpoczynających się od cyfry

[Progid](../../windows/progid.md) atrybut ma ograniczenia na podstawie wartości, które można wykonać.

Poniższy przykład spowoduje wygenerowanie C3507:

```
// C3507.cpp
[module(name="x")];
[
coclass,
progid("0123456789012345678901234567890123456789"),
uuid("00000000-0000-0000-0000-000000000001") // C3507 expected
]
struct CMyStruct {
};
int main() {
}
```