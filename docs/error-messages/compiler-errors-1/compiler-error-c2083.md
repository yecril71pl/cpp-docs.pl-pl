---
title: Błąd kompilatora C2083 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2083
dev_langs:
- C++
helpviewer_keywords:
- C2083
ms.assetid: 5fc4f931-eab6-4d8d-a3ee-3b8e11e64b18
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: adf2787f8aea3611abd9eeac054df6bb054d802a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103285"
---
# <a name="compiler-error-c2083"></a>Błąd kompilatora C2083

niedozwolone porównanie struct/union

Struktury lub Unii jest porównywana bezpośrednio z innego typu zdefiniowanego przez użytkownika. Nie jest to dozwolone, jeśli nie zdefiniowano operator porównania lub istnieje konwersja na typ skalarny.