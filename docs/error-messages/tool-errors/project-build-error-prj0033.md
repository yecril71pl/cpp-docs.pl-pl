---
title: "Błąd PRJ0033 kompilacji projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0033
dev_langs: C++
helpviewer_keywords: PRJ0033
ms.assetid: 84d4a052-0586-4b78-9315-81c1e8386c1e
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ab3cd4cdac74e7c64bfd786beb7aab147d5cdd82
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="project-build-error-prj0033"></a>Błąd PRJ0033 kompilacji projektu
Właściwość 'Dodatkowe zależności' dla niestandardowej kompilacji kroku dla pliku 'Plik' zawiera 'makra"co ewaluowane"macro_expansion".  
  
 Niestandardowego kroku kompilacji na plik zawiera błąd w jego dodatkowe zależności, prawdopodobnie z powodu problemu ocena makra. Ten błąd może również oznaczać czy ścieżka jest nieprawidłowo sformułowany, zawierające znaki lub kombinacji znaków, które są niedozwolone w ścieżce pliku.  
  
 Aby rozwiązać ten problem, Usuń makro lub usuń specyfikacji ścieżki. Obliczane ścieżka jest ścieżką bezwzględną od katalogu projektu.