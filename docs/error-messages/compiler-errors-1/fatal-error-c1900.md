---
title: "Błąd krytyczny C1900 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1900
dev_langs:
- C++
helpviewer_keywords:
- C1900
ms.assetid: 3aaa583b-4c1a-45de-aa34-527d806f2cb5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7bffc4c0a60b90ca7eb5f71f3457cced3ec64569
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1900"></a>Błąd krytyczny C1900
Niezgodność IL "tool1" "Liczba1" i "tool2" wersja "liczba2"  
  
 Narzędzia uruchamiane w różnych przebiegów kompilator nie są zgodne. ***Liczba1*** i ***liczba2*** odwoływać się do daty na podstawie plików. Na przykład w przebiegu 1, uruchamia zakończenia front kompilatora (c1.dll) i w przebiegu 2, kompilator ponownie uruchamia zakończenia (c2.dll). Dat na podstawie plików muszą być zgodne.  
  
 Aby rozwiązać ten problem, upewnij się, że wszystkie aktualizacje zostały zastosowane do programu Visual Studio. Jeśli problem będzie nadal występować, użyj **programy i funkcje** w Panelu sterowania systemu Windows do naprawy lub ponownej instalacji programu Visual Studio.