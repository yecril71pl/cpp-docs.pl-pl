---
title: Błąd krytyczny NMAKE U1056 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1056
dev_langs:
- C++
helpviewer_keywords:
- U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e0a83c62bedf995708d5e99fee19f05696d05c2d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065702"
---
# <a name="nmake-fatal-error-u1056"></a>Błąd krytyczny NMAKE U1056

Nie można znaleźć procesora poleceń

Procesor poleceń nie znajdowała się w ścieżce określonej w **COMSPEC** lub **ścieżki** zmiennych środowiskowych.

NMAKE używa COMMAND.COM lub CMD. EXE jako podmiot przetwarzający polecenia podczas wykonywania polecenia. Szuka procesora poleceń najpierw w ścieżce w **COMSPEC**. Jeśli **COMSPEC** nie istnieje, NMAKE wyszukiwania katalogów określonych w **ścieżki**.