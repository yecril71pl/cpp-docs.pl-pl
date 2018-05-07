---
title: Błąd PRJ0008 kompilacji projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0008
dev_langs:
- C++
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4011a27b7e6707f9c9b4e3ed386306b00f2792cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="project-build-error-prj0008"></a>Błąd PRJ0008 kompilacji projektu
Nie można usunąć pliku 'Plik'.  
  
 **Upewnij się, że plik nie jest otwarty przez inny proces i nie jest zabezpieczony przed zapisem.**  
  
 Podczas kompilowania lub czyszczenia, Visual C++ usuwa wszystkie znane plików pośrednich i wynikowych dla kompilacji, a także wszystkie pliki, które spełniają wymagania symbolu wieloznacznego w **rozszerzenia do usunięcia podczas oczyszczania** właściwości w [ogólne Strona właściwości ustawień konfiguracji](../../ide/general-property-page-project.md).  
  
 Zostanie wyświetlony ten błąd, jeśli Visual C++ nie można usunąć pliku. Aby rozwiązać problem, należy pliku i jego katalogu zapisywalny dla użytkownika podczas kompilacji.