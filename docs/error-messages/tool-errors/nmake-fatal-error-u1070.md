---
title: "Błąd krytyczny NMAKE U1070 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1070
dev_langs: C++
helpviewer_keywords: U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d1efb239043e86cfa2013aed86db264a68638419
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="nmake-fatal-error-u1070"></a>Błąd krytyczny NMAKE U1070
cykl w definicji makra "makra"  
  
 Definicji makra danego zawiera makra, którego definicja zawiera danego makra. Definicje makr cykliczne są nieprawidłowe.  
  
## <a name="example"></a>Przykład  
 Poniższe definicje makr  
  
```  
ONE=$(TWO)  
TWO=$(ONE)  
```  
  
 spowodować następujący błąd:  
  
```  
cycle in macro definition 'TWO'  
```