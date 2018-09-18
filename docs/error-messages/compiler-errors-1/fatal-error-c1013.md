---
title: Błąd krytyczny C1013 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1013
dev_langs:
- C++
helpviewer_keywords:
- C1013
ms.assetid: 5514a679-efe7-4055-bdd3-5693ca0c332f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33c10062cac83984fb1c68835780497b89c4cbc1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050524"
---
# <a name="fatal-error-c1013"></a>Błąd krytyczny C1013

ograniczenie kompilatora: zbyt wiele otwartych nawiasów

Wyrażenie zawiera zbyt wiele poziomów nawiasów w jednym wyrażeniu. Uprość wyrażenie lub podzielenie go na wiele instrukcji.

Przed Visual C++ 6.0 dodatek Service Pack 3 limit zagnieżdżone nawiasy w jednym wyrażeniu był 59. Obecnie limit zagnieżdżone nawiasy to 256.