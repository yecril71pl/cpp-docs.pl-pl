---
title: Ostrzeżenie NMAKE U4004
ms.date: 11/04/2016
f1_keywords:
- U4004
helpviewer_keywords:
- U4004
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
ms.openlocfilehash: 882f6c98b31d23d283f5e8b32b46a46c543b1a76
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436221"
---
# <a name="nmake-warning-u4004"></a>Ostrzeżenie NMAKE U4004

za dużo reguł dla docelowej "targetname"

Określono więcej niż jednego bloku opis dla danego obiektu docelowego przy użyciu pojedynczego dwukropki (**:**) jako separatora. NMAKE wykonywane polecenia w pierwszym bloku opisu i ignorowane nowsze bloków.

Aby określić ten sam element docelowy w wiele zależności, Użyj średników double (`::`) jako separatora w każdym wierszu zależności.