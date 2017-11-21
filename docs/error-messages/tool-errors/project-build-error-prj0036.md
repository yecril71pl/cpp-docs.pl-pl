---
title: "Błąd PRJ0036 kompilacji projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0036
dev_langs: C++
helpviewer_keywords: PRJ0036
ms.assetid: ee215cd1-2d66-474d-9a63-b9096f1c4923
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3bf9af905b2f76c816b21eea70fde5e93aae543b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="project-build-error-prj0036"></a>Błąd PRJ0036 kompilacji projektu
Właściwość 'Dodatkowe pliki' narzędzia wdrażania Web zawiera niepoprawny wpis.  
  
 Właściwość dodatkowe pliki na stronie właściwości sieci Web Deployment zawiera błąd, prawdopodobnie z powodu problemu ocena makra. Ten błąd może również oznaczać czy ścieżka jest nieprawidłowo sformułowany, zawierające znaki lub kombinacji znaków, które są niedozwolone w ścieżce pliku.  
  
 Aby rozwiązać ten problem, Usuń makro lub usuń specyfikacji ścieżki. Obliczane ścieżka jest ścieżką bezwzględną od katalogu projektu.  
  
 Ten błąd może również oznaczać jeden z plików, do których odwołuje się nie istnieje.