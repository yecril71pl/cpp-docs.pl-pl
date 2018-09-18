---
title: Błąd kompilatora C3728 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3728
dev_langs:
- C++
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e412824bd2afdadfc21d71b73f38eb8ba5ace82d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108420"
---
# <a name="compiler-error-c3728"></a>Błąd kompilatora C3728

"event": zdarzenie nie posiada metody wzrostu

Metadane utworzone za pomocą języka, takich jak C#, która nie zezwala na zdarzenia z poza klasy, w którym został zdefiniowany, został uwzględniony w [#using](../../preprocessor/hash-using-directive-cpp.md) dyrektywy i programu Visual C++ przy użyciu CLR — programowanie podjęto próbę Wywołaj zdarzenie.

Aby wywołać zdarzenie w programie w języku, takim jak C#, klasy zawierającej zdarzenia musi także definiować metodę publiczną, która wywołuje zdarzenie.