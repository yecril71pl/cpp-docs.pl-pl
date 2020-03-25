---
title: Ostrzeżenie kompilatora (poziom 4) C4960
ms.date: 11/04/2016
f1_keywords:
- C4960
helpviewer_keywords:
- C4960
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
ms.openlocfilehash: 286d3a1953c6c6badf15b712feac99afafe8b0a7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198123"
---
# <a name="compiler-warning-level-4-c4960"></a>Ostrzeżenie kompilatora (poziom 4) C4960

element "Function" jest zbyt duży, aby można go było profilować

W przypadku korzystania z [/LTCG: PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md)Kompilator wykrył Moduł wejściowy z funkcją przekraczającą 65 535 instrukcji. Taka duża funkcja nie jest dostępna w przypadku optymalizacji z przewodnikiem.

Aby usunąć to ostrzeżenie, zmniejsz rozmiar funkcji.
