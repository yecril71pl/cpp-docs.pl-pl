---
title: "Błąd PRJ0024 kompilacji projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- PRJ0024
dev_langs:
- C++
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2cf9ad974856f132599932a32b954e50453adf56
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0024"></a>Błąd PRJ0024 kompilacji projektu
Ścieżka Unikodowa 'path' nie mogą być przekonwertowana na stronę kodową ANSI użytkownika.  
  
 ***ścieżka*** jest z oryginalną wersją ciąg ścieżki Unicode. Ten błąd może wystąpić w przypadku braku ścieżki Unicode, której nie można bezpośrednio przetłumaczenia na ANSI na bieżącej stronie kodowej systemu.  
  
 Ten błąd może wystąpić, jeśli pracujesz z projektu, który został opracowany w systemie za pomocą stronę kodową, która nie znajduje się na tym komputerze.  
  
 Rozwiązanie dotyczące tego błędu jest zaktualizuj ścieżkę do tekst ANSI lub do Zainstaluj stronę kodową na komputerze i ustaw go jako domyślnego systemu.