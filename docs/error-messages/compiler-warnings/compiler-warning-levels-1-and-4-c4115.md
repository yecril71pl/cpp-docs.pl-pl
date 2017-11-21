---
title: "Kompilator C4115 ostrzeżenie (poziomy 1 i 4) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4115
dev_langs: C++
helpviewer_keywords: C4115
ms.assetid: f3f94e72-fc49-4d09-b3e7-23d68e61152f
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a0430aae30c3a9c25b9b7fd96651a82719d9068a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-levels-1-and-4-c4115"></a>Kompilator C4115 ostrzeżenie (poziomy 1 i 4)
'type': nazwana definicja typu w nawiasach  
  
 Dany symbol jest używany do definiowania struktury, Unią lub typ wyliczeniowy wewnątrz wyrażenia w nawiasach. Zakres definicji może być nieoczekiwany.  
  
 W wywołaniu funkcji C definicja ma zasięg globalny. W wywołaniu C++ definicji jest tym samym zakresie co wywołanie funkcji.  
  
 To ostrzeżenie może być również spowodowane deklaratorów wewnątrz nawiasów (na przykład prototypy), które nie są wyrażenia w nawiasach.  
  
 Jest to ostrzeżenia poziomu 1 z programami C++ i C — programy opracowane w ramach zgodność ANSI (/Za). W przeciwnym razie jest poziom 3.