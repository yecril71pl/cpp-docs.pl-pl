---
title: Miejsce definiowania makr | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- defining macros
- macros, NMAKE
- NMAKE program, defining macros
ms.assetid: 0fc59ec5-5f58-4644-b7da-7b021f7001af
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cfb17f531df5c232f1f376cd003acb7bf5a62206
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="where-to-define-macros"></a>Miejsce definiowania makr
Definiowanie makr w wierszu polecenia, pliku polecenia, pliku reguł programu make lub w pliku Tools.ini.  
  
 W pliku reguł programu make lub plik Tools.ini każdej definicji makra musi występować w osobnym wierszu i nie może zaczynać się od spacji lub kartę. Spacji ani karty wokół znaku równości są ignorowane. Wszystkie [ciąg znaków](../build/defining-an-nmake-macro.md) są literału, łącznie z otaczającego cudzysłowy i spacje.  
  
 W wierszu polecenia lub pliku polecenia spacje i tabulatory argumenty powinny one, a nie całe znaku równości. Jeśli `string` osadzone spacji ani karty, ujmij sam ciąg lub całe makro w podwójny cudzysłów ("").  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie makro NMAKE](../build/defining-an-nmake-macro.md)