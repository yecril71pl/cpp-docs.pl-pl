---
title: Ostrzeżenie NMAKE U4004
ms.date: 11/04/2016
f1_keywords:
- U4004
helpviewer_keywords:
- U4004
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
ms.openlocfilehash: d59b5656d76025fa56bfc76bad800659f25acf53
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193202"
---
# <a name="nmake-warning-u4004"></a>Ostrzeżenie NMAKE U4004

zbyt wiele reguł dla elementu docelowego "TargetName"

Określono więcej niż jeden blok opisu dla danego obiektu docelowego przy użyciu pojedynczych dwukropków ( **:** ) jako separatorów. NMAKE wykonał polecenia w pierwszym bloku opisu i zignorował późniejsze bloki.

Aby określić ten sam element docelowy w wielu zależnościach, użyj podwójnego dwukropka (`::`) jako separatora w każdej linii zależności.
