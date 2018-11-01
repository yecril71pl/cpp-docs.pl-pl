---
title: Błąd krytyczny C1307
ms.date: 11/04/2016
f1_keywords:
- C1307
helpviewer_keywords:
- C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
ms.openlocfilehash: 1acdda77ac9cbf8d99752de3b78ab9c32bbb4cbc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552272"
---
# <a name="fatal-error-c1307"></a>Błąd krytyczny C1307

Program został wyedytowany od czasu zebrania danych profilowych

Korzystając z [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), konsolidator wykryto moduł wejściowy nie kompilowanej po pginstrument, i że moduł został zmieniony w punkcie, w którym istniejące dane profilu nie są już odpowiednie. Na przykład jeśli zmienione wykresu wywołań w module ponownej kompilacji, kompilator wygeneruje C1307.

Aby rozwiązać ten problem, uruchom pginstrument, wykonaj ponownie wszystkie przebiegi testowe i uruchom /LTCG:PGOPTIMIZE. Jeśli nie możesz uruchomić pginstrument i powtórz test wszystkich przebiegów, zamiast /LTCG:PGUPDATE /LTCG:PGOPTIMIZE do utworzenia zoptymalizowanego obrazu.