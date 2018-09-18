---
title: Błąd krytyczny C1311 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1311
dev_langs:
- C++
helpviewer_keywords:
- C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d93aa28d0cef3c07fd469349d485c4009fa4771d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091065"
---
# <a name="fatal-error-c1311"></a>Błąd krytyczny C1311

COFF format statycznie nie może zainicjować "var" przy użyciu numeru bajtem(ów) adresu

Adres, którego wartość nie jest znany w czasie kompilacji nie statycznie przypisany do zmiennej, którego typ ma magazynu mniej niż cztery bajty.

Ten błąd może wystąpić na kod, który jest prawidłowy w języku C++.

Poniższy przykład przedstawia jeden warunek, który może spowodować C1311.

```
char c = (char)"Hello, world";   // C1311
char *d = (char*)"Hello, world";   // OK
```