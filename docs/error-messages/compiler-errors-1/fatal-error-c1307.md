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
ms.openlocfilehash: 9d06ce51ada7cd9159b8e02ff627bf12ebb7293d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33227138"
---
# <a name="fatal-error-c1307"></a>Błąd krytyczny C1307
Program został wyedytowany od czasu zebrania danych profilu  
  
 Korzystając z [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), konsolidator wykryto moduł wejściowy kompilowanej po /LTCG:PGINSTRUMENT i że moduł został zmieniony do punktu, w którym istniejące dane profilu jest już nieaktualny. Na przykład po zmianie wykresu wywołań w module ponownej kompilacji, kompilator wygeneruje C1307.  
  
 Aby rozwiązać ten problem, uruchom /LTCG:PGINSTRUMENT, wykonaj ponownie wszystkie uruchomień testów i uruchom /LTCG:PGOPTIMIZE. Jeśli nie możesz uruchomić /LTCG:PGINSTRUMENT i powtórz test wszystkie działa, należy użyć /LTCG:PGUPDATE zamiast /LTCG:PGOPTIMIZE do utworzenia zoptymalizowanego obrazu.