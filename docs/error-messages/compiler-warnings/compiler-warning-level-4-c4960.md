---
title: "Kompilatora (poziom 4) ostrzeżenie C4960 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4960
dev_langs: C++
helpviewer_keywords: C4960
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 160ae5a50d55ab0ebc89335aa3951aa781175feb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4960"></a>Kompilator C4960 ostrzegawcze (poziom 4)
"Funkcja" jest zbyt duży, aby zostać profilowanym  
  
 Korzystając z [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), kompilator wykryto wejściowych modułu przy użyciu funkcji większy niż 65 535 instrukcje. Duże funkcja nie jest dostępna dla optymalizacji sterowanych profilem.  
  
 Aby usunąć to ostrzeżenie, Zmniejsz rozmiar funkcji.