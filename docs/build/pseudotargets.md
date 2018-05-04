---
title: Pseudo cele | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- makefiles, pseudotargets
- pseudotargets and NMAKE
- NMAKE program, pseudotargets
- timestamps, makefile pseudotargets
- NMAKE program, targets
ms.assetid: c8c479dc-0129-4186-8366-bc6251f2b494
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 67dbc6ae3ad331ab3297b62d00044c3edf679994
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="pseudotargets"></a>Pseudo cele
Pseudotarget jest używany zamiast nazwy pliku w wierszu zależności etykiety. Jest interpretowany jako plik, który nie istnieje i dlatego jest nieaktualne. NMAKE przyjęto założenie, że sygnatura czasowa pseudotarget jest najnowsza wszystkich jego zależności. Jeśli ma ona nie zależności, przyjęto, że bieżący czas. Jeśli pseudotarget jest używana jako miejsce docelowe, jego polecenia są zawsze wykonywane. Pseudotarget, używany jako zależną musi być określone jako cel w innym zależności. Jednak Zależność ta nie musi być blokiem poleceń.  
  
 Nazwy pseudotarget zgodne reguły Składnia nazwy pliku dla celów. Jednak jeśli nazwa nie ma rozszerzenia (to znaczy nie zawierają kropki), może przekroczyć limit 8 znaków w nazwach plików i może zawierać maksymalnie 256 znaków.  
  
## <a name="see-also"></a>Zobacz też  
 [Docelowe elementy](../build/targets.md)