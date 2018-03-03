---
title: 'Porady: debugowanie kompilacji wydania | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], release builds
- release builds, debugging
ms.assetid: d333e4d1-4e6c-4384-84a9-cb549702da25
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 31113d9a5935536ac10b22c7b5f5af27b0d29970
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-debug-a-release-build"></a>Porady: debugowanie kompilacji wydania
Można debugować kompilację wersji aplikacji.  
  
### <a name="to-debug-a-release-build"></a>Debugowanie kompilacji wydania  
  
1.  Otwórz **strony właściwości** okno dialogowe dla projektu. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** węzła. Ustaw **Format informacji debugowania** do [C7 zgodne (/ Z7)](../../build/reference/z7-zi-zi-debug-information-format.md) lub **bazy danych programu (/Zi)**.  
  
3.  Rozwiń węzeł **konsolidatora** i kliknij przycisk **ogólne** węzła. Ustaw **włączenie konsolidowania przyrostowego** do [nr (/ PRZYROSTOWE: NO)](../../build/reference/incremental-link-incrementally.md).  
  
4.  Wybierz **debugowanie** węzła. Ustaw **generowanie informacji o debugowaniu** do [tak (/ DEBUG)](../../build/reference/debug-generate-debug-info.md).  
  
5.  Wybierz **optymalizacji** węzła. Ustaw **odwołania** do [/OPT:REF](../../build/reference/opt-optimizations.md) i **włączyć zwijaniu sekcji COMDAT** do [/OPT: ICF](../../build/reference/opt-optimizations.md).  
  
6.  Teraz można debugować aplikacji wersji kompilacji. Problem, krok za pomocą kodu (lub debugowanie Just In Time Użyj) do momentu znalezienia gdzie występuje błąd, a następnie ustalenie kodu lub niepoprawne parametry.  
  
     Jeśli aplikacja działa w trybie debugowania, ale nie powiedzie się w kompilacji wydania, jeden optymalizacje kompilatora może udostępnianie usterką w kodzie źródłowym. Aby ustalić przyczynę problemu, należy wyłączyć optymalizacje wybrane dla każdego pliku kodu źródłowego do momentu zlokalizowania pliku i optymalizacji, która powoduje problem. (Aby przyspieszyć proces, można podzielić na dwie grupy plików, wyłączysz optymalizacji na jedną grupę i Jeśli napotkasz problem w grupie, nadal dzielenia aż do izolowania pliku problem.)  
  
     Można użyć [/RTC](../../build/reference/rtc-run-time-error-checks.md) próby ujawnia takie błędy w kompilacjach do debugowania.  
  
     Aby uzyskać więcej informacji, zobacz [optymalizacji kodu](../../build/reference/optimizing-your-code.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Naprawianie problemów kompilacji wydania](../../build/reference/fixing-release-build-problems.md)