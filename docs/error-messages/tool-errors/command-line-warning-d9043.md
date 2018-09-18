---
title: Ostrzeżenie wiersza polecenia D9043 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9043
dev_langs:
- C++
helpviewer_keywords:
- D9043
ms.assetid: 9263e28d-217b-414c-bfb6-86efd3c27a77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d29371e147c693b2aa49f8dcf838841af3c75c8d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031876"
---
# <a name="command-line-warning-d9043"></a>Ostrzeżenie D9043 dla wiersza polecenia

Nieprawidłowa wartość "warning_level" do 'compiler_option'; Zakładając, że '4999'; Ostrzeżenia analizy kodu nie są skojarzone z poziomami ostrzeżeń

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C9043.

```
// D9043.cpp
// compile with: /analyze /w16001
// D9043 warning expected
int main() {}
```