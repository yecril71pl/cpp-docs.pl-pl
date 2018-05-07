---
title: Błąd krytyczny NMAKE U1059 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1059
dev_langs:
- C++
helpviewer_keywords:
- U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6eb038befdb7c587c6fe2a734003abba585c3e2a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-fatal-error-u1059"></a>Błąd krytyczny NMAKE U1059
Błąd składniowy: "}" brakuje w elemencie zależnym  
  
 Ścieżkę wyszukiwania dla zależną został niepoprawnie określony. Albo miejsca istniał w ścieżce lub zamykający nawias klamrowy (**}**) został pominięty.  
  
 Składnia specyfikacji katalogu dla zależną jest  
  
 **{**   
 ***katalogi* } zależne**  
  
 gdzie `directories` określa jeden lub więcej ścieżek rozdzielonych średnikami (**;**). Spacje nie są dozwolone.  
  
 Jeśli część lub całość ścieżki wyszukiwania zostanie zastąpiony przez makra, upewnij się, że istnieje bez spacji w rozwinięciu makra.