---
title: Błąd krytyczny C1046 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1046
dev_langs:
- C++
helpviewer_keywords:
- C1046
ms.assetid: 822ec5f5-b0b0-4711-99e1-fc237b619af6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 449b181167ef493c149e9e34cb2f1a681148411d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035475"
---
# <a name="fatal-error-c1046"></a>Błąd krytyczny C1046

ograniczenie kompilatora: struktury są zagnieżdżone zbyt głęboko

Struktura, Unia lub klasa Przekroczono limit zagnieżdżania poziomy 15. Należy zmodyfikować definicję, aby zmniejszyć poziom zagnieżdżenia. Dzielenie struktura, Unia lub klasa na dwie lub więcej części za pomocą `typedef` do zdefiniowania co najmniej jednym zagnieżdżonych struktur.