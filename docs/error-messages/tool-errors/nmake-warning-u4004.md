---
title: Ostrzeżenie NMAKE U4004
ms.date: 11/04/2016
f1_keywords:
- U4004
helpviewer_keywords:
- U4004
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
ms.openlocfilehash: 882f6c98b31d23d283f5e8b32b46a46c543b1a76
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298155"
---
# <a name="nmake-warning-u4004"></a>Ostrzeżenie NMAKE U4004

za dużo reguł dla docelowej "targetname"

Określono więcej niż jednego bloku opis dla danego obiektu docelowego przy użyciu pojedynczego dwukropki (**:**) jako separatora. NMAKE wykonywane polecenia w pierwszym bloku opisu i ignorowane nowsze bloków.

Aby określić ten sam element docelowy w wiele zależności, Użyj średników double (`::`) jako separatora w każdym wierszu zależności.