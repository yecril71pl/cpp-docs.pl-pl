---
title: Błąd narzędzi konsolidatora LNK2023
ms.date: 11/04/2016
f1_keywords:
- LNK2023
helpviewer_keywords:
- LNK2023
ms.assetid: c99e35a8-739a-4a20-a715-29b8c3744703
ms.openlocfilehash: c5bc70aeb3a7e39bc60bb745060e7a5740ad7a28
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386307"
---
# <a name="linker-tools-error-lnk2023"></a>Błąd narzędzi konsolidatora LNK2023

Zły biblioteki dll lub punkt wejścia \<biblioteki dll lub punkt wejście >

Konsolidator ładuje nieprawidłową wersję msobj90.dll. Upewnij się, że link.exe i msobj90.dll w ścieżce mają tę samą wersję.

Zależność msobj90.dll nie może być obecny. Na liście zależności dla msobj90.dll jest:

- Msvcr90.dll

- Kernel32.dll

Sprawdź swojej maszyny, wszelkie pozostałe kopie msobj90.dll, które mogą być nieaktualne.