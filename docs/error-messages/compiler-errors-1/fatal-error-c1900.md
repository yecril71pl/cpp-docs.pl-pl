---
title: "Błąd krytyczny C1900 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1900
dev_langs: C++
helpviewer_keywords: C1900
ms.assetid: 3aaa583b-4c1a-45de-aa34-527d806f2cb5
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3b64061401189fb37f28492fbffe1e9941e8aab8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1900"></a>Błąd krytyczny C1900
Niezgodność IL "tool1" "Liczba1" i "tool2" wersja "liczba2"  
  
 Narzędzia uruchamiane w różnych przebiegów kompilator nie są zgodne. ***Liczba1*** i ***liczba2*** odwoływać się do daty na podstawie plików. Na przykład w przebiegu 1, uruchamia zakończenia front kompilatora (c1.dll) i w przebiegu 2, kompilator ponownie uruchamia zakończenia (c2.dll). Dat na podstawie plików muszą być zgodne.  
  
 Aby rozwiązać ten problem, upewnij się, że wszystkie aktualizacje zostały zastosowane do programu Visual Studio. Jeśli problem będzie nadal występować, użyj **programy i funkcje** w Panelu sterowania systemu Windows do naprawy lub ponownej instalacji programu Visual Studio.