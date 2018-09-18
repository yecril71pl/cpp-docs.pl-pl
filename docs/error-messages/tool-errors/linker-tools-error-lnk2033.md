---
title: Błąd narzędzi konsolidatora LNK2033 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2033
dev_langs:
- C++
helpviewer_keywords:
- LNK2033
ms.assetid: d61db467-9328-4788-bf54-e2a20537f13f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6c547b4d35e2e7fe057cdd67f0dad47f58d000c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039998"
---
# <a name="linker-tools-error-lnk2033"></a>Błąd narzędzi konsolidatora LNK2033

Nierozpoznany token typeref (token) dla "type"

Typ nie ma definicji metadanych MSIL.

LNK2033 mogą wystąpić podczas kompilowania za pomocą **/CLR: Safe** i gdzie występuje tylko deklaracja typu w moduł MSIL, gdzie typ odwołuje się moduł MSIL.

Typ musi być zdefiniowane w obszarze **/CLR: Safe**.

Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie LNK2033.

```
// LNK2033.cpp
// compile with: /clr:safe
// LNK2033 expected
ref class A;
ref class B {};

int main() {
   A ^ aa = nullptr;
   B ^ bb = nullptr;   // OK
};
```