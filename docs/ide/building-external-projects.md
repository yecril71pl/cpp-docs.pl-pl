---
title: "Kompilowanie projektów zewnętrznych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- external projects
- Visual C++ projects, external projects
- builds [C++], external projects
- projects [C++], external projects
- Makefile projects, external projects
ms.assetid: 650b7803-ea91-489d-bee3-8f3e990e223c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9f3bd3c7019c98f1be163ee31264b9fef0c52ac5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="building-external-projects"></a>Kompilowanie projektów zewnętrznych
Projekt zewnętrzny jest to projekt Visual C++, korzystającą z pliku reguł programu make lub innych urządzeń znajdujących się poza (obcego lub zewnętrzne względem) środowisko projektowe Visual C++.  
  
 Jeśli projekt zewnętrzny (na przykład projektu pliku reguł programu make) do tworzenia w środowisku projektowym Visual C++, tworzenie projektu pliku reguł programu make i określ projektu tworzenie poleceń i danych wyjściowych w pliku reguł programu make Kreatora aplikacji. Aby uzyskać więcej informacji, zobacz [Tworzenie projektu pliku reguł programu make](../ide/creating-a-makefile-project.md).  
  
 Należy pamiętać, że Visual C++ nie obsługuje już możliwość eksportowania pliku reguł programu make dla aktywnego projektu ze środowiska projektowego. Użyj [przełączniki wiersza polecenia Devenv](/visualstudio/ide/reference/devenv-command-line-switches) do kompilacji projektów Visual Studio w wierszu polecenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilowanie projektów C++ w programie Visual Studio](../ide/building-cpp-projects-in-visual-studio.md)