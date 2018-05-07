---
title: Błąd krytyczny NMAKE U1095 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1095
dev_langs:
- C++
helpviewer_keywords:
- U1095
ms.assetid: a392582b-06db-4568-9c13-450293a4fbda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13c819d18149e61bca71f6a4cb10ea851a2d485d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-fatal-error-u1095"></a>Błąd krytyczny NMAKE U1095
rozwinięty wiersz polecenia "commandline" zbyt długa  
  
 Po rozwinięciu makra podanego wiersza polecenia przekroczyła limit długości wierszy poleceń do systemu operacyjnego.  
  
 MS-DOS zezwala na maksymalnie 128 znaków w wierszu polecenia.  
  
 W przypadku polecenia dla programu, który może zaakceptować wprowadzania wiersza polecenia z pliku, zmień polecenie, a następnie podaj dane wejściowe z pliku na dysku lub pliku wbudowanego. Na przykład LINK i LIB akceptuje dane wejściowe z pliku odpowiedzi.