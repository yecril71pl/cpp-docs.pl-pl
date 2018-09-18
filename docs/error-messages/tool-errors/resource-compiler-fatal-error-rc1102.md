---
title: Błąd krytyczny kompilatora zasobów RC1102 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1102
dev_langs:
- C++
helpviewer_keywords:
- RC1102
ms.assetid: bd2091f8-ef5e-4151-a8d6-98043e9422b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2be0a62b08b361f1cfa423fa3999a440e2fe4709
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073190"
---
# <a name="resource-compiler-fatal-error-rc1102"></a>Błąd krytyczny kompilatora zasobów RC1102

Błąd wewnętrzny: za dużo argumentów dla RCPP

Zbyt wiele argumentów zostało przekazanych do preprocesora kompilatora zasobów. Zmniejsz liczbę symboli zdefiniowanych z symbolami zdefiniować (/ d) opcja, definiując je w źródle. Ten błąd, również może być spowodowany określając zbyt wiele zawiera ścieżki wyszukiwania pliku przy użyciu opcji zawierają ścieżkę wyszukiwania (/ i).