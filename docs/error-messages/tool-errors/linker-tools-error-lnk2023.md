---
title: Błąd narzędzi konsolidatora LNK2023
ms.date: 11/04/2016
f1_keywords:
- LNK2023
helpviewer_keywords:
- LNK2023
ms.assetid: c99e35a8-739a-4a20-a715-29b8c3744703
ms.openlocfilehash: 363b6ef0ea9991ff5d657044282e99c558257fb9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194632"
---
# <a name="linker-tools-error-lnk2023"></a>Błąd narzędzi konsolidatora LNK2023

Nieprawidłowa Biblioteka DLL lub punkt wejścia \<dll lub punktu wejścia >

Konsolidator ładuje niepoprawną wersję msobj90. dll. Upewnij się, że link. exe i msobj90. dll w ścieżce mają tę samą wersję.

Zależność msobj90. dll może nie być obecna. Lista zależności dla msobj90. dll jest:

- Msvcr90.dll

- Kernel32.dll

Sprawdź, czy na maszynie istnieje inna kopia msobj90. dll, która może być nieaktualna.
