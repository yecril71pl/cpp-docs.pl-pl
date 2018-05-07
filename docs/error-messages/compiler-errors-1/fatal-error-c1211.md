---
title: Błąd krytyczny C1211 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1211
dev_langs:
- C++
helpviewer_keywords:
- C1211
ms.assetid: df0ca70d-ec6e-4400-926a-b877e2599978
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4ef92816c157d6bbc72d7c7539f2d0644c70082b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1211"></a>Błąd krytyczny C1211
Atrybut niestandardowy TypeForwardedTo nie jest obsługiwana przez wersję środowiska uruchomieniowego zainstalowany  
  
 C1211 występuje, gdy masz kompilatora dla bieżącej wersji, ale środowisko uruchomieniowe języka wspólnego z poprzedniej wersji.  
  
 Niektóre funkcje kompilator może nie działać w poprzedniej wersji czasu wykonywania.  
  
 Aby rozwiązać C1211 install środowisko uruchomieniowe języka wspólnego dostarczonej przez kompilator używasz.  
  
 Aby uzyskać więcej informacji, zobacz [przesyłania dalej typu (C + +/ CLI)](../../windows/type-forwarding-cpp-cli.md).