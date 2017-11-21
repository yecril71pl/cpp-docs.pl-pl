---
title: "Błąd krytyczny C1853 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1853
dev_langs: C++
helpviewer_keywords: C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 23b5302428fc216a8349e8cf022c184caa57202c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1853"></a>Błąd krytyczny C1853
  
> "*filename*" prekompilowany plik nagłówka pochodzi z poprzedniej wersji kompilatora lub prekompilowany nagłówek jest C++ i używania go w C (lub odwrotnie)  
  
Możliwe przyczyny:  
  
-   Prekompilowany nagłówek został skompilowany z poprzedniej wersji kompilatora. Spróbuj ponownej kompilacji nagłówek z bieżącego kompilatora.  
  
-   Prekompilowany nagłówek jest w C++ i korzystają z C. Spróbuj ponownej kompilacji nagłówka do użycia z C, określając jedną z [/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) — opcje kompilatora lub zmiana sufiksu pliku źródłowego "c". Aby uzyskać więcej informacji, zobacz [dwa wybory dla wstępnej kompilacji kodu](../../build/reference/creating-precompiled-header-files.md#two-choices-for-precompiling-code).