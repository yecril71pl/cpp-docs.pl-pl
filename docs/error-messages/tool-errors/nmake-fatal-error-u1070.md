---
title: Błąd krytyczny NMAKE U1070 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1070
dev_langs:
- C++
helpviewer_keywords:
- U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1fe39a5d6f6074596561cd8e32f7b9428bc60f6d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327044"
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