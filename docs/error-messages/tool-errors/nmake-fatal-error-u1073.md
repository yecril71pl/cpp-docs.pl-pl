---
title: Błąd krytyczny NMAKE U1073
ms.date: 11/04/2016
f1_keywords:
- U1073
helpviewer_keywords:
- U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
ms.openlocfilehash: 97d44594540d18bf008757506a9e36e6d16d2cd7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182698"
---
# <a name="nmake-fatal-error-u1073"></a>Błąd krytyczny NMAKE U1073

nie wiadomo, jak utworzyć element "TargetName"

Określony element docelowy nie istnieje i nie ma polecenia do wykonania lub wnioskowania o zastosowanie reguły.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać ten problem, można użyć następujących rozwiązań

1. Sprawdź pisownię nazwy docelowej.

1. Jeśli *TargetName* jest pseudotarget, określ ją jako element docelowy w innym bloku opisu.

1. Jeśli *TargetName* jest wywołaniem makra, upewnij się, że nie jest rozwinięty do pustego ciągu.
