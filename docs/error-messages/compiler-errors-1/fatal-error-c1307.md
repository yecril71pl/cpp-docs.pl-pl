---
title: Błąd krytyczny C1307
ms.date: 11/04/2016
f1_keywords:
- C1307
helpviewer_keywords:
- C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
ms.openlocfilehash: c7eb90c8e17408f6898ef7ff1a9d9e5efcafb4fa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203349"
---
# <a name="fatal-error-c1307"></a>Błąd krytyczny C1307

Program został wyedytowany od czasu zebrania danych profilowych

W przypadku korzystania z [/LTCG: PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md)konsolidator wykrył Moduł wejściowy, który został ponownie skompilowany po/LTCG: PGINSTRUMENT i że moduł został zmieniony do punktu, w którym istniejące dane profilowe nie są już ważne. Na przykład, jeśli wykres wywołań został zmieniony w module rekompilowanym, kompilator wygeneruje C1307.

Aby rozwiązać ten problem, Uruchom/LTCG: PGINSTRUMENT, ponów wszystkie przebiegi testowe i Uruchom/LTCG: PGOPTIMIZE. Jeśli nie możesz uruchomić/LTCG: PGINSTRUMENT i wykonaj ponownie wszystkie przebiegi testowe, użyj/LTCG: PGUPDATE zamiast/LTCG: PGOPTIMIZE w celu utworzenia zoptymalizowanego obrazu.
