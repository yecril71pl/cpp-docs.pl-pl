---
title: Miejsce definiowania makr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- defining macros
- macros, NMAKE
- NMAKE program, defining macros
ms.assetid: 0fc59ec5-5f58-4644-b7da-7b021f7001af
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c2e646de4cf67fc249d69fb07789f4c8a3e14bf0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="where-to-define-macros"></a>Miejsce definiowania makr
Definiowanie makr w wierszu polecenia, pliku polecenia, pliku reguł programu make lub w pliku Tools.ini.  
  
 W pliku reguł programu make lub plik Tools.ini każdej definicji makra musi występować w osobnym wierszu i nie może zaczynać się od spacji lub kartę. Spacji ani karty wokół znaku równości są ignorowane. Wszystkie [ciąg znaków](../build/defining-an-nmake-macro.md) są literału, łącznie z otaczającego cudzysłowy i spacje.  
  
 W wierszu polecenia lub pliku polecenia spacje i tabulatory argumenty powinny one, a nie całe znaku równości. Jeśli `string` osadzone spacji ani karty, ujmij sam ciąg lub całe makro w podwójny cudzysłów ("").  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie makro NMAKE](../build/defining-an-nmake-macro.md)