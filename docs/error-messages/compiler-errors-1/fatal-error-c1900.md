---
title: Błąd krytyczny C1900 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1900
dev_langs:
- C++
helpviewer_keywords:
- C1900
ms.assetid: 3aaa583b-4c1a-45de-aa34-527d806f2cb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da7cdd5601785f43748ec87d3219f43728536855
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1900"></a>Błąd krytyczny C1900
Niezgodność IL "tool1" "Liczba1" i "tool2" wersja "liczba2"  
  
 Narzędzia uruchamiane w różnych przebiegów kompilator nie są zgodne. ***Liczba1*** i ***liczba2*** odwoływać się do daty na podstawie plików. Na przykład w przebiegu 1, uruchamia zakończenia front kompilatora (c1.dll) i w przebiegu 2, kompilator ponownie uruchamia zakończenia (c2.dll). Dat na podstawie plików muszą być zgodne.  
  
 Aby rozwiązać ten problem, upewnij się, że wszystkie aktualizacje zostały zastosowane do programu Visual Studio. Jeśli problem będzie nadal występować, użyj **programy i funkcje** w Panelu sterowania systemu Windows do naprawy lub ponownej instalacji programu Visual Studio.