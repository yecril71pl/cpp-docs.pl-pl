---
title: Błąd kompilatora C3728
ms.date: 11/04/2016
f1_keywords:
- C3728
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
ms.openlocfilehash: 68aa23843b0470f15f409b6f3b58624f979ccfae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328110"
---
# <a name="compiler-error-c3728"></a>Błąd kompilatora C3728

"event": zdarzenie nie posiada metody wzrostu

Metadane utworzone za pomocą języka, takich jak C#, która nie zezwala na zdarzenia z poza klasy, w którym został zdefiniowany, został uwzględniony w [#using](../../preprocessor/hash-using-directive-cpp.md) dyrektywy i programu Visual C++ przy użyciu CLR — programowanie podjęto próbę Wywołaj zdarzenie.

Aby wywołać zdarzenie w programie w języku, takim jak C#, klasy zawierającej zdarzenia musi także definiować metodę publiczną, która wywołuje zdarzenie.