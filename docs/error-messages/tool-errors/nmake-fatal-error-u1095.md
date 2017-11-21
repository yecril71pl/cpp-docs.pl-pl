---
title: "Błąd krytyczny NMAKE U1095 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1095
dev_langs: C++
helpviewer_keywords: U1095
ms.assetid: a392582b-06db-4568-9c13-450293a4fbda
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 866975d84f570691f226f2130a2b4324af322b2f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="nmake-fatal-error-u1095"></a>Błąd krytyczny NMAKE U1095
rozwinięty wiersz polecenia "commandline" zbyt długa  
  
 Po rozwinięciu makra podanego wiersza polecenia przekroczyła limit długości wierszy poleceń do systemu operacyjnego.  
  
 MS-DOS zezwala na maksymalnie 128 znaków w wierszu polecenia.  
  
 W przypadku polecenia dla programu, który może zaakceptować wprowadzania wiersza polecenia z pliku, zmień polecenie, a następnie podaj dane wejściowe z pliku na dysku lub pliku wbudowanego. Na przykład LINK i LIB akceptuje dane wejściowe z pliku odpowiedzi.