---
title: Błąd kompilatora zasobów RC2151
ms.date: 11/04/2016
f1_keywords:
- RC2151
helpviewer_keywords:
- RC2151
ms.assetid: 3c47e535-c78d-4338-aab9-9b47e2c34728
ms.openlocfilehash: 8eaa50bc6080e37a4a74585eb03cbe4e40893bce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173447"
---
# <a name="resource-compiler-error-rc2151"></a>Błąd kompilatora zasobów RC2151

Nie można ponownie używać stałych ciągów

W przypadku korzystania z taką samą wartość, dwa razy w **STRINGTABLE** instrukcji. Upewnij się, że są nie mieszanie nakładających się wartości dziesiętnej i szesnastkowej.

Każdy identyfikator w **STRINGTABLE** muszą być unikatowe. Dla stałych ciągłego użycia maksymalną wydajność, która jest uruchamiana na wielokrotnością liczby 16.