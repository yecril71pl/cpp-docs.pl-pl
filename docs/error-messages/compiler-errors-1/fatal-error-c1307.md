---
title: Błąd krytyczny C1307 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1307
dev_langs:
- C++
helpviewer_keywords:
- C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65f398dd9885c571ea0d66171889f20d3321a3b9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085865"
---
# <a name="fatal-error-c1307"></a>Błąd krytyczny C1307

Program został wyedytowany od czasu zebrania danych profilowych

Korzystając z [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), konsolidator wykryto moduł wejściowy nie kompilowanej po pginstrument, i że moduł został zmieniony w punkcie, w którym istniejące dane profilu nie są już odpowiednie. Na przykład jeśli zmienione wykresu wywołań w module ponownej kompilacji, kompilator wygeneruje C1307.

Aby rozwiązać ten problem, uruchom pginstrument, wykonaj ponownie wszystkie przebiegi testowe i uruchom /LTCG:PGOPTIMIZE. Jeśli nie możesz uruchomić pginstrument i powtórz test wszystkich przebiegów, zamiast /LTCG:PGUPDATE /LTCG:PGOPTIMIZE do utworzenia zoptymalizowanego obrazu.