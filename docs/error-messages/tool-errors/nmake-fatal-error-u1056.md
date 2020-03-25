---
title: Błąd krytyczny NMAKE U1056
ms.date: 11/04/2016
f1_keywords:
- U1056
helpviewer_keywords:
- U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
ms.openlocfilehash: 10131e518fa608292fff58672ede36390bcd665b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182906"
---
# <a name="nmake-fatal-error-u1056"></a>Błąd krytyczny NMAKE U1056

nie można znaleźć procesora poleceń

Procesor poleceń nie znajduje się w ścieżce określonej w zmiennych środowiskowych **wywołana** lub **Path** .

NMAKE używa COMMAND.COM lub CMD. EXE jako procesor poleceń podczas wykonywania poleceń. Szuka najpierw procesora poleceń w ścieżce ustawionej w **wywołana**. Jeśli **wywołana** nie istnieje, NMAKE Przeszukuje katalogi określone w polu **ścieżka**.
