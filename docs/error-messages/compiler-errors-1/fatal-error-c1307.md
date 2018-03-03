---
title: "Błąd krytyczny C1307 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1307
dev_langs:
- C++
helpviewer_keywords:
- C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fe97f1658a74b0db5985ed755bf387811f2c6d1b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1307"></a>Błąd krytyczny C1307
Program został wyedytowany od czasu zebrania danych profilu  
  
 Korzystając z [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), konsolidator wykryto moduł wejściowy kompilowanej po /LTCG:PGINSTRUMENT i że moduł został zmieniony do punktu, w którym istniejące dane profilu jest już nieaktualny. Na przykład po zmianie wykresu wywołań w module ponownej kompilacji, kompilator wygeneruje C1307.  
  
 Aby rozwiązać ten problem, uruchom /LTCG:PGINSTRUMENT, wykonaj ponownie wszystkie uruchomień testów i uruchom /LTCG:PGOPTIMIZE. Jeśli nie możesz uruchomić /LTCG:PGINSTRUMENT i powtórz test wszystkie działa, należy użyć /LTCG:PGUPDATE zamiast /LTCG:PGOPTIMIZE do utworzenia zoptymalizowanego obrazu.