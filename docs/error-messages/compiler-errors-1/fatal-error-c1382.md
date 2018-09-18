---
title: Błąd krytyczny C1382 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1382
dev_langs:
- C++
helpviewer_keywords:
- C1382
ms.assetid: 7a100f8c-3179-4927-a2f1-98de4c753850
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3a5a6ce312c5ef886ef25e8de46e6d3376eded2e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030659"
---
# <a name="fatal-error-c1382"></a>Błąd krytyczny C1382

Plik PCH "file" został przebudowany od "obj" został wygenerowany. Przebuduj ten obiekt

Korzystając z [opcję/LTCG](../../build/reference/ltcg-link-time-code-generation.md), kompilator wykrył pliku .pch, która jest nowsza niż .obj CIL, wskazujące na. Informacje zawarte w pliku .obj CIL jest nieaktualna. Ponownie skompiluj obiektu.

C1382 może również wystąpić, jeśli kompilujesz z opcją **/Yc**, ale również przekazać wielu plików kodu w kompilatorze.  Aby rozwiązać problem, nie należy używać **/Yc** podczas przekazywania wielu plików kodu w kompilatorze.  Aby uzyskać więcej informacji, zobacz [/Yc (Utwórz prekompilowany plik nagłówkowy)](../../build/reference/yc-create-precompiled-header-file.md).