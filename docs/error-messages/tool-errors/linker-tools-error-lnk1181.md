---
title: "Błąd narzędzi konsolidatora LNK1181 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1181
dev_langs: C++
helpviewer_keywords: LNK1181
ms.assetid: 984b0db6-e331-4284-b2a7-a212fe96c486
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8f5092d4f3ce7b4f96ca4dc5c1554483a7fc3a0b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1181"></a>Błąd narzędzi konsolidatora LNK1181
Nie można otworzyć pliku wejściowego "filename"  
  
 Nie można odnaleźć konsolidator `filename` , ponieważ nie istnieje lub nie odnaleziono ścieżki.  
  
 Niektóre typowe przyczyny błędu LNK1181 obejmują:  
  
-   `filename`jest określany jako dodatkowe zależności w linii konsolidatora, ale plik nie istnieje.  
  
-   A **/libpath** instrukcji, która określa katalog zawierający `filename` brakuje.  
  
 Aby rozwiązać problemy z powyższych, upewnij się, że wszystkie odwołania do wiersza konsolidatora pliki są obecne w systemie.  Upewnij się również jest **/libpath** instrukcji dla każdego katalogu zawierającego plik zależny od konsolidatora.  
  
 Inną możliwą przyczyną LNK1181 jest, że długiej nazwy pliku ze spacjami nie został ujęty w cudzysłów.  W takim przypadku tylko rozpozna nazwę pliku do pierwszego obszaru konsolidator i Załóż, że rozszerzenie pliku. obiektu  Rozwiązaniem tej sytuacji jest ujmij długa nazwa pliku (nazwa ścieżki plus pliku) w znaki cudzysłowu.  
  
 Aby uzyskać więcej informacji, zobacz [pliki .lib — wejście konsolidatora](../../build/reference/dot-lib-files-as-linker-input.md).  
  
## <a name="see-also"></a>Zobacz też  
 [/LIBPATH (Dodatkowa Libpath)](../../build/reference/libpath-additional-libpath.md)