---
title: "Błąd krytyczny C1307 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1307
dev_langs: C++
helpviewer_keywords: C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1173f538f02e8178d523bb51476b4a10427099ea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1307"></a>Błąd krytyczny C1307
Program został wyedytowany od czasu zebrania danych profilu  
  
 Korzystając z [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), konsolidator wykryto moduł wejściowy kompilowanej po /LTCG:PGINSTRUMENT i że moduł został zmieniony do punktu, w którym istniejące dane profilu jest już nieaktualny. Na przykład po zmianie wykresu wywołań w module ponownej kompilacji, kompilator wygeneruje C1307.  
  
 Aby rozwiązać ten problem, uruchom /LTCG:PGINSTRUMENT, wykonaj ponownie wszystkie uruchomień testów i uruchom /LTCG:PGOPTIMIZE. Jeśli nie możesz uruchomić /LTCG:PGINSTRUMENT i powtórz test wszystkie działa, należy użyć /LTCG:PGUPDATE zamiast /LTCG:PGOPTIMIZE do utworzenia zoptymalizowanego obrazu.