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
ms.openlocfilehash: 82bb280036bf8ad1886d2943c3ec3e546c2eaff2
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466179"
---
# <a name="wildcard-expansion"></a>Rozwijanie symbolu wieloznacznego
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Można używać symboli wieloznacznych — znak zapytania (?) i gwiazdki (*), aby określić nazwę pliku i ścieżkę argumenty w wierszu polecenia.  
  
 Argumenty wiersza polecenia są obsługiwane przez procedurę o nazwie `_setargv` (lub `_wsetargv` w środowisku znaków dwubajtowych), które domyślnie nie jest powiększony, symboli wieloznacznych do oddzielnych ciągów w `argv` tablicy ciągów. Aby uzyskać więcej informacji na temat włączania rozszerzenia symboli wieloznacznych, zobacz [rozszerzanie argumentów z symbolami wieloznacznymi](../c-language/expanding-wildcard-arguments.md).  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz także  
 [main: uruchamianie programu](../cpp/main-program-startup.md)