---
title: Unicode w MFC | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- wide characters, Unicode
- Unicode [MFC], MFC
- wide characters, encoding
- strings [MFC], Unicode
- Unicode [MFC], enabling
ms.assetid: 1002004b-4113-4380-bf63-e1570934b793
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2c1a104ffc30a7463d640f63d26f7a80faad333b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="unicode-in-mfc"></a>Format Unicode w MFC
MFC obsługuje Unicode standard dla kodowania znaki dwubajtowe na platformach Windows NT, Windows 2000 i Windows XP. Unicode nie mogą być uruchomione na platformach Windows 98.  
  
 Wersje biblioteki MFC Unicode są opisane poniżej:  
  
### <a name="static-link-libraries"></a>Biblioteki statyczne  
  
|Wydanie|Debugowanie|Opis|  
|-------------|-----------|-----------------|  
|UAFXCW.lib, .pdb|UAFXCWD.lib, .pdb|Biblioteki dołączanej statycznie Unicode MFC|  
  
### <a name="dynamic-link-libraries"></a>Biblioteki dll  
  
|Wydanie|Debugowanie|Opis|  
|-------------|-----------|-----------------|  
|MFC100U.lib, .dbg, def, dll, .map, .pdb, .prf|MFC100UD.lib, .def, dll, .map, .pdb|Importowanie Unicode MFC biblioteki (zobacz uwagi poniżej wyjaśnienie rozszerzeń nazw plików)|  
|MFCS100U.lib, .pdb|MFCS100UD.lib, .pdb|Biblioteka zawierająca kod, który musi być statycznie połączone w aplikacji lub biblioteki DLL zaimportować Unicode MFC|  
  
 **Typy plików**  
  
-   Import biblioteki pliki mają rozszerzenie (lib).  
  
-   Biblioteka dołączana dynamicznie pliki mają rozszerzenie (.dll).  
  
-   Pliki definicji (.def) modułu są pliki tekstowe, które zawierają instrukcje określania .exe lub .dll.  
  
-   Plików map (.map) są plikami tekstowymi, które zawierają informacje, które konsolidator używa podczas łączenia programu.  
  
-   Pliki biblioteki (lib) są używane w połączeniu z wersjami biblioteki DLL MFC. Te pliki zawierają kod, który musi być statycznie połączone w aplikacji lub DLL.  
  
-   Pliki bazy danych (.pdb) program zawiera informacje o stanie debugowania i projektu.  
  
-   Pliki debugowania (.dbg) zawierają informacje (COFF FPO i CodeView), który używa debuger programu Visual C++.  
  
 Szczegółowe informacje na temat konwencji nazewnictwa, zobacz [konwencje nazewnictwa bibliotek](../mfc/library-naming-conventions.md).  
  
 Informacje o używaniu Unicode z MFC, zobacz [ciągów: Obsługa ustawić znaków wielobajtowych (MBCS) i Unicode](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../mfc/mfc-concepts.md)   
 [Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)

