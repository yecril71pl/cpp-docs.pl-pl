---
title: Błąd kompilatora C3552
ms.date: 11/04/2016
f1_keywords:
- C3552
helpviewer_keywords:
- C3552
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
ms.openlocfilehash: d2d3a60fcd4a26238cd6cf330f47b48c5b3198ad
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230834"
---
# <a name="compiler-error-c3552"></a>Błąd kompilatora C3552

"typename": określony typ zwracany przez późny nie może zawierać elementu "Auto"

Jeśli używasz **`auto`** słowa kluczowego jako symbolu zastępczego dla zwracanego typu funkcji, musisz podać typ zwracany określony jako późny. Nie można jednak użyć innego **`auto`** słowa kluczowego, aby określić typ zwracany określony jako opóźniony. Na przykład poniższy fragment kodu powoduje zwrócenie błędu C3552.

`auto myFunction->auto; // C3552`
