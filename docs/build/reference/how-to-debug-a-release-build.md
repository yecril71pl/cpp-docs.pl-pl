---
title: 'Porady: debugowanie kompilacji wydania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], release builds
- release builds, debugging
ms.assetid: d333e4d1-4e6c-4384-84a9-cb549702da25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e733375f01d4b2b8ec7090f7f70ad1ec5280cd9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374482"
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