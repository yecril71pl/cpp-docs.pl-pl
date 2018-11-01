---
title: Błąd krytyczny C1382
ms.date: 11/04/2016
f1_keywords:
- C1382
helpviewer_keywords:
- C1382
ms.assetid: 7a100f8c-3179-4927-a2f1-98de4c753850
ms.openlocfilehash: 2b7f6fd878f0d0ba6cde19a3a316a01c390e954a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50600606"
---
# <a name="fatal-error-c1382"></a>Błąd krytyczny C1382

Plik PCH "file" został przebudowany od "obj" został wygenerowany. Przebuduj ten obiekt

Korzystając z [opcję/LTCG](../../build/reference/ltcg-link-time-code-generation.md), kompilator wykrył pliku .pch, która jest nowsza niż .obj CIL, wskazujące na. Informacje zawarte w pliku .obj CIL jest nieaktualna. Ponownie skompiluj obiektu.

C1382 może również wystąpić, jeśli kompilujesz z opcją **/Yc**, ale również przekazać wielu plików kodu w kompilatorze.  Aby rozwiązać problem, nie należy używać **/Yc** podczas przekazywania wielu plików kodu w kompilatorze.  Aby uzyskać więcej informacji, zobacz [/Yc (Utwórz prekompilowany plik nagłówkowy)](../../build/reference/yc-create-precompiled-header-file.md).