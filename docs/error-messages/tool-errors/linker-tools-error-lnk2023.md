---
title: Błąd narzędzi konsolidatora LNK2023 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2023
dev_langs:
- C++
helpviewer_keywords:
- LNK2023
ms.assetid: c99e35a8-739a-4a20-a715-29b8c3744703
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7d8deaf8bfb10d3ceb56380560320ebb2cf9a7b8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090324"
---
# <a name="linker-tools-error-lnk2023"></a>Błąd narzędzi konsolidatora LNK2023

Zły biblioteki dll lub punkt wejścia \<biblioteki dll lub punkt wejście >

Konsolidator ładuje nieprawidłową wersję msobj90.dll. Upewnij się, że link.exe i msobj90.dll w ścieżce mają tę samą wersję.

Zależność msobj90.dll nie może być obecny. Na liście zależności dla msobj90.dll jest:

- Msvcr90.dll

- Kernel32.dll.

Sprawdź swojej maszyny, wszelkie pozostałe kopie msobj90.dll, które mogą być nieaktualne.