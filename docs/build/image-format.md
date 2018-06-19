---
title: Format obrazu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 3ca3654b-42fe-4253-9f2e-723644041aa0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 356480333a62d998213726016f3940b318c218a0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367943"
---
# <a name="image-format"></a>Format obrazu
Format obrazu wykonywalnego jest plikiem PE32 +. Obrazy wykonywalne (dll i exe) są ograniczone do maksymalnie rozmiar równy 2 gigabajty, więc względną adresowania o pojemności 32-bitowych może służyć do adresów statycznych danych. Te dane obejmują tabelę adresów importu, stałe typu string, statycznych danych globalnych i tak dalej.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencje kodowania x64](../build/x64-software-conventions.md)