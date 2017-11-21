---
title: "Kompilatora (poziom 1) ostrzeżenie C4729 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4729
dev_langs: C++
helpviewer_keywords: C4729
ms.assetid: 36a0151f-f258-48d9-9444-ae6d41ff70a4
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2d80512dd6aaecfbe1de06f69303eb3d42213856
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4729"></a>Kompilator C4729 ostrzegawcze (poziom 1)
Funkcja za duża dla przepływu wykres na podstawie ostrzeżenia  
  
 To ostrzeżenie jest generowany, gdy funkcja jest zbyt duży, aby być kompilowana przy użyciu niezawodnych sprawdzanie sytuacji generujących ostrzeżenia. To ostrzeżenie jest tylko generowane, gdy [/Od](../../build/reference/od-disable-debug.md) — opcja kompilatora używane.  
  
 Aby usunąć to ostrzeżenie, Podziel funkcji na mniejsze funkcji.