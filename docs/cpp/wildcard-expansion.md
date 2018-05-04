---
title: Rozwijanie symbolu wieloznacznego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _setargv
dev_langs:
- C++
helpviewer_keywords:
- asterisk wildcard
- _setargv function
- command line [C++], processing arguments
- command line [C++], wildcards
- command-line wildcards
- question mark, wildcard
ms.assetid: 1a543398-607b-4404-93d1-45d290bde638
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bb58d5da479d686cac0d18c9d36e500bd6b5a632
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="wildcard-expansion"></a>Rozwijanie symbolu wieloznacznego
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Można używać symboli wieloznacznych — znak zapytania (?) i gwiazdki (*), aby określić nazwę pliku i ścieżkę argumenty w wierszu polecenia.  
  
 Argumenty wiersza polecenia są obsługiwane przez procedury o nazwie **_setargv —** (lub **_wsetargv** w środowisku znaków dwubajtowych), które domyślnie nie zwiększa symbole wieloznaczne w oddzielnych ciągów w `argv`tablicy ciągów. Aby uzyskać więcej informacji na temat włączania rozwijanie symbolu wieloznacznego, zapoznaj się [rozszerzanie argumentów z symbolami wieloznacznymi](../c-language/expanding-wildcard-arguments.md).  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [main: uruchamianie programu](../cpp/main-program-startup.md)