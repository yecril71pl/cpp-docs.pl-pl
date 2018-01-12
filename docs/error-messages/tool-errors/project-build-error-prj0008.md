---
title: "Błąd PRJ0008 kompilacji projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0008
dev_langs: C++
helpviewer_keywords: PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1740b0cf1edfc90258de4fe26478298ddf2875c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0008"></a>Błąd PRJ0008 kompilacji projektu
Nie można usunąć pliku 'Plik'.  
  
 **Upewnij się, że plik nie jest otwarty przez inny proces i nie jest zabezpieczony przed zapisem.**  
  
 Podczas kompilowania lub czyszczenia, Visual C++ usuwa wszystkie znane plików pośrednich i wynikowych dla kompilacji, a także wszystkie pliki, które spełniają wymagania symbolu wieloznacznego w **rozszerzenia do usunięcia podczas oczyszczania** właściwości w [ogólne Strona właściwości ustawień konfiguracji](../../ide/general-property-page-project.md).  
  
 Zostanie wyświetlony ten błąd, jeśli Visual C++ nie można usunąć pliku. Aby rozwiązać problem, należy pliku i jego katalogu zapisywalny dla użytkownika podczas kompilacji.