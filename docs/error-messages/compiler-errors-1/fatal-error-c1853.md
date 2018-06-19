---
title: Błąd krytyczny C1853 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- devlang-cpp
ms.topic: error-reference
f1_keywords:
- C1853
dev_langs:
- C++
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9aa6a67c13f76b0bf43159b9e9de95068102a2b1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229212"
---
# <a name="fatal-error-c1853"></a>Błąd krytyczny C1853
  
> "*filename*" prekompilowany plik nagłówka pochodzi z poprzedniej wersji kompilatora lub prekompilowany nagłówek jest C++ i używania go w C (lub odwrotnie)  
  
Możliwe przyczyny:  
  
-   Prekompilowany nagłówek został skompilowany z poprzedniej wersji kompilatora. Spróbuj ponownej kompilacji nagłówek z bieżącego kompilatora.  
  
-   Prekompilowany nagłówek jest w C++ i korzystają z C. Spróbuj ponownej kompilacji nagłówka do użycia z C, określając jedną z [/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) — opcje kompilatora lub zmiana sufiksu pliku źródłowego "c". Aby uzyskać więcej informacji, zobacz [dwa wybory dla wstępnej kompilacji kodu](../../build/reference/creating-precompiled-header-files.md#two-choices-for-precompiling-code).