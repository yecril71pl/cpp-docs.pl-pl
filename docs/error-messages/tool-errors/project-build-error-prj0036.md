---
title: Błąd PRJ0036 kompilacji projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0036
dev_langs:
- C++
helpviewer_keywords:
- PRJ0036
ms.assetid: ee215cd1-2d66-474d-9a63-b9096f1c4923
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55ca9c282cbf36111bbc6b5d4316745508ccbb0c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317352"
---
# <a name="project-build-error-prj0036"></a>Błąd PRJ0036 kompilacji projektu
Właściwość 'Dodatkowe pliki' narzędzia wdrażania Web zawiera niepoprawny wpis.  
  
 Właściwość dodatkowe pliki na stronie właściwości sieci Web Deployment zawiera błąd, prawdopodobnie z powodu problemu ocena makra. Ten błąd może również oznaczać czy ścieżka jest nieprawidłowo sformułowany, zawierające znaki lub kombinacji znaków, które są niedozwolone w ścieżce pliku.  
  
 Aby rozwiązać ten problem, Usuń makro lub usuń specyfikacji ścieżki. Obliczane ścieżka jest ścieżką bezwzględną od katalogu projektu.  
  
 Ten błąd może również oznaczać jeden z plików, do których odwołuje się nie istnieje.