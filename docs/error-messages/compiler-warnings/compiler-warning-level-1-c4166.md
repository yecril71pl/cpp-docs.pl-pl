---
title: Kompilator ostrzeżenie (poziom 1) C4166 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4166
dev_langs:
- C++
helpviewer_keywords:
- C4166
ms.assetid: 4e5398a1-d913-4791-a470-06fc99c36ac5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c6112c684dc4896393b35309a0a3af7eedd455d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052000"
---
# <a name="compiler-warning-level-1-c4166"></a>Kompilator ostrzeżenie (poziom 1) C4166

**Niedozwolona konwencja wywołania dla konstruktora/destruktora**

Konstruktory i destruktory nie mogą mieć wywoływania konwencje inną niż domyślna platformy (z wyjątkiem sytuacji, gdy jawnie określić **__clrcall**).