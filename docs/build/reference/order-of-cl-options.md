---
title: "Kolejność opcji CL | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cl
dev_langs: C++
helpviewer_keywords: cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8ef67792b01d4d4dab535bfb180cd70beb2316b6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="order-of-cl-options"></a>Kolejność opcji CL
Opcje mogą występować w dowolnym miejscu w wierszu polecenia CL, z wyjątkiem opcji/Link musi występować jako ostatnia. Kompilator rozpoczyna się od określonego w opcji [zmiennej środowiskowej CL](../../build/reference/cl-environment-variables.md) i odczytuje wiersza polecenia od lewej do prawej — przetwarzania plików poleceń w kolejności ich wystąpienia. Każda opcja ma zastosowanie do wszystkich plików w wierszu polecenia. Jeśli CL napotka opcje powodujące konflikt, używa opcji po prawej stronie.  
  
## <a name="see-also"></a>Zobacz też  
 [Składnia wiersza polecenia kompilatora](../../build/reference/compiler-command-line-syntax.md)