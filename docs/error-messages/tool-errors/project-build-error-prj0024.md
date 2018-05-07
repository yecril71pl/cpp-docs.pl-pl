---
title: Błąd PRJ0024 kompilacji projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0024
dev_langs:
- C++
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 59bf76aba80093bf9e8e653bdfb9fad49687a501
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="project-build-error-prj0024"></a>Błąd PRJ0024 kompilacji projektu
Ścieżka Unikodowa 'path' nie mogą być przekonwertowana na stronę kodową ANSI użytkownika.  
  
 ***ścieżka*** jest z oryginalną wersją ciąg ścieżki Unicode. Ten błąd może wystąpić w przypadku braku ścieżki Unicode, której nie można bezpośrednio przetłumaczenia na ANSI na bieżącej stronie kodowej systemu.  
  
 Ten błąd może wystąpić, jeśli pracujesz z projektu, który został opracowany w systemie za pomocą stronę kodową, która nie znajduje się na tym komputerze.  
  
 Rozwiązanie dotyczące tego błędu jest zaktualizuj ścieżkę do tekst ANSI lub do Zainstaluj stronę kodową na komputerze i ustaw go jako domyślnego systemu.