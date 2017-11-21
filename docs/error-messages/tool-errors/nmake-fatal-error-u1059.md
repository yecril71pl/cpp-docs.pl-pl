---
title: "Błąd krytyczny NMAKE U1059 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1059
dev_langs: C++
helpviewer_keywords: U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 70b1546068678c811f6123d3c8059dfd6d914f4d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="nmake-fatal-error-u1059"></a>Błąd krytyczny NMAKE U1059
Błąd składniowy: "}" brakuje w elemencie zależnym  
  
 Ścieżkę wyszukiwania dla zależną został niepoprawnie określony. Albo miejsca istniał w ścieżce lub zamykający nawias klamrowy (**}**) został pominięty.  
  
 Składnia specyfikacji katalogu dla zależną jest  
  
 **{**   
 ***katalogi* } zależne**  
  
 gdzie `directories` określa jeden lub więcej ścieżek rozdzielonych średnikami (**;**). Spacje nie są dozwolone.  
  
 Jeśli część lub całość ścieżki wyszukiwania zostanie zastąpiony przez makra, upewnij się, że istnieje bez spacji w rozwinięciu makra.