---
title: Ostrzeżenie NMAKE U4004 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U4004
dev_langs:
- C++
helpviewer_keywords:
- U4004
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a89bb8abf212c8a0ffa9fb40fe5d3ea43307a08
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016653"
---
# <a name="nmake-warning-u4004"></a>Ostrzeżenie NMAKE U4004

za dużo reguł dla docelowej "targetname"

Określono więcej niż jednego bloku opis dla danego obiektu docelowego przy użyciu pojedynczego dwukropki (**:**) jako separatora. NMAKE wykonywane polecenia w pierwszym bloku opisu i ignorowane nowsze bloków.

Aby określić ten sam element docelowy w wiele zależności, Użyj średników double (`::`) jako separatora w każdym wierszu zależności.