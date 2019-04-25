---
title: Ostrzeżenie D9043 dla wiersza polecenia
ms.date: 11/04/2016
f1_keywords:
- D9043
helpviewer_keywords:
- D9043
ms.assetid: 9263e28d-217b-414c-bfb6-86efd3c27a77
ms.openlocfilehash: 62834c5f245bc1c0f6197638e4608b7fe71e7eb1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62213497"
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