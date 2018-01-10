---
title: Pseudo cele | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- makefiles, pseudotargets
- pseudotargets and NMAKE
- NMAKE program, pseudotargets
- timestamps, makefile pseudotargets
- NMAKE program, targets
ms.assetid: c8c479dc-0129-4186-8366-bc6251f2b494
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 761b71f05840c86516563df79d45cc1bb018fbba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="pseudotargets"></a>Pseudo cele
Pseudotarget jest używany zamiast nazwy pliku w wierszu zależności etykiety. Jest interpretowany jako plik, który nie istnieje i dlatego jest nieaktualne. NMAKE przyjęto założenie, że sygnatura czasowa pseudotarget jest najnowsza wszystkich jego zależności. Jeśli ma ona nie zależności, przyjęto, że bieżący czas. Jeśli pseudotarget jest używana jako miejsce docelowe, jego polecenia są zawsze wykonywane. Pseudotarget, używany jako zależną musi być określone jako cel w innym zależności. Jednak Zależność ta nie musi być blokiem poleceń.  
  
 Nazwy pseudotarget zgodne reguły Składnia nazwy pliku dla celów. Jednak jeśli nazwa nie ma rozszerzenia (to znaczy nie zawierają kropki), może przekroczyć limit 8 znaków w nazwach plików i może zawierać maksymalnie 256 znaków.  
  
## <a name="see-also"></a>Zobacz też  
 [Docelowe elementy](../build/targets.md)