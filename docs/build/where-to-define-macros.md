---
title: Miejsce definiowania makr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- defining macros
- macros, NMAKE
- NMAKE program, defining macros
ms.assetid: 0fc59ec5-5f58-4644-b7da-7b021f7001af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9cf3e87a50362c770d45f00c4dc17ac3d264f611
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380917"
---
# <a name="where-to-define-macros"></a>Miejsce definiowania makr
Definiowanie makr w wierszu polecenia, pliku polecenia, pliku reguł programu make lub w pliku Tools.ini.  
  
 W pliku reguł programu make lub plik Tools.ini każdej definicji makra musi występować w osobnym wierszu i nie może zaczynać się od spacji lub kartę. Spacji ani karty wokół znaku równości są ignorowane. Wszystkie [ciąg znaków](../build/defining-an-nmake-macro.md) są literału, łącznie z otaczającego cudzysłowy i spacje.  
  
 W wierszu polecenia lub pliku polecenia spacje i tabulatory argumenty powinny one, a nie całe znaku równości. Jeśli `string` osadzone spacji ani karty, ujmij sam ciąg lub całe makro w podwójny cudzysłów ("").  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie makro NMAKE](../build/defining-an-nmake-macro.md)