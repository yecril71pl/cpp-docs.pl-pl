---
title: Błąd kompilatora zasobów RC2151 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2151
dev_langs:
- C++
helpviewer_keywords:
- RC2151
ms.assetid: 3c47e535-c78d-4338-aab9-9b47e2c34728
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a15f3f1237df9e4b706a2c2048dddd6d5db395d5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109785"
---
# <a name="resource-compiler-error-rc2151"></a>Błąd kompilatora zasobów RC2151

Nie można ponownie używać stałych ciągów

W przypadku korzystania z taką samą wartość, dwa razy w **STRINGTABLE** instrukcji. Upewnij się, że są nie mieszanie nakładających się wartości dziesiętnej i szesnastkowej.

Każdy identyfikator w **STRINGTABLE** muszą być unikatowe. Dla stałych ciągłego użycia maksymalną wydajność, która jest uruchamiana na wielokrotnością liczby 16.