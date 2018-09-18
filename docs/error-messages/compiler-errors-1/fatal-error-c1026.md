---
title: Błąd krytyczny C1026 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1026
dev_langs:
- C++
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db9167383df48dad274ef8941defaa53f51d3bfa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068991"
---
# <a name="fatal-error-c1026"></a>Błąd krytyczny C1026

przepełnienie stosu analizatora składni, zbyt złożony program

Miejsca wymaganego do analizowania program spowodowało przepełnienie stosu kompilatora.

Zmniejsz złożoność wyrażenia przez:

- Zmniejszenie zagnieżdżenia w `for` i `switch` instrukcji. Umieść głębiej zagnieżdżonych instrukcji w funkcji.

- Podzielenie długich wyrażeń obejmujących operatory przecinkami lub wywołania funkcji.