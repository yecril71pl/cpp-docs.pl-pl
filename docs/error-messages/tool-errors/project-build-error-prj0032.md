---
title: "Błąd PRJ0032 kompilacji projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0032
dev_langs: C++
helpviewer_keywords: PRJ0032
ms.assetid: bc6acbea-4041-4237-8b5a-f0434705d89f
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c3ea007346793f8d06ac85f20649b7d348014e17
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="project-build-error-prj0032"></a>Błąd PRJ0032 kompilacji projektu
Właściwość 'Wyniki' dla projektów na poziomie niestandardowego kroku kompilacji zawarte makra, który ewaluowane jest jako "macro_expansion".  
  
 Niestandardowego kroku kompilacji w projekcie mają nieprawidłowe dane wyjściowe prawdopodobnie z powodu problemu ocena makra. Ten błąd może również oznaczać czy ścieżka jest nieprawidłowo sformułowany, zawierające znaki lub kombinacji znaków, które są niedozwolone w ścieżce pliku.  
  
 Aby rozwiązać ten problem, Usuń makro lub usuń specyfikacji ścieżki. Obliczane ścieżka jest ścieżką bezwzględną od katalogu projektu.